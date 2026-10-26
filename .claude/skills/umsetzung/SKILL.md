---
name: umsetzung
description: Setzt ein Anforderungsdokument aus docs/anforderungen/ (erstellt mit dem Skill anforderungsanalyse) um. Bei Mechanik ist das die Konstruktion in Fusion über den MCP-Server mit Exporten, bei Elektronik Schaltplan und Platine in KiCad über den KiCad-MCP-Server sowie Firmware. Danach wird jede Anforderung gegen ihr Abnahmekriterium geprüft, Stückliste und Dokumentation werden aktualisiert und der Pull Request wird erstellt. Verwenden, wenn der Nutzer eine Baugruppe oder Anforderung bauen, konstruieren, umsetzen oder implementieren lassen will, z. B. „setze die Grundplatte um“ oder „konstruiere MECH-CHA“.
---

# Umsetzung von Anforderungen

Ziel: Ein Anforderungsdokument wird in Konstruktion, Elektronik oder Firmware umgesetzt. Jede Anforderung hat am Ende einen Nachweis. Alles landet als **ein Commit in einem Pull Request**.

## 1. Vorbereiten

1. **Aktuellen Stand holen** (Pflicht laut `AGENTS.md`):
   ```sh
   git switch main && git pull
   git switch -c <mech|elek|docs>/<baugruppe>
   ```
   Gibt es nicht committete fremde Änderungen, nicht verwerfen, sondern den Nutzer fragen.
   **Ausnahme:** Wird der Skill vom Skill `neue-anforderung` aufgerufen, existiert der Branch bereits. Dann auf diesem Branch weiterarbeiten und `main` nicht auschecken.

2. **Anforderungsdokument finden:** `docs/anforderungen/<baugruppe>.md`
   - **Es gibt keins:** Zuerst den Skill `anforderungsanalyse` ausführen. Nicht ohne Anforderungen konstruieren.
   - **Status „Entwurf“ mit offenen Punkten, die die Umsetzung blockieren:** Diese Punkte zuerst mit dem Nutzer klären (`AskUserQuestion`) und im Dokument nachtragen.
   - **Status „abgestimmt“:** loslegen.

3. **Kontext lesen:**
   - `docs/plan.md`: Entscheidungen und Fahrzeugparameter
   - Anforderungsdokumente der Baugruppen, die hier eine Schnittstelle haben
   - `bom/stueckliste.csv`: Zukaufteile und ihre Maße
   - Datenblätter oder Maßzeichnungen von Zukaufteilen, die die Konstruktion berührt. Fehlen Maße, nachfragen oder recherchieren und die Quelle notieren. Nicht schätzen.

4. **Umsetzungsplan:** Jede MUSS- und SOLL-Anforderung bekommt einen konkreten Schritt, z. B. „MECH-CHA-003 → Lochraster als rechteckiges Muster, Parameter `raster_abstand`“. Dem Nutzer den Plan kurz zeigen, wenn er Entscheidungen enthält, die nicht im Dokument stehen. Sonst direkt beginnen.

## 2a. Mechanik in Fusion umsetzen

**Verbindung prüfen:** `fusion_mcp_read` mit `queryType: "document", operation: "open"`. Antwortet der Server nicht, den Nutzer bitten, Fusion zu starten.

**Design wählen:** Bestehende Designs suchen (`queryType: "document", operation: "search"`) und öffnen, sonst in einem neuen Design arbeiten. Das Skelettmodell bzw. die Fahrzeugbaugruppe ist die Referenz für alle Maße.

**Arbeiten mit Skripten** (`fusion_mcp_execute`, `featureType: "script"`):
- Vor unbekannten API-Aufrufen die Doku abfragen: `fusion_mcp_read` mit `queryType: "apiDocumentation"`.
- Jedes Skript definiert `def run(_context: str):` und fängt **keine** Exceptions ab, sonst sieht man Fehler nicht.
- Skripte, die nur lesen, mit `readOnly: true` ausführen.
- Kleine Schritte: ein Skript pro logischem Schritt (Parameter, Skizze, Feature …), nicht alles auf einmal.
- Geht etwas schief: `fusion_mcp_update` mit `featureType: "undo"`, dann korrigieren.

**Konstruktionsregeln:**
- **Parameter zuerst:** Alle Maße, die die Anforderungen nennen oder die sich ändern könnten, als Benutzerparameter anlegen, z. B. `radstand` oder `wandstaerke_min`. Skizzen und Features beziehen sich auf diese Parameter, es gibt keine festen Zahlen in Features.
- **Eine Komponente pro Teil.** Komponenten nach der Dateikonvention benennen, z. B. `chassis-bodenplatte`.
- **Skizzen** vollständig bestimmen und auf Ursprung, Ebenen oder Skelettgeometrie beziehen.
- **Zukaufteile** als vereinfachte Hüllkörper modellieren: Außenmaße, Befestigungslöcher, Wellen. So lassen sich Kollisionen prüfen.
- **Druckteile (FDM):**
  - in den Bauraum von 256 × 256 × 256 mm passend
  - Wandstärke ≥ 1,2 mm
  - Bohrungen für Passungen +0,2 bis 0,3 mm
  - Überhänge ≤ 45° oder mit einer gut druckbaren Auflagefläche
  - Druckausrichtung überlegen und in der Komponentenbeschreibung notieren
- **Spätere Frästeile:** 2,5D, Innenradien ≥ 1,5 mm, keine Hinterschnitte. Werkzeugzugang von oben bedenken.

**Kontrolle nach jedem größeren Schritt:**
- Screenshot (`fusion_mcp_read`, `queryType: "screenshot"`), bei Bedarf aus mehreren Richtungen
- Zeitleiste auf Fehler prüfen (read-only-Skript, `healthState` der Zeitleisten-Elemente)
- Kollisionen mit angrenzenden Teilen und Hüllkörpern prüfen (`design.analyzeInterference`)

**Speichern und Exportieren:**
- Das Design in Fusion **nur speichern, wenn der Nutzer es ausdrücklich will**. Vor dem Export also fragen. Ausnahme: Beim Ablauf `neue-anforderung` wurde das schon bei der Freigabe geklärt. Diese Freigabe gilt dann.
- Exporte per Skript über `design.exportManager`:
  - `.f3d` der Baugruppe nach `cad/fusion/`
  - `.step` je Baugruppe nach `cad/step/`
  - `.stl` je Druckteil nach `print/stl/`, Name nach der Konvention aus `AGENTS.md`
- Absolute Pfade in das Repository verwenden.

## 2b. Elektronik in KiCad umsetzen

Elektronik wird in **KiCad 10** entworfen, über den **KiCad-MCP-Server** (in `.mcp.json` unter dem Namen `kicad`).

**Verbindung prüfen:**
- Sind keine KiCad-MCP-Tools verfügbar, nicht ohne den Server weitermachen. Den Nutzer bitten, den Server einzurichten bzw. KiCad zu starten. Manche Server brauchen ein laufendes KiCad mit aktivierter IPC-API.
- Vor dem ersten Einsatz die Tool-Liste des Servers ansehen, ebenso nach einem Wechsel des Servers. Die Tool-Namen hängen vom Server ab.

**Projekt:**
- Ein KiCad-Projekt pro Baugruppe in `electronics/<baugruppe>/`. Der Projektname entspricht der Baugruppe, z. B. `bec-platine.kicad_pro`, `.kicad_sch` und `.kicad_pcb`.
- Unterordner:
  - `fertigung/`: Gerber, Bohrdaten, BOM, Bestückungsdaten
  - `firmware/`
  - `lib/`: projekteigene Symbole, Footprints und 3D-Modelle, als projektlokale Bibliothekstabellen eingebunden
- KiCad-Dateien sind Text und werden **nicht** über LFS versioniert. Backups (`*-backups/`), `fp-info-cache` und `*.lck` gehören nicht ins Repository.

**Arbeiten mit dem MCP-Server:**
- Kleine Schritte: Bauteile platzieren, verbinden, ERC, dann den nächsten Block.
- Nach jedem Block die Netze und Verbindungen über den Server zurücklesen und prüfen.
- Nur im Projektordner der Baugruppe schreiben.

**Prüfen und Exportieren mit `kicad-cli`.** Das ist unabhängig vom MCP-Server und dient als verbindlicher Nachweis. Pfad unter macOS: `/Applications/KiCad/KiCad.app/Contents/MacOS/kicad-cli`
- ERC: `kicad-cli sch erc --severity-all --exit-code-violations -o fertigung/erc.rpt <projekt>.kicad_sch`
- DRC: `kicad-cli pcb drc --severity-all --schematic-parity --exit-code-violations -o fertigung/drc.rpt <projekt>.kicad_pcb`
- Gerber und Bohrdaten: `kicad-cli pcb export gerbers` bzw. `kicad-cli pcb export drill`, nach `fertigung/`
- BOM: `kicad-cli sch export bom`. Bestückungsdaten: `kicad-cli pcb export pos`.
- 3D-Modell der Platine: `kicad-cli pcb export step`. Dieses Modell wird in Fusion als Hüllkörper verwendet.
- Die Optionen von `kicad-cli` vor dem ersten Einsatz mit `--help` prüfen.

**Ablage:** `electronics/<baugruppe>/` (siehe oben)
- **Reihenfolge:**
  1. Blockschaltbild
  2. Bauteilauswahl mit Datenblatt und Verfügbarkeit
  3. Schaltplan
  4. ERC ohne Fehler
  5. Layout
  6. DRC ohne Fehler und ohne Abweichung zum Schaltplan
  7. Fertigungsdaten

  Bleiben Warnungen bewusst stehen, werden sie im Nachweis begründet.
- **Pflicht bei Leistung und Akku:** Verpolschutz, Absicherung, Unterspannungsabschaltung und Failsafe aus den Anforderungen nachweisbar umsetzen. Strompfade und Leiterbahnbreiten rechnen und die Rechnung in der Doku festhalten.
- **Mechanische Integration:** Platinenumriss und Befestigungslöcher passend zum Lochraster des Chassis. Den STEP-Export der Platine in Fusion einfügen und auf Kollisionen prüfen.
- **Firmware:** Build-Anleitung in `firmware/README.md`. Den Failsafe-Pfad zuerst implementieren und testen.

## 3. Nachweis

Jede Anforderung des Dokuments gegen ihr Abnahmekriterium prüfen und das Ergebnis im Anforderungsdokument im Abschnitt **„Nachweis“** eintragen:

| Status | Bedeutung |
|---|---|
| ✅ erfüllt | im Modell oder in der Schaltung geprüft (wie: Messung, Screenshot, Prüfskript, ERC/DRC) |
| 🔧 am Prototyp prüfen | nur physisch prüfbar, z. B. Gewicht, Testfahrt oder Temperatur |
| ❌ nicht erfüllt | mit Begründung. Den Nutzer fragen, ob die Anforderung angepasst oder die Lösung geändert wird. |

- **Nie eine Anforderung stillschweigend weglassen oder abschwächen.** Ist eine Anforderung nicht umsetzbar oder widersprüchlich, anhalten und den Nutzer fragen. Eine Änderung an der Anforderung im Dokument unter „Entscheidungen“ festhalten.
- Maße, die im Modell gemessen wurden, mit Zahlen angeben. „Passt“ allein reicht nicht.

## 4. Dokumentation aktualisieren

- `bom/stueckliste.csv`: Für jedes neue Teil eine Zeile mit Pos, Bezeichnung, Menge, Typ (Druckteil/Frästeil/Zukauf/Normteil), Material und Datei oder Bezugsquelle
- Anforderungsdokument: Status auf **umgesetzt** setzen, sobald alle MUSS-Anforderungen ✅ oder 🔧 sind, und das Datum aktualisieren
- `docs/plan.md`: den passenden Punkt abhaken. Neue Grundsatzentscheidungen eintragen.
- Optional: Montagehinweise oder Druckeinstellungen als Notiz für die spätere Bauanleitung in `docs/`

## 5. Pull Request

Nach `AGENTS.md`: **ein Commit pro PR.**
1. `git add` nur die Dateien dieser Anforderung
2. Ein Commit mit kurzer deutscher Nachricht, z. B. „Chassis: Grundplatte v1“
3. `git push -u origin <branch>`
4. `gh pr create` mit dieser Beschreibung:
   - **Zusammenfassung:** was gebaut wurde
   - **Umgesetzte Anforderungen:** alle IDs mit ihrem Nachweis-Status
   - **Screenshots:** in `docs/images/` ablegen und verlinken
   - **Offene Punkte:** besonders 🔧 und ❌
5. Korrekturen nach dem Review: `git commit --amend` und `git push --force-with-lease`

## 6. Abschluss

Dem Nutzer kurz berichten:
- Link zum PR
- welche Anforderungen erfüllt sind
- was erst am Prototyp geprüft werden kann
- was offen ist oder vom Plan abweicht
- was als Nächstes sinnvoll ist. Das ist in der Regel ein **Review mit dem Skill `review`**, am besten in einer frischen Sitzung. Danach kommt die nächste Baugruppe laut `docs/plan.md`.

Befunde aus einem Review werden mit diesem Skill behoben, im selben Branch per `git commit --amend` und `git push --force-with-lease`.

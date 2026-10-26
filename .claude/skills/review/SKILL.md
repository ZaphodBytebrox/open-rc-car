---
name: review
description: Prüft einen Pull Request des RC-Auto-Projekts unabhängig und kritisch, bevor er gemergt wird. Geprüft wird gegen das Anforderungsdokument, die Mechanik im Fusion-Modell (Druckbarkeit, Toleranzen, Schnittstellen, Kollisionen, Parametrik), die Elektronik in KiCad (eigener ERC/DRC-Lauf, Ströme, Schutzfunktionen) und die Projektregeln aus AGENTS.md. Verwenden, wenn der Nutzer einen PR, eine Konstruktion, eine Schaltung oder eine Umsetzung reviewen, prüfen oder abnehmen lassen will, z. B. „review PR 5“ oder „prüf mal die Grundplatte“.
---

# Review

Ziel: Fehler finden, bevor gedruckt, gefräst oder bestellt wird. Das Review ist **unabhängig**. Es übernimmt keine Aussage aus PR-Beschreibung oder Nachweis ungeprüft, sondern prüft selbst nach.

## Grundhaltung
- Das Review möglichst in einer **frischen Sitzung** oder einem Subagenten machen, nicht in der Sitzung, in der umgesetzt wurde.
- Jede Behauptung im Nachweis ist eine Hypothese. Maße selbst im Modell messen, ERC und DRC selbst laufen lassen.
- Nur Befunde mit konkretem Fehlerbild melden: Was passiert wann, z. B. „Bohrung 3,0 mm, M3-Schraube klemmt im Druck“. Geschmacksfragen sind höchstens Hinweise.
- **Nur lesen.** Das Review ändert keine Dateien, kein Modell und keine Schaltung. Korrekturen macht danach der Skill `umsetzung`. In Fusion nur read-only-Skripte (`readOnly: true`), Screenshots und Abfragen verwenden.

## 1. Vorbereiten
1. PR bestimmen: Nummer vom Nutzer, sonst der offene PR des aktuellen Branches (`gh pr view`).
2. Lokal auschecken: `gh pr checkout <nr>`. Gibt es nicht committete Änderungen, nicht verwerfen, sondern nachfragen.
3. Einlesen:
   - `gh pr view <nr>` (Beschreibung)
   - `gh pr diff <nr>` (Änderungen)
   - das betroffene Anforderungsdokument in `docs/anforderungen/`
   - `docs/plan.md` und die Anforderungen angrenzender Baugruppen
   - `AGENTS.md`

## 2. Anforderungen prüfen
- Ist **jede** MUSS- und SOLL-Anforderung im Abschnitt „Nachweis“ aufgeführt?
- Ist jeder ✅-Nachweis nachvollziehbar: ein Messwert, ein Prüfskript, ein ERC/DRC-Bericht? Nur „passt“ oder „erfüllt“ ohne Beleg ist ein Befund.
- Wurde eine Anforderung abgeschwächt, umformuliert oder weggelassen, ohne dass ein Eintrag unter „Entscheidungen“ steht?
- Ist 🔧 (am Prototyp prüfen) nur dort verwendet, wo eine Prüfung im Modell wirklich unmöglich ist?
- Sicherheit ist immer MUSS: LiPo-Schutz, Failsafe, Schutz vor drehenden Teilen. Fehlt davon etwas, ist das **blockierend**.

## 3. Mechanik prüfen (Fusion)
Das Design öffnen bzw. die exportierte Datei in Fusion ansehen und mit read-only-Skripten prüfen:
- **Zeitleiste:** Gibt es Features mit Fehlern oder Warnungen (`healthState`)?
- **Parametrik:**
  - Sind alle relevanten Maße Benutzerparameter?
  - Gibt es feste Zahlen in Features, die eigentlich von Parametern abhängen?
  - Nicht im Modell ändern. Stattdessen prüfen, welche Skizzen und Features sich auf welche Parameter beziehen.
- **Kollisionen:** `design.analyzeInterference` zwischen den neuen Teilen und den angrenzenden Teilen bzw. Hüllkörpern der Zukaufteile
- **Druckbarkeit (FDM):**
  - Bounding Box jedes Druckteils ≤ 256 × 256 × 256 mm
  - Mindestwandstärke ≥ 1,2 mm
  - Überhänge und Druckausrichtung
  - Brücken, scharfe Innenecken, die unter Last reißen
- **Toleranzen:** Bohrungen für Schrauben, Lager und Wellen mit +0,2 bis 0,3 mm. Lagersitze passend zur Lagergröße aus der Stückliste.
- **Schnittstellen:** Lochbilder und Maße gegen die Anforderungen der angrenzenden Baugruppen und gegen die Datenblätter der Zukaufteile prüfen
- **Belastung:** Plausibilität an kritischen Stellen wie Querlenkeraufnahmen, Dämpferbrücke und Motorhalter. Ist genug Material und Rippung da? Liegt die Schichtrichtung günstig zur Last?
- **Fräsbarkeit** (bei Teilen, die später aus Alu gefräst werden): 2,5D, Innenradien ≥ 1,5 mm, keine Hinterschnitte
- **Montage und Wartung:** Sind die Schrauben mit Werkzeug erreichbar? Lassen sich Verschleißteile tauschen?
- **Optik:** Screenshots aus mehreren Richtungen (`fusion_mcp_read`, `queryType: "screenshot"`)

## 4. Elektronik prüfen (KiCad)
- **Eigener Lauf mit `kicad-cli`**, die Berichte im PR nicht übernehmen. Pfad unter macOS: `/Applications/KiCad/KiCad.app/Contents/MacOS/kicad-cli`
  - `kicad-cli sch erc --severity-all --exit-code-violations <projekt>.kicad_sch`
  - `kicad-cli pcb drc --severity-all --schematic-parity --exit-code-violations <projekt>.kicad_pcb`
  - Gibt es Warnungen, die nicht im Nachweis begründet sind? Das ist ein Befund.
- Schaltung über den KiCad-MCP-Server lesen, dann prüfen:
  - **Leistungspfad:** Leiterbahnbreiten und Kupferflächen für den Spitzenstrom, Vias parallel bei hohem Strom, Steckerbelastbarkeit (XT60 etwa 60 A)
  - **Schutz:** Verpolschutz, Sicherung, Unterspannungsabschaltung, Überstrom, Übertemperatur
  - **Failsafe:** Ist bei Signalverlust ein definierter Zustand garantiert (Motor aus), auch in Hardware, z. B. Pull-down am Gate-Treiber oder ein definierter Reset-Zustand?
  - **Bauteile:** Spannungs- und Stromreserven (Daumenregel: ≥ 1,5 × Maximalwert), Verlustleistung und Kühlung, Verfügbarkeit
  - **Signale:** Pegel zwischen den Bausteinen passen zusammen, Entkopplung an jedem IC, Programmierschnittstelle zugänglich
- **Mechanische Integration:** Platinenumriss und Befestigungslöcher zum Lochraster des Chassis. Das STEP-Modell ist im Fusion-Modell kollisionsfrei.
- **Firmware** (falls Teil des PR): Failsafe-Pfad und Abschaltungen sind implementiert. Die Build-Anleitung funktioniert.

## 5. Formales prüfen (AGENTS.md)
- Genau **ein Commit** im PR: `gh pr view <nr> --json commits`
- PR-Beschreibung mit Anforderungs-IDs, Nachweis-Status und offenen Punkten
- `bom/stueckliste.csv` enthält alle neuen Teile mit Datei oder Bezugsquelle
- Dateinamen nach Konvention. Exporte vorhanden: `.f3d`, `.step`, `.stl` bzw. Fertigungsdaten
- Binärdateien über LFS (`git lfs ls-files`), KiCad-Dateien nicht über LFS. Keine Backups oder Temporärdateien im Commit.
- Status des Anforderungsdokuments und Haken in `docs/plan.md` aktualisiert

## 6. Ergebnis
Befunde nach Schwere sortieren:

| Schwere | Bedeutung |
|---|---|
| 🔴 **blockierend** | Funktion, Sicherheit oder eine MUSS-Anforderung verletzt. Nicht mergen. |
| 🟡 **sollte behoben werden** | SOLL-Anforderung, Druckbarkeit, Wartbarkeit, Regelverstoß |
| 🔵 **Hinweis** | Verbesserung, kein Fehler |

Jeder Befund nennt:
- **Ort:** Datei, Komponente oder Feature, Bauteil-Referenz oder Netz
- **Fehlerbild:** Was passiert, und unter welchen Bedingungen?
- **Beleg:** Messwert, Screenshot, Ausgabe von ERC/DRC
- **Vorschlag** zur Behebung

Zum Schluss kommt ein **Fazit**: mergebereit, mergebereit nach den 🟡-Punkten oder nicht mergebereit.

Das Ergebnis dem Nutzer im Chat zeigen. **Nur wenn der Nutzer es will**, als PR-Kommentar posten: `gh pr comment <nr> --body-file <datei>`. Danach behebt der Skill `umsetzung` die Befunde per `git commit --amend` und `git push --force-with-lease`. Anschließend läuft ein erneutes Review nur für die geänderten Stellen.

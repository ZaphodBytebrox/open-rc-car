---
name: neue-anforderung
description: Steuert den ganzen Ablauf für eine neue Anforderung des Nutzers an das RC-Auto (Mechanik oder Elektronik). Zuerst wird die Anforderung mit dem Skill anforderungsanalyse bewertet und dokumentiert, dann wird auf die Freigabe des Nutzers gewartet. Danach wechseln sich eigene Agenten für Umsetzung und Review ab, bis das Review keine wesentlichen Befunde mehr hat (höchstens 5 Durchläufe). Verwenden, wenn der Nutzer eine neue Anforderung, Baugruppe oder Funktion gibt und sie vollständig bis zum PR bearbeitet haben will, z. B. „neue Anforderung: …“, „bau mir …“ oder „ich brauche eine Halterung für …“.
---

# Neue Anforderung: von der Idee zum geprüften PR

Ablauf: **Analyse → Freigabe → (Umsetzung → Review → Einarbeitung) × höchstens 5 → Übergabe an den Nutzer zum Merge**

Die Analyse und die Freigabe laufen in der Hauptsitzung, weil nur sie mit dem Nutzer sprechen kann. Umsetzung, Review und Einarbeitung laufen in **eigenen Agenten**. So prüft das Review unabhängig von der Umsetzung.

## Phase 1: Vorbereiten
1. `git switch main && git pull` (Pflicht laut `AGENTS.md`). Gibt es nicht committete fremde Änderungen, nachfragen und nichts verwerfen.
2. Branch anlegen: `git switch -c <mech|elek|docs>/<baugruppe>`. Alle späteren Agenten arbeiten auf **diesem** Branch.

## Phase 2: Anforderungen analysieren (Hauptsitzung)
1. Den Skill `anforderungsanalyse` vollständig durchführen. Dabei wird nachgefragt, wo etwas unklar ist, und `docs/anforderungen/<baugruppe>.md` geschrieben.
2. Es dürfen keine offenen Punkte übrig sein, die die Umsetzung blockieren. Sonst weiter nachfragen.

## Phase 3: Freigabe abwarten (Pflicht)
1. Dem Nutzer eine kurze Zusammenfassung zeigen:
   - Zweck
   - die MUSS-Anforderungen mit ihren IDs
   - die wichtigsten Annahmen
   - was bewusst *nicht* Teil der Aufgabe ist
   - Pfad zum Dokument
2. Mit `AskUserQuestion` fragen. Optionen:
   - **Freigeben**: Umsetzung starten. Dazu gehört die Erlaubnis, das Fusion-Design zu speichern und nach `cad/` und `print/` zu exportieren, weil die Agenten nicht nachfragen können.
   - **Freigeben ohne Speichern in Fusion**: Die Agenten konstruieren, speichern aber nicht in Fusion und exportieren nicht. Das macht der Nutzer am Ende selbst.
   - **Ändern**: Der Nutzer nennt Änderungen. Zurück zu Phase 2, danach erneut freigeben lassen.
3. **Ohne ausdrückliche Freigabe wird nichts umgesetzt.** Schweigen, Rückfragen oder „sieht gut aus, aber …“ sind keine Freigabe.
4. Nach der Freigabe: Status im Dokument auf **abgestimmt** setzen und die Freigabe mit Datum unter „Entscheidungen“ eintragen.

## Phase 4: Umsetzen und reviewen (eigene Agenten, höchstens 5 Durchläufe)

**Ein Durchlauf** besteht aus Umsetzung bzw. Einarbeitung (Agent) und anschließendem Review (neuer Agent).

**Agenten nacheinander starten, nie parallel.** Fusion und KiCad sind jeweils nur einmal vorhanden, und die Agenten teilen sich Branch und Arbeitsverzeichnis.

### Durchlauf 1: Umsetzung
Agent starten (`Agent`, `subagent_type: "general-purpose"`). Prompt-Vorlage:

> Setze die Anforderungen in `docs/anforderungen/<baugruppe>.md` um. Folge dabei genau der Anleitung in `.claude/skills/umsetzung/SKILL.md` und den Regeln in `AGENTS.md`.
> - Du arbeitest auf dem bereits vorhandenen Branch `<branch>`. Lege keinen neuen Branch an und checke nicht `main` aus.
> - Freigabe des Nutzers: <mit / ohne> Speichern und Export in Fusion.
> - Du kannst den Nutzer nicht fragen. Triffst du auf eine Frage, die die Umsetzung blockiert, oder ist eine Anforderung nicht umsetzbar: Brich ab, ändere die Anforderung nicht, und melde die Frage mit Optionen und Empfehlung zurück.
> - Am Ende: ein Commit, Push, PR erstellen (bzw. bei vorhandenem PR: `--amend` und `push --force-with-lease`).
> - Melde zurück: PR-Nummer, Nachweis-Status je Anforderungs-ID, offene Punkte, Abweichungen.

### Review (in jedem Durchlauf)
Immer einen **neuen** Agenten starten, nie den Umsetzungs-Agenten wiederverwenden. Prompt-Vorlage:

> Mache ein Review von PR #<nr>. Folge dabei genau `.claude/skills/review/SKILL.md`.
> - Ändere keine Dateien, kein Modell und keine Schaltung. Poste nichts in den PR.
> - Der Branch ist bereits ausgecheckt.
> - Melde alle Befunde mit Schwere (🔴/🟡/🔵), Ort, Fehlerbild, Beleg und Vorschlag zurück, dazu ein Fazit.

### Auswerten nach jedem Review
- **Keine 🔴- und keine 🟡-Befunde:** fertig, weiter mit Phase 5.
- **Es gibt 🔴/🟡-Befunde und der Durchlauf ist < 5:** Agent für die Einarbeitung starten (siehe unten). Danach den nächsten Durchlauf mit neuem Review.
- **Durchlauf 5 erreicht:** abbrechen, weiter mit Phase 5 und die offenen Befunde melden.
- **Früh abbrechen und den Nutzer fragen, wenn:**
  - ein Agent eine blockierende Frage meldet. Den Nutzer fragen, die Antwort im Anforderungsdokument festhalten und mit derselben Durchlaufzahl fortfahren.
  - derselbe Befund in zwei Reviews hintereinander wieder auftaucht, die Einarbeitung ihn also nicht löst
  - ein Befund eine Änderung an einer Anforderung verlangt. Anforderungen ändert nur der Nutzer.

### Einarbeitung
Neuen Agenten starten. Prompt-Vorlage:

> Arbeite die folgenden Review-Befunde zu PR #<nr> ein (Branch `<branch>`, Anforderungen in `docs/anforderungen/<baugruppe>.md`). Folge dabei `.claude/skills/umsetzung/SKILL.md`.
> - Behebe alle 🔴- und 🟡-Befunde. 🔵-Hinweise nur, wenn sie trivial sind.
> - Aktualisiere den Nachweis.
> - Ein Commit per `git commit --amend` und `git push --force-with-lease`, kein neuer PR.
> - Du kannst den Nutzer nicht fragen. Hältst du einen Befund für falsch oder ist er nur durch eine Änderung der Anforderung lösbar: Ändere nichts daran und melde es mit Begründung zurück.
> - Befunde: <Liste aus dem Review, vollständig mit Ort, Fehlerbild, Beleg und Vorschlag>

Meldet der Einarbeitungs-Agent einen Befund als falsch, diesen Widerspruch im nächsten Review-Prompt mitgeben. Das neue Review entscheidet dann unabhängig.

## Phase 5: Übergabe an den Nutzer
Kurz berichten:
- **Ergebnis:** PR-Link, mergebereit ja oder nein
- **Durchläufe:** Anzahl, mit den Befunden pro Durchlauf in je einer Zeile
- **Nachweis:** welche Anforderungen ✅ sind, welche 🔧 (am Prototyp prüfen)
- **Offen:** verbleibende Befunde, besonders wenn nach 5 Durchläufen abgebrochen wurde, sowie 🔵-Hinweise
- **Nächster Schritt:** Merge durch den Nutzer. Den Review-Bericht nur auf Wunsch als PR-Kommentar posten.

Gemergt wird **nie** durch einen Agenten, sondern immer durch den Nutzer.

# AGENTS.md – Arbeitsanweisungen für KI-Agenten

Diese Datei gilt für alle KI-Agenten, die in diesem Repository arbeiten (Claude Code, Codex, Copilot usw.).

## Projekt
Open-Source-RC-Auto im Maßstab 1:10 (Allround-Buggy). CAD in Autodesk Fusion, 3D-Druckteile, später gefräste Aluteile und eigene Elektronik. **Projektsprache ist Deutsch:** Dokumentation, Commit-Nachrichten und PR-Beschreibungen schreiben wir auf Deutsch.

Bevor du größere Arbeiten beginnst, lies `docs/plan.md`. Dort stehen der Gesamtplan und die Grundsatzentscheidungen.

## Git-Workflow
- **Vor jeder neuen Anforderung zuerst den aktuellen Stand holen.** Erst danach mit der Arbeit beginnen:
  ```sh
  git switch main
  git pull
  git switch -c <art>/<kurzbeschreibung>
  ```
  Gibt es nicht committete Änderungen, die nicht zur neuen Anforderung gehören, nicht verwerfen, sondern beim Nutzer nachfragen.
- **Ein Pull Request pro Anforderung.** Jede Anforderung bzw. Aufgabe bekommt einen eigenen Branch und einen eigenen PR. Zwei Anforderungen kommen nie in denselben PR.
- **Ein Commit pro Pull Request.** Bei Korrekturen während des Reviews den Commit ändern (`git commit --amend`) und mit `git push --force-with-lease` hochladen. Es kommen keine zusätzlichen Commits dazu.
- Nie direkt auf `main` committen.
- Branch-Namen: `<art>/<kurzbeschreibung>`. Art ist zum Beispiel:
  - `mech/hinterachse-querlenker`
  - `elek/bec-platine`
  - `docs/bauanleitung-grundplatte`
  - `setup/...`
- Commit-Nachricht und PR-Titel: kurze Beschreibung auf Deutsch, z. B. „Hinterachse: Querlenker und Radträger“.
- Wenn der PR Anforderungen aus `docs/anforderungen/` umsetzt, nennt die PR-Beschreibung deren IDs (z. B. `MECH-CHA-003`). Außerdem beschreibt sie, wie die Umsetzung geprüft wurde.

## Anforderungen
- Vor jeder neuen Baugruppe (Mechanik oder Elektronik) eine Anforderungsanalyse machen. Claude Code nutzt dafür den Skill `anforderungsanalyse` in `.claude/skills/`, andere Agenten folgen derselben Anleitung.
- Unklare Anforderungen werden beim Nutzer nachgefragt und nicht geraten.
- Ergebnis: `docs/anforderungen/<baugruppe>.md`
- Grundsatzentscheidungen kommen zusätzlich in `docs/plan.md` unter „Entscheidungen“.

## Struktur
| Ordner | Inhalt |
|---|---|
| `cad/fusion/` | Fusion-Quelldateien (`.f3d`) |
| `cad/step/` | STEP-Exporte |
| `print/stl/`, `print/3mf/` | Druckdateien |
| `electronics/` | Schaltpläne, Platinen, Firmware |
| `bom/stueckliste.csv` | Stückliste |
| `docs/` | Plan, Anforderungen, Bauanleitung |

## Konventionen
- Dateinamen: Kleinbuchstaben und Bindestriche, Baugruppe vorne. Beispiele:
  - `chassis-bodenplatte.stl`
  - `lenkung-achsschenkel-links.step`
- Einheiten: Millimeter. Normteile metrisch, bevorzugt M3.
- Jedes neue Teil kommt in `bom/stueckliste.csv`, mit Datei oder Bezugsquelle.
- Binärdateien (f3d, step, stl, 3mf, Bilder, pdf) laufen über Git LFS (siehe `.gitattributes`).
- Teile, die später aus Alu gefräst werden sollen, werden fräsgerecht konstruiert: 2,5D, Innenradien ≥ 1,5 mm.

## Fusion (MCP-Server)
- Der Fusion-MCP-Server läuft lokal (`.mcp.json`, `http://127.0.0.1:27182/mcp`) und braucht ein laufendes Fusion.
- Maße werden als benannte Benutzerparameter angelegt (z. B. `radstand`, `spurbreite`), damit das Modell parametrisch bleibt.
- Nach Änderungen am Modell einen Screenshot zur Kontrolle machen.
- Fusion speichert Designs in der Cloud. Für das Repository das Design als `.f3d` nach `cad/fusion/` und als `.step` nach `cad/step/` exportieren.

## Sicherheit
- LiPo-Schutz, Failsafe bei Signalverlust und Schutz vor drehenden Teilen sind immer Pflicht (MUSS) und werden nie weggelassen.

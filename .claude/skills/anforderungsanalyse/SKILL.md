---
name: anforderungsanalyse
description: Analysiert die Anforderungen an eine neue Baugruppe, ein Bauteil oder eine Elektronik des RC-Autos, deckt Lücken, Widersprüche und Unklarheiten auf und fragt gezielt beim Nutzer nach, bevor konstruiert wird. Verwenden, bevor CAD-Arbeit in Fusion, ein Schaltplan oder eine Platine begonnen wird, wenn eine Anforderung vage ist ("mach mal eine Aufhängung", "ich brauche einen Fahrtenregler") oder wenn der Nutzer Anforderungen klären, prüfen oder dokumentieren will. Gilt für mechanisches und elektronisches Design.
---

# Anforderungsanalyse

Ziel: Bevor etwas konstruiert wird, liegt ein kurzes, prüfbares Anforderungsdokument vor. Was unklar ist, wird gefragt und nicht geraten.

## Ablauf

### 1. Kontext sammeln (ohne Nachfrage)
Erst lesen, dann fragen. Nichts fragen, was schon im Repository steht:
- `docs/plan.md`: Gesamtplan, Grundsatzentscheidungen wie Maßstab, Antrieb und Akku
- `docs/anforderungen/`: vorhandene Anforderungen, besonders die von angrenzenden Baugruppen
- `bom/stueckliste.csv`: bereits gewählte Zukaufteile
- `AGENTS.md`: Konventionen und Git-Workflow
- Falls Fusion läuft und es um ein bestehendes Modell geht: Parameter und Screenshot über den Fusion-MCP-Server

### 2. Einordnen
- Domäne: **Mechanik**, **Elektronik** oder **beides**
- Ebene: Gesamtfahrzeug, Baugruppe (z. B. Vorderachse) oder Einzelteil (z. B. Achsschenkel)
- Schnittstellen: Mit welchen anderen Baugruppen ist es mechanisch, elektrisch oder über Signale verbunden?

### 3. Mit der Checkliste prüfen
Die passende Checkliste unten durchgehen. Jeden Punkt einordnen:
- **bekannt**: steht im Repository oder hat der Nutzer gesagt
- **ableitbar**: folgt eindeutig aus Bekanntem. Als Annahme notieren und kurz nennen.
- **offen**: muss der Nutzer entscheiden

Außerdem prüfen:
- **Widersprüche**, z. B. „leicht“ und „unzerstörbar“, oder eine Teilegröße, die größer als der Bauraum des Druckers ist
- **Messbarkeit**: Für „stabil“, „schnell“ oder „klein“ einen Zahlenwert vorschlagen

### 4. Nachfragen
- Fragen mit dem Tool `AskUserQuestion` stellen, höchstens 4 pro Runde.
- Nach Auswirkung sortieren: Zuerst kommen Entscheidungen, von denen viel abhängt, z. B. Maßstab vor Schraubengröße.
- Jede Frage bekommt konkrete Optionen mit Vor- und Nachteilen. Die empfohlene Option steht zuerst und ist mit „(Empfohlen)“ markiert.
- Keine Fragen stellen, die eine sinnvolle Standardannahme beantwortet. Die Annahme stattdessen im Dokument festhalten.
- Wenn nach einer Runde noch Wesentliches offen ist, eine zweite Runde stellen. Kleinigkeiten kommen unter „Offene Punkte“.

### 5. Dokumentieren
Das Ergebnis als `docs/anforderungen/<baugruppe>.md` schreiben, nach der Vorlage in `vorlage.md` im Skill-Ordner. Regeln:
- Jede Anforderung hat eine ID: `MECH-<KÜRZEL>-001` oder `ELEK-<KÜRZEL>-001`. Das Kürzel steht für die Baugruppe, z. B. `CHA` für Chassis oder `ESC` für den Fahrtenregler.
- Jede Anforderung hat eine Priorität: **MUSS**, **SOLL** oder **KANN**.
- Jede MUSS-Anforderung hat ein prüfbares Abnahmekriterium, also eine Zahl, einen Test oder eine Sichtprüfung.
- Annahmen und Nutzerentscheidungen stehen getrennt, damit später klar ist, was bewusst entschieden wurde.
- Neue Grundsatzentscheidungen, die mehrere Baugruppen betreffen, auch in `docs/plan.md` unter „Entscheidungen“ eintragen.

### 6. Abschluss
Dem Nutzer in wenigen Sätzen sagen:
- welche Entscheidungen jetzt feststehen
- welche Annahmen getroffen wurden
- was noch offen ist
- ob die Konstruktion starten kann

## Checkliste Mechanik

- **Funktion:** Was muss das Teil tun? Welche Bewegungen und Freiheitsgrade hat es? Welcher Federweg, Lenkwinkel oder welches Spiel ist nötig?
- **Lasten:** Gewicht des Fahrzeugs, Sprünge und Stöße (Annahme: etwa 5 g bei Offroad), Drehmoment vom Motor, Crash-Fall. Welches Teil darf als Sollbruchstelle versagen?
- **Bauraum und Maße:** Hüllmaße und Bezug zu den Fahrzeugparametern (Radstand, Spurbreite, Bodenfreiheit, Raddurchmesser)
- **Schnittstellen:** Befestigungspunkte, Schraubengrößen (Standard M3), Lochraster, Achsdurchmesser, Lager (Standardgrößen wie 5×11×4 oder 10×15×4), Kompatibilität zu Zukaufteilen
- **Fertigung:**
  - Verfahren: FDM-Druck, Kauf, Fräsen
  - Bauraum des Druckers
  - Druckausrichtung und Überhänge
  - Mindestwandstärke (FDM ab 1,2 mm)
  - Toleranzen: Passungen für Bohrungen +0,2 bis 0,3 mm, Gewindeeinsätze oder selbstschneidende Schrauben
- **Material:** PLA, PETG, ASA, PA-CF oder TPU (Reifen, Dämpfung). Dabei Temperatur am Motor und am Fahrtenregler, Schlagzähigkeit und UV-Beständigkeit bedenken.
- **Gewicht und Schwerpunkt**
- **Wartung:** Zugang zu Akku, Elektronik und Verschleißteilen. Kann man Teile ohne vollständige Demontage tauschen?
- **Normteile:** Verfügbarkeit, z. B. bei üblichen Händlern oder als Ersatzteil gängiger RC-Modelle
- **Parametrik:** Welche Maße sollen in Fusion als Benutzerparameter angelegt werden?

## Checkliste Elektronik

- **Funktion:** Was soll die Schaltung tun? Welche Betriebsarten gibt es, z. B. vorwärts, rückwärts, Bremse?
- **Versorgung:** Akkutyp und Zellzahl (z. B. LiPo 2S = 6,0–8,4 V), Spannungsbereich, Ruhestrom
- **Ströme und Leistung:** Dauer- und Spitzenstrom, Motordaten (KV, Typ bürstenbehaftet oder bürstenlos, sensored oder sensorless)
- **Schnittstellen:**
  - Stecker (XT60, XT30, Servo-JST, MR30)
  - Signale: PWM 50 Hz mit 1000–2000 µs, SBUS, CRSF/ELRS, PPM
  - Ausgang für die Empfängerversorgung (BEC: Spannung und Strom)
- **Schutz:**
  - Verpolung
  - Unterspannung (LiPo-Abschaltung ab etwa 3,3 V pro Zelle)
  - Überstrom und Übertemperatur
  - **Failsafe bei Signalverlust:** Motor aus und Lenkung neutral. Das ist immer MUSS.
- **Thermik:** Verlustleistung, Kühlung, Platz für einen Kühlkörper im Chassis
- **Mechanische Integration:** Platinengröße, Befestigungslöcher, Gehäuse, Schutz vor Spritzwasser und Staub
- **Funk und Regeln:**
  - Frequenzband (2,4 GHz)
  - Für die selbst gebaute Fernsteuerung: vorzugsweise zugelassene Module oder offene Protokolle wie ExpressLRS, CE/RED beachten
- **Fertigbarkeit:** Bauteile verfügbar (z. B. LCSC/JLCPCB), Handlötbarkeit oder Bestückung durch den Fertiger, Lagenzahl
- **Firmware:** Mikrocontroller, Programmierschnittstelle, Konfiguration, Update-Weg
- **Test:** Wie wird die Schaltung sicher getestet, z. B. mit strombegrenztem Labornetzteil und ohne Rad am Boden?

## Grundsätze
- Lieber eine gezielte Frage zu viel als eine falsche Annahme bei einer Grundsatzentscheidung.
- Bei Details lieber eine dokumentierte Annahme als eine Frage zu viel.
- Für die erste Version Zukaufteile bevorzugen und Schnittstellen so festlegen, dass Eigenbauten sie später ersetzen können. Beispiele: Befestigungsraster für den Fahrtenregler, Standard-Servo-Aufnahme, XT60.
- Sicherheit (LiPo, Failsafe, drehende Teile) nie als KANN einstufen.

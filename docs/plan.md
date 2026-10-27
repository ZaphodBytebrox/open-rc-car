# Grobplan open-rc-car

**Stand:** 2026-10-27

Ziel: ein offenes 1:10-Allround-Buggy zum Selberbauen. Version 1 fährt mit gedruckten Teilen und zugekauftem Fahrtenregler, Motor und Fernsteuerung. Danach werden Schritt für Schritt Teile durch eigene Konstruktionen ersetzt: Allrad, gefräste Aluteile und eigene Elektronik.

## Entscheidungen

| Datum | Thema | Entscheidung |
|---|---|---|
| 2026-10-26 | Maßstab | 1:10 |
| 2026-10-26 | Einsatz | Allround/Buggy: Wiese, Schotter, Asphalt |
| 2026-10-26 | Antrieb | Zuerst 2WD (hinten). Die Grundplatte wird von Anfang an für 4WD ausgelegt. |
| 2026-10-26 | Fertigung v1 | FDM-Druck mit Bauraum 256 × 256 mm. Zahnräder, Dämpfer, Lager usw. werden zugekauft. |
| 2026-10-26 | Fertigung später | Grundplatte und hoch belastete Teile aus Alu, auf der eigenen Portalfräse gefräst |
| 2026-10-26 | Motor/Regler v1 | Brushless sensorless, 2S LiPo, XT60 |
| 2026-10-26 | Fernsteuerung v1 | ExpressLRS (ELRS) |
| 2026-10-26 | Lenkservo | Standardservo 40 × 20 mm |
| 2026-10-26 | Elektronik-Werkzeug | KiCad 10 über einen KiCad-MCP-Server; Prüfung und Export mit `kicad-cli` |
| 2026-10-26 | KiCad-MCP-Server | `kicad-mcp-pro` 4.4.0 (MIT, unterstützt KiCad 10), Profil `builder` (216 Tools), Modus `write`. Verworfen: Konnect (wird archiviert, Nachfolger ist Closed Source) und `mcp-server-kicad` (nur noch Wartung). |
| 2026-10-26 | Höchstgeschwindigkeit und Budget v1 | ca. 50 km/h; Zukaufteile v1 600–1050 € inkl. Versand (ohne Sender, Ladegerät, Werkzeug); am 2026-10-26 erst wegen der Dämpfer von 600–900 € auf 600–1000 €, dann für die vollständige Liste mit allen Kleinteilen auf 600–1050 € angehoben |
| 2026-10-26 | Spenderplattform | Team Losi Racing 22X-4 (Ersatzteile der Elite, Bausatz TLR03026): 4WD, Kegelrad-Diffs vorne und hinten, CVA-Wellen, 12-mm-Sechskant, Spur 250 mm, Radstand 283,5 mm. Verglichen mit RC10B74.2 und XRAY XB4, Begründung in `docs/zukaufteile-v1.md` |
| 2026-10-26 | Zahnrad-Pitch | 48 Pitch; Diff-Übersetzung 2,5 : 1; Hauptzahnrad 78 Z, Motorritzel 26 Z (rechnerisch 51,4 km/h im Leerlauf, real darunter; am Prototyp messen) |
| 2026-10-26 | Mittelantrieb v1 | Rutschkupplung TLR232137 statt Mitteldiff (ein offenes Mitteldiff treibt bei freiem Vorderabtrieb hinten nicht an); Abtrieb nach vorne bleibt für 4WD |
| 2026-10-26 | Motor/Regler v1 | Hobbywing QuicRun 3652SL G2 3250 kV + QuicRun WP10BL60 G2; Unterspannung 3,4 V/Zelle, BEC 6 V/3 A |
| 2026-10-27 | Servoversorgung v1 | **Nutzerentscheidung:** Externer BEC Hobbywing UBEC 10A V2 auf 6,0 V für Empfänger und Servo statt Regler-BEC, weil das Servo Savöx SC-1258TG+ bis 5 A Blockierstrom zieht und der Regler-BEC nur 3 A liefert; rote Ader des Regler-Steuerkabels abziehen. Der Reglerschalter schaltet Empfänger und Servo dann nicht ab → Akku nach der Fahrt sofort abstecken |
| 2026-10-26 | Räder v1 | Allround-Räder Carson All Terrain 4WD (Ø 85 × 40 mm, 12 mm Sechskant, fertig verklebt) statt weicher Rennreifen; Einsatz auch auf Asphalt, längere Haltbarkeit. Nutzerentscheidung 2026-10-27: Räder bleiben, Einpresstiefe, Nabentiefe und Felgengröße werden am Teil gemessen, die Konstruktion gleicht über Radträger und Mitnehmer aus |
| 2026-10-26 | ELRS-Empfänger | HelloRadio HR7E (8 PWM-Ausgänge, ExpressLRS), Firmware mit Regulatory Domain EU_CE_2400 (LBT); Failsafe Kanal 2 (Gas) = 1500 µs, Kanal 1 (Lenkung) = 1500 µs |
| 2026-10-26 | Bezugsquellen v1 | Horizon Hobby EU (TLR-Teile, Lager 5x13x4), Modellbau Lindinger (Elektronik, Räder, Normteile), RC Team (Akku, Lager, XT60, UBEC); Stückliste `bom/stueckliste.csv` |
| 2026-10-27 | Radstand | **283,5 mm** statt 280 mm, wie der Spender TLR 22X-4; die Mittelwellen 93/68 mm sind darauf abgestimmt (`docs/anforderungen/skelett.md`) |
| 2026-10-27 | Skelettmodell | Fusion-Projekt „open-rc-car“, Design „open-rc-car-skelett“ (Hybrid-Design). Ergebnis: alles passt, Grundplatte 335,5 × 154 mm, für den Druck geteilt bei X = 50 mm mit 30 mm Überlappung (Teile 232,75 und 132,75 mm lang), siehe `docs/skelett.md` |

## Vorgeschlagene Architektur (noch zu bestätigen)

**Mittelmotor-Layout:** Motor und Hauptzahnrad sitzen in der Fahrzeugmitte. Eine Kardanwelle führt zum Hinterachsdifferential.
- In v1 ist nur der hintere Abtrieb belegt.
- Für 4WD kommen eine zweite Welle und ein Vorderachsdifferential dazu. Grundplatte, Motorhalter und Schwerpunkt bleiben gleich.
- So muss für den Umstieg auf Allrad nichts neu konstruiert werden.

**Grundplatte:** flache Platte mit Oberdeck für die Steifigkeit.
- Im Druck-Prototyp wird sie in zwei Teilen gedruckt (vorne und hinten) und verschraubt.
- Die Aluversion ist ein durchgehendes Frästeil mit gleichen Lochbildern. Deshalb wird die Geometrie von Anfang an fräsgerecht konstruiert: 2,5D, Innenradien ≥ 1,5 mm, keine Hinterschnitte.

**Elektronik-Bereich:** ein M3-Lochraster auf der Grundplatte. Zukaufregler, Empfänger und später eigene Platinen werden darauf mit Adapterplatten befestigt. Selbst gebaute Elektronik passt dann ohne Änderung am Chassis.

## Startwerte für die Fahrzeugparameter

Diese Werte werden in Fusion als Benutzerparameter angelegt und können später angepasst werden. Sie orientieren sich an üblichen 1:10-Buggys, damit Zukaufteile (Räder, Dämpfer, Antriebswellen) passen.

| Parameter | Startwert |
|---|---|
| `radstand` | 283,5 mm (wie Spender TLR 22X-4, Entscheidung 2026-10-27) |
| `spurbreite` | 250 mm (über die Räder) |
| `rad_durchmesser` | ca. 85 mm (2,2"-Buggy-Felgen) |
| `radmitnehmer` | 12 mm Sechskant |
| `bodenfreiheit` | 25 mm |
| `federweg` | 35 mm |
| `plattenstaerke` | 4 mm für Alu. Der Druck wird dicker oder mit Rippen gebaut. |
| `zielgewicht` | ≤ 2,0 kg fahrfertig |

## Phasen

### Phase 0: Grundlagen *(läuft)*
- [x] Repository, Lizenz, Struktur
- [x] Skill für die Anforderungsanalyse
- [x] Grundsatzentscheidungen
- [x] Spenderplattform für Zukaufteile wählen (`docs/zukaufteile-v1.md`)
- [x] Zukaufteile v1 festlegen (`bom/stueckliste.csv`, `docs/zukaufteile-v1.md`)
- [ ] Zukaufteile v1 bestellen (Nutzer; vorher Lieferbarkeit und Preis der Dämpfer prüfen)
- [x] Skelettmodell in Fusion: Parameter, Radpositionen, Hüllkörper der Zukaufteile (`docs/skelett.md`)

### Phase 1: Mechanik v1, 2WD-Prototyp aus dem Drucker
Reihenfolge nach Abhängigkeiten. Für jede Baugruppe wird vorher eine Anforderungsanalyse gemacht.
1. **Grundplatte und Oberdeck**: Lochbilder für alle Baugruppen, Lochraster für die Elektronik, Akkuschacht
2. **Hinterachse**: Getriebe- und Differentialgehäuse, Querlenker, Radträger, Dämpferbrücke
3. **Mittelantrieb**: Motorhalter mit Zahnspiel-Einstellung, Hauptzahnrad-Lagerung, Kardanwelle nach hinten, Zahnradabdeckung
4. **Vorderachse und Lenkung**: Querlenker, Achsschenkel, Lenkhebelsystem mit Ackermann, Servohalter, Servo-Saver
5. **Elektronikhalter**: Fahrtenregler, Empfänger, Akkuhalterung, Kabelführung
6. **Karosseriehalter und Rammschutz**
7. Drucken, Montage, erste Testfahrt, Schwachstellen dokumentieren
8. **Bauanleitung v1** in `docs/`

### Phase 2: Allrad (4WD)
- Vorderachsdifferential und Gehäuse, vordere Kardanwelle, Abtrieb vorne am Mittelantrieb
- Optional eine Rutschkupplung im Mittelantrieb

### Phase 3: Gefräste Aluteile
- Teile, die bei den Tests in Phase 1/2 brechen oder sich verbiegen, kommen zuerst dran
- Erwartet: Grundplatte, Dämpferbrücken, Lenkhebel, Motorhalter
- CAM in Fusion, Fräsparameter und Spannmittel unter `cad/`
- Vorher zu klären: Verfahrweg und Steifigkeit der Portalfräse

### Phase 4: Eigene Elektronik
Steigender Schwierigkeitsgrad. Jede Stufe ersetzt genau ein Zukaufteil.
1. **Stromverteilung/BEC-Platine**: XT60, Verpolschutz, 6-V-Servoversorgung, Spannungsmessung. Ein einfacher Einstieg ins Platinendesign.
2. **Fahrtenregler (ESC), brushless sensorless, 2S**
   - Auf Basis offener Firmware, z. B. AM32 oder VESC. Ob sie für den Fahrzeugbetrieb mit Vorwärts, Bremse und Rückwärts geeignet ist, wird in der Anforderungsanalyse geprüft.
3. **Fernsteuerung (Sender)**
   - Eigener Pistolengriff-Sender mit zugelassenem ELRS-Funkmodul und eigenem Mikrocontroller, Gehäuse und Bedienelementen
   - Der ELRS-Empfänger bleibt ein Zukaufteil, weil Funk-Hardware aufwendig zuzulassen ist
4. Optional: Telemetrie (Akkuspannung, Temperatur), Licht

## Offene Punkte
- [x] **Spenderplattform:** TLR 22X-4, siehe „Entscheidungen“
  - Differential, Dämpfer, Antriebswellen (CVD/Knochen), Radmitnehmer, Lager und Zahnräder möglichst als Ersatzteile *eines* verbreiteten 1:10-Buggys kaufen. So passen die Teile zueinander und sind einzeln nachkaufbar.
  - Verglichen wurden RC10B74.2, XRAY XB4 und TLR 22X-4 (`docs/zukaufteile-v1.md`).
- [x] **Zahnradmodul** für Motorritzel und Hauptzahnrad: 48 Pitch
- [x] **ELRS-Empfänger mit PWM-Ausgängen:** HelloRadio HR7E
- [ ] **Sender v1:** z. B. ein Pistolengriff-Sender mit eingebautem ELRS. Der Sender muss mit der Regulatory Domain **EU_CE_2400** (LBT) laufen, wie der Empfänger HR7E
- [ ] **Karosserie:** zugekaufte 1:10-Buggy-Karosserie aus Lexan, oder eigene
- [x] **Höchstgeschwindigkeit und Budget** für v1: ca. 50 km/h, 600–1050 €
- [ ] **Dämpfer v1:** TLR-Dämpfersatz TLR233064 derzeit nicht lieferbar, Preis offen. Lieferbarkeit und Preis bei der Bestellung prüfen. Alle Posten mit Preis: 812,56 €; mit Dämpfern (Vergleichspreis Associated 91994/91995, 2 × 75,90–76,90 €) 964,36–966,36 €; mit den Richtpreisen der Teile „manuell suchen“ (Spurstangen, TLR232110, TLR236006) 1042,34–1044,34 €, knapp im Budget von 1050 €. Kostet ein Dämpfersatz mehr als 79,73 €, wird 1050 € überschritten (`docs/zukaufteile-v1.md`, Abschnitt „Budget“)
- [ ] **Portalfräse:** Verfahrweg und welche Aluminiumlegierung (z. B. 6061/7075)

## Arbeitsweise
- Vor jeder Baugruppe läuft der Skill `anforderungsanalyse`. Das Ergebnis liegt unter `docs/anforderungen/`.
- CAD entsteht in Fusion über den MCP-Server, parametrisch mit den Benutzerparametern oben.
- Jedes Teil kommt in `bom/stueckliste.csv`.

# Grobplan open-rc-car

**Stand:** 2026-10-26

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
| `radstand` | 280 mm |
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
- [ ] Spenderplattform für Zukaufteile wählen (siehe „Offene Punkte“)
- [ ] Zukaufteile v1 festlegen und bestellen (`bom/stueckliste.csv`)
- [ ] Skelettmodell in Fusion: Parameter, Radpositionen, Hüllkörper der Zukaufteile

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
- [ ] **Spenderplattform:**
  - Differential, Dämpfer, Antriebswellen (CVD/Knochen), Radmitnehmer, Lager und Zahnräder möglichst als Ersatzteile *eines* verbreiteten 1:10-Buggys kaufen. So passen die Teile zueinander und sind einzeln nachkaufbar.
  - Kandidaten noch recherchieren und vergleichen.
- [ ] **Zahnradmodul** für Motorritzel und Hauptzahnrad. Hängt von der Spenderplattform ab.
- [ ] **ELRS-Empfänger mit PWM-Ausgängen:** Regler und Servo brauchen PWM, viele ELRS-Empfänger geben nur CRSF aus.
- [ ] **Sender v1:** z. B. ein Pistolengriff-Sender mit eingebautem ELRS
- [ ] **Karosserie:** zugekaufte 1:10-Buggy-Karosserie aus Lexan, oder eigene
- [ ] **Höchstgeschwindigkeit und Budget** für v1
- [ ] **Portalfräse:** Verfahrweg und welche Aluminiumlegierung (z. B. 6061/7075)

## Arbeitsweise
- Vor jeder Baugruppe läuft der Skill `anforderungsanalyse`. Das Ergebnis liegt unter `docs/anforderungen/`.
- CAD entsteht in Fusion über den MCP-Server, parametrisch mit den Benutzerparametern oben.
- Jedes Teil kommt in `bom/stueckliste.csv`.

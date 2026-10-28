# Zukaufteile v1: Spenderplattform, Shops und Stückliste

- **Anforderungen:** `docs/anforderungen/zukaufteile-v1.md` (Kürzel ZUK, Fassung 2)
- **Stückliste:** `bom/stueckliste.csv`
- **Stand der Recherche:** 2026-10-28. Preise und Verfügbarkeiten gelten für diesen Tag und ändern sich.
- **Fassung 2 (Plattformwechsel):** Bis 2026-10-27 war der TLR 22X-4 der Spender (Einzelteile, ca. 1040 €). Am 2026-10-28 hat der Nutzer für einen günstigen Einstieg auf den **Tamiya TT-02B als Bausatz** umgestellt. Die alte Fassung steht in der Git-Historie.

## Ergebnis in Kürze

| Thema | Ergebnis |
|---|---|
| Spenderplattform | **Tamiya TT-02B**, gekauft als Bausatz **Neo Scorcher (58568)** bei TAMICO, 110,91 € |
| Was der Bausatz liefert | Diffs vorne/hinten (4 Kegelräder, Harz), Kardanwelle, Antriebswellen (Knochen), Radachsen mit 12-mm-Mitnehmern, Hauptzahnrad 70Z, 4 CVA-Öldämpfer, 4 Räder Ø 82 mm, Kugelköpfe, Lenkspurstange. Wanne, Querlenker, Karosserie, Motor 540 und Regler sind Reserve. |
| Was dazu kommt | Kugellagersatz (der Bausatz hat Kunststoffbuchsen), Motorritzel 25Z Modul 0,6 (manuell suchen) |
| Eigenbau neu | **Rutschkupplung** (es gibt keine für den TT-02), Getriebegehäuse (beim TT-02B Teil der Wanne) |
| Fahrzeugmaße | Radstand **266 mm**, Spur **217 mm vorne / 208 mm hinten**, Räder **Ø 82 mm** (Tamiya) |
| Zahnräder | **Modul 0,6**; Diff 2,6 : 1, Hauptzahnrad 70Z (gerechnet) |
| Motor/Regler | unverändert Hobbywing 3652SL G2 3250 kV + WP10BL60 G2; mit Ritzel 25Z rechnerisch **51,1 km/h** |
| Elektronik sonst | unverändert: HR7E, Savöx SC-1258TG+, UBEC 10A V2, Voltz 2S 5000 Hardcase XT60 |
| Shops (3) | **TAMICO** (Bausatz), **Modellbau Lindinger** (Elektronik, Lager, Normteile), **RC Team** (Akku, UBEC, XT60, Lenkungslager). Horizon Hobby EU entfällt. |
| Budget | **ca. 500 €** inkl. Versand, mit Richtpreis für das Ritzel **ca. 512 €**, weit unter 1050 € (siehe [Budget](#budget-doc-zuk-004)) |

## Bausatzvergleich (MECH-ZUK-002)

Alle TT-02B-Bausätze haben dasselbe Chassis. Sie unterscheiden sich bei Karosserie, Rädern, Elektronik und Preis. Gesucht wurde der günstigste lieferbare Bausatz mit Öldämpfern und Rädern (MECH-ZUK-006/007).

| Bausatz | Shop | Preis | Lieferbar (28.10.2026) | Lieferumfang laut Shop/Tamiya |
|---|---|---|---|---|
| **Neo Scorcher 58568** | [TAMICO](https://tamico.de/Tamiya-Neo-Scorcher-TT-02B-Kit-58568) | **110,91 €** (inkl. 20 % MwSt. angezeigt) | auf Lager, 1–3 Werktage | 4 Öldruckdämpfer, Spike-Reifen, Motor Torque-Tuned 540, Regler, Karosserie; Kugellager nur als Zubehör angeboten |
| Neo Scorcher 58568 | [RC Team](https://www.rcteam.com/en/products/tamiya-tt-02b-buggy-neo-scorcher-kit-58568) | 134,90 € | auf Lager | Diffs, Dämpfer, Regler |
| Plasma Edge II 58630 | [Härtle](https://www.haertle.de/RC+Modellbau/RC+Autos/TAMIYA+58630+Plasma+Edge+II+TT+02B+RC+Auto+Bausatz+1+10.html) | 119,98 € | sofort lieferbar | CVA-Öldämpfer, Räder [P1] |
| Plasma Edge II 58630 | [RC Team](https://www.rcteam.com/en/products/tamiya-tt-02b-buggy-plasma-edge-ii-kit-58630) | 134,90 € | auf Lager | weiße CVA-Dämpfer, Sternfelgen |
| Plasma Edge II Gun Metal 47446 | [Lindinger](https://www.lindinger.at/en/CARS-BOATS/MODELS/Offroad-4x4-Cars/TAMIYA-PLASMA-EDGE-II-GUN-METAL-TT-02B-4WD-1-10-VORLACKIERT/9775674) | 139,99 € | nicht mehr verfügbar | lackierte Karosserie, Motor, Regler |
| TT-02B Chassis Kit (ohne Karosserie, Reifen, Felgen, Elektronik) | [TAMICO](https://tamico.de/Tamiya-TT-02B-Chassis-Kit) | 60,49 € | nur 2 Stück | ohne Räder; Lager nicht angegeben |

**Wahl: Neo Scorcher 58568 bei TAMICO.** Begründung:
1. Günstigster vollständiger TT-02B-Bausatz mit Öldämpfern **und** Rädern, lieferbar.
2. Das Chassis-Kit (60,49 €) wäre ohne Räder billiger, verstößt aber gegen die Nutzerentscheidung „Räder aus dem Bausatz“ (MECH-ZUK-007). Mit zugekauften Rädern (z. B. Carson All Terrain 25,49 €) läge es bei ca. 86 €, also ca. 25 € günstiger. Diese Möglichkeit wird nur notiert.
3. Mit TAMICO bleibt es bei 3 Shops, weil Horizon Hobby EU (nur TLR-Teile) wegfällt.

**Kunststoffbuchsen:** Tamiya nennt für den Neo Scorcher „Bearings: Plastic bushing“ [P3]. Deshalb kommt ein Kugellagersatz dazu (MECH-ZUK-008).

## Werte der Plattform mit Quelle (MECH-ZUK-003)

| Wert | TT-02B | Quelle | Startwert im Plan vorher |
|---|---|---|---|
| Radstand | **266 mm** | Tamiya 58568 und 58630, Specifications [P1][P2] | 283,5 mm |
| Spur | **217 mm vorne, 208 mm hinten** | [P1][P2] | 250 mm |
| Räder | vorne 32 × 82 mm, hinten 41 × 82 mm (Breite × Ø), Spike-Reifen | [P1][P2] | Ø 85 mm |
| Radmitnehmer | 12 mm Sechskant | in den Specifications nicht genannt → **am Teil prüfen** | 12 mm |
| Federweg | aus den CVA-Öldämpfern, Wert nicht veröffentlicht → **am Teil messen** | [P2]: „CVA oil dampers front and rear“ | ≥ 30 mm |
| Länge × Breite | 380 × 250 mm (Neo Scorcher) | [P2] | – |

Die Startwerte in `docs/plan.md` sind auf diese Werte gesetzt (Nutzerentscheidung 2026-10-28). **Folge:** Skelettmodell und Grundplatte/Oberdeck (PR #6) passen nicht mehr und werden in einem eigenen Schritt angepasst.

## Rechnungen

### Übersetzung und Höchstgeschwindigkeit (ELEK-ZUK-001)

**Diff-Übersetzung und Hauptzahnrad.** Tamiya nennt für den TT-02B 10,71 : 1 mit dem Bausatzritzel [P1][P2] und für den TT-02 8,27 : 1 ab Werk sowie einen Bereich von 11,38 bis 7,28 : 1 mit Zubehörritzeln [P4]. Alle Werte passen genau zu **Hauptzahnrad 70Z und Diff 2,6 : 1**:
- 70/17 × 2,6 = 10,71 (TT-02B, Bausatzritzel 17Z)
- 70/22 × 2,6 = 8,27 (TT-02 ab Werk)
- 70/16 × 2,6 = 11,38 und 70/25 × 2,6 = 7,28 (Bereich laut Tamiya)

Die Zähnezahlen 70Z und 17Z sind damit gerechnet und nicht direkt belegt → beim Auspacken prüfen.

**Geschwindigkeit:** v = kV × U ÷ i × π × D, mit 3250 kV, D = 82 mm (Umfang 0,2576 m).

| Motorritzel (Modul 0,6) | Gesamtübersetzung | v bei 7,4 V | v bei 8,4 V | Bezug |
|---|---|---|---|---|
| 17Z | 10,71 | 34,7 km/h | 39,4 km/h | im Bausatz |
| 22Z | 8,27 | 44,9 km/h | 51,0 km/h | – |
| 24Z | 7,58 | 49,0 km/h | 55,6 km/h | Set Tamiya 50477 |
| **25Z** | **7,28** | **51,1 km/h** | 58,0 km/h | **Set Tamiya 50477** |

Mit **25Z** liegt die Leerlaufgeschwindigkeit bei 51,1 km/h und damit im Ziel 45–55 km/h. Real fährt das Auto langsamer (Last, Reifen); am Prototyp messen. Das Set 50477 (24Z + 25Z, Bohrung 3,17 mm) ist in keinem der drei Shops nachweisbar → [Manuell suchen](#manuell-suchen-doc-zuk-002). Das Motorritzel sitzt auf unserem eigenen Motorhalter, deshalb gilt die Grenze des Tamiya-Motorhalters nicht.

**Belastung:** Der TT-02-Antrieb (Diffs und Kardanwelle aus Kunststoff) ist für Bürstenmotoren ausgelegt. Mit Brushless und 50 km/h schützt die **eigene Rutschkupplung** Diffs und Kardanwelle vor Lastspitzen (Nutzerentscheidung 2026-10-28). Brechen trotzdem Teile, gibt es Metall-Tuningteile (z. B. Alu-Kardanwelle Tamiya 54501, Metall-Diff 54875).

### Federweg (MECH-ZUK-006)

Die CVA-Öldämpfer des Bausatzes werden verwendet. Hub und Einbaulänge veröffentlicht Tamiya nicht → **am Teil messen**. Der Federweg am Rad ist dann s = Hub × i (Hebelverhältnis der eigenen Querlenker). Der Wert ersetzt die frühere Forderung ≥ 30 mm (Abschlag vom Nutzer akzeptiert, `fahrzeug.md` MECH-FZG-005). Die Federn werden am Prototyp auf ca. 2,0 kg abgestimmt (🔧).

### Elektronik: BEC, Unterspannung und Failsafe

- **Regler Hobbywing QuicRun WP10BL60 G2** [E1][E3]: sensorless, 60 A / 360 A, 2–3S. Fahrmodi Vorwärts/Bremse, **Vorwärts/Rückwärts/Bremse**, Vorwärts/Rückwärts. Unterspannungsabschaltung wählbar: aus, 2,6 / 2,8 / 3,0 / **3,2 / 3,4 V pro Zelle** → Einstellung **3,4 V/Zelle** (mindestens 3,2 V, ELEK-FZG-003). Zellenzahl manuell auf 2S stellen (Hobbywing rät von der Automatik ab). BEC **6 V / 3 A** Schaltregler. Schutz bei Verlust des Gassignals („Throttle signal loss protection“). Der Eingang hat **keinen Stecker**: XT60-Stecker anlöten (Stückliste).
- **Empfänger HelloRadio HR7E** [E4]: ExpressLRS 3.3.0, 8 PWM-Ausgänge, 4,5–8,4 V. Für den Betrieb in der EU wird die Firmware mit der Regulatory Domain **EU_CE_2400 (LBT)** geflasht [E5]. Beim Kauf ist die Domain nicht angegeben. **Der Sender muss ebenfalls mit EU_CE_2400 laufen**, sonst verbinden sich Sender und Empfänger nicht (gilt für die spätere Senderwahl).
- **Failsafe-Kette (ELEK-FZG-002):** Bei ELRS-PWM-Empfängern hat jeder Ausgang einen einstellbaren Failsafe-Wert (988–2012 µs, WebUI). Failsafe greift, wenn die Verbindungsqualität auf 0 fällt oder 1 s lang kein gültiges Kanalpaket kommt. Beim Einschalten gibt der Empfänger keine Impulse aus, bis der Sender verbunden ist [E6]. **Einstellung: Kanal 2 (Gas) Failsafe = 1500 µs (Neutral), Kanal 1 (Lenkung) Failsafe = 1500 µs (geradeaus).** Der Regler sieht dann Neutral und der Motor steht. Fallen die Impulse ganz weg, greift zusätzlich der Signalverlust-Schutz des Reglers [E1]. Hobbywing empfiehlt selbst, den Failsafe des Gaskanals auf Neutral zu setzen [E1]. Test mit hängendem Rad am Prototyp (🔧): Sender aus → Motor steht **und** Lenkung geht in Mittelstellung.
- **Servo Savöx SC-1258TG+** [E7]: 12 kg·cm und 0,08 s/60° bei 6 V, 4,8–6,0 V (nicht HV). **Blockierstrom 4000 mA bei 4,8 V und 5000 mA bei 6,0 V** [E7] (steht nur auf der englischen Lindinger-Seite).
- **Problem Servostrom:** Der Regler-BEC liefert 6 V / 3 A und versorgt zusätzlich den Reglerlüfter [E1]. Blockiert das Servo (Räder am Anschlag oder an einem Hindernis), braucht es bis zu 5 A. Dann bricht die BEC-Spannung ein; fällt sie unter 4,5 V, startet der Empfänger neu und die Lenkung ist kurz ohne Signal.
- **Lösung (Nutzerentscheidung 2026-10-27): externer BEC Hobbywing UBEC 10A V2** [E8][E9], 10 A Dauer / 15 A Spitze, Eingang 6–25,2 V (2S: 6,8 V bei der Abschaltschwelle 3,4 V/Zelle, also im Bereich), Ausgang auf **6,0 V** stellen (Servo max. 6,0 V). Er versorgt Empfänger und Servo; Reserve gegenüber 5 A Blockierstrom plus ca. 0,1 A Empfänger ist doppelt. Der Eingang wird an die Akkuleitung des Reglers (XT60-Seite) angelötet, die **rote Ader des Regler-Steuerkabels wird am Empfänger abgezogen**, damit nicht zwei BECs parallel speisen. Der Regler-BEC versorgt dann nur noch seinen Lüfter.
  - Verworfen: **Pufferkondensator** (z. B. 4700 µF, RC Team 4,90 €): überbrückt nur Millisekunden (2 A Defizit × 2,35 ms ≈ 1 V Einbruch bei 4700 µF), nicht ein Blockieren über Sekunden. **Anderes Servo:** nicht weiter verfolgt. Ein Servo mit ≥ 10 kg·cm braucht beim Blockieren ebenfalls mehrere Ampere, und Blockierströme werden oft nicht angegeben; ein belegter Wert ≤ 3 A wäre nötig. Der UBEC löst das Problem unabhängig vom Servo.
  - **Schalter:** Ob der UBEC einen Ein/Aus-Schalter hat, ist laut Quellen widersprüchlich (RC Team nennt keinen [E8], htmodel.sk nennt ihn „switched BEC“ [E9]) → **am Teil prüfen**.
  - **Wichtig (Hinweis für die Bauanleitung):** Der Schalter des Reglers schaltet Empfänger und Servo **nicht** mehr ab, weil der UBEC direkt am Akku hängt. Bei angestecktem Akku ziehen Empfänger und UBEC weiter Strom und können den LiPo bis zur Tiefentladung entladen. Auch nach der Unterspannungsabschaltung des Reglers (3,4 V/Zelle) laufen Empfänger und Servo weiter. Deshalb **den Akku nach der Fahrt sofort abstecken** (LiPo-Schutz). Hat der UBEC doch einen Schalter, ihn zusätzlich nutzen; das ersetzt das Abstecken nicht.
  - **Akkuspannung überwachen (Hinweis für die Bauanleitung):** Den Spannungsmesseingang des HR7E an den Akku anschließen, damit die Akkuspannung per Telemetrie übertragen wird. Am späteren Sender einen Telemetrie-Alarm für Unterspannung einstellen. Alternativ einen LiPo-Summer am Balancerstecker verwenden (nicht in der Stückliste v1).

## Lager (MECH-ZUK-008)

Der Bausatz hat Kunststoffbuchsen [P3]. Sie werden durch einen kompletten Kugellagersatz ersetzt.

| Größe | Stück | Position | Bezug |
|---|---|---|---|
| 5x11x4 | 12 | Radachsen vorne und hinten, Antrieb (Zuordnung laut Anleitung 58568, am Teil prüfen) | Carson 500904054 (Lindinger) |
| 8x12x3,5 | 4 | Diffs (Zuordnung laut Anleitung, am Teil prüfen) | Carson 500904054 (Lindinger) |
| 5x8x2,5 | 4 | eigenes Lenkhebelsystem (Annahme: 2 Umlenkhebel) | XRAY 940508, gummigedichtet (RC Team) |

- Inhalt des Carson-Satzes laut Lindinger: 12 × 5x11 mm und 4 × 8x12 mm [L1]. Die Breiten 4 und 3,5 mm stammen von einem gleich aufgebauten TT-02B-Satz (OZRC: 12 × 5x11x4, 4 × 8x12x3,5) [L2] → am Teil messen.
- **Dichtung:** Lindinger nennt keine Dichtung → **beim Auspacken prüfen.** Sind die Lager offen, werden gummigedichtete Lager MR115-2RS (5x11x4) und MR128-2RS (8x12x3,5) nachgekauft. Ein gummigedichteter TT-02B-Satz mit 16 Lagern kostet z. B. bei Racer's Paradise 9,50 € [L3], das wäre ein vierter Shop.
- Der Tamiya-Satz 54476 passt laut Tamiya **nicht** zum TT-02B [L4].
- Die bisherigen Lager 10x15x4, 8x14x4, 5x10x4 und 5x13x4 (TLR) entfallen.

## Verbindungselemente (MECH-ZUK-009)

Das M3-Sortiment bei Lindinger bleibt unverändert (340 M3-Schrauben Edelstahl in 6–30 mm, 60 Stoppmuttern, 30 Scheiben, 60 Gewindeeinsätze). **Kugelköpfe, Kugelpfannen, Lenkspurstange und Sturzstangen kommen aus dem Bausatz.** Fehlende Teile werden als Tamiya-Ersatzteil gekauft, z. B. der Turnbuckle-Satz TT-02B 54539. Entfallen sind die TLR-Kugelköpfe und -pfannen, die 3,5-mm-Spurstangen und die M2,5-Stoppmuttern.

**Annahme:** Die genauen Schraubenlängen und Mengen stehen erst nach der Konstruktion fest.

## Vorderachse und 4WD (MECH-ZUK-005, DOC-ZUK-007)

Die Vorderachse nutzt die Radachsen mit 12-mm-Mitnehmern aus dem Bausatz. Das sind dieselben Achsen, die beim TT-02B das angetriebene Vorderrad tragen. In v1 fehlen die Antriebswellen, deshalb sichert der Achsschenkel die Achse axial.

**Für 4WD (Phase 2) aufbewahren:** Vorderachsdiff, vordere Antriebswellen und der vordere Teil des Kardanantriebs aus dem Bausatz. Neu gekauft wird für 4WD voraussichtlich nichts außer Lagern.

## Vorgaben für die Konstruktion

Fehlende Maße werden am Teil gemessen.
- **Getriebegehäuse hinten (Eigenbau):** Beim TT-02B ist das Getriebegehäuse Teil der Wanne. Unser Gehäuse nimmt Diff, Kegelritzel und Lager (5x11x4, 8x12x3,5) auf. Achsabstand Tellerrad zu Kegelritzel, Lagersitze und Wellendurchmesser am Teil messen.
- **Spur und Radstand:** Hinten legen Diff, Antriebswellen (Knochen) und Radachsen die Spur von 208 mm fest. Die Kardanwelle legt den Abstand vom Mittelantrieb zum Hinterachsgetriebe fest. Die Längen am Teil messen und ins Skelett übernehmen.
- **Mittelantrieb:** **Eigene Rutschkupplung** mit dem Hauptzahnrad 70Z des Bausatzes. Die Normteile (Druckfeder, Reibbelag, Lager) legt die Anforderungsanalyse Mittelantrieb fest. Motor Ø 36 × 52 mm, Welle 3,175 mm; Motorhalter für Ritzel bis 25Z (Achsabstand Modul 0,6: (70 + 25) × 0,6 ÷ 2 = 28,5 mm).
- **Dämpfer:** CVA-Öldämpfer des Bausatzes. Einbaulänge, Hub und Befestigung am Teil messen.
- **Räder:** 32 × 82 mm vorne, 41 × 82 mm hinten. Einpresstiefe und Nabentiefe am Teil messen. Beim vollen Lenkeinschlag den Freigang des Vorderrads prüfen.
- **Elektronik:** Maße wie bisher, siehe Stückliste. Das Servo sitzt im eigenen Servohalter.

## Manuell suchen (DOC-ZUK-002)

Diese Teile sind in keinem der drei Shops nachweisbar. Sie stehen mit Vermerk in der Stückliste. Den Kauf erledigt der Nutzer. Richtpreise zählen nicht zur Summe der Stückliste, nur zur Budget-Spanne.

| Teil | Warum gebraucht | Richtpreis | Quelle |
|---|---|---|---|
| Motorritzel-Set Tamiya 50477 (24Z + 25Z, Modul 0,6, Bohrung 3,17 mm) | 50 km/h (ELEK-ZUK-001); mit dem Bausatzritzel 17Z nur 34,7 km/h | 11,96 € (eBay.de, versandkostenfrei) | [M1] |

## Verschleißteile (DOC-ZUK-006)

Nicht bestellt. Vorrat für später, als Tamiya-Ersatzteile:

| Teil | Tamiya-Nr. | Hinweis |
|---|---|---|
| Zahnräder TT-02 (G-Teile: Kegelräder, Antriebsräder, Hauptzahnrad) | 51531 | laut Händlerangabe [V1]; vor dem Kauf prüfen, ob sie zum TT-02B passen |
| Alu-Kardanwelle TT-02 | 54501 | stärker als die Kunststoffwelle [V2] |
| Motorritzel 24Z/25Z Modul 0,6 | 50477 | [M1] |
| Antriebswellen, Radachsen, Spurstangen | laut Anleitung 58568 | Teilenummern beim Bau eintragen |

Die vollständige Liste der Tamiya-Teilenummern für Mehrfachbauten ist ein offener Punkt im Plan (Nutzerwunsch 2026-10-28).

## Budget (DOC-ZUK-004)

Summen per Skript aus `bom/stueckliste.csv` (Menge × Preis je Zeile).

| Shop | Teile | Versand nach DE | Summe |
|---|---|---|---|
| TAMICO | 110,91 € | nicht belegt; frei erst ab 150 € [S4] → **Annahme 10,00 €** | 120,91 € |
| Modellbau Lindinger | 279,17 € | 0,00 € (frei nach DE ab 99 €) [S2] | 279,17 € |
| RC Team | 85,30 € | 7,99–14,99 € nach Gewicht, gerechnet mit 14,99 € [S3] | 100,29 € |
| **A: Summe aller Posten mit Preis** | **475,38 €** | **24,99 €** | **500,37 €** |
| Manuell suchen: Ritzel-Set 50477 | 11,96 € | versandkostenfrei (eBay) | 11,96 € |
| **B: vollständige Summe** | | | **512,33 €** |

- Obergrenze 1050 € (Anforderung DOC-ZUK-004) → **eingehalten**, Reserve ca. 538 €.
- Gegenüber Fassung 1 (TLR 22X-4, ca. 1042 €) spart der Wechsel ca. 530 €.
- Offen und deshalb in der Spanne: Versand TAMICO, ggf. gummigedichtete Ersatzlager (bis ca. 10 €, falls der Carson-Satz offen ist).
- Sender, Ladegerät, Werkzeug, Karosserie und Filament sind nicht enthalten.

## Quellen

- [P1] Tamiya, Plasma Edge II (TT-02B) 58630, Specifications (Radstand 266 mm, Spur 217/208 mm, Reifen 32/82 und 41/82 mm, 10,71 : 1, CVA-Öldämpfer, 4-Kegelrad-Diffs): https://tamiya.com/english/products/58630/index.html
- [P2] Tamiya, Neo Scorcher (TT-02B) 58568, Specifications (Länge 380 mm, Radstand 266 mm, Spur 217/208 mm, Reifen 32/82 und 41/82 mm, 10,71 : 1, CVA-Öldämpfer vorne und hinten, Regler separat): https://tamiya.com/english/products/58568/index.html
- [P3] Tamiya America, Neo Scorcher 58568-A („Bearings: Plastic bushing“): https://tamiyausa.com/shop/-road-buggies/rc-neo-scorcher-3
- [P4] Tamiya America, Raikiri GT (TT-02): 8,27 : 1 ab Werk, 11,38–7,28 : 1 mit Zubehörritzeln: https://www.tamiyausa.com/shop/110-4wd-shaft-drive-road-tt/rc-raikiri-gt
- [L1] Lindinger, Carson Kugellagersatz TT-01/TT-01E/TT-02B (16), 500904054: https://www.lindinger.at/de/Fahrzeuge-Boote/Auto-Ersatzteile-und-Tuning/CARSON-KUGELLAGERSATZ-TAMIYA-TT-01-TT-01E-TT-02B/9741877
- [L2] OZRC, Tamiya TT02B Bearing Kit (12 × 5x11x4, 4 × 8x12x3,5, gummigedichtet): https://ozrc.com.au/products/tamiya-tt02b-off-road-buggy-complete-bearing-kit
- [L3] Racer's Paradise, Kugellagersatz TT-02B, 16 Lager gummigedichtet: https://racersparadise.de/KUGELLAGERSATZ-DELUXE-FUeR-TAMIYA-TT-02B-MODELLE-16-GUMMIGEDICHTETE-LAGER
- [L4] Tamiya America, TT-02 Ball Bearing Set 54476 („not for use on the TT-02B Buggy Chassis“): https://tamiyausa.com/shop/ball-bearings/rc-tt02-ball-bearing-set
- [M1] eBay.de, Tamiya 50477 Motorritzel 24/25 Zähne Modul 0,6, Bohrung 3,17 mm: https://www.ebay.de/itm/396705117034
- [V1] Hobbyetc, Tamiya 51531 TT-02 G Parts (Gear): https://store.hobbyetc.com/parts/view/83836
- [V2] Lindinger und Alltron, Tamiya TT-02 Alu-Kardanwelle 54501 bzw. Metall-Öldiff 54875 (Händlerangaben)
- [E1] Hobbywing, Parameterliste und Anleitung QuicRun WP10BL60 (G2): https://support.hobbywingdirect.com/hc/article_attachments/20206396553107 und https://hobbywing.com/en/uploads/file/20221015/eba2fcdde83f06810fea0bc12d448f1a.pdf
- [E2] Lindinger, Hobbywing QuicRun 3652SL G2 3250 kV (Maße, Gewicht): https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Antriebe/Elektromotoren/HOBBYWING-QuicRun-3652SL-G2-Sensorless-Motor-3250kV-3.175mm-Welle/9796158
- [E3] Hobbywing, Produktseite QuicRun WP 10BL60: https://hobbywing.com/en/products/quicrun-wp-10bl6056
- [E4] Lindinger, HelloRadio HR7E (technische Daten): https://www.lindinger.at/de/RC-Elektronik/RC-Produkte/Empfaenger/HelloRadio-HR7E-ELRS-2-4GHz-Empfaenger-8-Kanaele-rot/9811430
- [E5] ExpressLRS, Firmware-Optionen (Regulatory Domain EU_CE_2400, LBT): https://www.expresslrs.org/quick-start/firmware-options/
- [E6] ExpressLRS, PWM-Empfänger (Failsafe): https://www.expresslrs.org/hardware/pwm-receivers/
- [E7] Lindinger, Savöx SC-1258TG+, englische Produktseite (technische Daten, u. a. „Running Current (no load): 100mA @4.8V, 120mA @6.0V“ und „Stall Current (at locked): 4000mA @4.8V, 5000mA @6.0V“): https://lindinger.at/en/RC-ELECTRONICS/Servos-Accessories/Servos-Digital-Low-Voltage/SAVOEX-SC-1258TG-6V-12KG-0.08s-DIGITAL-SERVO/9795331 (die deutsche Seite https://www.lindinger.at/de/RC-Elektronik/Servos-Zubehoer/Servos-Digital-Low-Voltage/SAVOEX-SC-1258TG-6V-12KG-0-08s-DIGITAL-SERVO/9795331 nennt den Blockierstrom nicht)
- [E8] RC Team, Hobbywing UBEC 10A V2 (2–6S) 30603003 (10 A / 15 A Spitze, Eingang 6–25,2 V, Ausgang 6,0/7,4/8,4 V, 43,1 × 32,3 × 12,5 mm, 34 g): https://www.rcteam.com/en/products/hobbywing-ubec-10a-v2-2-6s-30603003
- [E9] htmodel.sk, Hobbywing UBEC-10A V2 Car (HW30603003; „switched BEC“, 10 A / 15 A Spitze, Eingang 6–25,2 V, Ausgang 6,0/7,4/8,4 V, 45 × 20 × 16,2 mm, 34 g): https://www.htmodel.sk/en/hobbywing-ubec-10a-v2-car/
- [S2] Lindinger, Versandhinweis auf den Produktseiten („GRATIS-VERSAND: AT ab 89,- € / DE ab 99,- €“)
- [S3] RC Team, Versand: https://www.rcteam.com/en/pages/shipping-and-delivery
- [S4] TAMICO, Produktseite TT-02B Chassis Kit (Hinweis „kostenloser DHL-Versand innerhalb Deutschlands ab 150 €“; Versandkosten darunter nicht angegeben): https://tamico.de/Tamiya-TT-02B-Chassis-Kit

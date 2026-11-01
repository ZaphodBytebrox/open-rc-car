# Grobplan open-rc-car

**Stand:** 2026-11-01

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
| 2026-10-28 | Spenderplattform (ersetzt 2026-10-26) | **Tamiya TT-02B** statt TLR 22X-4, für einen günstigen Einstieg. Abschläge bei Spur, Radstand, Federweg und Zahnradmodul sind akzeptiert. Die Einträge zu Spender, Pitch, Mittelantrieb, Rädern, Bezugsquellen und Radstand vom 2026-10-26/27 gelten damit nicht mehr (`docs/anforderungen/zukaufteile-v1.md`, Fassung 2) |
| 2026-10-28 | Teilebeschaffung v1 | Ein **TT-02B-Bausatz** wird als Teilespender gekauft (Ausnahme von „nur Einzelteile“). Chassis, Getriebegehäuse, Querlenker, Radträger und Halter bleiben Eigenbau |
| 2026-10-28 | Fahrzeugmaße | Spur, Radstand, Raddurchmesser und Federweg vom TT-02B übernommen (Startwerte unten) |
| 2026-10-28 | Zahnradmodul | Tamiya Modul 0,6 statt 48 Pitch |
| 2026-10-28 | Mittelantrieb v1 (ersetzt 2026-10-26) | **Eigene Rutschkupplung** (Eigenbau), weil es für den TT-02 keine gibt; Ziel ca. 50 km/h mit Brushless bleibt |
| 2026-10-28 | Räder v1 (ersetzt 2026-10-26) | Räder aus dem TT-02B-Bausatz statt Carson All Terrain |
| 2026-10-28 | Layout wie TT-02B (ersetzt Mittelmotor-Layout) | **Nutzerentscheidung:** Layout genau wie der TT-02B (Bauanleitung 11053619): Kardanwelle E1 nur an den Getrieben gelagert, Hauptzahnrad 70Z mit eigener Rutschkupplung auf der hinteren Kegelritzelwelle am Hinterachsgetriebe, Motor hinten rechts, Akku längs links, Elektronik rechts, Servo vorne; Bauraum für Ritzel 16Z–25Z. Grund: Bausatzteile E1/E2 unverändert nutzbar, Plattenmitte frei (`docs/anforderungen/skelett.md`) |
| 2026-10-28 | Skelettmodell Fassung 2 | Skelett auf TT-02B umgestellt (Design-Version 10): alle Hüllkörper passen mit vorläufigen Maßen kollisionsfrei, Grundplatte 314 × 132 mm, für den Druck geteilt bei X = 0 mit 30 mm Überlappung (Teile je 172 mm lang). Antriebsachse bleibt hoch (56,6 mm), Wellenwinkel bei Lieferung prüfen. Offen für „Mittelantrieb“: Motorwelle reicht mit Motorhalter nicht bis zur Zahnebene (−3 mm); Rutschkupplung passt nach vorläufigen Maßen nicht in Reihe auf E2, Bauraum umschließt den Becher, auch dort fehlen 9 mm (`rk_luft`). MECH-SKE-008 deshalb nur teilweise erfüllt, vom Nutzer so abgenommen (`docs/skelett.md`) |
| 2026-10-28 | Bausatz und Bezugsquellen v1 (ersetzt 2026-10-26) | Tamiya **Neo Scorcher 58568** (TT-02B) bei TAMICO; Lindinger (Elektronik, Lagersatz, Normteile), RC Team (Akku, UBEC, XT60, Lenkungslager); Horizon EU entfällt. Motorritzel 25Z Modul 0,6 (Tamiya 50477) für rechnerisch 51,1 km/h, manuell suchen. Summe ca. 512 € inkl. Versand (`docs/zukaufteile-v1.md`) |
| 2026-10-27 | Grundplatte (gilt weiter) | Grundplatte als eigenes Fusion-Design „open-rc-car-grundplatte“, abgeleitet (Derive) vom Skelett; 4 mm im Druck wie in Alu, ohne Rippen; Druck zweiteilig mit Halbüberlappung, Aluvariante einteilig mit identischen Lochbildern; alle Befestigungen von unten mit M3-Senkkopf, Gewinde im aufgesetzten Teil; die Grundplatte legt die Lochbilder aller Baugruppen fest; Akku mit verschraubten Anschlägen (1 mm Spiel) und Bügel mit Schnellverschluss, vorderer Pfosten ersetzt den vorderen Anschlag (2026-10-28); Elektronik-Raster M3 10 × 10 mm; Material PETG zum Testen, Prusament PC fertig |
| 2026-10-31 | Grundplatte und Oberdeck Fassung 2 | **Nutzerentscheidungen:** Neuaufbau auf dem TT-02B-Skelett (v10) in PR #6. Plattenenden vorne und hinten 15 mm über die Getriebe hinaus verlängert (Rammschutz, Karosseriehalter). **Querlenkerböcke als eigene Teile auf der Platte**, je Achse vor und hinter der Achse neben dem Getriebe. **Oberdeck auf beiden Getrieben plus Mittelstütze** rechts neben der Kardanwelle am Stoß (ersetzt das entfallene Mittelschott, klemmt den Stoß). Eigenes Lochbild für das Lenkhebelsystem. Ergebnis: Grundplatte 344 × 144 mm, Druckteile je 186,8 × 144 mm (Stoß X −15…15), Oberdeck-Unterkante Z 84,2 mm, 107 Bohrungen, Druckteile 247,0 g; Review 1: Parametertest mit dem Skelett bestanden, Lenkhebelbock rechts mit eigener Lage. **Fügespiel am Stoß** 0,2 mm (`stoss_spiel`) an den Stufenflächen der Druckteile, dort Randabstand ≥ 4,8 mm statt 5 mm (Nutzerentscheidung nach Review 1) (`docs/grundplatte-oberdeck.md`) |
| 2026-10-31 | Hinterachse | **Nutzerentscheidungen (Anforderung HAC):** konstruiert mit vorläufigen Maßen aus der Bauanleitung, alle kritischen Bausatzmaße als Parameter, Messen nach Lieferung. Gehäuse lagert Diff und Kegelritzelwelle E2 vollständig (beide Lager); Rutschkupplung, Motorhalter und Zahnradabdeckung bleiben in „Mittelantrieb“. Aufhängung wie TT-02B: gedruckter unterer Querlenker auf vier Böcken, einstellbare Sturzstange oben, Vorspur fest im Radträger. Material PETG zum Testen, Prusament PC fertig. Nach Review 1 (Nutzerentscheidungen 2026-11-01): E2-Lagerung wie Bauanleitung (hinteres Lager im Gehäuse, vorderes in einem abnehmbaren Lagerbock kurz vor dem Becher, Hauptzahnrad/Rutschkupplung später zwischen den Lagern), Grundplatten-Schnittstellenmaße als Kopie (`ha_ql_*`, `ha_gp_*`, `ha_od_*`; ändert sich die Grundplatte, Hinterachse von Hand nachziehen), Sturzstangen als Zukauf, Überschneidung Lagerhals/Lagerbock mit Rutschkupplung und Zahnradabdeckung gewollt. Ergebnis (PR „Hinterachse“): Gehäuse zweiteilig (Teilung Y = 0) mit Lagerhals bis X −108 und Lagerbock X −109,5…−99,5; zwischen den E2-Lagern sind nach Review 2 5,0 mm frei (`ha_hz_raum`, Fehlbetrag 3,0 mm für GB3 + GB5, `ha_rk_luft` = −25,0 mm, offen bis zur Messung, siehe Eintrag unten), Dämpferbrücke als 2,5D-Platte hinter dem Gehäuse mit den Dämpfern dahinter (wie Halter A4 des TT-02B), Hebelverhältnis 1,76 (TT-02B ca. 1,5), Gelenkabstand N3 ändert sich über den Federweg höchstens um 0,33 mm, Vorspur konstant 2°, Druckteile 141,4 g. Der Bausatz hat keine Sturzstangen: Spannschlösser Tamiya 54539 und Kugelköpfe als Zukauf. Parametertest mit dem Skelett bestanden (Nutzerentscheidung 2026-11-01: Skelett als v13 mit 280 mm und v14 mit 266 mm gespeichert, maßgleich mit v12); Design-Version 11 (`docs/hinterachse.md`) |
| 2026-11-01 | Hinterachse: Zahnradraum zwischen den E2-Lagern (nach Review 2) | **Nutzerentscheidung:** Die Verluste aus dem Druckteil werden behoben: Lagerlippen von der Zahnradseite weg (außen nicht möglich, weil dort Kegelritzel und Becher liegen, deshalb weggelassen), Lager axial über die Teile auf der Welle gesichert (Becherschulter, GB3/Mitnehmer, Kegelritzel; hinteres Lager als Festlager im geteilten Sitz geklemmt, `ha_e2h_spiel`), vorderes Lager direkt am Becher, Schutz gegen negativen `ha_hz_raum` (Zeitleistenfehler am Hüllkörper `drehraum`). Ergebnis `ha_hz_raum` 0,5 → 5,0 mm. Der verbleibende Fehlbetrag (Bedarf GB3 + GB5 ≥ 8 mm, also 3,0 mm) bleibt **offen bis zur Messung** von E1 (Länge, Einstecktiefe), E2, GB3 und GB5; die vorläufigen Maße widersprechen sich (Kegelritzel läge mit E2 = 41 mm im Tellerrad-Zahnkranz). MECH-HAC-002 und -005 sind „⚠️ teilweise erfüllt, Zahnradraum offen bis Messung“ (vom Nutzer so abgenommen). **Getriebegehäuse und Lagerbock werden erst nach dem Messen gedruckt**; eine Korrektur von `getriebe_eingang` im Skelett ggf. in einem eigenen PR. Die übrigen Teile der Hinterachse (Aufhängung) können gemergt und gedruckt werden. **Folge für „Mittelantrieb“:** Die Zahnebene liegt mit dem Zahnrad zwischen den Lagern bei ca. X −105,5 statt −89 (Skelett `hz_ebene` 20), also 16,5 mm weiter hinten. Der Motor muss ca. 16,5 mm nach hinten (Flansch ca. X −91,5 statt −75), sonst fehlen an der Motorwelle ca. 19,5 mm statt 3 mm (`motor_welle_reserve`). Platz ist da (Motor 8,1 mm zum Lagerbock), aber die Motorritzel-Hülle reicht dann bis an die Gehäusetrommel (Überschneidung 26,6 mm³ mit Zuschlag) und auf 1,7 mm an den Querlenkerbock (`docs/hinterachse.md`) |
| 2026-11-01 | Hinterachse: axiale Festlegung von E2 (nach Review 3) | **Nutzerentscheidung:** Axiale Festlegung der Kegelritzelwelle E2: Vorläufig bleibt der Klemmsitz des hinteren Außenrings zwischen den Gehäusehälften (`ha_e2h_spiel`), mit messbarem Abnahmekriterium im Probelauf: E2 axial mit ca. 40 N (≈ 3 × Stoßwert 13 N) in beide Richtungen belasten, auch nach 24 h bei ca. 60 °C; Verschiebung ≤ 0,05 mm. Bei der Überarbeitung des Zahnradraums nach dem Messen wird **verbindlich ein formschlüssiges Festlager** vorgesehen: einseitiger Anschlag vor dem hinteren Außenring (ca. 1,2 mm, eigener Parameter) oder Lippe an der Vorderseite des Lagerbocks (wenn die Becherschulter durch ca. Ø 8 reicht); Bundlager F685 nur, wenn beides nicht passt (dann Änderung von MECH-HAC-017 durch den Nutzer). (`docs/anforderungen/hinterachse.md`, `docs/hinterachse.md`) |
| 2026-11-01 | Mittelantrieb v1 (ersetzt 2026-10-28) | **Nutzerentscheidungen (Anforderung MAN):** **keine Rutschkupplung in v1**; Antrieb wie TT-02B mit Mitnehmer GB3 und Hauptzahnrad GB5 zwischen den E2-Lagern, Schonung über die Reglereinstellung. Die eigene Rutschkupplung braucht ca. 30 mm auf E2 und kommt später als eigene Anforderung. **Kardanwelle E1 in v1 nicht eingebaut** (2WD), E1-Öffnung mit Blinddeckel. Motorhalter in Prusament PC (PETG nur Passprobe), fräsgerecht. Änderungen an der Hinterachse nur an der Schnittstelle. Konstruktion mit vorläufigen Maßen, Druck und Tischtest nach dem Messen (`docs/anforderungen/mittelantrieb.md`) |
| 2026-11-01 | Mittelantrieb: Motordose als Wand, Ritzel 20Z–25Z | **Nutzerentscheidung** nach Umsetzung Durchlauf 1: Mit voller Zahnbreite am GB5 liegt der Motor neben dem drehenden Becher von E2; zwischen Motor und Becher gibt es keine eigene Abdeckungswand, die Motordose ist dort die Wand (wie TT-02B). Ritzelbereich 20Z–25Z, das Bausatzritzel 17Z entfällt. Ergebnis (PR „Mittelantrieb“): Motorhalter = Vorderwand der Zahnradabdeckung, Motorplatte mit Becherhaube gleitet radial zu E2 (Achsabstand 26,5…29,0 mm, 3 Klemmschrauben von vorne), Motorachse 15° nach oben geschwenkt (Flansch X −93, Zahnebene X −105,5), Zahnradabdeckung dreiteilig; Ritzelwechsel durch Herausziehen des Motors nach vorne. Druckteile 42,3 g (PC). Hinterachse v12/v13: Freischnitt Ritzel an der Gehäusetrommel, Schnittstellenparameter als Favoriten (`docs/mittelantrieb.md`) |

## Vorgeschlagene Architektur (noch zu bestätigen)

*Überholt durch die Entscheidung „Layout wie TT-02B“ vom 2026-10-28 (Motor und Hauptzahnrad am Hinterachsgetriebe). Der ursprüngliche Vorschlag:* **Mittelmotor-Layout:** Motor und Hauptzahnrad sitzen in der Fahrzeugmitte. Eine Kardanwelle führt zum Hinterachsdifferential.
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
| `radstand` | 266 mm (Tamiya TT-02B 58568, Specifications) |
| `spurbreite` | 208 mm hinten (Radmitte zu Radmitte, Tamiya TT-02B 58568) |
| `spurbreite_v` | 217 mm vorne (Radmitte zu Radmitte, Tamiya TT-02B 58568) |
| `rad_durchmesser` | 82 mm (Räder aus dem TT-02B-Bausatz; Breite 32 mm vorne, 41 mm hinten) |
| `radmitnehmer` | 12 mm Sechskant |
| `bodenfreiheit` | 25 mm |
| `federweg` | 35 mm vorläufig (Anleitung nennt keinen Wert; am Prototyp messen) |
| `plattenstaerke` | 4 mm für Alu und Druck (Entscheidung 2026-10-27, keine Rippen) |
| `zielgewicht` | ≤ 2,0 kg fahrfertig |

## Phasen

### Phase 0: Grundlagen *(läuft)*
- [x] Repository, Lizenz, Struktur
- [x] Skill für die Anforderungsanalyse
- [x] Grundsatzentscheidungen
- [x] Spenderplattform für Zukaufteile wählen (`docs/zukaufteile-v1.md`)
- [x] Zukaufteile v1 festlegen (`bom/stueckliste.csv`, `docs/zukaufteile-v1.md`)
- [x] Zukaufteile v1 auf Tamiya TT-02B umgestellt (2026-10-28, `docs/zukaufteile-v1.md`)
- [ ] Zukaufteile v1 bestellen (Nutzer; Ritzel-Set 50477 manuell suchen, Dichtung des Lagersatzes beim Auspacken prüfen)
- [x] Skelettmodell in Fusion: Parameter, Radpositionen, Hüllkörper der Zukaufteile (`docs/skelett.md`)
- [x] Skelettmodell auf die TT-02B-Maße umgestellt (2026-10-28, Fassung 2)

### Phase 1: Mechanik v1, 2WD-Prototyp aus dem Drucker
Reihenfolge nach Abhängigkeiten. Für jede Baugruppe wird vorher eine Anforderungsanalyse gemacht.
1. **Grundplatte und Oberdeck** *(umgesetzt, Fassung 2, `docs/grundplatte-oberdeck.md`; Probemontage offen; Bohr-NC, Senken und CAM-Simulation der Aluvariante in Phase 3)*: Lochbilder für alle Baugruppen, Lochraster für die Elektronik, Akkuschacht
2. **Hinterachse** *(umgesetzt, `docs/hinterachse.md`; Probemontage offen; MECH-HAC-002/-005 teilweise: Zahnradraum zwischen den E2-Lagern offen bis zur Messung, Getriebegehäuse und Lagerbock erst danach drucken)*: Getriebe- und Differentialgehäuse, Querlenker, Radträger, Dämpferbrücke
3. **Mittelantrieb** *(umgesetzt, `docs/mittelantrieb.md`; Konstruktion mit vorläufigen Maßen, Druck und Tischtest nach Lieferung und Messung)*: Motorhalter mit Zahnspiel-Einstellung, Motorplatte mit Becherhaube, Zahnradabdeckung, Blinddeckel; ohne Rutschkupplung und ohne Kardanwelle E1 (Entscheidungen 2026-11-01); Skelett-Korrektur der Motorlage in einem eigenen PR
4. **Vorderachse und Lenkung**: Querlenker, Achsschenkel, Lenkhebelsystem mit Ackermann, Servohalter, Servo-Saver
5. **Elektronikhalter**: Fahrtenregler, Empfänger, Akkuhalterung, Kabelführung
6. **Karosseriehalter und Rammschutz**
7. Drucken, Montage, erste Testfahrt, Schwachstellen dokumentieren
8. **Bauanleitung v1** in `docs/`

### Phase 2: Allrad (4WD)
- Vorderachsdifferential und Gehäuse, vordere Kardanwelle, Abtrieb vorne am Mittelantrieb
- **Rutschkupplung** als eigene Anforderung (in v1 entfallen, Entscheidung 2026-11-01): braucht ca. 30 mm auf E2, also eine eigene E2 oder ein längeres Getriebe; Kardanwelle E1 einbauen, Blinddeckel der Becherhaube entfernen

### Phase 3: Gefräste Aluteile
- Teile, die bei den Tests in Phase 1/2 brechen oder sich verbiegen, kommen zuerst dran
- Erwartet: Grundplatte, Dämpferbrücken, Lenkhebel, Motorhalter
- CAM in Fusion, Fräsparameter und Spannmittel unter `cad/`
- Grundplatte (MECH-CHA-005, Nutzerentscheidungen 2026-10-28): Bohr-NC für alle 107 Bohrungen, Senk-Operation (90°-Senker bzw. Fasenfräser ≥ Ø 7 mm), Taschen-Operation und CAM-Simulation nachholen. Die Bohroperation neu aufsetzen (in Fassung 1 gab der Post nur 1 von 105 Bohrungen aus; Lösungsansatz: Löcher über ihre Mittelpunkte auswählen oder ein Setup von oben). Einzelheiten in `docs/grundplatte-oberdeck.md`
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
- [x] **Spenderplattform:** Tamiya TT-02B (seit 2026-10-28, vorher TLR 22X-4), siehe „Entscheidungen“
  - Differential, Dämpfer, Antriebswellen (CVD/Knochen), Radmitnehmer, Lager und Zahnräder möglichst als Ersatzteile *eines* verbreiteten 1:10-Buggys kaufen. So passen die Teile zueinander und sind einzeln nachkaufbar.
  - Verglichen wurden RC10B74.2, XRAY XB4 und TLR 22X-4 (`docs/zukaufteile-v1.md`).
- [x] **Zahnradmodul** für Motorritzel und Hauptzahnrad: Tamiya Modul 0,6 (seit 2026-10-28, vorher 48 Pitch)
- [x] **ELRS-Empfänger mit PWM-Ausgängen:** HelloRadio HR7E
- [ ] **Sender v1:** z. B. ein Pistolengriff-Sender mit eingebautem ELRS. Der Sender muss mit der Regulatory Domain **EU_CE_2400** (LBT) laufen, wie der Empfänger HR7E
- [ ] **Karosserie:** zugekaufte 1:10-Buggy-Karosserie aus Lexan, oder eigene
- [x] **Höchstgeschwindigkeit und Budget** für v1: ca. 50 km/h, 600–1050 €; seit dem Plattformwechsel 2026-10-28 gilt nur die Obergrenze 1050 € (günstiger Einstieg, Summe ca. 512 €)
- [x] ~~**Dämpfer v1:**~~ entfällt durch den Plattformwechsel 2026-10-28 (Dämpfer aus dem TT-02B). Alter Stand: TLR-Dämpfersatz TLR233064 derzeit nicht lieferbar, Preis offen. Lieferbarkeit und Preis bei der Bestellung prüfen. Alle Posten mit Preis: 812,56 €; mit Dämpfern (Vergleichspreis Associated 91994/91995, 2 × 75,90–76,90 €) 964,36–966,36 €; mit den Richtpreisen der Teile „manuell suchen“ (Spurstangen, TLR232110, TLR236006) 1042,34–1044,34 €, knapp im Budget von 1050 €. Kostet ein Dämpfersatz mehr als 79,73 €, wird 1050 € überschritten (`docs/zukaufteile-v1.md`, Abschnitt „Budget“)
- [ ] **Stückliste Tamiya-Einzelteile für Mehrfachbauten:** Für weitere Fahrzeuge ohne Bausatz alle genutzten TT-02B-Teile mit Tamiya-Teilenummer und Bezugsquelle auflisten (Nutzerwunsch 2026-10-28, später)
- [x] **Grundplatte/Oberdeck (PR #6) und Skelett** auf die TT-02B-Maße anpassen
  - [x] Skelett umgestellt (Fassung 2, `docs/skelett.md`)
  - [x] Grundplatte/Oberdeck (PR #6) auf dem neuen Skelett neu aufbauen (Fassung 2, 2026-10-31, `docs/grundplatte-oberdeck.md`)
- [ ] **Portalfräse:** Verfahrweg und welche Aluminiumlegierung (z. B. 6061/7075)

## Arbeitsweise
- Vor jeder Baugruppe läuft der Skill `anforderungsanalyse`. Das Ergebnis liegt unter `docs/anforderungen/`.
- CAD entsteht in Fusion über den MCP-Server, parametrisch mit den Benutzerparametern oben.
- Jedes Teil kommt in `bom/stueckliste.csv`.

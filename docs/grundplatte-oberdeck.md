# Grundplatte und Oberdeck

- **Anforderungen:** `docs/anforderungen/grundplatte-oberdeck.md` (Kürzel CHA, Fassung 2)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-grundplatte“, **Version 11**, abgeleitet von „open-rc-car-skelett“ **v12** (Fassung 2, Tamiya TT-02B; v12 ist maßgleich mit v10, siehe [Parametertest](#parametertest-mech-cha-001)). Version 8 ist ein Zwischenstand des Neuaufbaus, Version 9 der Stand vor Review 1, Version 10 der Stand nach Review 1 (ohne Fügespiel).
- **Exporte (alle aus Version 11):** `cad/fusion/chassis-grundplatte-oberdeck.f3d`, `cad/step/chassis-grundplatte-oberdeck.step` (8 Druckkörper), `cad/step/chassis-grundplatte-alu.step` (1 Körper), 8 STL in `print/stl/`
- **Stand:** 2026-10-31

Die Grundplatte trägt alle Baugruppen und legt deren **Lochbilder** fest (Schnittstellenblatt unten). Für den Druck ist sie zweiteilig mit Stoß in der Fahrzeugmitte, für die spätere Alufräsung einteilig. Das Oberdeck läuft mittig längs über der Kardanwelle und liegt auf beiden Achsgetrieben und auf einer neuen **Mittelstütze** auf. Vier Anschläge legen den Akku fest. Vorne und hinten ist die Platte über die Getriebe hinaus verlängert (Rammschutz, Karosseriehalter). Neben den Getrieben sind die Fußflächen der **Querlenkerböcke** reserviert, neben dem Servo die der **Lagerböcke des Lenkhebelsystems**.

![Grundplatte, Oberdeck, Mittelstütze und Anschläge](images/grundplatte-iso.png)

*Von vorne rechts. Blau: Grundplatte hinten, orange: Grundplatte vorne (im Stoß oben), schwarz: Oberdeck, violett: Mittelstütze, grün: Akkuanschläge, magenta: reservierte Fußflächen der Querlenkerböcke und Lenkhebel-Lagerböcke (kein Bauteil).*

![Von oben](images/grundplatte-oben.png)

*Von oben, vorne ist rechts, links ist oben.*

![Von unten](images/grundplatte-unten.png)

*Von unten (gespiegelt: vorne ist links, links ist oben). Alle Bohrungen mit 90°-Senkung. Die Senkungen der 15 Stoßbohrungen liegen im hinteren Teil (blau, untere Lage).*

![Mit Skelett](images/grundplatte-skelett-iso.png)

*Mit den Hüllkörpern des Skeletts (ohne Räder, Radräume und Akku-Entnahmeweg), Version 11. Magenta: reservierte Fußflächen, vorne rechts der Lenkhebel-Lagerbock in der Lage nach Review 1 (`lk_x_rechts`, 2 mm vor der Dämpfer-Hülle).*

## Ergebnis

| Teil | Komponente / Körper | Hüllquader X × Y × Z (mm) | Masse PETG, 100 % | Datei |
|---|---|---|---|---|
| Grundplatte hinten (Druck) | `chassis-grundplatte` / `grundplatte-hinten` | 186,8 × 144,0 × 4,0 (X −172…14,8) | 97,0 g | `print/stl/chassis-grundplatte-hinten.stl` |
| Grundplatte vorne (Druck) | `chassis-grundplatte` / `grundplatte-vorne` | 186,8 × 144,0 × 4,0 (X −14,8…172) | 96,6 g | `print/stl/chassis-grundplatte-vorne.stl` |
| Grundplatte Alu (einteilig) | `chassis-grundplatte` / `grundplatte-alu` | 344,0 × 144,0 × 4,0 | 412,0 g in Alu 6061 | `cad/step/chassis-grundplatte-alu.step` |
| Oberdeck | `chassis-oberdeck` / `oberdeck` | 244,0 × 41,0 × 3,0 | 20,7 g | `print/stl/chassis-oberdeck.stl` |
| Mittelstütze | `chassis-mittelstuetze` / `mittelstuetze` | 30,0 × 20,0 × 55,2 | 17,6 g | `print/stl/chassis-mittelstuetze.stl` |
| Akkuanschlag links | `chassis-akkuanschlag-links` | 60 × 8 × 10 | 5,7 g | `print/stl/chassis-akkuanschlag-links.stl` |
| Akkuanschlag rechts | `chassis-akkuanschlag-rechts` | 60 × 8 × 10 | 5,7 g | `print/stl/chassis-akkuanschlag-rechts.stl` |
| Akkuanschlag vorne (Platzhalter Bügelpfosten) | `chassis-akkuanschlag-vorne` | 8 × 20 × 10 | 1,8 g | `print/stl/chassis-akkuanschlag-vorne.stl` |
| Akkuanschlag hinten | `chassis-akkuanschlag-hinten` | 8 × 20 × 10 | 1,8 g | `print/stl/chassis-akkuanschlag-hinten.stl` |
| **Summe Druck** | | | **247,0 g** (≤ 250 g) | |
| Reservierte Fußflächen (kein Bauteil) | `chassis-fussflaechen` (10 Quader) | siehe Schnittstellenblatt | – | nur im f3d |

Masse = Volumen aus Fusion × 1,27 g/cm³ (PETG). Das ist eine obere Grenze, weil mit 100 % Füllung gerechnet ist. In Prusament PC (ca. 1,20 g/cm³) sind es 233,4 g. Ohne die vier Erleichterungstaschen (MECH-CHA-019) wären es rund 254 g: **Die Taschen sind für MECH-CHA-017 nötig** und dürfen nicht entfallen. Die Reserve bis 250 g ist mit 3,0 g klein; jedes zusätzliche Material (z. B. ein breiteres Oberdeck) muss an anderer Stelle eingespart werden.

## Aufbau in Fusion

- **Ableitung:** Das Design übernimmt aus „open-rc-car-skelett“ **v10** alle 155 Benutzerparameter (Favoriten), die 8 Bezugsebenen und die 38 Hüllkörper- und Bewegungsraum-Komponenten. Der Skelett-Körper `chassis-grundplatte` wird nicht übernommen, die Grundplatte entsteht hier neu. Die alte Ableitung (Skelett v6, Layout der Fassung 1, siehe [Historie](#historie)) und alle Features und Parameter der Fassung 1 sind entfernt; die Ableitung wurde neu angelegt. Nach dem Parametertest zeigt die Referenz auf Skelett **v12** (maßgleich mit v10, `Document.documentReferences`: Version 12, aktuell). Der Name des Zeitleisten-Elements bleibt „Abgeleitet von open-rc-car-skelett v10“; Fusion vergibt ihn beim Anlegen, und er lässt sich über die API nicht ändern.
- **Namen:** Abgeleitete Parameter heißen in Fusion `<name>_Ref`, z. B. `radstand_Ref`. In dieser Doku stehen sie ohne `_Ref`.
- **Ableitung aktualisieren (Erfahrung aus Fassung 1):** Nach einer Änderung das Skelett speichern und hier „Ableitung aktualisieren“ ausführen. Über die API aktualisiert `Document.updateAllReferences()` nur die Körper; erst `DeriveFeature.setSourceEntities(f.sourceEntities, [])` übernimmt auch die abgeleiteten Parameter, danach `Design.computeAll()`. Abgeleitete Parameter sind in diesem Design schreibgeschützt.
- **Komponenten:** `chassis-grundplatte` (Körper `grundplatte-alu`, `grundplatte-hinten`, `grundplatte-vorne`), `chassis-oberdeck`, `chassis-mittelstuetze`, `chassis-akkuanschlag-links`, `-rechts`, `-vorne`, `-hinten` und `chassis-fussflaechen` (10 Quader, nur für die Kollisionsprüfung). Jede Komponente hat eine Beschreibung mit Druckausrichtung.
- **Druck- und Aluvariante aus einer Kontur:** Die Umrissskizze `umriss` wird zweimal extrudiert (`grundplatte-alu`, `grundplatte-druck`). Der Druckkörper wird an den Ebenen „Stoss hinten“ (X = `stoss_x1`), „Stoss vorne“ (X = `stoss_x2`) und „Stoss Mitte“ (Z = `stoss_z`) geteilt und zu `grundplatte-hinten` und `grundplatte-vorne` vereint. Danach setzen zwei Features „Fläche versetzen“ (`stoss-spiel-hinten`, `stoss-spiel-vorne`, Abstand `-stoss_spiel`) die Zungenenden der beiden Druckteile um das Fügespiel zurück; der Alu-Körper ist davon nicht betroffen. Bohrungen, Senkungen, Raster und Taschen schneiden mit **demselben** Feature alle drei Körper. Deshalb sind die Lochbilder von Druck und Alu identisch; reine Stoßbohrungen gibt es nicht mehr.
- **Parametrik:** Alle 27 Skizzen sind voll bestimmt, alle Maße in Skizzen und Features sind Ausdrücke aus Parametern. Koordinaten sind als Abstand zum Skizzenursprung mit `abs(…)` bemaßt; Löcher auf derselben Flucht sind mit „vertikal/horizontal ausrichten“ gekoppelt. Feste Werte sind nur die Verjüngung der Senkung (−45°, aus 90° Senkwinkel ISO 10642).
- **Elektronik-Raster:** eine Bohrung mit Senkung an (`raster_x0`, `raster_y0`), dazu ein Rechteckmuster `raster_nx` × `raster_ny` mit Abstand `raster_teilung`.
- **CAM:** Setup „grundplatte-alu von unten“ mit der 2D-Kontur „Kontur aussen Fraeser 3 mm“ (siehe [Fräsbarkeit](#fräsbarkeit-mech-cha-004-mech-cha-005)). Die nicht funktionierende Bohroperation der Fassung 1 ist entfernt (Phase 3).

## Umriss (MECH-CHA-002)

Der Umriss ist achsparallel mit Radius `gp_kantenradius` = 2 mm an allen senkrechten Kanten:

| Bereich | X (mm) | Y (mm) | Parameter |
|---|---|---|---|
| Ende hinten mit Verlängerung, Hinterachse | −172 … −90 | ±46 | `platte_x_hinten − gp_ueberstand`, `gp_mitte_hinten_x`, `gp_achse_y` |
| Mitte links (Akkuschacht verbreitert) | −90 … 82 | bis 70 | `gp_links_breit` = `platte_links + gp_zugabe_links`, `gp_links_vorne_x` |
| Mitte rechts (Elektronik) | −90 … 85 | bis −74 | `platte_rechts`, `gp_rechts_vorne_x` |
| Absatz rechts (Lenkhebel-Lagerbock rechts) | 85 … 99,75 | bis −62 | `gp_rechts_lk`, `gp_lk_ende_x` (an `lk_x_rechts`) |
| Vorderachse und Ende vorne mit Verlängerung | 82 bzw. 99,75 … 172 | ±46 | `gp_ende_x` = `platte_x_vorne + gp_ueberstand` |

- **Verlängerung:** `gp_ueberstand` = 15 mm vorne und hinten über die Getriebe-Hüllen (X ±157) hinaus. Gemessen: Hüllquader **344,00 × 144,00 × 4,00 mm** = 314 + 2 × 15 mm lang, Unterkante Z 25,00 mm.
- **Querlenkerböcke:** Die Plattenenden sind ±46 mm breit (Fußflächen bis ±43 mm + `gp_fuss_rand` 3 mm), statt ±24,9 mm wie die Getriebe-Hülle im Skelett.
- **Akkuschacht:** links bis Y 70 mm (Akku bis 58 + 1 mm Spiel + 8 mm Anschlag + 3 mm Rand), von X −90 bis 82 mm. Die Kante springt vor dem vorderen Anschlag auf ±46 zurück, damit die Platte den Lenk-Bewegungsraum vorne links nicht erreicht. Rechts endet die volle Breite (Y −74) bei X 85 mm vor dem UBEC; der Skelett-Umriss reichte dort bis X 89,5 mm und hielt nur 3,92 mm Abstand zum Radraum vorne rechts.
- **Abstand zu den Bewegungsräumen** (alle drei Körper, `measureMinimumDistance`): Radräume min. **8,55 mm** (vorne rechts; Soll ≥ 5), Wellenräume min. **11,15 mm** (vorne; Soll ≥ 3). 0 Überschneidungen.

## Stoß (MECH-CHA-003)

- Halbüberlappung von X = −15 bis +15 mm (`teilung_x` ± `teilung_ueberlappung`/2). Der hintere Teil hat im Stoß die untere Lage (Z 25…27), der vordere die obere (Z 27…29). Die Unterseite ist im Stoß flach.
- **Keine eigenen Stoßschrauben mit Muttern mehr:** Den Stoß klemmen die Schrauben, die ohnehin durch die Überlappung gehen, alle M3-Senkkopf × 8 von unten in Gewindeeinsätze. Nichts steht oben über, es gibt keine Mutter und kein freies Schraubenende (LiPo-Schutz unter dem Akku, Regler):
  - Mittelstütze: 4 × (±10 / −16 und −26)
  - Akkuanschlag links: mittleres Loch (0 / 63)
  - Akkuanschlag rechts: mittleres Loch (0 / 7)
  - **Summe 6 Schrauben durch beide Lagen** (Soll ≥ 6). Dazu kommen 9 Rasterbohrungen (X −10 / 0 / 10, Y −69 / −59 / −49), die mit den Adapterplatten der Elektronik ebenfalls klemmen.
- Querverteilung der Klemmpunkte (Y): Raster −69…−49, Mittelstütze −26/−16, Anschlag rechts 7, Anschlag links 63. Größte Lücke ohne Schraube: Y 7…63 mm (unter dem Akku, an beiden Enden geklemmt).
- **Die Akkuanschläge links und rechts sind tragend für den Stoß.** Ohne sie bleibt zwischen Mittelstütze (Y −16) und dem linken Plattenrand (Y 70) eine Lücke von über 80 mm ohne Schraube, und die 9 Rasterbohrungen im Stoß klemmen erst, wenn die Adapterplatten der Elektronik verschraubt sind. Die Anschläge deshalb immer montieren, auch wenn der Akku nicht eingesetzt ist (Prüfpunkt in der [Probemontage](#probemontage-mech-cha-015-vom-nutzer-auszufüllen)).
- **Fügespiel an den Stufen** (Review 1, Nutzerentscheidung 2026-10-31): `stoss_spiel` = **0,2 mm** an den beiden senkrechten Stufenflächen. Die Zungen sind um das Spiel kürzer: Die untere Zunge des hinteren Teils endet bei X 14,8 (Stufe des vorderen Teils bei 15,0), die obere Zunge des vorderen Teils bei X −14,8 (Stufe des hinteren Teils bei −15,0). Gemessen (`measureMinimumDistance` Zungenende ↔ Stufenfläche): **0,200 mm** je Stufe. Die waagerechte Anlagefläche bei Z 27 hat kein Spiel (Abstand 0,000 mm), Interferenz zwischen den Teilen 0. Die Aluvariante hat keinen Stoß und bleibt unverändert.
  - Weil das Raster (Takt 10 mm auf `teilung_x`), die Mittelstütze und die Anschläge Löcher genau 5 mm vor bzw. hinter den Stufen haben, sinkt der Randabstand der Löcher in den Zungen (X ±10) auf **4,80 mm** zum Zungenende. Das ist die Ausnahme in MECH-CHA-008 (≥ 4,8 mm an den Stoßstufen). Die Löcher neben den Stufen (X ±20) behalten 5,00 mm. Die Wand zwischen Senkung (Ø 6,9 mm, hinterer Teil) und Zungenende ist **1,35 mm** (≥ 1,2 mm). Das Raster bleibt durchgehend.
  - Bei 0,2 mm Spiel je Stufe kann der vordere Teil gegenüber dem hinteren höchstens 0,2 mm in X wandern; die Bohrungen Ø 3,2 mm für M3 haben selbst 0,2 mm Spiel, die Schrauben richten den Stoß also aus. Der Spalt (0,2 mm) bleibt an den Stufen auf Ober- und Unterseite sichtbar.

  ![Stoß von rechts mit Fügespiel](images/grundplatte-stoss-spiel.png)

  *Stoß von rechts (X nach rechts, Z nach oben), Ausschnitt X ≈ −19…19: blau hinterer Teil mit unterer Zunge, orange vorderer Teil mit oberer Zunge, links und rechts je 0,2 mm Spalt an den Stufen.*
- Druckteile mit Überlappung: je **186,8 × 144,0 mm** (≤ 250 × 250).
- Schraubenenden: Platte 4 mm + 4 mm im Einsatz, Ende bei Z 33 mm im Sackloch (Ø 4 × 6 mm, bis Z 35). Interferenz der Anschläge und der Mittelstütze mit allen Skelett-Körpern: 0.

## Befestigung an der Grundplatte (MECH-CHA-008)

- Jede Bohrung hat Ø 3,2 mm (`gp_bohrung`) und unten eine 90°-Senkung Ø 6,9 mm (`gp_senkung_d`, Tiefe 1,85 mm) für M3-Senkkopf ISO 10642 (dk max. 6,72 mm, Kopf bündig).
- Schraube von unten, Gewinde im aufgesetzten Teil (Druck: Gewindeeinsatz M3 kurz, Stückliste Pos. 30; Alu: geschnitten). Schraubenlänge für Einsätze M3 × 8. Die Unterseite hat keine vorstehenden Teile.
- Zweierlochbilder haben den Abstand `gp_paar_d` = 9 mm (Steg zwischen den Senkungen 2,1 mm).
- **Prüfskript** (Flächen der Körper ausgewertet):
  - `grundplatte-alu`: **107 Bohrungen** Ø 3,2 mm, 107 Kegel mit Halbwinkel 45,0°, Ø 6,9 mm an der Unterseite, Z 25,00…26,85, Achse senkrecht. Keine Bohrung ohne Senkung.
  - `grundplatte-hinten` 58, `grundplatte-vorne` 64 Bohrungen, vereint 107 = Alu; 15 davon in beiden Druckteilen (Stoß). Kegel: hinten 58, vorne 49, also jede Senkung genau einmal, im Stoß in der unteren Lage.
  - Randabstand Lochmitte ↔ Umriss und Taschen min. **5,00 mm** (Raster am rechten Rand). Lochmitte ↔ Stoßstufe in den Druckteilen min. **4,80 mm** (Löcher X ±10 ↔ Zungenenden X ±14,8, Ausnahme MECH-CHA-008, Soll ≥ 4,8), Löcher X ±20 ↔ Stufen X ±15 5,00 mm. Wand Senkung ↔ Zungenende **1,35 mm** (Soll ≥ 1,2). Gerechnet in der Ebene über alle Kanten der Ober- und Unterseiten und der Stufenflächen (Version 11).
  - Lochabstand Mitte–Mitte min. **8,56 mm** (Motorhalter (−71 / −40,5) ↔ Raster (−70 / −49)), Soll ≥ 8 mm.

## Schnittstellenblatt: Lochbilder (MECH-CHA-007)

Koordinaten im Fahrzeugsystem des Skeletts: X längs nach vorne, Y quer nach links, Ursprung Fahrzeugmitte zwischen den Achsen, Z vom Boden. Alle Bohrungen Ø 3,2 mm mit Senkung unten (MECH-CHA-008), alle von unten zugänglich. Alle Lochbilder gelten für Druck- und Aluvariante. Werte im Startzustand des Skeletts v10 (`radstand` 266 mm, `achse_x` 133 mm). **Alle Lochbilder außer dem Raster sind vorläufig**; eine Änderung bedeutet einen Neudruck der betroffenen Plattenhälfte.

| Lochbild | Anzahl | Koordinaten X / Y (mm) | Parameter (X; Y) |
|---|---|---|---|
| Hinterachsgetriebe | 4 × M3 | (−152 / ±18); (−114 / ±18) | `-achse_x ∓ gp_getriebe_dx`; `±gp_getriebe_y` |
| Vorderachsgetriebe 4WD | 4 × M3 | (114 / ±18); (152 / ±18) | `achse_x ∓ gp_getriebe_dx`; `±gp_getriebe_y` |
| Querlenkerbock hinten, hinter der Achse | 2 × 2 × M3 | (−151 / 30,5; 39,5) und (−151 / −30,5; −39,5) | `-achse_x - ql_dx`; `±(ql_y ∓ gp_paar_d / 2)` |
| Querlenkerbock hinten, vor der Achse | 2 × 2 × M3 | (−115 / ±30,5; ±39,5) | `-achse_x + ql_dx`; wie oben |
| Querlenkerbock vorne, hinter der Achse | 2 × 2 × M3 | (115 / ±30,5; ±39,5) | `achse_x - ql_dx`; wie oben |
| Querlenkerbock vorne, vor der Achse | 2 × 2 × M3 | (151 / ±30,5; ±39,5) | `achse_x + ql_dx`; wie oben |
| Lagerbock Lenkhebel links | 2 × M3 | (94,5 / 30,5; 39,5) | `lk_x`; `lk_y_links ∓ gp_paar_d / 2` |
| Lagerbock Lenkhebel rechts | 2 × M3 | (92,75 / −46,5; −55,5) | `lk_x_rechts`; `-(lk_y_rechts ∓ gp_paar_d / 2)` |
| Servohalter | 4 × M3 | (53,2 / −27,1); (53,2 / −17,1); (85,0 / −37,2); (95,0 / −37,2) | `gp_sh_x_hinten`, `gp_sh_x_vorne - gp_sh_dx`, `gp_sh_x_vorne`; `servo_y ∓ gp_sh_dy`, `gp_sh_y_aussen` |
| Motorhalter (trägt die Zahnradabdeckung) | 3 × M3 | (−71 / −40,5; −28,5; −16,5) | `gp_mh_x`; `motor_y`, `motor_y ± gp_mh_dy` |
| Rammschutz hinten / vorne | je 2 × M3 | (−164,5 / ±8); (164,5 / ±8) | `platte_x_hinten - gp_ueberstand / 2`, `gp_ende_loch_x`; `±gp_ramm_y` |
| Karosseriehalter hinten / vorne | je 2 × M3 | (−164,5 / ±22); (164,5 / ±22) | wie Rammschutz; `±gp_karo_y` |
| Akkuanschlag links | 3 × M3 | (−20; 0; 20 / 63), mittleres im Stoß | `akku_anschlag_x ± akku_anschlag_dx`; `akku_anschlag_links_y` |
| Akkuanschlag rechts | 3 × M3 | (−20; 0; 20 / 7), mittleres im Stoß | wie links; `akku_anschlag_rechts_y` |
| Akkuanschlag vorne = Akkubügel-Pfosten vorne | 2 × M3 | (74 / 54; 63) | `akku_anschlag_vorne_x`; `akku_anschlag_vorne_y ∓ akku_anschlag_vh_dy` |
| Akkuanschlag hinten | 2 × M3 | (−74 / 30,5; 39,5) | `akku_anschlag_hinten_x`; `akku_anschlag_hinten_y ∓ akku_anschlag_vh_dy` |
| Akkubügel-Pfosten hinten | 2 × M3 | (−84 / 30,5; 39,5) | `akku_pfosten_x`; wie Anschlag hinten |
| Mittelstütze | 4 × M3 | (−10 / −16; −26); (10 / −16; −26), alle im Stoß | `ms_x ∓ ms_loch_dx`; `ms_y_mitte ∓ ms_loch_dy` |
| Elektronik-Raster | 48 × M3 | X −70…80 (16 Spalten), Y −69 / −59 / −49, Teilung 10 | `raster_x0`, `raster_nx` (abgeleitet aus `gp_rechts_vorne_x`), `raster_y0`, `raster_ny`, `raster_teilung` |
| **Summe** | **107** | | |

### Reservierte Fußflächen (MECH-CHA-020, MECH-CHA-022)

Quader in `chassis-fussflaechen`, von der Plattenoberkante (Z 29) bis Z 44 (15 mm, `ql_h`, `lk_h`; die Diff-Becher beginnen bei Z 46,3). Die Anlenkachse der Querlenker ist parallel zu X angenommen; je Seite und Achse ein Bock vor und einer hinter der Achse, beide **neben** dem Getriebe (Getriebe-Hülle Y ±24,86).

| Fußfläche | X (mm) | Y (mm) | Lage begründet durch | engster Abstand (gemessen) |
|---|---|---|---|---|
| Querlenkerbock hinten, hinter der Achse, links/rechts | −156…−146 | ±27…±43 | hinter dem Wellenraum, neben dem Getriebe | Getriebe 2,14; Wellenraum 7,39 |
| Querlenkerbock hinten, vor der Achse, links/rechts | −120…−110 | ±27…±43 | Fenster zwischen Wellenraum (bis X −122,7 bzw. Welle −126) und Zahnradabdeckung (ab X −109) bzw. Dämpfer (ab Y 44,75) | Zahnradabdeckung 1,00 (rechts); Dämpfer 1,79; Wellenraum 7,39 |
| Querlenkerbock vorne, hinter der Achse, links/rechts | 110…120 | ±27…±43 | zwischen Dämpfer (Y ab 44,75) und Wellenraum | Dämpfer 1,79; Getriebe 2,14; Wellenraum 6,94 |
| Querlenkerbock vorne, vor der Achse, links/rechts | 146…156 | ±27…±43 | vor dem Wellenraum, neben dem Getriebe | Getriebe 2,14; Wellenraum 6,94 |
| Lagerbock Lenkhebel links | 90,5…98,5 | 27…43 | zwischen XT60 (bis X 89,5), Vorderachsgetriebe (ab X 99) und Dämpfer | XT60 1,00; Getriebe 2,20; Radraum 28,46; Wellenraum 27,55 |
| Lagerbock Lenkhebel rechts | 88,75…96,75 | −59…−43 | rechts außerhalb von Servo (bis Y −32,2) und Servohalter-Lochbild (Y −37,2), vor dem UBEC (bis X 82,5), 2 mm vor der Dämpfer-Hülle vorne rechts (ab X 98,75) | Dämpfer vorne rechts **2,00**; UBEC 6,25; Servo 10,8; Radraum 12,46; Wellenraum 28,28 |

- **Querlenkerböcke:** Mitte der Fußflächen 18 mm (`ql_dx`) vor bzw. hinter der Achse, Stützweite der Querlenkerachse also 36 mm. Ein größerer Abstand geht vor der Hinterachse nicht: Zwischen Wellenraum und Zahnradabdeckung bleibt nur das Fenster X −122,7…−109. Die Lage ist vorläufig, bis „Hinterachse“ bzw. „Vorderachse“ die Aufhängungsgeometrie festlegen.
- **Lenkhebelsystem:** Die Lagerböcke sitzen wie beim TT-02B zwischen Servo und Vorderachsgetriebe. So bleibt die Verbindung zum Servo-Saver (Servo X 57,2…97,5) kurz und muss nicht über das Vorderachsgetriebe (bis Z 80,6) und unter dem Oberdeck hindurch. Die Alternative auf der Verlängerung vor dem Getriebe wurde verworfen, weil die Anlenkung vom Servo dann um das Getriebe herum führen müsste. Spurstangen und Ackermann-Geometrie legt „Vorderachse und Lenkung“ fest. Links bindet das XT60 die Lage (`lk_x`, 1,00 mm), rechts die Dämpfer-Hülle vorne rechts: Der rechte Bock hat deshalb eine eigene Lage `lk_x_rechts` = `achse_x − daempfer_dx − daempfer_d/2 − 2 mm − lk_l/2` (92,75 mm), 1,75 mm hinter dem linken (Review 1: vorher 0,25 mm zur Dämpfer-Hülle). Er folgt damit dem Dämpfer, wenn sich der Radstand ändert.
- Interferenz aller 10 Fußflächen mit allen 38 Skelett-Körpern: **0**. Abstand zu den Wellenräumen ≥ 6,94 mm (Soll ≥ 3), zu den Radräumen ≥ 12,46 mm (Soll ≥ 5), zu allen anderen Hüllkörpern ≥ 1,00 mm.

### Elektronik-Raster (MECH-CHA-009)

| Größe | Wert | Parameter |
|---|---|---|
| Teilung | 10 mm in X und Y | `raster_teilung` |
| Spalten | X = −70, −60 … 80 mm (16) | `raster_x0` = `teilung_x − 7 · raster_teilung`, `raster_nx` = `floor((gp_rechts_vorne_x − gp_rand − raster_x0) / raster_teilung) + 1` |
| Reihen | Y = −69, −59, −49 mm (3) | `raster_y0` = `−platte_rechts + gp_rand`, `raster_ny` |
| Bohrungen | 48 × M3, Senkung unten | |

- Der Takt hängt an `teilung_x`, deshalb läuft das Raster über den Stoß im gleichen Takt; die Spalten −10, 0 und 10 gehen durch beide Lagen, die Spalten ±20 liegen je 5 mm neben den Stoßstufen.
- Rasterbohrungen unter den Hüllkörpern: Empfänger (X −74…−28, Y −74…−48) 15, Regler (X −21…31,5) 18, UBEC (X 33,5…82,5, Y bis −37,7) 15; je ≥ 4.
- Die Spaltenzahl folgt dem Umriss: Die volle Breite rechts endet vor dem UBEC (`gp_rechts_vorne_x`), die letzte Spalte hält davon `gp_rand` Abstand. Wandert die Elektronik mit dem Skelett (z. B. `radstand` 280 mm: UBEC 7 mm weiter hinten), fällt eine Spalte weg, statt ins Leere zu bohren (Befund aus dem Parametertest).
- Eine vierte Reihe bei Y −39 entfällt: Sie läge unter dem Motor (Y bis −46,5) bzw. am Servohalter (Y −37,2). Kein Rasterloch liegt unter Motor, Motorhalter-Lochbild oder Servohalter (kleinster Abstand Raster ↔ Motorhalter-Loch 8,56 mm, ↔ Servohalter 12,8 mm).

### Oberdeck-Befestigung und Auflagehöhe (MECH-CHA-011)

| Verbindung | Löcher im Oberdeck (X / Y mm) | Parameter | Auflagehöhe (Unterkante Oberdeck) |
|---|---|---|---|
| Hinterachsgetriebe | (−115 / ±5) | `-(achse_x - od_getriebe_dx)`; `±od_loch_y` | **Z = 84,2 mm** |
| Mittelstütze | (0 / −16; −26) | `ms_x`; `ms_y_mitte ∓ ms_loch_dy` | **Z = 84,2 mm** |
| Vorderachsgetriebe | (115 / ±5) | `achse_x - od_getriebe_dx`; `±od_loch_y` | **Z = 84,2 mm** |

- `od_z` = `antrieb_z` + `abdeckung_r` + `od_luft` = 56,6 + 26,6 + 1 = **84,2 mm**: 1 mm über der Zahnradabdeckung (Oberkante 83,2). Das ist die **Vorgabe für die Getriebegehäuse**: Die Getriebe-Hülle endet bei Z 80,6, die Gehäuse brauchen an den Löchern (∓115 / ±5) Auflagen bis Z 84,2 (+3,6 mm) mit Gewindeeinsätzen. Die Mittelstütze reicht genau bis 84,2.
- Befestigung: M3-Zylinderkopf × 8 von oben in Gewindeeinsätze. Bohrung Ø 3,2 mm.
- Form: Streifen X −122…122, Y ±10 (`od_halb_b` = `akku_y_innen` − 2 mm) über der Kardanwelle, dazu eine Lasche X −15…15 bis Y −31 zur Mittelstütze. Eckradien außen 5 mm, an der Lasche 3 mm. 244 × 41 × 3 mm, einteilig.
- Frei bleiben: Akku-Entnahmeweg (2,00 mm daneben), Motor (Y bis −10,5, 9,6 mm darunter), Regler, Servo (Y ab −12) und Zahnradabdeckung (1,00 mm darunter). Engster Abstand zu allen 38 Skelett-Körpern **1,00 mm** (Zahnradabdeckung), Getriebe-Hüllen 3,60 mm.
- Steifigkeit: Das Oberdeck ist mit 20 mm schmaler als in Fassung 1 (30 mm), weil links der Akku-Entnahmeweg ab Y 12 beginnt. Die Breite ist der Parameter `od_halb_b`.

### Mittelstütze (MECH-CHA-021)

- Neues Druckteil anstelle des Mittelschotts: I-Profil in der XZ-Ebene, 20 mm tief (Y −31…−11), rechts neben der Kardanwelle am Stoß.
  - Fuß X −15…15 (`ms_l` = Überlappung), Z 29…37 (`ms_fuss_h`); Steg 8 mm (`ms_steg_b`); Kopf X −10…10, Z 76,2…84,2 (`ms_kopf_l`, `ms_kopf_h`); Innenecken R 2 mm (`ms_r`).
  - Unten 4 Gewindeeinsätze (±10 / −16; −26), Ø 4 × 6 mm: **4 × M3 × 8 Senkkopf von unten durch beide Lagen der Überlappung** (klemmt den Stoß).
  - Oben 2 Gewindeeinsätze (0 / −16; −26) für das Oberdeck.
- Lage aus den Skelett-Parametern: innen 1 mm neben der Becher-Hülle der Kardanwelle (`ms_y_innen` = −(`kardan_becher_d`/2 + 1 mm)), außen 1 mm neben dem Regler (`ms_y_aussen` = `regler_y + regler_b/2 + 1 mm`).
- Gemessen: Regler 1,00 mm, Kardanwelle 4,00 mm (die Welle selbst ist schlanker als die Becher-Hülle), Motor 8,16 mm, Akku-Entnahmeweg > 21 mm. 0 Überschneidungen.

### Zahnradabdeckung (MECH-CHA-012)

Befestigungspunkt ist das **Lochbild Motorhalter** (3 × M3): Die Zahnradabdeckung wird am Motorhalter befestigt. Grundplatte und Oberdeck lassen den Bauraum `mittelantrieb-zahnradabdeckung` frei: 0 Überschneidungen, Abstand 1,00 mm (Grundplatte, Luft unter der Abdeckung aus dem Skelett) und 1,00 mm (Oberdeck). Die Abdeckung muss den Ritzelwechsel ohne Abnehmen des Oberdecks erlauben (z. B. seitlicher Deckel); das ist eine Vorgabe an „Mittelantrieb“.

## Akkuschacht (MECH-CHA-010)

- Vier verschraubte Anschläge (Druckteile), 8 mm breit, 10 mm hoch (Z 29…39), Gewindeeinsätze M3 kurz (Bohrung Ø 4,0 × 6 mm, vorläufig), M3-Senkkopf × 8 von unten.
  - links (außen): X −30…30, Y 59…67, 3 Einsätze, das mittlere Loch klemmt den Stoß
  - rechts (innen): X −30…30, Y 3…11, 3 Einsätze, unter der Kardanwelle (Z 39 < 46,6, Abstand 11,12 mm), das mittlere Loch klemmt den Stoß
  - vorne: X 70…78, Y 48,5…68,5, links neben dem XT60 (2,50 mm Luft), nicht davor. Wird später durch den vorderen Bügelpfosten ersetzt (Entscheidung 2026-10-28), bis dahin Platzhalter auf demselben Lochbild.
  - hinten: X −78…−70, Y 25…45
- **Spiel gemessen** (`measureMinimumDistance` Anschlag ↔ Akku-Hülle): links, rechts, vorne und hinten je **1,00 mm**. 0 Überschneidungen mit Akku, XT60 und allen anderen Skelett-Körpern.
- **Entnahmeweg** nach oben: kein Anschlag und kein Oberdeck darin; Abstand Anschläge 15,19 mm, Oberdeck 2,00 mm.
- **LiPo-Schutz:** Alle Kanten der Anschläge außer der Auflagefläche R 1,5 mm (`akku_anschlag_r`). Schraubenenden enden im Sackloch der Einsätze (Z 33 < 35). Unter dem Akku steht auf der Oberseite nichts über.
- Lochbild für den hinteren Bügelpfosten 10 mm hinter dem hinteren Anschlag (−84 / 30,5; 39,5). Der Bügel mit Schnellverschluss kommt mit „Elektronikhalter“.

## Fräsbarkeit (MECH-CHA-004, MECH-CHA-005)

- **Aluvariante:** Körper `grundplatte-alu`, einteilig, aus derselben Umrissskizze und denselben Bohr-, Senk-, Raster- und Taschen-Features. Prüfskript: 107 Lochpositionen Alu = 107 Lochpositionen Druck (vereint), identisch. Reine Stoßbohrungen gibt es in Fassung 2 nicht. STEP `cad/step/chassis-grundplatte-alu.step` mit genau einem Körper (`MANIFOLD_SOLID_BREP('grundplatte-alu')`).
- **Prüfskript 2,5D** (Alu, beide Druckteile, Oberdeck): nur Ebenen parallel oder senkrecht zur Plattenebene, nur senkrechte Zylinder, Kegel nur an den Senkungen (Halbwinkel 45°, Achse senkrecht, alle an der Unterseite), keine anderen Flächentypen. Radien: Bohrungen 1,6, Umriss und Taschen 2,0, Oberdeck 3,0 und 5,0 mm (alle ≥ 1,5). Keine Hinterschnitte.
- **CAM über die API:** Setup „grundplatte-alu von unten“ (WCS Z gespiegelt, Rohteil +3 mm seitlich, +1 mm oben), Operation „Kontur aussen Fraeser 3 mm“ (2D-Kontur, Schaftfräser Ø 3 mm, Flächenkontur der Unterseite, nur Außenkontur). Werkzeugweg **ohne Fehler und ohne Warnung** berechnet. Die Bohroperation der Fassung 1 (Post gab nur 1 von 105 Bohrungen aus) ist entfernt.
- **⏳ Phase 3** (Entscheidungen 2026-10-28): Bohr-NC für 107 Bohrungen, Senk-Operation (90°-Senker oder Fasenfräser ≥ Ø 7 mm), Taschen-Operation für die 4 Erleichterungstaschen und Fräs-Simulation mit Kollisionsprüfung (in der API nicht verfügbar). Lösungsansatz aus Fassung 1 für das Bohren: Löcher über ihre Mittelpunkte auswählen oder ein Setup von oben anlegen.

## Druckhinweise (MECH-CHA-013)

| Teil | Lage auf dem Bett | Größe auf dem Bett | Stützen | Hinweis |
|---|---|---|---|---|
| Grundplatte hinten | Unterseite (Z 25) auf dem Bett | 186,8 × 144 mm | keine | Senkungen öffnen sich zum Bett, Kegelwand 45°. Die Stufe im Stoß zeigt nach oben. |
| Grundplatte vorne | **kopfüber**, Oberseite (Z 29) auf dem Bett | 186,8 × 144 mm | keine | Nur so liegt die obere Lage im Stoß auf dem Bett. STL liegt in Fahrzeuglage: im Slicer um 180° um X oder Y drehen. |
| Oberdeck | flach | 244 × 41 mm | keine | |
| Mittelstütze | auf einer Seitenfläche (Y-Fläche) | 30 × 55,2 mm, 20 hoch | keine | Profil liegt flach, die 6 Einsatzlöcher Ø 4 × 6 mm liegen waagerecht und werden überbrückt (Scheitel hängt leicht durch). Nach dem Druck die Löcher prüfen und bei Bedarf mit 4-mm-Bohrer nachziehen, Einsätze gerade einsetzen. Eine Tropfenform der Löcher ist nicht umgesetzt (Review 1, Hinweis). STL im Slicer um 90° um X drehen. |
| Akkuanschläge | Auflagefläche auf dem Bett | | keine | Sacklöcher Ø 4 mm offen zum Bett. Einsätze von unten einschmelzen und danach die Planlage prüfen. |

- Druckbett 256 × 256 mm: Das längste Teil ist das Oberdeck mit 244 mm, die Plattenhälften haben 186,8 × 144 mm. Geprüft an den STL-Dateien (Hüllquader wie in der Tabelle [Ergebnis](#ergebnis)). Ein Slicer ist auf diesem Rechner nicht installiert; die Slicer-Prüfung (im Bauraum, keine Stützen) macht der Nutzer bei der Probemontage.
- **Wandstärken** (Soll ≥ 1,2 mm):
  - Senkung ↔ Zungenende am Stoß (mit Fügespiel): 4,80 − 3,45 = **1,35 mm**
  - Senkung ↔ Plattenrand, Taschenrand und Stufe: min. 5,00 − 3,45 = **1,55 mm**
  - Steg zwischen Senkungen: min. 8,56 − 6,9 = **1,66 mm**, in Zweierlochbildern 9 − 6,9 = 2,1 mm
  - Tasche ↔ Plattenrand: 3,0 mm, Tasche ↔ Fußfläche 3,0 mm
  - Anschläge um den Einsatz: 2,0 mm; Mittelstütze um die Einsätze: ≥ 2,0 mm (Steg), 3,0 mm (Fuß, Seiten)
  - Oberdeck Loch ↔ Rand: ≥ 3,4 mm
  - Lagen im Stoß: je 2,0 mm. Die Senkung (1,85 mm) liegt im Stoß ganz in der 2-mm-Lage des hinteren Teils; der Rand unter dem Kegel zählt nicht als Wand (Entscheidung 2026-10-28).
- Bohrungen Ø 3,2 mm, das sind +0,2 mm auf M3.
- Fügespiel am Stoß: 0,2 mm je Stufe (`stoss_spiel`), nur in X. Elefantenfuß an der Bettseite trotzdem klein halten (erste Lage nicht zu stark gequetscht), sonst die Unterkante der Zungen leicht entgraten. Bei einem anderen Drucker oder Material lässt sich das Spiel über `stoss_spiel` anpassen; jedes 0,1 mm mehr verringert den Randabstand an den Stufen um 0,1 mm (Grenze 4,8 mm laut MECH-CHA-008, also ohne Rückfrage nicht über 0,2 mm).
- Material: PETG für die Probemontage, Prusament PC für das fertige Modell. Die Geometrie gilt für beide.
- Gewindeeinsätze MP-JET M3 kurz (Pos. 30): Maße nicht belegt, Bohrung Ø 4,0 × 6 mm ist ein Vergleichswert. **Bei Lieferung messen** und `akku_einsatz_d`, `akku_einsatz_t` anpassen (gilt auch für die Mittelstütze).

## Interferenz und Abstände

Fusion `analyzeInterference` über alle 19 neuen Körper und alle 38 abgeleiteten Skelett-Körper, ohne bloß berührende Flächen: **0 Überschneidungen** mit einem neuen Körper (zuletzt geprüft mit Version 11, Fügespiel 0,2 mm; die Paare `grundplatte-alu` ↔ `grundplatte-hinten`/`-vorne`, die am selben Ort liegen, meldet Fusion dabei nicht mehr). Kleinste Abstände (`measureMinimumDistance`):

| Prüfung | Überschneidungen | kleinster Abstand |
|---|---|---|
| Grundplatte (Alu, hinten, vorne) ↔ Radräume / Wellenräume | 0 | 8,55 mm (Radraum vorne rechts) / 11,15 mm (Wellenraum vorne) |
| Grundplatte ↔ alle Skelett-Körper | 0 | 0,00 mm (Teile liegen auf der Platte auf) |
| Oberdeck ↔ alle Skelett-Körper | 0 | 1,00 mm (Zahnradabdeckung) |
| Mittelstütze ↔ alle Skelett-Körper | 0 | 1,00 mm (Regler) |
| Akkuanschläge ↔ alle Skelett-Körper | 0 | 1,00 mm (Akku) |
| Fußflächen Querlenkerböcke ↔ alle Skelett-Körper | 0 | 1,00 mm (Zahnradabdeckung); Wellenraum 6,94 mm |
| Fußflächen Lenkhebel ↔ alle Skelett-Körper | 0 | 1,00 mm (XT60, links), rechts 2,00 mm (Dämpfer vorne rechts); Radraum 12,46 mm |
| Grundplatte, Oberdeck ↔ Zahnradabdeckung | 0 | 1,00 mm / 1,00 mm |

## Parametertest (MECH-CHA-001)

**Test mit dem Skelett, bestanden** (Review 1, 2026-10-31, Nutzerentscheidung 2026-10-31: Skelett darf dafür als v11 und v12 gespeichert werden):

1. Skelett `radstand` = 280 mm: Zeitleiste des Skeletts (327 Elemente) ohne Fehler, `achse_x` 140 mm. Gespeichert als **v11**.
2. Hier Ableitung aktualisiert (`Document.updateAllReferences()`, dann `DeriveFeature.setSourceEntities(…)` und `Design.computeAll()`): `radstand_Ref` 280 mm, Zeitleiste (83 Elemente) **ohne Fehler und Warnungen**.
3. Geprüft bei 280 mm (Bild unten):
   - Grundplatte 358 × 144 mm (X ±179), Druckteile X −179…15 und −15…179 (je 194 × 144 mm, ≤ 250), Oberdeck X ±129, Mittelstütze und Akkuanschläge unverändert (hängen an `teilung_x` und am Akku, nicht an der Achse).
   - Lochbilder folgen: Getriebe (∓159 / ∓121), Querlenkerböcke (∓158 / ∓122), Rammschutz und Karosseriehalter (±171,5), Motorhalter (−78), Servohalter (60,2; 92; 102), Lenkhebel rechts (99,75, folgt dem Dämpfer), Lenkhebel links (94,5, folgt dem XT60 und bleibt).
   - Fußflächen folgen: Querlenkerböcke X ∓163…∓153 und ∓127…∓117, Lenkhebel rechts X 95,75…103,75.
   - Interferenz aller neuen Körper mit allen 38 Skelett-Körpern: **0**. Mindestabstände: Radräume 9,46 mm, Wellenräume 11,15 mm (Platte); Querlenkerbock hinten vor der Achse ↔ Wellenraum **7,39 mm**, ↔ Zahnradabdeckung **1,00 mm** (rechts), ↔ Dämpfer **1,79 mm** (links), also gleich wie bei 266 mm, weil Bock, Wellenraum, Zahnradabdeckung und Dämpfer alle an `achse_x` hängen. Lenkhebel rechts ↔ Dämpfer 2,00 mm, ↔ UBEC 20,25 mm; links ↔ XT60 1,00 mm, ↔ Vorderachsgetriebe 7,80 mm. Oberdeck ↔ Zahnradabdeckung 1,00 mm, Mittelstütze ↔ Regler 1,00 mm.
   - **Befund und Korrektur:** Motor, Regler und UBEC wandern mit der Hinterachse um 7 mm nach hinten; die volle Plattenbreite rechts (`gp_rechts_vorne_x`, vor dem UBEC) endet dann bei X 78. Mit fest 16 Rasterspalten lag die Spalte X 80 außerhalb: Bohrung (80 / −69) ging ins Leere, (80 / −59) hatte nur 3,0 mm Randabstand. `raster_nx` ist jetzt aus dem Umriss abgeleitet (siehe [Elektronik-Raster](#elektronik-raster-mech-cha-009)). Danach bei 280 mm: 104 Bohrungen (15 Spalten), Randabstand min. **5,00 mm**, Lochabstand min. 9,00 mm, Rasterlöcher unter Empfänger 12, Regler 15, UBEC 15.
4. Skelett zurück auf `radstand` = 266 mm, Zeitleiste ohne Fehler, gespeichert als **v12** (Maße gleich v10). Ableitung erneut aktualisiert: Referenz auf v12, Zeitleiste ohne Fehler, wieder 107 Bohrungen, 344 × 144 mm, alle Werte wie im Startzustand. Die Skelett-Exporte bleiben aus v10 (Geometrie unverändert).

![Parametertest mit radstand 280 mm](images/grundplatte-parametertest-280.png)

*Parametertest bei `radstand` 280 mm, von oben (vorne ist unten). Platte, Oberdeck, Fußflächen (magenta) und Lochbilder folgen den Achsen.*

**Ersatztest mit den eigenen Parametern** (Durchlauf 1, vor Version 9, danach zurückgesetzt): `gp_ueberstand` 12, `ql_dx` 20, `od_getriebe_dx` 15, `raster_nx` 15, `akku_anschlag_l` 50, `gp_getriebe_y` 16, `ms_loch_dy` 4,5 mm gleichzeitig gesetzt: Zeitleiste ohne Fehler, alle Teile und Löcher folgen. (`raster_nx` ist inzwischen abgeleitet.)

Alle Lagen hängen über Ausdrücke an den abgeleiteten Skelett-Parametern (`achse_x`, `platte_x_*`, `platte_links`, `platte_rechts`, `servo_*`, `motor_*`, `xt60_*`, `ubec_*`, `regler_*`, `akku_*`, `teilung_*`, `antrieb_z`, `abdeckung_r`, `kardan_becher_d`, `daempfer_*`), siehe Parameterliste.

## Steifigkeit (MECH-CHA-016)

Wird am Prototyp gemessen: Grundplatte, Oberdeck und Mittelstütze verschraubt, an beiden Achsen aufgelegt, 20 N in der Mitte, Durchbiegung ≤ 2 mm. Eine statische Simulation lässt sich über den Fusion-MCP-Server bzw. die API nicht aufsetzen und auswerten.

**Handabschätzung** (Balken auf zwei Stützen, Stützweite 266 mm, Last 20 N in der Mitte, δ = F·L³ / (48·E·I), PETG E ≈ 2000 MPa, 100 % Füllung):

| Annahme | Flächenmoment I | Durchbiegung |
|---|---|---|
| Grundplatte allein (144 × 4 mm) | 768 mm⁴ | ≈ 5,1 mm |
| Grundplatte und Oberdeck (20 × 3 mm, 45 mm⁴) biegen getrennt, ohne Kopplung | 813 mm⁴ | ≈ 4,8 mm |
| Grundplatte und Oberdeck starr gekoppelt (Abstand der Mittelebenen 58,7 mm) | ≈ 188 000 mm⁴ | ≈ 0,02 mm |

Das Oberdeck allein ist schwach (45 mm⁴), die Steifigkeit entsteht nur, wenn Getriebegehäuse und Mittelstütze Platte und Oberdeck schubsteif verbinden (Rahmenwirkung). Die echte Durchbiegung liegt zwischen den beiden Grenzen und hängt vor allem an den Verbindungen; deshalb gezielt messen. Ist sie zu groß, sind die Hebel: Oberdeck dicker (`od_staerke`) oder rechts über Motor und Regler breiter (`od_halb_b`; berührt die Entscheidung „Elektronik von oben frei“ und braucht eine Rückfrage beim Nutzer) und steife Auflagen an den Getriebegehäusen.

## Erleichterungstaschen (MECH-CHA-019, KANN)

Vier durchgehende Taschen an den Achsen zwischen den Querlenkerböcken jeder Seite: X −143…−123 bzw. 123…143, Y ±27…±43, Eckradius 2 mm (`gp_tasche_rand`, `gp_tasche_r`). Dort sitzt kein Lochbild und keine Auflage; darüber liegen nur Querlenker und Antriebswellen. Sie sparen 6,4 g und bringen die Masse unter 250 g (MECH-CHA-017); **ohne sie wäre MECH-CHA-017 nicht erfüllt** (ca. 254 g). Weitere Taschen (z. B. unter dem Akku oder der Zahnradabdeckung) sind bewusst nicht vorgesehen: unter dem Akku wegen des LiPo-Schutzes, unter der Abdeckung wegen des Schutzes vor drehenden Teilen.

## Vorgaben an die nächsten Baugruppen

- **Hinterachse:**
  - Getriebegehäuse auf das Lochbild 4 × M3 (−152 / −114, Y ±18), Gewindeeinsätze im Gehäuse.
  - Auflagen für das Oberdeck bis **Z 84,2 mm** an (−115 / ±5), je ein Gewindeeinsatz.
  - Querlenkerböcke auf die Fußflächen X −156…−146 und −120…−110, Y ±27…±43, je 2 × M3 von unten. Das Gehäuse bleibt bis Z 44 innerhalb Y ±24,86 (keine Überdeckung der Fußflächen), damit jeder Bock von unten lösbar ist, ohne Gehäuse oder Oberdeck abzunehmen (MECH-CHA-018). Die Stützweite der Querlenkerachse ist 36 mm; mehr erlaubt das Fenster vor der Achse nicht (Wellenraum bis X −122,7, Zahnradabdeckung ab −109).
  - Dämpferbrücke auf dem Getriebegehäuse, kein Lochbild in der Grundplatte.
- **Vorderachse und Lenkung:**
  - Getriebegehäuse auf (114 / 152, Y ±18), Oberdeck-Auflage bis Z 84,2 an (115 / ±5).
  - Querlenkerböcke auf X 110…120 und 146…156, Y ±27…±43.
  - Servohalter auf 4 × M3 (53,2 / −27,1 und −17,1; 85 und 95 / −37,2).
  - Lagerböcke des Lenkhebelsystems links auf (94,5 / 30,5; 39,5), Fußfläche X 90,5…98,5, rechts auf (92,75 / −46,5; −55,5), Fußfläche X 88,75…96,75 (2 mm vor der vereinfachten Dämpfer-Hülle). Die echte Dämpferlage (schräg, Kugelköpfe) klärt die Vorderachse; der Bock darf nicht über X 97,75 hinaus nach vorne wachsen.
- **Mittelantrieb:**
  - Motorhalter auf 3 × M3 (−71 / −40,5; −28,5; −16,5), mit Zahnspiel-Einstellung im Halter (das Lochbild ist fest). Bei Ritzel 16Z wandert `motor_y` auf −25,8 mm und das Lochbild mit (Abstand zum Raster dann 11,2 mm).
  - Die Zahnradabdeckung wird am Motorhalter befestigt (MECH-CHA-012), Ritzelwechsel ohne Abnehmen des Oberdecks (z. B. seitlicher Deckel).
  - **Platz für den Querlenkerbock hinten rechts vor der Achse:** Die Zahnradabdeckung reicht im Bereich Y −43…−27 unterhalb Z 44 nicht weiter nach hinten als X −109 (die Fußfläche endet bei X −110; heute 1,00 mm Luft, im Parametertest bei 280 mm unverändert).
  - Es gibt **kein Mittelschott** (Stückliste Pos. 47 entfällt); die Mittelstütze gehört zur Grundplatte.
- **Elektronikhalter:**
  - Adapterplatten auf dem Raster 10 mm (Senkkopf von unten in Gewindeeinsätze der Platten). **Befestigen lassen sie sich nur auf den drei Reihen Y −69 / −59 / −49** (Spalten X −70…80); weiter zur Mitte gibt es kein Raster (Motor, Servohalter, Mittelstütze). Platten, die nach innen über Y −49 hinausreichen, kragen frei aus und müssen das selbst tragen. Adapterplatten im Stoßbereich (X −15…15) dürfen nicht über Y −31 hinaus zur Mitte reichen (Mittelstütze).
  - Die Adapterplatten im Stoßbereich (Spalten X −10 / 0 / 10) klemmen zusätzlich den Stoß.
  - Der vordere Pfosten des Akkubügels ersetzt den vorderen Anschlag (Entscheidung 2026-10-28): Lochbild (74 / 54; 63), Anschlagfläche bei X 70 mm (1 mm Spiel), Kanten zum Akku R ≥ 1 mm. Der hintere Pfosten sitzt auf (−84 / 30,5; 39,5).
- **Karosseriehalter und Rammschutz:** auf der Verlängerung vorne und hinten, Rammschutz (∓164,5 / ±8), Karosseriehalter (∓164,5 / ±22), je 2 × M3 von unten.
- **Messpunkte bei Lieferung:** Gewindeeinsätze MP-JET M3 kurz (Bohrung, Länge) für Anschläge und Mittelstütze.
- **Phase 3:** Bohr-NC, Senk- und Taschen-Operation, CAM-Simulation der Aluvariante (siehe [Fräsbarkeit](#fräsbarkeit-mech-cha-004-mech-cha-005)).

## Parameterliste (neue Benutzerparameter)

Alle Skelett-Parameter sind abgeleitet (siehe `docs/skelett.md`). Neu in diesem Design sind 95 Benutzerparameter mit Präfix `gp_`, `od_`, `ms_`, `raster_`, `akku_`, `stoss_`, `ql_` oder `lk_`, jeder mit Kommentar (Prüfskript: 0 ohne Kommentar, 0 ohne Präfix). Die Parameter der Fassung 1, die nur zum alten Layout gehörten (z. B. `gp_ms_*` Mittelschott, `stoss_schraube_*`, `stoss_mutter_*`, `gp_qlb_*`), sind entfernt. Werte im Startzustand, direkt aus Fusion ausgelesen (in den Ausdrücken ohne `_Ref`):

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `gp_bohrung` | `3.2 mm` | 3,20 mm | Bohrung M3 mit Spiel für Druck (+0,2) und Alu (MECH-CHA-008, -013) |
| `gp_senkung_d` | `6.9 mm` | 6,90 mm | Senkung 90° für M3 ISO 10642 (dk max. 6,72 mm), Kopf bündig (MECH-CHA-008) |
| `gp_senkung_t` | `( gp_senkung_d - gp_bohrung ) / 2` | 1,85 mm | abgeleitet: Tiefe der 90°-Senkung |
| `gp_rand` | `5 mm` | 5,00 mm | Randabstand Lochmitte min. (MECH-CHA-008) |
| `gp_lochabstand` | `8 mm` | 8,00 mm | Lochabstand Mitte-Mitte min. (MECH-CHA-008); Prüfgrenze |
| `gp_wand_min` | `1.2 mm` | 1,20 mm | Mindestwand seitliche Stege und Wände (MECH-CHA-013); Prüfgrenze |
| `gp_paar_d` | `gp_senkung_d + 2.1 mm` | 9,00 mm | abgeleitet: Lochabstand in Zweierlochbildern (Steg zwischen den Senkungen 2,1 mm >= gp_wand_min) |
| `gp_kantenradius` | `2 mm` | 2,00 mm | Grundplatte: Radius aller senkrechten Kanten, fräsgerecht >= 1,5 mm (MECH-CHA-005) |
| `gp_fuss_rand` | `3 mm` | 3,00 mm | Grundplatte: Plattenrand außerhalb der reservierten Fußflächen, vorläufig |
| `gp_ueberstand` | `15 mm` | 15,00 mm | Grundplatte: Verlängerung vorne und hinten über die Getriebe hinaus (Rammschutz, Karosseriehalter), vorläufig 12-15 mm (MECH-CHA-002) |
| `gp_ende_x` | `platte_x_vorne + gp_ueberstand` | 172,00 mm | abgeleitet: Plattenende vorne (hinten gespiegelt, platte_x_hinten symmetrisch) |
| `gp_rechts_vorne_x` | `ubec_x + ubec_l / 2 + 2.5 mm` | 85,00 mm | abgeleitet: Ende der vollen Breite rechts (vor dem UBEC); weiter vorne Abstand Radraum vorne rechts < 5 mm |
| `stoss_x1` | `teilung_x - teilung_ueberlappung / 2` | −15,00 mm | Stoß: abgeleitet, hintere Stufe |
| `stoss_x2` | `teilung_x + teilung_ueberlappung / 2` | 15,00 mm | Stoß: abgeleitet, vordere Stufe |
| `stoss_z` | `bodenfreiheit + plattenstaerke / 2` | 27,00 mm | Stoß: abgeleitet, Höhe der Halbüberlappung |
| `stoss_spiel` | `0.2 mm` | 0,20 mm | Stoß: Fügespiel an den senkrechten Stufenflächen der Druckteile, nur Druck (Review 1 Befund 2, Nutzerentscheidung 2026-10-31; Randabstand dort >= 4,8 mm) |
| `raster_teilung` | `10 mm` | 10,00 mm | Elektronik-Raster: Teilung (MECH-FZG-009, MECH-CHA-009) |
| `raster_x0` | `teilung_x - 7 * raster_teilung` | −70,00 mm | Elektronik-Raster: erste Spalte unter dem Empfänger; Takt auf teilung_x, damit die Stoßstufen 5 mm Abstand haben |
| `raster_nx` | `floor(( gp_rechts_vorne_x - gp_rand - raster_x0 ) / raster_teilung) + 1` | 16 | abgeleitet: Spalten ab X -70 bis zur vollen Breite rechts vor dem UBEC mit gp_rand (Startzustand 16, X -70...80); folgt dem Skelett (Parametertest Review 1) |
| `raster_y0` | `-platte_rechts + gp_rand` | −69,00 mm | Elektronik-Raster: erste Reihe am rechten Rand |
| `raster_ny` | `3` | 3 | Elektronik-Raster: Reihen Y -69/-59/-49; Reihe -39 entfällt (Motor bis Y -46,5, Servohalter) |
| `gp_getriebe_dx` | `19 mm` | 19,00 mm | Lochbild Achsgetriebe: Löcher vor und hinter der Achse, Abstand zur Achse, vorläufig (5 mm innerhalb der Getriebe-Hülle) |
| `gp_getriebe_y` | `18 mm` | 18,00 mm | Lochbild Achsgetriebe: quer +-, vorläufig (Hülle +-24,86 mm) |
| `ql_dx` | `18 mm` | 18,00 mm | Querlenkerbock: Mitte Fußfläche vor bzw. hinter der Achse, vorläufig (Fenster zwischen Wellenraum und Zahnradabdeckung/Dämpfer); Anlenkachse parallel X angenommen |
| `ql_y` | `35 mm` | 35,00 mm | Querlenkerbock: Mitte Fußfläche quer, vorläufig, neben dem Getriebe (Hülle +-24,86) |
| `ql_l` | `10 mm` | 10,00 mm | Querlenkerbock: Fußfläche längs, vorläufig |
| `ql_b` | `16 mm` | 16,00 mm | Querlenkerbock: Fußfläche quer, vorläufig |
| `ql_h` | `15 mm` | 15,00 mm | Querlenkerbock: Höhe des reservierten Quaders (MECH-CHA-020: 15 mm, unter den Diff-Bechern ab Z 46,3) |
| `lk_l` | `8 mm` | 8,00 mm | Lagerbock Lenkhebelsystem: Fußfläche längs, vorläufig |
| `lk_b` | `16 mm` | 16,00 mm | Lagerbock Lenkhebelsystem: Fußfläche quer, vorläufig |
| `lk_h` | `15 mm` | 15,00 mm | Lagerbock Lenkhebelsystem: Höhe des reservierten Quaders, vorläufig |
| `lk_x` | `xt60_x + xt60_b / 2 + 1 mm + lk_l / 2` | 94,50 mm | Lagerbock Lenkhebel links: Mitte längs, vorläufig, 1 mm vor dem XT60 und hinter Vorderachsgetriebe/Dämpfer |
| `lk_x_rechts` | `achse_x - daempfer_dx - daempfer_d / 2 - 2 mm - lk_l / 2` | 92,75 mm | Lagerbock Lenkhebel rechts: Mitte längs, vorläufig, 2 mm vor der Dämpfer-Hülle vorne rechts (Review 1, >= od_luft); links bindet das XT60 (lk_x) |
| `lk_y_links` | `35 mm` | 35,00 mm | Lagerbock Lenkhebel links: Mitte quer, vorläufig (zwischen Getriebe-Hülle 24,86 und Dämpfer 44,75) |
| `lk_y_rechts` | `51 mm` | 51,00 mm | Lagerbock Lenkhebel rechts: Mitte quer (Betrag, Y negativ), vorläufig, außerhalb Servo und Servohalter |
| `gp_sh_x_hinten` | `servo_x - servo_l / 2 - 4 mm` | 53,20 mm | Lochbild Servohalter: Reihe hinter dem Servo, vorläufig |
| `gp_sh_dy` | `5 mm` | 5,00 mm | Lochbild Servohalter: hinten quer zur Servomitte +-, vorläufig |
| `gp_sh_y_aussen` | `servo_y - servo_b / 2 - 5 mm` | −37,20 mm | Lochbild Servohalter: Reihe rechts neben dem Servo, vorläufig |
| `gp_sh_x_vorne` | `servo_x + servo_l / 2 - 2.5 mm` | 95,00 mm | Lochbild Servohalter: vorderes Loch rechts, vorläufig |
| `gp_sh_dx` | `10 mm` | 10,00 mm | Lochbild Servohalter: Abstand der Löcher rechts längs, vorläufig |
| `gp_mh_dx` | `4 mm` | 4,00 mm | Lochbild Motorhalter: vor dem Motorflansch, vorläufig |
| `gp_mh_x` | `motor_flansch_x + gp_mh_dx` | −71,00 mm | abgeleitet: Lochreihe Motorhalter längs |
| `gp_mh_dy` | `12 mm` | 12,00 mm | Lochbild Motorhalter: quer zur Motorachse +-, vorläufig (3 Löcher) |
| `gp_ende_loch_x` | `gp_ende_x - gp_ueberstand / 2` | 164,50 mm | abgeleitet: Lochreihe Rammschutz und Karosseriehalter auf der Verlängerung |
| `gp_ramm_y` | `8 mm` | 8,00 mm | Lochbild Rammschutz vorne/hinten: quer +-, vorläufig |
| `gp_karo_y` | `22 mm` | 22,00 mm | Lochbild Karosseriehalter vorne/hinten: quer +-, vorläufig |
| `akku_spiel` | `1 mm` | 1,00 mm | Akkuschacht: Spiel je Seite (MECH-CHA-010) |
| `akku_anschlag_b` | `8 mm` | 8,00 mm | Akkuanschlag: Breite (Einsatz 4 mm + 2 x 2 mm Wand), vorläufig |
| `akku_anschlag_h` | `10 mm` | 10,00 mm | Akkuanschlag: Höhe über der Grundplatte, vorläufig |
| `akku_anschlag_r` | `1.5 mm` | 1,50 mm | Akkuanschlag: Kantenradius zum Akku (LiPo-Schutz, >= 1 mm) |
| `akku_einsatz_d` | `4 mm` | 4,00 mm | Gewindeeinsatz M3 kurz: Bohrung, vorläufig (Vergleichsteil CNC Kitchen M3 kurz 4,0 mm), am Teil MP-JET 1903 messen |
| `akku_einsatz_t` | `6 mm` | 6,00 mm | Gewindeeinsatz M3 kurz: Bohrtiefe, vorläufig (Einsatz ca. 3 mm + Platz für das Schraubenende), am Teil messen |
| `akku_anschlag_l` | `60 mm` | 60,00 mm | Akkuanschlag links/rechts: Länge, vorläufig |
| `akku_anschlag_dx` | `20 mm` | 20,00 mm | Akkuanschlag links/rechts: Lochabstand längs (3 Löcher, mittleres bei teilung_x im Stoß) |
| `akku_anschlag_x` | `teilung_x` | 0,00 mm | Akkuanschlag links/rechts: Mitte längs = Stoß (mittleres Loch klemmt die Überlappung) |
| `akku_anschlag_links_y` | `akku_y_innen + akku_b + akku_spiel + akku_anschlag_b / 2` | 63,00 mm | abgeleitet: Akkuanschlag links (außen) Mitte quer |
| `akku_anschlag_rechts_y` | `akku_y_innen - akku_spiel - akku_anschlag_b / 2` | 7,00 mm | abgeleitet: Akkuanschlag rechts (innen) Mitte quer, unter der Kardanwelle (Z 29...39 < 46,6) |
| `akku_anschlag_vh_l` | `20 mm` | 20,00 mm | Akkuanschlag vorne/hinten: Länge quer, vorläufig |
| `akku_anschlag_vh_dy` | `gp_paar_d / 2` | 4,50 mm | Akkuanschlag vorne/hinten: Löcher quer +- |
| `akku_anschlag_vorne_x` | `akku_x + akku_l / 2 + akku_spiel + akku_anschlag_b / 2` | 74,00 mm | abgeleitet: Akkuanschlag vorne (= Pfosten Akkubügel vorne) Mitte längs |
| `akku_anschlag_vorne_y` | `xt60_y + xt60_l / 2 + 2.5 mm + akku_anschlag_vh_l / 2` | 58,50 mm | abgeleitet: Akkuanschlag vorne Mitte quer, links neben dem XT60 (2,5 mm Luft) |
| `akku_anschlag_hinten_x` | `akku_x - akku_l / 2 - akku_spiel - akku_anschlag_b / 2` | −74,00 mm | abgeleitet: Akkuanschlag hinten Mitte längs |
| `akku_anschlag_hinten_y` | `akku_y` | 35,00 mm | Akkuanschlag hinten: Mitte quer = Akkumitte |
| `akku_pfosten_dx` | `10 mm` | 10,00 mm | Lochbild Akkubügel-Pfosten hinten: hinter den Löchern des hinteren Anschlags; vorne gemeinsam mit dem Anschlag vorne (Entscheidung 2026-10-28) |
| `akku_pfosten_x` | `akku_anschlag_hinten_x - akku_pfosten_dx` | −84,00 mm | abgeleitet: Lochbild Akkubügel-Pfosten hinten längs |
| `ms_x` | `teilung_x` | 0,00 mm | Mittelstütze: Mitte längs = Stoß (MECH-CHA-021) |
| `ms_l` | `teilung_ueberlappung` | 30,00 mm | Mittelstütze: Fuß längs = Überlappung des Stoßes |
| `ms_y_innen` | `-( kardan_becher_d / 2 + 1 mm )` | −11,00 mm | abgeleitet: Mittelstütze Seite zur Kardanwelle (1 mm Abstand zur Becher-Hülle) |
| `ms_y_aussen` | `regler_y + regler_b / 2 + 1 mm` | −31,00 mm | abgeleitet: Mittelstütze Seite zum Regler (1 mm Abstand) |
| `ms_y_mitte` | `( ms_y_innen + ms_y_aussen ) / 2` | −21,00 mm | abgeleitet: Mittelstütze Mitte quer |
| `ms_fuss_h` | `8 mm` | 8,00 mm | Mittelstütze: Höhe Fuß (Einsätze von unten), vorläufig |
| `ms_kopf_h` | `8 mm` | 8,00 mm | Mittelstütze: Höhe Kopf (Einsätze von oben), vorläufig |
| `ms_kopf_l` | `20 mm` | 20,00 mm | Mittelstütze: Kopf längs, vorläufig |
| `ms_steg_b` | `8 mm` | 8,00 mm | Mittelstütze: Steg längs, vorläufig |
| `ms_r` | `2 mm` | 2,00 mm | Mittelstütze: Radius der Innenecken des Profils |
| `ms_loch_dx` | `teilung_ueberlappung / 2 - gp_rand` | 10,00 mm | abgeleitet: Mittelstütze Löcher unten längs +- (im Stoß, gp_rand zur Stufe) |
| `ms_loch_dy` | `5 mm` | 5,00 mm | Mittelstütze: Löcher quer +- zur Mitte (unten und oben) |
| `od_staerke` | `3 mm` | 3,00 mm | Oberdeck: Dicke, vorläufig (wie 1:10-Oberdecks 2,5-3 mm) (MECH-CHA-006) |
| `od_luft` | `1 mm` | 1,00 mm | Oberdeck: Mindestabstand zu den Hüllkörpern (MECH-CHA-011) |
| `od_z` | `antrieb_z + abdeckung_r + od_luft` | 84,20 mm | abgeleitet: Unterkante Oberdeck = Oberkante Zahnradabdeckung + Luft; Vorgabe Auflagehöhe für Getriebegehäuse und Mittelstütze |
| `od_halb_b` | `akku_y_innen - 2 mm` | 10,00 mm | Oberdeck: halbe Breite, 2 mm Abstand zum Akku-Entnahmeweg |
| `od_getriebe_dx` | `18 mm` | 18,00 mm | Oberdeck: Befestigung auf den Achsgetrieben, Abstand zur Achse nach innen |
| `od_loch_y` | `5 mm` | 5,00 mm | Oberdeck: Befestigungslöcher auf den Getrieben quer +- |
| `od_ueberstand` | `7 mm` | 7,00 mm | Oberdeck: Überstand über die äußeren Löcher |
| `od_eckradius` | `5 mm` | 5,00 mm | Oberdeck: Eckradius außen |
| `od_lasche_r` | `3 mm` | 3,00 mm | Oberdeck: Radius an der Lasche zur Mittelstütze (fräsgerecht >= 1,5 mm) |
| `gp_achse_y` | `ql_y + ql_b / 2 + gp_fuss_rand` | 46,00 mm | abgeleitet: halbe Plattenbreite an den Achsen (Querlenkerböcke neben dem Getriebe) |
| `gp_mitte_hinten_x` | `akku_pfosten_x - gp_rand - 1 mm` | −90,00 mm | abgeleitet: Beginn breiter Mittelteil hinten (hinter dem Lochbild Bügelpfosten hinten) |
| `gp_zugabe_links` | `akku_spiel + akku_anschlag_b + 3 mm` | 12,00 mm | Grundplatte: Verbreiterung links neben dem Akku für Anschlag und Bügelpfosten (Entscheidung 2026-10-27) |
| `gp_links_breit` | `platte_links + gp_zugabe_links` | 70,00 mm | abgeleitet: Außenkante links im Akkubereich |
| `gp_links_vorne_x` | `akku_anschlag_vorne_x + akku_anschlag_b / 2 + 4 mm` | 82,00 mm | abgeleitet: Vorderkante der Verbreiterung links (vor dem vorderen Anschlag, Abstand Radraum vorne links >= 5 mm) |
| `gp_rechts_lk` | `lk_y_rechts + lk_b / 2 + gp_fuss_rand` | 62,00 mm | abgeleitet: Plattenkante rechts am Lagerbock Lenkhebel rechts (Betrag) |
| `gp_lk_ende_x` | `lk_x_rechts + lk_l / 2 + gp_fuss_rand` | 99,75 mm | abgeleitet: Ende des Absatzes rechts am Lagerbock Lenkhebel rechts |
| `gp_tasche_rand` | `3 mm` | 3,00 mm | Erleichterungstasche: Abstand zu den Fußflächen der Querlenkerböcke (MECH-CHA-019) |
| `gp_tasche_r` | `2 mm` | 2,00 mm | Erleichterungstasche: Eckradius, fräsgerecht >= 1,5 mm (MECH-CHA-019) |

## Probemontage (MECH-CHA-015, vom Nutzer auszufüllen)

Teile in PETG drucken, Einsätze in Anschläge und Mittelstütze einschmelzen und mit den vorhandenen Zukauf- und Bausatzteilen montieren.

| Prüfpunkt | Soll | Ergebnis |
|---|---|---|
| Zungen passen ohne Kraft in die Stufen des anderen Teils (Fügespiel 0,2 mm je Stufe, siehe [Stoß](#stoß-mech-cha-003)); 15 Stoßbohrungen fluchten | ja | |
| Spalt an den Stufen nach dem Verschrauben (Fühlerlehre, Ober- und Unterseite) | ≈ 0,2 mm, kein Klemmen | |
| Stoß verschraubt (Mittelstütze 4 × M3 × 8, Anschläge links/rechts je mittleres Loch), Versatz an den Stufen | ≤ 0,3 mm | |
| Stoß ohne Adapterplatten der Elektronik: klafft er unter dem Akku oder am linken Rand? (Anschläge links/rechts sind tragend) | kein Spalt | |
| Unterseite im Stoß flach, Schraubenköpfe bündig | ja | |
| Anschläge und Mittelstütze liegen nach dem Einschmelzen der Einsätze plan auf | ja | |
| Einsätze in der Mittelstütze (waagerecht gedruckte Löcher) sitzen gerade und halten beim Anziehen der M3-Schrauben | ja | |
| Akku sitzt im Schacht zwischen den vier Anschlägen | Spiel ≈ 1 mm je Seite | |
| Akku lässt sich nach oben entnehmen | ohne Werkzeug | |
| Oberdeck liegt auf der Mittelstütze auf (Getriebegehäuse folgen mit den Achsen) | ja | |
| Rasterbohrungen und Lochbilder treffen M3-Schrauben ohne Nacharbeit | ja | |
| Slicer: Teile liegen ohne Skalierung im Bauraum, keine Stützen nötig | ja | |
| Masse gewogen (Grundplatte + Oberdeck + Mittelstütze + Anschläge) | ≤ 250 g | |
| Durchbiegung unter 20 N in der Mitte, Auflage an beiden Achsen (MECH-CHA-016) | ≤ 2 mm | |

Fotos: in `docs/images/` ablegen und hier einbinden.

## Historie

- **Fassung 1** (2026-10-27/28, PR #6, Commit `0a0ae17`, Design-Version 7, Skelett v6): auf dem Skelett mit dem Layout des früheren Spenders TLR 22X-4. Grundplatte 335,5 × 166 mm, Stoß bei X 35…65 mm mit 6 Stoßschrauben und Stoppmuttern, Oberdeck 30 mm breit auf Hinterachsgetriebe, Mittelschott und Vorderachsgetriebe (Unterkante Z 84,17), Querlenkerböcke unter den Getriebe-Hüllen, 105 Bohrungen. Wurde nach dem Plattformwechsel auf den Tamiya TT-02B (2026-10-28) verworfen.
- **Fassung 2** (2026-10-31, Design-Versionen 8 und 9): Neuaufbau auf dem TT-02B-Skelett v10 (dieses Dokument). Neu: Verlängerung vorne und hinten, Querlenkerböcke neben den Getrieben, Mittelstütze statt Mittelschott, Lochbild Lenkhebelsystem, Stoß ohne Muttern, Erleichterungstaschen.
- **Review 1** (2026-10-31, Design-Version 10, Skelett v11/v12): Parametertest mit dem Skelett (`radstand` 280 mm) nachgeholt; dabei `raster_nx` aus dem Umriss abgeleitet. Lenkhebel-Lagerbock rechts mit eigener Lage `lk_x_rechts` 1,75 mm nach hinten (2 mm statt 0,25 mm zur Dämpfer-Hülle). Doku: Stoß (tragende Anschläge, offenes Fügespiel), Steifigkeitsabschätzung, Vorgaben Mittelantrieb und Elektronikhalter, Probemontage-Liste.
- **Fügespiel** (2026-10-31, Design-Version 11, Nutzerentscheidung nach Review 1): `stoss_spiel` 0,2 mm an den Stufenflächen der Druckteile, Randabstand dort ≥ 4,8 mm (Ausnahme MECH-CHA-008). Bild „Mit Skelett“ erneuert (Lenkhebel-Lagerbock rechts in neuer Lage), Detailbild Stoß ergänzt.

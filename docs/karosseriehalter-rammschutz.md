# Karosseriehalter und Rammschutz

- **Anforderungen:** `docs/anforderungen/karosseriehalter-rammschutz.md` (Kürzel KRS)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-karosseriehalter-rammschutz“, **Version 4**, abgeleitet von „open-rc-car-skelett“ **v16** (maßgleich mit v14), „open-rc-car-grundplatte“ **v12**, „open-rc-car-vorderachse“ **v8** und „open-rc-car-hinterachse“ **v14** (`documentReferences` geprüft). Version 1 ist ein leerer Anfangsstand, Version 2 ein Zwischenstand vor der Bewegungsprüfung, Version 3 der Stand vor der Korrektur des Hüllenendes hinten (Teile gleich wie Version 4).
- **Exporte (alle aus Version 4):** `cad/fusion/karosseriehalter-rammschutz.f3d`, `cad/step/karosseriehalter-rammschutz.step` (nur die 6 Druckteil-Komponenten, 8 Körper), 6 STL in `print/stl/`
- **Stand:** 2026-11-13

Vorne und hinten sitzt je ein **Rammschutz** aus einem steifen **Träger** (Prusament PC, PETG für den Test) und einem **TPU-Puffer** davor. Der Träger steht auf dem Plattenende, liegt mit einer Lippe (vorne) bzw. mit dem Balken (hinten) an der Plattenstirn an und ist über alle 4 Löcher der Lochreihe verschraubt. Der Puffer ist ein Hohlprofil mit 5 mm Federweg vor dem Balken; unten läuft er als 45°-Anfahrschräge aus und deckt die Stirnkante der Grundplatte ab. Auf den Trägern stehen je zwei **Karosseriepfosten** mit Lochraster für die Klammern der Lexan-Karosserie **Neo Scorcher**. Eine vereinfachte **Karosseriehülle** dient der Freiraumprüfung. Alle Maße der Karosserie und der Klammern sind **vorläufig** (keine Quelle; die Bauanleitung ließ sich nicht auswerten), siehe [Messpunkte](#messpunkte-bei-lieferung).

![Isometrisch](images/karosseriehalter-rammschutz-iso.png)

*Von vorne rechts oben, Konstruktionslage. Gelb: Träger, schwarz: TPU-Puffer, blau (dunkel): Karosseriepfosten. Dazu Grundplatte, Vorder- und Hinterachse, Mittelantrieb und die Hüllkörper des Skeletts.*

![Mit Karosseriehülle](images/karosseriehalter-rammschutz-iso-huelle.png)

*Mit der vorläufigen Karosseriehülle (grau). Die Pfosten ragen durch die Befestigungslöcher.*

![Von vorne](images/karosseriehalter-rammschutz-vorne.png)

*Von vorne (orthografisch): Puffer ±61 mm deckt die Dämpfer (±58,8 mm) ab, die Pfosten stehen bei Y ±22.*

![Von hinten](images/karosseriehalter-rammschutz-hinten.png)

*Von hinten: Puffer ±78 mm deckt die Dämpfer (±77,2 mm) ab.*

![Von oben](images/karosseriehalter-rammschutz-oben.png)

*Von oben, vorne ist oben.*

![Seitlich mit Karosseriehülle](images/karosseriehalter-rammschutz-seitlich-huelle.png)

*Von links mit der vorläufigen Karosseriehülle, vorne ist rechts.*

## Ergebnis

| Teil | Komponente / Körper | Hüllquader X × Y × Z (mm) | Lage X / Y / Z (mm) | Masse PETG bzw. TPU, 100 % | Masse PC | Datei |
|---|---|---|---|---|---|---|
| Träger vorne | `rammschutz-traeger-vorne` / `traeger-vorne` | 19,3 × 122,0 × 45,0 | 165,5…184,8 / ±61,0 / 25,0…70,0 | 43,2 g | 40,8 g | `print/stl/rammschutz-traeger-vorne.stl` |
| Träger hinten | `rammschutz-traeger-hinten` / `traeger-hinten` | 15,3 × 156,0 × 55,0 | −180,8…−165,5 / ±78,0 / 25,0…80,0 | 55,8 g | 52,8 g | `print/stl/rammschutz-traeger-hinten.stl` |
| Puffer vorne (TPU) | `rammschutz-puffer-vorne` / `puffer-vorne` | 17,5 × 122,0 × 47,0 | 174,3…191,8 / ±61,0 / 25,0…72,0 | 18,0 g | – | `print/stl/rammschutz-puffer-vorne.stl` |
| Puffer hinten (TPU) | `rammschutz-puffer-hinten` / `puffer-hinten` | 17,5 × 156,0 × 57,0 | −187,8…−170,3 / ±78,0 / 25,0…82,0 | 26,6 g | – | `print/stl/rammschutz-puffer-hinten.stl` |
| Karosseriepfosten vorne (2 ×) | `karosserie-pfosten-vorne` / `pfosten-vorne-links`, `-rechts` | 8 × 8 × 83,0 | 165,35…173,35 / ±18…±26 / 35,5…118,5 | je 6,4 g | je 6,1 g | `print/stl/karosserie-pfosten-vorne.stl` (2 × drucken) |
| Karosseriepfosten hinten (2 ×) | `karosserie-pfosten-hinten` / `pfosten-hinten-links`, `-rechts` | 8 × 8 × 94,0 | −173,35…−165,35 / ±18…±26 / 35,5…129,5 | je 7,3 g | je 6,9 g | `print/stl/karosserie-pfosten-hinten.stl` (2 × drucken) |
| **Summe Druckteile (8)** | | | | **171,0 g** (Soll ≤ 175 g, vom Nutzer angehoben am 2026-11-13) | 164,1 g mit TPU | |

Masse = Volumen aus Fusion × 1,27 g/cm³ (PETG), 1,20 g/cm³ (Prusament PC) bzw. 1,21 g/cm³ (TPU), 100 % Füllung als obere Grenze. Volumen: Träger 33,99 / 43,97 cm³, Puffer 14,84 / 22,01 cm³, Pfosten 5,05 / 5,75 cm³ je Stück.

Kein Druckteil: `karosserie-huelle` (vereinfachte Hülle der Lexan-Karosserie, Wand 0,8 mm, X −182…186, Y ±88, Z 40…150, alle Maße vorläufig).

## Aufbau in Fusion

- **Ableitungen** wie bei Vorder- und Hinterachse:
  - Vom Skelett (jetzt **v16**, maßgleich mit v14): alle 155 Favoriten-Parameter (in Fusion `<name>_Ref`, hier ohne `_Ref`), die 8 Bezugsebenen und alle Hüllkörper außer dem Skelett-Körper `chassis-grundplatte`.
  - Von der Grundplatte **v12**: `chassis-grundplatte` (Druck und Alu), `chassis-oberdeck`, `chassis-mittelstuetze`, die vier Akkuanschläge und `chassis-fussflaechen`.
  - Von der Vorderachse **v8** und der Hinterachse **v14** (nur für die Prüfung): alle eigenen Komponenten (`vorderachse-*`, `lenkung-*` außer der Skelett-Hülle `lenkung-servo`, `hinterachse-*`) in Konstruktionslage. Die Vorderachse ist bewusst auf v8 abgeleitet (in der Cloud gibt es eine v9, laut Nutzer unwichtig); die Referenz ist deshalb als „veraltet“ markiert.
- **Grundplatten-Schnittstellen als Kopie** (wie Vorder- und Hinterachse): Die Grundplatte hat keine Favoriten-Parameter. Die Lochreihe ist mit **derselben Formel** wie `gp_ende_loch_x` nachgebaut (`kr_gp_ueberstand`, `kr_gp_rand`, `kr_gp_db_dx`, `kr_gp_ende_db_abstand`, `kr_einsatz_d`), dazu `kr_ramm_y`, `kr_karo_y`, `kr_gp_halb_b` (Kommentar „Schnittstelle Grundplatte v12 … von Hand nachziehen“). Alle Lagen in X hängen damit an `achse_x` und `platte_x_vorne` des Skeletts. Die Lagen der Dämpfer und Querlenker aus Vorder- und Hinterachse sind als `kr_va_*`, `kr_ha_*` übernommen (gemessen über alle Stellungen).
- **Komponenten:** je Druckteil eine Komponente nach der Dateikonvention, die zwei gleichen Pfosten eines Endes als zwei Körper in einer Komponente. Druckausrichtung und Material in der Komponentenbeschreibung.
- **Körper:** voll bestimmte Skizzen, jede Ecke mit Abstand zum Skizzenursprung bemaßt (`abs(…)` der Parameter), Extrusion mit Startversatz und Ausdruck. Bohrungen, Einsätze und Taschen sind Schnitt-Extrusionen. Das Klammer-Lochraster ist eine Rechteckanordnung mit `kr_raster_n` Exemplaren im Abstand `kr_raster_t`. Die senkrechten Innenecken der Träger sind mit `kr_tr_r` verrundet. Die Puffer entstehen aus einem XZ-Profil (Deckel, Stoßwand, Schräge) mit symmetrischer Extrusion; die Kammer wird mit `2 × (halbe Breite − Wand)` herausgeschnitten, so bleiben die Seitenwände stehen.
- **Karosseriehülle:** Schnitt zweier Extrusionen (Seitenprofil in XZ, Draufsicht in XY), danach Schale 0,8 mm nach innen, alle nach unten zeigenden Flächen offen. Die Oberkante läuft an den Pfosten genau durch `kr_karo_z_v` bzw. `kr_karo_z_h`.
- **Prüfskripte:** 32 Skizzen in den eigenen Komponenten, alle voll bestimmt. Zeitleiste 80 Elemente ohne Fehler und Warnungen. 108 Benutzerparameter, alle mit Präfix `kr_` und Kommentar (37 „vorläufig“, 14 „Schnittstelle“). Feste Zahlen in Features gibt es nur als Verjüngungswinkel 0° und Tangentengewichtung 1 der Verrundung.

## Rammschutz (MECH-KRS-002)

### Träger

| | vorne | hinten | Parameter |
|---|---|---|---|
| Fuß auf der Platte | X 165,5…177,3, Y ±30 (ab X 170 ±35,5), Z 29…37 | X −177,3…−165,5, Y ±45, Z 29…37 | `kr_fuss_x0` = Brücke + `kr_db_luft`, `kr_fuss_h`, `kr_v_fuss_b`, `kr_v_lippe_*`, `kr_h_fuss_b` |
| Anlage an der Plattenstirn | Lippe X 177,3…181,3, Y ±35,5, Z 25…37 | Balken-Innenseite X −177,3, Z 25…80 | `kr_stirn_spiel` 0,3 mm |
| Flansch unter den Dämpfern | X 177,3…181,3, Y ±61, Z 25…30 | – (Dämpfer reichen hinten bis Z 18,8) | `kr_v_flansch_h` |
| Balken | X 181,3…184,8 (3,5 mm), Y ±61, Z 25…70 | X −180,8…−177,3 (3,5 mm), Y ±78, Z 25…80 | `kr_v_balken_*`, `kr_h_balken_*` |
| Mittelsteg (Pufferschrauben) | X 174,3…181,3, Y ±10, bis Z 70 | X −177,3…−170,3, Y ±10, bis Z 80 | `kr_steg_l`, `kr_steg_b` |
| Gewindeeinsätze von unten | (169,35 / ±8), Ø 4 × 6 | (−169,35 / ±8) | `kr_einsatz_d`, `kr_einsatz_t` |
| Durchgang Pfostenschraube | (169,35 / ±22), Ø 3,4, mit Tasche 8,4 × 8,4 × 1,5 und Freistichen Ø 3 | (−169,35 / ±22) | `kr_bohrung`, `kr_pf_*` |
| Gewindeeinsätze von oben (Puffer) | (177,8 / ±5,5) | (−173,8 / ±5,5) | `kr_pu_schraube_y` |

- **Lochmitten gemessen** (Zylinderflächen im Modell): Einsätze (169,35 / ±8,0) und (−169,35 / ±8,0), Durchgänge Ø 3,4 bei (±169,35 / ±22,0) = Lochbild der Grundplatte v12 (`gp_ende_loch_x`, `gp_ramm_y`, `gp_karo_y`).
- **Abstützung** (Hinweis aus dem Review von PR #13): Alle 8 Löcher eines Endes liegen auf einer X-Linie. Deshalb liegt der Träger vorne mit der Lippe, hinten mit dem Balken über die ganze Breite der Plattenstirn (Y ±35,5 bzw. ±46, Z 25…29) an und ist über alle 4 Löcher verschraubt: 2 × M3 × 8 in die Einsätze (±8), 2 × M3 × 20 durch den Träger in die Pfosten (±22). Stoßkräfte nach innen gehen als Druck in die Plattenstirn, Kippmomente über den Fuß auf die Plattenoberseite und die 4 Schrauben.
- **Dämpferbrücken nicht berührt:** Fuß 3,00 mm vor bzw. hinter den Brücken (Einsatzwand bis zur Fußkante 1,85 mm, `kr_fuss_wand` ≥ 1,2).
- **Taschen der Pfosten:** Der Pfosten (X 165,35…173,35) steht 0,15 mm über die Fußkante (165,5) hinaus; die Tasche ist deshalb zur Brückenseite offen und sichert den Pfosten auf drei Seiten gegen Verdrehen. Eine geschlossene Rückwand ginge nur mit weniger als 1,2 mm Wand oder auf Kosten der Luft zur Brücke.

### Puffer und Befestigung

![Schnitt vorne durch die Pufferschraube](images/karosseriehalter-rammschutz-schnitt-puffer.png)

*Schnitt bei Y = 5,5 mm (Achse der Pufferschraube), vorne, Blick von rechts. Unten die Grundplatte, links die Dämpferbrücke, dahinter ein Pfosten (blau). Weiß schraffiert der Träger mit Lippe an der Plattenstirn, Fuß und Mittelsteg mit dem Gewindeeinsatz (Bohrung von oben); grün schraffiert der TPU-Puffer: Deckel und Zunge liegen auf Balken und Steg, die Bohrung Ø 3,4 in der Zunge sitzt über dem Einsatz. Vorn die Kammer (schwarz, 5 mm) zwischen Balken und Stoßwand, unten die 45°-Schräge ab Z 25.*

![Schnitt hinten durch die Pufferschraube](images/karosseriehalter-rammschutz-schnitt-puffer-hinten.png)

*Wie oben, hinten (Blick von rechts, hinten ist links). Der Balken liegt direkt an der Plattenstirn an.*

- **Profil:** Deckel 2 mm über dem Balken und dem Mittelsteg, Stoßwand 2 mm, Schräge 2 mm (senkrecht gemessen), Seitenwände 2 mm. Die Kammer zwischen Balken und Stoßwand ist **5 mm** tief (`kr_pu_federweg`): So weit kann die Stoßwand einfedern, bevor sie am Balken anliegt.
- **Befestigung (formschlüssig + verschraubt):** Der Deckel liegt auf dem Balken, die Zunge (Y ±10) auf dem Mittelsteg. 2 × M3 × 8 Zylinderkopf mit Scheibe DIN 9021 von oben durch die Zunge in die Einsätze des Stegs. Keine Gewindeeinsätze im TPU. In X hält der Puffer formschlüssig am Balken (Deckel hinten bis zur Balken-Innenseite).
- Stoßfläche **vorne X 191,8**, **hinten X −187,8** (`kr_v_stoss_x`, `kr_h_stoss_x`).

## Schutzwirkung (MECH-KRS-003)

| Prüfung | vorne | hinten | Soll |
|---|---|---|---|
| Stoßfläche | X 191,8 | X −187,8 | |
| vorderstes/hinterstes übriges Teil (außer Räder) | Dämpfer X 180,3 (über alle 9 Stellungen), Platte 177,0, Pfosten 173,35, Hülle 186,0 | Platte −177,0, Dämpfer −176,2, Pfosten −173,35, Hülle −182,0 | |
| Vorlauf der Stoßfläche | **11,5 mm** (Dämpfer), 5,8 mm zur Hülle | **10,8 mm** (Platte), 5,8 mm zur Hülle | ≥ 5 mm |
| Pufferbreite | ±61,0 | ±78,0 | |
| Dämpfer in Y (über alle Stellungen) | ±36,8…±58,8 | ±43,5…±77,2 | innerhalb ✓ |
| Dämpferlaschen der Querlenker in Y | Auge bei ±52,0 (Lasche 8 mm breit) | Auge bei ±69,8 (Lasche 8 mm breit) | innerhalb ✓ |
| **Gesamtlänge** über beide Puffer | **379,6 mm** (`kr_gesamtlaenge`) | | ≤ 380 mm |

Die Enden der Karosseriehülle sind Annahmen (`kr_hu_x_v`, `kr_hu_x_h`): Sie sind so gewählt, dass die Karosserie die Puffer nicht verdeckt (5,8 mm hinter den Stoßflächen). Nach dem Messen der Karosserie wird das neu geprüft.

**Längenbudget:** Vorne müssen Balken und Puffer vor den Dämpfern (X 180,3 + 1 mm Luft) liegen, hinten hinter dem Plattenende (X 177 + 0,3 mm Spalt). Mit Federweg 5 mm und TPU-Wand 2 mm bleiben für beide Balken zusammen 7,4 mm bis 380 mm Gesamtlänge; gewählt sind je 3,5 mm (Reserve 0,4 mm). Deshalb sind die Balken dünn und hoch (siehe [Lasten](#lasten-mech-krs-008)).

## Unterfahrschutz (MECH-KRS-005)

- Tiefster Punkt der Puffer: **Z 25,0** (gemessen, Hüllquader), also nicht unter der Plattenunterseite.
- Schräge: zwei ebene Flächen je Puffer mit **45,0°** zur Waagerechten (Prüfskript über die Flächennormalen), Parameter `kr_pu_schraege` (≥ 30°). Die Schräge beginnt an der Unterkante des Balkens bei Z 25 und endet an der Stoßwand bei Z 32.
- Stirnkante der Grundplatte (Z 25…29, Y ±46): In der Ansicht von vorne bzw. hinten deckt der Puffer Z 25…72 bzw. 25…82 über Y ±61 bzw. ±78 ab (Bilder oben, Schnittbilder). Der Träger liegt dahinter an der Stirn an.
- **Böschungswinkel** (Information, keine Anforderung): Tangente von der Radaufstandsfläche an den tiefsten vordersten Punkt. Plattenecke allein 41,1°; mit Rammschutz vorne **32,0°** (Schrägenbeginn X 184,8 / Z 25), hinten **35,9°** (X −180,8 / Z 25). Hindernisse bis zur Höhe der Schräge treffen zuerst auf die 45°-Fläche.

## Karosseriehalter (MECH-KRS-006)

| | vorne | hinten | vorläufige Karosseriemaße |
|---|---|---|---|
| Pfostenlage X / Y | 169,35 / ±22,0 (Lochbild Karosseriehalter) | −169,35 / ±22,0 | Karosserielöcher `kr_karo_x_v` 169,35, `kr_karo_x_h` 169,35, Abstand quer `kr_karo_dy_*` 44 mm → Versatz 0 (`kr_karo_versatz_*`) |
| Nennhöhe Karosserieoberfläche | – | – | `kr_karo_z_v` **105 mm**, `kr_karo_z_h` **116 mm** |
| Klammerlöcher (Mitte, gemessen) | Z 98,5 / 102,5 / **106,5** / 110,5 / 114,5 | Z 109,5 / 113,5 / **117,5** / 121,5 / 125,5 | Nennloch = Nennhöhe + `kr_klammer_ueber` 1,5 mm |
| Verstellbereich | ±8 mm in Schritten von 4 mm | ±8 mm in Schritten von 4 mm | Soll ±6 mm, Schritt ≤ 4 mm ✓ |
| Pfosten | 8 × 8 mm, Z 35,5…118,5 | 8 × 8 mm, Z 35,5…129,5 | Klammerloch Ø 2,0 (`kr_klammer_d` 1,4 + 0,6) |

- Jeder Pfosten steht in einer Tasche des Trägers (Verdrehsicherung) und wird mit einer M3 × 20 Senkkopf von unten durch Grundplatte und Träger in seinen Gewindeeinsatz gezogen. Die Klammerlöcher laufen quer (Y), die Klammer steckt man von außen ein.
- **Weichen die Karosserielöcher ab** (Prüfmaße `kr_karo_versatz_v/_h/_y/_yh`): bis ca. ±3 mm in X reicht das Spiel im Lexan-Loch; bei größerem Versatz bekommt der Pfosten einen Querträger bzw. eine Verlängerung oben (neues Pfostenteil, Lochbild der Grundplatte bleibt). Die Höhe stellt das Lochraster ein; reicht ±8 mm nicht, werden die Pfosten mit geänderter `kr_karo_z_*` neu gedruckt.
- 🔧 Probemontage der Karosserie nach Lieferung.

## Karosseriehülle (MECH-KRS-007)

Vereinfachte Hülle (Komponente `karosserie-huelle`, alle Maße **vorläufig**, Parameter `kr_hu_*`): Nase X 150…186 (halbe Breite 55…63), Haube bis X 80, Kabine X −82…72 (±88, Dach Z 150 zwischen X −50 und 30), Heck X −182…−90 (±74). Unterkante der Seitenwände an Nase und Heck Z 96, an der Kabine Z 40. Oberkante an den Pfosten genau bei den Nennhöhen.

**Prüfung** (Bewegungsprüfung wie unten, Hülle gegen alle Teile): keine Überschneidung außer den gewollten (Pfosten durch die Karosserielöcher; Akku-Entnahmeweg, weil der Akku bei abgenommener Karosserie gewechselt wird).

| Bereich | kleinster Abstand Hülle | Stellung |
|---|---|---|
| Räder vorne (9 Stellungen mit Lenkeinschlag) | 12,52 mm | ausgefedert, voll rechts |
| Räder hinten (3 Stellungen) | 7,01 mm | Konstruktionslage |
| Bewegungsräume Räder (Skelett) | 6,45 mm hinten / 12,08 mm vorne | |
| Sturzstangen vorne / hinten | **4,32** / 5,09 mm | eingefedert (vorne voll links) |
| Radträger hinten | 4,91 mm | eingefedert |
| Dämpfer vorne / hinten | 6,53 / 6,12 mm | hinten am Hüllenende (X-Lage der Dämpfer ändert sich nicht mit dem Federweg) |
| Dämpferbrücken vorne / hinten | 7,33 / 6,88 mm | |
| Lenkgestänge / Servo-Anlenkung / Umlenkhebel | **4,89** / 5,51 / 9,30 mm | voll rechts |
| Servo-Saver (Feder) | 22,17 mm | |
| Oberdeck | 26,52 mm | |
| Elektronik UBEC / Empfänger / Regler | 10,91 / 13,09 / 13,20 mm | |

Die Hülle ist eine Annahme; die Abstände sind dokumentiert, nicht angepasst. In der Umsetzung wurde die Hülle zweimal plausibler gemacht, weil die erste Annahme mit Teilen des Fahrzeugs kollidierte: Unterkante an Nase und Heck 92 → 96 mm (Sturzstangen vorne 0,46 mm, Radträger hinten 1,06 mm) und Übergang der Unterkante vorne bei X 70…80 statt 75…85 (Lenkgestänge bei vollem Rechtseinschlag 2,7 mm³, UBEC 3,8 mm³). 🔧 Probemontage: Karosserie schleift nirgends bei vollem Einfedern und Lenkeinschlag.

## Interferenz und Abstände (MECH-KRS-004)

**Konstruktionslage** (in diesem Design): Fusion `analyzeInterference` über alle eigenen und alle abgeleiteten Körper (ohne `grundplatte-alu`, die am selben Ort liegt), berührende Flächen nicht mitgezählt. Die vom Achsen-Design ersetzten Skelett-Hüllen (`fahrwerk-daempfer-*`, `fahrwerk-rad-*`, `antrieb-radachse-*`, `antrieb-antriebswelle-*`, `antrieb-getriebe-hinten`) sind wie bei Vorder- und Hinterachse ausgenommen. Ergebnis: **0 Überschneidungen der Träger, Puffer und Pfosten**; Träger ↔ Grundplatte, Puffer ↔ Träger und Pfosten ↔ Träger nur Berührung (Auflageflächen). Gewollt sind nur Pfosten ↔ Karosseriehülle (je 52,9 bzw. 52,4 mm³, Pfosten durch das Karosserieloch) und Hülle ↔ Akku-Entnahmeweg (Akkuwechsel bei abgenommener Karosserie).

**Bewegungsprüfung:** Die eigenen Körper werden als Kopie in die Designs „open-rc-car-vorderachse“ v8 und „open-rc-car-hinterachse“ v14 übertragen (Basis-Feature, nicht gespeichert; ein Einfügen als Referenz geht nicht, weil das neue Design die Achsen ableitet). Dort werden die Stellungsparameter gesetzt und Interferenz und Mindestabstände gemessen: vorne **9 Stellungen** (`va_ql_dphi` = ausgefedert / 0 / eingefedert × `va_lk_phi` = voll links / geradeaus / voll rechts), hinten **3 Stellungen** (`ha_ql_dphi`). Ergebnis: **0 Überschneidungen** der eigenen Teile mit Dämpfern, Querlenkern, Rädern, Radachsen, Radträgern, C-Hubs, Achsschenkeln, Sturzstangen, Spurstangen, Lenkgestänge, Servo-Anlenkung, Umlenkhebeln und Servo-Saver in allen Stellungen.

| Paar | kleinster Abstand | Stellung | Soll |
|---|---|---|---|
| Träger hinten ↔ Rad hinten (bewegt) | **3,29 mm** | ausgefedert | ≥ 3 |
| Träger hinten ↔ Bewegungsraum Rad hinten (Skelett) | 6,41 mm | | ≥ 3 |
| Puffer hinten ↔ Rad hinten / Bewegungsraum | 6,43 / 8,13 mm | ausgefedert | ≥ 3 |
| Träger vorne ↔ Rad vorne (bewegt, mit Lenkeinschlag) | 12,11 mm | ausgefedert, voll rechts | ≥ 3 |
| Puffer vorne ↔ Rad vorne / Bewegungsraum | 16,59 / 15,31 mm | | ≥ 3 |
| Träger und Puffer vorne ↔ Dämpfer vorne | **1,05 mm** | alle Stellungen (X-Lage fest) | ≥ 1 |
| Träger und Puffer hinten ↔ Dämpfer hinten | **1,05 mm** | alle Stellungen | ≥ 1 |
| Flansch vorne ↔ Dämpfer vorne (Höhe) | 1,2 mm (Flansch Z 30, Dämpfer ab Z 31,2) | ausgefedert | ≥ 1 |
| Träger ↔ Dämpferbrücke vorne / hinten | 3,00 / 3,00 mm | | ≥ 1, keine Berührung |
| Pfosten ↔ Dämpferbrücke vorne / hinten | 2,85 / 2,85 mm | | ≥ 1 |
| Träger vorne ↔ Querlenker vorne | 8,80 mm | ausgefedert | ≥ 1 |
| Pfosten ↔ Sturzstangen vorne / hinten | 10,85 / 9,74 mm | | ≥ 1 |
| Pfosten ↔ Dämpfer vorne / hinten | 10,76 / 17,54 mm | | ≥ 1 |
| Puffer ↔ Pfosten vorne / hinten | 7,95 / 3,95 mm | | |
| Lenkung (Spurstangen, Lenkgestänge, Servo) | > 40 mm | | ≥ 1 |

Die knappsten Werte (Dämpfer 1,05 mm) hängen an den vorläufigen Dämpfermaßen der Achsen (Messpunkt 3 der Vorderachse); `kr_va_daempfer_dx` und `kr_ha_daempfer_dx` müssen nach dem Messen nachgezogen werden.

## Lasten (MECH-KRS-008)

Statische Ersatzlasten aus der Anforderung: **200 N frontal mittig**, **100 N an der Pufferecke** (auch 30° schräg), **20 N quer an der Pfostenspitze**. Werkstoff wie in den anderen Baugruppen: PETG ca. 47 MPa, Prusament PC ca. 60 MPa (Zugfestigkeit, auch für Druck angesetzt). Biegebalken σ = M / W, Geometrie aus dem Modell.

| Teil, Stelle | Last, Hebel | M | Querschnitt | σ | Sicherheit PETG (PC) |
|---|---|---|---|---|---|
| **Balken vorne, Wurzel am Lippenrand** (Sollbruchstelle) | 100 N an der Ecke Y 61, Wurzel Y 35,5 → 25,5 mm | 2 550 N·mm | Balken 3,5 × 45 + Flansch 4,0 × 5 (L-Querschnitt), I = 437 mm⁴, W innen 82,0 / außen 201 mm³ | 31,1 (Druck) / 12,7 (Zug) MPa | **1,51** (1,93) |
| **Balken hinten, Wurzel am Fuß** (Sollbruchstelle) | 100 N an der Ecke Y 78, Wurzel Y 45 → 33 mm | 3 300 N·mm | 3,5 × 55, W 112 mm³ | 29,4 MPa | **1,60** (2,04) |
| Balken vorne / hinten, 30° schräg | 86,6 N quer zum Balken + 50 N längs | 2 210 / 2 860 N·mm | wie oben | 27,2 / 25,7 MPa | 1,73 / 1,83 |
| Balken vorne, frontal mittig | 200 N auf Puffermitte Z 48,5, Platte über der Lippe (Z 37) → 11,5 mm, Breite 71 mm | 2 300 N·mm | 71 × 3,5, W 145 mm³ | 15,9 MPa | 2,96 |
| Balken hinten, frontal mittig | 200 N auf Z 53,5, über dem Fuß (Z 37) → 16,5 mm, Breite 90 mm | 3 300 N·mm | 90 × 3,5, W 184 mm³ | 18,0 MPa | 2,62 |
| Anlage an der Plattenstirn | 200 N auf Lippe bzw. Balken, 4 × 71 bzw. 4 × 92 mm | – | 284 / 368 mm² | 0,7 / 0,5 MPa | > 50 |
| Grundplatte am Lochbild (Lochleibung), solange der Spalt 0,3 mm offen ist | 200 N auf 4 × M3 | – | 4 × (3 × 4 mm) | 4,2 MPa | > 10 |
| Schrauben M3 (Abscherung) | 50 N je Schraube | – | 5,0 mm² | 10 MPa | > 30 |
| Pfosten vorne / hinten, Wurzel an der Tasche (Z 37) | 20 N an der Spitze, 81,5 / 92,5 mm | 1 630 / 1 850 N·mm | 8 × 8, W 85,3 mm³ | 19,1 / 21,7 MPa | 2,46 / 2,17 (3,14 / 2,77) |
| Gewindeeinsatz im Pfosten (Zug) | Kippmoment 1 630 / 1 850 N·mm über halbe Pfostenbreite 4 mm, ohne Stütze der Tasche | – | – | 408 / 462 N | 🔧 Ausreißkraft am Teil prüfen |

- **Sollbruchstelle ist der Träger:** Bei der Eckenlast erreicht der Balken 29…31 MPa, die Grundplatte am Lochbild nur ca. 4 MPa (Lochleibung) bzw. < 1 MPa (Anlage an der Stirn). Bei Überlast bricht zuerst der Balken an der Wurzel, nicht die Platte.
- **Kippmoment** frontal: 200 N greifen ca. 21…26 mm über der Anlage an der Stirn an; der Träger drückt dabei mit dem Fuß auf die Plattenoberseite (Druck), die Schrauben werden kaum auf Zug belastet.
- **TPU-Puffer:** Federweg bis zur Anlage am Balken **5,0 mm** (Kammertiefe, `kr_pu_federweg`). Die Federkennlinie hängt an der TPU-Härte (Annahme Shore 95A) und wird am Prototyp geprüft.
- 🔧 Prototyp: Anfahren gegen eine Wand mit ca. 10 km/h vorne und rückwärts ohne Schaden an Grundplatte, Dämpfern und Querlenkern; 20 N an der Pfostenspitze (Federwaage).

## Druckhinweise (MECH-KRS-009)

| Teil | Druckausrichtung | Material | Hüllquader (mm) | Mindestwand |
|---|---|---|---|---|
| Träger vorne | Balken-Vorderseite (X 184,8) auf dem Bett; Fuß, Lippe, Flansch und Steg stehen senkrecht, ohne Stützen | PETG (Test), Prusament PC | 19,3 × 122 × 45 | Einsatz ↔ Fußkante 1,85; Einsatz im Steg ↔ Stegkante 1,5; Balken 3,5; Deckel über dem Einsatz 2,0 |
| Träger hinten | Balken-Außenseite (X −180,8) auf dem Bett, ohne Stützen | PETG (Test), Prusament PC | 15,3 × 156 × 55 | wie vorne |
| Puffer vorne / hinten | Stoßfläche auf dem Bett; Wände senkrecht, Schräge 45°, keine Stützen | TPU (Annahme Shore 95A) | 17,5 × 122 × 47 / 17,5 × 156 × 57 | 2,0 (alle Wände) |
| Pfosten | liegend auf einer Seitenfläche (Klammerlöcher senkrecht), keine Stützen | PETG (Test), Prusament PC | 8 × 8 × 83 / 94 | 2,0 um den Einsatz, 3,0 neben den Klammerlöchern |

- Alle Teile passen in 256 × 256 × 256 mm (MECH-FZG-003).
- **Toleranzen:** Durchgangsbohrungen M3 Ø 3,4 (3,2 + 0,2), Tasche für den Pfosten 8,4 × 8,4 (+0,2 je Seite), Klammerlöcher Ø 2,0 (Draht + 0,6), Einsatzbohrungen Ø 4,0 wie in allen Baugruppen (vorläufig).
- **Füllung:** Träger und Pfosten mindestens 4 Perimeter, 40 % Füllung; Puffer mit 2 Perimetern (Wand 2 mm), keine Füllung nötig.
- 🔧 Slicer-Prüfung durch den Nutzer.

## Fräsbarkeit (MECH-KRS-014, SOLL)

Die Träger sind 2,5D: alle Flächen parallel oder senkrecht zu den Achsen, von oben (Fuß, Lippe, Steg, Balken, Taschen, Einsätze oben) und von unten (Stufe Z 25/29, Einsätze unten) zugänglich, keine Hinterschnitte. Alle senkrechten Innenecken sind mit **2,0 mm** verrundet (`kr_tr_r`, Prüfskript: danach 0 scharfe senkrechte Innenkanten), die Taschen der Pfosten haben Freistiche Ø 3 (Radius 1,5). Waagerechte Innenkanten (Stufen) entstehen mit dem Schaftfräser. Abweichung: Für eine Alu-Version wäre der 3,5 mm dicke Balken überdimensioniert; er ist für PC/PETG ausgelegt.

## Montagefolge und Wartung (MECH-KRS-012, SOLL)

1. Gewindeeinsätze einschmelzen: je Träger 2 von unten (±8) und 2 von oben in den Mittelsteg, je Pfosten 1 von unten.
2. Träger auf das Plattenende setzen, Lippe bzw. Balken an die Plattenstirn, 2 × M3 × 8 Senkkopf von unten in die Einsätze (±8).
3. Pfosten in die Taschen stellen, je 1 × M3 × 20 Senkkopf von unten durch Grundplatte und Träger in den Pfosten (±22).
4. Puffer aufsetzen (Deckel über den Balken, Zunge auf den Steg), 2 × M3 × 8 Zylinderkopf mit Scheibe DIN 9021 von oben.
5. Karosserie auf die Pfosten setzen und mit den Klammern im passenden Rasterloch sichern.

- **Puffer tauschen:** 2 Schrauben oben lösen, der Träger bleibt verschraubt.
- **Träger lösen:** 4 Schrauben von unten (2 × M3 × 8, 2 × M3 × 20; die Pfosten kommen mit). Dämpferbrücke, Dämpfer und Querlenker bleiben montiert (Träger 3 mm vor bzw. hinter der Brücke, Schrauben von unten frei zugänglich).
- **Karosserie:** ohne Werkzeug, nur Klammern.

## Masse (MECH-KRS-013, SOLL)

8 Druckteile **171,0 g** (PETG und TPU, 100 % Füllung, obere Grenze), mit Prusament PC 164,1 g. Das ursprüngliche Soll ≤ 80 g ist nicht erreichbar; Nutzerentscheidung 2026-11-13: Soll auf ≤ 175 g angehoben. Ursache: Die Eckenlast 100 N mit Sicherheit 1,5 verlangt bei 3,5 mm Balkendicke (Längenbudget 380 mm) eine Balkenhöhe von 45 bzw. 55 mm über die volle Pufferbreite (122 bzw. 156 mm, gefordert durch die Dämpferbreite); die beiden Träger wiegen allein 99 g, die Puffer 45 g, die vier Pfosten 27 g. Mit üblicher Teilfüllung (z. B. 40 %) liegen die gedruckten Teile darunter (grobe Schätzung 60…70 %, nicht gemessen).

## Parametertest (MECH-KRS-001)

| Test | Ergebnis |
|---|---|
| **`radstand` 280 mm im Skelett → Ableitung aktualisieren** | **bestanden** (Freigabe 2026-11-10). Skelett `radstand` = 280 mm: Zeitleiste (327 Elemente) ohne Fehler, `achse_x` 140 mm, gespeichert als **v15**. Hier Referenz auf v15, `DeriveFeature.setSourceEntities(…)` der Skelett-Ableitung und `Design.computeAll()`: `radstand_Ref` 280 mm, Zeitleiste (80 Elemente) **ohne Fehler und Warnungen**. Lochreihe `kr_loch_x` 176,35 mm (= `gp_ende_loch_x` der Grundplatte bei 280 mm), Plattenende 184,0 mm. Alle Teile folgen um 7,0 mm in X, Y und Z bleiben gleich: Träger vorne X 172,5…191,8, hinten −187,8…−172,5, Puffer 181,3…198,8 bzw. −194,8…−177,3, Pfosten 172,35…180,35 bzw. −180,35…−172,35; Einsätze (±176,35 / ±8), Durchgänge (±176,35 / ±22). Die Karosseriehülle bleibt stehen (feste Bausatzmaße), Prüfmaß `kr_karo_versatz_v` −7,0 mm zeigt den nötigen Ausgleich; Gesamtlänge dann 393,6 mm (> 380, folgt aus dem längeren Radstand). Vorder- und Hinterachse wurden nicht aktualisiert (nicht Teil dieser Anforderung). Danach Skelett zurück auf 266 mm, ohne Fehler, gespeichert als **v16**; v16 ist maßgleich mit v14 (Prüfskript: alle 155 Parameter und alle 40 Körper gleich). Hier erneut aktualisiert: Referenz v16, Zeitleiste ohne Fehler, alle Hüllquader, Volumina, Lochlagen und Prüfmaße genau wie vorher. |
| Lochraster | Klammerlöcher bei Nennhöhe + 1,5 ± 0 / 4 / 8 mm (gemessen), folgt `kr_raster_n`, `kr_raster_t`, `kr_karo_z_*` |

![Parametertest mit radstand 280 mm](images/karosseriehalter-rammschutz-parametertest-280.png)

*Parametertest bei `radstand` 280 mm, von oben (vorne ist oben). Träger, Puffer und Pfosten sind mit Plattenende und Lochreihe 7 mm nach außen gewandert; Grundplatte, Vorder- und Hinterachse stehen noch bei 266 mm (nicht aktualisiert), die Bewegungsräume der Räder (grün) sind mitgewandert. Durchscheinend in der Mitte vorne: Darstellung des ViewCube (kein Bauteil).*

## Messpunkte bei Lieferung

Nach dem Messen die Parameter ersetzen, die Kommentare auf „belegt“ setzen und die Bewegungsprüfung wiederholen:

1. **Karosserie Neo Scorcher:** Lage der Befestigungslöcher vorne und hinten in X und Abstand quer (`kr_karo_x_v`, `kr_karo_x_h`, `kr_karo_dy_v`, `kr_karo_dy_h`), Höhe der Karosserieoberfläche an den Löchern bei aufgesetzter Karosserie (`kr_karo_z_v`, `kr_karo_z_h`). Bezug: Fahrzeugmitte zwischen den Achsen, Plattenunterseite Z 25. Ist der Versatz zum Pfosten > ca. 3 mm, Pfosten mit Querträger/Verlängerung neu konstruieren; liegt die Höhe außerhalb ±8 mm, Pfosten mit neuer Nennhöhe drucken.
2. **Karosseriehülle:** Länge, Breite an Nase, Kabine und Heck, Höhe an Haube, Dach und Heck, Unterkante der Seitenwände (`kr_hu_*`), dann MECH-KRS-007 neu prüfen; besonders Sturzstangen vorne (4,32 mm) und Lenkgestänge (4,89 mm).
3. **Karosserieklammern:** Drahtdurchmesser (`kr_klammer_d`) und Länge des geraden Schenkels (`kr_klammer_l`, muss > 10 mm sein); Klammerloch ggf. anpassen.
4. **TPU:** Shore-Härte des verwendeten Filaments; Federweg und Rückstellung am gedruckten Puffer prüfen (Druck mit der Hand bis zur Anlage am Balken).
5. **Gewindeeinsätze:** Bohrung und Länge (`kr_einsatz_d`, `kr_einsatz_t`), Ausreißkraft im Pfosten (≥ 470 N erwünscht, siehe Lasten).
6. **Dämpfer** (aus Vorder- und Hinterachse): vorderste bzw. hinterste Kante über den Federweg (`kr_va_daempfer_dx`, `kr_ha_daempfer_dx`, `kr_va_daempfer_z`, `kr_va_daempfer_b`, `kr_ha_daempfer_b`).

## Vorgaben an spätere Baugruppen

- **Elektronikhalter (Freiraum unter der Karosserie, vorläufige Hülle):** Unter der Kabine (X −82…72) ist bis Y ±85 und bis Z 145 (Dach Z 150 zwischen X −50 und 30, zur Haube bzw. zum Heck abfallend auf Z ca. 120) Platz; an Nase und Heck nur innerhalb Y ±60 bzw. ±71 und unter ca. Z 100 (vorne über den Dämpfern) bzw. 105 (hinten). Heutige Abstände der Elektronik zur Hülle: UBEC 10,9 mm, Empfänger 13,1 mm, Regler 13,2 mm. Die Empfängerantenne braucht ein Loch in der Karosserie oder muss unter der Hülle bleiben. Der Akku wird bei abgenommener Karosserie gewechselt.
- **Akkuhalter:** Die Hülle schneidet den Akku-Entnahmeweg; Akkuwechsel nur ohne Karosserie.
- **Spätere Alu-Teile:** Wird die Grundplatte gefräst, bleiben die Lochreihe und die Anlage an der Plattenstirn gleich; die Träger können als Alu-Frästeil nachgebaut werden (2,5D, Radien 2 mm).
- **Vorderachse 4WD:** Lochreihe und Träger sind unabhängig vom Frontschott; die Dämpferbrücke muss 3 mm Luft zum Träger behalten (Außenseite X ≤ 162,5).

## Abweichungen und offene Punkte

1. **Masse (MECH-KRS-013, SOLL):** 171 g, über dem ursprünglichen Soll ≤ 80 g. Nutzerentscheidung 2026-11-13: Soll auf ≤ 175 g angehoben (MUSS-Lasten und Länge erzwingen die Balken). Verworfen: Eckenlast/Sicherheit absenken (ca. −20…25 g), Puffer schmaler als die Dämpfer (widerspricht MECH-KRS-003).
2. **Böschungswinkel** sinkt vorne von 41,1° (Plattenecke) auf 32,0°, hinten auf 35,9° (keine Anforderung, Information).
3. **Längenreserve:** Gesamtlänge 379,6 mm, also 0,4 mm unter 380. Werden Dämpfer oder Puffer nach dem Messen größer, muss der Balken dünner oder der Federweg kleiner werden (Rückfrage).
4. **Pfosteneinsatz unter 20 N quer:** Zug im Einsatz bis ca. 460 N (ohne Stütze der Tasche); Ausreißkraft am Teil prüfen (Messpunkt 5), sonst Pfosten mit Flansch und 2 Schrauben.
5. Karosseriemaße, Karosseriehülle und Klammern sind **vorläufig** (keine Quelle; Annahme wie TT-02-Karosserien, Fahrzeug 380 × 250 mm). 🔧 Probemontage.
6. Die Vorderachse ist auf **v8** abgeleitet; die Referenz ist in Fusion als veraltet markiert (v9 ist laut Nutzer unwichtig). Nicht aktualisieren.

## Entscheidungen in der Umsetzung (nicht im Anforderungsdokument vorgegeben)

- **Träger mit Anlage an der Plattenstirn** (vorne Lippe, hinten Balken) statt nur Verschraubung auf der Lochreihe: Die 8 Löcher liegen auf einer X-Linie (Hinweis Review PR #13).
- **Flansch vorne unter den Dämpfern** (Z 25…30): stützt den dünnen Balken an der Wurzel, ohne die Länge zu vergrößern.
- **Puffer als TPU-Hohlprofil** (Kammer 5 mm, offen zum Balken) statt Vollmaterial: Vollmaterial aus TPU federt nicht 5 mm.
- **Pfosten auf dem Träger** über die Löcher ±22 (gemeinsame Schraube Platte–Träger–Pfosten), Verdrehsicherung über eine Tasche.
- **Karosseriehülle** als Schnitt aus Seitenprofil und Draufsicht mit Schale, offen nach unten; Lage der Karosserielöcher vorläufig gleich der Lochreihe.
- **Bewegungsprüfung** über Kopien der eigenen Körper in den Achsen-Designs (nicht gespeichert), weil ein Einfügen als Referenz eine zirkuläre Referenz wäre.

## Parameterliste (neue Benutzerparameter)

108 Benutzerparameter mit Präfix `kr_`, jeder mit Kommentar (Quelle; „belegt“, „vorläufig“, „abgeleitet“ oder „Schnittstelle“). Skelett-Parameter stehen ohne `_Ref`. Werte direkt aus Fusion (Version 4). Prüfmaße (`kr_fuss_wand`, `kr_gesamtlaenge`, `kr_v_vorlauf`, `kr_h_vorlauf`, `kr_raster_bereich`, `kr_karo_versatz_*`) steuern nichts im Modell.

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `kr_gp_ueberstand` | `20 mm` | 20,00 mm | Schnittstelle Grundplatte v12: gp_ueberstand, Plattenende ueber die Getriebe hinaus (Nutzerentscheidung 2026-11-13); Kopie, weil die Grundplatte keine Favoriten-Parameter hat, bei Aenderung von Hand nachziehen |
| `kr_gp_ende_x` | `platte_x_vorne + kr_gp_ueberstand` | 177,00 mm | abgeleitet: Plattenende vorne X 177 (= gp_ende_x), hinten gespiegelt |
| `kr_gp_rand` | `5 mm` | 5,00 mm | Schnittstelle Grundplatte v12: gp_rand, Randabstand Lochmitte (Formel der Lochreihe) |
| `kr_gp_db_dx` | `29.5 mm` | 29,50 mm | Schnittstelle Grundplatte v12 (gp_db_x), Vorderachse v8, Hinterachse v14: Aussenseite Daempferbruecke = achse_x + 29,5 |
| `kr_gp_db_x` | `achse_x + kr_gp_db_dx` | 162,50 mm | abgeleitet: Aussenseite Daempferbruecken X +-162,5 |
| `kr_einsatz_d` | `4 mm` | 4,00 mm | Gewindeeinsatz M3 kurz (Stueckliste Pos. 30): Bohrung, vorlaeufig wie akku_einsatz_d und va_einsatz_d, bei Lieferung messen |
| `kr_einsatz_t` | `6 mm` | 6,00 mm | Gewindeeinsatz M3 kurz: Bohrtiefe, vorlaeufig wie akku_einsatz_t, bei Lieferung messen |
| `kr_wand_min` | `1.2 mm` | 1,20 mm | belegt: Mindestwand Traeger und Pfosten (MECH-KRS-009); Pruefgrenze |
| `kr_gp_ende_db_abstand` | `kr_einsatz_d / 2 + kr_wand_min + 1 mm` | 4,20 mm | Schnittstelle Grundplatte v12: gp_ende_db_abstand (Formel der Lochreihe) |
| `kr_loch_x` | `( kr_gp_db_x + kr_gp_ende_db_abstand + kr_gp_ende_x - kr_gp_rand ) / 2` | 169,35 mm | abgeleitet: Lochreihe Rammschutz/Karosseriehalter X +-169,35 (= gp_ende_loch_x, gleiche Formel) |
| `kr_ramm_y` | `8 mm` | 8,00 mm | Schnittstelle Grundplatte v12: gp_ramm_y, Lochbild Rammschutz quer +- |
| `kr_karo_y` | `22 mm` | 22,00 mm | Schnittstelle Grundplatte v12: gp_karo_y, Lochbild Karosseriehalter quer +- |
| `kr_gp_halb_b` | `46 mm` | 46,00 mm | Schnittstelle Grundplatte v12: halbe Plattenbreite am Plattenende (gp_achse_y) |
| `kr_bohrung` | `3.4 mm` | 3,40 mm | Durchgangsbohrung M3 im Druckteil: 3,2 + 0,2 mm (MECH-KRS-009) |
| `kr_stirn_spiel` | `0.3 mm` | 0,30 mm | Spalt Traeger zur Plattenstirn (Fuegespiel; unter Last liegt der Traeger an der Stirn an) |
| `kr_va_daempfer_dx` | `47.3 mm` | 47,30 mm | Schnittstelle Vorderachse v8: vorderste Kante der Daempfer ueber alle 9 Stellungen X 180,3 = achse_x + 47,3 (gemessen) |
| `kr_va_daempfer_y` | `36.8 mm` | 36,80 mm | Schnittstelle Vorderachse v8: Daempfer innen /Y/ 36,8 (kleinster Wert ueber alle Stellungen, gemessen) |
| `kr_va_daempfer_z` | `31.2 mm` | 31,20 mm | Schnittstelle Vorderachse v8: tiefster Punkt der Daempfer Z 31,2 (ausgefedert, gemessen) |
| `kr_va_daempfer_b` | `58.8 mm` | 58,80 mm | Schnittstelle Vorderachse v8: Daempfer aussen /Y/ 58,8 (Schutzbreite MECH-KRS-003, gemessen) |
| `kr_va_ql_dx` | `35.5 mm` | 35,50 mm | Schnittstelle Vorderachse v8: vorderste Kante Querlenker (Daempferlasche) X 168,5 = achse_x + 35,5 |
| `kr_ha_daempfer_dx` | `43.2 mm` | 43,20 mm | Schnittstelle Hinterachse v14: hinterste Kante der Daempfer X -176,2 = -(achse_x + 43,2), gemessen ueber 3 Stellungen |
| `kr_ha_daempfer_b` | `77.2 mm` | 77,20 mm | Schnittstelle Hinterachse v14: Daempfer aussen /Y/ 77,2 (Schutzbreite MECH-KRS-003, gemessen) |
| `kr_luft` | `1 mm` | 1,00 mm | belegt: Mindestabstand zu allen Teilen ausser den Raedern (MECH-KRS-004); Pruefgrenze |
| `kr_luft_rad` | `3 mm` | 3,00 mm | belegt: Mindestabstand zu den Bewegungsraeumen der Raeder (MECH-KRS-004); Pruefgrenze |
| `kr_luft_ql` | `1.5 mm` | 1,50 mm | Luft Lippe vorne zur Daempferlasche des Querlenkers (>= kr_luft) |
| `kr_db_luft` | `3 mm` | 3,00 mm | Luft Fuss des Traegers zur Daempferbruecke (>= kr_luft; Einsatzwand bleibt >= kr_wand_min) |
| `kr_fuss_x0` | `kr_gp_db_x + kr_db_luft` | 165,50 mm | abgeleitet: Innenkante Fuss vorne und hinten X +-165,5 |
| `kr_fuss_h` | `8 mm` | 8,00 mm | Hoehe Fuss auf der Platte (Einsatz 6 mm + 2 mm Deckel) |
| `kr_fuss_wand` | `kr_loch_x - kr_einsatz_d / 2 - kr_fuss_x0` | 1,85 mm | Pruefmass: Wand zwischen Einsatzbohrung und Fusskante (>= kr_wand_min) |
| `kr_v_fuss_b` | `30 mm` | 30,00 mm | Fuss vorne hinter der Lippe: halbe Breite (Querlenker ab /Y/ 31,5) |
| `kr_v_lippe_x0` | `achse_x + kr_va_ql_dx + kr_luft_ql` | 170,00 mm | abgeleitet: Beginn der breiten Lippe vorne X 170 (vor den Querlenkern) |
| `kr_v_lippe_b` | `kr_va_daempfer_y - kr_luft - 0.3 mm` | 35,50 mm | abgeleitet: halbe Breite Lippe vorne 35,5 (1,3 mm zu den Daempfern) |
| `kr_v_stirn_x` | `kr_gp_ende_x + kr_stirn_spiel` | 177,30 mm | abgeleitet: Anlage des Traegers vor der Plattenstirn vorne X 177,3 |
| `kr_v_balken_x` | `achse_x + kr_va_daempfer_dx + kr_luft` | 181,30 mm | abgeleitet: Innenseite Balken vorne X 181,3 (kr_luft vor den Daempfern) |
| `kr_v_balken_d` | `3.5 mm` | 3,50 mm | Dicke Balken vorne (Laengenbudget 380 mm, Festigkeit siehe Doku) |
| `kr_v_balken_h` | `45 mm` | 45,00 mm | Hoehe Balken vorne ueber Unterkante Platte (Z 25...70) |
| `kr_v_halb_b` | `61 mm` | 61,00 mm | halbe Breite Balken und Puffer vorne: deckt die Daempfer (/Y/ 58,8) ab, >= 3 mm zu den Raedern |
| `kr_v_flansch_h` | `kr_va_daempfer_z - kr_luft - bodenfreiheit - 0.2 mm` | 5,00 mm | abgeleitet: Flansch unter den Daempfern vorne, Z 25...30 (1,2 mm unter den Daempfern) |
| `kr_steg_l` | `7 mm` | 7,00 mm | Mittelsteg: Laenge innen hinter dem Balken (Einsatz 4 + 2 x Wand 1,2 + Reserve) |
| `kr_steg_b` | `10 mm` | 10,00 mm | Mittelsteg: halbe Breite (traegt die Pufferschrauben; Pfosten bei /Y/ 18...26) |
| `kr_h_stirn_x` | `kr_gp_ende_x + kr_stirn_spiel` | 177,30 mm | abgeleitet: Innenseite Balken hinten X -177,3 (Anlage an der Plattenstirn; 1,1 mm hinter den Daempfern) |
| `kr_h_balken_d` | `3.5 mm` | 3,50 mm | Dicke Balken hinten |
| `kr_h_balken_h` | `55 mm` | 55,00 mm | Hoehe Balken hinten ueber Unterkante Platte (Z 25...80), Festigkeit Pufferecke siehe Doku |
| `kr_h_halb_b` | `78 mm` | 78,00 mm | halbe Breite Balken und Puffer hinten: deckt die Daempfer (/Y/ 77,2) ab |
| `kr_h_fuss_b` | `45 mm` | 45,00 mm | Fuss hinten: halbe Breite (Plattenende +-46) |
| `kr_pu_federweg` | `5 mm` | 5,00 mm | belegt: Federweg TPU-Puffer bis zur Anlage am Balken (MECH-KRS-008) |
| `kr_pu_wand` | `2 mm` | 2,00 mm | belegt: Wand TPU-Puffer (MECH-KRS-009, >= 2 mm) |
| `kr_pu_schraege` | `45 deg` | 45,0 deg | Anfahrschraege des Puffers zur Waagerechten (MECH-KRS-005, >= 30 Grad) |
| `kr_pu_schraube_y` | `5.5 mm` | 5,50 mm | Pufferschrauben M3 quer +- (im Mittelsteg) |
| `kr_v_stoss_x` | `kr_v_balken_x + kr_v_balken_d + kr_pu_federweg + kr_pu_wand` | 191,80 mm | abgeleitet: Stossflaeche Puffer vorne X 191,8 |
| `kr_h_stoss_x` | `kr_h_stirn_x + kr_h_balken_d + kr_pu_federweg + kr_pu_wand` | 187,80 mm | abgeleitet: Stossflaeche Puffer hinten X -187,8 (Betrag) |
| `kr_gesamtlaenge` | `kr_v_stoss_x + kr_h_stoss_x` | 379,60 mm | Pruefmass: Gesamtlaenge ueber beide Puffer (<= 380 mm, MECH-KRS-003) |
| `kr_v_vorlauf` | `kr_v_stoss_x - ( achse_x + kr_va_daempfer_dx )` | 11,50 mm | Pruefmass: Stossflaeche vorne vor dem vordersten uebrigen Teil (Daempfer), >= 5 mm |
| `kr_h_vorlauf` | `kr_h_stoss_x - kr_gp_ende_x` | 10,80 mm | Pruefmass: Stossflaeche hinten hinter dem hintersten uebrigen Teil (Plattenende -177, Daempfer -176,2), >= 5 mm |
| `kr_pf_b` | `8 mm` | 8,00 mm | Karosseriepfosten: Querschnitt quadratisch (Festigkeit 20 N quer, MECH-KRS-008) |
| `kr_pf_spiel` | `0.2 mm` | 0,20 mm | Pfosten in der Tasche des Traegers: Spiel je Seite (MECH-KRS-009) |
| `kr_pf_tasche_t` | `1.5 mm` | 1,50 mm | Tasche fuer den Pfostenfuss im Traeger (Verdrehsicherung) |
| `kr_pf_freistich` | `3 mm` | 3,00 mm | Freistich in den Taschenecken, Durchmesser (fraesgerecht, Radius 1,5 mm) |
| `kr_pf_bohr_t` | `11 mm` | 11,00 mm | Pfosten: Tiefe der Einsatzbohrung von unten (M3 x 20 Senkkopf greift 9,5 mm) |
| `kr_pf_oben` | `4 mm` | 4,00 mm | Pfosten: Ueberstand ueber dem obersten Klammerloch |
| `kr_pf_unten_z` | `bodenfreiheit + plattenstaerke + kr_fuss_h - kr_pf_tasche_t` | 35,50 mm | abgeleitet: Unterkante Pfosten (Taschengrund) Z 35,5 |
| `kr_karo_x_v` | `169.35 mm` | 169,35 mm | Karosserie Neo Scorcher: Befestigungsloecher vorne, Lage X, vorlaeufig (Annahme = Lochreihe, keine Quelle), nach Lieferung messen |
| `kr_karo_x_h` | `169.35 mm` | 169,35 mm | Karosserie Neo Scorcher: Befestigungsloecher hinten, Lage X (Betrag), vorlaeufig, nach Lieferung messen |
| `kr_karo_dy_v` | `44 mm` | 44,00 mm | Karosserie Neo Scorcher: Lochabstand quer vorne, vorlaeufig (Annahme = Lochbild 2 x 22), nach Lieferung messen |
| `kr_karo_dy_h` | `44 mm` | 44,00 mm | Karosserie Neo Scorcher: Lochabstand quer hinten, vorlaeufig, nach Lieferung messen |
| `kr_karo_z_v` | `105 mm` | 105,00 mm | Karosserie Neo Scorcher: Hoehe der Karosserieoberflaeche an den Loechern vorne (Nennhoehe), vorlaeufig: ueber Daempfern Z 95,7 und Bruecke Z 98,2 vorne, nach Lieferung messen |
| `kr_karo_z_h` | `116 mm` | 116,00 mm | Karosserie Neo Scorcher: Hoehe an den Loechern hinten (Nennhoehe), vorlaeufig: ueber Bruecke Z 108,9 und Daempfern Z 106,4 hinten, nach Lieferung messen |
| `kr_klammer_d` | `1.4 mm` | 1,40 mm | Karosserieklammer (R-Klammer, Bausatz): Drahtdurchmesser, vorlaeufig, nach Lieferung messen |
| `kr_klammer_l` | `25 mm` | 25,00 mm | Karosserieklammer: Laenge des geraden Schenkels, vorlaeufig (muss >= kr_pf_b + 2 mm sein), nach Lieferung messen |
| `kr_klammer_loch` | `kr_klammer_d + 0.6 mm` | 2,00 mm | abgeleitet: Klammerloch im Pfosten (Draht + 0,6 mm) |
| `kr_klammer_ueber` | `kr_klammer_loch / 2 + 0.5 mm` | 1,50 mm | abgeleitet: Lochmitte ueber der Karosserieoberflaeche (Klammer liegt auf) |
| `kr_raster_t` | `4 mm` | 4,00 mm | Lochraster der Pfosten: Teilung (MECH-KRS-006: <= 4 mm) |
| `kr_raster_n` | `5` | 5 | Lochraster der Pfosten: Anzahl Loecher (ungerade, Nennloch in der Mitte) |
| `kr_raster_bereich` | `( kr_raster_n - 1 ) / 2 * kr_raster_t` | 8,00 mm | Pruefmass: Verstellbereich +- um die Nennhoehe (MECH-KRS-006: >= 6 mm) |
| `kr_pf_oben_z_v` | `kr_karo_z_v + kr_klammer_ueber + kr_raster_bereich + kr_pf_oben` | 118,50 mm | abgeleitet: Oberkante Pfosten vorne |
| `kr_pf_oben_z_h` | `kr_karo_z_h + kr_klammer_ueber + kr_raster_bereich + kr_pf_oben` | 129,50 mm | abgeleitet: Oberkante Pfosten hinten |
| `kr_karo_versatz_v` | `kr_karo_x_v - kr_loch_x` | -0,00 mm | Pruefmass: Karosserieloch vorne gegen Pfosten in X (0 = kein Quertraeger noetig) |
| `kr_karo_versatz_h` | `kr_karo_x_h - kr_loch_x` | -0,00 mm | Pruefmass: Karosserieloch hinten gegen Pfosten in X |
| `kr_karo_versatz_y` | `kr_karo_dy_v / 2 - kr_karo_y` | 0,00 mm | Pruefmass: Karosserieloch vorne gegen Pfosten quer |
| `kr_karo_versatz_yh` | `kr_karo_dy_h / 2 - kr_karo_y` | 0,00 mm | Pruefmass: Karosserieloch hinten gegen Pfosten quer |
| `kr_hu_t` | `0.8 mm` | 0,80 mm | Karosseriehuelle: Wandstaerke der Huelle (Lexan, fuer die Pruefung vernachlaessigbar), vorlaeufig |
| `kr_hu_x_v` | `186 mm` | 186,00 mm | Karosseriehuelle Neo Scorcher: vorderes Ende X, vorlaeufig (Annahme: >= 5 mm hinter der Stossflaeche vorne, Fahrzeuglaenge 380 mm laut Tamiya), nach Lieferung messen |
| `kr_hu_x_h` | `182 mm` | 182,00 mm | Karosseriehuelle: hinteres Ende X (Betrag), vorlaeufig (Annahme: >= 5 mm vor der Stossflaeche hinten), nach Lieferung messen |
| `kr_hu_b_spitze` | `55 mm` | 55,00 mm | Karosseriehuelle: halbe Breite an der Spitze, vorlaeufig |
| `kr_hu_x_nase` | `150 mm` | 150,00 mm | Karosseriehuelle: Ende der Nasenverjuengung X, vorlaeufig |
| `kr_hu_b_nase` | `63 mm` | 63,00 mm | Karosseriehuelle: halbe Breite der Nase zwischen den Vorderraedern (Rad mit Lenkeinschlag ab /Y/ 66,5), vorlaeufig |
| `kr_hu_x_kab_v` | `80 mm` | 80,00 mm | Karosseriehuelle: Beginn der Verbreiterung zur Kabine X (hinter dem Radraum vorne X 79,5), vorlaeufig |
| `kr_hu_x_kab_v2` | `72 mm` | 72,00 mm | Karosseriehuelle: Kabine volle Breite ab X, vorlaeufig |
| `kr_hu_b_kab` | `88 mm` | 88,00 mm | Karosseriehuelle: halbe Breite der Kabine (Fahrzeugbreite 250 mm, Raeder aussen), vorlaeufig |
| `kr_hu_x_kab_h` | `82 mm` | 82,00 mm | Karosseriehuelle: Kabine volle Breite bis X (Betrag, vor dem Radraum hinten X -92), vorlaeufig |
| `kr_hu_x_heck_v` | `90 mm` | 90,00 mm | Karosseriehuelle: Beginn Heck schmal X (Betrag), vorlaeufig |
| `kr_hu_b_heck` | `74 mm` | 74,00 mm | Karosseriehuelle: halbe Breite des Hecks zwischen den Hinterraedern (Rad ab /Y/ 77,1), vorlaeufig |
| `kr_hu_z_spitze` | `100 mm` | 100,00 mm | Karosseriehuelle: Hoehe der Oberkante an der Spitze, vorlaeufig |
| `kr_hu_x_haube` | `90 mm` | 90,00 mm | Karosseriehuelle: Uebergang Haube/Windschutz X, vorlaeufig |
| `kr_hu_z_haube` | `122 mm` | 122,00 mm | Karosseriehuelle: Hoehe am Uebergang Haube/Windschutz, vorlaeufig |
| `kr_hu_x_dach_v` | `30 mm` | 30,00 mm | Karosseriehuelle: Dach vorne X, vorlaeufig |
| `kr_hu_x_dach_h` | `50 mm` | 50,00 mm | Karosseriehuelle: Dach hinten X (Betrag), vorlaeufig |
| `kr_hu_z_dach` | `150 mm` | 150,00 mm | Karosseriehuelle: Dachhoehe, vorlaeufig |
| `kr_hu_x_deck` | `100 mm` | 100,00 mm | Karosseriehuelle: Beginn Heckdeck X (Betrag), vorlaeufig |
| `kr_hu_z_deck` | `122 mm` | 122,00 mm | Karosseriehuelle: Hoehe Heckdeck, vorlaeufig |
| `kr_hu_z_heck` | `112 mm` | 112,00 mm | Karosseriehuelle: Hoehe am hinteren Ende, vorlaeufig |
| `kr_hu_z_unten_ende` | `96 mm` | 96,00 mm | Karosseriehuelle: Unterkante der Seitenwand an Nase und Heck (ueber Querlenker, Sturzstangen und Daempferaugen), vorlaeufig |
| `kr_hu_z_unten_mitte` | `40 mm` | 40,00 mm | Karosseriehuelle: Unterkante der Seitenwand an der Kabine, vorlaeufig |
| `kr_hu_x_unten_v` | `80 mm` | 80,00 mm | Karosseriehuelle: Uebergang Unterkante vorne X, vorlaeufig |
| `kr_hu_x_unten_v2` | `70 mm` | 70,00 mm | Karosseriehuelle: Unterkante Kabine vorne X, vorlaeufig |
| `kr_hu_x_unten_h` | `95 mm` | 95,00 mm | Karosseriehuelle: Uebergang Unterkante hinten X (Betrag), vorlaeufig |
| `kr_hu_x_unten_h2` | `85 mm` | 85,00 mm | Karosseriehuelle: Unterkante Kabine hinten X (Betrag), vorlaeufig |
| `kr_tr_r` | `2 mm` | 2,00 mm | Traeger: Radius der senkrechten Innenecken (fraesgerecht >= 1,5 mm, MECH-KRS-014) |

# Hinterachse

- **Anforderungen:** `docs/anforderungen/hinterachse.md` (Kürzel HAC)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-hinterachse“, **Version 11**, abgeleitet von „open-rc-car-skelett“ **v14** (maßgleich mit v12 und v10) und „open-rc-car-grundplatte“ **v11**. Version 11 enthält die Änderungen aus Review 2 nach der Nutzerentscheidung vom 2026-11-01 (Zahnradraum zwischen den E2-Lagern: zahnradseitige Lippen weggelassen, vorderes Lager am Becher, Lagerbock 3,5 mm dick, Hüllkörper `hinterachse-hauptzahnrad` mit Schutz gegen negativen `ha_hz_raum`, Passung `ha_e2h_spiel`; Version 9 und 10 waren Zwischenstände ohne `ha_e2h_spiel` bzw. mit veralteten Parameterkommentaren, Geometrie wie Version 11). Version 8 ist der Stand nach Review 1, Version 6 der Stand vor Review 1, Version 5 der Stand vor dem Parametertest mit dem Skelett.
- **Exporte (alle aus Version 11):** `cad/fusion/hinterachse.f3d`, `cad/step/hinterachse.step` (11 Druckteil-Komponenten, 12 Druckkörper), 12 STL in `print/stl/` (geändert gegenüber Version 8 nur Getriebegehäuse links/rechts und Lagerbock, die übrigen STL sind bytegleich)
- **Stand:** 2026-11-01

Die Hinterachse des 2WD-Prototyps besteht aus einem zweiteiligen Getriebe- und Differentialgehäuse für das TT-02B-Hinterachsdiff und die Kegelritzelwelle E2 mit einem abnehmbaren Lagerbock für das vordere E2-Lager, vier Querlenkerböcken auf der Grundplatte, zwei unteren Querlenkern, zwei Radträgern für die Radachsen N1 und einer Dämpferbrücke an der Rückseite des Gehäuses. Wie beim TT-02B führt oben eine einstellbare Sturzstange vom Radträger zur Brücke. Die CVA-Dämpfer sitzen wie beim TT-02B **hinter** der Brücke und sind oben nach innen geneigt.

![Hinterachse isometrisch](images/hinterachse-iso.png)

*Von vorne rechts oben. Gelb: Getriebegehäuse (zwei Hälften) mit dem Lagerbock E2 vorne, weiß: Querlenkerböcke, rot: Querlenker, grün: Radträger und Sturzstangen (durchscheinend), grau: Dämpferbrücke, durchscheinend rot: Dämpfer, blau: Antriebswellen N3, Diff-Becher N2 und Radachsen N1 (Hüllkörper), hellgrau: Räder. Dazu die Grundplatte (hinterer Teil) und das Oberdeck.*

![Hinterachse von hinten](images/hinterachse-hinten.png)

*Von hinten in Konstruktionslage. Die Dämpferbrücke trägt hinten die Dämpfer und vorne (verdeckt) die Kugelköpfe der Sturzstangen.*

![Hinterachse von oben](images/hinterachse-oben.png)

*Von oben, vorne ist oben.*

## Ergebnis

| Teil | Komponente / Körper | Abmessung X × Y × Z (mm) | Lage X / Y / Z (mm) | Masse PETG 100 % | Datei |
|---|---|---|---|---|---|
| Getriebegehäuse links | `hinterachse-getriebegehaeuse` / `getriebegehaeuse-links` | 48,5 × 22,4 × 63,0 | −156,5…−108,0 / 0…22,36 / 29…92 | 30,6 g | `print/stl/hinterachse-getriebegehaeuse-links.stl` |
| Getriebegehäuse rechts | `hinterachse-getriebegehaeuse` / `getriebegehaeuse-rechts` | 48,5 × 22,4 × 63,0 | −156,5…−108,0 / −22,36…0 / 29…92 | 31,1 g | `print/stl/hinterachse-getriebegehaeuse-rechts.stl` |
| Lagerbock E2 | `hinterachse-getriebegehaeuse-lagerbock` / `lagerbock` | 10,0 × 31,6 × 35,2 | −109,5…−99,5 / ±15,8 / 29…64,15 | 3,5 g | `print/stl/hinterachse-getriebegehaeuse-lagerbock.stl` |
| Querlenkerbock (4 ×) | `hinterachse-querlenkerbock-links-hinten`, `-links-vorne`, `-rechts-hinten`, `-rechts-vorne` | 10 × 16 × 19 | X −156…−146 bzw. −120…−110 / ±27…±43 / 29…48 | je 3,3 g | `print/stl/hinterachse-querlenkerbock-*.stl` |
| Querlenker links/rechts | `hinterachse-querlenker-links`, `-rechts` | 42,0 × 64,2 × 23,1 | −162,5…−120,5 / ±31,5…±95,7 / 20,4…43,5 | je 9,7 g | `print/stl/hinterachse-querlenker-links.stl`, `-rechts.stl` |
| Radträger links/rechts | `hinterachse-radtraeger-links`, `-rechts` | 16,4 × 35,6 × 47,6 | −141,2…−124,8 / ±73,3…±108,9 / 20,4…68,0 | je 6,3 g | `print/stl/hinterachse-radtraeger-links.stl`, `-rechts.stl` |
| Dämpferbrücke | `hinterachse-daempferbruecke` | 6,0 × 117,4 × 77,9 | −162,5…−156,5 / ±58,7 / 31,0…108,9 | 31,2 g | `print/stl/hinterachse-daempferbruecke.stl` |
| **Summe Druckteile** | | | | **141,4 g** (≤ 150 g) | |

Masse = Volumen aus Fusion × 1,27 g/cm³ (PETG, 100 % Füllung, obere Grenze). In Prusament PC (1,20 g/cm³) sind es 133,6 g. Volumen gesamt 111,31 cm³ (Version 11).

Hüllkörper (kein Druckteil, nur für Kollisions- und Bewegungsprüfung): `hinterachse-diff` (Diff-Gehäuse Ø 22 mit Nabe und den Lagern 8x12x3,5), `hinterachse-tellerrad` (GB4, Ring Ø 39 × 8), `hinterachse-kegelritzelwelle` (E2 Ø 5 mit Kegelritzel GB2 Ø 14 × 9 und den Lagern 5x11x4), `hinterachse-diffbecher` (N2), `hinterachse-antriebswelle-*` (N3), `hinterachse-radachse-*` (N1), `hinterachse-rad-*`, `hinterachse-sturzstange-*`, `hinterachse-daempfer-*`, neu `hinterachse-hauptzahnrad` (Review 2: `drehraum` = freier Zahnradraum zwischen den E2-Lagern und `hauptzahnrad` = Bedarf Mitnehmer GB3 + Hauptzahnrad GB5, siehe [Hüllkörper im Getriebe](#hüllkörper-im-getriebe-review-1--2-review-2--1)).

## Aufbau in Fusion

- **Ableitungen:**
  - Vom Skelett **v12** (maßgleich mit v10), nach dem Parametertest **v14** (maßgleich mit v12): alle 155 Favoriten-Parameter (in Fusion `<name>_Ref`, hier ohne `_Ref`), die 8 Bezugsebenen und alle 38 Hüllkörper außer dem Skelett-Körper `chassis-grundplatte`.
  - Von der Grundplatte **v11**: die Körper `chassis-grundplatte` (Druck und Alu), `chassis-oberdeck`, `chassis-mittelstuetze`, die vier Akkuanschläge und `chassis-fussflaechen` (Lochbilder und reservierte Fußflächen als Geometrie).
  - Die Benennung des Zeitleisten-Elements lautet weiterhin „Abgeleitet von open-rc-car-skelett v12“, obwohl die Ableitung auf **v14** zeigt (geprüft über `DeriveFeature` und die Parameter `*_Ref`). Fusion vergibt den Namen selbst; das Umbenennen über die API (`TimelineObject.name`) wird ohne Fehler ignoriert.
  - **Grundplatten-Schnittstellenmaße als Kopie (Nutzerentscheidung 2026-11-01):** Die Grundplatte hat **keine Favoriten-Parameter** (0 von 95). Ihre Parameter lassen sich deshalb nicht ableiten, ohne die Grundplatte zu ändern, was diese Anforderung ausschließt. Die Schnittstellenmaße (`ql_y`, `ql_dx`, `ql_l`, `ql_b`, `gp_paar_d`, `gp_getriebe_dx`, `gp_getriebe_y`, `od_getriebe_dx`, `od_loch_y`, `od_luft`) sind hier als eigene Parameter `ha_ql_y`, `ha_ql_dx` usw. mit dem Kommentar „Schnittstelle Grundplatte v11“ angelegt. Alle Lagen in X hängen trotzdem an `achse_x` (Skelett), die Oberdeck-Höhe an `antrieb_z + abdeckung_r + ha_od_luft`. Die Übereinstimmung mit den abgeleiteten Lochbildern ist gemessen (siehe [Schnittstellen](#schnittstellen-zur-grundplatte-mech-hac-003-mech-hac-007)). **Ändert sich die Grundplatte, muss die Hinterachse von Hand nachgezogen werden** (Parameter `ha_ql_*`, `ha_gp_*`, `ha_od_*`); besser markiert man dann dort die Schnittstellenparameter als Favoriten und leitet sie hier ab.
- **Komponenten:** je Teil eine Komponente nach der Dateikonvention, Druckausrichtung in der Beschreibung.
- **Aufbau der Körper:** wie im Skelett aus voll bestimmten Skizzen im Komponentenursprung (Rechteck mittig zum Ursprung oder Kreis um den Ursprung), symmetrischer Extrusion und einer Verschiebung bzw. Drehung (Move-Feature) mit Ausdrücken. Durchbrüche, Lagersitze und Einsatzbohrungen sind Werkzeugkörper, die mit „Kombinieren“ abgezogen werden. Das Getriebegehäuse wird an der Ebene Y = 0 geteilt (Split Body); die Einsätze für den Lagerbock werden danach je Hälfte abgezogen.
- **Prüfskripte:** 170 Skizzen, alle voll bestimmt. Zeitleiste 619 Elemente, ohne Fehler und Warnungen. 224 Benutzerparameter, alle mit Präfix `ha_` und Kommentar. Feste Zahlen in Features gibt es nur bei Winkeln von 0° (Verjüngung) und bei der Tangentengewichtung der Verrundung. Die Zugaben für durchgehende Schnitte laufen über `ha_durch`.
- **Kinematik im Modell:** Die Aufhängung ist über einen einzigen Parameter beweglich: `ha_ql_dphi` dreht den Querlenker gegen die Konstruktionslage. Lage und Drehung von Radträger, Rad, Radachse, Antriebswelle, Sturzstange und Dämpfer berechnen Ausdrücke aus dem Viergelenk Querlenker/Sturzstange (`ha_b_*`, `ha_rt_kappa`, `ha_w_*`, `ha_p_*`, `ha_e_*`, `ha_l_*`). Die Prüfstellungen sind `ha_dphi_aus` (Radhub −11,67 mm) und `ha_dphi_ein` (+23,33 mm); sie sind per Prüfskript so bestimmt, dass `ha_radhub` genau −`ausfederweg` bzw. +`einfederweg` ergibt. Nach dem Messen der Bausatzteile müssen sie neu bestimmt werden (Prüfmaß `ha_radhub` zeigt, ob sie noch stimmen).
- **Rechts = links gespiegelt:** Die rechten Teile entstehen mit denselben Ausdrücken und umgekehrtem Vorzeichen in Y und bei den Drehungen um X und Z.

## Getriebe- und Differentialgehäuse (MECH-HAC-002, -004, -005)

![Linke Gehäusehälfte von der Teilungsebene](images/hinterachse-getriebe-schnitt.png)

*Linke Hälfte, Blick von der Teilungsebene Y = 0 (Schnittbild): Zahnraum um Tellerrad und Diff (Ø 42 mm), in der Mitte der Sitz des Diff-Lagers 8x12x3,5 mit der Durchführung des Diff-Abtriebs, rechts der Ritzelraum und der hintere Lagersitz 5x11x4 der Kegelritzelwelle E2 im Lagerhals (seit Review 2 ohne Lippe, nach vorne offen), davor in Seitenansicht der Lagerbock; dazwischen liegt der freie Zahnradraum (5,0 mm). In den Ecken die Bohrungen der Verschraubung der Hälften.*

| Größe | Wert | Parameter |
|---|---|---|
| Diff-Achse | X −133,0 / Z **56,60** | `achse_x`, `antrieb_z` |
| Diff-Lager 8x12x3,5 | Mitte Y ±18,6, Sitz Ø 12,1 × 3,5, außen 2,01 mm Lippe mit Durchführung Ø 9 | `ha_diff_lager_y`, `ha_diff_lager_d`, `ha_lager_spiel`, `ha_diff_durchf_d` |
| Diff-Abtriebe (Kreuzstift N2) | Y **±31,86** | `diff_abtrieb_y` |
| Zahnraum | Ø 42 (Tellerrad Ø 39 + 2 × 1,5 mm Luft), Y ±16,85 | `ha_tellerrad_d`, `ha_zahn_luft` |
| Kegelritzelwelle E2 | Y **0** / Z **56,60**; hinteres Lager 5x11x4 im Gehäuse **X −112,0…−108,0** (Mitte −110, Sitz Ø 11,1 × 4, voll), vorderes im Lagerbock **X −103,0…−99,0** (Mitte −101, Sitz Ø 11,1 × 3,5, das Lager steht 0,5 mm vor und liegt am Becher an) | `ha_e2_einbau` = 23, `ha_e2v_x`, `ha_e2_lagerabstand` = 9,0 (abgeleitet) |
| Luft Tellerrad ↔ hinteres E2-Lager | in X **1,5 mm** (Tellerrad-Außenkreis r 19,5 bis Lagerrückseite r 21), Hüllkörper 3D 2,5 mm | `ha_e2_tr_luft` (Prüfmaß, ≥ `ha_zahn_luft`) |
| Lagerhals | Ø 15,1 von der Trommel (X −109,5) bis **X −108,0** = Vorderseite des hinteren Lagers; keine Lippe mehr (Nutzerentscheidung 2026-11-01 nach Review 2) | `ha_gh_hals_d`, `ha_gh_hals_x`, `ha_e2_lippe` = 0 |
| Lagerbock E2 | Lagerring Ø 15,1 × 3,5 (X −103,0…−99,5) mit durchgehendem Sitz Ø 11,1, keine Lippe; Steg 18 × 3,5; Fuß auf der Grundplatte X −109,5…−99,5, Y ±15,8, Z 29…32,3 (Querstege bis 34,28), 2 × M3 × 14 von vorne an (Y ±12,5 / Z 32,3) in Einsätze im Gehäuse | `ha_lb_*`, `ha_e2v_spalt` = 0,5 |
| Becheröffnung E2 / Kardanwelle | X **−84,0**, `kardan_spiel` = **0,00 mm** (unverändert, das Gehäuse ändert `getriebe_eingang` nicht) | Skelett |
| Außenmaße | Gehäuse X −156,5…−108,0, Y ±22,36, Z 29…92 (Turm), Trommel Ø 47; mit Lagerbock bis X −99,5 | `ha_gh_*`, `ha_lb_*` |

- **Zahneingriff einstellbar (MECH-HAC-002):** `ha_e2_einbau` verschiebt den hinteren E2-Lagersitz, den Lagerhals und den Ritzelraum in X (Einbaumaß Kegelritzel ↔ Tellerrad); der Lagerbock bleibt am Becher. `ha_e2_scheibe` (0,5 mm) und `ha_diff_spalt` (0,5 mm je Seite) sind die vorgesehenen Passscheiben-Stapel (Pos. 63). `ha_diff_versatz` verschiebt beide Diff-Lagersitze und den Zahnraum quer (Lage Tellerrad ↔ Kegelritzel). Im Probelauf wird zuerst mit Distanzscheiben zwischen Lager und Diff bzw. Kegelritzel eingestellt. Erst wenn das nicht reicht, werden die Parameter geändert und die Hälften neu gedruckt. Der Probelauf von Hand ist 🔧 nach Lieferung.
- **Teilung** in der Fahrzeugmitte (Y = 0): Jede Hälfte trägt ein Diff-Lager, die Lagerschale des hinteren E2-Lagers ist halbiert. Verschraubt mit 4 × M3 quer, Kopf in der linken Hälfte versenkt, Gewindeeinsatz in der rechten:
  - hinten unten (X −153 / Z 42): M3 × 25
  - vorne unten (X −112 / Z 41): M3 × 25
  - hinten oben im Turm (X −153 / Z 74): M3 × 20
  - vorne oben in der Oberdeck-Auflage (X −115 / Z 74): M3 × 14
- **Geschlossen (MECH-HAC-004):** Tellerrad, Kegelritzel und Diff liegen vollständig im Gehäuse. Offen sind nur die beiden Durchführungen der Diff-Abtriebe (Ø 9) und die Durchführung von E2. Das ist seit Review 2 der nach vorne offene hintere Lagersitz Ø 11,1, den das Lager selbst ausfüllt (vorher eine Lippe mit Ø 8). Hauptzahnrad bzw. Rutschkupplung zwischen den E2-Lagern liegen außerhalb des Gehäuses; sie deckt später die Zahnradabdeckung („Mittelantrieb“, Pflicht) ab. Es gibt keine Lüftungs- oder Erleichterungsöffnung. Prüfskript: Keine Einsatz- oder Schraubenbohrung erreicht den Zahnraum. Kleinste Wand zwischen Bohrung und Zahnraum (mit Ø 4 über die ganze Länge gerechnet, also pessimistisch): Verschraubung hinten unten 2,1 mm, vorne oben 2,0 mm, vorne unten 3,2 mm, hinten oben 3,5 mm; Einsätze Brücke 4,5 mm, Oberdeck 5,9 mm, Grundplatte 6,6 mm.
- **Wellendurchführungen und Becher:** Die Seitenwand endet 0,5 mm vor dem drehenden Diff-Becher N2 (`ha_n2_luft`, gemessen 0,50 mm). Die Becher N2 liegen wie beim TT-02B außerhalb des Gehäuses.

### E2-Lagerung und Lagerbock (Nutzerentscheidungen 2026-11-01, Review 1 🔴 1 und 🟡 1, Review 2 🔴 1)

![Lagerbock E2](images/hinterachse-lagerbock.png)

*Lagerbock vor dem Getriebegehäuse (von vorne rechts oben): Lagerring mit dem vorderen E2-Lager (blau, Hüllkörper). Es steht 0,5 mm vor und liegt am Becher an. Darunter der Steg 18 × 3,5 mm, der Fuß mit Querstegen und den beiden Schraubenaugen M3. Dahinter der Lagerhals des Gehäuses mit dem hinteren Lager (ohne Lippe), dazwischen der freie Zahnradraum (5,0 mm).*

![Hüllkörper im Getriebe](images/hinterachse-getriebe-huellen.png)

*Linke Gehäusehälfte mit den Hüllkörpern (blau): Diff mit Tellerrad, Kegelritzelwelle E2 mit Kegelritzel und beiden Lagern. Durchscheinend der Bedarf für Mitnehmer GB3 und Hauptzahnrad GB5 (`hinterachse-hauptzahnrad`, Ø 43,2 × 8 mm ab dem hinteren Lager). Er ragt um den Fehlbetrag von 3,0 mm in den Lagerbock (gelb). Rot: Becher der Kardanwelle (Skelett).*

- **Reihenfolge auf E2 wie TT-02B** (Anleitung S. 4, Schritt 2): Becher (X −99…−84, Hülle Kardanwelle) – vorderes Lager BB2 im Lagerbock (X −103,0…−99,0) – Zahnradraum für Mitnehmer GB3 und Hauptzahnrad GB5 bzw. Rutschkupplung (X −108,0…−103,0) – hinteres Lager BB2 im Gehäuse (X −112…−108) – Passscheibe 0,5 mm – Kegelritzel GB2 (X −121,5…−112,5). Das Hauptzahnrad sitzt damit zwischen den Lagern und nicht fliegend.
- **Zahnradraum (Nutzerentscheidung 2026-11-01 nach Review 2, Befund 🔴 1):** In Version 8 waren zwischen den Lagern nur 0,5 mm frei. Die Lippen auf der Zahnradseite (je 2 mm, Gehäuse X −108…−106, Lagerbock X −105,5…−103,5) sind jetzt weggelassen (`ha_e2_lippe` = 0). Das vordere Lager sitzt direkt am Becher (`ha_e2v_x` = Becher − halbe Lagerbreite), der Lagerbock bleibt mit `ha_e2v_spalt` = 0,5 mm hinter dem drehenden Becher, und das Lager steht um diesen Betrag vor (wie beim Radträger). Ergebnis: **`ha_hz_raum` 0,5 → 5,0 mm** (= `ha_e2_lager_frei`, Lagerabstand 9,0 mm). Der Steg des Lagerbocks liegt jetzt ganz vor dem Zahnradraum (X −103,0…−99,5), der Lagerhals endet an der Lagerseite (X −108,0). Zwischen X −108,0 und −103,0 ist der Ring um E2 von der Welle (r 2,5) bis r 23,6 frei drehbar. Das ist der Bauraum der Rutschkupplung, der Kopfkreis des Hauptzahnrads 70Z liegt bei r 21,6. Prüfung: Punkttest mit 4752 Punkten (11 Schnitte in X, r 2,6…23,5, je 36 Winkel) ohne einen Punkt in Gehäuse oder Lagerbock. Der Hüllkörper `drehraum` (Ø 47,2 × 5,0) hat zu Gehäuse und Lagerbock Interferenz 0 und Abstand 0,00 mm (Berührung an den Stirnseiten).
- **Fehlbetrag offen bis zur Messung (Nutzerentscheidung 2026-11-01):** Mitnehmer GB3 und Hauptzahnrad GB5 brauchen zusammen vorläufig mindestens 8 mm (`ha_hz_bedarf` = `e2_mitnehmer_l`). Es fehlen also **`ha_hz_fehl` = 3,0 mm**. Die Kette dahinter: Diff-Achse bis Becheröffnung braucht ca. Kegelritzel-Ferse 20,5 + Passscheibe 0,5 + BB2 4 + GB3/GB5 ≥ 8 + BB2 4 + Becher 15 ≥ 52 mm, das Skelett hat `getriebe_eingang` = 49 mm. Der unsicherste Wert ist `getriebe_eingang` (Kardanwelle E1 168 mm ohne Einstecktiefe). Die Maße passen auch untereinander nicht: Mit E2 = 41 mm [K1] und der Becheröffnung bei X −84 läge das Kegelritzel bei r 8…17 mitten im Zahnkranz des Tellerrads (r 11…19,5). Mindestens einer der Werte `getriebe_eingang`, `kardan_becher_l`, `ha_tellerrad_d` oder die Länge von E2 ist also falsch (Messpunkt 2). Getriebegehäuse und Lagerbock werden deshalb **erst nach dem Messen gedruckt**. Eine Korrektur von `getriebe_eingang` im Skelett kommt danach ggf. in einem eigenen PR.
- **Warum die Lippen nicht nach außen verlegt sind:** Hinter dem hinteren Lager liegen Passscheibe und Kegelritzel (0,5 mm Abstand, r bis 7), vor dem vorderen Lager liegt der Becher (Hülle r 10). Eine Lippe außen am Außenring (r 4,6…5,55) müsste das Lager um ihre Dicke zur Zahnradseite schieben und kostet damit genauso viel Zahnradraum wie innen. Die Lippen sind deshalb weggelassen. Wird nach dem Messen doch eine Lippe gebraucht, kostet `ha_e2_lippe` > 0 den Zahnradraum doppelt, weil der eine Parameter auf beide Sitze wirkt (Gehäuse und Lagerbock; 1 mm Lippe kostet 2 mm Zahnradraum, Review 3 🔵 1). Bei der Überarbeitung bekommen Gehäuse und Lagerbock deshalb getrennte Parameter; das ist die Voraussetzung für den einseitigen Anschlag (siehe [Vorgaben für die Überarbeitung](#vorgaben-für-die-überarbeitung-von-getriebegehäuse-und-lagerbock-nach-dem-messen)).
- **Axiale Sicherung ohne Lippen (Nutzerentscheidung):** Die Innenringe sitzen in einem Stapel auf der Welle: Becherschulter – Innenring vorne – Mitnehmer GB3 mit Hauptzahnrad GB5 – Innenring hinten – Passscheibe – Kegelritzel. Die Außenringe haben **keinen Anschlag**, weder im Gehäuse noch im Lagerbock. Die Axialkraft des Kegelritzels (4,4 N, mit Stoßfaktor 13 N, nach vorne gerichtet) läuft über Kegelritzel → Innenring hinten → GB3 → Innenring vorne → Becher von E2; gegen Verschieben hält nur die Reibung der Außenringe in ihren Sitzen. Vorgesehen ist, das **hintere Lager als Festlager** zu klemmen: Sein Sitz ist zwischen den beiden Gehäusehälften geteilt und hat den eigenen Passungsparameter `ha_e2h_spiel`. **Im exportierten Modell (Version 11) ist dieser Klemmsitz noch nicht vorhanden:** `ha_e2h_spiel` = +0,1 mm ist eine Spielpassung und klemmt nicht. Ein Übermaß von −0,05 mm lässt sich zwar ohne Zeitleistenfehler einstellen, liegt aber unter der Druckstreuung (ca. ±0,1 mm), und PETG kriecht unter Dauerlast und Wärme. Die axiale Festlegung ist damit **nicht nachgewiesen**. Das **vordere Lager ist Loslager** im Lagerbock (Sitz 3,5 mm tief). Der Becher kann nicht als Anschlag dienen: Er liegt 0,5 mm vor dem Lagerbock (`ha_e2v_spalt`) und würde E2 nur gegen eine Bewegung nach hinten begrenzen, also gegen die Lastrichtung, und dabei als drehendes Teil am stehenden Lagerbock schleifen. **Nutzerentscheidung 2026-11-01 (nach Review 3):** Vorläufig bleibt der Klemmsitz, 🔧 mit messbarem Abnahmekriterium im Probelauf: E2 axial mit ca. 40 N (≈ 3 × Stoßwert 13 N) in beide Richtungen belasten, auch nach 24 h bei ca. 60 °C; Verschiebung ≤ 0,05 mm. Bei der Überarbeitung nach dem Messen wird **verbindlich ein formschlüssiges Festlager** vorgesehen (siehe [Vorgaben für die Überarbeitung](#vorgaben-für-die-überarbeitung-von-getriebegehäuse-und-lagerbock-nach-dem-messen)).
- **Wände (Punkttest Version 11):** Hinterer Sitz X −112,0…−108,0 voll (4,0 mm), 972 Punkte auf r 5,6…7,5. Davon liegen 918 im Material, die übrigen 54 genau auf der Teilungsebene Y = 0 (Rand). Die Wand ist also ≥ 2,0 mm (Lagerhals Ø 15,1). Lagerbock: Sitz X −103,0…−99,5, alle 864 Punkte im Material, Wand 2,0 mm. Im Sitz (r ≤ 5,4) ist kein Material.
- **Tellerrad ↔ Lager:** `ha_e2_einbau` = Tellerrad-Radius 19,5 + Luft 1,5 + halbe Lagerbreite 2 = 23 mm. Das Lager liegt damit vollständig außerhalb des Tellerrad-Außenkreises, unabhängig davon, auf welcher Seite und in welcher Breite das Tellerrad sitzt (beides unbelegt). Nach dem Messen (Messpunkt 2) kann `ha_e2_einbau` kleiner werden, wenn das Tellerrad seitlich am Lager vorbeiläuft (Tellerrad Y +7,5…+15,5, Lager |Y| ≤ 5,5). `ha_e2_tr_luft` zeigt die Luft. Das bringt aber höchstens ca. 1 mm Zahnradraum, weil das Kegelritzel mitwandert und seine Lage vom Zahneingriff vorgegeben ist.
- **Lagerbock:** eigene Komponente `hinterachse-getriebegehaeuse-lagerbock` (Druckteil). Lagerring Ø 15,1 × 3,5 mm (X −103,0…−99,5) mit durchgehendem Sitz Ø 11,1. Die Vorderseite liegt 0,5 mm hinter dem Becher von E2 (`ha_e2v_spalt`, gemessen **0,50 mm** zur Hülle der Kardanwelle). Das Lager liegt am Becher an (Hüllkörper Lager ↔ Kardanwelle: Berührung). Die Becheröffnung bleibt bei X −84 (`kardan_spiel` 0,00). Der Steg ist **18 × 3,5 mm** (`ha_lb_steg_b` 18, vorher 14 × 6). Die Breite folgt aus der Lastrechnung, damit die Sicherheit bei der kleineren Dicke gleich bleibt. Der Fuß steht auf der Grundplatte (Berührung, keine Überschneidung) und liegt hinten an den vorderen Füßen des Gehäuses an (X −109,5). Er reicht bis Z 32,3, die Querstege bis Z 34,28 (`ha_lb_quer_z`, 0,5 mm unter dem Bauraum der Rutschkupplung). Damit bleibt der Fuß unter dem Zahnradraum: Drehraum ↔ Lagerbock ohne Überschneidung. Die Querstege halten 0,5 mm zum Bauraum der Rutschkupplung, der Fuß (Z 32,3) mindestens 0,7 mm, zum Kopfkreis des Hauptzahnrads (Z ≥ 35,0) mindestens 2,7 mm. Befestigung: 2 × M3 × 14 Zylinderkopf von vorne durch die Schraubenaugen in Gewindeeinsätze in den Gehäusefüßen (Y ±12,5 / Z 32,3, Einsatz X −115,5…−109,5). Die Schrauben sitzen so, dass Kopf und Auge unter dem Bauraum der Rutschkupplung bleiben. Die Einsätze liegen 1,5 mm neben den Einsätzen der Grundplatte (Y ±18) und 1,3 mm über der Plattenoberseite.
- **Abnehmbar für die Rutschkupplung:** Die zwei Schrauben lösen, dann lässt sich der Lagerbock mit E2 herausnehmen, wenn das Gehäuse geöffnet ist (siehe Montagefolge). Er berührt Motor (24,6 mm), Motorritzel (12,3 mm), Kardanwellen-Becher (0,5 mm) und Querlenkerböcke (11,2 mm) nicht.
- **Kipp- und Lagerlast:** siehe [Lasten](#lasten-mech-hac-016).

### Hüllkörper im Getriebe (Review 1 🟡 2, Review 2 🔴 1)

| Hüllkörper | Maße (vorläufig) | Lage | Parameter | kleinster Abstand |
|---|---|---|---|---|
| Diff-Gehäuse mit Nabe | Ø 22 × 32,7 (Y ±16,35), Nabe Ø 8 bis Y ±20,35 | Diff-Achse | `ha_diff_d`, `ha_diff_nabe_d`, `ha_diff_spalt` | Gehäuse 0,50 mm (Passscheibe), Kegelritzelwelle 0,50 mm |
| Diff-Lager 8x12x3,5 (2) | Ring Ø 12/8 × 3,5, Y ±(16,85…20,35) | in den Sitzen | `ha_diff_lager_*` | Sitz (Berührung, gewollt) |
| Tellerrad GB4 | Ring Ø 39/22 × 8, Y +7,5…+15,5 (Seite vorläufig links) | am Diff | `ha_tellerrad_d`, `ha_tellerrad_b`, `ha_tellerrad_y0` | Gehäuse 1,35 mm (Zahnraumdecke), hinteres E2-Lager 2,50 mm, Kegelritzel 0,5 mm |
| Kegelritzelwelle E2 mit Kegelritzel GB2 | Welle Ø 5 X −121,5…−99,0, Kegelritzel Ø 14 × 9 (X −121,5…−112,5) | Y 0 / Z 56,6 | `ha_e2_welle_d`, `ha_ritzel_d`, `ha_ritzel_l`, `ha_e2_scheibe` | Gehäuse 0,50 mm (Schulter Ritzelraum), Diff 0,50 mm, Becher Kardanwelle (Berührung = Becher von E2, gewollt) |
| E2-Lager 5x11x4 (2) | Ring Ø 11/5 × 4 | X −112…−108 und −103…−99 | `ha_e2_lager_*`, `ha_e2v_x` | Sitze (Berührung, gewollt); vorderes Lager ↔ Becher Kardanwelle Berührung (Becherschulter, gewollt) |
| **Drehraum** zwischen den Lagern (`hinterachse-hauptzahnrad` / `drehraum`) | Ring Ø 47,2 (`rk_d`) / Ø 5 × **`ha_hz_raum_pruef`** = 5,0 | X −108,0…−103,0 | `ha_hz_x0`, `ha_hz_raum_pruef` | Gehäuse, Lagerbock, beide Lager: 0,00 (Berührung, keine Überschneidung); Grundplatte 4,0 mm |
| **Hauptzahnrad-Bedarf** GB3 + GB5 (`hinterachse-hauptzahnrad` / `hauptzahnrad`) | Ring Ø 43,2 (`hz_d`, Kopfkreis 70Z) / Ø 5 × `ha_hz_bedarf` = 8 | X −108,0…−100,0 | `ha_hz_x0`, `ha_hz_bedarf` | **gewollte Überschneidung = Fehlbetrag:** Lagerbock 1110,0 mm³, vorderes E2-Lager 226,2 mm³; Gehäuse 0,00; Kardanwelle 1,0 mm; Motorritzel 5,0 mm; Grundplatte 6,0 mm |
| Bauraum Rutschkupplung | `mittelantrieb-rutschkupplung` aus dem Skelett (Ø 47,2, X −109…−84) | um E2 | Skelett `rk_*` | gewollte Überschneidung, siehe unten |

Interferenz der Hüllkörper mit Gehäuse und Lagerbock: **0**, außer der gewollten Überschneidung des Hauptzahnrad-Bedarfs mit Lagerbock und vorderem Lager (Fehlbetrag). Berührungen gibt es nur in den Lagersitzen und an den Stirnseiten des Drehraums. **Schutz gegen negativen Zahnradraum (Review 2 🔵 1):** Die Breite des Drehraums ist `ha_hz_raum_pruef` = (`ha_hz_raum` + |`ha_hz_raum`|) / 2. Für `ha_hz_raum` ≤ 0 wird sie 0, und die Extrusion `drehraum` schlägt in der Zeitleiste fehl. Getestet: `ha_e2_lippe` 3 mm (`ha_hz_raum` −1,0) und 2,5 mm (0,0) geben jeweils einen Fehler am Element `drehraum`, zurück auf 0 ohne Fehler. Das Prüfskript (Interferenz) muss außerdem zeigen: Gehäuse ↔ Lagerbock 0, Drehraum ↔ Gehäuse/Lagerbock 0 und `ha_hz_fehl` ≤ 0. Das letzte gilt erst nach dem Messen.

### Schnittstelle zum Mittelantrieb (MECH-HAC-005)

- Nach vorne reicht das Gehäuse nur mit dem Lagerhals des hinteren E2-Lagers über X −109,5 hinaus, bis X −108,0 (`ha_hals_l` = **1,0 mm** in den Bauraum der Rutschkupplung, Ø 15,1 um E2). Davor liegt der freie Zahnradraum, dann der Lagerbock (Fuß X −109,5…−99,5, Lagerring und Steg X −103,0…−99,5). Lagerring, Steg und die Oberseite der Querstege liegen im Bauraum von Rutschkupplung und Zahnradabdeckung. Das ist nach Nutzerentscheidung 2026-11-01 gewollt, soweit unvermeidbar: Das vordere Lager muss vor dem Becher sitzen, und jede Verbindung zu ihm kreuzt den Bauraum, der E2 bis r 23,6 umschließt. Der Steg liegt dabei vor dem Zahnradraum, nicht in ihm.
- **Interferenz mit `mittelantrieb-*` (alle gewollt, dokumentiert):**
  - Gehäuse (Lagerhals) ↔ Rutschkupplung: 41,2 mm³ je Hälfte (Version 8: 170,0); dasselbe Volumen auch ↔ Zahnradabdeckung, weil deren Hülle den Bauraum der Rutschkupplung einschließt.
  - Lagerbock ↔ Rutschkupplung: 1424,6 mm³; Lagerbock ↔ Zahnradabdeckung: 2022,7 mm³ (Version 8: 2015,1 / 2659,7).
  - Hüllkörper E2 (Welle, hinteres Lager, vorderes Lager) ↔ Rutschkupplung und Zahnradabdeckung: 196,3 / 75,4 / 301,6 mm³ (Bauraum umschließt E2).
  - Hüllkörper `drehraum` bzw. `hauptzahnrad` ↔ Rutschkupplung und Zahnradabdeckung: 8650,5 bzw. 11568,9 mm³ (liegen im Bauraum).
  - Nicht berührt: Motor (Lagerbock 24,6 mm, Gehäuse 33,1 mm), Motorritzel (Lagerbock 12,3 mm, Gehäuse 14,5 mm), Kardanwelle (Lagerbock 0,5 mm zum Becher, Gehäuse 9,0 mm).
- **`rk_luft`:** im Skelett **−9,0 mm** (Rutschkupplung um den Becher: Bauraum 25 mm − Lager BB2 4 − Mitnehmer 8 − Rutschkupplung 22); in Version 6 mit dem Lagerhals −11,0 mm; in Version 8 mit Lippen −29,5 mm. Jetzt liegt die Rutschkupplung nach Nutzerentscheidung **zwischen den E2-Lagern**. Frei sind dort **`ha_hz_raum` = 5,0 mm** (Version 8: 0,5 mm), zwischen den Innenringen ebenso 5,0 mm (`ha_e2_lager_frei`). `ha_rk_luft` = 5,0 − Mitnehmer 8 − Rutschkupplung 22 = **−25,0 mm**. Für das Bausatz-Hauptzahnrad GB5 mit Mitnehmer GB3 fehlen **3,0 mm** (`ha_hz_fehl`), offen bis zur Messung (siehe oben). Vorgaben an „Mittelantrieb“ unten.
- **Folge für Zahnebene und Motor (Review 2 🟡 1):** Im Skelett liegt die Zahnebene bei X −89 (`ritzel_x` = `rk_x_hinten` + `hz_ebene` 20), das Motorritzel bei X −95…−83 (Hülle mit Zuschlag). Mit dem Zahnrad zwischen den Lagern liegt die Zahnebene in der Mitte des Zahnradraums bei **X −105,5**, also **16,5 mm weiter hinten**. Mit dem Bedarf von 8 mm ab dem hinteren Lager wären es X −104 bzw. 15 mm. Bleibt der Motor stehen, reicht seine Welle nicht hin: `motor_welle_reserve` −3 → ca. **−19,5 mm**. Der Motor muss also um ca. 16,5 mm nach hinten wandern, Flansch von X −75 auf ca. −91,5. Geprüft mit verschobenen Kopien der Skelett-Hüllen (nicht im Modell gespeichert):

| Verschiebung | Motor (X −91,5…−39,5) | Motorritzel-Hülle (X −111,5…−99,5) |
|---|---|---|
| −16,5 mm | Gehäuse 16,8 mm, Lagerbock 8,1 mm, vorderes Lager 9,0 mm, Querlenkerbock 18,5 mm, Kardanwelle 0,5 mm (wie bisher), Oberdeck 15,2 mm, Grundplatte 9,6 mm: frei | Gehäuse (Trommel) **Überschneidung 26,6 mm³**, Lagerbock 11,4 mm, Querlenkerbock rechts vorne 1,7 mm, Kardanwelle 10,4 mm; mit Drehraum/Hauptzahnrad überschneidet sie sich (Zahneingriff, gewollt) |
| −15,0 mm | Gehäuse 18,2 mm, Lagerbock 9,6 mm: frei | Gehäuse **Überschneidung 5,3 mm³**, Querlenkerbock 1,7 mm |

  Bauraum: Der Motor findet hinter X −75 Platz, ohne Lagerbock oder Gehäuse zu berühren (kleinster Abstand 8,1 mm zum Lagerbock). Das Motorritzel kommt mit seiner Hülle (8 mm netto + 2 × 2 mm Zuschlag) aber bis an die Trommel des Gehäuses. Netto (X −109,5…−101,5) liegt es genau an der Gehäusevorderseite X −109,5. Die Lösung (Ritzelbreite, Lage der Zahnebene im Zahnradraum, Motorhalter, Zahnradabdeckung) gehört zu „Mittelantrieb“ und hängt an der Messung. Die Vorgaben stehen unten und in `docs/plan.md`.

## Querlenkerböcke (MECH-HAC-007)

- Je Bock: Fußfläche 10 × 16 mm genau auf der reservierten Fläche (X −156…−146 bzw. −120…−110, Y ±27…±43), oben rund (Ø 16 um die Achse). Damit ist das Profil glatt, ohne Innenecke. Höhe bis Z 48, also 4 mm über die reservierte Höhe (Z 44) hinaus. Erlaubt laut MECH-HAC-007, weil dort nichts kollidiert.
- 2 × M3 × 8 Senkkopf von unten in Gewindeeinsätze (Ø 4 × 6) auf den Lochpaaren Y ±30,5 / ±39,5.
- Querlenkerachse: **Zylinderstift ISO 2338 3 m6 × 40** je Seite. Er steckt in Sacklöchern Ø 3,1 × 7,25 mm, die zur Achse hin offen sind. Sind die Böcke verschraubt, ist der Stift axial gefangen (0,25 mm Luft je Ende). Querlenkerrohr Ø 3,2 mm, 0,5 mm Axialspiel je Seite.
- **Lösbar von unten (MECH-CHA-018):** Alle Bockschrauben kommen von unten. Über den Böcken liegen weder Gehäuse noch Brücke noch Oberdeck (Abstände unten).

## Querlenker, Radträger, Sturzstange (MECH-HAC-006, -008, -009)

- **Querlenker:** Platte 5 mm, innen 25 mm breit mit Rohr Ø 7 um den Stift, außen eine Gabel 18,4 mm breit mit Schlitz für die Lasche des Radträgers (0,2 mm Spiel je Seite). Bolzen außen M3 × 25 mit Stoppmutter, parallel zu X. Die äußere Platte liegt 2 mm unter der Querlenkerebene (`ha_ql_platte_z`), sonst berührt sie beim Ausfedern den Becher der Radachse. Nach hinten führt eine Lasche (8 × 8 mm) zum unteren Dämpferauge, mit Gewindeeinsatz für M3 × 14.
- **Radträger:** Lagernabe Ø 16,1 mit 2 Lagern 5x11x4 (Sitze Ø 11,1, `ha_lager_spiel`), Lagerabstand Mitte–Mitte **6 mm** (`ha_radlager_abstand`, Steg 2 mm). Die Lager stehen 0,5 mm über die Nabe vor (`ha_rt_spalt`). So läuft der Becher N1 innen und der Sechskant-Mitnehmer außen am Innenring, nicht an der Nabe. Unten eine Lasche Ø 8 × 8 mit Bolzen M3 zum Querlenker, 16,5 mm unter der Radmitte. Oben ein Block 8 × 8 × 8 mit Gewindeeinsatz für den Kugelkopf der Sturzstange (Kugelmitte 10 mm hinter, 27 mm innerhalb und 22,5 mm über der Radmitte). Der Radträger liegt mit der Nabe in der Felge (Felgeninnenraum Ø 50 vorläufig).
- **Vorspur fest:** Die Lagernabe ist um `ha_vorspur` = 2,0° um die Hochachse gedreht. Bolzen und Kugelkopf bleiben parallel zu X. Gemessen: `ha_vorspur_ist` = **2,000°** in Konstruktionslage.
- **Sturzstange:** Spannschloss aus dem Tamiya-Satz 54539 mit Kugelpfannen auf Kugelköpfen 5 mm. Innen an der Vorderseite der Dämpferbrücke (Kugelmitte X −150,5 / Y ±29 / Z 78), außen am Radträger (X −143 / Y ±77,4 / Z 64,0). Kugelmitte bis Kugelmitte **50,95 mm**.
  - **Abweichung:** Der Neo-Scorcher-Bausatz hat **keine Sturzstangen**. Er hat hinten starre obere Lenker C2 (Anleitung S. 10, Schritt 17), und seine 4 Kugelköpfe MB8 braucht die Lenkung. Sturzstangen und Kugelköpfe sind deshalb Zukauf (Annahme im Anforderungsdokument: „fehlende Längen als Tamiya-Ersatzteil, z. B. 54539“). Der Satz 54539 enthält laut Händler die Spannschlösser der oberen Lenker hinten. Länge und Pfannen bei Lieferung prüfen.

### Geometrie in Konstruktionslage (MECH-HAC-008, -009)

| Maß | Wert gemessen | Soll |
|---|---|---|
| Radmitte | Y **±104,00** / Z **41,00** (`ha_w_y`, `ha_w_z`) | ±104 / 41 |
| `radachse_h_spiel` (Skelett) | −0,00 mm | 0 ± 0,5 |
| Gelenkabstand N3 (Kreuzstift zu Kreuzstift) | 59,949 mm (`ha_gelenk_dl` = −0,051 mm durch Sturz und Vorspur) | 60 |
| Vorspur | **2,000°** je Rad (`ha_vorspur_ist`) | `ha_vorspur` = 2° |
| Sturz | **−0,999°** (`ha_sturz_ist`) | `ha_sturz` = −1° |
| Querlenker | Achse innen Y ±35 / Z 40, Bolzen außen Y ±91,71 / Z 24,71, Länge 58,74 mm, Winkel −15,09° | |
| Dämpfer | unten Y ±69,76 / Z 30,63, oben Y ±51,70 / Z 101,89 (beide X −166,0), Augenabstand 73,51 mm, oben 14,2° nach innen geneigt | |

**Sturz einstellen (MECH-HAC-009):** Die Sturzstange dreht den Radträger um den unteren Bolzen. Gerechnet mit festem Querlenker (Längenänderung der Sturzstange Kugelmitte zu Kugelmitte):

| Sturz | −5° | −4° | **−3°** | −2° | **−1°** | **0°** | +1° | +2° | +3° |
|---|---|---|---|---|---|---|---|---|---|
| Δ Länge Sturzstange (mm) | +2,41 | +1,79 | **+1,19** | +0,59 | **0** | **−0,58** | −1,14 | −1,69 | −2,23 |

Für −3° bis 0° braucht es also +1,19 bis −0,58 mm. Ein Spannschloss mit Rechts-/Linksgewinde hat bei 4 mm Mindesteinschraubtiefe und ca. 7 mm Gewindetiefe der Pfannen etwa ±3 mm Verstellweg (`ha_sturzstange_verstell`, vorläufig). Das reicht für ca. −6° bis +4°. Kollisionsprüfung mit `ha_sturz` = −3° und 0° in Konstruktionslage: Zeitleiste ohne Fehler, **0 ungewollte Überschneidungen**; kleinster Abstand Sturzstange ↔ Rad 1,41 mm (−3°) bzw. 1,16 mm (0°).

**Sturz-Grenzlagen über den Federweg (Review 1 🔵 1, eigene Messung):** `ha_sturz` −3° bzw. 0° kombiniert mit den Prüfstellungen `ha_dphi_aus`/`ha_dphi_ein` (die für −1° bestimmt sind, deshalb weicht der Radhub um bis zu 0,2 mm ab):

| Sturz eingestellt | Stellung | Radhub | Sturz ist | Querlenker ↔ Rad | Sturzstange ↔ Rad | Querlenker ↔ Radachse | ungewollte Überschneidungen |
|---|---|---|---|---|---|---|---|
| −3° | eingefedert | +23,16 mm | −2,18° | **0,25 mm** | 1,56 mm | 4,56 mm | 0 |
| −3° | ausgefedert | −11,68 mm | −2,56° | 2,25 mm | 0,76 mm | 2,09 mm | 0 |
| 0° | ausgefedert | −11,66 mm | +1,39° | 2,36 mm | **0,58 mm** | 1,05 mm | 0 |
| 0° | eingefedert | +23,42 mm | +0,26° | 0,69 mm | 1,65 mm | 4,56 mm | 0 |

Die knappsten Werte (0,25 mm und 0,58 mm) hängen am vorläufigen Felgeninnenraum Ø 50 und an der Pfannen-Hülle; sie stehen bei den Messpunkten. **Modellvereinfachung:** `ha_sturz` stellt im Modell die Lage des unteren Bolzens neu ein und ändert damit auch die Querlenkerlänge (`ha_ql_l` hängt an `ha_b0_*`). Physikalisch ändert nur die Sturzstange ihre Länge, der Querlenker bleibt gleich. Die Werte der Grenzlagen sind deshalb Näherungen; sie zeigen, dass der Einstellbereich ohne Kollision nutzbar ist, aber mit wenig Luft am Rad.

## Federweg und Kinematik (MECH-HAC-010, -011, -012, -014)

Bewegungsprüfung in Fusion über `ha_ql_dphi` in drei Stellungen. Je Stellung: Zeitleiste neu berechnet, `analyzeInterference` über alle Körper (ohne die ersetzten Skelett-Hüllen, siehe [Interferenz](#interferenz-und-abstände)), Mindestabstände der bewegten Teile.

![Ausgefedert](images/hinterachse-federweg-aus.png)

*Ausgefedert (Radhub −11,67 mm), von hinten. Der Dämpfer ist voll ausgezogen (80,0 mm).*

![Eingefedert](images/hinterachse-federweg-ein.png)

*Eingefedert (Radhub +23,33 mm), von hinten. Der Dämpfer ist bis auf 60,09 mm eingefahren (Hub 19,91 von 20 mm).*

| Stellung | Radhub | Querlenkerwinkel | Radmitte Y / Z | Gelenkabstand N3 | Änderung zur Konstruktionslage | Wellenwinkel | Vorspur | Sturz | Dämpfer (Augenabstand) | Überschneidungen ungewollt |
|---|---|---|---|---|---|---|---|---|---|---|
| ausgefedert (`ha_dphi_aus` = −12,47°) | −11,667 mm | −27,56° | 99,07 / 29,33 | 59,618 mm | **−0,331 mm** | **27,22°** | 2,000° | +0,03° | **80,00 mm** (= ausgefedert, Endanschlag) | **0** |
| Konstruktionslage | 0 | −15,09° | 104,00 / 41,00 | 59,949 mm | 0 | 14,84° | 2,000° | −1,00° | 73,51 mm | **0** |
| eingefedert (`ha_dphi_ein` = +22,86°) | +23,333 mm | +7,78° | 105,35 / 64,33 | 59,820 mm | **−0,129 mm** | −7,56° | 2,000° | −0,54° | **60,09 mm** (Hub 19,91 mm) | **0** |

- **Den Federweg begrenzt der Dämpfer (MECH-HAC-010):** Der obere Dämpferpunkt ist so berechnet (`ha_du_z`), dass der Dämpfer bei −11,67 mm genau ausgezogen ist. Bei +23,33 mm sind 19,91 mm des Hubs von 20 mm verbraucht (`ha_daempfer_reserve` = 0,09 mm). Der Endanschlag im Dämpfer liegt also 0,09 × 1,76 ≈ 0,15 mm Radhub hinter dem Ende des Federwegs. In beiden Endlagen schlägt kein Querlenker, Radträger und keine Welle an. Die kleinsten Abstände stehen in der Tabelle unten.
- **Hebelverhältnis Rad : Dämpfer:** `ha_hebel` = 35 / 19,91 = **1,76** über den Federweg gemittelt. TT-02B hinten (aus der Anleitung abgeschätzt, vorläufig): **ca. 1,5** (Spanne 1,4–1,6), `ha_hebel_tt02b`. Herleitung: Das untere Dämpferauge sitzt am Querlenker auf der mittleren von drei Bohrungen kurz vor dem äußeren Bolzen, ca. 0,8 der Querlenkerlänge von der inneren Achse (S. 10 Schritt 16/17, S. 11 Schritt 19, S. 14 Schritt 26). Die Radmitte liegt ca. 1,15 Querlenkerlängen außen, weil Radachse N1 und Lager außerhalb des Bolzens MB1 sitzen (S. 11 Schritt 18/19). Der Dämpfer ist oben um ca. 15° nach innen geneigt (Halter A4, S. 10/14). Daraus i ≈ 1,15 / 0,8 / cos 15° ≈ 1,49; mit der inneren bzw. äußeren Bohrung 1,4–1,6. **1,76 ≥ 1,6**: Mit denselben Dämpfern wird der Federweg nicht kleiner als beim TT-02B. Hub und Länge der CVA-Dämpfer sind vorläufig (🔧 messen). **Folge für die Federung (Review 1 🔵 5):** Die Federrate am Rad ist die Dämpfer-Federrate geteilt durch i². Gegenüber dem TT-02B (i ≈ 1,5) ist sie mit i = 1,76 um den Faktor (1,5 / 1,76)² ≈ 0,73 kleiner, die Hinterachse wird mit den Bausatzfedern also ca. 27 % weicher. Für die Abstimmung am Prototyp heißt das: härtere Federn bzw. dickeres Öl einplanen.
- **Untere Dämpferaufnahme (MECH-HAC-014):** Bolzen M3 × 14 durch das Dämpferauge in den Gewindeeinsatz der Querlenkerlasche, 36 mm von der Querlenkerachse (`ha_ql_dl`). Lage: X −166 / Y ±69,76 / Z 30,63. Sie geht über `ha_l_*` in Hebelverhältnis und `ha_du_z` ein.
- **Antriebswelle N3 bleibt im Eingriff (MECH-HAC-011):** Der Gelenkabstand ändert sich über den Federweg um höchstens **0,33 mm** gegen die Konstruktionslage (bzw. 0,38 mm gegen die Knochenlänge 60 mm). Zulässig sind ±2 mm (`ha_knochen_schiebeweg`, vorläufig). Der Wellenwinkel ist ausgefedert 27,2° wie im Skelett (Risiko vom Nutzer akzeptiert). 🔧 Bei Lieferung prüfen, dass der Knochen voll ausgefedert nicht herausfällt.
- **Spuränderung (MECH-HAC-012):** Querlenkerachse und unterer Bolzen sind parallel zu X. Der Radträger dreht sich deshalb nur um X, und die Vorspur bleibt über den ganzen Federweg **2,000°** (Änderung < 0,001°, gefordert ≤ 0,5°). Sturz: +0,03° ausgefedert, −1,00° statisch, −0,54° eingefedert. Die Sturzänderung ist also klein (≤ 1,03°) und geht in beiden Richtungen zu weniger negativem Sturz.

**Kleinste Abstände der bewegten Teile** (links = rechts, Hüllkörper mit Zuschlag; gewollte Spalte in Klammern):

| Paar | ausgefedert | Konstruktionslage | eingefedert |
|---|---|---|---|
| Querlenker ↔ Becher N1 | 1,41 | 4,54 | 4,56 |
| Querlenker ↔ Antriebswelle N3 | 2,82 | 4,74 | 6,18 |
| Querlenker ↔ Diff-Becher N2 | 4,6 | 4,6 | 4,6 |
| Querlenker ↔ Grundplatte | 2,16 | 5,26 | 7,5 |
| Querlenker ↔ Rad | 2,34 | 2,01 | **0,55** |
| Radträger ↔ Antriebswelle N3 | 1,75 | 4,97 | 5,64 |
| Sturzstange ↔ Rad | **0,64** | 1,24 | 1,62 |
| Sturzstange ↔ Getriebegehäuse | 2,43 | 1,58 | 1,84 |
| Dämpfer ↔ Rad | 4,62 | 7,42 | 8,68 |
| Dämpfer ↔ Grundplatte | 9,22 | 14,38 | 24,83 |
| Antriebswelle ↔ Getriebegehäuse | 6,3 | 7,71 | 8,58 |
| gewollt: Radträger ↔ Gabel Querlenker | (0,2) | (0,2) | (0,2) |
| gewollt: Radträger ↔ Becher N1 / Sechskant (Rad) | (0,5) | (0,5) | (0,5) |
| gewollt: Querlenkerrohr ↔ Bock | (0,5) | (0,5) | (0,5) |
| gewollt: Dämpferauge ↔ Brücke / Querlenkerlasche (Scheibe) | (0,5) | (0,5) | (0,5) |
| gewollt: Pfanne ↔ Kugelkopfblock / Brücke (Kugelkopf dazwischen) | (0,89) | (0,89) | (0,89) |

Die knappsten Werte (Querlenker ↔ Rad 0,55 mm eingefedert, Sturzstange ↔ Rad 0,64 mm ausgefedert) hängen am vorläufigen Felgeninnenraum Ø 50 mm und am Hüllkörper der Pfanne. Sie gehören zu den Messpunkten bei Lieferung.

## Dämpferbrücke (MECH-HAC-013)

- Platte 6 mm (`ha_db_dicke`) quer an der Rückseite des Getriebegehäuses (X −162,5…−156,5), wie der Halter A4 des TT-02B. 4 × M3 × 10 Zylinderkopf von hinten in Gewindeeinsätze im Gehäuse (Y ±10 / Z 36 und Z 86 im Turm).
- Vorne die Kugelköpfe der Sturzstangen (Gewindeeinsatz, Y ±29 / Z 78), hinten die Dämpferaugen (M3 × 20 + Stoppmutter, Y ±51,7 / Z 101,89). Der Dämpfer sitzt also **hinter** der Achse statt wie die vorläufige Skelett-Hülle 24 mm davor. Grund: Vor der Achse liegen Oberdeck, Zahnradabdeckung und Rutschkupplung; dahinter ist frei. Die Brücke trennt Sturzstange (vorne) und Dämpfer (hinten). Vom Skelett abweichende Dämpferlage: unten X −166 / Y ±69,76 / Z 30,63, oben X −166 / Y ±51,70 / Z 101,89, oben 14,2° nach innen geneigt.
- **Fräsgerecht:** Prüfskript 2,5D: nur Ebenen parallel oder senkrecht zu X, nur Zylinder parallel zu X, keine anderen Flächentypen. Radien: Bohrungen 1,6, Einsätze 2,0, Innenecken 2,0 (`ha_db_r`), Augen 7,0 mm. Alle Innenradien ≥ 1,5 mm, keine Hinterschnitte, Werkzeugzugang von einer Seite.
- **Abstände:** Brücke ↔ Skelett 47,5 mm (nächster Körper Rutschkupplung), ↔ Grundplatte **2,00 mm**, ↔ Oberdeck 34,5 mm, ↔ Mittelstütze und Akkuanschläge > 79 mm; Motor, Zahnradabdeckung und Akku-Entnahmeweg ≥ 47,5 mm. Interferenz 0.

## Schnittstellen zur Grundplatte (MECH-HAC-003, MECH-HAC-007)

| Prüfung | Ergebnis (gemessen am Modell) |
|---|---|
| Gewindeeinsätze Gehäuse unten | (−152,0 / ±18,0) und (−114,0 / ±18,0), Z 29…35 = Lochbild Grundplatte |
| Oberdeck-Auflage | Einsätze (−115,0 / ±5,0), Auflagefläche **Z 84,200** = Unterkante Oberdeck |
| Gehäuse unter Z 44 | innerhalb Y ±22,36 (< ±24,86), Fußflächen frei (Abstand 4,64 mm) |
| Einsätze Böcke | (−151,0 / ±30,5; ±39,5) und (−115,0 / ±30,5; ±39,5) = Lochbild Grundplatte |
| Interferenz Gehäuse ↔ Grundplatte, Fußflächen, Oberdeck | 0 (Gehäuse steht auf der Platte, Oberdeck liegt auf den Auflagen: nur Berührung) |
| Interferenz Böcke ↔ Fußflächen | gewollt: Der Bock steht in der reservierten Fläche (2166,7 mm³ je Bock = Bockvolumen bis Z 44) |

## Interferenz und Abstände

Fusion `analyzeInterference` über alle Körper des Designs ohne `grundplatte-alu` (liegt am selben Ort wie die Druckteile) und ohne die Skelett-Hüllen, die diese Baugruppe ersetzt: `antrieb-getriebe-hinten`, `fahrwerk-daempfer-hl/-hr`, `fahrwerk-rad-hl/-hr`, `antrieb-radachse-hl/-hr`, `antrieb-antriebswelle-hl/-hr`, `fahrwerk-radraum-hl/-hr`, `antrieb-wellenraum-hl/-hr`. An ihre Stelle treten die echten Teile und die bewegten Hüllkörper dieser Baugruppe, die in allen drei Stellungen geprüft werden. Ergebnis in allen drei Stellungen (Version 11, neu gemessen): **29 Überschneidungen mit Teilen der Hinterachse, alle gewollt, 0 ungewollt**, Zeitleiste ohne Fehler (Version 6: 14, Version 8: 22; neu sind die 7 Überschneidungen der Hüllkörper `drehraum` und `hauptzahnrad`).

| Überschneidung | Anzahl | Volumen je Fall | Begründung |
|---|---|---|---|
| Getriebegehäuse ↔ Rutschkupplung / Zahnradabdeckung | 2 + 2 | 41,2 mm³ | Lagerhals E2 im Bauraum der Rutschkupplung (MECH-HAC-005) |
| Lagerbock ↔ Rutschkupplung / Zahnradabdeckung | 1 + 1 | 1424,6 / 2022,7 mm³ | Lagerbock im Bauraum (MECH-HAC-005, Nutzerentscheidung 2026-11-01) |
| Hauptzahnrad-Bedarf ↔ Lagerbock / vorderes E2-Lager | 1 + 1 | 1110,0 / 226,2 mm³ | **Fehlbetrag 3,0 mm** (`ha_hz_fehl`), offen bis zur Messung (Nutzerentscheidung 2026-11-01) |
| Drehraum / Hauptzahnrad-Bedarf ↔ Rutschkupplung / Zahnradabdeckung | 2 + 2 | 8650,5 / 11568,9 mm³ | Hüllkörper liegen im Bauraum |
| Drehraum ↔ Hauptzahnrad-Bedarf | 1 | 7230,5 mm³ | zwei Hüllkörper für denselben Raum (frei bzw. Bedarf) |
| Kegelritzelwelle, E2-Lager hinten/vorne ↔ Rutschkupplung / Zahnradabdeckung | 3 + 3 | 196,3 / 75,4 / 301,6 mm³ | Bauraum umschließt E2 |
| Querlenkerbock ↔ reservierte Fußfläche | 4 | 2166,7 mm³ | Bock steht in seiner Fußfläche |
| Diff-Becher N2 ↔ Antriebswelle | 2 | 1414 mm³ | Knochen im Becher |
| Radachse N1 ↔ Antriebswelle | 2 | 1414 mm³ | Knochen im Becher |
| Radachse N1 ↔ Rad | 2 | 160 mm³ | Achse im Sechskant-Mitnehmer der Felge |

Mindestabstände in Konstruktionslage (`measureMinimumDistance`):

| Prüfung | kleinster Abstand | Soll |
|---|---|---|
| Böcke ↔ alle Skelett-Körper | **1,00 mm** (Bock rechts vorne ↔ Zahnradabdeckung) | ≥ 1 |
| Böcke ↔ Wellenräume (Skelett) | **7,06 mm** | ≥ 3 |
| Böcke ↔ Antriebswelle (bewegt), Getriebe, Diff-Becher, Brücke | 6,96 / 4,64 / > 6 / 11,0 mm | ≥ 1 |
| Brücke ↔ Skelett, Grundplatte, Oberdeck | 47,5 / **2,00** / 34,5 mm | ≥ 1 |
| Getriebe ↔ Kardanwelle, Motorritzel, Fußflächen | 9,0 / 14,5 / 4,64 mm | |
| Lagerbock ↔ Kardanwelle (Becher), Motorritzel, Motor, Querlenkerböcke, Oberdeck | **0,50** / 12,3 / 24,6 / 11,2 / 20,1 mm | ≥ 0,5 (`ha_e2v_spalt`) |
| Drehraum zwischen den E2-Lagern ↔ Gehäuse, Lagerbock, E2-Lager | 0,00 (Berührung an den Stirnseiten, keine Überschneidung) | Interferenz 0 (Review 2 🔵 1) |
| Lagerbock ↔ Grundplatte, Getriebegehäuse | 0 (Auflage bzw. Anlage, keine Überschneidung) | gewollt, Interferenz 0 |
| Hüllkörper Getriebe (siehe oben) ↔ Gehäuse | ≥ 0,50 mm außer den Lagersitzen | |
| Getriebe ↔ Diff-Becher N2 (drehend) | 0,50 mm | gewollt (`ha_n2_luft`) |

## Lasten (MECH-HAC-016)

Annahmen aus dem Anforderungsdokument: 2,0 kg, Sprung 5 g, 60 % hinten → **30 N senkrecht je Rad**; Seitenstoß **50 N je Rad**. Werkstoff: PETG Zugfestigkeit ca. 47 MPa (Prusament PETG, in Schichtrichtung), Prusament PC ca. 60 MPa. Gerechnet als Biegebalken σ = M / W, W = b·h²/6, Geometrie aus dem Modell in Konstruktionslage.

| Teil, Stelle | Last | Moment | Querschnitt | σ | Sicherheit PETG |
|---|---|---|---|---|---|
| **Querlenker, Dämpferlasche** (Sollbruchstelle) | Dämpferkraft 50,5 N (30 N × 56,7 / 34,8 mm, Neigung 14,2°) am Auge X −166, Lasche ab Platte X −142,2 | 50,5 × 23,8 = 1202 N·mm | 8 × 8 mm, W 85,3 mm³ | 14,1 MPa | **3,3** (PC 4,3) |
| Querlenker, Platte am Dämpferpunkt | 30 N am Bolzen, Hebel 21,95 mm | 658 N·mm | 18,4 × 5 mm, W 76,7 mm³ | 8,6 MPa | 5,5 |
| Dämpferbrücke, Steg oben am Mittelteil (Y 16) | 50,5 N, Hebelarm 34,6 mm | 1747 N·mm | 14 × 6 mm (in der Plattenebene), W 196 mm³ | 8,9 MPa | 5,3 |
| Radträger, unterer Steg | 30 N, Hebel Aufstandspunkt ↔ Bolzen ca. 13 mm | 390 N·mm | 8 × 8 mm, W 85,3 mm³ | 4,6 MPa | 10 |
| Querlenkerbock | Lagerkraft ca. 12 N je Bock, Hebel 11 mm | 132 N·mm | 10 × 16 mm, W 427 mm³ | 0,3 MPa | > 100 |
| Getriebegehäuse, Turm | 2 × 50,5 N, 9,5 mm hinter der Rückwand | 960 N·mm | 10 × 32 mm, W 533 mm³ (dazu 2 untere Schrauben) | < 1,8 MPa | > 25 |

- **Seitenstoß 50 N** am Aufstandspunkt (24,7 mm unter dem unteren Bolzen): Kraft in der Sturzstange 1235 / 33,7 ≈ 37 N, Querlenker auf Druck ca. 50 N (Querschnitt 92 mm², 0,6 MPa). Kugelkopf-Auge der Brücke 37 N × 13 mm → 2,4 MPa, Kugelblock am Radträger 37 N × 6 mm → 2,6 MPa. Unkritisch.
- **Ergebnis:** Kleinste Sicherheit **3,3 an der Dämpferlasche des Querlenkers** (≥ 1,5 gefordert). Gehäuse, Böcke, Brücke und Radträger haben alle eine höhere Sicherheit (≥ 5,3). Bei Überlast bricht also zuerst der Querlenker (Sollbruchstelle, billiges Druckteil). Die Lasche wird beim Flachdruck in Schichtrichtung belastet. 🔧 Sprungtest am Prototyp.
- Das Antriebsmoment begrenzt die Rutschkupplung (Mittelantrieb); im Getriebe sind die Zahnräder des Bausatzes das schwächste Teil.

**Kegelritzelwelle E2 und Lagerbock (Nutzerentscheidung 2026-11-01, überschlägig):**

- **Moment auf E2:** begrenzt durch die Haftung der Hinterräder: 2,0 kg × 9,81 × 60 % × μ 1,0 = 11,8 N am Umfang, × 41 mm = 0,48 N·m an den Rädern, durch die Diff-Übersetzung 2,6 (Stückliste Pos. 2) → **0,19 N·m an E2**. Mit Stoßfaktor 3 (Landung, Rutschkupplung noch nicht abgestimmt): **0,56 N·m**.
- **Zahnkräfte (mit Stoßfaktor):** Kegelritzel (mittlerer Radius ca. 5,5 mm, Eingriffswinkel 20°, Teilkegelwinkel 21°): tangential 101 N, radial 34 N, axial 13 N. Hauptzahnrad 70Z (Teilkreis r 21 mm): tangential 27 N, radial 10 N.
- **Lagerkräfte** (alle Kräfte ungünstig gleichgerichtet addiert; Version 11: Lagerabstand 9,0 mm, Kegelritzel 7 mm hinter dem hinteren Lager, Hauptzahnrad in der Mitte des Zahnradraums 4,5 mm davor): vorderes Lager (Lagerbock) R_B = (106,7 × 7 + 13,2 × 5,5 + 28,2 × 4,5) / 9,0 = **105 N**, hinteres Lager R_A ≈ 106,7 + 105,2 + 28,2 = **240 N**. Ohne Stoßfaktor 35 N bzw. 80 N. Die statische Tragzahl eines Lagers 685 (5x11x4) liegt bei ca. 0,27 kN (Richtwert gängiger Kataloge, am gelieferten Lager prüfen): mit Stoß S0 ≈ 1,1, im Fahrbetrieb ≈ 3,4. Version 8 (Lagerabstand 8,5 mm): 111 / 245 N. Die Axialkraft des Kegelritzels (13 N mit Stoß, 4,4 N ohne) soll das hintere Lager als Festlager über die Klemmung im geteilten Sitz aufnehmen; im exportierten Modell ist der Klemmsitz noch nicht vorhanden (`ha_e2h_spiel` +0,1), die Festlegung ist nicht nachgewiesen (siehe [E2-Lagerung](#e2-lagerung-und-lagerbock-nutzerentscheidungen-2026-11-01-review-1--1-und--1-review-2--1)).
- **Lagerbock (PETG, mit Stoßfaktor, Version 11: Steg 18 × 3,5 mm):**

| Stelle | Last | Moment | Querschnitt | σ | Sicherheit PETG (PC) |
|---|---|---|---|---|---|
| Steg, quer (Y) | 105 N, Hebel Lagermitte ↔ Fuß 24,3 mm | 2556 N·mm | 3,5 (X) × 18 (Y) mm, W 189 mm³ | 13,5 MPa | 3,5 (4,4) |
| Steg, längs (X, Axialkraft, falls sie über den Lagerbock geht) | 13 N, Hebel 24,3 mm | 321 N·mm | 18 × 3,5 mm, W 36,8 mm³ | 8,7 MPa | 5,4 (6,9) |
| Quersteg zwischen Steg und Schraube (Zug nach oben) | 53 N je Schraube, Hebel 3,5 mm | 184 N·mm | 10 × 5,28 mm, W 46,5 mm³ | 4,0 MPa | 12 (15) |
| Lagerring, Flächenpressung | 105 N auf 11 × 3,5 mm | | | 2,7 MPa | > 15 |
| Schrauben M3 / Einsätze | 53 N Zug je Schraube (Kippen um die Vorderkante: 13 N × 24,3 mm / 3,3 mm ≈ 97 N) | | | | unkritisch |

  **Kerbwirkung (Review 3 🔵 3):** Die Übergänge Steg ↔ Fuß bzw. Querstege (Z ca. 32,3…34,3) sind im Modell scharfe Innenecken. Mit einem Kerbfaktor von ca. 2 sinkt die Sicherheit am Steg quer mit Stoß von 3,5 auf ca. **1,7** (PC ca. 2,2). Das liegt noch über 1,5, aber unter der Sicherheit des Querlenkers (3,3). Kein Modellumbau jetzt (Getriebegehäuse und Lagerbock werden erst nach dem Messen gedruckt). Vorgabe für die Überarbeitung: Verrundung r ≥ 1,5 mm in der YZ-Ebene an diesen Übergängen.
  Mit dem Steg 14 × 6 mm aus Version 8 wäre die Sicherheit bei 3,5 mm Dicke auf 2,0 gefallen. Deshalb ist der Steg jetzt 18 mm breit. Die Sicherheit bleibt damit über der des Querlenkers (3,3).
  Nach unten stützt sich der Lagerbock direkt auf die Grundplatte ab. Ohne Stoßfaktor liegen alle Sicherheiten über 10. Im Lastfall der Radlasten (30 N / 50 N) trägt der Lagerbock nichts; die Sollbruchstelle bleibt der Querlenker.


## Druckhinweise (MECH-HAC-015)

| Teil | Lage auf dem Bett | Stützen | Hinweis |
|---|---|---|---|
| Getriebegehäuse links/rechts (**erst nach dem Messen drucken**, Nutzerentscheidung 2026-11-01) | **Teilungsfläche (Y = 0) auf dem Bett** | **nur im Zahnraum** (Support-Enforcer unter der Decke) | Die Decke des Zahnraums bei \|Y\| 16,85 ist eine Ringfläche Ø 42 mit Loch Ø 12,1, direkt darüber sitzt der Diff-Lagersitz Ø 12,1 × 3,5. Ohne Stützen hängt PETG dort durch und der Sitz wird unmaßhaltig (Review 1 🟡 3). Die Stützen stehen im Zahnraum auf dem Bett und sind von der offenen Teilungsseite aus entfernbar; Kontaktabstand 0,2 mm. Eine 45°-Kegeldecke ist nicht möglich: Sie würde bei r 19,5 schon ab \|Y\| ≈ 3 beginnen und mit dem Tellerrad kollidieren. Der Diff-Lagersitz selbst und die Querbohrungen stehen senkrecht; die halbe Lagerschale des hinteren E2-Lagers und die Bohrungen in X/Z werden als Bogen gedruckt (Überhang am Scheitel r 5,55 bzw. r 8,5 im Ritzelraum, unkritisch). Lagersitze nach dem Druck mit dem Lager prüfen. STL in Fahrzeuglage: im Slicer um 90° um X drehen. |
| Lagerbock E2 | **Vorderseite (X −99,5) auf dem Bett** | keine | Lagersitz (durchgehend, ohne Lippe) und Schraubenbohrungen stehen senkrecht, keine Überhänge. Das ganze Teil liegt flach: Der Steg liegt mit der Vorderseite auf dem Bett und ist in Druckrichtung nur 3,5 mm hoch (18 mm breit). Die Biegespannungen aus den Lagerkräften liegen damit in der Schichtebene (Review 3 🔵 2). **Erst nach dem Messen drucken** (Nutzerentscheidung 2026-11-01). STL in Fahrzeuglage: im Slicer so drehen, dass die Vorderseite unten liegt. |
| Querlenkerbock (4 ×) | Seitenfläche (X) auf dem Bett, Sackloch nach oben | keine | Profil liegt flach. Die Einsatzbohrungen von unten werden als waagerechter Bogen gedruckt. |
| Querlenker | Unterseite der äußeren Platte auf dem Bett | wenig (unter Rohr und Lasche) | In dieser Lage liegt die Dämpferlasche in Schichtrichtung (Last in der Schicht). Alternative: Stützen nur unter dem Rohr. |
| Radträger | **äußere Stirnfläche der Lagernabe auf dem Bett** (Nabenachse senkrecht) | wenig: unter den Stegen (1 mm über dem Bett, ca. 220 mm²) und unter dem Kugelkopfblock (32 mm²) | Review 1 🔵 2: So werden die Lagersitze rund und maßhaltig. Die Stege enden 1 mm vor der Nabenstirn (`ha_rt_verb_kurz`, Freigang zu Becher und Mitnehmer), deshalb brauchen sie eine dünne Stützlage. Die Bohrungen für Bolzen und Kugelkopf liegen dann waagerecht (Bogen). Bettfläche 107 mm². Nach dem Druck mit dem Lager prüfen. |
| Dämpferbrücke | flach (X-Fläche) auf dem Bett | keine | 2,5D-Platte |

- **Bauraum (MECH-FZG-003):** größtes Teil Dämpferbrücke 117,4 × 77,9 × 6 mm, alle Teile ≤ 256 mm (Hüllquader oben). Stützmaterial nur im Zahnraum des Gehäuses und unter den Stegen bzw. dem Kugelkopfblock der Radträger (MECH-HAC-015: „ohne oder mit wenig Stützmaterial“). Ein Slicer ist auf diesem Rechner nicht installiert; 🔧 die Slicer-Prüfung macht der Nutzer.
- **Wandstärken** (Soll ≥ 1,2 mm, an Lagersitzen ≥ 2 mm):
  - Lagersitze: Diff-Lager radial ≥ 10 mm, axiale Lippe **2,01 mm**; hinteres E2-Lager radial **2,00 mm** (Lagerhals Ø 15,1 um Sitz Ø 11,1, voller Sitz 4,0 mm, Punkttest), keine Lippe (Nutzerentscheidung 2026-11-01); vorderes E2-Lager im Lagerbock radial 2,00 mm, Sitz 3,5 mm, keine Lippe; Radlager radial **2,50 mm**, Steg 2,0 mm
  - Einsätze: Bock zur Seite **1,50 mm** (Review 1 🔵 3: knapp, aber ≥ 1,2 mm; bleibt so, weil die Fußfläche der Grundplatte 16 mm breit ist), Lagerbock-Einsätze im Gehäusefuß 1,3 mm über der Plattenoberseite und 1,5 mm neben den Einsätzen der Grundplatte, Gehäusefüße 2,36 mm, Oberdeck-Auflage 2,5 mm, Kugelblock Radträger 2,0 mm, Querlenkerlasche 2,0 mm, Brücke 5,0 mm
  - Bohrung ↔ Zahnraum ≥ 2,0 mm (siehe oben), Querlenkerrohr 1,9 mm, Gabel und Lasche 2,4 mm, Querlenkerplatte 5 mm, Gehäusewand 2,5 mm
- **Toleranzen:** Bohrungen M3 Ø 3,2 (+0,2, `ha_bohrung`). Lagersitze Nennmaß + `ha_lager_spiel` = 0,1 mm (vorläufig) auf den Durchmesser, 🔧 per Probedruck eines Lagersitzes einstellen. Der hintere E2-Sitz hat einen eigenen Parameter `ha_e2h_spiel` (vorläufig = `ha_lager_spiel`): Er wird nach dem Probedruck so gewählt, dass die verschraubten Gehäusehälften den Außenring klemmen (Festlager). Im exportierten Modell ist er noch +0,1 mm (Spielpassung, klemmt nicht); Abnahmekriterium siehe [E2-Lagerung](#e2-lagerung-und-lagerbock-nutzerentscheidungen-2026-11-01-review-1--1-und--1-review-2--1). Stift im Bock Ø 3,1 (+0,1, `ha_stift_spiel_bock`), im Querlenker Ø 3,2. Gewindeeinsätze MP-JET M3 kurz (Pos. 30), Bohrung Ø 4 × 6 vorläufig wie die Grundplatte.
- **Material:** PETG für den Test, Prusament PC für das fertige Modell. Die Konstruktion gilt für beide.

## Montagefolge und Wartung (MECH-HAC-019)

1. Gewindeeinsätze einschmelzen: Gehäuse 16 (4 unten, 2 oben, 4 hinten, 4 in der rechten Hälfte für die Verschraubung, 2 vorne für den Lagerbock), Böcke je 2, Querlenker je 1, Radträger je 1, Brücke 2.
2. E2 vormontieren (wie TT-02B von hinten aufschieben): vorderes Lager auf E2 bis an die Becherschulter schieben und den Lagerbock darüberstecken (Loslager), dann Mitnehmer GB3 und Hauptzahnrad GB5 bzw. später die Rutschkupplung, hinteres Lager, Passscheiben, Kegelritzel; der Stapel der Innenringe ist damit axial gesichert. Diff mit 2 Lagern 8x12x3,5 und Passscheiben und E2 in die rechte Hälfte legen, Zahneingriff mit Passscheiben (Pos. 63) einstellen, linke Hälfte aufsetzen, 4 × M3 quer verschrauben (soll den Außenring des hinteren E2-Lagers klemmen, Festlager; im exportierten Modell ist der Sitz noch Spielpassung, siehe E2-Lagerung).
3. Gehäuse mit 4 × M3 × 8 Senkkopf von unten auf die Grundplatte schrauben, Lagerbock mit 2 × M3 × 14 Zylinderkopf von vorne an die Gehäusefüße schrauben.
4. Dämpferbrücke mit 4 × M3 × 10 an die Gehäuserückseite, Kugelköpfe vorne einschrauben, Dämpfer oben mit M3 × 20 + Stoppmutter.
5. Radträger: Lager einpressen, Radachse N1 durchstecken, Kugelkopf einschrauben, mit M3 × 25 + Stoppmutter in die Gabel des Querlenkers.
6. Querlenker mit Stift 3 × 40 zwischen die beiden Böcke, Böcke mit je 2 × M3 × 8 Senkkopf von unten verschrauben (der Stift ist dann gefangen).
7. Antriebswelle N3 zwischen Diff-Becher und Becher N1, Sturzstange einhängen, Dämpfer unten mit M3 × 14 an die Querlenkerlasche, Sturz einstellen.

**Wartung:**
- **Querlenker, Radträger oder Bock tauschen:** Dämpfer unten lösen, Sturzstange abziehen, die 4 Bockschrauben von unten lösen. Dann Querlenker mit Böcken, Stift, Radträger und Welle nach oben herausnehmen. Getriebegehäuse, Brücke und Oberdeck bleiben montiert.
- **Diff ausbauen:** Oberdeck-Schrauben (2), Brücke (4) und Lagerbock (2) lösen, Gehäuse von unten (4) lösen, abnehmen, Hälften trennen. Die Grundplatte wird dabei nicht zerlegt.
- **Rutschkupplung bzw. Hauptzahnrad montieren oder tauschen:** wie beim Diff das Gehäuse abnehmen und öffnen, E2 mit Lagerbock herausnehmen, Kegelritzel, hinteres Lager und Rutschkupplung von hinten abziehen; der Lagerbock mit dem vorderen Lager geht ebenfalls nach hinten ab. Der Lagerbock ist dafür nur mit 2 Schrauben befestigt (Nutzerentscheidung 2026-11-01).

## Fräsbarkeit (MECH-HAC-013, MECH-HAC-022)

- **Dämpferbrücke:** 2,5D, fräsgerecht (siehe oben).
- **Querlenkerböcke:** Das Profil (YZ) ist in X extrudiert, Stiftloch in X, Innenradien ≥ 1,55 mm. Nur die zwei Einsatzbohrungen kommen von unten (in Alu als Gewinde M3 gebohrt). Damit fräsbar in zwei Aufspannungen.
- **Radträger:** **nicht 2,5D.** Die Lagernabe ist um die Vorspur (2°) gedreht und hat ihre Achse in Y, Lasche und Kugelblock haben ihre Achsen in X. In Alu braucht es zwei bis drei Aufspannungen oder eine 4. Achse. Grund: Die Vorspur ist laut MECH-HAC-008 fest im Radträger. Für eine Alu-Version wäre die Nabe ohne Vorspur und die Vorspur über eine Scheibe denkbar; das ist eine Entscheidung für Phase 3.
- **Querlenker:** 2,5D in X (Prüfskript ohne Befund), aber kein Alu-Teil vorgesehen (Sollbruchstelle).

## Parametrik für das Vorderachsgetriebe (MECH-HAC-023, KANN)

Das Getriebegehäuse hängt nur an `achse_x`, `antrieb_z`, `diff_abtrieb_y`, `gelenk_becher` und den Parametern `ha_gh_*`, `ha_diff_*`, `ha_e2_*`, `ha_od_*`, `ha_gp_getriebe_*`. Für vorne (4WD, Phase 2): Gehäuse an der Ebene X = 0 spiegeln (alle Lagen über −`achse_x` → +`achse_x`), Lagerhals zeigt dann nach hinten zur Kardanwelle. Den Turm für die Dämpferbrücke nach vorne setzen (`ha_turm_*`). Der Lagerbock (`ha_lb_*`, `ha_e2v_x`) entfällt vorne oder wird wie hinten am Becher der vorderen E2 gespiegelt; vorne sitzt kein Zahnrad zwischen den Lagern, dort kann `ha_e2_lippe` wieder > 0 sein (eigener Parameter für vorne nötig, weil `ha_e2_lippe` hinten 0 ist). Kardanwelle und Oberdeck-Auflage (`ha_od_dx`) passen bereits symmetrisch.

## Messpunkte bei Lieferung

Alle vorläufigen Bausatzmaße, danach Parameter ersetzen, `ha_dphi_aus`/`ha_dphi_ein` neu bestimmen (bis `ha_radhub` = −11,667/+23,333) und Prüfskript (Interferenz, drei Stellungen) wiederholen:

1. **Diff:** Tellerrad-Durchmesser, -Breite und Seite (`ha_tellerrad_d`, `ha_tellerrad_b`, `ha_tellerrad_y0`), Diff-Gehäuse-Durchmesser (`ha_diff_d`), Lagermitte/Breite des Diffs (`ha_diff_lager_y`), Lager 8x12x3,5 Breite (`ha_diff_lager_b`), Nabe/Durchführung (`ha_diff_durchf_d`), Passscheiben Diff (`ha_diff_spalt`), Becher N2 Durchmesser und Boden (`ha_n2_d`, `ha_n2_boden`).
2. **Kegelritzelwelle E2:** Ritzel-Durchmesser und -Länge (`ha_ritzel_d`, `ha_ritzel_l`), Einbaumaß Diff-Achse ↔ hinteres Lager (`ha_e2_einbau`; darf kleiner werden, wenn das Tellerrad seitlich am Lager vorbeiläuft, Prüfmaß `ha_e2_tr_luft`), Lagerbreite (`ha_e2_lager_b`), Länge von E2 und Abstand Becherschulter ↔ Kegelritzel, Breite von Mitnehmer GB3 und Hauptzahnrad GB5 zusammen (`ha_hz_bedarf`, vorläufig 8 mm; bestimmt `ha_hz_fehl` und `ha_rk_luft`), Passscheibe (`ha_e2_scheibe`), **Becherschulter** (liegt sie am Innenring an, Durchmesser und Länge des Absatzes). Kriterium (Review 3 🔵 4, das vordere Lager steht 0,5 mm aus dem Sitz vor): Becherschulter ≤ Außendurchmesser des Innenrings, sonst Distanzscheibe 5 × 7. Für die Lippe am Lagerbock: reicht die Becherschulter durch ca. Ø 8? Zusammen mit den Messpunkten 1 des Skeletts: **Kardanwelle E1 Länge und Einstecktiefe in die Becher** (`getriebe_eingang`, `kardan_becher_l`, `rk_luft`). Danach `ha_hz_fehl` ≤ 0 herstellen, z. B. über `getriebe_eingang` im Skelett (eigener PR) oder `ha_e2_einbau` (höchstens ca. 1 mm), und die Lage des Lagerbocks (`ha_e2v_spalt`) prüfen. **Widerspruch in den vorläufigen Maßen (Review 2):** Mit E2 = 41 mm [K1] und der Becheröffnung bei X −84 läge das Kegelritzel bei r 8…17 im Tellerrad-Zahnkranz (r 11…19,5). Mindestens einer der Werte `getriebe_eingang`, `kardan_becher_l`, `ha_tellerrad_d` oder die Länge von E2 ist falsch; alle vier messen. **Axiale Festlegung (Nutzerentscheidung 2026-11-01 nach Review 3):** 🔧 Probelauf mit dem Klemmsitz (`ha_e2h_spiel` per Probedruck auf Klemmung einstellen): E2 axial mit ca. 40 N in beide Richtungen belasten, auch nach 24 h bei ca. 60 °C; Verschiebung ≤ 0,05 mm. Unabhängig vom Ergebnis bekommt die Überarbeitung ein formschlüssiges Festlager (siehe [Vorgaben für die Überarbeitung](#vorgaben-für-die-überarbeitung-von-getriebegehäuse-und-lagerbock-nach-dem-messen)).
3. **Radachse N1:** Becherlänge und -durchmesser (`ha_n1_becher_l`, `ha_n1_becher_d`), Wellenabschnitt (`ha_n1_welle_l`), Lage des Mitnehmerstifts zur Anlage am Lager (`ha_u_nabe`, `ha_radlager_abstand`).
4. **Antriebswelle N3:** Kreuzstiftabstand (`antriebswelle_h_l`, Skelett) und zulässiger Schiebeweg (`ha_knochen_schiebeweg`). 🔧 Knochen fällt voll ausgefedert (Wellenwinkel 27,2°) nicht heraus.
5. **Rad:** Felgeninnendurchmesser (`ha_felge_innen_d`, vorläufig 50 mm). Davon hängen die knappsten Abstände ab: in Konstruktionssturz Querlenker ↔ Rad 0,55 mm (eingefedert), Sturzstange ↔ Rad 0,64 mm (ausgefedert); in den Sturz-Grenzlagen **Querlenker ↔ Rad 0,25 mm** (Sturz −3°, eingefedert) und **Sturzstange ↔ Rad 0,58 mm** (Sturz 0°, ausgefedert). Bei zu wenig Luft nach dem Messen: Radträger-Kugelpunkt (`ha_rt_e_*`) bzw. Querlenkerplatte (`ha_ql_platte_z`) anpassen.
6. **CVA-Dämpfer hinten:** Augenabstand ausgefedert (`ha_daempfer_l_aus`, 80), Hub (`ha_daempfer_hub`, 20), Augen (`ha_d_auge_d`, `ha_d_auge_b`, `ha_d_auge_l`), Durchmesser Feder/Zylinder (`daempfer_d`, Skelett).
7. **Kugelköpfe/Pfannen/Spannschloss 54539:** Kugelhöhe (`ha_kugel_h`), Pfannen-Durchmesser und -Überstand (`ha_pfanne_d`, `ha_pfanne_ueber`), Verstellweg (`ha_sturzstange_verstell`), Länge Kugelmitte–Kugelmitte 50,95 mm einstellbar?
8. **Lager 5x11x4:** Breite (`ha_radlager_b`); Lagersitz-Passung per Probedruck (`ha_lager_spiel`), Klemmsitz des hinteren E2-Lagers im geteilten Gehäuse per Probedruck (`ha_e2h_spiel`, im Export noch +0,1 = Spielpassung), Abnahme mit dem Kriterium aus Messpunkt 2 (40 N, 24 h bei ca. 60 °C, ≤ 0,05 mm).
9. **Gewindeeinsätze MP-JET M3 kurz:** Bohrung und Länge (`ha_einsatz_d`, `ha_einsatz_t`).
10. **Spannschloss 54539:** Laut Tamiya USA enthält der Satz 4 Wellen 3 × 32 mm und 3 × 23 mm; prüfen, ob 3 × 32 mm mit den Pfannen 50,95 mm Kugelmitte–Kugelmitte erreicht (Messpunkt 7).

## Vorgaben für die Überarbeitung von Getriebegehäuse und Lagerbock nach dem Messen

Getriebegehäuse und Lagerbock werden erst nach dem Messen gedruckt und dann überarbeitet (Nutzerentscheidung 2026-11-01). Dabei gilt verbindlich:

1. **Formschlüssiges Festlager für E2** (Nutzerentscheidung 2026-11-01 nach Review 3, 🟡 1): einseitiger Anschlag vor dem hinteren Außenring auf der Zahnradseite (ca. 1,2 mm, eigener Parameter, nur im Gehäuse) **oder** Lippe an der Vorderseite des Lagerbocks, wenn die Becherschulter durch ca. Ø 8 reicht. Das Bundlager F685 nur, wenn beides nicht passt; dann ändert der Nutzer MECH-HAC-017 (Pos. 14). Bis dahin gilt der Klemmsitz mit dem Abnahmekriterium aus Messpunkt 2.
2. **Getrennte Lippen-Parameter** für Gehäuse und Lagerbock statt des gemeinsamen `ha_e2_lippe` (Review 3 🔵 1). Sonst kostet 1 mm Lippe 2 mm Zahnradraum, und ein einseitiger Anschlag ist nicht möglich.
3. **Verrundung r ≥ 1,5 mm in der YZ-Ebene** an den Übergängen Steg ↔ Fuß bzw. Querstege des Lagerbocks (Z ca. 32,3…34,3, Review 3 🔵 3). Ohne Verrundung sinkt die Sicherheit mit Stoß von 3,5 auf ca. 1,7 (siehe [Lasten](#lasten-mech-hac-016)).
4. **Vorderes Lager** (steht 0,5 mm aus dem Sitz vor, Review 3 🔵 4): Becherschulter ≤ Außendurchmesser des Innenrings, sonst Distanzscheibe 5 × 7 (Messpunkt 2).

## Vorgaben an die nächsten Baugruppen

- **Mittelantrieb:**
  - **Rutschkupplung bzw. Hauptzahnrad zwischen den E2-Lagern** (Nutzerentscheidungen 2026-11-01): Der Zahnradraum reicht von der Vorderseite des hinteren Lagers (X −108,0) bis zur Rückseite des Lagerbocks und des vorderen Lagers (X −103,0). Das sind **5,0 mm** (`ha_hz_raum`), ohne Lippen und ohne Steg; der Ring um E2 ist von r 2,5 bis r 23,6 frei (Hüllkörper `drehraum`). Was dort liegt, sichert die Lager axial: Mitnehmer bzw. Nabe der Rutschkupplung liegen an beiden Innenringen an (Stapel Becherschulter – Lager – Mitnehmer/Zahnrad – Lager – Passscheibe – Kegelritzel). An den stehenden Außenringen und am Lagerbock darf nichts schleifen, also braucht die Nabe Absätze kleiner als die Schulter der Innenringe (Ø ca. 7, am Lager messen). Für das Bausatz-Hauptzahnrad GB5 mit Mitnehmer GB3 (≥ 8 mm) fehlen nach vorläufigen Maßen **3,0 mm** (`ha_hz_fehl`), für Rutschkupplung und Mitnehmer (8 + 22 mm) **25,0 mm** (`ha_rk_luft`). Das ist offen bis zur Messung (Messpunkt 2). Danach muss „Mittelantrieb“ die Rutschkupplung so auslegen, dass sie in `ha_hz_raum` passt, oder `getriebe_eingang` wird vorher in einem eigenen PR korrigiert.
  - **Zahnebene und Motor (Review 2 🟡 1):** Die Zahnebene liegt nicht mehr bei X −89 (Skelett `hz_ebene` 20), sondern in der Mitte des Zahnradraums bei ca. **X −105,5**, 16,5 mm weiter hinten. Der Motor muss deshalb um ca. 16,5 mm nach hinten (Flansch ca. X −91,5 statt −75), sonst fehlen an der Motorwelle ca. 19,5 mm statt 3 mm (`motor_welle_reserve`). Platz dafür ist da: Der verschobene Motor hält 8,1 mm zum Lagerbock und 16,8 mm zum Gehäuse. Das Motorritzel liegt dann aber netto genau an der Gehäusevorderseite (X −109,5), seine Hülle mit Zuschlag schneidet die Trommel (26,6 mm³); bei 15 mm Verschiebung sind es noch 5,3 mm³. Zum Querlenkerbock rechts vorne bleiben 1,7 mm. Die Abstände Lagerbock ↔ Motorritzel 12,3 mm und ↔ Motor 24,6 mm gelten nur für die alte Zahnebene. Ritzelbreite, Motorhalter und die Lage der Zahnebene im Zahnradraum legt „Mittelantrieb“ nach dem Messen fest.
  - Der **Lagerbock** liegt im Bauraum der Rutschkupplung und in der Hülle der Zahnradabdeckung (Fuß X −109,5…−99,5, Lagerring und Steg X −103,0…−99,5, Y ±15,8, Z 29…64,15). Die Zahnradabdeckung muss ihn umschließen oder integrieren (Öffnung für Lagerring und Steg) und die zwei Schrauben M3 von vorne (Y ±12,5 / Z 32,3) zugänglich lassen. Der Lagerbock ist für die Montage der Rutschkupplung abnehmbar. Ein topfförmiges Zahnrad über Lagerhals oder Lagerring ist nicht möglich, weil der Steg vor dem Zahnradraum bis zum Lagerring hochgeht. Das Zahnrad muss also ganz in den Zahnradraum passen.
  - Die Rückwand der Zahnradabdeckung braucht eine Öffnung für den Lagerhals (Ø ≥ 16 mm, X −109…−108).
  - Der Querlenkerbock rechts vorne hält 1,00 mm zur Hülle der Zahnradabdeckung. Die Abdeckung darf dort (Y −43…−27, unter Z 48) nicht hinter X −109 reichen.
  - Die Becheröffnung E2 bleibt bei X −84 (`kardan_spiel` = 0).
- **Karosseriehalter und Rammschutz:**
  - Hinter dem Getriebe sitzen die Dämpferbrücke (X −162,5…−156,5, Y ±58,7, Z 31…109) und die Dämpfer (X −176…−156, |Y| 44…77, Z 26…109; sie ragen hinten 4 mm über die Grundplatte hinaus).
  - Die Lochbilder Rammschutz (−164,5 / ±8) und Karosseriehalter (−164,5 / ±22) liegen 2 mm hinter der Brücke. Halter dort dürfen die Brücke nicht berühren und müssen neben den Dämpfern bleiben.
- **Vorderachse:** gleiche Bauart möglich (Böcke, Gabel, Radträger mit Kugelkopf). Das Getriebe lässt sich spiegeln, siehe oben.

## Parameterliste (neue Benutzerparameter)

224 Benutzerparameter mit Präfix `ha_`, jeder mit Kommentar (Quelle; „belegt“, „vorläufig“ oder „abgeleitet“). Skelett-Parameter stehen ohne `_Ref`. Werte in Konstruktionslage, direkt aus Fusion ausgelesen. **Prüfmaße** (`ha_radhub`, `ha_gelenk_*`, `ha_wellenwinkel`, `ha_vorspur_ist`, `ha_sturz_ist`, `ha_daempfer_reserve`, `ha_hebel`, `ha_hals_l`, `ha_rk_luft`, `ha_e2_tr_luft`, `ha_e2_lager_frei`, `ha_hz_raum`, `ha_hz_fehl`) steuern nichts im Modell. `ha_hz_raum_pruef` steuert nur die Breite des Hüllkörpers `drehraum` (Schutz gegen negativen Zahnradraum).

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `ha_ql_y` | `35 mm` | 35,00 mm | Schnittstelle Grundplatte v11: Querlenkerbock Mitte Fussflaeche quer (= ql_y, Schnittstellenblatt), belegt durch Grundplatte; Wert uebernommen, weil die Grundplatte keine Favoriten-Parameter hat |
| `ha_ql_dx` | `18 mm` | 18,00 mm | Schnittstelle Grundplatte v11: Mitte Fussflaeche vor/hinter der Achse (= ql_dx), Stuetzweite 2*ha_ql_dx = 36 mm (MECH-HAC-006) |
| `ha_ql_fuss_l` | `10 mm` | 10,00 mm | Schnittstelle Grundplatte v11: Fussflaeche Querlenkerbock laengs (= ql_l) |
| `ha_ql_fuss_b` | `16 mm` | 16,00 mm | Schnittstelle Grundplatte v11: Fussflaeche Querlenkerbock quer (= ql_b) |
| `ha_gp_paar_d` | `9 mm` | 9,00 mm | Schnittstelle Grundplatte v11: Lochabstand Zweierlochbild (= gp_paar_d) |
| `ha_gp_getriebe_dx` | `19 mm` | 19,00 mm | Schnittstelle Grundplatte v11: Getriebe-Lochbild vor/hinter der Achse (= gp_getriebe_dx, X -152/-114) |
| `ha_gp_getriebe_y` | `18 mm` | 18,00 mm | Schnittstelle Grundplatte v11: Getriebe-Lochbild quer (= gp_getriebe_y) |
| `ha_od_luft` | `1 mm` | 1,00 mm | Schnittstelle Grundplatte v11: Oberdeck 1 mm ueber der Zahnradabdeckung (= od_luft) |
| `ha_od_z` | `antrieb_z + abdeckung_r + ha_od_luft` | 84,20 mm | abgeleitet: Unterkante Oberdeck = od_z Grundplatte (84,2 mm), Auflagehoehe der Gehaeuse-Pfosten (MECH-HAC-003) |
| `ha_od_dx` | `18 mm` | 18,00 mm | Schnittstelle Grundplatte v11: Oberdeck-Loecher 18 mm vor der Hinterachse (= od_getriebe_dx, X -115) |
| `ha_od_y` | `5 mm` | 5,00 mm | Schnittstelle Grundplatte v11: Oberdeck-Loecher quer (= od_loch_y) |
| `ha_bohrung` | `3.2 mm` | 3,20 mm | Bohrung M3 im Druck (+0,2 mm, MECH-HAC-015) |
| `ha_einsatz_d` | `4 mm` | 4,00 mm | Gewindeeinsatz M3 kurz (Stueckliste Pos. 30): Bohrung, vorlaeufig wie Grundplatte (akku_einsatz_d), bei Lieferung messen |
| `ha_einsatz_t` | `6 mm` | 6,00 mm | Gewindeeinsatz M3 kurz: Bohrtiefe, vorlaeufig wie Grundplatte (akku_einsatz_t), bei Lieferung messen |
| `ha_kopf_d` | `6 mm` | 6,00 mm | Senkung fuer M3-Zylinderkopf (dk 5,5 mm + Spiel) |
| `ha_lager_spiel` | `0.1 mm` | 0,10 mm | Passung Lagersitz: Zugabe auf den Durchmesser, vorlaeufig, per Probedruck einstellen (MECH-HAC-015) |
| `ha_lager_wand` | `2 mm` | 2,00 mm | Mindestwand an Lagersitzen (MECH-HAC-015: >= 2 mm) |
| `ha_diff_lager_d` | `12 mm` | 12,00 mm | Diff-Lager 8x12x3,5 (Stueckliste Pos. 14): Aussendurchmesser, belegt (Lindinger), am Teil pruefen |
| `ha_diff_lager_b` | `3.5 mm` | 3,50 mm | Diff-Lager 8x12x3,5: Breite, vorlaeufig (gleichwertiger Satz OZRC), am Teil messen |
| `ha_diff_lager_y` | `18.6 mm` | 18,60 mm | Diff-Lager: Lagermitte quer ab Fahrzeugmitte, vorlaeufig (Diff-Breite unbelegt, so gewaehlt, dass Lager + 2 mm Wand vor dem Becher N2 liegen), am Teil messen |
| `ha_diff_versatz` | `0 mm` | 0,00 mm | Zahneingriff: Verschiebung des Diffs quer (Distanzscheiben-Sitz, Tellerrad zum Kegelritzel), vorlaeufig 0, nach Probelauf einstellen (MECH-HAC-002) |
| `ha_diff_durchf_d` | `9 mm` | 9,00 mm | Durchfuehrung Diff-Abtrieb in der Seitenwand (Lippe vor dem Diff-Lager), vorlaeufig: Nabe 8 mm + Luft |
| `ha_tellerrad_d` | `39 mm` | 39,00 mm | Tellerrad GB4: Aussendurchmesser vorlaeufig ca. 39 mm ([A1] S. 23, Massstab ueber GB5 wie Skelett), am Teil messen |
| `ha_zahn_luft` | `1.5 mm` | 1,50 mm | Luft zwischen drehenden Zahnraedern und Gehaeusewand, Annahme |
| `ha_zahnraum_d` | `ha_tellerrad_d + 2 * ha_zahn_luft` | 42,00 mm | abgeleitet: Zahnraum um Tellerrad/Diff |
| `ha_gh_wand` | `2.5 mm` | 2,50 mm | Getriebegehaeuse: Wand um den Zahnraum (>= 1,2 mm Druck) |
| `ha_gh_trommel_d` | `ha_zahnraum_d + 2 * ha_gh_wand` | 47,00 mm | abgeleitet: Aussendurchmesser Diff-Trommel |
| `ha_n2_boden` | `gelenk_becher` | 9,00 mm | Diff-Becher N2: Kreuzstift bis Becherboden, vorlaeufig wie Skelett (= gelenk_becher), am Teil messen |
| `ha_n2_d` | `17 mm` | 17,00 mm | Diff-Becher N2: Aussendurchmesser vorlaeufig 17 mm (1:1-Zeichnung [A1] S. 10/11, gemessen 17,1 mm) |
| `ha_n2_luft` | `0.5 mm` | 0,50 mm | Luft Gehaeuse-Seitenwand zum drehenden Becher N2, Annahme |
| `ha_gh_y` | `diff_abtrieb_y - ha_n2_boden - ha_n2_luft` | 22,36 mm | abgeleitet: Aussenflaeche Gehaeuse quer (22,36 mm < 24,86 mm laut Grundplatte, MECH-HAC-003) |
| `ha_gh_x_hinten` | `-achse_x - ha_gh_trommel_d / 2` | -156,50 mm | abgeleitet: Rueckseite Getriebegehaeuse (Anlage Daempferbruecke) |
| `ha_gh_x_vorne` | `-achse_x + ha_gh_trommel_d / 2` | -109,50 mm | abgeleitet: Vorderseite Getriebegehaeuse (ohne Lagerhals) |
| `ha_gh_fuss_l` | `9 mm` | 9,00 mm | Getriebegehaeuse: Fuss laengs vorn und hinten um die Lochbilder (Einsatz + Wand) |
| `ha_gh_fuss_z` | `50 mm` | 50,00 mm | Getriebegehaeuse: Oberkante der Fuesse (verbindet Lochbild und Trommel) |
| `ha_e2_lager_d` | `11 mm` | 11,00 mm | Lager 5x11x4 (Pos. 14) fuer E2: Aussendurchmesser belegt (Lindinger), am Teil pruefen |
| `ha_e2_lager_b` | `e2_lager_b` | 4,00 mm | Lager 5x11x4: Breite (= e2_lager_b Skelett), vorlaeufig, am Teil messen |
| `ha_e2_einbau` | `23 mm` | 23,00 mm | Zahneingriff: Einbaumass Diff-Achse bis Mitte hinteres E2-Lager, vorlaeufig 23 mm = Tellerrad-Radius + Luft + halbe Lagerbreite (Lager ganz ausserhalb Tellerrad und Zahnraum, Review 1), nach Probelauf einstellen (MECH-HAC-002) |
| `ha_e2_lagerabstand` | `ha_e2v_x + achse_x - ha_e2_einbau` | 9,00 mm | abgeleitet: Lagerabstand E2 Mitte-Mitte (hinteres Lager im Gehaeuse, vorderes im Lagerbock; dazwischen spaeter Hauptzahnrad/Rutschkupplung, Nutzerentscheidung 2026-11-01) |
| `ha_e2_lippe` | `0 mm` | 0,00 mm | Lippe zahnradseitig vor dem hinteren E2-Lager (Gehaeuse) und hinter dem vorderen (Lagerbock): 0 = weggelassen (Nutzerentscheidung 2026-11-01 nach Review 2, Zahnradraum). Lager axial ueber die Teile auf der Welle (Becherschulter, GB3/Mitnehmer, Passscheibe, Kegelritzel), hinterer Aussenring als Festlager im geteilten Sitz geklemmt. Wert > 0 kostet ha_hz_raum doppelt |
| `ha_e2_durchf_d` | `8 mm` | 8,00 mm | Durchfuehrung E2 (Welle 5 mm) in Lippe und Steg; wirkt nur bei ha_e2_lippe > 0 (seit Review 2 ohne Lippen) |
| `ha_ritzel_d` | `14 mm` | 14,00 mm | Kegelritzel GB2: Aussendurchmesser vorlaeufig ([A1] S. 23, Verhaeltnis), am Teil messen |
| `ha_ritzel_raum_l` | `ha_e2_einbau - ha_e2_lager_b / 2` | 21,00 mm | abgeleitet: Ritzelraum von der Diff-Achse bis zum hinteren E2-Lager |
| `ha_gh_hals_d` | `ha_e2_lager_d + ha_lager_spiel + 2 * ha_lager_wand` | 15,10 mm | abgeleitet: Aussendurchmesser Lagerhals/Tunnel E2 |
| `ha_gh_hals_x` | `-achse_x + ha_e2_einbau + ha_e2_lager_b / 2 + ha_e2_lippe` | -108,00 mm | abgeleitet: Vorderkante Lagerhals E2 = Vorderseite hinteres E2-Lager + ha_e2_lippe (seit Review 2 ohne Lippe) |
| `ha_hals_l` | `ha_gh_hals_x - rk_x_hinten` | 1,00 mm | Pruefmass: Lagerhals (hinteres E2-Lager, ggf. mit Lippe) im Bauraum der Rutschkupplung (X ab rk_x_hinten) |
| `ha_rk_luft` | `ha_hz_raum - e2_mitnehmer_l - rk_l_bedarf` | -25,00 mm | Pruefmass wie rk_luft im Skelett: Rutschkupplung mit Mitnehmer zwischen den E2-Lagern (Nutzerentscheidung 2026-11-01), muss >= 0 sein; negativ = Ergebnis vorlaeufiger Masse, offener Punkt Mittelantrieb |
| `ha_od_post_l` | `9 mm` | 9,00 mm | Oberdeck-Auflage: Laenge in X (Einsatz + Wand) |
| `ha_od_post_rand` | `2.5 mm` | 2,50 mm | Oberdeck-Auflage: Wand neben den Einsaetzen |
| `ha_od_post_z` | `60 mm` | 60,00 mm | Oberdeck-Auflage: Unterkante des Pfostenblocks (verbindet mit Trommel und Tunnel) |
| `ha_turm_l` | `10 mm` | 10,00 mm | Turm fuer die Daempferbruecke: Laenge in X ab Gehaeuserueckseite |
| `ha_turm_b` | `32 mm` | 32,00 mm | Turm fuer die Daempferbruecke: Breite quer |
| `ha_turm_z` | `92 mm` | 92,00 mm | Turm fuer die Daempferbruecke: Oberkante |
| `ha_vs_hx` | `20 mm` | 20,00 mm | Verschraubung der Gehaeusehaelften hinten: X hinter der Achse |
| `ha_vs_hz` | `42 mm` | 42,00 mm | Verschraubung hinten unten: Hoehe |
| `ha_vs_oz` | `74 mm` | 74,00 mm | Verschraubung oben (Turm und Oberdeck-Auflage): Hoehe |
| `ha_vs_vx` | `21 mm` | 21,00 mm | Verschraubung vorne unten: X vor der Achse |
| `ha_vs_vz` | `41 mm` | 41,00 mm | Verschraubung vorne unten: Hoehe |
| `ha_vs_senk` | `3 mm` | 3,00 mm | Verschraubung unten: Tiefe der Kopfsenkung (M3 x 25) |
| `ha_vs_senk_turm` | `2 mm` | 2,00 mm | Verschraubung im Turm: Tiefe der Kopfsenkung (M3 x 20) |
| `ha_vs_senk_post` | `1.5 mm` | 1,50 mm | Verschraubung in der Oberdeck-Auflage: Tiefe der Kopfsenkung (M3 x 14) |
| `ha_vs_einsatz_t` | `7 mm` | 7,00 mm | Verschraubung: Tiefe der Einsatzbohrung in der rechten Haelfte |
| `ha_db_sy` | `10 mm` | 10,00 mm | Daempferbruecke: Schrauben quer |
| `ha_db_sz_u` | `36 mm` | 36,00 mm | Daempferbruecke: untere Schrauben, Hoehe |
| `ha_db_sz_o` | `86 mm` | 86,00 mm | Daempferbruecke: obere Schrauben (Turm), Hoehe |
| `ha_sturz` | `-1 deg` | -1,00° | Sturz statisch, vorlaeufig -1 Grad (MECH-HAC-009), Einstellung ueber die Sturzstange |
| `ha_vorspur` | `2 deg` | 2,00° | Vorspur je Rad fest ueber den Radtraeger, vorlaeufig 2 Grad (MECH-HAC-008) |
| `ha_n1_becher_l` | `18.3 mm` | 18,30 mm | Radachse N1: Becherlaenge, vorlaeufig aus 1:1-Zeichnung [A1] S. 11 (Gesamt 43,7 - Welle/Gewinde 25,4), am Teil messen |
| `ha_n1_becher_d` | `17 mm` | 17,00 mm | Radachse N1: Becher-Aussendurchmesser, vorlaeufig 1:1-Zeichnung [A1] S. 11 (gemessen 17,1 mm), am Teil messen |
| `ha_n1_welle_d` | `5 mm` | 5,00 mm | Radachse N1: Wellendurchmesser 5 mm, belegt (Lager 5x11, 1:1-Zeichnung 4,98 mm) |
| `ha_n1_welle_l` | `14.1 mm` | 14,10 mm | Radachse N1: Wellenabschnitt Becherboden bis Absatz, vorlaeufig 1:1-Zeichnung [A1] S. 11 |
| `ha_n1_gewinde_d` | `3 mm` | 3,00 mm | Radachse N1: Gewinde am Ende, vorlaeufig |
| `ha_u_rad` | `rad_y - antriebswelle_h_y - ( ha_n1_becher_l - gelenk_becher )` | 4,90 mm | abgeleitet: Becherboden N1 bis Radmitte entlang der Achse |
| `ha_p_abst` | `ha_u_rad + ha_n1_becher_l - gelenk_becher` | 14,20 mm | abgeleitet: Radmitte bis Kreuzstift der Antriebswelle im Becher N1 |
| `ha_radlager_d` | `11 mm` | 11,00 mm | Radlager 5x11x4 (Pos. 14): Aussendurchmesser belegt, am Teil pruefen |
| `ha_radlager_b` | `4 mm` | 4,00 mm | Radlager 5x11x4: Breite vorlaeufig, am Teil messen |
| `ha_radlager_abstand` | `6 mm` | 6,00 mm | Radtraeger: Lagerabstand Mitte-Mitte (Steg 2 mm = Mindestwand an Lagersitzen), vorlaeufig (MECH-HAC-008); Lage des Sechskant-Mitnehmers am Teil pruefen |
| `ha_radlager_steg_d` | `8 mm` | 8,00 mm | Radtraeger: Bohrung im Steg zwischen den Lagern (Welle 5 mm) |
| `ha_rt_spalt` | `0.5 mm` | 0,50 mm | Radtraeger: Lager steht 0,5 mm ueber die Nabe vor (Abstand zum drehenden Becher bzw. Mitnehmer) |
| `ha_rt_lager_wand` | `2.5 mm` | 2,50 mm | Radtraeger: Wand um die Lagersitze (>= 2 mm) |
| `ha_rt_boss_d` | `ha_radlager_d + ha_lager_spiel + 2 * ha_rt_lager_wand` | 16,10 mm | abgeleitet: Aussendurchmesser Lagernabe Radtraeger |
| `ha_u_nabe` | `ha_radlager_abstand + ha_radlager_b` | 10,00 mm | abgeleitet: Becherboden N1 bis Anlage Sechskant-Mitnehmer |
| `ha_rt_b_dy` | `-12 mm` | -12,00 mm | Radtraeger: unterer Anlenkpunkt (Bolzen zum Querlenker) quer zur Radmitte, im Radtraegersystem, aus Kinematikrechnung |
| `ha_rt_b_dz` | `-16.5 mm` | -16,50 mm | Radtraeger: unterer Anlenkpunkt Hoehe zur Radmitte (Freigang Querlenker zum Becher N1 beim Ausfedern) |
| `ha_rt_e_dx` | `-10 mm` | -10,00 mm | Radtraeger: Kugelmitte Sturzstange laengs zur Radmitte |
| `ha_rt_e_dy` | `-27 mm` | -27,00 mm | Radtraeger: Kugelmitte Sturzstange quer zur Radmitte (innerhalb der Felgeninnenseite) |
| `ha_rt_e_dz` | `22.5 mm` | 22,50 mm | Radtraeger: Kugelmitte Sturzstange Hoehe zur Radmitte, aus Kinematikrechnung |
| `ha_rt_lasche_d` | `8 mm` | 8,00 mm | Radtraeger: Lasche unten, Durchmesser um den Bolzen |
| `ha_rt_lasche_b` | `8 mm` | 8,00 mm | Radtraeger: Lasche unten, Breite in X |
| `ha_lasche_spalt` | `0.2 mm` | 0,20 mm | Spiel Lasche Radtraeger in der Gabel des Querlenkers je Seite |
| `ha_rt_steg_b` | `8 mm` | 8,00 mm | Radtraeger: Stege Breite in X |
| `ha_rt_e_lug` | `8 mm` | 8,00 mm | Radtraeger: Block fuer den Kugelkopf oben (Kantenlaenge) |
| `ha_felge_innen_d` | `50 mm` | 50,00 mm | Rad: Innendurchmesser Felge (Raum fuer den Radtraeger), vorlaeufig, am Teil messen |
| `ha_kugel_h` | `6 mm` | 6,00 mm | Kugelkopf 5 mm (Tamiya): Kugelmitte ueber Auflageflaeche, vorlaeufig, am Teil messen |
| `ha_pfanne_d` | `9 mm` | 9,00 mm | Kugelpfanne/Sturzstange: Huellkoerper-Durchmesser, vorlaeufig |
| `ha_pfanne_ueber` | `4.5 mm` | 4,50 mm | Kugelpfanne: Ueberstand ueber die Kugelmitte, vorlaeufig |
| `ha_ql_z` | `40 mm` | 40,00 mm | Querlenkerachse innen: Hoehe (Stift im Bock), aus Kinematikrechnung (Gelenkabstand N3 nahezu konstant) |
| `ha_stift_d` | `3 mm` | 3,00 mm | Querlenkerachse: Stahlstift ISO 2338 3 m6 (MECH-HAC-007) |
| `ha_stift_spiel_bock` | `0.1 mm` | 0,10 mm | Querlenkerachse: Spiel im Bock (Stift fest), per Probedruck einstellen |
| `ha_stift_l` | `40 mm` | 40,00 mm | Querlenkerachse: Stiftlaenge 40 mm (ISO 2338 3 x 40) |
| `ha_stift_luft` | `0.25 mm` | 0,25 mm | Querlenkerachse: Axialluft des Stifts je Ende im Sackloch |
| `ha_ql_axial` | `0.5 mm` | 0,50 mm | Querlenker: Axialspiel zwischen Rohr und Bock je Seite |
| `ha_ql_rohr_d` | `7 mm` | 7,00 mm | Querlenker: Rohr um die Achse innen |
| `ha_ql_rohr_l` | `2 * ha_ql_dx - ha_ql_fuss_l - 2 * ha_ql_axial` | 25,00 mm | abgeleitet: Rohrlaenge zwischen den Boecken |
| `ha_stift_t` | `( ha_stift_l + 2 * ha_stift_luft - ha_ql_rohr_l - 2 * ha_ql_axial ) / 2` | 7,25 mm | abgeleitet: Sacklochtiefe des Stifts je Bock |
| `ha_ql_dicke` | `5 mm` | 5,00 mm | Querlenker: Plattendicke (Sollbruchstelle, MECH-HAC-016) |
| `ha_ql_y1` | `20 mm` | 20,00 mm | Querlenker: breiter innerer Teil bis 20 mm vom Rohr |
| `ha_ql_wange` | `5 mm` | 5,00 mm | Querlenker: Wange der Gabel aussen |
| `ha_ql_gabel_b` | `ha_rt_lasche_b + 2 * ha_lasche_spalt + 2 * ha_ql_wange` | 18,40 mm | abgeleitet: Breite der Gabel aussen |
| `ha_ql_gabel_d` | `8 mm` | 8,00 mm | Querlenker: Gabel, Durchmesser um den Bolzen |
| `ha_ql_schlitz` | `7 mm` | 7,00 mm | Querlenker: Schlitz fuer die Radtraeger-Lasche, Tiefe ab Bolzenmitte |
| `ha_ql_bock_d` | `ha_ql_fuss_b` | 16,00 mm | Querlenkerbock: Rundung um den Stift (tangential an die Fussbreite) |
| `ha_db_dicke` | `6 mm` | 6,00 mm | Daempferbruecke: Plattendicke (MECH-HAC-013), Alu spaeter gleich |
| `ha_sl_c_y` | `29 mm` | 29,00 mm | Sturzstange: innere Kugelmitte quer (an der Daempferbruecke), aus Kinematikrechnung |
| `ha_sl_c_z` | `78 mm` | 78,00 mm | Sturzstange: innere Kugelmitte Hoehe, aus Kinematikrechnung |
| `ha_sl_c_x` | `ha_gh_x_hinten + ha_kugel_h` | -150,50 mm | abgeleitet: innere Kugelmitte laengs (Kugelkopf auf der Vorderseite der Bruecke) |
| `ha_ql_dl` | `36 mm` | 36,00 mm | Daempfer unten: Lage auf dem Querlenker ab der Achse (bestimmt das Hebelverhaeltnis) |
| `ha_ql_dl_z` | `0 mm` | 0,00 mm | Daempfer unten: Versatz senkrecht zur Querlenkerebene |
| `ha_dl_lasche` | `8 mm` | 8,00 mm | Querlenker: Daempferlasche, Querschnitt |
| `ha_d_auge_d` | `9 mm` | 9,00 mm | CVA-Daempfer hinten: Auge Aussendurchmesser, vorlaeufig, am Teil messen |
| `ha_d_auge_b` | `6 mm` | 6,00 mm | CVA-Daempfer: Auge Breite, vorlaeufig |
| `ha_d_auge_l` | `10 mm` | 10,00 mm | CVA-Daempfer: Augenmitte bis Koerper/Federteller, vorlaeufig (Skelett: Augen 20 mm gesamt) |
| `ha_d_spalt` | `0.5 mm` | 0,50 mm | Daempfer: Scheibe zwischen Auge und Anlage |
| `ha_d_x` | `ha_gh_x_hinten - ha_db_dicke - ha_d_spalt - ha_d_auge_b / 2` | -166,00 mm | abgeleitet: Daempferebene laengs (hinter der Bruecke, wie TT-02B) |
| `ha_daempfer_l_aus` | `80 mm` | 80,00 mm | CVA-Daempfer hinten: Augenabstand ausgefedert, vorlaeufig (Feder MB5 64,5 mm + Teller/Augen), am Teil messen |
| `ha_daempfer_hub` | `20 mm` | 20,00 mm | CVA-Daempfer hinten: Hub, vorlaeufig (Kolbenstange MB12 46,5 mm, 1:1 [A1] S. 13), am Teil messen |
| `ha_du_y` | `51.7 mm` | 51,70 mm | Daempfer oben: Lage quer an der Bruecke (oben nach innen geneigt wie TT-02B) |
| `ha_hebel_tt02b` | `1.5` | 1,500 | Hebelverhaeltnis Rad:Daempfer TT-02B hinten, vorlaeufig aus der Anleitung abgeschaetzt (docs/hinterachse.md), Spanne 1,4-1,6 |
| `ha_knochen_schiebeweg` | `2 mm` | 2,00 mm | Antriebswelle N3: zulaessiger Schiebeweg je Richtung, vorlaeufig (MECH-HAC-011), am Teil messen |
| `ha_sturzstange_verstell` | `3 mm` | 3,00 mm | Sturzstange: Verstellweg je Richtung (Spannschloss, Gewinde), vorlaeufig, am Teil pruefen (MECH-HAC-009) |
| `ha_dphi_aus` | `-12.4693 deg` | -12,47° | Pruefstellung ausgefedert: Querlenkerwinkel, so bestimmt, dass ha_radhub = -ausfederweg (Pruefskript) |
| `ha_dphi_ein` | `22.8615 deg` | 22,86° | Pruefstellung eingefedert: Querlenkerwinkel, so bestimmt, dass ha_radhub = +einfederweg (Pruefskript) |
| `ha_ql_dphi` | `0 deg` | 0,00° | Stellung der Aufhaengung: Querlenkerdrehung gegen Konstruktionslage (0 = Konstruktionslage, ha_dphi_aus, ha_dphi_ein) |
| `ha_b0_y` | `rad_y + ha_rt_b_dy * cos(ha_sturz) - ha_rt_b_dz * sin(ha_sturz)` | 91,71 mm | abgeleitet: unterer Anlenkpunkt quer in Konstruktionslage |
| `ha_b0_z` | `rad_z + ha_rt_b_dy * sin(ha_sturz) + ha_rt_b_dz * cos(ha_sturz)` | 24,71 mm | abgeleitet: unterer Anlenkpunkt Hoehe in Konstruktionslage |
| `ha_ql_l` | `sqrt(( ha_b0_y - ha_ql_y ) ^ 2 + ( ha_b0_z - ha_ql_z ) ^ 2)` | 58,74 mm | abgeleitet: Querlenkerlaenge Achse innen bis Bolzen aussen |
| `ha_ql_phi0` | `atan(( ha_b0_z - ha_ql_z ) / ( ha_b0_y - ha_ql_y ))` | -15,09° | abgeleitet: Querlenkerwinkel in Konstruktionslage (negativ = aussen tiefer) |
| `ha_ql_phi` | `ha_ql_phi0 + ha_ql_dphi` | -15,09° | abgeleitet: Querlenkerwinkel in der aktuellen Stellung |
| `ha_b_y` | `ha_ql_y + ha_ql_l * cos(ha_ql_phi)` | 91,71 mm | abgeleitet: Bolzen aussen quer (Stellung) |
| `ha_b_z` | `ha_ql_z + ha_ql_l * sin(ha_ql_phi)` | 24,71 mm | abgeleitet: Bolzen aussen Hoehe (Stellung) |
| `ha_e0_y` | `rad_y + ha_rt_e_dy * cos(ha_sturz) - ha_rt_e_dz * sin(ha_sturz)` | 77,40 mm | abgeleitet: Kugel Radtraeger quer in Konstruktionslage |
| `ha_e0_z` | `rad_z + ha_rt_e_dy * sin(ha_sturz) + ha_rt_e_dz * cos(ha_sturz)` | 63,97 mm | abgeleitet: Kugel Radtraeger Hoehe in Konstruktionslage |
| `ha_sl_lp` | `sqrt(( ha_e0_y - ha_sl_c_y ) ^ 2 + ( ha_e0_z - ha_sl_c_z ) ^ 2)` | 50,39 mm | abgeleitet: Sturzstange, Laenge in der YZ-Ebene (fest ueber die Stellung) |
| `ha_rt_re` | `sqrt(( ha_rt_e_dy - ha_rt_b_dy ) ^ 2 + ( ha_rt_e_dz - ha_rt_b_dz ) ^ 2)` | 41,79 mm | abgeleitet: Abstand Bolzen - Kugel am Radtraeger |
| `ha_rt_brel` | `180 deg - atan(( ha_rt_e_dz - ha_rt_b_dz ) / ( ha_rt_b_dy - ha_rt_e_dy ))` | 111,04° | abgeleitet: Richtung Bolzen -> Kugel im Radtraegersystem (gilt fuer ha_rt_b_dy > ha_rt_e_dy) |
| `ha_bc_d` | `sqrt(( ha_sl_c_y - ha_b_y ) ^ 2 + ( ha_sl_c_z - ha_b_z ) ^ 2)` | 82,30 mm | abgeleitet: Abstand Bolzen - innere Kugel (Stellung) |
| `ha_bc_g` | `180 deg - atan(( ha_sl_c_z - ha_b_z ) / ( ha_b_y - ha_sl_c_y ))` | 139,65° | abgeleitet: Richtung Bolzen -> innere Kugel (Stellung) |
| `ha_rt_kappa` | `ha_bc_g - acos(( ha_rt_re ^ 2 + ha_bc_d ^ 2 - ha_sl_lp ^ 2 ) / ( 2 * ha_rt_re * ha_bc_d )) - ha_rt_brel` | -1,00° | abgeleitet: Drehung des Radtraegers um X (Stellung, Viergelenk Querlenker/Sturzstange) |
| `ha_w_y` | `ha_b_y - ha_rt_b_dy * cos(ha_rt_kappa) + ha_rt_b_dz * sin(ha_rt_kappa)` | 104,00 mm | abgeleitet: Radmitte quer (Stellung); Konstruktionslage = rad_y |
| `ha_w_z` | `ha_b_z - ha_rt_b_dy * sin(ha_rt_kappa) - ha_rt_b_dz * cos(ha_rt_kappa)` | 41,00 mm | abgeleitet: Radmitte Hoehe (Stellung); Konstruktionslage = rad_z |
| `ha_radhub` | `ha_w_z - rad_z` | 0,00 mm | Pruefmass: Radhub gegen Konstruktionslage (+ = eingefedert) |
| `ha_p_x` | `-achse_x - ha_p_abst * sin(ha_vorspur)` | -133,50 mm | abgeleitet: Kreuzstift N3 im Becher N1, laengs (Stellung) |
| `ha_p_y` | `ha_w_y - ha_p_abst * cos(ha_vorspur) * cos(ha_rt_kappa)` | 89,81 mm | abgeleitet: Kreuzstift N3 aussen, quer (Stellung) |
| `ha_p_z` | `ha_w_z - ha_p_abst * cos(ha_vorspur) * sin(ha_rt_kappa)` | 41,25 mm | abgeleitet: Kreuzstift N3 aussen, Hoehe (Stellung) |
| `ha_gelenk_l` | `sqrt(( ha_p_x + achse_x ) ^ 2 + ( ha_p_y - diff_abtrieb_y ) ^ 2 + ( ha_p_z - antrieb_z ) ^ 2)` | 59,95 mm | Pruefmass: Abstand der Kreuzstifte von N3 (Diff-Becher bis Becher N1) in der Stellung (MECH-HAC-011) |
| `ha_gelenk_dl` | `ha_gelenk_l - antriebswelle_h_l` | -0,05 mm | Pruefmass: Gelenkabstand minus Knochenlaenge, /Aenderung/ <= ha_knochen_schiebeweg |
| `ha_wellenwinkel` | `asin(( antrieb_z - ha_p_z ) / ha_gelenk_l)` | 14,84° | Pruefmass: Neigung Antriebswelle N3 (aussen tiefer = positiv) |
| `ha_n3_wz` | `-atan(( ha_p_x + achse_x ) / ( ha_p_y - diff_abtrieb_y ))` | 0,49° | abgeleitet: Drehung Huellkoerper N3 um Z |
| `ha_vorspur_ist` | `atan(sin(ha_vorspur) / ( cos(ha_vorspur) * cos(ha_rt_kappa) ))` | 2,00° | Pruefmass: Vorspur in der Stellung (MECH-HAC-012) |
| `ha_sturz_ist` | `asin(cos(ha_vorspur) * sin(ha_rt_kappa))` | -1,00° | Pruefmass: Sturz in der Stellung (MECH-HAC-012) |
| `ha_e_x` | `-achse_x + ha_rt_e_dx` | -143,00 mm | abgeleitet: Kugel Radtraeger laengs |
| `ha_e_y` | `ha_b_y + ( ha_rt_e_dy - ha_rt_b_dy ) * cos(ha_rt_kappa) - ( ha_rt_e_dz - ha_rt_b_dz ) * sin(ha_rt_kappa)` | 77,40 mm | abgeleitet: Kugel Radtraeger quer (Stellung) |
| `ha_e_z` | `ha_b_z + ( ha_rt_e_dy - ha_rt_b_dy ) * sin(ha_rt_kappa) + ( ha_rt_e_dz - ha_rt_b_dz ) * cos(ha_rt_kappa)` | 63,97 mm | abgeleitet: Kugel Radtraeger Hoehe (Stellung) |
| `ha_sl_l` | `sqrt(( ha_e_x - ha_sl_c_x ) ^ 2 + ( ha_e_y - ha_sl_c_y ) ^ 2 + ( ha_e_z - ha_sl_c_z ) ^ 2)` | 50,95 mm | abgeleitet: Sturzstange Kugelmitte bis Kugelmitte (3D) |
| `ha_sl_wx` | `asin(( ha_e_z - ha_sl_c_z ) / ha_sl_l)` | -15,99° | abgeleitet: Drehung Huellkoerper Sturzstange um X |
| `ha_sl_wz` | `-atan(( ha_e_x - ha_sl_c_x ) / ( ha_e_y - ha_sl_c_y ))` | -8,81° | abgeleitet: Drehung Huellkoerper Sturzstange um Z |
| `ha_l_y` | `ha_ql_y + ha_ql_dl * cos(ha_ql_phi) - ha_ql_dl_z * sin(ha_ql_phi)` | 69,76 mm | abgeleitet: Daempfer unten quer (Stellung) |
| `ha_l_z` | `ha_ql_z + ha_ql_dl * sin(ha_ql_phi) + ha_ql_dl_z * cos(ha_ql_phi)` | 30,63 mm | abgeleitet: Daempfer unten Hoehe (Stellung) |
| `ha_l_aus_y` | `ha_ql_y + ha_ql_dl * cos(ha_ql_phi0 + ha_dphi_aus) - ha_ql_dl_z * sin(ha_ql_phi0 + ha_dphi_aus)` | 66,92 mm | abgeleitet: Daempfer unten quer, ausgefedert |
| `ha_l_aus_z` | `ha_ql_z + ha_ql_dl * sin(ha_ql_phi0 + ha_dphi_aus) + ha_ql_dl_z * cos(ha_ql_phi0 + ha_dphi_aus)` | 23,35 mm | abgeleitet: Daempfer unten Hoehe, ausgefedert |
| `ha_l_ein_y` | `ha_ql_y + ha_ql_dl * cos(ha_ql_phi0 + ha_dphi_ein) - ha_ql_dl_z * sin(ha_ql_phi0 + ha_dphi_ein)` | 70,67 mm | abgeleitet: Daempfer unten quer, eingefedert |
| `ha_l_ein_z` | `ha_ql_z + ha_ql_dl * sin(ha_ql_phi0 + ha_dphi_ein) + ha_ql_dl_z * cos(ha_ql_phi0 + ha_dphi_ein)` | 44,87 mm | abgeleitet: Daempfer unten Hoehe, eingefedert |
| `ha_du_z` | `ha_l_aus_z + sqrt(ha_daempfer_l_aus ^ 2 - ( ha_du_y - ha_l_aus_y ) ^ 2)` | 101,89 mm | abgeleitet: Daempfer oben Hoehe, so dass der Daempfer ausgefedert genau ha_daempfer_l_aus lang ist (Endanschlag begrenzt das Ausfedern) |
| `ha_daempfer_l_ein` | `sqrt(( ha_du_y - ha_l_ein_y ) ^ 2 + ( ha_du_z - ha_l_ein_z ) ^ 2)` | 60,09 mm | abgeleitet: Augenabstand eingefedert |
| `ha_daempfer_hub_bedarf` | `ha_daempfer_l_aus - ha_daempfer_l_ein` | 19,91 mm | Pruefmass: Daempferhub fuer den ganzen Federweg |
| `ha_daempfer_reserve` | `ha_daempfer_hub - ha_daempfer_hub_bedarf` | 0,09 mm | Pruefmass: Hub minus Bedarf, >= 0 und klein = Daempfer begrenzt den Federweg am Ende (MECH-HAC-010) |
| `ha_hebel` | `federweg / ha_daempfer_hub_bedarf` | 1,758 | Pruefmass: Hebelverhaeltnis Rad:Daempfer gemittelt ueber den Federweg, muss >= ha_hebel_tt02b sein (MECH-HAC-010) |
| `ha_daempfer_l` | `sqrt(( ha_du_y - ha_l_y ) ^ 2 + ( ha_du_z - ha_l_z ) ^ 2)` | 73,51 mm | abgeleitet: Augenabstand in der Stellung |
| `ha_daempfer_w` | `90 deg + atan(( ha_l_y - ha_du_y ) / ( ha_du_z - ha_l_z ))` | 104,22° | abgeleitet: Drehung Huellkoerper Daempfer um X |
| `ha_daempfer_neig` | `90 deg - ha_daempfer_w` | -14,22° | Pruefmass: Neigung des Daempfers gegen die Senkrechte (oben nach innen = negativ) |
| `ha_d_stiel_d` | `6 mm` | 6,00 mm | CVA-Daempfer: Stiel/Kolbenstangenende am Auge, vorlaeufig |
| `ha_db_mitte_b` | `ha_turm_b` | 32,00 mm | Daempferbruecke: Breite des Mittelteils (= Turmbreite) |
| `ha_db_z_u` | `ha_db_sz_u - 5 mm` | 31,00 mm | Daempferbruecke: Unterkante (2 mm ueber der Grundplatte) |
| `ha_db_steg_h` | `14 mm` | 14,00 mm | Daempferbruecke: Breite der Stege zur Sturzstange und zum Daempfer |
| `ha_db_auge_d` | `14 mm` | 14,00 mm | Daempferbruecke: Rundung um Kugelkopf und Daempferbolzen |
| `ha_db_r` | `2 mm` | 2,00 mm | Daempferbruecke: Radius der Innenecken (fraesbar, >= 1,5 mm) |
| `ha_dl_bohr_t` | `ha_einsatz_t + 3 mm` | 9,00 mm | Querlenker: Bohrtiefe Daempferlasche (Einsatz + Freiraum fuer M3 x 14) |
| `ha_ql_platte_z` | `-2 mm` | -2,00 mm | Querlenker: aeussere Platte 2 mm unter die Querlenkerebene versetzt (Freigang zum Becher N1 beim Ausfedern, tiefster Punkt >= 20 mm) |
| `ha_rt_verb_kurz` | `1 mm` | 1,00 mm | Radtraeger: Verbindungsstege je Seite kuerzer als die Nabe (Abstand zu Becher N1 und Mitnehmer trotz Vorspur) |
| `ha_durch` | `2 mm` | 2,00 mm | Modellierhilfe: Zugabe fuer durchgehende Schnitte und Ueberlappungen beim Vereinen (keine Wirkung auf die Bauteilmasse) |
| `ha_e2_tr_luft` | `ha_e2_einbau - ha_e2_lager_b / 2 - ha_tellerrad_d / 2` | 1,50 mm | Pruefmass: Luft Tellerrad-Aussenkreis bis hinteres E2-Lager in X, muss >= ha_zahn_luft sein (MECH-HAC-002, Review 1) |
| `ha_e2v_spalt` | `0.5 mm` | 0,50 mm | Lagerbock E2: Luft Vorderseite Lagerbock/vorderes Lager bis Huelle Becher E2 (Kardanwelle), Annahme wie ha_n2_luft |
| `ha_e2v_x` | `ha_e2_becher_x - ha_e2_lager_b / 2` | -101,00 mm | abgeleitet: Mitte vorderes E2-Lager im Lagerbock; Vorderseite Lager = Hinterkante Becher E2, die Becherschulter liegt am Innenring an und sichert das Lager axial (Nutzerentscheidung 2026-11-01 nach Review 2) |
| `ha_lb_d` | `ha_gh_hals_d` | 15,10 mm | abgeleitet: Lagerbock E2, Aussendurchmesser Lagerring (Wand 2 mm um den Lagersitz) |
| `ha_lb_dicke` | `ha_lb_x_vorne - ( ha_e2v_x - ha_e2_lager_b / 2 ) + ha_e2_lippe` | 3,50 mm | abgeleitet: Lagerbock E2, Dicke in X (Lagersitz ohne Ueberstand + Lippe zahnradseitig ha_e2_lippe) |
| `ha_lb_x_vorne` | `ha_e2_becher_x - ha_e2v_spalt` | -99,50 mm | abgeleitet: Vorderseite Lagerbock E2, ha_e2v_spalt hinter dem drehenden Becher E2; das vordere Lager steht um ha_e2v_spalt vor (wie Radtraeger ha_rt_spalt) |
| `ha_lb_xm` | `ha_lb_x_vorne - ha_lb_dicke / 2` | -101,25 mm | abgeleitet: Mitte Lagerring und Steg des Lagerbocks in X |
| `ha_lb_steg_b` | `18 mm` | 18,00 mm | Lagerbock E2: Breite des senkrechten Stegs (quer); 18 mm, damit die Biegesicherheit bei 3,5 mm Dicke wie vorher bleibt (Lastrechnung docs/hinterachse.md, Review 2) |
| `ha_lb_s_y` | `12.5 mm` | 12,50 mm | Lagerbock E2: Schrauben M3 quer (zwischen den Gewindeeinsaetzen der Grundplatte bei +-18 und dem Bauraum der Rutschkupplung) |
| `ha_lb_s_z` | `32.3 mm` | 32,30 mm | Lagerbock E2: Schrauben M3 Hoehe (unter dem Bauraum der Rutschkupplung, Einsatz 1,3 mm ueber der Grundplatte) |
| `ha_lb_auge_d` | `2 * ( ha_lb_s_z - platte_oben )` | 6,60 mm | abgeleitet: Lagerbock E2, Rundung um die Schrauben (endet unten auf der Grundplatte, Schraubenkopf Ø 5,5 liegt voll auf) |
| `ha_lb_fuss_y` | `ha_lb_s_y + ha_lb_auge_d / 2` | 15,80 mm | abgeleitet: Lagerbock E2, Fuss halbe Breite quer |
| `ha_lb_fuss_h` | `ha_lb_s_z - platte_oben` | 3,30 mm | abgeleitet: Lagerbock E2, Fusshoehe auf der Grundplatte (unter dem Bauraum der Rutschkupplung) |
| `ha_lb_l` | `ha_lb_x_vorne - ha_gh_x_vorne` | 10,00 mm | abgeleitet: Lagerbock E2, Fusslaenge von der Vorderseite des Getriebegehaeuses bis zur Vorderseite des Lagerbocks |
| `ha_e2_lager_frei` | `ha_e2_lagerabstand - ha_e2_lager_b` | 5,00 mm | Pruefmass: Abstand der E2-Lager innen (Innenring zu Innenring), Platz fuer Mitnehmer und Hauptzahnrad/Rutschkupplung |
| `ha_hz_raum` | `ha_lb_x_vorne - ha_lb_dicke - ha_gh_hals_x` | 5,00 mm | Pruefmass: freie Laenge auf E2 zwischen hinterem Lager bzw. Lagerhals (Gehaeuse) und Rueckseite Lagerbock/vorderes Lager fuer Hauptzahnrad/Rutschkupplung (Zahnradraum, Review 2: ohne Lippen und ohne Steg im Drehraum) |
| `ha_hz_bedarf` | `e2_mitnehmer_l` | 8,00 mm | Bedarf auf E2 zwischen den Lagern fuer Mitnehmer GB3 + Hauptzahnrad GB5 (Bausatz) zusammen, vorlaeufig >= 8 mm (= e2_mitnehmer_l Skelett, Massskette Review 2), am Teil messen |
| `ha_hz_fehl` | `ha_hz_bedarf - ha_hz_raum` | 3,00 mm | Pruefmass: Fehlbetrag Zahnradraum = Bedarf GB3+GB5 - ha_hz_raum; > 0 = offen bis Messung (Nutzerentscheidung 2026-11-01), muss nach dem Messen <= 0 werden |
| `ha_hz_raum_pruef` | `( ha_hz_raum + abs(ha_hz_raum) ) / 2` | 5,00 mm | Pruefmass mit Schutz: = ha_hz_raum fuer ha_hz_raum > 0, sonst 0; steuert die Breite des Huellkoerpers hinterachse-hauptzahnrad/drehraum, eine Extrusion mit 0 mm schlaegt fehl, so wird ein Zahnradraum <= 0 als Fehler in der Zeitleiste sichtbar (Review 2) |
| `ha_hz_x0` | `ha_gh_hals_x` | -108,00 mm | abgeleitet: Beginn des Zahnradraums auf E2 = Vorderseite hinteres E2-Lager bzw. Lagerhals (Huellkoerper hinterachse-hauptzahnrad) |
| `ha_e2h_spiel` | `ha_lager_spiel` | 0,10 mm | Passung hinterer E2-Lagersitz (Festlager im geteilten Gehaeuse): vorlaeufig = ha_lager_spiel; nach dem Probedruck so waehlen, dass die verschraubten Haelften den Aussenring klemmen (axiale Festlegung ohne Lippe, Nutzerentscheidung 2026-11-01 nach Review 2) |
| `ha_diff_d` | `22 mm` | 22,00 mm | Huellkoerper Diff-Gehaeuse: Durchmesser vorlaeufig 22 mm (Annahme, Kegelritzel muss innen vorbei), am Teil messen |
| `ha_diff_nabe_d` | `8 mm` | 8,00 mm | Diff: Nabe in den Diff-Lagern 8x12x3,5 (Innendurchmesser 8 mm), belegt durch Lagergroesse |
| `ha_tellerrad_b` | `8 mm` | 8,00 mm | Huellkoerper Tellerrad GB4: Breite quer vorlaeufig 8 mm, am Teil messen |
| `ha_tr_spalt` | `0.5 mm` | 0,50 mm | Huellkoerper: Spalt Tellerrad zur Kegelritzel-Huelle (die Zaehne greifen in Wirklichkeit ineinander) |
| `ha_tellerrad_y0` | `ha_ritzel_d / 2 + ha_tr_spalt` | 7,50 mm | abgeleitet: Zahnseite Tellerrad quer ab Fahrzeugmitte (Seite links, vorlaeufig; der Zahnraum ist symmetrisch) |
| `ha_ritzel_l` | `9 mm` | 9,00 mm | Huellkoerper Kegelritzel GB2: Laenge vorlaeufig 9 mm (vom hinteren E2-Lager zur Diff-Achse), am Teil messen |
| `ha_e2_welle_d` | `5 mm` | 5,00 mm | Kegelritzelwelle E2: Wellendurchmesser 5 mm, belegt durch Lager 5x11x4 |
| `ha_e2_hinten_x` | `-achse_x + ha_e2_einbau - ha_e2_lager_b / 2 - ha_e2_scheibe - ha_ritzel_l` | -121,50 mm | abgeleitet: hinteres Ende Kegelritzel/E2 (Huellkoerper) |
| `ha_e2_becher_x` | `kardan_hinten_x - kardan_becher_l` | -99,00 mm | abgeleitet: Hinterkante Becher E2 (Huelle Kardanwelle im Skelett), Ende Welle E2 im Huellkoerper |
| `ha_e2_scheibe` | `0.5 mm` | 0,50 mm | Passscheibe zwischen Kegelritzel GB2 und hinterem E2-Lager (Zahneingriff, Stueckliste Pos. 63), vorlaeufig 0,5 mm; Kegelritzel laeuft damit frei vor der Schulter des Lagersitzes |
| `ha_diff_spalt` | `0.5 mm` | 0,50 mm | Passscheibe zwischen Diff und Diff-Lager je Seite (Stueckliste Pos. 63), vorlaeufig 0,5 mm; Diff laeuft damit frei vor der Zahnraumdecke |
| `ha_lb_rk_luft` | `0.5 mm` | 0,50 mm | Lagerbock E2: Luft der Querstege zum Bauraum der Rutschkupplung (Skelett rk_d) |
| `ha_lb_quer_z` | `antrieb_z - sqrt(( rk_d / 2 ) ^ 2 - ( ha_lb_steg_b / 2 ) ^ 2) - ha_lb_rk_luft` | 34,28 mm | abgeleitet: Lagerbock E2, Oberkante der Querstege zwischen Steg und Schraubenaugen (unter dem Bauraum der Rutschkupplung), aus Lastrechnung (docs/hinterachse.md) |

## Parametertest (MECH-HAC-001)

| Test | Ergebnis |
|---|---|
| Lagersitz: `ha_lager_spiel` 0,1 → 0,3 mm (Version 6) | Zeitleiste (511 Elemente) **ohne Fehler**; Sitze Diff Ø 12,3, E2 Ø 11,3, Radlager Ø 11,3 mm; Nabe des Radträgers wächst mit (Wand bleibt 2,5 mm). Zurück auf 0,1 mm, ohne Fehler. |
| Ersatztest eigene Parameter (gleichzeitig): `ha_ql_z` 41, `ha_rt_b_dy` −13, `ha_sl_c_y` 30, `ha_e2_einbau` 21, `ha_diff_lager_y` 18,2, `ha_db_dicke` 8, `ha_tellerrad_d` 40, `ha_radlager_abstand` 5,5, `ha_ql_dicke` 6, `ha_felge_innen_d` 52, `ha_daempfer_l_aus` 82 mm, `ha_vorspur` 3°, `ha_sturz` −2° | Zeitleiste **ohne Fehler**, `ha_vorspur_ist` 3,00°, `ha_sturz_ist` −2,00°. Zurückgesetzt, ohne Fehler. |
| Sturz −3° und 0° (MECH-HAC-009) | ohne Fehler, 0 ungewollte Überschneidungen (siehe oben) |
| Stellungen ausgefedert / eingefedert (`ha_ql_dphi`) | ohne Fehler (siehe Federweg) |
| Version 8, Lagersitz und neue Teile (gleichzeitig): `ha_lager_spiel` 0,3, `ha_e2_einbau` 24, `ha_lb_s_y` 13, `ha_e2v_spalt` 1, `ha_tellerrad_d` 40, `ha_diff_d` 20, `ha_ritzel_l` 8, `ha_lb_steg_b` 12 mm | Zeitleiste **ohne Fehler**; Lagerhals folgt (X −105,0), Lagerbock X −109,0…−100,0. Zurückgesetzt, ohne Fehler. Die neuen Teile hängen nur an abgeleiteten Skelett-Parametern (`achse_x`, `antrieb_z`, `platte_oben`, `kardan_hinten_x`, `kardan_becher_l`, `rk_d`) und folgen damit auch dem Radstand; der Radstand-Test mit dem Skelett wurde in Version 6 gemacht und nicht wiederholt, weil das Skelett nicht erneut gespeichert werden sollte. |
| Review 2 (Arbeitsstand von Version 11, gleichzeitig): `ha_lager_spiel` 0,3, `ha_e2_lippe` 1, `ha_e2v_spalt` 1, `ha_lb_steg_b` 16, `ha_hz_bedarf` 10, `ha_e2_einbau` 24, `ha_tellerrad_d` 40 mm | Zeitleiste **ohne Fehler**; `ha_hz_raum` 2,0, `ha_hz_fehl` 8,0; Lagerbock X −109,0…−100,0, Gehäuse bis X −106,0, Drehraum X −106,0…−104,0, Hauptzahnrad-Bedarf X −106,0…−96,0, vorderes Lager X −103,0…−99,0 (bleibt am Becher). Zurückgesetzt, ohne Fehler. Dazu einzeln: `ha_e2h_spiel` −0,05 mm (Sitz Ø 10,95) ohne Fehler; **Schutz** `ha_e2_lippe` 3 mm (`ha_hz_raum` −1,0) bzw. 2,5 mm (0,0): Fehler am Element `drehraum`, wie gewollt; zurück ohne Fehler. Bewegungsprüfung in drei Stellungen ohne Fehler (siehe Interferenz). |
| **`radstand` 280 mm im Skelett → Ableitung aktualisieren** | **bestanden** (Nutzerentscheidung 2026-11-01, siehe Anforderungsdokument). Skelett `radstand` = 280 mm: Zeitleiste des Skeletts (327 Elemente) ohne Fehler, `achse_x` 140 mm, gespeichert als **v13**. Hier `Document.updateAllReferences()`, dann `DeriveFeature.setSourceEntities(…)` der Skelett-Ableitung und `Design.computeAll()`: `radstand_Ref` 280 mm, Zeitleiste (511 Elemente) **ohne Fehler und Warnungen**. Alle Teile der Hinterachse folgen der Achse um −7,0 mm in X, Y und Z bleiben gleich (Bild unten): Getriebegehäuse X −163,5…−110,0, Böcke X −163…−153 und −127…−117, Querlenker −169,5…−127,5, Radträger −148,2…−131,8, Dämpferbrücke −169,5…−163,5. Prüfmaße unverändert (Radmitte 104,00 / 41,00, `ha_gelenk_dl` −0,051 mm, Vorspur 2,000°, Sturz −0,999°, `ha_daempfer_reserve` 0,088 mm). Interferenz der Hinterachse mit sich selbst und dem Mittelantrieb: 0 ungewollt. Die abgeleiteten Körper der Grundplatte bleiben dabei bei 266 mm stehen, weil die Grundplatte nicht mit aktualisiert wurde (gewollt, die Grundplatte ist nicht Teil dieser Anforderung). Danach Skelett zurück auf 266 mm, ohne Fehler, gespeichert als **v14** (Maße gleich v12), hier erneut aktualisiert: Referenz v14, Zeitleiste ohne Fehler, alle Hüllquader, Volumina (109,396 cm³ gesamt), Prüfmaße und die 14 gewollten Überschneidungen genau wie in Version 5. Gespeichert als Version 6, Exporte aus Version 6 erneuert (Geometrie gleich). Nach Review 1 ersetzt durch Version 8, nach Review 2 durch Version 11 (siehe Kopf). Die Skelett-Exporte bleiben aus v10, weil sich die Geometrie nicht geändert hat. |

![Parametertest mit radstand 280 mm](images/hinterachse-parametertest-280.png)

*Parametertest bei `radstand` 280 mm, von oben (vorne ist oben). Die Hinterachse ist mit der Achse 7 mm nach hinten gewandert; Grundplatte und Oberdeck (abgeleitet von der Grundplatte v11) stehen noch bei 266 mm.*

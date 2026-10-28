# Skelettmodell des Fahrzeugs

- **Anforderungen:** `docs/anforderungen/skelett.md` (Kürzel SKE, Fassung 2)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-skelett“, **Version 10** (Fassung 2; v7 ist der erste Stand der Umstellung, v8 hat korrigierte Parameterkommentare, v9 enthält die Änderungen aus Review 1: Motorhalter, Bilanz auf E2; v10 die aus Review 2: `rk_luft` mit vorderem Lager und Mitnehmer, Kommentare)
- **Exporte:** `cad/fusion/skelett.f3d`, `cad/step/skelett.step` (beide aus Version 10)
- **Stand:** 2026-10-31

Das Skelett ist kein Bauteil. Es ist die Bezugsgeometrie für Grundplatte, Achsen, Mittelantrieb, Lenkung und Elektronikhalter: Fahrzeugparameter, Radpositionen mit Bewegungsraum, Hüllkörper aller räumlich relevanten Bausatz- und Zukaufteile und Bauraum für den späteren 4WD-Antrieb.

> **Fassung 2 (Plattformwechsel):** Spenderplattform ist seit dem 2026-10-28 der **Tamiya TT-02B** (Bausatz Neo Scorcher 58568). Spur, Radstand, Räder, Antriebsstrang und Layout kommen vom TT-02B. Die Fassung 1 mit dem früheren Spender steht in der Git-Historie (PR #5), siehe [Historie](#historie).

## Ergebnis des Meilensteins

| Frage | Ergebnis |
|---|---|
| Passt alles hinein? | **Die Hüllkörper ja, der Antrieb vom Motor zum Hauptzahnrad noch nicht.** Die Interferenzanalyse über alle 39 Hüllkörper-Komponenten (+ Root) findet mit Ritzel 25Z und mit Ritzel 16Z jeweils **51 Überschneidungen, alle gewollt, 0 ungewollt** (Tabelle [Interferenz](#interferenzprüfung-mech-ske-010)). Mit Bauraum für den Motorhalter (`motorhalter_dicke` = 4 mm, vorläufig) reicht die Motorwelle aber nicht bis in die Zahnebene: **`motor_welle_reserve` = −3,0 mm** (siehe [Zahnebene](#zahnebene-ritzel-und-motor)). Das ist ein offener Punkt für „Mittelantrieb“; MECH-SKE-008 ist deshalb nur **teilweise erfüllt** (vom Nutzer so abgenommen, Entscheidung 2026-10-28 nach Review 2). Ebenso fehlt der Rutschkupplung um den Becher von E2 Platz: **`rk_luft` = −9 mm**, vom Nutzer am 2026-10-31 als offener Punkt für „Mittelantrieb“ abgenommen. Alle Aussagen gelten für vorläufige Maße. |
| Länge der Grundplatte | **314,0 mm** (Hinterkante Hinterachsgetriebe bis Vorderkante Vorderachsgetriebe) |
| Breite der Grundplatte | **132,0 mm** im breiten Teil (Akku links bis Y = 58 mm, Elektronik rechts bis Y = −74 mm). Hinten 49,7 mm (Getriebe), vorne 57,1 mm (Getriebe links bis Servo rechts). |
| Trennstelle | **`teilung_x` = 0 mm** (Fahrzeugmitte), Stoß mit 30 mm Überlappung von X = −15 bis +15 mm |
| Teile für den Druck | hinten **172,0 × 132,0 mm**, vorne **172,0 × 132,0 mm**, beide einschließlich Überlappung ≤ 250 × 250 mm |
| Schwerpunkt quer | **−4,19 mm** (rechts) neben der Fahrzeugmitte (Grenze 10 mm), über das ganze Design (1123,7 g, Räder vorläufig je 100 g) |
| Kardanwelle | `getriebe_eingang` ist so gelegt, dass E1 mit dem Vergleichswert 168 mm passt; `kardan_spiel` = **0,00 mm** ist deshalb **kein unabhängiger Nachweis**. Länge von E1 und Einstecktiefe in die Becher sind unbelegt (🔧 bei Lieferung). |
| **Wichtigste offene Punkte** (für „Mittelantrieb“) | 1. **Motorwelle zu kurz** für Motorhalter, Abdeckung und Ritzel hintereinander (`motor_welle_reserve` = −3,0 mm). 2. Auf der Kegelritzelwelle E2 bleiben zwischen Getriebe und Becher nach den vorläufigen Maßen nur **10 mm** (`e2_frei`); Lager BB2, Mitnehmer und Rutschkupplung in Reihe brauchen **34 mm** (`rk_serie_luft` = **−24 mm**). Der Bauraum der Rutschkupplung umschließt deshalb den Becher von E2 (siehe [Rutschkupplung](#rutschkupplung-auf-der-kegelritzelwelle)); auch dann fehlen mit vorderem Lager BB2 und Mitnehmer **9 mm** (`rk_luft` = **−9 mm**). Beides ist ein **Ergebnis vorläufiger Maße**: Schon die Bausatzteile BB2 und GB3 (ca. 12 mm) passen rechnerisch nicht in die 10 mm, die Kette `getriebe_eingang`/`kardan_becher_l`/`getriebe_vor_achse` ist also um einige Millimeter unsicher. |

![Skelett von oben](images/skelett-oben.png)

*Von oben, vorne ist oben, links ist links. Blau: Maße belegt. Rot: Maße vorläufig mit Zuschlag. Gelb: Bauraum (Zahnradabdeckung, Entnahmeweg Akku). Grün durchscheinend: Bewegungsraum der Räder, der Antriebswellen und der Radachsen. Grau: Grundplatte.*

![Skelett von der Seite](images/skelett-seite.png)

*Von rechts, vorne ist rechts. Man sieht den Stoß der Grundplatte in der Fahrzeugmitte (Überlappung mit halber Plattenstärke je Teil), den Motor vor dem Hinterachsgetriebe und den Entnahmeweg über dem Akku.*

![Skelett isometrisch](images/skelett-iso.png)

## Quellen

| Kürzel | Quelle |
|---|---|
| [A1] | Tamiya, Bauanleitung TT-02B Chassis (11053619): https://www.tamiya.com/english/rc/rcmanual/tt02b.pdf. **Enthält keine Längenmaße.** Maße daraus stammen aus den Zeichnungen: Kleinteile am Seitenrand und auf S. 23 sind im Maßstab 1:1 gezeichnet (geprüft an der Schraube MB1 3 × 32 mm: 31,75 mm Schaft gemessen, und an der Radachse N1: 5,07 mm Wellendurchmesser für das Lager 1150 = 5 × 11 mm). Längen aus Explosionszeichnungen sind nur als Verhältnis zu einem 1:1-Teil in derselben Achsrichtung verwertbar. |
| [P2] | Tamiya, Neo Scorcher (TT-02B) 58568, Specifications (Radstand 266 mm, Spur 217/208 mm, Reifen 32/82 und 41/82 mm, Länge 380 mm, Breite 250 mm): https://tamiya.com/english/products/58568/index.html |
| [K1] | HobbyEtc, X-Spede Alu-Kardanwelle mit Stahlbechern für TT-02 (TTT125HS06): Welle 168 mm × Ø 6 mm, Gelenk vorne 33,5 mm, hinten 41 mm. Vergleichswert für E1 und E2: https://store.hobbyetc.com/parts/view/84121 |
| [E2], [E4], [E8] | wie in `docs/zukaufteile-v1.md` (Motor, Empfänger, UBEC) |

Bausatzteile werden mit der Teilebezeichnung der Anleitung genannt: **E1** Kardanwelle, **E2** Kegelritzelwelle mit Becher (2 ×), **GB2** Kegelritzel, **GB4** Tellerrad, **GB5** Hauptzahnrad 70Z, **N1** Radachse, **N2** Diff-Becher, **N3** Antriebswelle (Knochen), **MB5/MB11** Dämpferfedern hinten/vorne.

## Koordinatensystem (MECH-SKE-003)

- Ursprung: Fahrzeugmitte quer, Mitte zwischen den Achsen längs, Bodenebene.
- **X** längs, positiv nach vorne. **Y** quer, positiv nach links. **Z** hoch, Boden bei Z = 0.
- Konstruktionslage: statisch, fahrfertig, Räder auf dem Boden, Lenkung geradeaus.
- Das Design ist ein **Hybrid-Design** (Komponenten und Bezugsgeometrie in der Wurzel).

Benannte Konstruktionsebenen in der Wurzelkomponente, alle als Versatz der Ursprungsebenen:

| Ebene | Lage | Parameter |
|---|---|---|
| Vorderachse | X = +133,0 mm | `achse_x` |
| Hinterachse | X = −133,0 mm | `-achse_x` |
| Fahrzeugmitte | Y = 0 | Ursprungsebene XZ |
| Boden | Z = 0 | Ursprungsebene XY |
| Unterkante Grundplatte | Z = 25 mm | `bodenfreiheit` |
| Oberkante Grundplatte | Z = 29 mm | `platte_oben` |
| Antriebsachse | Z = 56,6 mm | `antrieb_z` |
| Teilung Grundplatte | X = 0 mm | `teilung_x` |

Dazu je Vorderrad eine Lenkachse (`lenkachse-vl`, `lenkachse-vr`), Schnitt zweier Ebenen bei X = `achse_x` und Y = ±(`rad_y_v` − `lenkachse_versatz`) = ±88,5 mm.

## Aufbau in Fusion

- Jeder Hüllkörper ist eine eigene Komponente, Name nach dem Schema `<baugruppe>-<teil>`, z. B. `elektronik-akku` oder `antrieb-getriebe-hinten`.
- Jeder Körper entsteht aus einer voll bestimmten Skizze im Ursprung der Komponente (Rechteck mittig zum Ursprung oder Kreis um den Ursprung), einer symmetrischen Extrusion und einer Verschiebung (X/Y/Z). Alle Maße der Skizzen, die Extrusionslängen und die Verschiebungen sind Ausdrücke aus Benutzerparametern. Zusammengesetzte Hüllkörper (Zahnradabdeckung, Kardanwelle mit Bechern, Getriebe mit Diff-Bechern, Bewegungsräume) werden mit „Kombinieren“ vereinigt.
- Feste Zahlen gibt es nur bei Lagen auf der Fahrzeugmitte (Verschiebung Y = 0 mm), bei Winkeln von 0° und bei den Ursprungsebenen Fahrzeugmitte und Boden. Das sind Festlegungen des Koordinatensystems, keine Maße eines Hüllkörpers. Prüfskript über alle 517 Modellparameter: keine andere feste Zahl.
- **Vorne und hinten getrennt:** Spur und Radbreite sind beim TT-02B vorne und hinten verschieden. Alle vorderen Komponenten (`*-vl`, `*-vr`) verwenden `rad_y_v` und `rad_breite_v`, die hinteren `rad_y` und `rad_breite`. Die Dämpfer vorne verwenden `daempfer_l_v`.
- Bewegungsraum der Räder: zwei Zylinder in der tiefsten und höchsten Radstellung, verbunden durch einen Quader; vorne zusätzlich als Kreismuster um die Lenkachse mit `lenk_schritte` = 7 Stellungen über ±`lenkwinkel_max` (Schritt 10°) und vereinigt.
- Antriebswellen: schräger Zylinder `antriebswelle_d` × Wellenlänge vom inneren Kreuzstift (Y = ±`diff_abtrieb_y`, Z = `antrieb_z`) zum äußeren Kreuzstift auf Radmittenhöhe. Die Wellenlänge gilt räumlich; das äußere Gelenk liegt bei Y = `diff_abtrieb_y` + √(l² − `antrieb_dz`²) = 89,80 mm.
- Bewegungsraum der Wellen und Radachsen (`antrieb-wellenraum-*`): Die Welle schwenkt um das innere Gelenk von ausgefedert bis eingefedert (`wellen_schritte` = 7 Stellungen), die Radachse folgt dem Rad über den Federweg. Vorne dreht die Radachse zusätzlich mit `lenk_schritte` Stellungen um die Lenkachse, die Welle schwenkt um ±`antriebswelle_v_gier` um eine senkrechte Achse durch das innere Gelenk. **Neu in Fassung 2:** Das äußere Gelenk liegt beim TT-02B nur 1,30 mm neben der Lenkachse; der rechnerische Schwenk wäre ±0,62°. Dann fallen die 3 Musterstellungen fast zusammen und die Vereinigung in Fusion scheitert. `antriebswelle_v_gier` ist deshalb mindestens 2° (größer ist sicher).
- Massen: Die Hüllkörper mit belegter Masse haben je ein eigenes Material (`masse-<komponente>`), die Räder je Achse ein gemeinsames Material (`masse-fahrwerk-rad-v`, `masse-fahrwerk-rad-h`, weil die Räder vorne und hinten verschieden breit sind). Die Dichte ist so gesetzt, dass Fusion den Wert des Masse-Parameters anzeigt. Alle anderen Körper haben das Material `masse-null` (0,001 kg/m³). **Die Masse-Parameter sind nicht ans Modell gebunden.** Nach einer Änderung eines Masse-Parameters oder der Maße dieser Hüllkörper den [Massenabgleich](#massenabgleich-skript) ausführen.
- **Referenz für spätere Baugruppen:** Jede Baugruppe entsteht in einem eigenen Fusion-Design im Projekt „open-rc-car“ und übernimmt Benutzerparameter, Bezugsebenen und Hüllkörper per **Ableiten** aus „open-rc-car-skelett“. Alle Benutzerparameter sind als Favoriten markiert (Prüfskript: 155 von 155). Die Umstellung ist eine neue Version desselben Designs, die Ableitung der Grundplatte (PR #6) bleibt erhalten und wird dort mit „Ableitung aktualisieren“ nachgezogen.

## Parameterliste (MECH-SKE-001, MECH-SKE-002)

155 Benutzerparameter, jeder mit Kommentar (Quelle, „belegt“, „vorläufig“ oder „abgeleitet“), Werte im Startzustand, direkt aus Fusion ausgelesen. **Prüfmaße** (`*_spiel`, `*_luft`, `*_reserve`, `e2_frei`) steuern nichts im Modell; sie zeigen, ob feste Bausatz- und Zukaufteil-Maße zusammenpassen. Die Parameter und Hüllkörper der Fassung 1 sind entfernt (Liste unter [Historie](#historie)). Prüfskript: Suche nach den Bezeichnungen des früheren Spenders und seiner Quellen in Parameternamen, Ausdrücken, Kommentaren und Komponentennamen ergibt 0 Treffer.

**Spur:** Tamiya nennt „Tread“ 217 mm vorne und 208 mm hinten [P2]. Der Wert bezieht sich auf **Radmitte zu Radmitte**: 217 + 32 = 249 mm und 208 + 41 = 249 mm, das ist die Fahrzeugbreite von 250 mm [P2]. Außen über die Räder gemessen wäre das Auto nur 217 mm breit. Deshalb `rad_y` = `spurbreite` / 2.

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `radstand` | `266 mm` | 266,00 mm | Fahrzeug: belegt, Tamiya TT-02B 58568 Specifications [P2] (Wheelbase 266 mm) |
| `spurbreite` | `208 mm` | 208,00 mm | Fahrzeug: Spur hinten, belegt [P2] (Tread 208 mm hinten); Bezug Radmitte zu Radmitte, weil 208 + 41 = 249 mm ≈ Fahrzeugbreite 250 mm [P2] |
| `rad_durchmesser` | `82 mm` | 82,00 mm | Rad: belegt, Reifen Tamiya 58568 [P2] (82 mm) |
| `rad_breite` | `41 mm` | 41,00 mm | Rad hinten: belegt, Reifen Tamiya 58568 [P2] (41 mm) |
| `bodenfreiheit` | `25 mm` | 25,00 mm | Fahrzeug: Plan, MECH-FZG-006 |
| `federweg` | `35 mm` | 35,00 mm | Fahrzeug: vorläufig, am Prototyp messen (MECH-SKE-017): Hub und Einbaulage der CVA-Dämpfer gibt die Anleitung [A1] nicht her, eher zu großer Bewegungsraum |
| `plattenstaerke` | `4 mm` | 4,00 mm | Grundplatte: Plan (Alu) |
| `huelle_zuschlag` | `2 mm` | 2,00 mm | Zuschlag je Seite für vorläufige Hüllkörper (MECH-SKE-007) |
| `einfederweg` | `federweg * 2 / 3` | 23,33 mm | Rad: Annahme 2/3 des Federwegs |
| `ausfederweg` | `federweg - einfederweg` | 11,67 mm | Rad: Annahme 1/3 des Federwegs |
| `lenkwinkel_max` | `30 deg` | 30,00° | Lenkung: Annahme, vorläufig |
| `lenkachse_versatz` | `20 mm` | 20,00 mm | Lenkung: Lenkachse innerhalb der Radmitte, Annahme, vorläufig; für das TT-02B-Rad geprüft über lenkgelenk_versatz |
| `lenk_schritte` | `7` | 7 | Lenkung: Anzahl Radstellungen im Lenk-Bewegungsraum (Schritt 2*lenkwinkel_max/(n-1)) |
| `achse_x` | `radstand / 2` | 133,00 mm | abgeleitet: Radmitte längs |
| `rad_y` | `spurbreite / 2` | 104,00 mm | abgeleitet: Radmitte quer hinten (Spur = Radmitte zu Radmitte) |
| `rad_z` | `rad_durchmesser / 2` | 41,00 mm | abgeleitet: Radmitte Höhe |
| `platte_oben` | `bodenfreiheit + plattenstaerke` | 29,00 mm | abgeleitet: Oberkante Grundplatte |
| `hz_zaehne` | `70` | 70 | Hauptzahnrad: belegt, 70Z (GB5 70T Spur gear, Anleitung [A1] S. 4) |
| `ritzel_zaehne` | `25` | 25 | Motorritzel: Bauraum 16Z bis 25Z (Nutzerentscheidung 2026-10-28), Startwert 25Z = größtes Ritzel; Interferenz auch mit 16 prüfen. Tamiya gibt 16-19Z frei ([A1] S. 19) |
| `hz_d` | `( hz_zaehne + 2 ) * zahn_modul` | 43,20 mm | Hauptzahnrad: Kopfkreis berechnet (z + 2) * m |
| `ritzel_d` | `( ritzel_zaehne + 2 ) * zahn_modul` | 16,20 mm | Motorritzel: Kopfkreis berechnet (z + 2) * m |
| `zahn_achsabstand` | `( hz_zaehne + ritzel_zaehne ) * zahn_modul / 2` | 28,50 mm | Motor: Achsabstand berechnet (z1 + z2) * m / 2 |
| `ritzel_breite` | `ritzel_b_netto + 2 * huelle_zuschlag` | 12,00 mm | Motorritzel: vorläufig, mit Zuschlag |
| `abdeckung_abstand` | `3 mm` | 3,00 mm | Zahnradabdeckung: MECH-SKE-014 |
| `abdeckung_wand` | `2 mm` | 2,00 mm | Zahnradabdeckung: Wand, vorläufig |
| `abdeckung_r` | `hz_d / 2 + abdeckung_abstand + abdeckung_wand` | 26,60 mm | Zahnradabdeckung: abgeleitet |
| `abdeckung_ritzel_r` | `ritzel_d / 2 + abdeckung_abstand + abdeckung_wand` | 13,10 mm | Zahnradabdeckung: abgeleitet |
| `antrieb_luft` | `1 mm` | 1,00 mm | Antrieb: Luft Zahnradabdeckung zu Grundplatte |
| `antrieb_z` | `platte_oben + abdeckung_r + antrieb_luft` | 56,60 mm | abgeleitet: Höhe Kegelritzelwellen, Kardanwelle und Diff-Achsen (Zahnradabdeckung unter dem Hauptzahnrad auf der Grundplatte) |
| `getriebe_b` | `2 * ( diff_abtrieb_y - gelenk_becher ) + 2 * huelle_zuschlag` | 49,72 mm | Getriebe: abgeleitet, Gehäusebreite bis Boden der Diff-Becher N2, mit Zuschlag |
| `getriebe_hinter_achse` | `22 mm + huelle_zuschlag` | 24,00 mm | Getriebe: vorläufig, mit Zuschlag; Tellerrad GB4 ca. Ø 39 mm (Teilezeichnung [A1] S. 23, Maßstab über GB5 Ø 43,2 mm) + Wand, Überstand außen über Diff-Achse |
| `getriebe_eingang` | `49 mm` | 49,00 mm | Getriebe: Diff-Achse bis Becheröffnung der Kegelritzelwelle E2 (Eingang Kardanwelle), vorläufig: so gelegt, dass E1 mit dem Vergleichswert kardan_l passt ((266 - 168) / 2); Länge E1 und Einstecktiefe in die Becher unbelegt, am Teil messen |
| `getriebe_ueber_achse` | `22 mm + huelle_zuschlag` | 24,00 mm | Getriebe: vorläufig, mit Zuschlag; Tellerrad r ca. 19,5 mm + Wand, Höhe über Diff-Achse |
| `getriebe_l` | `getriebe_hinter_achse + getriebe_vor_achse` | 48,00 mm | Getriebe hinten: abgeleitet (Diff, Kegelritzel, Lager) |
| `getriebe_h` | `antrieb_z + getriebe_ueber_achse - platte_oben` | 51,60 mm | Getriebe: abgeleitet |
| `diff_abtrieb_y` | `31.86 mm` | 31,86 mm | Getriebe: Kreuzstift Diff-Abtrieb N2 quer, aus Startlage abgeleitet (Spur 208/217, N1 43,7 mm, N3 60 mm), fest, damit Spuränderungen als radachse_*_spiel sichtbar werden; Vorgabe für das Getriebegehäuse |
| `rk_d` | `hz_d + 2 * huelle_zuschlag` | 47,20 mm | Rutschkupplung: vorläufig, mit Zuschlag, Kopfkreis Hauptzahnrad 70Z |
| `rk_l` | `getriebe_eingang - getriebe_vor_achse` | 25,00 mm | Rutschkupplung: abgeleitet, Bauraum auf der Kegelritzelwelle E2 vom Getriebe bis zur Becheröffnung (umschließt vorderes Lager BB2, Mitnehmer GB3 und Becher von E2) |
| `motor_d` | `36 mm` | 36,00 mm | Motor: belegt, Lindinger [E2] |
| `motor_l` | `52 mm` | 52,00 mm | Motor: belegt, Lindinger [E2] |
| `motor_y` | `-zahn_achsabstand` | -28,50 mm | Motor: abgeleitet, rechts neben der Kegelritzelwelle (wie TT-02B) |
| `antriebswelle_h_l` | `60 mm` | 60,00 mm | Antriebswelle N3 (Knochen), vorne und hinten gleich ([A1] S. 19): Kreuzstiftabstand vorläufig 59-61 mm aus Zeichnung [A1] S. 10/11 (Verhältnis zu N2, 1:1 31,8 mm) |
| `antriebswelle_v_l` | `antriebswelle_h_l` | 60,00 mm | Antriebswelle vorne 4WD: gleiches Teil N3 ([A1] S. 10) |
| `antriebswelle_d` | `10 mm + 2 * huelle_zuschlag` | 14,00 mm | Antriebswelle N3: vorläufig, mit Zuschlag, Kugelende ca. Ø 10 mm (Zeichnung [A1] S. 10) |
| `radachse_d` | `gelenk_becher_d` | 20,60 mm | Radachse N1: Becher Ø 16,6 mm (1:1 [A1] S. 9) mit Zuschlag |
| `daempfer_augen` | `20 mm` | 20,00 mm | Dämpfer: Kappe und Augen, vorläufig, Vergleichsteil |
| `daempfer_feder_d` | `16.5 mm` | 16,50 mm | Dämpfer: Außendurchmesser Feder 16,5 mm aus 1:1-Zeichnung [A1] S. 23, vorläufig |
| `daempfer_d` | `daempfer_feder_d + 2 * huelle_zuschlag` | 20,50 mm | Dämpfer: vorläufig, mit Zuschlag |
| `daempfer_l` | `daempfer_feder_h + daempfer_augen + 2 * huelle_zuschlag` | 88,50 mm | Dämpfer hinten: vorläufig, mit Zuschlag, ausgefedert ca. freie Federlänge + Augen |
| `daempfer_y` | `55 mm` | 55,00 mm | Dämpfer: Lage quer, vorläufig (außerhalb der Diff-Becher) |
| `daempfer_dx` | `24 mm` | 24,00 mm | Dämpfer: Versatz zur Fahrzeugmitte hin, vorläufig |
| `daempfer_z_unten` | `35 mm` | 35,00 mm | Dämpfer: unteres Auge, vorläufig |
| `servo_l` | `40.3 mm` | 40,30 mm | Lenkservo: belegt, Lindinger |
| `servo_b` | `20.2 mm` | 20,20 mm | Lenkservo: belegt, Lindinger |
| `servo_h` | `37.2 mm` | 37,20 mm | Lenkservo: belegt, Lindinger |
| `servo_x` | `achse_x - getriebe_v_l + getriebe_hinter_achse - 1.5 mm - servo_l / 2` | 77,35 mm | Lenkservo: Lage vorläufig, hinter dem Vorderachsgetriebe |
| `servo_y` | `-( kardan_becher_d / 2 + 2 mm + servo_b / 2 )` | -22,10 mm | Lenkservo: Lage vorläufig, rechts neben der Kardanwelle |
| `elektronik_y_aussen` | `74 mm` | 74,00 mm | Elektronik: Außenkante rechts, vorläufig (Empfänger neben dem Motor) |
| `regler_l` | `48.5 mm + 2 * huelle_zuschlag` | 52,50 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 46 / Hobbywing 48,5 |
| `regler_b` | `38 mm + 2 * huelle_zuschlag` | 42,00 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 36,5 / Hobbywing 38 |
| `regler_h` | `34.3 mm + 2 * huelle_zuschlag` | 38,30 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 34,3 / Hobbywing 32, mit Lüfter |
| `regler_x` | `motor_flansch_x + motor_l + 2 mm + regler_l / 2` | 5,25 mm | Regler: Lage vorläufig, vor dem Motor |
| `regler_y` | `-( elektronik_y_aussen - regler_b / 2 )` | -53,00 mm | Regler: Lage |
| `ubec_l` | `45 mm + 2 * huelle_zuschlag` | 49,00 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 43,1 / htmodel 45 |
| `ubec_b` | `32.3 mm + 2 * huelle_zuschlag` | 36,30 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 32,3 / htmodel 20 |
| `ubec_h` | `16.2 mm + 2 * huelle_zuschlag` | 20,20 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 12,5 / htmodel 16,2 |
| `ubec_x` | `regler_x + regler_l / 2 + 2 mm + ubec_l / 2` | 58,00 mm | UBEC: Lage vorläufig, vor dem Regler, neben dem Servo |
| `ubec_y` | `-( elektronik_y_aussen - ubec_b / 2 )` | -55,85 mm | UBEC: Lage |
| `empf_l` | `46 mm` | 46,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_b` | `26 mm` | 26,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_h` | `15 mm` | 15,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_x` | `motor_flansch_x + 1 mm + empf_l / 2` | -51,00 mm | Empfänger: Lage vorläufig, rechts neben dem Motor |
| `empf_y` | `-( elektronik_y_aussen - empf_b / 2 )` | -61,00 mm | Empfänger: Lage |
| `akku_l` | `138 mm` | 138,00 mm | Akku: belegt, RC Team |
| `akku_b` | `46 mm` | 46,00 mm | Akku: belegt, RC Team |
| `akku_h` | `25 mm` | 25,00 mm | Akku: belegt, RC Team |
| `akku_x` | `0 mm` | 0,00 mm | Akku: Lage, vorläufig |
| `akku_y_innen` | `12 mm` | 12,00 mm | Akku: Innenkante links, vorläufig (Kardanwelle + Luft) |
| `akku_y` | `akku_y_innen + akku_b / 2` | 35,00 mm | Akku: abgeleitet |
| `akku_entnahme_h` | `100 mm` | 100,00 mm | Akku: Höhe des freizuhaltenden Entnahmewegs nach oben (MECH-SKE-015) |
| `xt60_l` | `30 mm + 2 * huelle_zuschlag` | 34,00 mm | XT60: vorläufig, mit Zuschlag, Steckerpaar gesteckt, Vergleichsteil |
| `xt60_b` | `16 mm + 2 * huelle_zuschlag` | 20,00 mm | XT60: vorläufig, mit Zuschlag, Vergleichsteil |
| `xt60_h` | `8 mm + 2 * huelle_zuschlag` | 12,00 mm | XT60: vorläufig, mit Zuschlag, Vergleichsteil |
| `xt60_x` | `akku_x + akku_l / 2 + 0.5 mm + xt60_b / 2` | 79,50 mm | XT60: Lage vor dem Akku |
| `xt60_y` | `akku_y_innen + xt60_l / 2` | 29,00 mm | XT60: Lage |
| `teilung_x` | `0 mm` | 0,00 mm | Grundplatte: Trennstelle für den Druck (MECH-SKE-013) |
| `teilung_ueberlappung` | `30 mm` | 30,00 mm | Grundplatte: Überlappung des Stoßes, Annahme |
| `platte_x_hinten` | `-( achse_x + getriebe_hinter_achse )` | -157,00 mm | Grundplatte: abgeleitet, Hinterkante = Getriebe hinten |
| `platte_x_vorne` | `achse_x + getriebe_hinter_achse` | 157,00 mm | Grundplatte: abgeleitet, Vorderkante = Getriebe vorne |
| `platte_mitte_hinten` | `rk_x_hinten` | -109,00 mm | Grundplatte: abgeleitet, breiter Teil ab Rutschkupplung/Zahnradabdeckung |
| `platte_mitte_vorne` | `xt60_x + xt60_b / 2` | 89,50 mm | Grundplatte: abgeleitet, breiter Teil bis XT60 |
| `platte_links` | `akku_y_innen + akku_b` | 58,00 mm | Grundplatte: abgeleitet, Außenkante Akku |
| `platte_rechts` | `elektronik_y_aussen` | 74,00 mm | Grundplatte: abgeleitet, Außenkante Elektronik |
| `platte_schmal_rechts` | `-servo_y + servo_b / 2` | 32,20 mm | Grundplatte: abgeleitet, vorne rechts bis Servo |
| `platte_laenge` | `platte_x_vorne - platte_x_hinten` | 314,00 mm | Grundplatte: Ergebnis Gesamtlänge |
| `platte_breite` | `platte_links + platte_rechts` | 132,00 mm | Grundplatte: Ergebnis Gesamtbreite |
| `akku_masse` | `300 g` | 300,0 g | Masse: belegt, RC Team; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `motor_masse` | `223 g` | 223,0 g | Masse: belegt, Lindinger [E2]; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `regler_masse` | `90 g` | 90,0 g | Masse: belegt, größerer Wert Hobbywing 90 / Lindinger 86,6; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `servo_masse` | `64 g` | 64,0 g | Masse: belegt, Lindinger; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `empf_masse` | `12.7 g` | 12,7 g | Masse: belegt, Lindinger [E4]; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `ubec_masse` | `34 g` | 34,0 g | Masse: belegt, RC Team [E8]; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `antrieb_dz` | `antrieb_z - rad_z` | 15,60 mm | abgeleitet: Höhe Diff-Abtrieb über Radmitte in Konstruktionslage |
| `antriebswelle_h_y` | `diff_abtrieb_y + sqrt(antriebswelle_h_l ^ 2 - antrieb_dz ^ 2)` | 89,80 mm | abgeleitet: äußerer Kreuzstift hinten quer, Welle schräg mit Länge antriebswelle_h_l |
| `antriebswelle_v_y` | `diff_abtrieb_y + sqrt(antriebswelle_v_l ^ 2 - antrieb_dz ^ 2)` | 89,80 mm | abgeleitet: äußerer Kreuzstift vorne quer, Welle schräg mit Länge antriebswelle_v_l |
| `antriebswelle_h_winkel` | `asin(antrieb_dz / antriebswelle_h_l)` | 15,07° | abgeleitet: Neigung Antriebswelle hinten in Konstruktionslage (außen tiefer) |
| `antriebswelle_v_winkel` | `asin(antrieb_dz / antriebswelle_v_l)` | 15,07° | abgeleitet: Neigung Antriebswelle vorne in Konstruktionslage (außen tiefer) |
| `antriebswelle_h_winkel_aus` | `asin(( antrieb_dz + ausfederweg ) / antriebswelle_h_l)` | 27,03° | abgeleitet: Neigung Antriebswelle hinten ausgefedert (Rad um ausfederweg tiefer) |
| `antriebswelle_h_winkel_ein` | `asin(( antrieb_dz - einfederweg ) / antriebswelle_h_l)` | -7,41° | abgeleitet: Neigung Antriebswelle hinten eingefedert (negativ = außen höher) |
| `antriebswelle_v_winkel_aus` | `asin(( antrieb_dz + ausfederweg ) / antriebswelle_v_l)` | 27,03° | abgeleitet: Neigung Antriebswelle vorne ausgefedert |
| `antriebswelle_v_winkel_ein` | `asin(( antrieb_dz - einfederweg ) / antriebswelle_v_l)` | -7,41° | abgeleitet: Neigung Antriebswelle vorne eingefedert (negativ = außen höher) |
| `wellen_schritte` | `7` | 7 | Bewegungsraum Antriebswelle: Anzahl Stellungen über den Federweg |
| `lenkgelenk_versatz` | `antriebswelle_v_y - ( rad_y_v - lenkachse_versatz )` | 1,30 mm | abgeleitet: äußeres Gelenk vorne außerhalb der Lenkachse (ideal 0, Hinweis für die Lenkung) |
| `antriebswelle_v_gier` | `max(asin(abs(lenkgelenk_versatz) * sin(lenkwinkel_max) / antriebswelle_v_l); 2 deg)` | 2,00° | abgeleitet: Schwenk der Welle vorne um das innere Gelenk beim vollen Lenkeinschlag, mindestens 2 deg (sonst fallen die Musterstellungen fast zusammen und die Vereinigung scheitert; größer = sicher) |
| `radachse_h_l` | `43.7 mm` | 43,70 mm | Radachse N1 hinten: Gesamtlänge 43,7 mm aus 1:1-Zeichnung [A1] S. 9/11; Lage: Gewindeende bündig mit Radaußenseite (Annahme), fest, am Teil messen |
| `radachse_v_l` | `radachse_h_l` | 43,70 mm | Radachse vorne: gleiches Teil N1 ([A1] S. 9) |
| `radachse_h_spiel` | `antriebswelle_h_y - ( rad_y + rad_breite / 2 - radachse_h_l + gelenk_becher )` | -0,00 mm | Prüfmaß: Kreuzstift hinten zu Becher der Radachse N1, Soll 0 (±0,5 mm) |
| `radachse_v_spiel` | `antriebswelle_v_y - ( rad_y_v + rad_breite_v / 2 - radachse_v_l + gelenk_becher )` | -0,00 mm | Prüfmaß: Kreuzstift vorne zu Becher der Radachse N1, Soll 0 (±0,5 mm) |
| `ritzel_b_netto` | `8 mm` | 8,00 mm | Motorritzel: Breite vorläufig, Vergleichsteil |
| `hz_ebene` | `20 mm` | 20,00 mm | Hauptzahnrad: Zahnmitte ab Hinterkante Bauraum Rutschkupplung, vorläufig (Grenze siehe motor_welle_reserve) |
| `ritzel_x` | `rk_x_hinten + hz_ebene` | -89,00 mm | abgeleitet: Zahnebene, Mitte Ritzel = Mitte Hauptzahnrad |
| `motor_welle_l` | `15 mm` | 15,00 mm | Motor: Wellenlänge belegt, Lindinger [E2] (3,175 x 15 mm) |
| `motor_welle_reserve` | `ritzel_x - ritzel_b_netto / 2 - ( motor_flansch_x - motor_welle_l )` | -3,00 mm | Prüfmaß: Motorwelle ragt hinter das Ritzel hinaus, muss >= 0 sein; enthält motorhalter_dicke über motor_flansch_x; negativ = Ritzel erreicht die Zahnebene nicht (offener Punkt Mittelantrieb) |
| `abdeckung_x_hinten` | `rk_x_hinten` | -109,00 mm | Zahnradabdeckung: abgeleitet, Rückwand am Hinterachsgetriebe |
| `abdeckung_x_vorne` | `kardan_hinten_x + abdeckung_abstand + abdeckung_wand` | -79,00 mm | Zahnradabdeckung: abgeleitet, Vorderwand 3 mm Abstand + 2 mm Wand vor der Becheröffnung von E2 (Ende Bauraum Rutschkupplung) |
| `rad_masse` | `100 g` | 100,0 g | Masse: vorläufig, Vergleichswert 1:10-Buggyrad (Nutzerentscheidung 2026-10-27), nach Lieferung wiegen; nicht ans Modell gebunden: wirkt über die Dichte des Materials masse-*, nach Änderung Massenabgleich (docs/skelett.md) ausführen |
| `wellen_gier_schritte` | `3` | 3 | Bewegungsraum Antriebswelle vorne: Anzahl Stellungen über den Lenkeinschlag |
| `spurbreite_v` | `217 mm` | 217,00 mm | Fahrzeug: Spur vorne, belegt [P2] (Tread 217 mm vorne); Bezug Radmitte zu Radmitte, weil 217 + 32 = 249 mm ≈ Fahrzeugbreite 250 mm [P2] |
| `rad_breite_v` | `32 mm` | 32,00 mm | Rad vorne: belegt, Reifen Tamiya 58568 [P2] (32 mm) |
| `rad_y_v` | `spurbreite_v / 2` | 108,50 mm | abgeleitet: Radmitte quer vorne (Spur = Radmitte zu Radmitte) |
| `zahn_modul` | `0.6 mm` | 0,60 mm | Zahnräder: belegt, Tamiya Modul 0,6 (docs/zukaufteile-v1.md) |
| `gelenk_becher` | `9 mm` | 9,00 mm | Gelenkbecher N1/N2: Kreuzstift bis Becheröffnung (Schlitztiefe), vorläufig, 1:1-Zeichnung [A1] S. 9/10 |
| `gelenk_becher_d` | `16.6 mm + 2 * huelle_zuschlag` | 20,60 mm | Gelenkbecher N1/N2: vorläufig, mit Zuschlag; Ø 16,6 mm aus 1:1-Zeichnung [A1] S. 9/10 |
| `getriebe_vor_achse` | `22 mm + huelle_zuschlag` | 24,00 mm | Getriebe: vorläufig, mit Zuschlag; Kegelritzel GB2 und hinteres Lager BB2 vor der Diff-Achse ([A1] S. 4); vorderes BB2 und Mitnehmer GB3 liegen davor im Bauraum der Rutschkupplung |
| `kardan_l` | `168 mm` | 168,00 mm | Kardanwelle E1: Länge vorläufig, Vergleichswert Nachbau-Kardanwelle TT-02 168 mm [K1]; am Teil messen |
| `kardan_d` | `10 mm + 2 * huelle_zuschlag` | 14,00 mm | Kardanwelle E1: vorläufig, mit Zuschlag; Kunststoffwelle ca. Ø 10 mm (Zeichnung [A1] S. 4; Alu-Nachbau 6 mm [K1]) |
| `kardan_becher_l` | `15 mm` | 15,00 mm | Gelenkbecher der Kegelritzelwelle E2: Länge vorläufig, ca. 36 % von E2 laut Zeichnung [A1] S. 4, E2 ca. 41 mm [K1] |
| `kardan_becher_d` | `16 mm + 2 * huelle_zuschlag` | 20,00 mm | Gelenkbecher E2: vorläufig, mit Zuschlag; ca. Ø 16 mm (Zeichnung [A1] S. 4, Verhältnis zum Lager 1150 Ø 11 mm) |
| `kardan_hinten_x` | `-achse_x + getriebe_eingang` | -84,00 mm | abgeleitet: Becheröffnung E2 hinten (Eingang Hinterachsgetriebe) |
| `kardan_vorne_x` | `achse_x - getriebe_eingang` | 84,00 mm | abgeleitet: Becheröffnung E2 vorne (Eingang Vorderachsgetriebe) |
| `kardan_spiel` | `( kardan_vorne_x - kardan_hinten_x ) - kardan_l` | 0,00 mm | Prüfmaß (MECH-SKE-008): Abstand der Getriebeeingänge minus Kardanwellenlänge, Soll 0 (±0,5 mm) |
| `getriebe_v_l` | `getriebe_hinter_achse + getriebe_eingang - kardan_becher_l` | 58,00 mm | Getriebe vorne: abgeleitet, bis zum Becher der Kegelritzelwelle E2 (ohne Rutschkupplung) |
| `diff_becher_l` | `2 * ( diff_abtrieb_y + gelenk_becher + huelle_zuschlag )` | 85,72 mm | Getriebe: abgeleitet, Länge quer über beide Diff-Becher N2 bis Becheröffnung, mit Zuschlag |
| `rk_x_hinten` | `-achse_x + getriebe_vor_achse` | -109,00 mm | Rutschkupplung: abgeleitet, Hinterkante Bauraum = Vorderkante Hinterachsgetriebe |
| `rk_l_bedarf` | `18 mm + 2 * huelle_zuschlag` | 22,00 mm | Rutschkupplung: Länge vorläufig, Vergleichswert 18 mm (Hauptzahnrad, Reibbeläge, Feder, Mutter), mit Zuschlag; Ausführung klärt Mittelantrieb |
| `rk_luft` | `rk_l - e2_lager_b - e2_mitnehmer_l - rk_l_bedarf` | -9,00 mm | Prüfmaß: Bauraum minus vorderes Lager BB2, Mitnehmer/Nabe und Rutschkupplung, muss >= 0 sein; negativ = Ergebnis vorläufiger Maße (offener Punkt Mittelantrieb) |
| `e2_frei` | `getriebe_eingang - kardan_becher_l - getriebe_vor_achse` | 10,00 mm | Prüfmaß: freie Länge auf E2 zwischen Getriebe und Becher; Bausatz: vorderes Lager BB2, Mitnehmer GB3 und Hauptzahnrad GB5 ([A1] S. 4 Schritt 2); Ergebnis vorläufiger Maße |
| `rk_serie_luft` | `e2_frei - e2_lager_b - e2_mitnehmer_l - rk_l_bedarf` | -24,00 mm | Prüfmaß: Rutschkupplung in Reihe vor dem Becher von E2, mit vorderem Lager BB2 und Mitnehmer; negativ = sie muss den Becher umschließen oder das Getriebe wird länger (dann passt E1 nicht); Ergebnis vorläufiger Maße |
| `motor_flansch_x` | `abdeckung_x_vorne + motorhalter_dicke` | -75,00 mm | Motor: abgeleitet, Motorflansch vor der Vorderwand der Abdeckung, dazwischen der Motorhalter (motorhalter_dicke); Motor zeigt nach vorne (wie TT-02B, [A1] S. 6) |
| `daempfer_feder_h` | `64.5 mm` | 64,50 mm | Dämpfer hinten: Feder MB5 freie Länge 64,5 mm aus 1:1-Zeichnung [A1] S. 23, vorläufig |
| `daempfer_feder_v` | `39.6 mm` | 39,60 mm | Dämpfer vorne: Feder MB11 freie Länge 39,6 mm aus 1:1-Zeichnung [A1] S. 23, vorläufig |
| `daempfer_l_v` | `daempfer_feder_v + daempfer_augen + 2 * huelle_zuschlag` | 63,60 mm | Dämpfer vorne: vorläufig, mit Zuschlag, ausgefedert ca. freie Federlänge + Augen |
| `motorhalter_dicke` | `4 mm` | 4,00 mm | Motorhalter: Dicke vorläufig, Annahme eigener Alu-Halter zwischen Vorderwand der Zahnradabdeckung und Motorflansch; Bausatz D9 mit Motorplatte MA11 ca. 6 mm (1:1-Zeichnung [A1] S. 6 Schritt 8); Ausführung klärt Mittelantrieb |
| `e2_lager_b` | `4 mm` | 4,00 mm | Kegelritzelwelle E2: Breite vorderes Lager BB2 (1150 = 5 x 11 x 4 mm, [A1] S. 4), vorläufig, am Teil messen |
| `e2_mitnehmer_l` | `8 mm` | 8,00 mm | Kegelritzelwelle E2: Länge Mitnehmer GB3 bzw. Nabe der Rutschkupplung, vorläufig ca. 2 x Lagerbreite aus Zeichnung [A1] S. 4 Schritt 2, am Teil messen |

## Hüllkörper (MECH-SKE-006, MECH-SKE-007)

**Belegt:** Maße mit Quelle (Tamiya-Specifications, Stückliste), ohne Zuschlag. **Vorläufig:** aus der Bauanleitung [A1] (1:1-Zeichnungen oder Verhältnis in einer Zeichnung), einem Vergleichswert [K1] oder einem Vergleichsteil, mit `huelle_zuschlag` = 2 mm je Seite; bei widersprüchlichen Quellen gilt das größere Maß. Ein Hüllkörper ist vorläufig, sobald eines seiner Maße vorläufig ist. In Fusion sind belegte Hüllkörper blau, vorläufige rot, Bauräume gelb, Bewegungsräume grün. Maße als Länge (X) × Breite (Y) × Höhe (Z) bzw. Durchmesser × Länge; Lage als Bereich im Fahrzeugkoordinatensystem (Messung der Hüllquader in Fusion).

| Komponente | Teil (Stückliste Pos.) | Maße im Modell | Lage X / Y / Z (mm) | Status | Quelle |
|---|---|---|---|---|---|
| `elektronik-akku` | Akku Voltz 2S 5000 (36) | 138 × 46 × 25 | −69…69 / 12…58 / 29…54 | belegt | RC Team, Stückliste |
| `elektronik-regler` | Regler WP10BL60 G2 mit Lüfter (31) | 52,5 × 42 × 38,3 (48,5 × 38 × 34,3 + Zuschlag) | −21…31,5 / −74…−32 / 29…67,3 | vorläufig | Lindinger / Hobbywing, je Achse das größere Maß |
| `elektronik-ubec` | UBEC 10A V2 (35) | 49 × 36,3 × 20,2 (45 × 32,3 × 16,2 + Zuschlag) | 33,5…82,5 / −74…−37,7 / 29…49,2 | vorläufig | RC Team [E8], htmodel [E9], je Achse das größere Maß |
| `elektronik-empfaenger` | Empfänger HR7E (33) | 46 × 26 × 15 | −74…−28 / −74…−48 / 29…44 | belegt | Lindinger [E4] |
| `elektronik-xt60` | XT60-Steckerpaar gesteckt (37) | 20 × 34 × 12 (16 × 30 × 8 + Zuschlag) | 69,5…89,5 / 12…46 / 29…41 | vorläufig | Vergleichsteil (Stückliste: „am Teil messen“) |
| `lenkung-servo` | Servo Savöx SC-1258TG+ (34), stehend | 40,3 × 20,2 × 37,2 | 57,2…97,5 / −32,2…−12 / 29…66,2 | belegt | Lindinger |
| `mittelantrieb-motor` | Motor 3652SL G2 (32) | Ø 36 × 52, Achse längs, Flansch hinten, 4 mm (`motorhalter_dicke`) vor der Zahnradabdeckung | −75…−23 / Achse Y −28,5 (25Z) bzw. −25,8 (16Z) / Achse Z 56,6 | belegt | Lindinger [E2] |
| `mittelantrieb-motorritzel` | Motorritzel 16Z bis 25Z Modul 0,6 (5, 13) | Ø 16,2 × 12 (25Z) bzw. Ø 10,8 × 12 (16Z) | −95…−83 (Mitte `ritzel_x` = Zahnebene) / Motorachse | vorläufig | Kopfkreis (z + 2) · 0,6 berechnet; Breite Vergleichsteil 8 mm + Zuschlag |
| `mittelantrieb-rutschkupplung` | Rutschkupplung, Eigenbau (48), mit Hauptzahnrad 70Z (4) | Ø 47,2 × 25 | −109…−84 / Y ±23,6 / Z 33…80,2 | vorläufig (Bauraum) | Kopfkreis 70Z: (70 + 2) · 0,6 = 43,2 mm + Zuschlag; Länge = Bauraum auf E2 vom Getriebe bis zur Becheröffnung (siehe [Rutschkupplung](#rutschkupplung-auf-der-kegelritzelwelle)) |
| `mittelantrieb-kardanwelle` | Kardanwelle E1 (3) mit den Bechern der Kegelritzelwellen E2 | Welle Ø 14 zwischen den Becheröffnungen (168), Becher Ø 20 × 15 an beiden Enden | −99…99 / ±10 / Z 46,6…66,6 | vorläufig | Länge Vergleichswert 168 mm [K1]; Ø 10 mm und Becher Ø 16 × 15 mm aus Zeichnung [A1] S. 4, + Zuschlag |
| `mittelantrieb-zahnradabdeckung` | Zahnradabdeckung, Eigenbau (50) | Zylinder r 26,6 um das Hauptzahnrad und r 13,1 um das Ritzel (25Z), Länge 30 | −109…−79 / −41,6…26,6 / 30…83,2 | Bauraum | MECH-SKE-014: 3 mm Abstand + 2 mm Wand zum Kopfkreis |
| `antrieb-getriebe-hinten` | Hinterachsdiff mit Tellerrad GB4, Kegelritzel GB2, Lagern (2) im eigenen Gehäuse (43); Diff-Becher N2 | Kasten 48 × 49,7 × 51,6, dazu Zylinder Ø 20,6 × 85,7 quer (Diff-Becher) | −157…−109 / ±24,9 (Becher ±42,9) / 29…80,6 | vorläufig | Tellerrad ca. Ø 39 mm ([A1] S. 23, Maßstab über GB5 geeicht) + Wand + Zuschlag; Becher N2 Ø 16,6 mm (1:1, [A1] S. 10) |
| `antrieb-getriebe-vorne` | Vorderachsdiff, 4WD (12), mit Kegelritzelwelle E2 bis zum Becher | Kasten 58 × 49,7 × 51,6, Diff-Becher wie hinten | 99…157 / ±24,9 (Becher ±42,9) / 29…80,6 | vorläufig | wie hinten |
| `antrieb-antriebswelle-hl`, `-hr` | Antriebswellen N3 (6) | Ø 14 × 60, schräg 15,07° (Kreuzstift innen Y ±31,86 / Z 56,6, außen Y ±89,80 / Z 41) | X −140…−126 / ±30,0…±91,6 / 34,2…63,4 | vorläufig | Länge 59–61 mm aus Zeichnung [A1] S. 10/11 (Verhältnis zu N2); Kugel ca. Ø 10 mm + Zuschlag |
| `antrieb-antriebswelle-vl`, `-vr` | Antriebswellen N3 vorne, 4WD (12) | wie hinten | X 126…140 | vorläufig | wie hinten, gleiches Teil ([A1] S. 19) |
| `antrieb-radachse-hl`, `-hr` | Radachsen N1 hinten (7) mit 12-mm-Mitnehmer | Ø 20,6 × 43,7 | Y ±80,8…±124,5 / Z Achse 41 | vorläufig | Länge 43,7 mm und Becher Ø 16,6 mm aus 1:1-Zeichnung [A1] S. 9/11, + Zuschlag Ø; Annahme: Gewindeende bündig mit der Radaußenseite |
| `antrieb-radachse-vl`, `-vr` | Radachsen N1 vorne (8) | wie hinten | Y ±80,8…±124,5 | vorläufig | gleiches Teil N1 |
| `antrieb-wellenraum-hl`, `-hr` | Bewegungsraum Antriebswelle und Radachse hinten | Welle −7,41…27,03° um das innere Gelenk, Radachse über den Federweg | X −143,3…−122,7 / ±28,7…±124,5 / 19,0…74,6 | abgeleitet | Parameter Welle, Radachse, Federweg |
| `antrieb-wellenraum-vl`, `-vr` | Bewegungsraum vorne | wie hinten, dazu Welle ±2° um das innere Gelenk und Radachse ±30° um die Lenkachse | X 106,1…159,9 / ±28,7…±125,9 / 19,0…74,6 | abgeleitet | Parameter Welle, Radachse, Federweg, Lenkung |
| `fahrwerk-daempfer-hl`, `-hr` | CVA-Dämpfer hinten (9) | Ø 20,5 × 88,5, senkrecht | X −119,25…−98,75 / ±44,75…±65,25 / 35…123,5 | vorläufig | Feder MB5 frei 64,5 mm und Ø 16,5 mm (1:1, [A1] S. 23) + Augen 20 mm (Vergleichsteil) + Zuschlag |
| `fahrwerk-daempfer-vl`, `-vr` | CVA-Dämpfer vorne (9) | Ø 20,5 × 63,6, senkrecht | X 98,75…119,25 / ±44,75…±65,25 / 35…98,6 | vorläufig | Feder MB11 frei 39,6 mm (1:1, [A1] S. 23) + Augen + Zuschlag |
| `fahrwerk-rad-hl`, `-hr` | Räder hinten (10) | Ø 82 × 41 | Radmitte X −133 / Y ±104 / Z 41 | belegt | Tamiya [P2] |
| `fahrwerk-rad-vl`, `-vr` | Räder vorne (10) | Ø 82 × 32 | Radmitte X 133 / Y ±108,5 / Z 41 | belegt | Tamiya [P2] |
| `fahrwerk-radraum-*` | Bewegungsraum der Räder | Höhe 117 (82 + 35); vorne mit Lenkeinschlag ±30° | Z −11,67…105,33; vorne X 79,5…186,5 / Y ±71,5…±140,2 | abgeleitet | Parameter Rad, Federweg, Lenkung |
| `elektronik-akku-entnahmeweg` | freizuhaltender Weg nach oben | 138 × 46 × 100 | über dem Akku, Z 54…154 | Bauraum | MECH-SKE-015 |
| `chassis-grundplatte` | Grundplatte (41), zwei Körper | siehe [Grundplatte](#grundplatte-mech-ske-012-mech-ske-013) | Z 25…29 | Bauraum | abgeleitet |

**Positionen der Stückliste ohne eigenen Hüllkörper (begründet):**

| Pos. | Teil | Begründung |
|---|---|---|
| 1 | Bausatz Neo Scorcher 58568 | Sammelposition; die verbauten Bausatzteile haben eigene Positionen (2–12) |
| 11 | Kugelköpfe, Kugelpfannen, Lenkspurstange, Sturzstangen | Normteile bzw. Länge erst nach der Konstruktion von Lenkung und Querlenkern |
| 14, 15 | Kugellager | Normteile, sitzen in Getrieben, Radträgern und Lenkung (in deren Hüllkörpern enthalten) |
| 16–30 | Schrauben, Muttern, Scheiben, Gewindeeinsätze | Normteile laut Anforderung ohne Hüllkörper |
| 38, 39 | Servo-Verlängerung, Kabelbinder | Kabel, ohne festen Bauraum |
| 40 | LiPo-Schutztasche | nicht im Fahrzeug |
| 42 | Oberdeck | Eigenbau, noch nicht konstruiert; muss den Entnahmeweg des Akkus freilassen |
| 43 | Getriebegehäuse hinten | im Hüllkörper `antrieb-getriebe-hinten` enthalten |
| 44, 45, 46 | Radträger, Querlenker, Dämpferbrücken | Eigenbau, noch nicht konstruiert; laut Anforderung keine Hüllkörper |
| 47 | Mittelschott | **entfällt im TT-02B-Layout**: Die Kardanwelle ist nur an den Getrieben gelagert (MECH-SKE-008). Die Stückliste wird mit der Anforderung „Mittelantrieb“ angepasst. |
| 49 | Motorhalter | Eigenbau, noch nicht konstruiert; kein eigener Hüllkörper, aber Bauraum über `motorhalter_dicke` = 4 mm (vorläufig) zwischen Vorderwand der Zahnradabdeckung (X −79) und Motorflansch (X −75) freigehalten. Damit reicht die Motorwelle nicht bis zur Zahnebene (`motor_welle_reserve` = −3,0 mm, siehe [Zahnebene](#zahnebene-ritzel-und-motor)). |
| 51, 52, 53 | Achsschenkel, Lenkhebelsystem, Elektronikhalter | Eigenbau, noch nicht konstruiert |

## Layout (MECH-SKE-008)

Wie beim TT-02B laut Bauanleitung [A1] S. 4–6 (Nutzerentscheidung 2026-10-28):
- **Kardanwelle E1** in der Fahrzeugmitte zwischen den Bechern der beiden Kegelritzelwellen E2, nur an den Getrieben gelagert, **kein Lagerbock in der Mitte**.
- **Hauptzahnrad 70Z** mit eigener Rutschkupplung auf der **hinteren Kegelritzelwelle E2** direkt vor dem Hinterachsgetriebe (beim TT-02B sitzt GB5 auf E2 zwischen den Lagern, [A1] S. 4 Schritt 2).
- **Motor hinten rechts**, Achse längs, Flansch vor der Zahnradabdeckung mit dem Motorhalter dazwischen, Motor zeigt nach vorne (wie [A1] S. 6 Schritt 9).
- **Akku längs links** (Y 12…58 mm), mittig zwischen den Achsen, XT60 davor.
- **Elektronik rechts:** Empfänger neben dem Motor, Regler vor dem Motor, UBEC vor dem Regler neben dem Servo.
- **Servo vorne**, stehend, rechts neben der Kardanwelle, hinter dem Vorderachsgetriebe.

### Kardanwelle (Prüfmaß `kardan_spiel`)

| Maß | Wert | Messung in Fusion |
|---|---|---|
| Becheröffnung E2 hinten (`kardan_hinten_x`) | X = −84,0 mm | Kardanwelle: Becher hinten endet bei −84,0 |
| Becheröffnung E2 vorne (`kardan_vorne_x`) | X = +84,0 mm | Becher vorne beginnt bei +84,0 |
| Abstand der Getriebeeingänge | 168,0 mm | |
| Kardanwelle E1 (`kardan_l`, Vergleichswert [K1]) | 168,0 mm | |
| **`kardan_spiel`** | **0,00 mm** (Soll 0 ± 0,5) | |

**`kardan_spiel` = 0 ist kein unabhängiger Nachweis.** `getriebe_eingang` = 49 mm ist so gelegt, dass E1 beim TT-02B-Radstand passt: (266 − 168) / 2 = 49 mm. Das Prüfmaß ist damit beim Startwert immer 0; es zeigt nur Fehler, wenn sich Radstand oder `kardan_l` ändern (Parametertest: +14 mm bei 280 mm). Belegt ist keiner der Werte:
- `kardan_l` = 168 mm ist die Wellenlänge eines Alu-Nachbaus [K1], nicht das Maß von E1.
- **Annahme:** Die Länge von E1 ist der Abstand der Becheröffnungen. Laut Anleitung wird E1 aber in die Becher von E2 gesteckt („Fully push in“, [A1] S. 4 Schritt 3). Um die Einstecktiefe kann die Annahme falsch sein.
- Zur Plausibilität: E2 ist hinten etwa 41 mm lang [K1]; dann liegt das hintere Ende von E2 im Kegelritzel 8 mm vor der Diff-Achse.

Länge von E1, Einstecktiefe in die Becher, Länge von E2 und Abstand Diff-Achse–Becheröffnung werden bei Lieferung gemessen (🔧, [Messpunkt 1](#offene-punkte-und-hinweise-für-die-nächsten-baugruppen)). Davon hängen `e2_frei` und `rk_serie_luft` ab.

### Rutschkupplung auf der Kegelritzelwelle

Beim TT-02B sitzt auf E2 von vorne nach hinten: Becher, Lager BB2, Mitnehmer GB3, Hauptzahnrad GB5 (Stift MA10), Lager BB2, Kegelritzel GB2 ([A1] S. 4, Schritt 2 und 3). Im Modell:

| Abschnitt auf E2 | X (mm) | Länge |
|---|---|---|
| Getriebe (Kegelritzel, hinteres Lager) bis `getriebe_vor_achse` | −133…−109 | 24 mm (mit Zuschlag) |
| frei zwischen Getriebe und Becher (`e2_frei`) | −109…−99 | **10 mm** |
| Becher von E2 (`kardan_becher_l`) | −99…−84 | 15 mm |

**Bilanz in Reihe** (alles zwischen Getriebe und Becher, Werte vorläufig):

| Teil | Parameter | Länge |
|---|---|---|
| vorderes Lager BB2 (1150, 5 × 11 × 4 mm) | `e2_lager_b` | 4 mm |
| Mitnehmer GB3 bzw. Nabe der Rutschkupplung (ca. 2 × Lagerbreite, Zeichnung [A1] S. 4) | `e2_mitnehmer_l` | 8 mm |
| Rutschkupplung mit Hauptzahnrad, Reibbelägen, Feder, Mutter (Vergleichswert 18 mm + Zuschlag) | `rk_l_bedarf` | 22 mm |
| **Bedarf** | | **34 mm** |
| verfügbar | `e2_frei` | 10 mm |
| **`rk_serie_luft`** | | **−24 mm** |

**In Reihe vor dem Becher fehlen also 24 mm.** Wird das Getriebe dafür länger, rückt der Becher nach vorne und E1 passt nicht mehr. Dieser Befund ist ein **Ergebnis vorläufiger Maße**: Schon die Bausatzteile BB2 und GB3 brauchen nach diesen Werten 12 mm und passen nicht in `e2_frei` = 10 mm, obwohl beim TT-02B dort zusätzlich noch GB5 sitzt. Mindestens eines der Maße `getriebe_eingang`, `kardan_becher_l`, `getriebe_vor_achse` oder `e2_mitnehmer_l` ist also zu ungünstig angesetzt. Der genaue Fehlbetrag steht erst nach dem Messen fest; dass eine Rutschkupplung mit eigenem Zuschlag in Reihe passt, ist trotzdem unwahrscheinlich.

Das Skelett hält deshalb den Bauraum **von der Vorderkante des Hinterachsgetriebes bis zur Becheröffnung** frei (`rk_l` = 25 mm, Ø 47,2 mm). Er umschließt den Becher von E2. Laut Anleitung ([A1] S. 4 Schritt 2: Becher, BB2, GB3, GB5, BB2, GB2) sitzen das vordere Lager BB2 und der Mitnehmer GB3 **vor** dem Getriebe, also in diesem Bauraum; im Getriebe-Hüllkörper (`getriebe_vor_achse`) liegen nur Kegelritzel GB2 und hinteres BB2. Die Bilanz zählt deshalb wie `rk_serie_luft` Lager und Mitnehmer mit: `rk_luft` = 25 − 4 − 8 − 22 = **−9 mm** (Review 2; vorher +3 mm ohne Lager und Mitnehmer). Auch der Bauraum um den Becher reicht also nach vorläufigen Maßen nicht; `rk_luft` und `rk_serie_luft` unterscheiden sich genau um die Becherlänge (15 mm). Ein Teil des Fehlbetrags kann wegfallen, wenn die Nabe der Rutschkupplung den Mitnehmer GB3 ersetzt oder über den Becher greift; das klärt „Mittelantrieb“ nach dem Messen (Messpunkt 1). Die Überschneidung Rutschkupplung ↔ Becher ist gewollt (Bauraum). **Wie die Rutschkupplung gebaut wird, entscheidet die Anforderungsanalyse „Mittelantrieb“** (Nutzerentscheidung 2026-10-28). Möglichkeiten:
1. Rutschkupplung umschließt den Becher von E2 (Hauptzahnrad mit großer Bohrung, Kraftschluss auf E2 vor dem Becher). E1 und E2 bleiben unverändert.
2. Getriebe länger und E1 um denselben Betrag kürzen (z. B. eigene oder gekürzte Alu-Welle).
3. Radstand vergrößern (weicht vom TT-02B-Radstand ab).

**Abhängigkeit von der Motorlage:** Die Zahnebene liegt im Skelett bei X = −89 mm, also auf dem Becher von E2 (−99…−84). Das Hauptzahnrad muss dort den Becher umschließen. Die Motorlage im Skelett setzt damit **Möglichkeit 1 schon voraus**. Wählt „Mittelantrieb“ Möglichkeit 2 oder 3, ändern sich Zahnebene, Motorlage und `motor_welle_reserve` mit.

### Zahnebene, Ritzel und Motor

Der Motor (r 18 mm) liegt mit 25,8–28,5 mm Achsabstand neben der Kegelritzelwelle. Er kann den Bauraum der Rutschkupplung (r 23,6 mm) und den Becher von E2 (r 10 mm) nur vor dem Becher passieren. Die Vorderwand der Zahnradabdeckung liegt deshalb 5 mm vor der Becheröffnung (`abdeckung_x_vorne` = −79 mm: 3 mm Abstand + 2 mm Wand). Davor sitzt der **Motorhalter** (`motorhalter_dicke` = 4 mm, vorläufig; Bausatz D9 mit Motorplatte MA11 laut 1:1-Zeichnung [A1] S. 6 Schritt 8 ca. 6 mm), dann der Motorflansch (`motor_flansch_x` = −75 mm). Das Ritzel muss auf der Motorwelle (15 mm, belegt) nach hinten durch Halter und Abdeckungswand bis in die Zahnebene reichen. Die Zahnebene liegt `hz_ebene` = 20 mm vor der Hinterkante des Rutschkupplungs-Bauraums (X = −89 mm), also auf dem Becher von E2.

| Kette ab Motorflansch nach hinten | Länge |
|---|---|
| Motorhalter (`motorhalter_dicke`) | 4 mm |
| Wand der Zahnradabdeckung (`abdeckung_wand`) | 2 mm |
| Abstand zum Zahnrad (`abdeckung_abstand`, MECH-SKE-014) | 3 mm |
| bis Mitte Zahnebene (Becheröffnung −84 bis −89) | 5 mm |
| halbe Ritzelbreite (`ritzel_b_netto` / 2) | 4 mm |
| **Bedarf** | **18 mm** |
| Motorwelle (`motor_welle_l`, belegt) | 15 mm |
| **`motor_welle_reserve`** | **−3,0 mm** |

**Die Motorwelle reicht nicht bis in die Zahnebene.** Ohne Motorhalter wäre die Reserve +1,0 mm. Die Zahnebene lässt sich kaum verschieben: Nach vorne endet der Bauraum der Rutschkupplung an der Becheröffnung (−84); das Ritzel braucht davor 3 mm Abstand zur Abdeckung. Bestenfalls (`hz_ebene` = 21 mm, Ritzel-Vorderkante an der Becheröffnung) wären es −2,0 mm. Das Prüfmaß bleibt deshalb **negativ sichtbar** im Modell. Möglichkeiten für „Mittelantrieb“:
1. Der Motorhalter ist zugleich die Vorderwand der Zahnradabdeckung (spart 2 mm Wand): Reserve −1,0 mm, mit `hz_ebene` = 21 mm 0,0 mm.
2. Dünnerer Motorhalter (≤ 2 mm Stahl) oder Motorhalter mit Ausdrehung, in der der Motorflansch versenkt sitzt.
3. Ritzel mit Bund nach hinten bzw. schmaleres Ritzel (Zahnbreite < 8 mm).
4. Motor mit längerer Welle (z. B. 17–20 mm) oder anderes Layout (Motorflansch hinten am Getriebe, Motor zeigt nach hinten).

Beim TT-02B sitzt das Ritzel 10 mm vor dem Motorhalter (Außenkante Ritzel, [A1] S. 6, Schritt 8); dort liegt das Hauptzahnrad im Getriebe ohne eigene Abdeckungswand dazwischen.

**Bauraum für Ritzel 16Z bis 25Z** (Parameter `ritzel_zaehne`):

| Ritzel | Achsabstand | Kopfkreis Ritzel | Motor ↔ Kardanwelle | Interferenz |
|---|---|---|---|---|
| **25Z** (Startwert) | 28,50 mm | 16,2 mm | 3,50 mm | 51 Überschneidungen, alle gewollt, Zeitleiste ohne Fehler; `motor_welle_reserve` −3,0 mm |
| **16Z** | 25,80 mm | 10,8 mm | **0,80 mm** | 51 Überschneidungen, dieselben Paare, Zeitleiste ohne Fehler; `motor_welle_reserve` −3,0 mm |

Mit 16Z ist der Motor nur 0,8 mm von der Kardanwelle (Hülle mit Zuschlag) entfernt. Der Motorhalter muss das Zahnspiel über einen Bogen um die Kegelritzelwelle einstellen (wie die Lochreihe A–D des TT-02B-Halters D9, [A1] S. 19); der Achsabstand bleibt dabei gleich.

## Höhe der Antriebsachse

Die Höhe der Kegelritzelwellen, der Kardanwelle und der Diff-Achsen ist `antrieb_z` = 56,6 mm. Sie folgt aus der Zahnradabdeckung: Unter dem Hauptzahnrad (Kopfkreis 43,2 mm) müssen 3 mm Abstand und 2 mm Wand auf die Grundplatte passen. Beim TT-02B liegt die Diff-Achse etwa auf Radmittenhöhe und das Hauptzahnrad taucht in die Wanne ([A1] S. 5–6). Das ginge hier nur mit einer Aussparung in der Grundplatte: Das Hauptzahnrad würde bis Z ≈ 14 mm hinunterreichen, unter die Bodenfreiheit von 25 mm (MECH-SKE-011).

**Nutzerentscheidung 2026-10-28 (nach Review 1): Die Antriebsachse bleibt hoch** (`antrieb_z` = 56,6 mm, 15,6 mm über Radmitte), die Grundplatte bekommt keine Aussparung unter dem Hauptzahnrad. Bodenfreiheit und flache Grundplatte haben Vorrang. Die Entscheidung ersetzt die Annahme „sonst aus der Anleitung übernehmen“ (`docs/anforderungen/skelett.md`, Abschnitt „Entscheidungen“).

Die Radmitte liegt bei 41 mm, die Antriebswellen laufen um `antrieb_dz` = 15,6 mm schräg:

| Welle N3 (60 mm) | ausgefedert | statisch | eingefedert |
|---|---|---|---|
| vorne und hinten | **27,0°** | 15,1° | −7,4° |

Den zulässigen Beugewinkel der Knochen N3 nennt Tamiya nicht. **27° ausgefedert ist ein Risiko** (Knochen können bei großem Winkel aus dem Becher springen oder klemmen). Der Nutzer nimmt es bewusst in Kauf; die Winkel (statisch 15,07°, ausgefedert 27,03°) werden **bei Lieferung geprüft (🔧, [Messpunkt 2](#offene-punkte-und-hinweise-für-die-nächsten-baugruppen))**. Passen sie nicht, bleiben als Abhilfe weniger Ausfederweg oder eine neue Entscheidung zur Höhe der Antriebsachse.

## Interferenzprüfung (MECH-SKE-010)

Fusion `analyzeInterference` über alle 39 Hüllkörper-Komponenten (+ Root), ohne bloß berührende Flächen. Ergebnis mit 25Z und mit 16Z: **51 Überschneidungen, alle gewollt, 0 ungewollt.** Geprüft sind die statischen Hüllkörper und die Bewegungsräume der Räder, der Antriebswellen und der Radachsen über Federweg und Lenkeinschlag. Im 4WD-Bauraum (Vorderachsgetriebe, Antriebswellen vorne, vorderer Becher der Kardanwelle) gibt es außer den gewollten Fällen keine Überschneidung. Damit ist auch MECH-FZG-002 nachgewiesen.

| Überschneidung | Anzahl | Volumen je Fall | Begründung (gewollt) |
|---|---|---|---|
| Rad ↔ eigener Bewegungsraum | 4 | 168 993–216 522 mm³ | Das Rad liegt im eigenen Bewegungsraum. |
| Rad ↔ Wellenraum, Radraum ↔ Wellenraum | 8 | 43 226–73 003 mm³ | Der Bewegungsraum von Welle und Radachse liegt teilweise im Rad. |
| Radachse ↔ Rad, ↔ Radraum, ↔ Wellenraum | 12 | 10 665–14 565 mm³ | Radachse N1 sitzt in der Radnabe; der Wellenraum enthält die Radachse. |
| Antriebswelle ↔ Rad, ↔ Radraum | 6 | 10–1 004 mm³ | Das äußere Gelenk sitzt in der Felge bzw. reicht vorne beim Lenkeinschlag in den Radraum. |
| Antriebswelle ↔ Radachse | 4 | 1 434 mm³ | Gelenk: Knochen im Becher von N1. |
| Antriebswelle ↔ eigener Wellenraum | 4 | 9 232–9 236 mm³ | Die Welle liegt in ihrem Bewegungsraum. |
| Antriebswelle ↔ Achsgetriebe, Wellenraum ↔ Achsgetriebe | 8 | 1 754–2 501 mm³ | Knochen im Diff-Becher N2. |
| Rutschkupplung ↔ Zahnradabdeckung | 1 | 43 744 mm³ | Die Abdeckung umschließt Hauptzahnrad und Rutschkupplung. |
| Motorritzel ↔ Zahnradabdeckung | 1 | 2 473 mm³ | Die Abdeckung umschließt das Ritzel. |
| Motorritzel ↔ Rutschkupplung | 1 | 281 mm³ | Zahneingriff; die Überschneidung kommt aus dem Zuschlag der Hüllkörper. |
| Kardanwelle ↔ Zahnradabdeckung | 1 | 5 482 mm³ | Becher von E2 und E1 laufen durch die Abdeckung; ihre Vorderwand hat eine Durchführung. |
| Rutschkupplung ↔ Kardanwelle | 1 | 4 712 mm³ | Der Bauraum der Rutschkupplung umschließt den Becher von E2 (siehe [Rutschkupplung](#rutschkupplung-auf-der-kegelritzelwelle)). |

Engste Abstände ohne Überschneidung (Fusion `measureMinimumDistance`, 25Z):

| Hüllkörper | Abstand |
|---|---|
| Kardanwelle, Rutschkupplung, Abdeckung ↔ Getriebe bzw. Abdeckung | 0,00 mm (Berührung an gemeinsamen Flächen, gewollt) |
| Akku ↔ XT60 | 0,50 mm |
| Antriebswelle vorne ↔ Rad vorne | 0,88 mm |
| Servo ↔ Vorderachsgetriebe | 1,50 mm |
| Motor ↔ Regler, Regler ↔ UBEC, Servo ↔ Kardanwelle | 2,00 mm |
| Motor ↔ Zahnradabdeckung | 4,00 mm (Bauraum Motorhalter, `motorhalter_dicke`) |
| Zahnradabdeckung ↔ Dämpfer hinten rechts | 3,15 mm (16Z: 8,55 mm) |
| Motor ↔ Kardanwelle | 3,50 mm (16Z: **0,80 mm**) |
| Grundplatte ↔ Lenk-Bewegungsraum vorne rechts | 3,92 mm |
| Motor ↔ Motorritzel | 8,00 mm (Ritzel erreicht die Motorwelle nicht, siehe [Zahnebene](#zahnebene-ritzel-und-motor)) |
| Motor ↔ Rutschkupplung | 9,00 mm |
| Motor ↔ Empfänger | 5,22 mm (16Z: 7,53 mm) |
| Akku ↔ Kardanwelle | 5,28 mm |
| UBEC ↔ Servo | 5,50 mm |
| Dämpfer vorne ↔ Wellenraum vorne | 5,93 mm |
| Dämpfer ↔ Antriebswelle, Dämpfer hinten ↔ Wellenraum hinten | 6,75 mm |

## Bodenfreiheit (MECH-SKE-011)

Tiefster Punkt aller Hüllkörper außer Rädern und ihren Bewegungsräumen: Unterkante Grundplatte bei **Z = 25,0 mm**. Danach folgen die Achsgetriebe und alle Teile auf der Platte bei 29,0 mm, die Rutschkupplung bei 33,0 mm, die Radachsen bei 30,7 mm, die Antriebswellen bei 34,2 mm. Die Bewegungsräume der Räder reichen beim Ausfedern bis Z = −11,67 mm, die der Wellen und Radachsen bis Z = 19,0 mm. Sie zählen zu den Rädern: Ausgefedert hängt das Rad, die Bodenfreiheit gilt in Konstruktionslage.

## Grundplatte (MECH-SKE-012, MECH-SKE-013)

Der Umriss folgt den Hüllkörpern, die auf der Platte sitzen:
- hinten schmal: X −157…−109, Breite `getriebe_b` = 49,7 mm (Hinterachsgetriebe)
- Mitte breit: X −109…89,5, Y −74…58 (Zahnradabdeckung, Motor, Akku links, Elektronik rechts, XT60)
- vorne schmal: X 89,5…157, Y −32,2…24,9 (Vorderachsgetriebe, Servo)

**Gesamt: 314,0 × 132,0 × 4 mm** (Messung Hüllquader in Fusion).

**Teilung für den Druck:** Stoß bei `teilung_x` = 0 mm mit `teilung_ueberlappung` = 30 mm. Im Stoß hat jedes Teil die halbe Plattenstärke (hinten unten, vorne oben).

| Teil | X | Hüllquader (L × B) | ≤ 250 × 250 mm |
|---|---|---|---|
| `grundplatte-hinten` | −157,0…15,0 | 172,0 × 132,0 mm | ja |
| `grundplatte-vorne` | −15,0…157,0 | 172,0 × 132,0 mm | ja |

**Begründung der Lage:** Damit beide Teile einschließlich Überlappung höchstens 250 mm lang sind, muss `teilung_x` zwischen −78 und +78 mm liegen. Der Stoß (`teilung_x` ± 15 mm) darf nicht unter Motor (X −75…−23), Motorhalter, Zahnradabdeckung und Rutschkupplung (−109…−75) oder einem Achsgetriebe (bis −109 bzw. ab 99) liegen. Daraus folgt −8 < `teilung_x` < 84 mm, zusammen **−8 < `teilung_x` ≤ 78 mm**. Gewählt ist 0 mm: Beide Teile sind gleich lang (172 mm), der Stoß liegt 8 mm vor dem Motor. Er liegt unter Akku und Regler; das ist erlaubt (Entscheidung 2026-10-27). **Hinweis für die Anforderung „Grundplatte“:** Die Verbindung am Stoß muss unter Akku und Regler flach bleiben bzw. deren Halter mit einbeziehen.

## Akku-Wechsel (MECH-SKE-015)

Über dem Akku ist ein Entnahmeweg von 138 × 46 × 100 mm als Bauraum modelliert (`elektronik-akku-entnahmeweg`). Er überschneidet sich mit keinem Hüllkörper (engster Abstand zur Kardanwelle 5,0 mm). Ein späteres Oberdeck muss diesen Weg freilassen oder abnehmbar sein.

## Schwerpunkt (MECH-SKE-016)

Hüllkörper mit Masse, Werte aus Fusion (`physicalProperties`). Alle anderen Körper haben das Material `masse-null`. Der Schwerpunkt wird über das **ganze Design** bestimmt (`rootComponent.getPhysicalProperties`):

| Hüllkörper | Masse | Status | Schwerpunkt X / Y / Z (mm) |
|---|---|---|---|
| Akku | 300,0 g | belegt | 0,0 / 35,0 / 41,5 |
| Motor | 223,0 g | belegt | −49,0 / −28,5 / 56,6 |
| Regler | 90,0 g | belegt | 5,3 / −53,0 / 48,1 |
| Servo | 64,0 g | belegt | 77,3 / −22,1 / 47,6 |
| UBEC | 34,0 g | belegt | 58,0 / −55,9 / 39,1 |
| Empfänger | 12,7 g | belegt | −51,0 / −61,0 / 36,5 |
| 4 Räder | 4 × 100,0 g | vorläufig (`rad_masse`) | ±133 / ±104 bzw. ±108,5 / 41 |
| **Ganzes Design** | **1123,7 g** | | **−3,72 / −4,19 / 45,07** |

Der Schwerpunkt liegt quer **4,19 mm** rechts der Fahrzeugmitte (Grenze 10 mm). Die Räder liegen symmetrisch und ändern den Querwert nur über die Gesamtmasse. Reserve zum Ausgleich: Akku weiter nach links (`akku_y_innen`).

### Massenabgleich (Skript)

Die Masse-Parameter wirken nicht von selbst. Nach jeder Änderung eines Masse-Parameters oder der Maße von Akku, Motor, Regler, Servo, Empfänger, UBEC oder Rad dieses Skript in Fusion ausführen (Skripte und Add-Ins oder MCP `fusion_mcp_execute`). Es setzt die Dichte jedes `masse-*`-Materials auf Masse/Volumen, alle anderen Körper auf `masse-null`, und gibt den Schwerpunkt aus.

```python
import adsk.core, adsk.fusion

MASSEN = {
    'elektronik-akku': 'akku_masse', 'mittelantrieb-motor': 'motor_masse', 'elektronik-regler': 'regler_masse',
    'lenkung-servo': 'servo_masse', 'elektronik-empfaenger': 'empf_masse', 'elektronik-ubec': 'ubec_masse',
    'fahrwerk-rad-vl': 'rad_masse', 'fahrwerk-rad-vr': 'rad_masse', 'fahrwerk-rad-hl': 'rad_masse', 'fahrwerk-rad-hr': 'rad_masse',
}

def material(d, name):
    m = d.materials.itemByName(name)
    return m if m else d.materials.addByCopy(d.materials.item(0), name)

def matname(cname):
    # Räder vorne und hinten sind verschieden breit: je Achse ein Material
    if cname.startswith('fahrwerk-rad-'):
        return 'masse-fahrwerk-rad-' + cname[-2]
    return 'masse-' + cname

def run(_context: str):
    d = adsk.fusion.Design.cast(adsk.core.Application.get().activeProduct)
    null = material(d, 'masse-null')
    null.materialProperties.itemById('structural_Density').value = 0.001  # kg/m³
    for occ in d.rootComponent.occurrences:
        c = occ.component
        par = MASSEN.get(c.name)
        for b in c.bRepBodies:
            m = null
            if par:
                m = material(d, matname(c.name))
                kg = d.userParameters.itemByName(par).value
                m.materialProperties.itemById('structural_Density').value = kg / (b.volume * 1e-6)
            if b.material.name != m.name:
                farbe = b.appearance
                b.material = m
                b.appearance = farbe
    pp = d.rootComponent.getPhysicalProperties(adsk.fusion.CalculationAccuracy.VeryHighCalculationAccuracy)
    cg = pp.centerOfMass
    print('Gesamt %.1f g, Schwerpunkt X %.2f Y %.2f Z %.2f mm' % (pp.mass * 1000, cg.x * 10, cg.y * 10, cg.z * 10))
```

## Federweg (MECH-SKE-017)

Die Anleitung [A1] zeigt die CVA-Dämpfer und ihre Teile, nennt aber weder Hub noch Einbaulänge. Aus den 1:1-Zeichnungen auf S. 23 lassen sich nur Teilmaße abgreifen: Kolbenstange hinten MB12 ca. 46,5 mm, vorne MB13 ca. 30,9 mm, Federn hinten MB5 64,5 mm und vorne MB11 39,6 mm frei, Federdurchmesser 16,5 mm. Der Hub hängt zusätzlich von Kolben, Dichtungen und Anschlag im Zylinder ab, und der Federweg am Rad vom Hebelverhältnis der eigenen Querlenker, die es noch nicht gibt. **Die Anleitung gibt den Federweg also nicht her.** `federweg` bleibt bei **35 mm, vorläufig, am Prototyp messen** (eher zu großer Bewegungsraum, sicher für die Freigänge). Aufteilung wie bisher 2/3 ein (23,33 mm), 1/3 aus (11,67 mm), Annahme aus dem Anforderungsdokument.

## Parametertest (MECH-SKE-001)

`radstand` = 280 mm und `spurbreite` = 220 mm gesetzt: Zeitleiste (327 Elemente) ohne Fehler und Warnungen. Räder hinten bei X −140 und Y ±110 (Radmitte), vorne bei X 140; Getriebe, Dämpfer, Servo, Kardanwelle, Wellen und Bewegungsräume folgen (Bild). Die Prüfmaße zeigen, was mit den festen Bausatzteilen nicht mehr passt: `kardan_spiel` = +14,0 mm (E1 zu kurz), `radachse_h_spiel` = −6,0 mm (Knochen N3 erreicht den Becher der Radachse nicht mehr), vorne unverändert 0,0 mm. Interferenz: 51 Überschneidungen, dieselben Paare, keine neue. Danach auf 266 / 208 mm zurückgesetzt: wieder ohne Fehler, 51 Überschneidungen, alle Prüfmaße wie oben.

Dabei aufgefallen und behoben: Die Kardanwelle war zunächst mit fester Länge 168 mm modelliert; bei 280 mm Radstand berührte sie die Becher nicht mehr und das Vereinigen scheiterte. Jetzt reicht der Hüllkörper immer von Becher zu Becher, und die Länge von E1 wird über `kardan_spiel` geprüft.

Weiterer Test: `ritzel_zaehne` = 16 (siehe [Zahnebene](#zahnebene-ritzel-und-motor)), ohne Zeitleistenfehler.

![Parametertest mit 280/220 mm](images/skelett-parametertest-280-220.png)

*Bild aus Version 8, vor Review 1. Seitdem liegen Motor und Elektronik rechts 4 mm weiter vorne (Motorhalter); am Ergebnis des Tests ändert das nichts.*

## Offene Punkte und Hinweise für die nächsten Baugruppen

**Messpunkte bei Lieferung des Bausatzes, in dieser Reihenfolge** (danach Parameter ersetzen und Interferenzprüfung wiederholen):
1. **Kegelritzelwelle E2 und Kardanwelle E1:** Länge E1, Einstecktiefe von E1 in die Becher von E2, Länge E2, Lage der Becheröffnung zur Diff-Achse (`getriebe_eingang`), Becherlänge und -durchmesser, freie Länge zwischen den Lagern (`e2_frei`), Breite von BB2 und Länge von GB3 (`e2_lager_b`, `e2_mitnehmer_l`). Davon hängen `kardan_spiel` und die Bauart der Rutschkupplung ab (`rk_serie_luft` = −24 mm, `rk_luft` = −9 mm).
2. 🔧 **Knochen N3:** Kreuzstiftabstand (vorläufig 60 mm) und zulässiger Beugewinkel. **Prüfen, ob N3 die Wellenwinkel statisch 15,07° und ausgefedert 27,03° mitmacht** (Nutzerentscheidung „Antriebsachse bleibt hoch“), ohne zu klemmen oder aus dem Becher zu springen.
3. **Motor und Ritzel:** Wellenlänge des Motors (15 mm laut [E2]), Zahnbreite und Bund des Ritzels; danach `motor_welle_reserve` neu prüfen (zurzeit −3,0 mm).
4. **Radachse N1 und Rad:** Gesamtlänge, Lage im Rad (Gewindeende zur Radaußenseite), Schlitztiefe des Bechers (`gelenk_becher`); danach `diff_abtrieb_y` neu ableiten und `radachse_*_spiel` prüfen.
5. **Diff und Tellerrad:** Durchmesser Tellerrad, Breite Diff, Lage des Kegelritzels (`getriebe_*`).
6. **CVA-Dämpfer:** Länge ausgefedert und eingefedert, Durchmesser Zylinder und Kappe; danach `federweg` aus Hub und Hebelverhältnis neu bestimmen.
7. Übrige vorläufige Maße (rote Hüllkörper): Regler, UBEC, XT60, Ritzelbreite. Räder wiegen (`rad_masse`) und [Massenabgleich](#massenabgleich-skript) ausführen.

**Hinweise:**
- **Mittelantrieb:** Motorwelle zu kurz für Motorhalter, Abdeckungswand und Ritzel (`motor_welle_reserve` = −3,0 mm, Möglichkeiten unter [Zahnebene](#zahnebene-ritzel-und-motor)); Bauart der Rutschkupplung auf E2 (siehe [Rutschkupplung](#rutschkupplung-auf-der-kegelritzelwelle); auch um den Becher fehlen 9 mm, `rk_luft`), die Motorlage setzt Möglichkeit 1 voraus; Motorhalter mit Verstellung auf dem Bogen um E2 für 16Z–25Z; Motor ↔ Kardanwelle bei 16Z nur 0,8 mm; Stückliste Pos. 47 (Mittelschott) entfällt.
- **Antriebswellen schräg** (siehe [Höhe der Antriebsachse](#höhe-der-antriebsachse)): 27° ausgefedert, vom Nutzer bewusst in Kauf genommen, Prüfung bei Lieferung (Messpunkt 2).
- **Lenkung:** Das äußere Gelenk der vorderen Welle liegt 1,30 mm außerhalb der angenommenen Lenkachse (`lenkgelenk_versatz`), also fast auf der Achse. `lenkachse_versatz` = 20 mm passt damit zum TT-02B-Rad.
- **Dämpfer** sind vereinfacht senkrecht bei Y ±55 mm modelliert. Die echte Lage und das Hebelverhältnis legen Querlenker und Dämpferbrücken fest (Vorgabe Hebelverhältnis in `docs/zukaufteile-v1.md`).
- Federweg-Aufteilung (2/3 ein, 1/3 aus), `lenkwinkel_max` und `lenkachse_versatz` sind Annahmen aus dem Anforderungsdokument.

## Historie

- **Fassung 1** (2026-10-27, PR #5, Design-Version 6): Spender TLR 22X-4, Radstand 283,5 mm, Spur 250 mm außen, Räder Carson Ø 85 × 40 mm, Mittelantrieb mit TLR-Rutschkupplung, Mittelschott und zwei Mittelwellen. Ergebnis damals: Grundplatte 335,5 × 154 mm, Teilung bei X = 50 mm. In Fassung 2 entfernt: die Hüllkörper `mittelantrieb-mittelschott`, `mittelantrieb-abtrieb-vorne`, `mittelantrieb-mittelwelle-vorne` (die hintere Mittelwelle ist jetzt `mittelantrieb-kardanwelle`) und die Parameter `zahn_pitch`, `mittelwelle_*`, `mitte_*`, `mittelantrieb_*`, `ms_*`, `abtrieb_*`, `daempfer_gehaeuse`, `daempfer_hub`, `motor_vorne_x`, `radachse_becher`.
- **Fassung 2** (2026-10-28, Design-Version 8): Umstellung auf Tamiya TT-02B (dieses Dokument).
- **Review 1** (2026-10-28, Design-Version 9): Bauraum für den Motorhalter (`motorhalter_dicke`, Motor und Elektronik rechts 4 mm nach vorne), Bilanz auf E2 mit Lager BB2 und Mitnehmer GB3 (`e2_lager_b`, `e2_mitnehmer_l`, `rk_serie_luft` −12 → −24 mm), Kommentare `getriebe_eingang` und `e2_frei` ehrlich formuliert, Nutzerentscheidung „Antriebsachse bleibt hoch“ eingearbeitet.
- **Review 2** (2026-10-28, Design-Version 10): `rk_luft` zählt vorderes Lager BB2 und Mitnehmer GB3 mit (+3 → −9 mm), Kommentare `getriebe_vor_achse` und `rk_l` angeglichen; MECH-SKE-008 „teilweise erfüllt“ nach Nutzerentscheidung (Abnahme mit `motor_welle_reserve` < 0); Komponentenzahl genau angegeben (39 Hüllkörper + Root).

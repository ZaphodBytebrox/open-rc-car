# Skelettmodell des Fahrzeugs

- **Anforderungen:** `docs/anforderungen/skelett.md` (Kürzel SKE)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-skelett“
- **Exporte:** `cad/fusion/skelett.f3d`, `cad/step/skelett.step`
- **Stand:** 2026-10-27

Das Skelett ist kein Bauteil. Es ist die Bezugsgeometrie für Grundplatte, Achsen, Mittelantrieb, Lenkung und Elektronikhalter: Fahrzeugparameter, Radpositionen mit Bewegungsraum, Hüllkörper aller räumlich relevanten Zukaufteile und Bauraum für den späteren 4WD-Antrieb.

## Ergebnis des Meilensteins

| Frage | Ergebnis |
|---|---|
| Passt alles hinein? | **Ja.** Die Interferenzanalyse über alle 42 Komponenten (Hüllkörper, Bauräume und Bewegungsräume, auch der Wellen und Radachsen über Federweg und Lenkeinschlag) findet keine ungewollte Überschneidung. Die 53 Überschneidungen sind alle gewollt (Tabelle [Interferenz](#interferenzprüfung-mech-ske-010)). |
| Länge der Grundplatte | **335,5 mm** (von der Hinterkante des hinteren bis zur Vorderkante des vorderen Achsgetriebes) |
| Breite der Grundplatte | **154,0 mm** im breiten Mittelteil (Akku links 76 mm, Elektronik rechts 78 mm). Vorne und hinten 64 mm (Getriebebreite), vorne rechts bis zum Servo 64,2 mm. |
| Trennstelle | **`teilung_x` = 50 mm** (vor dem Mittelschott), Stoß mit 30 mm Überlappung von X = 35 bis 65 mm |
| Teile für den Druck | hinten **232,75 × 154,0 mm**, vorne **132,75 × 154,0 mm**, beide einschließlich Überlappung ≤ 250 × 250 mm |
| Schwerpunkt quer | **+0,3 mm** (links) neben der Fahrzeugmitte, über das ganze Design (1123,7 g, Räder vorläufig mit je 100 g) |

![Skelett von oben](images/skelett-oben.png)

*Von oben, vorne ist oben, links ist links. Blau: Maße belegt. Rot: Maße vorläufig mit Zuschlag. Gelb: Bauraum (Mittelschott, Zahnradabdeckung, Entnahmeweg Akku). Grün durchscheinend: Bewegungsraum der Räder, der Antriebswellen und der Radachsen. Grau: Grundplatte.*

![Skelett von der Seite](images/skelett-seite.png)

*Von rechts, vorne ist rechts. Man sieht den Stoß der Grundplatte (Überlappung mit halber Plattenstärke je Teil).*

![Skelett isometrisch](images/skelett-iso.png)

## Koordinatensystem (MECH-SKE-003)

- Ursprung: Fahrzeugmitte quer, Mitte zwischen den Achsen längs, Bodenebene.
- **X** längs, positiv nach vorne. **Y** quer, positiv nach links. **Z** hoch, Boden bei Z = 0.
- Konstruktionslage: statisch, fahrfertig, Räder auf dem Boden, Lenkung geradeaus.
- Das Design ist in Fusion als **Hybrid-Design** angelegt (Komponenten und Bezugsgeometrie in der Wurzel). Ein neues Fusion-Dokument ist ein Bauteil-Design mit nur einer Komponente, deshalb wurde die Design-Absicht auf „Hybrid“ umgestellt.

Benannte Konstruktionsebenen in der Wurzelkomponente, alle als Versatz der Ursprungsebenen:

| Ebene | Lage | Parameter |
|---|---|---|
| Vorderachse | X = +141,75 mm | `achse_x` |
| Hinterachse | X = −141,75 mm | `-achse_x` |
| Fahrzeugmitte | Y = 0 | Ursprungsebene XZ |
| Boden | Z = 0 | Ursprungsebene XY |
| Unterkante Grundplatte | Z = 25 mm | `bodenfreiheit` |
| Oberkante Grundplatte | Z = 29 mm | `platte_oben` |
| Antriebsachse | Z = 56,17 mm | `antrieb_z` |
| Teilung Grundplatte | X = 50 mm | `teilung_x` |

Dazu je Vorderrad eine Lenkachse (`lenkachse-vl`, `lenkachse-vr`), Schnitt zweier Ebenen bei X = `achse_x` und Y = ±(`rad_y` − `lenkachse_versatz`).

## Aufbau in Fusion

- Jeder Hüllkörper ist eine eigene Komponente, Name nach dem Schema `<baugruppe>-<teil>`, z. B. `elektronik-akku` oder `antrieb-getriebe-hinten`.
- Jeder Körper entsteht aus einer voll bestimmten Skizze im Ursprung der Komponente (Rechteck mittig zum Ursprung oder Kreis um den Ursprung), einer symmetrischen Extrusion und einer Verschiebung (Verschieben, X/Y/Z). Alle Maße der Skizzen, die Extrusionslängen und die Verschiebungen sind Ausdrücke aus Benutzerparametern.
- Feste Zahlen gibt es nur bei Lagen auf der Fahrzeugmitte (Verschiebung Y = 0 mm) und bei den Ursprungsebenen Fahrzeugmitte und Boden (Versatz 0 mm). Das sind Festlegungen des Koordinatensystems, keine Maße eines Hüllkörpers (Prüfskript über alle Modellparameter).
- Bewegungsraum der Räder: zwei Zylinder in der tiefsten und höchsten Radstellung, verbunden durch einen Quader; vorne zusätzlich als Kreismuster um die Lenkachse mit `lenk_schritte` = 7 Stellungen über ±`lenkwinkel_max` (Schritt 10°) und vereinigt. Zwischen den Stellungen fehlt am Radumfang höchstens r·(1 − cos 5°) ≈ 0,2 mm (r = 58,4 mm Abstand der äußersten Radkante von der Lenkachse).
- Antriebswellen: schräger Zylinder `antriebswelle_d` × Wellenlänge vom inneren Gelenk (Y = ±`diff_abtrieb_y`, Z = `antrieb_z`) zum äußeren Gelenk auf Radmittenhöhe. Die Wellenlänge gilt räumlich (Kreuzstiftabstand), das äußere Gelenk liegt deshalb bei Y = `diff_abtrieb_y` + √(l² − `antrieb_dz`²) (`antriebswelle_h_y`, `antriebswelle_v_y`). Umgesetzt als Kreis, symmetrische Extrusion, Drehung um die X-Achse um `antriebswelle_*_winkel` und Verschiebung.
- Bewegungsraum der Wellen und Radachsen (`antrieb-wellenraum-*`): Die Welle schwenkt um das innere Gelenk von ausgefedert (`antriebswelle_*_winkel_aus`) bis eingefedert (`antriebswelle_*_winkel_ein`), als Kreismuster mit `wellen_schritte` = 7 Stellungen. Die Radachse bewegt sich mit dem Rad über den Federweg (zwei Zylinder und ein Quader wie beim Rad). Vorne kommt der Lenkeinschlag dazu: Die Radachse dreht mit `lenk_schritte` Stellungen um die Lenkachse, die Welle schwenkt um eine senkrechte Achse durch das innere Gelenk um ±`antriebswelle_v_gier` (3 Stellungen, `wellen_gier_schritte`). Vereinfachung: Das äußere Gelenk folgt dem Rad senkrecht, die echte Kinematik kommt mit den Querlenkern. Zwischen den Stellungen fehlt am Wellenende höchstens 0,1 mm.
- Massen: Die Hüllkörper mit belegter Masse haben je ein eigenes Material (`masse-<komponente>`), die vier Räder das gemeinsame Material `masse-fahrwerk-rad`. Die Dichte ist so gesetzt, dass Fusion den Wert des Parameters (`akku_masse` … `ubec_masse`, `rad_masse`) anzeigt. Alle anderen Körper (Getriebe, Wellen, Bauräume, Bewegungsräume, Grundplatte) haben das Material `masse-null` mit 0,001 kg/m³ (zusammen unter 0,01 g). So stimmt der Schwerpunkt über das ganze Design mit dem Schwerpunkt der Teile mit Masse überein. **Die Masse-Parameter sind nicht ans Modell gebunden** (Fusion kann die Dichte nicht aus einem Ausdruck rechnen). Nach einer Änderung eines Masse-Parameters oder der Maße dieser Hüllkörper den [Massenabgleich](#massenabgleich-skript) ausführen.
- **Referenz für spätere Baugruppen (Vorschlag):** Jede Baugruppe (Grundplatte, Hinterachse, Mittelantrieb …) entsteht in einem eigenen Fusion-Design im Projekt „open-rc-car“ und übernimmt Benutzerparameter, Bezugsebenen und die nötigen Hüllkörper per **Ableiten (Derive)** aus „open-rc-car-skelett“. Maße, die das Skelett festlegt, werden dort nicht neu eingegeben. Änderungen am Skelett kommen über „Ableitung aktualisieren“ in die Baugruppen. Die erste Baugruppe (Grundplatte) bestätigt oder ändert dieses Vorgehen.

## Parameterliste (MECH-SKE-001, MECH-SKE-002)

145 Benutzerparameter, jeder mit Kommentar (Quelle, „belegt“, „vorläufig“ oder „abgeleitet“). Werte im Startzustand. **Prüfmaße** (`*_spiel`, `*_luft`, `*_reserve`) steuern nichts im Modell; sie zeigen, ob feste Zukaufteil-Maße noch zusammenpassen, und werden im Nachweis geprüft.

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `radstand` | `283.5 mm` | 283,50 mm | Fahrzeug: Spender TLR 22X-4 [T1]; Nutzerentscheidung 2026-10-27 |
| `spurbreite` | `250 mm` | 250,00 mm | Fahrzeug: über die Räder, [T1] |
| `rad_durchmesser` | `85 mm` | 85,00 mm | Rad: belegt, Carson All Terrain [R1] |
| `rad_breite` | `40 mm` | 40,00 mm | Rad: belegt, Carson All Terrain [R1] |
| `bodenfreiheit` | `25 mm` | 25,00 mm | Fahrzeug: Plan, MECH-FZG-006 |
| `federweg` | `35 mm` | 35,00 mm | Fahrzeug: Plan, MECH-FZG-005 |
| `plattenstaerke` | `4 mm` | 4,00 mm | Grundplatte: Plan (Alu) |
| `huelle_zuschlag` | `2 mm` | 2,00 mm | Zuschlag je Seite für vorläufige Hüllkörper (MECH-SKE-007) |
| `einfederweg` | `federweg * 2 / 3` | 23,33 mm | Rad: Annahme 2/3 des Federwegs |
| `ausfederweg` | `federweg - einfederweg` | 11,67 mm | Rad: Annahme 1/3 des Federwegs |
| `lenkwinkel_max` | `30 deg` | 30,0° | Lenkung: Annahme, vorläufig |
| `lenkachse_versatz` | `20 mm` | 20,00 mm | Lenkung: Lenkachse innerhalb der Radmitte, Annahme, vorläufig |
| `lenk_schritte` | `7` | 7 | Lenkung: Anzahl Radstellungen im Lenk-Bewegungsraum |
| `wellen_schritte` | `7` | 7 | Bewegungsraum Antriebswelle: Anzahl Stellungen über den Federweg |
| `wellen_gier_schritte` | `3` | 3 | Bewegungsraum Antriebswelle vorne: Anzahl Stellungen über den Lenkeinschlag |
| `achse_x` | `radstand / 2` | 141,75 mm | abgeleitet: Radmitte längs |
| `rad_y` | `( spurbreite - rad_breite ) / 2` | 105,00 mm | abgeleitet: Radmitte quer |
| `rad_z` | `rad_durchmesser / 2` | 42,50 mm | abgeleitet: Radmitte Höhe |
| `platte_oben` | `bodenfreiheit + plattenstaerke` | 29,00 mm | abgeleitet: Oberkante Grundplatte |
| `hz_zaehne` | `78` | 78 | Hauptzahnrad: belegt, TLR232116 |
| `ritzel_zaehne` | `26` | 26 | Motorritzel: belegt, TLR332026 |
| `zahn_pitch` | `48` | 48 | Zahnräder: belegt, 48 Pitch |
| `hz_d` | `( hz_zaehne + 2 ) / zahn_pitch * 1 in` | 42,33 mm | Hauptzahnrad: Kopfkreis berechnet (z+2)/P Zoll |
| `ritzel_d` | `( ritzel_zaehne + 2 ) / zahn_pitch * 1 in` | 14,82 mm | Motorritzel: Kopfkreis berechnet (z+2)/P Zoll |
| `zahn_achsabstand` | `( hz_zaehne + ritzel_zaehne ) / zahn_pitch / 2 * 1 in` | 27,52 mm | Motor: Achsabstand berechnet |
| `ritzel_b_netto` | `8 mm` | 8,00 mm | Motorritzel: Breite vorläufig, Vergleichsteil |
| `ritzel_breite` | `ritzel_b_netto + 2 * huelle_zuschlag` | 12,00 mm | Motorritzel: vorläufig, mit Zuschlag |
| `hz_ebene` | `5 mm` | 5,00 mm | Hauptzahnrad: Zahnmitte ab Hinterkante Hüllkörper Rutschkupplung, vorläufig, am Teil messen (Grenze siehe `motor_welle_reserve`) |
| `ritzel_x` | `mitte_hinten_x + hz_ebene` | −3,75 mm | abgeleitet: Zahnebene, Mitte Ritzel = Mitte Hauptzahnrad |
| `abdeckung_abstand` | `3 mm` | 3,00 mm | Zahnradabdeckung: MECH-SKE-014 |
| `abdeckung_wand` | `2 mm` | 2,00 mm | Zahnradabdeckung: Wand, vorläufig |
| `abdeckung_r` | `hz_d / 2 + abdeckung_abstand + abdeckung_wand` | 26,17 mm | Zahnradabdeckung: abgeleitet |
| `abdeckung_ritzel_r` | `ritzel_d / 2 + abdeckung_abstand + abdeckung_wand` | 12,41 mm | Zahnradabdeckung: abgeleitet |
| `abdeckung_x_hinten` | `motor_vorne_x` | −13,75 mm | Zahnradabdeckung: abgeleitet, Rückwand am Motorflansch |
| `abdeckung_x_vorne` | `mitte_hinten_x + rk_l + abdeckung_abstand + abdeckung_wand` | 18,25 mm | Zahnradabdeckung: abgeleitet, Vorderwand 3 mm + Wand vor der Rutschkupplung (überschneidet das Mittelschott, gewollt) |
| `antrieb_luft` | `1 mm` | 1,00 mm | Mittelantrieb: Luft Abdeckung zu Grundplatte |
| `antrieb_z` | `platte_oben + abdeckung_r + antrieb_luft` | 56,17 mm | abgeleitet: Höhe Mittelwellen und Diff-Achsen |
| `getriebe_b` | `60 mm + 2 * huelle_zuschlag` | 64,00 mm | Getriebe: vorläufig, mit Zuschlag, Abbildungen [T1] |
| `getriebe_hinter_achse` | `24 mm + huelle_zuschlag` | 26,00 mm | Getriebe: vorläufig, mit Zuschlag, Überstand außen über Diff-Achse |
| `getriebe_eingang` | `40 mm` | 40,00 mm | Getriebe: Abstand Diff-Achse zu Kreuzstift Ritzelwelle, vorläufig |
| `getriebe_ueber_achse` | `25 mm + huelle_zuschlag` | 27,00 mm | Getriebe: vorläufig, mit Zuschlag, Höhe über Diff-Achse |
| `getriebe_l` | `getriebe_hinter_achse + getriebe_eingang` | 66,00 mm | Getriebe: abgeleitet |
| `getriebe_h` | `antrieb_z + getriebe_ueber_achse - platte_oben` | 54,17 mm | Getriebe: abgeleitet |
| `diff_abtrieb_y` | `22 mm` | 22,00 mm | Getriebe: Kreuzstift Diff-Abtrieb quer, vorläufig |
| `mittelwelle_h_l` | `93 mm` | 93,00 mm | Mittelwelle hinten: belegt, TLR232105 (Abstand der Kreuzstifte, Annahme) |
| `mittelwelle_v_l` | `68 mm` | 68,00 mm | Mittelwelle vorne: belegt, TLR232105 (Abstand der Kreuzstifte, Annahme) |
| `mittelwelle_d` | `10 mm + 2 * huelle_zuschlag` | 14,00 mm | Mittelwelle: vorläufig, mit Zuschlag |
| `mitte_hinten_x` | `-achse_x + getriebe_eingang + mittelwelle_h_l` | −8,75 mm | Mittelantrieb: abgeleitet, Kreuzstift Abtrieb hinten |
| `mitte_vorne_x` | `achse_x - getriebe_eingang - mittelwelle_v_l` | 33,75 mm | Mittelantrieb: abgeleitet, Kreuzstift Abtrieb vorne |
| `mittelantrieb_l` | `mitte_vorne_x - mitte_hinten_x` | 42,50 mm | Mittelantrieb: Ergebnis, Länge zwischen den Abtrieben |
| `rk_d` | `hz_d + 2 * huelle_zuschlag` | 46,33 mm | Rutschkupplung: vorläufig, mit Zuschlag |
| `rk_l` | `18 mm + 2 * huelle_zuschlag` | 22,00 mm | Rutschkupplung: vorläufig, mit Zuschlag, Abbildungen [T1] S. 18 |
| `ms_dicke` | `12 mm` | 12,00 mm | Mittelschott: Bauraum Eigenbau, vorläufig (2 × Lager 10x15x4) |
| `ms_b` | `50 mm` | 50,00 mm | Mittelschott: Bauraum Eigenbau, vorläufig |
| `ms_ueber` | `15 mm` | 15,00 mm | Mittelschott: Bauraum Eigenbau, vorläufig, über Wellenachse |
| `ms_h` | `antrieb_z + ms_ueber - platte_oben` | 42,17 mm | Mittelschott: abgeleitet |
| `abtrieb_d` | `14 mm + 2 * huelle_zuschlag` | 18,00 mm | Abtrieb vorne: vorläufig, mit Zuschlag |
| `abtrieb_l` | `8.5 mm` | 8,50 mm | Abtrieb vorne: Länge vorläufig, mit Zuschlag; fest, damit fehlender Platz als Überschneidung sichtbar wird; am Teil messen |
| `mittelantrieb_luft` | `mittelantrieb_l - rk_l - ms_dicke - abtrieb_l` | 0,00 mm | Prüfmaß: freie Länge im Mittelantrieb, muss ≥ 0 sein |
| `motor_d` | `36 mm` | 36,00 mm | Motor: belegt, Lindinger [E2] |
| `motor_l` | `52 mm` | 52,00 mm | Motor: belegt, Lindinger [E2] |
| `motor_y` | `-zahn_achsabstand` | −27,52 mm | Motor: abgeleitet, rechts |
| `motor_vorne_x` | `mitte_hinten_x - abdeckung_abstand - abdeckung_wand` | −13,75 mm | Motor: abgeleitet, Motorflansch an Rückwand der Abdeckung |
| `motor_welle_l` | `15 mm` | 15,00 mm | Motor: Wellenlänge belegt, Lindinger [E2] (3,175 × 15 mm) |
| `motor_welle_reserve` | `motor_vorne_x + motor_welle_l - ( ritzel_x + ritzel_b_netto / 2 )` | 1,00 mm | Prüfmaß: Motorwelle ragt über das Ritzel hinaus, muss ≥ 0 sein |
| `antriebswelle_h_l` | `67 mm` | 67,00 mm | Antriebswelle hinten: belegt, TLR232102 |
| `antriebswelle_v_l` | `74 mm` | 74,00 mm | Antriebswelle vorne 4WD: belegt, TLR232104 |
| `antriebswelle_d` | `10 mm + 2 * huelle_zuschlag` | 14,00 mm | Antriebswelle: vorläufig, mit Zuschlag |
| `antrieb_dz` | `antrieb_z - rad_z` | 13,67 mm | abgeleitet: Höhe Diff-Abtrieb über Radmitte in Konstruktionslage |
| `antriebswelle_h_y` | `diff_abtrieb_y + sqrt(antriebswelle_h_l ^ 2 - antrieb_dz ^ 2)` | 87,59 mm | abgeleitet: äußerer Kreuzstift hinten quer, Welle schräg mit Länge `antriebswelle_h_l` |
| `antriebswelle_v_y` | `diff_abtrieb_y + sqrt(antriebswelle_v_l ^ 2 - antrieb_dz ^ 2)` | 94,73 mm | abgeleitet: äußerer Kreuzstift vorne quer |
| `antriebswelle_h_winkel` | `asin(antrieb_dz / antriebswelle_h_l)` | 11,77° | abgeleitet: Neigung Welle hinten in Konstruktionslage (außen tiefer) |
| `antriebswelle_v_winkel` | `asin(antrieb_dz / antriebswelle_v_l)` | 10,64° | abgeleitet: Neigung Welle vorne in Konstruktionslage |
| `antriebswelle_h_winkel_aus` | `asin(( antrieb_dz + ausfederweg ) / antriebswelle_h_l)` | 22,22° | abgeleitet: Neigung Welle hinten ausgefedert |
| `antriebswelle_h_winkel_ein` | `asin(( antrieb_dz - einfederweg ) / antriebswelle_h_l)` | −8,30° | abgeleitet: Neigung Welle hinten eingefedert (negativ = außen höher) |
| `antriebswelle_v_winkel_aus` | `asin(( antrieb_dz + ausfederweg ) / antriebswelle_v_l)` | 20,02° | abgeleitet: Neigung Welle vorne ausgefedert |
| `antriebswelle_v_winkel_ein` | `asin(( antrieb_dz - einfederweg ) / antriebswelle_v_l)` | −7,51° | abgeleitet: Neigung Welle vorne eingefedert |
| `lenkgelenk_versatz` | `antriebswelle_v_y - ( rad_y - lenkachse_versatz )` | 9,73 mm | abgeleitet: äußeres Gelenk vorne außerhalb der Lenkachse (ideal 0, Hinweis für die Lenkung) |
| `antriebswelle_v_gier` | `asin(abs(lenkgelenk_versatz) * sin(lenkwinkel_max) / antriebswelle_v_l)` | 3,77° | abgeleitet: Schwenk der Welle vorne um das innere Gelenk beim vollen Lenkeinschlag |
| `radachse_d` | `16 mm + 2 * huelle_zuschlag` | 20,00 mm | Radachse mit Mitnehmer: vorläufig, mit Zuschlag |
| `radachse_becher` | `8 mm` | 8,00 mm | Radachse: Becher innen über Kreuzstift, vorläufig |
| `radachse_h_l` | `45.4 mm` | 45,40 mm | Radachse hinten mit Mitnehmer und Radmutter: Länge vorläufig (aus Startlage abgeleitet), am Teil messen; fest, damit Spuränderungen sichtbar werden |
| `radachse_v_l` | `38.3 mm` | 38,30 mm | Radachse vorne: wie hinten |
| `radachse_h_spiel` | `antriebswelle_h_y - ( rad_y + rad_breite / 2 - radachse_h_l + radachse_becher )` | −0,01 mm | Prüfmaß: Kreuzstift hinten zu Becher der Radachse, Soll 0 (±0,5 mm) |
| `radachse_v_spiel` | `antriebswelle_v_y - ( rad_y + rad_breite / 2 - radachse_v_l + radachse_becher )` | 0,03 mm | Prüfmaß: Kreuzstift vorne zu Becher der Radachse, Soll 0 (±0,5 mm) |
| `daempfer_gehaeuse` | `42 mm` | 42,00 mm | Dämpfer: belegt, TLR233064 |
| `daempfer_hub` | `30.5 mm` | 30,50 mm | Dämpfer: belegt, [T1] Setup-Sheet |
| `daempfer_augen` | `20 mm` | 20,00 mm | Dämpfer: Kappe und Augen, vorläufig, Vergleichsteil |
| `daempfer_feder_d` | `21 mm` | 21,00 mm | Dämpfer: Außendurchmesser Feder, vorläufig, Vergleichsteil |
| `daempfer_d` | `daempfer_feder_d + 2 * huelle_zuschlag` | 25,00 mm | Dämpfer: vorläufig, mit Zuschlag |
| `daempfer_l` | `daempfer_gehaeuse + daempfer_hub + daempfer_augen + 2 * huelle_zuschlag` | 96,50 mm | Dämpfer: vorläufig, mit Zuschlag, ausgefedert |
| `daempfer_y` | `52 mm` | 52,00 mm | Dämpfer: Lage quer, vorläufig |
| `daempfer_dx` | `24 mm` | 24,00 mm | Dämpfer: Versatz zur Fahrzeugmitte hin, vorläufig |
| `daempfer_z_unten` | `35 mm` | 35,00 mm | Dämpfer: unteres Auge, vorläufig |
| `servo_l` | `40.3 mm` | 40,30 mm | Lenkservo: belegt, Lindinger |
| `servo_b` | `20.2 mm` | 20,20 mm | Lenkservo: belegt, Lindinger |
| `servo_h` | `37.2 mm` | 37,20 mm | Lenkservo: belegt, Lindinger |
| `servo_x` | `achse_x - getriebe_eingang - 1.5 mm - servo_l / 2` | 80,10 mm | Lenkservo: Lage, vorläufig |
| `servo_y` | `-( mittelwelle_d / 2 + 5 mm + servo_b / 2 )` | −22,10 mm | Lenkservo: Lage, vorläufig |
| `elektronik_y_aussen` | `78 mm` | 78,00 mm | Elektronik: Außenkante rechts, vorläufig |
| `regler_l` | `48.5 mm + 2 * huelle_zuschlag` | 52,50 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 46 / Hobbywing 48,5 |
| `regler_b` | `38 mm + 2 * huelle_zuschlag` | 42,00 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 36,5 / Hobbywing 38 |
| `regler_h` | `34.3 mm + 2 * huelle_zuschlag` | 38,30 mm | Regler: vorläufig, mit Zuschlag, größtes Maß aus Lindinger 34,3 / Hobbywing 32, mit Lüfter |
| `regler_x` | `63.25 mm` | 63,25 mm | Regler: Lage, vorläufig |
| `regler_y` | `-( elektronik_y_aussen - regler_b / 2 )` | −57,00 mm | Regler: Lage |
| `ubec_l` | `45 mm + 2 * huelle_zuschlag` | 49,00 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 43,1 / htmodel 45 |
| `ubec_b` | `32.3 mm + 2 * huelle_zuschlag` | 36,30 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 32,3 / htmodel 20 |
| `ubec_h` | `16.2 mm + 2 * huelle_zuschlag` | 20,20 mm | UBEC: vorläufig, mit Zuschlag, größtes Maß aus RC Team 12,5 / htmodel 16,2 |
| `ubec_x` | `11.5 mm` | 11,50 mm | UBEC: Lage, vorläufig |
| `ubec_y` | `-( elektronik_y_aussen - ubec_b / 2 )` | −59,85 mm | UBEC: Lage |
| `empf_l` | `46 mm` | 46,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_b` | `26 mm` | 26,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_h` | `15 mm` | 15,00 mm | Empfänger: belegt, Lindinger [E4] |
| `empf_x` | `-37 mm` | −37,00 mm | Empfänger: Lage, vorläufig |
| `empf_y` | `-( elektronik_y_aussen - empf_b / 2 )` | −65,00 mm | Empfänger: Lage |
| `akku_l` | `138 mm` | 138,00 mm | Akku: belegt, RC Team |
| `akku_b` | `46 mm` | 46,00 mm | Akku: belegt, RC Team |
| `akku_h` | `25 mm` | 25,00 mm | Akku: belegt, RC Team |
| `akku_x` | `0 mm` | 0,00 mm | Akku: Lage, vorläufig |
| `akku_y_innen` | `30 mm` | 30,00 mm | Akku: Innenkante links, vorläufig |
| `akku_y` | `akku_y_innen + akku_b / 2` | 53,00 mm | Akku: abgeleitet |
| `akku_entnahme_h` | `100 mm` | 100,00 mm | Akku: Höhe des freizuhaltenden Entnahmewegs nach oben (MECH-SKE-015) |
| `xt60_l` | `30 mm + 2 * huelle_zuschlag` | 34,00 mm | XT60: vorläufig, mit Zuschlag, Steckerpaar gesteckt, Vergleichsteil |
| `xt60_b` | `16 mm + 2 * huelle_zuschlag` | 20,00 mm | XT60: vorläufig, mit Zuschlag, Vergleichsteil |
| `xt60_h` | `8 mm + 2 * huelle_zuschlag` | 12,00 mm | XT60: vorläufig, mit Zuschlag, Vergleichsteil |
| `xt60_x` | `akku_x + akku_l / 2 + 0.5 mm + xt60_b / 2` | 79,50 mm | XT60: Lage vor dem Akku |
| `xt60_y` | `akku_y_innen + xt60_l / 2` | 47,00 mm | XT60: Lage |
| `teilung_x` | `50 mm` | 50,00 mm | Grundplatte: Trennstelle für den Druck (MECH-SKE-013) |
| `teilung_ueberlappung` | `30 mm` | 30,00 mm | Grundplatte: Überlappung des Stoßes, Annahme |
| `platte_x_hinten` | `-( achse_x + getriebe_hinter_achse )` | −167,75 mm | Grundplatte: abgeleitet, Hinterkante = Getriebe hinten |
| `platte_x_vorne` | `achse_x + getriebe_hinter_achse` | 167,75 mm | Grundplatte: abgeleitet, Vorderkante = Getriebe vorne |
| `platte_mitte_hinten` | `akku_x - akku_l / 2` | −69,00 mm | Grundplatte: abgeleitet, breiter Teil ab Akku |
| `platte_mitte_vorne` | `regler_x + regler_l / 2` | 89,50 mm | Grundplatte: abgeleitet, breiter Teil bis Regler |
| `platte_links` | `akku_y_innen + akku_b` | 76,00 mm | Grundplatte: abgeleitet, Außenkante Akku |
| `platte_rechts` | `elektronik_y_aussen` | 78,00 mm | Grundplatte: abgeleitet, Außenkante Elektronik |
| `platte_schmal_rechts` | `-servo_y + servo_b / 2` | 32,20 mm | Grundplatte: abgeleitet, vorne rechts bis Servo |
| `platte_laenge` | `platte_x_vorne - platte_x_hinten` | 335,50 mm | Grundplatte: Ergebnis Gesamtlänge |
| `platte_breite` | `platte_links + platte_rechts` | 154,00 mm | Grundplatte: Ergebnis Gesamtbreite |
| `akku_masse` | `300 g` | 300,0 g | Masse: belegt, RC Team; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `motor_masse` | `223 g` | 223,0 g | Masse: belegt, Lindinger [E2]; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `regler_masse` | `90 g` | 90,0 g | Masse: belegt, größerer Wert Hobbywing 90 / Lindinger 86,6; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `servo_masse` | `64 g` | 64,0 g | Masse: belegt, Lindinger; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `empf_masse` | `12.7 g` | 12,7 g | Masse: belegt, Lindinger [E4]; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `ubec_masse` | `34 g` | 34,0 g | Masse: belegt, RC Team [E8]; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |
| `rad_masse` | `100 g` | 100,0 g | Masse: vorläufig, Vergleichswert 1:10-Buggyrad (Nutzerentscheidung 2026-10-27), nach Lieferung wiegen; nicht ans Modell gebunden, wirkt über die Dichte des Materials `masse-*`, nach Änderung [Massenabgleich](#massenabgleich-skript) ausführen |

Quellen in eckigen Klammern wie in `docs/zukaufteile-v1.md`, Abschnitt „Quellen“.

## Hüllkörper (MECH-SKE-006, MECH-SKE-007)

**Belegt:** Maße aus der Stückliste mit Quelle, ohne Zuschlag. **Vorläufig:** abgeleitet aus Anleitung TLR03026 [T1] (Abbildungen), Produktseite oder Vergleichsteil, mit `huelle_zuschlag` = 2 mm je Seite; bei widersprüchlichen Quellen gilt das größere Maß. Ein Hüllkörper ist vorläufig, sobald eines seiner Maße vorläufig ist. In Fusion sind belegte Hüllkörper blau, vorläufige rot. Maße als Länge (X) × Breite (Y) × Höhe (Z) bzw. Durchmesser × Länge; Lage als Bereich im Fahrzeugkoordinatensystem.

| Komponente | Teil (Stückliste Pos.) | Maße im Modell | Lage (X / Y / Z in mm) | Status | Quelle |
|---|---|---|---|---|---|
| `elektronik-akku` | Akku Voltz 2S 5000 (51) | 138 × 46 × 25 | −69…69 / 30…76 / 29…54 | belegt | RC Team, Stückliste |
| `elektronik-regler` | Regler WP10BL60 G2 mit Lüfter (46) | 52,5 × 42 × 38,3 (48,5 × 38 × 34,3 + Zuschlag) | 37…89,5 / −78…−36 / 29…67,3 | vorläufig | Lindinger 46 × 36,5 × 34,3, Hobbywing 48,5 × 38 × 32: je Achse das größere Maß |
| `elektronik-ubec` | UBEC 10A V2 (50) | 49 × 36,3 × 20,2 (45 × 32,3 × 16,2 + Zuschlag) | −13…36 / −78…−41,7 / 29…49,2 | vorläufig | RC Team 43,1 × 32,3 × 12,5 [E8], htmodel 45 × 20 × 16,2 [E9]: je Achse das größere Maß |
| `elektronik-empfaenger` | Empfänger HR7E (48) | 46 × 26 × 15 | −60…−14 / −78…−52 / 29…44 | belegt | Lindinger [E4] |
| `elektronik-xt60` | XT60-Steckerpaar gesteckt (52) | 20 × 34 × 12 (16 × 30 × 8 + Zuschlag) | 69,5…89,5 / 30…64 / 29…41 | vorläufig | Vergleichsteil XT60 (Stückliste: „am Teil messen“) |
| `lenkung-servo` | Servo Savöx SC-1258TG+ (49), stehend | 40,3 × 20,2 × 37,2 | 59,95…100,25 / −32,2…−12 / 29…66,2 | belegt | Lindinger |
| `mittelantrieb-motor` | Motor 3652SL G2 (47) | Ø 36 × 52, Achse längs | −65,75…−13,75 / Achse Y −27,52 / Achse Z 56,17 | belegt | Lindinger [E2] |
| `mittelantrieb-motorritzel` | Motorritzel 26Z 48P (15) | Ø 14,82 × 12 | −9,75…2,25 (Mitte `ritzel_x` = Zahnebene) / Motorachse | vorläufig | Kopfkreis aus 26Z/48P berechnet; Breite Vergleichsteil 8 mm + Zuschlag; Lage in der Zahnebene des Hauptzahnrads (`hz_ebene`, vorläufig) |
| `mittelantrieb-rutschkupplung` | Rutschkupplung (12) mit Hauptzahnrad 78Z (13) und Abtrieb hinten | Ø 46,33 × 22 | −8,75…13,25 / Y 0 / Z 56,17 | vorläufig | Kopfkreis 42,33 mm aus 78Z/48P berechnet + Zuschlag; Länge 18 mm aus [T1] S. 18 + Zuschlag |
| `mittelantrieb-abtrieb-vorne` | Abtrieb vorne der Rutschkupplung (12), 4WD | Ø 18 × 8,5 | 25,25…33,75 / Achse | vorläufig | Vergleichsteil 14 mm + Zuschlag; Länge fest (`abtrieb_l`), endet am Kreuzstift `mitte_vorne_x`; Platz geprüft über `mittelantrieb_luft` |
| `mittelantrieb-mittelwelle-hinten` | Mittelwelle 93 mm (14) | Ø 14 × 93 | −101,75…−8,75 / Achse | vorläufig (Länge belegt) | Länge TLR232105; Ø 10 mm Vergleichsteil + Zuschlag |
| `mittelantrieb-mittelwelle-vorne` | Mittelwelle 68 mm (14), 4WD | Ø 14 × 68 | 33,75…101,75 / Achse | vorläufig (Länge belegt) | wie oben |
| `antrieb-getriebe-hinten` | Hinterachsdiff mit Tellerrad und Kegelritzel (1, 2, 3, 4) | 66 × 64 × 54,17 | −167,75…−101,75 / −32…32 / 29…83,17 | vorläufig | Abbildungen [T1] S. 9–10, 27–28; 60 × 24 + 40 × 25 über Achse, + Zuschlag |
| `antrieb-getriebe-vorne` | Vorderachsdiff, 4WD (DOC-ZUK-007) | wie hinten, gespiegelt | 101,75…167,75 / −32…32 / 29…83,17 | vorläufig | wie hinten |
| `antrieb-antriebswelle-hl`, `-hr` | Antriebswellen hinten 67 mm (5) | Ø 14 × 67, schräg 11,77° (Kreuzstift innen Y ±22 / Z 56,17, außen Y ±87,59 / Z 42,5) | X −148,75…−134,75 / ±20,57…±89,02 / 35,65…63,02 | vorläufig (Länge belegt) | Länge TLR232102; Ø 10 mm Vergleichsteil + Zuschlag |
| `antrieb-antriebswelle-vl`, `-vr` | Antriebswellen vorne 74 mm, 4WD (TLR232104) | Ø 14 × 74, schräg 10,64° (außen Y ±94,73) | X 134,75…148,75 / ±20,71…±96,02 / 35,62…63,05 | vorläufig (Länge belegt) | wie oben |
| `antrieb-radachse-hl`, `-hr` | Radachsen hinten (6) mit Mitnehmer 12 × 5 (7), Radmutter (11) | Ø 20 × 45,4 (`radachse_h_l`, fest) | ±79,6…±125 / Z Achse 42,5 | vorläufig | Vergleichsteil 16 mm + Zuschlag; Länge aus der Startlage abgeleitet, fest, reicht bis zur Außenseite des Rads |
| `antrieb-radachse-vl`, `-vr` | Radachsen vorne (16) mit Mitnehmer 12 × 4 (17), Radmutter (11) | Ø 20 × 38,3 (`radachse_v_l`, fest) | ±86,7…±125 | vorläufig | wie oben |
| `antrieb-wellenraum-hl`, `-hr` | Bewegungsraum Antriebswelle und Radachse hinten | Welle geschwenkt −8,30…22,22° um das innere Gelenk, Radachse über den Federweg | X −151,75…−131,75 / ±19,35…±125 / 20,83…75,83 | abgeleitet | Parameter Welle, Radachse, Federweg |
| `antrieb-wellenraum-vl`, `-vr` | Bewegungsraum Antriebswelle und Radachse vorne | wie hinten (−7,51…20,02°), dazu Welle ±3,77° um das innere Gelenk und Radachse ±30° um die Lenkachse | X 113,09…170,41 / ±19,56…±126,13 / 20,83…75,83 | abgeleitet | Parameter Welle, Radachse, Federweg, Lenkung |
| `fahrwerk-daempfer-vl`, `-vr`, `-hl`, `-hr` | Dämpfer TLR G3 42 mm (18) | Ø 25 × 96,5, senkrecht | X ±(105,25…130,25) / ±39,5…±64,5 / 35…131,5 | vorläufig | Gehäuse 42 mm und Hub 30,5 mm belegt [T1]; Augen/Kappe 20 mm und Feder Ø 21 mm Vergleichsteil, + Zuschlag |
| `fahrwerk-rad-vl`, `-vr`, `-hl`, `-hr` | Räder Carson All Terrain (19) | Ø 85 × 40 | Radmitte ±141,75 / ±105 / 42,5 | belegt | Lindinger [R1] |
| `fahrwerk-radraum-*` | Bewegungsraum der Räder | Höhe 120 (85 + 35); vorne mit Lenkeinschlag ±30° | hinten −11,67…108,33 hoch; vorne X 84,94…198,56, Y ±63,75…±140,89 | abgeleitet | Parameter Rad, Federweg, Lenkung |
| `mittelantrieb-mittelschott` | Mittelschott (62), Eigenbau | 12 × 50 × 42,17 | 13,25…25,25 / −25…25 / 29…71,17 | Bauraum, vorläufig | Lager 2 × 10x15x4; Maße wie 22X-4 angenommen |
| `mittelantrieb-zahnradabdeckung` | Zahnradabdeckung (64), Eigenbau | Zylinder r 26,17 um das Hauptzahnrad und r 12,41 um das Ritzel, Länge 32 | −13,75…18,25 / −39,92…26,17 / 30…82,33 | Bauraum | MECH-SKE-014: 3 mm Abstand + 2 mm Wand radial sowie vor und hinter der Rutschkupplung |
| `elektronik-akku-entnahmeweg` | freizuhaltender Weg nach oben | 138 × 46 × 100 | über dem Akku, Z 54…154 | Bauraum | MECH-SKE-015 |
| `chassis-grundplatte` | Grundplatte (56), zwei Körper | siehe [Grundplatte](#grundplatte-mech-ske-012-mech-ske-013) | Z 25…29 | Bauraum | abgeleitet |

**Positionen der Stückliste ohne eigenen Hüllkörper (begründet):**

| Pos. | Teil | Begründung |
|---|---|---|
| 2, 3, 4, 45 | Tellerrad, Kegelritzel, Ritzelwelle, Distanzscheiben | im Hüllkörper `antrieb-getriebe-hinten` enthalten |
| 13 | Hauptzahnrad 78Z | im Hüllkörper `mittelantrieb-rutschkupplung` enthalten |
| 7, 11, 17 | Radmitnehmer, Radmuttern | im Hüllkörper der Radachse enthalten |
| 8, 9, 10 | Mitnehmerstifte, CVA-Stifte, CVA-Hülsen | Kleinteile in Wellen und Achsen |
| 20–24 | Kugellager | Normteile, sitzen in Getriebe, Mittelschott, Radträgern |
| 25–41, 44 | Schrauben, Muttern, Scheiben, Gewindeeinsätze, Kugelköpfe, Kugelpfannen | Normteile laut Anforderung ohne Hüllkörper |
| 42 | Spurstangen | Länge erst nach der Konstruktion der Lenkung und der Querlenker |
| 43 | Befestigungssatz Kegelritzel | im Getriebe enthalten |
| 53, 54 | Servo-Verlängerung, Kabelbinder | Kabel, ohne festen Bauraum |
| 55 | LiPo-Schutztasche | nicht im Fahrzeug |
| 57–61, 63, 65–67 | Oberdeck, Getriebegehäuse, Radträger, Querlenker, Dämpferbrücken, Motorhalter, Achsschenkel, Lenkhebel, Elektronikhalter | Eigenbau, noch nicht konstruiert; laut Anforderung keine Hüllkörper für Querlenker, Radträger und Dämpferbrücken. Getriebegehäuse ist im Getriebe-Hüllkörper enthalten. |

## Layout (MECH-SKE-008)

Wie beim Spender 22X-4:
- Akku längs links (Y 30…76 mm), mittig über der Fahrzeugmitte längs (X −69…69 mm), XT60 vor dem Akku.
- Motor rechts neben der Mittelwelle (Achse Y −27,52 mm = Achsabstand 78Z/26Z), Motorflansch an der Rückwand der Zahnradabdeckung, Motor nach hinten.
- Rutschkupplung mit Hauptzahnrad mittig auf der Wellenachse, davor das Mittelschott.
- Rechts vorne: Regler und UBEC, Empfänger rechts neben dem Motor. Servo vorne rechts, stehend, hinter dem Vorderachsgetriebe.
- **Wellenaufnahmen:** Abstand Kreuzstift Rutschkupplung hinten (X −8,75) zu Eingang Hinterachsgetriebe (X −101,75) = **93,0 mm**; Abtrieb vorne (X 33,75) zu Eingang Vorderachsgetriebe (X 101,75) = **68,0 mm** (Messung an den Hüllkörpern). Annahme: Die Wellenlänge ist der Abstand der Kreuzstifte; am Teil messen.
- Die Länge des Mittelantriebs zwischen den Abtrieben ergibt sich daraus zu `mittelantrieb_l` = 42,5 mm. Rutschkupplung (22 mm), Mittelschott (12 mm) und Abtrieb vorne (8,5 mm, feste Länge) füllen sie genau: `mittelantrieb_luft` = 0,0 mm. Es gibt **keine Reserve**. Wird `getriebe_eingang` größer oder ist der Kreuzstiftabstand der Mittelwellen anders als angenommen, überschneidet sich der Abtrieb vorne mit dem Mittelschott und `mittelantrieb_luft` wird negativ (Test mit `getriebe_eingang` = 45 mm: −10 mm, Abtrieb ↔ Mittelschott sichtbar in der Interferenzprüfung).

### Zahnebene, Ritzel und Motor

Wo das Hauptzahnrad axial in der Rutschkupplung sitzt, ist nicht belegt. Der Parameter `hz_ebene` (vorläufig 5 mm) gibt die Zahnmitte ab der Hinterkante des Rutschkupplungs-Hüllkörpers an; das Ritzel sitzt mittig in dieser Ebene (`ritzel_x` = −3,75 mm, Hüllkörper X −9,75…2,25).

Der Motor kann nicht weiter nach vorne: Motor (r 18 mm) und Rutschkupplung (r 23,17 mm) liegen nur 27,52 mm auseinander (Achsabstand), überdecken sich also radial. Der Motorflansch bleibt deshalb an der Rückwand der Zahnradabdeckung (`motor_vorne_x` = −13,75 mm), und das Ritzel muss auf der Motorwelle (15 mm, belegt) die Zahnebene erreichen. Prüfmaß `motor_welle_reserve` = Wellenende − Vorderkante Ritzel (8 mm Nettobreite):

| `hz_ebene` | Zahnebene X | `motor_welle_reserve` | Interferenz |
|---|---|---|---|
| 4 mm | −4,75 | 2,0 mm | keine neue Überschneidung |
| **5 mm (Modell)** | **−3,75** | **1,0 mm** | 53 gewollte |
| 6 mm | −2,75 | 0,0 mm | keine neue Überschneidung |
| 11 mm (Zahnrad mittig) | 2,25 | **−5,0 mm** | keine neue Überschneidung, aber die Welle reicht nicht |

Ergebnis: Das Hauptzahnrad muss im hinteren Teil der Rutschkupplung sitzen (`hz_ebene` ≤ 6 mm, also Zahnmitte höchstens etwa 4 mm vor der hinteren Stirnseite der echten Rutschkupplung). Sitzt es weiter vorne, braucht der Mittelantrieb eine andere Lösung (Ritzel mit Überstand, Motor auf der anderen Seite der Rutschkupplung, Rutschkupplung gewendet). **Messpunkt bei Lieferung.** In allen Lagen bleibt das Ritzel in der Zahnradabdeckung, und der Motor überschneidet sich nicht mit der Rutschkupplung (Abstand 5,0 mm).

## Höhe der Antriebsachse

Die Höhe der Mittelwellen und der Diff-Achsen ist `antrieb_z` = 56,17 mm. Sie folgt aus der Zahnradabdeckung: Unter dem Hauptzahnrad (Kopfkreis 42,33 mm) müssen 3 mm Abstand und 2 mm Wand auf die Grundplatte passen, ohne dass sich die Hüllkörper überschneiden. Die Radmitte liegt bei 42,5 mm. Die Antriebswellen laufen deshalb in Konstruktionslage um `antrieb_dz` = 13,67 mm schräg von innen oben nach außen unten. Die Wellenlänge wird räumlich gerechnet: Das äußere Gelenk liegt hinten bei Y = 87,59 mm (nicht 89 mm), vorne bei 94,73 mm. **Diese Lage ist die Vorgabe für die Radträger der Hinterachse.**

| Welle | ausgefedert | statisch | eingefedert |
|---|---|---|---|
| hinten 67 mm | 22,2° | 11,8° | −8,3° |
| vorne 74 mm | 20,0° | 10,6° | −7,5° |

**Hinweise für Hinterachse und Mittelantrieb:**
- Winkel der CVA-Gelenke über den ganzen Federweg prüfen (ausgefedert hinten 22°). Die echte Kinematik mit Querlenkern ändert die Werte.
- Alternative: Diff-Achse tiefer legen und die Grundplatte unter dem Hauptzahnrad aussparen (Abdeckung ragt dann durch die Platte nach unten, Bodenfreiheit an dieser Stelle prüfen). Damit werden die Wellen flacher. Entscheidung in der Anforderung „Mittelantrieb“ bzw. „Grundplatte“.

## Interferenzprüfung (MECH-SKE-010)

Fusion `analyzeInterference` über alle 42 Komponenten, ohne bloß berührende Flächen. Ergebnis: **53 Überschneidungen, alle gewollt, 0 ungewollt.** Geprüft sind die statischen Hüllkörper und die Bewegungsräume der Räder sowie der Antriebswellen und Radachsen über Federweg und Lenkeinschlag. Im 4WD-Bauraum (Getriebe vorne, Mittelwelle vorne, Antriebswellen vorne, Abtrieb vorne) gibt es außer den gewollten Fällen keine Überschneidung. Damit ist auch MECH-FZG-002 nachgewiesen.

| Überschneidung | Anzahl | Volumen je Fall | Begründung (gewollt) |
|---|---|---|---|
| Rad ↔ eigener Bewegungsraum | 4 | 226 980 mm³ | Das Rad liegt im eigenen Bewegungsraum. |
| Rad ↔ Wellenraum, Radraum ↔ Wellenraum | 8 | 40 566–88 299 mm³ | Der Bewegungsraum von Welle und Radachse liegt teilweise im Rad. |
| Radachse ↔ Rad, ↔ Radraum, ↔ Wellenraum | 12 | 12 032–14 263 mm³ | Radachse mit Mitnehmer sitzt in der Radnabe; Wellenraum enthält die Radachse. |
| Antriebswelle ↔ Rad, ↔ Radraum | 8 | 407–1 792 mm³ | Das äußere CVA-Gelenk sitzt in der Felge (wie beim 22X-4). |
| Antriebswelle ↔ Radachse | 4 | 1 257 mm³ | CVA-Gelenk: Welle im Becher der Radachse. |
| Antriebswelle ↔ eigener Wellenraum | 4 | 10 310–11 391 mm³ | Die Welle liegt in ihrem Bewegungsraum. |
| Antriebswelle ↔ Achsgetriebe, Wellenraum ↔ Achsgetriebe | 8 | 1 566–2 225 mm³ | Wellenende im Diff-Abtrieb. |
| Rutschkupplung ↔ Zahnradabdeckung | 1 | 37 094 mm³ | Die Abdeckung umschließt Hauptzahnrad und Rutschkupplung. |
| Motorritzel ↔ Zahnradabdeckung | 1 | 2 069 mm³ | Die Abdeckung umschließt das Ritzel. |
| Mittelschott ↔ Zahnradabdeckung | 1 | 8 988 mm³ | Die Vorderwand der Abdeckung (3 mm Abstand + 2 mm Wand vor der Rutschkupplung) liegt im Mittelschott. Die Grundplatte-/Mittelantrieb-Konstruktion entscheidet, ob das Mittelschott diese Wand bildet (dann muss es den Kopfkreis des Hauptzahnrads bis Z 82,33 mm und Y ±26,17 mm abdecken) oder eine eigene Abdeckung davor sitzt. |
| Mittelwelle hinten ↔ Zahnradabdeckung | 1 | 770 mm³ | Die Welle tritt durch die Rückwand der Abdeckung. |
| Motorritzel ↔ Rutschkupplung | 1 | 252 mm³ | Zahneingriff; die Überschneidung kommt aus dem Zuschlag der beiden Hüllkörper. |

Engste Abstände ohne Überschneidung (Fusion `measureMinimumDistance`):

| Hüllkörper | Abstand |
|---|---|
| Motor ↔ UBEC | 0,75 mm |
| Servo ↔ Vorderachsgetriebe | 1,50 mm |
| Dämpfer vorne ↔ Wellenraum vorne (Federweg und Lenkeinschlag) | 2,48 mm |
| Motor ↔ Mittelwelle hinten | 2,52 mm |
| UBEC ↔ Zahnradabdeckung | 3,39 mm |
| Akku ↔ Zahnradabdeckung | 3,91 mm |
| Dämpfer vorne ↔ Lenk-Bewegungsraum vorne | 4,08 mm |
| Dämpfer ↔ Antriebswelle (statisch), Dämpfer hinten ↔ Wellenraum hinten | 4,50 mm |
| Motor ↔ Rutschkupplung | 5,00 mm |
| Regler ↔ Lenk-Bewegungsraum vorne rechts | 6,25 mm |
| Abtrieb vorne ↔ Zahnradabdeckung | 7,00 mm |
| Grundplatte ↔ Wellenraum | 14,37 mm (hinten), 15,09 mm (vorne) |
| Dämpfer hinten ↔ Bewegungsraum hinten | 20,5 mm |

Abtrieb vorne und Mittelschott berühren sich (0,00 mm, ohne Überschneidung, `mittelantrieb_luft` = 0). Die Grundplatte, die Dämpfer, Akku, Entnahmeweg, Elektronik, Servo und die Bewegungsräume (vorne mit vollem Lenkeinschlag) überschneiden sich mit nichts außer den gewollten Fällen oben. Das gilt auch für die Zahnradabdeckung gegenüber allen anderen Hüllkörpern außer den umschlossenen Teilen und dem Mittelschott (MECH-SKE-014).

## Bodenfreiheit (MECH-SKE-011)

Tiefster Punkt aller Hüllkörper außer Rädern und ihren Bewegungsräumen: Unterkante Grundplatte bei **Z = 25,0 mm**. Danach folgen die Achsgetriebe und alle Teile auf der Platte bei 29,0 mm, die Radachsen bei 32,5 mm, die Antriebswellen bei 35,6 mm. Die Bewegungsräume der Räder reichen beim Ausfedern bis Z = −11,67 mm, die der Wellen und Radachsen bis Z = 20,83 mm. Sie zählen zu den Rädern: Ausgefedert hängt das Rad, die Bodenfreiheit gilt in Konstruktionslage.

## Grundplatte (MECH-SKE-012, MECH-SKE-013)

Der Umriss folgt den Hüllkörpern, die auf der Platte sitzen, und bleibt aus dem Lenk-Bewegungsraum der Vorderräder heraus:
- hinten schmal: X −167,75…−69, Breite `getriebe_b` = 64 mm (Hinterachsgetriebe, Mittelwelle)
- Mitte breit: X −69…89,5, Y −78…76 (Akku links, Elektronik rechts)
- vorne schmal: X 89,5…167,75, Y −32,2…32 (Vorderachsgetriebe, Servo)

**Gesamt: 335,5 × 154,0 × 4 mm** (Messung Hüllquader in Fusion).

**Teilung für den Druck:** Stoß bei `teilung_x` = 50 mm mit `teilung_ueberlappung` = 30 mm. Im Stoß hat jedes Teil die halbe Plattenstärke (hinten unten, vorne oben).

| Teil | X | Hüllquader (L × B) | ≤ 250 × 250 mm |
|---|---|---|---|
| `grundplatte-hinten` | −167,75…65,0 | 232,75 × 154,0 mm | ja |
| `grundplatte-vorne` | 35,0…167,75 | 132,75 × 154,0 mm | ja |

**Begründung der Lage:** Damit beide Teile höchstens 250 mm lang sind, muss die Teilung zwischen X = −65,25 und +65,25 mm liegen. Von X = −65,75 bis 25,25 ist die Platte durchgehend belegt: Motor (−65,75…−13,75), Zahnradabdeckung mit Rutschkupplung (−13,75…18,25) und Mittelschott (13,25…25,25). Hinter dem Motor ist kein Platz (der Stoß müsste vor −65,25 enden). Vor dem Mittelschott bleibt der Bereich X 40,25…65,25 für `teilung_x`; gewählt ist 50 mm mit Abstand zu beiden Grenzen. Der ganze Stoß (X 35…65) liegt frei von Mittelschott, Motor, Zahnradabdeckung und beiden Achsgetrieben.

Der Stoß liegt unter Akku, Regler, UBEC und Servo (Nutzerentscheidung 2026-10-27, nach Review Durchlauf 1). Der Akku (X −69…69) überdeckt den ganzen zulässigen Bereich der Teilung (−65,25…65,25); eine Teilung frei vom Akku gibt es in diesem Layout nicht. Regler (X 37…89,5) und Servo (59,95…100,25) liegen über der Stoßzone, das UBEC (bis X 36) ragt 1 mm hinein. **Hinweis für die Anforderung „Grundplatte“:** Die Verbindung am Stoß muss unter Akku, Regler und Servo flach bleiben bzw. deren Halter und Adapterplatten mit einbeziehen.

## Akku-Wechsel (MECH-SKE-015)

Über dem Akku ist ein Entnahmeweg von 138 × 46 × 100 mm als Bauraum modelliert (`elektronik-akku-entnahmeweg`). Er überschneidet sich mit keinem Hüllkörper. Ein späteres Oberdeck muss diesen Weg freilassen oder abnehmbar sein.

## Schwerpunkt (MECH-SKE-016)

Hüllkörper mit Masse, Werte aus Fusion (`physicalProperties`). Alle anderen Körper haben das Material `masse-null` (siehe [Aufbau in Fusion](#aufbau-in-fusion)). Der Schwerpunkt wird über das **ganze Design** bestimmt (`rootComponent.getPhysicalProperties`):

| Hüllkörper | Masse | Status | Schwerpunkt X / Y / Z (mm) |
|---|---|---|---|
| Akku | 300,0 g | belegt | 0,0 / 53,0 / 41,5 |
| Motor | 223,0 g | belegt | −39,8 / −27,5 / 56,2 |
| Regler | 90,0 g | belegt | 63,3 / −57,0 / 48,1 |
| Servo | 64,0 g | belegt | 80,1 / −22,1 / 47,6 |
| UBEC | 34,0 g | belegt | 11,5 / −59,9 / 39,1 |
| Empfänger | 12,7 g | belegt | −37,0 / −65,0 / 36,5 |
| 4 Räder | 4 × 100,0 g | vorläufig (`rad_masse`) | ±141,75 / ±105,0 / 42,5 |
| **Ganzes Design** | **1123,7 g** | | **1,67 / 0,32 / 45,52** |

Der Schwerpunkt liegt quer **0,32 mm** links der Fahrzeugmitte (Grenze 10 mm). Die Räder liegen symmetrisch und ändern den Querwert nur über die Gesamtmasse (ohne Räder: 0,5 mm).

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
                m = material(d, 'masse-fahrwerk-rad' if par == 'rad_masse' else 'masse-' + c.name)
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

## Parametertest (MECH-SKE-001)

`radstand` = 290 mm und `spurbreite` = 260 mm gesetzt: Zeitleiste (323 Elemente) ohne Fehler und Warnungen. Räder bei X ±145 und Y ±110 (Außenmaß 260 mm), Getriebe, Dämpfer, Motor, Wellen und die Bewegungsräume folgen. Die Radachsen haben jetzt eine feste Länge und wandern mit dem Rad nach außen; die Antriebswellen nicht. Das zeigen die Prüfmaße: `radachse_h_spiel` = −5,01 mm, `radachse_v_spiel` = −4,97 mm (Soll 0). Die Spur lässt sich also nicht über das Skelett allein ändern, sondern nur über Radträger, Achsschenkel und Einpresstiefe (siehe `docs/zukaufteile-v1.md`). Interferenz: 49 Überschneidungen, alle aus der Liste oben (4 entfallen, weil die hinteren Wellen das Rad nicht mehr erreichen), keine neue. Danach auf 283,5 / 250 mm zurückgesetzt, wieder ohne Fehler, 53 Überschneidungen.

Weitere Tests: `hz_ebene` 4 / 6 / 11 mm (Tabelle [Zahnebene](#zahnebene-ritzel-und-motor)) und `getriebe_eingang` = 45 mm (siehe [Layout](#layout-mech-ske-008)), jeweils ohne Zeitleistenfehler.

![Parametertest mit 290/260 mm](images/skelett-parametertest-290-260.png)

## Offene Punkte und Hinweise für die nächsten Baugruppen

**Messpunkte bei Lieferung, in dieser Reihenfolge** (danach Parameter ersetzen und Interferenzprüfung wiederholen):
1. **Kreuzstiftabstand der Mittelwellen 93/68 mm** (TLR232105) und **`getriebe_eingang` = 40 mm** (Diff-Achse bis Kreuzstift der Ritzelwelle). Zusammen legen sie den Mittelantrieb fest, und dort gibt es **0 mm Reserve** (`mittelantrieb_luft`). Jeder Millimeter mehr fehlt zwischen Rutschkupplung, Mittelschott und Abtrieb vorne.
2. **Lage des Hauptzahnrads in der Rutschkupplung** (`hz_ebene`, vorläufig 5 mm, zulässig ≤ 6 mm) und Länge der Motorwelle mit Ritzel (`motor_welle_reserve` ≥ 0).
3. **Radachsen** TLR232108/107: Länge mit Mitnehmer und Radmutter (`radachse_h_l`, `radachse_v_l`) und Becher bis Kreuzstift (`radachse_becher`); danach `radachse_*_spiel` prüfen.
4. Länge der Antriebswellen 67/74 mm als Kreuzstiftabstand.
5. Übrige vorläufige Maße (rote Hüllkörper): Getriebe (`getriebe_*`, `diff_abtrieb_y`), Rutschkupplung, Abtrieb vorne, Regler, UBEC, XT60, Dämpfer (Einbaulänge, Federdurchmesser), Wellen- und Achsdurchmesser. Räder wiegen (`rad_masse`) und [Massenabgleich](#massenabgleich-skript) ausführen.

**Hinweise:**
- **Antriebswellen schräg** (siehe [Höhe der Antriebsachse](#höhe-der-antriebsachse)), mit der Alternative „Aussparung in der Grundplatte unter dem Hauptzahnrad“.
- **Lenkung:** Das äußere Gelenk der vorderen Welle liegt 9,73 mm außerhalb der angenommenen Lenkachse (`lenkgelenk_versatz`; Gelenk Y 94,73 mm, Lenkachse Y 85 mm bei `lenkachse_versatz` = 20 mm). Ideal liegt das Gelenk auf der Lenkachse, sonst wandert es beim Einlenken (±4,9 mm in X bei 30°) und die Welle schwenkt um ±3,8°. Das ist im Wellenraum berücksichtigt. Die Anforderung „Lenkung“ legt `lenkachse_versatz` so fest, dass der Versatz möglichst 0 wird.
- **Dämpfer** sind vereinfacht senkrecht bei Y ±52 mm modelliert. Das entspricht nicht der geneigten Lage beim 22X-4. Am Querlenker bei Y ±52 mm und Radmitte bei Y ±105 mm ergibt sich ein Hebelverhältnis von etwa 3; dann wird nur etwa ein Drittel des Dämpferhubs (30,5 mm) genutzt, und 35 mm Federweg am Rad brauchen nur ca. 12 mm Hub. **Hinweis für Querlenker und Dämpferbrücke:** Dämpfer weiter außen anlenken und neigen (Vorgabe Hebelverhältnis ≥ 1,15 aus `docs/zukaufteile-v1.md`). Grenzen sind der Lenk-Bewegungsraum (4,08 mm) und der Wellenraum vorne (2,48 mm).
- Federweg-Aufteilung (2/3 ein, 1/3 aus), `lenkwinkel_max` und `lenkachse_versatz` sind Annahmen aus dem Anforderungsdokument.

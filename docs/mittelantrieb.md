# Mittelantrieb

- **Anforderungen:** `docs/anforderungen/mittelantrieb.md` (Kürzel MAN)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-mittelantrieb“, **Version 4**, abgeleitet von „open-rc-car-skelett“ **v14**, „open-rc-car-grundplatte“ **v11** und „open-rc-car-hinterachse“ **v13** (neue Versionen nach MECH-MAN-012, siehe [Änderungen an der Hinterachse](#änderungen-an-der-hinterachse-mech-man-012); die Bezeichnung des Zeitleisten-Elements lautet weiter „Abgeleitet von open-rc-car-hinterachse v12“, die Ableitung zeigt auf v13). Version 1 war das leere Design, Version 2 und 3 Zwischenstände (Version 3 noch mit Abdeckungsmaterial in den Schraubenbohrungen der Gehäuse-Verschraubung, siehe [Montagefolge](#montagefolge-und-ritzelwechsel-mech-man-007--018)). Die Screenshots stammen aus Version 3; die Änderung zu Version 4 ist darin nicht sichtbar.
- **Exporte (alle aus Version 4):** `cad/fusion/mittelantrieb.f3d`, `cad/step/mittelantrieb.step` (4 Druckteil-Komponenten, 6 Körper), 6 STL in `print/stl/` (`mittelantrieb-motorhalter`, `-motorplatte`, `-zahnradabdeckung-oben`, `-zahnradabdeckung-unten-links`, `-zahnradabdeckung-unten-rechts`, `-blinddeckel`). Hinterachse aus Version 13 neu exportiert (siehe unten).
- **Stand:** 2026-11-01

Der Mittelantrieb des 2WD-Prototyps v1 bringt die Kraft des Motors wie beim TT-02B direkt auf das Hinterachsgetriebe: Das Motorritzel greift in das Hauptzahnrad GB5, das mit dem Mitnehmer GB3 zwischen den beiden Lagern der Kegelritzelwelle E2 sitzt. Es gibt **keine Rutschkupplung** und **keine Kardanwelle E1** (beides Nutzerentscheidungen 2026-11-01). Neu konstruiert sind:

- **Motorhalter** (Prusament PC, fräsgerecht): steht auf dem Lochbild der Grundplatte und ist zugleich die **Vorderwand der Zahnradabdeckung**. In seinem Fenster gleitet der Sockel der Motorplatte radial zur E2-Achse (Zahnspiel-Einstellung).
- **Motorplatte** (Prusament PC): trägt den Motor (2 × M3 Senkkopf in den Flansch), wird mit 3 Klemmschrauben **von vorne** in Langlöchern am Halter geklemmt und trägt die **Becherhaube**, die den drehenden Becher von E2 umschließt. Zwischen Motor und Becher ist die **Motordose die Wand** (Nutzerentscheidung 2026-11-01).
- **Zahnradabdeckung** (PETG Test / PC fertig), dreiteilig: Oberteil und zwei Unterteile um GB5, GB3 und das Motorritzel, hinten an Getriebegehäuse und Lagerbock angepasst, vorne vom Motorhalter geschlossen.
- **Blinddeckel** in der E1-Öffnung der Becherhaube (für 4WD entfernbar).

![Mittelantrieb isometrisch](images/mittelantrieb-iso.png)

*Von vorne rechts oben, Ritzel 25Z. Blau: Motorhalter (mit Fuß auf der Grundplatte), orange: Motorplatte mit Klemmrand und Becherhaube, grün: Zahnradabdeckung (Ober- und Unterteile mit den Laschen), schwarz: Motor (Hüllkörper), rot: Blinddeckel. Dahinter das Getriebegehäuse (gelb) mit Lagerbock und Querlenkerböcken (weiß).*

![Mittelantrieb von oben](images/mittelantrieb-oben.png)

*Von oben, vorne ist oben, rechts ist rechts. Oberdeck durchscheinend.*

## Ergebnis

| Teil | Komponente / Körper | Hüllquader X × Y × Z (mm) | Lage X / Y / Z (mm) | Masse PC 100 % | Datei |
|---|---|---|---|---|---|
| Motorhalter | `mittelantrieb-motorhalter` / `motorhalter` | 35,0 × 81,3 × 61,8 | −100,5…−65,5 / −54,7…26,6 / 29,0…90,8 | 21,2 g | `print/stl/mittelantrieb-motorhalter.stl` |
| Motorplatte (25Z) | `mittelantrieb-motorplatte` / `motorplatte` | 18,0 × 69,9 × 50,4 | −97,0…−79,0 / −55,4…14,5 / 38,8…89,2 | 9,5 g | `print/stl/mittelantrieb-motorplatte.stl` |
| Zahnradabdeckung oben | `mittelantrieb-zahnradabdeckung-v1` / `zahnradabdeckung-oben` | 16,0 × 87,5 × 27,0 | −113,0…−97,0 / −53,4…34,1 / 56,6…83,6 | 6,0 g | `print/stl/mittelantrieb-zahnradabdeckung-oben.stl` |
| Zahnradabdeckung unten links | `…-v1` / `zahnradabdeckung-unten-links` | 16,0 × 21,3 × 22,0 | −113,0…−97,0 / 12,8…34,1 / 34,6…56,6 | 1,6 g | `print/stl/mittelantrieb-zahnradabdeckung-unten-links.stl` |
| Zahnradabdeckung unten rechts | `…-v1` / `zahnradabdeckung-unten-rechts` | 16,0 × 40,6 × 22,0 | −113,0…−97,0 / −53,4…−12,8 / 34,6…56,6 | 2,4 g | `print/stl/mittelantrieb-zahnradabdeckung-unten-rechts.stl` |
| Blinddeckel | `mittelantrieb-blinddeckel` / `blinddeckel` | 4,5 × 22,2 × 22,5 | −82,0…−77,5 / um E2 | 1,7 g | `print/stl/mittelantrieb-blinddeckel.stl` |
| **Summe Druckteile** | | | | **42,3 g** (PETG 44,8 g; Soll ≤ 60 g) | |

Masse = Volumen aus Fusion × 1,20 g/cm³ (Prusament PC, 100 % Füllung, obere Grenze), Volumen gesamt 35,25 cm³. Der Name der Abdeckungs-Komponente endet auf `-v1`, weil das Skelett schon einen Hüllkörper `mittelantrieb-zahnradabdeckung` hat.

Hüllkörper (kein Druckteil): `mittelantrieb-huelle-motor` (Motor Ø 36 × 52 mit Welle Ø 3,175 × 15, belegt), `mittelantrieb-huelle-ritzel` (Kopfkreis des eingebauten Ritzels × `ma_ritzel_l`), `mittelantrieb-huelle-hauptzahnrad` (GB5 Ø 43,2 × `ma_gb5_b`, GB3 Ø `ma_gb3_d` × `ma_gb3_b`, vorläufig). Die Skelett-Hüllen `mittelantrieb-motor`, `-motorritzel`, `-zahnradabdeckung` und `-rutschkupplung` beschreiben die alte Lage und sind in diesem Design ausgeblendet; sie werden von den Prüfungen ausgenommen (siehe [Vorgaben](#vorgaben-an-die-nächsten-baugruppen): Skelett-Korrektur).

## Aufbau in Fusion

- **Ableitungen:** vom Skelett v14 alle Favoriten-Parameter (`*_Ref`), die 8 Bezugsebenen und 37 Hüllkörper (ohne `chassis-grundplatte`); von der Grundplatte v11 die Körper Grundplatte, Oberdeck, Mittelstütze, Akkuanschläge und Fußflächen; von der Hinterachse (v12, Ableitung jetzt auf v13 aktualisiert) die **66 Favoriten-Parameter** (`ha_hz_*`, `ha_e2*`, `ha_lb_*`, `ha_gh_*`, `ha_od_*`, `ha_ql_dx/_y/_fuss_*`, `ha_ma_*` usw., neu markiert, MECH-MAN-012) und alle 26 eigenen Komponenten der Hinterachse (Gehäuse, Lagerbock, Kegelritzelwelle, Querlenker, Böcke, Radträger, Dämpferbrücke, Hüllkörper). Die Grundplatte hat weiterhin keine Favoriten; ihre zwei Schnittstellenmaße des Motorhalter-Lochbilds sind wie bei der Hinterachse als Kopie angelegt (`ma_gp_mh_x`, `ma_gp_mh_dy`, Kommentar „Schnittstelle Grundplatte v11“). Ebenso als Kopie: die Lage der Gehäuse-Verschraubung vorne (`ma_ha_vs_vx`, `ma_ha_vs_vz`, `ma_ha_vs_oz`, `ma_ha_kopf_d`). Sie sind in v13 der Hinterachse als Favoriten markiert; ein erneutes Übernehmen der Parameter (`DeriveFeature.setSourceEntities`) verliert aber die Körperreferenzen der Schnitte an Gehäuse und Lagerbock, deshalb bleiben es bis zur nächsten Überarbeitung Kopien.
- **Komponenten:** je Teil eine Komponente, Druckausrichtung und Material in der Beschreibung.
- **Aufbau der Körper:** wie Skelett und Hinterachse aus voll bestimmten Skizzen im Komponentenursprung (Kreis, Rechteck oder Langloch mittig zum Ursprung), symmetrischer Extrusion und Verschiebung (Move) mit Ausdrücken. Alles, was am Motor hängt, wird zusätzlich um eine Achse durch E2 (`E2-Achse`, Ebene Z = `antrieb_z`) um `ma_winkel` gedreht. Radiale Lage zu E2 heißt im Folgenden **s**, die Richtung quer dazu **v**. Durchbrüche sind Werkzeugkörper, die mit „Kombinieren“ abgezogen werden. Die Abdeckung wird zuletzt mit den abgeleiteten Körpern von Getriebegehäuse und Lagerbock geschnitten (Werkzeuge bleiben erhalten) und an der Ebene Z = `antrieb_z` geteilt.
- **Prüfskripte (Version 4):** 308 Zeitleisten-Elemente ohne Fehler und Warnungen, 72 Skizzen, alle voll bestimmt. 107 Benutzerparameter, alle mit Präfix `ma_` und Kommentar („belegt“, „vorläufig“, „abgeleitet“, „gewählt“, „Prüfmaß“ oder „Schnittstelle“). Feste Zahlen in Features gibt es nur bei den Senkungen (Verjüngung ±45°, aus 90° Senkwinkel ISO 10642).

## Zahnebene und Ritzel (MECH-MAN-002, -003)

| Größe | Wert | Parameter |
|---|---|---|
| Zahnradraum zwischen den E2-Lagern | X −108,0…−103,0 (5,0 mm) | `ha_hz_x0`, `ha_hz_raum` (Hinterachse) |
| Hauptzahnrad GB5 | X −108,0…−103,0 (Breite 5 mm, vorläufig), Kopfkreis Ø 43,2 | `ma_gb5_b`, `ma_gb5_d` |
| Mitnehmer GB3 | X −103,0…−100,0 (3 mm, vorläufig), Ø 14 | `ma_gb3_b`, `ma_gb3_d` |
| **Zahnebene (Mitte GB5)** | **X −105,5** (Skelett: −89,0) | `ma_hz_ebene_x` = `ha_hz_x0 + ma_gb5_b / 2` |
| Fehlbetrag GB3 + GB5 im Zahnradraum | **3,0 mm vorher (`ha_hz_fehl`) und nachher (`ma_hz_fehl`)** | ausgewiesen: GB3 überschneidet Lagerbock (171,5 mm³) und vorderes E2-Lager (226,2 mm³), gewollt, offen bis zur Messung |
| Motorritzel | Hinterkante bündig mit GB5 (X −108,0), Länge 8 mm (vorläufig) bis X −100,0 | `ma_ritzel_x`, `ma_ritzel_l`, `ma_ritzel_versatz` = 0 |
| **Überdeckung Ritzel ↔ GB5** | **5,0 mm = volle Zahnbreite GB5** (mit `ma_gb5_b` = 6: 6,0 mm) | `ma_ueberdeckung` |

Das Ritzel kann nicht weiter nach vorne, ohne die Überdeckung zu verlieren. Die Zahnebene folgt den Hinterachs-Parametern; ändert sich nach dem Messen der Zahnradraum (`ha_hz_x0`), wandern Ritzel, Motor, Halter und Abdeckung mit.

## Motorlage (MECH-MAN-003)

| Kette ab Ritzel-Hinterkante nach vorne | Länge | Parameter |
|---|---|---|
| Motorritzel | 8,0 mm | `ma_ritzel_l` |
| Abstand Ritzel ↔ Halter/Sockel (Zahnräder 3 mm) | 3,0 mm | `abdeckung_abstand` |
| Sockel der Motorplatte = Dicke der Halterwand | 4,0 mm | `ma_platte_d` |
| **Motorflansch** | **X −93,0** (Skelett −75,0) | `ma_flansch_x` |
| Motorwelle 15 mm reicht bis | X −108,0 = Ritzel-Hinterkante | |
| **Wellenreserve** (Definition wie `motor_welle_reserve` im Skelett) | **0,0 mm** (Soll ≥ 0) | `ma_welle_reserve` |
| Welle über die Madenschraube hinaus (Ritzelmitte, M3) | **2,5 mm** (Soll ≥ 0) | `ma_ms_reserve` |

Die Halterwand liegt außerdem mindestens 2 mm vor GB3 (`ma_halter_x0` = max(Ritzel + 3 mm; GB3 + 2 mm)); mit den vorläufigen Maßen bestimmt das Ritzel die Lage.

**Lage der Motorachse:** Der Motor liegt rechts hinten, Achse parallel zu X, Welle nach hinten. Die Achse ist um **`ma_winkel` = 15°** um die E2-Achse nach oben geschwenkt, die Zahnspiel-Einstellung läuft radial in dieser Richtung.

| Ritzel | Achsabstand `ma_a` | Motorachse Y / Z | Motor X | Spalt Motordose ↔ Becher E2 netto |
|---|---|---|---|---|
| 25Z (Startwert) | 28,5 mm | −27,53 / 63,98 | −93,0…−41,0 | **2,5 mm** |
| 20Z | 27,0 mm | −26,08 / 63,59 | −93,0…−41,0 | **1,0 mm** |
| Verstellbereich | 26,5…29,0 mm (`ma_a_min`, `ma_a_max`) | | | (0,5…3,0 mm an den Enden der Reserve) |

**Abweichung vom Skelett (wird nicht geändert, Vorgabe für einen eigenen PR):** Flansch 18 mm weiter hinten (X −93 statt −75), Achse 7,4 mm höher und 15° geschwenkt (Y −27,5 / Z 64,0 statt −28,5 / 56,6), Zahnebene X −105,5 statt −89, Ritzelbereich 20Z–25Z statt 16Z–25Z. Grund für die Schwenkung: Mit der Achse auf Z 56,6 läge die Unterkante der Ritzelabdeckung (Ritzel 25Z, 3 mm Luft, 2 mm Wand) bei Z 43,5 und damit im Bereich des Querlenkerbocks rechts vorne (Y −43…−27, unter Z 48), wo die Abdeckung nicht hinter X −109 reichen darf, das Ritzel aber bis X −108 hinten liegt (3 mm Luft nach hinten wären X −111). Mit 15° liegt die Unterkante der Ritzelabdeckung bei Z 50,4 (kleinstes Ritzel, Verstellung innen); der Motor bleibt unter dem Oberdeck (Oberkante Z 82,0 bei 29 mm Achsabstand, das Oberdeck liegt nur bei |Y| ≤ 10).

## Zahnspiel-Einstellung (MECH-MAN-004)

- **Bauart:** Die Motorplatte hat hinten einen **Sockel** (2·14,0 × 2·13,49 mm, 4 mm dick, Ecken R 1,5), der im **Fenster** der Halterwand gleitet (Spiel 0,3 mm je Seite, `ma_spiel`), und vorne einen **Klemmrand** (R 25,2 um die Motorachse, 3 mm). Der Rand liegt vorne an der Halterwand an und wird mit **3 × M3 × 8 Zylinderkopf von vorne** durch **Langlöcher** in Gewindeeinsätze im Halter geklemmt. Die Langlöcher laufen radial zur E2-Achse (Richtung s), die Einsätze sitzen für die Mitte des Verstellbereichs (`ma_a_mid` 27,75 mm) bei 22 mm um ±80° und 24 mm außen.
- **Verstellweg:** Achsabstand **26,5…29,0 mm**, also 20Z (27,0) − 0,5 mm bis 25Z (28,5) + 0,5 mm (`ma_a_min`, `ma_a_max`, Langlöcher 2 × 1,25 mm). Gemessen im Modell: Ritzel 20Z ↔ Motorachse Achsabstand 27,00 mm, 25Z 28,50 mm (= `zahn_modul · (70 + z) / 2`); an den Enden (Parameter auf 26,5 bzw. 29,0 gesetzt) Zeitleiste ohne Fehler, keine neue Überschneidung, Motorplatte ↔ Becher-Hülle 1,00 mm.
- **Interferenz Ritzel ↔ GB5:** nur der Zahneingriff (Kopfkreise überschneiden sich, 25Z 29,7 mm³, 20Z 27,4 mm³), sonst nichts.
- **Erreichbarkeit:** Die drei Klemmschrauben sitzen vorne auf dem Rand neben dem Motor und sind mit einem Inbus 2,5 mm von vorne erreichbar (oben über dem Motor, außen rechts, unten unter dem Motor über dem Fuß). Halter und Abdeckung bleiben dabei montiert. Die beiden Motorschrauben (Motor an Motorplatte, Senkkopf im Sockel) liegen auf der Zahnradseite; sie werden auf der Werkbank angezogen und sind erreichbar, sobald der Motor mit der Platte nach vorne herausgezogen ist (siehe Ritzelwechsel). Das Motorlochbild ist um 45° zur Verstellrichtung gedreht (`ma_motor_loch_w`), damit die Senkungen in den schmalen Sockel passen.

![Schnitt durch die Becherhaube, Ritzel 20Z](images/mittelantrieb-ritzel-20z.png)

*Schnitt bei X −86 (Becherhaube), Blick von vorne, Ritzel 20Z (Achsabstand 27,0 mm). Orange schraffiert: Motordose, grün schraffiert: Becherhaube der Motorplatte, rot: Becher von E2, grau: Hülle der Kardanwelle (Skelett). Die Motordose schließt die Haube zum Becher hin (Spalt netto 1,0 mm).*

![Schnitt durch die Becherhaube, Ritzel 25Z](images/mittelantrieb-ritzel-25z.png)

*Wie oben mit Ritzel 25Z (Achsabstand 28,5 mm, Spalt netto 2,5 mm). Motorplatte, Haube und Motor wandern mit, Halter und Abdeckung bleiben gleich.*

## Schutz vor drehenden Teilen und Zahnradabdeckung (MECH-MAN-006, -007, -019)

![Schnitt in der Zahnebene](images/mittelantrieb-schnitt-zahnebene.png)

*Schnitt in der Zahnebene X −105,5, Blick von vorne (rechts im Fahrzeug ist links im Bild), Ritzel 25Z. Violett: GB5, weiß: Ritzel mit Motorwelle, weiß schraffiert: Zahnradabdeckung (Ober- und Unterteile, rechts die Ritzelabdeckung mit den Laschen), gelb: Lagerbock-Fuß, Getriebegehäuse und Grundplatte, oben das Oberdeck.*

**Aufbau der Umschließung:**
- **Zahnradabdeckung:** Hohlraum r 24,6 um GB5 (3 mm Luft zum Kopfkreis), Langloch r 11,1 um das Ritzel über den ganzen Verstellbereich (3 mm Luft zum Kopfkreis 25Z) und vorne der Bereich des Fensters; Wand 2 mm; Rückwand X −113…−111. Hinten ist die Abdeckung auf die Kontur von Getriebegehäuse und Lagerbock geschnitten (Anlage ohne Spalt). Die **Öffnung für den Lagerhals** ist damit die Kontur der Gehäusetrommel (Ø 47); der Lagerhals (Ø 15,1) liegt im Innenraum. Unten bilden Lagerbock-Fuß und Gehäusefuß den Boden.
- **Motorhalter** = Vorderwand: Fenster für den Sockel, Durchgang r 11 um den Becher, Durchgänge Ø 7,5 für die Köpfe der Lagerbock-Schrauben, Bodenleiste vor dem Lagerbock (liegt am Lagerbock an).
- **Motorplatte:** Der Sockel füllt das Fenster, der Klemmrand deckt die Restspalte des Fensters in jeder Stellung ab (kleinster Überstand 3,5 mm). Die **Becherhaube** (Ring r 12,25…15,25 um den Becher, Stirnwand 3 mm vor dem Becher, X −93…−79) umschließt den Becher von E2 oben, links und unten; rechts ist die **Motordose die Wand**. Die Haube hängt an der Motorplatte und bewegt sich mit dem Motor: Die **Fuge zur Motordose ist in jeder Stellung 0,5 mm** (`ma_dose_fuge`, Soll ≤ 1 mm), und zum Becher bleibt in jeder Stellung ≥ 1 mm zur Hülle (netto ≥ 3 mm). Eine Haube an der feststehenden Abdeckung hätte bei der Verstellung eine Fuge bis 3 mm.
- **Blinddeckel** in der E1-Öffnung (r 9,25) der Stirnwand, Presssitz mit Flansch.

**Prüfung „geschlossen“ (Prüfskript, Version 4):** Luftraum in einem Quader X −116…−76, Y −58…37, Z 29…90 minus Abdeckung, Halter, Motorplatte, Blinddeckel, Getriebegehäuse, Lagerbock, E2 mit Lagern und Motor. Die Fugen, die als Spalt gewollt sind (Motordose 0,5 mm, Köpfe der Lagerbock-Schrauben im Durchgang 1,0 mm, Lagersitz-Spiel 0,05 mm der Hinterachse), und die beiden Schrauben der Gehäuse-Verschraubung vorne werden dafür gefüllt. Ergebnis: Der Raum um GB5, Ritzel und Becher ist **ein eigener, abgeschlossener Luftkörper** (36,5 cm³, X −111…−82) ohne Verbindung zur Umgebung. Daraus folgt: Offen sind nur
- die Fuge Motordose ↔ Motorplatte/Haube **0,5 mm**,
- der Ringspalt um die Köpfe der Lagerbock-Schrauben **1,0 mm** (Durchgang Ø 7,5, Kopf Ø 5,5),
- die Gleitfuge Sockel ↔ Fenster **0,3 mm** (vom Klemmrand überdeckt, kein Durchgang nach außen).

Kein Spalt zu drehenden Teilen ist größer als 2 mm; ein Prüfdorn Ø 6 kommt nirgends hinein. Keine Lüftungsöffnungen zu den Zahnrädern. Die Fugen zwischen Abdeckung, Halter, Gehäuse und Lagerbock sind Anlageflächen (0 mm), an der Gehäusetrommel laufen die geschnittenen Kanten der Rückwand teils spitz aus (Restspalt nach dem Druck < 0,5 mm). MECH-MAN-019 (Fugen ≤ 0,5 mm) ist damit bis auf den Ringspalt an den Lagerbock-Schrauben (1,0 mm) erfüllt.

**Abstände zu drehenden Teilen (gemessen, `measureMinimumDistance`):**

| Paar | 25Z | 20Z | Soll |
|---|---|---|---|
| Abdeckung ↔ GB5 | 3,00 | 3,00 | ≥ 3 |
| Abdeckung ↔ Ritzel | 3,00 | 3,00 | ≥ 3 |
| Motorplatte ↔ Ritzel | 3,00 | 3,00 | ≥ 3 |
| Halter ↔ GB5 / GB3 | 3,57 / 5,00 | 3,57 / 5,00 | ≥ 3 / ≥ 2 |
| Motorplatte ↔ GB5 | 6,00 | 6,00 | ≥ 3 |
| Abdeckung ↔ Motorwelle | 3,00 | 3,00 | ≥ 2 |
| Getriebegehäuse ↔ Ritzel (nach Freischnitt) | 2,00 | 2,00 | ≥ 2 (MECH-MAN-008) |
| Halter ↔ Becher (Hülle / netto) | 1,00 / 3,00 | 1,00 / 3,00 | netto ≥ 2 |
| Motorplatte/Haube ↔ Becher (Hülle / netto) | 1,50 / 3,50 (Enden des Verstellbereichs 1,00 / 3,00) | 1,50 / 3,50 | netto ≥ 2 |
| Stirnwand Haube ↔ Becher-Stirnseite | 2,00 | 2,00 | ≥ 2 |
| **Motordose ↔ Becher E2 netto** | **2,50** | **1,00** | ≥ 1,0 (Ausnahme MECH-MAN-006) |

**Weitere Prüfungen MECH-MAN-007:** Interferenz Abdeckung ↔ alle Körper 0 (nur Anlage an Gehäuse, Lagerbock, Halter und zwischen den Teilen). Unterkante Oberdeck: Abdeckung **1,00 mm**, Halter **1,00 mm**, Motorplatte 3,57 mm. **Querlenkerbock rechts vorne:** Abdeckung, Halter und Motorplatte haben im Bereich X < −109, Y −43…−27, Z < 48 kein Volumen (Prüfskript: Schnittkörper 0 mm³); Abstand Abdeckung ↔ Bock 1,64 mm (links 1,52 mm).

## Interferenz und Abstände (MECH-MAN-005, -008, -009)

Fusion `analyzeInterference` über alle Körper im Bereich X −130…−20 ohne `grundplatte-alu`, ohne die Skelett-Hüllen, die Hinterachse und Mittelantrieb ersetzen (`mittelantrieb-motor`, `-motorritzel`, `-zahnradabdeckung`, `-rutschkupplung`, `antrieb-getriebe-hinten`, Dämpfer, Räder, Radachsen, Antriebswellen, Rad- und Wellenräume hinten) und ohne die Hüllen `hinterachse-hauptzahnrad` (ersetzt durch GB5/GB3). Ergebnis mit 25Z, 20Z und an beiden Enden des Verstellbereichs: **0 ungewollte Überschneidungen.** Gewollt (mit Teilen des Mittelantriebs):

| Überschneidung | 25Z | 20Z | Begründung |
|---|---|---|---|
| Blinddeckel ↔ Hülle Kardanwelle | 692,7 mm³ | 692,7 mm³ | verschließbare E1-Öffnung (MECH-MAN-009) |
| GB3 ↔ Lagerbock / vorderes E2-Lager | 171,5 / 226,2 mm³ | gleich | Fehlbetrag Zahnradraum 3,0 mm, offen bis Messung |
| GB5, GB3 ↔ Kegelritzelwelle | 98,2 / 58,9 mm³ | gleich | sitzen auf E2 |
| GB5 ↔ Ritzel | 29,7 mm³ | 27,4 mm³ | Zahneingriff |
| Motor ↔ Ritzel | 63,3 mm³ | 63,3 mm³ | Welle im Ritzel |
| Motor ↔ Hülle Kardanwelle (Becher) | – (0,50 mm Abstand) | 42,7 mm³ | Hülle mit Zuschlag, netto 1,0 mm (Ausnahme MECH-MAN-006/-008) |

**Kleinste Abstände** (25Z / 20Z, mm; Soll ≥ 1, zu bewegten Teilen ≥ 2):

| Teil | Getriebegehäuse | Lagerbock | Querlenkerbock r. v. | Querlenker (3 Stellungen) | Antriebswelle / Wellenraum | Oberdeck | Mittelstütze | Regler | Empfänger | Akku / Entnahmeweg | Grundplatte |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Motorhalter | > 9 | Anlage Bodenleiste | 9,5 | 20,0 | 26,5 / 26,0 | 1,00 | 50,5 | 44,5 | **2,00** | 24,0 | Fuß steht auf |
| Motorplatte | > 9 | 6,3 / 5,0 | 13,5 | 24,9 | 29,0 | 3,57 | 64,4 | 60,5 | 16,4 | 10,0 | 9,8 / 9,4 |
| Abdeckung (3 Teile) | Anlage | Anlage | **1,64** | 11,3 | 13,0 | **1,00** | > 82 | ≥ 76 | ≥ 24,6 | ≥ 28 | 5,6 |
| Motor | 4,4 / 3,2 (Welle) | 6,8 / 6,5 | 15,7 | 23,6 | 19,1 / 19,0 | 8,8 / 8,1 | 27,5 | 20,0 | 10,6 / 11,4 | 22,8 / 21,5 | 17,0 |
| Ritzel | 2,00 | 11,8 | 9,2 / 10,8 | 18,4 | 18,0 | 18,7 | 87 | 79 | 33 | 45 | 26,9 |
| Blinddeckel | – | 17,5 | 35 | 46 | 49 | 16,2 | 63 | 60 | 38 | 8,7 / 8,6 | 16,5 |

- **Federweg (drei Stellungen `ha_dphi_aus`, 0, `ha_dphi_ein`):** Die bewegten Teile der Hinterachse (Querlenker, Radträger, Antriebswellen, Radachsen, Räder, Sturzstangen, Dämpfer) wurden in der Hinterachse in jede Stellung gebracht, als Kopie übernommen und gegen alle Teile des Mittelantriebs gemessen: keine Überschneidung, kleinster Abstand in allen drei Stellungen **11,33 mm** (Abdeckung unten rechts ↔ Querlenker rechts am Drehpunkt). Die Hinterachse wurde danach ohne Speichern zurückgesetzt.
- **Kardanwellen-Bauraum (MECH-MAN-008/-009):** Halter 1,00 mm und Motorplatte 1,50 mm (an den Enden 1,00 mm) zur Hülle, Abdeckung ≥ 12,3 mm. Der Motor ragt mit 20Z um 1,0 mm in die Becher-Hülle (Zuschlag 2 mm); eine 4WD-Kardanwelle mit netto Ø 16 (wie der Becher) hätte dann netto **1,0 mm** zur Motordose, mit 25Z 2,5 mm. `kardan_spiel` bleibt 0,00 mm (Becheröffnung X −84, Skelett unverändert).
- **Elektronik:** Empfänger (Skelett-Hülle) 2,00 mm zum Fuß des Halters, Regler ≥ 20 mm zum Motor. Die Halter folgen mit „Elektronikhalter“.

## Lasten (MECH-MAN-010)

Annahmen aus dem Anforderungsdokument: Motor 223 g mit 5 g Stoß in jeder Richtung = **10,9 N**; Motorspitzenmoment 60 A × kT, kT = 1 / (3250 · 2π/60) = 2,94 mN·m/A → **0,176 N·m**. Zahnkraft am Ritzel (Teilkreis r = 0,6 · z / 2): 25Z (r 7,5 mm) **23,5 N** tangential, 20Z (r 6,0 mm) **29,4 N** (ungünstigster Fall), radial je × tan 20° = 10,7 N (20Z). Resultierende 20Z: 31,3 N. Werkstoff Prusament PC, Zugfestigkeit ca. 60 MPa (in Schichtrichtung), E ≈ 2,3 GPa.

| Stelle | Last | Moment / Kraft | Querschnitt | σ | Sicherheit PC |
|---|---|---|---|---|---|
| Halterwand am Fuß, quer zur Wand (Stoß in X am Motorschwerpunkt, 27,5 mm über dem Fuß) | 10,9 N | 300 N·mm | 4 × 33 mm, W 88 mm³ | 3,4 MPa | 17,6 (mit Kerbfaktor 2: 8,8) |
| Halterwand am Fuß, Stoß senkrecht (Hebel Motorschwerpunkt 26 mm vor der Wand) | 10,9 N | 283 N·mm | wie oben | 3,2 MPa | 18,8 (Kerbe: 9,4) |
| Halterwand in ihrer Ebene (Zahnkraft 20Z + Stoß) | 42,2 N × 27,5 mm | 1161 N·mm | 4 × 60 mm, W 2400 mm³ | 0,5 MPa | > 100 |
| Klemmung Motorplatte (3 × M3 in Einsätzen, Vorspannung angenommen 300 N je Schraube, μ 0,3) | 42,2 N | Reibkraft 270 N; Moment 5,9 N·m gegen 0,18 N·m | | | 6,4 (Rutschen) |
| Motorschrauben (2 × M3 Senkkopf) | Stoßmoment 283 N·mm / 25 mm | 11 N je Schraube | | | unkritisch |
| Klemmrand an den Langlöchern | 10,9 N, Hebel 22 mm | 240 N·mm | Rand 3 × ca. 15 mm, W 22,5 mm³ | 10,7 MPa | 5,6 (Kerbe: 2,8) |

- **Kleinste Sicherheit 2,8 (Klemmrand mit Kerbfaktor 2)** ≥ 2 gefordert und höher als der Querlenker der Hinterachse (Sollbruchstelle, Sicherheit 3,3 in PETG bzw. 4,3 in PC ohne Kerbfaktor, mit Kerbfaktor 2: 2,2). Bei Überlast bricht also zuerst der Querlenker.
- **Zahneingriff unter Last (≤ 0,1 mm am Ritzel):** Motorwelle Ø 3,175 als Kragarm vom Flansch bis Ritzelmitte (11 mm): δ = F·L³ / (3·E·I) = 31,3 · 1331 / (3 · 210 000 · 4,99) = **0,013 mm**. Halterwand in ihrer Ebene: δ ≈ 42,2 · 27,5³ / (3 · 2300 · 72 000) = **0,002 mm**. Klemmung rutscht nicht (siehe oben). Summe ca. **0,02 mm** ≤ 0,1 mm. Kriechen von PC unter der Klemmkraft: Klemmschrauben nach der ersten Fahrt nachziehen (🔧).
- **Schwächstes Glied ohne Rutschkupplung:** Das Moment an E2 begrenzt nur die Haftung der Räder (0,19 N·m, mit Stoß 0,56 N·m, `docs/hinterachse.md`). Lastspitzen beim harten Anfahren und Landen mit Gas gehen ungedämpft über Ritzel, GB5 (Kunststoff) und die Kegelräder des Diffs. Das schwächste Glied sind die **Zähne von GB5 bzw. der Kegelräder**, nicht die Druckteile. Schonung über die Reglereinstellung (siehe [Reglereinstellungen](#reglereinstellungen-ohne-rutschkupplung-mech-man-017)). 🔧 Tischtest und erste Fahrt.

## Wärme (MECH-MAN-011)

- Motorhalter und Motorplatte (Kontakt zum Motor) in **Prusament PC** (Tg ca. 110 °C), auch die Becherhaube ist Teil der Motorplatte. Kein PETG-Teil berührt den Motor im fertigen Modell; der Blinddeckel (PETG oder PC) hat 0,5 mm Luft zur Motordose. Material je Teil in `bom/stueckliste.csv` (Pos. 49, 50, 65, 66).
- **Anteil der Mantelfläche innerhalb der Abdeckung:** Die Becherhaube liegt auf 14 mm der 52 mm Motorlänge (27 %) an einem Bogen von ca. 61° der Dose (17 % des Umfangs, Becherseite) → **4,6 %**. Der Klemmrand umgibt die hinteren 3 mm mit 0,5 mm Luft (5,8 %). Zusammen **ca. 10 %** (Richtwert ≤ 30 %). Der Rest der Dose ist frei angeströmt; der Flansch liegt am Sockel bzw. an der Halterwand an (Wärme geht in den Halter).
- 🔧 Motortemperatur nach Tischtest und erster Fahrt ≤ 80 °C (Infrarot-Thermometer).

## Fräsbarkeit Motorhalter (MECH-MAN-005)

Prüfskript (Version 4): alle Flächen sind Ebenen senkrecht zu X, Y oder Z bzw. parallel zu X (Fensterflanken, schräg um 15°, in X durchgehend), Zylinder mit Achse in X (21) oder Z (3), Kegel in X (Senkungen). Kleinster Innenradius **1,5 mm** (Fensterecken, Ecke des Oberdeck-Freiraums), Einsätze R 2. Konkave Kanten ohne Radius (5) liegen nur dort, wo sie quer zur Werkzeugachse der jeweiligen Seite liegen: Fuß ↔ Wand (Kante in Y, von oben) und Bodenleiste ↔ Wand-Rückseite (Kanten in Y und Z, von hinten). **2,5D in drei Aufspannungen:** Vorderseite in X (Fenster, Durchgänge, Einsätze, Senkungen), Rückseite in X (Augen, Bodenleiste), Unterseite in Z (Fuß, Lochbild). Keine Hinterschnitte. Abweichung von „einer Aufspannung“: Der Fuß steht senkrecht zur Wand, das ist bei einem Winkelhalter nicht vermeidbar.

## Druckhinweise (MECH-MAN-013)

| Teil | Lage auf dem Bett | Stützen | Hinweis |
|---|---|---|---|
| Motorhalter | Unterseite des Fußes (Z 29) | keine; Fenster (Brücke ca. 31 mm) und Durchgänge als Brücke bzw. Bogen | Die Halterwand steht senkrecht; die Biegelasten aus dem Motor liegen in der Schichtebene der Wand bzw. am Übergang zum Fuß. Erst nach dem Messen drucken. |
| Motorplatte | Rückseite des Sockels (X −97) | **ja, unter dem Klemmrand** (4 mm hoch, Rand steht über den Sockel) | Die Stirnwand der Becherhaube wird als Decke über den Tunnel gedruckt (Brücke ca. 25 mm, ggf. Stützen im Tunnel). Erst nach dem Messen drucken. |
| Zahnradabdeckung oben, unten links, unten rechts | Rückwand (X −113) | wenig: unter dem Absatz des Fensterbereichs (X −109) | Die Teile sind in X extrudiert; die spitz auslaufenden Kanten an der Gehäusetrommel lässt der Slicer teils weg (Restspalt < 0,5 mm). |
| Blinddeckel | Flansch | keine | Presssitz per Probedruck einstellen. |

- **Bauraum:** größtes Teil Abdeckung oben 87,5 × 27 × 16 mm, alle ≤ 256 mm.
- **Wandstärken:** Abdeckung 2,0 mm (`abdeckung_wand`), Becherhaube 3,0 mm radial und 3,0 mm Stirnwand, Klemmrand 3,0 mm, Sockel und Halterwand 4,0 mm, Fuß 7,5 mm. Um die Gewindeeinsätze 1,5 mm (`ma_einsatz_wand`, Augen Ø 7), zwischen Langloch und Randkontur ≥ 1,35 mm, Steg zwischen Fenster und Becher-Durchgang im Halter 1,2 mm (`ma_wand_min`). Alle Werte aus den Parametern; Ausnahme sind die spitz auslaufenden Ränder der Abdeckung an der Gehäusetrommel (Anlagekanten, nicht tragend).
- **Toleranzen:** Bohrungen M3 Ø 3,2 (+0,2), Gewindeeinsätze wie Pos. 30 (Ø 4 × 6, vorläufig), Gleitspiel Sockel 0,3 mm je Seite, Fuge zur Motordose 0,5 mm.
- 🔧 Slicer-Prüfung durch den Nutzer.

## Montagefolge und Ritzelwechsel (MECH-MAN-007, -018)

**Erstmontage:**
1. Gewindeeinsätze einschmelzen: Halter 6 (Fuß 3 von unten, Klemmung 3 von vorne), Abdeckung unten links und rechts je 2 (Auge vorne, Lasche oben).
2. Hinterachse mit E2, GB3 und GB5 nach `docs/hinterachse.md` montieren und auf die Grundplatte schrauben (Lagerbock mit 2 × M3 × 14 von vorne).
3. **Unterteile der Abdeckung von vorne** nach hinten einschieben (links alternativ von links, rechts von rechts), bis sie an Gehäuse und Lagerbock anliegen; **Oberteil von oben** aufsetzen und mit 2 × M3 × 10 Zylinderkopf an den Laschen mit den Unterteilen verschrauben. Das Oberdeck ist dabei noch nicht montiert. Geprüft per Skript: Jedes Teil wurde in Schritten bis 45 mm aus seiner Endlage verschoben (Unterteile in +X, Oberteil in +Z) – keine Überschneidung mit Gehäuse, Lagerbock, GB5, GB3, E2 und Lagern. Dafür ist die Abdeckung aus den Bohrungen der Gehäuse-Verschraubung vorne (M3 × 25 bei X −112 / Z 41, M3 × 14 bei X −115 / Z 74) herausgenommen (Zylinder Ø 6 = `ha_kopf_d`); in Version 3 hatte sie dort Zungen, die das Teil im Gehäuse verriegelt hätten.
4. **Motorhalter** von vorne über den Becher von E2 schieben (Ring r 11 um den Becher), Fuß mit 3 × M3 × 8 Senkkopf von unten an die Grundplatte schrauben, Unterteile der Abdeckung mit 2 × M3 × 10 Senkkopf von vorne durch den Halter anschrauben.
5. Oberdeck montieren.
6. Motor auf der Werkbank mit 2 × M3 × 6 Senkkopf an die Motorplatte schrauben, Ritzel aufstecken (Hinterkante bündig mit dem Wellenende), Madenschraube anziehen. Blinddeckel in die Becherhaube drücken.
7. Motor mit Platte von vorne einsetzen: Sockel ins Fenster, Becherhaube über den Becher. Zahnspiel einstellen (Papierstreifen-Methode), 3 Klemmschrauben M3 × 8 von vorne anziehen.

**Ritzelwechsel** (ohne Oberdeck, Halter oder Abdeckung abzubauen):
1. Akku abstecken. 3 Klemmschrauben von vorne herausdrehen.
2. Motor mit Motorplatte ca. 15 mm nach vorne ziehen, bis das Ritzel aus dem Fenster ist (der Motor kommt dabei bis X −26, 5 mm vor die Regler-Hülle; Motorkabel genug Länge lassen).
3. Madenschraube lösen, Ritzel nach hinten von der Welle ziehen, neues Ritzel aufsetzen (Hinterkante bündig mit dem Wellenende), Madenschraube anziehen.
4. Motor zurückschieben, Zahnspiel einstellen, Klemmschrauben anziehen. Bei einem Wechsel der Zähnezahl innerhalb 20Z–25Z bleiben alle Druckteile gleich; nur der Achsabstand ändert sich.

**Wartung:** Der Motorhalter lässt sich ohne Getriebegehäuse und Oberdeck abbauen: Motor herausziehen (wie oben), 2 Schrauben Abdeckung ↔ Halter von vorne und 3 Schrauben von unten lösen, Halter nach vorne abziehen. Die Abdeckung hängt dann nur an Gehäuse und Lagerbock; zum Abnehmen des Oberteils muss das Oberdeck ab. Für die Lagerbock-Schrauben (Inbus 2,5 von vorne durch die Durchgänge im Halter): links gerader Zugang; rechts verdeckt der Fuß des Halters den geraden Weg um 0,75 mm (Einsatz des Lochbilds bei Y −16,5), dort einen Kugelkopf-Inbus leicht schräg ansetzen.

## Änderungen an der Hinterachse (MECH-MAN-012)

Neue Versionen **open-rc-car-hinterachse v12** (Freischnitt, Favoriten) und **v13** (weitere Favoriten, Geometrie wie v12). Exporte aus Version 13: `cad/fusion/hinterachse.f3d`, `cad/step/hinterachse.step` (11 Komponenten, 12 Körper) und alle 12 STL; geändert ist nur `print/stl/hinterachse-getriebegehaeuse-rechts.stl`, die übrigen 11 STL sind bytegleich mit Version 11.

| Änderung | Umfang |
|---|---|
| **Freischnitt für das Ritzel** an der Gehäusetrommel rechts | Langloch r 10,1 (Kopfkreis 25Z + 2 mm) um den Verstellbereich des Ritzels, X −110,0…−106,0; entfernt 11,85 mm³ aus `getriebegehaeuse-rechts`. Ritzel ↔ Gehäuse vorher 1,5 mm, jetzt **2,00 mm** (20Z und 25Z). Neue Parameter `ha_ma_winkel`, `ha_ma_a_min`, `ha_ma_a_max`, `ha_ma_ritzel_r` (Kopien der Mittelantriebs-Werte, Kommentar „Schnittstelle Mittelantrieb, von Hand nachziehen“; im Mittelantrieb prüfen `ma_schnitt_pruef` = 0 und `ma_schnitt_pruef_w` = 0, dass sie übereinstimmen), `ha_ma_fs_luft` = 2 mm, `ha_ma_fs_x`. |
| **Favoriten** | Version 12: 66 Schnittstellenparameter (`ha_hz_*`, `ha_e2*`, `ha_lb_*`, `ha_gh_*`, `ha_od_*`, `ha_ql_dx`, `ha_ql_y`, `ha_ql_fuss_*`, `ha_bohrung`, `ha_einsatz_*`, `ha_lager_spiel`, `ha_zahn_luft`, `ha_hals_l`, `ha_rk_luft`, `ha_ma_*`), damit der Mittelantrieb sie ableitet. Version 13: zusätzlich die Verschraubung vorne (`ha_vs_vx`, `ha_vs_vz`, `ha_vs_oz`, `ha_kopf_d`, `ha_vs_senk`, `ha_vs_senk_post`); Geometrie wie Version 12. |

Keine Änderung an Lagerung, Zahneingriff Tellerrad/Kegelritzel, Lagerbock oder Aufhängung. **Neu geprüft (Prüfskript der Hinterachse, Version 12, gleiche Geometrie wie 13):** Interferenz in den drei Stellungen `ha_dphi_aus`, 0, `ha_dphi_ein` – jeweils dieselben 56 Paare mit denselben Volumen wie Version 11, **keine neue Überschneidung, keine weggefallene**; Zeitleiste 626 Elemente ohne Fehler. Der Freischnitt liegt bei X ≥ −110 und damit mindestens 23 mm von der Diff-Achse; die Wand zum Zahnraum (r 21) bleibt **≥ 2,0 mm**, der Zahnraum bleibt geschlossen (MECH-HAC-004). Lochbilder (MECH-HAC-003), Druckausrichtung und Bauraum (MECH-HAC-015) unverändert; Exporte aus einer Version (MECH-HAC-018). Nachgezogen in `docs/hinterachse.md` und `docs/anforderungen/hinterachse.md`.

## Parametertest (MECH-MAN-001)

| Test | Ergebnis |
|---|---|
| `ma_ritzel_zaehne` 25 → 20 | Zeitleiste ohne Fehler. Ritzel, Motor, Motorplatte und Blinddeckel wandern auf 27,0 mm Achsabstand; Halter und Abdeckung bleiben (Bild oben). Interferenz: dieselben gewollten Paare plus Motor ↔ Kardan-Hülle (42,7 mm³, netto 1,0 mm). |
| `ma_ritzel_zaehne` → 18,33 und 26,67 (Enden des Verstellbereichs 26,5 / 29,0 mm) | Zeitleiste ohne Fehler, keine ungewollte Überschneidung, Motorplatte ↔ Becher-Hülle 1,00 mm. |
| `ma_gb5_b` 5 → 6 mm (Bausatzmaß +1 mm) | Zeitleiste ohne Fehler; Zahnebene X −105,0, GB3 wandert auf X −102…−99, Überdeckung 6,0 mm, `ma_hz_fehl` 4,0 mm. Die Halterwand bleibt bei X −97, weil sie jetzt genau 2 mm vor GB3 liegt (`ma_halter_x0` = max(…)). Zurückgesetzt. |
| alle Tests zurückgesetzt | 25Z, `ma_gb5_b` 5 mm, Zeitleiste ohne Fehler, als Version 3 bzw. 4 gespeichert. |

## Prüfanleitung Tischtest (MECH-MAN-016)

**Ziel:** Das Heck lässt sich auf dem Tisch antreiben; der Failsafe stoppt den Motor.

**Vorbereitung (vor dem ersten Anschließen des Akkus):**
1. Mechanik: Hinterachse, Mittelantrieb und Zahnradabdeckung **vollständig montiert**, Blinddeckel eingesetzt. Zahnspiel eingestellt, Ritzel dreht von Hand mit den Rädern ohne Klemmen.
2. **Heck aufbocken**, beide Hinterräder frei in der Luft, Fahrzeug gegen Wegrutschen sichern. Hände, Kabel und Werkzeug von Rädern und Antriebswellen fernhalten.
3. Elektronik provisorisch mit Klettband: Regler WP10BL60 G2, Empfänger HR7E, UBEC auf 6,0 V. **Rote Ader des Regler-Steuerkabels abziehen** (UBEC versorgt Empfänger und Servo, Entscheidung 2026-10-27).
4. Regler einstellen (Hobbywing-Anleitung): Akkutyp LiPo, **Unterspannung 3,4 V/Zelle**, Einstellungen gegen Lastspitzen nach [Reglereinstellungen](#reglereinstellungen-ohne-rutschkupplung-mech-man-017).
5. Sender und Empfänger binden (ELRS, Regulatory Domain EU_CE_2400). **Failsafe Kanal 1 (Lenkung) und Kanal 2 (Gas) = 1500 µs** einstellen (Entscheidung 2026-10-26) und ohne Motor prüfen: Sender aus → Servo geht in die Mitte.
6. Regler auf den Sender einmessen (Neutral, Vollgas, Vollbremse) nach Hobbywing-Anleitung.
7. Akku 2S in der LiPo-Schutztasche bereitlegen, Feuerlöschmittel bzw. Sand in Reichweite.

**Ablauf:**
1. Sender einschalten, Gas auf neutral. Akku anstecken, Regler einschalten. Prüfen: Motor steht.
2. Gas **langsam** erhöhen bis ca. 20 %, dann bis ca. 50 %; Drehrichtung prüfen (vorwärts), auf Geräusche (Zahneingriff, Schleifen an der Abdeckung) und Vibrationen achten. Rückwärts und Bremse kurz prüfen.
3. **Failsafe:** Bei ca. 30 % Gas den **Sender ausschalten** → Motor muss **≤ 1 s** stoppen (Stoppuhr bzw. Video mitlaufen lassen), Lenkung geht in die Mitte.
4. Sender wieder einschalten, Gas neutral, Regler aus.
5. **Akku sofort abstecken** (der Reglerschalter schaltet Empfänger und Servo nicht ab).
6. Nach dem Test: Motor- und Haltertemperatur messen (Infrarot-Thermometer, ≤ 80 °C), Klemmschrauben und Madenschraube nachziehen, Zahnspiel prüfen.

**Abnahme:** Motor steht ≤ 1 s nach Abschalten des Senders, Lenkung neutral; Zahnräder laufen ohne Klemmen und ohne Überspringen; keine Berührung zwischen drehenden Teilen und Abdeckung (Schleifspuren prüfen).

### Tischtest (vom Nutzer auszufüllen)

| Datum | Ritzel | Failsafe: Motor steht nach … s | Lenkung neutral | Zahnräder (Klemmen / Überspringen / Geräusch) | Motortemperatur | Bemerkung |
|---|---|---|---|---|---|---|
| | | | | | | |

## Reglereinstellungen ohne Rutschkupplung (MECH-MAN-017)

Ohne Rutschkupplung schützt nur der Regler den Antrieb vor Lastspitzen. Empfehlung für den Start (Bezeichnungen und Stufen laut Anleitung des Hobbywing QuicRun WP10BL60 G2 prüfen, Einstellung per Programmierkarte oder Tastenfolge):
- **Punch / Anfahrkraft:** niedrig (unterste bis zweite Stufe); erst nach der Erprobung erhöhen.
- **Maximale Bremskraft:** begrenzt, ca. 50 %; **Schleppbremse (Drag Brake):** 0 %.
- **Rückwärts:** auf ca. 50 % begrenzen, Modus „Vorwärts/Bremse/Rückwärts“ mit Verzögerung.
- **Unterspannung:** 3,4 V/Zelle (Pflicht, LiPo-Schutz).
- Fahrweise: nicht mit Vollgas landen, kein Vollgas aus dem Stand auf griffigem Untergrund.

## Messpunkte bei Lieferung

Danach Parameter ersetzen, Prüfskripte (Interferenz, Abstände, „geschlossen“) wiederholen, erst dann drucken:
1. **GB5 und GB3** (mit E2, Hinterachse Messpunkt 2): Zahnbreite und Lage von GB5 (`ma_gb5_b`), Breite und Durchmesser von GB3 (`ma_gb3_b`, `ma_gb3_d`), Reihenfolge auf E2. Davon hängen Zahnebene, `ma_hz_fehl` und die Lage der Halterwand ab.
2. **Motorritzel 24Z/25Z (Pos. 13):** Länge, Zahnbreite, Bund (vorne oder hinten), Lage und Gewinde der Madenschraube (`ma_ritzel_l`, `ma_ritzel_ms`, `ma_ms_d`); ggf. `ma_ritzel_versatz` anpassen, damit das Ritzel GB5 voll überdeckt und `ma_welle_reserve` ≥ 0 bleibt.
3. **Motor 3652SL G2:** Wellenlänge (15 mm laut Datenblatt), Lochbild (`ma_motor_loch_a`, Annahme 25 mm), Gewindetiefe im Flansch (Schraubenlänge M3 × 6), Lagerbund am Flansch (`ma_motor_bund_d`, Annahme Ø 13), Kabelabgang.
4. **Becher von E2:** Durchmesser (Annahme Ø 16 netto, `kardan_becher_d` − 2 · Zuschlag); davon hängt der Spalt Motordose ↔ Becher ab (`ma_spalt_becher_min` = 1,0 mm bei 20Z). Das kleinste zulässige Ritzel (20Z) wird damit bestätigt oder angepasst.
5. **Gewindeeinsätze M3 kurz:** Bohrung und Länge (`ha_einsatz_d`, `ha_einsatz_t`, wirken auch hier).
6. **Probedruck:** Gleitspiel Sockel/Fenster (`ma_spiel`), Presssitz Blinddeckel.

## 4WD und Parametrik (MECH-MAN-021, KANN)

Für 4WD wird nur der **Blinddeckel weggelassen**: Die Öffnung in der Stirnwand der Becherhaube (r 9,25) lässt die Hülle der Kardanwelle (r 7) in jeder Stellung mit ≥ 1 mm frei. Halter, Abdeckung und Motorplatte bleiben unverändert. Zu beachten: Mit 20Z hat eine Kardanwelle E1 mit netto Ø 16 nur 1,0 mm zur Motordose; für 4WD sind 22Z–25Z vorzuziehen.

## Vorgaben an die nächsten Baugruppen

- **Elektronikhalter:** Der Fuß des Motorhalters belegt X −97…−65,5, Y −46…−13 (Z bis 36,5); die Empfänger-Hülle des Skeletts liegt 2,0 mm daneben. Die Klemmschrauben müssen von vorne erreichbar bleiben (oben über dem Motor, rechts außen bei Y ca. −50 / Z 70, unten unter dem Motor bei Z ca. 42). Beim Ritzelwechsel wandert der Motor um ca. 15 mm nach vorne (bis X −26): davor ≥ 5 mm frei lassen und die Motorkabel mit Reserve verlegen.
- **Skelett-Korrektur (eigener PR, mit der Messung):** Motor- und Ritzel-Hülle in die neue Lage (`motor_flansch_x` −93, Achse 15° geschwenkt, Achsabstand 26,5…29,0), `hz_ebene` bzw. `ritzel_x` auf die Zahnebene X −105,5, Ritzelbereich 20Z–25Z, Zahnradabdeckungs-Hülle durch die neue Abdeckung ersetzen, Rutschkupplungs-Hülle entfernen bzw. für später neu fassen.
- **Spätere Rutschkupplung:** braucht ca. 30 mm auf E2 und damit eine eigene E2 oder ein längeres Getriebe (Zahnradraum heute 5 mm). Halter und Abdeckung hängen an `ha_hz_x0` und `ma_halter_x0` und lassen sich mitführen.
- **4WD:** siehe oben; Blinddeckel weg, E1 einbauen.
- **Hinterachse nach dem Messen:** Ändern sich `ha_hz_x0` oder der Verstellbereich, die Kopien `ha_ma_*` in der Hinterachse von Hand nachziehen (`ma_schnitt_pruef` zeigt Abweichungen).

## Entscheidungen in der Umsetzung (nicht im Anforderungsdokument vorgegeben)

- **Motorachse 15° nach oben geschwenkt** (`ma_winkel`), Verstellung radial zu E2: sonst passt die Ritzelabdeckung nicht über den Querlenkerbock rechts vorne (siehe [Motorlage](#motorlage-mech-man-003)).
- **Becherhaube an der Motorplatte** statt an der Abdeckung: Sie bewegt sich mit dem Motor, so bleibt die Fuge zur Motordose in jeder Stellung 0,5 mm (MECH-MAN-006: ≤ 1 mm). Eine feste Haube hätte über den Verstellweg bis 3 mm Fuge.
- **Motorhalter = Vorderwand der Abdeckung** (Möglichkeit 1 aus `docs/skelett.md`), Motorplatte mit Sockel im Fenster und Klemmrand davor („Motorplatte außen am Halter geklemmt“). Die Klemmschrauben sind von vorne erreichbar; die zwei Schrauben Motor ↔ Platte sitzen auf der Zahnradseite und werden auf der Werkbank angezogen.
- **Ritzelwechsel ohne seitlichen Deckel:** Motor mit Platte nach vorne herausziehen; ein Deckel ist nicht nötig.
- **Abdeckung dreiteilig** (Oberteil, Unterteil links und rechts), damit sie sich um das montierte Getriebe legen lässt.
- **Motorlochbild 45° gedreht**, damit die Senkungen in den Sockel passen.
- **Zugang zur rechten Lagerbock-Schraube** nur mit Kugelkopf-Inbus leicht schräg (der Fuß des Halters steht 0,75 mm im geraden Weg).

## Parameterliste (neue Benutzerparameter)

107 Benutzerparameter mit Präfix `ma_`, jeder mit Kommentar. Abgeleitete Parameter von Skelett und Hinterachse stehen mit `_Ref`. **Prüfmaße** (`ma_hz_fehl`, `ma_ueberdeckung`, `ma_welle_reserve`, `ma_ms_reserve`, `ma_schnitt_pruef`, `ma_schnitt_pruef_w`, `ma_spalt_becher`, `ma_spalt_becher_min`) steuern nichts im Modell. Werte mit Ritzel 25Z.

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `ma_ritzel_zaehne` | `25` | 25 | gewaehlt: eingebautes Motorritzel (ma_-Gegenstueck zu ritzel_zaehne im Skelett); zulaessig ma_ritzel_min..ma_ritzel_max, Startwert 25Z (Stueckliste Pos. 13) |
| `ma_ritzel_min` | `20` | 20 | belegt: kleinstes zulaessiges Ritzel 20Z (Nutzerentscheidung 2026-11-01, MECH-MAN-004) |
| `ma_ritzel_max` | `25` | 25 | belegt: groesstes zulaessiges Ritzel 25Z (MECH-MAN-004) |
| `ma_zs_reserve` | `0.5 mm` | 0,5 mm | belegt: Reserve der Zahnspiel-Einstellung ueber den Ritzelbereich hinaus (MECH-MAN-004: >= +-0,5 mm) |
| `ma_a` | `zahn_modul_Ref * ( hz_zaehne_Ref + ma_ritzel_zaehne ) / 2` | 28,5 mm | abgeleitet: Achsabstand E2 - Motorachse fuer das eingebaute Ritzel |
| `ma_a_min` | `zahn_modul_Ref * ( hz_zaehne_Ref + ma_ritzel_min ) / 2 - ma_zs_reserve` | 26,5 mm | abgeleitet: kleinster einstellbarer Achsabstand (20Z - Reserve) |
| `ma_a_max` | `zahn_modul_Ref * ( hz_zaehne_Ref + ma_ritzel_max ) / 2 + ma_zs_reserve` | 29 mm | abgeleitet: groesster einstellbarer Achsabstand (25Z + Reserve) |
| `ma_a_mid` | `( ma_a_min + ma_a_max ) / 2` | 27,75 mm | abgeleitet: Mitte des Verstellbereichs (Lage der Klemm-Einsaetze im Halter) |
| `ma_zs_halb` | `( ma_a_max - ma_a_min ) / 2` | 1,25 mm | abgeleitet: halber Verstellweg der Motorplatte |
| `ma_winkel` | `15 deg` | 15° | gewaehlt: Motorachse um die E2-Achse nach oben gedreht (Verstellrichtung radial); haelt die Ritzelabdeckung ueber dem Querlenkerbock rechts vorne (Z >= 48) und den Motor unter dem Oberdeck |
| `ma_ritzel_r` | `( ma_ritzel_zaehne + 2 ) * zahn_modul_Ref / 2` | 8,1 mm | abgeleitet: Kopfkreisradius eingebautes Ritzel |
| `ma_ritzel_r_max` | `( ma_ritzel_max + 2 ) * zahn_modul_Ref / 2` | 8,1 mm | abgeleitet: Kopfkreisradius groesstes Ritzel (Bauraum Abdeckung) |
| `ma_ritzel_l` | `8 mm` | 8 mm | vorlaeufig: Laenge Motorritzel = Zahnbreite (Vergleichsteil wie ritzel_b_netto), Zahnbreite und Bund am Teil messen |
| `ma_ritzel_ms` | `4 mm` | 4 mm | vorlaeufig: Lage der Madenschraube ab Ritzel-Hinterkante (Annahme Mitte), am Teil messen |
| `ma_ms_d` | `3 mm` | 3 mm | vorlaeufig: Madenschraube M3 im Ritzel (Annahme), am Teil messen |
| `ma_ritzel_versatz` | `0 mm` | 0 mm | gewaehlt: Ritzel-Hinterkante gegenueber GB5-Hinterkante (ha_hz_x0); 0 = buendig, Ritzel ueberdeckt GB5 auf voller Breite |
| `ma_gb5_b` | `5 mm` | 5 mm | vorlaeufig: Zahnbreite Hauptzahnrad GB5 (Annahme: 5 der 8 mm von e2_mitnehmer_l), am Teil messen |
| `ma_gb3_b` | `3 mm` | 3 mm | vorlaeufig: Breite Mitnehmer GB3 vor GB5 (Annahme, GB3 + GB5 = ha_hz_bedarf 8 mm), am Teil messen |
| `ma_gb3_d` | `14 mm` | 14 mm | vorlaeufig: Durchmesser Mitnehmer GB3 (Annahme aus [A1] S. 4), am Teil messen |
| `ma_gb5_d` | `hz_d_Ref` | 43,2 mm | abgeleitet: Kopfkreis Hauptzahnrad 70Z (= hz_d Skelett) |
| `ma_ritzel_x` | `ha_hz_x0_Ref + ma_ritzel_versatz` | -108 mm | abgeleitet: Hinterkante Motorritzel = Hinterkante GB5 (Vorderseite hinteres E2-Lager, ha_hz_x0) |
| `ma_hz_ebene_x` | `ha_hz_x0_Ref + ma_gb5_b / 2` | -105,5 mm | abgeleitet: Zahnebene (Mitte GB5), aus ha_hz_x0 und Breite GB5 (MECH-MAN-002) |
| `ma_hz_fehl` | `ma_gb5_b + ma_gb3_b - ha_hz_raum_Ref` | 3 mm | Pruefmass: Fehlbetrag Zahnradraum GB3 + GB5 gegen ha_hz_raum (> 0 = offen bis Messung, wie ha_hz_fehl) |
| `ma_ueberdeckung` | `min(ma_ritzel_x + ma_ritzel_l; ha_hz_x0_Ref + ma_gb5_b) - max(ma_ritzel_x; ha_hz_x0_Ref)` | 5 mm | Pruefmass: Ueberdeckung Ritzel mit GB5 in X, Soll = ma_gb5_b (volle Zahnbreite, MECH-MAN-003) |
| `ma_luft_stat` | `1 mm` | 1 mm | belegt: Mindestabstand zu nicht verbundenen Teilen und Huellkoerpern (MECH-MAN-005, -008) |
| `ma_luft_dreh` | `2 mm` | 2 mm | belegt: Mindestabstand zu drehenden Teilen netto (MECH-MAN-007, -008) |
| `ma_wand_min` | `1.2 mm` | 1,2 mm | belegt: Mindestwand Druck (MECH-MAN-013) |
| `ma_spiel` | `0.3 mm` | 0,3 mm | gewaehlt: Spiel der Gleitfuehrung Sockel Motorplatte im Fenster des Halters (je Seite) |
| `ma_r_innen` | `1.5 mm` | 1,5 mm | belegt: Innenradius fraesgerecht (AGENTS.md: >= 1,5 mm) |
| `ma_bohrung` | `ha_bohrung_Ref` | 3,2 mm | abgeleitet: Bohrung M3 im Druck (+0,2 mm) |
| `ma_einsatz_d` | `ha_einsatz_d_Ref` | 4 mm | abgeleitet: Gewindeeinsatz M3 kurz (Pos. 30): Bohrung |
| `ma_einsatz_t` | `ha_einsatz_t_Ref` | 6 mm | abgeleitet: Gewindeeinsatz M3 kurz: Bohrtiefe |
| `ma_einsatz_wand` | `1.5 mm` | 1,5 mm | belegt: Wand um Gewindeeinsaetze (MECH-MAN-013: >= 1,5 mm) |
| `ma_senk_d` | `6.9 mm` | 6,9 mm | belegt: Senkung M3 ISO 10642 (Kopf 6,72 mm + 0,2 mm), 90 Grad |
| `ma_kopf_d` | `5.5 mm` | 5,5 mm | belegt: Kopf Zylinderschraube M3 ISO 4762 |
| `ma_platte_d` | `4 mm` | 4 mm | gewaehlt: Dicke Sockel der Motorplatte = Dicke Wand des Motorhalters (PC) |
| `ma_halter_x0` | `max(ma_ritzel_x + ma_ritzel_l + abdeckung_abstand_Ref; ha_hz_x0_Ref + ma_gb5_b + ma_gb3_b + ma_luft_dreh)` | -97 mm | abgeleitet: Rueckseite Halterwand und Sockel: 3 mm vor dem Ritzel (MECH-SKE-014) und 2 mm vor GB3 |
| `ma_flansch_x` | `ma_halter_x0 + ma_platte_d` | -93 mm | abgeleitet: Motorflansch (Motor zeigt nach hinten), MECH-MAN-003: <= ca. -93 |
| `ma_welle_reserve` | `motor_welle_l_Ref - ( ma_flansch_x - ma_ritzel_x )` | -0 mm | Pruefmass: Motorwelle reicht bis Ritzel-Hinterkante (>= 0, Definition wie motor_welle_reserve im Skelett) |
| `ma_ms_reserve` | `( ma_ritzel_x + ma_ritzel_ms - ma_ms_d / 2 ) - ( ma_flansch_x - motor_welle_l_Ref )` | 2,5 mm | Pruefmass: Welle reicht ueber die Madenschraube hinaus (>= 0, MECH-MAN-003) |
| `ma_motor_welle_d` | `3.175 mm` | 3,175 mm | belegt: Motorwelle 1/8 Zoll (Lindinger, Hobbywing 3652SL G2) |
| `ma_motor_loch_a` | `25 mm` | 25 mm | vorlaeufig: Motorlochbild 2 x M3, Abstand (Annahme wie Groesse 540), am Motor messen |
| `ma_motor_bund_d` | `13 mm` | 13 mm | vorlaeufig: Durchgang im Sockel fuer Welle und Lagerbund des Motors, am Motor messen |
| `ma_sockel_u` | `ma_a_min - ma_spiel - ma_becher_r - ma_wand_min` | 14 mm | abgeleitet: Sockel Motorplatte, halbe Laenge in Verstellrichtung (Fenster endet 1,2 mm vor dem Freiraum um den Becher) |
| `ma_sockel_v` | `ma_motor_loch_a / 2 * sin(ma_motor_loch_w) + ma_senk_d / 2 + ma_wand_min` | 13,489 mm | abgeleitet: Sockel Motorplatte, halbe Breite quer zur Verstellrichtung |
| `ma_fenster_l` | `ma_a_max - ma_a_min + 2 * ( ma_sockel_u + ma_spiel )` | 31,1 mm | abgeleitet: Fenster im Halter fuer den Sockel: Laenge (Verstellweg + Sockel + Spiel) |
| `ma_fenster_b` | `2 * ( ma_sockel_v + ma_spiel )` | 27,578 mm | abgeleitet: Fenster im Halter fuer den Sockel: Breite |
| `ma_becher_r` | `kardan_becher_d_Ref / 2 + ma_luft_stat` | 11 mm | abgeleitet: Freiraum um den Becher E2 im Halter (Huelle + 1 mm, netto 3 mm) |
| `ma_dose_r` | `motor_d_Ref / 2` | 18 mm | abgeleitet: Radius Motordose |
| `ma_dose_fuge` | `0.5 mm` | 0,5 mm | gewaehlt: Fuge Motorplatte/Haube zur Motordose (MECH-MAN-006: <= 1 mm) |
| `ma_rand_d` | `3 mm` | 3 mm | gewaehlt: Rand der Motorplatte vor dem Halter (Klemmflaeche) |
| `ma_rand_r` | `25.2 mm` | 25,2 mm | gewaehlt: Rand der Motorplatte: Radius um die Motorachse (deckt das Fenster in jeder Stellung ab) |
| `ma_haube_ri` | `ma_becher_r + ma_zs_halb` | 12,25 mm | abgeleitet: Becherhaube an der Motorplatte: Innenradius (Becher-Huelle + 1 mm in jeder Stellung) |
| `ma_haube_wand` | `3 mm` | 3 mm | gewaehlt: Becherhaube: Wand radial |
| `ma_haube_ro` | `ma_haube_ri + ma_haube_wand` | 15,25 mm | abgeleitet: Becherhaube: Aussenradius |
| `ma_haube_front_d` | `3 mm` | 3 mm | gewaehlt: Becherhaube: Stirnwand vor dem Becher (Sitz Blinddeckel) |
| `ma_haube_x1` | `kardan_hinten_x_Ref + ma_luft_dreh + ma_haube_front_d` | -79 mm | abgeleitet: Becherhaube: Vorderkante (2 mm vor der Becheroeffnung E2 + Stirnwand) |
| `ma_e1_r` | `kardan_d_Ref / 2 + ma_luft_stat + ma_zs_halb` | 9,25 mm | abgeleitet: Oeffnung fuer E1 (4WD) in der Becherhaube, in v1 mit Blinddeckel verschlossen (MECH-MAN-006, -021) |
| `ma_deckel_flansch_r` | `ma_e1_r + 2 mm` | 11,25 mm | gewaehlt: Blinddeckel: Flansch |
| `ma_deckel_flansch_d` | `1.5 mm` | 1,5 mm | gewaehlt: Blinddeckel: Flanschdicke |
| `ma_klemm_r` | `22 mm` | 22 mm | gewaehlt: Klemmschrauben oben/unten: Abstand zur Motorachse |
| `ma_klemm_w` | `80 deg` | 80° | gewaehlt: Klemmschrauben oben/unten: Winkel zur Verstellrichtung |
| `ma_klemm_aussen` | `24 mm` | 24 mm | gewaehlt: Klemmschraube aussen: Abstand zur Motorachse in Verstellrichtung |
| `ma_klemm_boss_d` | `ma_einsatz_d + 2 * ma_einsatz_wand` | 7 mm | abgeleitet: Auge um die Klemm-Einsaetze hinter dem Halter |
| `ma_klemm_boss_l` | `ma_einsatz_t + ma_einsatz_wand - ma_platte_d` | 3,5 mm | abgeleitet: Auge hinter der Halterwand (Einsatz + Boden) |
| `ma_lasche_d` | `ma_kopf_d + 1.5 mm` | 7 mm | gewaehlt: Lasche um das aeussere Langloch der Motorplatte |
| `ma_od_ecke_u` | `-5 mm` | -5 mm | gewaehlt: Freischnitt Oberdeck an der Motorplatte: Grenze in Verstellrichtung |
| `ma_od_ecke_v` | `20.5 mm` | 20,5 mm | gewaehlt: Freischnitt Oberdeck an der Motorplatte: Grenze quer |
| `ma_od_z` | `antrieb_z_Ref + abdeckung_r_Ref + ha_od_luft_Ref` | 84,2 mm | abgeleitet: Unterkante Oberdeck (84,2 mm, wie ha_od_z) |
| `ma_od_halb_b` | `10 mm` | 10 mm | Schnittstelle Grundplatte v11 (Kopie od_halb_b): halbe Breite Oberdeck |
| `ma_gp_mh_x` | `-71 mm` | -71 mm | Schnittstelle Grundplatte v11 (Kopie gp_mh_x): Lochbild Motorhalter in X |
| `ma_gp_mh_dy` | `12 mm` | 12 mm | Schnittstelle Grundplatte v11 (Kopie gp_mh_dy): Lochabstand quer |
| `ma_gp_mh_y` | `motor_y_Ref` | -28,5 mm | abgeleitet: Lochbild Motorhalter quer (motor_y Skelett, wie gp_mh_y) |
| `ma_fuss_h` | `7.5 mm` | 7,5 mm | gewaehlt: Fuss Motorhalter: Hoehe (Einsatz 6 + Boden 1,5) |
| `ma_fuss_x1` | `ma_gp_mh_x + ma_einsatz_d / 2 + ma_einsatz_wand + 2 mm` | -65,5 mm | abgeleitet: Fuss Motorhalter: Vorderkante |
| `ma_fuss_y_aussen` | `ma_gp_mh_y - ma_gp_mh_dy - ( ma_einsatz_d / 2 + ma_einsatz_wand + 2 mm )` | -46 mm | abgeleitet: Fuss Motorhalter: Aussenkante |
| `ma_fuss_y_innen` | `ma_gp_mh_y + ma_gp_mh_dy + ma_einsatz_d / 2 + ma_einsatz_wand` | -13 mm | abgeleitet: Fuss Motorhalter: Innenkante |
| `ma_halter_r` | `27 mm` | 27 mm | gewaehlt: Halterwand: Radius um die Motorachse (Mitte Verstellbereich) |
| `ma_lb_kopf_d` | `ma_kopf_d + 2 * ma_luft_stat` | 7,5 mm | abgeleitet: Durchgang fuer die Koepfe der Lagerbock-Schrauben (Inbus von vorne) |
| `ma_ab_ri` | `ma_gb5_d / 2 + abdeckung_abstand_Ref` | 24,6 mm | abgeleitet: Abdeckung: Innenradius um GB5 (3 mm, MECH-SKE-014) |
| `ma_ab_ro` | `ma_ab_ri + abdeckung_wand_Ref` | 26,6 mm | abgeleitet: Abdeckung: Aussenradius um GB5 (= abdeckung_r) |
| `ma_ab_x0` | `ha_hz_x0_Ref - abdeckung_abstand_Ref - abdeckung_wand_Ref` | -113 mm | abgeleitet: Abdeckung: Rueckseite der Rueckwand |
| `ma_rz_ri` | `ma_ritzel_r_max + abdeckung_abstand_Ref` | 11,1 mm | abgeleitet: Abdeckung: Innenradius um das Ritzel (3 mm) |
| `ma_rz_ro` | `ma_rz_ri + abdeckung_wand_Ref` | 13,1 mm | abgeleitet: Abdeckung: Aussenradius um das Ritzel |
| `ma_bock_x` | `-achse_x_Ref + ha_ql_dx_Ref + ha_ql_fuss_l_Ref / 2 + ma_luft_stat` | -109 mm | abgeleitet: hinterste Lage der Abdeckung neben dem Querlenkerbock rechts vorne (-109, MECH-MAN-007) |
| `ma_ab_boss_r` | `29 mm` | 29 mm | gewaehlt: Abdeckung unten: Augen fuer die Schrauben vom Halter, Abstand zu E2 |
| `ma_ab_boss_w1` | `-35 deg` | -35° | gewaehlt: Abdeckung unten: Auge links, Winkel um E2 |
| `ma_ab_boss_w2` | `-146 deg` | -146° | gewaehlt: Abdeckung unten: Auge rechts, Winkel um E2 |
| `ma_ab_boss_l` | `8 mm` | 8 mm | gewaehlt: Abdeckung: Laenge der Augen in X |
| `ma_lasche_l` | `8 mm` | 8 mm | gewaehlt: Laschen Ober-/Unterteil: Laenge in X |
| `ma_lasche_h_unten` | `7.5 mm` | 7,5 mm | gewaehlt: Laschen: Hoehe Unterteil (Einsatz von oben) |
| `ma_lasche_h_oben` | `4 mm` | 4 mm | gewaehlt: Laschen: Hoehe Oberteil |
| `ma_lasche_b` | `9 mm` | 9 mm | gewaehlt: Laschen: Breite quer |
| `ma_lasche_y_links` | `ma_ab_ro + 3 mm` | 29,6 mm | abgeleitet: Lasche links: Lage des Einsatzes |
| `ma_lasche_y_rechts` | `-( ma_a_mid + ma_fenster_l / 2 + abdeckung_wand_Ref ) / cos(ma_winkel) - ma_einsatz_d / 2` | -48,898 mm | abgeleitet: Lasche rechts: Lage des Einsatzes (aussen am Fensterbereich der Abdeckung in der Teilungsebene) |
| `ma_schnitt_pruef` | `abs(ha_ma_a_min_Ref - ma_a_min) + abs(ha_ma_a_max_Ref - ma_a_max) + abs(ha_ma_ritzel_r_Ref - ma_ritzel_r_max)` | 0 mm | Pruefmass: Kopien in der Hinterachse (Freischnitt) stimmen mit dem Mittelantrieb ueberein (Soll 0) |
| `ma_schnitt_pruef_w` | `abs(ha_ma_winkel_Ref - ma_winkel)` | 0° | Pruefmass: Winkel-Kopie in der Hinterachse (Soll 0) |
| `ma_spalt_becher` | `ma_a - ma_dose_r - ( kardan_becher_d_Ref / 2 - huelle_zuschlag_Ref )` | 2,5 mm | Pruefmass: Spalt Motordose - Becher E2 netto (MECH-MAN-006: >= 1,0 mm) |
| `ma_spalt_becher_min` | `zahn_modul_Ref * ( hz_zaehne_Ref + ma_ritzel_min ) / 2 - ma_dose_r - ( kardan_becher_d_Ref / 2 - huelle_zuschlag_Ref )` | 1 mm | Pruefmass: Spalt Motordose - Becher netto beim kleinsten Ritzel 20Z (>= 1,0 mm) |
| `ma_motor_loch_w` | `45 deg` | 45° | gewaehlt: Motorlochbild um 45 Grad zur Verstellrichtung gedreht (Senkungen passen in den schmalen Sockel) |
| `ma_durch` | `2 mm` | 2 mm | Modellierhilfe: Zugabe fuer durchgehende Schnitte (keine Wirkung auf die Teile) |
| `ma_leiste_y` | `ha_lb_s_y_Ref - ma_lb_kopf_d / 2` | 8,75 mm | abgeleitet: Bodenleiste des Halters vor dem Lagerbock, halbe Breite (zwischen den Lagerbock-Schrauben) |
| `ma_leiste_z` | `ha_lb_quer_z_Ref` | 34,283 mm | abgeleitet: Bodenleiste des Halters, Oberkante (= Querstege Lagerbock) |
| `ma_ha_vs_vx` | `21 mm` | 21 mm | Schnittstelle Hinterachse v13 (Kopie, von Hand nachziehen): ha_vs_vx, Verschraubung der Gehaeusehaelften vorne unten, X vor der Achse |
| `ma_ha_vs_vz` | `41 mm` | 41 mm | Schnittstelle Hinterachse v13 (Kopie, von Hand nachziehen): ha_vs_vz, Verschraubung vorne unten, Hoehe |
| `ma_ha_vs_oz` | `74 mm` | 74 mm | Schnittstelle Hinterachse v13 (Kopie, von Hand nachziehen): ha_vs_oz, Verschraubung oben in der Oberdeck-Auflage, Hoehe (X = ha_od_dx) |
| `ma_ha_kopf_d` | `6 mm` | 6 mm | Schnittstelle Hinterachse v13 (Kopie, von Hand nachziehen): ha_kopf_d, Senkung fuer M3-Zylinderkopf; Abdeckung bleibt aus den Schraubenbohrungen des Gehaeuses heraus |

# Vorderachse und Lenkung

- **Anforderungen:** `docs/anforderungen/vorderachse.md` (Kürzel VAC)
- **Fusion:** Projekt „open-rc-car“, Design „open-rc-car-vorderachse“, **Version 8**, abgeleitet von „open-rc-car-skelett“ **v14** (maßgleich mit v12 und v10) und „open-rc-car-grundplatte“ **v11** (Verweise im Dokument geprüft: `documentReferences` = Skelett v14, Grundplatte v11). Version 1 bis 7 sind Zwischenstände der Umsetzung.
- **Exporte (alle aus Version 8):** `cad/fusion/vorderachse.f3d`, `cad/step/vorderachse.step` (nur die 19 Druckteile), 19 STL in `print/stl/`
- **Stand:** 2026-11-08

Die gelenkte, in v1 nicht angetriebene Vorderachse des 2WD-Prototyps: Frontschott als Platzhalter für das spätere Vorderachsgetriebe, vier Querlenkerböcke, zwei untere Querlenker, zwei C-Hubs mit festem Nachlauf, zwei Achsschenkel auf Kingpin-Passschrauben M3, Dämpferbrücke vor dem Schott mit den CVA-Dämpfern davor, einstellbare Sturzstangen (Spannschloss 54539). Die Lenkung besteht aus zwei Umlenkhebeln auf den Lagerböcken der Grundplatte (je 2 Lager 5x8x2,5), dem Lenkgestänge zwischen den Umlenkhebeln, zwei Spurstangen (54539), der Servo-Anlenkung (54539) und einem gedruckten Servo-Saver mit Rastnocken und Druckfeder auf einem Alu-Servohorn 25Z. Alle Maße der Bausatz- und Zukaufteile sind **vorläufig** (Messpunkte unten).

![Vorderachse isometrisch](images/vorderachse-iso.png)

*Von vorne rechts oben, Konstruktionslage. Durchscheinend: Bauraum des Vorderachsgetriebes (Skelett-Hülle, 4WD); darin das Frontschott. Vorne die Dämpferbrücke mit den Dämpfern, hinten (links im Bild) Servo, Servohalter, Servo-Saver, Umlenkhebel und Lenkgestänge.*

![Von vorne](images/vorderachse-vorne.png)

*Von vorne, ohne Räder: Querlenker, C-Hubs, Achsschenkel, Sturzstangen zur Dämpferbrücke, Dämpfer (oben 9,1° nach innen geneigt).*

![Von oben](images/vorderachse-oben.png)

*Von oben, Konstruktionslage (vorne ist oben).*

![Lenkung von oben](images/vorderachse-lenkung-oben.png)

*Lenkhebelsystem von oben: Umlenkhebel links (Y 35) und rechts (Y −51) auf den Lagerböcken, Lenkgestänge hinter dem Servo-Saver quer über das Servo, Servo-Anlenkung vom Saver-Arm zum erhöhten Auge des rechten Umlenkhebels, Spurstangen zu den nach hinten zeigenden Spurhebeln.*

## Ergebnis

| Teil | Komponente | Hüllquader X × Y × Z (mm) | Lage X / Y / Z (mm) | Masse PETG 100 % | Masse PC | Datei |
|---|---|---|---|---|---|---|
| Frontschott | `vorderachse-frontschott` | 47,0 × 44,7 × 55,2 | 109,5…156,5 / ±22,36 / 29,0…84,2 | 30,3 g | 28,7 g | `print/stl/vorderachse-frontschott.stl` |
| Querlenkerbock (4 ×) | `vorderachse-querlenkerbock-links-hinten`, `-links-vorne`, `-rechts-hinten`, `-rechts-vorne` | 10 × 16 × 17 | 110…120 bzw. 146…156 / ±27…±43 / 29…46 | je 2,8 g | je 2,7 g | `print/stl/vorderachse-querlenkerbock-*.stl` |
| Querlenker links/rechts | `vorderachse-querlenker-links`, `-rechts` | 48,0 × 48,5 × 22,6 | 120,5…168,5 / ±31,5…±80,0 / 23,0…45,6 | je 8,3 g | je 7,8 g | `print/stl/vorderachse-querlenker-links.stl`, `-rechts.stl` |
| C-Hub links/rechts | `vorderachse-c-hub-links`, `-rechts` | 24,4 × 20,5 × 44,4 | 127,6…152,0 / ±72,0…±92,5 / 21,2…65,6 | je 4,0 g | je 3,8 g | `print/stl/vorderachse-c-hub-links.stl`, `-rechts.stl` |
| Achsschenkel links | `lenkung-achsschenkel-links` | 34,2 × 28,9 × 31,8 | 106,9…141,1 / 79,8…108,7 / 25,4…57,2 | 5,5 g | 5,2 g | `print/stl/lenkung-achsschenkel-links.stl` |
| Achsschenkel rechts | `lenkung-achsschenkel-rechts` | 33,0 × 25,1 × 31,8 | 108,0…141,1 / −108,7…−83,6 / 25,4…57,2 | 5,4 g | 5,1 g | `print/stl/lenkung-achsschenkel-rechts.stl` |
| Dämpferbrücke | `vorderachse-daempferbruecke` | 6,0 × 102,0 × 67,2 | 156,5…162,5 / ±51,0 / 31,0…98,2 | 30,1 g | 28,4 g | `print/stl/vorderachse-daempferbruecke.stl` |
| Umlenkhebel links | `lenkung-umlenkhebel-links` | 46,0 × 20,8 × 8,0 | 71,9…117,9 / 28,9…49,7 / 59,2…67,2 | 2,8 g | 2,7 g | `print/stl/lenkung-umlenkhebel-links.stl` |
| Umlenkhebel rechts | `lenkung-umlenkhebel-rechts` | 55,1 × 15,5 × 14,8 | 60,2…115,3 / −57,0…−41,6 / 59,2…74,0 | 3,5 g | 3,3 g | `print/stl/lenkung-umlenkhebel-rechts.stl` |
| Lagerbock links/rechts | `lenkung-lagerbock-links`, `-rechts` | 8,0 × 16,0 × 29,7 | 90,5…98,5 / 27…43 bzw. 88,75…96,75 / −59…−43 / 29…58,7 | je 4,5 g | je 4,2 g | `print/stl/lenkung-lagerbock-links.stl`, `-rechts.stl` |
| Servohalter | `lenkung-servohalter` | 54,6 × 28,4 × 26,0 | 50,0…104,6 / −40,4…−12,0 / 29,0…55,0 | 11,8 g | 11,2 g | `print/stl/lenkung-servohalter.stl` |
| Servo-Saver Nabe | `lenkung-servo-saver-nabe` | 18,0 × 18,0 × 18,8 | Achse 87,3 / −22,1, Z 69,2…88,0 | 2,9 g | 2,8 g | `print/stl/lenkung-servo-saver-nabe.stl` |
| Servo-Saver Arm | `lenkung-servo-saver-arm` | 40,4 × 25,3 × 4,0 | 55,9…96,3 / −31,1…−5,8 / 79,0…83,0 | 2,0 g | 1,9 g | `print/stl/lenkung-servo-saver-arm.stl` |
| **Summe Druckteile (19)** | | | | **139,3 g** (≤ 150 g) | 131,6 g | |

Masse = Volumen aus Fusion × 1,27 g/cm³ (PETG, 100 % Füllung, obere Grenze) bzw. × 1,20 g/cm³ (Prusament PC). Volumen gesamt 109,69 cm³.

Hüllkörper (kein Druckteil, nur für Kollisions- und Bewegungsprüfung): `vorderachse-rad-*` (Rad 82 × 32 mit Felgeninnenraum Ø 50), `vorderachse-radachse-*` (Radachse N1 mit Becher Ø 17 und Sechskant-Mitnehmer), `vorderachse-antriebswelle-*` (Bauraum der Antriebswelle N3 für 4WD, `va_n3_d`), `vorderachse-daempfer-*`, `vorderachse-sturzstange-*`, `lenkung-spurstange-*`, `lenkung-lenkgestaenge`, `lenkung-servoanlenkung` (Stange Ø 3 mit Kugelpfannen als Zylinder Ø 9 × 9), `lenkung-servo-laschen` (Servolaschen und Abtrieb, das Gehäuse steht im Skelett), `lenkung-servo-horn` (Alu-Horn), `lenkung-servo-saver-feder` (Feder mit Scheibe und Schraube in Einbaulänge). Alle Hüllkörper bewegen sich mit den Stellungsparametern.

## Aufbau in Fusion

- **Ableitungen:** vom Skelett v14 alle 155 Favoriten-Parameter (`<name>_Ref`, hier ohne `_Ref`), die 8 Bezugsebenen und alle Hüllkörper außer `chassis-grundplatte`; von der Grundplatte v11 die Komponenten `chassis-grundplatte`, `chassis-oberdeck`, `chassis-mittelstuetze`, die vier Akkuanschläge und `chassis-fussflaechen`.
- **Grundplatten-Schnittstellen als Kopie** (wie Hinterachse, Nutzerentscheidung 2026-11-01): Die Grundplatte hat keine Favoriten-Parameter. Die Lochbilder und Fußflächen sind hier als `va_ql_*`, `va_gp_*`, `va_od_*`, `va_lk_*`, `va_sh_*` angelegt (Kommentar „Schnittstelle Grundplatte v11 … von Hand nachziehen“). Wo die Grundplatte eine Formel aus Skelett-Parametern hat, ist dieselbe Formel übernommen (`va_lk_x`, `va_lk_x_rechts`, `va_sh_x_hinten`, `va_sh_x_vorne`, `va_sh_y_aussen`, `va_od_z`). Übereinstimmung gemessen, siehe [Schnittstellen](#schnittstellen-zur-grundplatte).
- **Körper** wie in Skelett und Hinterachse: voll bestimmte Skizzen im Komponentenursprung (Rechteck mittig, Kreis um den Ursprung), symmetrische Extrusion, Verschieben/Drehen mit Ausdrücken, Bohrungen und Einsätze als Werkzeugkörper (Kombinieren). Eine Komponente je Teil, Druckausrichtung in der Komponentenbeschreibung.
- **Prüfskripte:** 237 Skizzen in den eigenen Komponenten, alle voll bestimmt. Zeitleiste 911 Elemente ohne Fehler und Warnungen. 400 Benutzerparameter, alle mit Präfix `va_` und Kommentar. Feste Zahlen in Features gibt es nur bei 0-Lagen, bei der Flanke der Rastnocken (45°) und bei kleinen Spielmaßen in Bohrungs-Werkzeugen (0,1–0,4 mm, z. B. Bohrung im Saver-Arm); alle Maße der Teile sind Parameter.
- **Kinematik vollständig in Parametern:** Zwei Stellungsparameter bewegen alles: `va_ql_dphi` (Querlenkerdrehung = Federweg) und `va_lk_phi` (Drehwinkel des linken Umlenkhebels = Lenkung), dazu `va_sl_dl` (Sturzverstellung über die Sturzstange). Daraus berechnen Ausdrücke in geschlossener Form:
  - das Viergelenk Querlenker/Sturzstange (`va_k_*`, `va_kappa`, Lage `va_t_*` des Lenkachspunkts K0),
  - die Gelenkvierecke Lenkgestänge (rechter Umlenkhebel `va_lk_phi_r`), Spurstange links/rechts (`va_ll_*`, `va_rl_*` → Lenkwinkel `va_lenk_l`, `va_lenk_r`) und Servo-Anlenkung (`va_servo_phi`).
  Die Gleichungen haben die Form a·cos φ + b·sin φ = m; gelöst mit der Halbwinkelform φ = 2·atan(b/(√(a²+b²)+a)) ± acos(m/√(a²+b²)), der Zweig ist so gewählt, dass in Konstruktionslage 0 herauskommt. **Prüfmaße** `va_pruef_spst_l`, `va_pruef_spst_r`, `va_pruef_lg`, `va_pruef_sa`, `va_pruef_sl` vergleichen in jeder Stellung die Gelenkabstände mit den Solllängen: in allen 9 Prüfstellungen ≤ 2·10⁻¹⁴ mm. Die Ausdrücke sind zusätzlich offline gegen einen unabhängigen 3D-Löser geprüft (größte Abweichung 0,003°, Rundung der Entwurfswerte).
- **Koordinatensysteme:** Achsschenkel, Rad und Radachse entstehen im Achsschenkelsystem (Ursprung K0 = Punkt der Lenkachse auf der Radachse, z = Lenkachse, y = Radachse ohne Neigung) und werden mit Rz(Lenkwinkel) → Ry(−Nachlauf) → Rx(Spreizung + C-Hub-Drehung) → Verschieben nach K0 platziert. Der C-Hub: Kingpin-Ohren im Lenkachsensystem (gekippt), übrige Körper im C-Hub-System, dann Rx(`va_kappa`) und Verschieben. Rechts = links gespiegelt (Y und Drehungen um X und Z mit umgekehrtem Vorzeichen); nur die Spurhebel und die Umlenkhebel sind links und rechts verschieden (`va_sph_r_dl`, `va_sph_r_dw`, `va_ulh_r_*`), weil die Lagerböcke nicht symmetrisch liegen.
- **Entwurf der Geometrie:** Die Lage der Gelenkpunkte (Sturzstange, Spurhebel, Umlenkhebel, Lenkgestänge, Servo-Anlenkung) ist offline mit einem 3D-Kinematikmodell optimiert (Bump-Steer ≤ 0,5°, Ackermann bei 30° nahe 100 %, Servowinkel ≤ ±40°, Übertragungswinkel, Bauraum in den Endstellungen, Stangenlängen der Spannschlösser) und als Parameter mit Kommentar „aus Kinematikrechnung“ übernommen.

## Frontschott (MECH-VAC-002)

- Rahmen aus zwei Bodenschienen (8 × 8 mm) mit den Gewindeeinsätzen auf dem Getriebe-Lochbild (114 / ±18) und (152 / ±18), zwei Pfosten an der Oberdeck-Auflage, einem Querriegel X 110,5…119,5, Z 76…84,2 mit den Einsätzen (115 / ±5), zwei oberen Längsschienen und der Vorderwand (6 mm, X 150,5…156,5) mit Fenster und 4 Einsätzen für die Dämpferbrücke (Y ±10 / Z 36 und 73).
- **Gemessen:** Einsätze unten (114,0 / ±18,0) und (152,0 / ±18,0), Z 29…35; Oberdeck-Einsätze (115,0 / ±5,0), Auflagefläche **Z 84,200** (= `va_od_z`). Breite **Y ±22,36** (< ±24,86) über die ganze Höhe, also bis Z 44 außerhalb der Fußflächen der Böcke (Abstand Bock ↔ Schott 4,64 mm).
- **Interferenz:** Schott ↔ Grundplatte, Fußflächen, Oberdeck, Wellenräume (Skelett) und Antriebswellen-Hüllen: 0 (Grundplatte und Oberdeck nur Berührung an den Auflageflächen). Abstand zu den Wellenräumen 11,41 mm, zu den N3-Hüllen 11,49 mm.
- **In der Getriebehülle:** Schott ∩ Hülle `antrieb-getriebe-vorne` = 22 528,5 mm³ bei 23 887,0 mm³ Schottvolumen. Der Rest (1 358,5 mm³) ist genau der Querriegel der Oberdeck-Auflage zwischen Z 80,6 (Oberkante Hülle) und Z 84,2, den MECH-VAC-002 selbst verlangt (die Getriebe-Hülle endet 3,6 mm unter dem Oberdeck, siehe `docs/grundplatte-oberdeck.md`: „die Gehäuse brauchen an den Löchern Auflagen bis Z 84,2 (+3,6 mm)“). Sonst liegt das Schott ganz in der Hülle.
- **4WD:** Lochbild, Auflagehöhe und Anlage der Dämpferbrücke (X 156,5) entsprechen dem gespiegelten Hinterachsgetriebe (`ha_gh_x_hinten`); das Getriebe ersetzt das Schott ohne Änderung an Grundplatte, Oberdeck, Böcken oder Brücke.

## Aufhängung (MECH-VAC-003, -004, -005, -006)

### Querlenkerböcke und Querlenker

- Böcke wie hinten: Fußfläche 10 × 16 mm genau auf X 110…120 bzw. 146…156, Y ±27…±43, oben rund (Ø 16). Querlenkerachse **Z 38** (hinten 40): tiefer wegen der Vorderachs-Kinematik; die Bocksenkung bleibt 1,45 mm über dem Gewindeeinsatz (Z 29…35). Höhe bis Z 46, also 2 mm über die reservierte Höhe 44 (erlaubt, keine Kollision). 2 × M3 × 8 Senkkopf von unten in Einsätze (30,5 / 39,5 bzw. ±). Zylinderstift ISO 2338 3 m6 × 40, Sacklöcher Ø 3,1 × 7,25, Rohr Ø 7 mit 0,5 mm Axialspiel.
- Querlenker: Rohr Ø 7, Platte 5 mm (1 mm über der Querlenkerebene, Freigang zur Plattenkante ausgefedert), innen 25 mm breit bis 12 mm vom Rohr, außen Gabel 18,4 mm mit Schlitz 8,4 mm für die C-Hub-Lasche, Bolzen M3 × 25 mit Stoppmutter parallel zu X bei **B = (133 / ±76,0 / 27,0)**. Länge 42,45 mm, Winkel −15,0°. Nach vorne die Dämpferlasche 8 × 8 mm (7 mm über der Ebene) bis X 168,5 mit Einsatz für M3 × 14.
- Lösbar von unten: über den Böcken liegen weder Schott noch Brücke noch Oberdeck (Abstände 4,64 / 4,67 / > 30 mm), alle Bockschrauben kommen von unten.

### C-Hub und Achsschenkel

- **C-Hub** (Nachlauf fest 4°): Kingpin-Ohren Ø 8 × 4 oben und unten, um den Nachlauf gekippt; Lasche Ø 8 × 8 um den Bolzen B in der Gabel (0,2 mm Spiel je Seite); Steg Lasche ↔ unteres Ohr; Säule vor der Lenkachse (x 14…19, y −15…−7,5 rel. K0); schräge Arme (3,5 mm, 30° zur Lenkachse) vom Ohr zur Säule. Die Arme und die Säule liegen innerhalb der Linie, die das Rad bei vollem Einschlag überstreicht (Abstand C-Hub ↔ Rad ≥ 1,96 mm in allen Stellungen). Oben ein Knoten vom Ohr zum Kugelauge der Sturzstange (Kugelkopf stehend, Kugelmitte E = 139,0 / ±81,6 / 71,6).
- **Achsschenkel:** Lagernabe Ø 16,1 (2 Lager 5x11x4 in Sitzen Ø 11,1, Lagerabstand 6 mm, Steg 2 mm mit Bohrung Ø 8), um `va_eps` = 1° gegen die Lenkachse geneigt; Kingpin-Augen Ø 8 × 6 oben (z 9,5…15,5 über K0) und unten (z −15…−9) mit Gewindeeinsätzen; Arme 8 mm zur Nabe; Spurhebel 8 × 6 mm nach hinten (links 21,6 mm unter 12,6° nach innen, rechts eigene Länge/Winkel) mit hängendem Kugelkopf.
- **Kingpin:** Passschraube ISO 7379 Bund Ø 4, Gewinde M3 (Kingpin-Schraube M3), oben von oben, unten von unten: Bund dreht im C-Hub-Ohr (Bohrung Ø 4,1), Gewinde im Einsatz des Achsschenkels; 0,2 mm Axialluft. Maße vorläufig.
- **Radachse** N1 (Pos. 8) gleiches Teil wie hinten: Gewindeende bündig mit der Radaußenseite (Skelett), offenes Becherende 7,7 mm innerhalb der Lenkachse, Kreuzstift (4WD) 1,3 mm außerhalb der Lenkachse = `antriebswelle_v_y` 89,80 mm (`radachse_v_spiel` −0,00).
- **Axiale Sicherung in v1 (ohne Antriebswelle):** Innenringe zwischen Becherschulter (innen) und Sechskant-Mitnehmer (außen, Stift, Radmutter), Außenringe beidseitig am 2-mm-Steg. Zug nach außen: Becher → inneres Lager → Steg; Druck nach innen: Mitnehmer → äußeres Lager → Steg. Die Lager stehen 0,5 mm über die Nabe vor (wie hinten).

![Schnitt Achsschenkel](images/vorderachse-achsschenkel-schnitt.png)

*Schnitt in der Ebene X = K0 (Blick von vorne, links), weiß: Achsschenkel, blau: Radachse mit Becher (Becher im „C“ des Achsschenkels, oben und unten die Kingpin-Augen), rechts davon die beiden Lagersitze mit dem Steg dazwischen (Lager selbst nicht dargestellt), grün: C-Hub-Ohren und Lasche, rot: Querlenker, grau: Rad.*

![Achsschenkel](images/vorderachse-achsschenkel.png)

*Linke Radseite von außen (Rad ausgeblendet): Achsschenkel mit Lagernabe und Spurhebel, C-Hub mit Säule und Kingpin-Ohren, Radachse, Querlenker.*

### Geometrie in Konstruktionslage (MECH-VAC-005, -006)

| Maß | Wert gemessen | Soll |
|---|---|---|
| Radmitte | Y **±108,50** / Z **41,00** (`va_w_y`, `va_w_z`) | ±108,5 / 41,0 |
| `radachse_v_spiel` (Skelett) | −0,00 mm | 0 ± 0,5 |
| Lenkachse in Radmittenhöhe | Y **±88,50** (K0 = 133,02 / ±88,50 / 40,65) | ±88,5 ± 0,5 |
| Nachlauf | **4,00°** (`va_nachlauf`), Nachlaufstrecke am Boden 2,84 mm | 4° |
| Spreizung | **0,00°** (`va_spreizung`) | 0° |
| Sturz | **−1,00°** | −1° |
| Vorspur | **0,07° Nachspur** je Rad (Radachse um 1° geneigt und um den Nachlauf gekippt; über die Spurstange auf 0 einstellbar: 0,03 mm) | 0° |
| Lenkrollradius | 20 mm (Lenkachse bei Spreizung 0 senkrecht, Boden Y 88,5) | – |

**Sturz einstellen:** Längenänderung der Sturzstange (Kugelmitte–Kugelmitte 49,46 mm, Spannschloss 3 × 32 mm) für den Sturz in Konstruktionslage (Prüfskript, `va_sl_dl`): −3° → **−1,52 mm**, −2° → −0,76 mm, −1° → 0, 0° → **+0,76 mm**, +1° → +1,52 mm. Gefordert −3° bis 0°: −1,52 bis +0,76 mm, Verstellweg des Spannschlosses ca. ±3 mm (wie hinten, `ha_sturzstange_verstell`) → reicht für ca. −5° bis +3°.

**Vorspur einstellen:** Spurstange links 43,55 mm, rechts 43,39 mm (Spannschloss 3 × 23 mm, 41,95 ± 3 mm). Der Spurhebel ist 21,6 mm lang, also ändert 1 mm Spurstange die Vorspur um ca. 2,65°. −2° bis +2° braucht ±0,75 mm, das Spannschloss erlaubt ca. +1,4 / −4,6 mm (Mitte 41,95). Einstellbereich mindestens ±2° ✓.

## Lenkung (MECH-VAC-007 bis -012)

### Aufbau

| Gelenkpunkt | Lage in Konstruktionslage (mm) | Höhe Z |
|---|---|---|
| Umlenkhebel links, Drehpunkt | (94,50 / 35,00), Lagerbock X 90,5…98,5 | Nabe 59,2…67,2 |
| Umlenkhebel rechts, Drehpunkt | (92,75 / −51,00), Lagerbock X 88,75…96,75 (vorne ≤ 97,75 ✓) | Nabe 59,2…67,2 |
| Spurstange innen links / rechts | (113,92 / 41,66) / (111,31 / −45,57), Kugelkopf hängend | 54,23 |
| Lenkgestänge links / rechts | (75,92 / 45,72) / (72,97 / −51,00), stehend | 72,23 |
| Servo-Anlenkung am rechten Umlenkhebel | (63,39 / −49,03), stehend auf 7,8 mm Erhöhung | 80,03 |
| Servo-Anlenkung am Saver-Arm | (59,93 / −9,82), hängend | 73,03 |
| Servoabtrieb (Achse) | (87,30 / −22,10), Abtrieb vorne am Servo (`va_servo_ab_dx` 10,2 mm, vorläufig) | Gehäuse bis 66,2 |
| Spurhebelkugel links | (111,68 / 83,80) | 43,46 |
| Kugel Sturzstange C-Hub / Brücke | (139,0 / 81,60) / (150,5 / 34,70) | 71,62 / 82,29 |

- Die Umlenkhebel drehen nur in den Lagern 5x8x2,5 (Innenringe auf einer Messinghülse 5 × 0,9 mit M3 × 14 in den Einsatz des Lagerbocks, unten ein Bund 0,5 mm nur unter dem Innenring, oben Scheibe DIN 433); alle Gelenke der Stangen sind Kugelköpfe 5 mm mit Kugelpfannen. Keine Kunststoffgleitlager im Lenkhebelsystem ✓.
- Stangen: Spurstangen 2 × 54539 3 × 23 (43,55 / 43,39 mm), Servo-Anlenkung 54539 3 × 23 (39,36 mm im Grundriss, 39,94 mm räumlich, Verstellweg nach unten nur ca. 1 mm), Lenkgestänge **96,76 mm** – zu lang für 54539, Ersatz Gewindestange M3 mit 2 Kugelpfannen (Stückliste Pos. 78). Sturzstangen 2 × 54539 3 × 32 (49,46 mm).
- Lenkgestänge: Die beiden Hebel bilden kein Parallelogramm (Abstand der Drehpunkte 86 mm, Hebel 18,6 bzw. 19,8 mm, leicht nach außen gespreizt). Das gleicht die unsymmetrische Lage der Lagerböcke (Y 35 / −51) aus und liefert einen Teil des Ackermann-Anteils.

### Lenkeinschlag, Ackermann, Servoweg (MECH-VAC-007, -008)

Prüfstellungen `va_lk_phi_l30` = −28,33° und `va_lk_phi_r30` = +28,30° (Umlenkhebel links), bestimmt so, dass das kurveninnere Rad in Konstruktionslage 30,00° um die Lenkachse einschlägt (Projektion im Grundriss 30,00° bzw. 29,88°). Ackermann-Soll (100 %) bei Radstand 266 mm und Lenkachsabstand 177,0 mm:

| innen | Ackermann ideal außen | Linkskurve: außen | Anteil | Servo | Rechtskurve: außen | Anteil | Servo |
|---|---|---|---|---|---|---|---|
| 10° | 8,97° | 9,08° | 89 % | −10,9° | 9,43° | 55 % | +11,5° |
| 20° | 16,33° | 16,81° | 87 % | −20,5° | 16,99° | 82 % | +22,3° |
| 25° | 19,59° | 20,09° | 91 % | −24,8° | 19,93° | 94 % | +27,2° |
| **30°** | **22,64°** | **22,92°** | **96 %** | **−28,6°** | **22,30°** | **105 %** | **+31,6°** |

Ackermann-Anteil = (innen − außen)/(innen − außen ideal). Bei vollem Einschlag 96 % bzw. 105 % (gefordert 80–120 %). Bei kleinen Einschlägen ist der Anteil kleiner (bei 10° rechts 55 %, absolut 0,5° Unterschied); MECH-VAC-008 bewertet den vollen Einschlag. Der Parameter **`va_ackermann`** (1 = 100 %) verstellt den Spurhebelwinkel linear (`va_ack_steig` 12° je 100 %, aus der Rechnung ca. 8,3 % je Grad; z. B. `va_ackermann` 0,8 → Spurhebel 2,4° weniger nach innen). Die Ist-Werte zeigt dieses Prüfskript; der Zusammenhang ist eine Linearisierung.

- **Servoweg:** −28,6° / +31,6° für 30° innen, also innerhalb ±40° ✓. Bei ±33° Servoweg schlägt das innere Rad ca. 34° ein; die Gelenke haben bis 6° Hebelweg über den vollen Einschlag hinaus keinen Totpunkt (Übertragung |sin| ≥ 0,47 in allen Gelenkvierecken).
- **Begrenzung des Einschlags:** über den Servoweg (Endpunkte im Sender, Servo-Endpunkte so einstellen, dass das innere Rad 30° erreicht: ca. −28,6° / +31,6° am Abtrieb, das sind ca. 64 % / 70 % des üblichen Servowegs ±45°). Bis zum vollen Einschlag schlägt kein Teil an (siehe Bewegungsprüfung).

![Voller Einschlag links](images/vorderachse-einschlag-links.png)

*Voller Einschlag links (linkes Rad 30°, rechtes 22,9°), von oben.*

![Voller Einschlag rechts](images/vorderachse-einschlag-rechts.png)

*Voller Einschlag rechts (rechtes Rad 30°, linkes 22,3°), von oben.*

### Failsafe-Mitte (MECH-VAC-012)

Servomitte (1500 µs, Failsafe Kanal 1) ↔ `va_servo_phi` = 0 ↔ beide Räder 0,00° (Konstruktionslage, Prüfmaße `va_lenk_l`, `va_lenk_r` = 0). Die mechanische Mitte wird ohne Servo-Trimmung am **Lenkgestänge** eingestellt: 1 mm Längenänderung dreht beide Umlenkhebel gegeneinander um ca. 2,9°, also ca. 3° Radeinschlag; ±2° Radeinschlag brauchen ±0,7 mm (Gewindestange mit Kugelpfannen, Verstellweg mehrere Millimeter) ✓. Die Spurstangen stellen die Vorspur je Rad ein (±0,75 mm für ±2°). Einstellen siehe [Montage](#montagefolge-einstellen-und-wartung-mech-vac-020).

### Servo-Saver (MECH-VAC-010)

![Servo und Saver](images/vorderachse-servo-saver.png)

*Servo mit Servohalter, Saver (Nabe auf dem Alu-Horn, Arm, Feder), Servo-Anlenkung zum rechten Umlenkhebel, Lenkgestänge quer über das Servo.*

- **Aufbau:** Alu-Servohorn 25Z doppelt (Savöx, Pos. 74) mit der Servo-Schraube auf dem Abtrieb. Darauf die gedruckte **Nabe** (Ø 18, 2 × M3 × 8 durch die Nabe in die Gewindelöcher des Horns, Lochkreis r 7,5 vorläufig) mit Zapfen Ø 7 und Gewindeeinsatz oben. Auf dem Zapfen der **Arm** (Scheibe Ø 18 × 4, Hebel 30,0 mm zur Kugel, Kugelkopf hängend). Zwischen Nabe und Arm zwei radiale **Rastnocken** (V-Profil, Flanke 45°, Höhe 1 mm, r 4…8,5) in passenden Kerben. Über dem Arm die **Druckfeder** (Pos. 79) mit Scheibe DIN 9021 und der Vorspannschraube M3 × 12 in den Einsatz des Zapfens. Die Vorspannung stellt man über die Schraube ein (Schraubensicherung, Pos. 67).
- **Ohne Überlast spielfrei:** Die Feder drückt den Arm mit ca. 47 N in die V-Kerben; die 45°-Flanken zentrieren den Arm in Drehrichtung und quer. Erst wenn das Moment am Arm die Flanken hochschiebt, dreht der Arm gegen die Nabe (Ausrasten) und rastet beim Nachlassen wieder in der Mitte ein (selbsthemmungsfrei, weil Flankenwinkel 45° > Reibwinkel 8,5…16,7°).

**Lenkmoment (Abschätzung, Rad im Stand auf Asphalt):**
- Radlast vorne statisch: 2,0 kg × 9,81 m/s² × 40 % / 2 = **3,92 N**.
- Reibradius: Lenkrollradius 20 mm (Spreizung 0), Nachlaufstrecke 2,84 mm, dazu die Aufstandsfläche (32 mm breit) → wirksam ca. **22 mm**.
- Moment je Rad um die Lenkachse: 0,8 × 3,92 N × 0,022 m = **0,069 Nm**.
- Übersetzung Lenkachse : Servo ca. 1 : 1 (30° Rad ↔ 28,6…31,6° Servo; bei kleinen Winkeln 10° ↔ 10,9…11,5°). Ungünstig 1,15 angesetzt: Servomoment = 2 × 0,069 × 1,15 = **0,16 Nm**, × 1,5 = **0,24 Nm** (Untergrenze für das Auslösemoment).
- Obergrenze: 70 % von 12 kg·cm (1,18 Nm) = **0,82 Nm**.

**Auslösemoment:** T = F · r_m · tan(α + ρ), F = Federkraft, r_m = 6,25 mm (mittlerer Radius der Nocken), α = 45°, ρ = atan μ.
- Soll `va_saver_moment` = **0,40 Nm** bei μ = 0,15 (gefettet): F = 0,40 Nm / (6,25 mm × tan 53,5°) = **47,3 N** (`va_sv_federkraft`).
- Streuung des Reibwerts: μ = 0,05 → 0,33 Nm; μ = 0,30 → 0,55 Nm. Beide liegen zwischen 0,24 und 0,82 Nm ✓. Während des Ausrastens (1 mm Hub, +5,6 N) steigt das Moment um ca. 12 %, höchstens 0,61 Nm ✓.
- **Feder** (Pos. 79): Federstahldraht EN 10270-1 SH, d = 1,2 mm, Da = 10 mm (D = 8,8 mm), L0 = 20 mm, 5,5 federnde Windungen (7,5 gesamt). Federrate R = G·d⁴/(8·D³·n) = 81 500 × 2,07 / (8 × 681,5 × 5,5) = **5,64 N/mm** (`va_sv_feder_r`). Vorspannweg 47,3 / 5,64 = 8,4 mm → Einbaulänge **11,6 mm** (`va_sv_feder_l`), beim Ausrasten 10,6 mm, Blocklänge 9,0 mm → Reserve **1,6 mm** (`va_sv_feder_reserve`). Schubspannung beim Ausrasten (52,9 N): τ = 8·F·D·k/(π·d³) ≈ 820 MPa (k ≈ 1,2), auf Block (62 N) ≈ 960 MPa < τ_zul ≈ 1 050 MPa (0,5 · Rm bei d 1,2 mm) ✓. Einstellbereich: ±2 mm Schraube ≈ ±0,17 Nm.
- 🔧 Prototyp: Saver löst bei festgehaltenem Rad aus, kehrt in die Mitte zurück, Spiel am Rad ≤ 1 mm am Reifenumfang; Vorspannung am Prototyp einstellen.

### Servohalter (MECH-VAC-011)

- L-förmiger Halter: hinterer Pfosten (X 50…56,7) mit den Einsätzen der Grundplatte (53,2 / −27,1; −17,1) und den Einsätzen der hinteren Servolasche; Seitenwand rechts neben dem Servo (Y −36,7…−33,2, 1 mm Luft zum Servo) bis X 99,5; zwei Füße Ø 6,4 um die Einsätze (85,0 / −37,2) und (95,0 / −37,2); vorne die Auflage der vorderen Lasche (X 98…104,6, Y −31…−12, Z 47,8…55) mit 2 Einsätzen. Laschen-Lochbild 49,5 × 10 mm und Laschenhöhe 26 mm über dem Gehäuseboden (`va_servo_loch_dx`, `va_servo_loch_dy`, `va_servo_lasche_z`, vorläufig, am Servo messen).
- **Servo tauschen:** Kugelpfanne der Servo-Anlenkung vom Saver abziehen und das Lenkgestänge an einem Ende aushängen (es liegt quer über dem Servo), 4 Laschenschrauben M3 × 8 lösen, Servo nach oben herausnehmen. Oberdeck, Schott und Grundplatte bleiben montiert ✓.
- **Kabel:** Das Servokabel kommt hinten unten aus dem Gehäuse (Standardservo) und läuft auf der Grundplatte nach hinten rechts zum Empfänger (Elektronikbereich, Raster); Führung mit Kabelbindern (Pos. 39) an den Rasterlöchern Y −49, X 40…80 (ELEK-FZG-005). Die Kabelführung selbst gehört zum Elektronikhalter.
- Abweichungen vom Mindestabstand siehe [Interferenz](#interferenz-und-abstände).

## Federweg und Kinematik (MECH-VAC-013, -014)

Prüfstellungen `va_dphi_aus` = −16,437° und `va_dphi_ein` = +31,782° (Prüfskript: `va_radhub` = −11,667 bzw. +23,333 mm).

| Stellung | Radhub | Radmitte Y / Z | Sturz | Lenkwinkel bei Geradeaus (+ = links) links / rechts | Änderung gegen Konstruktionslage | Dämpfer (Augenabstand) |
|---|---|---|---|---|---|---|
| ausgefedert | −11,67 | 103,93 / 29,33 | −0,09° | +0,38° / +0,34° | **+0,31° / +0,41°** | 56,00 mm (= ausgefedert, Endanschlag) |
| halb aus | −5,96 | 106,60 / 35,04 | −0,63° | +0,17° / +0,05° | +0,10° / +0,12° | 53,58 |
| Konstruktionslage | 0 | 108,50 / 41,00 | −1,00° | +0,07° / −0,07° | 0 | 51,12 |
| halb ein | +11,83 | 109,86 / 52,83 | −1,33° | +0,09° / −0,00° | +0,02° / +0,07° | 46,39 |
| eingefedert | +23,33 | 108,11 / 64,33 | −1,16° | +0,29° / +0,30° | **+0,22° / +0,37°** | 42,10 (Hub 13,90 von 14) |

- **Bump-Steer ≤ 0,5° je Rad ✓** (größte Änderung 0,41° rechts ausgefedert). Die Vorspuränderung ist bei beiden Rädern gleichgerichtet (beide nach links), weil die Spurstangen links und rechts verschieden liegen.
- **Sturzänderung:** −1,00° → −0,09° ausgefedert, −1,33° halb eingefedert, −1,16° voll eingefedert.
- **Den Federweg begrenzt der Dämpfer ✓:** Die obere Dämpferaufnahme ist so berechnet (`va_du_z`), dass der Dämpfer bei −11,67 mm genau ausgezogen ist (56,0 mm); bei +23,33 mm sind 13,90 von 14 mm Hub verbraucht (`va_daempfer_reserve` 0,10 mm). In beiden Endlagen schlägt kein Teil an (Bewegungsprüfung).
- **Hebelverhältnis Rad : Dämpfer = 35 / 13,90 = 2,52** (`va_hebel`). TT-02B vorne (aus der Anleitung abgeschätzt wie hinten, vorläufig): ca. 1,5 (`va_hebel_tt02b`). 2,52 ≥ 1,5 ✓. Folge: Die Federrate am Rad ist (1,5/2,52)² ≈ 0,35 der TT-02B-Federung, die Vorderachse wird mit den Bausatzfedern deutlich weicher; härtere Federn bzw. dickeres Öl einplanen (Abstimmung nicht Teil dieser Anforderung).
- **Dämpferlage** (weicht von der Skelett-Hülle ab, erlaubt): unten X 172,0 / Y ±52,04 / Z 40,68 an der Querlenkerlasche (15,77 mm von der Querlenkerachse, 7 mm über der Ebene), oben X 172,0 / Y ±44,00 / Z 91,15 an der Vorderseite der Dämpferbrücke mit Distanzhülse 6 mm, oben 9,1° nach innen geneigt. Der Dämpferkörper stand 4 mm über die Plattenvorderkante (X 172) hinaus (wie hinten); seit Grundplatte v12 endet die Platte bei X 177.
- **4WD (Information):** Gelenkabstand der Antriebswelle N3 über den Federweg 58,02…60,12 mm (Knochen 60 mm): eingefedert −2,07 mm. Das liegt knapp am vorläufigen Schiebeweg ±2 mm der Hinterachse und ist bei 4WD zu prüfen.

![Ausgefedert](images/vorderachse-federweg-aus.png)

*Ausgefedert (Radhub −11,67 mm), von vorne, rechtes Rad ausgeblendet.*

![Eingefedert](images/vorderachse-federweg-ein.png)

*Eingefedert (Radhub +23,33 mm), von vorne.*

## Dämpferbrücke (MECH-VAC-015)

- Platte 6 mm (`va_db_dicke`) X 156,5…162,5 vor dem Frontschott, 4 × M3 × 10 Zylinderkopf von vorne in die Einsätze des Schotts (Y ±10 / Z 36 und 73). Mittelteil Y ±22,36, Z 31…79; Arme zu den Kugelköpfen der Sturzstangen (Rückseite, Kugelmitte 150,5 / ±34,70 / 82,29, Einsatz durch die Platte) und zu den oberen Dämpferaugen (Vorderseite, Y ±44 / Z 91,15, M3 × 25 + Distanzhülse + Stoppmutter).
- **Fräsgerecht (Prüfskript):** 10 Ebenen, alle parallel oder senkrecht zu X; 20 Zylinder, alle mit Achse parallel zu X; keine anderen Flächentypen. Radien: Bohrungen 1,6, Einsätze 2,0, alle Kanten parallel zu X mit `va_db_r` = **2,0 mm** verrundet (Innenradien ≥ 1,5 ✓), Augen 7,0. Keine Hinterschnitte, Werkzeugzugang von einer Seite.
- **Abstände:** Grundplatte **2,00 mm**, Oberdeck 34,5 mm, Dämpfer 1,80 mm, Querlenkerbock 4,67 mm, Servo 59 mm, XT60 67 mm. Interferenz mit Skelett, Grundplatte, Oberdeck: 0. Lochbilder Rammschutz/Karosseriehalter damals (164,5 / ±8; ±22): 2,0 mm vor der Brücke; seit Grundplatte v12 (Entscheidung 2026-11-13) bei (169,35 / ±8; ±22), **6,85 mm** vor der Brücke; der Dämpfer liegt dort bei Y ±37…±59 (neben ±22).
- **Getriebehülle:** Die Brücke überschneidet die Hülle `antrieb-getriebe-vorne` mit einer 0,5 mm dicken Scheibe (1 106 mm³), weil die Hülle bis X 157 reicht, das Schott (wie das Hinterachsgetriebe) aber bei X 156,5 endet. Ein gespiegeltes Hinterachsgetriebe endet ebenfalls bei 156,5; gewollt.

## Interferenz und Abstände

**Bewegungsprüfung:** Fusion `analyzeInterference` über alle Körper der Vorderachse und die Skelett-Körper Grundplatte (Druck), Oberdeck, Fußflächen, XT60, UBEC, Regler, Akku-Entnahmeweg, Servo, Kardanwelle, Vorderachsgetriebe-Hülle und Wellenräume vorne, in **9 Stellungen** (ausgefedert / Konstruktionslage / eingefedert × voll links / geradeaus / voll rechts). Die von dieser Baugruppe ersetzten Skelett-Hüllen (Räder, Radräume, Radachsen, Antriebswellen und Dämpfer vorne) sind ausgenommen; an ihre Stelle treten die bewegten eigenen Hüllkörper. Zeitleiste in allen Stellungen ohne Fehler, Prüfmaße der Gelenklängen 0.

**Gewollte Überschneidungen** (in allen Stellungen):

| Überschneidung | Volumen | Begründung |
|---|---|---|
| Frontschott ↔ Vorderachsgetriebe-Hülle | 22 528,5 mm³ | Schott liegt im Getriebebauraum (Rest = Oberdeck-Auflage, siehe oben) |
| Querlenkerböcke ↔ reservierte Fußflächen, Lagerböcke ↔ Fußflächen | je 2 094,7 / 1 769,2 mm³ | Bock steht in seiner Fußfläche |
| Dämpferbrücke ↔ Getriebehülle | 1 106,2 mm³ | 0,5-mm-Scheibe X 156,5…157 |
| Rad ↔ Radachse; Radachse ↔ N3-Hülle; N3-Hülle ↔ Getriebehülle | 863 / 1 414 / 1 756 mm³ | Achse im Mitnehmer, Knochen im Becher, Knochen im Diff-Becher |
| Servo-Abtrieb ↔ Servo, ↔ Servohorn | 57 / 99 mm³ | Abtrieb im Gehäuse bzw. im Horn |
| Saver-Nabe ↔ Feder (Hülle) | 129,6 mm³ | Zapfen in der Feder |
| eigene Teile ↔ Wellenräume vorne (Skelett) | Achsschenkel 3 797, C-Hub 1 297, Querlenker 410, Sturzstange 298, Rad 42 050, Radachse 5 213 mm³ | Der Skelett-Wellenraum ist die Hülle aller Lagen von Radachse und Welle (Ø 20,6 mit Zuschlag, mit Lenkeinschlag); Achsschenkel und C-Hub umschließen die Radachse zwangsläufig. Den 4WD-Durchgang prüft stattdessen die bewegte N3-Hülle (unten). |
| Kugelpfanne ↔ Auge ihres Kugelkopfs (Spurstange ↔ Achsschenkel/Umlenkhebel) | 0,00 mm³ (Berührung) | Pfannen-Hülle (Zylinder Ø 9 × 9) am Auge des eigenen Kugelkopfs |

**Nicht gewollte Überschneidungen (offen, siehe Abweichungen):**

| Überschneidung | Stellung | Volumen | Bewertung |
|---|---|---|---|
| Servolasche vorne (Servo) ↔ Getriebehülle; Servohalter (vordere Auflage) ↔ Getriebehülle | alle | 180,0 / 443,1 mm³ | Die vordere Servolasche (X 97,5…104,6) liegt zwangsläufig in der Hülle, weil das Servo im Skelett 1,5 mm hinter der Hülle steht und die Hülle nur das Gehäuse kennt. Ein gespiegeltes Hinterachsgetriebe (Gehäuse ab X 109,5, Lagerbock bis Y ±15,8 unter Z 34) bleibt frei. |
| Servohalter ↔ UBEC-Hülle | alle | 12,35 mm³ | Fuß um den Einsatz (85 / −37,2): das Loch der Grundplatte liegt nur 2,55 mm von der Ecke der UBEC-Hülle; Einsatz Ø 4 + 1,2 mm Wand geht nicht ohne Überschneidung. Die Hülle hat 2 mm Zuschlag, zum echten UBEC bleiben 1,3 mm. |
| Spurstange rechts (Pfanne innen) ↔ Servolasche vorne | eingefedert, voll rechts | 1,0 mm³ | Ecke der zylindrischen Pfannen-Hülle; vorläufige Laschenhöhe; in allen anderen Stellungen frei (Konstruktionslage 9,2 mm, ausgefedert voll rechts 0,09 mm) |
| Lenkgestänge (Pfanne links) ↔ Akku-Entnahmeweg | voll rechts | 10,5 mm³ | Der Entnahmeweg gilt bei Geradeausstellung; MECH-VAC-009 nennt ihn nicht. In Geradeausstellung 2,28 mm frei. Vorgabe für den Akkuhalter. |
| N3-Hülle (4WD, mit 2 mm Zuschlag) ↔ Achsschenkel / Querlenker | ausgefedert, voll links | 8,0 / 0,32 mm³ | **Mit der echten Kugel Ø 10 (ohne Zuschlag, `va_n3_d` = 10 mm) in allen 9 Stellungen 0** (Prüfskript). Der Durchgang für die spätere Antriebswelle bleibt frei. |

**Kleinste Abstände über alle Prüfstellungen** (Mindestabstand ≥ 1 mm gefordert für Böcke, Lenkhebelsystem, Servohalter/Servo und Brücke gegen das Skelett):

| Paar | min. | Soll |
|---|---|---|
| Querlenkerböcke ↔ Wellenräume / Skelett (XT60, Servo) / Schott / Spurstange / N3 | **7,51** / 12,5 / 4,64 / 2,78 / 7,71 mm | ≥ 3 / ≥ 1 |
| Umlenkhebel ↔ XT60 / Servo / UBEC / Oberdeck / Schott / Dämpferbrücke | 18,23 / **1,75** / 10,87 / 25,19 / 5,29 / 38,77 mm | ≥ 1 |
| Lagerböcke ↔ XT60 / Servo / UBEC / Getriebehülle / Servohalter | **1,00** / 10,80 / 6,25 / 2,20 / 2,60 mm | ≥ 1 |
| Lenkgestänge ↔ Servo / UBEC / XT60 / Oberdeck / Kardanwelle / Saver-Nabe / Servo-Anlenkung | 4,53 / 18,53 / 26,73 / 10,47 / 6,35 / 0,27 / 2,52 mm | ≥ 1 (Saver-Nabe: internes Teil, kollisionsfrei) |
| Servo-Anlenkung ↔ Servo / Oberdeck / XT60 / UBEC / Kardanwelle / Servohalter | **1,84** / 5,77 / 27,81 / 21,41 / 5,19 / 13,03 mm | ≥ 1 |
| Servo-Saver ↔ Oberdeck / Servo / Kardanwelle / Getriebehülle | **1,17** / 3,00 / 8,18 / 2,70 mm | ≥ 1 |
| Servohalter ↔ Servo / Kardanwelle / Lagerbock / Schott / Oberdeck | 0,50 (Servo sitzt im Halter) / 2,11 / 2,60 / 6,90 / 29,27 mm | |
| Spurstange ↔ Rad / Querlenkerbock / Getriebehülle / N3 | **0,32** / 2,78 / 1,15 / 3,97 mm | kollisionsfrei |
| Sturzstange ↔ Rad / Dämpferbrücke / Schott | **0,33** / 0,58 (Pfanne an ihrem Kugelkopf) / 6,41 mm | kollisionsfrei |
| C-Hub ↔ Rad / Radachse / Achsschenkel | 1,96 / 3,05 / 0,20 (Kingpin-Luft) mm | |
| Achsschenkel ↔ Rad / Radachse | 0,22 (Nabe im Felgeninnenraum) / 0,35 mm | |
| Querlenker ↔ Rad / Radachse / Grundplatte | 8,24 / 3,63 / > 0 (ausgefedert, Interferenz 0) mm | |
| Dämpferbrücke ↔ Grundplatte / Dämpfer | 2,00 / 1,80 mm | ≥ 1 |

Die knappsten Werte zu Rad und Felge hängen am vorläufigen Felgeninnenraum Ø 50 und an der eckigen Pfannen-Hülle; sie stehen bei den Messpunkten.

## Schnittstellen zur Grundplatte

| Prüfung | Ergebnis (gemessen) |
|---|---|
| Frontschott | Einsätze (114,0 / ±18,0) und (152,0 / ±18,0); Oberdeck (115,0 / ±5,0), Auflage Z 84,200 |
| Querlenkerböcke | Einsätze (115,0 / ±30,5; ±39,5) und (151,0 / ±30,5; ±39,5); Fußflächen X 110…120 und 146…156, Y ±27…±43 |
| Lagerböcke | links Einsätze (94,5 / 30,5; 39,5), Fußfläche X 90,5…98,5; rechts (92,75 / −46,5; −55,5), Fußfläche X 88,75…96,75 (≤ 97,75 ✓) |
| Servohalter | Einsätze (53,2 / −27,1; −17,1), (85,0 / −37,2), (95,0 / −37,2) |
| Befestigung | alle Teile auf der Grundplatte mit M3 × 8 Senkkopf von unten in Gewindeeinsätze; die Grundplatte ist unverändert |

## Lasten (MECH-VAC-017)

Annahmen: 2,0 kg, Sprung 5 g, Vorderachse 40 % → **19,6 N senkrecht je Rad**, Seitenstoß und Frontalstoß am Rad je **50 N**. PETG ca. 47 MPa, Prusament PC ca. 60 MPa. Biegebalken σ = M/W, W = b·h²/6.

| Teil, Stelle | Last | Moment | Querschnitt | σ | Sicherheit PETG (PC) |
|---|---|---|---|---|---|
| **Querlenker, Dämpferlasche** (Sollbruchstelle) | Dämpferkraft 19,6 N × 2,52 / cos 9° = 50 N, Hebel Plattenkante X 145,5 ↔ Auge X 168,5 = 23 mm | 1 150 N·mm | 8 × 8 mm, W 85,3 mm³ | 13,5 MPa | **3,5** (4,4) |
| Querlenker, Platte innen | 19,6 N am Bolzen, Hebel bis zur Rohrkante ca. 39 mm, Platte 25 × 5 mm | 765 N·mm | W 104 mm³ | 7,4 MPa | 6,4 |
| Querlenker, Seitenstoß 50 N | Druck in der Platte 18,4 × 5 mm | – | 92 mm² | 0,5 MPa | > 50 |
| C-Hub, Knoten Ohr ↔ Kugelauge | Kraft Sturzstange bei 50 N Seitenstoß: 50 × 27 / 44,6 = 30 N, als Schub/Zug durch den Knoten 8 × 3,4 mm | – | 27 mm² | 1,1 MPa | > 40 |
| C-Hub, Lasche/Steg unten | 50 N über den Steg 8 × 3,4 mm zur Lasche | – | 27 mm² | 1,9 MPa | > 20 |
| Achsschenkel, Arme zu den Kingpins | 50 N am Aufstandspunkt, Kingpin-Abstand 31 mm → ca. 70 N je Auge, Hebel Auge ↔ Nabe 8 mm | 560 N·mm | 8 × 6 mm, W 64 mm³ (hochkant 48) | 11,7 MPa | 4,0 (5,1) |
| Kingpin-Ohr C-Hub (Lochleibung) | 70 N auf Bund Ø 4 × 4 mm | – | 16 mm² | 4,4 MPa | > 10 |
| Querlenkerbock | Lagerkraft ca. 12 N, Hebel 9 mm | 108 N·mm | 10 × 16 mm, W 427 mm³ | 0,25 MPa | > 100 |
| Dämpferbrücke, Arm zum Dämpferauge | 50 N, Hebel 21,6 mm (Mittelteil ↔ Auge) | 1 080 N·mm | 6 × 12 mm, W 144 mm³ | 7,5 MPa | 6,3 |
| Frontschott | 2 × 50 N über 4 Schrauben in die Vorderwand, Rahmen 7 × 6 mm | < 600 N·mm | W 49 mm³ | < 12 MPa | > 3,9 |

- **Ergebnis:** Kleinste Sicherheit **3,5 an der Dämpferlasche des Querlenkers** (≥ 1,5 ✓). C-Hub, Achsschenkel, Böcke, Schott und Brücke haben alle eine höhere Sicherheit (≥ 3,9). Bei Überlast bricht zuerst der Querlenker (billiges Druckteil). 🔧 Sprungtest am Prototyp.
- **Lenkung, begrenzt durch den Servo-Saver:** größtes Auslösemoment 0,61 Nm (μ 0,3, ausrastend). Kraft an der Saver-Kugel 0,61 / 0,030 = 20 N; Umlenkhebel rechts, Arm zur Servo-Kugel 29,4 mm: 600 N·mm, Arm 8 × 6 mm (W 64 mm³) → 9,4 MPa, Sicherheit **5,0**; Erhöhung Ø 6,4 × 7,8 mm: 20 N × 13,8 mm = 276 N·mm, W ≈ 21,8 mm³ → 12,7 MPa, Sicherheit **3,7**. Spurstangenkraft höchstens ca. 28 N; Spurhebel 21,6 mm: 605 N·mm, 8 × 6 mm → 9,5 MPa, Sicherheit **5,0**. Alle ≥ 1,5 ✓. Lagerbock (Säule 8 × 16 mm, Höhe 30 mm, 28 N): 840 N·mm / 171 mm³ = 4,9 MPa, Sicherheit 9,6.

## Druckhinweise (MECH-VAC-016)

| Teil | Lage auf dem Bett | Stützen | Hinweis |
|---|---|---|---|
| Frontschott | Unterseite (Z 29) | keine (Querriegel der Oberdeck-Auflage als Brücke über 31 mm) | Einsätze der Brücke waagerecht (Bogen) |
| Querlenkerbock (4 ×) | Seitenfläche (X), Sackloch nach oben | keine | wie hinten |
| Querlenker | Plattenunterseite | wenig (Rohr, Lasche) | Lasche in Schichtrichtung belastet |
| C-Hub | Säulen-Vorderseite (X) | unter den Kingpin-Ohren | Kingpin-Bohrungen Ø 4,1 nach dem Druck mit dem Bund prüfen (`va_kp_spiel`) |
| Achsschenkel | äußere Stirnfläche der Lagernabe (Nabenachse senkrecht) | unter Spurhebel und oberem Auge | Lagersitze rund und maßhaltig |
| Dämpferbrücke | flach (X-Fläche) | keine | 2,5D |
| Umlenkhebel | Hebelplatte unten | keine (links), rechts keine (Erhöhung steht auf der Platte) | Lagersitze senkrecht |
| Lagerbock | Fußfläche | keine | Bund oben |
| Servohalter | Unterseite | unter der vorderen Laschenauflage | |
| Saver-Nabe | Hornseite unten | keine | Rastnocken oben, 45° |
| Saver-Arm | Oberseite unten (Kerben oben) | keine | |

- **Bauraum (MECH-FZG-003):** größtes Teil Dämpferbrücke 102,0 × 67,2 × 6,0 mm, alle Teile ≤ 256 mm (Hüllquader oben). 🔧 Slicer-Prüfung durch den Nutzer.
- **Wandstärken** (Soll ≥ 1,2 mm, an Lagersitzen ≥ 2 mm): Radlager radial 2,5 mm, Steg 2 mm; Umlenkhebel-Lager radial 2,0 mm; Einsätze: Kingpin-Augen 2,0, Spurhebel/Umlenkhebel-Augen 2,0, Erhöhung Servo-Kugel 1,2, Kugelauge C-Hub 2,5, Saver-Zapfen 1,5, Servohalter-Füße 1,2, Querlenkerbock 1,5 (wie hinten) bzw. 1,45 zur Stiftbohrung, Schott-Bodenschienen 1,64; C-Hub-Arme 3,5 mm, Querlenkerplatte 5 mm, Querlenkerrohr 1,9 mm.
- **Toleranzen:** Bohrungen M3 Ø 3,2 (`va_bohrung`), Lagersitze + `va_lager_spiel` 0,1 mm (vorläufig, Probedruck), Stift im Bock Ø 3,1, Kingpin-Bund Ø 4,1 (`va_kp_spiel`), Saver-Zapfen 7,0 / Bohrung 7,2. Gewindeeinsätze Pos. 30 (Bohrung Ø 4 × 6 vorläufig).
- **Material:** PETG für den Test, Prusament PC für das fertige Modell (Saver-Teile nur PC).

## Fräsbarkeit (MECH-VAC-023, SOLL)

- **Dämpferbrücke:** 2,5D, Prüfskript ohne Befund (siehe oben).
- **Querlenkerböcke:** wie hinten, Profil in X extrudiert, zwei Aufspannungen.
- **Lagerböcke:** Quader 8 × 16 mit Bund und Bohrungen von oben/unten: 2,5D in zwei Aufspannungen (Innenradien entfallen, keine Innenecken).
- **Umlenkhebel:** Platte mit Nabe und Augen, alle Achsen senkrecht: 2,5D von oben bzw. unten; links in einer, rechts in zwei Aufspannungen (Erhöhung). Innenecken zwischen Arm und Nabe sind scharf (Union aus Quader und Zylinder) – für Alu mit r ≥ 1,5 nachziehen (Abweichung, Phase 3).
- **Servohalter:** nicht 2,5D in einer Aufspannung (Laschenauflage vorne und Füße auf verschiedenen Höhen), als Druckteil vorgesehen; Abweichung begründet (kein Alu-Teil geplant).

## Montagefolge, Einstellen und Wartung (MECH-VAC-020)

1. Gewindeeinsätze einschmelzen: Schott 10, Böcke je 2, Querlenker je 1, C-Hub je 1, Achsschenkel je 3, Umlenkhebel links 2 / rechts 3, Lagerböcke je 3, Servohalter 8, Saver-Nabe 1, Saver-Arm 1, Dämpferbrücke 2.
2. Schott mit 4 × M3 × 8 Senkkopf von unten, Lagerböcke (je 2 × M3 × 8 Senkkopf von unten), Servohalter (4 × M3 × 8 Senkkopf von unten). Dämpferbrücke mit 4 × M3 × 10 von vorne ans Schott; Kugelköpfe der Sturzstangen hinten einschrauben.
3. Achsschenkel: Lager einpressen, Radachse von innen durchstecken, Kugelkopf des Spurhebels von unten. In den C-Hub setzen, Kingpin-Passschrauben oben von oben und unten von unten durch das C-Hub-Ohr in die Einsätze des Achsschenkels (mittelfeste Sicherung), Kugelkopf der Sturzstange auf den C-Hub.
4. C-Hub mit M3 × 25 + Stoppmutter in die Gabel des Querlenkers. Querlenker mit Stift 3 × 40 zwischen die Böcke, Böcke mit je 2 × M3 × 8 Senkkopf von unten (Stift gefangen).
5. Dämpfer unten M3 × 14 in die Lasche, oben M3 × 25 + Distanzhülse 6 + Stoppmutter an die Brücke. Sturzstange einhängen.
6. Umlenkhebel: Lager einpressen, Kugelköpfe (Spurstange hängend, Lenkgestänge und Servo-Anlenkung stehend) einschrauben, mit Messinghülse, Scheibe DIN 433 und M3 × 14 auf den Lagerbock. Lenkgestänge, Spurstangen einhängen.
7. Servo in den Halter (4 × M3 × 8 an den Laschen), Servo auf Mitte (1500 µs, Sender ohne Trimmung), Alu-Horn quer zur Fahrtrichtung aufsetzen, Saver-Nabe mit 2 × M3 × 8 auf das Horn, Arm nach hinten auf den Zapfen (Nocken in die Kerben), Feder, Scheibe DIN 9021, Vorspannschraube M3 × 12 bis zur Einbaulänge 11,6 mm. Servo-Anlenkung einhängen.
8. **Lenkungsmitte einstellen:** Servo auf 1500 µs; Lenkgestänge so einstellen, dass beide Umlenkhebel in Mittellage stehen (Spurstangenkugeln auf gleichem X), dann die Spurstangen so, dass beide Räder geradeaus (Vorspur 0) stehen. Die Servo-Anlenkung (54539) stellt die Saver-Stellung ein. Danach Endpunkte im Sender: inneres Rad 30° (≈ 28,6° / 31,6° am Abtrieb).

**Wartung:**
- **Querlenker, C-Hub, Achsschenkel tauschen:** Dämpfer unten lösen, Sturzstange und Spurstange abziehen, 4 Bockschrauben von unten lösen → Querlenker mit Böcken, Stift, C-Hub und Achsschenkel herausnehmen. Achsschenkel einzeln: 2 Kingpin-Schrauben. Schott, Oberdeck, Grundplatte bleiben montiert ✓.
- **Umlenkhebel tauschen:** Pfannen abziehen, Achsschraube M3 × 14 von oben lösen ✓.
- **Servo tauschen:** siehe Servohalter ✓.

## Bodenfreiheit (MECH-VAC-021, SOLL)

In Konstruktionslage liegen die tiefsten Druckteile bei **Z 21,22** (C-Hub, unteres Kingpin-Ohr) und Z 23,0 (Querlenkergabel), also über Z 20 ✓. **Darunter liegt aber der Kopf der unteren Kingpin-Passschraube**: Unterseite Ohr 21,2 − Kopf 3 mm (vorläufig) ≈ **Z 18,2** < 20. Grund: Die Lenkachse läuft für 4WD durch den Becher der Radachse (Ø 17 bis Z 32,5); darunter stapeln sich Luft 0,5, Achsschenkel-Auge 6 (Gewindeeinsatz), Luft 0,2, C-Hub-Ohr 4 und der Kopf. Abweichung, siehe offene Punkte.

## Masse (MECH-VAC-022, SOLL)

19 Druckteile **139,3 g** in PETG (100 % Füllung, obere Grenze), 131,6 g in PC ✓ (≤ 150 g).

## Parametertest (MECH-VAC-001)

| Test | Ergebnis |
|---|---|
| Ersatztest eigene Parameter (gleichzeitig): `va_ackermann` 0,8, `va_nachlauf` 6°, `va_sturz` −2°, `va_lager_spiel` 0,3, `va_ql_z` 39, `va_db_dicke` 8, `va_radlager_abstand` 6,5, `va_sv_feder_l0` 22, `va_servo_loch_dx` 48, `va_sh_wand` 4, `va_kugel_h` 6,5, `va_einsatz_d` 4,2 mm | Zeitleiste (911 Elemente) **ohne Fehler**; Prüfmaße der Gelenklängen 0,000; Lenkachse Y 88,51; `va_daempfer_reserve` 0,05 mm; zurückgesetzt ohne Fehler |
| Stellungen (9 Bewegungsprüfungen), Sturzverstellung `va_sl_dl` −1,52…+1,52 mm, `va_n3_d` 10 mm | ohne Fehler |
| **`radstand` 280 mm im Skelett** | **offen:** Dafür muss das Skelett als neue Version mit 280 mm und danach wieder mit 266 mm gespeichert werden (bei der Hinterachse Nutzerentscheidung 2026-11-01, Skelett v13/v14). Die Freigabe dieser Anforderung umfasst nur das Speichern der Vorderachse; der Test ist deshalb nicht gemacht. Alle Lagen in X hängen an `achse_x` (Skelett) bzw. an Skelett-Formeln (`va_lk_x`, `va_lk_x_rechts`, `va_sh_*`, `va_servo_ab_x`), die Lagerböcke und der Servohalter wandern mit der Grundplatten-Formel. |

## Messpunkte bei Lieferung

Alle vorläufigen Maße messen, Parameter ersetzen, dann `va_dphi_aus`/`va_dphi_ein` (bis `va_radhub` = −11,667/+23,333), `va_lk_phi_l30`/`va_lk_phi_r30` (inneres Rad 30°) neu bestimmen und die Bewegungsprüfung (9 Stellungen) wiederholen:

1. **Radachse N1 vorne:** Becherlänge/-durchmesser (`va_n1_becher_l`, `va_n1_becher_d`), Lage des Mitnehmerstifts (`va_u_nabe`, `va_radlager_abstand`), Länge (`radachse_v_l`, Skelett).
2. **Rad vorne:** Felgeninnendurchmesser und -tiefe (`va_felge_innen_d`); davon hängen Spurstange ↔ Rad 0,32 mm, Sturzstange ↔ Rad 0,33 mm (voller Einschlag) und Achsschenkel ↔ Rad 0,22 mm ab.
3. **CVA-Dämpfer vorne:** Augenabstand ausgefedert (`va_daempfer_l_aus` 56), Hub (`va_daempfer_hub` 14), Augen (`va_d_auge_*`), Körper (`va_d_koerper_d`, `va_d_stiel_d`); danach `va_ql_dl` so wählen, dass `va_daempfer_reserve` klein und ≥ 0 bleibt.
4. **Kugelköpfe/Pfannen/Spannschlösser 54539:** Kugelhöhe (`va_kugel_h`), Pfannen (`va_pfanne_d`, `va_pfanne_ueber`), Verstellweg; Längen 3 × 32 für 49,46 mm und 3 × 23 für 43,55 / 43,39 / 39,94 mm einstellbar? (Servo-Anlenkung liegt am unteren Ende.)
5. **Servo Savöx SC-1258TG+:** Laschen-Lochabstand und -höhe (`va_servo_loch_dx`, `va_servo_loch_dy`, `va_servo_lasche_z`, `va_servo_lasche_l`), Lage und Höhe des Abtriebs (`va_servo_ab_dx`, `va_servo_abtrieb_h`). Von der Laschenhöhe hängt die Berührung Spurstange ↔ Lasche (1,0 mm³) ab.
6. **Alu-Servohorn:** Nabenhöhe, Lochkreis (`va_horn_loch_r` 7,5 – ggf. nachbohren), Arme auf 24 mm kürzen.
7. **Kingpin-Passschraube:** Kopf (`va_kp_kopf_d`, `va_kp_kopf_h`), Bundlänge; Bodenfreiheit neu bewerten.
8. **Feder Servo-Saver:** Federrate am Teil, Einbaulänge für 0,4 Nm; 🔧 Auslösemoment am Prototyp messen (Hebelwaage am Rad) und Vorspannung einstellen.
9. **Lager 5x11x4 / 5x8x2,5:** Sitze per Probedruck (`va_lager_spiel`); Innenring-Durchmesser 5x8 für den Bund (`va_ulh_bund_d` 6,4).
10. **Gewindeeinsätze:** Bohrung und Länge (`va_einsatz_d`, `va_einsatz_t`).

## Vorgaben an spätere Baugruppen

- **Vorderachsgetriebe 4WD:** ersetzt das Frontschott auf dem Lochbild (114 / 152, ±18), Oberdeck-Auflage bis Z 84,2 an (115 / ±5), Anlage der Dämpferbrücke an der Vorderseite X 156,5 mit Einsätzen (±10 / 36 und 73). Freihalten: vordere Servolasche und Servohalter-Auflage (X 97,5…104,6, Y −31…−12, Z 47,8…57,5), die Spurstangen (Y ≥ 30 links, ≤ −35 rechts, Z ca. 50…60), die Sturzstangen (X 139…150,5, Z 66…87). Die Antriebswelle N3 (echte Kugel Ø 10) ist in allen Stellungen frei; Gelenkabstand 58,0…60,1 mm über den Federweg prüfen.
- **Karosseriehalter und Rammschutz:** Lochbilder seit Grundplatte v12 (Entscheidung 2026-11-13) bei (169,35 / ±8; ±22), **6,85 mm** vor der Dämpferbrücke (vorher 164,5, nur 2 mm); Plattenende X 177. Davor bzw. daneben die Dämpfer (X 163…181, Y ±37…±59, Z 36…96) und die Querlenkerlaschen bis X 168,5. Halter dort nur zwischen Y ±30 und über/unter den Dämpfern. Die Prüfung der verlängerten Platte gegen diese Baugruppe (9 Stellungen mit Lenkeinschlag) steht in `docs/grundplatte-oberdeck.md`: Dämpfer ≥ 4,60 mm, Querlenker ≥ 6,05 mm, Räder ≥ 26,13 mm.
- **Elektronikhalter / Akkuhalter:** Das Lenkgestänge kreuzt bei voller Rechtslenkung den Akku-Entnahmeweg an der Vorderkante (X ≈ 70…75, Y ≈ 40…50, Z ≈ 67…77); der Akku wird bei Geradeausstellung entnommen. Servokabel nach hinten rechts zum Empfänger. Über dem Servo (Z 66…84) und dem UBEC (Z 50…85, X 55…80) laufen Lenkgestänge, Servo-Anlenkung und Saver-Arm; Halter dort nur bis Z 49.

## Abweichungen und offene Punkte

1. **Servolasche vorne in der Vorderachsgetriebe-Hülle** (180 mm³ Servo, 443 mm³ Servohalter): MECH-VAC-011 verlangt Interferenz 0 zum Skelett. Ursache ist das Skelett (Servo-Hülle ohne Laschen, 1,5 mm vor der Getriebehülle). Das echte gespiegelte Getriebe bleibt frei. Nutzerentscheidung nötig (Empfehlung: als gewollt abnehmen und die Getriebehülle beim 4WD-Getriebe an der Servoseite verkürzen).
2. **Servohalter ↔ UBEC-Hülle 12,35 mm³** (Lochbild (85 / −37,2) liegt 2,55 mm von der Hüllen-Ecke); zum echten UBEC 1,3 mm. Nutzerentscheidung nötig (Empfehlung: abnehmen; alternativ Loch in der Grundplatte verschieben – eigener PR).
3. **Bodenfreiheit (SOLL MECH-VAC-021):** Kingpin-Kopf unten ca. Z 18,2 (Druckteile ≥ 21,2). Optionen: abnehmen; kürzerer Einsatz (4 mm) im Achsschenkel-Auge und Ohr 3,5 mm → ca. Z 19,7; flacher Kopf (ISO 7380 mit Hülse).
4. **Spurstange rechts ↔ Servolasche 1,0 mm³** nur eingefedert bei vollem Rechtseinschlag (Pfannen-Hülle eckig, Laschenhöhe vorläufig). Messpunkt 5; falls real Berührung: Servo-Endpunkt rechts um ca. 1° zurück.
5. **Lenkgestänge ↔ Akku-Entnahmeweg 10,5 mm³** bei vollem Rechtseinschlag (nicht in MECH-VAC-009 genannt); Akku bei Geradeausstellung wechseln.
6. **Radstand-Parametertest** (MECH-VAC-001) offen, siehe Parametertest.
7. **Lenkgestänge** nicht aus 54539 (96,76 mm zu lang): Ersatz Gewindestange M3 mit Kugelpfannen (Pos. 78, erlaubt laut MECH-VAC-018). Die Servo-Anlenkung (39,94 mm) liegt am unteren Ende des 3 × 23-Spannschlosses.
8. **Vorspur** konstruktiv 0,07° Nachspur je Rad (statt 0,00°), mit der Spurstange (0,03 mm) auf 0 einstellbar.
9. **Ackermann bei kleinen Einschlägen** unter 80 % (rechts 55 % bei 10°); bei vollem Einschlag 96 / 105 %.
10. **Frontschott** über der Getriebehülle (Oberdeck-Auflage Z 80,6…84,2), von MECH-VAC-002 verlangt.
11. Knappe Abstände zu Rad/Felge (0,22…0,33 mm) mit vorläufigem Felgeninnenraum.

## Entscheidungen in der Umsetzung (nicht im Anforderungsdokument vorgegeben)

- **Dämpfer vor der Achse** (wie TT-02B und gespiegelte Hinterachse): Dämpferbrücke vor dem Schott, Dämpfer davor mit Distanzhülse 6 mm. Hinter der Achse liegen die Spurstangen und Umlenkhebel.
- **Servo mit Abtrieb vorne**, Saver-Arm nach hinten; das Lenkgestänge kreuzt quer über das Servo hinter dem Saver, die Servo-Anlenkung kreuzt das Lenkgestänge 7,8 mm höher.
- **Kingpins als Passschrauben ISO 7379 (Bund Ø 4, Gewinde M3)** statt Vollgewindeschrauben, damit das C-Hub-Ohr auf einem glatten Bund dreht.
- **Rastnocken-Saver** (axial, Druckfeder) statt Torsionsfeder: einstellbar, spielfrei, einfach zu drucken.
- **Umlenkhebel-Lagerung** auf Messinghülse 5 × 0,9 mit M3-Schraube.

## Parameterliste (neue Benutzerparameter)

400 Benutzerparameter mit Präfix `va_`, jeder mit Kommentar. Skelett-Parameter stehen mit `_Ref`. Werte in Konstruktionslage. Prüfmaße (`va_radhub`, `va_lenk_l`, `va_lenk_r`, `va_servo_phi`, `va_pruef_*`, `va_daempfer_hub_bedarf`, `va_daempfer_reserve`, `va_hebel`, `va_daempfer_neig`, `va_sv_feder_reserve`) steuern nichts im Modell.

| Parameter | Ausdruck | Wert | Kommentar |
|---|---|---|---|
| `va_ql_y` | `35 mm` | 35,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Querlenkerbock Mitte Fussflaeche quer (= ql_y) |
| `va_ql_dx` | `18 mm` | 18,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Querlenkerbock Mitte Fussflaeche vor/hinter der Achse (= ql_dx), Stuetzweite 36 mm |
| `va_ql_fuss_l` | `10 mm` | 10,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Fussflaeche Querlenkerbock laengs (= ql_l) |
| `va_ql_fuss_b` | `16 mm` | 16,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Fussflaeche Querlenkerbock quer (= ql_b) |
| `va_gp_paar_d` | `9 mm` | 9,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochabstand Zweierlochbild (= gp_paar_d) |
| `va_gp_getriebe_dx` | `19 mm` | 19,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Getriebe-Lochbild vor/hinter der Achse (= gp_getriebe_dx, X 114/152) |
| `va_gp_getriebe_y` | `18 mm` | 18,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Getriebe-Lochbild quer (= gp_getriebe_y) |
| `va_od_luft` | `1 mm` | 1,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Oberdeck 1 mm ueber der Zahnradabdeckung (= od_luft) |
| `va_od_z` | `antrieb_z_Ref + abdeckung_r_Ref + va_od_luft` | 84,200 mm | abgeleitet: Unterkante Oberdeck = od_z Grundplatte (84,2 mm), Auflagehoehe Frontschott (MECH-VAC-002) |
| `va_od_dx` | `18 mm` | 18,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Oberdeck-Loecher 18 mm hinter der Vorderachse (= od_getriebe_dx, X 115) |
| `va_od_y` | `5 mm` | 5,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Oberdeck-Loecher quer (= od_loch_y) |
| `va_lk_l` | `8 mm` | 8,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Fussflaeche Lagerbock Lenkhebel laengs (= lk_l) |
| `va_lk_b` | `16 mm` | 16,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Fussflaeche Lagerbock Lenkhebel quer (= lk_b) |
| `va_lk_x` | `xt60_x_Ref + xt60_b_Ref / 2 + 1 mm + va_lk_l / 2` | 94,500 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lagerbock Lenkhebel links Mitte laengs (= lk_x, 94,5 mm) |
| `va_lk_x_rechts` | `achse_x_Ref - daempfer_dx_Ref - daempfer_d_Ref / 2 - 2 mm - va_lk_l / 2` | 92,750 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lagerbock Lenkhebel rechts Mitte laengs (= lk_x_rechts, 92,75 mm; nicht ueber X 97,75) |
| `va_lk_y_links` | `35 mm` | 35,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lagerbock Lenkhebel links Mitte quer (= lk_y_links) |
| `va_lk_y_rechts` | `51 mm` | 51,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lagerbock Lenkhebel rechts Mitte quer, Betrag (= lk_y_rechts) |
| `va_sh_x_hinten` | `servo_x_Ref - servo_l_Ref / 2 - 4 mm` | 53,200 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochbild Servohalter hinten (= gp_sh_x_hinten, 53,2 mm) |
| `va_sh_dy` | `5 mm` | 5,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochbild Servohalter hinten quer zur Servomitte (= gp_sh_dy) |
| `va_sh_y_aussen` | `servo_y_Ref - servo_b_Ref / 2 - 5 mm` | -37,200 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochbild Servohalter rechts (= gp_sh_y_aussen, -37,2 mm) |
| `va_sh_x_vorne` | `servo_x_Ref + servo_l_Ref / 2 - 2.5 mm` | 95,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochbild Servohalter vorderes Loch rechts (= gp_sh_x_vorne, 95 mm) |
| `va_sh_dx` | `10 mm` | 10,000 mm | Schnittstelle Grundplatte v11 (Wert uebernommen, Grundplatte hat keine Favoriten-Parameter; aendert sich die Grundplatte, von Hand nachziehen): Lochbild Servohalter rechts Lochabstand laengs (= gp_sh_dx) |
| `va_bohrung` | `3.2 mm` | 3,200 mm | Bohrung M3 im Druck (+0,2 mm, MECH-VAC-016) |
| `va_einsatz_d` | `4 mm` | 4,000 mm | Gewindeeinsatz M3 kurz (Stueckliste Pos. 30): Bohrung, vorlaeufig wie Hinterachse, bei Lieferung messen |
| `va_einsatz_t` | `6 mm` | 6,000 mm | Gewindeeinsatz M3 kurz: Bohrtiefe, vorlaeufig wie Hinterachse, bei Lieferung messen |
| `va_kopf_d` | `6 mm` | 6,000 mm | Senkung fuer M3-Zylinderkopf (dk 5,5 mm + Spiel) |
| `va_lager_spiel` | `0.1 mm` | 0,100 mm | Passung Lagersitz: Zugabe auf den Durchmesser, vorlaeufig, per Probedruck einstellen (MECH-VAC-016) |
| `va_wand_min` | `1.2 mm` | 1,200 mm | Mindestwand Druck (MECH-VAC-016) |
| `va_durch` | `2 mm` | 2,000 mm | Modellierhilfe: Zugabe fuer durchgehende Schnitte und Ueberlappungen beim Vereinen |
| `va_kugel_h` | `6 mm` | 6,000 mm | Kugelkopf 5 mm (Tamiya 50592 / MB8): Kugelmitte ueber Auflage, vorlaeufig wie ha_kugel_h, am Teil messen |
| `va_pfanne_d` | `9 mm` | 9,000 mm | Kugelpfanne 54539: Huellkoerper-Durchmesser, vorlaeufig wie ha_pfanne_d |
| `va_pfanne_ueber` | `4.5 mm` | 4,500 mm | Kugelpfanne: Ueberstand ueber die Kugelmitte, vorlaeufig wie ha_pfanne_ueber |
| `va_stange_d` | `3 mm` | 3,000 mm | Spannschloss/Gewindestange M3: Durchmesser Huellkoerper |
| `va_versatz` | `lenkachse_versatz_Ref` | 20,000 mm | Lenkachse innerhalb der Radmitte, entlang der Radachse (= lenkachse_versatz Skelett, MECH-VAC-005) |
| `va_nachlauf` | `4 deg` | 4,000° | Nachlauf fest im C-Hub, vorlaeufig 4 Grad (MECH-VAC-006) |
| `va_spreizung` | `0 deg` | 0,000° | Spreizung (Lenkachse gegen Senkrechte, Vorderansicht) in Konstruktionslage, vorlaeufig 0 Grad (MECH-VAC-006) |
| `va_sturz` | `-1 deg` | -1,000° | Sturz statisch in Konstruktionslage, vorlaeufig -1 Grad (MECH-VAC-006); einstellbar ueber die Sturzstange (va_sl_dl) |
| `va_eps` | `-va_sturz - va_spreizung` | 1,000° | abgeleitet: Neigung der Radachse gegen die Lenkachse im Achsschenkel (Sturz und Spreizung in Konstruktionslage) |
| `va_k0_dx` | `-va_versatz * sin(va_eps) * sin(va_nachlauf)` | -0,024 mm | abgeleitet: Radmitte minus Lenkachspunkt K0, laengs |
| `va_k0_dy` | `va_versatz * ( cos(va_eps) * cos(va_spreizung) - sin(va_eps) * cos(va_nachlauf) * sin(va_spreizung) )` | 19,997 mm | abgeleitet: Radmitte minus K0, quer |
| `va_k0_dz` | `va_versatz * ( cos(va_eps) * sin(va_spreizung) + sin(va_eps) * cos(va_nachlauf) * cos(va_spreizung) )` | 0,348 mm | abgeleitet: Radmitte minus K0, Hoehe |
| `va_k0_x` | `achse_x_Ref - va_k0_dx` | 133,024 mm | abgeleitet: K0 = Punkt der Lenkachse auf der Radachse (Ursprung Achsschenkel/C-Hub), laengs |
| `va_k0_y` | `rad_y_v_Ref - va_k0_dy` | 88,503 mm | abgeleitet: K0 quer (Lenkachse in Radmittenhoehe, Soll 88,5 mm) |
| `va_k0_z` | `rad_z_Ref - va_k0_dz` | 40,652 mm | abgeleitet: K0 Hoehe |
| `va_ql_z` | `38 mm` | 38,000 mm | Querlenkerachse innen: Hoehe (Stift im Bock), aus Kinematikrechnung (Bump-Steer, Sturzaenderung) und Wand zum Bockeinsatz |
| `va_ch_b_dy` | `-32.500 mm` | -32,500 mm | C-Hub: Bolzen zum Querlenker quer zur Radmitte (Konstruktionslage), aus Kinematikrechnung |
| `va_ch_b_dz` | `-14.000 mm` | -14,000 mm | C-Hub: Bolzen zum Querlenker Hoehe zur Radmitte, aus Kinematikrechnung |
| `va_b0_y` | `rad_y_v_Ref + va_ch_b_dy` | 76,000 mm | abgeleitet: Bolzen aussen quer in Konstruktionslage |
| `va_b0_z` | `rad_z_Ref + va_ch_b_dz` | 27,000 mm | abgeleitet: Bolzen aussen Hoehe in Konstruktionslage |
| `va_b_hx` | `achse_x_Ref - va_k0_x` | -0,024 mm | abgeleitet: Bolzen im C-Hub-System (rel. K0), laengs |
| `va_b_hy` | `va_b0_y - va_k0_y` | -12,503 mm | abgeleitet: Bolzen im C-Hub-System, quer |
| `va_b_hz` | `va_b0_z - va_k0_z` | -13,652 mm | abgeleitet: Bolzen im C-Hub-System, Hoehe |
| `va_ql_l` | `sqrt(( va_b0_y - va_ql_y ) ^ 2 + ( va_b0_z - va_ql_z ) ^ 2)` | 42,450 mm | abgeleitet: Querlenkerlaenge Achse innen bis Bolzen aussen |
| `va_ql_phi0` | `atan(( va_b0_z - va_ql_z ) / ( va_b0_y - va_ql_y ))` | -15,018° | abgeleitet: Querlenkerwinkel in Konstruktionslage (negativ = aussen tiefer) |
| `va_ql_dphi` | `0 deg` | 0,000° | Stellung der Aufhaengung: Querlenkerdrehung gegen Konstruktionslage (0 = Konstruktionslage, va_dphi_aus, va_dphi_ein) |
| `va_ql_phi` | `va_ql_phi0 + va_ql_dphi` | -15,018° | abgeleitet: Querlenkerwinkel in der Stellung |
| `va_b_y` | `va_ql_y + va_ql_l * cos(va_ql_phi)` | 76,000 mm | abgeleitet: Bolzen aussen quer (Stellung) |
| `va_b_z` | `va_ql_z + va_ql_l * sin(va_ql_phi)` | 27,000 mm | abgeleitet: Bolzen aussen Hoehe (Stellung) |
| `va_ch_e_dx` | `6.000 mm` | 6,000 mm | C-Hub: Kugelmitte Sturzstange laengs zur Achse (Kugelkopf senkrecht auf dem oberen Arm) |
| `va_ch_e_dy` | `-26.899 mm` | -26,899 mm | C-Hub: Kugelmitte Sturzstange quer zur Radmitte, aus Kinematikrechnung |
| `va_ch_e_dz` | `30.620 mm` | 30,620 mm | C-Hub: Kugelmitte Sturzstange Hoehe zur Radmitte, aus Kinematikrechnung |
| `va_e0_x` | `achse_x_Ref + va_ch_e_dx` | 139,000 mm | abgeleitet: Kugel C-Hub laengs |
| `va_e0_y` | `rad_y_v_Ref + va_ch_e_dy` | 81,601 mm | abgeleitet: Kugel C-Hub quer (Konstruktionslage) |
| `va_e0_z` | `rad_z_Ref + va_ch_e_dz` | 71,620 mm | abgeleitet: Kugel C-Hub Hoehe (Konstruktionslage) |
| `va_e_hx` | `va_e0_x - va_k0_x` | 5,976 mm | abgeleitet: Kugel im C-Hub-System, laengs |
| `va_e_hy` | `va_e0_y - va_k0_y` | -6,902 mm | abgeleitet: Kugel im C-Hub-System, quer |
| `va_e_hz` | `va_e0_z - va_k0_z` | 30,968 mm | abgeleitet: Kugel im C-Hub-System, Hoehe |
| `va_fs_dx` | `23.5 mm` | 23,500 mm | Frontschott: Vorder- bzw. Rueckseite 23,5 mm vor/hinter der Achse (Spiegel des Hinterachsgetriebes, ha_gh_trommel_d / 2; X 109,5...156,5) |
| `va_sl_c_x` | `achse_x_Ref + va_fs_dx - va_kugel_h` | 150,500 mm | abgeleitet: innere Kugelmitte Sturzstange laengs (Kugelkopf an der Rueckseite der Daempferbruecke) |
| `va_sl_c_y` | `34.697 mm` | 34,697 mm | Sturzstange: innere Kugelmitte quer (an der Daempferbruecke), aus Kinematikrechnung |
| `va_sl_c_z` | `82.291 mm` | 82,291 mm | Sturzstange: innere Kugelmitte Hoehe, aus Kinematikrechnung |
| `va_sl_l0` | `sqrt(( va_e0_x - va_sl_c_x ) ^ 2 + ( va_e0_y - va_sl_c_y ) ^ 2 + ( va_e0_z - va_sl_c_z ) ^ 2)` | 49,458 mm | abgeleitet: Sturzstange Kugelmitte bis Kugelmitte in Konstruktionslage (Spannschloss 54539 3 x 32) |
| `va_sl_dl` | `0 mm` | 0,000 mm | Sturzverstellung: Laengenaenderung der Sturzstange gegen Konstruktionslage (MECH-VAC-006); 0 = va_sturz |
| `va_sl_lp` | `sqrt(( va_sl_l0 + va_sl_dl ) ^ 2 - ( va_e0_x - va_sl_c_x ) ^ 2)` | 48,103 mm | abgeleitet: Sturzstange, Laenge in der YZ-Ebene |
| `va_k_r0` | `va_e_hy - va_b_hy` | 5,601 mm | abgeleitet: Viergelenk, Bolzen -> Kugel im C-Hub, quer |
| `va_k_r1` | `va_e_hz - va_b_hz` | 44,620 mm | abgeleitet: Viergelenk, Bolzen -> Kugel im C-Hub, Hoehe |
| `va_k_d0` | `va_b_y - va_sl_c_y` | 41,303 mm | abgeleitet: Viergelenk, innere Kugel -> Bolzen, quer (Stellung) |
| `va_k_d1` | `va_b_z - va_sl_c_z` | -55,291 mm | abgeleitet: Viergelenk, innere Kugel -> Bolzen, Hoehe (Stellung) |
| `va_k_m` | `( va_sl_lp ^ 2 - va_k_d0 ^ 2 - va_k_d1 ^ 2 - va_k_r0 ^ 2 - va_k_r1 ^ 2 ) / 2` | -2235,7 mm² | abgeleitet: Viergelenk-Gleichung a cos(k) + b sin(k) = m |
| `va_k_a` | `va_k_d0 * va_k_r0 + va_k_d1 * va_k_r1` | -2235,7 mm² | abgeleitet: Viergelenk, Koeffizient a |
| `va_k_b` | `va_k_d1 * va_k_r0 - va_k_d0 * va_k_r1` | -2152,6 mm² | abgeleitet: Viergelenk, Koeffizient b |
| `va_kappa` | `2 * atan(va_k_b / ( sqrt(va_k_a ^ 2 + va_k_b ^ 2) + va_k_a )) + acos(va_k_m / sqrt(va_k_a ^ 2 + va_k_b ^ 2))` | 0,000° | abgeleitet: Drehung des C-Hubs um X (Stellung, Viergelenk Querlenker/Sturzstange); 0 in Konstruktionslage |
| `va_t_x` | `achse_x_Ref - va_b_hx` | 133,024 mm | abgeleitet: Lage K0 (Stellung), laengs |
| `va_t_y` | `va_b_y - ( va_b_hy * cos(va_kappa) - va_b_hz * sin(va_kappa) )` | 88,503 mm | abgeleitet: Lage K0 (Stellung), quer |
| `va_t_z` | `va_b_z - ( va_b_hy * sin(va_kappa) + va_b_hz * cos(va_kappa) )` | 40,652 mm | abgeleitet: Lage K0 (Stellung), Hoehe |
| `va_rho` | `va_kappa + va_spreizung` | 0,000° | abgeleitet: Drehung der Lenkachse um X (Stellung): C-Hub + Spreizung |
| `va_w_y` | `va_t_y + va_k0_dy * cos(va_kappa) - va_k0_dz * sin(va_kappa)` | 108,500 mm | abgeleitet: Radmitte quer bei Geradeausstellung (Stellung) |
| `va_w_z` | `va_t_z + va_k0_dy * sin(va_kappa) + va_k0_dz * cos(va_kappa)` | 41,000 mm | abgeleitet: Radmitte Hoehe bei Geradeausstellung (Stellung) |
| `va_radhub` | `va_w_z - rad_z_Ref` | 0,000 mm | Pruefmass: Radhub gegen Konstruktionslage (+ = eingefedert) |
| `va_dphi_aus` | `-16.4371 deg` | -16,437° | Pruefstellung ausgefedert: Querlenkerwinkel, so bestimmt, dass va_radhub = -ausfederweg (Pruefskript) |
| `va_dphi_ein` | `31.7816 deg` | 31,782° | Pruefstellung eingefedert: Querlenkerwinkel, so bestimmt, dass va_radhub = +einfederweg (Pruefskript) |
| `va_fs_y` | `diff_abtrieb_y_Ref - gelenk_becher_Ref - 0.5 mm` | 22,360 mm | Frontschott: halbe Breite wie Hinterachsgetriebe (ha_gh_y, 22,36 mm < 24,86 mm Getriebehuelle, MECH-VAC-002) |
| `va_fs_x_h` | `achse_x_Ref - va_fs_dx` | 109,500 mm | abgeleitet: Rueckseite Frontschott (X 109,5) |
| `va_fs_x_v` | `achse_x_Ref + va_fs_dx` | 156,500 mm | abgeleitet: Vorderseite Frontschott = Anlage Daempferbruecke (X 156,5) |
| `va_fs_schiene_b` | `8 mm` | 8,000 mm | Frontschott: Breite der Bodenschienen (Gewindeeinsatz Grundplatte + Wand) |
| `va_fs_schiene_h` | `8 mm` | 8,000 mm | Frontschott: Hoehe der Bodenschienen |
| `va_fs_wand` | `6 mm` | 6,000 mm | Frontschott: Dicke der Vorderwand (Einsaetze fuer die Daempferbruecke) |
| `va_fs_rahmen` | `7 mm` | 7,000 mm | Frontschott: Stegbreite des Rahmens der Vorderwand und der Pfosten |
| `va_fs_oben_z` | `79 mm` | 79,000 mm | Frontschott: Oberkante der Vorderwand (unter der Getriebehuelle Z 80,6) |
| `va_fs_post_l` | `9 mm` | 9,000 mm | Frontschott: Oberdeck-Auflage, Laenge in X (Einsatz + Wand) |
| `va_fs_post_h` | `8.2 mm` | 8,200 mm | Frontschott: Oberdeck-Auflage, Hoehe des Querriegels unter Z 84,2 |
| `va_fs_bs_y` | `10 mm` | 10,000 mm | Frontschott: Schrauben der Daempferbruecke quer |
| `va_fs_bs_z1` | `36 mm` | 36,000 mm | Frontschott: untere Schrauben der Daempferbruecke, Hoehe |
| `va_fs_bs_z2` | `73 mm` | 73,000 mm | Frontschott: obere Schrauben der Daempferbruecke, Hoehe |
| `va_qb_d` | `va_ql_fuss_b` | 16,000 mm | Querlenkerbock: Rundung um den Stift (tangential an die Fussbreite) |
| `va_stift_d` | `3 mm` | 3,000 mm | Querlenkerachse: Stahlstift ISO 2338 3 m6 (MECH-VAC-003) |
| `va_stift_spiel_bock` | `0.1 mm` | 0,100 mm | Querlenkerachse: Spiel im Bock (Stift fest), per Probedruck einstellen |
| `va_stift_l` | `40 mm` | 40,000 mm | Querlenkerachse: Stiftlaenge 40 mm (ISO 2338 3 x 40) |
| `va_stift_luft` | `0.25 mm` | 0,250 mm | Querlenkerachse: Axialluft des Stifts je Ende im Sackloch |
| `va_ql_axial` | `0.5 mm` | 0,500 mm | Querlenker: Axialspiel zwischen Rohr und Bock je Seite |
| `va_ql_rohr_d` | `7 mm` | 7,000 mm | Querlenker: Rohr um die Achse innen |
| `va_ql_rohr_l` | `2 * va_ql_dx - va_ql_fuss_l - 2 * va_ql_axial` | 25,000 mm | abgeleitet: Rohrlaenge zwischen den Boecken |
| `va_stift_t` | `( va_stift_l + 2 * va_stift_luft - va_ql_rohr_l - 2 * va_ql_axial ) / 2` | 7,250 mm | abgeleitet: Sacklochtiefe des Stifts je Bock |
| `va_ql_dicke` | `5 mm` | 5,000 mm | Querlenker: Plattendicke (Sollbruchstelle, MECH-VAC-017) |
| `va_ql_y1` | `12 mm` | 12,000 mm | Querlenker: breiter innerer Teil bis 12 mm vom Rohr (Freigang zur Plattenkante ausgefedert) |
| `va_ch_lasche_b` | `8 mm` | 8,000 mm | C-Hub: Lasche unten fuer den Bolzen zum Querlenker, Breite in X |
| `va_ch_lasche_d` | `8 mm` | 8,000 mm | C-Hub: Lasche unten, Durchmesser um den Bolzen |
| `va_lasche_spalt` | `0.2 mm` | 0,200 mm | Spiel Lasche C-Hub in der Gabel des Querlenkers je Seite |
| `va_ql_wange` | `5 mm` | 5,000 mm | Querlenker: Wange der Gabel aussen |
| `va_ql_gabel_b` | `va_ch_lasche_b + 2 * va_lasche_spalt + 2 * va_ql_wange` | 18,400 mm | abgeleitet: Breite der Gabel aussen |
| `va_ql_gabel_d` | `8 mm` | 8,000 mm | Querlenker: Gabel, Durchmesser um den Bolzen |
| `va_ql_schlitz` | `7 mm` | 7,000 mm | Querlenker: Schlitz fuer die C-Hub-Lasche, Tiefe ab Bolzenmitte |
| `va_ql_platte_z` | `1 mm` | 1,000 mm | Querlenker: Platte 1 mm ueber die Querlenkerebene versetzt (Freigang zur Grundplatte ausgefedert) |
| `va_ql_dl` | `15.769 mm` | 15,769 mm | Daempfer unten: Lage auf dem Querlenker ab der Achse (bestimmt Hebelverhaeltnis und Hubausnutzung), aus Rechnung |
| `va_dl_lasche` | `8 mm` | 8,000 mm | Querlenker: Daempferlasche, Querschnitt |
| `va_ql_dl_z` | `7 mm` | 7,000 mm | Daempfer unten: Versatz ueber der Querlenkerebene (Freigang Lasche/Daempferauge zur Grundplatte ausgefedert) |
| `va_db_dicke` | `6 mm` | 6,000 mm | Daempferbruecke: Plattendicke (MECH-VAC-015), Alu spaeter gleich |
| `va_d_auge_d` | `9 mm` | 9,000 mm | CVA-Daempfer vorne: Auge Aussendurchmesser, vorlaeufig wie hinten, am Teil messen |
| `va_d_auge_b` | `6 mm` | 6,000 mm | CVA-Daempfer vorne: Auge Breite, vorlaeufig |
| `va_d_auge_l` | `10 mm` | 10,000 mm | CVA-Daempfer vorne: Augenmitte bis Koerper/Federteller, vorlaeufig |
| `va_d_spalt` | `0.5 mm` | 0,500 mm | Daempfer: Scheibe zwischen Auge und Anlage |
| `va_d_distanz` | `6 mm` | 6,000 mm | Daempfer oben: Distanzhuelse M3 x 6 zwischen Bruecke und Auge (Daempferkoerper frei vor der Bruecke) |
| `va_d_x` | `va_fs_x_v + va_db_dicke + va_d_distanz + va_d_spalt + va_d_auge_b / 2` | 172,000 mm | abgeleitet: Daempferebene laengs (vor der Bruecke, Spiegel der Hinterachse) |
| `va_daempfer_l_aus` | `56 mm` | 56,000 mm | CVA-Daempfer vorne: Augenabstand ausgefedert, vorlaeufig (Feder MB11 39,6 + Augen 20, Verhaeltnis wie hinten 80/84,5), am Teil messen |
| `va_daempfer_hub` | `14 mm` | 14,000 mm | CVA-Daempfer vorne: Hub, vorlaeufig (Verhaeltnis Hub/Laenge wie hinten 20/80), am Teil messen |
| `va_du_y` | `44.000 mm` | 44,000 mm | Daempfer oben: Lage quer an der Bruecke |
| `va_hebel_tt02b` | `1.5` | 1,5 | Hebelverhaeltnis Rad:Daempfer TT-02B vorne, vorlaeufig wie hinten abgeschaetzt (docs/vorderachse.md) |
| `va_ql_phi_aus` | `va_ql_phi0 + va_dphi_aus` | -31,455° | abgeleitet: Querlenkerwinkel ausgefedert |
| `va_ql_phi_ein` | `va_ql_phi0 + va_dphi_ein` | 16,763° | abgeleitet: Querlenkerwinkel eingefedert |
| `va_l_y` | `va_ql_y + va_ql_dl * cos(va_ql_phi) - va_ql_dl_z * sin(va_ql_phi)` | 52,044 mm | abgeleitet: Daempfer unten quer (Stellung) |
| `va_l_z` | `va_ql_z + va_ql_dl * sin(va_ql_phi) + va_ql_dl_z * cos(va_ql_phi)` | 40,675 mm | abgeleitet: Daempfer unten Hoehe (Stellung) |
| `va_l_aus_y` | `va_ql_y + va_ql_dl * cos(va_ql_phi_aus) - va_ql_dl_z * sin(va_ql_phi_aus)` | 52,105 mm | abgeleitet: Daempfer unten quer, ausgefedert |
| `va_l_aus_z` | `va_ql_z + va_ql_dl * sin(va_ql_phi_aus) + va_ql_dl_z * cos(va_ql_phi_aus)` | 35,742 mm | abgeleitet: Daempfer unten Hoehe, ausgefedert |
| `va_l_ein_y` | `va_ql_y + va_ql_dl * cos(va_ql_phi_ein) - va_ql_dl_z * sin(va_ql_phi_ein)` | 48,080 mm | abgeleitet: Daempfer unten quer, eingefedert |
| `va_l_ein_z` | `va_ql_z + va_ql_dl * sin(va_ql_phi_ein) + va_ql_dl_z * cos(va_ql_phi_ein)` | 49,251 mm | abgeleitet: Daempfer unten Hoehe, eingefedert |
| `va_du_z` | `va_l_aus_z + sqrt(va_daempfer_l_aus ^ 2 - ( va_du_y - va_l_aus_y ) ^ 2)` | 91,153 mm | abgeleitet: Daempfer oben Hoehe, so dass der Daempfer ausgefedert genau va_daempfer_l_aus lang ist (Endanschlag begrenzt das Ausfedern) |
| `va_daempfer_l_ein` | `sqrt(( va_du_y - va_l_ein_y ) ^ 2 + ( va_du_z - va_l_ein_z ) ^ 2)` | 42,101 mm | abgeleitet: Augenabstand eingefedert |
| `va_daempfer_hub_bedarf` | `va_daempfer_l_aus - va_daempfer_l_ein` | 13,899 mm | Pruefmass: Daempferhub fuer den ganzen Federweg |
| `va_daempfer_reserve` | `va_daempfer_hub - va_daempfer_hub_bedarf` | 0,101 mm | Pruefmass: Hub minus Bedarf, >= 0 und klein = Daempfer begrenzt den Federweg (MECH-VAC-013) |
| `va_hebel` | `federweg_Ref / va_daempfer_hub_bedarf` | 2,518 | Pruefmass: Hebelverhaeltnis Rad:Daempfer gemittelt ueber den Federweg, muss >= va_hebel_tt02b sein (MECH-VAC-013) |
| `va_daempfer_l` | `sqrt(( va_du_y - va_l_y ) ^ 2 + ( va_du_z - va_l_z ) ^ 2)` | 51,115 mm | abgeleitet: Augenabstand in der Stellung |
| `va_daempfer_w` | `90 deg + atan(( va_l_y - va_du_y ) / ( va_du_z - va_l_z ))` | 99,055° | abgeleitet: Drehung Huellkoerper Daempfer um X |
| `va_daempfer_neig` | `90 deg - va_daempfer_w` | -9,055° | Pruefmass: Neigung des Daempfers gegen die Senkrechte (oben nach innen = negativ) |
| `va_n3_d` | `antriebswelle_d_Ref` | 14,000 mm | Huellkoerper Antriebswelle N3 (4WD): Durchmesser, = antriebswelle_d Skelett (Kugel 10 mm + 2 x 2 mm Zuschlag); fuer die Pruefung ohne Zuschlag auf 10 mm setzen |
| `va_d_koerper_d` | `daempfer_feder_d_Ref` | 16,500 mm | CVA-Daempfer vorne: Koerper/Feder Durchmesser (= daempfer_feder_d Skelett, 16,5 mm, vorlaeufig) |
| `va_n1_becher_l` | `18.3 mm` | 18,300 mm | Radachse N1 (vorne gleiches Teil wie hinten): Becherlaenge, vorlaeufig (ha_n1_becher_l), am Teil messen |
| `va_n1_becher_d` | `17 mm` | 17,000 mm | Radachse N1: Becher-Aussendurchmesser, vorlaeufig (ha_n1_becher_d), am Teil messen |
| `va_n1_welle_d` | `5 mm` | 5,000 mm | Radachse N1: Wellendurchmesser 5 mm, belegt (Lager 5x11) |
| `va_n1_welle_l` | `14.1 mm` | 14,100 mm | Radachse N1: Wellenabschnitt Becherboden bis Absatz, vorlaeufig (ha_n1_welle_l) |
| `va_n1_gewinde_d` | `3 mm` | 3,000 mm | Radachse N1: Gewinde am Ende, vorlaeufig |
| `va_n1_innen` | `va_versatz + rad_breite_v_Ref / 2 - radachse_v_l_Ref` | -7,700 mm | abgeleitet: offenes Becherende der Radachse entlang der Radachse ab K0 (negativ = innerhalb der Lenkachse); Gewindeende buendig mit der Radaussenseite (Annahme Skelett) |
| `va_u_becher` | `va_n1_innen + va_n1_becher_l` | 10,600 mm | abgeleitet: Becherboden entlang der Radachse ab K0 |
| `va_u_kreuz` | `va_n1_innen + gelenk_becher_Ref` | 1,300 mm | abgeleitet: Kreuzstift der Antriebswelle im Becher (4WD) entlang der Radachse ab K0 |
| `va_radlager_d` | `11 mm` | 11,000 mm | Radlager 5x11x4 (Pos. 14): Aussendurchmesser belegt, am Teil pruefen |
| `va_radlager_b` | `4 mm` | 4,000 mm | Radlager 5x11x4: Breite vorlaeufig, am Teil messen |
| `va_radlager_abstand` | `6 mm` | 6,000 mm | Achsschenkel: Lagerabstand Mitte-Mitte (Steg 2 mm), vorlaeufig wie Hinterachse (MECH-VAC-005) |
| `va_radlager_steg_d` | `8 mm` | 8,000 mm | Achsschenkel: Bohrung im Steg zwischen den Lagern (Welle 5 mm), Anschlag der Aussenringe = axiale Sicherung der Radachse |
| `va_as_spalt` | `0.5 mm` | 0,500 mm | Achsschenkel: Lager steht 0,5 mm ueber die Nabe vor (Abstand zum drehenden Becher bzw. Mitnehmer) |
| `va_as_lager_wand` | `2.5 mm` | 2,500 mm | Achsschenkel: Wand um die Lagersitze (>= 2 mm, MECH-VAC-016) |
| `va_as_nabe_d` | `va_radlager_d + va_lager_spiel + 2 * va_as_lager_wand` | 16,100 mm | abgeleitet: Aussendurchmesser Lagernabe Achsschenkel |
| `va_u_nabe` | `va_radlager_abstand + va_radlager_b` | 10,000 mm | abgeleitet: Becherboden bis Anlage Sechskant-Mitnehmer (wie Hinterachse) |
| `va_mitnehmer_d` | `12 mm` | 12,000 mm | Sechskant-Mitnehmer 12 mm (Pos. 8): Huellkoerper Durchmesser (Schluesselweite), vorlaeufig |
| `va_mitnehmer_l` | `6 mm` | 6,000 mm | Sechskant-Mitnehmer: Laenge, vorlaeufig |
| `va_felge_innen_d` | `50 mm` | 50,000 mm | Rad vorne: Innendurchmesser Felge (Raum fuer den Achsschenkel), vorlaeufig wie hinten, am Teil messen |
| `va_becher_luft` | `0.5 mm` | 0,500 mm | Achsschenkel/C-Hub: Luft der Kingpin-Augen zum Becher der Radachse (dreht mit dem Achsschenkel) |
| `va_kp_d` | `4 mm` | 4,000 mm | Kingpin: Passschraube ISO 7379, Bund 4 mm, Gewinde M3 (MECH-VAC-003 Kingpin-Schraube M3), vorlaeufig |
| `va_kp_spiel` | `0.1 mm` | 0,100 mm | Kingpin: Spiel des Bundes in der C-Hub-Bohrung, per Probedruck einstellen |
| `va_kp_kopf_d` | `7 mm` | 7,000 mm | Kingpin-Passschraube: Kopfdurchmesser, vorlaeufig, am Teil messen |
| `va_kp_kopf_h` | `3 mm` | 3,000 mm | Kingpin-Passschraube: Kopfhoehe, vorlaeufig, am Teil messen |
| `va_kp_luft` | `0.2 mm` | 0,200 mm | Kingpin: Axialluft zwischen Achsschenkel-Auge und C-Hub-Ohr |
| `va_as_auge_d` | `8 mm` | 8,000 mm | Achsschenkel: Kingpin-Augen, Durchmesser (Einsatz 4 mm + 2 mm Wand) |
| `va_as_auge_h` | `6 mm` | 6,000 mm | Achsschenkel: Kingpin-Augen, Hoehe (Gewindeeinsatz fuer den Kingpin) |
| `va_as_oben_luft` | `1.788 mm` | 1,788 mm | Achsschenkel: Luft oberes Kingpin-Auge und Spurhebel zum Becher (aus der Spurhebelhoehe der Kinematikrechnung, >= va_becher_luft) |
| `va_as_oben_z0` | `va_n1_becher_d / 2 + va_as_oben_luft` | 10,288 mm | abgeleitet: Unterkante oberes Achsschenkel-Auge und Spurhebel ueber K0 |
| `va_as_unten_z0` | `va_n1_becher_d / 2 + va_becher_luft` | 9,000 mm | abgeleitet: Oberkante unteres Achsschenkel-Auge unter K0 (Betrag) |
| `va_ch_ohr_h` | `4 mm` | 4,000 mm | C-Hub: Dicke der Kingpin-Ohren |
| `va_ch_ohr_d` | `8 mm` | 8,000 mm | C-Hub: Durchmesser der Kingpin-Ohren |
| `va_ch_steg` | `4 mm` | 4,000 mm | C-Hub: Hoehe der Verbindungsarme oben und unten (= Ohrdicke) |
| `va_ch_arm_b` | `3.5 mm` | 3,500 mm | C-Hub: Breite des schraegen Arms vom Ohr zur Saeule (Reifenfreigang bei vollem Einschlag) |
| `va_ch_arm_w` | `30 deg` | 30,000° | C-Hub: Richtung des schraegen Arms (Reifenfreigang bei lenkwinkel_max) |
| `va_ch_s_x0` | `14 mm` | 14,000 mm | C-Hub: Saeule vor der Lenkachse, Beginn laengs |
| `va_ch_s_x1` | `19 mm` | 19,000 mm | C-Hub: Saeule, Ende laengs |
| `va_ch_s_y0` | `-15 mm` | -15,000 mm | C-Hub: Saeule quer, innen (rel. K0) |
| `va_ch_s_y1` | `-7.5 mm` | -7,500 mm | C-Hub: Saeule quer, aussen (Reifenfreigang bei vollem Einschlag) |
| `va_sph_b` | `8 mm` | 8,000 mm | Spurhebel: Breite |
| `va_as_arm_b` | `8 mm` | 8,000 mm | Achsschenkel: Breite der Arme zwischen Kingpin-Augen und Lagernabe |
| `va_ackermann` | `1` | 1 | Ackermann-Anteil Soll (1 = 100 %, Nutzerentscheidung 2026-11-08: fest ca. 100 %); verstellt den Spurhebelwinkel linearisiert (va_sph_winkel), Ist-Werte per Pruefskript in docs/vorderachse.md |
| `va_ack_steig` | `12 deg` | 12,000° | Spurhebelwinkel je 100 % Ackermann-Anteil (Kinematikrechnung: ca. 8,3 % je Grad, linearisiert) |
| `va_sph_l` | `21.611 mm` | 21,611 mm | Spurhebel links: Laenge Lenkachse bis Kugelmitte (Grundriss), aus Kinematikrechnung |
| `va_sph_w100` | `12.575 deg` | 12,575° | Spurhebel links: Winkel nach innen gegen die Fahrzeuglaengsachse bei va_ackermann = 1, aus Kinematikrechnung |
| `va_sph_winkel` | `va_sph_w100 + ( va_ackermann - 1 ) * va_ack_steig` | 12,575° | abgeleitet: Spurhebelwinkel links nach innen (Hebel zeigt nach hinten) |
| `va_sph_x` | `-va_sph_l * cos(va_sph_winkel)` | -21,093 mm | abgeleitet: Spurhebelkugel links im Achsschenkelsystem, laengs |
| `va_sph_y` | `-va_sph_l * sin(va_sph_winkel)` | -4,705 mm | abgeleitet: Spurhebelkugel links im Achsschenkelsystem, quer |
| `va_sph_z` | `va_as_oben_z0 - va_kugel_h` | 4,288 mm | abgeleitet: Spurhebelkugel (beide Seiten) Hoehe ueber K0 entlang der Lenkachse (Kugelkopf haengend unter dem Spurhebel) |
| `va_sph_r_dl` | `-1.660 mm` | -1,660 mm | Spurhebel rechts: Laengenzugabe gegen links (eigene Teile links/rechts, Abgleich der Lenkasymmetrie aus den Lagerboecken) |
| `va_sph_r_dw` | `-9.957 deg` | -9,957° | Spurhebel rechts: Winkelzugabe gegen links |
| `va_sph_rx` | `-( va_sph_l + va_sph_r_dl ) * cos(va_sph_winkel + va_sph_r_dw)` | -19,930 mm | abgeleitet: Spurhebelkugel rechts (gespiegeltes System), laengs |
| `va_sph_ry` | `-( va_sph_l + va_sph_r_dl ) * sin(va_sph_winkel + va_sph_r_dw)` | -0,911 mm | abgeleitet: Spurhebelkugel rechts (gespiegeltes System), quer |
| `va_s0_x` | `va_k0_x + va_sph_x * cos(va_nachlauf) - va_sph_z * sin(va_nachlauf)` | 111,684 mm | abgeleitet: Spurhebelkugel links in Konstruktionslage, laengs |
| `va_s0_hz` | `va_sph_x * sin(va_nachlauf) + va_sph_z * cos(va_nachlauf)` | 2,806 mm | abgeleitet: Hilfsgroesse (Nachlauf gedreht) |
| `va_s0_y` | `va_k0_y + va_sph_y * cos(va_spreizung) - va_s0_hz * sin(va_spreizung)` | 83,798 mm | abgeleitet: Spurhebelkugel links in Konstruktionslage, quer |
| `va_s0_z` | `va_k0_z + va_sph_y * sin(va_spreizung) + va_s0_hz * cos(va_spreizung)` | 43,458 mm | abgeleitet: Spurhebelkugel links in Konstruktionslage, Hoehe |
| `va_s0r_x` | `va_k0_x + va_sph_rx * cos(va_nachlauf) - va_sph_z * sin(va_nachlauf)` | 112,844 mm | abgeleitet: Spurhebelkugel rechts (gespiegelt, Y positiv) in Konstruktionslage, laengs |
| `va_s0r_hz` | `va_sph_rx * sin(va_nachlauf) + va_sph_z * cos(va_nachlauf)` | 2,887 mm | abgeleitet: Hilfsgroesse rechts |
| `va_s0r_y` | `va_k0_y + va_sph_ry * cos(va_spreizung) - va_s0r_hz * sin(va_spreizung)` | 87,592 mm | abgeleitet: Spurhebelkugel rechts (gespiegelt) quer, Betrag |
| `va_s0r_z` | `va_k0_z + va_sph_ry * sin(va_spreizung) + va_s0r_hz * cos(va_spreizung)` | 43,539 mm | abgeleitet: Spurhebelkugel rechts Hoehe |
| `va_ulh_g_z` | `54.226 mm` | 54,226 mm | Umlenkhebel: Hoehe der Spurstangenkugeln (haengend), aus Kinematikrechnung (Bump-Steer) |
| `va_ulh_platte` | `6 mm` | 6,000 mm | Umlenkhebel: Dicke der Hebelplatte (Gewindeeinsaetze fuer die Kugelkoepfe) |
| `va_ulh_d_z` | `va_ulh_g_z + 2 * va_kugel_h + va_ulh_platte` | 72,226 mm | abgeleitet: Hoehe der Kugeln fuer Lenkgestaenge und Servo-Anlenkung (stehend auf der Hebelplatte) |
| `va_ulh_l_gx` | `19.418 mm` | 19,418 mm | Umlenkhebel links: Spurstangenkugel laengs zum Drehpunkt, aus Kinematikrechnung |
| `va_ulh_l_gy` | `6.664 mm` | 6,664 mm | Umlenkhebel links: Spurstangenkugel quer zum Drehpunkt |
| `va_ulh_l_dx` | `-18.582 mm` | -18,582 mm | Umlenkhebel links: Lenkgestaenge-Kugel laengs zum Drehpunkt |
| `va_ulh_l_dy` | `10.719 mm` | 10,719 mm | Umlenkhebel links: Lenkgestaenge-Kugel quer zum Drehpunkt |
| `va_ulh_r_gx` | `18.558 mm` | 18,558 mm | Umlenkhebel rechts: Spurstangenkugel laengs zum Drehpunkt |
| `va_ulh_r_gy` | `5.428 mm` | 5,428 mm | Umlenkhebel rechts: Spurstangenkugel quer zum Drehpunkt |
| `va_ulh_r_dx` | `-19.776 mm` | -19,776 mm | Umlenkhebel rechts: Lenkgestaenge-Kugel laengs zum Drehpunkt |
| `va_ulh_r_dy` | `-0.000 mm` | -0,000 mm | Umlenkhebel rechts: Lenkgestaenge-Kugel quer zum Drehpunkt |
| `va_ulh_r_ux` | `-29.362 mm` | -29,362 mm | Umlenkhebel rechts: Kugel Servo-Anlenkung laengs zum Drehpunkt |
| `va_ulh_r_uy` | `1.972 mm` | 1,972 mm | Umlenkhebel rechts: Kugel Servo-Anlenkung quer zum Drehpunkt |
| `va_lk_r_y` | `-va_lk_y_rechts` | -51,000 mm | abgeleitet: Drehpunkt Umlenkhebel rechts quer (Vorzeichen) |
| `va_servo_ab_dx` | `10.2 mm` | 10,200 mm | Servo: Abtriebsachse ab Gehaeuse-Vorderkante (Abtrieb vorne), vorlaeufig (Standardservo), am Teil messen |
| `va_servo_ab_x` | `servo_x_Ref + servo_l_Ref / 2 - va_servo_ab_dx` | 87,300 mm | abgeleitet: Servo-Abtriebsachse laengs |
| `va_servo_ab_y` | `servo_y_Ref` | -22,100 mm | abgeleitet: Servo-Abtriebsachse quer (Gehaeusemitte) |
| `va_sv_vx` | `-27.373 mm` | -27,373 mm | Servo-Saver: Kugel der Servo-Anlenkung laengs zur Abtriebsachse (Geradeaus), aus Kinematikrechnung |
| `va_sv_vy` | `12.282 mm` | 12,282 mm | Servo-Saver: Kugel quer zur Abtriebsachse (ausserhalb des Servogehaeuses) |
| `va_g0_x` | `va_lk_x + va_ulh_l_gx` | 113,918 mm | abgeleitet: Spurstangenkugel links innen, laengs (Konstruktionslage) |
| `va_g0_y` | `va_lk_y_links + va_ulh_l_gy` | 41,664 mm | abgeleitet: Spurstangenkugel links innen, quer |
| `va_gr0_x` | `va_lk_x_rechts + va_ulh_r_gx` | 111,308 mm | abgeleitet: Spurstangenkugel rechts innen, laengs |
| `va_gr0_y` | `va_lk_r_y + va_ulh_r_gy` | -45,572 mm | abgeleitet: Spurstangenkugel rechts innen, quer |
| `va_spst_l` | `sqrt(( va_s0_x - va_g0_x ) ^ 2 + ( va_s0_y - va_g0_y ) ^ 2 + ( va_s0_z - va_ulh_g_z ) ^ 2)` | 43,545 mm | abgeleitet: Spurstange links Kugelmitte bis Kugelmitte (Spannschloss 54539 3 x 23) |
| `va_spst_rl` | `sqrt(( va_s0r_x - va_gr0_x ) ^ 2 + ( va_s0r_y + va_gr0_y ) ^ 2 + ( va_s0r_z - va_ulh_g_z ) ^ 2)` | 43,385 mm | abgeleitet: Spurstange rechts Kugelmitte bis Kugelmitte (Spannschloss 54539 3 x 23) |
| `va_lg_l` | `sqrt(( va_lk_x + va_ulh_l_dx - va_lk_x_rechts - va_ulh_r_dx ) ^ 2 + ( va_lk_y_links + va_ulh_l_dy - va_lk_r_y - va_ulh_r_dy ) ^ 2)` | 96,764 mm | abgeleitet: Lenkgestaenge Kugelmitte bis Kugelmitte (Gewindestange M3 mit Kugelpfannen, Ersatz fuer 54539) |
| `va_sa_l` | `sqrt(( va_servo_ab_x + va_sv_vx - va_lk_x_rechts - va_ulh_r_ux ) ^ 2 + ( va_servo_ab_y + va_sv_vy - va_lk_r_y - va_ulh_r_uy ) ^ 2)` | 39,362 mm | abgeleitet: Servo-Anlenkung Kugelmitte bis Kugelmitte im Grundriss (Spannschloss 54539 3 x 23 bzw. Ersatz) |
| `va_lk_phi` | `0 deg` | 0,000° | Stellung der Lenkung: Drehwinkel des linken Umlenkhebels (0 = geradeaus; + = Rechtskurve), Pruefstellungen siehe va_lk_phi_l30/_r30 |
| `va_gl_x` | `va_lk_x + va_ulh_l_gx * cos(va_lk_phi) - va_ulh_l_gy * sin(va_lk_phi)` | 113,918 mm | abgeleitet: Spurstangenkugel links innen (Stellung), laengs |
| `va_gl_y` | `va_lk_y_links + va_ulh_l_gx * sin(va_lk_phi) + va_ulh_l_gy * cos(va_lk_phi)` | 41,664 mm | abgeleitet: Spurstangenkugel links innen (Stellung), quer |
| `va_lw_x` | `va_gl_x - va_t_x` | -19,106 mm | abgeleitet: Spurstangenkugel links relativ zu K0, laengs |
| `va_lw_y` | `va_gl_y - va_t_y` | -46,839 mm | abgeleitet: dito quer |
| `va_lw_z` | `va_ulh_g_z - va_t_z` | 13,574 mm | abgeleitet: dito Hoehe |
| `va_lq1_y` | `va_lw_y * cos(va_rho) + va_lw_z * sin(va_rho)` | -46,839 mm | abgeleitet: Rueckdrehung um X |
| `va_lq1_z` | `-va_lw_y * sin(va_rho) + va_lw_z * cos(va_rho)` | 13,574 mm | abgeleitet: Rueckdrehung um X |
| `va_lq_x` | `va_lw_x * cos(va_nachlauf) + va_lq1_z * sin(va_nachlauf)` | -18,113 mm | abgeleitet: Spurstangenkugel links im Achsschenkelsystem, laengs |
| `va_lq_y` | `va_lq1_y` | -46,839 mm | abgeleitet: dito quer |
| `va_lq_z` | `-va_lw_x * sin(va_nachlauf) + va_lq1_z * cos(va_nachlauf)` | 14,874 mm | abgeleitet: dito Hoehe |
| `va_ll_m` | `( va_sph_x ^ 2 + va_sph_y ^ 2 + va_sph_z ^ 2 + va_lq_x ^ 2 + va_lq_y ^ 2 + va_lq_z ^ 2 - va_spst_l ^ 2 ) / 2 - va_lq_z * va_sph_z` | 602,4 mm² | abgeleitet: Gelenkgleichung Spurstange links |
| `va_ll_a` | `va_lq_x * va_sph_x + va_lq_y * va_sph_y` | 602,4 mm² | abgeleitet: Gelenkgleichung Spurstange, a |
| `va_ll_b` | `va_lq_y * va_sph_x - va_lq_x * va_sph_y` | 902,7 mm² | abgeleitet: Gelenkgleichung Spurstange, b |
| `va_delta_l` | `2 * atan(va_ll_b / ( sqrt(va_ll_a ^ 2 + va_ll_b ^ 2) + va_ll_a )) - acos(va_ll_m / sqrt(va_ll_a ^ 2 + va_ll_b ^ 2))` | -0,000° | abgeleitet: Drehung des Achsschenkels links um die Lenkachse (Stellung) |
| `va_dl_x` | `va_lk_x + va_ulh_l_dx * cos(va_lk_phi) - va_ulh_l_dy * sin(va_lk_phi)` | 75,918 mm | abgeleitet: Lenkgestaenge-Kugel links (Stellung), laengs |
| `va_dl_y` | `va_lk_y_links + va_ulh_l_dx * sin(va_lk_phi) + va_ulh_l_dy * cos(va_lk_phi)` | 45,719 mm | abgeleitet: Lenkgestaenge-Kugel links (Stellung), quer |
| `va_dq_x` | `va_dl_x - va_lk_x_rechts` | -16,832 mm | abgeleitet: Lenkgestaenge-Kugel links relativ zum rechten Drehpunkt, laengs |
| `va_dq_y` | `va_dl_y - va_lk_r_y` | 96,719 mm | abgeleitet: dito quer |
| `va_dq_m` | `( va_ulh_r_dx ^ 2 + va_ulh_r_dy ^ 2 + va_dq_x ^ 2 + va_dq_y ^ 2 - va_lg_l ^ 2 ) / 2` | 332,9 mm² | abgeleitet: Gelenkgleichung Lenkgestaenge |
| `va_dq_a` | `va_dq_x * va_ulh_r_dx + va_dq_y * va_ulh_r_dy` | 332,9 mm² | abgeleitet: Gelenkgleichung Lenkgestaenge, a |
| `va_dq_b` | `va_dq_y * va_ulh_r_dx - va_dq_x * va_ulh_r_dy` | -1912,7 mm² | abgeleitet: Gelenkgleichung Lenkgestaenge, b |
| `va_lk_phi_r` | `2 * atan(va_dq_b / ( sqrt(va_dq_a ^ 2 + va_dq_b ^ 2) + va_dq_a )) + acos(va_dq_m / sqrt(va_dq_a ^ 2 + va_dq_b ^ 2))` | -0,000° | abgeleitet: Drehwinkel rechter Umlenkhebel (Stellung) |
| `va_gr_x` | `va_lk_x_rechts + va_ulh_r_gx * cos(va_lk_phi_r) - va_ulh_r_gy * sin(va_lk_phi_r)` | 111,308 mm | abgeleitet: Spurstangenkugel rechts innen (Stellung), laengs |
| `va_gr_y` | `va_lk_r_y + va_ulh_r_gx * sin(va_lk_phi_r) + va_ulh_r_gy * cos(va_lk_phi_r)` | -45,572 mm | abgeleitet: Spurstangenkugel rechts innen (Stellung), quer |
| `va_grm_x` | `va_gr_x` | 111,308 mm | abgeleitet: Spurstangenkugel rechts gespiegelt, laengs |
| `va_grm_y` | `-va_gr_y` | 45,572 mm | abgeleitet: Spurstangenkugel rechts gespiegelt, quer (Y positiv) |
| `va_rw_x` | `va_grm_x - va_t_x` | -21,716 mm | abgeleitet: Spurstangenkugel rechts (gespiegelt) relativ zu K0, laengs |
| `va_rw_y` | `va_grm_y - va_t_y` | -42,931 mm | abgeleitet: dito quer |
| `va_rw_z` | `va_ulh_g_z - va_t_z` | 13,574 mm | abgeleitet: dito Hoehe |
| `va_rq1_y` | `va_rw_y * cos(va_rho) + va_rw_z * sin(va_rho)` | -42,931 mm | abgeleitet: Rueckdrehung um X |
| `va_rq1_z` | `-va_rw_y * sin(va_rho) + va_rw_z * cos(va_rho)` | 13,574 mm | abgeleitet: Rueckdrehung um X |
| `va_rq_x` | `va_rw_x * cos(va_nachlauf) + va_rq1_z * sin(va_nachlauf)` | -20,717 mm | abgeleitet: Spurstangenkugel rechts (gespiegelt) im Achsschenkelsystem, laengs |
| `va_rq_y` | `va_rq1_y` | -42,931 mm | abgeleitet: dito quer |
| `va_rq_z` | `-va_rw_x * sin(va_nachlauf) + va_rq1_z * cos(va_nachlauf)` | 15,056 mm | abgeleitet: dito Hoehe |
| `va_rl_m` | `( va_sph_rx ^ 2 + va_sph_ry ^ 2 + va_sph_z ^ 2 + va_rq_x ^ 2 + va_rq_y ^ 2 + va_rq_z ^ 2 - va_spst_rl ^ 2 ) / 2 - va_rq_z * va_sph_z` | 452,0 mm² | abgeleitet: Gelenkgleichung Spurstange rechts (gespiegelt) |
| `va_rl_a` | `va_rq_x * va_sph_rx + va_rq_y * va_sph_ry` | 452,0 mm² | abgeleitet: Gelenkgleichung Spurstange, a |
| `va_rl_b` | `va_rq_y * va_sph_rx - va_rq_x * va_sph_ry` | 836,7 mm² | abgeleitet: Gelenkgleichung Spurstange, b |
| `va_delta_r` | `2 * atan(va_rl_b / ( sqrt(va_rl_a ^ 2 + va_rl_b ^ 2) + va_rl_a )) - acos(va_rl_m / sqrt(va_rl_a ^ 2 + va_rl_b ^ 2))` | -0,000° | abgeleitet: Drehung des Achsschenkels rechts (gespiegelt) um die Lenkachse (Stellung) |
| `va_lenk_l` | `va_delta_l` | -0,000° | Pruefmass: Lenkwinkel links um die Lenkachse (+ = Linkskurve) |
| `va_lenk_r` | `-va_delta_r` | 0,000° | Pruefmass: Lenkwinkel rechts um die Lenkachse (+ = Linkskurve) |
| `va_u_x` | `va_lk_x_rechts + va_ulh_r_ux * cos(va_lk_phi_r) - va_ulh_r_uy * sin(va_lk_phi_r)` | 63,388 mm | abgeleitet: Kugel Servo-Anlenkung am rechten Umlenkhebel (Stellung), laengs |
| `va_u_y` | `va_lk_r_y + va_ulh_r_ux * sin(va_lk_phi_r) + va_ulh_r_uy * cos(va_lk_phi_r)` | -49,028 mm | abgeleitet: dito quer |
| `va_sq_x` | `va_u_x - va_servo_ab_x` | -23,912 mm | abgeleitet: Kugel Servo-Anlenkung relativ zur Servoachse, laengs |
| `va_sq_y` | `va_u_y - va_servo_ab_y` | -26,928 mm | abgeleitet: dito quer |
| `va_sq_m` | `( va_sv_vx ^ 2 + va_sv_vy ^ 2 + va_sq_x ^ 2 + va_sq_y ^ 2 - va_sa_l ^ 2 ) / 2` | 323,8 mm² | abgeleitet: Gelenkgleichung Servo-Anlenkung |
| `va_sq_a` | `va_sq_x * va_sv_vx + va_sq_y * va_sv_vy` | 323,8 mm² | abgeleitet: Gelenkgleichung Servo-Anlenkung, a |
| `va_sq_b` | `va_sq_y * va_sv_vx - va_sq_x * va_sv_vy` | 1030,8 mm² | abgeleitet: Gelenkgleichung Servo-Anlenkung, b |
| `va_servo_phi` | `2 * atan(va_sq_b / ( sqrt(va_sq_a ^ 2 + va_sq_b ^ 2) + va_sq_a )) - acos(va_sq_m / sqrt(va_sq_a ^ 2 + va_sq_b ^ 2))` | -0,000° | Pruefmass: Drehwinkel des Servoabtriebs (Stellung), muss innerhalb +-40 Grad bleiben (MECH-VAC-007) |
| `va_ulh_u_h` | `7.8 mm` | 7,800 mm | Umlenkhebel rechts: Erhoehung fuer den Kugelkopf der Servo-Anlenkung (Servo-Anlenkung kreuzt das Lenkgestaenge darueber; aus Kollisionsrechnung) |
| `va_ulh_u_z` | `va_ulh_d_z + va_ulh_u_h` | 80,026 mm | abgeleitet: Kugel der Servo-Anlenkung am rechten Umlenkhebel (stehend auf der Erhoehung) |
| `va_sv_v_z` | `va_ulh_d_z + 0.8 mm` | 73,026 mm | abgeleitet: Kugel der Servo-Anlenkung am Servo-Saver (haengend; Saver-Arm bleibt 1,2 mm unter dem Oberdeck), aus Kollisionsrechnung |
| `va_e_y` | `va_t_y + va_e_hy * cos(va_kappa) - va_e_hz * sin(va_kappa)` | 81,601 mm | abgeleitet: Kugel C-Hub (Sturzstange) quer (Stellung) |
| `va_e_z` | `va_t_z + va_e_hy * sin(va_kappa) + va_e_hz * cos(va_kappa)` | 71,620 mm | abgeleitet: Kugel C-Hub Hoehe (Stellung) |
| `va_sl_dx` | `va_sph_x * cos(va_delta_l) - va_sph_y * sin(va_delta_l)` | -21,093 mm | abgeleitet: Spurhebelkugel nach Lenkdrehung, laengs (Achsschenkelsystem) |
| `va_sl_dy` | `va_sph_x * sin(va_delta_l) + va_sph_y * cos(va_delta_l)` | -4,705 mm | abgeleitet: dito quer |
| `va_sl_hz` | `va_sl_dx * sin(va_nachlauf) + va_sph_z * cos(va_nachlauf)` | 2,806 mm | abgeleitet: dito nach Nachlauf, Hoehe |
| `va_sl_x` | `va_t_x + va_sl_dx * cos(va_nachlauf) - va_sph_z * sin(va_nachlauf)` | 111,684 mm | abgeleitet: Spurhebelkugel l (Stellung), laengs |
| `va_sl_y` | `( va_t_y + va_sl_dy * cos(va_rho) - va_sl_hz * sin(va_rho) )` | 83,798 mm | abgeleitet: Spurhebelkugel l (Stellung), quer |
| `va_sl_z` | `va_t_z + va_sl_dy * sin(va_rho) + va_sl_hz * cos(va_rho)` | 43,458 mm | abgeleitet: Spurhebelkugel l (Stellung), Hoehe |
| `va_kl_ax` | `-va_u_kreuz * cos(va_eps) * sin(va_delta_l)` | 0,000 mm | abgeleitet: Kreuzstift im Becher nach Lenkdrehung, laengs (Achsschenkelsystem) |
| `va_kl_ay` | `va_u_kreuz * cos(va_eps) * cos(va_delta_l)` | 1,300 mm | abgeleitet: dito quer |
| `va_kl_hz` | `va_kl_ax * sin(va_nachlauf) + va_u_kreuz * sin(va_eps) * cos(va_nachlauf)` | 0,023 mm | abgeleitet: dito nach Nachlauf, Hoehe |
| `va_kl_x` | `va_t_x + va_kl_ax * cos(va_nachlauf) - va_u_kreuz * sin(va_eps) * sin(va_nachlauf)` | 133,023 mm | abgeleitet: Kreuzstift l (Stellung), laengs |
| `va_kl_y` | `( va_t_y + va_kl_ay * cos(va_rho) - va_kl_hz * sin(va_rho) )` | 89,803 mm | abgeleitet: Kreuzstift l (Stellung), quer |
| `va_kl_z` | `va_t_z + va_kl_ay * sin(va_rho) + va_kl_hz * cos(va_rho)` | 40,674 mm | abgeleitet: Kreuzstift l (Stellung), Hoehe |
| `va_sr_dx` | `va_sph_rx * cos(va_delta_r) - va_sph_ry * sin(va_delta_r)` | -19,930 mm | abgeleitet: Spurhebelkugel nach Lenkdrehung, laengs (Achsschenkelsystem) |
| `va_sr_dy` | `va_sph_rx * sin(va_delta_r) + va_sph_ry * cos(va_delta_r)` | -0,911 mm | abgeleitet: dito quer |
| `va_sr_hz` | `va_sr_dx * sin(va_nachlauf) + va_sph_z * cos(va_nachlauf)` | 2,887 mm | abgeleitet: dito nach Nachlauf, Hoehe |
| `va_sr_x` | `va_t_x + va_sr_dx * cos(va_nachlauf) - va_sph_z * sin(va_nachlauf)` | 112,844 mm | abgeleitet: Spurhebelkugel r (Stellung), laengs |
| `va_sr_y` | `-( va_t_y + va_sr_dy * cos(va_rho) - va_sr_hz * sin(va_rho) )` | -87,592 mm | abgeleitet: Spurhebelkugel r (Stellung), quer |
| `va_sr_z` | `va_t_z + va_sr_dy * sin(va_rho) + va_sr_hz * cos(va_rho)` | 43,539 mm | abgeleitet: Spurhebelkugel r (Stellung), Hoehe |
| `va_kr_ax` | `-va_u_kreuz * cos(va_eps) * sin(va_delta_r)` | 0,000 mm | abgeleitet: Kreuzstift im Becher nach Lenkdrehung, laengs (Achsschenkelsystem) |
| `va_kr_ay` | `va_u_kreuz * cos(va_eps) * cos(va_delta_r)` | 1,300 mm | abgeleitet: dito quer |
| `va_kr_hz` | `va_kr_ax * sin(va_nachlauf) + va_u_kreuz * sin(va_eps) * cos(va_nachlauf)` | 0,023 mm | abgeleitet: dito nach Nachlauf, Hoehe |
| `va_kr_x` | `va_t_x + va_kr_ax * cos(va_nachlauf) - va_u_kreuz * sin(va_eps) * sin(va_nachlauf)` | 133,023 mm | abgeleitet: Kreuzstift r (Stellung), laengs |
| `va_kr_y` | `-( va_t_y + va_kr_ay * cos(va_rho) - va_kr_hz * sin(va_rho) )` | -89,803 mm | abgeleitet: Kreuzstift r (Stellung), quer |
| `va_kr_z` | `va_t_z + va_kr_ay * sin(va_rho) + va_kr_hz * cos(va_rho)` | 40,674 mm | abgeleitet: Kreuzstift r (Stellung), Hoehe |
| `va_dr_x` | `va_lk_x_rechts + va_ulh_r_dx * cos(va_lk_phi_r) - va_ulh_r_dy * sin(va_lk_phi_r)` | 72,974 mm | abgeleitet: Lenkgestaenge-Kugel rechts (Stellung), laengs |
| `va_dr_y` | `va_lk_r_y + va_ulh_r_dx * sin(va_lk_phi_r) + va_ulh_r_dy * cos(va_lk_phi_r)` | -51,000 mm | abgeleitet: dito quer |
| `va_v_x` | `va_servo_ab_x + va_sv_vx * cos(va_servo_phi) - va_sv_vy * sin(va_servo_phi)` | 59,927 mm | abgeleitet: Kugel Servo-Saver (Stellung), laengs |
| `va_v_y` | `va_servo_ab_y + va_sv_vx * sin(va_servo_phi) + va_sv_vy * cos(va_servo_phi)` | -9,818 mm | abgeleitet: dito quer |
| `va_pruef_spst_l` | `sqrt(( va_sl_x - va_gl_x ) ^ 2 + ( va_sl_y - va_gl_y ) ^ 2 + ( va_sl_z - va_ulh_g_z ) ^ 2) - va_spst_l` | 0,000 mm | Pruefmass: Spurstange links in der Stellung minus Sollaenge, muss 0 sein (Gelenkgleichung richtig geloest) |
| `va_pruef_spst_r` | `sqrt(( va_sr_x - va_gr_x ) ^ 2 + ( va_sr_y - va_gr_y ) ^ 2 + ( va_sr_z - va_ulh_g_z ) ^ 2) - va_spst_rl` | 0,000 mm | Pruefmass: Spurstange rechts in der Stellung minus Sollaenge, muss 0 sein |
| `va_pruef_lg` | `sqrt(( va_dl_x - va_dr_x ) ^ 2 + ( va_dl_y - va_dr_y ) ^ 2) - va_lg_l` | 0,000 mm | Pruefmass: Lenkgestaenge in der Stellung minus Sollaenge, muss 0 sein |
| `va_pruef_sa` | `sqrt(( va_v_x - va_u_x ) ^ 2 + ( va_v_y - va_u_y ) ^ 2) - va_sa_l` | 0,000 mm | Pruefmass: Servo-Anlenkung in der Stellung minus Sollaenge (Grundriss), muss 0 sein |
| `va_pruef_sl` | `sqrt(( va_e0_x - va_sl_c_x ) ^ 2 + ( va_e_y - va_sl_c_y ) ^ 2 + ( va_e_z - va_sl_c_z ) ^ 2) - va_sl_l0 - va_sl_dl` | -0,000 mm | Pruefmass: Sturzstange in der Stellung minus Sollaenge, muss 0 sein |
| `va_ulh_lager_d` | `8 mm` | 8,000 mm | Lager 5x8x2,5 (Pos. 15): Aussendurchmesser, belegt (XRAY 940508) |
| `va_ulh_lager_b` | `2.5 mm` | 2,500 mm | Lager 5x8x2,5: Breite, belegt |
| `va_ulh_lager_wand` | `2 mm` | 2,000 mm | Umlenkhebel: Wand um die Lagersitze (>= 2 mm, MECH-VAC-016) |
| `va_ulh_nabe_h` | `8 mm` | 8,000 mm | Umlenkhebel: Nabenhoehe (2 Lager 2,5 mm + Steg 3 mm) |
| `va_ulh_nabe_d` | `va_ulh_lager_d + va_lager_spiel + 2 * va_ulh_lager_wand` | 12,100 mm | abgeleitet: Aussendurchmesser Nabe Umlenkhebel |
| `va_ulh_steg_bohr` | `6 mm` | 6,000 mm | Umlenkhebel: Bohrung im Steg zwischen den Lagern (Huelse 5 mm), Anschlag der Aussenringe |
| `va_ulh_spalt` | `0.5 mm` | 0,500 mm | Umlenkhebel: Lager steht 0,5 mm ueber die Nabe vor |
| `va_ulh_bund_h` | `0.5 mm` | 0,500 mm | Lagerbock: Bund unter dem Innenring (Aussenring laeuft frei) |
| `va_ulh_bund_d` | `6.4 mm` | 6,400 mm | Lagerbock: Bund-Durchmesser (Innenring 5x8, am Lager pruefen) |
| `va_ulh_arm_b` | `8 mm` | 8,000 mm | Umlenkhebel: Breite der Hebelarme |
| `va_ulh_auge_d` | `8 mm` | 8,000 mm | Umlenkhebel: Durchmesser um die Gewindeeinsaetze der Kugelkoepfe |
| `va_ulh_nabe_z0` | `va_ulh_g_z + va_kugel_h + va_ulh_platte / 2 - va_ulh_nabe_h / 2` | 59,226 mm | abgeleitet: Unterkante Nabe Umlenkhebel |
| `va_lb_oben_z` | `va_ulh_nabe_z0 - va_ulh_spalt - va_ulh_bund_h` | 58,226 mm | abgeleitet: Oberkante Lagerbock (Auflage Bund) |
| `va_ulh_huelse_l` | `va_ulh_nabe_h + 2 * va_ulh_spalt` | 9,000 mm | abgeleitet: Laenge der Lagerhuelse (Messingrohr 5 x 0,9) |
| `va_servo_loch_dx` | `49.5 mm` | 49,500 mm | Servo: Lochabstand der Laschen laengs, vorlaeufig (Standardservo), am Teil messen (MECH-VAC-011) |
| `va_servo_loch_dy` | `10 mm` | 10,000 mm | Servo: Lochabstand der Laschen quer, vorlaeufig, am Teil messen |
| `va_servo_lasche_l` | `7.1 mm` | 7,100 mm | Servo: Ueberstand der Laschen ueber das Gehaeuse, vorlaeufig, am Teil messen |
| `va_servo_lasche_z` | `26 mm` | 26,000 mm | Servo: Unterseite der Laschen ueber dem Gehaeuseboden, vorlaeufig, am Teil messen |
| `va_servo_lasche_t` | `2.5 mm` | 2,500 mm | Servo: Dicke der Laschen, vorlaeufig |
| `va_servo_abtrieb_h` | `4 mm` | 4,000 mm | Servo: Hoehe der Abtriebswelle ueber dem Gehaeuse, vorlaeufig, am Teil messen (MECH-VAC-001) |
| `va_servo_abtrieb_d` | `6 mm` | 6,000 mm | Servo: Abtrieb 25Z, Durchmesser 6,0 mm (Lindinger) |
| `va_servo_z0` | `platte_oben_Ref` | 29,000 mm | abgeleitet: Servo steht auf der Grundplatte (Skelett) |
| `va_servo_oben` | `va_servo_z0 + servo_h_Ref` | 66,200 mm | abgeleitet: Oberkante Servogehaeuse |
| `va_servo_x_h` | `servo_x_Ref - servo_l_Ref / 2` | 57,200 mm | abgeleitet: Servo hinten (Gehaeuse) |
| `va_servo_x_v` | `servo_x_Ref + servo_l_Ref / 2` | 97,500 mm | abgeleitet: Servo vorne (Gehaeuse) |
| `va_sh_luft` | `1 mm` | 1,000 mm | Servohalter: Luft zu Servogehaeuse und UBEC-Huelle |
| `va_sh_wand` | `3.5 mm` | 3,500 mm | Servohalter: Dicke der Seitenwand zwischen Servo und UBEC |
| `va_sh_lz` | `va_servo_z0 + va_servo_lasche_z` | 55,000 mm | abgeleitet: Auflage der Servolaschen (Oberkante Servohalter) |
| `va_sh_vorne_y0` | `-31 mm` | -31,000 mm | Servohalter: vordere Laschenauflage beginnt quer erst hier (Freigang Spurstange rechts bei vollem Einschlag) |
| `va_sh_wand_x1` | `va_servo_x_v + 2 mm` | 99,500 mm | Servohalter: Ende der Seitenwand vorne (Freigang Spurstange rechts) |
| `va_sh_fuss_d` | `va_einsatz_d + 2 * va_wand_min` | 6,400 mm | abgeleitet: Fuss um die Einsaetze der Grundplatte rechts (Mindestwand, UBEC-Huelle) |
| `va_saver_moment` | `0.4` | 0,4 | Servo-Saver: Ausloesemoment Soll in Nm (MECH-VAC-010: > 1,5 x Lenkmoment, <= 0,82 Nm), Rechnung docs/vorderachse.md |
| `va_sv_mu` | `0.15` | 0,15 | Servo-Saver: Reibwert Rastnocken (Kunststoff, gefettet), Annahme |
| `va_sv_rippe_w` | `45 deg` | 45,000° | Servo-Saver: Flankenwinkel der Rastnocken |
| `va_sv_rippe_h` | `1 mm` | 1,000 mm | Servo-Saver: Hoehe der Rastnocken (Hub der Feder beim Ausloesen) |
| `va_sv_rippe_r0` | `4 mm` | 4,000 mm | Servo-Saver: Rastnocken innen (Radius) |
| `va_sv_rippe_r1` | `8.5 mm` | 8,500 mm | Servo-Saver: Rastnocken aussen (Radius) |
| `va_sv_rm` | `( va_sv_rippe_r0 + va_sv_rippe_r1 ) / 2` | 6,250 mm | abgeleitet: mittlerer Radius der Rastnocken |
| `va_sv_federkraft` | `va_saver_moment * 1000 / ( va_sv_rm / 1 mm * tan(va_sv_rippe_w + atan(va_sv_mu)) )` | 47,3 | abgeleitet: Federvorspannkraft in N fuer va_saver_moment |
| `va_sv_feder_da` | `10 mm` | 10,000 mm | Feder Servo-Saver: Druckfeder Aussendurchmesser (Stueckliste) |
| `va_sv_feder_d` | `1.2 mm` | 1,200 mm | Feder Servo-Saver: Drahtdurchmesser |
| `va_sv_feder_l0` | `20 mm` | 20,000 mm | Feder Servo-Saver: ungespannte Laenge |
| `va_sv_feder_n` | `5.5` | 5,5 | Feder Servo-Saver: federnde Windungen |
| `va_sv_feder_r` | `81500 * ( va_sv_feder_d / 1 mm ) ^ 4 / ( 8 * ( ( va_sv_feder_da - va_sv_feder_d ) / 1 mm ) ^ 3 * va_sv_feder_n )` | 5,636 | abgeleitet: Federrate in N/mm (G = 81500 N/mm2, DIN EN 13906-1) |
| `va_sv_feder_lc` | `( va_sv_feder_n + 2 ) * va_sv_feder_d` | 9,000 mm | abgeleitet: Blocklaenge der Feder |
| `va_sv_feder_l` | `va_sv_feder_l0 - va_sv_federkraft / va_sv_feder_r * 1 mm` | 11,607 mm | abgeleitet: Federlaenge bei Vorspannung (Einbaulaenge) |
| `va_sv_feder_reserve` | `va_sv_feder_l - va_sv_rippe_h - va_sv_feder_lc` | 1,607 mm | Pruefmass: Abstand zur Blocklaenge beim Ausloesen, muss > 0 sein |
| `va_horn_spalt` | `0.5 mm` | 0,500 mm | Servohorn (Alu 25Z, Zukauf): Abstand zum Servogehaeuse |
| `va_horn_h` | `5 mm` | 5,000 mm | Servohorn: Nabenhoehe, vorlaeufig, am Teil messen |
| `va_horn_hub_d` | `10 mm` | 10,000 mm | Servohorn: Nabendurchmesser, vorlaeufig |
| `va_horn_arm_l` | `24 mm` | 24,000 mm | Servohorn doppelt: Laenge ueber beide Arme, vorlaeufig; laengere Hornarme auf 24 mm kuerzen (Abstand zur Kardanwellen-Huelle 4WD) |
| `va_horn_arm_b` | `7 mm` | 7,000 mm | Servohorn: Armbreite, vorlaeufig |
| `va_horn_arm_t` | `2.5 mm` | 2,500 mm | Servohorn: Armdicke, vorlaeufig |
| `va_horn_loch_r` | `7.5 mm` | 7,500 mm | Servohorn: Radius der Befestigungsloecher fuer die Saver-Nabe, vorlaeufig (am Horn messen, ggf. nachbohren) |
| `va_sv_z0` | `va_servo_oben + va_horn_spalt + va_horn_arm_t` | 69,200 mm | abgeleitet: Unterkante Saver-Nabe (auf den Hornarmen) |
| `va_sv_arm_z0` | `va_sv_v_z + va_kugel_h` | 79,026 mm | abgeleitet: Unterkante Saver-Arm (Kugelkopf haengend) |
| `va_sv_arm_h` | `4 mm` | 4,000 mm | Servo-Saver: Dicke des Arms (Oberkante 1 mm unter dem Oberdeck) |
| `va_sv_nabe_d` | `18 mm` | 18,000 mm | Servo-Saver: Durchmesser Nabe und Armscheibe (Abstand zum Lenkgestaenge) |
| `va_sv_post_d` | `7 mm` | 7,000 mm | Servo-Saver: Zapfen der Nabe (Fuehrung Arm und Feder, Einsatz M3) |
| `va_sv_post_l` | `5 mm` | 5,000 mm | Servo-Saver: Zapfen ueber dem Arm (Federfuehrung) |
| `va_sv_arm_b` | `8 mm` | 8,000 mm | Servo-Saver: Breite des Hebels zur Kugel |
| `va_sv_drehung` | `atan(va_sv_vy / va_sv_vx) + 180 deg` | 155,835° | abgeleitet: Richtung der Saver-Kugel gegen +X (Hebel nach hinten) |
| `va_lk_phi_l30` | `-28.3322 deg` | -28,332° | Pruefstellung Lenkung voll links: va_lk_phi, bei der das linke (innere) Rad 30 Grad einschlaegt (Pruefskript); entspricht dem Servo-Endpunkt |
| `va_lk_phi_r30` | `28.2979 deg` | 28,298° | Pruefstellung Lenkung voll rechts: rechtes (inneres) Rad 30 Grad (Pruefskript) |
| `va_db_rand` | `5 mm` | 5 mm | Daempferbruecke: Rand unter den unteren Schrauben (Unterkante 2 mm ueber der Grundplatte) |
| `va_db_auge_d` | `14 mm` | 14 mm | Daempferbruecke: Rundung um Kugelkopf und Daempferbolzen |
| `va_db_r` | `2 mm` | 2 mm | Daempferbruecke: Radius aller Kanten parallel zu X (fraesgerecht, Innenradien >= 1,5 mm) |
| `va_d_stiel_d` | `6 mm` | 6 mm | CVA-Daempfer vorne: Stiel/Kolbenstangenende und Kappe zwischen Auge und Koerper, vorlaeufig |
| `va_ch_kipp` | `0.6 mm` | 0,6 mm | C-Hub: Arme und Steg 0,6 mm kuerzer als die Ohren (die Ohren sind um den Nachlauf gekippt, Luft zu den Achsschenkel-Augen) |
| `va_ch_knoten_y1` | `-1.5 mm` | -1,5 mm | C-Hub: Knoten oben zwischen Kingpin-Ohr und Kugelauge, Aussenkante quer (Reifenfreigang bei vollem Einschlag) |

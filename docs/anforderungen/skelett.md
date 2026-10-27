# Anforderungen: Skelettmodell des Fahrzeugs in Fusion

- **Kürzel:** SKE
- **Domäne:** Mechanik
- **Status:** umgesetzt
- **Stand:** 2026-10-27

## Zweck
Ein parametrisches Grundgerüst des ganzen Fahrzeugs in Fusion: Fahrzeugparameter, Radpositionen mit Bewegungsraum, Hüllkörper aller räumlich relevanten Zukaufteile aus `bom/stueckliste.csv` und Bauraum für den späteren 4WD-Antrieb. Das Skelett ist kein Bauteil. Es ist die Bezugsgeometrie, an der Grundplatte, Achsen und Halter später konstruiert werden.

**Meilenstein:** Man sieht, ob alles hineinpasst, wie lang die Grundplatte wird und wo sie für den Druck geteilt wird.

## Schnittstellen
| Zu | Art | Beschreibung |
|---|---|---|
| Gesamtfahrzeug (`fahrzeug.md`) | mechanisch | MECH-FZG-001 (Parameter `radstand`, `spurbreite`), MECH-FZG-002 (4WD-Hüllkörper kollisionsfrei), MECH-FZG-003 (Bauraum 256 × 256 × 256 mm), MECH-FZG-005 (Federweg ≥ 30 mm), MECH-FZG-006 (Bodenfreiheit 25 mm) |
| Zukaufteile v1 (`zukaufteile-v1.md`, `bom/stueckliste.csv`) | mechanisch | Maße der Zukaufteile; Abschnitt „Vorgaben für die Konstruktion“ in `docs/zukaufteile-v1.md` (Mittelwellen 93/68 mm, Antriebswellen hinten 67 mm, Hebelverhältnis Dämpfer ≥ 1,15) |
| Grundplatte, Achsen, Mittelantrieb, Lenkung, Elektronikhalter (spätere Anforderungen) | mechanisch | Diese Baugruppen werden später auf das Skelett referenziert (Parameter und Bezugsebenen). |

## Koordinatensystem
- Ursprung: in der Fahrzeugmitte (quer), in der Mitte zwischen Vorder- und Hinterachse (längs), auf der Bodenebene (Höhe).
- **X** längs, positiv nach vorne. **Y** quer, positiv nach links. **Z** hoch, Boden bei Z = 0.
- Fahrzeug in Konstruktionslage: statisch, fahrfertig, Räder auf dem Boden, Lenkung geradeaus.

## Anforderungen
| ID | Priorität | Anforderung | Abnahmekriterium |
|---|---|---|---|
| MECH-SKE-001 | MUSS | Benutzerparameter für die Fahrzeugmaße: `radstand` = 283,5 mm, `spurbreite` = 250 mm (über die Räder), `rad_durchmesser` = 85 mm, `rad_breite` = 40 mm, `bodenfreiheit` = 25 mm, `federweg` = 35 mm, `plattenstaerke` = 4 mm. Alle Positionen im Skelett hängen über Ausdrücke an diesen Parametern, nicht an festen Zahlen. | Parameterliste in Fusion. Test: `radstand` auf 290 mm und `spurbreite` auf 260 mm setzen → Modell rechnet ohne Fehler in der Zeitleiste, Räder und abhängige Hüllkörper folgen (Screenshot), danach Rücksetzen auf die Startwerte. |
| MECH-SKE-002 | MUSS | Jedes Maß eines Hüllkörpers ist ein Benutzerparameter mit Präfix der Baugruppe (z. B. `akku_laenge`, `motor_d`). Im Kommentar des Parameters steht die Quelle oder „vorläufig“. | Parameterliste: kein Hüllkörper mit festem Zahlenwert in Skizze oder Extrusion; jeder Hüllkörper-Parameter hat einen Kommentar. |
| MECH-SKE-003 | MUSS | Koordinatensystem wie oben beschrieben. Bezugsebenen für Vorderachse, Hinterachse, Fahrzeugmitte, Boden und Unterkante Grundplatte sind als benannte Konstruktionsebenen vorhanden. | Sichtprüfung im Browser: benannte Ebenen vorhanden und an Parameter gebunden. |
| MECH-SKE-004 | MUSS | 4 Rad-Hüllkörper (Zylinder `rad_durchmesser` × `rad_breite`) in statischer Lage: Radmitten bei X = ±`radstand`/2, Y = ±(`spurbreite` − `rad_breite`)/2, Z = `rad_durchmesser`/2. | Messen in Fusion: Radmittenabstand längs = 283,5 mm, Außenmaß über die Räder = 250,0 mm, Räder berühren Z = 0. |
| MECH-SKE-005 | MUSS | Bewegungsraum der Räder: je Rad ein Hüllkörper über den ganzen Federweg (Einfederung `einfederweg` + Ausfederung `ausfederweg` = `federweg`). Vorne zusätzlich über den Lenkeinschlag ±`lenkwinkel_max` um eine Lenkachse im Abstand `lenkachse_versatz` innerhalb der Radmitte. | Sichtprüfung und Messen: Hüllkörper überdecken den vollen Federweg (Höhe = `rad_durchmesser` + `federweg`) und vorne den vollen Lenkeinschlag. |
| MECH-SKE-006 | MUSS | Hüllkörper für alle Zukaufteile mit räumlicher Ausdehnung in Einbaulage: Akku, Motor, Motorritzel, Hauptzahnrad mit Rutschkupplung, Mittelwelle hinten (93 mm), Hinterachsgetriebe (Diff mit Tellerrad und Kegelritzel), Antriebswellen hinten (67 mm), Radachsen mit Mitnehmern (vorne und hinten), 4 Dämpfer, Lenkservo, Fahrtenregler mit Lüfter, Empfänger, UBEC, XT60-Stecker. Normteile (Schrauben, Lager, Kugelköpfe) bekommen keinen eigenen Hüllkörper. | Liste in `docs/skelett.md`: jede räumlich relevante Position der Stückliste ist einem Hüllkörper zugeordnet oder begründet ausgelassen. Jeder Hüllkörper ist eine eigene, benannte Komponente. |
| MECH-SKE-007 | MUSS | Maßquelle jedes Hüllkörpers ist dokumentiert: **belegt** (Stückliste mit Quelle) oder **vorläufig** (abgeleitet aus Anleitung TLR03026, Produktfoto oder Vergleichsteil, mit Zuschlag `huelle_zuschlag` = 2 mm je Seite). Bei widersprüchlichen Quellen gilt das größere Maß. | Tabelle in `docs/skelett.md` mit Hüllkörper, Maßen, Status belegt/vorläufig und Quelle. Vorläufige Hüllkörper sind in Fusion farblich unterscheidbar. |
| MECH-SKE-008 | MUSS | Layout wie beim Spender 22X-4: Akku längs auf der linken Seite, Motor und Rutschkupplung mittig rechts, Mittelwelle 93 mm zum Hinterachsgetriebe, Regler, Empfänger und UBEC rechts vorne bzw. wo Platz ist, Servo vorne. Abstand Mittelschott ↔ Hinterachsgetriebe passend zur Mittelwelle 93 mm. | Messen in Fusion: Abstand der Wellenaufnahmen passt zu 93 mm (bzw. 68 mm vorne). Screenshot von oben. |
| MECH-SKE-009 | MUSS | Bauraum für 4WD (Phase 2): Hüllkörper für Vorderachsgetriebe (wie hinten, gespiegelt), vordere Mittelwelle 68 mm, vordere Antriebswellen und Abtrieb vorne am Mittelantrieb. Gilt zugleich als Nachweis für MECH-FZG-002. | Interferenzprüfung (MECH-SKE-010) schließt die 4WD-Hüllkörper ein. |
| MECH-SKE-010 | MUSS | Alle Hüllkörper sind kollisionsfrei, einschließlich Rad-Bewegungsraum, Lenkeinschlag und 4WD-Bauraum. Gewollte Berührungen (z. B. Welle in Getriebe) sind als solche dokumentiert. | Fusion-Interferenzanalyse über alle Hüllkörper: 0 Überschneidungen außer den dokumentierten gewollten. Ergebnis in `docs/skelett.md`. |
| MECH-SKE-011 | MUSS | Bodenfreiheit: Unterkante Grundplatte bei Z = `bodenfreiheit`. Außer den Rädern liegt kein Hüllkörper unter dieser Ebene. | Messen in Fusion: tiefster Punkt aller Hüllkörper außer Rädern ≥ 25 mm. |
| MECH-SKE-012 | MUSS | Hüllkörper der Grundplatte: Umriss aus den darauf sitzenden Hüllkörpern abgeleitet, Dicke `plattenstaerke`. Länge und Breite sind als Ergebnis ausgewiesen. | Gesamtlänge und -breite der Grundplatte in `docs/skelett.md` (Messwert aus Fusion). |
| MECH-SKE-013 | MUSS | Teilung der Grundplatte für den Druck: Trennstelle als Parameter `teilung_x`, Überlappung des Stoßes als Parameter `teilung_ueberlappung`. Beide Teile einschließlich Überlappung passen auf einen Drucker mit 256 × 256 mm (mit 3 mm Rand, also ≤ 250 × 250 mm). Die Trennstelle liegt nicht unter dem Hüllkörper von Mittelschott, Motor oder einem Achsgetriebe. | Messen in Fusion: Hüllquader beider Teile ≤ 250 × 250 mm. Begründung der Lage in `docs/skelett.md`. |
| MECH-SKE-014 | MUSS | Schutz vor drehenden Teilen: Für Motorritzel und Hauptzahnrad ist ein Bauraum für eine Zahnradabdeckung reserviert (Abstand ≥ 3 mm zum Zahnrad), der mit keinem anderen Hüllkörper kollidiert. | Hüllkörper „Zahnradabdeckung“ vorhanden, in der Interferenzprüfung enthalten. |
| MECH-SKE-015 | SOLL | Akku-Wechsel (MECH-FZG-008): Über dem Akku-Hüllkörper bleibt ein freier Entnahmeweg nach oben oder zur Seite. | Sichtprüfung: kein Hüllkörper im Entnahmeweg. |
| MECH-SKE-016 | SOLL | Schwerpunkt: Hüllkörper mit belegter Masse (Akku, Motor, Regler, Servo, Empfänger, UBEC, Räder) bekommen ihre Masse. Der Schwerpunkt dieser Teile liegt quer höchstens 10 mm neben der Fahrzeugmitte. | Schwerpunkt-Koordinaten aus Fusion in `docs/skelett.md`. |
| DOC-SKE-001 | MUSS | Dokumentation `docs/skelett.md`: Koordinatensystem, Parameterliste, Hüllkörper-Tabelle (MECH-SKE-007), Ergebnis Meilenstein (passt alles hinein, Länge Grundplatte, Trennstelle), Screenshots von oben, von der Seite und isometrisch in `docs/images/`. | Datei vorhanden, Screenshots eingebunden. |
| DOC-SKE-002 | MUSS | Fusion: Projekt „open-rc-car“ anlegen, Design „open-rc-car-skelett“ darin speichern. Export nach `cad/fusion/skelett.f3d` und `cad/step/skelett.step` (über Git LFS). | Dateien im PR, LFS-Pointer (`git lfs ls-files`). |
| DOC-SKE-003 | MUSS | `docs/plan.md`: Radstand 283,5 mm unter „Entscheidungen“ und in den Startwerten; Phase-0-Punkt „Skelettmodell“ abhaken. | Diff von `docs/plan.md` |

## Entscheidungen (vom Nutzer)
- 2026-10-27: Hüllkörper für Teile ohne gemessene Maße werden vorläufig aus Anleitung, Produktseiten und Vergleichsteilen abgeleitet, mit Zuschlag, als Parameter und als „vorläufig“ markiert. Nach Lieferung werden sie gemessen und ersetzt. (Grund: Skelett kann sofort starten.)
- 2026-10-27: Layout wie beim Spender TLR 22X-4: Akku längs links, Motor und Rutschkupplung mittig rechts, Elektronik rechts vorne, Servo vorne. (Grund: passt direkt zu den gekauften Mittelwellen 93/68 mm.)
- 2026-10-27: Radstand 283,5 mm statt 280 mm (Grund: wie der Spender, die Mittelwellen sind darauf abgestimmt).
- 2026-10-27: Fusion-Projekt „open-rc-car“ neu anlegen, Design „open-rc-car-skelett“.
- 2026-10-27: Anforderungsdokument vom Nutzer freigegeben, mit Speichern und Export in Fusion.
- 2026-10-27 (nach Review Durchlauf 1): Räder bekommen für MECH-SKE-016 eine vorläufige Masse (Vergleichswert eines 1:10-Buggyrads, ca. 100 g pro Rad) als Parameter, markiert als „vorläufig“, nach Lieferung wiegen. (Grund: Keine Quelle nennt das Gewicht.)
- 2026-10-27 (nach Review Durchlauf 1): Die Trennstelle der Grundplatte darf unter Akku, Regler, UBEC und Servo liegen. Der Akku überdeckt ohnehin den ganzen zulässigen Bereich. Die Verbindung am Stoß legt die Anforderung „Grundplatte“ fest. (Grund: Eine Teilung frei von Akku und Elektronik ginge nur mit anderem Layout oder dreiteiliger Platte.)

## Annahmen (abgeleitet, noch nicht bestätigt)
- Federweg-Aufteilung: `einfederweg` = 2/3 und `ausfederweg` = 1/3 von `federweg` (üblich bei 1:10-Buggys). Nur für den Bewegungsraum, die echte Kinematik kommt mit den Querlenkern.
- `lenkwinkel_max` = 30°, `lenkachse_versatz` = 20 mm (Lenkachse innerhalb der Radmitte). Vorläufig, wird mit der Lenkung festgelegt.
- Dämpfer-Hüllkörper: Zylinder aus Gehäuse 42 mm plus Kolbenstange, Außendurchmesser mit Feder vorläufig; Lage etwa wie beim 22X-4 (oben an Dämpferbrücke, unten am Querlenker), statische Länge vorläufig.
- `plattenstaerke` = 4 mm gilt für Alu. Im Druck wird die Platte dicker oder mit Rippen gebaut; das legt die Anforderung „Grundplatte“ fest. Im Skelett genügt die Unterkante.
- Die Trennstelle wird als Stoß mit Überlappung vorgesehen (Annahme `teilung_ueberlappung` = 30 mm). Die Gestaltung der Verbindung (Schrauben, Lochbild) gehört zur Anforderung „Grundplatte“.
- Querlenker, Radträger und Dämpferbrücken sind noch nicht konstruiert. Das Skelett nutzt für sie keine Hüllkörper, nur die Rad- und Wellenlagen.
- Fusion legt ein neues Projekt über die API an. Falls das nicht geht, speichert der Agent im „Default Project“ und meldet das.
- Das Skelett kommt nicht in die Stückliste, weil es kein Teil ist. Druckdateien entstehen nicht.
- (nach Review Durchlauf 1) Lage des Hauptzahnrads in der Rutschkupplung `hz_ebene` = 5 mm ab Hinterkante Hüllkörper, Radachslängen 45,4/38,3 mm und Länge Abtrieb vorne 8,5 mm sind vorläufig und werden bei Lieferung gemessen. Die Bewegungsräume der Antriebswellen nehmen vereinfacht an, dass das äußere Gelenk dem Rad senkrecht folgt.
- (nach Review Durchlauf 1) Spätere Baugruppen übernehmen Parameter und Bezugsgeometrie per Ableiten (Derive) aus „open-rc-car-skelett“ (Vorschlag, wird mit der Grundplatte bestätigt).

## Nicht Teil dieser Anforderung
- Konstruktion echter Teile (Grundplatte, Querlenker, Gehäuse, Halter)
- Aufhängungs- und Lenkgeometrie (Querlenkerlängen, Sturz, Nachlauf, Ackermann)
- Gestaltung der Trennfuge und des Lochrasters der Grundplatte
- Oberdeck und Karosserie
- Messen der Zukaufteile (nach Lieferung, durch den Nutzer)

## Offene Punkte
- keine, die die Umsetzung blockieren

## Nachweis
Umsetzung am 2026-10-27, überarbeitet nach Review Durchlauf 1. Fusion-Design „open-rc-car-skelett“ (Version 3) im Projekt „open-rc-car“. Messwerte und Tabellen in `docs/skelett.md`.

| ID | Status | Nachweis |
|---|---|---|
| MECH-SKE-001 | ✅ erfüllt | 145 Benutzerparameter, darunter `radstand` 283,5, `spurbreite` 250, `rad_durchmesser` 85, `rad_breite` 40, `bodenfreiheit` 25, `federweg` 35, `plattenstaerke` 4 mm. Test 290/260 mm: Zeitleiste (323 Elemente) ohne Fehler, Räder bei X ±145 / Y ±110, Getriebe, Dämpfer, Motor, Wellen und Bewegungsräume folgen (Screenshot `docs/images/skelett-parametertest-290-260.png`). Die Radachsen haben feste Länge; die Spuränderung wird als Prüfmaß sichtbar (`radachse_h_spiel` −5,01 mm, `radachse_v_spiel` −4,97 mm). Zurückgesetzt, wieder ohne Fehler. |
| MECH-SKE-002 | ✅ erfüllt | Prüfskript über alle 512 Modellparameter: Skizzenmaße, Extrusionen, Drehungen, Verschiebungen und Muster sind Ausdrücke aus Benutzerparametern. Feste Werte nur „0 mm“ für Lagen auf der Fahrzeugmitte und die Ursprungsebenen (Koordinatensystem, kein Hüllkörpermaß) sowie Fusion-interne Werte (Formschräge 0°, Zusatzversatz 0). Feste Zukaufteil-Längen (`radachse_*_l`, `abtrieb_l`) sind eigene Parameter, Restmaße sind als Prüfmaße ausgewiesen (`mittelantrieb_luft`, `radachse_*_spiel`, `motor_welle_reserve`). Alle 145 Parameter haben einen Kommentar mit Quelle bzw. „vorläufig“/„abgeleitet“/„Prüfmaß“. Alle Skizzen voll bestimmt. |
| MECH-SKE-003 | ✅ erfüllt | Koordinatensystem wie gefordert (Z oben). Benannte Ebenen Vorderachse (`achse_x`), Hinterachse (`-achse_x`), Fahrzeugmitte, Boden, Unterkante Grundplatte (`bodenfreiheit`), zusätzlich Oberkante Grundplatte, Antriebsachse, Teilung Grundplatte. |
| MECH-SKE-004 | ✅ erfüllt | Gemessen: Radmittenabstand längs 283,50 mm, Außenmaß über die Räder vorne und hinten 250,00 mm, Radunterkante Z = 0,00 mm, Radmitte Y ±105, Z 42,5 mm. |
| MECH-SKE-005 | ✅ erfüllt | 4 Bewegungsräume der Räder, Höhe gemessen 120,00 mm (= 85 + 35), Z −11,67…108,33 mm. Vorne Kreismuster um die Lenkachse (20 mm innerhalb der Radmitte), ±30° in 7 Stellungen, vereinigt; Ausdehnung X 84,94…198,56, Y 63,75…140,89 mm. Lücke zwischen den Stellungen ≤ 0,2 mm. Zusätzlich je Ecke ein Bewegungsraum für Antriebswelle und Radachse (`antrieb-wellenraum-*`): Welle hinten −8,3…22,2°, vorne −7,5…20,0° um das innere Gelenk, Radachse über den Federweg, vorne zusätzlich ±30° Lenkeinschlag (Radachse) bzw. ±3,77° (Welle). |
| MECH-SKE-006 | ✅ erfüllt | 42 Komponenten, jeder Hüllkörper eine eigene benannte Komponente: Akku, Motor, Motorritzel, Rutschkupplung mit Hauptzahnrad, Mittelwelle hinten 93, Hinterachsgetriebe, Antriebswellen hinten 67 (schräge Zylinder), Radachsen mit Mitnehmern vorne und hinten, 4 Dämpfer, Servo, Regler mit Lüfter, Empfänger, UBEC, XT60; dazu Bauräume und Bewegungsräume. Zuordnung jeder Stücklistenposition bzw. Begründung der Auslassung in `docs/skelett.md`. |
| MECH-SKE-007 | ✅ erfüllt | Tabelle „Hüllkörper“ in `docs/skelett.md` mit Maßen, Status und Quelle. Vorläufige Maße mit `huelle_zuschlag` 2 mm je Seite, bei Widerspruch (Regler, UBEC) je Achse das größere Maß. In Fusion: belegt blau, vorläufig rot, Bauraum gelb, Bewegungsraum grün. |
| MECH-SKE-008 | ✅ erfüllt | Layout wie 22X-4 (Screenshot von oben). Gemessen: Abtrieb hinten Rutschkupplung zu Eingang Hinterachsgetriebe 93,00 mm, Abtrieb vorne zu Eingang Vorderachsgetriebe 68,00 mm. Mittelantrieb 42,5 mm ohne Reserve (`mittelantrieb_luft` = 0,0 mm), als erster Messpunkt in `docs/skelett.md`. Zahnebene als Parameter `hz_ebene` (vorläufig), Ritzel daran ausgerichtet; Motorwelle reicht bis `hz_ebene` ≤ 6 mm (`motor_welle_reserve` 1,0 mm). |
| MECH-SKE-009 | ✅ erfüllt | Hüllkörper Vorderachsgetriebe (gespiegelt), Mittelwelle vorne 68, Antriebswellen vorne 74 (TLR232104), Abtrieb vorne; in der Interferenzprüfung enthalten, keine ungewollte Überschneidung. Nachweis für MECH-FZG-002. |
| MECH-SKE-010 | ✅ erfüllt | `analyzeInterference` über alle 42 Komponenten einschließlich der Bewegungsräume von Rädern, Antriebswellen und Radachsen (Federweg und Lenkeinschlag): 53 Überschneidungen, alle als gewollt dokumentiert (Welle in Getriebe/Radachse/Felge, Radachse in Radnabe, Rad bzw. Welle im eigenen Bewegungsraum, Abdeckung umschließt Zahnräder, Vorderwand der Abdeckung im Mittelschott, Welle durch Abdeckungswand, Zahneingriff Ritzel); 0 ungewollte. Engster Abstand Dämpfer vorne ↔ Wellenraum 2,48 mm. Tabelle in `docs/skelett.md`. |
| MECH-SKE-011 | ✅ erfüllt | Tiefster Punkt aller Hüllkörper außer Rädern und Bewegungsräumen: Unterkante Grundplatte Z = 25,00 mm; nächste Teile bei 29,00 mm. Die Bewegungsräume von Wellen und Radachsen (bis Z 20,83 mm, ausgefedert) zählen wie die Radräume zu den Rädern. |
| MECH-SKE-012 | ✅ erfüllt | Grundplatte aus den aufsitzenden Hüllkörpern abgeleitet, Dicke `plattenstaerke`. Gemessen: Länge 335,5 mm, Breite 154,0 mm (Parameter `platte_laenge`, `platte_breite`). |
| MECH-SKE-013 | ✅ erfüllt | `teilung_x` = 50 mm, `teilung_ueberlappung` = 30 mm. Gemessen: hinten 232,75 × 154,0 mm, vorne 132,75 × 154,0 mm, beide ≤ 250 × 250 mm. Stoß X 35…65 mm frei von Mittelschott, Motor, Zahnradabdeckung und Achsgetrieben; liegt unter Akku, Regler, UBEC und Servo (zulässig laut Nutzerentscheidung nach Review Durchlauf 1). Begründung in `docs/skelett.md`. |
| MECH-SKE-014 | ✅ erfüllt | Komponente `mittelantrieb-zahnradabdeckung`: Radius Kopfkreis + 3 mm Abstand + 2 mm Wand um Hauptzahnrad und Ritzel, axial 3 mm + 2 mm Wand vor und hinter der Rutschkupplung (X −13,75…18,25). In der Interferenzprüfung; Überschneidung nur mit den umschlossenen Teilen und dem Mittelschott (gewollt: Vorderwand im Mittelschott, Ausführung legt der Mittelantrieb fest). |
| MECH-SKE-015 | ✅ erfüllt | Bauraum `elektronik-akku-entnahmeweg` (138 × 46 × 100 mm über dem Akku) ohne Überschneidung. |
| MECH-SKE-016 | ✅ erfüllt | Massen über Materialdichte: Akku 300, Motor 223, Regler 90, Servo 64, UBEC 34, Empfänger 12,7 g, Räder vorläufig je 100 g (`rad_masse`, Nutzerentscheidung). Alle anderen Körper `masse-null` (< 0,01 g). Schwerpunkt über das ganze Design: 1123,7 g, X 1,67 / Y 0,32 / Z 45,52 mm, quer 0,32 mm ≤ 10 mm. Masse-Parameter wirken über den Massenabgleich (Skript in `docs/skelett.md`), Kommentar in Fusion entsprechend. |
| DOC-SKE-001 | ✅ erfüllt | `docs/skelett.md` mit Koordinatensystem, Parameterliste, Hüllkörper-Tabelle, Meilenstein-Ergebnis; Screenshots `docs/images/skelett-oben.png`, `skelett-seite.png`, `skelett-iso.png`. |
| DOC-SKE-002 | ✅ erfüllt | Projekt „open-rc-car“ über die API angelegt, Design „open-rc-car-skelett“ gespeichert. Exporte `cad/fusion/skelett.f3d` und `cad/step/skelett.step` über Git LFS (`git lfs ls-files`). |
| DOC-SKE-003 | ✅ erfüllt | `docs/plan.md`: Radstand 283,5 mm unter „Entscheidungen“ und in den Startwerten, Phase-0-Punkt „Skelettmodell“ abgehakt. |

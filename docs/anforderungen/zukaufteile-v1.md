# Anforderungen: Zukaufteile v1 und Spenderplattform

- **Kürzel:** ZUK
- **Domäne:** beides
- **Status:** umgesetzt
- **Stand:** 2026-10-28

> **Version 2 (Plattformwechsel):** Die erste Fassung (umgesetzt am 2026-10-26/27) hatte den TLR 22X-4 als Spender und nur Einzelteile. Am 2026-10-28 hat der Nutzer auf einen günstigen Einstieg mit dem **Tamiya TT-02B** umgestellt. Der Spender wird als **Bausatz** gekauft. Die alte Fassung steht in der Git-Historie.

## Zweck
Festlegen, welche Teile für den 2WD-Prototyp v1 gekauft werden, bei welchen Shops und von welcher Spenderplattform. Ziel ist ein **günstiger Einstieg**: Ein Tamiya-TT-02B-Bausatz liefert die Antriebs- und Fahrwerksteile, die man nicht sinnvoll selbst drucken kann. Chassis, Getriebegehäuse, Querlenker, Radträger und Halter werden weiterhin selbst konstruiert. Die Maße der Bausatzteile sind die Grundlage für Skelett, Grundplatte und Achsen.

## Schnittstellen
| Zu | Art | Beschreibung |
|---|---|---|
| Gesamtfahrzeug (`fahrzeug.md`) | mechanisch | Spur, Radstand, Raddurchmesser und Federweg kommen vom TT-02B (Nutzerentscheidung 2026-10-28), 12 mm Sechskant |
| Grundplatte, Hinterachse, Mittelantrieb | mechanisch | Diffs, Kegelräder, Kardanwelle, Antriebswellen, Dämpfer und Lager des TT-02B bestimmen Gehäuse, Lagersitze und Lochbilder |
| Mittelantrieb | mechanisch | Hauptzahnrad Tamiya Modul 0,6; **Rutschkupplung ist Eigenbau** (Nutzerentscheidung 2026-10-28) |
| Vorderachse und Lenkung | mechanisch | Standardservo 40 × 20 mm, 25T-Abtrieb; vordere Radachsen und Lager aus dem Bausatz |
| Elektronik | elektrisch/Signal | unverändert: 2S LiPo, XT60; Hobbywing-Regler mit PWM 50 Hz; ELRS-Empfänger HR7E, Kanal 1 Lenkung, Kanal 2 Gas; UBEC 6 V |
| Sender | Funk | ExpressLRS 2,4 GHz, wählt der Nutzer später, nicht in der Stückliste |

## Anforderungen
| ID | Priorität | Anforderung | Abnahmekriterium |
|---|---|---|---|
| MECH-ZUK-001 | MUSS | Die Teile der Spenderplattform kommen für v1 aus **einem TT-02B-Bausatz** (Nutzerentscheidung 2026-10-28). Darüber hinaus werden nur Teile gekauft, die sich nicht drucken oder selbst bauen lassen. Chassis/Grundplatte, Getriebe- und Differentialgehäuse, Querlenker, Radträger, Achsschenkel, Halter und die Rutschkupplung sind Eigenbau. Die nicht genutzten Bausatzteile (Wanne, Querlenker, Karosserie, Bürstenmotor) sind Reserve und werden nicht verbaut. | Stückliste: genau ein Bausatz als Zukauf; jede Zeile hat den Typ „Zukauf“, „Bausatz“, „Druck“ oder „Fräs“; die Eigenbauteile stehen als „Druck“. |
| MECH-ZUK-002 | MUSS | Spenderplattform: **Tamiya TT-02B** (4WD, Kegelrad-Diffs vorne und hinten, Kardanwelle). Gewählt wird der günstigste in DE/EU lieferbare TT-02B-Bausatz; die Wahl wird begründet. | Vergleich der TT-02B-Bausätze (mindestens Plasma Edge II 58630 und Neo Scorcher 58568) mit Preis, Lieferbarkeit und Lieferumfang (Diffs, Dämpfer, Räder, Lager) in `docs/zukaufteile-v1.md` |
| MECH-ZUK-003 | MUSS | Die Fahrzeugmaße kommen vom TT-02B: Spur, Radstand, Raddurchmesser und Federweg. Die Startwerte in `docs/plan.md` werden auf diese Werte gesetzt (Nutzerentscheidung 2026-10-28). 12 mm Sechskant bleibt. | Werte mit Quelle (Anleitung oder Herstellerseite Tamiya) in `docs/zukaufteile-v1.md` und als Startwerte in `docs/plan.md`. Werte ohne Quelle: „am Teil messen“. |
| MECH-ZUK-004 | MUSS | Antriebsstrang hinten für v1 vollständig: Hinterachsdiff mit Tellerrad und Kegelritzel, Kardanwelle, 2 Antriebswellen, 2 Radachsen mit 12-mm-Mitnehmern, Hauptzahnrad Modul 0,6, Motorritzel Modul 0,6 für 3,175-mm-Welle, alle Lager. Die Rutschkupplung ist Eigenbau (Baugruppe Mittelantrieb); die dafür nötigen Normteile (z. B. Druckfeder, Reibbelag, Lager) werden in deren Anforderungsanalyse festgelegt. | Stückliste: jedes Teil vom Motor bis zum Rad ist entweder aus dem Bausatz, Zukauf oder als Eigenbau markiert. |
| MECH-ZUK-005 | MUSS | Vorderachse v1 (nicht angetrieben): Radachsen mit 12-mm-Mitnehmern und Lagern aus dem Bausatz. Die Teile für 4WD (Vorderdiff, vordere Wellen) sind im Bausatz enthalten und werden für Phase 2 aufbewahrt. | Stückliste bzw. Lieferumfang laut Bausatzanleitung |
| MECH-ZUK-006 | MUSS | 4 Öldämpfer passend zum TT-02B. Sind im gewählten Bausatz keine Öldämpfer enthalten, werden Tamiya-Öldämpfer für den TT-02B dazugekauft. Der Federweg ergibt sich aus diesen Dämpfern (Abschlag gegenüber ≥ 30 mm akzeptiert, Nutzerentscheidung 2026-10-28). | Dämpfertyp, Hub und Einbaulänge mit Quelle oder „am Teil messen“; Federweg am Rad in `docs/zukaufteile-v1.md` berechnet bzw. als Messung am Prototyp vorgesehen |
| MECH-ZUK-007 | MUSS | Räder: die 4 Räder aus dem Bausatz, 12 mm Sechskant (Nutzerentscheidung 2026-10-28). Die Carson-Räder entfallen. | Durchmesser und Breite mit Quelle oder „am Teil messen“ in der Stückliste |
| MECH-ZUK-008 | MUSS | Lager nur in metrischen Standardgrößen und gedichtet. Enthält der Bausatz Gleitlager (Buchsen), wird ein vollständiger gedichteter Kugellagersatz für den TT-02/TT-02B gekauft. | Stückliste: Größe je Lagerposition und Gesamtmenge je Größe |
| MECH-ZUK-009 | MUSS | Verbindungselemente: Schrauben metrisch, bevorzugt M3, Stahl 10.9/12.9 oder Edelstahl, als Sortiment; M3-Stoppmuttern, Scheiben, M3-Gewindeeinsätze. Kugelköpfe, Kugelpfannen und Spurstangen kommen aus dem Bausatz; fehlende Teile werden als Tamiya-Ersatzteil gekauft. | Stückliste mit Größen und Mengen; genaue Schraubenlängen nach der Konstruktion (Annahme vermerkt) |
| MECH-ZUK-010 | MUSS | Nicht mehr benötigte Teile der ersten Fassung (alle TLR-Teile, Carson-Räder, nicht mehr passende Lager und Normteile) werden aus der Stückliste entfernt. | Stückliste enthält keine TLR-Teile mehr |
| ELEK-ZUK-001 | MUSS | Motor/Regler bleiben: Hobbywing QuicRun 3652SL G2 3250 kV + WP10BL60 G2 (brushless sensorless, 2S, XT60, Vorwärts/Bremse/Rückwärts, LiPo-Abschaltung). **Ziel ca. 50 km/h bleibt** (Nutzerentscheidung 2026-10-28). | Rechnung (KV × Spannung ÷ Gesamtübersetzung × Radumfang) mit der TT-02-Diffübersetzung und erhältlichem Modul-0,6-Ritzel und Hauptzahnrad ergibt 45–55 km/h. Ritzelbohrung 3,175 mm. |
| ELEK-ZUK-002 | MUSS | ELRS-Empfänger HelloRadio HR7E bleibt, Failsafe Motor aus (ELEK-FZG-002) | unverändert aus Fassung 1 übernommen |
| ELEK-ZUK-003 | MUSS | Lenkservo Savöx SC-1258TG+ und UBEC Hobbywing 10A V2 bleiben. Das Servo passt in den eigenen Servohalter (Eigenbau), nicht in die Tamiya-Wanne. | unverändert aus Fassung 1 übernommen |
| ELEK-ZUK-004 | MUSS | LiPo Voltz 2S 5000 mAh Hardcase XT60 bleibt (LiPo-Schutz) | unverändert aus Fassung 1 übernommen |
| ELEK-ZUK-005 | SOLL | Kleinteile Elektronik und LiPo-Schutztasche bleiben | Stückliste |
| DOC-ZUK-001 | MUSS | Shops: Der Bausatz wird beim günstigsten DE/EU-Shop gekauft, der ihn lieferbar hat. Insgesamt höchstens 3 Shops; bevorzugt Shops, die schon in der Liste stehen (Lindinger, RC Team). | Preisvergleich für den Bausatz mit Link; höchstens 3 Shops in der Stückliste |
| DOC-ZUK-002 | MUSS | Was in keinem Shop zu finden ist, wird nicht geraten, sondern als „manuell suchen“ aufgeschrieben. | Abschnitt „Manuell suchen“ in `docs/zukaufteile-v1.md` |
| DOC-ZUK-003 | MUSS | `bom/stueckliste.csv` ist ausgefüllt. Jede Zeile hat Bezeichnung, Menge, Typ, Hersteller, Teilenummer, Shop, Link, Preis und die für die Konstruktion wichtigen Maße mit Quelle oder „am Teil messen“. Teile aus dem Bausatz stehen mit Typ „Bausatz“ und Tamiya-Teilenummer (soweit in der Anleitung genannt) und ohne eigenen Preis. | CSV gültig (gleiche Spaltenzahl); jedes Zukaufteil mit Shop, Link, Preis und Maßen bzw. „am Teil messen“ |
| DOC-ZUK-004 | MUSS | Budget: Summe aller Zukaufteile inklusive Versand höchstens 1050 € (Sender, Ladegerät, Werkzeug nicht enthalten) | Summe in `docs/zukaufteile-v1.md` |
| DOC-ZUK-005 | MUSS | Plan aktualisieren: Spenderplattform, Zahnradmodul, Mittelantrieb (Rutschkupplung Eigenbau), Räder, Bezugsquellen und Startwerte in `docs/plan.md`. | Diff von `docs/plan.md` |
| DOC-ZUK-006 | SOLL | Liste der Verschleißteile als Tamiya-Ersatzteile mit Teilenummer (Kegelräder, Hauptzahnrad, Ritzel, Kardanwelle, Antriebswellen). Sie werden nicht bestellt. | Abschnitt in `docs/zukaufteile-v1.md` |
| DOC-ZUK-007 | KANN | Teile für 4WD (Phase 2): welche Bausatzteile dafür aufbewahrt werden | Abschnitt in `docs/zukaufteile-v1.md` |

## Entscheidungen (vom Nutzer)
- 2026-10-26 bis 2026-10-27: Entscheidungen der ersten Fassung zu Budget, Geschwindigkeit, Shops in DE/EU, Sender, Ladegerät, Akku, Servoversorgung über UBEC: gelten weiter, soweit unten nichts anderes steht.
- 2026-10-28: Spenderplattform **Tamiya TT-02B** statt TLR 22X-4 (Grund: günstiger Einstieg; Abschläge bei Spur, Radstand, Federweg und Zahnradmodul werden in Kauf genommen).
- 2026-10-28: Für v1 wird **ein TT-02B-Bausatz** als Teilespender gekauft. Die Regel „nur Einzelteile, kein Bausatz“ gilt für v1 nicht mehr (Grund: am günstigsten). Für spätere Mehrfachbauten soll es eine Stückliste der Tamiya-Einzelteile mit Teilenummern und Bezugsquellen geben; die wird später erstellt und steht als offener Punkt im Plan.
- 2026-10-28: Variante **TT-02B** (Buggy), nicht TT-02 (Tourenwagen).
- 2026-10-28: Spur, Radstand, Raddurchmesser und Federweg werden **vom TT-02B übernommen**. Grundplatte/Oberdeck (PR #6) und Skelett werden danach angepasst.
- 2026-10-28: Brushless-Antrieb bleibt, **Ziel ca. 50 km/h bleibt**.
- 2026-10-28: Weil es für den TT-02 keine Rutschkupplung gibt, wird **eine eigene Rutschkupplung konstruiert** (Baugruppe Mittelantrieb).
- 2026-10-28: **Räder aus dem Bausatz**, die Carson-Räder entfallen.
- 2026-10-28: PR #6 (Grundplatte und Oberdeck) wird pausiert und nach Freigabe dieser Änderung angepasst.
- 2026-10-28: Anforderungsdokument (Fassung 2) vom Nutzer freigegeben.

## Annahmen (abgeleitet, noch nicht bestätigt)
- Bausatz: voraussichtlich **Plasma Edge II (58630)**, nach Vorrecherche der günstigste TT-02B-Bausatz (ca. 120–130 € auf eBay.de, ohne Regler). Die endgültige Wahl trifft die Umsetzung nach Preis und Lieferumfang (MECH-ZUK-002).
- TT-02B-Werte laut Tamiya: Radstand 266 mm, Spur 217 mm vorne / 208 mm hinten; Reifen Ø ca. 82 mm (Neo Scorcher). Die Umsetzung belegt sie mit Quelle.
- Zahnräder: Tamiya Modul 0,6 (Tamiya nennt Ritzel „06 Module“). Die Diff-Übersetzung des TT-02 liegt rechnerisch bei 2,6 : 1 (Werksübersetzung 8,27 : 1). Für 50 km/h mit 3250 kV, 7,4 V und Ø 82 mm ist eine Gesamtübersetzung von etwa 7,4 : 1 nötig; Tamiya gibt für den TT-02 einen Bereich bis 7,28 : 1 an. Das ist knapp und wird in der Umsetzung mit konkreten Zahnrädern nachgerechnet.
- Der Plastik-Antriebsstrang des TT-02 ist für Bürstenmotoren ausgelegt. Mit Brushless und 50 km/h schützt die eigene Rutschkupplung Diffs und Kardanwelle. Brechen trotzdem Teile, werden Metall-Tuningteile (z. B. Alu-Kardanwelle 54501) nachgekauft.
- Die Getriebegehäuse sind beim TT-02 Teil der Wanne. Da wir die Wanne nicht nutzen, werden Getriebegehäuse und Lagerung der Kegelräder selbst konstruiert (wie bisher geplant).
- Die Elektronik (Regler, Motor, Empfänger, Servo, UBEC, Akku, Kleinteile) bleibt unverändert aus der ersten Fassung.
- Budget: Die Obergrenze 1050 € bleibt; die Summe wird voraussichtlich deutlich darunter liegen.

## Nicht Teil dieser Anforderung
- Bestellung (macht der Nutzer)
- Überarbeitung von Skelettmodell und Grundplatte/Oberdeck (PR #6) auf die TT-02B-Maße: eigener Schritt danach
- Konstruktion der Rutschkupplung: Teil der Baugruppe Mittelantrieb
- Stückliste der Tamiya-Einzelteile für Mehrfachbauten: später (offener Punkt im Plan)
- Sender, Ladegerät, Werkzeug, Karosserie, Filament

## Offene Punkte
- keine, die die Umsetzung blockieren

## Nachweis
Umsetzung am 2026-10-28: `docs/zukaufteile-v1.md` (Fassung 2: Bausatzvergleich, Werte, Rechnungen, Lager, Budget) und `bom/stueckliste.csv` (53 Zeilen, 18 Spalten). Reine Recherche, kein Fusion.

| ID | Status | Nachweis |
|---|---|---|
| MECH-ZUK-001 | ✅ erfüllt | Stückliste per Python `csv` geprüft: Typen nur „Zukauf“, „Bausatz“, „Druck“. Genau ein Bausatz als Zukauf (Pos. 1, Neo Scorcher 58568); die genutzten Bausatzteile stehen als „Bausatz“ (11 Zeilen). Getriebegehäuse, Radträger, Querlenker, Achsschenkel, Halter, Grundplatte, Oberdeck und die neue Rutschkupplung stehen als „Druck“. Nicht genutzte Bausatzteile (Wanne, Querlenker, Karosserie, Motor, Regler) als Reserve in der Bemerkung von Pos. 1. |
| MECH-ZUK-002 | ✅ erfüllt | Vergleich von 6 Angeboten (Neo Scorcher 58568 bei TAMICO und RC Team, Plasma Edge II 58630 bei Härtle und RC Team, Plasma Edge II Gun Metal bei Lindinger, TT-02B Chassis Kit bei TAMICO) mit Preis, Lieferbarkeit und Lieferumfang in `docs/zukaufteile-v1.md`, „Bausatzvergleich“. Wahl Neo Scorcher bei TAMICO (110,91 €, auf Lager), begründet; das billigere Chassis Kit hat keine Räder (MECH-ZUK-007). |
| MECH-ZUK-003 | ✅ erfüllt | Radstand 266 mm, Spur 217/208 mm, Räder 32/82 und 41/82 mm laut Tamiya-Specifications 58568 und 58630; Federweg und 12-mm-Sechskant ohne veröffentlichte Quelle → „am Teil messen/prüfen“. Startwerte in `docs/plan.md` gesetzt. |
| MECH-ZUK-004 | ✅ erfüllt | Antriebsstrang vom Motor bis zum Rad: Motorritzel 25Z (manuell suchen; 17Z im Bausatz) → Hauptzahnrad 70Z (Bausatz) in eigener Rutschkupplung (Druck) → Kardanwelle (Bausatz) → Hinterachsdiff mit Tellerrad und Kegelritzel (Bausatz) → Antriebswellen (Bausatz) → Radachsen mit 12-mm-Mitnehmern (Bausatz) → Räder; Lager 5x11x4 und 8x12x3,5 (Carson-Satz), Getriebegehäuse Eigenbau. Normteile der Rutschkupplung: Anforderungsanalyse Mittelantrieb. 70Z und 17Z sind aus Tamiyas Übersetzungen gerechnet (10,71 / 8,27 / 7,28 : 1 passen alle zu 70Z und 2,6 : 1) → beim Auspacken prüfen. |
| MECH-ZUK-005 | ✅ erfüllt | Vordere Radachsen mit 12-mm-Mitnehmern aus dem Bausatz (dieselben wie beim angetriebenen TT-02B-Vorderrad); Vorderdiff und vordere Wellen als „Bausatz, Phase 2 aufbewahren“ in der Stückliste. |
| MECH-ZUK-006 | 🔧 am Prototyp prüfen | 4 CVA-Öldämpfer im Bausatz laut Tamiya [P2] und TAMICO; kein Zukauf nötig. Hub und Einbaulänge nicht veröffentlicht → „am Teil messen“; Federweg s = Hub × i wird bei der Konstruktion berechnet und am Prototyp gemessen. |
| MECH-ZUK-007 | ✅ erfüllt | Räder aus dem Bausatz: vorne 32 × 82 mm, hinten 41 × 82 mm laut Tamiya [P2]; Einpresstiefe und Nabentiefe „am Teil messen“. Carson-Räder aus der Stückliste entfernt. |
| MECH-ZUK-008 | 🔧 beim Auspacken prüfen | Bausatz hat Kunststoffbuchsen [P3] → Carson-Satz 500904054 (12 × 5x11, 4 × 8x12, metrisch) bei Lindinger. **Dichtung ist auf der Shopseite nicht angegeben** und damit nicht belegt. Vorgehen in Stückliste und Doku: beim Auspacken prüfen, offene Lager durch MR115-2RS/MR128-2RS ersetzen (gummigedichteter Satz z. B. 9,50 € bei Racer's Paradise). Lenkungslager 5x8x2,5 XRAY gummigedichtet. Tabelle mit Größe, Position und Menge in `docs/zukaufteile-v1.md`, „Lager“. |
| MECH-ZUK-009 | ✅ erfüllt | M3-Sortiment Edelstahl unverändert (Lindinger); Kugelköpfe, Kugelpfannen, Lenkspurstange und Sturzstangen aus dem Bausatz; Ersatz über Tamiya 54539 genannt. Annahme Schraubenlängen vermerkt. |
| MECH-ZUK-010 | ✅ erfüllt | Prüfskript: keine Zeile enthält „TLR“; Carson-Räder, TLR-Lager, Axial-Lager, TLR-Kugelköpfe/-pfannen, Spurstangen 3,5 mm und M2,5-Muttern entfernt. |
| ELEK-ZUK-001 | ✅ erfüllt | Motor/Regler unverändert. Rechnung: 3250 kV × 7,4 V ÷ (70/25 × 2,6 = 7,28) × π × 82 mm = **51,1 km/h** (24Z: 49,0 km/h), im Bereich 45–55 km/h. Ritzel-Set 50477 hat Bohrung 3,17 mm (passt auf 3,175-mm-Welle); erhältlich, aber nur außerhalb der drei Shops → „manuell suchen“. Leerlaufwert, real darunter (🔧 Messung). |
| ELEK-ZUK-002 | ✅ erfüllt | unverändert aus Fassung 1 (HR7E, EU_CE_2400, Failsafe 1500 µs auf Kanal 1 und 2), Abschnitt „Elektronik“ übernommen |
| ELEK-ZUK-003 | ✅ erfüllt | unverändert aus Fassung 1 (Savöx SC-1258TG+, UBEC 10A V2 auf 6,0 V) |
| ELEK-ZUK-004 | ✅ erfüllt | unverändert (Voltz 2S 5000 mAh Hardcase XT60) |
| ELEK-ZUK-005 | ✅ erfüllt | unverändert (XT60, Servo-Verlängerung, Kabelbinder, Lipoguard) |
| DOC-ZUK-001 | ✅ erfüllt | Bausatz-Preisvergleich mit Links (TAMICO, RC Team, Härtle, Lindinger); 3 Shops in der Stückliste: TAMICO, Lindinger, RC Team (Prüfskript). |
| DOC-ZUK-002 | ✅ erfüllt | Abschnitt „Manuell suchen“: Ritzel-Set 50477 mit Richtpreis und Quelle; Zeile in der Stückliste mit Vermerk „MANUELL SUCHEN“. |
| DOC-ZUK-003 | ✅ erfüllt | CSV mit Python `csv` geprüft: 54 Zeilen inkl. Kopf, überall 18 Spalten; Summe_EUR = Menge × Preis_EUR in jeder Zeile mit Preis. Zukaufteile mit Shop, Link, Preis und Maßen bzw. „am Teil messen“ (Ausnahme: Ritzel-Set, manuell suchen). Bausatzteile mit Typ „Bausatz“; Tamiya-Teilenummern stehen erst in der Anleitung → „Nr. laut Anleitung 58568“, die Liste der Einzelteilnummern ist ein offener Punkt im Plan. |
| DOC-ZUK-004 | ✅ erfüllt | Abschnitt „Budget“: alle Posten mit Preis 500,37 € inkl. Versand (TAMICO-Versand als Annahme 10 €, nicht belegt), mit Ritzel-Richtpreis 512,33 € ≤ 1050 €. |
| DOC-ZUK-005 | ✅ erfüllt | `docs/plan.md`: Entscheidungen Spenderplattform, Teilebeschaffung, Fahrzeugmaße, Zahnradmodul, Mittelantrieb, Räder, Bausatz und Bezugsquellen (2026-10-28); Startwerte; offene Punkte (Einzelteil-Stückliste, PR #6/Skelett), Phase 0 aktualisiert. |
| DOC-ZUK-006 | ✅ erfüllt | Abschnitt „Verschleißteile“ mit Tamiya-Nummern 51531, 54501, 50477. |
| DOC-ZUK-007 | ✅ erfüllt | Abschnitt „Vorderachse und 4WD“: Vorderdiff, vordere Wellen und Kardanteil aus dem Bausatz aufbewahren. |

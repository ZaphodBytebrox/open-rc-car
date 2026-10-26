# Zukaufteile v1: Spenderplattform, Shops und Stückliste

- **Anforderungen:** `docs/anforderungen/zukaufteile-v1.md` (Kürzel ZUK)
- **Stückliste:** `bom/stueckliste.csv`
- **Stand der Recherche:** 2026-10-26, überarbeitet 2026-10-27. Preise und Verfügbarkeiten gelten für den 2026-10-26 und ändern sich.

## Ergebnis in Kürze

| Thema | Ergebnis |
|---|---|
| Spenderplattform | **Team Losi Racing (TLR) 22X-4** (Elite-Ersatzteile, Bausatz TLR03026). 4WD, Kegelrad-Differentiale vorne und hinten, Mittelantrieb über CVA-Wellen. |
| Zahnrad-Pitch | **48 Pitch** (Motorritzel und Hauptzahnrad) |
| Getriebeübersetzung im Diff | 2,5 : 1 |
| Mittelantrieb v1 | **Rutschkupplung** (TLR232137) statt Mitteldiff, siehe Begründung unten |
| Motor/Regler | Hobbywing QuicRun 3652SL G2 3250 kV + QuicRun WP10BL60 G2 (sensorless) |
| Ritzel | 26 Zähne 48P → rechnerisch **51,4 km/h** bei 7,4 V (Leerlaufwert, siehe [Höchstgeschwindigkeit](#höchstgeschwindigkeit-elek-zuk-001)) |
| ELRS-Empfänger | HelloRadio HR7E, 8 PWM-Ausgänge, ExpressLRS 3.3.0 |
| Lenkservo | Savöx SC-1258TG+ (12 kg·cm, 0,08 s/60° bei 6 V, 25Z, Titangetriebe), versorgt über **externen BEC Hobbywing UBEC 10A V2** (6,0 V), weil der Blockierstrom (5 A) über dem Regler-BEC (3 A) liegt (Nutzerentscheidung 2026-10-27) |
| Akku | Voltz 2S 5000 mAh 50C, Hardcase, XT60 (138 × 46 × 25 mm) |
| Dämpfer | 4 × TLR G3 42 mm (2 Sätze TLR233064), Hub 30,5 mm |
| Räder | **Carson All Terrain 4WD** (4 Stück, Reifen fertig verklebt), 12 mm Sechskant, Ø 85 × 40 mm, Allround-Profil für Gelände und Straße. Einpresstiefe, Nabentiefe und Felgengröße am Teil messen (Nutzerentscheidung 2026-10-27) |
| Shops (3) | **Horizon Hobby EU** (alle TLR-Teile, Lager 5x13x4), **Modellbau Lindinger** (Elektronik, Räder, Normteile), **RC Team** (Akku, Lager, XT60, UBEC) |
| Budget | **812,56 €** inkl. Versand für alle Posten mit Preis. Mit Dämpfern (Vergleichspreis) **964,36–966,36 €**, mit den Richtpreisen der Teile „manuell suchen“ **1042,34–1044,34 €** und damit knapp im Budget von 600–1050 €. Der Dämpferpreis ist offen, siehe [Budget](#budget). |
| Abweichung von den Startwerten | keine (siehe [Werte mit Quelle](#werte-der-gewählten-plattform-mit-quelle-mech-zuk-003)) |

## Plattformvergleich (MECH-ZUK-002)

Kandidaten nach der Vorrecherche im Anforderungsdokument: Team Associated RC10B74.2, XRAY XB4 (2026) und TLR 22X-4. Arrma 4x4 BLX 223S (14-mm-Sechskant) und Tamiya TT-02B (Spur zu schmal) wurden schon dort ausgeschlossen und nicht weiter geprüft.

| Kriterium | Associated RC10B74.2 | XRAY XB4 2026 | **TLR 22X-4 (Elite / 2.0)** |
|---|---|---|---|
| Layout | 4WD, Kegelrad-Getriebediffs vorne und hinten, Mittelwellen (CVA), Rutschkupplung oder Mitteldiff [B1][B2] | 4WD, Getriebediffs vorne und hinten, Mittelwellen, Rutschkupplung (C) oder Mitteldiff (D) [X1] | 4WD, Kegelrad-Getriebediffs vorne und hinten, CVA-Mittelwellen, Mitteldiff oder Rutschkupplung [T1][T2] |
| Radmitnehmer | 12 mm Sechskant [B2] | 12 mm Sechskant [X1][X2] | 12 mm Sechskant [T1] |
| Spur | „varies“, keine Zahl [B1] | 245–250 mm (Händler-/Pressetext, offizielle 2026-Angabe nicht gefunden) [X3] | **250 mm** vorne und hinten [T1] |
| Radstand | 280,5–285,5 mm [B1] | 279–281 mm (Händler-/Pressetext) [X3] | **283,5 mm** [T1] (Horizon: 284 mm [T3]) |
| Pitch | 48P (Ritzel 48P, Hauptzahnrad 78T-48P) [B2] | 48P (Hauptzahnräder „/48“) [X2] | 48P [T3] |
| Übersetzung Diff | 2,50 : 1 [B1] | nicht gefunden | 2,5 : 1 [T1] |
| Dämpferhub | vorne 22 mm, hinten 27,5 mm [B2] | nicht gefunden | vorne 23 mm, **hinten 30,5 mm** [T1] |
| Einzelteile in den Kandidaten-Shops | lückenhaft: rc-race-shop.de hat einige B74-Teile (Diff-Gehäuse 92135, Abtriebe 92136, Kegelritzel 92142), RC Team nur einzelne (z. B. Hauptzahnrad 92295); Diff-Zahnradsatz 92306, Tellerrad/Ritzel 92318, CVA-Sätze 92299/92190 und Rutschkupplungsteile bei rc-race-shop.de und RC Team nicht gefunden; 13-mm-Dämpfersätze (91994, 91995) führt RC Team; Lindinger: keine Associated-Ersatzteile | RC Team führt viele XB4-Teile; Lindinger nur Bausätze; Horizon EU (Suche „XRAY XB4“ nur Pro-Line-Reifen) und rc-race-shop.de (Suche „XB4“): keine | **Horizon Hobby EU** (offizieller TLR-Vertrieb) führt fast alle benötigten Teile, auch **komplette Baugruppen** (Diff, Rutschkupplung); Lücken siehe [Manuell suchen](#manuell-suchen) |
| Preis der benötigten Teile | nicht ermittelbar, weil Teile fehlen | nur Stichprobe: komplette Dämpfer vorne (2) 87,20 €, Antriebswelle hinten 68 mm 22,00 € (RC Team) | 373,76 € bei Horizon EU ohne Dämpfer (TLR-Teile, Kugelköpfe, Lager 5x13x4; siehe Stückliste) |

**Wahl: TLR 22X-4.** Begründung:
1. **Verfügbarkeit in der EU:** Horizon Hobby EU ist der offizielle Vertrieb von TLR und führt Differential, Ritzel, CVA-Achsen, Wellen, Rutschkupplung, Mitnehmer und Federn als Einzelteile, das meiste lagernd. Bei der B74.2 fehlen in allen geprüften Shops zentrale Antriebsteile.
2. **Komplette Baugruppen:** Differential (TLR332086) und Rutschkupplung (TLR232137) gibt es fertig. Das spart Einzelteile und Fehler beim Zusammenstellen.
3. **Dokumentierte Maße:** Die Anleitung nennt Radstand, Spur, Übersetzung und Dämpferhub. Der hintere Dämpferhub von 30,5 mm erfüllt MECH-ZUK-006 schon ohne Hebelübersetzung. Bei der XB4 fehlen offizielle Werte für das Modell 2026.
4. **Werte passen zu den Startwerten** im Plan, ohne Abweichung.

Nachteile, die bleiben: Die kompletten Dämpfersätze sind bei Horizon EU derzeit nicht lieferbar, einige Teile sind nur vorbestellbar, und die TLR-Spurstangen (3,5 mm) gibt es in keinem der Shops. Einige Kleinteile (Spurstangensatz TLR334077, Ritzel-Befestigungssatz TLR232110, Distanzscheiben TLR236006, Kugelpfannen TLR234107, Mutter TLR6312) führt Horizon EU nur noch als Auslaufartikel. Ersatzteile, die es nur für die 22X-4 2.0 gibt (Nummern TLR-12xx), wurden bei Horizon EU nicht gefunden (Stichprobe TLR-1292, TLR-1298). Deshalb basiert die Liste auf den Elite-Teilen (TLR23xxxx/TLR33xxxx), die laut Anleitung der 2.0 zum großen Teil auch dort verbaut sind [T2].

**Warum Rutschkupplung statt Mitteldiff in v1:** Ein offenes Mitteldiff überträgt kein Moment nach hinten, wenn der vordere Abtrieb frei dreht. Für 2WD braucht v1 deshalb die starre Rutschkupplung TLR232137. Sie hat Abtriebe nach vorne und hinten und bleibt für 4WD nutzbar.

## Werte der gewählten Plattform mit Quelle (MECH-ZUK-003)

| Startwert im Plan | Anforderung | TLR 22X-4 | Quelle | Bewertung |
|---|---|---|---|---|
| `radmitnehmer` 12 mm Sechskant | 12 mm | 12 mm Sechskant (Mitnehmer TLR232111/TLR232113) | [T1] Teileliste | passt |
| `spurbreite` 250 mm | 240–260 mm über die Räder | 250,0 mm vorne und hinten | [T1] „Completed Kit Specifications“ | passt |
| `radstand` 280 mm | 270–290 mm erreichbar | 283,5 mm | [T1] | passt |
| `rad_durchmesser` ca. 85 mm | – | Räder Carson All Terrain 4WD: 85 mm vorne und hinten | [R1] | passt |
| `federweg` 35 mm | ≥ 30 mm (MECH-FZG-005) | Dämpferhub hinten 30,5 mm, vorne im Bausatz 23 mm; v1 nutzt vier 42-mm-Dämpfer mit 30,5 mm | [T1] Setup-Sheet | passt, siehe [Federweg](#federweg-mech-zuk-006) |

**Keine Abweichung von den Startwerten.** Spur und Radstand des Spenders gelten für dessen Querlenker. Bei uns entstehen Spur und Radstand durch die eigene Konstruktion. Damit die TLR-Antriebswellen (67 mm hinten) passen, muss der Abstand vom Diff-Abtrieb zum Radträger auf diese Wellen abgestimmt werden (siehe [Vorgaben für die Konstruktion](#vorgaben-für-die-konstruktion)).

## Teileliste und Abdeckung (DOC-ZUK-001)

Zuerst wurde die Teileliste aufgestellt (vollständig in `bom/stueckliste.csv`). Danach wurde je Teil geprüft, welcher Shop es führt. Geprüft wurde über die Suche der Shops und die Produktseite.

**Kandidaten-Shops:**
- **Horizon Hobby EU** (horizonhobby.com/eu/de, Versand aus der EU): offizieller Vertrieb von TLR und Pro-Line-Rädern
- **Modellbau Lindinger** (lindinger.at, AT)
- **RC Team** (rcteam.com, FR)
- **rc-race-shop.de** (DE)
- **Conrad:** Suche und Produktseiten liefern „403 Forbidden“, automatisch nicht abrufbar → **Verfügbarkeit ungeprüft**
- **RC Linde:** kein Shop unter diesem Namen gefunden (rc-linde.de und rclinde.de nicht erreichbar, Websuche ohne Treffer)

Legende: ✅ geführt (Link zur Produktseite), ⏳ nur vorbestellbar bzw. Bestellware, ⛔ derzeit nicht lieferbar, ❌ in der Shop-Suche nicht gefunden, – nicht geprüft. Die Spalte „Conrad“ ist überall ungeprüft und deshalb weggelassen.

| Teil | Horizon EU | Lindinger | RC Team | rc-race-shop.de |
|---|---|---|---|---|
| Hinterachsdiff komplett TLR332086 | ✅ [49,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-front-rear-differential-complete-metal-22x-4/TLR332086.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Tellerrad TLR232127 | ✅ [9,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-ring-gear-22x-4/TLR232127.html) | – | – | – |
| Kegelritzel TLR232126 | ✅ [9,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-pinion-gear-steel-22x-4/TLR232126.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Ritzelwelle CVA TLR232109 | ⏳ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-pinion-cva-axle-2-22x-4/TLR232109.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| CVA-Wellen hinten 67 mm TLR232102 | ✅ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-cva-driveshaft-bones-67mm-2-22x/TLR232102.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Radachsen hinten TLR232108 | ✅ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-rear-cva-axle-2-22x-4/TLR232108.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Radachsen vorne TLR232107 | ⏳ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-front-cva-axle-2-22x-4/TLR232107.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Mittelwellen 68/93 mm TLR232105 | ✅ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-cva-driveshaft-bones-68mm-93mm-22x/TLR232105.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Rutschkupplung komplett TLR232137 | ✅ [69,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-slipper-assembly-complete-22x-4/TLR232137.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Hauptzahnrad 78Z TLR232116 | ✅ [7,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-78t-spur-gear-slipper-22x-4/TLR232116.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| Motorritzel 26Z 48P TLR332026 | ✅ [8,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-pinion-gear-26t-48p-1-8in-aluminum/TLR332026.html) | – | – | – |
| Radmitnehmer 12 × 5 / 12 × 4 TLR232113/111 | ✅ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-wheel-hex-12mm-x-5.0mm-2/TLR232113.html) / ✅ [19,99 €](https://www.horizonhobby.com/eu/de/product/team-losi-racing-wheel-hex-12mm-x-4.0mm-2/TLR232111.html) | ❌ ¹ | ❌ ² | ❌ ³ |
| CVA-Stifte, Hülsen, Mitnehmerstifte, Radmuttern | ✅ [TLR332074](https://www.horizonhobby.com/eu/de/product/team-losi-racing-vha-cva-rebuild-set-2-22-5.0/TLR332074.html), ⏳ [TLR232132](https://www.horizonhobby.com/eu/de/product/team-losi-racing-cva-sleeve-composite-8-22x/TLR232132.html), ✅ [TLR232002](https://www.horizonhobby.com/eu/de/product/team-losi-racing-solid-drive-pin-set-8-22-t-sct-22-4/TLR232002.html), ✅ [TLR336000](https://www.horizonhobby.com/eu/de/product/team-losi-racing-tlr-4mm-aluminium-stoppmutter-mit-flansch-schwarz-6st./TLR336000.html) | – | – | – |
| Dämpfersatz 42 mm TLR233064 | ⛔ [Produktseite](https://www.horizonhobby.com/eu/de/product/team-losi-racing-42mm-shock-set-g3-3mm-ticn-2/TLR233064.html) | ❌ ⁴ | ❌ ² | ❌ ⁴ |
| Räder Allround 1:10-Buggy 12 mm, vorne und hinten | ❌ nur Pro-Line-Rennreifen (Hole Shot, Blockade, Bald Eagle u. a., Kategorie „Hard Pack“, Mischung M3/S3/MC) | ⏳ [Carson All Terrain 4WD (4), 25,49 €](https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Zubehoer/Reifen-Felgen/Reifen-Felgen-Sets/CARSON-1-10-Raeder-4-All-Terrain-4WD/9806731) | hinten ✅ [Hobbytech HTR AllTerrain HTR-T432](https://www.rcteam.com/en/products/hobbytech-htr-tires-rims-buggy-allterrain-rear-x2-htr-t432), vorne ⛔ [HTR-T431](https://www.rcteam.com/en/products/hobbytech-htr-tires-rims-buggy-allterrain-front-x2-htr-t431); sonst nur „Soft“-Reifen (Louise RC) | – |
| Regler Hobbywing WP10BL60 G2 | ❌ (kein Hobbywing) | ✅ [44,99 €](https://www.lindinger.at/de/RC-Elektronik/Antriebe/Regler/HOBBYWING-QuicRun-WP10BL60-G2-Brushless-Regler-60A-2-3s-fuer-1-10/9801863) | ✅ [50,90 €](https://www.rcteam.com/en/products/hobbywing-esc-quicrun-wp10bl60-g2-60a-2-3s-3) | ✅ [Produktseite](https://www.rc-race-shop.de/hobbywing/hw30107300-hobbywing-quicrun-wp10bl60-g2-brushless-regler-60a-2-3s) |
| Motor Hobbywing 3652SL G2 3250 kV | ❌ (kein Hobbywing) | ✅ [32,99 €](https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Antriebe/Elektromotoren/HOBBYWING-QuicRun-3652SL-G2-Sensorless-Motor-3250kV-3.175mm-Welle/9796158) | ✅ [34,90 €](https://www.rcteam.com/en/products/hobbywing-quickrun-3652sl-g2-motor) (kV-Auswahl ungeprüft) | ✅ [Produktseite](https://www.rc-race-shop.de/hobbywing/hw30404400-quicrun-3652sl-g2-sensorless-motor-3250kv) |
| ELRS-Empfänger mit PWM | ❌ (Suche „ExpressLRS“) | ✅ [HR7E 24,90 €](https://www.lindinger.at/de/RC-Elektronik/RC-Produkte/Empfaenger/HelloRadio-HR7E-ELRS-2-4GHz-Empfaenger-8-Kanaele-rot/9811430) | ❌ (Suche „ELRS receiver“) | ❌ (Suche „ELRS“) |
| Externer BEC ≥ 5 A, 6 V | – | – | ✅ [Hobbywing UBEC 10A V2, 29,90 €](https://www.rcteam.com/en/products/hobbywing-ubec-10a-v2-2-6s-30603003) | – |
| Servo Savöx SC-1258TG+ | ❌ (kein Savöx) | ✅ [54,99 €](https://www.lindinger.at/de/RC-Elektronik/Servos-Zubehoer/Servos-Digital-Low-Voltage/SAVOEX-SC-1258TG-6V-12KG-0-08s-DIGITAL-SERVO/9795331) | ✅ [65,90 €](https://www.rcteam.com/en/products/savox-servo-sx-sc-1258tg-12kg-0-08s-titanium) | ❌ (nur Ersatzgehäuse) |
| LiPo 2S Hardcase XT60 ≥ 4000 mAh | ❌ (nur Spektrum IC3/IC5) | ❌ (2S-Hardcase nur mit T-, XT90- oder IC-Stecker gefunden) | ✅ [Voltz 5000, 36,90 €](https://www.rcteam.com/en/products/voltz-lipo-5000mah-2s-7-4v-50c-hard-case-xt60-battery) | – |
| Kugellager 10x15x4 gedichtet | ❌ (Suche) | ✅ [Traxxas Gummidichtung 7,90 €/2](https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Zubehoer/Auto-Zubehoer/TRAXXAS-Kugellager-schwarze-Gummidichtung-10x15x4mm-2/9715538) | ✅ [Arrma 2RS 6,99 €/2](https://www.rcteam.com/en/products/arrma-ball-bearing-10x15x4mm-2rs-x2-ara610046) | ✅ [Traxxas 5119](https://www.rc-race-shop.de/rc-marken/traxxas/ersatzteile/5119-kugellager-10x15x4mm-gummiged) |
| Kugellager 8x14x4 / 5x10x4 / 5x8x2,5 gedichtet | 5x10x4 und 5x8x2,5 nur TLR, Dichtung nicht angegeben | ✅ z. B. [Traxxas 5x10x4](https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Zubehoer/Auto-Zubehoer/TRAXXAS-Kugellager-schwarze-Gummidichtung-5x10x4mm-2/9758844) | ✅ [XRAY 940814](https://www.rcteam.com/en/products/xray-bearing-8x14x4-high-speed-940814), [940510](https://www.rcteam.com/en/products/xray-bearing-5x10x4-metal-with-seals-940510), [940508](https://www.rcteam.com/en/products/xray-ball-bearing-5x8x2-5mm-x2-940508) | – |
| Kugellager 5x13x4 gedichtet | ✅ [Axial AXI237009, „sealed“, 2 Stk, 9,99 €](https://www.horizonhobby.com/eu/de/product/axial-5mm-x-13mm-x-4mm-ball-bearing-2/AXI237009.html); [Arrma ARA610054 RS](https://www.horizonhobby.com/eu/de/product/arrma-ball-bearing-5x13x4-rs-2/ARA610054.html) nur vorbestellbar (April 2027); [LOSA6955](https://www.horizonhobby.com/eu/de/product/losi-5-x-13mm-hd-clutch-bearings-28b-8t-22-22t-22sct-22-4-8x-8xe/LOSA6955.html) (Dichtung nicht angegeben) | ❌ (Suche „Kugellager 5x13x4“) | ✅ [GForce „Rubber“](https://www.rcteam.com/en/products/gforce-rubber-bearings-5x13x4-gf-0500-008) (Inhalt nicht angegeben), [T-Work's BB-5134-10](https://www.rcteam.com/en/products/t-works-bearings-5x13x4-x10-bb-5134-10) (Dichtung nicht angegeben) | – |
| Schrauben M3 Edelstahl, Zylinder- und Senkkopf, 6–30 mm | – | ✅ Robbe-Einzelpackungen à 30 Stk, z. B. [Zylinderkopf M3x20](https://www.lindinger.at/de/Bauzubehoer-Mehr/Bauzubehoer-Kleinteile/Schrauben-Muttern-Scheiben/Schrauben-metrisch/Robbe-Modellsport-Zylinderkopfschrauben-Innensechskant-M3x20mm-30Stk.-Edelstahl/9796364), [Senkkopf M3x10](https://www.lindinger.at/de/Bauzubehoer-Mehr/Bauzubehoer-Kleinteile/Schrauben-Muttern-Scheiben/Schrauben-metrisch/Robbe-Modellsport-Senkkopfschrauben-Innensechskant-M3-0x10mm-30Stk.-Edelstahl/9796384) (alle Längen in der Stückliste) | ✅ z. B. [Yeah Racing SSS-400](https://www.rcteam.com/en/products/yeah-racing-set-of-400-m3-screws-sss-400) (nur Linsen- und Senkkopf 6–14 mm, kein Zylinderkopf) | – |
| Stoppmuttern, Scheiben M3, Stoppmuttern M2,5 Edelstahl | – | ✅ [Stoppmuttern M3](https://www.lindinger.at/de/Bauzubehoer-Mehr/Bauzubehoer-Kleinteile/Schrauben-Muttern-Scheiben/Muttern-Stoppmuttern/Robbe-Modellsport-Stoppmuttern-M3-30Stk.-Edelstahl/9796427), [Stoppmuttern M2,5](https://www.lindinger.at/de/Bauzubehoer-Mehr/Bauzubehoer-Kleinteile/Schrauben-Muttern-Scheiben/Muttern-Stoppmuttern/Robbe-Modellsport-Stoppmuttern-M2.5-30Stk.-Edelstahl/9796426) | – | – |
| Gewindeeinsätze M3 | – | ✅ [MP-JET](https://www.lindinger.at/de/Bauzubehoer-Mehr/Bauzubehoer-Kleinteile/Schrauben-Muttern-Scheiben/Diverses-Befestigungsmaterial/MP-JET-Gewindeeinsatz-M3-kurz-20-Stueck/9795599) | ❌ (Suche „insert M3“) | – |
| Kugelköpfe 4,8 mm | ✅ [TLR6023](https://www.horizonhobby.com/eu/de/product/team-losi-racing-ball-stud-4.8-x-10mm-4-22/TLR6023.html) | ⏳ [4,8 × 8](https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Zubehoer/Auto-Zubehoer/LOSI-TLR-Kugelkopf-mit-Gewinde-4.8-x-8mm-4-22/9754050) | – | – |
| Kugelpfannen TLR 22 HD TLR234107 | ⛔ [Auslaufartikel](https://www.horizonhobby.com/eu/de/product/team-losi-racing-hd-ball-cup-set-all-22/TLR234107.html) | ⏳ [9,99 €](https://www.lindinger.at/de/Bauzubehoer-Mehr/Kopter-Auto-Ersatzteile/LOSI-HD-Ball-Cup-Set-All-22/9801037) | ❌ (Suche „TLR ball cup“) | – |
| Spurstangen 3,5 mm (TLR) | ⛔ [TLR334077 HD-Satz Titan 22X-4, Auslaufartikel](https://www.horizonhobby.com/eu/de/product/team-losi-racing-hd-turnbuckle-kit-titanium-22x-4/TLR334077.html); sonst nur Losi/TLR 4–4,5 mm (8IGHT) und Arrma M3–M7 | ❌ (nur 4/5/6 mm und Hobao) | nur [Revolution Design 3,5 × 48 mm für RC10 B7](https://www.rcteam.com/en/products/revolution-design-titanium-connecting-rod-3-5x48mm-6pcs-rc10-b7-rdrp0643) (Passung zu TLR-Pfannen ungeprüft) | ⛔ [Lunsford TLR22 Titan-Satz, 3 Paar, 32,00 €](https://www.rc-race-shop.de/lunsford/2059-team-losi-tlr22-titan-spurstangensatz), nicht lagernd (vierter Shop) |
| Ritzel-Befestigungssatz TLR232110, Distanzscheiben TLR236006 | ⛔ Auslaufartikel ([TLR232110](https://www.horizonhobby.com/eu/de/product/team-losi-racing-pinion-mounting-hardware-4-22x-4/TLR232110.html), [TLR236006](https://www.horizonhobby.com/eu/de/product/team-losi-racing-10-x-14mm-shims-0.1-0.2mm-5ea./TLR236006.html)) | ❌ ¹ | ❌ ² (Scheiben nur 10 × 12,5 mm) | ❌ ³ |
| XT60-Steckerpaar | – | ❌ (Suche liefert nur Kabel) | ✅ [6,50 €](https://www.rcteam.com/en/products/gforce-connector-xt60-male-vario-female-battery-gf-1003-001) | – |
| LiPo-Schutztasche | – | ✅ [Lipoguard L](https://www.lindinger.at/de/RC-Elektronik/Antriebe/Akkus/Robbe-Modellsport-Lipoguard-L-Lipo-Tasche-ca.-215x155x110-Hochwertige-Ausfuehrung/9811107) | ✅ z. B. [LRP 23x30](https://www.rcteam.com/en/products/lrp-lipo-protective-bag-23x30cm-65865) | – |

Fußnoten:
1. Lindinger: Suche „LOSI 22X-4“ liefert nur Teile der älteren TLR 22-4 (Riemenantrieb), keine 22X-4-Antriebsteile. Suchen nach den Teilenummern ohne passenden Treffer.
2. RC Team: Suche nach den Teilenummern TLR233064, TLR233063, TLR332086, TLR232137, TLR232108, TLR232107, TLR232102, TLR232105, TLR232126, TLR232109 und nach „TLR 22X-4“ jeweils ohne Treffer.
3. rc-race-shop.de: Suche „TLR“ liefert 6 Artikel, keiner für die 22X-4. Suchen nach den Teilenummern ohne Treffer.
4. Lindinger und rc-race-shop.de: Suche „TLR233064“ ohne passenden Treffer.

**Gewählte Shops (höchstens 3):**

| Shop | Anteil | Begründung |
|---|---|---|
| Horizon Hobby EU | alle TLR-Teile, Kugelköpfe, Lager 5x13x4 (Axial) | höchste Abdeckung der Plattform, als einziger Shop mit 22X-4-Antriebsteilen |
| Modellbau Lindinger | Regler, Motor, Empfänger, Servo, Räder, Kugelpfannen, Schrauben, Muttern, Scheiben, Gewindeeinsätze, Kleinteile Elektronik | einziger Shop mit ELRS-PWM-Empfänger und mit Allround-Rädern vorne und hinten; günstigster Preis für Regler, Motor und Servo; M3-Schrauben in allen Längen |
| RC Team | Akku, Lager, XT60-Steckerpaar, UBEC | einziger Shop mit 2S-Hardcase-Akku mit XT60; Lager mit ausgewiesener Gummidichtung; externer BEC |

Die Teile „manuell suchen“ sind in keinem dieser drei Shops lieferbar. Kauft der Nutzer sie woanders, kommt ein vierter Shop dazu; das ist eine Entscheidung des Nutzers.

## Rechnungen

### Höchstgeschwindigkeit (ELEK-ZUK-001)

Formel: v = kV × U ÷ i_ges × π × D

| Größe | Wert | Quelle |
|---|---|---|
| kV | 3250 1/(min·V) | Hobbywing 3652SL G2 [E2] |
| U | 7,4 V (2S nominal) | – |
| Motordrehzahl | 3250 × 7,4 = 24 050 1/min | – |
| Hauptzahnrad | 78 Zähne | TLR232116 |
| Diff-Übersetzung | 2,5 : 1 | [T1] |
| Raddurchmesser D | 85 mm (Carson All Terrain 4WD) | [R1] |
| Radumfang | π × 0,085 m = 0,2670 m | – |

| Motorritzel | Gesamtübersetzung (78/z × 2,5) | Raddrehzahl | v bei 7,4 V | v bei 8,4 V (voll geladen) | erhältlich (Horizon EU) |
|---|---|---|---|---|---|
| 24 Z | 8,125 | 2960 1/min | 47,4 km/h | 53,8 km/h | nicht gefunden |
| 25 Z | 7,8 | 3083 1/min | 49,4 km/h | 56,1 km/h | vorbestellbar (TLR332025) |
| **26 Z** | **7,5** | **3207 1/min** | **51,4 km/h** | 58,3 km/h | **lagernd (TLR332026)** |

Gewählt ist das lagernde **26-Z-Ritzel: 51,4 km/h** (Ziel 45–55 km/h). Der Regler ist laut Hobbywing für 2S-Buggys bis kV < 4000 freigegeben [E1], 3250 kV liegt darunter.

**Hinweis: Das ist ein Leerlaufwert.** Die Rechnung nimmt die Leerlaufdrehzahl (kV × U) ohne Last, Spannungseinbruch und Schlupf an. Die echte Höchstgeschwindigkeit liegt darunter (Hinweis aus dem Review: real etwa 42–46 km/h; nicht belegt). Sie wird am Prototyp gemessen (GPS). Reicht sie nicht, ist das 27- oder 28-Z-Ritzel die nächste Stufe; Ritzel sind Verschleißteile und schnell getauscht.

### Federweg (MECH-ZUK-006)

- Dämpfer: TLR G3 42 mm, **Hub h = 30,5 mm** (Bausatz-Setup hinten) [T1]. v1 nutzt diesen Dämpfer an allen vier Rädern (2 Sätze TLR233064).
- Federweg am Rad: s = h × i, mit i = Abstand Querlenker-Drehpunkt bis Radmitte ÷ Abstand Drehpunkt bis Dämpferanlenkung (Dämpfer senkrecht zum Querlenker; steht der Dämpfer schräg um den Winkel θ, wird s = h × i ÷ cos θ größer).
- Für **s ≥ 30 mm** (MECH-FZG-005): i ≥ 30 ÷ 30,5 = **0,98**. Schon mit i = 1 erfüllt.
- Für den Startwert **`federweg` = 35 mm**: i ≥ 35 ÷ 30,5 = **1,15**. Das ist eine Vorgabe für die Querlenker-Konstruktion.
- Befestigung: oben und unten mit M3-Schrauben und M3-Stoppmuttern an Dämpferbrücke und Querlenker [T1 S. 26, 32]. Einbaulänge: **am Teil messen**.
- **Federn für 2,0 kg:** Statische Radlast bei 50 : 50 Verteilung 2,0 kg × 9,81 m/s² ÷ 4 = 4,9 N. Die Kraft am Dämpfer ist 4,9 N × i. Die Federrate der mitgelieferten TLR-Federn („LF weiß“) ist in keiner Quelle angegeben. Die Abstimmung kann deshalb erst am Prototyp erfolgen (🔧). Härtere oder weichere TLR-LF-Federn (12 mm) gibt es einzeln bei Horizon EU, z. B. [TLR233056](https://www.horizonhobby.com/eu/de/product/team-losi-racing-rear-springs-white-low-frequency-12mm-2/TLR233056.html).

### Elektronik: BEC, Unterspannung und Failsafe

- **Regler Hobbywing QuicRun WP10BL60 G2** [E1][E3]: sensorless, 60 A / 360 A, 2–3S. Fahrmodi Vorwärts/Bremse, **Vorwärts/Rückwärts/Bremse**, Vorwärts/Rückwärts. Unterspannungsabschaltung wählbar: aus, 2,6 / 2,8 / 3,0 / **3,2 / 3,4 V pro Zelle** → Einstellung **3,4 V/Zelle** (mindestens 3,2 V, ELEK-FZG-003). Zellenzahl manuell auf 2S stellen (Hobbywing rät von der Automatik ab). BEC **6 V / 3 A** Schaltregler. Schutz bei Verlust des Gassignals („Throttle signal loss protection“). Der Eingang hat **keinen Stecker**: XT60-Stecker anlöten (Stückliste).
- **Empfänger HelloRadio HR7E** [E4]: ExpressLRS 3.3.0, 8 PWM-Ausgänge, 4,5–8,4 V. Für den Betrieb in der EU wird die Firmware mit der Regulatory Domain **EU_CE_2400 (LBT)** geflasht [E5]. Beim Kauf ist die Domain nicht angegeben. **Der Sender muss ebenfalls mit EU_CE_2400 laufen**, sonst verbinden sich Sender und Empfänger nicht (gilt für die spätere Senderwahl).
- **Failsafe-Kette (ELEK-FZG-002):** Bei ELRS-PWM-Empfängern hat jeder Ausgang einen einstellbaren Failsafe-Wert (988–2012 µs, WebUI). Failsafe greift, wenn die Verbindungsqualität auf 0 fällt oder 1 s lang kein gültiges Kanalpaket kommt. Beim Einschalten gibt der Empfänger keine Impulse aus, bis der Sender verbunden ist [E6]. **Einstellung: Kanal 2 (Gas) Failsafe = 1500 µs (Neutral), Kanal 1 (Lenkung) Failsafe = 1500 µs (geradeaus).** Der Regler sieht dann Neutral und der Motor steht. Fallen die Impulse ganz weg, greift zusätzlich der Signalverlust-Schutz des Reglers [E1]. Hobbywing empfiehlt selbst, den Failsafe des Gaskanals auf Neutral zu setzen [E1]. Test mit hängendem Rad am Prototyp (🔧): Sender aus → Motor steht **und** Lenkung geht in Mittelstellung.
- **Servo Savöx SC-1258TG+** [E7]: 12 kg·cm und 0,08 s/60° bei 6 V, 4,8–6,0 V (nicht HV). **Blockierstrom 4000 mA bei 4,8 V und 5000 mA bei 6,0 V** [E7] (steht nur auf der englischen Lindinger-Seite).
- **Problem Servostrom:** Der Regler-BEC liefert 6 V / 3 A und versorgt zusätzlich den Reglerlüfter [E1]. Blockiert das Servo (Räder am Anschlag oder an einem Hindernis), braucht es bis zu 5 A. Dann bricht die BEC-Spannung ein; fällt sie unter 4,5 V, startet der Empfänger neu und die Lenkung ist kurz ohne Signal.
- **Lösung (Nutzerentscheidung 2026-10-27): externer BEC Hobbywing UBEC 10A V2** [E8][E9], 10 A Dauer / 15 A Spitze, Eingang 6–25,2 V (2S: 6,8 V bei der Abschaltschwelle 3,4 V/Zelle, also im Bereich), Ausgang auf **6,0 V** stellen (Servo max. 6,0 V). Er versorgt Empfänger und Servo; Reserve gegenüber 5 A Blockierstrom plus ca. 0,1 A Empfänger ist doppelt. Der Eingang wird an die Akkuleitung des Reglers (XT60-Seite) angelötet, die **rote Ader des Regler-Steuerkabels wird am Empfänger abgezogen**, damit nicht zwei BECs parallel speisen. Der Regler-BEC versorgt dann nur noch seinen Lüfter.
  - Verworfen: **Pufferkondensator** (z. B. 4700 µF, RC Team 4,90 €): überbrückt nur Millisekunden (2 A Defizit × 2,35 ms ≈ 1 V Einbruch bei 4700 µF), nicht ein Blockieren über Sekunden. **Anderes Servo:** nicht weiter verfolgt. Ein Servo mit ≥ 10 kg·cm braucht beim Blockieren ebenfalls mehrere Ampere, und Blockierströme werden oft nicht angegeben; ein belegter Wert ≤ 3 A wäre nötig. Der UBEC löst das Problem unabhängig vom Servo.
  - **Schalter:** Ob der UBEC einen Ein/Aus-Schalter hat, ist laut Quellen widersprüchlich (RC Team nennt keinen [E8], htmodel.sk nennt ihn „switched BEC“ [E9]) → **am Teil prüfen**.
  - **Wichtig (Hinweis für die Bauanleitung):** Der Schalter des Reglers schaltet Empfänger und Servo **nicht** mehr ab, weil der UBEC direkt am Akku hängt. Bei angestecktem Akku ziehen Empfänger und UBEC weiter Strom und können den LiPo bis zur Tiefentladung entladen. Auch nach der Unterspannungsabschaltung des Reglers (3,4 V/Zelle) laufen Empfänger und Servo weiter. Deshalb **den Akku nach der Fahrt sofort abstecken** (LiPo-Schutz). Hat der UBEC doch einen Schalter, ihn zusätzlich nutzen; das ersetzt das Abstecken nicht.
  - **Akkuspannung überwachen (Hinweis für die Bauanleitung):** Den Spannungsmesseingang des HR7E an den Akku anschließen, damit die Akkuspannung per Telemetrie übertragen wird. Am späteren Sender einen Telemetrie-Alarm für Unterspannung einstellen. Alternativ einen LiPo-Summer am Balancerstecker verwenden (nicht in der Stückliste v1).

## Lager (MECH-ZUK-008)

Alle Lager sind metrische Standardgrößen und gedichtet. Positionen nach der Anleitung der 22X-4 Elite [T1].

| Größe | Position | Stück v1 | Bestellt | Quelle Position |
|---|---|---|---|---|
| 10x15x4 | Hinterachsdiff | 2 | | [T1] S. 28 |
| 10x15x4 | Mittelschott, Rutschkupplung | 2 | | [T1] S. 18 |
| 10x15x4 | Radträger hinten innen | 2 | | [T1] S. 31 |
| **10x15x4 gesamt** | | **6** | 3 × 2 Stk (Arrma 2RS) | |
| 8x14x4 | Ritzelwelle hinten | 1 | 1 × 2 Stk (XRAY 940814) | [T1] S. 27 |
| 5x10x4 | Ritzelwelle hinten | 1 | | [T1] S. 27 |
| 5x10x4 | Achsschenkel vorne | 2 | | [T1] S. 24 |
| **5x10x4 gesamt** | | **3** | 2 × 2 Stk (XRAY 940510) | |
| 5x13x4 | Radträger hinten außen | 2 | | [T1] S. 31 |
| 5x13x4 | Achsschenkel vorne | 2 | | [T1] S. 24 |
| **5x13x4 gesamt** | | **4** | 2 × 2 Stk (Axial AXI237009, „sealed“) | |
| 5x8x2,5 | Lenkung (Umlenkhebel) | 4 | 2 × 2 Stk (XRAY 940508) | [T2] Lenkung, Annahme für eigene Lenkung |

Die Stückzahl je Getriebe (je ein 8x14x4 und ein 5x10x4 für die Ritzelwelle) ist im Textauszug der Anleitung nicht eindeutig erkennbar. Sie wird bei der Konstruktion am Teil geprüft. Die XRAY-Lager sind laut XRAY-Ersatzteilliste gummigedichtet [X2].

## Verbindungselemente (MECH-ZUK-009)

Startsortiment, alles Edelstahl, bei Lindinger (Einzelpackungen, Artikelnamen auf den Produktseiten):

| Art | Längen | Stück |
|---|---|---|
| M3 Zylinderkopf Innensechskant (Robbe, je 30 Stk) | 6, 8, 10, 14, 20, 30 mm | 180 |
| M3 Zylinderkopf Innensechskant (Planet-Hobby, 10 Stk) | 25 mm | 10 |
| M3 Senkkopf Innensechskant (Robbe, je 30 Stk), u. a. für die Grundplatte | 6, 8, 10, 14, 20 mm | 150 |
| **M3-Schrauben gesamt** | 6–30 mm | **340** |
| M3-Stoppmuttern / Scheiben M3 3,2 × 7 / Gewindeeinsätze M3 | – | 60 / 30 / 60 |
| M2,5-Stoppmuttern (Ritzelbefestigung, statt TLR6312) | – | 30 |
| Kugelköpfe 4,8 × 10 mm TLR6023 / Kugelpfannen HD TLR234107 | – | 16 / 2 Sätze |

**Annahme:** Die genauen Längen und Mengen stehen erst nach der Konstruktion fest. Fehlende Längen (z. B. M3x4, M3x12, M3x16) werden dann nachbestellt. Die Robbe-Reihe Innensechskant führt bei Lindinger nur die Längen oben. Die vorherigen Schraubenboxen (Robbe 9796451/452/453) wurden ersetzt, weil sie je nur 20 M3-Schrauben in zwei Längen enthalten und sonst M4/M5.

## Vorderachse 4WD-tauglich (MECH-ZUK-005)

Die Vorderachse nutzt die **Front CVA Axle TLR232107**. Das ist dieselbe Achse, die in der 22X-4 das angetriebene Vorderrad trägt [T1 S. 23]. Dazu kommen dieselben Mitnehmer (TLR232111, 12 × 4 mm) und Lager (5x13x4, 5x10x4) wie beim Spender. Für Phase 2 kommen nur die Antriebswellen TLR232104 (74 mm), das Vorderdiff und das Getriebe dazu. Die Radachsen werden nicht neu gekauft. In v1 fehlt die Antriebswelle, deshalb muss der Achsschenkel die Achse axial sichern.

## Vorgaben für die Konstruktion

Aus den Zukaufteilen folgen diese Vorgaben für das Skelettmodell. Alle Maße, die hier fehlen, werden am Teil gemessen.
- **Hinterachse:** Lagersitze 10x15x4 für das Diff, 8x14x4 und 5x10x4 für die Ritzelwelle. Abstand Diff-Abtrieb zu Radträger passend zur Welle **67 mm** (TLR232102). Radträger mit 10x15x4 innen und 5x13x4 außen.
- **Mittelantrieb:** Mittelschott mit 2 × 10x15x4 für die Rutschkupplung. Abstand Mittelschott zum Hinterachsgetriebe passend zur Mittelwelle **93 mm**, nach vorne passend zu **68 mm** (TLR232105). Motor Ø 36 × 52 mm, Welle 3,175 mm; Lochbild am Teil messen.
- **Vorderachse:** Achsschenkel mit 5x13x4 und 5x10x4, Achse in v1 axial sichern.
- **Dämpfer:** Hebelverhältnis i ≥ 1,15 für 35 mm Federweg. Befestigung M3.
- **Elektronik:** Regler 46 × 36,5 × 34,3 mm laut Lindinger, 48,5 × 38 × 32 mm laut Hobbywing → am Teil messen. Empfänger 46 × 26 × 15 mm. UBEC 43,1 × 32,3 × 12,5 mm laut RC Team [E8], 45 × 20 × 16,2 mm laut htmodel.sk [E9] → am Teil messen. Servo 40,3 × 20,2 × 37,2 mm, Lochabstand und Abtriebshöhe am Teil messen. Akku 138 × 46 × 25 mm.
- **Räder** (Nutzerentscheidung 2026-10-27: Carson All Terrain bleiben, die Konstruktion gleicht aus): Ø 85 × 40 mm vorne und hinten, 12 mm Sechskant [R1]. **Einpresstiefe, Nabentiefe und Felgengröße (2,2") am Teil messen**, keine Quelle nennt sie. Daraus folgen diese Vorgaben:
  - **Radmutter:** Prüfen, ob das M4-Gewinde der Radachsen TLR232107 (vorne) und TLR232108 (hinten) mit Mitnehmer (12 × 4 bzw. 12 × 5 mm) weit genug durch die Nabe ragt, damit die Radmutter TLR336000 voll greift. Reicht es nicht: Mitnehmer bzw. Achse anpassen (z. B. schmalerer Mitnehmer) oder andere Radmutter.
  - **Spur 250 mm** (`spurbreite`, über die Räder) über Radträger, Achsschenkel und die gemessene Einpresstiefe einstellen. Hinten legen die Wellen 67 mm (TLR232102) und das Diff die Innenlage der Radträger fest; die Spur lässt sich dort nur über Radträger und Einpresstiefe einstellen, nicht über die Wellenlänge.
  - **Freigang beim Lenkeinschlag:** Die Vorderräder sind mit 40 mm so breit wie die hinteren (4WD-Buggys haben vorne meist schmalere Räder, die Vorderachse TLR232107 mit Mitnehmer 12 × 4 ist darauf abgestimmt). Beim vollen Lenkeinschlag Freigang des 40-mm-Rads zu Querlenker, Achsschenkel, Spurstange und Grundplatte im Modell prüfen.
- **Gewindeeinsätze:** Bohrungsmaß am Teil messen.

## Manuell suchen

Diese Teile sind in keinem der drei gewählten Shops lieferbar. Sie stehen mit Vermerk in der Stückliste. Den Rest erledigt der Nutzer. Die Richtpreise stammen von Produktseiten (Stand 26.10.2026) und gehen **nicht** in die Summe der Stückliste ein, sondern nur in die Budget-Spanne.

| Teil | Problem | Richtpreis (Quelle) | Hinweis |
|---|---|---|---|
| Dämpfersatz TLR233064 (2 Sätze) | bei Horizon EU derzeit nicht lieferbar, kein Preis angezeigt; in keinem anderen Kandidaten-Shop | 2 × 75,90–76,90 € = 151,80–153,80 € (Vergleichspreis Associated 91994/91995, RC Team); Horizon USA: 62,99 USD je Satz [S4] | wieder bei Horizon EU prüfen; Einzelteile sind dort nur teilweise zu finden: Gehäuse TLR233026, Kolbenstange TLR333012, Kolben, Dichtungen und Federteller-Ring sind lagernd, Kappen (TLR333021, TLR5086) und Federteller (TLR233030) wurden nicht gefunden |
| Spurstangen 3,5 mm (4 Paar: Sturz vorne/hinten, Lenkung) | TLR334077 bei Horizon EU Auslaufartikel; Lunsford bei rc-race-shop.de nicht lagernd und vierter Shop | 64,00 € (2 × Lunsford-Satz à 3 Paar, 32,00 € [S5]); TLR334077 Listenpreis 39,99 € [S6] | Länge erst nach der Konstruktion |
| Befestigungssatz Kegelritzel TLR232110 | bei Horizon EU Auslaufartikel, sonst in keinem Shop | 7,99 € (Listenpreis Horizon EU [S6]) | Inhalt am Teil bzw. in der Anleitung prüfen |
| Diff-Distanzscheiben 10 × 14 mm TLR236006 | bei Horizon EU Auslaufartikel; RC Team nur 10 × 12,5 mm | 5,99 € (Listenpreis Horizon EU [S6]) | zum Einstellen des Zahnspiels; Normscheibe DIN 988 10 × 14 mm möglich |
| **Summe Richtpreise** | | **77,98 €** ohne Dämpfer | zuzüglich Versand eines vierten Shops, falls nötig |

Erledigt in der Überarbeitung: Lager 5x13x4 (jetzt Axial AXI237009, „sealed“, 2 Stk je Packung, Horizon EU) und Stoppmutter M2,5 (jetzt Normteil Robbe Edelstahl, Lindinger).

## Verschleißteile (DOC-ZUK-006)

Vorrätig halten, aber in v1 nicht bestellen:

| Teil | Teilenummer | Shop | Preis |
|---|---|---|---|
| Motorritzel 26Z 48P | TLR332026 | Horizon EU | 8,99 € |
| Hauptzahnrad 78Z 48P | TLR232116 | Horizon EU | 7,99 € |
| Rutschkupplungsscheiben | TLR232121 | Horizon EU | 29,99 € |
| Antriebswellen hinten 67 mm (2) | TLR232102 | Horizon EU | 19,99 € |
| CVA-Stifte (2 Sätze) | TLR332074 | Horizon EU | 7,99 € |
| Mitnehmerstifte (8) | TLR232002 | Horizon EU | 2,99 € |
| Kugelpfannen HD | TLR234107 (LOSI HD Ball Cup Set, Lindinger 9801037) | Lindinger | 9,99 € |
| Kegelritzel und Tellerrad | TLR232126, TLR232127 | Horizon EU | 9,99 € / 9,99 € (Tellerrad ist bestellt; ist es schon im Diff TLR332086, bleibt es als Ersatz) |

## Teile für 4WD, Phase 2 (DOC-ZUK-007)

Nicht bestellen. Preise vom 26.10.2026 bei Horizon EU.

| Teil | Teilenummer | Preis | Bemerkung |
|---|---|---|---|
| Vorderachsdiff komplett | TLR332086 | 49,99 € | wie hinten |
| Kegelritzel vorne | TLR232126 | 9,99 € | |
| Ritzelwelle vorne | TLR232109 | – | zweites Stück aus dem Zweierpack von v1 |
| Antriebswellen vorne 74 mm (2) | TLR232104 | 19,99 € | |
| Mittelwelle nach vorne 68 mm | TLR232105 | – | schon im Satz von v1 enthalten |
| Abtrieb vorne am Mittelantrieb | TLR232137 | – | die Rutschkupplung hat beide Abtriebe |
| Lager vorderes Getriebe | 2 × 10x15x4, 1 × 8x14x4, 1 × 5x10x4 | – | 8x14x4 und 5x10x4 sind als Reserve in den Packungen von v1 |
| CVA-Stifte | TLR332074 | 7,99 € | |

## Budget

Alle Summen per Skript aus `bom/stueckliste.csv` (Menge × Preis je Zeile).

| Posten | Teile | Versand nach DE | Summe |
|---|---|---|---|
| Horizon Hobby EU | 373,76 € (ohne Dämpfer) | 0,00 € (kostenlos ab 90 €) [S1] | 373,76 € |
| Modellbau Lindinger | 299,54 € | 0,00 € (kostenlos nach DE ab 99 €) [S2] | 299,54 € |
| RC Team | 124,27 € | 7,99–14,99 € nach Gewicht, gerechnet mit 14,99 € [S3] | 139,26 € |
| **A: Summe aller Posten mit Preis** | **797,57 €** | **14,99 €** | **812,56 €** |
| Dämpfer TLR233064 (2 Sätze), Preis offen | Vergleichspreis 2 × 75,90–76,90 € = 151,80–153,80 € | 0,00 € (Horizon EU) [S1] | 151,80–153,80 € |
| **B: A + Dämpfer** | | | **964,36–966,36 €** |
| Teile „manuell suchen“ (Richtpreise, siehe [Manuell suchen](#manuell-suchen)) | Spurstangen 64,00 €, TLR232110 7,99 €, TLR236006 5,99 € | offen (vierter Shop) | 77,98 € |
| **C: vollständige Summe (B + Richtpreise)** | | | **1042,34–1044,34 €** |

- Budget laut Entscheidung des Nutzers vom 26.10.2026: **600–1050 €** inkl. Versand (vorher 600–900 € und 600–1000 €).
- Die vollständige Summe C liegt mit **1042,34–1044,34 €** im Budget. Die Reserve bis 1050 € beträgt nur **5,66–7,66 €**.
- **Unsicher bleibt der Dämpferpreis.** Horizon EU zeigt für TLR233064 keinen Preis, solange der Artikel nicht lieferbar ist (erneut geprüft am 26.10.2026). Als Vergleich dienen komplette 1:10-Buggy-Dämpfersätze (2 Stück) von Associated bei RC Team, 75,90 € (91994) und 76,90 € (91995); sie haben 13 mm Bohrung, der TLR G3 hat 12 mm (Big Bore). Bei Horizon USA kostet TLR233064 62,99 USD [S4]. **Kostet ein Satz in der EU mehr als 79,73 €, liegt C über 1050 €.**
- Kauft der Nutzer Teile „manuell suchen“ bei einem vierten Shop, kommt dessen Versand dazu und kann die Reserve aufbrauchen.
- Sparmöglichkeiten, falls es nicht reicht: Spurstangen aus TLR334077 statt zwei Lunsford-Sätzen (−24,01 €, falls noch erhältlich), M3-Schrauben-Sortiment nach der Konstruktion auf die nötigen Längen reduzieren (bis −29,28 €), CVA-Hülsen TLR232132 und Mitnehmerstifte nur bei Bedarf.
- Sender, Ladegerät, Werkzeug und Karosserie sind nicht enthalten.

## Quellen

- [T1] TLR 22X-4 Elite, Anleitung TLR03026 (mehrsprachig, Horizon Hobby): https://assets.horizonhobby.com/on/demandware.static/-/Sites-horizon-master/default/dwec1871dd/Manuals/TLR03026_Manual-MULTI.pdf (Radstand, Spur, Übersetzung, Dämpferhub, Teileliste, Lagerpositionen)
- [T2] TLR 22X-4 2.0 DC, Anleitung TLR-1264: https://assets.horizonhobby.com/on/demandware.static/-/Sites-horizon-master/default/dwb45986b4/Manuals/TLR-1264-MANUAL-ML.pdf
- [T3] Horizon Hobby, Produktseite 22X-4 Elite (Specs: 48-pitch, Wheelbase 284 mm, Width 249 mm): https://www.horizonhobby.com/product/1-10-22x-4-elite-4x4-buggy-race-kit/TLR03026.html
- [B1] Team Associated, Pressemitteilung RC10B74.2D (Radstand 280,5–285,5 mm, Übersetzung 2,50:1): https://img2.associatedelectrics.com/pdf/cars_and_trucks/RC10B74.2D/PressRelease_052722_90037-RC10B74.2D.pdf
- [B2] Team Associated, Anleitung RC10B74.2: https://img2.associatedelectrics.com/pdf/cars_and_trucks/RC10B74.2/Team/B742C_Kit_Manual_12_29_2023.pdf
- [X1] XRAY XB4 2026, Herstellerseite: https://teamxray.com/xb4/2026
- [X2] XRAY XB4 2026, Ersatzteilliste: https://teamxray.com/downloads/99/xb4_2026_part_list.pdf
- [X3] XB4-Daten aus Händler-/Pressetexten (Breite 245–250 mm, Radstand 279–281 mm): https://www.competitionx.com/?p=13868
- [R1] Lindinger, Carson 1:10 Räder (4) All Terrain 4WD, 500900136 (technische Daten: Ø 85 mm, Breite 40 mm, Mitnehmer 12 mm, „Durch das All Terrain Reifenprofil sind sie sowohl im Gelände als auch auf der Straße bestens unterwegs“): https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Zubehoer/Reifen-Felgen/Reifen-Felgen-Sets/CARSON-1-10-Raeder-4-All-Terrain-4WD/9806731
- [E1] Hobbywing, Parameterliste und Anleitung QuicRun WP10BL60 (G2): https://support.hobbywingdirect.com/hc/article_attachments/20206396553107 und https://hobbywing.com/en/uploads/file/20221015/eba2fcdde83f06810fea0bc12d448f1a.pdf
- [E2] Lindinger, Hobbywing QuicRun 3652SL G2 3250 kV (Maße, Gewicht): https://www.lindinger.at/de/Fahrzeuge-Boote/Fahrzeug-Antriebe/Elektromotoren/HOBBYWING-QuicRun-3652SL-G2-Sensorless-Motor-3250kV-3.175mm-Welle/9796158
- [E3] Hobbywing, Produktseite QuicRun WP 10BL60: https://hobbywing.com/en/products/quicrun-wp-10bl6056
- [E4] Lindinger, HelloRadio HR7E (technische Daten): https://www.lindinger.at/de/RC-Elektronik/RC-Produkte/Empfaenger/HelloRadio-HR7E-ELRS-2-4GHz-Empfaenger-8-Kanaele-rot/9811430
- [E5] ExpressLRS, Firmware-Optionen (Regulatory Domain EU_CE_2400, LBT): https://www.expresslrs.org/quick-start/firmware-options/
- [E6] ExpressLRS, PWM-Empfänger (Failsafe): https://www.expresslrs.org/hardware/pwm-receivers/
- [E7] Lindinger, Savöx SC-1258TG+, englische Produktseite (technische Daten, u. a. „Running Current (no load): 100mA @4.8V, 120mA @6.0V“ und „Stall Current (at locked): 4000mA @4.8V, 5000mA @6.0V“): https://lindinger.at/en/RC-ELECTRONICS/Servos-Accessories/Servos-Digital-Low-Voltage/SAVOEX-SC-1258TG-6V-12KG-0.08s-DIGITAL-SERVO/9795331 (die deutsche Seite https://www.lindinger.at/de/RC-Elektronik/Servos-Zubehoer/Servos-Digital-Low-Voltage/SAVOEX-SC-1258TG-6V-12KG-0-08s-DIGITAL-SERVO/9795331 nennt den Blockierstrom nicht)
- [E8] RC Team, Hobbywing UBEC 10A V2 (2–6S) 30603003 (10 A / 15 A Spitze, Eingang 6–25,2 V, Ausgang 6,0/7,4/8,4 V, 43,1 × 32,3 × 12,5 mm, 34 g): https://www.rcteam.com/en/products/hobbywing-ubec-10a-v2-2-6s-30603003
- [E9] htmodel.sk, Hobbywing UBEC-10A V2 Car (HW30603003; „switched BEC“, 10 A / 15 A Spitze, Eingang 6–25,2 V, Ausgang 6,0/7,4/8,4 V, 45 × 20 × 16,2 mm, 34 g): https://www.htmodel.sk/en/hobbywing-ubec-10a-v2-car/
- [S1] Horizon Hobby EU, Versandkosten: https://www.horizonhobby.com/eu/de/eu-shipping-cost
- [S2] Lindinger, Versandhinweis auf den Produktseiten („GRATIS-VERSAND: AT ab 89,- € / DE ab 99,- €“)
- [S3] RC Team, Versand: https://www.rcteam.com/en/pages/shipping-and-delivery
- [S4] Horizon Hobby USA, TLR233064 (Preis 62,99 USD, lagernd am 26.10.2026): https://www.horizonhobby.com/product/team-losi-racing-42mm-shock-set-g3-3mm-ticn-2/TLR233064.html
- [S5] rc-race-shop.de, Lunsford Team Losi TLR22 Titan-Spurstangensatz (6 Stk: je 2 Lenkung, Sturz vorne, Sturz hinten; 32,00 €, nicht lagernd): https://www.rc-race-shop.de/lunsford/2059-team-losi-tlr22-titan-spurstangensatz
- [S6] Horizon Hobby EU, Auslaufartikel mit Listenpreis in den Produktdaten der Seite: TLR334077 (39,99 €) https://www.horizonhobby.com/eu/de/product/team-losi-racing-hd-turnbuckle-kit-titanium-22x-4/TLR334077.html, TLR232110 (7,99 €) https://www.horizonhobby.com/eu/de/product/team-losi-racing-pinion-mounting-hardware-4-22x-4/TLR232110.html, TLR236006 (5,99 €) https://www.horizonhobby.com/eu/de/product/team-losi-racing-10-x-14mm-shims-0.1-0.2mm-5ea./TLR236006.html

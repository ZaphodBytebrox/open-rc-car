# Anforderungen: Gesamtfahrzeug

- **Kürzel:** FZG
- **Domäne:** beides
- **Status:** Entwurf
- **Stand:** 2026-10-28

## Zweck
Ein offenes 1:10-Allround-Buggy. Version 1 nutzt eine zugekaufte Antriebs- und Funkelektronik. Alle Schnittstellen sind so festgelegt, dass eigene Mechanik- und Elektronikteile die Zukaufteile später ersetzen können.

## Schnittstellen
| Zu | Art | Beschreibung |
|---|---|---|
| Akku | elektrisch | 2S LiPo, XT60 |
| Fahrtenregler | elektrisch/Signal | XT60 rein, Motorstecker raus, PWM 50 Hz mit 1000–2000 µs vom Empfänger |
| Lenkservo | mechanisch/Signal | Standardservo 40 × 20 mm, 25T-Abtrieb, PWM vom Empfänger |
| Empfänger | Signal | ELRS-Empfänger mit PWM-Ausgängen: Kanal 1 Lenkung, Kanal 2 Gas |
| Räder | mechanisch | 12-mm-Sechskantmitnehmer |

## Anforderungen
| ID | Priorität | Anforderung | Abnahmekriterium |
|---|---|---|---|
| MECH-FZG-001 | MUSS | Maßstab 1:10 Buggy, Radstand und Spurbreite als Fusion-Parameter | Parameter `radstand` und `spurbreite` vorhanden. Das Modell aktualisiert sich bei Änderung. |
| MECH-FZG-002 | MUSS | Antrieb v1: 2WD hinten. Die Grundplatte hat Platz und Lochbilder für das spätere Vorderdifferential und die vordere Welle. | Hüllkörper für den 4WD-Antriebsstrang im Modell kollisionsfrei |
| MECH-FZG-003 | MUSS | Alle selbst konstruierten Teile v1 sind auf einem Drucker mit 256 × 256 × 256 mm druckbar | Jedes Teil liegt im Slicer ohne Skalierung im Bauraum |
| MECH-FZG-004 | MUSS | Die Grundplatte ist fräsgerecht konstruiert (2,5D, Innenradien ≥ 1,5 mm), damit sie später als Aluteil gefertigt werden kann | Sichtprüfung in Fusion, CAM-Simulation ohne Kollision |
| MECH-FZG-005 | MUSS | Einzelradaufhängung vorne und hinten mit Öldämpfern (Zukauf bzw. aus dem TT-02B-Bausatz) | Federweg pro Rad mindestens so groß wie beim TT-02B mit denselben Dämpfern (bis 2026-10-27: ≥ 30 mm; Abschlag vom Nutzer am 2026-10-28 akzeptiert) |
| MECH-FZG-006 | SOLL | Bodenfreiheit etwa 25 mm | Messung am fahrfertigen Fahrzeug |
| MECH-FZG-007 | SOLL | Gewicht fahrfertig ≤ 2,0 kg | Wiegen |
| MECH-FZG-008 | MUSS | Akku ohne Werkzeug oder mit höchstens einer Schraube wechselbar | Wechsel in < 1 min |
| MECH-FZG-009 | MUSS | Elektronik-Bereich mit M3-Lochraster für Adapterplatten | Zukaufregler und Empfänger werden ohne Änderung an der Grundplatte montiert |
| MECH-FZG-010 | SOLL | Verschleißteile (Querlenker, Lenkhebel, Zahnräder) ohne Zerlegen der Grundplatte tauschbar | Montageprobe |
| MECH-FZG-011 | MUSS | Normteile metrisch, bevorzugt M3. Lager in Standardgrößen. | Stückliste prüfen |
| ELEK-FZG-001 | MUSS | Versorgung 2S LiPo (6,0–8,4 V), XT60 | Stückliste |
| ELEK-FZG-002 | MUSS | Failsafe: Bei Signalverlust geht der Motor aus, die Lenkung bleibt in Position oder geht neutral | Test: Sender ausschalten, das Rad hängt in der Luft und muss innerhalb 1 s stehen |
| ELEK-FZG-003 | MUSS | Unterspannungsschutz für den LiPo (≥ 3,2 V pro Zelle unter Last) | Einstellung am Regler nachgewiesen |
| ELEK-FZG-004 | MUSS | Fahrtenregler und Motor sind belüftet und nicht vollständig eingeschlossen | Temperatur des Motors nach 5 min Fahrt < 80 °C |
| ELEK-FZG-005 | SOLL | Kabelwege kurz und gegen drehende Teile geschützt | Sichtprüfung |

## Entscheidungen (vom Nutzer)
- 2026-10-26: Maßstab 1:10, Allround/Buggy
- 2026-10-26: Zuerst 2WD, später 4WD
- 2026-10-26: Prototyp gedruckt (256 mm Bauraum), später Grundplatte und hoch belastete Teile aus gefrästem Alu
- 2026-10-26: Brushless sensorless 2S, ELRS, Standardservo
- 2026-10-28: Spenderplattform Tamiya TT-02B; Spur, Radstand, Raddurchmesser und Federweg vom TT-02B (siehe `zukaufteile-v1.md`)

## Annahmen (abgeleitet, noch nicht bestätigt)
- Mittelmotor-Layout mit Kardanwelle, damit der Umstieg auf 4WD ohne Neukonstruktion möglich ist
- Die Grundplatte wird im Druck-Prototyp zweiteilig gebaut, weil sie mit etwa 330–380 mm länger als 256 mm ist
- Startwerte: seit 2026-10-28 vom TT-02B (Radstand ca. 266 mm, Spur ca. 208–217 mm, Raddurchmesser ca. 82 mm), Sechskant 12 mm; aktuelle Werte in `docs/plan.md`
- Ein Spritzwasserschutz ist für v1 nicht nötig

## Offene Punkte
- [ ] Spenderplattform für Differential, Dämpfer, Antriebswellen und Zahnräder
- [ ] Zielgeschwindigkeit und Budget
- [ ] Konkretes Modell für ELRS-Empfänger (mit PWM) und Sender
- [ ] Karosserie

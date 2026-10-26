# open-rc-car

Ein offenes RC-Auto zum Selberbauen, im Maßstab 1:10 als Allround-Buggy. Das Repository enthält alles, was man dafür braucht: CAD-Daten, Druckdateien, Stückliste und Bauanleitung. Später kommen eigene Elektronik und gefräste Aluteile dazu.

> **Status:** frühe Planungsphase. Es gibt noch keine fahrbare Version.

## Ziel

| | Version 1 | Später |
|---|---|---|
| Antrieb | 2WD (hinten) | 4WD (Allrad) |
| Mechanik | 3D-gedruckt (FDM) | Grundplatte und hoch belastete Teile aus gefrästem Alu |
| Fahrtenregler | Zukauf, brushless 2S | eigene Entwicklung |
| Fernsteuerung | Zukauf, ExpressLRS | eigener Sender |
| Zukaufteile | Zahnräder, Dämpfer, Lager, Differential, Antriebswellen, Räder | |

Was genau geplant ist und welche Entscheidungen schon getroffen sind, steht in [`docs/plan.md`](docs/plan.md).

## Eckdaten (vorläufig)

- Maßstab 1:10, Radstand ca. 280 mm, Spurbreite ca. 250 mm
- 2S LiPo mit XT60-Stecker, brushless sensorless Motor
- Standard-Lenkservo 40 × 20 mm
- Alle Druckteile passen in einen Bauraum von 256 × 256 mm

## Projektstruktur

| Ordner | Inhalt |
|---|---|
| `cad/fusion/` | Fusion-Quelldateien (`.f3d` / `.f3z`) |
| `cad/step/` | Neutrale CAD-Exporte (`.step`) für andere CAD-Programme |
| `print/stl/` | Druckfertige Einzelteile (`.stl`) |
| `print/3mf/` | Druckprojekte mit Einstellungen (`.3mf`) |
| `electronics/` | Elektronik: Schaltpläne, Platinen, Firmware |
| `bom/` | Stückliste (`stueckliste.csv`) |
| `docs/` | Plan, Anforderungen (`docs/anforderungen/`), Bauanleitung |

## Repository klonen

CAD- und Druckdateien liegen in [Git LFS](https://git-lfs.com). Installiere es einmalig, bevor du das Repository klonst:

```sh
brew install git-lfs   # macOS, andere Systeme siehe git-lfs.com
git lfs install
git clone https://github.com/ZaphodBytebrox/open-rc-car.git
```

## Mitmachen

So läuft die Arbeit am Projekt:
- Jede Anforderung bekommt einen eigenen Pull Request.
- Jeder Pull Request besteht aus genau einem Commit.
- Für eine neue Baugruppe werden zuerst die Anforderungen in `docs/anforderungen/` festgehalten, dann wird konstruiert.

Die Details stehen in [`AGENTS.md`](AGENTS.md). Die Datei gilt für Menschen und KI-Agenten.

## Lizenz

- **Hardware** (CAD-, STEP-, STL- und 3MF-Dateien, Elektronik): [CERN-OHL-S v2](LICENSE-HARDWARE)
- **Dokumentation** (Bauanleitung, Bilder, Stückliste): [CC BY-SA 4.0](LICENSE-DOCS)

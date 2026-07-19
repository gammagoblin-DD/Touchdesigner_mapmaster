# TouchDesigner MapMaster

Professionelles, modulares TouchDesigner-System für Projection Mapping, VJ-Visuals, Audioanalyse und shaderbasierte Echtzeiteffekte.

## Aktuelle Version

**MapMaster v1.0.0 – Stable Production Baseline**

TouchDesigner-Build:

```text
2025.32460
```

Milestone:

```text
GG_POST_MAP_MASTER_V39E2_FINAL_CLEANUP_19.07.2026_10-54-59.toe
```

## Verifizierter Projektstatus

- 0 Fehler
- 0 Warnungen
- 0 Node-Überlappungen
- Topologie unverändert
- Node-Größen unverändert
- Parameterstruktur unverändert
- Shader-, Callback- und Code-DAT-Inhalte unverändert
- archivierte und Test-COMPs vom Cooking getrennt
- FX01-Ausgabe valide bei 1920 × 1080
- finaler Output valide bei 1920 × 1080

## Projektstruktur

```text
/project1/MAP_MASTER
├─ 00_INPUT
├─ 01_MASK
├─ 02_ANALYSIS
├─ 03_AUDIO
├─ 04_FX
├─ 05_ROUTER
├─ 06_CONTROL
├─ 07_OUTPUT
└─ 99_DEBUG
```

## Hauptfunktionen

- portable `gg://`-Projektpfade
- Bild- und Video-Input
- No-Animation-Masken
- zentraler Audio-Analyzer
- Tempo-, Beat- und Feature-Auswertung
- modulare FX-Struktur
- FX-Routing
- zentrale Steuerbusse
- finaler Output mit Master-Postprocessing
- Deep-Export-, Audit- und Bridge-Workflow
- Milestone- und Backup-System

## Versionierte Dateien

```text
project/MAP_MASTER_v1.0.0.toe
docs/VERIFY_REPORT_v1.0.0.json
docs/RELEASE_NOTES_v1.0.0.md
CHANGELOG.md
VERSION
```

## Git LFS

TouchDesigner-Projektdateien werden über Git LFS verwaltet:

```text
*.toe
*.tox
```

Nach dem Klonen:

```powershell
git lfs install
git lfs pull
```

## Status der Effekte

### FX01 – Slime Mask

Produktiv und aktiv.

### FX02 – Psy Clean Post

Strukturell vorbereitet und aufgeräumt.

### FX03 – Electric Arcs

Strukturell vorbereitet und aufgeräumt.

## Entwicklungsregeln

- vor Änderungen PRE-Milestone speichern
- nach erfolgreicher Verifikation POST-Milestone speichern
- keine Node-Überlappungen
- keine automatischen Display-Flags
- bestehende Node-Größen erhalten
- Shader-, Callback- und Signalwege nur gezielt verändern
- Deep Export vor größeren Umbauten
- deutsche Datumsformate in Dateinamen

## Lizenz

Noch nicht festgelegt.

Vor einer öffentlichen Weitergabe sollte eine passende Lizenz ergänzt werden.

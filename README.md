# TouchDesigner MapMaster

Professionelles, modulares TouchDesigner-System für Projection Mapping, VJ-Visuals, Audioanalyse und shaderbasierte Echtzeiteffekte.

## Aktuelle Version

**MapMaster v1.1.0 – V47A3 Lightning Checkpoint**

TouchDesigner-Build:

```text
2025.32460
```

Milestone:

```text
GG_POST_GG_V47A3_APERIODIC_MULTISCALE_DISCHARGE_POLISH_07.08.2026_00-32-53.1.toe
```

## Verifizierter Projektstatus

- 0 Fehler und 0 Warnungen im V47Z0-Deep-Export
- 451 Runtime-Samples ohne Ausfall
- 58,32 FPS während des 45-Sekunden-Referenzlaufs
- stabiler Router auf FX03
- echte ungeclampte BPM-Auslesung einschließlich 200-BPM-Referenztrack
- kausale, audioqualifizierte Blitzereignisse
- keine beobachteten Spiralen, geschlossenen Pfade oder Rückwärtsanimationen
- aperiodische Mehrskalen-Tortuosität und strike-stabile Restrikes

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
project/MAP_MASTER_v1.1.0.toe
docs/RELEASE_NOTES_v1.1.0.md
docs/v1.1.0/PROJECT_DOSSIER_V47A3.md
docs/v1.1.0/HANDOVER_PROTOCOL_V47A3.md
docs/v1.1.0/VERIFY_REPORT_V47Z0.json
releases/v1.1.0/MAP_MASTER_V47Z0_FINAL_HANDOVER_DEEP_EXPORT_*.zip
CHANGELOG.md
VERSION
```

## Git LFS

TouchDesigner-Projektdateien werden über Git LFS verwaltet:

```text
*.toe
*.tox
*.zip
```

Nach dem Klonen:

```powershell
git lfs install
git lfs pull
```

## Status der Effekte

### FX01 – Slime Mask

Produktiv und aktiv.

### FX02 – Orbiting 3D Lights

Vorhanden und weiterhin Teil der modularen Effektstruktur.

### FX03 – Lightning Storm

V47A3 ist als stabiler, stilisiert-realistischer und live-tauglicher
Lightning-Checkpoint eingefroren. Der aktive V47A2-Controller nutzt echte BPM,
audioqualifizierte Transienten, gelatchte Hauptkanäle und Same-Channel-Restrikes.

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

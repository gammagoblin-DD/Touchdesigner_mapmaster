# TouchDesigner MapMaster

Professionelles, modulares TouchDesigner-System für Projection Mapping, VJ-Visuals, Audioanalyse und shaderbasierte Echtzeiteffekte.

## Aktuelle Version

**MapMaster v1.1.1 – V49Z0 Current Project Handover**

TouchDesigner-Build:

```text
2025.32460
```

Milestone:

```text
MAP_MASTER_V49Z0_CURRENT_PROJECT_HANDOVER_DEEP_EXPORT_07.08.2026_04-49-26.zip
```

## Verifizierter Projektstatus

- 0 Fehler und 0 Warnungen im V49Z0-Deep-Export
- 451 Runtime-Samples ohne Ausfall
- 56,31 FPS während des 45-Sekunden-Referenzlaufs
- aktueller Router-Snapshot auf FX11 dokumentiert
- akzeptierter FX03-Lightning-Checkpoint bleibt erhalten
- native Shaderbank FX04 bis FX11 dokumentiert
- neues Übergabedossier und Masterprompt für nahtlosen Neustart in frischem Chat

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
└─ TD_CODEX_BRIDGE
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
docs/RELEASE_NOTES_v1.1.1.md
docs/v1.1.1/PROJECT_DOSSIER_V49Z0.md
docs/v1.1.1/MASTERPROMPT_V49Z0.txt
docs/v1.1.1/VERIFY_REPORT_V49Z0.json
releases/v1.1.1/MAP_MASTER_V49Z0_CURRENT_PROJECT_HANDOVER_DEEP_EXPORT_*.zip
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

V47A3 bleibt der akzeptierte, stilisiert-realistische und live-taugliche
Lightning-Checkpoint. Der neue V49Z0-Handover konserviert diesen Stand und
dokumentiert die Regeln für Folgearbeit in einem frischen Chat.

### FX04 bis FX11 – Native Shaderbank

Die aktuelle Projektlinie enthält eine native Shaderbank mit dokumentierten
Effekten von Mapping Master über Physarum/Saber-Varianten bis Electric Contour
Arcs und Clean Pack.

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

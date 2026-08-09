# Changelog

Alle wichtigen Änderungen dieses Projekts werden hier dokumentiert.

Das Projekt orientiert sich an Semantic Versioning.

## [1.1.0-pre-cleanup] – 09.08.2026

### Checkpoint

- aktueller Projektstand vor neuen Features und Aufräumarbeiten gesichert
- Stand basiert auf `GG_POST_GG_V49D2R3_FX08_UNROLLED_EXTRACTED_PATH_RESERVED_WORD_FIX_09.08.2026_03-06-50.1.toe`
- V49Z2 Deep Export als Analyse- und Handover-Basis referenziert
- Projektziel als modulares, audioreaktives Mapping-/Live-Visual-Instrument dokumentiert

### Current State

- Router läuft im Expression-Modus über `null_CONTROL_BUS['fx_index']`
- aktiver Router-Index im V49Z2-Export: `4` / `FX04_MAPPING_MASTER`
- finaler Output: 1920 × 1080, RGBA16F
- Audio-Master-Bus vorhanden: `null_AUDIO_MASTER_FEATURES_V27`
- FX08 ist bei `GG_V49D2R3` geparkt: technisch lauffähig, visuell nicht final

### Known Next Architecture Work

- Input-/Maskenstruktur muss bereinigt werden
- normale Stage-Fotos sollen ohne transparenten Hintergrund funktionieren
- Pink-/NoAnim-Maske soll offizielle Begrenzungs- und Kantenreferenz werden
- doppelte Input-Nodes und unklare Previews müssen reduziert werden
- Network-Boxes müssen logisch, farbig und überlagerungsfrei angeordnet werden
- Erweiterbarkeit für mehrere Beamer, flexible Audioanalyse und spätere UI muss berücksichtigt werden

## [1.0.0] – 19.07.2026

### Added

- stabile TouchDesigner-Produktionsbasis
- portable `gg://`-Projektpfade
- modulare Projektstruktur
- zentraler Audio-Analyzer
- FX-Router
- Control-Bus
- Master-Output-Pipeline
- Bridge-Workflow
- Deep-Export-System
- Audit- und Verify-Workflow
- Git-LFS-Unterstützung für `.toe` und `.tox`

### Fixed

- alle bekannten Operatorfehler
- alle bekannten Warnungen
- alle Node-Überlappungen
- Script-CHOP-Cook-Loops
- nicht-finite Audio- und Tempo-Werte
- fehlerhafte Time-Slice-Ausgabe
- unvollständige Input-, Router- und Output-Signalwege
- unnötiges Cooking von Archiv- und Test-COMPs
- Layoutprobleme in Audio, FX00, FX01, FX02 und FX03

### Verified

- `GLOBAL_ERRORS=0`
- `GLOBAL_WARNINGS=0`
- `PROJECT_OVERLAPS=0`
- `TOPOLOGY_UNCHANGED=TRUE`
- `NODE_SIZES_UNCHANGED=TRUE`
- `PARAMETER_STRUCTURE_UNCHANGED=TRUE`
- `CODE_SHADER_CALLBACK_CONTENT_UNCHANGED=TRUE`
- `ARCHIVES_COOKING_DISABLED=TRUE`
- `FX01_OUTPUT=OK`
- `FINAL_OUTPUT=OK`

### Milestone

```text
GG_POST_MAP_MASTER_V39E2_FINAL_CLEANUP_19.07.2026_10-54-59.toe
```

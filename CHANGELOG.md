# Changelog

Alle wichtigen Änderungen dieses Projekts werden hier dokumentiert.

Das Projekt orientiert sich an Semantic Versioning.

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

# Changelog

Alle wichtigen Änderungen dieses Projekts werden hier dokumentiert.

Das Projekt orientiert sich an Semantic Versioning.

## [1.1.0] – 07.08.2026

### Added

- produktiver FX03-Lightning-Storm auf V47A3
- kausaler Beat-Lock mit absoluter Audioqualifikation
- echte ungeclampte BPM-Auslesung einschließlich 200-BPM-Tempo-Debug
- strikt vorwärtslaufende, selbstvermeidende Blitzgeometrie
- gelatchte Hauptkanäle und Same-Channel-Restrikes
- aperiodische Mehrskalen-Tortuosität und Leitfähigkeitsvariation
- vollständiges Projektdossier und Übergabeprotokoll
- V47Z0-Deep-Export mit TOE-, TOX-, Quellcode-, Runtime- und Health-Daten
- Git-LFS-Unterstützung für Deep-Export-ZIP-Dateien

### Fixed

- BPM-Werte wurden zuvor durch einen 0..1-Featureleser begrenzt und fielen auf
  ein falsches 120-BPM-Raster zurück
- spiralförmige, geschlossene und rückläufige Blitzpfade
- Pop-up-Äste ohne klare Hauptstranghierarchie
- regelmäßige Dreier-Treppen in der finalen Pfadverfeinerung
- zu geringe und musikalisch invertierte Blitzdichte

### Verified

- `GLOBAL_ERRORS=0`
- `GLOBAL_WARNINGS=0`
- `RUNTIME_SAMPLES=451`
- `RUNTIME_SAMPLE_FAILURES=0`
- `RUNTIME_EFFECTIVE_FPS=58.316`
- `ROUTER_SELECTED_INPUT=FX03`
- `AUDIO_NON_FINITE_VALUES=0`
- `REQUIRED_TOX_EXPORTS_FAILED=0`
- `DEEP_EXPORT_SHA256=caf5fef27d95eed6299ea12f648c4d33e08b8f82b40a12d96ab4fff11427585a`

### Milestone

```text
GG_POST_GG_V47A3_APERIODIC_MULTISCALE_DISCHARGE_POLISH_07.08.2026_00-32-53.1.toe
```

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

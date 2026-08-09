# TouchDesigner MapMaster

Modulares TouchDesigner-System für Projection Mapping, Live-Visuals, Audioanalyse und shaderbasierte Echtzeiteffekte.

## Aktueller Git-Checkpoint

**MapMaster v1.1.0-pre-cleanup – vor neuen Features / Aufräumen**

TouchDesigner-Build:

```text
2025.32460
```

Maßgeblicher Projektstand:

```text
GG_POST_GG_V49D2R3_FX08_UNROLLED_EXTRACTED_PATH_RESERVED_WORD_FIX_09.08.2026_03-06-50.1.toe
```

Deep-Export-Referenz:

```text
MAP_MASTER_V49Z2_FULL_PROJECT_ERROR_AUDIT_DEEP_EXPORT_09.08.2026_03-11-37
```

## Projektidee

MAP_MASTER soll ein audioreaktives, maskenbasiertes Live-Visual-Instrument werden.
Ein normales Foto der Mappingfläche wird mit einer Pink-/NoAnim-Maske und Analyse-Maps kombiniert.
Darauf bauen mehrere Effekte auf, die live über Router und Control-Bus geschaltet oder später kombiniert werden können.

Langfristige Ziele:

- flexible Updates für Effekte, Audioanalyse, Router und Output
- normale Inputfotos ohne zwingenden transparenten Hintergrund
- Pink = nicht animieren / Kantenreferenz / Schutzbereich
- stabiler Audio-Master-Bus als Vertrag zwischen Analyzer und Effekten
- modular abschaltbare Effekte für Performance
- vorbereitet für mehrere Beamer / Output-Ziele
- spätere Master-UI und Effekt-Dashboards
- portable `gg://`-Projektpfade

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
└─ 07_OUTPUT
```

## Aktueller technischer Status aus V49Z2

- Deep Export: vollständig
- Runtime-Samples: 451
- Effektive FPS: ca. 54.54
- Projektfehler: 0
- Warnungen: 0
- Overlaps: 0
- Router-Modus: Expression
- aktiver Router-Index im Export: 4 (`FX04_MAPPING_MASTER`)
- finaler Output: 1920 × 1080, RGBA16F
- Audio-Master-Bus: `/project1/MAP_MASTER/03_AUDIO/null_AUDIO_MASTER_FEATURES_V27`

## Effektbank

```text
FX00 Bypass
FX01 Slime Mask
FX02 Orbiting 3D Lights
FX03 Lightning Storm
FX04 Mapping Master
FX05 Shadertoy Surface
FX06 Physarum Surface
FX07 Saber Outline
FX08 Saber Path
FX09 Orbiting Relief Lights
FX10 Electric Contour Arcs
FX11 Clean Pack
```

## Aktuelle Arbeitsregeln

- Vor riskanten Änderungen read-only Audit oder Deep Export durchführen.
- PRE-/POST-Saves erzeugen.
- Keine alte TOX/TOE-Struktur direkt einbetten; alte Dateien nur als Referenz/Shaderquelle nutzen.
- Keine Effektshader blind umbauen, wenn Router/Input/Mask/Audio die eigentliche Ursache sein können.
- Keine neuen Nodes ohne Cleanup-Plan.
- Altlasten entfernen oder klar als Legacy/Fallback gruppieren.
- Keine Node-Überlagerungen.
- Network Boxes logisch benennen, farblich trennen und sauber layouten.
- Inaktive Effektketten perspektivisch vom aktiven Cook-Pfad trennen.
- Audioeffekte nur an stabile Audio-Bus-Kanäle koppeln, nicht an Analyzer-Interna.

## Aktuell erkannter nächster Architekturfehler

Die produktive Maske wird aktuell primär aus dem Alpha-Kanal des Inputbildes abgeleitet.
Das ist für den gewünschten Workflow falsch, weil normale Fotos ohne transparenten Hintergrund dann komplett animierbar werden.

Gewünschte Zielstruktur:

```text
normales Stage-Foto
+ Pink-/NoAnim-Maske
→ NoAnim-Maske
→ AnimAllowed-Maske
→ Edge-/Kantenreferenz
→ Effekte
```

Dieser Git-Checkpoint wurde bewusst vor dem nächsten Feature-/Cleanup-Umbau gespeichert.

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

## Lizenz

Noch nicht festgelegt.

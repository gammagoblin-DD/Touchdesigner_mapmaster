# MAP_MASTER V49Z0 – Projektdossier und Übergabeprotokoll

## 1. Zweck dieses Dokuments

Dieses Dokument ist für die Übergabe in einen komplett neuen ChatGPT/Codex-Chat gedacht. Es fasst den aktuellen technischen Stand, die Historie der zentralen Eingriffe, die Architektur, die Shaderbank, die Lightning-Erkenntnisse und die operativen Regeln so zusammen, dass ohne Vorwissen nahtlos weitergearbeitet werden kann.

Dieses Dossier beschreibt den Stand am 7. August 2026. Maßgeblicher aktueller Arbeitsstand ist die V49-Linie nach Integration der nativen Shaderbank, kontrollierter Bereinigung und technischem Visual-Polish.

## 2. Projektziel

`MAP_MASTER` ist ein modularer TouchDesigner-Echtzeitbaukasten für visuelle Effekte auf Basis von:

- Bild-/Video-Input
- Maskierung
- Bildanalyse
- Audioanalyse
- Effektbank
- Router/Output
- kontrollierter Bridge-Ausführung für externe Patches

Wichtige Zielvorgabe des Projekts:

- Live- und festivaltaugliche, performante, stabile visuelle Effekte
- kontrollierte, versionierte Patch-Ausführung über die TD-Bridge
- saubere Alpha-/Masken-Semantik
- konsistente Audioanbindung
- keine ungeprüften Schnellschüsse direkt im Live-Netz

## 3. Maßgeblicher aktueller Stand

Der aktuelle relevante Projektstand ist nicht mehr die frühe FX03-only-Phase, sondern die spätere V49-Projektlinie:

- `V47A3` bleibt der akzeptierte stabile Lightning-Checkpoint für `FX_03_LIGHTNING_STORM`
- `V49A1R1` integrierte eine native Shaderbank für `FX04` bis `FX11`
- `V49A2R2` bereinigte historisch überflüssige Knoten kontrolliert und referenzgesichert
- `V49B0R1` führte einen gezielten technischen Visual-Polish für problematische Effekte durch

Wesentlicher Status:

- Das Projekt ist technisch gesund
- Router-Topologie mit 12 Slots ist vorhanden
- Canonical Audio ist angebunden
- Alte Debug-/Archiv-/Legacy-Knoten wurden weitgehend entfernt
- Der Lightning-Effekt `FX03` wurde nicht durch die V49-Arbeiten zerstört
- Mehrere neue Shader-Effekte sind als native Projektbestandteile integriert

## 4. Harte Projektinvarianten

Diese Regeln dürfen in einem neuen Chat nicht stillschweigend verletzt werden:

1. `FX_03_LIGHTNING_STORM` ist ein akzeptierter stabiler Checkpoint und darf nicht ohne konkrete Evidenz neu umgebaut werden.
2. Die alte `.tox`- oder `.toe`-Quelle aus `v0.3` darf nicht als eingebettete Altstruktur in das neue Projekt geladen oder referenziert werden.
3. Nur Shaderlogik und verwertbare Look-Ideen aus Altständen dürfen adaptiert werden.
4. Bridge-Patches laufen kontrolliert über `text_RUN_PENDING`.
5. Pro Lauf genau ein Patch, sofern die Bridge nicht explizit als Batch-System umgebaut wurde.
6. Vor destruktiven Strukturänderungen immer PRE-Checkpoint und danach Report/POST-TOE prüfen.
7. Alpha-Verträge, Output-Auflösung und Router-Topologie sind nicht optional.
8. Audio-Reaktivität muss messbar und visuell sinnvoll sein, nicht nur numerisch > 0.

## 5. Hauptarchitektur

Aktive Hauptstruktur im Projekt:

1. `/project1/MAP_MASTER/00_INPUT`
2. `/project1/MAP_MASTER/01_MASK`
3. `/project1/MAP_MASTER/02_ANALYSIS`
4. `/project1/MAP_MASTER/03_AUDIO`
5. `/project1/MAP_MASTER/04_FX`
6. `/project1/MAP_MASTER/05_ROUTER`
7. `/project1/MAP_MASTER/06_CONTROL`
8. `/project1/MAP_MASTER/07_OUTPUT`
9. `/project1/TD_CODEX_BRIDGE`

Funktionsbedeutung:

- `00_INPUT`: Medien-/Testinput
- `01_MASK`: erlaubte Bildregionen / Schutzmaske
- `02_ANALYSIS`: Tiefe, Normals, Contours, weitere Analyse-Outputs
- `03_AUDIO`: Audio-Feature-Extraktion
- `04_FX`: Effektmodule
- `05_ROUTER`: Effektwahl und Weiterleitung
- `06_CONTROL`: Control-Bus und Router-Steuerlogik
- `07_OUTPUT`: finale Ausgabe
- `TD_CODEX_BRIDGE`: externer Patch-Runner

## 6. Bridge- und Patch-Modell

Zentrale operative Realität:

- Externe Änderungen werden als Python-Patches in die Bridge-Inbox gelegt
- Arbeitsordner für auszuführende Scripte:
  `D:\Desktop\td-bridge\outputs\td_bridge\inbox`
- Ausführung erfolgt über:
  `/project1/TD_CODEX_BRIDGE/text_RUN_PENDING`
- Ergebnisse landen in:
  - `outputs/reports`
  - `outputs/saves`
  - `outputs/td_bridge/done`
  - `outputs/td_bridge/failed`
  - `outputs/deep_exports`

Frühere Fehlerquelle:

- Wenn `text_RUN_PENDING` "nichts tut", liegt häufig entweder ein Pfadproblem, ein Queue-/Batch-Statusproblem oder ein Script vor, das im Bridge-Kontext nicht sauber initialisiert.

## 7. Lightning-Entwicklung und Erkenntnisse

`FX_03_LIGHTNING_STORM` war ein langer eigener Forschungsstrang. Wichtige Erkenntnisse:

### 7.1 Frühe Fehlbilder

Frühere Versionen litten unter:

- spiralförmigen oder aufgerollten Ästen
- rückläufigen oder sich zurückrollenden Pfaden
- zu geraden, mechanischen Leitern
- Pop-up-Ästen ohne erkennbaren Hauptstrang
- unnatürlicher Gleichförmigkeit
- Beat-Reaktivität ohne glaubwürdige Blitzdynamik

### 7.2 Zielbild für Lightning

Das gewünschte visuelle Modell wurde klar definiert als:

- ein Hauptblitzstrang als primäre Kausalstruktur
- optionale Verästelungen nur nachgeordnet
- BAM-artiger sichtbarer Hauptimpuls
- organisches Abklingen
- Restrikes auf demselben Kanal statt kompletter Neuaufbau-Illusion
- verschiedene Richtungen, Intensitäten und Verästelungsgrade
- rhythmisch plausibel zum Beat, aber nicht mechanisch getaktet

### 7.3 Wichtige technische Durchbrüche

Entscheidende Lightning-Fortschritte:

- streng vorwärtslaufende Kanal-/Pfadlogik
- Ausschluss von Loops und Spiralfehlern
- Hauptstrang-Hierarchie vor Astbildung
- entkoppelte restrike-fähige Eventlogik
- echter BPM-Fix in V47A2

### 7.4 BPM-Erkenntnis

Eine zentrale frühere Fehlannahme war die falsche BPM-Auslesung. Der echte BPM-Wert durfte nicht über eine 0..1-normalisierte Leselogik geklemmt werden. Diese Klammerung führte zu falscher oder permanenter Fallback-Logik. In `V47A2` wurde das korrigiert.

### 7.5 Aktueller Lightning-Status

`FX03` ist als stabiler Lightning-Checkpoint akzeptiert. Neue Chats sollen ihn nicht reflexhaft neu erfinden, sondern nur bei belegter Regression oder klar neuem Zielbild anfassen.

## 8. V49-Projektlinie: struktureller Umbau

Die V49-Linie war kein reines Look-Tuning, sondern ein größerer Projektumbau.

### 8.1 V49A0

Read-only-Audit und Shader-Extraktion aus der alten `v0.3`-Quelle.

Wichtige Regel:

- Altmaterial nur als Shader-/Referenzquelle
- keine direkte Altprojekt-Einbettung

### 8.2 V49A1R1

Rename-safe Integration der neuen nativen Shaderbank.

Wichtige Eigenschaften:

- Legacy-TOX wird nicht geladen oder eingebettet
- sechs verifizierte GLSL-Quellen wurden SHA-256 geprüft
- zwei netzabhängige Legacy-Looks wurden als native One-Pass-Shader neu aufgebaut
- `FX04` wurde nur ersetzt, nachdem der staged Nachfolger sauber kompiliert und validiert war
- Ziel war ein sauberer 12-Slot-Router mit einheitlicher Audio-/Input-Struktur

### 8.3 V49A2R2

Historisch gespeicherte Altlasten und obsolete Nodes wurden referenzgesichert entfernt.

Wichtiger Effekt:

- 30 Root-Kandidaten bzw. 78 Operatoren wurden entfernt
- zwei alte V39-Storage-Snapshots wurden als historisch, nicht live-relevant identifiziert
- Produktionsstruktur wurde schlanker
- Projektgesundheit blieb erhalten

### 8.4 V49B0R1

Gezielter technischer Visual-Polish für problematische Effekte:

- `FX05`
- `FX06`
- `FX07`
- `FX08`
- `FX10`

Nicht verändert:

- `FX04`
- `FX09`
- `FX11`
- Router-Topologie
- Audio-Topologie
- Mask-/Output-Topologie

## 9. Aktuelle Shaderbank

Nach V49A1R1 existiert eine aktive Bank für die Indizes 4 bis 11:

### FX04

- Name: `FX_04_MAPPING_MASTER`
- Rolle: Mapping Master
- Quelle: verifizierte extrahierte Shaderbasis
- Status: erhalten, nicht durch V49B0R1 verändert

### FX05

- Name: `FX_05_SHADERTOY_SURFACE`
- Look-Ziel nach V49B0R1: holografische Scanfläche
- Problem vor Polish: zu ähnlich zu FX04
- Status: technisch valide, visueller Distanzgewinn implementiert

### FX06

- Name: `FX_06_PHYSARUM_SURFACE`
- Look-Ziel: emissive, organische Physarum-/Vein-Struktur
- Problem vor Polish: eher Flächenflackern als lesbares Netzwerk
- Status: technisch valide, Look stärker Richtung Ader-/Netzlesbarkeit geschoben

### FX07

- Name: `FX_07_SABER_OUTLINE`
- Look-Ziel: edge-only, source-preserving outline
- Problem vor Polish: starkes sichtbares Clipping
- Status: technischer Highlight-/Clipping-Schaden deutlich reduziert

### FX08

- Name: `FX_08_SABER_PATH`
- Look-Ziel: travelling path entlang Kanten
- Problem vor Polish: kein kohärenter wandernder Pfad
- Status: technisch auf sparse travelling packets umgebaut

### FX09

- Name: `FX_09_ORBITING_RELIEF_LIGHTS`
- Rolle: Relief-/Orbiting-Light-Effekt
- Status: von V49B0R1 bewusst nicht verändert

### FX10

- Name: `FX_10_ELECTRIC_CONTOUR_ARCS`
- Look-Ziel: explizite elektrische Konturbögen
- Problem vor Polish: Energie und Arc-Lesbarkeit zu schwach
- Status: technisch verbessert, aber noch visuell verdächtig unter finaler Wahrnehmungsprüfung

### FX11

- Name: `FX_11_CLEAN_PACK`
- Rolle: Clean-Pack / Mode-Bank
- Status: erhalten, nicht durch V49B0R1 verändert

## 10. Audio-System

Aktiver kanonischer Audio-Pfad:

- `/project1/MAP_MASTER/03_AUDIO/null_AUDIO_MASTER_FEATURES_V27`

Wichtige erwartete Kanäle aus der V49-Linie:

- `kick_smooth`
- `kick_pulse`
- `bass_body`
- `high_detail`
- `section_energy`
- `fx_pulse`
- `tempo_bpm`
- `tempo_confidence`

Wichtige Lehre:

- technische Audio-Reaktion ist nicht identisch mit guter visueller Audio-Reaktion
- ein Effekt kann Messwerte bestehen und trotzdem musikalisch schwach wirken

## 11. Router-Status und aktuelles Risiko

Technisch validierter Stand aus `V49B0R1`:

- 12 korrekte Router-Inputs
- 1920x1080 Output-Vertrag
- keine Projektfehler oder Warnungen im Prüflauf
- Router wurde unverändert konserviert

Wichtiger operativer Hinweis:

Der Router wurde in `V49B0R1` bewusst nicht umgestellt, sondern exakt in seinem damaligen Zustand erhalten. Dabei war der aktive Zustand laut Prüfung:

- aktiver Index: `11`
- aktiver Mode: `CONSTANT`

Das bedeutet:

- die zentrale `fx_index`-Buslogik steuert den Router in diesem konservierten Zustand nicht zwingend live
- eine neue Chat-Session darf nicht einfach annehmen, dass der Router bereits wieder im echten Expression-/Bus-Modus hängt

Dieses Thema ist ein bekannter Folgeschritt für Live-Bedienbarkeit.

## 12. Technisch bestätigte V49B0R1-Ergebnisse

Bestätigt durch den letzten bekannten technischen Prüfstand:

- Erfolgsmeldung und POST-TOE vorhanden
- modifiziert: `FX05, FX06, FX07, FX08, FX10`
- erhalten: `FX04, FX09, FX11`
- alle getesteten Shader ohne GLSL-Compilefehler
- alle getesteten Outputs endlich
- Alpha-Vertrag eingehalten
- Highlight-Clipping für `FX07` deutlich reduziert

Wichtige Einordnung:

Diese technische Validierung beweist Funktionsfähigkeit, aber nicht automatisch perfekte Wahrnehmungsqualität auf Show-Niveau.

## 13. Noch offene qualitative Risiken

Trotz technischem Erfolg bleiben aus Übergabesicht drei inhaltliche Risiken:

1. `FX07`, `FX08` und besonders `FX10` könnten musikalisch/visuell noch zu schwach oder zu wenig eindeutig sein.
2. Der Router ist konserviert, aber nicht sicher auf finalem Live-Control-Bus-Mode.
3. Für die neue Shaderbank fehlt noch ein wirklich abschließender wahrnehmungsorientierter Video-QA-Durchlauf über alle relevanten Indizes.

## 14. Was ein neuer Chat zuerst tun soll

Ein neuer Codex-Chat soll nicht sofort patchen, sondern diese Reihenfolge einhalten:

1. Handover-Dokumente lesen
2. Deep-Export entpacken und Struktur prüfen
3. Aktuelle Topologie bestätigen
4. Router-Zustand prüfen
5. Nur dann entscheiden, ob read-only Audit oder neuer Patch nötig ist

## 15. Was ausdrücklich nicht wiederholt werden soll

- Lightning ohne Evidenz komplett neu bauen
- alte `.tox`-/`.toe`-Logik direkt einbinden
- Audio-Reaktivität nur an einem numerischen Delta festmachen
- Router-/Control-Bus-Zustand annehmen statt messen
- mehrere große Risiken gleichzeitig in einem Patch mischen
- erst optisch "verbessern" und danach technische Basis prüfen

## 16. Empfohlene Artefakte für die neue Session

Die neue Session soll mindestens diese Dinge nutzen:

- dieses Dossier
- das Masterprompt
- den neuen Read-only-Deep-Export
- den zuletzt erzeugten POST-TOE-Checkpoint
- die zugehörigen Reports/Last-Status-Dateien
- ein frisches Video mit Audio, falls visuelle QA weitergehen soll

## 17. Konkrete Wiederanlaufstrategie

Wenn in der neuen Session direkt weitergearbeitet werden soll, ist die pragmatische Reihenfolge:

1. aktuellen Deep Export lesen
2. Router/Control-Bus prüfen
3. `FX05/06/07/08/10` per Video mit Audio wahrnehmungsorientiert bewerten
4. nur bei klaren Defiziten einen kleinen, isolierten Patch bauen
5. danach wieder Report, POST-TOE und Video prüfen

## 18. Kurzfazit

Der Projektstand ist deutlich reifer als in den frühen Lightning-Iterationsphasen. Die wichtigste Verschiebung ist:

- `FX03` gilt als akzeptierter, stabiler Lightning-Baustein
- die Arbeit hat sich auf die neue native Shaderbank und die Projektgesundheit ausgeweitet
- das Projekt ist technisch sauberer, modularer und besser übergabefähig

Der neue Chat soll diesen Stand als belastbare technische Basis behandeln, nicht als offenen Totalumbau.

# MAP_MASTER – tiefes Projektdossier

## 1. Dokumentstatus

- Übergabestand: **V47A3 – APERIODIC MULTISCALE DISCHARGE POLISH**
- Entscheidung: **als stabiler Lightning-Checkpoint angenommen**
- Zielsystem: TouchDesigner 2025.32460, Windows, NVIDIA
- Geladene Projektdatei beim Export: `D:\Desktop\td-bridge\outputs\saves\GG_POST_GG_V47A3_APERIODIC_MULTISCALE_DISCHARGE_POLISH_07.08.2026_00-32-53.1.toe`
- Referenz-Checkpoint: `GG_POST_GG_V47A3_APERIODIC_MULTISCALE_DISCHARGE_POLISH_07.08.2026_00-32-53.toe`
- Exportzeit: `2026-08-07T00:46:48+02:00`
- Exportmodus: read-only; keine Netzwerk-, Parameter- oder Speicheränderung

## 2. Projektziel und Arbeitsweise

MAP_MASTER ist ein modularer, audio- und maskenreaktiver Echtzeit-Visualbaukasten.
Die Hauptkette ist in Eingabe, Maskenerzeugung, Analyse, Audio, Effekte,
Routing/Output und Diagnose gegliedert. Änderungen werden über
`/project1/TD_CODEX_BRIDGE/text_RUN_PENDING` als einzeln versionierte Python-
Patches ausgeführt. Jeder erfolgreiche Patch erzeugt einen POST-TOE-Checkpoint
und maschinenlesbare Reports. Die Bridge-Inbox soll bei kontrollierten Läufen
genau einen Patch enthalten.

## 3. Architektur

1. `/project1/MAP_MASTER/00_INPUT` – Bild-/Videoeingaben und Testquellen.
2. `/project1/MAP_MASTER/01_MASK` – Objekt-/Alpha-Masken und Schutzbereiche.
3. `/project1/MAP_MASTER/02_ANALYSIS` – Luma, Kanten, Gradienten, Normalen,
   Distanz-/AO-/Kurvatur-Proxys und gepackte Analyseinformationen.
4. `/project1/MAP_MASTER/03_AUDIO` – File-/Live-Audio, Goldclass-Features,
   Kick/Onset/Bass/Energie, Abschnittssignale und Tempo-Debug.
5. `/project1/MAP_MASTER/04_FX` – unabhängige Effektmodule. Aktueller
   Abschlussfokus ist `FX_03_LIGHTNING_STORM`.
6. `/project1/MAP_MASTER/05_ROUTER` und Outputpfade – Effektauswahl und finale
   Ausgabe.
7. `/project1/TD_CODEX_BRIDGE` – kontrollierte Patchausführung, Done/Failed-
   Lifecycle, Status und Logs.

Das vollständige Operator-, Parameter- und Verbindungsmodell befindet sich in
`04_inventory`, `05_connections` und `06_architecture` dieses Pakets.

## 4. FX03 – eingefrorener Lightning-Stand

### 4.1 Kritische Pfade

- Effektwurzel: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM`
- Aktiver Eventcontroller: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/execute_FX03_V47A2_TRUE_TEMPO_FRACTAL_CHANNEL`
- Geodesischer Pfadshader: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/text_FX03_V43C21_MASK_GEODESIC_PATH_SHADER`
- Mehrskalen-Refinement: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/text_FX03_V43C26_ORGANIC_SPLINE_REFINE_SHADER`
- Leader-/Return-Stroke-Renderer: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/text_FX03_LEADER_RENDER_SHADER_V43C2`
- Telemetrie: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/text_FX03_V47A2_AUDIO_TELEMETRY`
- Finaler FX-Ausgang: `/project1/MAP_MASTER/04_FX/FX_03_LIGHTNING_STORM/null_FX03_OUT`

### 4.2 Visuelles Modell

Jedes neue Ereignis besitzt einen gelatchten Hauptkanal. Der Pfad wächst mit
streng positiver Vorwärtsprojektion, wodurch Rückläufe, geschlossene Schleifen
und frühere Spiralfehler konstruktiv ausgeschlossen werden. Optionale Äste
entstehen erst, nachdem der Hauptleader ihren Ansatzpunkt erreicht hat. Der
Return Stroke erzeugt den dominanten BAM. Restrikes verwenden denselben Kanal,
anstatt die Geometrie sichtbar neu aufzubauen. V47A3 ersetzt regelmäßige
Dreier-Zickzackgruppen durch incommensurate, strike-stabile Mehrskalenvariation
und ergänzt eine dezente Leitfähigkeitsvariation der Strangdicke.

### 4.3 Audiomodell

Die Ereignisberechtigung beruht auf absolut messbarer Audioenergie plus
qualifizierten Kick-, Beat-, Onset-, Novelty- oder Drop-Flanken. Tempo wird in
V47A2 bewusst **nicht** durch den normalisierten 0..1-Featureleser geführt.
Gültige BPM-Kanäle werden ungeclamped gelesen; `tempo_debug_fallback_bpm`
liefert beim Referenztrack 200 BPM. Lautheit steuert Dichte und Intensität,
während neue Geometrie weiterhin nur an kausalen Transienten beginnt.

### 4.4 Abnahmebefund

- Lange V47A2-Referenzaufnahme: 46,43 Sekunden, 40 erkannte Flash-Peaks.
- 85 % aller Peaks lagen bereits in der Gesamtaufnahme innerhalb von 250 ms
  eines Audio-Onsets; stille/ruhige Vorlaufbereiche sind darin enthalten.
- Aktive Musikabschnitte erzeugten ungefähr 1,1–1,2 neue Blitze pro Sekunde.
- V47A3 behielt Controller und Ereignisdichte unverändert.
- Keine Spiralen, geschlossenen Pfade oder rückläufiges Aufrollen beobachtet.
- BAM, schnelles organisches Abklingen und Same-Channel-Restrikes bestätigt.
- Resultat ist ein stilisiert-realistischer, transparenter, live-tauglicher
  Lightning-Layer; er ist kein physikalischer Atmosphären-/Wolken-Simulator.

## 5. Versionschronik und Erkenntnisse

- V44B0–V44D2: Festivalaufbau und direkte Audioreaktivität; optisch entstanden
  Pop-up-Äste, rückläufige Pfade und unklare Hauptstranghierarchie.
- V44E0: forensischer Audio-/Lightning-Deep-Export.
- V44F0: Trigger-/Renderhierarchie korrigiert; Geometrie blieb uniform.
- V45A0/V45A1: Natural-Discharge-Neustart und Deadlock-Recovery.
- V46A0: Beatstorm-Rebuild; GLSL-Reparaturen nötig, Form weiterhin unnatürlich.
- V47A0: kausaler Beat-Lock und selbstvermeidende, strikt vorwärtslaufende
  Entladung; Loop-/Spiralproblem gelöst.
- V47A1: absolute Audioqualifikation, Dichtegesetz und stärkere Tortuosität.
- V47A2: entscheidender BPM-Fix – normalisierte Lesefunktion hatte echte BPM
  auf 1.0 begrenzt und permanent den 120-BPM-Fallback ausgelöst.
- V47A3: rein optischer, aperiodischer Mehrskalen-Polish; Timing unverändert.

## 6. Unveränderliche Sicherheitsregeln

1. V47A3 zuerst als Checkpoint sichern; niemals direkt überschreiben.
2. Keine Änderung am BPM-Leser zurück zu `_maximum()` oder einer 0..1-Klemme.
3. Keine zeitabhängigen Expressions auf den vom Controller gelatchten Constant-
   Parametern reaktivieren.
4. Neue Äste dürfen nicht vor Erreichen ihres Hauptstrang-Ankerpunkts sichtbar
   werden.
5. Geometrie muss in der globalen Fortschrittsachse monoton bleiben.
6. Restrikes dürfen Topologie und Seed innerhalb eines Kanals nicht wechseln.
7. Pro Bridge-Lauf genau ein Patch; danach Report, Status und POST-TOE prüfen.
8. Keine neuen GPU-Pässe ohne gemessenen Nutzen und Performancevergleich.

## 7. Performance und Live-Betrieb

Der Export enthält Start-/End-Cook-Snapshots und einen 45-Sekunden-Mitschnitt
unter `14_performance_runtime`. Effektive Export-FPS:
`58.315512213407736`. Runtime-Samples:
`451`. Neue Strukturänderung während des
Exports: `True`. Projektfehler, Warnungen und
Overlaps werden als Diagnosewerte exportiert und sind nicht automatisch dem
FX03-Modul zuzuordnen.

## 8. Wiederherstellung

Primärer Rollback ist die gespeicherte POST-TOE-Datei. Zusätzlich enthält das
Paket eine Kopie der aktuell gespeicherten TOE sowie Live-TOX-Exporte der
zentralen Komponenten. Bei Abweichungen zwischen TOE und Livezustand haben die
TOX-Exporte diagnostischen Vorrang, da die TOE-Kopie nur den letzten
gespeicherten On-Disk-Stand abbildet.

## 9. Nächster Arbeitsauftrag

FX03 nicht weiter verändern, solange keine konkrete neue Abweichung mit Video,
Audio und Report belegt ist. Für den nächsten Effekt zuerst dessen bestehende
COMP, Ein-/Ausgänge, Masken-, Analyse- und Audiokanäle read-only inventarisieren.
Danach einen kleinen aktivierbaren Baseline-Patch erstellen, technische
Funktion prüfen und erst anschließend Lookentwicklung beginnen.

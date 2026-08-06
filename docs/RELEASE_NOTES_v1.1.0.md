# MapMaster v1.1.0 – V47A3 Lightning Checkpoint

## Überblick

Version 1.1.0 erweitert die stabile Produktionsbasis um den abgenommenen
FX03-Lightning-Storm. Der Effekt verbindet kausale Audioreaktivität mit einer
klaren Hauptstranghierarchie, strikt vorwärtslaufender Geometrie und
aperiodischer Mehrskalenvariation.

## Wichtigste Änderungen

- echter 200-BPM-Tempo-Lock ohne 0..1-Clamping
- neue Kanäle nur auf qualifizierten Audioflanken
- unterschiedliche Richtungen, Intensitäten und Astklassen
- gelatchte Geometrie für natürliche Restrikes
- keine beobachteten Spiralen oder rückläufigen Pfade
- schneller BAM und organisches Abklingen
- keine zusätzlichen GPU-Pässe in V47A2/V47A3

## Technische Verifikation

Der V47Z0-Abschlussexport erfasste 45 Sekunden Livebetrieb:

```text
Runtime-Samples: 451
Sample-Ausfälle: 0
Effektive FPS: 58.316
Projektfehler: 0
Projektwarnungen: 0
Audio-NaN/Inf: 0
Router: FX03, ohne Wechsel
```

Die acht dokumentierten Node-Overlaps sind Netzwerkeditor-Layoutwerte und
keine Signal-, Compile- oder Runtimefehler. Der Struktur-Fingerprint änderte
sich ausschließlich durch erwartbare laufende Audio-, Seed- und
Eventparameter; die Operatorzahl blieb bei 551.

## Enthaltene Artefakte

```text
project/MAP_MASTER_v1.1.0.toe
docs/v1.1.0/PROJECT_DOSSIER_V47A3.md
docs/v1.1.0/HANDOVER_PROTOCOL_V47A3.md
docs/v1.1.0/V47A3_ACCEPTANCE_RECORD.json
docs/v1.1.0/VERIFY_REPORT_V47Z0.json
releases/v1.1.0/MAP_MASTER_V47Z0_FINAL_HANDOVER_DEEP_EXPORT_*.zip
```

## Integrität

```text
SHA256: caf5fef27d95eed6299ea12f648c4d33e08b8f82b40a12d96ab4fff11427585a
```

## Upgrade-Hinweis

V47A3 ist der eingefrorene FX03-Checkpoint. Weitere Effekte sollen von dieser
Version aus entwickelt werden. Änderungen am Lightning-Modul benötigen einen
neuen PRE-Checkpoint und einen konkret belegten Regressionsgrund.

# Gletscher-Archiv — `glacier/v1/`

Ablage der Gletscher-Linie von buscosun (Phase GL, `buscosun-web/audit/gletscher.md`), append-only, für Gate E
(Sommer 2027: Schmelzindex und Satellit gegen die Messung, mit neu eingefrorenem Protokoll).

```
glacier/v1/<YYYY-MM-DD>/melt-<lauf>.json.gz   die Zeilen der Leitgletscher (rund 44 Gletscher mit Massenbilanz-Messung) jedes Schmelzlaufs von buscosun Fusion: Schmelzindex je Höhenband, Spannen, Zustand
glacier/v1/index.json                         Tage, Dateien und Bytes
```

Geschrieben von `.github/workflows/glacier-archiv.yml` (alle 6 h; Code `scripts/glacier/glacier-archive.mjs` und `glacier-publish.mjs` in buscosun-web,
Daten aus `buscosun-data/glacier/v1/melt`). Die Läufe selbst bleiben im Daten-Repo nur 72 h; vergangene Läufe sind nicht nachholbar. Die Satellitenszenen
(`obs/`, `season/`) liegen dauerhaft in `buscosun-data` und brauchen keine Ablage hier. Eine Datei, die schon da ist, wird nie ersetzt.
Modellwerte (Schmelzindex ohne Einheit) — keine Messung. Quellen und Vermerke: `buscosun-data` README, Abschnitt Gletscher.

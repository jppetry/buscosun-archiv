# Gletscher-Archiv — `glacier/v1/`

Ablage der Gletscher-Linie von buscosun (Phase GL, `buscosun-web/audit/gletscher.md`), append-only, für Gate E
(Sommer 2027: Schmelzindex und Satellit gegen die Messung, mit neu eingefrorenem Protokoll).

```
glacier/v1/<YYYY-MM-DD>/melt-<lauf>.json.gz   die Zeilen der Leitgletscher (rund 44 Gletscher mit Massenbilanz-Messung) jedes Schmelzlaufs von buscosun Fusion: Schmelzindex je Höhenband, Spannen, Zustand
glacier/v1/<YYYY-MM-DD>/stn-<yyyymmddhh>.json.gz  Stationsmessungen einer Stunde in der Nähe der Gletscher (Tirol, Südtirol, zugeordnete Stationen aus obs/v1), wie veröffentlicht
glacier/v1/<YYYY-MM-DD>/stn-stations-<stand>.json.gz  der Stationskatalog dazu, einmal je Stand
glacier/v1/index.json                         Tage, Dateien und Bytes
```

Geschrieben von `.github/workflows/glacier-archiv.yml` (alle 6 h; Code `scripts/glacier/glacier-archive.mjs` und `glacier-publish.mjs` in buscosun-web,
Daten aus `buscosun-data/glacier/v1/melt`). Die Läufe selbst bleiben im Daten-Repo nur 72 h; vergangene Läufe sind nicht nachholbar. Die Satellitenszenen
(`obs/`, `season/`) liegen dauerhaft in `buscosun-data` und brauchen keine Ablage hier. Eine Datei, die schon da ist, wird nie ersetzt.
Modellwerte (Schmelzindex ohne Einheit) — keine Messung. Quellen und Vermerke: `buscosun-data` README, Abschnitt Gletscher.

## Stationsmessungen (`stn-…`, seit 21.11.2026)

Geschrieben von `.github/workflows/glacier-stations-archiv.yml` (alle 6 h; Code `scripts/glacier/stations-archive.mjs` in buscosun-web, Daten aus
`buscosun-data/glacier/v1/stn/h`, dort nur 72 h). Messwerte, keine Modellwerte: Rohdaten der Betreiber, von buscosun auf Alter, Spanne, Sprung und
Stillstand geprüft; was herausfiel, steht im Dokument unter `rejected`. Für die Höhen-Validierung und Gate E.

- **Datenquelle: Land Tirol - data.tirol.gv.at** (Lawinenwarndienst Tirol, Hydrographischer Dienst Tirol), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Geändert: Wind und Böen von km/h in m/s umgerechnet, ungeprüfte Werte nach benannten Regeln weggelassen.
- **Autonome Provinz Bozen – Südtirol**, [CC0](https://creativecommons.org/publicdomain/zero/1.0/). Geändert: Niederschlag der 5-min-Werte zu Summen addiert, ungeprüfte Werte nach benannten Regeln weggelassen.
- DWD · GeoSphere Austria · MeteoSchweiz (CC BY 4.0), aus dem Messspiegel `buscosun-data/obs/v1`, Werte unverändert.

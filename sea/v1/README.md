# Seewetter-Archiv — `sea/v1/`

Ablage der Seewetter-Linie von buscosun (Phase SW, `buscosun-web/audit/seewetter.md`), append-only, für Gate D
(buscosun Fusion Wind am Spot gegen die Messung an der Küste, mindestens 14 Tage).

```
sea/v1/<YYYY-MM-DD>/spots-<lauf>.json.gz   Spot-Reihen jedes veröffentlichten CWAM-Laufs (Welle Modell CWAM, Wind/Böe buscosun Fusion)
sea/v1/<YYYY-MM-DD>/poi.json.gz            stündliche Messungen der Küstenstationen des Spotkatalogs (DWD POI: 10-min-Wind zur vollen Stunde, Richtung, Böe der letzten Stunde, m/s)
sea/v1/<YYYY-MM-DD>/text.json.gz           alle Textausgaben des Tages (FQDL50, FQDL51, WODL45, FXDL40) mit raw, Ausgabezeit, sha256
sea/v1/index.json                          Tage und Inhalt
```

Geschrieben von `.github/workflows/sea-archiv.yml` (alle 6 h; Code `scripts/sea/sea-archive.mjs` in buscosun-web,
Daten aus `buscosun-data/sea/v1`). Vergangene Vorhersagen sind nicht nachholbar, Messungen schon (DWD CDC).
Auswertung: `scripts/sea/sea-gate-d.mjs`. Daten: Deutscher Wetterdienst (GeoNutzV).

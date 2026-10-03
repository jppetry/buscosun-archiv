# Straßenwetter — Archiv `road/v1`

Dauerhafte Ablage der Autobahnwetter-Linie von buscosun (`buscosun-web/audit/autobahnwetter.md` §12). Das Daten-Repo
`buscosun-data` hält `road/v1` nur 24 h; dieser Ordner wächst nur.

Quelle: Deutscher Wetterdienst, Glättemeldeanlagen (SWIS) der Länder — opendata.dwd.de, GeoNutzV; verändert: dekodiert, geprüft, umkodiert.

Geschrieben alle 3 h von `.github/workflows/road-archiv.yml` mit `scripts/road/road-archive.mjs`
aus `buscosun-web` (frisch geklont je Lauf). Ein Lauf füllt nur Lücken, er löscht und überschreibt keinen Wert.

| Datei | Inhalt |
|---|---|
| `<Tag>/00.json.gz`, `<Tag>/12.json.gz` | Halbtag (UTC, 48 Slots à 15 min): je Station Stammdaten, Fahrbahn `rs`, Luft `ta`, Taupunkt `td` (0,1 °C; nur Werte nach den harten Regeln, sonst `null`), Klasse je Slot `k` (`i` Glätte · `f` Frostgefahr · `w` nass · `d` trocken · `u` Zustand unbekannt · `n` keine gültige Messung · `-` kein Punkt); `quarantine` = jeder verworfene und jeder „wäre verworfene" Wert des Slots mit Regel und Rohwert; `rings`/`windows` = welche Ringe beigetragen haben |
| `<Tag>/slots.json` | Slot-Protokoll: freigegeben, Punkte, Anteil verworfen, Reihen, DWD-Ankunft, Ableitung, Sperrgrund |
| `index.json` | Tage, Halbtage, gefüllte Slots |

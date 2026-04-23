# Challenge 2: Radverkehrsströme in Mannheim

## Worum geht es?

Wo wird in Mannheim tatsächlich Rad gefahren?  
Diese Challenge nutzt reale Radverkehrsdaten, um zu analysieren, welche Routen und Korridore besonders häufig genutzt werden. Mit diesem Wissen können wir gezielt Vorschläge erarbeiten, um die Priorisierung beim Winterdienst, die Identifizierung von Unfallschwerpunkten und die Infrastrukturplanung datengestützt zu verbessern.

## Datenquellen & Herausforderungen

### 1. Stadtradeln-App-Daten (2022-2024)
Diese Datensätze basieren auf per GPS aufgezeichneten Fahrten von Bürgern während der jährlichen Aktion "Stadtradeln".  
*Wichtig: Die Rohdaten sind ggf. lizenzbeschränkt und liegen nicht in diesem Repo (siehe Hinweise zum Datenzugriff).*

**⚠️ Herausforderungen bei der Analyse (Datenqualität & GIS):**
- **Inkonsistente Dateiformate:** Die Struktur der gelieferten Daten hat sich über die Jahre verändert. Während die Daten für 2022 und 2023 oft noch als Shapefiles (`.shp`) mit bestimmten Spaltennamen geliefert wurden, liegen die Daten für 2024 teilweise als GeoPackage (`.gpkg`) mit abweichenden Spalten (z.B. `number_of_matched_trips` statt `count`) vor. Ein sauberes Data-Engineering zur Harmonisierung ist hier der erste Pflichtschritt.
- **Lückenhafte Segmente ("Fragmentierung"):** Durch ungenaues GPS, Tunnel, Baumkronen oder stark veränderte OpenStreetMap-Geometrien über die Jahre brechen die Track-Linien oft ab. Selbst bei stark frequentierten Hauptrouten (z.B. Neckarufer) können Teilstücke in der Visualisierung fehlen oder null Fahrten aufweisen.
- **GPS-Ungenauigkeit & Map-Matching:** Die rohen GPS-Punkte liegen oft neben der eigentlichen Straße. Die Fahrten müssen zunächst präzise auf ein bestehendes, einheitliches Straßennetz (z.B. das OSM-Netz von 2024) gemappt werden (Spatial Join / Nearest Match).
- **Repräsentativität (Bias):** Die Daten spiegeln das Verhalten einer sehr motivierten, fahrradaffinen Zielgruppe wider (oft schnelle Pendler oder sportliche Fahrer). Langsame Alltagsradler, Kinder oder ältere Menschen sind möglicherweise unterrepräsentiert.

### 2. Dauerradzählstellen Mannheim (`bike_counter.csv`)
Detaillierte Zähldaten der im Mannheimer Stadtgebiet fest installierten Induktionsschleifen und Eco-Counter (z.B. Friedrich-Ebert-Brücke, Kurpfalzbrücke). Diese Daten liegen direkt hier im Repository unter `data/radzaehlstellen/`.

**⚠️ Herausforderungen bei der Analyse:**
- **Lücken & Ausfälle:** Zählstellen können durch Baustellen (z.B. Sperrungen auf Brücken), technische Defekte oder Batteriewechsel temporär ausfallen, was zu Nullwerten in den Zeitreihen führt.
- **Witterungseffekte:** Die Zählungen schwanken extrem je nach Wetterlage (Regen, Schnee, Hitze). Eine Analyse (z.B. für Winterdienst-Priorisierung) erfordert oft die zusätzliche Einbindung historischer Wetterdaten.
- **Punktuelle vs. Flächendeckende Daten:** Zählstellen liefern absolute, hochpräzise Zahlen, allerdings nur für exakt diese spezifischen Querschnitte. Sie müssen oft mit den flächendeckenden (aber weniger repräsentativen) Stadtradeln-Daten kombiniert werden.

## Leitfragen

- Wo befinden sich die wichtigsten Radverkehrsachsen und -hotspots?
- Auf welchen Strecken sollte im Winter prioritär gestreut werden, weil dort morgens die meisten Radfahrenden unterwegs sind?
- Wo fehlen möglicherweise durchgängige und sichere Verbindungen, obwohl die Nachfrage hoch ist?

## 🗂️ Repo-Struktur

```text
challenge-02-radverkehrstroeme/
│
├── data/
│   ├── radzaehlstellen/   # Enthält die frei nutzbare bike_counter.csv
│   └── stadtradeln/       # Hierhin die heruntergeladene .zip-Datei entpacken
├── notebooks/             # Jupyter Notebooks für Exploration & Analyse
├── src/                   # Python-Skripte (z.B. für Datenbereinigung oder Geodaten-Handling)
├── results/               # Generierte Karten, Charts und Präsentationen
└── README.md              # Diese Datei
```

## 🔒 Datenzugriff

### 1. Zählstellen-Daten (Frei verfügbar)
Die Datei `bike_counter.csv` liegt bereits im Ordner `data/radzaehlstellen/`. Ihr könnt sie direkt in euren Notebooks einlesen (z.B. mit `pd.read_csv('../data/radzaehlstellen/bike_counter.csv')`).

### 2. Stadtradeln-Daten (Lizenzbeschränkt)
Da wir die Stadtradeln-Daten ggf. nicht öffentlich teilen dürfen, müsst ihr diese als `.zip`-Datei über den separaten Download-Link des Orga-Teams herunterladen. 
Bitte entpackt die ZIP-Datei exakt im Ordner `data/stadtradeln/` dieser Challenge, sodass die Ordner `2022`, `2023` und `2024` dort liegen.
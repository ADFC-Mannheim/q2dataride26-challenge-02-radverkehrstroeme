# Challenge 2: Radverkehrsströme in Mannheim

## Worum geht es?

Wo wird in Mannheim tatsächlich Rad gefahren?  
Diese Challenge nutzt reale Radverkehrsdaten, um zu analysieren, welche Routen und Korridore besonders häufig genutzt werden. Mit diesem Wissen können wir gezielt Vorschläge erarbeiten, um die Priorisierung beim Winterdienst, die Identifizierung von Unfallschwerpunkten und die Infrastrukturplanung datengestützt zu verbessern.

## Datenquellen

- **Stadtradeln-App-Daten (2022-2024)**  
  *Wichtig: Die Rohdaten sind ggf. lizenzbeschränkt und liegen nicht in diesem Repo (siehe Hinweise zum Datenzugriff).*
- **Dauerradzählstellen Mannheim**  
  (z.B. Eco-Counter Renzstraße)

## Leitfragen

- Wo befinden sich die wichtigsten Radverkehrsachsen und -hotspots?
- Auf welchen Strecken sollte im Winter prioritär gestreut werden, weil dort morgens die meisten Radfahrenden unterwegs sind?
- Wo fehlen möglicherweise durchgängige und sichere Verbindungen, obwohl die Nachfrage hoch ist?


## 🗂️ Repo-Struktur

```text
challenge-02-radverkehrstroeme/
│
├── data/                  # Daten-Ordner (Rohdaten via .gitignore ignoriert)
│   └── stadtradeln/       # Hierhin die heruntergeladene .zip-Datei entpacken
├── notebooks/             # Jupyter Notebooks für Exploration & Analyse
├── src/                   # Python-Skripte (z.B. für Datenbereinigung oder Geodaten-Handling)
├── results/               # Generierte Karten, Charts und Präsentationen
└── README.md              # Diese Datei
```

## 🔒 Datenzugriff

Die Rohdaten für diese Challenge (insbesondere die Stadtradeln-Daten) liegen **im Hauptordner** unter `data/stadtradeln/`. 

Da wir die Stadtradeln-Daten ggf. nicht öffentlich teilen dürfen, müsst ihr diese als `.zip`-Datei über den separaten Download-Link des Orga-Teams herunterladen. Entpackt die ZIP-Datei bitte exakt im Ordner `../../data/stadtradeln/`, sodass die Ordner `2022`, `2023` und `2024` dort liegen.
# Stadtradeln-Daten (2022-2024)

Aus lizenzrechtlichen Gründen dürfen die Rohdaten des Stadtradelns nicht öffentlich in diesem GitHub-Repository geteilt werden.

## 📥 Anleitung für Hackathon-Teilnehmer

Damit ihr an dieser Challenge arbeiten könnt, müsst ihr die Daten manuell aus unserem privaten Daten-Repository hinzufügen:

1. Geht auf unsere [GitHub-Organisationsseite (Repositories)](https://github.com/ADFC-Mannheim?tab=repositories).
2. Öffnet das private Repository **`q2dataride26-restricted-data`** *(Hinweis: Dieses seht ihr erst, nachdem ihr uns euren GitHub-Namen geschickt habt und von uns eingeladen wurdet).*
3. Ladet euch die Daten aus dem privaten Repo herunter (entweder klonen oder über `<> Code` -> `Download ZIP` herunterladen und entpacken).
4. Kopiert die Ordner `2022`, `2023` und `2024` aus dem dortigen Verzeichnis exakt hier in diesen lokalen Ordner.

Nach dem Einfügen sollte eure Ordnerstruktur hier exakt so aussehen:

```text
data/stadtradeln/
├── 2022/
│   ├── trafficvolumes.prj
│   ├── trafficvolumes.shp
│   └── trafficvolumes.shx
├── 2023/
│   ├── trafficvolumes.cpg
│   ├── trafficvolumes.dbf
│   ├── trafficvolumes.fix
│   ├── trafficvolumes.prj
│   ├── trafficvolumes.shp
│   └── trafficvolumes.shx
├── 2024/
│   └── trafficvolumes.gpkg
└── readme.md (diese Datei)
```

⚠️ **Hinweis:** Solange ihr diese Struktur beibehaltet, finden die vorbereiteten Jupyter-Notebooks und Skripte die Geodaten automatisch über die voreingestellten relativen Pfade. Die `.gitignore` sorgt dafür, dass ihr diese Daten nicht aus Versehen öffentlich zu GitHub hochladet.
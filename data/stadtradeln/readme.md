# Stadtradeln-Daten (2022-2024)

Aus lizenzrechtlichen Gründen dürfen die Rohdaten des Stadtradelns ggf. nicht öffentlich in diesem GitHub-Repository geteilt werden.

## 📥 Anleitung für Hackathon-Teilnehmer

Damit ihr an dieser Challenge arbeiten könnt, müsst ihr die Daten manuell hinzufügen:

1. Ladet die bereitgestellte Datei `Stadtradeln.zip` über den separaten Download-Link (oder via USB-Stick) herunter.
2. Legt die `.zip`-Datei genau in diesen Ordner (`challenge-02-radverkehrstroeme/data/stadtradeln/`).
3. Entpackt die ZIP-Datei hier.

Nach dem Entpacken sollte eure Ordnerstruktur exakt so aussehen:

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

⚠️ **Hinweis:** Solange ihr diese Struktur beibehaltet, finden die vorbereiteten Jupyter-Notebooks und Skripte die Geodaten automatisch über die voreingestellten relativen Pfade. Die `.gitignore` sorgt dafür, dass ihr diese Daten nicht aus Versehen zu GitHub hochladet.
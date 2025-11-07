# TUXVideoConvert - Professional Video Conversion Tool 🎬

<div align="center">

![Version](https://img.shields.io/badge/version-3.1.0-blue)
![License](https://img.shields.io/badge/license-GPL--3.0-green)
![Platform](https://img.shields.io/badge/platform-Linux-lightgrey)
![Python](https://img.shields.io/badge/python-3.9+-yellow)

**Professionelles Video-Konvertierungs-Tool mit moderner PyQt6-GUI**

[Features](#-features) • [Installation](#-installation) • [Verwendung](#-verwendung) • [Screenshots](#-screenshots) • [Lizenz](#-lizenz)

</div>

---

## 📖 Überblick

**TUXVideoConvert** ist ein leistungsstarkes Video-Konvertierungs-Tool für Linux mit intuitiver grafischer Oberfläche. Es unterstützt die Konvertierung von Videos für verschiedene Social-Media-Plattformen mit automatischer Größenanpassung, Rotation, Qualitätseinstellung und vielen weiteren Features.

### 🎯 Hauptmerkmale

- 🎬 **Moderne PyQt6-GUI** mit KDE Breeze Dark Theme
- 📦 **Batch-Modus** - Mehrere Videos gleichzeitig konvertieren
- 🎯 **Drag & Drop** - Videos einfach reinziehen
- 💾 **Einstellungen merken** - Automatisch beim nächsten Start
- 📐 **Plattform-Presets** - YouTube Shorts, Instagram, TikTok, etc.
- 🔄 **Video-Rotation** - 90°, 180°, 270°
- ✂️ **Video-Schnitt** - Start-/Endzeit festlegen
- 🎨 **Qualitätseinstellung** - CRF-Slider (0-51)
- 🌐 **Web-Optimierung** - Dateigrößen-Limits für Upload
- 📊 **Live-Größenschätzung** - Vor der Konvertierung
- 🔊 **Audio-Steuerung** - Audio behalten oder entfernen
- ⚡ **Geschwindigkeitsoptionen** - ultrafast bis veryslow

---

## ✨ Features im Detail

### 🎬 Video-Konvertierung

- **Mehrere Formate**: MP4, AVI, MKV, MOV, WebM, FLV, M4V
- **Automatisches Skalieren**: Mit Aspect-Ratio-Erhalt und Padding
- **Hochwertige Ausgabe**: H.264-Kodierung mit einstellbarer Qualität
- **FastStart-Flag**: Optimiert für Streaming und Web

### 📐 Plattform-Presets

| Plattform        | Auflösung   | Seitenverhältnis | Optimiert für      |
|------------------|-------------|------------------|--------------------|
| YouTube Shorts   | 1080x1920   | 9:16             | Vertical Video     |
| Instagram Reel   | 1080x1920   | 9:16             | Vertical Video     |
| TikTok           | 1080x1920   | 9:16             | Vertical Video     |
| Twitter/X        | 1280x720    | 16:9             | Horizontal Video   |
| Spotify Canvas   | 720x1280    | 9:16             | Vertical Video     |
| Custom           | Variabel    | Beliebig         | Eigene Auflösung   |

### 🌐 Web-Optimierung

Vordefinierte Upload-Limits für verschiedene Plattformen:

- **5 MB** - Twitter/X
- **10 MB** - Discord
- **25 MB** - WhatsApp
- **50 MB** - Telegram
- **100 MB** - YouTube Shorts
- **Custom** - Benutzerdefiniert (1-500 MB)

⚠️ **Automatischer Split-Modus**: Videos werden automatisch in Teile zerlegt, wenn sie das Limit überschreiten.

### 📊 Intelligente Größenschätzung

Das Tool berechnet die voraussichtliche Ausgabegröße basierend auf:
- Auflösung (Bitrate-Heuristik)
- CRF-Qualität
- Audio ein/aus
- Video-Länge nach Trim

### 🎨 Qualitätseinstellungen (CRF)

- **0-18**: Sehr hoch (große Dateien, Archivierung)
- **19-23**: Hoch (Standard, empfohlen) ⭐
- **24-28**: Mittel (kleinere Dateien)
- **29-51**: Niedrig (sehr kleine Dateien)

💡 **Empfehlung**: CRF 23 bietet das beste Verhältnis von Qualität zu Dateigröße.

---

## 🚀 Installation

### Voraussetzungen

- **Python**: 3.9 oder höher
- **ffmpeg**: Für Video-Verarbeitung
- **PyQt6**: GUI Framework

### System-Abhängigkeiten

```bash
# Arch Linux / CachyOS
sudo pacman -S python python-pip ffmpeg

# Debian / Ubuntu
sudo apt install python3 python3-pip python3-venv ffmpeg

# Fedora
sudo dnf install python3 python3-pip ffmpeg
```

### Installation

1. **Repository klonen**:
```bash
git clone https://github.com/tuxplayer/TUXVideoConvert.git
cd TUXVideoConvert
```

2. **Erste Ausführung** (erstellt automatisch venv und installiert Abhängigkeiten):
```bash
./start.sh
```

Das Start-Script:
- ✅ Erstellt automatisch Python Virtual Environment
- ✅ Installiert PyQt6
- ✅ Prüft ffmpeg-Installation
- ✅ Startet die GUI

---

## 📖 Verwendung

### GUI starten

```bash
./start.sh
```

### Workflow

1. **Videos hinzufügen**:
   - Einzeln: "📂 Video hinzufügen" Button
   - Mehrere: "📂+ Mehrere" Button (Batch-Modus)
   - Drag & Drop: Videos einfach in die Vorschau ziehen

2. **Preset wählen**:
   - Wählen Sie eine Plattform aus der Liste
   - Oder nutzen Sie "Custom" für eigene Größen

3. **Optionen einstellen**:
   - **Rotation**: Keine, 90°, 180°, 270°
   - **Audio**: Ein/Aus
   - **Qualität (CRF)**: 0-51 (Standard: 23)
   - **Geschwindigkeit**: ultrafast, fast, medium, slow, veryslow
   - **Web-Optimierung**: Optional Dateigrößen-Limit setzen

4. **Video schneiden** (optional):
   - Checkbox aktivieren
   - Start-Zeit in Sekunden eingeben
   - End-Zeit in Sekunden eingeben

5. **Konvertierung starten**:
   - Klicken Sie auf "🎬 Konvertierung starten"
   - Beobachten Sie den Fortschritt im Log
   - Nach Abschluss wird das Ausgabeverzeichnis geöffnet

### Ausgabe

- **Verzeichnis**: `~/Videos/converted/`
- **Dateiformat**: `{original}_{preset}_{timestamp}.mp4`
- **Log-Datei**: `~/.local/share/tuxhs/video_convert.log`

---

## 📁 Projektstruktur

```
TUXVideoConvert/
├── src/
│   ├── main.py                 # Entry Point
│   ├── ui/
│   │   ├── main_window.py      # Hauptfenster mit Tabs
│   │   ├── convert_tab.py      # Konvertierungs-Tab (Batch, Drag&Drop)
│   │   └── help_tab.py         # Hilfe & Info Tab
│   ├── core/
│   │   └── video_converter.py  # Video-Konvertierungs-Engine
│   └── utils/
│       └── config.py            # Konfiguration & Presets
├── presets.json                 # Plattform-Presets
├── requirements.txt             # Python-Abhängigkeiten
├── start.sh                     # Launcher-Script
├── README.md                    # Diese Datei
├── LICENSE                      # GPL-3.0 Lizenz
└── backups/                     # Backup-Verzeichnis
```

---

## 🎨 Screenshots

### Hauptfenster

- **Links**: Video-Vorschau mit Thumbnail, Warteschlange, Video-Informationen
- **Rechts**: Scrollbare Einstellungen (Plattform, Web-Optimierung, Optionen)

### Features in Action

- ✅ **Drag & Drop**: Videos einfach reinziehen
- ✅ **Batch-Modus**: Mehrere Videos in Warteschlange
- ✅ **Live-Schätzung**: Ausgabegröße wird in Echtzeit berechnet
- ✅ **Web-Optimierung**: Warnung bei Überschreitung des Limits

---

## ⚙️ Konfiguration

### Presets anpassen

Bearbeiten Sie `presets.json`:

```json
{
  "YouTube Shorts": {"width": 1080, "height": 1920},
  "Instagram Reel": {"width": 1080, "height": 1920},
  "TikTok": {"width": 1080, "height": 1920},
  "Twitter/X": {"width": 1280, "height": 720},
  "Spotify Canvas": {"width": 720, "height": 1280},
  "Custom": {"width": 1920, "height": 1080}
}
```

### Einstellungen

Einstellungen werden automatisch gespeichert in:
- **Linux**: `~/.config/TUXHS/TUXVideoConvert.conf`

Gespeicherte Werte:
- Letztes Preset
- Rotation
- Audio ein/aus
- CRF-Qualität
- Geschwindigkeit
- Web-Optimierung

---

## 🛠️ Technische Details

### Video-Pipeline

```bash
ffmpeg -y [-ss START] [-t DURATION] -i INPUT \
  -vf "scale=WIDTH:HEIGHT:force_original_aspect_ratio=decrease,
       pad=WIDTH:HEIGHT:(ow-iw)/2:(oh-ih)/2,setsar=1[,transpose=...]" \
  -c:v libx264 -preset PRESET -crf CRF \
  [-c:a aac -b:a 128k | -an] \
  -movflags +faststart \
  OUTPUT.mp4
```

### Geschwindigkeits-Presets

| Preset     | Konvertierungszeit | Dateigröße | Empfohlen für           |
|------------|-------------------|------------|-------------------------|
| ultrafast  | Sehr schnell      | Groß       | Schnelle Tests          |
| fast       | Schnell           | Mittel     | Batch-Konvertierung     |
| medium     | ⭐ Standard        | ⭐ Optimal  | Allgemeiner Gebrauch    |
| slow       | Langsam           | Klein      | Beste Qualität          |
| veryslow   | Sehr langsam      | Sehr klein | Maximale Kompression    |

---

## 🐛 Troubleshooting

### ffmpeg nicht gefunden

```bash
# Arch / CachyOS
sudo pacman -S ffmpeg

# Debian / Ubuntu
sudo apt install ffmpeg
```

### PyQt6 Import-Fehler

```bash
source venv/bin/activate
pip install --upgrade PyQt6
```

### GUI startet nicht

Prüfen Sie X11/Wayland-Display:
```bash
echo $DISPLAY
# Sollte ":0" oder ähnlich sein
```

### Konvertierung schlägt fehl

1. Prüfen Sie das Log: `~/.local/share/tuxhs/video_convert.log`
2. Testen Sie ffmpeg manuell:
   ```bash
   ffmpeg -i input.mp4 -c:v libx264 -crf 23 test.mp4
   ```
3. Stellen Sie sicher, dass genug Festplattenspeicher vorhanden ist

---

## 📝 Changelog

### v3.1.0 (2025-11-07)
- ✨ **Batch-Modus** - Mehrere Videos gleichzeitig konvertieren
- ✨ **Drag & Drop** - Videos einfach in GUI ziehen
- ✨ **Einstellungen speichern** - Automatisch beim Neustart laden
- ✨ **Warteschlange** - Video-Queue mit Vorschau
- ✨ **Verbesserte Scrollbar** - Dezenter und moderner
- 🐛 **Fix**: Custom MB Spinbox funktioniert jetzt korrekt
- 🎨 **UI-Verbesserungen** - Größere Abstände, bessere Lesbarkeit

### v3.0.0 (2025-11-07)
- 🎉 Komplette Neuentwicklung mit PyQt6
- ✨ 2-Spalten-Layout (Video-Preview + Einstellungen)
- ✨ Video-Thumbnail-Extraktion
- ✨ Web-Optimierung mit Dateigrößen-Limits
- ✨ Live-Größenschätzung
- ✨ Video-Schnitt (Trim)
- ✨ CRF-Qualitätsauswahl mit Slider
- ✨ KDE Breeze Dark Theme

### v2.1.0 (2025-11-07)
- ✨ Video-Stückelung für Upload-Limits

### v2.0.0 (2025-11-07)
- 🐛 Diverse Bugfixes

### v1.0.0 (2025-10-08)
- 🎉 Initiale Version mit kdialog-GUI

---

## 🔮 Roadmap

- [ ] Video-Player statt Thumbnail
- [ ] Fortschrittsbalken mit Prozentanzeige
- [ ] Exportierte Profile speichern/laden
- [ ] Untertitel-Support
- [ ] Wasserzeichen hinzufügen
- [ ] GPU-Beschleunigung (NVENC, VAAPI)
- [ ] Multi-Threading für Batch
- [ ] Cloud-Upload (YouTube, Dropbox, etc.)

---

## 👤 Autor

**Heiko Schäfer (TUXPLAYER)**

- 📧 E-Mail: contact@tuxhs.de
- 🌐 Website: [tuxhs.de](https://tuxhs.de)
- 💻 GitHub: [@tuxplayer](https://github.com/tuxplayer)

---

## 📜 Lizenz

Dieses Projekt ist lizenziert unter der **GNU General Public License v3.0** (GPL-3.0).

```
TUXVideoConvert - Video Konvertierungs-Tool
Copyright (C) 2025 Heiko Schäfer (TUXPLAYER)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.
```

Vollständige Lizenz: [LICENSE](LICENSE)

---

## 🙏 Danksagungen

- **ffmpeg-Team** - Für das großartige Video-Processing-Tool
- **Riverbank Computing** - PyQt6 Entwicklung
- **KDE-Community** - Breeze Dark Theme-Inspiration
- **CachyOS Linux** - Entwicklungsplattform

---

## 🤝 Beitragen

Beiträge sind willkommen! Bitte:

1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch (`git checkout -b feature/NeuesFeature`)
3. Committen Sie Ihre Änderungen (`git commit -m '✨ Füge NeuesFeature hinzu'`)
4. Pushen Sie zum Branch (`git push origin feature/NeuesFeature`)
5. Öffnen Sie einen Pull Request

### Commit-Konventionen

```
🎉 Initial commit
✨ Add feature
🐛 Fix bug
♻️ Refactor code
📝 Update docs
🔧 Update config
🎨 Improve UI
⚡ Improve performance
🔒 Fix security issue
```

---

## ⭐ Support

Wenn Ihnen dieses Projekt gefällt, geben Sie ihm einen ⭐ auf GitHub!

### Probleme melden

Bei Problemen oder Feature-Wünschen:
- Öffnen Sie ein [Issue auf GitHub](https://github.com/tuxplayer/TUXVideoConvert/issues)
- Oder kontaktieren Sie mich per E-Mail: contact@tuxhs.de

---

<div align="center">

**Made with ❤️ by TUXPLAYER • 2025**

*Für die Linux/KDE-Community*

[⬆️ Nach oben](#tuxvideoconvert---professional-video-conversion-tool-)

</div>
# TUXVideoConvert

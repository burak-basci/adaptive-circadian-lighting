# Adaptive Circadian Lighting für Home Assistant

Diese Home Assistant Blueprint passt die Farbtemperatur deiner Lichter automatisch an den Sonnenstand an, um einen natürlichen circadianen Rhythmus zu simulieren.

## ✨ Features

- 🌅 **Automatische Anpassung**: Farbtemperatur ändert sich basierend auf der Sonnenelevation
- 🌡️ **Anpassbare Bereiche**: Konfigurierbare Min/Max Kelvin-Werte (Standard: 2200K - 6500K)
- 🎯 **Sanfte Übergänge**: Verwendet Sigmoid-Kurve für natürliche Farbübergänge
- ⚡ **Minutengenaue Updates**: Aktualisiert sich jede Minute
- 🔦 **Flexible Modi**: Optional nur anpassen wenn Licht bereits an ist
- ⏱️ **Konfigurierbare Transition**: Einstellbare Übergangszeit (0-30 Sekunden)

## 📊 Wie es funktioniert

Die Blueprint berechnet die Farbtemperatur basierend auf der Sonnenelevation:

- **Tiefe Nacht** (≤ -18°): Wärmste Temperatur (Standard: 2200K)
- **Hoher Sonnenstand** (≥ 45°): Kälteste Temperatur (Standard: 6500K)
- **Dazwischen**: Sanfte Sigmoid-Kurve für natürliche Übergänge

## 🚀 Installation

### Methode 1: Import über URL

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fburak-basci%2Fadaptive-circadian-lighting%2Fblob%2Fmain%2Fadaptive_circadian_lighting.yaml)

Oder manuell:
1. Gehe zu **Einstellungen** → **Automatisierungen & Szenen** → **Blueprints**
2. Klicke auf **Blueprint importieren**
3. Füge die URL ein: `https://github.com/burak-basci/adaptive-circadian-lighting/blob/main/adaptive_circadian_lighting.yaml`

### Methode 2: Manuelle Installation

1. Downloade `adaptive_circadian_lighting.yaml`
2. Kopiere die Datei nach `config/blueprints/automation/`
3. Starte Home Assistant neu

## ⚙️ Konfiguration

Nach der Installation:

1. Gehe zu **Einstellungen** → **Automatisierungen & Szenen**
2. Klicke auf **Automation erstellen** → **Blueprint verwenden**
3. Wähle **Adaptive Lichttemperatur nach Sonnenstand**
4. Konfiguriere:
   - **Ziel-Lichter**: Wähle die Lichter aus, die angepasst werden sollen
   - **Minimale Farbtemperatur**: Wärmste Temperatur für Abend/Nacht (1800-4000K)
   - **Maximale Farbtemperatur**: Kälteste Temperatur für Mittag (4000-10000K)
   - **Übergangszeit**: Dauer des Farbwechsels in Sekunden (0-30s)
   - **Nur wenn Licht an**: Aktivieren um nur eingeschaltete Lichter anzupassen

## 📝 Beispiel-Konfiguration

**Wohnzimmer - Warmes Licht:**
- Min: 2000K
- Max: 4000K
- Übergangszeit: 10s
- Nur wenn an: ✓

**Arbeitszimmer - Kaltes Licht:**
- Min: 3000K
- Max: 6500K
- Übergangszeit: 5s
- Nur wenn an: ✓

## 🔧 Voraussetzungen

- Home Assistant mit sun.sun Integration (standardmäßig aktiv)
- Lichter die Kelvin-Farbtemperatur unterstützen

## 📖 Technische Details

Die Blueprint verwendet eine Sigmoid-Transformation für natürliche Übergänge:

```
sigmoid(x) = 1 / (1 + e^(-k*(x-0.5)))
```

Mit k=8 für eine sanfte S-Kurve, die biologische circadiane Rhythmen nachahmt.

## 🤝 Beitragen

Feedback und Verbesserungsvorschläge sind willkommen! Erstelle gerne ein Issue oder Pull Request.

## 📄 Lizenz

MIT License

---

Erstellt mit ❤️ für die Home Assistant Community

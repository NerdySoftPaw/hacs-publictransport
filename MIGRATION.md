# Migration Guide / Migrationsanleitung

## Deutsch

### Wichtige Ankündigung: Repository-Umzug

Das VRR Public Transport Integration wurde in ein neues Repository verschoben:

**Altes Repository:** `NerdySoftPaw/hacs-vrr`
**Neues Repository:** `NerdySoftPaw/hacs-publictransport`

Das neue Repository unterstützt nun mehrere Provider (VRR, KVV, HVV, Trafiklab, NTA) und wird aktiv weiterentwickelt.

---

## Option 1: Schnelle Migration (Empfohlen)

Diese Methode behält deine bestehende Konfiguration und Sensoren bei.

### Schritt 1: Repository in HACS wechseln

1. Öffne **HACS** in der Seitenleiste
2. Gehe zu **Integrationen**
3. Suche nach "VRR"
4. Klicke auf die Integration
5. Klicke auf die drei Punkte (⋮) oben rechts → **Entfernen**
6. **WICHTIG:** Nur aus HACS entfernen, NICHT die Integration in Home Assistant löschen!

### Schritt 2: Neues Repository hinzufügen

1. Klicke in HACS auf die drei Punkte (⋮) oben rechts
2. Wähle **Benutzerdefinierte Repositories**
3. Füge hinzu:
   ```
   https://github.com/NerdySoftPaw/hacs-publictransport
   ```
4. Kategorie: **Integration**
5. Klicke **Hinzufügen**

### Schritt 3: Neue Version installieren

1. Suche in HACS nach "Public Transport"
2. Klicke auf **Public Transport Departures**
3. Klicke **Herunterladen**
4. Wähle die neueste Version

### Schritt 4: Home Assistant neu starten

1. Gehe zu **Einstellungen** → **System** → **Neu starten**
2. Fertig! Deine Konfiguration sollte erhalten bleiben.

---

## Option 2: Manuelle Migration (Für Experten)

Falls HACS Probleme macht, kannst du die Dateien direkt ersetzen.

### Schritt 1: Neue Dateien herunterladen

```bash
cd /config/custom_components/
rm -rf vrr/
wget https://github.com/NerdySoftPaw/hacs-publictransport/releases/latest/download/vrr.zip
unzip vrr.zip
rm vrr.zip
```

### Schritt 2: Home Assistant neu starten

Deine bestehende Konfiguration bleibt erhalten.

---

## Option 3: Saubere Neuinstallation

Falls du Probleme hast oder einen Neuanfang möchtest.

### Schritt 1: Alte Integration komplett entfernen

1. **Einstellungen** → **Geräte & Dienste**
2. Suche "VRR" → drei Punkte (⋮) → **Löschen**

### Schritt 2: Aus HACS entfernen

1. **HACS** → **Integrationen** → "VRR" → **Entfernen**

### Schritt 3: Neu starten

**Einstellungen** → **System** → **Neu starten**

### Schritt 4: Neues Repository hinzufügen & installieren

(Siehe Option 1, Schritte 2-4)

### Schritt 5: Integration neu einrichten

1. **Einstellungen** → **Geräte & Dienste** → **+ Integration hinzufügen**
2. Suche "Public Transport"
3. Folge dem Einrichtungsassistenten

---

## Wichtige Hinweise

| Methode | Konfiguration | Historische Daten | Entity-IDs |
|---------|--------------|-------------------|------------|
| Option 1 (Schnell) | ✅ Bleibt erhalten | ✅ Bleibt erhalten | ✅ Bleiben gleich |
| Option 2 (Manuell) | ✅ Bleibt erhalten | ✅ Bleibt erhalten | ✅ Bleiben gleich |
| Option 3 (Sauber) | ❌ Neu einrichten | ❌ Geht verloren | ❌ Können sich ändern |

---

## Neue Features

- Multi-Provider Support (VRR, KVV, HVV, Trafiklab, NTA)
- Verbesserte Haltestellensuche mit Fuzzy-Matching
- Binary Sensor für Verspätungen
- Caching für schnellere Antworten
- Bessere Fehlerbehandlung

---

## Hilfe

Bei Problemen: https://github.com/NerdySoftPaw/hacs-publictransport/issues

---
---

## English

### Important: Repository Move

**Old Repository:** `NerdySoftPaw/hacs-vrr`
**New Repository:** `NerdySoftPaw/hacs-publictransport`

---

## Option 1: Quick Migration (Recommended)

This method keeps your existing configuration and sensors.

### Step 1: Switch Repository in HACS

1. Open **HACS** in the sidebar
2. Go to **Integrations**
3. Search for "VRR"
4. Click on the integration
5. Click three dots (⋮) → **Remove**
6. **IMPORTANT:** Only remove from HACS, do NOT delete the integration in Home Assistant!

### Step 2: Add New Repository

1. In HACS, click three dots (⋮) top right
2. Select **Custom repositories**
3. Add:
   ```
   https://github.com/NerdySoftPaw/hacs-publictransport
   ```
4. Category: **Integration**
5. Click **Add**

### Step 3: Install New Version

1. Search in HACS for "Public Transport"
2. Click **Public Transport Departures**
3. Click **Download**
4. Select latest version

### Step 4: Restart Home Assistant

1. Go to **Settings** → **System** → **Restart**
2. Done! Your configuration should be preserved.

---

## Option 2: Manual Migration (For Experts)

If HACS has issues, you can replace files directly.

```bash
cd /config/custom_components/
rm -rf vrr/
wget https://github.com/NerdySoftPaw/hacs-publictransport/releases/latest/download/vrr.zip
unzip vrr.zip
rm vrr.zip
```

Then restart Home Assistant.

---

## Option 3: Clean Reinstall

If you have issues or want a fresh start.

1. Remove integration: **Settings** → **Devices & Services** → "VRR" → **Delete**
2. Remove from HACS: **HACS** → **Integrations** → "VRR" → **Remove**
3. Restart Home Assistant
4. Add new repository (see Option 1, Steps 2-4)
5. Set up integration again

---

## Summary

| Method | Configuration | History | Entity IDs |
|--------|--------------|---------|------------|
| Option 1 (Quick) | ✅ Preserved | ✅ Preserved | ✅ Same |
| Option 2 (Manual) | ✅ Preserved | ✅ Preserved | ✅ Same |
| Option 3 (Clean) | ❌ Re-setup | ❌ Lost | ❌ May change |

---

## Help

Issues: https://github.com/NerdySoftPaw/hacs-publictransport/issues

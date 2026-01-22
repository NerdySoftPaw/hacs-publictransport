# Migration Guide

> **Note:** This migration guide is only relevant when upgrading from version `2026.01.22` or earlier to version `2026.01.23`.
> If you're installing fresh, you can skip this guide entirely.

## Repository Change

The integration has moved to a new repository:

| | Old | New |
|--|-----|-----|
| **Repository** | `NerdySoftPaw/VRRAPI-HACS` | `NerdySoftPaw/hacs-publictransport` |
| **Providers** | VRR only | VRR, KVV, HVV, Trafiklab, NTA |
| **Status** | ⚠️ Deprecated | ✅ Active Development |

---

## Migration Steps

Your existing configuration will be **automatically migrated**. Just follow these simple steps:

### Step 1: Change Repository URL in HACS

1. Open **HACS** → **Integrations**
2. Find "VRR" or "Public Transport"
3. Click the three dots (⋮) → **Redownload**
4. In the repository field, change the URL to:
   ```
   https://github.com/NerdySoftPaw/hacs-publictransport
   ```
5. Click **Download**

### Step 2: Restart Home Assistant

1. Go to **Settings** → **System** → **Restart**
2. Wait for Home Assistant to restart

### Step 3: Done! ✅

Your existing sensors, configuration, and historical data are automatically preserved.

---

## What Gets Migrated

| Item | Status |
|------|--------|
| Sensor configuration | ✅ Preserved |
| Entity IDs | ✅ Unchanged |
| Historical data | ✅ Preserved |
| Automations using VRR entities | ✅ Continue working |
| Dashboard cards | ✅ Continue working |

---

## New Features After Migration

After migrating to version `2026.01.23`, you'll have access to:

- 🇮🇪 **NTA Ireland** - New provider for Irish public transport
- 🧠 **Fuzzy Search** - Find stops even with typos
- ⚡ **Better Performance** - 20-30% faster updates
- 📦 **API Caching** - Reduced API calls

---

## Troubleshooting

### Integration not showing after restart?

1. Check if the custom component folder exists: `/config/custom_components/vrr/`
2. Check Home Assistant logs for errors
3. Try clearing browser cache and refreshing

### HACS shows old version?

1. In HACS, click on the integration
2. Click three dots (⋮) → **Redownload**
3. Make sure the repository URL is correct

### Need Help?

- 📖 [Documentation](https://hacs-publictransport.readthedocs.io/)
- 🐛 [Report an Issue](https://github.com/NerdySoftPaw/hacs-publictransport/issues)

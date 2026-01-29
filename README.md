# AutoMeds

**AutoMeds** is a Windower addon for Final Fantasy XI that tracks debuffs and automatically uses items to remove them. It features advanced aura detection to prevent wasting items on permanent aura debuffs.

## Features

### 🛡️ Buff Tracking & Item Usage
* **Auto Removal:** Automatically uses the correct item for common debuffs (Curse, Doom, Paralysis, Silence, Disease).
* **Inventory Check:** Skips usage if the required item isn't in your inventory.
* **Persistence:** Retries item usage until the debuff is cleared.
* **Configurable:** Maintain a custom list of monitored debuffs.

### 📡 IPC Multi-Character Support
* **Alt Broadcast:** Broadcast debuff info to your alts via `trackalt`.
* **Sneak/Invis Tracker:** Notify alts when Sneak/Invisible is wearing off via `sitrack`.

### 🧠 Aura Awareness (Target-Based)
* **Distance Scanning:** Continuously scans nearby targets (within 20 yalms by default).
* **Auto-Suppress:** If a mob known to emit an aura (e.g., *Biune Ice Elemental*) is nearby, AutoMeds will stop trying to cure that specific debuff.
* **Customizable List:** Add specific mobs and their debuffs to your aura list.
* **Efficiency:** Prevents wasting stacks of Holy Waters or Panaceas on permanent auras.

### 🛑 Smart Aura Block (Behavior-Based)
* **Auto-Pause:** If a debuff persists after **2 attempts** (default), AutoMeds assumes it is an aura and pauses item usage for that debuff.
* **Cool-down:** Pauses usage for **120 seconds** (configurable 60-600s) before trying again.
* **Independent:** Works even if "Aura Awareness" is disabled or if the mob isn't in your database yet.

---

## Installation

1.  Download the files and place them in `Windower4/addons/AutoMeds/`.
2.  Load the addon in game: `//lua load automeds`

---

## Commands

Use `//ameds` followed by the command. Do not type `[ ]`.

| Category | Command | Arguments | Description |
| :--- | :--- | :--- | :--- |
| **General** | `toggle` | | Toggle AutoMeds On/Off |
| | `watch` | `[buff]` | Track a specific debuff |
| | `unwatch` | `[buff]` | Stop tracking a specific debuff |
| | `list` | | Show all currently tracked debuffs |
| **Multi-Box** | `trackalt` | | Toggle alt broadcast |
| | `sitrack` | | Toggle Sneak/Invisible wear tracker |
| **Auras** | `aura` | `on` / `off` | Enable/Disable Aura Awareness |
| | `aurasmart` | `on` / `off` | Enable/Disable Smart Aura Block |
| | `aurablock` | `[60-600]` | Set Smart Block pause duration (Default: 120s) |
| | `auradistance`| `[1-20]` | Set detection range for Aura Awareness |
| | `auraadd` | `"[target]" [buff]` | Add a mob to the aura blacklist |
| | `aurarem` | `"[target]" [buff]` | Remove a mob from the aura blacklist |
| | `auralist` | | List all known aura sources |

### Examples
* `//ameds auraadd "Triboulex" paralysis`
* `//ameds aurablock 60`
* `//ameds watch curse`

---

## Notes
* **Performance:** This addon checks conditions roughly twice per second to ensure high framerates.
* **Configuration:** It is recommended to add permanent aura targets directly to `sources_list` in `data/settings.xml` (or via the `auraadd` command) if you frequently encounter specific aura mobs.

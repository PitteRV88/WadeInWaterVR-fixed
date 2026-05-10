# WadeInWater VR - Fixed

Synthesis patcher for [Wade in Water VR](https://www.nexusmods.com/skyrimspecialedition/mods/33720).

Patches all water records in your load order to include the **Causes Damage** flag required by the Wade in Water VR script to detect water and slow the player.

This is a fork of [matm-git/WadeInWater](https://github.com/matm-git/WadeInWater) with a build fix applied.

---

## Fix applied in this fork

**Problem:** `MSB6006: "csc.exe" exited with code -1073741819`

The original patcher targeted `net6.0` and had no SDK constraint. On systems with **.NET SDK 10.x** installed as the default, the Roslyn compiler (`csc.exe`) crashes with an Access Violation (`0xC0000005`) when building this project via Synthesis.

**Solution:**
- Added `global.json` at the repository root to pin the build to **.NET SDK 8.x** (`rollForward: latestPatch`).
- Updated `TargetFramework` from `net6.0` to `net8.0` (Synthesis 0.35.x requires net8.0 anyway and swaps it automatically, but setting it explicitly avoids confusion).

These two changes together fix the crash without changing any patcher logic.

---

## Requirements

- [Synthesis](https://github.com/Mutagen-Modding/Synthesis) 0.35.x or later
- [Wade in Water VR](https://www.nexusmods.com/skyrimspecialedition/mods/33720) installed and active in your load order
- .NET SDK 8.0 or later installed

## Usage

Add this patcher in Synthesis via **Git Repository** using the URL:

```
https://github.com/PitteRV88/WadeInWaterVR-fixed
```

Run Synthesis as usual. The patcher will add the Causes Damage flag to all water records in your load order.

---

*Original patcher by [matm-git](https://github.com/matm-git/WadeInWater). Fix by PitteRV88.*

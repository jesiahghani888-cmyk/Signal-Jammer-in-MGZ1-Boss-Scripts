# Signal Jammer in MGZ1 Boss Mod

## Overview
This mod for **Sonic 3 Angel Island Revisited (v26.03.28.0)** replaces the original **Tunnelbot** boss in **Marble Garden Zone Act 1** with the **Signal Jammer** from *Sonic 3 & Tenna*.

## Features
- **Boss Replacement**: Replaces the MGZ1 mini-boss with a fully functional Signal Jammer.
- **Custom Logic**: Includes unique movement patterns, drone spawning, and attack phases.
- **Global Variables**: Utilizes Lemon script global variables for state management and boss behavior.
- **Signpost Integration**: Correctly triggers the signpost spawn upon defeat using `SetupAsSignpostSpawner()`.

## Installation
1. Ensure you are running **Sonic 3 A.I.R. v26.03.28.0**.
2. Place the `signaljammer_boss_mgz1.lemon` file into your mod's `scripts` folder.
3. Make sure any required sprites (e.g., `tenna_signaljammer_body`, `tenna_signaljammer_drone_body_0`) are included in your mod's `sprites` folder.
4. Enable the mod in the Sonic 3 A.I.R. mod menu.

## Script Details
The script uses address hooks to intercept the original MGZ1 boss initialization:
- **Hook Address**: `0x088568`
- **Logic**: Checks for `global.zone_act == 0x0200` to ensure the replacement only occurs in Marble Garden Zone Act 1.

## Credits
- **Original Boss Design**: Sonic 3 & Tenna Team.
- **Mod Scripting**: jesiahghani888-cmyk.
- **Platform**: Sonic 3 Angel Island Revisited.

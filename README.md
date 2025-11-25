# Sylvarcon2049GameLegazy
# Virtual Machine Setup Guide for Sylvarcon 2049

This guide explains how to set up the virtual machines required to run the complete Sylvarcon 2049 game experience.

## Overview

The game uses VirtualBox virtual machines to simulate hacking environments. Two main VM packages are required:
- **PlayerVM** - The main player environment
- **Character VMs** (Ethan, Claire, etc.) - Mission-specific environments

## Prerequisites

- VirtualBox 7.0.4 or higher installed
- Sufficient disk space for VM files (~5-10 GB per VM)
- Download both VM packages (ZIP files)

---

## Installation Instructions

### Step 1: Download Required Files

Download the following ZIP packages:
1. **PlayerVM.zip** - Main player virtual machine
2. **Character VM packages** (e.g., Ethan_Medium_01.zip through Ethan_Hard_14.zip, Claire missions, etc.)

### Step 2: Extract PlayerVM

**Location:** `F:\VM-DRIVE (F)\SteamLibrary\steamapps\common\Sylvarcon 2049\redist\PlayerVM\`

1. Navigate to your game installation directory
2. Go to `redist` folder
3. Extract the **PlayerVM.zip** contents into the `PlayerVM` folder

**Expected structure:**
```
Sylvarcon 2049/
└── redist/
    └── PlayerVM/
        ├── installscript.vdf
        ├── testFile.txt
        └── VirtualBox-7.0.4-154605-Win.exe
```

### Step 3: Extract Character VMs (Ethan Example)

**Location:** `F:\VM-DRIVE (F)\SteamLibrary\steamapps\common\Sylvarcon 2049\` (root game directory)

1. Navigate to your game installation root directory
2. Extract character VM folders directly to the root

**Expected structure:**
```
Sylvarcon 2049/
├── Sylvarcon 2049.exe
├── Sylvarcon 2049_Data/
├── redist/
├── MonoBleedingEdge/
├── Ethan_Medium_01/
├── Ethan_Medium_02/
├── Ethan_Medium_03/
├── ...
├── Ethan_Hard_14/
├── Claire_Mission_01/
└── Claire_Mission_02/
```

⚠️ **Important:** Character VM folders must be in the game root directory, NOT inside subdirectories.

---

## Save Game Management

### Save File Location

**Path:** `F:\VM-DRIVE (F)\SteamLibrary\steamapps\common\Sylvarcon 2049\Sylvarcon 2049_Data\saves\`

The save files store your game progress, including:
- Campaign progression
- Completed missions
- Player statistics
- VM configurations

**Save file types:**
```
saves/
├── settings.sav           (2 KB) - Game settings
├── settingsTut.sav       (1 KB) - Tutorial settings
├── SLOT1.sav             (3 KB) - Save slot 1
├── SLOT2.sav             (3 KB) - Save slot 2
└── steam_autocloud.vdf   (1 KB) - Steam cloud sync
```

### Restoring Original Save Files

To continue from a specific point in the campaign:

1. Navigate to the saves folder:
   ```
   Sylvarcon 2049_Data\saves\
   ```

2. **Backup your current saves** (optional):
   ```powershell
   Copy-Item "saves" "saves_backup" -Recurse
   ```

3. Copy the original save files into the `saves` folder:
   - Replace `SLOT1.sav` and/or `SLOT2.sav` with the original files
   - Keep `settings.sav` for your personal preferences or replace it

4. Launch the game and load the corresponding slot

⚠️ **Note:** Overwriting save files will permanently replace your current progress unless you create a backup.

---

## Folder Structure Summary

Complete installation structure:

```
F:\VM-DRIVE (F)\SteamLibrary\steamapps\common\Sylvarcon 2049\
│
├── Sylvarcon 2049.exe                          [Game executable]
├── UnityCrashHandler64.exe
├── UnityPlayer.dll
├── steam_appid.txt
│
├── Sylvarcon 2049_Data\                        [Game data]
│   ├── saves\                                  [Save files - copy originals here]
│   │   ├── settings.sav
│   │   ├── SLOT1.sav
│   │   └── SLOT2.sav
│   └── ...
│
├── redist\                                     [Redistribution files]
│   ├── PlayerVM\                               [Extract PlayerVM.zip here]
│   │   ├── installscript.vdf
│   │   ├── testFile.txt
│   │   └── VirtualBox-7.0.4-154605-Win.exe
│   └── ...
│
├── MonoBleedingEdge\                           [Unity runtime]
│
├── Ethan_Medium_01\                            [Character VMs - extract in root]
├── Ethan_Medium_02\
├── Ethan_Medium_03\
├── ...
├── Ethan_Hard_14\
├── Claire_Mission_01\
└── Claire_Mission_02\
```

---

## Troubleshooting

### VM Not Found Error

**Problem:** Game shows "Virtual Machine not found" error

**Solution:**
- Verify character VM folders are in the game root directory
- Check folder names match exactly (case-sensitive)
- Ensure VirtualBox is installed from `redist\PlayerVM\VirtualBox-7.0.4-154605-Win.exe`

### Save File Issues

**Problem:** Cannot load saved game

**Solution:**
- Verify save files are in `Sylvarcon 2049_Data\saves\`
- Check file permissions (should not be read-only)
- Ensure save files are not corrupted (3 KB size is normal)

### Disk Space Issues

**Problem:** Not enough space for VMs

**Solution:**
- Each mission VM requires ~300-800 MB
- Ensure at least 10 GB free space on the installation drive
- Consider moving installation to a larger drive

---

## Additional Notes

- **First Launch:** The game will automatically configure VirtualBox settings on first run
- **Steam Cloud:** Save files can sync via Steam Cloud (requires `steam_autocloud.vdf`)
- **VM Performance:** Ensure VT-x/AMD-V virtualization is enabled in BIOS for optimal performance
- **Updates:** Character VM packages may be updated; check for new versions periodically

---

## Support

For technical issues or questions:
- Check game logs in `Sylvarcon 2049_Data\output_log.txt`
- Verify VirtualBox installation is working correctly
- Ensure all VM folders are extracted properly

---

## Legal Notice and Copyright

**© 2025 Sylvarcon 2049®. All Rights Reserved.**

Sylvarcon 2049® is a registered trademark. All game content, including but not limited to:
- Game software and executable files
- Virtual machine configurations and environments
- Graphics, audio, video, and multimedia assets
- Game design, storylines, characters, and mission content
- Documentation and instructional materials

are the exclusive property of the copyright holders and are protected by international copyright laws, trademark laws, and other intellectual property rights.

### License Terms

This software is licensed, not sold. By installing and using Sylvarcon 2049, you agree to:

- **Personal Use Only:** This game and its components are licensed for personal, non-commercial use only
- **No Redistribution:** You may not distribute, share, sell, lease, or sublicense any part of the game, including virtual machines, save files, or game assets
- **No Modification:** Reverse engineering, decompiling, disassembling, or modifying the game files is strictly prohibited
- **No Unauthorized Reproduction:** Making unauthorized copies of the game or any of its components is prohibited

### Violation of Terms

Unauthorized use, reproduction, distribution, or modification of this software may result in:
- Immediate termination of your license
- Civil and criminal penalties under applicable laws
- Legal action to protect intellectual property rights

### Warranty Disclaimer

This software is provided "AS IS" without warranty of any kind, either express or implied. The copyright holders shall not be liable for any damages arising from the use or inability to use this software.

### Contact Information

For licensing inquiries, permissions, or support:
- **Email:** contact@sylvarcon2049.com
- **Discord Community:** https://discord.com/invite/ujZCPCUSVD

---

**Version:** 1.0  
**Last Updated:** November 2025  
**Game Version:** Sylvarcon 2049 (Steam Edition)


# Sylvarcon 2049 - Complete Setup Guide Steam Legacy Version

# 📦 Legacy Version Setup (Standalone)

**This section is for users who want to play the original standalone version.**

⚠️ **IMPORTANT:** This is an **unsupported legacy version** provided "AS IS". It may contain bugs and is no longer actively maintained. We strongly recommend using the new platform at [www.sylvarcon2049.com](https://www.sylvarcon2049.com).

⚠️ **DISCLAIMER:** Use at your own risk. We assume no responsibility for any issues, damages, or data loss that may occur from using this legacy software.

---

## About This Legacy Version

This standalone version uses VirtualBox virtual machines to simulate hacking environments. Four main VM packages are available:
- **PlayerVM** - Contains Claire's challenges and the Kali Linux investigation machine
- **Ethan Easy Missions** - Ethan's easy difficulty missions
- **Ethan Medium Missions** - Ethan's medium difficulty missions  
- **Ethan Hard Missions** - Ethan's hard difficulty missions

All VMs are configured to communicate through a dedicated VirtualBox NAT Network called "Sylvarcon" on the 12.0.0.0/24 subnet.

**Note:** This is a standalone version that does NOT require Steam to play.

---

## Prerequisites for Legacy Version

- VirtualBox 7.0.4 or higher installed
- Sufficient disk space for VM files:
  - Linux VMs: ~15 GB each
  - Windows VMs: ~60 GB each
  - Total space needed: 100+ GB recommended for all missions
- 7-Zip or compatible archive tool to extract .7z files
- Download all legacy packages from **[www.sylvarcon2049.com](https://www.sylvarcon2049.com)** (legacy download section)

---

## Legacy Version Installation Instructions

### Step 1: Download Required Files

**Download Links Available at:** **[https://www.sylvarcon2049.com](https://www.sylvarcon2049.com)**

All game files and VM packages can be downloaded from the official website.

Download the following 7z packages:
1. **Sylvarcon 2049 Game Build** - Main game executable and files
2. **PlayerVM.7z** - Contains Claire's missions and Kali investigation VM
3. **Ethan_Easy.7z** - All Ethan easy difficulty missions
4. **Ethan_Medium.7z** - All Ethan medium difficulty missions
5. **Ethan_Hard.7z** - All Ethan hard difficulty missions

⚠️ **Note:** Visit [[www.sylvarcon2049.com](https://1drv.ms/f/c/247d16c23b691d87/IgCp8RAvYTiNTY_krJbL4ymiAWoBGjbUlJVMRFLfDc51Ze4?e=fWoN0K)]([https://www.sylvarcon2049.com](https://1drv.ms/f/c/247d16c23b691d87/IgCp8RAvYTiNTY_krJbL4ymiAWoBGjbUlJVMRFLfDc51Ze4?e=fWoN0K)) to access the download section. All packages are hosted on the official website.

### Step 2: Extract PlayerVM

**Location:** `Sylvarcon 2049\redist\PlayerVM\`

1. Navigate to your Sylvarcon 2049 installation directory
2. Go to `redist` folder
3. Extract the **PlayerVM.7z** contents into the `PlayerVM` folder using 7-Zip

**Expected structure:**
```
Sylvarcon 2049/
└── redist/
    └── PlayerVM/
        ├── installscript.vdf
        ├── testFile.txt
        ├── VirtualBox-7.0.4-154605-Win.exe
        ├── Claire_Mission_XX/
        └── Sylvarcon-2049/ (Kali Linux VM)
```

### Step 3: Extract Ethan Mission Packages

**Location:** `Sylvarcon 2049\` (root game directory)

1. Navigate to your Sylvarcon 2049 installation root directory
2. Extract each Ethan mission package directly to the root:
   - Extract **Ethan_Easy.7z** 
   - Extract **Ethan_Medium.7z**
   - Extract **Ethan_Hard.7z**

**Expected structure:**
```
Sylvarcon 2049/
├── Sylvarcon 2049.exe
├── Sylvarcon 2049_Data/
├── redist/
├── MonoBleedingEdge/
├── Ethan_Easy_01/
├── Ethan_Easy_02/
├── ...
├── Ethan_Medium_01/
├── Ethan_Medium_02/
├── ...
├── Ethan_Hard_01/
├── Ethan_Hard_02/
└── ...
```

⚠️ **Important:** Ethan mission VM folders must be in the game root directory, NOT inside subdirectories.

---

## VirtualBox NAT Network Configuration

The game requires a specific VirtualBox NAT Network for VM communication. The game automatically creates this network, but you can also configure it manually if needed.

### Automatic Configuration

On first launch, the game will automatically:
1. Create a NAT Network named "Sylvarcon"
2. Configure it with network range 12.0.0.0/24
3. Enable DHCP for automatic IP assignment
4. Start the network

### Manual Configuration Steps

If you need to configure the network manually or troubleshoot network issues:

#### Using VBoxManage (Command Line)

1. Open PowerShell or Command Prompt as Administrator

2. Navigate to VirtualBox installation folder:
   ```powershell
   cd "C:\Program Files\Oracle\VirtualBox"
   ```

3. Remove any existing "Sylvarcon" network (if present):
   ```powershell
   .\VBoxManage.exe natnetwork remove --netname Sylvarcon
   ```

4. Create the Sylvarcon NAT Network:
   ```powershell
   .\VBoxManage.exe natnetwork add --netname Sylvarcon --network "12.0.0.0/24" --enable --dhcp on
   ```

5. Start the network:
   ```powershell
   .\VBoxManage.exe natnetwork start --netname Sylvarcon
   ```

6. Verify the network was created successfully:
   ```powershell
   .\VBoxManage.exe list natnets
   ```

   Expected output should show:
   ```
   NetworkName: Sylvarcon
   Network:     12.0.0.0/24
   Gateway:     12.0.0.1
   IPv6:        No
   Enabled:     Yes
   ```

#### Using VirtualBox GUI

1. Open VirtualBox Manager
2. Go to **File** → **Preferences** (or **Tools** → **Network**)
3. Select the **Network** tab
4. Click on **NAT Networks**
5. Click the **+** button to add a new NAT Network
6. Configure the network:
   - **Network Name:** Sylvarcon
   - **Network CIDR:** 12.0.0.0/24
   - **Enable DHCP:** ✓ Checked
   - **Supports IPv6:** (Optional)
7. Click **OK** to save

### Verifying Network Configuration

After configuration, verify that:
- The network "Sylvarcon" appears in VirtualBox NAT Networks list
- Network is enabled (Status: Yes)
- All mission VMs are configured to use this network
- DHCP is enabled for automatic IP assignment

### Troubleshooting Network Issues

**Problem:** VMs cannot communicate with each other

**Solution:**
- Verify all VMs are using the "Sylvarcon" NAT Network (not "NAT" adapter)
- Restart the Sylvarcon network: `VBoxManage natnetwork stop --netname Sylvarcon` then `VBoxManage natnetwork start --netname Sylvarcon`
- Check VirtualBox is not blocked by Windows Firewall
- Ensure virtualization (VT-x/AMD-V) is enabled in BIOS

**Problem:** Network creation fails

**Solution:**
- Run VBoxManage as Administrator
- Remove any conflicting networks with similar IP ranges
- Restart VirtualBox service: `services.msc` → Find "VirtualBox" services → Restart

---

## Save Game Management

### Save File Location

**Path:** `Sylvarcon 2049\Sylvarcon 2049_Data\saves\`

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
└── steam_autocloud.vdf   (1 KB) - Steam cloud config (not used in standalone version)
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
Sylvarcon 2049\
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
│   ├── PlayerVM\                               [Extract PlayerVM.7z here]
│   │   ├── installscript.vdf
│   │   ├── testFile.txt
│   │   ├── VirtualBox-7.0.4-154605-Win.exe
│   │   ├── Claire_Mission_XX\
│   │   └── Sylvarcon-2049\                     [Kali Linux investigation VM]
│   └── ...
│
├── MonoBleedingEdge\                           [Unity runtime]
│
├── Ethan_Easy_01\                              [Extract from Ethan_Easy.7z]
├── Ethan_Easy_02\
├── ...
├── Ethan_Medium_01\                            [Extract from Ethan_Medium.7z]
├── Ethan_Medium_02\
├── ...
├── Ethan_Hard_01\                              [Extract from Ethan_Hard.7z]
├── Ethan_Hard_02\
└── ...
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
- Linux mission VMs require approximately 15 GB each when extracted
- Windows mission VMs require approximately 60 GB each when extracted
- Total space needed: 100+ GB for all missions (varies by mission count)
- Ensure at least 150 GB free space on the installation drive for optimal performance
- Consider moving installation to a larger drive or external SSD
- Delete unused mission VMs to free up space if needed

### Network Communication Issues

**Problem:** VMs cannot connect to each other

**Solution:**
- Verify the "Sylvarcon" NAT Network exists in VirtualBox
- Check that all VMs are configured to use NAT Network (not regular NAT)
- Restart the Sylvarcon network (see NAT Network Configuration section)
- Ensure Windows Firewall allows VirtualBox

### 7-Zip Extraction Issues

**Problem:** Cannot extract .7z files

**Solution:**
- Download and install 7-Zip from https://www.7-zip.org/
- Right-click the .7z file → 7-Zip → Extract Here
- Ensure sufficient disk space before extraction
- Verify downloaded files are not corrupted (check file size)

---

## Additional Notes

- **⚠️ LEGACY VERSION:** This is an unsupported version that may contain bugs and is provided without any warranties
- **Standalone Version:** This version does NOT require Steam. Launch the game directly from `Sylvarcon 2049.exe`
- **No Support:** No technical support, updates, or bug fixes will be provided for this version
- **Use at Own Risk:** Users assume all responsibility for any issues that may arise
- **Backup Recommended:** Always backup your system and data before installation
- **First Launch:** The game will automatically configure VirtualBox settings on first run
- **Save Files:** All progress is saved locally in the `saves` folder (no cloud sync in standalone version)
- **VM Performance:** Ensure VT-x/AMD-V virtualization is enabled in BIOS for optimal performance
- **Disk Space:** VMs are resource-intensive. Linux VMs (~15 GB) and Windows VMs (~60 GB) require significant storage
- **Storage Recommendations:** Use an SSD for better VM performance and faster loading times
- **Updates:** Character VM packages may be updated; check for new versions periodically (no guarantee of availability)

---

## Support

**⚠️ NO OFFICIAL SUPPORT PROVIDED FOR THIS VERSION ⚠️**

This is an unsupported legacy release. No technical support, updates, or bug fixes will be provided.

**🎯 Want Full Support and New Features?**

Upgrade to the new version at **[www.sylvarcon2049.com](https://www.sylvarcon2049.com)** for:
- Active technical support
- Professional skills certification
- New challenges and content
- Regular updates and improvements
- Steam players can upgrade to Premium by validating their license

For community assistance or general questions about this legacy version:
- **Discord Community:** https://discord.com/invite/ujZCPCUSVD
- **Email:** contact@sylvarcon2049.com (inquiries only, no support guaranteed)

If you encounter issues with this legacy version:
- Check game logs in `Sylvarcon 2049_Data\output_log.txt`
- Verify VirtualBox installation is working correctly
- Ensure all VM folders are extracted properly
- Seek help from the community (no official support available)

**Remember:** You use this software at your own risk and responsibility.

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

**ADDITIONAL LIABILITY DISCLAIMER:**

- This is an **UNSUPPORTED LEGACY VERSION** no longer under active maintenance or support
- The software **MAY CONTAIN BUGS, ERRORS, OR COMPATIBILITY ISSUES**
- Use of this software is **ENTIRELY AT YOUR OWN RISK**
- We assume **NO RESPONSIBILITY OR LIABILITY** for:
  - Any damage to your computer, hardware, or virtual machines
  - Data loss or corruption
  - System instability or crashes
  - Compatibility issues with your operating system or hardware
  - Performance issues or security vulnerabilities
  - Any other direct, indirect, incidental, or consequential damages
- **NO TECHNICAL SUPPORT** is provided for this version
- Users are **SOLELY RESPONSIBLE** for:
  - Backing up their data before installation
  - Ensuring system compatibility
  - Any consequences of using this software
  - Compliance with all applicable laws and regulations

By using this software, you acknowledge and accept all risks and agree to hold the copyright holders harmless from any and all claims, damages, or liabilities.

### Contact Information

For licensing inquiries, permissions, or general information:
- **Website:** https://www.sylvarcon2049.com (New version available here!)
- **Email:** contact@sylvarcon2049.com
- **Discord Community:** https://discord.com/invite/ujZCPCUSVD

**Upgrade to Premium:** Steam players can validate their license at www.sylvarcon2049.com for exclusive Premium access.

---

**Legacy Version:** 1.0 (Unsupported)  
**Last Updated:** November 2025  
**Game Version:** Sylvarcon 2049 (Standalone Edition - No Steam Required)  
**Status:** ⚠️ UNSUPPORTED - USE AT YOUR OWN RISK ⚠️

---

## 🌟 Remember: The New Version Awaits!

**For the best Sylvarcon 2049 experience with full support, new features, and professional certifications:**

👉 **Visit [www.sylvarcon2049.com](https://www.sylvarcon2049.com)**

Steam players get **FREE Premium upgrade**!

# Sylvarcon 2049 - Complete Setup Guide (Steam Legacy Version)

> [!TIP]
> **🔄 NEW: Retrocompatibility & Web Platform Option**
>
> **Prefer not to install this unsupported legacy version?**
>
> We have introduced **retrocompatibility** on the official platform at **[www.sylvarcon2049.com](https://www.sylvarcon2049.com)**. We'll open registration very soon, stay tuned. 
>
> You can now access the legacy content directly on the new platform with fully integrated features:
> * **Mission Descriptions:** View full details within the modern interface.
> * **Flag Submission:** Enter flags directly on the web.
> * **Hint System:** Consult clues and hints if you get stuck.
> * **Integrated Questions:** Answer mission questions seamlessly.
>
> **⚠️ NOTE ON SCORING:** Since this legacy material is considered "open/released," completing these missions on the official platform **will not count towards your ranking points or score**. However, using the web platform allows you to enjoy the content in a stable, maintained environment without needing to perform the complex setup described below.

---

# 📦 Legacy Version Setup (Standalone)

**This section is for users who want to play the original standalone version locally.**

> [!WARNING]
> **UNSUPPORTED SOFTWARE**  
> This is an **unsupported legacy version** provided "AS IS". It may contain bugs and is no longer actively maintained. We strongly recommend using the new platform at [www.sylvarcon2049.com](https://www.sylvarcon2049.com).

> [!CAUTION]
> **DISCLAIMER:** Use at your own risk. We assume no responsibility for any issues, damages, or data loss that may occur from using this legacy software.

---

## About This Legacy Version

This standalone version uses VirtualBox virtual machines to simulate hacking environments. Four main VM packages are available:

- **PlayerVM** – Contains Claire's challenges and the Kali Linux investigation machine.
- **Ethan Easy Missions** – Ethan's easy difficulty missions.
- **Ethan Medium Missions** – Ethan's medium difficulty missions.
- **Ethan Hard Missions** – Ethan's hard difficulty missions.

All VMs are configured to communicate through a dedicated VirtualBox NAT Network called **"Sylvarcon"** on the `12.0.0.0/24` subnet.

**Note:** This is a standalone version that does **NOT** require Steam to play.

---

## Prerequisites

- **VirtualBox 7.0.4** or higher installed.
- **Sufficient disk space** for VM files:
  - Linux VMs: ~15 GB each.
  - Windows VMs: ~60 GB each.
  - **Total space needed:** 100+ GB recommended for all missions.
- **7-Zip** or compatible archive tool to extract `.7z` files.
- **Legacy Packages:** Download from the OneDrive folder below.

📥 **[OneDrive – Sylvarcon 2049 Legacy Packages](https://1drv.ms/f/c/247d16c23b691d87/IgCp8RAvYTiNTY_krJbL4ymiAWoBGjbUlJVMRFLfDc51Ze4?e=fWoN0K)**

---

## Installation Instructions

### Step 1: Download Required Files

**Download Links Available at:** **[https://www.sylvarcon2049.com](https://www.sylvarcon2049.com)**

All game files and VM packages can be downloaded from the official website or the OneDrive link above.

Download the following `.7z` packages:

1. **Sylvarcon 2049 Game Build** – Main game executable and files.  
2. **PlayerVM.7z** – Contains Claire's missions and Kali investigation VM.  
3. **Ethan_Easy.7z** – All Ethan easy difficulty missions.  
4. **Ethan_Medium.7z** – All Ethan medium difficulty missions.  
5. **Ethan_Hard.7z** – All Ethan hard difficulty missions.  

---

### Step 2: Extract PlayerVM

**Target Location:** `Sylvarcon 2049\redist\PlayerVM\`

1. Navigate to your Sylvarcon 2049 installation directory.  
2. Go to the `redist` folder.  
3. Extract the **PlayerVM.7z** contents into the `PlayerVM` folder using 7-Zip.

**Expected structure:**

```text
Sylvarcon 2049/
└── redist/
    └── PlayerVM/
        ├── installscript.vdf
        ├── testFile.txt
        ├── VirtualBox-7.0.4-154605-Win.exe
        ├── Claire_Mission_XX/
        └── Sylvarcon-2049/      (Kali Linux VM)
```text

---
Step 3: Extract Ethan Mission Packages
Target Location: Sylvarcon 2049\ (root game directory)
Navigate to your Sylvarcon 2049 installation root directory.

Extract each Ethan mission package directly to the root:
Extract Ethan_Easy.7z
Extract Ethan_Medium.7z
Extract Ethan_Hard.7z

Expected structure:
Sylvarcon 2049/
├── Sylvarcon 2049.exe
├── Sylvarcon 2049_Data/
├── redist/
├── MonoBleedingEdge/
├── Ethan_Easy_01/
├── Ethan_Medium_01/
├── Ethan_Hard_01/
└── ...
---

[!IMPORTANT]
Ethan mission VM folders must be in the game root directory, NOT inside subdirectories.
VirtualBox NAT Network Configuration
The game requires a specific VirtualBox NAT Network for VM communication.
Automatic Configuration
On first launch, the game will automatically:
Create a NAT Network named "Sylvarcon".
Configure it with network range 12.0.0.0/24.
Enable DHCP.
Start the network.
Manual Configuration Steps (PowerShell)
If you need to configure manually or troubleshoot:
Open PowerShell as Administrator.
Run the following commands:
<!-- end list -->

# Navigate to VirtualBox folder
cd "C:\Program Files\Oracle\VirtualBox"

# Remove existing network (if needed)
.\VBoxManage.exe natnetwork remove --netname Sylvarcon

# Create the Sylvarcon NAT Network
.\VBoxManage.exe natnetwork add --netname Sylvarcon --network "12.0.0.0/24" --enable --dhcp on

# Start the network

.\VBoxManage.exe natnetwork start --netname Sylvarcon

# Verify configuration
.\VBoxManage.exe list natnets

Expected Output:

NetworkName: Sylvarcon
Network:     12.0.0.0/24
Gateway:     12.0.0.1
IPv6:        No
Enabled:     Yes

---
Save Game Management
Path: Sylvarcon 2049\Sylvarcon 2049_Data\saves\
The save files store campaign progression, statistics, and VM configs.
Restoring Original Save Files
To continue from a specific point:
Navigate to Sylvarcon 2049_Data\saves\.
Backup your current saves (optional).
Copy the original save files into the saves folder:
Replace SLOT1.sav or SLOT2.sav.
Keep settings.sav for preferences.
Launch the game.
[!NOTE]
Overwriting save files will permanently replace your current progress unless you create a backup.

---
Troubleshooting

Problem Possible Solution
VM Not Found Error Verify character VM folders are in the game root directory. Check folder names match exactly (case-sensitive).
Save File Issues Verify save files are in Sylvarcon 2049_Data\saves\ and permissions are not read-only.
Disk Space Issues Linux VMs need ~15 GB; Windows VMs need ~60 GB. Ensure 150GB+ free space for optimal performance.
Network Issues Verify "Sylvarcon" NAT Network exists. Restart it via VBoxManage. Check Windows Firewall.
7-Zip Issues Use the latest 7-Zip. Ensure download isn't corrupted. Check disk space before extracting.

Legal Notice and Copyright
© 2025 Sylvarcon 2049®. All Rights Reserved.
Sylvarcon 2049® is a registered trademark. All game content is the exclusive property of the copyright holders.
License Terms
This software is licensed, not sold.
Personal Use Only: Licensed for personal, non-commercial use.
No Redistribution: You may not distribute, share, or sell game assets/VMs.
No Modification: Reverse engineering is prohibited.
Warranty Disclaimer
[!WARNING]
NO WARRANTY
This software is provided "AS IS" without warranty of any kind. The copyright holders shall not be liable for any damages arising from the use or inability to use this software.
ADDITIONAL LIABILITY DISCLAIMER:
This is an UNSUPPORTED LEGACY VERSION.
The software MAY CONTAIN BUGS.
Use is ENTIRELY AT YOUR OWN RISK.
We assume NO RESPONSIBILITY for damage to hardware, data loss, or system instability.
Support
⚠️ NO OFFICIAL SUPPORT PROVIDED FOR THIS VERSION ⚠️
This is an unsupported legacy release. No technical support, updates, or bug fixes will be provided.
🎯 Want Full Support and New Features?
Upgrade to the new version at www.sylvarcon2049.com for active support, certifications, and new challenges.
Community Assistance:
Discord: https://discord.com/invite/ujZCPCUSVD
Email: contact@sylvarcon2049.com (inquiries only)
Legacy Version: 1.0 (Unsupported)
Last Updated: November 2025
Game Version: Standalone Edition
Status: ⚠️ UNSUPPORTED - USE AT YOUR OWN RISK ⚠️


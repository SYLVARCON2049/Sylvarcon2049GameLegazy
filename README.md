# Sylvarcon 2049 - Complete Setup Guide (Steam Legacy Version)

> [!TIP]
> **🔄 NEW: Retrocompatibility & Web Platform Option**
>
> **Prefer not to install this unsupported legacy version?**
>
> We have introduced **retrocompatibility** on the official platform at **[www.sylvarcon2049.com](https://www.sylvarcon2049.com)**.
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

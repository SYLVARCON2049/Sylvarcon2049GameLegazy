# Sylvarcon 2049 - Legacy Version Setup Guide

> [!TIP]
> **NEW: Retrocompatibility & Web Platform Option**
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
> **NOTE ON SCORING:** Since this legacy material is considered "open/released," completing these missions on the official platform **will not count towards your ranking points or score**. However, it allows you to enjoy the content in a stable environment without the complex setup below.

---

# 📦 Legacy Version Setup (Standalone)

**This section is for users who want to play the original standalone version locally.**

> [!WARNING]
> **UNSUPPORTED SOFTWARE**
> This is an **unsupported legacy version** provided "AS IS". It may contain bugs and is no longer actively maintained. We strongly recommend using the new platform.

> [!CAUTION]
> **DISCLAIMER:** Use at your own risk. We assume no responsibility for any issues, damages, or data loss that may occur from using this legacy software.

## About This Legacy Version

This standalone version uses VirtualBox virtual machines to simulate hacking environments. Four main VM packages are available:
- **PlayerVM** - Contains Claire's challenges and the Kali Linux investigation machine
- **Ethan Easy Missions** - Ethan's easy difficulty missions
- **Ethan Medium Missions** - Ethan's medium difficulty missions
- **Ethan Hard Missions** - Ethan's hard difficulty missions

All VMs are configured to communicate through a dedicated VirtualBox NAT Network called "Sylvarcon" on the `12.0.0.0/24` subnet.

**Note:** This is a standalone version that does NOT require Steam to play.

---

## Prerequisites

* **VirtualBox 7.0.4** or higher installed.
* **Sufficient disk space** (100+ GB recommended for all missions).
    * Linux VMs: ~15 GB each.
    * Windows VMs: ~60 GB each.
* **7-Zip** or compatible archive tool.
* **Legacy Packages:** Download from the OneDrive folder below.

📥 **[OneDrive – Sylvarcon 2049 Legacy Packages](https://1drv.ms/f/c/247d16c23b691d87/IgCp8RAvYTiNTY_krJbL4ymiAWoBGjbUlJVMRFLfDc51Ze4?e=fWoN0K)**

---

## Installation Instructions

### Step 1: Download Required Files

**Download Links Available at:** **[https://www.sylvarcon2049.com](https://www.sylvarcon2049.com)**

Download the following 7z packages:
1.  **Sylvarcon 2049 Game Build** - Main game executable.
2.  **PlayerVM.7z** - Claire's missions & Kali VM.
3.  **Ethan_Easy.7z** - Ethan easy missions.
4.  **Ethan_Medium.7z** - Ethan medium missions.
5.  **Ethan_Hard.7z** - Ethan hard missions.

### Step 2: Extract PlayerVM

**Target Location:** `Sylvarcon 2049\redist\PlayerVM\`

1.  Navigate to your `Sylvarcon 2049` installation directory.
2.  Go to `redist` folder.
3.  Extract **PlayerVM.7z** here.

**Expected structure:**
```text
Sylvarcon 2049/
└── redist/
    └── PlayerVM/
        ├── installscript.vdf
        ├── testFile.txt
        ├── VirtualBox-7.0.4-154605-Win.exe
        ├── Claire_Mission_XX/
        └── Sylvarcon-2049/ (Kali Linux VM)

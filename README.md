# Universal Windows Installer

Universal Windows Installer is a lightweight, fast, and versatile setup utility designed to deploy multiple Windows NT family operating systems — from NT 3.1 to Windows 11 — within seconds. It supports both modern and legacy systems, making multi-version Windows installation easier and more accessible.

---

## Features

- **Supports a wide range of Windows NT versions:** NT 3.1, NT 3.5, NT 3.51, NT 4.0, Windows 2000, Windows XP (x86 & x64), Windows Vista, Windows 7, Windows 8.0 via regular installation, and Windows 8.1, 10, 11 via Custom Installation, both vanilla and patched editions where applicable.
- **Fast installation:** Deploys OS setups in just a few seconds.
- **Compatible with modern and legacy hardware:** Supports numerous controllers and patches.
- **Modern and Legacy boot modes:** Choose between Modern and Legacy installer modes right at startup, before setup begins.
- **Multiple bootloaders supported:** Installs and configures BOOTMGR, NTLDR or FreeLdr as the MBR bootloader depending on the target OS.
- **Built-in disk utilities:** Includes an MBR/GPT converter, a CHS/LBA converter, and an MBR viewer/fix tool for inspecting and repairing boot records.
- **Open Source:** Licensed under GNU GPLv3 for maximum "open-source" freedom.
- **Cross-platform ISO build:** Supports building bootable ISO images using syslinux (vmlinuz + core.gz) that work on both Linux and Windows systems.
- **Bootable ISO creation:** The folder contents can be directly converted into a bootable ISO file ready for writing to USB or CD/DVD, and can also be deployed via Ventoy.

---

## Important Notes
- All operating systems used, including Windows®, are trademarks of Microsoft Corporation. This product is not endorsed or affiliated with Microsoft Corporation.
- This project is in **BETA** stage. Not responsible for any data loss, damage, or malfunction. Use at your own risk.
- Installer only supports Legacy Boot/CSM mode. If you want to use the installer in a computer which does not support Legacy Boot/CSM mode, look at the cool project [CSMWrap](https://github.com/FlyGoat/csmwrap) made by [FlyGoat](https://github.com/FlyGoat). It enables CSM support even on UEFI Class 3 systems. But it's still beta and may not work.
- Readme file will contain more information in the future.
- Support for DOS-based operating systems is planned for an upcoming release.
- Regular installation is supported up to Windows 8.0. Deploying Windows 8.1, 10 or 11 requires **Custom Installation** mode.
- Don't hesitate to report any issues you find. I will try to fix them as best as I can, whenever I get free time.
- [Original repository](https://github.com/ages2001/Universal-NT-Installer) developed by ages2001.

---

## System Requirements for Universal Windows Installer

- CPU: At least i486
- RAM: 64 MiB of memory
- Disk: MBR/GPT/SGI/SUN scheme and compatible hard disk controller supported by Tiny Core Linux
- Installation media: USB or CD/DVD at least 2.5 GiB
- Media writer: **Rufus 3.10** and **SysLinux 6.03** are required to properly prepare bootable media for Universal Windows Installer v0.3.0. **Ventoy** is also supported as an alternative to writing a dedicated ISO each time.

**NOTE:** For x64 OSes, x86-64 (EM64T) capable CPU is required!

---

## OS Requirements and Patches

### Windows NT 3.1 (Vanilla)
- **Controller**: IDE or SATA (IDE)
- **IRQ Assignment**: Disk controller must be assigned to IRQ 14
- **Position**: Primary master (channel 0, position 0) for PATA IDE, SATA first port (port 0) for SATA IDE
- **Filesystem**: FAT12 or FAT16 CHS
- **Disk Layout**: Entire partition must be within first 8.3 GB (CHS-accessible)

### Windows NT 3.50 / 3.51 (Vanilla)
- **Controller**: IDE, SATA (IDE) or NVMe
- **Position**: Primary or secondary master (channel 0 or 1, position 0) for PATA IDE 
- **Filesystem**: FAT12 or FAT16 CHS
- **Disk Layout**: Entire partition must be within first 8.3 GB (CHS-accessible)

### Windows NT 3.51 (Patched)
- **Controller**: IDE, SATA (IDE), NVMe or AHCI
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA
- **Patches Applied**: UniATA, FAT32

### Windows NT 4.00 (Vanilla)
- **Controller**: IDE or SATA (IDE)
- **Filesystem**: FAT12, FAT16 CHS/LBA, or NTFS
- **Disk Layout**: Must reside within first 137.4 GB of disk

### Windows NT 4.00 (Patched)
- **Controller**: IDE, SATA (IDE), NVMe or AHCI
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA NTFS
- **Patches Applied**: UniATA, FAT32, USB 1.x/2.0, SSE/SSE2, ext2/3, HPFS

### Windows 2000 (Vanilla)
- **Controller**: IDE or SATA (IDE)
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA or NTFS
- **Free Space**: At least 650 MiB

### Windows 2000 (Patched)
- **Controller**: IDE, SATA (IDE), AHCI or NVMe
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA, NTFS or ext2/3
- **Free Space**: At least 980 MiB
- **Patches Applied**: ACPI, USB 1.x/2.0/3.x, AHCI, NVMe, exFAT, ext2/3, HPFS

### Windows XP (Vanilla)
- **Controller**: IDE or SATA (IDE)
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA or NTFS

### Windows XP (Patched)
- **Controller**: IDE, SATA (IDE), AHCI, RAID, eMMC or NVMe
- **Filesystem**: FAT12, FAT16 CHS/LBA, FAT32 CHS/LBA, NTFS, BTRFS or ext2/3
- **Patches Applied**: ACPI, USB 3.x, AHCI, RAID, eMMC, NVMe, ext2/3, BTRFS, AVX/AVX2 (x86 only), HPFS (x86 only)

### Windows Vista
- **Controller**: IDE, SATA (IDE), NVMe (for only patched ediitons) or AHCI
- **Filesystem**: NTFS
- **Patches Applied**: ACPI, USB 3.x, AHCI, RAID, eMMC, NVMe, ext2/3, BTRFS, HPFS (x86 only)

### Windows 7
- **Controller**: IDE, SATA (IDE), NVMe (for only patched ediitons) or AHCI
- **Filesystem**: NTFS
- **Patches Applied**: ACPI, USB 3.x, AHCI, RAID, eMMC, NVMe, ext2/3, BTRFS, HPFS (x86 only)

### Windows 8.0
- **Controller**: IDE, SATA (IDE), NVMe or AHCI
- **Filesystem**: NTFS, exFAT
- **Patches Applied**: ACPI, USB 3.x, AHCI, RAID, eMMC, NVMe, ext2/3, BTRFS, HPFS (x86 only), CPU Features Patch (x86 only)

---

### Bootloaders and Disk Tools
- **MBR Bootloader Selection**: Depending on the target OS, the installer sets up **BOOTMGR** (Vista/7), **NTLDR** (2000/XP) or **FreeLdr** as the MBR bootloader.
- **MBR/GPT Converter**: Convert a disk between MBR and GPT partitioning schemes from within the installer.
- **CHS/LBA Converter**: Convert partition addressing between CHS and LBA where the target OS requires it.
- **MBR Viewer/Fix**: Inspect the current Master Boot Record and repair a damaged or missing one.

---

### Notes
- **Drivers for booting**: Successful installation cannot be guaranteed in all cases, as driver-related issues may arise.
- **CHS and LBA**: CHS (Cylinder-Head-Sector) addressing is required for early NT editions and mandates small partition sizes.
- **Boot Partition**: Must exist and be a primary, supported filesystem (FAT12/FAT16/FAT32/NTFS).
- **exFAT Filesystem**: Windows 2000 Patched and Windows XP Vanilla/Patched (x86/x64) can read and write an exFAT partition but cannot boot from it because NTLDR cannot recognize exFAT partitions. So, you cannot install it to exFAT partition. However, you can create/delete/format exFAT partitions using Partition Editor/Formatter.

---

## Getting Started

### Prerequisites

- A Linux or Windows environment capable of running ISO building tools supporting syslinux (e.g. `genisoimage`, `mkisofs`, `xorriso`, `mkisofs.exe`).
- Access to the required OS `.tar.gz` archives (see below).

### Important Note on `.tar.gz` Archives

The actual OS image archives (`.tar.gz`) **are not included** in this repository due to their large size. The ISO files can be downloaded from the [Releases](https://github.com/ages2001/Universal-NT-Installer/releases) section.

Please extract these archives from the ISO files available in the [Releases](https://github.com/ages2001/Universal-NT-Installer/releases) and place them inside the `osfiles/` directory before running the installer.

To keep the repository lightweight, all `.tar.gz` files in `osfiles/` are **ignored by Git**.

---

## Installation Instructions

The installation process consists of booting the target PC from a prepared ISO file written onto a bootable USB drive or CD/DVD.

- Download the ISO file from the [Releases](https://github.com/ages2001/Universal-NT-Installer/releases) section.
- Write the ISO to a USB drive (minimum 2.5 GB) using a tool like **Rufus** (Windows), **Ventoy**, or appropriate software on Linux.
- Alternatively, burn the ISO to a CD/DVD.
- Boot the target PC from the USB or CD/DVD media.
- Before the installer starts, choose between **Modern** and **Legacy** mode depending on the target system and OS you're installing.
- Follow the on-screen instructions to install the desired Windows NT version.

No additional setup on the target PC is needed beyond booting from the prepared media.

---

## ISO Building Instructions

If you want to build or customize the bootable ISO yourself from the repository files, follow the guidelines below.

---

### Linux/WSL

You need to have ISO creation tools that support the syslinux bootloader such as:

- `genisoimage` and `mkisofs` (preferred)
- `xorriso` (alternative)
- `syslinux` (for bootloader binaries like `isolinux.bin`, `vmlinuz`, `core.gz`)

#### Step-by-step Instructions

1. **Clone the repository**:

   ```bash
   git clone https://github.com/ages2001/Universal-NT-Installer.git
   cd Universal-NT-Installer
   ```

2. **Download and extract the OS files**:

   - Go to the [Releases](https://github.com/ages2001/Universal-NT-Installer/releases) page.
   - Download any ISO file available.
   - Extract the ISO using any archive manager (e.g. `7z`, `bsdtar`, or a GUI tool).
   - Copy the contents of the extracted `osfiles/` folder into your local `osfiles/` directory in the repository.

   Example:

   ```bash
   cp -r extracted_folder/osfiles/* ./osfiles/
   ```

3. **Build the ISO**:

   Once the folder structure is complete, run:

   ```bash
   sudo mkisofs -o ../Universal_NT_Installer.iso \
     -b boot/isolinux/isolinux.bin \
     -c boot/isolinux/boot.cat \
     -no-emul-boot -boot-load-size 4 -boot-info-table \
     -J -R -V "UNVNTINSTLR" .
   ```

   This will generate `Universal_NT_Installer.iso` in the parent directory using the current folder's contents.

---

### Windows

For Windows users, an unofficial port of `mkisofs.exe` is available in tools like:

- **Cygwin**
- **MinGW**
- Standalone distributions (e.g. part of `cdrtools`)

However, ISO generation on Windows using `mkisofs.exe` has **not been fully tested** with Universal Windows Installer and may result in boot or file structure issues. For best results, we recommend using a Linux environment or **WSL** (Windows Subsystem for Linux).

You may follow the similar steps as above in Linux/WSL to build the ISO.

## Preparing Bootable Media

- Use the ISO file from the Releases section.
- Minimum USB or CD/DVD size: 2.5 GB.
- For USB, tools like **Rufus** (Windows) or `dd` (Linux) can be used. USB partition must be formatted with FAT16 or FAT32.
- For CD/DVDs, use any standard burning software like UltraISO etc.
- Boot the target machine from the USB or CD/DVD to start installation.

---

## License

This project is licensed under the **GNU General Public License v3 (GPLv3)** — see the [LICENSE](LICENSE) file for details.

---

*“Universal Windows Installer makes old and new Windows setups easy and fast, all in one place.”*

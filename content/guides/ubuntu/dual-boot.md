---
title: "Install Ubuntu LTS Server Dual-Booted alongside Windows"
socialImage: "#https://labs.workflare.in/thumbs/#"
description: "A comprehensive guide to dual-booting (sideloading) Ubuntu LTS Server (non-GUI) on a machine running Windows."
date: 2026-07-20
ytUrl: "#"
---

# Install Ubuntu LTS Server Dual-Booted alongside Windows

Dual-booting (sideloading) allows you to install Ubuntu LTS Server on a secondary partition on your Windows computer, allowing you to choose which operating system to run at boot. Since this is the Server variant, it installs a non-GUI command-line interface.

> [!WARNING]
> Modifying disk partitions carries a risk of data loss. Back up all important data on Windows before proceeding.

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- #

## Prerequisites

Before starting, ensure you have:
- [ ] A PC running Windows 10 or 11.
- [ ] A USB flash drive (8GB or larger).
- [ ] At least 30GB of free space on your main drive (SSD/HDD).
- [ ] A backup of your important files.

## Installation & Configuration

### Step 1: Download the Ubuntu LTS Server ISO
1. Navigate to the official [Ubuntu Server download page](https://ubuntu.com/download/server).
2. Download the latest **Ubuntu Server LTS** ISO file (e.g., Ubuntu 24.04 LTS).

### Step 2: Create a Bootable USB Drive
1. Download a tool like [Rufus](https://rufus.ie/) on Windows.
2. Insert your USB flash drive.
3. Open Rufus, select your USB drive under "Device", and choose the downloaded Ubuntu Server ISO under "Boot selection".
4. Keep the partition scheme as **GPT** (highly recommended for modern UEFI systems) and click **START** to write the ISO to the USB.

### Step 3: Shrink Your Windows Partition
1. Right-click the Start Menu and select **Disk Management**.
2. Right-click your main Windows partition (usually `C:`) and select **Shrink Volume**.
3. Enter the amount of space to shrink in MB (e.g., `30720` for 30GB) and click **Shrink**.
4. You will see an area of **Unallocated Space** on your disk. Leave it as is; the Ubuntu installer will use this space.

### Step 4: Disable Windows Fast Startup
1. Open the Control Panel, go to **Power Options** -> **Choose what the power buttons do**.
2. Click **Change settings that are currently unavailable**.
3. Uncheck **Turn on fast startup** and save changes (Fast Startup prevents Ubuntu from cleanly accessing shared partitions).

### Step 5: Boot from the USB Drive
1. Keep the USB drive plugged in and restart your computer.
2. Press the BIOS/UEFI boot menu key repeatedly as the computer turns on (common keys are `F12`, `F11`, `F8`, `F2`, or `Esc` depending on your motherboard).
3. Select your USB drive from the boot menu (choose the UEFI option if available).

### Step 6: Install Ubuntu LTS Server
The Ubuntu Server installer (Subiquity) is text-based and keyboard-driven:
1. Select **Try or Install Ubuntu Server**.
2. Choose your **Language** and **Keyboard layout**.
3. Select **Ubuntu Server** (do not select the minimized version unless you have very tight constraints).
4. Configure your network connection (use Ethernet if possible, or configure Wi-Fi).
5. For **Storage configuration**:
   - Select **Custom storage layout**.
   - Navigate to the **free space** you created in Step 3.
   - Create a partition, setting the format to `ext4` and mounting it at `/`.
   - Ensure the bootloader is installed to the main drive (where the Windows Boot Manager ESP partition is located). The installer will automatically add Ubuntu to your existing EFI partition.
6. Enter your profile information (your name, server name, username, and password).
7. Enable **Install OpenSSH server** if you plan to connect to this server remotely.
8. Wait for the installation to finish, then select **Reboot Now** and remove the USB drive when prompted.

## Verification & Next Steps

1. When the computer boots up, you will be greeted by the **GRUB Boot Loader** menu.
2. Select **Ubuntu** to boot into your new command-line server environment, or **Windows Boot Manager** to boot back into Windows.
3. Log into Ubuntu with the username and password you created during setup.
4. Run system updates:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
5. You are now ready to install [[guides/containerization-platform/docker-compose|Docker Compose]]!

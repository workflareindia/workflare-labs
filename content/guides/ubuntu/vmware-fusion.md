---
title: "Install Ubuntu LTS Server via VMware Fusion on macOS"
socialImage: "#"
description: "A detailed guide to setting up Ubuntu LTS Server (non-GUI) as a virtual machine on macOS using VMware Fusion."
date: 2026-07-20
ytUrl: "#"
---

# Install Ubuntu LTS Server via VMware Fusion on macOS

VMware Fusion allows you to run full virtualized operating systems on macOS. It is free for personal use (under the VMware Fusion Player license) and fully supports both Apple Silicon (ARM64) and Intel (x86_64) Macs.

This guide details how to install the latest **Ubuntu LTS Server** (non-GUI) as a VMware Fusion virtual machine.

> [!IMPORTANT]
> **Check your Mac CPU Architecture:**
> - If you have an Apple Silicon Mac (M1/M2/M3/M4), you must download the **ARM64** Ubuntu Server ISO.
> - If you have an Intel Mac, you must download the standard **AMD64/x86_64** Ubuntu Server ISO.

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- #

## Prerequisites

Before starting, ensure you have:
- [ ] A Mac running macOS 12 (Monterey) or newer.
- [ ] VMware Fusion installed (free personal license available from Broadcom/VMware).
- [ ] A minimum of 4GB RAM and 20GB free storage on your Mac.

## Installation & Configuration

### Step 1: Download the Correct Ubuntu Server ISO
1. Navigate to the official [Ubuntu Server download page](https://ubuntu.com/download/server).
2. Choose your architecture:
   - **Apple Silicon Macs**: Download the **Ubuntu Server ARM64 installer** (under alternative downloads/ARM64).
   - **Intel Macs**: Download the standard **Ubuntu Server** ISO (x86_64).

### Step 2: Create a New Virtual Machine
1. Open **VMware Fusion**.
2. Go to **File** -> **New** (or press `Cmd + N`).
3. Select **Install from disc or image** and click **Continue**.
4. Drag and drop your downloaded Ubuntu Server ISO file into the window, select it, and click **Continue**.
5. Choose the operating system type (select **Ubuntu 64-bit** or **Ubuntu 64-bit ARM** depending on your processor) and click **Continue**.
6. On the summary page, click **Customize Settings** to change resources (e.g., set RAM to `2048 MB` or `4096 MB` and CPU cores to at least `2`).
7. Save the VM configuration to your preferred location.

### Step 3: Install Ubuntu LTS Server
1. Click the large **Play** button to start the virtual machine.
2. Press any key if prompted to boot from the CD/DVD.
3. Select **Try or Install Ubuntu Server**.
4. Follow the text-based Subiquity installer prompts:
   - Select **Language** and **Keyboard layout**.
   - Configure **Network Connection** (the default NAT setup will give you internet access via host).
   - For **Storage configuration**, select **Use an entire disk** and hit **Done**.
   - Set up your name, server name, username, and password.
   - Select **Install OpenSSH server** when prompted.
5. Once the installation is complete, select **Reboot Now**. VMware Fusion will automatically unmount the ISO, booting you directly into your new Ubuntu Server.

## Verification & Next Steps

1. Log in with the username and password you configured during setup.
2. Find your VM's IP address by running:
   ```bash
   ip a
   ```
3. Update system packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
4. You can now SSH into your Ubuntu VM from your macOS Terminal using:
   ```bash
   ssh username@<vm-ip-address>
   ```
5. You are now ready to install [[guides/containerization-platform/docker-compose|Docker Compose]]!

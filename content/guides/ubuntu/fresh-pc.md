---
title: "Install Ubuntu LTS Server on a Fresh/No-OS PC"
socialImage: "#"
description: "A complete step-by-step guide to installing the latest Ubuntu LTS Server (non-GUI) on a fresh or bare-metal PC without any pre-existing operating system."
date: 2026-07-20
ytUrl: "#"
---

# Install Ubuntu LTS Server on a Fresh/No-OS PC

Installing Ubuntu LTS Server on a bare-metal PC (or a fresh computer with no operating system) is the ideal way to set up a dedicated home server or lab environment. Since this is the Server variant, it installs a non-GUI command-line interface.

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- #

## Prerequisites

Before starting, ensure you have:
- [ ] A PC (Intel/AMD) with no operating system (or one you are comfortable wiping completely).
- [ ] A USB flash drive (8GB or larger).
- [ ] Access to another computer (Windows, Mac, or Linux) to create the installer USB.
- [ ] An active internet connection (Ethernet cable connected to the server is highly recommended).

## Installation & Configuration

### Step 1: Download the Ubuntu LTS Server ISO
1. On your working computer, download the latest **Ubuntu Server LTS** ISO file from the official [Ubuntu Server download page](https://ubuntu.com/download/server).

### Step 2: Create a Bootable USB Drive
Use one of the following utilities to flash the ISO to your USB:
- **Windows**: Use [Rufus](https://rufus.ie/). Select your USB device, select the Ubuntu ISO, choose **GPT** partition scheme, and click **START**.
- **macOS / Linux**: Use [BalenaEtcher](https://etcher.balena.io/). Select the ISO, select the USB drive, and click **Flash**.

### Step 3: Boot the Target PC from the USB
1. Insert the bootable USB into the target PC.
2. Turn on the PC and immediately press the boot menu key (common keys are `F12`, `F11`, `F8`, `F2`, or `Esc` depending on the manufacturer).
3. Select your USB drive from the boot menu.

### Step 4: Step-by-Step Installation (Subiquity)
The installer is text-based and keyboard-driven (use arrow keys to move, Space/Enter to select):

1. **Welcome**: Select **Try or Install Ubuntu Server**.
2. **Language**: Choose your preferred language.
3. **Installer Update**: If prompted, choose **Update to the new installer** to get the latest fixes.
4. **Keyboard**: Select your layout (default is English US).
5. **Type of Install**: Choose **Ubuntu Server** (standard).
6. **Network Connections**: The installer will detect your Ethernet card and attempt to obtain an IP address via DHCP. If you need a static IP, you can configure it here.
7. **Configure Proxy**: Leave blank unless your network requires a proxy.
8. **Configure Ubuntu Archive Mirror**: Leave the default URL unless you want to use a local mirror.
9. **Storage Configuration**:
   - Select **Use an entire disk**.
   - Check **Set up this disk as an LVM group** (recommended for easier partition resizing later).
   - *Optionally* check **Encrypt the LVM group with LUKS** if physical security is a concern.
   - Select your target hard drive/SSD and choose **Done**.
10. **Profile Setup**:
    - Enter your name, your server's host name (e.g., `homeserver`), a username, and a strong password.
11. **SSH Setup**:
    - Check **Install OpenSSH server** (highly recommended so you can manage the server headless from your other computers).
12. **Featured Server Snaps**: You can choose to pre-install packages like Docker, microk8s, or Nextcloud, but we recommend leaving them blank to install manually later.
13. **Installing System**: Wait for the installation to finish. Once completed, select **Reboot Now** and remove the USB drive when prompted.

## Verification & Next Steps

1. After the PC reboot, you will see the Ubuntu login prompt on the screen.
2. Log in using the username and password you created.
3. Run updates to ensure you have the latest packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
4. Now that your bare-metal server is running, you can proceed to [[guides/containerization-platform/docker-compose|Docker Compose]]!

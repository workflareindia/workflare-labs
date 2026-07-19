---
title: "Install Ubuntu LTS Server via WSL on Windows"
socialImage: "#"
description: "A step-by-step guide to installing the latest Ubuntu LTS Server (non-GUI) on Windows using Windows Subsystem for Linux (WSL)."
date: 2026-07-20
ytUrl: "#"
---

# Install Ubuntu LTS Server via WSL on Windows

Windows Subsystem for Linux (WSL) allows you to run a GNU/Linux environment—including most command-line tools, utilities, and applications—directly on Windows, unmodified, without the overhead of a traditional virtual machine or dual-boot setup.

This guide covers installing the latest **Ubuntu 24.04 LTS Server** (non-GUI command-line environment).

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- #

## Prerequisites

Before starting, ensure you have:
- [ ] Windows 10 (version 2004 and higher, Build 19041 and higher) or Windows 11.
- [ ] Virtualization enabled in your BIOS/UEFI settings (usually enabled by default on modern machines).

## Installation & Configuration

### Step 1: Install WSL and Ubuntu

1. Open **PowerShell** or **Windows Command Prompt** as an Administrator (right-click and select "Run as administrator").
2. Run the following command to install the default WSL features and the latest Ubuntu LTS release:
   ```powershell
   wsl --install
   ```
   *Note: If you want to explicitly install the latest Ubuntu 24.04 LTS release, you can run:*
   ```powershell
   wsl --install -d Ubuntu-24.04
   ```
3. Wait for the download and installation to complete.

### Step 2: Restart Your Computer

Once the command finishes successfully, restart your PC to complete the installation of the required Windows features.

### Step 3: Initialize Ubuntu Server

1. After restarting, open the newly installed **Ubuntu** application from your Windows Start Menu, or open a terminal and run:
   ```cmd
   wsl
   ```
2. A console window will open. Wait for a minute or two for the initial setup to finish.
3. You will be prompted to create a **Username** and **Password** for your Ubuntu environment:
   - Enter a new username (e.g., `serveradmin`).
   - Enter a secure password (the cursor will not move or show characters while typing for security).
   - Re-enter the password to confirm.

## Verification & Next Steps

1. Verify that your system is running the latest Ubuntu LTS version:
   ```bash
   lsb_release -a
   ```
2. Update the package list and upgrade the system to ensure you have the latest security patches:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
3. Your Ubuntu LTS Server is now ready! You can now proceed to [[guides/containerization-platform/docker-compose|Docker Compose]] inside WSL.

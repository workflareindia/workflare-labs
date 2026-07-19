---
title: "Install Ubuntu LTS Server via OrbStack on macOS"
socialImage: "#"
description: "A quick and modern guide to running Ubuntu LTS Server (non-GUI) on macOS (Apple Silicon/Intel) using OrbStack."
date: 2026-07-20
ytUrl: "#"
---

# Install Ubuntu LTS Server via OrbStack on macOS

[OrbStack](https://orbstack.dev/) is an extremely fast, lightweight, and resource-efficient alternative to Docker Desktop and traditional virtual machines (like VirtualBox or VMware) on macOS. It is highly optimized for Apple Silicon (M1/M2/M3/M4) chips.

With OrbStack, you can spin up a non-GUI Ubuntu LTS Server machine in seconds.

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- #

## Prerequisites

Before starting, ensure you have:
- [ ] A Mac running macOS 12 (Monterey) or newer.
- [ ] Apple Silicon (M1/M2/M3/M4) or Intel processor.

## Installation & Configuration

### Step 1: Install OrbStack
You can install OrbStack using either of the following methods:

#### Method A: Using Homebrew (Recommended)
Open your macOS Terminal and run:
```bash
brew install --cask orbstack
```

#### Method B: Direct Download
1. Download the installer from the official [OrbStack website](https://orbstack.dev/).
2. Open the downloaded `.dmg` file and drag OrbStack into your **Applications** folder.
3. Launch OrbStack from your Applications folder.

### Step 2: Create a New Ubuntu LTS Machine
1. Open the OrbStack GUI application.
2. Click on the **Machines** tab on the sidebar.
3. Click the **+ New Machine** button in the top right corner.
4. Set the options:
   - **Name**: e.g., `ubuntu-server`
   - **OS**: Select **Ubuntu**
   - **Version**: Select **24.04** (or the latest LTS)
5. Click **Create**. OrbStack will pull the lightweight image and start the virtual machine in seconds.

*Alternatively, you can create the machine directly from your macOS terminal using the OrbStack CLI:*
```bash
orb create ubuntu:24.04 ubuntu-server
```

### Step 3: Access your Ubuntu Server Terminal
Once created, you can access the command-line interface of your new Ubuntu Server:
- **GUI**: Click the terminal icon next to `ubuntu-server` in the OrbStack application.
- **Terminal CLI**: Run the following command in your macOS Terminal:
  ```bash
  orb -m ubuntu-server
  ```
  *(This drops you directly into a root shell on your Ubuntu VM)*

## Verification & Next Steps

1. Verify that your VM is running the latest Ubuntu LTS:
   ```bash
   lsb_release -a
   ```
2. Update packages to ensure the VM is up to date:
   ```bash
   apt update && apt upgrade -y
   ```
3. OrbStack automatically shares your macOS home directory under `/mnt/mac` and routes ports natively to `localhost`. This makes it incredibly easy to start [[guides/containerization-platform/docker-compose|Docker Compose]] or run web servers that you can access instantly at `http://localhost:<port>`.

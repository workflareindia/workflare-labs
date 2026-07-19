---
title: "Setting up Dockge"
socialImage: "#"
description: "Learn how to use Dockge, a reactive self-hosted manager for docker-compose.yml files."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Setting up Dockge

Dockge is a modern, responsive, self-hosted manager for `docker-compose.yml` stacks, developed by the creator of Uptime Kuma. It focuses strictly on compose stacks and provides an elegant, real-time web editor for your yaml files.

## Why Use Dockge?

- **Real-Time Editor**: Edit your `docker-compose.yml` files inside the browser with built-in auto-completion and validation.
- **Interactive Stack Controls**: Start, stop, restart, update, and monitor terminal outputs for compose stacks in real-time.
- **Convert run commands to compose**: Paste a standard `docker run` command, and Dockge will automatically convert it into a Docker Compose stack.
- **File Structure Friendly**: Keeps your compose stacks in standard directories, so you can still use terminal commands like `docker compose up` directly if needed.

## Deploying Dockge with Docker Compose

Below is the configuration to deploy Dockge using Docker Compose.

### Docker Compose Setup

```yaml
version: "3.8"
services:
  dockge:
    image: louislam/dockge:1
    container_name: dockge
    restart: always
    ports:
      - 5001:5001
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - ./data:/app/data
      # Stacks directory (where your compose files will be stored)
      - /opt/stacks:/opt/stacks
    environment:
      - DOCKGE_STACKS_DIR=/opt/stacks
```

### Deploying the Stack

Run the following command to start Dockge:

```bash
docker compose up -d
```

Open your browser and navigate to `http://<your-server-ip>:5001` to set up your administrator credentials.

See other [[index#Containerization Platform|Containerization Platform Guides]] to manage containers effectively.

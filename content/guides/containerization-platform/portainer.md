---
title: "Setting up Portainer"
socialImage: "#"
description: "Learn how to deploy Portainer to manage your Docker containers from a beautiful web UI."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Setting up Portainer

Portainer is a powerful, lightweight management toolset that allows you to easily build, manage, and maintain Docker, Kubernetes, and Nomad environments via a clean web interface.

## Why Use Portainer?

- **Visual Dashboard**: View running containers, CPU/memory usage, and logs without touching the command line.
- **App Templates**: Deploy common selfhosted services with a single click.
- **Multi-Node Management**: Connect and control containers running on remote servers from one interface.
- **Access Control**: Define user roles and permissions for team environments.

## Deploying Portainer with Docker Compose

Below is the recommended configuration to deploy Portainer Community Edition (CE) using Docker Compose.

### Docker Compose Setup

```yaml
version: "3.8"
services:
  portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer
    command: -H unix:///var/run/docker.sock
    ports:
      - 9443:9443
      - 9000:9000
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
    restart: always

volumes:
  portainer_data:
```

### Deploying the Stack

Run the following command to start Portainer:

```bash
docker compose up -d
```

Open your browser and navigate to `https://<your-server-ip>:9443` (HTTPS) or `http://<your-server-ip>:9000` (HTTP) to configure your admin account.

Check out other [[index#Containerization Platform|Containerization Platform Guides]] for managing your selfhosted stacks.

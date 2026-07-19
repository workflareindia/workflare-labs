---
title: "Introduction to Docker Compose"
socialImage: "#"
description: "Learn how to use Docker and Docker Compose to selfhost open source services."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Introduction to Docker Compose

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

Docker and Docker Compose form the foundation of modern selfhosting. They allow you to run applications in isolated containers, making it easy to deploy, update, and manage services without polluting your host operating system.

## Why Selfhost with Docker Compose?

- **Isolation**: Each service runs in its own environment.
- **Portability**: Move your configuration files (and Docker Compose files) to any server and spin them up instantly.
- **Easy Maintenance**: Updating a service is usually as simple as pulling a new image and restarting the container.

## Getting Started with Docker Compose

Docker Compose lets you define multi-container applications using a single YAML file. Here is a simple example of a `docker-compose.yml` for selfhosting a dashboard like **Homepage**:

```yaml
version: "3.8"
services:
  homepage:
    image: ghcr.io/gethomepage/homepage:latest
    container_name: homepage
    ports:
      - 3000:3000
    volumes:
      - ./config:/app/config
      - /var/run/docker.sock:/var/run/docker.sock # Optional: for Docker integration
    restart: unless-stopped
```

### Deploying the Service

To run this container:

1. Save the above code as `docker-compose.yml`.
2. Run the command:
   ```bash
   docker compose up -d
   ```
3. Open your browser and navigate to `http://<your-server-ip>:3000`.

Next, set up your server by following one of our [[index#Ubuntu Guides|Ubuntu Installation Guides]].

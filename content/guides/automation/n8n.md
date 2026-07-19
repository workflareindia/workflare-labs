---
title: "Selfhosting n8n"
socialImage: "#"
description: "How to selfhost n8n, the extendable workflow automation tool."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting n8n

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[n8n](https://n8n.io/) is an extendable workflow automation tool that lets you connect anything to everything.

## Docker Compose Setup

```yaml
version: "3"
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n:latest
    container_name: n8n
    ports:
      - "5678:5678"
    volumes:
      - ./n8n_data:/home/node/.n8n
    environment:
      - N8N_HOST=localhost
      - N8N_PORT=5678
      - N8N_PROTOCOL=http
    restart: unless-stopped
```

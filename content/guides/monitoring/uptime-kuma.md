---
title: "Selfhosting Uptime Kuma"
socialImage: "#"
description: "A setup guide for Uptime Kuma, a self-hosted monitoring tool."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Uptime Kuma

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Uptime Kuma](https://github.com/louislam/uptime-kuma) is an easy-to-use self-hosted monitoring tool.

## Docker Compose Setup

```yaml
version: "3"
services:
  uptime-kuma:
    image: louislam/uptime-kuma:1
    container_name: uptime-kuma
    ports:
      - "3001:3001"
    volumes:
      - ./uptime-kuma-data:/app/data
    restart: unless-stopped
```

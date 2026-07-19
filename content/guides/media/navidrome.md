---
title: "Selfhosting Navidrome"
socialImage: "#"
description: "How to set up Navidrome, a modern self-hosted music server and streamer."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Navidrome

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Navidrome](https://www.navidrome.org/) is a lightweight, open-source music server and streamer.

## Docker Compose Setup

```yaml
version: "3"
services:
  navidrome:
    image: deluan/navidrome:latest
    container_name: navidrome
    ports:
      - "4533:4533"
    environment:
      ND_SCANSCHEDULE: "@every 30m"
      ND_LOGLEVEL: info
    volumes:
      - ./data:/data
      - /path/to/your/music/folder:/music:ro
    restart: unless-stopped
```

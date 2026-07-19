---
title: "Selfhosting Jellyfin"
socialImage: "#"
description: "Learn how to selfhost Jellyfin, the free and open source software media system."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Jellyfin

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Jellyfin](https://jellyfin.org/) is a free and open-source media system that lets you control media management and streaming.

## Docker Compose Setup

```yaml
version: "3.8"
services:
  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    user: 1000:1000
    network_mode: host
    volumes:
      - ./config:/config
      - ./cache:/cache
      - /path/to/media/movies:/data/movies
      - /path/to/media/tvshows:/data/tvshows
    restart: unless-stopped
```

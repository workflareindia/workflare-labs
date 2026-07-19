---
title: "Selfhosting Komga"
socialImage: "#"
description: "A complete guide to selfhosting Komga, a media server for your comics, manga, and ebooks."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Komga

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Komga](https://komga.org/) is a free and open-source media server for your comics, mangas, BDs, and eBooks.

## Docker Compose Setup

```yaml
version: "3"
services:
  komga:
    image: gotson/komga:latest
    container_name: komga
    ports:
      - "8080:8080"
    volumes:
      - ./config:/config
      - /path/to/your/comics:/data
    environment:
      - TZ=UTC
    restart: unless-stopped
```

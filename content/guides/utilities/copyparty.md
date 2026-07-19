---
title: "Selfhosting Copyparty"
socialImage: "#"
description: "A fast, lightweight file server and sharing suite."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Copyparty

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Copyparty](https://github.com/9001/copyparty) is a versatile and fast file server with a web UI.

## Docker Compose Setup

```yaml
version: "3"
services:
  copyparty:
    image: copyparty/copyparty:latest
    container_name: copyparty
    ports:
      - "3923:3923"
    volumes:
      - ./srv:/srv
    restart: unless-stopped
```

---
title: "Selfhosting Umami"
socialImage: "#"
description: "How to set up Umami, a simple, fast, privacy-focused alternative to Google Analytics."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Umami

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Umami](https://umami.is/) is an open-source, privacy-focused alternative to Google Analytics.

## Docker Compose Setup

```yaml
version: '3'
services:
  umami:
    image: ghcr.io/umami-software/umami:postgresql-latest
    container_name: umami
    ports:
      - "3000:3000"
    environment:
      DATABASE_URL: postgresql://umami:umami123@db:5432/umami
      APP_SECRET: replace-this-with-a-random-string
    depends_on:
      - db
    restart: unless-stopped
  db:
    image: postgres:15-alpine
    container_name: umami-db
    environment:
      POSTGRES_DB: umami
      POSTGRES_USER: umami
      POSTGRES_PASSWORD: umami123
    volumes:
      - ./db-data:/var/lib/postgresql/data
    restart: unless-stopped
```

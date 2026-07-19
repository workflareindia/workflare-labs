---
title: "Selfhosting Flarum"
socialImage: "#"
description: "A deployment guide for Flarum, the lightweight community forum software."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Flarum

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Flarum](https://flarum.org/) is a delightfully simple discussion forum for your website.

## Docker Compose Setup

```yaml
version: "3"
services:
  flarum:
    image: mondedie/flarum:latest
    container_name: flarum
    ports:
      - "8088:8888"
    environment:
      - DEBUG=false
      - DB_HOST=mariadb
      - DB_USER=flarum
      - DB_PASS=flarumpass
      - DB_NAME=flarum
      - FORUM_URL=http://localhost:8088
    depends_on:
      - mariadb
    restart: unless-stopped

  mariadb:
    image: mariadb:10.5
    container_name: flarum-db
    environment:
      - MYSQL_ROOT_PASSWORD=rootpass
      - MYSQL_DATABASE=flarum
      - MYSQL_USER=flarum
      - MYSQL_PASSWORD=flarumpass
    volumes:
      - ./db-data:/var/lib/mysql
    restart: unless-stopped
```

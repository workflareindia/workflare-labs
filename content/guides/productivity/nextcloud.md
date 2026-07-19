---
title: "Selfhosting Nextcloud"
socialImage: "#"
description: "A setup guide to host your own Nextcloud instance for private cloud storage."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Nextcloud

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Nextcloud](https://nextcloud.com/) is a suite of client-server software for creating and using file hosting services.

## Docker Compose Setup

```yaml
version: '3'
services:
  db:
    image: mariadb:10.6
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW
    restart: always
    volumes:
      - db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=nextcloud
      - MYSQL_PASSWORD=nextcloud
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud:latest
    restart: always
    ports:
      - 8080:80
    links:
      - db
    volumes:
      - nextcloud:/var/www/html
    environment:
      - MYSQL_PASSWORD=nextcloud
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db

volumes:
  db:
  nextcloud:
```

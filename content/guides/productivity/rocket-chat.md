---
title: "Selfhosting Rocket.Chat"
socialImage: "#"
description: "How to deploy Rocket.Chat for decentralized team communications."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Rocket.Chat

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Rocket.Chat](https://rocket.chat/) is an open-source team communication platform.

## Docker Compose Setup

```yaml
version: '3'
services:
  rocketchat:
    image: registry.rocket.chat/rocketchat/rocket.chat:latest
    container_name: rocketchat
    ports:
      - 3000:3000
    environment:
      - PORT=3000
      - ROOT_URL=http://localhost:3000
      - MONGO_URL=mongodb://mongo:27017/rocketchat
      - MONGO_OPLOG_URL=mongodb://mongo:27017/local
    depends_on:
      - mongo
    restart: unless-stopped

  mongo:
    image: docker.io/bitnami/mongodb:5.0
    container_name: rocketchat-mongo
    volumes:
      - ./mongo-data:/bitnami/mongodb
    restart: unless-stopped
```

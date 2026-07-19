---
title: "Selfhosting Nginx Proxy Manager"
socialImage: "#"
description: "Setting up Nginx Proxy Manager to manage SSL certificates and reverse proxying."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Nginx Proxy Manager

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Nginx Proxy Manager](https://nginxproxymanager.com/) makes it easy to forward incoming traffic to your selfhosted apps with SSL.

## Docker Compose Setup

```yaml
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

---
title: "Selfhosting Odoo"
socialImage: "#"
description: "How to set up Odoo ERP and CRM using Docker Compose."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Odoo

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Odoo](https://www.odoo.com/) is a suite of open-source business apps, including CRM, e-commerce, billing, and accounting.

## Docker Compose Setup

```yaml
version: '3.1'
services:
  web:
    image: odoo:16.0
    depends_on:
      - db
    ports:
      - "8069:8069"
    volumes:
      - odoo-web-data:/var/lib/odoo
    restart: unless-stopped

  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
    volumes:
      - odoo-db-data:/var/lib/postgresql/data
    restart: unless-stopped

volumes:
  odoo-web-data:
  odoo-db-data:
```

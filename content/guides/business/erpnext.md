---
title: "Selfhosting ERPNext"
socialImage: "#"
description: "Guidelines for setting up ERPNext using Docker Compose."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting ERPNext

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[ERPNext](https://erpnext.com/) is an open-source, full-featured ERP system.

## Docker Setup

ERPNext is complex and requires several interconnected services (Redis, MariaDB, Python app, Node assets, etc.). It is recommended to use the official repository configurations.

### Clone the official environment

```bash
git clone https://github.com/frappe/frappe_docker.git
cd frappe_docker
```
Refer to the `pwd.yml` template in the repo for local development, which configures the complete network layout.

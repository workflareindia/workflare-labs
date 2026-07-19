---
title: "Selfhosting Discourse"
socialImage: "#"
description: "Guidelines on deploying Discourse for modern discussion forums."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Selfhosting Discourse

## YouTube Video Tutorial

If you prefer a visual walkthrough, you can watch our step-by-step video guide here:
- https://youtube.com/watch?v=example

[Discourse](https://www.discourse.org/) is a modern forum and discussion platform.

## Docker Setup Note

Discourse is typically installed using their official launcher template (`discourse_docker`) rather than a simple standalone Compose file to ensure performance and reliability.

### Official Install Process

```bash
# Clone the official repo
git clone https://github.com/discourse/discourse_docker.git /var/discourse
cd /var/discourse

# Run the setup tool
sudo ./discourse-setup
```
Follow the interactive prompts to configure mail, domains, and certificates.

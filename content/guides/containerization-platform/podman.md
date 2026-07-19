---
title: "Introduction to Podman"
socialImage: "#"
description: "Learn how to use Podman as a daemonless, rootless alternative to Docker."
date: 2026-07-20
ytUrl: "https://youtube.com/watch?v=example"
---

# Introduction to Podman

Podman (the Pod Manager) is a daemonless, open-source, Linux-native tool designed to make it easy to find, run, build, share, and deploy applications using Open Container Initiative (OCI) Containers and Container Images.

## Why Use Podman instead of Docker?

- **Daemonless Architecture**: Docker relies on a background daemon (`dockerd`). Podman runs containers directly under the user process, improving stability and resource usage.
- **Rootless by Default**: Podman containers do not require root privileges to run, significantly improving the security posture of your selfhosted services.
- **Pods Concept**: Like Kubernetes, Podman allows you to group containers together in "pods" that share the same network namespace and resources.
- **Docker Compatible**: Podman matches the Docker CLI commands. You can even set up an alias: `alias docker=podman`.

## Installing Podman on Ubuntu

To install Podman on Ubuntu, run:

```bash
sudo apt update
sudo apt install -y podman
```

To run a simple container without root privileges:

```bash
podman run -d --name webserver -p 8080:80 nginx
```

Check out our [[index#Containerization Platform|Containerization Platform Guides]] to learn more.

---
title: "Guide Traefik"
date: 2022-05-27T21:00:00+02:00
draft: true
image: "mini.jpg"
---

## Introduction

Le service est composé principalement de 3 parties:

- le service backend (node, flask, ...)
- l' "entrypoint" (un port)
- le router, des règles de routage

## Installation

### Docker Compose

```yml
version: '3'
services:
  traefik:
    image: traefik:latest
    container_name: traefik
    restart: always
    volumes:
      - ./traefik.yml:/etc/traefik/traefik.yml
    ports:
      - 8080:8080
      - 80:80
```

## Configuration

### Routage Statique

```yaml
# Static configuration
entryPoints:
    unsecure:
        address: :80
    secure:
        address: :443
```

---
title: "Guide Traefik"
date: 2022-05-27T21:00:00+02:00
draft: false
image: "mini.jpg"
---

## Introduction

Le service est composé principalement de 3 parties:

- le service backend (node, flask, ...)
- l' "entrypoint" (un port)
- le router, des règles de routage

## Installation

### Brew

`brew install traefik`

### apt

`apt install traefik -y`

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
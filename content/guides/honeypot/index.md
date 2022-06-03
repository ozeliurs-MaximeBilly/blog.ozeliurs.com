---
title: "Creer son propre \"Honeypot\" (Pot de Miel)"
date: 2022-06-03T21:00:00+02:00
draft: false
image: "mini.jpg"
---

## Introduction

Un Honeypot est un système qui peut être utile pour éduquer les devs à la securité et aussi à développer des mesures de protection contre les attaques.

Pour en savoir plus sur le Honeypot, visitez [Wikipedia](https://fr.wikipedia.org/wiki/Honeypot).

## Installation de Honeypot

J'ai choisi Cowrie pour mon Honeypot. On peut facilement l'installer avec un container Docker.

### Docker

`docker run -p 2222:2222/tcp  -v ./logs:var/lib/cowrie cowrie/cowrie`

### Docker Compose

```
version: "3"  # optional since v1.27.0
services:
  cowrie:
    image: cowrie/cowrie
    ports:
      - "2222:2222"
    volumes:
      - ./logs:var/lib/cowrie
```

## Fin

Et voila votre honeypot est installé et écoute les connections ssh sur le port 2222. Vous devriez le changer pour le port 22 (ssh par défaut).

Les connections sont toutes logguées dans le dossier `./logs/cowrie.log` vous pouvez aussi customiser votre honeypot (voir [la documentation de cowrie](https://cowrie.readthedocs.io/en/latest/)).
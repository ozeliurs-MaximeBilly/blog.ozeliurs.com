---
title: "Installer des clés ssh pour accéder aux serveurs sans mot de passe"
date: 2022-05-01T21:00:00+02:00
draft: false
image: "mini.jpg"
---

# Clés SSH

## Génération des clés pour le client

`$ ssh-keygen -t ed25519`

## Installation des clés sur le serveur

`ssh-copy-id -i ~/.ssh/id_ed25519.pub <user>@<ip>`
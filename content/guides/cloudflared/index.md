---
title: "Installer cloudflared tunnels sur debian (ou similaire)"
date: 2022-05-01T21:03:00+02:00
draft: false
image: "mini.jpg"
---

# Installer & Configurer cloudflared tunnels

## Installer le fichier .deb

`$ wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb`

`$ dpkg -i cloudflared-linux-amd64.deb`

## Authentifier cloudflared

`$ cloudflared tunnel login`

## Creer un tunnel

`$ cloudflared tunnel create <NAME>`

## Ajouter des sousdomains

`$ cloudflared tunnel route dns <UUID or NAME> <hostname>`

## Configurer cloudflared

`$ nano /etc/cloudflared/config.yml`

```yml
tunnel: <Tunnel-UUID>
credentials-file: /etc/cloudflared/<Tunnel-UUID>.json

ingress:
- hostname: gitlab.example.com
    service: http://localhost:80
    originRequest:
        noTLSVerify: true
- hostname: gitlab-ssh.exmaple.com
    service: ssh://localhost:22
- service: http_status:404
```

## Valider les règles ingress

`$ cloudflared tunnel ingress validate`

## Installer cloudflared comme un service

`$ cloudflared service install`

`$ systemctl start cloudflared`

`$ systemctl status cloudflared`

## Verifier l'etat du tunnel

`$ cloudflared tunnel info`

## Documentation

[Install and Setup Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide/#set-up-a-tunnel-locally-cli-setup)

[Ingress Rules Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/configuration/local-management/ingress/)

[Run as a Service Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/run-tunnel/as-a-service/)

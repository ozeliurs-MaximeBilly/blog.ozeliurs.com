---
title: "Installer cloudflared tunnels sur debian (ou similaire)"
date: 2022-05-01T21:03:00+02:00
draft: false
image: "mini.jpg"
---

# Set up cloudflared tunnels

## Install .deb file

`$ wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb`

`$ dpkg -i cloudflared-linux-amd64.deb`

## Authenticate cloudflared

`$ cloudflared tunnel login`

## Create a Tunnel

`$ cloudflared tunnel create <NAME>`

## Add subdomains

`$ cloudflared tunnel route dns <UUID or NAME> <hostname>`

## Configure cloudflared

`$ nano /etc/cloudflared/config.yml`

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

## Validate ingress rules

`$ cloudflared tunnel ingress validate`

## Install as a service

`$ cloudflared service install`

`$ systemctl start cloudflared`

`$ systemctl status cloudflared`

## Check tunnel status

`$ cloudflared tunnel info`

## Documentation

[Install and Setup Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide/#set-up-a-tunnel-locally-cli-setup)

[Ingress Rules Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/configuration/local-management/ingress/)

[Run as a Service Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/run-tunnel/as-a-service/)
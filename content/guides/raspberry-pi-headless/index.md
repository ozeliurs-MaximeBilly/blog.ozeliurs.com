---
title: "Installer Raspberry PI OS en mode \"headless\""
date: 2022-05-28T08:00:00+02:00
draft: false
image: "mini.jpg"
---

## Introduction

Configurer un raspberry pi en mode headless est très pratique. Avec la possibilité d'y accéder dans écran, clavier ni souris supplémentaire, c'est une facon de configurer qui est très avantageuse.

## Installation de Raspberry PI OS

Avec votre méthode pour flasher favori, flashez l'image Raspberry PI OS sur votre carte Micro SD.

Je conseille [Balena Etcher](https://www.balena.io/etcher) pour flasher l'image.

## Configuration de Raspberry PI OS en mode "headless"

### Fichier "ssh"

Dans la partition boot du Raspberry PI, il faut ajouter le fichier "ssh"

`touch ssh`

### Fichier "userconf.txt"

Depuis peu, Raspberry PI OS n'a plus de mot de passe configuré par défaut.
If faut donc configurer un mot de passe.

Premièrement, on génère un mot de passe:

`echo '<mypassword>' | openssl passwd -6 -stdin`

Ensuite on ajoute notre utilisateur et le mot de passe crypté dans le fichier "userconf.txt".

`echo "<username>:<encrypted>\n" > userconf.txt`

Si vous voulez garder la configuration historique cela donne:

```
echo "pi:$6$iJB/UcLM9Xzsj.Vw$sfZsqvR3219FA2bAA6utpdONdR27p4QUg/u6uHcCMfVGberamK7TkNLcL76MenFuFsTxm4Zh7j.3lzwmDJ4hp/" > userconf.txt
```

### Configuration du wifi (optionnel)

Modifiez le fichier "" avec la configuration ci dessous (en rmplacant les valeurs par vos propres):

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=<country>

network={
    ssid="<SSID>"
    psk="<password>"
    key_mgmt=WPA-PSK
}
```

## Fin

Vous pouvez maintenant vous connecter à votre Raspberry PI via ssh avec l'utilisateur et le mot de passe définit plus tot.

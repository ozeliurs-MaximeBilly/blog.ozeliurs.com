---
title: "Internet à plus de 2 kms"
date: 2022-05-01T23:00:00+02:00
draft: false
image: "mini.jpg"
---

# Une installation internet compliquée

## Situation initiale

Avec une box de chez orange en adsl et à plus de 2kms du dernier répéteur adsl, on avait vraiment une connexion merdique.

On parle ici de 1Mbps en descendant et 0,5Mbps en montant et un ping qui grimpe à 200ms dès que du traffic transite sur la ligne.

Mais avec l'arrivée du télétravail, il a fallu trouver une solution.

## Solution n°1

J'ai premièrement décidé d'acheter un routeur 4g de la marque TP-Link, plus précisément le modèle TL-MR6400.

Avec une vitesse maximale de 150 Mbps, j'ai été décu de voir que la connexion n'était que de ~10-15 Mbps, c'était fonctionnel et répondait au problème actuel que nous rencontroins.

Sachant que l'antenne 4g la plus proche était à moins de 500m en vue directe c'était dévevant. De plus le ping posait problème puisque en 4g nous avions un ping constant de 70-90 ms.

## Solution n°2 (la dernière)

J'ai décidé d'investir et de complètement changer les installations internet.

Premièrement j'ai pris un forfait fibre à installer dans une maison au "village", là où la fibre est disponible. Il restait à trouver un moyen d'acheminer internet, on en parleras plus tard.

Deuxièmement, acheter du matériel dédié au réseau, un routeur (Edgerouter X), deux points d'accès (UAP AC Lite) ainsi qu'une cloudkey afin de tout orchestrer.

Cette installation à un prix mais depuis cette installation nous n'avons plus jamais eu de problème de couverture ou de connexion en wifi et en filaire.

Et finalement pour lier les deux sites j'ai acheté deux NanoStation 5AC Loco pour faire un lien entre les sites qui se trouvent à plus de 2 kms.

Avec cette installation je recois donx internet en fibre au site du village, transmet internet via les deux Nanostation qui arrive directement dans l'Edgerouter X.

A noter, j'ai gardé le routeur 4g qui est lui aussi branché sur l'edgerouter afin de faire du failover au cas ou le lien principal devait faillir.

Ensuite sur le réseau local les deux APs forment un seul réseau wifi et cette installation nous a permis d'atteindre des vitesses de 250 Mbps en symétrique. Bien mieux qu'avant. Le ping aussi qui était problématique, ne nous pose plus problème puisqu'on tourne autour des 20ms.
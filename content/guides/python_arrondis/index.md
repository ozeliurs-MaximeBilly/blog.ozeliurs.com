---
title: "Régler les problèmes d'arrondis sur python"
date: 2022-06-10T11:11:00+02:00
draft: false
image: "mini.jpg"
---

## Introduction

Récamment j'ai rencontré un problème d'arrondi sur python.

## Investigation

Voila le morceau de code qui me posait problème:

```
var = 79.6

print(int(var * 100))
```

En voulant prendre l'entier de `var * 100` on à comme résultat 7959 au lieu de 7960.

On peut comprendre ce résultat en regardant le résultat de `var * 100`. C'est égal à `7959.999999999999` donc l'entier associé est 7959 et non 7960.

## Solution

La solution à ce problème est assez simple. Remplacer `int()` par `round()`.

En effet round aura pour effet de prendre en compte les chiffres après la virgule et l'entier le plus proche et non l'entier tronqué.

```
var = 79.6

print(round(var * 100))
```

Cela donne la bonne valeur.
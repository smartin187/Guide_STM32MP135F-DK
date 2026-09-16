# Guide sur STM32 MP135F-DK

Ce dépôt contient un guide pour utiliser le STM32MP135F-DK avec le système Linux embarqué Open ST Linux.

Open ST Linux : [https://www.st.com/en/embedded-software/stm32-mpu-openstlinux-distribution.html](https://www.st.com/en/embedded-software/stm32-mpu-openstlinux-distribution.html)

> Si vous avez besoin de transférer des fichiers, utilisez une clé USB ou copiez-les directement sur la carte microSD (cette dernière méthode nécessite un ordinateur sous Linux).

Vous trouverez également des [projets à réaliser sur le STM32](#projet-stm-32).

## Introduction

Dans ce chapitre, vous n'utiliserez pas encore le STM32, mais vous découvrirez cette carte. Si vous la connaissez déjà, allez directement à la partie [Configuration](#configuration).

### Présentation de la carte STM32MP135F-DK

[Présentation de la carte STM32MP135F-DK](introduction/présentation_STM32MP1.md)

### Présentation d'Open ST Linux

[Présentation de Open St Linux](introduction/présentation_open_st_linux.md)

## Configuration

[Configuration de `~/.config/weston.ini`](ini_config/configuration_ini.md)


## Connexion Wi-Fi

[Connexion au Wi-Fi et ajout d'une adresse IP](Connection_wifi/connection_wifi.md)

## Réglage de l'heure

> Cette étape est nécessaire pour utiliser `apt`.

[réglage de l'heure](réglage_heur/réglage_heur.md)

## Connexion SSH

La connexion SSH est très utile pour utiliser le STM32 à distance ou pour transférer des fichiers.

[Connexion SSH](connection_ssh/connection_ssh.md)

## Outils utiles

Certains outils peuvent être utiles sur le STM32. Voici comment les installer.

[Installation d'outil](outil_utiles/outil_utiles.md)

## Programmation en C

> Sur le STM32 avec Open ST Linux, vous devez compiler de manière croisée en ARM32 (armhf ou armel).

> Un interpréteur Python 3 est également disponible. Il est plus facile à utiliser, car il ne nécessite pas de compilation croisée.

[Programmation en C](Programmation_C/programmation_C.md)


## Projets STM32

Voici d'autres projets que vous pouvez réaliser sur le STM32.

### Projet serveur HTML

Il est possible d'héberger un serveur sur le STM32 pour héberger un site Web.

[Projet serveur HTML](Projet_Web/projet_web.md)


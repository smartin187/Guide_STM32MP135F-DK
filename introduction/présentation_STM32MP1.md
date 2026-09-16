# Présentation de la carte STM32MP135F-DK

Dans ce guide, vous allez découvrir la carte STM32MP135F-DK, une carte de développement pour le processeur STM32MP1.

## Le processeur STM32MP1

Le processeur STM32MP1 est le processeur présent sur la carte. Il s'agit d'un processeur ARM 32 bits. Les architectures prises en charge sont `armhf` et `armel`.

Ce processeur dispose de ressources limitées, mais il est prévu pour faire fonctionner un système Linux embarqué et minimaliste : Open ST Linux.

## Informations sur la carte

- Processeur : 1 GHz, ARM 32 bits
- Écran intégré : écran LCD de 480 × 272 pixels
- Wi-Fi et Bluetooth Low Energy intégrés
- 2 × 2 ports USB-A + 1 port USB-C
- 2 ports Ethernet
- Carte microSD (généralement utilisée par l'OS)
- USB-C « Power in » pour l'alimentation. **Attention à ne pas le confondre avec l'autre port USB-C, qui n'est pas prévu pour l'alimentation.** « Power in » est écrit à côté du port USB-C d'alimentation.
- GPIO (connexions pour des périphériques externes)
- Micro USB ST-Link (pour déboguage avancé)

### Composants

__Avant__
![STM32-2](images/STM32-2.png)

__Arrière__
![STM32-1](images/STM32-1.png)

#### Écran

Un écran tactile utilisé par l'OS.

4.3" 480×272 pixels LCD

#### GPIO

Les broches GPIO permettent de connecter des périphériques externes à la carte.

#### Bouton utilisateur

Vous pouvez configurer ce bouton.

#### ST-Link

Un port micro-USB pour le débogage.

#### Boutons de contrôle

Trois boutons se trouvent sous l'écran.

Le bouton « Wake up » permet de rallumer la carte après un arrêt via `shutdown`.

Le bouton « Reset » permet de redémarrer le STM32.

#### Sélecteur de démarrage

Contrairement à un ordinateur classique, le choix du périphérique de démarrage ne se fait pas via un BIOS, mais via ces interrupteurs.

> En général, le démarrage s'effectue sur la carte microSD. Les interrupteurs sont souvent déjà configurés pour la microSD.

> Attention : le nom des périphériques n'est pas indiqué, seuls `boot0`, `boot1` et `boot2` le sont.

__`boot1` correspond à la carte microSD.__

#### USB-C d'alimentation

Ce port USB-C doit être utilisé pour alimenter la carte. La mention « Power in » se trouve à côté.

Veillez à utiliser une alimentation suffisamment puissante pour le STM32.

#### 2 ports Ethernet

Cette carte possède deux ports Ethernet.

#### Connexion du module caméra

Le module caméra est connecté via une nappe.

Le module caméra est généralement fourni avec la carte.

#### CPU

Le CPU est un processeur ARM 32 bits conçu par ST.

#### RAM

#### Micro SD

Un emplacement pour carte microSD, très souvent utilisé par l'OS (Open ST Linux).

#### 4 ports USB-A

Quatre ports USB-A permettent de connecter des périphériques USB.

> Pour utiliser Open ST Linux, il est nécessaire d'avoir un clavier et généralement une souris, même si l'écran est tactile.

#### USB-C

Un port USB-C permet de connecter des périphériques USB.

> Ne le confondez pas avec le port USB-C d'alimentation, qui porte la mention « Power in ».

## Documentation officielle

[Présentation STM32MP1-DK](https://www.st.com/en/evaluation-tools/stm32mp135f-dk.html#overview)

[Documentation officiel](https://www.st.com/resource/en/data_brief/stm32mp135f-dk.pdf)

[Schéma électrique](https://www.st.com/resource/en/schematic_pack/mb1635-mp135f-e02-schematic.pdf)



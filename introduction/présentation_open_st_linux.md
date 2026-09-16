# Présentation d'Open ST Linux

Open ST Linux est une distribution Linux embarquée et minimaliste, qui peut être utilisée sur le STM32MP1.

Elle est construite avec Yocto.

## Installation d'Open ST Linux

En général, une carte microSD est fournie avec le STM32MP1-DK et Open ST Linux est déjà installé. Si vous avez besoin de réinstaller Open ST Linux, par exemple sur une nouvelle carte ou à la suite d'une panne du système, voici comment procéder sur une carte microSD ou un autre support de stockage :

### Récupérer l'image d'Open ST Linux

Récupérez Open ST Linux sur GitHub et cherchez l'image officielle, ou utilisez Yocto : [Open ST Linux](https://github.com/STMicroelectronics/meta-st-openstlinux). Si cette procédure est trop compliquée, utilisez l'image de ce dépôt (voir ci-dessous).

> Si récupérer Open ST Linux est trop compliqué, vous trouverez une image prête dans les versions publiées de ce dépôt, **à utiliser comme sauvegarde** : [image Open ST Linux](https://github.com/smartin187/STM32_MP1_Bidulab/releases/tag/ajout_backup). Pour installer l'image, téléchargez l'archive ZIP, décompressez-la et utilisez `dd` pour la copier sur la carte microSD. Toutes les commandes se trouvent dans la release.<br>Mais attention : **cette image n'est pas forcément la version la plus récente d'Open ST Linux**.

## Gestionnaire de paquet

Open ST Linux utilise `apt` pour installer des paquets. Mais attention : Open ST Linux n'utilise pas les dépôts officiels Debian ou Ubuntu, mais un dépôt de ST. Tous les paquets ne seront pas forcément disponibles sur ce dépôt.

L'outil `dpkg` est donc installé si vous avez besoin d'installer manuellement des paquets `*.deb`. Consultez la section [Installation d'une application](#installation-dapplication).

## Interface graphique

Cette distribution possède une interface graphique basée sur Wayland avec Weston. Il s'agit d'une interface simple, mais elle permet tout de même d'exécuter des applications graphiques.

Notez que certaines applications ne pourront pas fonctionner, notamment celles qui utilisent X11. Dans la plupart des distributions utilisant Wayland, `XWayland` permet aux applications X11 de fonctionner sur Wayland. Open ST Linux, qui est une distribution minimaliste, n'inclut pas `XWayland`.

## Installation d'application

L'installation d'une application peut être compliquée dans certains cas.

Avant d'installer une application, vérifiez qu'elle est compatible avec le STM32 et ses ressources matérielles.

Le STM32 possède un processeur `ARM` 32 bits. Les architectures prises en charge sont `armhf` et `armel`.

Si une application n'est pas disponible dans le dépôt ST, mais qu'elle est disponible en `armhf` ou `armel`, vous pouvez tenter de l'installer manuellement.

> Attention : certaines applications pourraient endommager votre système en cas de conflit entre dépendances. Soyez prudent avec les dépendances.

### Installation

Il peut y avoir plusieurs méthodes pour installer une application.

> N'oubliez pas que les applications graphiques ne doivent pas utiliser `X11`.

#### Installation via `.deb`

Si l'application est disponible sur les dépôts officiels Debian/Ubuntu, vous pouvez télécharger le fichier `.deb` depuis un ordinateur puis le transférer sur le STM32 et enfin l'installer avec `dpkg`.

1. Téléchargez le paquet :

**Option 1 : télécharger via apt :**
```bash
apt download <nom_du_package:armhf>
```

> Veillez à installer le paquet dans l'architecture `armhf` ou `armel` via `apt`. Il est possible que vous deviez exécuter la commande `sudo dpkg --add-architecture armhf` pour ajouter l'architecture `armhf`, **mais attention à ne pas « polluer » votre système**. Vous pouvez aussi utiliser Docker pour le télécharger. Sinon, choisissez l'option 2.

**Option 2 : télécharger le paquet en ligne :**

Vous pouvez également télécharger le paquet depuis le site de Debian ou d'Ubuntu.

- [Installation via Debian](https://packages.debian.org/search?suite=stable&section=all&arch=any&searchon=names&keywords=package)
- [Installation via Ubuntu](https://packages.ubuntu.com/)

2. Installez le paquet sur le STM32 :

```bash
dpkg -i <nom_du_package>.deb    # vous devez être administrateur ; utilisez su pour ouvrir un terminal root.
```

> Soyez très prudent avec les dépendances ! Si des dépendances sont incompatibles, vous risquez d'endommager votre système !

#### Installation manuelle

Si vous pouvez récupérer les binaires Linux de l'application, vous pouvez les exécuter à condition qu'ils soient en `armhf` ou en `armel`.

Dans ce cas, transférez le ou les binaires sur le STM32 et exécutez-les.

## Limitation

Cette distribution est minimaliste : certaines applications ou commandes ne sont pas installées par défaut. Certaines pourront être installées directement depuis le dépôt ST, d'autres non.

Voici les principales choses à savoir :

### Pas de `sudo`

Cette distribution n'a pas la commande `sudo`.

Il n'est toutefois pas difficile d'exécuter des commandes d'administration.

Il faut utiliser la commande `su`. Voici les possibilités :
1. Saisissez la commande `su`. Un terminal root s'ouvrira et vous pourrez exécuter des commandes d'administration. Attention, toutes les commandes seront alors exécutées en tant que root jusqu'à la fermeture du terminal root.
2. Saisissez la commande `su -c "<commande>"` pour exécuter une seule commande en tant que root.

> Notez que si vous utilisez cette commande pour accéder au dossier personnel d'un utilisateur, vous ne devez pas écrire `~`, car cela désignera le dossier personnel de root. Utilisez le chemin complet dans ce cas.

### Pas de `XWayland`

Dans la plupart des distributions utilisant Wayland, `XWayland` permet aux applications X11 de fonctionner sur Wayland. Open ST Linux, qui est une distribution minimaliste, n'inclut pas `XWayland`.



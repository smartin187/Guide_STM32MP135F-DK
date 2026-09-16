# Programmer en C

Il est possible de programmer en C sur un ordinateur et de compiler de manière croisée pour ARM32 (armhf), l'architecture du `STM32`.

Il faut utiliser le compilateur croisé `arm-linux-gnueabihf-gcc` pour compiler le code C pour l'architecture ARM32.

## Compilation

Exécutez la commande suivante dans un terminal :
```bash
arm-linux-gnueabihf-gcc programme.c
```

Cette commande génère un binaire ARM32 nommé `a.out`.

Vous pouvez vérifier l'architecture du binaire généré avec la commande `file` :
```bash
file a.out
```

## Utilisation sur STM32

Copiez le fichier sur le STM32 (via une carte microSD ou un autre moyen), puis exécutez-le avec `./a.out` (ou avec le nom du fichier utilisé).

## Exemple

Dans le dossier `Exemple`, vous trouverez un programme C que vous pouvez exécuter sur le STM32.

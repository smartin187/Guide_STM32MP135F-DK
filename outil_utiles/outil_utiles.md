# Outils utiles

Dans ce chapitre, vous allez pouvoir installer quelques outils (applications) pour faciliter l'utilisation du système.

Nous allons installer :
- [`nano`](#installation-de-nano)
- [`pip`](#installation-de-pip)
- [`python venv`](#installation-de-python-venv)

## Installation de Nano

Nano est un éditeur de texte en ligne de commande. Par défaut, sur le STM32, `vi` est installé. Nano est plus simple à utiliser pour les débutants.

> Nano pourra également vous être utile si vous souhaitez programmer sur le STM32 (il propose une légère coloration syntaxique).

Installez Nano via `apt`.

```bash
su # utilisez cette commande pour passer en root

apt update # facultatif, si vous n'avez pas effectué de mise à jour depuis longtemps

apt install nano
```

Vous pouvez ensuite saisir la commande `nano`.

Dans l'éditeur, tous les raccourcis clavier (enregistrer, quitter, etc.) sont indiqués.


## Installation de Pip

Pip est un gestionnaire de paquets pour Python. Il permet d'installer des bibliothèques Python.

> En général, il est possible d'installer des bibliothèques Python sans `pip`, mais via `apt`, avec la commande `apt install python3-<bibliothèque Python>`.

Pour installer `pip`, installez le paquet `python3-pip` via `apt`.

```bash
su # utilisez cette commande pour passer en root
apt update # facultatif, si vous n'avez pas effectué de mise à jour depuis longtemps
apt install python3-pip
```

Vous pouvez ensuite installer des bibliothèques Python.

> **Attention** : dans certains cas, saisir `pip` ne suffit pas ; il faut utiliser `python3 -m pip`. Vous pouvez également essayer `pip3`.

### Installation de librairie Python

Pour installer une bibliothèque Python (ou un autre paquet Python), saisissez la commande suivante :

```bash
python3 -m pip install <nom de la librairie>
```

La commande suivante peut également fonctionner dans certains cas :

```bash
pip3 install <nom de la librairie>
```

## Installation de Python venv

Python venv est un module qui permet de créer des environnements virtuels Python. Cela permet d'isoler les dépendances d'un projet Python.

Pour installer `python3-venv`, installez le paquet via `apt`.

```bash
su # utilisez cette commande pour passer en root
apt update # facultatif, si vous n'avez pas effectué de mise à jour depuis longtemps
apt install python3-venv
```

Après, vous pouvez créer un environnement virtuel Python.

```bash
python3 -m venv .venv
```

Pour activer l'environnement virtuel :

```bash
source .venv/bin/activate
```

Pour désactiver l'environnement virtuel :

```bash
deactivate
```

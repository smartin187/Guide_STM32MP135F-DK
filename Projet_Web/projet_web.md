# Projet Web sur STM32MP1

Il est possible d'utiliser le STM32MP1 pour héberger un serveur Web.

Il existe plusieurs outils pour le faire. Nous allons utiliser `python3`, qui est déjà installé sur le STM32MP1.

## Création et copie du fichier HTML

Dans notre exemple, nous allons utiliser un fichier HTML simple.

Vous le trouverez dans `site_web/index.html`.

> Vous pouvez créer votre propre fichier HTML ou modifier celui-ci.

Copiez le fichier `index.html` dans le répertoire `/home/weston/projet_web/` (copiez le fichier à l'aide d'une clé USB ou de la carte micro SD).

> Copiez également le fichier `start.sh` pour lancer le serveur plus facilement.

### Lancement du serveur web

Pour lancer le serveur web, nous allons utiliser `python3 -m http.server`.

Commencez par vous placer dans le répertoire du projet HTML, puis lancez la commande suivante pour démarrer le serveur :

```bash
cd /home/weston/projet_web/   # aller dans le projet
python3 -m http.server 8000   # lancer le serveur web sur le port 8000
```

> Si vous fermez le terminal dans lequel le serveur a été lancé, celui-ci s'arrêtera.

> Vous pouvez également utiliser le script `start.sh` pour lancer le serveur Web. Il se trouve dans le répertoire du projet HTML.

### Connexion au serveur via un navigateur Web

Pour tester votre serveur, vous pouvez utiliser un navigateur Web sur votre ordinateur.

> Note : le serveur Web est accessible sur le réseau local. Votre ordinateur doit être connecté au même réseau.

#### Trouver l'adresse IP du STM32MP1

Vous devez connaître l'adresse IP du STM32MP1 pour vous connecter.

Dans un terminal du STM-32, écriver :

```bash
ip -4 addr show     # enlever -4 pour utiliser IPv6
```

Vous obtiendrez plusieurs adresses IP. Pour trouver la bonne :
Si vous êtes connecté en Wi-Fi, l'adresse IP se trouve dans la section `wlan0`. Le mot `inet` apparaît généralement avant l'adresse IP. Si plusieurs adresses sont affichées, vous pouvez toutes les tester.


#### Connexion via le navigateur Web

Dans un navigateur web, écrivez :
```http
http://<adresse_ip>:8000
```

> Si vous avez changer le port lors du lancement du serveur, changez-le aussi sur le navigateur.

> La principale limite du serveur Python est que seul `http` est disponible, et non `https`.

En cas de problème, allez voir la section [problème et debug](#probl%C3%A8me-et-debug).

### Problème et debug

Vous pouvez rencontrer plusieurs problème avec le serveur.

#### Mauvaise adresse IP

Vérifiez que vous avez saisi la bonne adresse IP du STM32MP1 dans votre navigateur.

> La commande `ip -4 addr show` affiche plusieurs adresses IP, mais elles ne correspondent pas toutes au STM32MP1.

#### Test de connexion

Pour vérifier que votre ordinateur peut se connecter au STM32MP1, vous pouvez utiliser la commande `ping` dans un terminal de votre ordinateur.

```bash
ping <adresse_ip_STM32>
```

Si cela fonctionne, le problème vient probablement du serveur plutôt que de la connexion.

#### Vérifier le log du serveur

Lorsque vous lancez le serveur avec Python, ses journaux s'affichent dans le terminal. Vérifiez que le serveur est bien actif et qu'il n'y a pas d'erreur.

> Dès qu'un appareil se connecte au serveur, un journal s'affiche. Vérifiez sa présence lorsque vous vous connectez avec le navigateur Web.

#### Tester serveur directement sur STM-32

Vous pouvez également tester le serveur directement sur le STM32MP1 :

```bash
curl http://localhost:8000
```

Si le contenu de la page HTML s'affiche, le serveur fonctionne. Le problème peut alors venir de la connexion, notamment si un pare-feu bloque l'accès.


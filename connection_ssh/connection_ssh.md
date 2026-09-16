# Connexion SSH

La connexion SSH permet de se connecter à distance au STM32 depuis un autre ordinateur. Vous avez accès à la console du STM32 et pouvez transférer des fichiers.

## Connexion

Par défaut, le serveur SSH est activé sur le STM32. Il est donc facile de s'y connecter.

Voici les étapes à suivre :

### Trouver l'adresse IP

Vous devez connaître l'adresse IP du STM32.

```bash
ip a
```

Cette commande affiche plusieurs adresses IP. **Attention : une seule est la bonne.** Pour la trouver, si vous êtes connecté en Wi-Fi, l'adresse IP se trouve dans la section `wlan0`. Si vous êtes connecté autrement, elle se trouve dans une autre section. En général, l'adresse IP commence par `192.168` ou `10.0`.

Si vous ne savez pas quelle est la bonne adresse IP, vous pouvez tester les différentes adresses IP lors de la connexion SSH.

### Connexion SSH

Depuis un autre ordinateur, écrivez la commande :

```bash
ssh root@<adresse_ip>
```

> Par défaut, il n'y a pas de mot de passe. Vous aurez cependant probablement un message d'avertissement. Saisissez `yes` si cela arrive.

Si la connexion a fonctionné, vous devriez voir l'invite de commande du STM32 (connecté en tant que root).

> Dans cet exemple, l'utilisateur SSH du STM32 est `root`. Si vous n'avez pas besoin des droits d'administrateur, vous pouvez vous connecter avec l'utilisateur `weston` (un utilisateur non root présent sur le STM32). Utilisez la même commande qu'avec `root`, en remplaçant `root` par `weston`.

### Fin de la connexion

Utilisez simplement le raccourci clavier `Ctrl + D` sur votre ordinateur pour fermer la connexion SSH.


## Transfert de fichiers

Vous pouvez utiliser SSH pour transférer des fichiers entre votre ordinateur et le STM32. Vous pouvez envoyer ou recevoir des fichiers avec la commande `scp` :

### Envoyer un fichier

```bash
scp fichier.txt root@<adresse_ip>:/chemin/de/la/copie/
```

### Recevoir un fichier

```bash
scp root@<adresse_ip>:/chemin/du/fichier.txt ./
```

> Placez `./` à la fin de la commande pour récupérer le fichier dans le dossier courant. Sinon, indiquez le chemin du dossier de destination.

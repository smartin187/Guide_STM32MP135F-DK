# Connection ssh

La connection ssh permet de se connecter à distance (avec un autre ordinateur) au STM32. Vous avez accès à la console du STM32 et vous pouvez transférer des fichiers.

## Connection

Par défaut, le ssh est activer sur le STM32. Il est donc facile de ce connecter.

Voici les étapes a suivre :

### Trouver l'adress ip

Il vous faut connaitre l'adress ip du STM32.

```bash
ip a
```

Cette commande affiche plusieurs adress ip. **Attention : un seul est la bonne**. Pour la trouver, si vous vous être connecter en wifi, l'adress ip sera dans la section `wlan0`. Si vous êtes conencter autrement, l'adress ip sera dans une autre section. En suite, l'adress ip commence souvent par `192.168` ou `10.0`.

Si vous ne saver pas quelle adress ip, vous pouvez tester les différentes adress ip lors de la connection ssh...

### Connection ssh

Depuis un autre ordinateur, écrivez la commande :

```bash
ssh root@<adress ip>
```

> Par défaut, il n'y a pas de mot de passe. Mais vous aurez surement un message d'avertissement. Ecriver `yes` si cela arrive...

Si la connection a fonctionner, vous devait voir le prompt du STM32 (connecter sur root).

> Dans cette exemple, l'utilisateur pour le ssh sur le STM32 est `root`. Mais si vous n'avez pas besoin d'être administrateur, vous pouvez vous connecter sur `weston` (un utilisateur non root présent sur le STM32). Utiliser la même commande que pour `root` en remplacant `root` par `weston`.

### Fin de la connection

Utiliser simplement le racoursis clavier `Ctrl + D` (sur votre ordinateur) pour fermer la connection ssh.


## Transfert de fichier

Vous pouvez utiliser le ssh pour transférer des fichiers entre votre ordinateur et le STM32. Vous pouvez envoyer ou recevoir des fichiers. Utiliser la commande `scp` :

### Envoyer un fichier

```bash
scp fichier.txt root@<adress ip>:/chemin/de/la/copie/
```

### Recevoir un fichier

```bash
scp root@<adress ip>:/chemin/du/fichier.txt ./
```

> Metter `./` a la fin de la commande pour récupérer le fichier dans le dossier courant, sinon metter le chemin du dossier de destination.

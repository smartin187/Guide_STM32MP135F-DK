# Configurer le STM32 et le personnaliser

La configuration de l'interface Weston et d'autres paramètres, comme le clavier (AZERTY), se fait dans le fichier `~/.config/weston.ini`.

> Par défaut, ce fichier n'existe pas. Créez-le pour le configurer.

Utilisez le fichier `weston.ini` du dépôt comme exemple.

Si vous souhaitez seulement mettre le clavier en AZERTY :

```ini
[keyboard]
keymap_layout=fr
```

L'exemple de fichier INI ajoute aussi un fond d'écran et un bouton « Arrêt » dans la barre de lancement. Si vous utilisez ce fichier, copiez également l'image de fond d'écran et le fichier `arret.sh`.

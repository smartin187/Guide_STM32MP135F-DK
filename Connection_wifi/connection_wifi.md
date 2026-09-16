# Connecter le STM32 au Wi-Fi

Guide pour connecter le STM32 au Wi-Fi.

## Fichier de configuration

Créez ou remplacez le fichier de configuration `/etc/wpa_supplicant.conf`.

```wpa_supplicant.conf
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=weston
update_config=1
country=FR

network={
        ssid="nom_réseau"
        psk="mot_de_passe"
        key_mgmt=WPA-PSK

}
```

> Remplacez `GROUP=weston` si vous avez modifié les groupes. Sinon, gardez cette valeur telle quelle.

## Lancement manuel

Exécutez les commandes suivantes en tant qu'administrateur (`su`) :

- `wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf` (utilisation du fichier de configuration pour la connexion)
- `udhcpc -i wlan0` (obtention d'une adresse IP)

Vous devriez être connecté. Testez la connexion avec `ping`.

## Lancement automatique

Avec le [lancement manuel](#lancement-manuel), la connexion est perdue à chaque redémarrage.

Pour lancer la connexion automatiquement, créez le fichier `/etc/rc.local` :

```bash
#!/bin/bash
su -c "wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf"
su -c "udhcpc -i wlan0"
exit 0
```

Si le fichier existe déjà, ajoutez les deux lignes avant `exit 0`.

Redémarrez le STM32, attendez quelques secondes que la connexion soit établie, puis vérifiez-la avec `ping`.


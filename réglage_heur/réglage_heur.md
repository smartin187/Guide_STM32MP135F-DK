# Réglage de l'heure et mise à jour avec `apt`

Par défaut, l'heure du STM32 est réglée sur l'année `2022`. Cela pose notamment problème avec `apt`, qui a besoin que l'heure soit correcte.

Commencez par régler l'heure manuellement afin de pouvoir installer avec `apt` un paquet de mise à jour de l'heure.

## Réglage manuel

Saisissez la commande avec l'heure actuelle (il peut y avoir un léger décalage) :

```bash
date -s "2026-06-29 12:00:00"
```

Vérifiez l'heure avec la commande suivante :

```bash
date
```

## Mise à jour `apt`

> Les commandes suivantes doivent être exécutées en tant qu'administrateur (`su`).

Mettez les paquets à jour :

```bash
apt update

# facultatif (mise à jour du système) :
apt full-upgrade
```

Installez ensuite le paquet `ntpdate` :

```bash
apt install ntpdate
```

Exécutez ensuite :
```bash
ntpdate pool.ntp.org
```

> L'heure peut avoir un décalage correspondant au fuseau horaire, mais cela ne pose pas de problème avec `apt`.

L'heure sera correcte. En revanche, si vous arrêtez le STM32, elle ne sera pas actualisée pendant ce temps. Consultez la section [mise à jour automatique](#mise-à-jour-automatique).

## Mise à jour automatique

Dans le fichier `/etc/rc.local`, ajoutez la ligne suivante avant `exit 0` (ou créez le fichier s'il n'existe pas, avec la ligne `exit 0` à la fin, en plus de la ligne suivante) :

```bash
su -c "ntpdate pool.ntp.org"
```

Normalement, après avoir redémarré le STM32, l'heure sera automatiquement mise à jour.

> Note : l'heure peut mettre du temps à se synchroniser, surtout s'il y a d'autres commandes dans `rc.local`, notamment une connexion Wi-Fi, qui peut être nécessaire pour la mise à jour de l'heure.


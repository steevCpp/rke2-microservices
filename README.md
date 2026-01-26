# 1. Installation de RKE2 sur deux servers ubuntu
- a. Prérequis: https://www.suse.com/suse-rke2/support-matrix/all-supported-versions/rke2-v1-34/

- b. Réseau

Ouverture de ports

`sudo systemctl disable --now ufw && sudo systemctl disable --now apparmor.service`

# 2. Architecure technique

# 3. Configuration

- a. Mise à jour et configuration de la VM
 
Mise à jour de la VM contoller plan

```
sudo apt update && sudo apt upgrade -y
```

Configuration du nom de la machine

```
hostnamectl set-hostname rke2-server
```
vim  /etc/hosts et ajout de contollerplan

- b. Installation de rke2 sur contollerplan

On passe en mode root

```
sudo su -
```
Récupération du script d'installation de rke2 et exécution du script

```
curl -sfL https://get.rke2.io | sh -
```
Activation et démarrage du service rke2-server.service

```
systemctl enable rke2-server.service
```

```
systemctl start rke2-server.service
```


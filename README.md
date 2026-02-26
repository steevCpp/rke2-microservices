# 1. Contexte
Installation d'un cluster k8s via rancher et configuration de cilium comme ingress controller, et deployement HA d'une application wordpress.

## Prérequis

- a. vm : https://www.suse.com/suse-rke2/support-matrix/all-supported-versions/rke2-v1-34/

- b. Réseau

Ouverture de ports

`sudo systemctl disable --now ufw && sudo systemctl disable --now apparmor.service`

# 2. Architecure technique

Nous sommes sur un environnement hybride composé de 3 serveurs:
- un wsl ubuntu24.04  qui servira de control plan  
- deux vm ubuntu24.04 sur virtuelbox

# 3. Installation et configuration du cluster

- a. Mise à jour de la VM contoller plan

```
sudo apt update && sudo apt upgrade -y
```

Configuration du nom de la machine

```
hostnamectl set-hostname ubuntu
```
vim  /etc/hosts et ajout de contollerplan

- b. Installation et configuration de rke2 sur contollerplan `ubuntu`

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

- c. Installation et configuration des nodes `node-1-rke2` `node-2-rke2`

Mise à jour de la VM contoller plan

```
sudo apt update && sudo apt upgrade -y
```

Nommage des vms

```
hostnamectl set-hostname node-1-rke2
```


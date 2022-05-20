# serveur nfs

## Description

NFS est l'abréviation de Network File System, c'est-à-dire système de fichiers réseau.

Ce système de fichiers en réseau permet de partager des données principalement entre systèmes de type UNIX mais des versions existent également pour Microsoft Windows™ et Mac.
NFS est compatible avec IPv6 sur la plupart des systèmes.

## Installation coté serveur

Mettre à jour la liste des paquets :

> ``sudo apt install update``

Installez sur le serveur NFS (le paquet **nfs-kernel-server**)

>`sudo su`<br>
>`apt-get install nfs-kernel-server`

## Configuration

La configuration d'un 'export' NFS se fait en éditant le fichier **/etc/exports**

>`nano /etc/exports`

ajouter les lignes
```
/partage 192.168.1.29(rw)
/partage 192.168.1.0/24(ro)
```

Redémarrer le service nfs

>`service nfs-kernel-server restart`

## Installation (poste client)

Le paquet nécessaire pour accéder à un NFS est nfs-common

>`apt-get install nfs-common`

## Montage (poste client)

Monter le système de fichier depuis l'hôte `192.168.1.51 et le dossier `/partage`

> `mount `192.168.1.51:/partage /mnt -t nfs

Vérifier si le système de fichier est bien monté

> `df -h`

![](images/nfs.png)

Démonter le dossier **/mnt**

> `umount /mnt`

Créer un nouveau dossier de destination dans lequel le NFS viendra se loger

>`mkdir /partage_nfs`

Vous pouvez créer un répertoire du nom de votre choix; dans ce cas adaptez les instructions suivantes au besoin.

Pour ce faire, il suffit de modifier le fichier **/etc/fstab**

>`nano /etc/fstab`

Et ajouter le ligne :
```
# Pour mon montage NFS
192.168.1.51:/partage /partage_nfs nfs rw 0 0
```

Vérification du montage

> `mount -a` <br>
> `df -h`

![](images/nfs2.png)

Vérifier que le montage fonctionne après le redémarrage du poste

> `cd /partage_nfs`<br>
> `ls -l`

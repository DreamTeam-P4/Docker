# Comment utiliser Docker sur un projet Laravel
<img src="https://cdn.1min30.com/wp-content/uploads/2018/04/Symbole-Docker-500x281.jpg"  width=100%  />

# Pourquoi utiliser Docker 

Docker introduit un logiciel pour automatiser le déploiement et la gestion des applications dans un environnement de virtualisation au niveau du système d’exploitation. Il permet d` »emballer » une application avec tout son environnement et ses dépendances dans un conteneur qui peut être déplacé sur n’importe quel système basé sur Linux avec prise en charge « cgroups » dans le noyau, et fournit un environnement de gestion de conteneurs. 

# Commande de base
installer un OS par exemple => ubuntu
```yml
docker pull ubuntu
```

<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker1.PNG"  width=100%  />

Pour y acceder 
```yml
docker run -it ubuntu 
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker2.PNG"  width=100%  />

Exemple2 : Installer Mysql sur docker

```yml
docker run --name mysql-epsilon -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:5.7
```
Pour lister les images installer 
```yml
docker ps
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker3.PNG"  width=100%  />

pour supprimer, utiliser la commande "docker rm". En y ajoutant les options "-vf", la suppression est forcée et l'espace disque est récupéré. Cela ne supprime pas les images. Vous devez ensuite utiliser la commande "docker rmi" en forçant la suppression pour également supprimer les images.

```yml
docker rm -vf bec
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker5.PNG"  width=100%  />

```yml
docker ps
```
confirmation de la suppression
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker6.PNG"  width=100% />









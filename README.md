# Comment utiliser Docker sur un projet Laravel
<img src="https://cdn.1min30.com/wp-content/uploads/2018/04/Logo-Docker.jpg"  width=100%  />

# Pourquoi utiliser Docker 

Docker introduit un logiciel pour automatiser le déploiement et la gestion des applications dans un environnement de virtualisation au niveau du système d’exploitation. Il permet d` »emballer » une application avec tout son environnement et ses dépendances dans un conteneur qui peut être déplacé sur n’importe quel système basé sur Linux avec prise en charge « cgroups » dans le noyau, et fournit un environnement de gestion de conteneurs. 

# Commande de base
installer un OS par exemple => ubuntu
```yml
docker pull ubuntu
```

<img src="docker1.jpg"  width=100%  />

Pour y acceder 
```yml
docker run -it ubuntu 
```
<img src="docker1.jpg"  width=100%  />



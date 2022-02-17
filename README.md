# Comment utiliser Docker sur un projet Laravel
<img src="https://cdn.1min30.com/wp-content/uploads/2018/04/Symbole-Docker-500x281.jpg"  width=100%  />

# Pourquoi utiliser Docker 

Docker introduit un logiciel pour automatiser le déploiement et la gestion des applications dans un environnement de virtualisation au niveau du système d’exploitation. Il permet d` »emballer » une application avec tout son environnement et ses dépendances dans un conteneur qui peut être déplacé sur n’importe quel système basé sur Linux avec prise en charge « cgroups » dans le noyau, et fournit un environnement de gestion de conteneurs. 

# Commande de base
Exemple1:installer un OS par exemple => ubuntu
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


```yml
docker exec -it bec bash
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker7.PNG"  width=100%  />

pour supprimer, utiliser la commande "docker rm". En y ajoutant les options "-vf", la suppression est forcée et l'espace disque est récupéré. Cela ne supprime pas les images. Vous devez ensuite utiliser la commande "docker rmi" en forçant la suppression pour également supprimer les images.

```yml
docker rm -vf bec
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker4.PNG"  width=100%  />

```yml
docker ps
```
confirmation de la suppression
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/docker6.PNG"  width=100% />

# II COmment utiliser Docker sur un projet Laravel

Commencons d'abord par creer un projet Laravel

```
composer create-project --prefer-dist laravel/laravel epsilonDemo

```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/lara1.PNG"  width=100% />

creer une fichier  
# > docker-compose.yml
 C est sur ce fichier que nous allons definir les définir les differents dependances de notre projet 😁😁😁😁😁<br>
 C est fini les "Pourquoi le projet ne marche pas chez moi 🤦‍♂️🤦‍♂️🤦‍♂️🤦‍♂️🤦‍♂️🤦‍♂️"<br>
 Avec Docker on est tous nikel.<br>
 C'est top ca. 
 ```yml
 version: '3.9'

networks:
  laravel:

services:
  nginx:
    build:
      context: .
      dockerfile: docker/nginx.dockerfile
    ports:
      - 8098:80
    volumes:
      - ./:/var/www/html
    links:
      - fpm
    networks:
      - laravel

  fpm:
    build:
      context: .
      dockerfile: docker/fpm.dockerfile
    volumes:
      - ./:/var/www/html
    links:
      - db
    networks:
      - laravel

  db:
    image: mysql:5.7
    ports:
      - 3306:3306
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_USER=root
      - MYSQL_PASSWORD=ok
      - MYSQL_DATABASE=laravel
    networks:
      - laravel
```

Creer un dossier Doker sur votre projet & le fichier( nginx.dockerfile && fpm.dockerfile)
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/lara3.PNG"  width=100% />

# nginx.dockerfile
```yml
FROM nginx

ADD docker/conf/vhost.conf /etc/nginx/conf.d/default.conf

WORKDIR /var/www/html
```
# fpm.dockerfile
```yml
FROM php:8.1-fpm

RUN apt-get update \
    && docker-php-ext-install pdo pdo_mysql
```
Creer un autre dossier sur le dossier Docker => conf
Ce dossier permet de specifier la configuration de docker.
#  vhost.conf

```yml
server {
    listen 80;
    server_name _;
    root /var/www/html/public;
    index index.php;
    error_log /var/log/nginx/error.log;
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location ~ \.php$ {
        fastcgi_pass fpm:9000;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
```

# La derniere etape

lancer la commande

```
docker-compose build
```

<img src="https://github.com/DreamTeam-P4/Docker/blob/main/lara-build.PNG"  width=100% />

Ensuite demarrer les services .

```yml
docker-compose up -d
```

<img src="https://github.com/DreamTeam-P4/Docker/blob/main/lara-up.PNG"  width=100% />

❤❤❤❤❤❤❤❤❤❤❤👏👏👏👏👏👏👏👏

Maintenant il est temps de verifier 

```yml
docker ps
```
<img src="https://github.com/DreamTeam-P4/Docker/blob/main/lara-verif.PNG"  width=100% />

C'est fini 
On lance notre application sur le port spécifié => pour nous c est 8089
# localhost:8098


<img src="https://github.com/DreamTeam-P4/Docker/blob/main/terminé.PNG"  width=100% />



# Auteur => Epsilon

<img src="https://thumbs.gfycat.com/DeadHandyLaughingthrush-max-1mb.gif"  width=100% />















 















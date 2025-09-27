# 🐋 Introduction à Docker --- Jour1
Ce projet retrace mon initiation à Docker, en détaillant les concepts fondamentaux et en les illustrant par des exemples concrets.
Il s'agit de la documentation de ma première immersion dans Docker, comprenant une exploration des concepts de base et leur mise en pratique.
Ce repository consigne les découvertes et les expérimentations de ma première journée à découvrir Docker, de la théorie aux applications pratiques.
   
     Docker Desktop installé et lancé
     Accès à un terminal (CLI)
     Connaissances de base en lignes de commande Unix/bash

📒 Concepts Découverts - Jour 1

Commandes de Vérification et d'Information.
Ces commandes permettent de s'assurer que l'environnement Docker est prêt.
    
     docker --version: Affiche la version de Docker CLI.
     docker info: Fournit des informations détaillées sur l'installation et l'environnement Docker.

Gestion du Cycle de Vie d'un Conteneur.
Les commandes de base pour contrôler l'état d'un conteneur ont été pratiquées.

Exécution (run) : Lance un nouveau conteneur à partir d'une image.  
Listage (ps) : Affiche les conteneurs actifs.  
Arrêt (stop) : Stoppe un conteneur en cours d'exécution.  
Démarrage (start) : Redémarre un conteneur arrêté.

📈 Mise en Pratique : Déploiement d'un Serveur Web Apache.

Pour concrétiser ces concepts, un conteneur Apache a été déployé.  
Commande de déploiement :  

     docker run -d -p 8000:80 --name mon-apache httpd
 
Vérification : Le serveur est accessible via l'URL http://localhost:8000 dans le navigateur web.

# 🐋 Introduction à Docker --- Jour2

Ce projet retrace ma deuxième journée d’apprentissage de Docker, en abordant des notions plus avancées ainsi que des applications concrètes.   

📋Jour 1 en résumé  

-Test de l’installation de Docker  
-Exécution de conteneurs Nginx et Apache  
-Manipulation simple des conteneurs (démarrage et arrêt)  

🚀 Notions abordées lors du Jour 2  
Gestion des images Docker

    Afficher la liste des images présentes localement  
    docker images  

    Effectuer une recherche d’image sur Docker Hub  
    docker search redis  

    Télécharger une image sans la lancer  
    docker pull mysql:8.0  

    Supprimer une image du système  
    docker rmi nom-image  

🔎 Inspection des conteneurs 

    Consulter les journaux d’un conteneur  
    docker logs mon-premier-nginx  

    Afficher les processus actifs dans un conteneur  
    docker top mon-premier-nginx  

    Examiner les informations détaillées d’un conteneur  
    docker inspect mon-premier-nginx  

    Visualiser les statistiques d’utilisation des ressources  
    docker stats  

🖥️ Conteneurs interactifs

    Démarrer un conteneur Ubuntu en mode interactif  
    docker run -it --name mon-ubuntu ubuntu /bin/bash  

    Lancer une commande dans un conteneur déjà en cours d’exécution  
    docker exec -it mon-premier-nginx /bin/bash  

    Déployer un conteneur MySQL avec des variables d’environnement définies  
    docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=mon_mot_de_passe -p 3306:3306 mysql:8.0  

⚙️ Gestion avancée des conteneurs

    Changer le nom d’un conteneur  
    docker rename mon-premier-nginx nginx-server  

    Générer une nouvelle image à partir d’un conteneur modifié  
    docker commit nginx-server nginx-personnalise  

    Effacer un conteneur qui a été arrêté  
    docker rm nginx-server  

    Supprimer en une fois tous les conteneurs arrêtés  
    docker container prune  

🎯 Cas pratique : Application multi-conteneurs  

Mise en place d’une application web basique composée d’un serveur Nginx et d’une base de données Redis:  

Démarrer un conteneur Redis:  

    docker run -d --name redis-server redis  

Lancer un conteneur Nginx relié à Redis:  

    docker run -d --name web-app --link redis-server:redis -p 8080:80 nginx  

🔧 Commandes de gestion des volumes Docker  

Création de volume:  

    # Créer un nouveau volume
    docker volume create mon-volume

    # Alternative : Générer un volume de stockage
    docker volume create mon-volume  

Liste des volumes:

    # Afficher la liste des volumes
    docker volume ls

    # Alternative : Lister tous les volumes disponibles
    docker volume ls  

Container avec volume:

    # Démarrer un container avec montage de volume
    docker run -d --name nginx-with-volume -v mon-volume:/usr/share/nginx/html -p 8082:80 nginx

    # Alternative : Lancer un conteneur avec volume attaché
    docker run -d --name nginx-with-volume -v mon-volume:/usr/share/nginx/html -p 8082:80 nginx  

Inspection de volume:

    # Examiner les détails d'un volume
    docker volume inspect mon-volume

    # Alternative : Obtenir les informations détaillées d'un volume
    docker volume inspect mon-volume  
🔄 Stratégies de redémarrage automatique des conteneurs

Redémarrage systématique:

    # Déployer un conteneur avec redémarrage automatique permanent
    docker run -d --name nginx-always --restart always -p 8083:80 nginx  

Redémarrage conditionnel sur échec:

    # Lancer un conteneur avec redémarrage uniquement en cas d'échec (5 tentatives max)
    docker run -d --name nginx-on-failure --restart on-failure:5 -p 8084:80 nginx  

# 🐋 Introduction à Docker --- Jour3  

Ce dossier retrace ma troisième journée de formation Docker, consacrée à l'approfondissement des Dockerfiles, des réseaux Docker et de la création d'images sur mesure.  

📚 Bilan du Jour 2  
   
    *Manipulation des images Docker (téléchargement, suppression, recherche)  
    *Analyse détaillée et consultation des journaux des conteneurs  
    *Utilisation de conteneurs interactifs (Ubuntu, MySQL)  
    *Gestion avancée des conteneurs (renommage, création d'images, nettoyage)  
    *Déploiement d'applications multi-conteneurs (Nginx + Redis)  
    *Gestion des volumes Docker  
    *Configuration du redémarrage automatique des conteneurs  

🚀 Acquis du Jour 3  

1️⃣ Développement d'images personnalisées via Dockerfile  

Un Dockerfile sert à concevoir une image Docker personnalisée selon des spécifications précises.  

    # Illustration : Construire une image Nginx customisée
    FROM nginx:latest
    COPY ./site-html /usr/share/nginx/html
    EXPOSE 80  

🔨 Construction et exécution de l'image personnalisée :

Générer l'image à partir du Dockerfile  

    docker build -t mon-nginx-personnalise .

Déployer un conteneur utilisant cette nouvelle image  

    docker run -d -p 8085:80 --name nginx-custom mon-nginx-personnalise  

2️⃣ Réseaux Docker  

Docker met à disposition plusieurs types de réseaux pour interconnecter les conteneurs.  

Afficher la liste des réseaux disponibles

    docker network ls  

Créer un réseau bridge personnalisé  

    docker network create mon-reseau  

Déployer deux conteneurs interconnectés sur le même réseau  

    docker run -d --name redis-db --network mon-reseau redis
    docker run -d --name app-web --network mon-reseau nginx  

🔍 Vérification de la connectivité :  
Tester la communication entre les conteneurs  

    docker exec -it app-web ping redis-db  

3️⃣ Variables d'environnement et fichiers .env  

Définir des configurations via des variables d'environnement dans un conteneur :  

    # Lancer un conteneur avec variables d'environnement directes
    docker run -d --name app-env -e APP_ENV=production -e APP_DEBUG=false nginx  

📁 Utilisation d'un fichier .env :  

Fichier .env :  

    MYSQL_ROOT_PASSWORD=supersecret
    MYSQL_DATABASE=appdb  

Commande de déploiement :  

    docker run -d --name mysql-env --env-file .env mysql:8.0  

4️⃣ Partage de fichiers via bind mounts  

Contrairement aux volumes classiques, les bind mounts permettent de lier directement un répertoire local à un conteneur.  

    docker run -d --name nginx-bind \
      -v $(pwd)/site-html:/usr/share/nginx/html \
      -p 8086:80 nginx  

🎯 Cas Pratique : Application Web + Base de données avec réseau personnalisé et Dockerfile  

🌐 Création d'un réseau dédié  

    docker network create app-network  

🗄️ Déploiement de la base de données MySQL  

    docker run -d --name db-app \
      --network app-network \
      -e MYSQL_ROOT_PASSWORD=monpass \
      -e MYSQL_DATABASE=appdb \
      mysql:8.0  

🔨 Développement de l'application PHP avec Dockerfile  
Dockerfile :  

    FROM php:7.4-apache
    RUN docker-php-ext-install mysqli
    COPY ./src /var/www/html
    EXPOSE 80  

🚀 Construction et déploiement de l'application  

    docker build -t php-app .
    docker run -d --name web-app --network app-network -p 8087:80 php-app  

🔗 Fonctionnement  
L'application PHP pourra communiquer avec la base MySQL via le nom db-app grâce au réseau partagé.  




      

    


    


    


    













    

    

    




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
    

    




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

# Laravel Docker

Un projet docker compose que j'ai créer dans le but de pouvoir mettre en place rapidement un tel projet dans une équipe.

(ce README sera amené à évoluer au fur et à mesure qu'on rencontre des problèmes)

## Mise en place du projet

- installer Docker et Docker Compose
- (optionnel) faire la config pour ne plus avoir à utiliser sudo
pour exécuter Docker (sinon, on le met à chaque fois)

- Cloner ce projet, ainsi que le projet Laravel si ce n'est pas déjà fait, il doivent être dans le même dossier :
```
xxx
  /laravel-docker
    /...
  /projet-laravel
    /... 
```
- Entrer dans le projet docker : `cd laravel-docker`
- Copier le `.env` : `cp .env.dist .env`, et éventuellement le personnaliser
- Construire les conteneurs : `[sudo] ./tools/dkup.sh`
- Vérifier que vous avez 4 conteneurs de lancé : `[sudo] docker ps`

Si vous avez un problème, vous pouvez utiliser la commande `[sudo] ./tools/dklogs.sh <nom du service Compose>`

## Liste des conteneurs / services

- webserver : Nginx, serveur web accessible sur le port 8989 (je le rendrai personnalisable plus tard)
- engine : PHP-FPM, c'est lui qui s'exécutent pour traiter les requêtes HTTP (les commandes php se feront sur un CLI, pour l'instant sur le système hôte)
- db : MySQL, base de données, **à configurer dans le .env avant de construire**
- phpmyadmin : accessible sur localhost:8020

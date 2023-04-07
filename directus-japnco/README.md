# Projet - Jap&Co
![LogoJap&Co](../src/assets/LogoJapnco.png)

***

## Introduction

Notre site web a pour objectif de créer une plateforme en ligne complète pour les
passionnés de la culture japonaise et les voyageurs qui cherchent à découvrir le pays.
Nous sommes convaincus que notre site web sera une ressource précieuse pour tous ceux
qui cherchent à en apprendre davantage sur le Japon, et nous avons hâte de partager
notre passion avec vous.

***

## Installation

1. Clonez ce repo sur sa machine : 
```bash
git clone ...
```
2. Ouvrir le repo depuis son terminal.
   
3. Une fois ouvert dans VS Code vous pouvez lancer la commande suivante pour installer et demarrer Directus : 
```bash
npx directus start
```
🚨 Cette commande fonctionne seulement si Directus a déjà été installer au moins 1 fois  sur ça machine, sinon ça sera la commande suivante : 🚨
```bash
npm install
```
4. Une fois tout installer, pensez a crée un fichier `.env` depuis l'`.env.example`, demander en MP les données des lignes 190 et 191 et les modifier afin depouvoir acceder au serveur Directus.
   
5. Voila, normalement tout doit fonctionner correctement ! 👍

***

## Routes back

***⚠️ Toutes les routes backs sont dans le README, donc c'est normale de ne pas voir toutes les routes dans Insomnia, car elles ne sont pas faites. ⚠️***

***N.B : Un [fichier Insomnia](/directus-japnco/doc/Insomnia_routes_back) (en JSON) sera envoyer à recuperer sur son PC. Ouvrir Insomnia, appuyer sur importer/exporter, selectionner le fichier JSON à importer. Cela vous créera le "Dashboard - Jap&Co" avec les requetes effectuer.***

### Coté ADMIN

***

#### ROLE

🟩POST /roles (crée un role)

🟪GET /roles (liste pour obtenir id des roles)

🟥DELETE /role (supprimer un role)

🟨PATCH /role (modifier un role)

#### USER

🟩POST /users (pour crée un nouveau user avec un rôle au choix(via son id))

🟪GET /users (liste des users)

🟥DELETE /users (supprimer un user)

🟨PATCH /users (modifier un user)

#### ARTICLE

🟨PATCH /items/Article/:id (modifier un article)

🟨PATCH /items/Comment/:id (modifier un article)

***

### Coté UTILISATEUR

#### USER

🟩POST /users (pour s'inscrire avec le rôle "Private" attribué par défaut et non-modifiable par le user)

🟥DELETE /users/:id (supprimer son compte)

🟨PATCH /users/:id (modifier infos de son compte)

***

### Coté USER et ADMIN

#### AUTHENTIFICATION

🟩POST /auth/login (pour se connecter)

🟩POST /auth/refresh (pour se connecter)

🟩POST /auth/logout (pour se connecter)

🟩POST /auth/password/request (email envoyer avec lien pour reset sont mot de passe)

🟩POST /auth/password/reset (email redirigeant sur la page pour reset son mot de passe avec le token de l'email)


#### ARTICLE

🟩POST /items/Article (pour poster un nouveau article)

🟪GET /items/Article (pour obtenir les articles)

🟥DELETE /items/Article/:id (supprimer son article)

#### COMMENTAIRE

🟩POST /items/Comment (pour commenter un article)

🟪GET /items/Comment (pour voir tout les commentaires)

🟥DELETE /items/Comment:id (supprimer son commentaire)

#### IMAGES

🟩POST /files/import (pour importer une image via un url)

🟩POST /files (pour telecharger une image depuis son PC)

🟪GET /files/all (pour voir toute les images)

🟥DELETE /files/:id (supprimer une image)

***
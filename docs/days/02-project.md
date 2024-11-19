# Jour 2 : Le projet

Aujourd'hui, on va définir les spécifications du projet. Ce sont les mêmes que le [Jobeet originel](https://symfony.com/legacy/doc/jobeet/1_4/fr/02)

## *User stories*

Il y a plusieurs types d'utilisateurs de la plateforme que nous allons créer :

- l'**admin** qui administre et configure le site
- l'**usager** qui cherche un emploi
- l'**entreprise** qui poste des offres d'emploi
- l'**affilié** qui republie des offres sur son site

Dans le tutoriel originel, il y avait deux « applications », une pour le frontend (recherche d'emploi,...) et une pour le backend (administration).

Avec F3, nous n'allons pas faire pareil. Il y aura qu'une application avec un espace sécurisé pour les admins.

### « Front »

#### Histoire 1 : la page d'accueil et les derniers jobs

Sur la page d'accueil, on retrouve la liste des 10 derniers jobs classés par catégories.
Seulement la localisation, le poste et l'entreprise sont indiqués pour chacun des jobs.

Pour chaque catégorie, un lien permet d'aller sur la liste de tous les jobs de cette catégorie.

Il y a également une recherche et un lien pour poster un job.

#### Histoire 2 : Liste des jobs d'une catégorie

L'usager voit la liste, paginée par 20, de tout les jobs d'une catégorie.

#### Histoire 3 : Filtre de la liste avec des mots-clés

L'usager peut rechercher via des mots-clés pour affiner les résultats. Les mots-clés peuvent être basé sur la localisation, le poste, la catégorie ou l'entreprise.

#### Histoire 4 : La fiche

L'usager peut sélectionner une offre pour voir plus d'information à propos de l'offre.

#### Histoire 5 : Création d'un job

Une entreprise peut poster un job. Plusieurs infos sont requises :

- Le nom de l'entreprise
- Le type (CDI, CDD, Interim, …)
- Un logo (optionel)
- Une URL (optionel)
- Une localisation
- Un poste
- Une catégorie (liste prédéfinie)
- Une description de l'offre
- Comment postuler
- Ouvert publiquement (publiable sur d'autres sites)
- L'email du créateur

Le processus se fait en deux étapes : l'entreprise rempli les champs requis, arrive sur une page de prévisualisation et valide son offre.

Il n'y a pas besoin de créer un compte pour créer un job. L'offre peut être modifiée plus tard grâce à une URL secrète générée et envoyée au créateur.

Chaque job est affiché pendant 30 jours (configurable dans l'administration). L'entreprise peut venir réactiver l'offre ou étendre pour 30 jours de plus seulement si l'offre expire dans moins de 5 jours.

#### Histoire 6 : Demande d'affiliation

Un utilisateur peut demander à devenir affilié pour pouvoir utiliser l'api et récupérer des jobs.

Pour faire la demande, 3 informations sont nécessaires :

- Un nom
- Un email
- L'url de son site

L'affilié doit être activé par un admin. Une fois activé, l'affilié reçoit un token par email.

#### Histoire 7 : L'affilié récupère des jobs

Grâce à son token, l'affilié récupère la liste des jobs via l'api. Cette liste peut être dans plusieurs formats : XML, JSON, YML.
Il peut filtrer la liste numériquement, ou par catégorie.

### « Back »

#### Histoire 8 : L'admin configure le site

L'admin configure la liste des catégories disponibles, et le temps d'affichage des jobs.

#### Histoire 9 : L'admin gère des jobs

Un admin peut éditer ou supprimer des jobs de la liste.

#### Histoire 10 : L'admin gère les affiliés

L'admin peut créer ou éditer des affiliés. Il est responsable de l'activation et peut en désactiver. Quand un admin active un affilié, le système créé un nouveau token qui est associé à l'affilié.

## La suite

La suite du tutoriel : [Jour 3](03-models.md)
Le jour précédent : [Jour 1](01-starting.md)
L'[index](../../README.md)

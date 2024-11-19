# Jour 1 : Démarrage du projet

<!--toc:start-->
- [Jour 1 : Démarrage du projet](#jour-1-démarrage-du-projet)
  - [Prérequis](#prérequis)
  - [Arborescence de base](#arborescence-de-base)
  - [Installation du framework](#installation-du-framework)
    - [Décompresser l'archive](#décompresser-larchive)
    - [Composer](#composer)
  - [Hello world](#hello-world)
  - [La suite](#la-suite)
<!--toc:end-->

## Prérequis

Ce guide va se focaliser sur un environnement Linux.

Il est nécessaire d'avoir une version de PHP récente (7.4+) même si le framework F3 à la rétrocompatibilité jusqu'à
PHP 5.4. Au moins le module `PDO` est nécessaire pour la connexion à une base de donnée.

## Arborescence de base

Fatfree est assez permissif sur l'arborescence d'un projet. Une arborescence type, respectant le MVC, pourrait se traduire ainsi :

```sh
.
├── app
│   ├── Controllers
│   └── Models
├── db
├── public
│   ├── css
│   ├── index.php
│   └── js
├── vendor
└── views
```

| Répertoire | Description |
|------------|-------------|
| app/       | Toutes les classes relatives à l'application |
| app/Controllers | Les controllers de l'application |
| app/Models | Les modeles de l'application |
| db/        | Tout ce qui est relatif à la base (base sql, migrations, …) |
| vendor/    | Les libs externes à l'application |
| views/     | Les vues de l'application |
| public/    | La configuration du serveur web doit pointer sur ce dossier |

## Installation du framework

Il existe deux moyens d'installer le framework :

### Décompresser l'archive

La méthode la plus simple. [Téléchargez](https://github.com/bcosca/fatfree-core/releases/latest) la version la plus récente du framework, et décompresser l'archive dans le dossier `vendor` puis renommez le en `fatfree-core`.

### Composer

[Composer](https://getcomposer.org) permet la gestion et la mise à jour de dépendance dans un projet PHP.

Pour l'installer, il suffit de faire un `composer require bcosca/fatfree-core` à la racine du projet. Il installera le framework dans le dossier `vendor` (en plus des fichiers dont composer à besoin).

## Hello world

Il est temps de faire notre première page avec le framework.

Dans votre éditeur, ouvrez le fichier `public/index.php` et écrivez ceci :

```php
<?php

$f3 = require (__DIR__.'/../vendor/fatfree-core/base.php');
$f3->route('GET /', function () {
    echo "Hello world !";
});

$f3->run();
```

Si vous avez opté pour l'installation via composer, remplacez uniquement la première ligne par :

```diff
 <?php
 
-$f3 = require (__DIR__.'/../vendor/fatfree-core/base.php');
+require __DIR__.'/../vendor/autoload.php';
+$f3 = \Base::instance();
 $f3->route('GET /', function () {
     echo "Hello world !";
 });
 
 $f3->run();
```

Pour voir le résultat, ouvrez un terminal à la racine du projet, et lancez le serveur de développement de php :
```sh
php -S localhost:8000 -t public
```

Ouvrez ensuite votre navigateur [](http://localhost:8000) ! Tada !

## La suite

La suite du tutoriel se situe ici : [Jour 2, le projet](02-project.md)

Retour à [l'index]()

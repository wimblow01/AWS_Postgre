# Une infra dans le Cloud
 
## Contexte du projet

Vous devez mettre en place, pour votre équipe, une infrastructure. Le choix se porte sur AWS, car vous n'avez personne en interne avec les compétences requises pour déployer et maintenir une infrastructure physique. De plus, les services élastiques proposées par Amazon répondent au besoin de scalabilité de l'infra.

L'infrastructure doit inclure une base PostgreSQL (sur RDS, donc) et une API proposant l'accès à cette base (sur EC2). Le fichier SQL servant à créer la base doit être sauvegardé sur S3.

L'API est codée en Python, langage largement maîtrisé par les équipes.

## 1. Mise en place de l'instance EC2

Pour ce faire, j'ai utilisé la version gratuite d'`EC2` qui nous propose de travailler avec une image d'`Ubuntu 20.04`.

La connection se fait ensuite via `VSCode` en `SSH` afin de pouvoir travailler dans la VM et avoir un terminal.

## 2. La base de données

La base de données a été faite sur `PostgreSQL`. Puis j'y ai inséré le fichier SQL de [clubdata](clubdata.sql)

## 3. FastAPI

L'API est faite via `FastAPI` pour sa rapidité et sa simplicité de mise en place. 

Pour faciliter le déploiement de l'API, tout a été fait via un docker-compose. Ce fichier va permettre de créer l'environnement de travail et va lancer le script pour FastAPI

## 4. Opérations

Deux résultats sont obtenus grâce à 2 endpoints:

* la réservation via l'ID ([/booking_by_id/4040](http://35.180.191.25:8080/booking_by_id/4040))

![id](/resources/id.png)

* toutes les réservations pour une personne via son nom et prénom ([/bookings_by_name?firstname=Florence&surname=Bader](http://35.180.191.25:8080/bookings_by_name?firstname=Florence&surname=Bader))

![name](/resources/name.png)
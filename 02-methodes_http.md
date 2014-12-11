# Les méthodes HTTP

Les méthodes HTTP, font parties du protocol. Elles permettent de savoir ce que l'on va chercher.

La liste des méthodes est la suivante :
* OPTIONS
* GET
* HEAD
* POST
* PUT
* DELETE
* TRACE
* CONNECT

Chacune à une fonction bien définie. On peut retrouver leur définition [ici](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9).

Nous allons donc nous intéresser uniquement aux 4 méthodes suivantes :
* GET
* POST
* PUT
* DELETE

## La méthode GET
Elle est dit "Idempotent" et "Safe".

En français, ça donne ça :
* Elle doit pouvoir être appelée plusieurs fois et avoir les mêmes conséquences (idempotent quoi ...).
* Elle ne doit pas permettre d'effectuer des modifications du coté serveur. Uniquement de la récupération.
* Les paramètres sont passés dans l'url sous la forme
  * http://www.picta-it.com/formations?**clé**=**valeur**&**clé**=**valeur**
  * ou
  * http://www.picta-it.com/formations/**valeur**/**valeur**

Ses paramètres sont dans l'url.

Par exemple :
GET http://www.picta-it.com/formation/http HTTP/1.1

Permet d'accéder à la formation http.

## La méthode POST
Elle permet d'ajouter des éléments sur le serveur.

Ses paramètres sont dans le corps du message envoyé au serveur. Le contenu peut être en binaire. Pour envoyer un stream vidéo par exemple.

Par exemple :
POST http://www.picta-it.com/formation HTTP/1.1

Avec un contenu comme :
nom=methodes http
description=...

Permet de créer une nouvelle formation.

## La méthode PUT
Elle est "idempotent", mais pas sécurisée.

Elle permet de modifier une ressource existante à l'URL spécifiée, ou de la créer si elle n'existe pas.

Le coté idempotent signifie que si on l'appelle plusieurs fois avec les mêmes informations, elle fera la même chose. Contrairement à la méthode POST qui ajoute de nouveaux éléments.

Par exemple :
PUT http://www.picta-it.com/formation/pouet HTTP/1.1

Avec un contenu comme :
nom=pouet
description=...

Va modifier la formation "pouet", ou la créer si elle n'existe pas.

## La méthode DELETE
Elle est "idempotent", mais pas sécurisée *(Comme le méthode PUT)*.

Elle permet de supprimer la ressource spécifiée par l'URL. Elle est idempotent, car quoiqu'il se passe, la ressource n'existe plus après.

Par exemple :
DELETE http://www.picta-it.com/formation/pouet HTTP/1.1

Permet de supprimer la ressource.

# HTTP  : La notion Client / Serveur

## Les normes HTTP 1.1 sont décrit dans la [rfc2616](http://www.w3.org/Protocols/rfc2616/rfc2616.html) :

L'URL est découpée en plusieurs parties :
* http :                  Le protocol
* www.picta-it.com :      Le DNS du serveur
* :80 :                   Le port *(facultatif)*
* /test :                 La ressource demandée *(facultatif)*
* ?key1=val1&key2=val2 :  Les paramètres *(facultatif et principalement pour la méthode GET)*

La communication ressemble à ça :

           --- requête -------------------------->
    Client -------------------v------------------- Serveur
           <-------------------------- réponse ---

### Requête *(client -> serveur)*
Le client envoie une requête au serveur au format texte.

Le résultat ressemble à ce qui suit :
En premier, la méthode :
Ex.
GET http://www.picta-it.com/formations HTTP/1.1

Cette partie, est utilisée par Apache, Nginx ou autre pour savoir où on accède sur le serveur.

Pour l'entête *(HEADER)*, une fois parsée en JSON *(pour les couleurs)* ça donne :
```json
{
  'user-agent':       'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:30.0) Gecko/20100101 Firefox/30.0',
  accept:             'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
  'accept-language':  'en-US,en;q=0.5',
  'accept-encoding':  'gzip, deflate',
  cookie:             'cookie=valeur',
  connection:         'keep-alive',
  'cache-control':    'max-age=0'
}
```

On peut trouver un descriptif sur [Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields).

Le corps du message quant à lui, n'est renseigné que pour les méthodes POST et PUT.

### Réponse *(serveur -> client)*
Le serveur répond avec :
En premier, le code de status de la liste [suivante](http://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html)

Ex.
HTTP/1.1 404 Not Found

Cette partie est utilisée pour informer le client de ce qui se passe.

Puis, avec le HEADER *(qui ressemble à celui de la requête)* :
http://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html#sec6.2

Description [Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Response_fields).

Les informations du HEADER permettent par exemple de donner le type MIME, ou de préciser que le fichier est à télécharger et non à interpréter.

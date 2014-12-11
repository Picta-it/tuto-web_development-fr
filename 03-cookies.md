# Les cookies (avec un cappuccino s'il vous plaît)
## Théorie
Les cookies permettent de stocker des informations du coté utilisateur.

Ils sont envoyés par le client au serveur et sont situés dans le header du message envoyé.

La définition d'un Cookie ressemble à ça :

```
Set-Cookie: cle=valeur
```

Et on peut leur définir une durée de validité :

```
Set-Cookie: lu=Rg3vHJZnehYLjVg7qi3bZjzg; Expires=Tue, 15-Jan-2013 21:47:38 GMT; Path=/; Domain=.example.com; HttpOnly
Set-Cookie: made_write_conn=1295214458; Path=/; Domain=.example.com
Set-Cookie: reg_fb_gate=deleted; Expires=Thu, 01-Jan-1970 00:00:01 GMT; Path=/; Domain=.example.com; HttpOnly
```

## Pratique
On y stocke tout ce qu'on veut. Mais ça permet de garder la session de l'utilisateur.

### A ne pas faire
On va commencer par ce qu'on **pourrait**, me que l'on **ne doit pas** faire !

On pourrait très bien stocker les informations suivantes :
* nom=NOM DE L'UTILISATEUR
* mdp=MOT PASSE
* derniers_produits=LISTE SEPARE PAR UNE VIRGULE
* pleins d'autres informations sur l'utilisateur

**Alors, pourquoi ferait-on ça ??**
Le nom et le mot de passe pour rester authentifier **(A NE PAS FAIRE TOUJOURS !!)**.
Et pour garder les informations sur l'utilisateur.

**Et pourquoi on ne fait pas ça.**
Parce que ce n'est pas sécurisé.
Que ce soit le nom d'utilisateur ou le mot de passe. On ne stocke rien de ça dans les cookies.
Idems pour toutes les autre informations.

Il n'y aurait même pas de challenge pour récupérer ce genre d'informations.

### Alors quoi faire
On utilise un token.

Ca va ressembler à ça :
* token=AFx_qI4tB2qWle0QAxl_FElsOcd9fCzYBLt8SCaFkdNKdfeBx9s7XDN...

**Mais ça marche comment ?**
Il s'agit d'une clef qui va permettre a serveur de vous reconnaitre.
Et en fonction de cette clé, le serveur aura les informations nécessaires sur vous de son coté.

Il saura si vous êtes authentifié, si vous avez le droits de faire ce que vous souhaitez.
Et vous pourrez stocker toutes les informations nécessaires pour faciliter la navigation de vos internautes.

### Pour le mettre en place
C'est assez pointu pour optimiser la sécurité.

Le plus simple pour commencer est d'utiliser des frameworks qui le permettent.

Que ce soit en Php, Javascript, Java, Perl ou dans la quasi totalité des langages, c'est implémenté
par défault.

En Php par exemple, il suffira de faire le fameux :
```php
session_start()
```

Si le cookie existe déjà, il le reçoit du HEADER HTTP, et il sait qui vous êtes.
Sinon, il ajoute le cookie au HEADER du message qu'il envoie au client.

# Scénario de motivation Comptes fonciers

## Nom

Suivi des mutations de parcelles à partir des comptes fonciers

## Description

Un compte foncier est une liste d'états des parcelles associé à un ou plusieurs propriétaires. L'ensemble des comptes fonciers d'une commune sont consignés dans la matrice cadastrale. Ces comptes fonciers portent différents noms : **article, folio ou case**.

Chaque compte est scindé en deux parties :
- la liste des propriétaires sucessifs qui lui sont associés, appelés "articles de mutation" dans le <i>Recueil de 1811</i>. ;
- les états des parcelles détenues par ce(s) propriétaire(s), appelés "articles de classement" dans le <i>Recueil de 1811</i>.

Un compte foncier est associé à un numéro (plus rarement à plusieurs). Selon le type de tableau pré-imprimé utilisé, ce numéro peut faire référence à un ou à plusieurs comptes fonciers différents. 

Pour chaque état de parcelle (article de classement = ligne de compte foncier), il est possible d'indiquer de quel compte foncier est issu la précédente mention de la parcelle ("Tiré de") et dans quel compte foncier se trouve la (ou les) mention(s)(s) suivantes ("Porté à"). Les évènements qui concernent les propriétés bâties peuvent également être indiqués dans ces colonnes : "Nouvelle construction" (C.N/N.C), "Augmentation" (Aug), "Evaluation du bâti" (E.B.), "Destruction", "Ruine".

Les lignes obsolètes d'un compte foncier sont rayées. Un compte foncier clos est généralement barré. 

- Les propriétés d'un **article de matrice** sont :
    - *{obligatoire}* son/ses **numéro**(s)
    - *{obligatoire}* le ou les **propriétaires** auquel il a été associé
    - *{optionnel}* son **style** (barré ou non)
    - *{optionnel}* la **zone correspondant au compte dans la page**
    - *{optionnel}* le **numéro du folio où se poursuit le compte foncier** (ex: en cas de manque de place dans la page)
    - *{optionnel}* la **liste des états de parcelles** qu'il mentionne

- Les propriétés d'un **état de parcelle** : 
    - *{obligatoire}* la **section** où se trouve la parcelle
    - *{obligatoire}* l'**identifiant de la parcelle**
    - *{obligatoire}* la **nature** de la parcelle parcelle
    - *{optionnel}* le **style de la ligne** (barré ou non)
    - *{optionnel}* le **numéro de folio précédent**("Tiré de")
    - *{obligatoire}* **le/les numéro(s) de folio(s) suivant**(s) ("Porté à")
    - *{optionnel}* la **date de début de validité** des informations la ligne
    - *{optionnel}* la **date de fin de validité** des informations la ligne
    - *{optionnel}* la **zone où il se trouve dans la page numérisée**

Pour connaître la nature d'une mutation, il faut disposer de deux articles de classement sucessifs traitant de la même parcelle.
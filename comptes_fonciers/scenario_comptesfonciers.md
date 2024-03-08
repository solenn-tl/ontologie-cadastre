# Scénario de motivation Comptes fonciers

## Nom

Comptes fonciers et mutations

## Description

Un compte foncier est une liste d'états des parcelles associé à un ou plusieurs propriétaires (sucessifs ou pas). L'ensemble des comptes fonciers d'une commune sont consignés dans la matrice cadastrale. Ces comptes fonciers portent différents noms dans la documentation cadastrale : **article, folio ou case**.

Dans les documents cadastraux, chaque compte foncier est scindé en deux parties :
- la liste des propriétaires sucessifs qui lui sont associés, appelés "articles de mutation" dans le <i>Recueil de 1811</i>. ;
- les états des parcelles détenues par ce(s) propriétaire(s), appelés "articles de classement" dans le <i>Recueil de 1811</i>.

Un compte foncier est associé à un numéro (plus rarement à plusieurs, généralement quand plusieurs pages sont nécessaires pour lister l'ensemble des parcelles appartenant aux propriétaires mentionnés). Selon le type de matrice cadastrale traité, ce numéro peut faire référence à un ou à plusieurs comptes fonciers différents. 

Pour chaque état de parcelle, il est possible d'indiquer le compte foncier où il se trouvait précédement ("Tiré de") et dans quel compte foncier se trouve il est porté après une modification de cet état ("Porté à"). Les évènements qui concernent les propriétés (principalement bâties) sont également indiqués dans ces colonnes : "Nouvelle construction" (C.N/N.C), "Augmentation" (Aug), "Evaluation du bâti" (E.B.), "Destruction", "Ruine".
Ces passages d'un compte foncier à un autre sont des informations particulièrement utile pour ordonner les états d'une même parcelle dans l'ordre chronologique.

Les lignes obsolètes d'un compte foncier sont rayées. 
Un compte foncier entièrement barré est clôt. 

- Un **compte foncier** est caractérisé par:
    - *{obligatoire}* son **numéro de folio/article/case**
    - *{obligatoire}* la **matrice cadastrale** dans laquelle il se trouve
    - *{obligatoire}* le ou les **propriétaires** qu'il mentionne
    - *{obligatoire}* la **liste des états de parcelles** qu'il mentionne
    - *{optionnel}* le **numéro du folio où se poursuit le compte foncier** (ex: en cas de manque de place dans la page)
    - *{optionnel}* le **numéro du folio précédent le folio actuel** (ex: en cas de manque de place dans la page)
    - *{optionnel}* le **numéro de folio/article/case dans la matrice précédente**

## Exemples

### Exemple 1
> Article 42, Matrice de rôles (1810-1822), Marolles-en-Brie
- **Numéro** : 42
- **Propriétaire** : Lhuillier Veuve Vigneronne à Marolles (1812-1822)
- **Liste des parcelles mentionnées** :
    - A-44 (1812-1822)
    - D-115 (1812-1822)
    - D-118 (1812-1822)
- **Matrice** : Matrice de rôles de Marolles-en-Brie (1810-1822)

### Exemple 2
> Folio 602/1040, Matrice des propriétés foncières/non bâties (1822-1914), Champigny-sur-Marne (<a href="comptes_fonciers\img\folio_champigny_FRAD094_3P_000108_01_0004.PNG">Voir l'image</a>)
- **Numéro** : 602 <i>ET</i> 1040
- **Propriétaire**:
    - Macreau Laurent à Chennevière
    - Bessault Louis à Champigny, rue du Bousquet
    - Coutable Eugène 141 Grande Rue à Champigny 1906
- **Liste des parcelles mentionnées** :
    - C-1474 (1822-1861)
    - F-758p (1893-1847)
    - C-1028 (1906-1914)
- **Matrice** : Matrice des propriétés foncières/non bâties (1822-1914), Champigny-sur-Marne 

### Exemple 3
> Case , Matrice des propriétés non bâties (1914-rénovation), Champigny-sur-Marne 
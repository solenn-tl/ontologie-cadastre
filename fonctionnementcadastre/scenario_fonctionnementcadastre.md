# Scénario de motivation Documentation cadastrale

## Nom

Documentation cadastrale : fonctionnement des registres

## Description

### Documents

Le cadastre napoléonien est composé d'un ensemble documentaire créé et complété selon des règles définies. Ce modelet s'attache à décrire la documentation cadastrale non pas en tant que source d'archives mais en tant qu'objet administratif fonctionnel. Les modelets **Sources** et **Documentation cadastrale** sont intrinsèquement liés.

Les registres qui composent la documentation cadastrale sont les états de sections et les matrices.

Les **états de sections** sont composés de chapitres. Chaque chapitre débute par une page de couverture qui décrit la section décrite (nom, identifiant) et d'un tableau ou chaque ligne est l'état initial de la parcelle à la création du cadastre. Avant 1822, il existe également des chapitres dédiés à l'imposition des propriétés bâties.

Les **matrices cadastrales** contiennent un ensemble de tableaux dont la structure varie au cours du temps. Appelés, "article", "**folio**" ou "case", ils associent un numéro d'identifiant à un ou plusieurs ensembles composés d'une liste de propriétaires et des états de parcelles qui lui sont associé. 

Si pour un numéro de folio, on trouve plusieurs ensembles 'propriétaires sucessifs/liste d'états de parcelles', chaque ensemble sera appelé **sous-folio**.

Dans les documents cadastraux, chaque folio/sous-folio est scindé en deux parties :
- la liste des propriétaires successifs qui lui sont associés, appelé "**article de mutation**" dans le <i>Recueil de 1811</i>. ;
- les états des parcelles détenues par ce(s) propriétaire(s), appelés "**articles de classement**" dans le <i>Recueil de 1811</i>.

Un **compte foncier** est ainsi la liste des parcelles appartenant à un propriétaire donné pour une période donnée.
Le compte foncier d'un propriétaire peut être décrit dans un ou plusieurs folios, consécutifs ou non, dans une ou plusieurs matrices.

### Fonctionnement détaillé

Dans chaque état de parcelle, il est indiqué le compte foncier dans lequel la parcelle se trouvait avant sa dernière modification ("Tiré de") et dans quel compte foncier elle est ajoutée après la modification suivante ("Porté à"). 
Des évènements qui concernent les propriétés (principalement bâties) sont également indiqués dans ces colonnes : "Nouvelle construction" (C.N/N.C), "Augmentation" (Aug), "Evaluation du bâti" (E.B.), "Destruction", "Ruine".
Les passages d'un compte foncier à un autre sont des informations particulièrement utiles pour ordonner les différents états d'une même parcelle dans l'ordre chronologique.

Les lignes obsolètes d'un compte foncier sont rayées. 
Un compte foncier entièrement barré est clôt. 

### Classes
*Les documents de type 'Registre' (matrices et états de sections) sont instanciés sous la forme de RecordSet décrits dans le modelet Sources. Les folios, articles de mutations et de classement sont des objets de type RecordPart.* 

- Un **folio** est caractérisé par:
    - *{obligatoire}* son **numéro de folio/article/case**
    - *{optionnel}* un ou plusieurs **numéro de folio/article/case alternatifs** (souvent rayés)
    - *{obligatoire}* la **page de matrice dans laquel il se trouve**
    - *{obligatoire}* l'**article de mutation qu'il contient**
    - *{obligatoire}* les **articles de classement qu'il contient**
    - *{optionnel}* un ou plusieurs **commentaires** (ex : *suite du compte foncier au folio XX*, *en-être de page* etc.)
    - *{optionnel}* le **numéro de folio/article/case dans la matrice précédente**
    - *{optionnel}* le **numéro de folio/article/case dans la matrice suivante**
    - *{optionnel, si matrice des propriétés bâties}* le **numéro de folio associé dans la matrice des propriétés non bâties**
    - *{optionnel, si matrice des propriétés non bâties}* le **numéro de folio associé dans la matrice des propriétés bâties**

- Un **sous-folio** hérite des propriétés du folio ainsi que:
    - {obligatoire}* le/les **folios** dans lequel il se trouve

- Un **article de mutation** est caractérisé par:
    - *{obligatoire}* le/les **folios** dans lequel il se trouve
    - *{obligatoire}* le/les **propriétaires** qu'il mentionne
    - *{optionnel}* la/les **dates de mutations de propriétaires** qu'il mentionne

- Un **article de classement** décrit une parcelle pour une période donnée. Il est caractérisé par:
    - *{obligatoire}* le/les **folios** dans lequel il se trouve
    - *{obligatoire}* l'**identifiant de la parcelle** décrite (section,parcelle)
    - *{obligatoire}* la **nature de la parcelle** décrite (section,parcelle)
    - *{obligatoire}* le renvoi vers le folio où se trouve l'**article de classement précédent** de la parcelle ("Tiré de"). Il peut aussi être indiqué une valeur spéciale décrivent l'état précédent de la parcelle.
    - *{obligatoire}* le renvoi vers le folio où se trouve l'**article de classement suivant** de la parcelle ("Porté à"). Il peut aussi être indiqué une valeur spéciale décrivent l'état suivant de la parcelle.
    - *{optionnel}* la **date de début de validité de l'article de classement** ('Date d'entrée')
    - *{optionnel}* la **date de fin de validité de l'article de classement** ('Date de sortie')

- Un **compte foncier** est caractérisé par:
    - *{obligatoire}* son **propriétaire**
    - *{obligatoire}* la **liste des parcelles** du propriétaire concerné (différentes versions)

## Exemples

### Exemple 1 [Article (folio)]
> Article 42, Matrice de rôles (1810-1822), Marolles-en-Brie
- **Numéro** : 42
- **Propriétaire** : Lhuillier Veuve Vigneronne à Marolles (1812-1822)
- **Liste des parcelles mentionnées** :
    - A-44 (1812-1822)
    - D-115 (1812-1822)
    - D-118 (1812-1822)
- **Matrice** : Matrice de rôles de Marolles-en-Brie (1810-1822)

### Exemple 2 [Folio]
> Folio 602/1040, Matrice des propriétés foncières/non bâties (1822-1914), Champigny-sur-Marne (<a href="https://github.com/solenn-tl/ontologie-cadastre/blob/main/comptes_fonciers/img/folio_champigny_FRAD094_3P_000108_01_0004.PNG">Voir l'image</a>)
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
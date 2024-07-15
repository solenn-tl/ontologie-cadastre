# Scénario de motivation Documentation cadastrale

## Nom

Documentation cadastrale : fonctionnement des registres

## Description

### Documents

Le cadastre napoléonien est composé d'un ensemble documentaire créé et complété selon des règles définies. Ce modelet s'attache à décrire la documentation cadastrale non pas en tant que source mais en tant qu'objet administratif dont le fonctionnement peut s'apparenter à celui d'une base de données manuscrite. Les modelets **Sources** et **Documentation cadastrale** sont intrinsèquement liés.

Les registres qui composent la documentation cadastrale sont les états de sections et les matrices.

Les **états de sections** sont composés de chapitres. Chaque chapitre débute par une page de couverture qui décrit la section considérée (nom, identifiant) et d'un tableau où chaque ligne correspond à l'état initial d'une la parcelle à la création du cadastre. Avant 1822, il existe également des chapitres dédiés à l'imposition des propriétés bâties.
Pour assembler les données contenues dans les états de sections: 
- il faut tenir compte de l'ordre des pages "Couvertures" puis "Tableau" afin de construire l'identifiant des parcelles.
- le tableau peut contenir une colonne qui indique l'identifiant d'un porpriétaire dans la matrice (à utiliser comme un champ de jointure)
- dans la majorité des cas, c'est le nom du propriétaire dans l'état de sections qui permet de retrouver son folio dans la matrice.

Les **matrices cadastrales** contiennent un ensemble de tableaux dont la structure varie au cours du temps. Appelés, "article", "**folio**" ou "case", les pages de tableaux principaux associent un numéro d'identifiant à un ou plusieurs ensembles composés d'une liste de propriétaires et des états de parcelles qui lui sont associé. 

Si pour un numéro de folio, on trouve plusieurs ensembles 'propriétaires sucessifs/liste d'états de parcelles', chaque ensemble sera appelé **compte foncier**.

D'après le Recueil de 1810, chaque folio est scindé en deux parties :
- la liste des propriétaires successifs qui lui sont associés, appelé "**article de mutation**" dans le <i>Recueil de 1811</i> :
- les états des parcelles détenues par ce(s) propriétaire(s), appelés "**articles de classement**" dans le <i>Recueil de 1811</i> :

Un **compte foncier** est ainsi la liste des parcelles appartenant à un propriétaire donné pour une période donnée.
Le compte foncier d'un propriétaire peut être décrit dans un ou plusieurs folios, consécutifs ou non, dans une ou plusieurs matrices.

### Fonctionnement détaillé

Dans chaque état de parcelle, il est indiqué le folio dans lequel la parcelle se trouvait avant sa dernière modification ("Tiré de") et dans quel folio elle est ajoutée après la modification suivante ("Porté à"). 
Des évènements qui concernent les propriétés (principalement bâties) sont également indiqués dans ces colonnes : "Nouvelle construction" (C.N/N.C), "Augmentation" (Aug), "Evaluation du bâti" (E.B.), "Destruction", "Ruine".
Les passages d'un folio à un autre sont des informations particulièrement utiles pour ordonner les différents états d'une même parcelle dans l'ordre chronologique ou déduire des fusions/divisions.

Les lignes obsolètes d'un compte foncier sont rayées. 
Un compte foncier entièrement barré est clôt. 

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
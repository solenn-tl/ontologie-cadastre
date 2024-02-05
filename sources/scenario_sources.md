# Scénario de motivation du modelet Sources

## Nom

Sources

## Description

Le modelet Sources a pour objectif de faire le lien entre les informations décrites dans le graphe de connaissances et les sources dont elles sont extraites. 

Une source peut prendre différentes formes : 
* concept : contenu de la source considéré indépendement de sa forme concrète;
* physique : exemplaire précis d'un concept, généralement caractérisé par une référence et une localisation ;
* numérisée : scan d'un exemplaire
* autres formes dérivées faisant suite à un traitement automatique ou manuel (ex: plan géoréférencé).

Il peut exister plusieurs instances (physique, numérisée, dérivée) d'un même concept.

Une source peut être scindée en plusieurs parties (ex : une matrice comprend la liste alphabétique des propriétaires, les augmentations/diminutions et les folios).

Quatre principaux documents composent le cadastre napoléonien :
* les plans parcellaires (plan)
* le tableau d'assemblage (plan)
* l'état de sections (registre)
* la matrice des propriétaires (registre)

Une **source** peut être décrite par les propriétés suivantes :
* {*obligatoire*} son **titre ou intitulé**;
* {*obligatoire*} son **type** (plan parcellaire, plan d'assemblage, etat de section, matrice...)
* {*optionnel*} son **précision de son type** (ex: plan issu d'atlas, plan minute, plan révisé)
* {*optionnel*} son **auteur**
* {*optionnel*} sa **date de création**
* {*optionnel*} sa **date de début de validité**
* {*optionnel*} sa **date de fin de validité**
* {*optionnel*} sa **description**
* {physique, numérisée:*obligatoire*} sa **cote d'archive**
* {physique: *optionnel*} sa **localisation**
* {physique: *optionnel*} ses **dimensions** 
* {numérisée: *optionnel*} sa **résolution**
* {numérisée: *optionnel*} son **URL IIIF**
* {numérisée,dérivée:*obligatoire*} sa **licence de diffusion**
* {dérivée: *obligatoire*} son **processus de création** 
(géoréférencement, vectorisation, transcription)
* {dérivée: *optionnel*} son **DOI**

Les **relations entre les différentes formes de sources** peuvent être décrites ainsi:
* il existe toujours au moins un concept de source qui donne lieu à une source physique;
* dans le cas des sources historiques, un concept possède au moins une instance physique ;
* une instance physique peut être numérisée (mais pas forcément) ;
* les sources physiques et numérisées peuvent faire l'objet d'instanciations dérivées (transcription, géoréférencement).

Une source est généralement associée à une version d'un attribut (ex: nom du propriétaire, nature de la parcelle) ou à un évènement 

## Exemples

### Exemple 1
Exemple de description de l'état de sections primitifs de Marolles en Brie dans ses différentes instanciations

#### [Concept de source]

* **Intitulé** : Etat de sections de Marolles-en-Brie
* **Type** : état de sections 
* **Date de création** : 1810
* **Précision du type** : registre primitif produit avant 1822

#### [Source physique]

* **Intitulé** : Etat de sections de Marolles-en-Brie
* **Type** : état de sections 
* **Date de création** : 1810
* **Précision du type** : registre primitif produit avant 1822
* **Cote d'archive** : 3 P 387
* **Localisation** : Archives départementales du Val-de-Marne

#### [Source numérisée]

* **Intitulé** : Etat de sections numérisé de Marolles-en-Brie
* **Type** : état de sections 
* **Précision du type** : registre primitif produit avant 1822
* **Date de création** : 1810
* **Cote d'archive** : FRAD094_3P_000387_01
* **Licence** : Etalab

#### [Source dérivée]

* **Intitulé** : Dataset contenant la transcription de l'état de sections Marolles en Brie
* **Type** : transcription structurée
* **Date de création** : novembre et décembre 2023
* **Processus de création** : annotation manuelle avec Callico

### Exemple 2

Exemple de description du plan parcellaire de la section C de Marolles en Brie dans ses différentes instanciations

#### [Concept de source]

* **Intitulé** : Plan parcellaire de la Section C "dite du Village" Marolles-en-Brie
* **Type** : plan parcellaire
* **Date de création** : 1810

#### [Source physique]

* **Intitulé** : Plan parcellaire de la Section C "dite du Village" Marolles-en-Brie
* **Type** : plan parcellaire
* **Précision du type** : plan extrait d'un atlas
* **Date de création** : 1810
* **Cote d'archive** : 3 P 1197
* **Localisation** : Archives départementales du Val-de-Marne

#### [Source numérisée]

* **Intitulé** : Plan parcellaire numérisé de la Section C "dite du Village" Marolles-en-Brie
* **Type** : plan parcellaire
* **Précision du type** : plan extrait d'un atlas
* **Date de création** : 1810
* **Cote d'archive** : FRAD094_3P_001197_01
* **Licence** : Etalab

#### [Source dérivée]

* **Intitulé** : Plan parcellaire vectorisé de la section C de Marolles en Brie
* **Type** : plan vectorisé
* **Date de création** : mai 2023
* **Processus de création** : annotation manuelle avec QGIS

## Mémo
<table>
  <tr>
    <th>Document</th>
    <th>Informations fournies</th>
    <th>Traitements associés</th>
  </tr>
  <tr>
    <td>Plan parcellaire</td>
    <td><ul>
            <li>Localisation des parcelles dans les sections</li>
            <li>Forme des parcelles (géométrie)</li>
            <li>Association parcelle/numéro</li>
            <li>Toponymie</li>
            <li>Métadonnées (échelle du plan, nom du géomètre...)</li>
        </ul>
    </td>
    <td>Géoréférencement, Vectorisation, Détection et reconnaissance de texte</td>
  </tr>
  <tr>
    <td>Tableau d'assemblage</td>
    <td>
    <ul><li>Position relative des zones représentées dans les plans parcellaires au sein de la commune</li>
    <li>Toponymie</li>
    </ul></td>
    <td>   Géoréférencement, Vectorisation, Détection et reconnaissance de texte</td>
  </tr>
  <tr>
    <td>Etat de section</td>
    <td>Etat des parcelles à T0</td>
    <td>Classification des pages<br>DAN</td>
  </tr>
  <tr>
    <td>Matrice des mutations</td>
    <td>Etats sucessifs des parcelles au cours de la période de validité du cadastre.</td>
    <td>Classification des pages<br>DAN</td>
  </tr>
</table>
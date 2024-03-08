# Scénario de motivation du modelet Sources

## Nom

Sources

## Description

Le modelet Sources a pour objectif de faire le lien entre les informations décrites dans le graphe de connaissances et les sources dont elles sont extraites. 

Une source historique peut prendre différentes formes : 
* concept : contenu de la source considéré indépendement de sa forme concrète;
* physique : exemplaire physique d'un concept, généralement caractérisé par un identifiant et une localisation ;
* numérisée : version numérisé d'un exemplaire
* autres formes dérivées faisant suite à un traitement automatique ou manuel (ex: plan géoréférencé, page transcrite).

Une source peut être scindée en plusieurs parties (ex : une matrice comprend la liste alphabétique des propriétaires, les augmentations/diminutions et les folios), elle peut comprendre plusieurs éléments. Ces éléments peuvent eux-mêmes être comprendre plusieurs zones

Une **source** peut être décrite par les propriétés suivantes :
* {*obligatoire*} son **titre ou intitulé**;
* {*obligatoire*} son **type** (ex: plan parcellaire, plan d'assemblage, état de section, matrice, référentiel géographique...)
* {*optionnel*} son **précision de son type** (ex: plan issu d'atlas, plan minute, plan révisé)
* {*optionnel*} son **auteur** (personne physique ou morale)
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
(ex: géoréférencement, vectorisation, transcription)
* {dérivée: *optionnel*} son **DOI**

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
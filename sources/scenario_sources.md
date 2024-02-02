# Scénario de motivation du modelet Sources

## Nom

Sources

## Description

Le modelet Sources a pour objectif de faire le lien entre les informations décrites dans le graphe de connaissances et les sources dont elles sont extraites. 

Une source peut prendre différentes formes : 
* concept : contenu de la source considéré indépendement de sa forme concrète;
* matérielle : exemplaire précis d'un concept, généralement caractérisé par une référence et une localisation ;
* numérisée : scan d'un exemplaire
* autres formes dérivées faisant suite à un traitement automatique ou manuel (ex: plan géoréférencé).

Il peut exister plusieurs instances (physique, scannée, dérivée) d'un même concept.

Une source peut être scindée en plusieurs parties (ex : une matrice comprend la liste alphabétique des propriétaires, les augmentations/diminutions et les folios).

Quatre principaux documents composent le cadastre napoléonien :
* les plans parcellaires (plan)
* le tableau d'assemblage (plan)
* l'état de sections (registre)
* la matrice des propriétaires (registre)

Une **source** peut être décrite par les propriétés suivantes :
* {*obligatoire*} son **type** (plan parcellaire, plan d'assemblage, etat de section, matrice...)
* {*optionnel*} son **précision de son type** (type d'état de section, de matrice, de plan)
* {concept, physique : *obligatoire*} sa **date de début de validité**
* {concept, physique : *optionnel*} sa **date de fin de validité**
* {concept, physique, numérisée:*obligatoire*} sa **cote d'archive**
* {physique: *optionnel*} sa **localisation**
* {physique: *optionnel*} ses **dimensions** 
* {numérisée: *optionnel*} sa **résolution**
* {numérisée: *optionnel*} son **URL IIIF**
* {numérisée,dérivée:*obligatoire*} sa **licence de diffusion**
* {dérivée: *obligatoire*} son **processus de création** (géoréférencement, vectorisation, transcription)

## Exemples

### Exemple 1 [Concept de source]

Etat de sections de Marolles-en-Brie

### Exemple 2 [Source imprimée]

Etat de sections de Marolles-en-Brie
Cote d'archive 3 P 387

### Exemple 3 [Source numérisée]

Dossier FRAD094_3P_000387_01 contenant 127 vues numérisées issues de l'état de sections de Marolles en Brie.

### Exemple 4 [Extraction]

Dataset contenant la transcriptions de l'état de sections Marolles en Brie

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
    <td>Position relative des zones représentées dans les plans parcellaires au sein de la commune</td>
    <td></td>
  </tr>
  <tr>
    <td>Etat de section</td>
    <td>Etat des parcelles à T0</td>
    <td>DAN</td>
  </tr>
  <tr>
    <td>Matrice des mutations</td>
    <td>Etats sucessifs des parcelles au cours de la période de validité du cadastre.</td>
    <td>DAN</td>
  </tr>
</table>
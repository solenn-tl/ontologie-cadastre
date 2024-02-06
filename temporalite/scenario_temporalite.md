# Scénario de motivation Temporalité

## Nom

Evolution temporelle des parcelles

## Description

L'objectif de la thèse est de pouvoir suivre l'évolution des parcelles au cours du temps, de la création du cadastre (entre 1808 et 1850) à sa rénovation (entre 1930 et 1975). 

L'**identité d'une parcelle est fixée par son numéro**. Tant que le numéro ne change pas, son identité reste la même.

Une parcelle est caractérisée par plurieurs propriétés : 
* un ou plusieurs propriétaires
* une nature de sol
* une géométrie
* une localisation (section, commune...)
Ces propriétés peuvent changer au cours du temps. Un changement d'une des propriétés n'implique pas nécessairement un changement des autres propriétés. 

De ce fait : 
* la parcellaire possède une période d'existance (de sa création à sa disparition);
* chacune de ses propriétés possède des versions qui elles-mêmes ont une période de validité, **d'un état de classement au suivant**.

Un état de classement (= une ligne de l'état de sections ou de la matrice des propriétaire) caractérise donc un **état** de la parcelle.

On distingue deux types d'évènements : les évènements liés directement à l'identité de la parcelle et les évènements liés à ses propriétés.

Les **évènements qui affectent l'identité** de la parcelle sont les suivants:
* apparition
* disparition
* fusion de parcelles (sans persistance du numéro)
* division de parcelle (sans persistance du numéro)
* re-numérotation
Ils interviennent généralement en même temps que des changements majeurs de la documentation cadastrale (nouvelle cadastration). 
A la suite de ces évènements, il est possible d'**établir des liens de parentés entre les parcelles** qui recouvrent une même zone.

Les évènements qui n'affectent pas l'identité de la parcelle sont généralement caractérisés par le ou les changements détectés entre une ou plusieurs attributs de deux états sucessifs :
* un chagement de **nature**
* un changement de **propriétaire(s)**
* un changement de **géométrie**
    * division de parcelle (avec persistance du numéro)
    * fusion de parcelles (avec persistance du numéro)
* un changement de **localisation** (échange de sections entre communes, changement d'intitulé de lieu-dit)

La granularité temporelle dans le cadastre napoléonien est de l'ordre de l'année. Les durées d'existence des parcelles et de validité de leurs valeurs d'attributs sont donc relativement floues.

Deux états peuvent être associés à une même date voir à une même période de validité (ex:**de 1856 à 1856**). En cas d'incomplétude des informations extraites, il peut être complexe de les replacer dans le bon ordre chronologique. 
Il est de ce fait important de connaître l'ordre d'apparition des états dans la documentation cadastrale pour reconstituter l'historique de la parcelle dans le bon ordre chronologique.

La reconstitution de l'ordre des états dans la documentation cadastrale s'appuie donc sur leur position dans un compte foncier et dans les reports effecués d'un compte foncier à un autre.

Certaines évènements liés à l'évolution de la documentation cadastrale (à l'échelle nationale ou départementale) sont connus. 
Il peut s'agir de nouvelle cadastration ou de lois faisant évoluer le cadastre. Dans le cas des lois qui impliquent des évolutions de documentation, nous ne connaissons généralement que la date de publication de la loi, pas celle de son application dans chaque commune de chaque département.

## Caractéristiques des entités temporelles
Cf [Ontologie des addresses](https://github.com/charlybernard/phd-ontologie/blob/main/temps_argumentaire.md)

## Exemples

### Exemple 1 : Instant

Les états de sections fournissent l'état initial de la parcelle (dans une version du cadastre donnée). La date associée à cet état est l'année de production de cet état de section. Elle peut être indiquée/récupérée de plusieurs façons (dans la):
* extraction depuis la source numérisée
* indiquée dans les métadonnées du dossier d'images numérisée

Année de production de l'état de sections de Marolles en Brie : *1810*


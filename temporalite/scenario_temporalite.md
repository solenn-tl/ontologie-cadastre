# Scénario de motivation Temporalité

## Nom

Evolution des parcelles

## Description

L'objectif de la thèse est de pouvoir suivre l'évolution des parcelles au cours du temps, de la création du cadastre (entre 1808 et 1850) à sa rénovation (entre 1930 et 1975). 

Une parcelle est caractérisée par plusieurs propriétés (à une date donnée): 
* un **propriétaire** (ou groupe de propriétaires)
* une ou plusieurs **natures** de sol (ex: bâtiment et cour)
* une **géométrie**
* une **localisation** (section, commune)
* une **précision de la localisation** (lieu-dit)

Ces propriétés peuvent changer au cours du temps. Un évènement intervenant sur une parcelle peut concerner une ou plusieurs propriétés.

De ce fait, la parcelle possède une période d'existance (de sa création à sa disparition) et chacune de ses propriétés possède des versions qui elles-mêmes ont une période de validité.

On distingue deux types d'évènements : les évènements liés directement à l'identité de la parcelle et les évènements liés à ses propriétés.

### Evènements qui affectent les propriétés de la parcelle sans changer son identité

Une version d'un attribut correspond à une période de stabilité de sa valeur. Cet état stable peut être attesté par un ou plusieurs états de classement sucessifs extrait des documents (ligne d'état de classement dans les matrices). La compilation des états qui attestent de cette stabilité permet d'en déduire les dates de la période de validité.

Les changements liés aux propriétés sont :
* un chagement de **nature**
* un changement de **propriétaire(s)**
* un changement de **géométrie**
    * division de parcelle (avec persistance du numéro)
    * fusion de parcelles (avec persistance du numéro)
* un changement de **localisation** (échange de sections entre communes) <span style="color:red">A discuter (changement d'ientité ?)</span>

### Evènements qui affectent l'identité de la parcelle

<span style="color:red">Identité d'une parcelle ???</span>
Identité d'une parcelle : même numéro/section/commune ???

Les **évènements qui affectent l'identité** de la parcelle sont les suivants:
* apparition
* disparition
* fusion de parcelles (sans persistance du numéro)
* division de parcelle (sans persistance du numéro)
* re-numérotation

Ils interviennent généralement en même temps que des changements majeurs de la documentation cadastrale (nouvelle cadastration ou création d'une nouvelle commune). 
A la suite de ces évènements, il est possible d'**établir des liens de parentés entre les parcelles** qui recouvrent une même surface.

### Temporalité

La précision temporelle dans le cadastre napoléonien est de l'ordre de l'année.

Les bornes de l'intervalle de validité d'une propriété peuvent être :
* deux années (ex : <i>1810-1850</i>,<i>1856-1856</i>)
* une année et une intervalle (ex : <i>1810-entre 1832 et 1882</i>,<i>entre 1832 et 1882-1914</i>)

## Exemples

### Exemple 1 : Initialisation d'une parcelle

#### Contexte
Les états de sections fournissent l'état initial de la parcelle (dans une version du cadastre donnée). La date associée à cet état est l'année de production de cet état de section. Elle peut être indiquée/récupérée de plusieurs façons :
* extraction depuis la source numérisée
* **indiquée dans les métadonnées de la côte d'archive**

#### Exemple
>Année de production de l'état de sections de Marolles en Brie : *1810*
* Date d'apparition de chaque parcelle : 1810
* Borne de début de l'intervalle de validité de l'ensemble des propriétés : 1810

### Exemple 2 : Validité d'une propriété

#### Contexte
L'intervalle de validité d'une propriété est déduite à l'aide des dates des N états sucessifs de la parcelle pour lesquels la propriété conserve la même valeur ainsi qu'à partir de la date d'entrée de l'état N+x pour lequel la valeur de la propriété change.

Ces états sont principalements décrits dans les matrices cadastrales. 

#### Exemple
>Parcelle 191, Section C, Marolles-en-Brie

*1. Sucession d'états*
<table>
    <tr><th>Source <i>(+ num extraction)</i></th>
        <th>Compte foncier</th>
        <th>Propriétaire</th>
        <th>Nature</th>
        <th>Tiré de</th>
        <th>Date d'entrée</th>
        <th>Porté à</th>
        <th>Date de sortie</th>
    </tr>
    <tr>
        <td>Etat de section</td>
        <td></td>
        <td>Mazarot Pierre cabaretier à id</td>
        <td>Jardin</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>Matrice de rôle</td>
        <td>43</td>
        <td>Mazarot Pierre cabaretier,
            D’Auvergne de Noiseau et
            Jn Bt Fleury
        </td>
        <td>Jardin</td>
        <td></td>
        <td></td>
        <td>94</td>
        <td></td>
    </tr>
    <tr>
        <td>Matrice de rôle</td>
        <td>94</td>
        <td>Mazarot Pierre cabaretier à id</td>
        <td>Jardin</td>
        <td>43</td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>Matrice des propriétés foncières</td>
        <td>57</td>
        <td>Mazarot Pierre cabaretier à Marolles</td>
        <td>Jardin</td>
        <td></td>
        <td></td>
        <td>45</td>
        <td>1832</td>
    </tr>
    <tr>
        <td>Matrice des propriétés foncières</td>
        <td>45</td>
        <td>Guillot Pierre Louis Victor ainé à</td>
        <td>Jardin</td>
        <td></td>
        <td></td>
        <td>45</td>
        <td>1832</td>
    </tr>
</table>


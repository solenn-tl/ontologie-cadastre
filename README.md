# Ontologie Cadastre Napoléonien

Cette ontologie a pour objectif de décrire les informations et documents qui constituent le cadastre napoléonien, premier cadastre produit à l'échelle de l'ensemble des départements français.

Elle comporte cinq modelets:
- entités géographiques
- propriétaires
- comptes fonciers
- sources
- temporalité

## Vocabulaires et ontologies existants

### Entités géographiques
* [HHT : Hierarchical Historical Territories](https://www.irit.fr/recherches/MELODI/ontologies/HHT/index-en.html)
* [Adresses](https://github.com/charlybernard/phd-ontologie)
* [data.ign.fr](http://data.ign.fr/data.html)

### Sources
* [RiC-CM](https://www.ica.org/fr/records-in-contexts-modele-conceptuel), modèle utilisé dans les services d'Archives
* [FPO (Factoid Prosopography)](https://www.kcl.ac.uk/factoid-prosopography/fpo-sources)
<img src="https://www.kcl.ac.uk/newimages/ah/factiod/fpo-sources.png"/>

* [PROV-O: The PROV Ontology](https://www.w3.org/TR/prov-o/)
* IFLA LRM : utilisé dans les bibliothèques
* CIDOC-CRM : utilisé dans les musées

### Temporalité
* [Adresses, modelet Temporalité](https://github.com/charlybernard/phd-ontologie)

## TO DO
- Intégrer à l'ontologie ```ontologie.ttl```
    - [X] le modelet Entités Géographiques 
    - [X] le modelet Temps à l'ontologie
    - [X] le modelet Propriétaires à l'ontologie
    - [ ] le modelet Sources à l'ontologie
    - [X] le modelet Comptes fonciers à l'ontologie
- [ ] Ecrire exemple complet => *quasi finalisé, reste à finir les sources*
- Ecrire les requêtes SPARQL + vérifier questions de compétences
    - [X] Modelet Entités Géographiques
    - [ ] Modelet Temps => *en cours*
    - [X] Modelet Propriétaires
    - [ ] Modelet Sources
    - [ ] Modelet Comptes fonciers
- Initialisation du KG avec les données annotées pour les états de sections
    - [ ] Code python
    - [ ] Test
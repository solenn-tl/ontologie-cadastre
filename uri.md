# URIs

## Ontologie PegazuS
### Adresses
```
http://rdf.geohistoricaldata.org/def/address#
```
### Cadastre
```
http://data.ign.fr/def/cadastre#
```

## KG final
### URI Parcelle
L'identité d'une parcelle change :
- s'il y a subdivision d'une parcelle AVEC une mutation de propriétaire ;
- s'il y a une fusion de parcelles ;
- s'il y a un changement d'identifiant (numéro/section/commune).

L'URI d'une parcelle est :
```
http://data.ign.fr/id/plot/{NUMDEPT}_{NOM_COMM}_{DATE_PLAN}_{LETTRE_SECTION}_{ID_PARCELLE}_{ID_SUB_PARCELLE}
```
avec 
- NUMDEPT : numéro du département actuel
- NOM_COMM : nom de la commune (de l'époque)
- DATE_PLAN : date du plan ou de la version de cadastre dans laquelle la parcelle existe avec cette identité
- LETTRE_SECTION : lettre identifiant la section
- ID_PARCELLE : identifiant de la parcelle
- ID_SUB_PARCELLE : identifiant d'une subdivision de la parcelle

Remarque : créer des URI pour les entités gégraphiques administratives et cadastrales ?

### URI Propriétaire
L'identité d'un propriétaire est définie par son nom de famille (personne physique) ou sa raison sociale (personne morale) ainsi que par ses différentes propriétés. 
En cas d'ambiguité entre deux mentions de propriétaires similaire, il est préférable de créer deux propriétaires et d'établir un lien de potentielle équivalence entre eux.
```
http://data.ign.fr/id/owner/{UUID}
```

### URI Compte foncier
A créer ou pas ?
```
http://data.ign.fr/id/propertyaccount/{REGISTRE_ID}_{NUM_FOLIO}_{opt:NUM_SOUS_PARTIE_PAGE_uuid}
```

## Triplets intermédiaires
### URI Parcelle
```
http://data.ign.fr/id/plot/{NUMDEPT}_{NOM_COMM}_{DATE_PLAN}_{LETTRE_SECTION}_{ID_PARCELLE}_{ID_SUB_PARCELLE}_{UUID}
```
- UUID : identifier chaque état indépendament
Remarque : la suppression de l'UUID final permet d'accéder à l'URI de la parcelle

### URI Propriétaire
```
http://data.ign.fr/id/owner/{UUID}
```
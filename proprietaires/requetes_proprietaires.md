## Requêtes SPARQL du modelet Propriétaires
*A jour le 20 mars 2024*

## Liste des propriétaires dans l'ordre alphabétique
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
select * where { 
	?owner a nap:Owner;
        rdfs:label ?name
}
ORDER BY ?name
```

## Liste des propriétaires dont le nom commence par ...
>Exemple : Liste des propriétaires dont le nom commence par G
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
select * where { 
	?owner a nap:Owner;
        rdfs:label ?name
       FILTER(regex(lcase(?owner),'^g'))
}
```

## Liste des propriétaires d'une parcelle
>Liste des propriétaires de la parcelle C-191 à Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
select distinct ?owner ?ownername ?owneraddress ?owneractivity where { 
	?parcel a nap:Landmark ;
         nap:isLandmarkType ltype:Parcel;
         nap:hasAttribute [a nap:Attribute;
         nap:isAttributeType atype:ParcelOwner;
         	nap:hasAttributeVersion[ a nap:AttributeVersion;
                                  nap:hasOwner ?owner]
].
    ?owner rdfs:label ?ownername.
    OPTIONAL{?owner nap:address ?owneraddress}
    OPTIONAL{?owner nap:activity ?owneractivity}
    FILTER(?parcel = landmark:PARC_Marolles_en_Brie_C_191_1810)
}
ORDERBY ?ownername
```
## Liste des parcelles appartenant à un propriétaire
>Liste des parcelles de Pierre Mazarot
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>
select distinct ?parcelname where { 
	?owner a nap:Owner ;
        nap:isOwnerOf ?parcelversion.
    ?parcelversion nap:isAttributeVersionOf ?attribute.
    ?attribute nap:isAttributeOf ?landmark.
    ?landmark rdfs:label ?parcelname.
    FILTER(?owner = owner:0001)
}
```

## Liste des parcelles appartenant à un propriétaire dans une commune donnée
>Liste des parcelles de Pierre Mazarot à Marolles-en-Brie 
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>

select distinct ?parcelname where { 
	?owner a nap:Owner ;
        nap:isOwnerOf ?parcelversion.
    ?parcelversion nap:isAttributeVersionOf ?attribute.
    ?attribute nap:isAttributeOf ?landmark.
    ?landmark rdfs:label ?parcelname;
              nap:hasAttribute [ a nap:Attribute;
              nap:isAttributeType atype:SpatialDescription;
    	      nap:hasAttributeVersion [ a nap:AttributeVersion;
    				nap:firstStep/nap:relatum ?commune
              ]
    ].
    FILTER(?owner = owner:0001)
    FILTER(?commune = landmark:COMM_Marolles_en_Brie)
}
```

## Liste des propriétaires domiciliés à une addresse donnée
>Exemple : liste de propriétaires domicilliés à Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
select ?owner ?name ?address where { 
	?owner a nap:Owner;
        rdfs:label ?name;
        nap:address ?address.
    FILTER(regex(lcase(?address),"marolles"))
}
```

## Liste des propriétaires exerçant une profession donnée
>Exemple : liste de propriétaires exerçant la profession de cabaretier
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
select ?owner ?name ?address where { 
	?owner a nap:Owner;
        rdfs:label ?name;
        nap:activity ?activity.
    FILTER(regex(lcase(?activity),"cabaretier"))
}
```
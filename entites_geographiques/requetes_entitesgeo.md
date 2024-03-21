# Requêtes SPARQL pour le modelet Entités géographiques

Remarque : les requêtes impliquant une dimension temporelle sont décrites dans le modelet Temporalité
*A jour le 21 mars 2024*

## Compter le nombre de parcelles dans une commune
> Nombre de parcelles à Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX dcterms: <http://purl.org/dc/terms/>

PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>

select (count(distinct ?num) as ?num_parcels) where { 
	?parcel a nap:Landmark;
         nap:isLandmarkType ltype:Parcel;
		 dcterms:identifier ?num;
         nap:hasAttribute [ a nap:Attribute;
              nap:isAttributeType atype:SpatialDescription;
    	      nap:hasAttributeVersion [ a nap:AttributeVersion;
    				nap:firstStep/nap:locatum ?commune
              ]
    ].
    FILTER(?commune = landmark:COMM_Marolles_en_Brie)
}
```

## Liste des natures associées à une parcelle
> Natures de sol contenues dans la Parcelle 191, Section C, Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
select distinct ?nature  where { 
	?parcel a nap:Landmark ;
         nap:isLandmarkType ltype:Parcel;
         nap:hasAttribute [a nap:Attribute;
         nap:isAttributeType atype:ParcelNature;
         	nap:hasAttributeVersion[ a nap:AttributeVersion;
                                  nap:hasParcelNature ?nature]
].
    FILTER(?parcel = landmark:PARC_Marolles_en_Brie_C_191_1810)
}
```

## Liste des propriétaires d'une parcelle
> Propriétaires de la parcelle 191, Section C, Marolles-en-Brie
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

## Liste des parcelles d'une certaine nature dans une commune donnée
>Liste des parcelles de Marolles-en-Brie ayant contenu une Maison
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>
select distinct ?parcel  where { 
	?parcel a nap:Landmark ;
         nap:isLandmarkType ltype:Parcel;
         nap:hasAttribute [a nap:Attribute;
         nap:isAttributeType atype:ParcelNature;
         	nap:hasAttributeVersion[ a nap:AttributeVersion;
                                  nap:hasParcelNature ?nature]
			];
         nap:hasAttribute [ a nap:Attribute;
              nap:isAttributeType atype:SpatialDescription;
    	      nap:hasAttributeVersion [ a nap:AttributeVersion;
    				nap:firstStep/nap:locatum ?commune
              ]
    ].
    FILTER(?commune = landmark:COMM_Marolles_en_Brie)
    FILTER(?nature = pnature:Maison)
}
```

## Liste des parcelles situées dans un lieu-dit
>Liste des parcelles de Marolles-en-Brie situées dans le lieu-dit Du Village
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
select ?parcel where { 
	?parcel a nap:Landmark ;
         nap:isLandmarkType ltype:Parcel;
         nap:hasAttribute [ a nap:Attribute;
              nap:isAttributeType atype:SpatialDescription;
    	      nap:hasAttributeVersion [ a nap:AttributeVersion;
    				nap:firstStep/nap:locatum ?commune;
    				nap:firstStep [nap:nextStep+/nap:locatum ?segment]
              ]
    ].
    ?segment a nap:Landmark;
                 nap:isLandmarkType ltype:District;
                 rdfs:label ?name
    FILTER(?commune = landmark:COMM_Marolles_en_Brie)
    FILTER(regex(lcase(?name),'village'))
}
```
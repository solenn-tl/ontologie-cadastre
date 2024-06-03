# Questions de compétences du modelet Temps
*A jour le 21 mars 2024*

## Parcelles d'une nature donnée à une date donnée dans une commune donnée
> Parcelles de nature "Jardin" en 1820 à Marolles-en-Brie ?
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>

SELECT ?parcel ?label
WHERE {
  ?parcel a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  ?parcel rdfs:label ?label.
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:SpatialDescription ;
                             nap:hasAttributeVersion ?versionloc ] .
  ?versionloc nap:firstStep/nap:relatum <http://data.ign.fr/id/cadastrenap/landmark/COMM_Marolles_en_Brie>.
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelNature ;
                             nap:hasAttributeVersion ?version ] .
  ?version nap:hasParcelNature pnature:Jardin.
    
  ?version nap:isMadeBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.
  OPTIONAL{?eventStart rdfs:label ?eventtitle.}
  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.}
    
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}		
  }
    FILTER((?Cstart <= "1820"^^xsd:dateTimeStamp || ?FSstart <= "1820"^^xsd:dateTimeStamp) && (?Cend >= "1820"^^xsd:dateTimeStamp || ?FEend >= "1820"^^xsd:dateTimeStamp))
}
```

## Natures successives d'une parcelle donnée
>Natures sucsessives de la parcelle C-191 à Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>

SELECT ?parcel (group_concat(distinct ?naturelabel; separator=', ') as ?nature) 
  (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?Start)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?End)
WHERE { 
  ?parcel a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelNature ;
                             nap:hasAttributeVersion ?version ] .
  
  ?version nap:hasParcelNature ?nature.
  ?nature skos:prefLabel ?naturelabel.
    
  ?version nap:isMadeBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.

  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.}
    
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}		
  }
  FILTER (lang(?naturelabel) != "en")
} 
GROUP BY ?parcel ?version ?Cstart ?FSstart ?FEstart ?Cend ?FSend ?FEend
```

## Nature d'une parcelle donnée à une certaine date
>Nature de la parcelle C-191 à Marolles-en-Brie en 1820
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>

SELECT ?parcel (group_concat(distinct ?naturelabel; separator=', ') as ?nature) 
  (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?Start)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?End)
WHERE { 
  landmark:PARC_Marolles_en_Brie_C_191_1810 a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelNature ;
                             nap:hasAttributeVersion ?version ] .
  
  ?version nap:hasParcelNature ?nature.
  ?nature skos:prefLabel ?naturelabel.
    
  ?version nap:isMadeBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.

  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.}
    
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}		
  }
  FILTER (lang(?naturelabel) != "en")
  FILTER((?Cstart <= "1820"^^xsd:dateTimeStamp || ?FSstart <= "1820"^^xsd:dateTimeStamp) && (?Cend >= "1820"^^xsd:dateTimeStamp || ?FEend >= "1820"^^xsd:dateTimeStamp))
} 
GROUP BY ?parcel ?version ?Cstart ?FSstart ?FEstart ?Cend ?FSend ?FEend
```

## Propriétaires successifs d'une parcelle
>Propriétaires successifs de la parcelle C-191 à Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>

SELECT ?parcel (group_concat(distinct ?ownername; separator=', ') as ?owners) (count(distinct ?owner) as ?num_co_owners) 
  (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?Start)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?End)
WHERE { 
  ?parcel a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelOwner ;
                             nap:hasAttributeVersion ?version ] .
  
  ?version nap:hasOwner ?owner.
  ?owner rdfs:label ?ownername.
    
  ?version nap:isMadeBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.

  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.}
    
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}		
  }
    
} 
GROUP BY ?parcel ?version ?Cstart ?FSstart ?FEstart ?Cend ?FSend ?FEend
```

## Historique des parcelles ayant appartenues à un propriétaire donné
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX time: <http://www.w3.org/2006/time#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT distinct ?landmark ?label (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?Start)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?End)
WHERE {
    owner:0001 a nap:Owner;
           nap:isOwnerOf ?version.
    ?version a nap:AttributeVersion;
               nap:isAttributeVersionOf ?attr.
    ?attr nap:isAttributeOf ?landmark.
    
    ?landmark rdfs:label ?label.
    
  ?version nap:isMadeBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.
  OPTIONAL{?eventStart rdfs:label ?eventtitle.}
  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.}
    
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}
  }}
```

## Liste des propriétaires dans une commune à une date donnée
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX landmark: <http://data.ign.fr/id/cadastrenap/landmark/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

select ?owner ?ownername (count (distinct ?parcel) as ?num_parcels) where { 
	?owner a nap:Owner ;
        rdfs:label ?ownername;
        nap:isOwnerOf ?version.
    ?version nap:isAttributeVersionOf ?attribute.
    ?attribute nap:isAttributeOf ?parcel.
    ?parcel rdfs:label ?parcelname;
              nap:hasAttribute [ a nap:Attribute;
              nap:isAttributeType atype:SpatialDescription;
    	      nap:hasAttributeVersion [ a nap:AttributeVersion;
    				nap:firstStep/nap:relatum ?commune
              ]
    ].
    FILTER(?commune = landmark:COMM_Marolles_en_Brie)
    
      ?version nap:isMadeEffectiveBy ?changeStart.
  ?changeStart nap:dependsOn ?eventStart.
  ?eventStart nap:hasTime ?tEntityStart.

  OPTIONAL {?tEntityStart nap:timeStamp ?Cstart.}
  OPTIONAL {?tEntityStart nap:hasFuzzyBeginning/nap:timeStamp ?FSstart; 
                                               nap:hasFuzzyEnd/nap:timeStamp ?FEstart.} 
  OPTIONAL{?version nap:isMadeOutdatedBy ?changeEnd.
        ?changeEnd nap:dependsOn ?eventEnd.
        ?eventEnd nap:hasTime ?tEntityEnd.
        OPTIONAL {?tEntityEnd nap:timeStamp ?Cend.}
        OPTIONAL {?tEntityEnd nap:hasFuzzyBeginning/nap:timeStamp ?FSend; 
                                                   nap:hasFuzzyEnd/nap:timeStamp ?FEend.}		
  }
  FILTER((?Cstart <= "1820"^^xsd:dateTimeStamp || ?FSstart <= "1820"^^xsd:dateTimeStamp) && (?Cend >= "1820"^^xsd:dateTimeStamp || ?FEend >= "1820"^^xsd:dateTimeStamp))
}
GROUP BY ?owner ?ownername
ORDER BY ?ownername
```
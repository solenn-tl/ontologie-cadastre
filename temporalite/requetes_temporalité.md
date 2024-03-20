# Questions de compétences Temporalité
*A jour le 19/03/2024*

## Quelles sont les parcelles d'une nature donnée à une date donnée dans une commune donnée ?
> Quelles sont les parcelles de nature "Jardin" en 1820 à Marolles-en-Brie ?
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
  ?versionloc nap:firstStep/nap:locatum <http://data.ign.fr/id/cadastrenap/landmark/COMM_Marolles_en_Brie>.
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelNature ;
                             nap:hasAttributeVersion ?version ] .
  ?version nap:hasParcelNature pnature:Jardin.
    
  ?version nap:isMadeEffectiveBy ?changeStart.
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

## Quelles sont les natures successives d'une parcelle ?

```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX pnature: <http://data.ign.fr/id/codes/cadastrenap/parcelNature/>

SELECT ?parcel (group_concat(distinct ?naturelabel; separator=', ') as ?nature) 
  (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?EffectiveStart)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?EffectiveEnd) ?eventtitle
WHERE { 
  ?parcel a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelNature ;
                             nap:hasAttributeVersion ?version ] .
  
  ?version nap:hasParcelNature ?nature.
  ?nature skos:prefLabel ?naturelabel.
    
  ?version nap:isMadeEffectiveBy ?changeStart.
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
  FILTER (lang(?naturelabel) != "en")
} 
GROUP BY ?parcel ?version ?Cstart ?FSstart ?FEstart ?Cend ?FSend ?FEend ?eventtitle
```

## Quels sont les propriétaires successifs d'une parcelle ?
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>

SELECT ?parcel (group_concat(distinct ?ownername; separator=', ') as ?owners) (count(distinct ?owner) as ?num_co_owners) 
  (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?EffectiveStart)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?EffectiveEnd) ?eventtitle
WHERE { 
  ?parcel a nap:Landmark ;
          nap:isLandmarkType ltype:Parcel .
  
  ?parcel nap:hasAttribute [ a nap:Attribute ;
                             nap:isAttributeType atype:ParcelOwner ;
                             nap:hasAttributeVersion ?version ] .
  
  ?version nap:hasOwner ?owner.
  ?owner rdfs:label ?ownername.
    
  ?version nap:isMadeEffectiveBy ?changeStart.
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
    
} 
GROUP BY ?parcel ?version ?Cstart ?FSstart ?FEstart ?Cend ?FSend ?FEend ?eventtitle
```

## Quels est l'historique des parcelles ayant appartenues à un propriétaire donné ?
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX time: <http://www.w3.org/2006/time#>
PREFIX ltype: <http://data.ign.fr/id/codes/cadastrenap/landmarkType/>
PREFIX atype: <http://data.ign.fr/id/codes/cadastrenap/attributeType/>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT distinct ?landmark ?label (COALESCE(?Cstart, CONCAT("entre ", str(?FSstart), " et ", str(?FEstart))) AS ?EffectiveStart)
  (COALESCE(?Cend, CONCAT("entre ", str(?FSend), " et ", str(?FEend))) AS ?EffectiveEnd)
WHERE {
    owner:0001 a nap:Owner;
           nap:isOwnerOf ?version.
    ?version a nap:AttributeVersion;
               nap:isAttributeVersionOf ?attr.
    ?attr nap:isAttributeOf ?landmark.
    
    ?landmark rdfs:label ?label.
    
  ?version nap:isMadeEffectiveBy ?changeStart.
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
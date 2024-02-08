# Requêtes SPARQL pour le modelet Entités géographiques

## Compter le nombre de parcelles dans une commune
*Exemple : nombre de parcelles à Boissy-Saint-Léger*
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (count(?parcel) as ?numparcelles)
WHERE {
  ?parcel nap:isLandmarkType nap:Parcel;
          rdfs:label ?parcelnum;
          nap:hasSpatialDescription ?spat.
   ?spat a nap:SpatialDescription;
   		  nap:targets ?parcel.
   ?spat nap:firstStep [a nap:Segment;
              nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?commune]
FILTER(?commune=nap:COMM_Boissy_Saint_Leger)
}
```
## Connaître les informations d'une parcelle (nature et propriétaire)
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

SELECT ?section_id ?parcelnum ?ownername ?nature 
WHERE {
  ?parcel nap:isLandmarkType nap:Parcel;
          rdfs:label ?parcelnum;
          nap:isOwnedBy ?owner;
          nap:isParcelNature ?nature;
          nap:hasSpatialDescription ?spat.
   ?spat a nap:SpatialDescription;
   		  nap:targets ?parcel.
   ?spat nap:firstStep [a nap:Segment;
              nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?commune].
    ?spat nap:firstStep/nap:nextStep [a nap:Segment;
			  nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?section].
    ?section rdfs:label ?secname;
             dcterms:identifier ?section_id.
   	?owner rdfs:label ?ownername.
FILTER(?parcelnum="207")
FILTER(?section_id="A"@fr)
FILTER(?commune=nap:COMM_Boissy_Saint_Leger)
}
```

## Liste des parcelles d'une certaine nature dans une commune donnée
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?parcelnum ?section ?nature 
WHERE {
  ?parcel nap:isLandmarkType nap:Parcel;
          rdfs:label ?parcelnum;
          nap:isParcelNature ?nature;
          nap:hasSpatialDescription ?spat.
   ?spat a nap:SpatialDescription;
   		  nap:targets ?parcel.
   ?spat nap:firstStep [a nap:Segment;
              nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?commune].
    ?spat nap:firstStep/nap:nextStep [a nap:Segment;
			  nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?section].
    ?section rdfs:label ?secname.
FILTER(?nature=nap:Ground)
FILTER(?commune=nap:COMM_Boissy_Saint_Leger)
}
```

## Connaître la liste des parcelles situées dans une commune/section/lieu-dit
* Remplacer *?commune* ET/OU *?section* ET/OU *?place* par l'URI d'un objet précis pour réduire la liste à une zone précise.
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?parcelnum ?placename ?secname ?commname
WHERE {
  ?parcel nap:isLandmarkType nap:Parcel;
          rdfs:label ?parcelnum;
          nap:hasSpatialDescription ?spat.
   ?spat a nap:SpatialDescription;
   		  nap:targets ?parcel.
   ?spat nap:firstStep [a nap:Segment;
              nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?commune].
    ?commune rdfs:label ?commname.
    ?spat nap:firstStep/nap:nextStep [a nap:Segment;
			  nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?section].
    ?section rdfs:label ?secname.
    OPTIONAL{?spat nap:firstStep/nap:nextStep+ [a nap:FinalSegment;
        	  nap:isSpatialRelationType nap:within;
              nap:locatum ?parcel;
              nap:relatum ?place].
    ?place rdfs:label ?placename}
}
```
# Requêtes SPARQL pour le modelet Entités géographiques

## Connaître la liste des parcelles situées dans une commune/section/lieu-dit
* Remplacer 
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



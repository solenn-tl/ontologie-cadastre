## Requêtes SPARL du modelet Propriétaires

## Liste des propriétaires
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?name ?othername ?activity ?address
WHERE {
  ?owner a nap:Owner;
         rdfs:label ?name.
  OPTIONAL{?owner skos:altLabel ?othername;
         		nap:activity ?activity;
                nap:address ?address}.
}
```

## Liste des parcelles d'un propriétaire dans une commune donnée
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?parcelnum ?SECname ?COMMname ?name ?othername ?activity ?address 
WHERE {
  ?owner a nap:Owner;
         rdfs:label ?name.
  OPTIONAL{?owner skos:altLabel ?othername;
         nap:activity ?activity;
         nap:address ?address}.
  ?parcel a nap:Landmark;
    nap:isLandmarkType nap:Parcel;
    rdfs:label ?parcelnum;
    nap:hasSpatialDescription [
        a nap:SpatialDescription;
        nap:targets ?parcel;
        nap:firstStep [
            a nap:Segment;
            nap:isSpatialRelationType nap:within;
            nap:locatum ?parcel;
            nap:relatum ?commune;
            nap:nextStep [
                a nap:Segment;
                nap:isSpatialRelationType nap:within;
                nap:locatum ?parcel;
                nap:relatum ?section]]].
  ?section rdfs:label ?SECname.
  ?commune rdfs:label ?COMMname.
  ?parcel nap:isOwnedBy ?owner.
  FILTER(?commune=nap:COMM_Boissy_Saint_Leger)
  FILTER(regex(?name,"^Charlier"))
}
```

## Liste des propriétaires domiciliés à une addresse
*Exemple : liste de propriétaires vivant à Paris*
```sparql
SELECT ?name ?othername ?activity ?address 
WHERE {
  ?owner a nap:Owner;
         rdfs:label ?name;
         skos:altLabel ?othername;
         nap:activity ?activity;
         nap:address ?address.
  FILTER(regex(?address,"Paris$"))
}
```
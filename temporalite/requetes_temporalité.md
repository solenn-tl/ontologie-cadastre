# Questions de compétences temporalité

## Quelles sont les natures sucessives d'une parcelle ?
```
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

PREFIX dept: <http://data.ign.fr/id/cadastrenap/departement>
PREFIX arr: <http://data.ign.fr/id/cadastrenap/arrondissement>
PREFIX cant: <http://data.ign.fr/id/cadastrenap/canton>
PREFIX comm: <http://data.ign.fr/id/cadastrenap/commune>
PREFIX sec: <http://data.ign.fr/id/cadastrenap/section>
PREFIX parc: <http://data.ign.fr/id/cadastrenap/parcelle>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner>

SELECT ?parcel ?nature ?beginning ?end ?previous
WHERE {
  ?parcel a nap:Landmark ;
          nap:isLandmarkType nap:Parcel;
          nap:hasAttribute [a nap:Nature;
          nap:hasVersion ?v].
   ?v nap:hasBeginning ?beginning;
      nap:isParcelNature ?nature.
   OPTIONAL{?v nap:hasEnd ?end.}
}
```

## Quels sont les propriétaires sucessifs d'une parcelle ?
```
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

PREFIX dept: <http://data.ign.fr/id/cadastrenap/departement>
PREFIX arr: <http://data.ign.fr/id/cadastrenap/arrondissement>
PREFIX cant: <http://data.ign.fr/id/cadastrenap/canton>
PREFIX comm: <http://data.ign.fr/id/cadastrenap/commune>
PREFIX sec: <http://data.ign.fr/id/cadastrenap/section>
PREFIX parc: <http://data.ign.fr/id/cadastrenap/parcelle>
PREFIX owner: <http://data.ign.fr/id/cadastrenap/owner>

SELECT ?parcel ?owner ?ownerName ?ownerAddress ?beginning ?end ?previous
WHERE {
  ?parcel a nap:Landmark ;
          nap:isLandmarkType nap:Parcel;
          nap:hasAttribute [a nap:Owner;
          nap:hasVersion ?v].
   ?v nap:hasBeginning ?beginning;
   	  nap:hasEnd ?end;
      nap:isOwnedBy ?owner.
   #Propriétaire actuel
   ?owner rdfs:label ?ownerName.
   OPTIONAL{?owner nap:activity ?ownerActivity;
                   nap:activity ?ownerAddress;
                   }
   OPTIONAL{?v nap:after ?previous.}
}
```
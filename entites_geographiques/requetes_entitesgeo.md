# Requêtes SPARQL pour le modelet Entités géographiques

## Compter le nombre de parcelles dans une commune
*Exemple : nombre de parcelles à Marolles-en-Brie*
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX landmark: <http://data.ign.fr/id/codes/cadastrenap/landmark/>

select (count(distinct ?parcel) as ?count)
where { 
	?parcel a nap:Landmark;
         nap:isLandmarkType landmark:Parcel;
         nap:hasAttribute [ nap:isAttributeType nap:SpatialDescription;
        nap:version ?v
    ].
    ?v nap:firstStep [a nap:Segment;
       nap:relatum <http://data.ign.fr/id/cadastrenap/landmark/COMM_Marolles_en_Brie>
       ].
}
```
## Liste des propriétaires d'une parcelle (indépendament du temps)
> Parcelle 191, Section C, Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX landmark: <http://data.ign.fr/id/codes/cadastrenap/landmark/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

select distinct ?owner ?name ?activity ?address where { 
	<http://data.ign.fr/id/cadastrenap/landmark/Marolles_en_Brie_C_191> a nap:Landmark;
         nap:isLandmarkType landmark:Parcel;
         nap:hasAttribute [nap:isAttributeType nap:Owner;
         nap:version [
        	nap:isOwnedBy ?owner
    		]
         ].
    ?owner a nap:Owner;
           rdfs:label ?name.
    OPTIONAL{?owner nap:activity ?activity;
                    nap:address ?address.}
}
```

## Liste des natures d'une parcelle (indépendament du temps)
> Parcelle 191, Section C, Marolles-en-Brie
```sparql
PREFIX nap: <http://data.ign.fr/def/cadastrenap#>
PREFIX landmark: <http://data.ign.fr/id/codes/cadastrenap/landmark/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

select distinct ?nature where { 
	<http://data.ign.fr/id/cadastrenap/landmark/Marolles_en_Brie_C_191> a nap:Landmark;
         nap:isLandmarkType landmark:Parcel;
         nap:hasAttribute [nap:isAttributeType nap:Nature;
         nap:version [
        	nap:hasParcelNature ?nature
    		]
         ].
}
```

## Liste des parcelles d'une certaine nature dans une commune donnée
```sparql

```

## Connaître la liste des parcelles situées dans une commune/section/lieu-dit
* Remplacer *?commune* ET/OU *?section* ET/OU *?place* par l'URI d'un objet précis pour réduire la liste à une zone précise.
```sparql

```
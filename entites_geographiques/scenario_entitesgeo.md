# Scénario de motivation du modelet Entités géographiques

## Nom
Entités géographiques

## Description

La parcelle est l'entité géographique élémentaire utilisée pour définir le montant de l'allivrement. Elle est caractérisée par son numéro, sa géométrie, sa nature et son appartenance à un ou plusieurs propriétaires.

Une parcelle est rattachée à une section cadastrale qui se trouve elle-même dans une commune. Par ce biais, elle est rattachée aux différentes circonscriptions administratives/électorales françaises. La production du cadastre imcombait aux départements. L'organisation des opérations cadastrales étaient basée sur une distribution par canton et arrondissement. Ces circonscriptions étaient également utilisées pour effectuer des résumés statistiques. 

Les parcelles et les objets du domaine non cadastrés - tels que les routes ou les cours d'eau - constituent les deux unités géographiques élémentaires qui permettent de reconstituer la géométrie complète des sections puis des communes.

Une **parcelle** est caractérisée par :
- {*obligatoire*} son **numéro cadastral**
- {*obligatoire*} sa **localisation** : (lieu-dit) => section => commune
- {*obligatoire*} sa **nature**
- {*obligatoire*} son/ses **propriétaire(s) ou usufruitiers**
- {*optionnel*} sa **géométrie**

Un **objet du domaine non cadastré** est caractérisé par : 
- {*obligatoire*} son **nom**
- {*optionnel*} sa **nature**
- {*optionnel*} sa **géométrie**
- {*optionnelle*} sa **localisation**
<p><span style="color:red">Comment gérer les objets qui se trouvent dans plusieurs sections, voir communes, voir département (ex : "La Seine", "Grande route de Paris à Provins") ? => "portion de" ?</span>=> Portion d'un objet théorique ? Apparaît dans telle section ?</p>

Une **section cadastrale** est caractérisée par :
- {*obligatoire*} son **identifiant** (lettre)
- {*obligatoire*} son **nom**
- {*obligatoire*} sa **localisation** : commune => canton => arrondissement => département
- {*optionnelle*} sa **géométrie**

Une **circonscription administrative** est caractérisée par :
- {*obligatoire*} son **classe** : commune => canton => arrondissement => département
- {*obligatoire*} son **nom**
- {*obligatoire*} sa **localisation** : par rapport aux autres circonscriptions administratives
- {*optionnelle*} sa **géométrie**

*Remarque : l'existance des entités administratives et la valeur de leurs propriétés est possède une dimension temporelle décrite en détails dans le modelet "Temporalité". Les exemples fournis ici décrivent les entités géographiques à un instant T*.

## Exemples

### Exemple 1 [Parcelle]
<ul>
    <li>Numéro : 207</li>
    <li>Localisation : Lieu-dit Le Village, Section A, Commune de Boissy-Saint-Léger</li>
    <li>Propriétaire : Charlier</li>
    <li>Nature : Pâture</li>
</ul>
 - FRA094_3P_000065_01_0030, Etats de sections de Boissy-Saint-Léger, 1810

 ### Exemple 2 [Objet du domaine non cadastré]
<ul>
    <li>Nom : Grande route de Paris à Provins</li>
    <li>Nature : route</li>
    <li>Localisation : Section A, Commune de Boissy-Saint-Léger</li>
</ul>
 - FRA094_3P_000851, Plan parcellaire de la section C de Boissy-Saint-Léger, 1810

### Exemple 3 [Section]
<ul>
    <li>Identifiant (lettre) : A</li>
    <li>Nom : Section A dite du Piple</li>
    <li>Localisation : Commune de Boissy-Saint-Léger, Justice de Paix de Boissy-Saint-Léger, Arrondissement de Corbeil, Département de Seine-et-Oise</li>
</ul>
 - FRA094_3P_000065_01_0001, Etats de sections de Boissy-Saint-Léger, 1810

### Exemple 4 [Commune]
<ul>
    <li>Nom : Boissy-Saint-Léger</li>
    <li>Localisation : Justice de Paix de Boissy-Saint-Léger, Arrondissement de Corbeil, Département de Seine-et-Oise</li>
</ul>
 - FRA094_3P_000065_01_0001, Etats de sections de Boissy-Saint-Léger, 1810
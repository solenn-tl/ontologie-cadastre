# Scénario de motivation du modelet Entités géographiques

## Nom
Entités géographiques

## Description

La parcelle est l'entité géographique élémentaire utilisée pour définir le montant de l'allivrement. Elle est caractérisée par son identifiant, sa géométrie, sa nature et son appartenance à un ou plusieurs propriétaires. L'objectif de la thèse est de suivre l'évolution de chaque parcelle au cours du temps. 

Une parcelle est rattachée à une section cadastrale qui se trouve elle-même dans une commune. Par ce biais, elle est rattachée aux différentes circonscriptions administratives/électorales françaises. Ce rattachement s'explique par la responsabilité de production du cadastre qui imcombait aux départements et par l'organisation des opérations qui étaient distribuée par canton et arrondissement. Ces circonscriptions étaient également utilisées pour effectuer des résumés statistiques. 

Les parcelles et les objets du domaine non cadastrés - tels que les routes ou les cours d'eau - constituent les deux unités géographiques élémentaires qui permettent de reconstituer la géométrie complète des sections puis des communes.

Une **parcelle** est caractérisée par :
- {*obligatoire*} son **numéro cadastral**
- {*obligatoire*} sa **localisation** : (lieu-dit) => section => commune
- {*obligatoire*} sa **nature**
- {*obligatoire*} son/ses **propriétaire(s) ou usufruitiers**
- {*optionnel*} sa **géométrie**

Un **objet du docmaine non cadastré** est caractérisé par : 
- {*obligatoire*} son **nom**
- {*obligatoire*} sa **nature**
- {*optionnel*} sa **géométrie**
- {*obligatoire*} sa **localisation** : section [1..n] => commune

Une **section cadastrale** est caractérisée par :
- {*obligatoire*} son **identifiant** (lettre)
- {*obligatoire*} son **nom**
- {*obligatoire*} sa **localisation** : commune => canton => arrondissement => département

Une **circonscription administrative** est caractérisée par :
- {*obligatoire*} son **nom**
- {*obligatoire*} son **classe** : commune => canton => arrondissement =>  département
- {*obligatoire*} sa **localisation** : par rapport aux autres circonscriptions administratives

*Remarque : l'existance des entités administratives et la valeur de leurs propriétés est possède une dimenssion temporelle décrite en détails dans le modelet "Temporalité"*.

## Exemples

### Exemple 1 [Parcelle]
<ul>
    <li>Numéro : 207</li>
    <li>Localisation : Le Village, Section A, Boissy-Saint-Léger<li>
    <li>Propriétaire : Charlier</li>
    <li>Nature : Pâture</li>
</ul>
 - FRA094_3P_000065_01_0030, Etats de sections de Boissy-Saint-Léger, 1810

### Exemple 2 [Section]
<ul>
    <li>Lettre : A</li>
    <li>Nom : Section A dite du Piple</li>
    <li>Localisation : Commune de Boissy-Saint-Léger, Justice de Paix de Boissy-Saint-Léger, Arrondissement de Corbail, Département de Seine-et-Oise<li>
</ul>
 - FRA094_3P_000065_01_0001, Etats de sections de Boissy-Saint-Léger, 1810
# Annotation sémantique de tables

>Jixiong Liu, Yoan Chabot, Raphaël Troncy, Viet-Phi Huynh, Thomas Labbé, Pierre Monnin, *From tabular data to knowledge graphs: A survey of semantic table interpretation tasks and methods*,
Journal of Web Semantics,
Volume 76,
2023,
100761,
ISSN 1570-8268,
https://doi.org/10.1016/j.websem.2022.100761.
(https://www.sciencedirect.com/science/article/pii/S1570826822000452)

## Tâches et leur application au cadastre

<table>
    <tr>
        <th>Tâche</th>
        <th>Description</th>
        <th>Application</th>
    </tr>
    <tr>
        <td>Cell-Entity Annotation (CEA)</td>
        <td>Entity Linking</td>
        <td><ul><li>Lier une mention de propriétaire à une instance de Propriétaire</li>
        <li>Lier une mention de nature à un Concept Nature (Terre, Jardin...)</li>
        <li>Lier une mention de lieu-dit à une instance Lieu-dit</li>
        </ul>
        </td>
    </tr>
    <tr>
        <td>Column-Type Annotation (CTA)</td>
        <td>Associer une colonne du tableau à une propriété du KG</td>
        <td><ul>
            <li>Tâche en partie effectuée par le choix du formulaire d'entités utilisé pour annoter les données pour l'entraînement avec DAN</li>
            <li>Pour certaine colonnes (ex: identité du propriétaire) : ajout d'un niveau dans la hiérarchie de propriétés avec une étape de NER (nom, activité, addresse).</li>
        </ul></td>
    </tr>
    <tr>
        <td>Columns-Propert Annotation (CPA)</td>
        <td>Associer une paire de colonnes à une propriété</td>
        <td>Localisation d'une parcelle (Section > Numéro) dans les matrices</td>
    </tr>
    <tr>
        <td>Topic annotation</td>
        <td>Annoter tout ou partir du tableau à l'aide d'une entité</td>
        <td><ul>
            <li>La commune est déduite des métadonnées de la côte d'archive traitée.</li>
            <li>La date d'une information issue des états de sections est généralement celle de l'état de section lui même.</li>
            <li>Dans les matrices, les cellules vides dans "Date d'entrée" correspondent à la date d'ouverture de la matrice.</li>
            <li>Idem pour les cellules vides dans "Date de sortie" correspondent à la date de clôture de la matrice.</li>
        </ul></td>
    </tr>
    <tr>
        <td>Row-To-Instance</td>
        <td>Attribuer un type d'entité à la ligne elle même à partir de ses colonnes</td>
        <td>???</td>
    </tr>
</table>

Dans notre cas, il semble y avoir deux niveaux de Topic Annotation:
- à l'échelle d'un registre (propagation des métadonnées)
- à l'échelle de la page

## Etapes

1. Pre-processing
    - Format normalization
        - Gestion du format
        - Gestion de l'encodage
        - Gestion de la langue
        - Nettoyage des valeurs
            - Gestion des idem
    - Informational analysis
        - Type de tableau
        - Orientation du tableau
        - En-têtes de colonnes
2. Candidate generation
3. Table element processing
4. Iterative desambiguisation
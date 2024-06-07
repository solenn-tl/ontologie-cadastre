# Schéma du graphe

Outil de visualisation : [Gaphviz Visual Editor](http://magjac.com/graphviz-visual-editor/)

## Graphe initial
### Lien
[Lien](http://magjac.com/graphviz-visual-editor/?dot=strict%20digraph%20%7B%0D%0A%20%20%20%20comment%3D%22Landmark%22%0D%0A%20%20%20%20a%20%5Blabel%3D%22Landmark%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22%231f77b4%22%5D%0D%0A%20%20%20%20b%20%5Blabel%3D%22Plot%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22%23ff7f0e%22%5D%0D%0A%20%20%20%20c%20%5Blabel%3D%22Parcelle%20X%5CnSection%20Y%5CnCommune%22%20shape%3D%22rectangle%22%20style%3D%22filled%22%20fillcolor%3D%22yellow%22%5D%0D%0A%20%20%20%20a%20-%3E%20b%20%5Blabel%3D%22isLandmarkType%22%5D%0D%0A%20%20%20%20a%20-%3E%20c%20%5Blabel%3D%22rdfs%3Alabel%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Attribut%20nature%22%0D%0A%20%20%20%20d%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20e%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20f%20%5Blabel%3D%22Plot%5CnNature%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22pink%22%5D%0D%0A%20%20%20%20g%20%5Blabel%3D%22Jardin%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22cyan%22%5D%0D%0A%20%20%20%20a%20-%3E%20d%20%5Blabel%3D%22hasAttribute%22%5D%0D%0A%20%20%20%20d%20-%3E%20e%20%5Blabel%3D%22hasAttributeVersion%22%5D%0D%0A%20%20%20%20d%20-%3E%20f%20%5Blabel%3D%22isAttributeType%22%5D%0D%0A%20%20%20%20e%20-%3E%20g%20%5Blabel%3D%22hasPlotNature%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Folios%20pr%C3%A9c%C3%A9dents%20et%20suivants%22%0D%0A%20%20%20%20w%20%5Blabel%3D%2250%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgrey%22%5D%0D%0A%20%20%20%20x%20%5Blabel%3D%22176%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgrey%22%5D%0D%0A%20%20%20%20a%20-%3E%20x%20%5Blabel%3D%22takenFrom%22%5D%0D%0A%20%20%20%20a%20-%3E%20w%20%5Blabel%3D%22passedTo%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Compte%20foncier%22%0D%0A%20%20%20%20z%20%5Blabel%3D%22Compte%5Cnfoncier%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22darkgrey%22%5D%0D%0A%20%20%20%20a%20-%3E%20z%20%5Blabel%3D%22isMentionnedIn%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Propri%C3%A9taire%22%0D%0A%20%20%20%20o%20%5Blabel%3D%22Berthier%20%5Cnalexandre%20%5Cnprince%20de%20%5Cnneufch%C3%A2tel%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22magenta%22%5D%0D%0A%20%20%20%20oo%20%5Blabel%3D%22Vauguyon%5Cnmaire%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22magenta%22%5D%0D%0A%20%20%20%20k%20%5Blabel%3D%22Plot%5CnTaxpayer%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22pink%22%5D%0D%0A%20%20%20%20n%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20p%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20z%20-%3E%20l%20%5Blabel%3D%22hasAttribute%22%5D%0D%0A%20%20%20%20l%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20l%20-%3E%20k%20%5Blabel%3D%22isAttributeType%22%5D%0D%0A%20%20%20%20l%20-%3E%20m%20%5Blabel%3D%22hasAttribute%22%5D%0D%0A%20%20%20%20m%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20m%20-%3E%20n%20%5Blabel%3D%22hasAttributeVersion%22%5D%0D%0A%20%20%20%20n%20-%3E%20o%20%5Blabel%3D%22hasTaxpayer%22%5D%0D%0A%20%20%20%20m%20-%3E%20on%20%5Blabel%3D%22hasAttributeVersion%22%5D%0D%0A%20%20%20%20on%20%5Blabel%3D%22%22%20shape%3D%22circle%22%5D%0D%0A%20%20%20%20on%20-%3E%20oo%20%5Blabel%3D%22hasTaxpayer%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Folio%20actuel%22%0D%0A%20%20%20%20aa%20%5Blabel%3D%22Folio%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgrey%22%5D%0D%0A%20%20%20%20z%20-%3E%20aa%20%5Blabel%3D%22isOrWasIncludedIn%22%5D%0D%0A%20%20%20%20aa%20-%3E%20ab%5Blabel%3D%22hasNum%22%5D%0D%0A%20%20%20%20aa%20-%3E%20ac%5Blabel%3D%22hasAlternativeNum%22%5D%0D%0A%20%20%20%20ab%20%5Blabel%3D%22NumFolio%22%20shape%3D%22rectangle%22%5D%0D%0A%20%20%20%20ac%20%5Blabel%3D%22AlternativeNumFolio%22%20shape%3D%22rectangle%22%5D%0D%0A%20%20%20%20xx%20%5Blabel%3D%22Page%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgrey%22%5D%0D%0A%20%20%20%20aa%20-%3E%20xx%20%5Blabel%3D%22isOrWasIncludedIn%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Dates%20d%27entr%C3%A9es%20et%20de%20sortie%22%0D%0A%20%20%20%20q%20%5Blabel%3D%22Date%20d%27entr%C3%A9e%22%20shape%3D%22rectangle%22%5D%0D%0A%20%20%20%20r%20%5Blabel%3D%22Date%20de%20sortie%22%20shape%3D%22rectangle%22%5D%0D%0A%20%20%20%20a%20-%3E%20p%20%5Blabel%3D%22hasTime%22%5D%0D%0A%20%20%20%20p%20-%3E%20q%20%5Blabel%3D%22hasBeginning%22%5D%0D%0A%20%20%20%20p%20-%3E%20r%20%5Blabel%3D%22hasEnd%22%5D%0D%0A%0D%0A%20%20%20%20comment%3D%22Changes%22%0D%0A%20%20%20%20comment%3D%22Owner%20Changes%22%0D%0A%20%20%20%20cht1%20%5Blabel%3D%22Attribute%5CnVersion%5CnAppearance%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22green%22%5D%0D%0A%20%20%20%20cht2%20%5Blabel%3D%22Attribute%5CnVersion%5CnTransition%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22green%22%5D%0D%0A%20%20%20%20cht3%20%5Blabel%3D%22Attribute%5CnVersion%5CnDisappearance%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22green%22%5D%0D%0A%20%20%20%20cht1%20-%3E%20l%20%5B%5D%0D%0A%20%20%20%20oc1%20%5Blabel%3D%22Owner%5Cnchange%5Cn1%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgreen%22%5D%0D%0A%20%20%20%20oc2%20%5Blabel%3D%22Owner%5Cnchange%5Cn2%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgreen%22%5D%0D%0A%20%20%20%20oc3%20%5Blabel%3D%22Owner%5Cnchange%5Cn3%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightgreen%22%5D%0D%0A%20%20%20%20oc1%20-%3E%20cht1%20%5Blabel%3D%22isChangeType%22%5D%0D%0A%20%20%20%20oc2%20-%3E%20cht2%20%5Blabel%3D%22isChangeType%22%5D%0D%0A%20%20%20%20oc3%20-%3E%20cht3%20%5Blabel%3D%22isChangeType%22%5D%0D%0A%20%20%20%20oc2%20-%3E%20oc1%20%5Blabel%3D%22after%22%5D%0D%0A%20%20%20%20oc3%20-%3E%20oc2%20%5Blabel%3D%22after%22%5D%0D%0A%20%20%20%20%0D%0A%20%20%20%20comment%3D%22Event%22%0D%0A%20%20%20%20evo1%20%5Blabel%3D%22Owner%5Cnmutation%5Cn1%22%20shape%3D%22circle%22%20style%3D%22filled%22%20fillcolor%3D%22lightblue%22%5D%0D%0A%7D)

### Code
```
strict digraph {
    comment="Landmark"
    a [label="Landmark" shape="circle" style="filled" fillcolor="#1f77b4"]
    b [label="Plot" shape="circle" style="filled" fillcolor="#ff7f0e"]
    c [label="Parcelle X\nSection Y\nCommune" shape="rectangle" style="filled" fillcolor="yellow"]
    a -> b [label="isLandmarkType"]
    a -> c [label="rdfs:label"]
    
    comment="Attribut nature"
    d [label="" shape="circle"]
    e [label="" shape="circle"]
    f [label="Plot\nNature" shape="circle" style="filled" fillcolor="pink"]
    g [label="Jardin" shape="circle" style="filled" fillcolor="cyan"]
    a -> d [label="hasAttribute"]
    d -> e [label="hasAttributeVersion"]
    d -> f [label="isAttributeType"]
    e -> g [label="hasPlotNature"]
    
    comment="Folios précédents et suivants"
    w [label="50" shape="circle" style="filled" fillcolor="lightgrey"]
    x [label="176" shape="circle" style="filled" fillcolor="lightgrey"]
    a -> x [label="takenFrom"]
    a -> w [label="passedTo"]
    
    comment="Compte foncier"
    z [label="Compte\nfoncier" shape="circle" style="filled" fillcolor="lightgreen"]
    a -> z [label="isMentionnedIn"]
    
    comment="Propriétaire"
    o [label="Berthier \nalexandre \nprince de \nneufchâtel" shape="circle" style="filled" fillcolor="magenta"]
    oo [label="Vauguyon\nmaire" shape="circle" style="filled" fillcolor="magenta"]
    k [label="Plot\nTaxpayer" shape="circle" style="filled" fillcolor="pink"]
    n [label="" shape="circle"]
    p [label="" shape="circle"]
    z -> l [label="hasAttribute"]
    l [label="" shape="circle"]
    l -> k [label="isAttributeType"]
    l -> m [label="hasAttribute"]
    m [label="" shape="circle"]
    m -> n [label="hasAttributeVersion"]
    n -> o [label="hasTaxpayer"]
    m -> on [label="hasAttributeVersion"]
    on [label="" shape="circle"]
    on -> oo [label="hasTaxpayer"]
    
    comment="Folio actuel"
    aa [label="Folio" shape="circle" style="filled" fillcolor="lightgrey"]
    z -> aa [label="isOrWasIncludedIn"]
    aa -> ab[label="hasNum"]
    aa -> ac[label="hasAlternativeNum"]
    ab [label="NumFolio" shape="rectangle"]
    ac [label="AlternativeNumFolio" shape="rectangle"]
    xx [label="Page" shape="circle" style="filled" fillcolor="lightgrey"]
    aa -> xx [label="isOrWasIncludedIn"]
    
    comment="Dates d'entrées et de sortie"
    q [label="Date d'entrée" shape="rectangle"]
    r [label="Date de sortie" shape="rectangle"]
    a -> p [label="hasTime"]
    p -> q [label="hasBeginning"]
    p -> r [label="hasEnd"]

    comment="Changes"
    
    comment="Event"
}
```
## Graphe final
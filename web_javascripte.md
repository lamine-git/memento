# Document

## Recherche element par Id

    document.getElementById(<Id>)

## Recherche element par class

    document.getElementByClassName(<class>)

## Recherche element par nom balise

    document.getElementByTagName()

## Recherche complexe

    document.querySelector("#myId p.article > a")

Recherche dans l'élément ayant pour id #myId , les éléments de type '<p>' qui ont pour classe article , afin de récupérer le lien ( '<a>' ) qui est un enfant direct (pas des enfants de ses enfants).

    querySelector()  ne renvoie pas une liste des résultats, mais le premier élément qui correspond à la recherche.

# Les recherches depuis un element

_element.children_ : cette propriété nous retourne la liste des enfants de cet élément ;

_element.parentElement_ : cette propriété nous retourne l'élément parent de celui-ci ;

_element.nextElementSibling / element.previousElementSibling_ : ces propriétés nous permettent de naviguer vers l'élément suivant / précédent de même niveau que notre élément.

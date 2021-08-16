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

# MODIFIER LE DOM

## Modifiez le contenu d'un element

**'innerHTML'** demande à ce que vous entriez du texte représentant un contenu HTML

**'textContent'** , quant à elle, demande un simple texte qui ne sera pas interprété comme étant du HTML.

## Modifiez des classes

**classlist** permet d'acceder à la liste des classes d'un element. **classlist** est fourni avec une serie de fonctions par exemple:

    add(<string>, [<string>, ...] )
    remove(<string>, [<string>, ...] )
    contains(<string> )    vérifie si la classe spécifiée est contenue par cet élément
    replace(<old>, <new> )

## changer les styles d'un element

**style** , vous permet de récupérer et modifier les différents styles d'un élément. exemple:
elt.style.color = "#fff";

## Modifier les attributs

**setAttribut** permet de definir ou remplacer les attributs d'un element. exemple:
elt.setAttribute("type", "password"); // Change le type de l'input en un type password
elt.setAttribute("name", "my-password"); // Change le nom de l'input en my-password
elt.getAttribute("name"); // Retourne my-password

## Créez de nouveaux elements

    const newElt = document.createElement("div"); // div ou une autre balise

## ajoutez des enfants

    parentNode.appendChild(<element>)

## supprimez et remplacez des elements

### supprimer

    parentNode.removeChild(<element>)

### remplacer

    parentNode.replaceChild(<newElement>, <oldElement>)

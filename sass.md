## le principe DRY
c'est une abréviation en anglais signifiant “Don’t repeat yourself”. “Ne vous répétez pas !”

    < button class="btn btn-rounded btn-wide" >...</button>
le fait d'ajouter btn btn-rounded ... permet de reutiliser les .btn par exemple ailleurs sur le site

## Créez des sélecteurs HTML avec la méthodologie BEM
* BEM signifie bloc, élément, modificateur :

    * les blocs sont des bouts de code autonomes ;

    * les éléments sont les parties qui forment le bloc ;

    * les modificateurs changent l’apparence ou le comportement d’un bloc ou d’un élément.

* Les blocs sont nommés en fonction de leur rôle :

    * les éléments indiquent le nom de leur bloc parent, suivi d’un double underscore/dunder (__) puis du rôle de l’élément : form__label.

* Les modificateurs utilisent le nom du bloc ou de l’élément qu’ils modifient, suivi de deux tirets (--) et de ce que le sélecteur modifie : button--green.

* Vous n’avez pas besoin d’attribuer à chaque élément d’une page web un sélecteur de classe. Vous pouvez utiliser les sélecteurs pour que votre code HTML soit plus propre et concis.

# Utilisez les préprocesseurs CSS pour des fonctionnalités avancées
* Les préprocesseurs CSS vous permettent d’imbriquer votre code (on appelle ça le **nesting**) pour créer une hiérarchie plus facile à lire et regrouper des morceaux de code entre eux.

* Il existe plein de préprocesseurs, mais le plus courant est Sass, qui signifie Syntactically Awesome Style Sheets (“Feuilles de style syntaxiquement fantastiques”).

* Au-delà du nesting, les préprocesseurs vous permettent d’utiliser des fonctionnalités de programmation pour créer une codebase plus maintenable, tout en diminuant les énormes quantités de code à écrire.

Exemple de **Nesting**

    ul {
        list-style: none;
        text-align: right;
        li {
            display: inline;
            font-size: 3rem;
            color: #D6FFF5;
        }
    }

# Utilisez les combinateurs

## Combinateur parent
    .parent {
        background-color: #15DEA5;
    }

## Combinateur descendant
    .parent .descendant {
        color: #fff;
    }

## Combinateur parent > enfant
    .parent > .child {
        color: #D6FFF5;
    }

## Combinateur adjacent
    .parent + .adjacent {
        color: #001534;
    }

1. Dans le premier cas, tout ce qui est relié à l’élément parent adoptera la couleur de fond spécifiée. 

2. Dans le deuxième cas, si le deuxième élément est le descendant du premier, alors il adoptera la couleur spécifiée. 

3. Dans le troisième cas, si le deuxième élément est un enfant du premier, alors il adoptera la couleur spécifiée.

4. Dans le quatrième cas,  si le deuxième élément est immédiatement précédé du premier, alors il adoptera la couleur spécifiée.

### En ajoutant le bon symbole de combinateur devant un sélecteur, vous pouvez créer tous les combinateurs CSS dans Sass :

    .parent {
        background-color: #15DEA5;
        .descendant {
            color: #fff;
        }
        >.child {
            color: #D6FFF5;
        }
        +.adjacent {
            color: #001534;
        }
    }

## Utilisez l’esperluette

Ajoutons donc une esperluette avant notre pseudosélecteur  :hover  :

    ul {
        list-style: none;
        text-align: right;
        li {
            display: inline;
            font-size: 3rem;
            color: #D6FFF5;
            &:hover {
                color: #001534;
            }
        }
    }

Et voici le CSS qui en découle :

    ul {
        list-style: none;
        text-align: right;
    }
    ul li {
        display: inline;
        font-size: 3rem;
        color: #D6FFF5;
    }
    ul li:hover {
        color: #001534;
    }

# Utilisez des sélecteurs BEM avec Sass

    .block{
        background-color: #15DEA5;
        &__element {
            color: #fff;
            &--modifier {
                background-color: #001534;
            }
        }
    }

Nous obtenons un CSS compilé parfaitement conforme avec ce que nous voulions :

    .block {
        background-color: #15DEA5;
    }
    .block__element {
            color: #fff;
    }
    .block__element--modifier {
        background-color: #001534;
    }

## Utilisez les spécificités là où vous en avez besoin

    .btn {
        display: inline-block;
        margin: 0 auto;
        background: #15DEA5;
        padding: 1rem;
        &--disabled {
            background: grey;
        }
        &--outline {
            background: transparent;
            border: 2px solid #15DEA5;
            &.btn--disabled{
                border: 2px solid grey;
            }
        }
    }

Nous utilisons l’esperluette pour créer deux sélecteurs distincts. Le premier est un **modificateur standard**
    btn--disabled
, qui outrepassera la couleur de fond de
    .btn
pour la mettre en gris. Le second est un **sélecteur** avec deux classes,
    .btn--outline
et  
    btn--disabled
, ce qui signifie que les deux classes doivent être appliquées afin que les règles que comporte ce sélecteur entrent en vigueur pour changer la couleur du contour en gris.
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
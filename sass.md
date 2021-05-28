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

Nous utilisons l’esperluette pour créer deux sélecteurs distincts. Le premier est un **modificateur standard** 'btn--disabled' , qui outrepassera la couleur de fond de '.btn' pour la mettre en gris. Le second est un **sélecteur** avec deux classes, '.btn--outline' et 'btn--disabled' , ce qui signifie que les deux classes doivent être appliquées afin que les règles que comporte ce sélecteur entrent en vigueur pour changer la couleur du contour en gris.

    .btn {
        display: inline-block;
        margin: 0 auto;
        background: #15DEA5;
        padding: 1rem;
    }
    .btn--disabled {
        background: grey;
    }
    .btn--outline {
        background: transparent;
        border: 2px solid #15DEA5;
    }
    .btn--outline.btn--disabled {
        border: 2px solid grey;
    }

# Améliorez la maintenabilité du code avec les variables Sass

nommer la variable en fonction de son rôle

exemple: 

    $color-primary (couleur principale en anglais)

    $mint: #15DEA5;

# Utilisez les mixins Sass avec des arguments

    @mixin mixin-name {
        css-property: value;
    }

### Exemple

    @mixin heading-shadow{
        text-shadow: .55rem .55rem #15DEA5;
    }

    .form {
        &__heading {
            @include heading-shadow;
        }
    }

## Customisez la valeur par défaut de la mixin

### Exemple:

    @mixin heading-shadow($colour){
        text-shadow: .55rem .55rem $colour;
    }

    .heading{
        &__header {
            @include heading-shadow(#fff);
        }
    }

Plutôt que de renseigner une valeur de couleur chaque fois que vous utilisez votre mixin heading-shadow, vous pouvez régler la valeur par défaut de l’argument.

### exemple

    @mixin heading-shadow($colour: $colour-primary){
        text-shadow: .55rem .55rem $colour;
    }

## Allez plus loin en sophistiquant vos mixins

    $heading-shadow-size: 0.55rem;
    @mixin heading-shadow($colour: $colour-primary, $shadow-size: $heading-shadow-size){
        text-shadow: $shadow-size $shadow-size $colour;
    }

* On utilise le mot clé  @mixin  pour déclarer une mixin.

* On utilise le mot clé  @include  pour placer une instance du mixin dans son code.

# Écrivez du code plus propre grâce aux extensions Sass

## Utilisez les extensions Sass

    .typography {
        color: $colour-primary;
        font-size: 2rem;
        font-weight: 100;
        line-height: 1.7;
    }

    h1 {
        @extend .typography;
    }

## Utilisez les placeholders

    %typography {
        color: $colour-primary;
        font-size: 2rem;
        font-weight: 100;
        line-height: 1.7;
    }

    h1 {
        @extend %typography;
    }
    textarea {
        @extend %typography;
    }
    button {
        @extend %typography;
    }
    input {
        @extend %typography;
    }

Pour éviter la présence de sélecteurs inutilisés dans votre codebase, vous pouvez utiliser des placeholders d’ensembles de règles en préfixant leur nom d’un symbole pourcent (%) :  %extend-placeholder 

### !!!!!!!!!!!!!!!!!!!!!!!! n’utilisez pas d’extensions mais plutot des mixins

# Améliorez les mixins avec les fonctions Sass

## Utilisez la bonne fonction

    @mixin heading-shadow($colour:$colour-primary, $size: $heading-shadow-size){
        text-shadow: $size $size darken($colour, 10%);
    }

Nous avons remplacé $colour dans les arguments de text-shadow par la fonction  darken()  et avons passé $colour en premier argument, et la proportion dans laquelle nous voulons la rendre plus foncée en deuxième argument : ici 10 %.

Quand vous regardez le CSS compilé, vous voyez que le mixin heading-shadow produit une ombre ayant la valeur hex  #11af82, soit une version 10 % plus foncée que $colour-primary (#15dea5) :

# Optimisez les mixins grâce aux conditions dans Sass

    @if ( lightness($colour) < 25% ) {
        $colour: lighten($colour, 10%);
    }
    @else{
        $colour: darken($colour, 10%);
    }

Du coup, si la condition est vraie et que la luminosité de $colour est inférieure à 25 %, on veut utiliser la fonction  lighten()  pour l’éclaircir de 10 %. Mais si l’instruction est fausse, alors on veut utiliser la fonction  darken()  pour l’assombrir de 10 %.

Intégrons à présent notre nouvelle condition si/alors dans notre mixin heading-shadow  :

    @mixin heading-shadow($colour: $colour-primary, $size: $heading-shadow-size){
        @if ( lightness($colour) < 25% ) {
            $colour: lighten($colour, 10%);
        }@else{
            $colour: darken($colour, 10%);
        }
        text-shadow: $size $size $colour;
    }

    .form {
        &__heading {
            @include heading-shadow($colour-secondary);
        }
    }

    resultat:

    .form__heading {
        text-shadow: 0.55rem 0.55rem #002a67;
    }

    autre exemple

    @if ( lightness($colour) < 25% ) and ( lightness($colour) > 10% ) {...}

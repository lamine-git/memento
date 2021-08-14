# Créez des animations simples avec les transitions

    $cd-btn: #011c37;
    $cd-txt: #15DEA5;
    .btn {
        background: $cd-btn;
        color: $cd-txt;
        font-size: 3rem;
        cursor: pointer;
        padding: 1.85rem 3rem;
        border-radius: 10rem;
        transform: scale(1);
        transition-property: transform; //on applique la propriété transition à transform dans :hover
        transition-duration: 400ms; //ajout de la durée
        &:hover {
            transform: scale(1.15);
    }

}

## Maîtrisez les propriétés raccourcies

ecrire ceux ci

    transition-property: transform;transition-duration: 400ms;

revient à ecrire

    transition: transform 400ms;

## Resumé

- les 5 éléments nécessaires pour créer une transition sont :

  - une propriété CSS à modifier,

  - une valeur initiale pour votre propriété CSS,

  - une valeur finale pour cette même propriété,

  - une durée,

  - une pseudoclasse pour déclencher l’animation ;

- on applique la valeur initiale à l’élément qu’on veut modifier, et la valeur finale dans la pseudoclasse qui déclenche la transition ;

- la durée peut s’exprimer en secondes : 0.4s, ou en millisecondes : 400ms ;

- les propriétés d’une transition peuvent être déclarées individuellement : transition-duration: 400ms ;

- ou bien combinées en une seule propriété comme : transition: transform 400ms .

# Déclenchez vos transitions avec les pseudoclasses

## liste des pseudoclasses les plus couramment utilisées pour déclencher des transitions :

- :hover, qui est déclenché au survol de la souris ;

- :active, activé au clic de l'utilisateur (le plus souvent pour les liens et boutons) ;

  \*:focus, qui se déclenche lorsque son élément reçoit le focus (soit il est sélectionné à l'aide du clavier, soit il est activé avec la souris) ;

- :valid, dont la validation du contenu s'effectue correctement par rapport au type de donnée attendu ;

- :invalid, qui inversement, correspond à un élément dont la validation du contenu ne s'effectue pas correctement par rapport au type de donnée attendu ;

- :not(), qui correspond à la négation. Elle prend un sélecteur en argument et permet de cibler les éléments qui ne sont pas représentés par cet argument ;

- :checked, qui correspond aux input de type checkbox, option ou radio qui sont cochés ;

- :enabled, un élément avec lequel on peut interagir ;

- :disabled, qui correspond à un élément dont l'interaction a été bloquée.

## Validez un formulaire

    $cd-txt: #6300a0;
    $cd-txt--invalid: #fff;
    $cd-danger: #b20a37;
    .form {
        &__group {
            & input {
                border: 2px solid $cd-box;
                border-radius: 100rem;
                color: $cd-txt;
                font-family: 'Montserrat', sans-serif;
                font-size: 2.5rem;
                outline: none;
                padding: .5rem 1.5rem;
                width: 100%;
                &:focus {
                    border: 2px solid $cd-txt;
                }
                &:not(:focus):invalid {
                    background: $cd-danger;
                    border: 2px solid $cd-danger;
                    color: $cd-txt--invalid;
                }
            }
        }
    }

l’adresse e-mail est bien vérifiée pendant que l’utilisateur la tape. Mais le clignotement entre l’effet :focus et l’effet :invalid est assez désagréable à l’œil. Pour affiner tout ça, nous avons utiliser la pseudoclasse :not(), combinée à la pseudoclasse :focus, afin de s’assurer que l’utilisateur a terminé de renseigner son adresse e-mail avant de lui faire un feedback de validation.

### ajouter une propriété transition au background-color

En reprenant le meme exemple que precedemment

    $cd-txt: #6300a0;
    $cd-txt--invalid: #fff;
    $cd-danger: #b20a37;
    .form {
        &__group {
            & input {
                border: 2px solid $cd-box;
                border-radius: 100rem;
                color: $cd-txt;
                font-family: 'Montserrat', sans-serif;
                font-size: 2.5rem;
                outline: none;
                padding: .5rem 1.5rem;
                width: 100%;
                transition: background-color 500ms;
                &:focus {
                    border: 2px solid $cd-txt;
                }
                &:not(:focus):invalid {
                    background-color: $cd-danger;
                    border: 2px solid $cd-danger;
                    color: $cd-txt--invalid;
                }
            }
        }
    }

## Modifiez les éléments voisins avec les pseudoclasses

Mais vous pouvez également utiliser les pseudoclasses pour changer le style d’autres éléments.

### Exemple

    <body>
        <div class="container">
            <div class="btn">
                C'est partiii!
            </div>
            <div class="ball"></div>
        </div>
    </body>

On peut utiliser le combinateur d’adjacence pour combiner la pseudoclasse :hover avec l’élément .ball à la place :

    .btn {
        background: $cd-primary;
        font-size: 3rem;
        cursor: pointer;
        padding: 1.85rem 3rem;
        border-radius: 10rem;
        &:hover + .ball{
            transform: scale(1.15);
        }
    }
    .ball {
        width: $ball-size;
        height: $ball-size;
        background: $cd-secondary;
        margin-bottom: 1rem;
        border-radius: $ball-size \* 0.5;
    }

Maintenant, c’est .ball qui va grossir lorsque l’utilisateur survolera le bouton avec sa souris.

# Créez des transitions CSS à propriétés multiples

    .btn {
        background-color: $cd-btn-start;
        border: 4px solid $cd-btn;
        border-radius: 10rem;
        cursor: pointer;
        font-size: 3rem;
        overflow: hidden;
        padding: 1.85rem 3rem;
        position: relative;
        transition: all 450ms;  // pour tenir compte de "transform" et de "background-color on utilise "all"
        &:hover {
        transform: scale(1.13); // sur la taille
        background-color: $cd-btn-end; // sur la couleur
        }
    }

mais il est des fois necessaire de separer les propriétés

    transition: transform 450ms, background-color 450ms;  // on separe par une "virgule"

## Retardez le début d'une transition

    transition-delay: 150ms; //retard de 150ms

s'il y a deux trasformations on peut choisir de retarder un seul par exemple

    transition: transform 450ms, background-color 300ms;
    transition-delay: 0, 150ms; // dans ce cas background-c commence 150ms apres transform !attention a l'ordre

on peut ecrir tout cela sur une meme ligne comme suit:

    transition: transform 450ms, background-color 300ms 150ms;

# Créez des animations plus naturelles avec les fonctions de timing

## Découvrez les principales fonctions de timing par défaut

### La fonction linear

    transition: transform 1000ms;
    transition-timing-function: linear;

qui peut s'ecrir comme suit:

    transition: transform 1000ms linear;

### Les fonctions ease-in-out, ease-in, ease-out et ease(par defaut)

### Allez à votre propre rythme avec la fonction cubic-bezier

    $trans-dur: 2000ms;
    transform: translateY(100%);
    transition: transform $trans-dur;

    .selector {
        /*(X1,Y1)(X2,Y2)*/
        transition-timing-function: cubic-bezier(.42, 0, .58, 1);
    }

Exemple sur une monté verticalement

    $trans-dur: 2000ms;
    .strength {
        transform: translateY(100%);
        transition: transform $trans-dur cubic-bezier(0, .75, .08, 1);
    }

# Créez des animations fluides avec la propriété CSS transform

## Modifiez la taille d'un élément avec scale

    .btn {
        &:hover + .box {
        transform: scale(3, 0.5);   // agrandissement de 300% sur X et 50% sur Y
        }
    }
    .box {
        transition: transform 330ms ease-in-out;
    }

Quand on veut modifier l’échelle dans une seule direction, on peut utiliser les fonctions scaleX() et scaleY()

## Modifiez la position d'un élément: La fonction "translate" modifie la position d'un élément

    .btn {
        &:hover + .box {
            transform: translate(150px, -7vh);
        }
    }

    .box {
        transition: transform 330ms ease-in-out;
    }

il est possible de déplacer des éléments sur l’axe X et Y séparément, grâce aux fonctions translateX() et translateY().

Exemple à etudier:

    .btn {
        &:hover + .box {
            transform: scale(1);
            span {
                transform: translateY(0);
            }
        }
    }
    .box {
        transform: scale(0.1);
        transition: transform 3000ms ease-in-out;
        overflow: hidden;
        span {
            display: inline-block;
            transform: translateY(100%);
            transition: transform 2800ms ease-out 500ms;
        }
    }

## Faites pivoter vos éléments avec rotate()

    <div class="container">
        <button class="btn">Transform!</button>
        <div class="boxes">
            <div class="boxes__base boxes--rotDegrees">rotate(360deg)</div>
            <div class="boxes__base boxes--rotTurns">rotate(1turn)</div>
        </div>
    </div>

    .btn {
        &:hover + .boxes {
            & > .boxes--rotDegrees {
                transform: rotate(0deg);
            }
            & > .boxes--rotTurns {
                transform: rotate(0turn);
            }
        }
    }

    .boxes {
        &--rotDegrees {
            transform: rotate(-360deg); //  -360deg == -1turn donc on a les memes effets
            transition: transform 500ms ease-in-out;
        }

        &--rotTurns {
            background: pink;
            transform: rotate(-1turn);
            transition: transform 500ms ease-in-out;
        }
    }

## Combinez les fonctions scale, position et rotate !

    .btn {
        &:hover + .box {
            transform: scale(1) rotate(0deg);
            span {
                transform: translateY(0);
            }
        }
    }

    .box {
        overflow: hidden;
        transform: scale(.1) rotate(-90deg);
        transition: transform 330ms ease-in-out;
        span {
            transform: translateY(250%);
            transition: transform 280ms ease-out 50ms;
            display: block;
        }
    }

L’utilisation de plusieurs fonctions a un bémol : l’ordre dans lequel on assigne les fonctions peut avoir un gros impact sur le résultat final. Il faut savoir que le navigateur effectue les calculs de chaque fonction dans l’ordre, de droite à gauche.

Ici, l'ordre selon lequel vous effectuez la rotation et le changement d’échelle ne va pas poser de problème. En effet, les deux n’ont pas d’effet l’un sur l’autre. Une rotation de 90 degrés suivie d’un agrandissement de 200 % aura le même effet qu’un agrandissement de 200 % suivi d’une rotation de 90 degrés.

Pour scale et translate, en revanche, c’est très différent. Si on déplace un élément de 200 % avant de l’agrandir à 200 %, cela aura un résultat très différent par rapport au fait de l’agrandir avant de le déplacer :

    .btn {
        &:active + .box {
            & > .box__base--tranxScale {
                transform: translateX(200%) scale(2);
            }
            & > .box__base--scaleTranx {
                transform: scale(2) translateX(200%);
            }
        }
    }

    .box {
        &__base {
            &--tranxScale {
                background-color: #15dea5;
                transition: transform 330ms ease-in-out;
            }
            &--scaleTranx {
                background-color: pink;
                transition: transform 330ms ease-in-out;
            }
        }
    }

## la fonction skew()

    .box {
        &--skewX {
            transform: skewX(45deg);
        }
        &--skewY {
            transform: skewY(45deg);
        }
        &--skew {
            transform: skew(45deg, 45deg);
        }
    }

## Modifiez le point d’ancrage d’un élément grâce à transform-origin

### Déplacez le centre

transform-origin(X Y) en % : deplace le point d'ancrage

ATTENTION  on ne le met pas dans :active

On peut ecrire: transform-origin(left 50%) unité possible (left rigth top bottom)

transform-origin en 3D:

sur l'axe Z on doit obligatoirement utiliser des unités par de % 

exemple d'unité: px, cm, vw(7.5 exemple)

# Animez les couleurs de manière performante avec opacity

### exemple

    <button class="btn">
        Survole moi!
    </button>

    $border-rad: 2rem;
    $clr-btn: #15DEA5;
    .btn {
        border-radius: $border-rad;
        background-color: $clr-btn;
        position: relative;
        z-index: 1;
        &:hover {
            &::after {
                opacity: 1;
            }
        }
        &::after {
            content: "";
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
            background-color: darken($clr-btn, 5);
            opacity: 0;
            z-index: -1;
            transition: opacity 250ms;
        }
    }


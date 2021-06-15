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
&\_\_group {
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

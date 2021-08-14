## Declarer une variable

    let nomVar = valeur;

## Declarer une constante

    const nomConstante : valeur;

## Type d'une variable

    number, string et boolean

## Les chaines de caracteres

Pour declarer on utilise des guillemets simples ou doubles " ou '

### exemple

    let firstName = "will" ou 'will';

### concatenation

    let nomPrenom = firstName + " " + lastName;  // valeur: "will Alexandre"

### string interpolation

Pour créer une string interpolation on écrit du texte encadrée par le signe ` et si on veut injecter une variable dans ce code on utilise l’expression ${maVariable}.

     const myName = `Alexander`;
     const salutation = `Bienvenue sur mon site ${myName}!`;
     console.log(salutation);   //retournera “Bienvenue sur mon site Alexander!” 

# Définissez des objets et leurs attributs avec des classes

## Découvrez les objets

#### Exemple

    let myBook = {
        title: 'The Story of Tau',
        author: 'Will Alexander',
        numberOfPages: 250,
        isAvailable: true
    };

### Accédez aux données d'un objet

Deux façons pour acceder aux données

#### notation pontée (dot notation)

    let bookTitle = myBook.title;  // "L'Histoire de Tao"
    let bookPages = myBook.numberOfPages  // 250

#### notation braket (bracket notation)

    let bookTitle = myBook["title"];  // "L'Histoire de Tao"
    let bookPages = myBook["numberOfPages"];  // 250

L'intérêt ici c’est qu’on va pouvoir mettre entre bracket une variable qui contient en string le nom de la propriété que l’on souhaite atteindre. Par exemple :

    let propertyToAccess = "title"
    let bookTitle = myBook[propertyToAccess];  // "L'Histoire de Tao"

## Manipulez des classes

Une classe est un modele pour un objet qui s'ecrit comme suit:

    class Book {
        constructor(title, author, pages) {
            this.title = title;
            this.author = author;
            this.pages = pages;
        }
    }

Pour cette classe, nous souhaitons que chaque Book ait un titre, un auteur et un nombre de pages. Pour cela, vous utilisez ce qu'on appelle un constructor.

    Le  constructor d'une classe est la fonction qui est appelée quand on crée une nouvelle instance de cette classe avec le mot clé   new  .

    Pour attribuer le titre, l'auteur et le nombre de pages reçus à cette instance, utilisez le mot clé   this  et la notation dot.
    Ici, le mot clé   this  fait référence à la nouvelle instance.

Maintenant que la classe est terminée, vous pouvez créer des instances par le mot clé new :

#### Exemple

    let myBook = new Book("L'Histoire de Tao", "Will Alexander", 250);
    Cette ligne crée l'objet suivant :
    {
        title: "L'Histoire de Tao",
        author: "Will Alexander",
        pages: 250
    }

# Regroupez vos données avec les tableaux et les objets

Pour créer un tableau

    let guests = []; //Tableau vide
    let guests = ["Sarah Kate", "Audrey Simon", "Will Alexander"]; //Tableau rempli

Pour acceder aux valeurs d'un tableau

    let firstGuest = guests[0]; // "Sarah Kate"
    let thirdGuest = guests[2]; // "Will Alexander"
    let undefinedGuest = guests[12] // undefined

### Le comptge d'elements

    let howManyGuests = guests.length; // 3

### L'ajout et la suppression d'éléments

- Pour ajouter votre element sur un tableau

1. A la fin du tableau
   guests.push("Tao Perkington"); // ajoute "Tao Perkington" à la fin de notre tableau guests
2. Au debut du tableau
   guests.unshift("Tao Perkington"); // "Tao Perkington" est ajouté au début du tableau guests

- Pour supprimer le dernier element sur un tableau
  guests.pop(); // supprimer le dernier élément du tableau

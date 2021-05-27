<meta charset="UTF-8">
# Memento de HTML
voici un petit condens� de balises html

# Balises de premier niveau

Les balises de premier niveau sont les principales balises qui structurent une page HTML. Elles sont indispensables pour r�aliser le � code minimal � d'une page web.

### Balise	Description

'<'html'>'	Balise pricipale 

'<'head'>'	En-tete de la page

'<'body'>'	Corps de la page

Code minimal d'une page HTML:

	<!DOCTYPE html>
		<html>
    		<head>
        		<meta charset="utf-8" />
        		<title>Titre</title>
    		</head>

    		<body>
    
    		</body>
		</html>

## Balises d'en-t�te

Ces balises sont toutes situ�es dans l'en-t�te de la page web, c'est-�-dire entre 	<head>  et 	</head>  :

### balise		Description

	<link/>		Liaison avec une feuille de style

	<meta/>		M�tadonn�es de la page web (charset, mots-cl�s, etc.)

	<script>	Code JavaScript

	<style>		Code CSS

	<title>		Titre de la page

## Balises de structuration du texte

### balise		#### Description

	<abbr>		Abreviation

	<blockquote>	Citation(longue)

	<cite>		Citation du titre d'une oeuvre ou d'un evenement

	<q>		Citation (courte)

	<sub>		indice

	<Strong>	Mise en valeur forte

	<em>		Mise en valeur normal

	<mark>		Mise en valeur visuelle

	<h1>		Titre de niveau 1

	<h2>		titre de niveau 2

	<h3>		Titre de niveau 3

	<h4>		Titre de niveau 4

	<h5>		Titre de niveau 5

	<h6>		Titre de niveau 6

	<img />		image

	<figure>	Figure (image, code, etc.)

	<figcaption>	Description de la figure

	<audio>		Son

	<video>		Vid�o

	<source>	Format source pour les balises <audio>

	<a>		Lien hypertexte

	<br />		Retour � la ligne

	<p>		Paragraphe

	<hr />		Ligne de separation horizontale

	<address>	Adresse de contact

	<del>		Texte supprim�

	<ins>		Texte ins�r�

	<dfn>		Definition

	<kbd>		Saisie clavier

	<pre>		Affichage format� (pour les codes sources)

	<progress>	Barre de progression

	<time>		Date ou heure

## Balises de listes

cette section �num�re toutes les balises HTML permettant de cr�er des listes (listes � puces, listes numerot�es, listes de d�finitions...)

### Balise		### Description

	<ul>		liste � puces, non num�rot�e

	<ol>		liste num�rot�z

	<li>		�l�ment de la liste � puces

	<dl>		Terme � d�finir

	<dd>		D�finition du terme

## Balises de tableau

### Balise		### Description

	<table>		Tableau

	<caption>	tire du tableau

	<tr>		Ligne de tableau

	<th>		Cellule d'en-tete

	<td>		Cellule

	<thead>		Section de l'en-tete du Tableau

	<tbody>		Section du pied du tableau

	<tfoot>		Section du pied du tableau


## Balise de formulaire

### Balise		### Description

	<form>		Formulaire

	<fieldset>	Groupe de champs

	<legend>	Titre d'un groupe de champs

	<label>		Libell� d'un champ

	<input />	Champ de formulaire (texte, mot de passe, case � cocher, bouton, etc.)

	<textarea>	Zone de saisie multiligne

	<select>	Liste d�roulante

	<option>	�l�ment d'une liste d�roulante

	<optgroup>	Groupe d'�l�ments d'une liste d�roulante

## Balises sectionnantes

Ces balises permettent de construire le squelette de notre site web.

### Balise		### Description

	<header>	En-t�te

	<nav>		Liens principaux de navigation

	<footer>	Pied de page

	<section>	Section de page

	<article>	Article (contenu autonome)

	<aside>		Informations compl�mentaires

## Balises g�n�riques

Les balises g�n�riques sont des balises qui n'ont pas de sens s�mantique.

En effet, toutes les autres balises HTML ont un sens : '<'p'>'  signifie � paragraphe �, '<'h2'>'  signifie � sous-titre �, etc.
Parfois, on a besoin d'utiliser des balises g�n�riques (aussi appel�es *balises universelles*) car aucune des autres balises ne convient. On utilise le plus souvent des balises g�n�riques pour construire son design.

Il y a deux balises g�n�riques : l'une est inline, l'autre est block.

### Balise		### Description

	<span>		Balise g�n�rique de type inline

	<div>		Balise g�n�rique de type block

Ces balises ont un int�r�t uniquement si vous leur associez un attribut	class  , 	id  ou 	style  :

* class  : indique le nom de la classe CSS � utiliser.

* id  : donne un nom � la balise. Ce nom doit �tre unique sur toute la page car il permet d'identifier la balise. Vous pouvez vous servir de l'ID pour de nombreuses choses, par exemple pour cr�er un lien vers une ancre, pour un style CSS de type ID, pour des manipulations en JavaScript, etc.

* style  : cet attribut vous permet d'indiquer directement le code CSS � appliquer. Vous n'�tes donc pas oblig� d'avoir une feuille de style � part, vous pouvez mettre directement les attributs CSS. Notez qu'il est pr�f�rable de ne pas utiliser cet attribut et de passer � la place par une feuille de style externe, car cela rend votre site plus facile � mettre � jour par la suite.

Ces trois attributs ne sont pas r�serv�s aux balises g�n�riques : vous pouvez aussi les utiliser sans aucun probl�me dans la plupart des autres balises.


	

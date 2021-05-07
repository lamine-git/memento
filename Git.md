## Quelques definition
### Qu'est-ce qu’un gestionnaire de versions ?
	Un gestionnaire de versions est un programme qui permet aux développeurs de conserver un historique des modifications et des versions de tous leurs fichiers.
	L’action de contrôler les versions est aussi appelée "versioning" en anglais, vous pourrez entendre les deux termes.
Le gestionnaire de versions permet de garder en mémoire :
* chaque modification de chaque fichier ;
* pourquoi elle a eu lieu ;
* et par qui 
## Git ou GitHub ? Quelle est la différence ?
Git et GitHub sont deux choses différentes.
Git est un gestionnaire de versions. Vous l’utiliserez pour créer un dépôt local et gérer les versions de vos fichiers.
GitHub est un service en ligne qui va héberger votre dépôt. Dans ce cas, on parle de dépôt distant puisqu’il n’est pas stocké sur votre machine.
## Travaillez à partir d’un nouveau projet
### Créer un neveau repository en ligne de commande
	echo "# exemple" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git branch -M main
	git remote add origin https://github.com/lamine-git/exemple.git
	git push -u origin main
## Accédez à un dépôt distant OC
### pousser (push) d'un repository existant en ligne de commande
	git remote add origin https://github.com/lamine-git/exemple.git
	git branch -M main
	git push -u origin main

### Modifiez le message du dernier commit poussé:
	git commit --amend -m "New commit message."
### Forcer push pour mettre à jour l'historique du référentiel distant:
	git push --force branch-name



### Créer un neveau repositorie en ligne de commande
	echo "# exemple" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git branch -M main
	git remote add origin https://github.com/lamine-git/exemple.git
	git push -u origin main
### or push an existing repository from the command line
	git remote add origin https://github.com/lamine-git/exemple.git
	git branch -M main
	git push -u origin main

...Modifiez le message du dernier commit poussé:
git commit --amend -m "New commit message."

...Forcer push pour mettre à jour l'historique du référentiel distant:
git push --force branch-name



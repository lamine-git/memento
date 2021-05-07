## Quelques definition
### Qu'est-ce qu�un gestionnaire de versions ?
	Un gestionnaire de versions est un programme qui permet aux d�veloppeurs de conserver un historique des modifications et des versions de tous leurs fichiers.
	L�action de contr�ler les versions est aussi appel�e "versioning" en anglais, vous pourrez entendre les deux termes.
Le gestionnaire de versions permet de garder en m�moire :
* chaque modification de chaque fichier ;
* pourquoi elle a eu lieu ;
* et par qui 
## Git ou GitHub ? Quelle est la diff�rence ?
Git et GitHub sont deux choses diff�rentes.
Git est un gestionnaire de versions. Vous l�utiliserez pour cr�er un d�p�t local et g�rer les versions de vos fichiers.
GitHub est un service en ligne qui va h�berger votre d�p�t. Dans ce cas, on parle de d�p�t distant puisqu�il n�est pas stock� sur votre machine.
## Travaillez � partir d�un nouveau projet
### Cr�er un neveau repository en ligne de commande
	echo "# exemple" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git branch -M main
	git remote add origin https://github.com/lamine-git/exemple.git
	git push -u origin main
## Acc�dez � un d�p�t distant OC
### pousser (push) d'un repository existant en ligne de commande
	git remote add origin https://github.com/lamine-git/exemple.git
	git branch -M main
	git push -u origin main

### Modifiez le message du dernier commit pouss�:
	git commit --amend -m "New commit message."
### Forcer push pour mettre � jour l'historique du r�f�rentiel distant:
	git push --force branch-name



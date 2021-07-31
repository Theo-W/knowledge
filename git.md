# Git

## Rappel

Ne pas oublier: l'aide en ligne de commande

```shell
git help config
git help push
git help pull
git help branch
```

List des glabals
`git config --list`

## Setup git
- `git config --global user.name Isox-z`
- `git config --global user.username isox`
- `git config --global user.signingkey ...........`
- `git config --global user.email theo.meunier41@gmail.com`
- `git config --global commit.gpgsign true`
- `git config --global commit.autocrlf true`


## Créer un projet

- Créer le repo distant sur github
- Créer un dossier pour le projet`mkdir <nom_du_projet>`
- Initialiser git`git init`
- Créer le premier commit `git add .` puis `git commit -m "Initial commit"`
- Ajouter le repo distant`git remote add origin git@github.com:theomeunier/project.git`
- Le push sur le repo distant `git push -u origin master`

## Récupérer un projet
```shell
git clone .....git chemin/vers/mon_dossier
```

## Les branches

### Crée une branche
```shell
# Si la branch est local et n'est pas créée sur le repo distant
git branch -d nom_de_ma_branch_local

# Si la branch est présente sur le repo distant
git push origin --delete nom_de_ma_branch_distante
```

### Supprimer une branche

- Si la branche est local et n'est pas créée sur le dépot distant
```shell
git checkout -d npm_de_la_branche_local
```

- Si la branche est présente sur le dépot distant
```shell
git push origin --delete nom_de_la_braznhce_distante
```

### Changer de branche
```shell
git checkout npm_de _la_branchee
```

## Les commits, les pulls, les pushs et les supprésions

### les commits
- Faire un commit `git add .` et `git commit -m "Mon message"` 
- Annuler le dernier commit et modifs `git reset --hard md5_commit` ou `git push --force`

### Les pulls
- Mettre à jour le dépot local `git pull`
- Mettre à jour sur une branche spécifique `git pull origin MA_BRANCHE`

### les pushs
- Envoyer ses commits vers le dépot distant `git push`
- Envoyer ses commits vers le dépot distant sur une branche spécifique `git push origine MA_BRANCHE`

### Les supprésions
- Supprimer un fichier du répertoire de travail et de l'index `git rm nom_du_fichier`
- Supprimer un fichier de l'index `git rmg --cached nom_du_fichier`

## Annuler un commit

Seul le commit est retiré de Git mais les fichiers reste modifier.
### Annuler commits (soft)
```shell
git reset HAED^
```
Pour indiquer à quel commit on souhaite revenir, il existe plusieurs notations: 

- `HEAD`: dernier commit
- `HEAD^`: avant-dernier commit
- `HEAD^^`: avant-avant-dernier commit
- `HEAD~2`: avant-avant-dernier commit
- indiquer le numéro du commit

### Annuler les commits (hard)
Si vous voulez annuler votre dernier commit et les changements effectués dans les fichiers, il faut faire un reset hard.
Cela annulera sans confirmation tout votre travail 

- Annuler les commits et perdre tous les changements
```shell
git reset --hard HEAD^
```
- Annuler les commits et perdre tous les changements
```shell
git reset --hard HEAD^
```
- Annuler les commits et perdre tous les changements
```shell
git reset --hard HEAD^
```

## Changer le nom du dernier commit
```shell
git commit --amend
```
La commande ci-dessus charge le dernier message dans l'éditeur.
- modifier message
- Enregistrer et quitter l'éditeur afin de perdre les modifs en compte

## Ajouter des fichier au dernier commit
```shell
git add mon_fichier
git commit --amend
```

## Logs
- Le classique `git log`
- Afficher X derniers commits `git log -n X`
- Afficher les commit concernant un dossier `git log --oneline -- chemain/vers/mon_dossier`
- Afficher un ensemble de commits par date `git log --since=date --until=date`
- Représentation de l'historique à partir de HEAD (commit / branch) `git log --oneline --graph --decorate`
- Représentation de l'historique à partir d'un fichier (commit / branch) `git log --oneline --graph --decorate nom_dossier`

## Tag

### Retourne la liste des tags disponible 
```shell
git tag
#ou 
git tag -l
git tag --list
```

### Crée un tag
- Crée un tag `git tag -a v1.0 -m "Mon commentaire pour la version 1.0"`
- Crée un tag sur un commit antérieur `git tag -a v1.0 -m "Mon commentaire pour la version 1.0 md5_commit`

### Vérifier un tag en affichant les informations
```shell
git tag -v nom_de_l_étiquette
```

### Pousser les tags sur la branch distante
```shell
git push origin non_de_l_étiquette

#Pousser plusieurs tags sur la branch
git push origin --tags
```

# Git

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

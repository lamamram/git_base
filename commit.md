# création de commit

## trois zones

1. copie de travail
2. index (staging area)
3. dépôt (dossier .git)

## étapes 

1. modifier les fics
2. ajouter des fichiers à l'index
3. valider les modifs de l'index dans le dépôt

## procédure

1. `git status [-s]`
  - voir le delta entre le dépôt et la copie de travail
  - voir les fichiers dans l'index

2. `git add <paths> | . | -A | -i:` ajout à l'index
  - -i interactif si trop de fichiers à ajouter à la main
  - -p: pour ajouter des "hunks" i.e des modification atomiques dans le fichier

3. `git commit [-a] [-m "msg"]`: valider les modifs comme commit
  - -a ajout auto des fichiers à l'état M
  - -m message obligatoire pour créer le commit
  - git config --global core.editor notepad sur windows pour gérer
    les message demande un éditeur par défaut si -m omis

## alias usuels

* ```
  git config --global alias.st status
  git config --global alias.ci commit
  git config --global alias.co checkout
  ```

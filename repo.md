## initialisation d'un dépôt

* `git init`: mais avant cette commande on peut spécifier le nom de la brache par défaut.

  - `git config --global init.defaultBranch`
    > pour windows > 2.28

* `git config [--local|--global]:` ajout des meta utilisateurs ou config de base
* `git config --global core.editor notepad`

* `git config --global alias.st status`: pour fabriquer un raccourcis **git st**

## les commandes d'introspection

### les git diff

* `git diff`: index -> copie de travail
* `git diff --cached`: HEAD -> index
* `git diff <rev>`: commit -> copie de travail
* `git diff <rev1> <rev2>`: entre commits


## utilisation du stash:

   * stash complet avec les fichier "Untracked": `git stash -u`
   * si le `stash pop` cause un conflit en rasion de la mauvaise branche 
   => le stash est gardé !!
   * l'état de conflit peut être enlevé sur le fichier avec `git restore --staged <fic>`
     => on doit réparer également les données : `gco -- <fic>`
   * on peut stasher avec un nom indiquant la branche : `git stash push -m "name_of_the_stash"`
     => on peut uniquement l'utilser qu'avec `git stash apply`

## git tag
  1. création (annoté)
  2. voir git show
  3. pousser
  4. mettre à jour
  5. supprimer
  6. archiver
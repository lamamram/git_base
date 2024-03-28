# Commandes d'inversion

## inversion dans la copie de travail

1. `git checkout -- <paths>`: écrase la copie de travail pour un ou plusieurs fichiers en paramètres d'après l'état dans le commit pointé par HEAD
  - `git checkout <rev> | HEAD~n -- <paths>`: même chose d'après l'état d'un commit plus ancien (ATTENTION le fichier arrive dans l'index !!)

2. `git rm [-r] <paths>`: supprime le fichier de la copie de travail et place dans l'index un ordre de suppression pour le prochain commit
  - effet: le fichier n'apparait plus dans l'arbre des commits du dépôt
  - cependant on peut le retrouver dans un ou des commits anciens
  - `git rm --cached <paths>`: demande de suppression du dépôt mais conservation dans la copie de travail

3. `git mv` : renommage dans le dépôt
   - si on veut restaurer un état d'un commit précédent le renommage, on utilise l'ancien nom

4. `git reset -- <paths>`: désindexation de fichiers

5. `git reset <rev> | HEAD~n [--soft | --mixed | --hard]`: 
   - déplacement de HEAD sur le commit pointé
   - suppression de l'historique des commits devant le nouveau HEAD
   - conservation ou écrasement de la copie de travail et de l'index

   - |option   | copie    | index
     |---------|----------|------
     | soft    | conservée|conservé
     | mixed   | conservée| vidé
   
   > on ne reset pas un commit déjà poussé sur une branche commune !!!
   > réécriture d'historique
   > si c'est le cas, le push suivant ne passe pas
   > ne pas faire de pull, préférer restaurer le ou les commits disparus depuis le reflog via un reset


6. `git revert <rev> | HEAD~n`: crée un nouveau commit qui inverse les modifications du commit pointé
  - --no-edit pour laisser un message auto pour le nouveau commit
  - --no-commit se contente d'inverser les modifs dans la copie, charge au dev de terminer avec de possible modifs supplémentaire + commit
  - annuler un commit de fusion : `git revert <rev> | HEAD~n -m 1`: recrée l'état avant le commit de fusion, du point de vue de la branche de réception (ligne n° 1).
    REM: à partir du revert le merge est considéré comme consommé donc il faut reverter le revert
    REM2: on en revertant le revert on voit le message "Reaplly: commit"

  * REM: 
    + reset est un verbe intransitif en "git" donc on reset VERS un commit
      Donc: tous les commits précédents sont supprimés de l'historique.
    + revert      //     transitif      //    donc on revert le commit et lui seul
      Donc: si les modifications inversées étaient les fondements d'autres modifications dans d'autres commit plus récents => nous verrons des conflits !!!

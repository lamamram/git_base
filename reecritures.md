## réécritures de l'historique

### commit --amend

* si l'on se rend compte d'un contenu lacunaire et/ou d'un nom inapproprié
  lié à un unique commit
  => on peut corriger ces pbs de cohérence avec commit --amend 

* sachant qu'un commit demande un message on peut ajouter l'option --no-edit si le message précédent est statisfaisant

### le rebasage

* principe: créer une fiction historique en modifiant le commit de base d'une branche
* mise en oeuvre: les modification de chaque commit de la branche à rebaser doivent être recalculés avec les modifications des commits précédents le nouveau commit de base compris et suivants l'ancien commit de base. 

#### exécution simple
* contrairement au merge il faut se positionner sur la branche qui va se déplacer
  et appeler la branche dont le commit de bout par défaut va être le nouveau commit de base
* condenser plusieurs en un seul commit parce qu'ils constituent une évolution cohérente

#### rebasage automatisé
* `git rebase -i`
* on l'utilise sur une branche qu'on veut resculpter
* on utilise l'éditeur par défaut qui va lister les commit qu'on veut changer dans la 
branche courante
* mes actions possibles:
  1. ne rien changer
  2. supprimer le commit (violent)
  3. changer le nom d'un commit
  4. éditer complètement un commit
  5. squasher
  6. éditer et squasher
  7. autres avancés comme x (lancer un shell, ...) 

### squash

* condenser plusieurs en un seul commit parce qu'ils constituent une évolution cohérent
# Git Tips
*S'il est facile d'utiliser les fonctionnalités basiques de Git, le maitrise est un tout autre défi. J'ai ainsi décidé de regrouper l'ensemble des commandes un peu plus poussées / rares / utiles que j'ai trouvé au fil des années.*


## Ajouter un fichier/répertoire à votre `.gitignore` après coup
### Le problème
Vous synchronisez le répertoire `dist/` depuis le début de votre projet, jusqu'à ce jour où vous réalisez que c'est inutile. Vous l'ajoutez alors au `.gitignore`, mais ce dernier reste présent dans votre repo en ligne.

### La solution
- Purger le cache : `git rm -r --cached dist/`
- Ajouter la modification : `git add .`
- Commiter : `git commit -m "git: Gitignore updated"`
- Pusher : `git push`

Le répertoire en question ne devrait plus être tracké et avoir disparu du répo.


## Restaurer un fichier/répertoire précis à l'état d'un commit
### Le problème
Vous avez effectué des modifications importantes dans le répertoire `assets/css/` de votre projet. Ces modifications ont été l'objet d'un commit, lui-même suivi de deux autres commits (du plus récent au plus ancien)
- `d2a99e4: Amazing feature #2`
- `6cc7313: Amazing feature #1`
- `5f8a6b8: Huge CSS refactor`
- `c6e3f90: My horse is amazing`
- ...

Malheureusement, vous réalisez que le refactor du CSS est plutôt néfaste... C'est pourquoi vous voulez récupérer l'état de ce répertoire **avant** modification, tout en conservant les commits suivants (les deux "amazing feature").

### La solution
Bonne nouvelle, il est tout à fait possible d'effectuer un "rollback" sur un fichier/répertoire précis à un état (commit) donné.
- Commande : `git checkout <commitID> -- path/to/dir/`
- Dans notre cas : `git checkout c6e3f90 -- assets/css/`

Ô joie, seul le répertoire contenant le CSS a été rollbacké alors que tout le reste du projet conserve son avancée.

## Tools
 - [**Git Cheatsheet**](http://rogerdudler.github.io/git-guide/index.html) --> The git basics on your wall.
 - [**GitIgnore.io**](https://www.gitignore.io/) :uk: --> Create `.gitignore`. for specific OS, IDE, language.
 - [**Try Github**](https://try.github.io) :uk: --> Learn Git basics with interactive challenges.

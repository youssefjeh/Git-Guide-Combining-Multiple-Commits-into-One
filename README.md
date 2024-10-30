# Git: Guide Combining Multiple Commits into One

Dans certains cas, il peut être utile de combiner plusieurs commits en un seul pour simplifier l'historique des modifications. Voici comment faire cela avec `git reset --mixed`.

## Étapes pour Combiner des Commits

1. **Vérifiez l'historique des commits :** Identifiez le commit précédent à ceux que vous voulez combiner. Ce commit sera votre point de référence. Utilisez cette commande pour voir les derniers commits et copier le hash du commit cible :
   
  ```bash
   git log --oneline
  ```
Par exemple :

  ```sql
  abc1234 Mon premier commit
  def5678 Mon deuxième commit
  ghi9012 Mon troisième commit
  ```
Si vous souhaitez combiner les commits def5678 et ghi9012, votre cible sera abc1234.

2. Réinitialisez avec --mixed jusqu'au commit cible : Cette commande va annuler les commits suivants tout en conservant les modifications dans l'espace de travail.

  ```bash
   git reset --mixed <hash_du_commit_cible>
  ```

Par exemple :

  ```bash
  git reset --mixed abc1234
  ```

3. Stagez tous les changements pour un nouveau commit : Après le reset, toutes les modifications sont dans votre espace de travail. Stagez-les à nouveau pour préparer un nouveau commit unique.

  ``` bash
git add .
  ```
4. Créez un nouveau commit unique : Ce commit va inclure tous les changements des commits précédents.

  ```bash
git commit -m "Votre message de commit combiné"
  ```

5. Push des modifications : Si vous avez déjà poussé les commits que vous venez de combiner, vous devrez effectuer un push forcé pour écraser l’historique distant.

  ```bash
git push origin <nom_de_branche> --force
  ```
⚠️ Attention : Utiliser --force peut écraser l'historique sur le dépôt distant, ce qui pourrait affecter les autres collaborateurs. Assurez-vous que cette opération est appropriée pour votre flux de travail.

## Exemple Complet
  ```bash
# Afficher les commits récents
git log --oneline

# Réinitialiser au commit cible
git reset --mixed abc1234

# Stager les changements pour un commit unique
git add .

# Créer le commit combiné
git commit -m "Combinaison de plusieurs commits en un seul"

# Pousser avec --force si nécessaire
git push origin main --force
  ```



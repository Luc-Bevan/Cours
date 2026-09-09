# README

Ce vault contient mes notes de cours, réorganisées et corrigées à partir de mes prises de notes manuscrites. Il est partagé pour que tu puisses t'en servir comme base ou comme complément à tes propres notes.

## Comment le vault est organisé

- **[année universitaire]** (ex : 2026-2027) : un dossier par année.
  - **R[n]** : un dossier par semestre, avec un sous-dossier par unité d'enseignement (UE).
  - **SAE[n]** : dossier(s) pour les situations d'apprentissage et d'évaluation du semestre correspondant.
- **Compétences** : suivi des compétences visées par la formation.
- **Contacts Profs & Admin** : coordonnées utiles (enseignants, administration).
- **Lesson Tree** : vue d'ensemble / plan de tous les cours, pratique pour naviguer rapidement.
- **Reminder** : deadlines et choses à ne pas oublier.

Le contenu s'enrichit en continu au fil des semestres : ce README décrit juste la logique de rangement, pas la liste exacte de ce qui est disponible à un instant donné.

### Une remarque sur la fiabilité des notes

Certaines notes ont été reconstruites ou corrigées à partir de prises de notes manuscrites rapides, donc pas mot pour mot ce qui a été dit en cours. Quand une note contient une section **"Points à vérifier avec le support de cours original"**, ça signifie qu'un passage a été supposé, complété ou corrigé sans certitude à 100 % : mieux vaut recroiser ces points-là avec les slides ou le prof avant de s'en servir pour réviser un exam.

---

## Récupérer et utiliser ce vault

### 1. Installer Obsidian

Télécharger et installer Obsidian depuis [obsidian.md](https://obsidian.md) (Windows, macOS, Linux).

### 2. Installer le plugin Obsidian Git

1. Dans Obsidian : **Paramètres > Community plugins**.
2. Désactiver le "Restricted mode" si besoin.
3. Cliquer sur **Browse**, chercher **Obsidian Git**, l'installer puis l'activer.

Ce plugin permet à Obsidian de récupérer les mises à jour du vault directement depuis l'interface, sans passer par un terminal au quotidien.

### 3. Récupérer le vault

Prérequis : avoir Git installé ([git-scm.com](https://git-scm.com)).

Dans un terminal :

```
git clone [URL_DU_REPO]
```

Puis dans Obsidian : **Open folder as vault**, et sélectionner le dossier qui vient d'être cloné.

### 4. Recevoir les mises à jour automatiquement

Dans les paramètres du plugin **Obsidian Git** :

- Activer **"Auto Pull interval (minutes)"** et régler un intervalle (par exemple 15 ou 30 minutes) : les nouvelles notes ou corrections seront récupérées automatiquement.
- Activer aussi **"Pull on startup"** pour être à jour dès l'ouverture d'Obsidian.
- Laisser les options d'auto-commit / auto-push désactivées : ce vault est en lecture pour toi, pas besoin de pousser quoi que ce soit dessus (voir la section suivante si tu veux signaler quelque chose).

Une fois configuré, tu n'as plus rien à faire : à chaque mise à jour du vault d'origine, tes notes se mettent à jour toutes seules.

### 5. Signaler une erreur ou proposer une correction

- Pour signaler une erreur, une coquille, ou demander l'ajout d'un cours manquant : ouvrir une **Issue** sur la page du dépôt (`[URL_DU_REPO]/issues`), en décrivant le problème.
- Pour proposer directement une correction : faire un fork (voir ci-dessous), modifier le fichier concerné, puis ouvrir une **Pull Request**. La modification sera relue avant d'être intégrée.

### 6. Te faire ta propre copie personnalisable

Si tu veux réorganiser, annoter ou modifier librement les notes de ton côté, sans attendre de validation et sans risquer de casser le vault d'origine :

1. Sur la page du dépôt, cliquer sur **Fork** : ça crée une copie complète sous ton propre compte.
2. Cloner ce fork localement (`git clone [URL_DU_FORK]`) et l'ouvrir comme vault dans Obsidian, comme à l'étape 3.
3. Ce fork est indépendant : tu peux y modifier, réorganiser ou supprimer des notes librement.
4. Pour que ton fork se garde automatiquement à jour avec le dépôt d'origine (sans devoir taper de commandes à chaque fois), ajouter un workflow GitHub Actions qui fait la synchronisation à ta place. Dans ton fork, créer le fichier `.github/workflows/sync.yml` avec ce contenu :

   ```yaml
   name: Sync fork with upstream

   on:
     schedule:
       - cron: "0 * * * *"   # toutes les heures, à ajuster selon le besoin
     workflow_dispatch:        # permet aussi de le lancer manuellement depuis GitHub

   permissions:
     contents: write

   jobs:
     sync:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
           with:
             fetch-depth: 0

         - name: Ajouter le dépôt d'origine comme remote
           run: git remote add upstream [URL_DU_REPO]

         - name: Récupérer les changements du dépôt d'origine
           run: git fetch upstream

         - name: Fusionner dans la branche principale
           run: |
             git checkout main
             git merge upstream/main --no-edit

         - name: Pousser les changements sur le fork
           run: git push origin main
   ```

   Adapter `main` si la branche principale du dépôt s'appelle autrement (par exemple `master`). Une fois ce fichier ajouté et poussé sur ton fork, GitHub exécutera automatiquement la synchronisation selon le planning défini (ici toutes les heures), sans aucune action de ta part. Combiné avec l'auto-pull d'Obsidian Git configuré à l'étape 4 de la section précédente, tes notes se mettent à jour toutes seules à la fois côté GitHub et côté Obsidian.

### Si tu ne veux pas utiliser Git du tout

Télécharger le dépôt en ZIP (bouton **Code > Download ZIP** sur la page du dépôt) et ouvrir le dossier extrait comme vault dans Obsidian. Dans ce cas, aucune mise à jour automatique : il faudra retélécharger le ZIP manuellement à chaque fois que tu veux les dernières notes.

### À savoir sur la synchronisation automatique du fork

Si tu modifies aussi des notes de ton côté, la fusion automatique (`git merge upstream/main`) peut échouer en cas de conflit sur un fichier modifié à la fois par toi et par le dépôt d'origine : dans ce cas, le workflow GitHub Actions s'arrêtera en erreur sur cette synchronisation-là, et il faudra résoudre le conflit manuellement (localement, avec les mêmes commandes `git fetch upstream` / `git merge upstream/main`, en choisissant quoi garder) avant que la synchronisation automatique reprenne normalement.
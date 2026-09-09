---
aliases:
  - Cours 1.1.1
---

# Linux - Gestion de fichiers, utilisateurs et droits d'accès

## 1. Commandes de base sur fichiers et répertoires

| Commande                   | Effet                                                                         |
| -------------------------- | ----------------------------------------------------------------------------- |
| `ls -a`                    | Liste les fichiers d'un répertoire, y compris les fichiers cachés             |
| `cp [ancien] [nouveau]`    | Copie un fichier                                                              |
| `cp -r [ancien] [nouveau]` | Copie récursive (pour copier un répertoire entier avec son contenu)           |
| `mv [ancien] [nouveau]`    | Déplace ou renomme un fichier/répertoire                                      |
| `rm [fichier]`             | Supprime un fichier                                                           |
| `rm -r [répertoire]`       | Supprime un répertoire de façon récursive (même non vide)                     |
| `touch [fichier]`          | Crée un fichier vide (ou met à jour sa date de modification s'il existe déjà) |
| `mkdir [répertoire]`       | Crée un répertoire                                                            |
| `rmdir [répertoire]`       | Supprime un répertoire, mais uniquement s'il est vide                         |

## 2. Caractères spéciaux (jokers / wildcards)

| Motif | Signification |
|---|---|
| `*` | N'importe quelle chaîne de caractères (y compris vide) |
| `?` | Un caractère unique quelconque |
| `[abc]` | Un caractère parmi a, b ou c |
| `[c-j]` | Un caractère dans la plage donnée (de c à j) |
| `[!0-9]` | Tous les caractères sauf ceux compris dans la plage indiquée |
| `{mot1,mot2,mot3}` | Prend chaque élément de l'ensemble, un par un (d'abord mot1, puis mot2, puis mot3) |
| `{1..4}` | Spécifie une plage d'éléments allant de 1 à 4 |

Correction : l'énumération de mots (`mot1,mot2,mot3`) et la plage (`1..4`) utilisent toutes les deux des **accolades** `{}`, pas des crochets `[]`. Les crochets `[...]` servent à faire correspondre un seul caractère parmi un ensemble (comme `[abc]` ou `[c-j]`), alors que les accolades `{...}` servent à l'expansion de motifs, souvent utilisée à la création de fichiers (exemple : `mkdir dossier{1..4}` crée `dossier1`, `dossier2`, `dossier3`, `dossier4`).

La logique reste la même que tu l'avais notée : `[c-j]` sert à filtrer parmi des fichiers déjà existants, alors que `{1..4}` sert plutôt à générer des noms lors d'une création.

## 3. La commande find

Syntaxe générale :

```
find [répertoire] [critère] [action]
```

| Élément | Rôle |
|---|---|
| `-print` | Affiche les résultats trouvés (comportement par défaut si aucune action n'est précisée) |
| `-exec cmd {} \;` | Exécute la commande `cmd` sur chaque résultat trouvé. Les accolades `{}` sont remplacées par le fichier trouvé, et le `\;` termine la commande |
| `-ok cmd {} \;` | Même effet que `-exec`, mais demande une confirmation à l'utilisateur avant chaque exécution |

Exemple :
```
find ~ -name "*.pdf" -exec ls -l {} \;
```
Affiche les informations détaillées sur tous les fichiers dont le nom comporte l'extension `.pdf` dans le répertoire personnel de l'utilisateur.

Correction : il manquait les accolades `{}` (qui représentent le fichier trouvé) et le `\;` final, qui est obligatoire pour terminer une action `-exec` ou `-ok`. Sans ces éléments, la commande ne fonctionne pas.

### Opérateurs logiques pour combiner des critères

| Opérateur | Signification |
|---|---|
| `-a` | ET logique (par défaut entre deux critères) |
| `-o` | OU logique |
| `!` | NON logique |
| `\( ... \)` | Parenthèses, pour grouper des critères (à échapper avec `\` dans le shell) |

## 4. Utilisateurs et groupes

Un utilisateur possède :
- un numéro d'utilisateur unique (**uid**)
- une appartenance à un ou plusieurs groupes (avec un groupe principal identifié par un **gid**)
- un répertoire personnel

Chaque fichier ou répertoire possède un unique propriétaire.

| Commande | Effet |
|---|---|
| `id user_login` | Donne l'uid de l'utilisateur ainsi que la liste des groupes auxquels il appartient |
| `su user_login` | Ouvre une session en tant que `user_login` |
| `su -` | Ouvre une session en tant qu'administrateur du système (root), avec l'environnement complet de root |

### Les 3 types d'utilisateurs concernant un fichier

- Le propriétaire (**user**)
- Le groupe (**group**)
- Les autres (**other**)

## 5. Droits d'accès aux fichiers

À chaque fichier sont associés des droits pour chacun des 3 types d'utilisateurs ci-dessus :

- lecture (**read**, r)
- écriture (**write**, w)
- exécution (**execute**, x)

Les droits d'accès sont codés sur **9 bits** (visibles avec la commande `ls -l`), répartis ainsi :

```
rwx        rwx         rwx
(user)   (group)     (other)
```

### Conversion en octal

Chaque groupe de 3 bits se convertit en un chiffre octal (0 à 7) :

| Droits | Binaire | Octal |
|---|---|---|
| rwx | 111 | 7 |
| r-x | 101 | 5 |
| --- | 000 | 0 |

Exemple : `rwxr-x---` = `111 101 000` = `7 5 0` = **750**

## 6. umask

`umask code_octal` définit les droits attribués par défaut lors de la création d'un fichier ou d'un répertoire.

Droits maximaux par défaut avant application du umask :
- Fichiers : 666 (jamais exécutable par défaut, pour éviter qu'un fichier créé devienne automatiquement un programme exécutable)
- Répertoires : 777

Formule de calcul des droits finaux :

```
droits_finaux = droits_par_défaut  ET(bit à bit)  NON(umask)
```

Exemple avec `umask 022` :
- Fichiers : `666 ET NON(022)` = **644**
- Répertoires : `777 ET NON(022)` = **755**

Correction : la formule initiale était inversée (elle indiquait `NOT(666)`, alors que c'est le umask qui doit être inversé, pas la valeur par défaut). Autre point à préciser : la valeur de départ n'est pas toujours 666, elle dépend du type d'élément créé (666 pour un fichier, 777 pour un répertoire).

## 7. Changer propriétaire et groupe

| Commande | Effet |
|---|---|
| `chown [user] [liste-fichiers]` | Change le propriétaire des fichiers listés |
| `chown [user:group] [liste-fichiers]` | Change à la fois le propriétaire et le groupe propriétaire |
| `chown -R [user:group] [liste-fichiers]` | Même effet, mais appliqué récursivement à un répertoire et son contenu |
| `chgrp groupe [liste-fichiers]` | Change uniquement le groupe propriétaire des fichiers listés |

Correction : la syntaxe `user.group` (avec un point) fonctionne sur certains systèmes mais la forme standard et recommandée est `user:group` (avec deux points). Autre correction : le flag récursif de `chown` s'écrit avec un **R majuscule** (`-R`), contrairement à `cp -r` ou `rm -r` qui utilisent un r minuscule.

## Points à vérifier avec le support de cours original

- Vérifier la syntaxe exacte utilisée en cours pour `chown` (point ou deux-points)
- Confirmer si le cours mentionne d'autres critères de `find` (par type, taille, date de modification, etc.)
- Vérifier si d'autres exemples de umask ont été donnés en cours
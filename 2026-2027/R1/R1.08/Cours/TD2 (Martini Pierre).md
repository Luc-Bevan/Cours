---
aliases:
  - Cours 1.1.1
---
*TD1 à rattraper
![[TD2.pdf]]

# TD - Commandes shell, historique et VirtualBox Guest Additions

## 1. Enregistrer une session de terminal avec script

| Commande | Effet |
|---|---|
| `script test` | Démarre l'enregistrement de tout ce qui se passe dans le terminal, dans un fichier nommé `test` |
| `exit` | Arrête l'enregistrement démarré par `script` et sauvegarde le contenu dans le fichier |

Important : tout ce qui est tapé (et affiché) entre le `script test` et le `exit` correspondant est enregistré dans le fichier `test`. C'est ce mécanisme qui doit être utilisé pour garder une trace de la suite du TD2.

Astuce de sélection dans le terminal : cliquer à l'endroit de départ du texte à sélectionner, puis Maj + clic (Shift + clic) à l'endroit de fin, pour sélectionner toute la zone entre les deux d'un coup (utile pour copier le contenu affiché dans le terminal).

## 2. Historique des commandes

| Commande | Effet |
|---|---|
| `history` | Affiche la liste des commandes précédemment tapées, chacune avec un numéro d'ordre |
| `Ctrl + r` | Lance une recherche incrémentale dans l'historique : on tape une partie du nom d'une commande passée et le terminal propose la plus récente correspondance |
| `!n` | Relance directement la commande n° `n` de l'historique (n étant le numéro affiché par `history`) |

Correction : la notation correcte est `!n` (point d'exclamation suivi du numéro), sans crochets. Exemple : `!42` relance la commande numéro 42 de l'historique.

Note : `Ctrl+R` et `history` ne font pas exactement la même chose : `history` affiche toute la liste d'un coup, alors que `Ctrl+R` permet de chercher une commande précise en tapant un mot-clé, sans avoir à parcourir toute la liste.

## 3. Commandes de base à tester

| Commande | Effet |
|---|---|
| `id` | Affiche l'uid de l'utilisateur courant et ses groupes |
| `pwd` | Affiche le répertoire courant (print working directory) |
| `cd -` | Retourne dans le répertoire précédent (celui où on était avant le dernier `cd`) |
| `ls` | Liste le contenu du répertoire courant |
| `ls -l` | Liste le contenu du répertoire avec les détails (droits, propriétaire, taille, date...) |
| `exit` | Quitte le terminal ou la session en cours (ou arrête l'enregistrement `script`, voir section 1) |

## 4. Suite du TD

*(faire le reste du TD2)*

## 5. Navigation et création de fichiers

| Commande | Effet |
|---|---|
| `pwd` | Affiche le répertoire courant |
| `cd /tmp/` | Se déplace dans le répertoire `/tmp` |
| `cd /root/` | Se déplace dans le répertoire `/root` (nécessite généralement les droits root) |
| `touch td1.txt` | Crée un fichier vide nommé `td1.txt` |

## 6. Installation de paquets et des VirtualBox Guest Additions

| Commande | Effet |
|---|---|
| `sudo apt update && sudo apt install bzip2 tar` | Met à jour la liste des paquets puis installe `bzip2` et `tar`, nécessaires pour décompresser certaines archives (souvent utilisé en préparation de l'installation des Guest Additions) |
| `sudo ./VBoxLinuxAdditions.run` | Lance l'installation des VirtualBox Guest Additions dans la VM (permet le partage de dossiers, le presse-papiers partagé, une meilleure résolution d'écran, etc.) |

Point à vérifier : selon la distribution utilisée, l'installation des Guest Additions peut aussi nécessiter les paquets `build-essential`, `dkms` et `linux-headers-$(uname -r)` en plus de `bzip2` et `tar`, pour pouvoir compiler les modules noyau. À confirmer avec les instructions exactes du TD.

Concernant "Windows + T + W + E pour activer coller avec le milieu" : cette instruction n'est pas claire dans les notes de départ (elle mélange une combinaison façon raccourci Windows avec un comportement de collage habituellement lié à X11/Linux, le "clic du milieu" qui colle la dernière sélection). À revoir avec le support du TD pour connaître le contexte exact (menu VirtualBox, paramètres système, ou autre).

## 7. Créer une arborescence de répertoires

| Commande | Effet |
|---|---|
| `mkdir -p ~/r1.06/TD ~/r1.06/TP/Correction` | Crée toute l'arborescence en une fois : `~/r1.06/TD` et `~/r1.06/TP/Correction`, en créant automatiquement les répertoires parents manquants (`-p`) |

Sans l'option `-p`, `mkdir` renverrait une erreur si le répertoire parent (`~/r1.06`) n'existe pas encore.

## 8. Obtenir de l'aide sur une commande

| Commande | Effet |
|---|---|
| `[commande] --help` | Affiche l'aide résumée de la commande concernée (options disponibles, syntaxe) |

## Points à vérifier avec le support de cours original

- Contexte exact de l'instruction sur le collage avec le clic du milieu (section 6)
- Paquets supplémentaires éventuellement nécessaires pour les VirtualBox Guest Additions selon la distribution utilisée
- Contenu précis du "reste du TD2" à compléter
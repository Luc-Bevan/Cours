---
aliases:
  - Cours 1.1.1
---
![[TD1.pdf]]**Commandes utilisées:**
# Configuration d'une VM Linux (GNOME) et extensions Shell

## 1. Commandes de base et mise à jour du système

| Commande | Effet |
|---|---|
| `ip a` | Affiche les interfaces réseau et leurs adresses IP |
| `clear` | Efface l'écran du terminal |
| `id` | Affiche l'uid de l'utilisateur courant ainsi que les groupes auxquels il appartient |
| `sudo apt update` | Met à jour la liste des paquets disponibles (index des dépôts) |
| `sudo apt upgrade` | Met à jour les paquets déjà installés vers leur dernière version disponible |
| `sudo apt install gnome-shell-extension-manager gnome-tweaks` | Installe le gestionnaire d'extensions GNOME Shell et l'outil de réglages avancés GNOME Tweaks |

Rappel utile : `apt update` doit être exécuté avant `apt upgrade` (et avant tout `apt install`), sinon le système risque d'installer des versions obsolètes puisque l'index des paquets n'est pas à jour.

## 2. Partage de dossier avec la machine hôte (VirtualBox)

| Commande | Effet |
|---|---|
| `sudo mkdir /mnt/VMShare` | Crée le point de montage dans la VM Linux, dans lequel le dossier partagé sera monté |
| `sudo mount -t vboxsf VMShare /mnt/VMShare` | Monte le dossier partagé VirtualBox nommé `VMShare` (défini côté hôte) dans le répertoire créé juste avant |

Correction : le chemin `c:\VMShare` était une syntaxe Windows, invalide sous Linux (les chemins Linux utilisent `/` et non `\`, et il n'y a pas de lettre de lecteur comme `c:`). Le point de montage doit être un chemin Linux classique, par exemple `/mnt/VMShare` ou `/media/VMShare`.

Autre point : le nom `VMShare` utilisé dans la commande `mount` doit correspondre exactement au nom du dossier partagé configuré dans les paramètres de VirtualBox (Paramètres de la VM -> Dossiers partagés), et le second `VMShare` de la commande `mount` doit correspondre au dossier créé par `mkdir` juste avant (donc bien penser à utiliser le même chemin dans les deux commandes).

## 3. Installer des extensions GNOME Shell

1. Ouvrir l'application **Extension Manager** (chercher "manager" ou "extensions" dans les activités/le menu des applications — c'est l'application avec une icône en forme de pièce de puzzle).
2. Aller dans l'onglet **Parcourir** (Browse).
3. Rechercher et installer les extensions suivantes :

| Extension | Auteur |
|---|---|
| Hide Activities Button | zeten30 |
| ddterm | amezin |
| Dash to Dock | michele_g |
| Apps Menu | fmuellner |
| Panel Scroll | sun_wang |
| Extension List | gnome-shell-extensions.gitlab.io ou grroot (à vérifier selon la source) |

Note pour ddterm (amezin) : si l'extension ne fonctionne pas directement après installation, vérifier sa page officielle sur GitHub ou sur extensions.gnome.org pour des instructions de dépannage spécifiques (dépendances manquantes, version de GNOME Shell incompatible, etc.).

## Points à vérifier avec le support de cours original

- Confirmer le chemin exact utilisé pour le point de montage (`/mnt/VMShare` proposé ici à titre d'exemple standard)
![[TP2.pdf]]

1) La commande ```ls *```  ser à lister tous ce qui se trouve dans le répertoire courant, elle fais la meme chose que simplement ```ls``` .
2) En faisant ```ls /usr/include/s*``` .
3) commande: ```ls /usr/include/[abc]*.h```
4) commande: ```ls /usr/include/???.h```
5) commande: ```cp /usr/include/a*.h ~```
6) commande: ```rm ~/r1.06/TP/*.h```
7) commande: ```ls /usr/include/????.*```
8) commande: ```cp -r /usr/include/[aci]*.* ~/r1.06/TP/```
9) commande: ```cp /usr/include/std*.h ~/r1.06/TP/```
10) commande: ```touch -r ~/r1.06/TP/tp1/1{a..d}.txt```
11) Une erreur, car mon dossier TP contient des choses, il faudrait faire ```rmdir -r TP```
12) commande: ```rm -r ~/r1.06/TP/*```
13) commande: ```rmdir ~/r1.06/TP/```
14) La commande ```touch ∼/a{1..3}{d..g}.txt``` sert à créer les fichier dans le répertoire personnels qui commencent par a, suivit de soit 1,2 ou 3, puis un des charactère entre d et g suivit de .txt , tout en testant les combinaisons dans l'ordre.
15) commande: ```find /usr/include/std*.h ```
16) commande:  ```find /usr/include/std*.h -exec ls -l {} \;```
17) commande:  ```find /usr/include/std*.h -exec cp {} ~r1.06/TD/ \;```
18) commande:  ```find ~/ -type d -exec ls -l {} \;```
19) commande: ```find / -type f -size 0c -daystart -mtime 0```
20) commande: ```find ~ -type f -not -newer ~/test```
21)  commande: ```find ~ -type f -daystart -mtime 1 -size +1k```
22) y'en a un qui vérifie prend que les extensions .txt et pas l'autre.

| Commande           | Utilité                                                                           |
| :----------------- | :-------------------------------------------------------------------------------- |
| `apt update`       | Met à jour la liste des paquets disponibles depuis les dépôts.                    |
| `apt upgrade`      | Met à jour les paquets installés vers leurs dernières versions disponibles.       |
| `apt-cache search` | Recherche un paquet à partir d’un mot-clé.                                        |
| `apt-cache show`   | Affiche les informations détaillées d’un paquet.                                  |
| `apt install`      | Installe un paquet et ses dépendances.                                            |
| `apt autoremove`   | Supprime les paquets devenus inutiles.                                            |
| `apt remove`       | Désinstalle un paquet, sans supprimer généralement ses fichiers de configuration. |
| `apt autoclean`    | Supprime du cache les anciens paquets `.deb` qui ne sont plus nécessaires.        |
| `apt clean`        | Supprime tous les paquets `.deb` présents dans le cache local.                    |

23-26) déjà fais.
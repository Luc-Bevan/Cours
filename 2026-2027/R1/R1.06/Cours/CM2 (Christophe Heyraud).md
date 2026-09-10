# R1.06 - Notions de base sur les microcontrôleurs.
Différence microcontrôleur et microprocesseur:
un microprocesseur ne contient que l'unité de calcul (le cerveau), tandis qu'un microcontrôleur réunit sur une seule et même puce le processeur, la mémoire et les entrées/sorties les trois sortes de mémoire sont contenues elles dans le microcontroleur.
Bus = technologie de réseau, au minimum deux fils (comme usb qui possede deux fils pour l'alim, et deux pour la communication).
petite info comme ça: les clés usb sont juste des composants en dérivation (puisqu'ils sont en parallèle néanmoins il ne doivent pas communiquer en meme synchronisation).

## 1 Problmatique
De plus en plus de systèmes embarqué nécessitent des systèes de gestion dits intelligents et programmables. Le composant électroniue ayant cette fonction est appellé microcontroleur (ou microprocesseur). Ils est présent sur une carte électronique.
## 2 Charactéristique d'un microcontroleur
![[Pasted image 20260910085317.png|642]]
Pour la suite du cours nous allons partir sur la carte arduino uno et son microcontroleur ATMEGA3288P de la société ATMEL
ce composant comporte 32 pattes
chacune de ces pattes peut avoir une ou plusieurs fonctions
certaines sont attribuées à des ports d'entrées/sorties
d'autres sont connecté à un quartz créant le signal d'horloge
d'autres permettent des fonctions appelées sinusoidales 
Certaines permettent également la communication
deux types de capteurs: analogiques ou TOR (tout ou rien = numérique, 0 ou 1)
on parle de périphérique d'entré d'entré ou de sortie lorsqu'il y a une majorité d'informations dans un sens meme si il y en a quelques unes dans un autre.

## 3 Structure d'un microcontroleur
## 4 Langage de programation
## 5 Environnement de développement integre arduino
## 6 Annexe
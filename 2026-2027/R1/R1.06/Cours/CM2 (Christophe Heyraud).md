# R1.06 - Notions de base sur les microcontrôleurs.
Différence microcontrôleur et microprocesseur:
un microprocesseur ne contient que l'unité de calcul (le cerveau), tandis qu'un microcontrôleur réunit sur une seule et même puce le processeur, la mémoire et les entrées/sorties les trois sortes de mémoire sont contenues elles dans le microcontrôleur.
Bus = technologie de réseau, au minimum deux fils (comme USB qui possède deux fils pour l'alim, et deux pour la communication).
petite info comme ça: les clés USB sont juste des composants en dérivation (puisqu'ils sont en parallèle néanmoins il ne doivent pas communiquer en même synchronisation).

## 1 Problématique
De plus en plus de systèmes embarqué nécessitent des systèmes de gestion dits intelligents et programmables. Le composant électronique ayant cette fonction est appelés microcontrôleur (ou microprocesseur). Ils est présent sur une carte électronique.
## 2 Caractéristique d'un microcontrôleur
![[Pasted image 20260910085317.png|642]]
Pour la suite du cours nous allons partir sur la carte Arduino uno et son microcontroleur ATMEGA3288P de la société ATMEL
ce composant comporte 32 pattes
chacune de ces pattes peut avoir une ou plusieurs fonctions
certaines sont attribuées à des ports d'entrées/sorties
d'autres sont connecté à un quartz créant le signal d'horloge
d'autres permettent des fonctions appelées sinusoïdales 
Certaines permettent également la communication
deux types de capteurs: analogiques ou TOR (tout ou rien = digital/numérique, 0 ou 1)
on parle de périphérique d'entré d'entré ou de sortie lorsqu'il y a une majorité d'informations dans un sens même si il y en a quelques unes dans un autre.

## 3 Structure d'un microcontrôleur
## 4 Langage de programmation
## 5 Environnement de développement intégré Arduino
## 6 Annexe
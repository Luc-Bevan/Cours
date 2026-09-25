---
aliases:
  - CM1.1.1
---

# R1.06 - Notions de base sur les microcontrôleurs

## Différence microcontrôleur / microprocesseur

> [!note]
> Un **microprocesseur** ne contient que l'unité de calcul (le "cerveau"), tandis qu'un **microcontrôleur** réunit sur une seule et même puce :
> - Le processeur
> - La mémoire
> - Les entrées / sorties
>
> Les trois types de mémoire sont donc contenus dans le microcontrôleur.

**Bus** = technologie de réseau, au minimum deux fils (ex : l'USB possède deux fils pour l'alimentation et deux pour la communication).

> [!tip] Info complémentaire
> Les clés USB sont de simples composants **en dérivation** (en parallèle) — néanmoins, elles ne doivent pas communiquer en même synchronisation.

---

## 1. Problématique

De plus en plus de systèmes embarqués nécessitent des systèmes de gestion dits **intelligents et programmables**. Le composant électronique ayant cette fonction est appelé **microcontrôleur** (parfois aussi désigné, par abus de langage, "microprocesseur"). Il est présent sur une carte électronique.

---

## 2. Caractéristiques d'un microcontrôleur

![[Pasted image 20260910085317.png|439]]

Pour la suite du cours, nous allons partir sur la carte **Arduino Uno** et son microcontrôleur **ATmega328P** de la société **Atmel**.

> [!warning]
> Tes notes indiquaient "ATMEGA3288P" — le microcontrôleur de l'Arduino Uno est bien l'**ATmega328P**. Corrige si besoin selon ce qu'a dit le prof.

Ce composant comporte **32 pattes** (broches).

Chacune de ces pattes peut avoir **une ou plusieurs fonctions** :
- Certaines sont attribuées à des ports d'**entrées/sorties**
- D'autres sont connectées à un **quartz**, créant le signal d'horloge
- D'autres permettent des fonctions appelées **sinusoïdales**
- Certaines permettent également la **communication**

### Types de capteurs
- **Analogiques**
- **TOR** (Tout Ou Rien = digital / numérique, 0 ou 1)

> [!info]
> On parle de périphérique d'**entrée** ou de **sortie** lorsqu'il y a une majorité d'informations circulant dans un sens, même s'il y en a quelques-unes dans l'autre.

!Attention! l'entrée d'un microprocesseur ne dois jamais être câblé en l'air. Il faut une résistance de PullDown (ou Pullup)
---

## 3. Structure d'un microcontrôleur

![[Pasted image 20260916161350.png|700]]

Flash Program Memory = Mémoire FLASH Programme: 32kBytes.
Program Counter = Compteur de programme.
Data SRAM = Mémoire RAM : 2kBytes
Mémoire EEPROM 64 octets: Erasable programmable read only memory =
memoire morte( lecture seule).
Status and Control = Registre d'etat: certains bits changent d'état dans certaines conditions.
Watchdog TIMER : En cas de crash, il possède un timer, qui quand arrive  0, relance la carte.
pour eviter qu'il arrive à 0 il est nécessairre d'en mettre les instructions dans ton code.
attention 225+1 = 0 dans un processeur, il est donc nécessaire d'avoir une retenues, et c'est las que viens le registre d'etat, qui sert au calcul quand il y a une retenue. un bit carry.
car 255 = 11111111 et 1 = 00000001.
il y a un truc qui fais positif négatif, je sais plus trop 127 pour aller en négatif par e.
ALU = Unité Arithmétique et Logique.
==**ATTENTION :** un Byte = un octet = 8 bit.==


Le cross sais décoder (RISK) 35 instructions simples. Certaines ne font rien
(exemple 00 0001 0xxx xxxx)
x signifie que cela peut être 0 ou 1 cela n'aura pas d'importance.
NOP = une instruction qui ne fais rien (no opération) et pourtant elle perd un cycle d'horloge, elle sert à différer quelque chose.

![[PIC16F84A.pdf]]

---
1
Il ne sais pas calculer plusieurs chiffres en même temps, mais il les fait très rapidement, ex:
il ne fais pas 1+ 2 + 3, il fais 1 + 2 = 3 ; 3 + 3 = 6.

![[Pasted image 20260916175126.png]]
PSI = Port SPI.
USART 0 = Port Série.
Convertisseur analogique numérique A/D, numérique analogique
TImer tempo 8 bit TX2  16bit TX
Chien de garde (watchdog)

## 4. Langage de programmation

Langage machine, code en binaire utilisé directement par la machine.
§ Attention les codes des machines ne sont pas fixes.
quand un code est rentré dans une puce, il n'est pas envoyé en binaire mais en hexadécimal ( c'est pour ça que les codes en bits sont séparés par 4)car2^4 = 16.
LSb et MSb à définir.
C -> langage binaire -> langage machine

UAL et ALU connaitre les deux termes et définitions unité arithmétique et logique, calculatrice basique en gros.
Calcul de deux nombres par 2.

port : i2c 2pin pour pour l'alim, un pin pour l'horloge et un pin pour le data
 = def d'un bus.
 Le timer définie le nombre de "places", il se décrémente (pas compris)
 !attention gigaoctet(1000 octets) differrent de gibyoctet (1024 octets)
 
 La mémoire programme est stockée dans une mémoire Flash. Celle -ci peut êre Reprogrammée 10000 fois, La mémoire est de 32kBytes instructions.
 Le compteur de programme est un registre contenant l'addresse de l'instruction suivante à executer.
 La mémoire RAMest constituée de 2k octest. Cette mémoire contient des registres permettant de configurer les ports d'entrées/sorties. Le registre d'état, etc...
 Cettte mémoire s'efface lors d'un coupure de l'alimentation.
 La mémoire EEPROM est constituée de 64 octet. C'est une mémoire ROM Effaçablle électrquemet. Celle -ci permet de stocker des données.
 Le registre d'état est un registre contenant l'état d'une opération ( résultat nul, avec retenue,...)
 Le timer est un élément permettant de générer un signal ou une interruption lorsqu'une réselection est atteinte. on s'en sert pour du comptage ou des temporisations.
 L'ALU: unité arithmétique et logique est l'élément qui comme son nom l'indique Permet d'effectuer les calculs arithmétiques (addition, soustraction) et logique ( ou, et, ...)
 Le chien de garde(watchdog) est un dispositif servant à contrôler le bon fonctionnement d'un programme. S'il est activé, il permet, en cas de plantage du prgramme de réinitialiser automatiquement le miicrocontroler
 L'entrée Quartz permet d''accueillir le signal d'horloge nécessaire au fonctionnement du microcontrôleur.
 On connecte sur ce pattes, un quartz, composant permettant de générer un signal d'horloge de très grande précision +/-20 ppm (ppm = part per million) cela signifie que l'erreur est de 1.7s par jour ou 10 minutes par an.
 Il existe différents langages de programmation. Par défaut, le seul langage compréhensible par le comoposant est le langage machine: il est constitué d'une suite de 0 et de 1


---

## 5. Environnement de développement intégré Arduino

*(à compléter)*

---

## 6. Annexe

*(à compléter)*

---

## À retenir
- [ ] Différence microcontrôleur vs microprocesseur
- [ ] Rôle du quartz (signal d'horloge)
- [ ] Capteurs analogiques vs TOR
- [ ] Nombre de pattes de l'ATmega328P et leurs fonctions

#arduino #microcontroleur #atmega328p
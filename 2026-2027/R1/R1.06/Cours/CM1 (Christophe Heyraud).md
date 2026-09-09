---
tags:
---

# Architecture des systèmes numériques

## Architecture de base d'un ordinateur

> [!note] Définition
> Une architecture à **x bit** = le nombre de bits qu'un microprocesseur peut traiter à la fois.

Un PC est **modulaire**.

### Composants de base d'un PC
- Le boîtier
- La carte mère
- Le processeur
- Les barrettes mémoires
- Le disque dur
- Les cartes réseaux
- La carte graphique

> [!info] PC = Personal Computer
> Le premier PC à base de **microprocesseur 8086 d'Intel** a été conçu par **IBM** en **1981**.

**Caractéristiques :**
- 256 kO de RAM
- 2 disques 5"
- Pas de disque dur
- Fréquence 2,5 MHz
- Mode turbo 3 MHz

Un **boîtier** est relié à des **constituants annexes** et des **périphériques**.

---

## 1. Tensions et signaux logiques

Les processeurs tels qu'Intel tournent autour de **3,3 V**.

Pour le calculer : $P = \dfrac{V^2}{R}$

> [!tip] Économie d'énergie
> En passant de 5 V à 3,3 V, on divise par **2,5** la puissance absorbée par le processeur → moins de chauffe. C'est ce qu'on appelle la technologie **TTL**.

Cela concerne la distinction entre un niveau "1" et un niveau "0" :
- **1** logique → entre **2,7 V** et **3,3 V**
- **0** logique → entre **0 V** et **0,6 V**
- Entre 0,6 V et 2,7 V → il n'y a normalement rien : c'est la **zone interdite**

> [!warning] Zone interdite
> Quand un "bruit" / parasite apparaît dans cette zone interdite, il y a une chance égale d'obtenir un 0 ou un 1. C'est ce genre d'erreur qui entraîne l'**écran bleu** ("écran de la mort").

Les perturbations peuvent être très fréquentes car les opérations sont nombreuses ; de plus, **plus une fréquence est haute, plus elle crée des interférences**.

Certaines fréquences peuvent altérer les processeurs — ce sont des bruits pouvant aller jusqu'à endommager une machine.

---

## 2. Le boîtier

Le boîtier est la partie **visible** du PC. Il sert à protéger les éléments internes des agressions extérieures :
- Chocs
- Poussière
- Champs électromagnétiques

Ce boîtier contient :
- Un bloc d'alimentation
- Une carte mère, sur laquelle se trouvent les composants électroniques

**Formats courants :** ATX et micro-ATX

> [!note] Refroidissement
> Comme tous les éléments chauffent, un refroidissement du boîtier est nécessaire. Le fabricant prévoit un refroidissement par **convection**. Certains composants (alimentation, microprocesseur…) chauffent davantage : des **ventilateurs** aident au refroidissement.

---

## 3. La carte mère

*Exemple : Asus P6T*

### Connecteurs présents
- Connecteur clavier / souris
- Connecteur USB 2.0
- Connecteur FireWire et SATA on the go
- Socket
- Connecteur mémoire RAM
- Connecteur d'alimentation
- Port SATA
- Connecteurs boîtier
- Connecteur disquette
- Connecteur réseau Gigabit
- Connecteur audio analogique
- Connecteur PCI
- 3 connecteurs PCIe 2.0 x16

> [!tip] Pâte thermique
> Son utilité est d'améliorer la **surface de contact** : il ne faut pas d'air, car c'est l'un des meilleurs isolants — ce qui n'est absolument pas recherché dans cette situation.

> [!important] Rôle de la carte mère
> La carte mère est le **système nerveux** du PC : c'est sur elle que sont connectés tous les éléments du PC.

Son choix est primordial pour faire évoluer sa configuration à moindre coût. Une bonne carte mère permet également de profiter au maximum de ses périphériques, qui ne seront pas limités.

### Structure d'une carte mère
![[Pasted image 20260909174110.png|530]]

---

## 4. Les processeurs

Les processeurs sont fabriqués à partir de **silice**, trouvée dans le sable. Cela nécessite beaucoup de traitement, car il faut une bonne finesse (les Taïwanais sont les meilleurs pour cela).

> [!note] Transistor
> Un **transistor** = un interrupteur électronique.

Un processeur peut communiquer de deux manières :
- **Analogique** (0 à 1)
- **Numérique** (0 ou 1)

### Technologies CISC vs RISC

| Technologie | Signification | Caractéristiques |
|---|---|---|
| **CISC** | Complex Instruction Set Computing | Beaucoup d'instructions, au détriment de la surface de la puce |
| **RISC** | Reduced Instruction Set Computing | Une cinquantaine d'instructions, plus petits, moins performants |

- Un microprocesseur intègre plusieurs **millions de transistors** (gravure à 3 nm) et de la **mémoire cache** (mémoire ultra rapide).
- Fréquence d'horloge de plusieurs **GHz** → calculs très rapides, effectués sur **32 ou 64 bits** selon le modèle.
- En raison des pertes Joule, le CPU est refroidi par un **ventilateur** (ou **watercooling**).
- Les processeurs grand public sont de type **CISC**.

> [!example] RISC et IoT
> Les microprocesseurs RISC équipent des équipements embarqués ou des objets connectés → c'est l'**Internet des Objets (IoT)**.

---

## À retenir
- [ ] Différence entre architecture 32/64/84 bits
- [ ] Fonctionnement de la zone interdite (0,6 V – 2,7 V)
- [ ] Formats de boîtier ATX / micro-ATX
- [ ] Différence CISC vs RISC
- [ ] Rôle de la pâte thermique

#architecture #hardware #processeur #carte-mère
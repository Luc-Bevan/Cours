---
aliases:
  - PERSO
---
# Les systèmes de numération : binaire, octal, décimal, hexadécimal

> **Niveau** : lycée (NSI), IUT, licence d'informatique, électronique numérique.
> **Contenu** : bases 2, 8, 10 et 16, conversions, nombres signés (positifs et négatifs), addition et soustraction dans chaque base.

---

## Sommaire

1. [Principe d'un système positionnel](#1-principe-dun-système-positionnel)
2. [Les quatre bases](#2-les-quatre-bases)
3. [Conversions entre bases](#3-conversions-entre-bases)
4. [Nombres fractionnaires](#4-nombres-fractionnaires)
5. [Nombres négatifs : représentation des entiers signés](#5-nombres-négatifs--représentation-des-entiers-signés)
6. [Addition](#6-addition)
7. [Soustraction](#7-soustraction)
8. [Retenue, dépassement et extension de signe](#8-retenue-dépassement-et-extension-de-signe)
9. [Exercices corrigés](#9-exercices-corrigés)
10. [Fiche de synthèse](#10-fiche-de-synthèse)

---

## 1. Principe d'un système positionnel

### 1.1 Idée générale

Dans un système de numération **positionnel** de **base** $b$ (avec $b \geq 2$), on utilise $b$ symboles appelés **chiffres**, de $0$ à $b - 1$. La valeur d'un chiffre dépend de sa **position** dans le nombre.

Un nombre entier s'écrit $(a_{n-1}\,a_{n-2} \dots a_1\,a_0)_b$ et sa valeur est :

$$N = \sum_{k=0}^{n-1} a_k \, b^k = a_{n-1}\,b^{n-1} + \dots + a_1\,b + a_0$$
s
avec $0 \leq a_k \leq b - 1$.

- $a_0$ est le chiffre de **poids faible** (le plus à droite).
- $a_{n-1}$ est le chiffre de **poids fort** (le plus à gauche).

**Exemple en décimal.** $(4096)_{10} = 4 \times 10^3 + 0 \times 10^2 + 9 \times 10^1 + 6 \times 10^0$.

### 1.2 Notations

Pour éviter les ambiguïtés (que vaut « 10 » ?), on précise la base :

| Base | Notation mathématique | Préfixe en programmation | Suffixe |
|---|---|---|---|
| 2 (binaire) | $(1011)_2$ | `0b1011` | `1011b` |
| 8 (octal) | $(13)_8$ | `0o13` ou `013` | `13o` |
| 10 (décimal) | $(11)_{10}$ | (aucun) | `11d` |
| 16 (hexadécimal) | $(B)_{16}$ | `0xB` | `Bh` |

Les quatre écritures ci-dessus désignent **le même nombre** (onze).
a
### 1.3 Vocabulaire

- **Bit** (*binary digit*) : un chiffre binaire, $0$ ou $1$.
- **Quartet** (*nibble*) : 4 bits. Il correspond à **un** chiffre hexadécimal.
- **Octet** (*byte*) : 8 bits, soit **deux** chiffres hexadécimaux.
- **MSB** (*Most Significant Bit*) : bit de poids fort. **LSB** : bit de poids faible.

### 1.4 Puissances à connaître

| $n$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| $2^n$ | 1 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 | 512 | 1024 | 2048 | 4096 | 65536 |

| $n$ | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| $8^n$ | 1 | 8 | 64 | 512 | 4096 |
| $16^n$ | 1 | 16 | 256 | 4096 | 65536 |

---

## 2. Les quatre bases

### 2.1 Chiffres utilisés

| Base | Chiffres |
|---|---|
| Binaire (2) | `0 1` |
| Octal (8) | `0 1 2 3 4 5 6 7` |
| Décimal (10) | `0 1 2 3 4 5 6 7 8 9` |
| Hexadécimal (16) | `0 1 2 3 4 5 6 7 8 9 A B C D E F` |

En hexadécimal : $A = 10$, $B = 11$, $C = 12$, $D = 13$, $E = 14$, $F = 15$.

### 2.2 Table de correspondance de 0 à 16

| Décimal | Binaire | Octal | Hexadécimal |
| ------- | ------- | ----- | ----------- |
| 0       | 0000    | 0     | 0           |
| 1       | 0001    | 1     | 1           |
| 2       | 0010    | 2     | 2           |
| 3       | 0011    | 3     | 3           |
| 4       | 0100    | 4     | 4           |
| 5       | 0101    | 5     | 5           |
| 6       | 0110    | 6     | 6           |
| 7       | 0111    | 7     | 7           |
| 8       | 1000    |       | 8           |
| 9       | 1001    |       | 9           |
|         | 1010    |       | A           |
|         | 1011    |       | B           |
|         | 1100    |       | C           |
|         | 1101    |       | D           |
|         | 1110    |       | E           |
|         | 1111    |       | F           |



**À retenir par cœur** : cette table (surtout les colonnes binaire et hexadécimal) sert dans presque tous les calculs.

### 2.3 Pourquoi l'octal et l'hexadécimal ?

Comme $8 = 2^3$ et $16 = 2^4$ :

- **1 chiffre octal = 3 bits** ;
- **1 chiffre hexadécimal = 4 bits**.

Ces deux bases sont donc des **écritures compactes du binaire**, faciles à convertir (voir 3.4). L'hexadécimal est omniprésent : adresses mémoire, couleurs web (`#FF8800`), codes de caractères, adresses MAC. L'octal reste utilisé pour les permissions Unix (`chmod 755`).

---

## 3. Conversions entre bases

### 3.1 Vers le décimal (somme des puissances)

On applique la formule $N = \sum a_k b^k$.

**Binaire → décimal.** $(11010110)_2$ :

| Position | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|---|
| Bit | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 |
| Poids | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

$N = 128 + 64 + 16 + 4 + 2 = 214$.

**Octal → décimal.** $(345)_8 = 3 \times 64 + 4 \times 8 + 5 = 192 + 32 + 5 = 229$.

**Hexadécimal → décimal.** $(2F3)_{16} = 2 \times 256 + 15 \times 16 + 3 = 512 + 240 + 3 = 755$.

**Méthode de Horner** (moins de multiplications) : on lit de gauche à droite en calculant $r \leftarrow r \times b + \text{chiffre}$.

$(2F3)_{16}$ : $2 \to 2 \times 16 + 15 = 47 \to 47 \times 16 + 3 = 755$. ✓

### 3.2 Depuis le décimal (divisions successives)

On divise le nombre par la base $b$ de façon répétée jusqu'à obtenir un quotient nul. Les **restes**, lus **de bas en haut** (le dernier reste est le chiffre de poids fort), donnent l'écriture.

**Décimal → binaire.** $214$ :

| Division | Quotient | Reste |
|---|---|---|
| $214 \div 2$ | 107 | **0** |
| $107 \div 2$ | 53 | **1** |
| $53 \div 2$ | 26 | **1** |
| $26 \div 2$ | 13 | **0** |
| $13 \div 2$ | 6 | **1** |
| $6 \div 2$ | 3 | **0** |
| $3 \div 2$ | 1 | **1** |
| $1 \div 2$ | 0 | **1** |

Lecture de bas en haut : $(214)_{10} = (11010110)_2$.

**Décimal → hexadécimal.** $755$ :

- $755 = 47 \times 16 + 3$ → reste $3$
- $47 = 2 \times 16 + 15$ → reste $15 = F$
- $2 = 0 \times 16 + 2$ → reste $2$

Lecture de bas en haut : $(755)_{10} = (2F3)_{16}$.

**Décimal → octal.** $229$ :

- $229 = 28 \times 8 + 5$
- $28 = 3 \times 8 + 4$
- $3 = 0 \times 8 + 3$

Donc $(229)_{10} = (345)_8$.

### 3.3 Méthode des soustractions de puissances (décimal → binaire)

On soustrait la plus grande puissance de 2 possible, puis on recommence avec le reste.

**Exemple.** $214$ : $214 - 128 = 86$ ; $86 - 64 = 22$ ; $22 - 16 = 6$ ; $6 - 4 = 2$ ; $2 - 2 = 0$.
Les puissances utilisées sont $128, 64, 16, 4, 2$, donc les bits $7, 6, 4, 2, 1$ valent $1$ :
$$11010110$$

### 3.4 Conversions rapides entre binaire, octal et hexadécimal

**Binaire → hexadécimal.** On groupe les bits **par 4 en partant de la droite** (on complète à gauche par des zéros), puis on remplace chaque groupe par son chiffre hexadécimal.

$$(1011\,0111\,1010)_2 \to (B\,7\,A)_{16} = (B7A)_{16}$$

**Hexadécimal → binaire.** On remplace chaque chiffre par ses 4 bits.

$$(2F3)_{16} \to 0010\;1111\;0011 \to (1011110011)_2 \text{ (zéros de tête supprimés)}$$

**Binaire → octal.** On groupe **par 3** en partant de la droite.

$$(11\,010\,110)_2 \to (3\,2\,6)_8 = (326)_8$$

Vérification : $3 \times 64 + 2 \times 8 + 6 = 214$ ✓.

**Octal → binaire.** Chaque chiffre octal devient 3 bits.

$$(345)_8 \to 011\;100\;101 \to (11100101)_2$$

**Octal ↔ hexadécimal.** On passe **toujours par le binaire**.

$$(345)_8 = 011\,100\,101_2 = 0\,1110\,0101_2 = (E5)_{16}$$

Vérification : $14 \times 16 + 5 = 229$ ✓.

### 3.5 Schéma récapitulatif

```
        ┌─────────── groupes de 3 bits ───────────┐
  Octal ◄──────────►  BINAIRE  ◄──────────► Hexadécimal
                         ▲                (groupes de 4 bits)
                         │
        divisions /      │      somme des
        soustractions    ▼      puissances
                     DÉCIMAL
```

Pour passer d'une base quelconque à une autre : **base 2 ou 8 ou 16 → binaire → 8 ou 16**, ou bien **via le décimal**.

---

## 4. Nombres fractionnaires

### 4.1 Écriture positionnelle

Après la virgule, les poids sont des puissances **négatives** de la base :

$$(a_{n-1} \dots a_0 \,,\, a_{-1}\,a_{-2} \dots)_b = \sum_{k} a_k\,b^k, \quad k \text{ pouvant être négatif}$$

**Exemple.** $(101{,}011)_2 = 4 + 1 + 0 + \tfrac{1}{4} + \tfrac{1}{8} = 5{,}375$.

| Poids | $2^{-1}$ | $2^{-2}$ | $2^{-3}$ | $2^{-4}$ |
|---|---|---|---|---|
| Valeur | 0,5 | 0,25 | 0,125 | 0,0625 |

### 4.2 Décimal → binaire : multiplications successives

On **multiplie la partie fractionnaire par 2** ; la partie entière obtenue est le bit suivant. On recommence avec la nouvelle partie fractionnaire jusqu'à obtenir $0$ (ou jusqu'à la précision voulue).

**Exemple.** $0{,}625$ :

| Opération | Résultat | Bit |
|---|---|---|
| $0{,}625 \times 2$ | $1{,}25$ | **1** |
| $0{,}25 \times 2$ | $0{,}5$ | **0** |
| $0{,}5 \times 2$ | $1{,}0$ | **1** |

Lecture de haut en bas : $(0{,}625)_{10} = (0{,}101)_2$.

**Exemple complet.** $13{,}25 = (1101)_2 + (0{,}01)_2 = (1101{,}01)_2$.

> ⚠️ Certains décimaux « simples » n'ont pas d'écriture binaire finie : $0{,}1_{10} = 0{,}0\overline{0011}\ldots_2$. C'est pourquoi `0.1 + 0.2 != 0.3` en informatique.

### 4.3 Hexadécimal et octal fractionnaires

On groupe par 4 (ou 3) bits **à partir de la virgule**, vers la droite pour la partie fractionnaire.

$(1101{,}0110)_2 = (D{,}6)_{16}$.

---

## 5. Nombres négatifs : représentation des entiers signés

En machine, un entier est stocké sur un nombre **fixe** $n$ de bits (8, 16, 32, 64…). Il faut donc **convenir** d'une façon de représenter le signe. On présente ci-dessous les représentations sur $n = 8$ bits.

### 5.1 Entiers non signés

Tous les bits servent à la valeur : on représente $0 \leq N \leq 2^n - 1$.

Sur 8 bits : de $0$ à $255$ (`00000000` à `11111111`, soit `00` à `FF` en hexadécimal).

### 5.2 Signe et valeur absolue (signe-grandeur)

- Le bit de poids fort est le **signe** : $0$ pour positif, $1$ pour négatif.
- Les $n - 1$ autres bits donnent la **valeur absolue**.

| Nombre | Représentation sur 8 bits |
|---|---|
| $+5$ | `0000 0101` |
| $-5$ | `1000 0101` |
| $+0$ | `0000 0000` |
| $-0$ | `1000 0000` |

- Plage : $-(2^{n-1} - 1)$ à $+(2^{n-1} - 1)$, soit $-127$ à $+127$ sur 8 bits.
- **Défauts** : deux représentations de zéro ; l'addition n'est pas directe (il faut comparer les signes).

### 5.3 Complément à 1 (complément restreint)

Pour obtenir l'opposé d'un nombre, on **inverse tous les bits**.

$+5 = 0000\,0101 \;\Rightarrow\; -5 = 1111\,1010$.

- Plage : $-127$ à $+127$ sur 8 bits.
- **Défaut** : deux zéros (`0000 0000` et `1111 1111`) et une retenue à « ramener » dans l'addition (*end-around carry*).

### 5.4 Complément à 2 (représentation standard)

C'est la représentation utilisée par **tous les processeurs modernes**.

> **Définition.** Sur $n$ bits, l'opposé d'un entier $N$ est représenté par $2^n - N$ (soit le complément à 1 de $N$, plus 1).

**Méthode 1 : inverser puis ajouter 1.**

$-5$ sur 8 bits : $5 = 0000\,0101$ → inversion : $1111\,1010$ → $+1$ : $\mathbf{1111\,1011}$.

**Méthode 2 : recopier jusqu'au premier 1.** On recopie les bits en partant de la droite jusqu'au premier $1$ **inclus**, puis on inverse tous les bits restants.

$00001\underline{1}00$ ($12$) → on recopie `100` à droite, on inverse `00001` → `11110` : $1111\,0100$ = $-12$.

**Valeur d'un nombre en complément à 2.** Le bit de poids fort a un **poids négatif** $-2^{n-1}$ :

$$N = -a_{n-1}\,2^{n-1} + \sum_{k=0}^{n-2} a_k\,2^k$$

**Exemple.** $1111\,1011 = -128 + 64 + 32 + 16 + 8 + 2 + 1 = -128 + 123 = -5$ ✓.

**Plage sur $n$ bits** : $-2^{n-1}$ à $2^{n-1} - 1$.

| Bits $n$ | Non signé | Signé (complément à 2) |
|---|---|---|
| 4 | 0 à 15 | −8 à 7 |
| 8 | 0 à 255 | −128 à 127 |
| 16 | 0 à 65 535 | −32 768 à 32 767 |
| 32 | 0 à 4 294 967 295 | −2 147 483 648 à 2 147 483 647 |

**Avantages** : un seul zéro, et l'addition fonctionne **sans se soucier du signe** (voir section 6).

**Table complète sur 4 bits :**

| Binaire | Non signé | Signé (compl. à 2) |
|---|---|---|
| 0000 | 0 | 0 |
| 0001 | 1 | 1 |
| 0010 | 2 | 2 |
| 0011 | 3 | 3 |
| 0100 | 4 | 4 |
| 0101 | 5 | 5 |
| 0110 | 6 | 6 |
| 0111 | 7 | 7 |
| 1000 | 8 | −8 |
| 1001 | 9 | −7 |
| 1010 | 10 | −6 |
| 1011 | 11 | −5 |
| 1100 | 12 | −4 |
| 1101 | 13 | −3 |
| 1110 | 14 | −2 |
| 1111 | 15 | −1 |

> ⚠️ Le plus petit nombre ($-8$ sur 4 bits, $-128$ sur 8 bits) n'a **pas d'opposé positif** représentable. L'opposer le laisse inchangé.

### 5.5 Représentation par excès (décalage ou biais)

On stocke $N + \text{biais}$ en non signé. Avec un biais de $127$ sur 8 bits : $N = 130 - 127 = 3$ se lit `1000 0010`. Cette représentation sert pour l'**exposant** des nombres flottants (norme IEEE 754).

### 5.6 Négatifs en hexadécimal et en octal

Le **complément à 2 se lit en hexadécimal** : c'est la même suite de bits regroupée.

| Valeur | Binaire 8 bits | Hexadécimal |
|---|---|---|
| $+5$ | `0000 0101` | `05` |
| $-5$ | `1111 1011` | `FB` |
| $+127$ | `0111 1111` | `7F` |
| $-128$ | `1000 0000` | `80` |
| $-1$ | `1111 1111` | `FF` |

Repère rapide : en hexadécimal, un nombre signé est **négatif** si son premier chiffre est $\geq 8$ (`8` à `F`).

**Complément directement en hexadécimal.** Sur $n$ chiffres hexadécimaux, $-N = 16^n - N$. En pratique : on remplace chaque chiffre $c$ par $15 - c$, puis on ajoute 1.

$-(2F3)_{16}$ sur 3 chiffres (12 bits) : $2F3 \to D0C \to D0C + 1 = \mathbf{D0D}$.
Vérification : $4096 - 755 = 3341 = (D0D)_{16}$ ✓.

**En octal**, même principe avec $7 - c$ (complément à 7) puis $+1$ (complément à 8). L'octal convient aux mots de $3k$ bits (9, 12 bits…). Sur 3 chiffres (9 bits) :

$-(267)_8 \to 7-2,\,7-6,\,7-7 = 510 \to 510 + 1 = (511)_8$. Vérification : $512 - 183 = 329 = (511)_8$ ✓.

---

## 6. Addition

### 6.1 Principe commun à toutes les bases

On additionne **colonne par colonne**, de droite à gauche. Pour chaque colonne : $s = a + b + r_{\text{entrante}}$.

- Si $s < b$ (base) : on écrit $s$, retenue sortante $= 0$.
- Si $s \geq b$ : on écrit $s - b$, retenue sortante $= 1$.

### 6.2 Addition binaire

Table :

| $a$ | $b$ | $a + b$ | Écrit | Retenue |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 | 0 |
| 1 | 1 | 10 | 0 | **1** |
| 1 | 1 | + retenue 1 = 11 | 1 | **1** |

**Exemple.** $(1011)_2 + (0110)_2$ ($11 + 6 = 17$) :

```
  retenues :  1 1 1 0
              1 0 1 1      (11)
            + 0 1 1 0      ( 6)
            ---------
            1 0 0 0 1      (17)
```

Le résultat tient sur **5 bits** : si on travaille sur 4 bits, la dernière retenue est perdue (voir section 8).

### 6.3 Addition octale

On additionne en décimal puis on retire $8$ si la somme atteint ou dépasse $8$.

**Exemple.** $(345)_8 + (267)_8$ :

- colonne 0 : $5 + 7 = 12 = 1 \times 8 + 4$ → écrire $4$, retenue $1$ ;
- colonne 1 : $4 + 6 + 1 = 11 = 1 \times 8 + 3$ → écrire $3$, retenue $1$ ;
- colonne 2 : $3 + 2 + 1 = 6$ → écrire $6$.

Résultat : $(634)_8$.
Vérification : $229 + 183 = 412 = 6 \times 64 + 3 \times 8 + 4$ ✓.

### 6.4 Addition hexadécimale

On additionne en décimal (avec $A = 10, \dots, F = 15$) puis on retire $16$ si besoin.

**Exemple.** $(2F3)_{16} + (1AE)_{16}$ :

- colonne 0 : $3 + E = 3 + 14 = 17 = 16 + 1$ → écrire $1$, retenue $1$ ;
- colonne 1 : $F + A + 1 = 15 + 10 + 1 = 26 = 16 + 10$ → écrire $A$, retenue $1$ ;
- colonne 2 : $2 + 1 + 1 = 4$ → écrire $4$.

Résultat : $(4A1)_{16}$.
Vérification : $755 + 430 = 1185 = 4 \times 256 + 10 \times 16 + 1$ ✓.

### 6.5 Addition en complément à 2

**Règle d'or** : on additionne les mots binaires **comme des entiers non signés**, on **ignore la retenue finale**, et le résultat est correct (interprété en complément à 2) tant qu'il n'y a pas de **dépassement** (section 8).

**Exemple 1 (positif + négatif).** $13 + (-6)$ sur 8 bits :

```
    0000 1101    ( 13)
  + 1111 1010    ( -6)
  -----------
  1 0000 0111    → on ignore la retenue finale → 0000 0111 = 7 ✓
```

**Exemple 2 (négatif + négatif).** $(-5) + (-3)$ sur 8 bits :

```
    1111 1011    (-5)
  + 1111 1101    (-3)
  -----------
  1 1111 1000    → on ignore la retenue → 1111 1000 = -8 ✓
```

Vérification : $1111\,1000 = -128 + 64 + 32 + 16 + 8 = -8$ ✓.

---

## 7. Soustraction

### 7.1 Méthode directe (avec emprunt)

Colonne par colonne, de droite à gauche. Si $a - b - e < 0$ ($e$ = emprunt entrant), on **ajoute la base** à $a$ et on génère un **emprunt** de $1$ pour la colonne suivante.

**Binaire.** $(1101)_2 - (0110)_2$ ($13 - 6 = 7$) :

- colonne 0 : $1 - 0 = 1$ ;
- colonne 1 : $0 - 1$ → on emprunte : $2 + 0 - 1 = 1$, emprunt $1$ ;
- colonne 2 : $1 - 1 - 1 = -1$ → on emprunte : $2 + 1 - 1 - 1 = 1$, emprunt $1$ ;
- colonne 3 : $1 - 0 - 1 = 0$.

Résultat : $(0111)_2 = 7$ ✓.

**Octal.** $(345)_8 - (267)_8$ ($229 - 183 = 46$) :

- colonne 0 : $5 - 7 < 0$ → $5 + 8 - 7 = 6$, emprunt $1$ ;
- colonne 1 : $4 - 6 - 1 < 0$ → $4 + 8 - 6 - 1 = 5$, emprunt $1$ ;
- colonne 2 : $3 - 2 - 1 = 0$.

Résultat : $(056)_8 = (56)_8 = 5 \times 8 + 6 = 46$ ✓.

**Hexadécimal.** $(2F3)_{16} - (1AE)_{16}$ ($755 - 430 = 325$) :

- colonne 0 : $3 - E < 0$ → $3 + 16 - 14 = 5$, emprunt $1$ ;
- colonne 1 : $F - A - 1 = 15 - 10 - 1 = 4$ ;
- colonne 2 : $2 - 1 = 1$.

Résultat : $(145)_{16} = 256 + 64 + 5 = 325$ ✓.

### 7.2 Méthode par addition de l'opposé (complément à 2)

Les processeurs n'ont pas besoin de circuit de soustraction :

$$A - B = A + (-B) = A + \overline{B} + 1$$

où $\overline{B}$ est $B$ avec tous ses bits inversés.

**Exemple 1.** $13 - 6$ sur 8 bits.

- $6 = 0000\,0110$, inversion : $1111\,1001$, $+1$ : $1111\,1010$ ($= -6$).
- $0000\,1101 + 1111\,1010 = 1\,0000\,0111$ → on ignore la retenue → $0000\,0111 = 7$ ✓.

**Exemple 2 (résultat négatif).** $6 - 13$ sur 8 bits.

- $13 = 0000\,1101$, inversion : $1111\,0010$, $+1$ : $1111\,0011$ ($= -13$).
- $0000\,0110 + 1111\,0011 = 1111\,1001$ (pas de retenue finale).
- Lecture : bit de poids fort $= 1$ donc négatif ; valeur $= -128 + 64 + 32 + 16 + 8 + 1 = -7$ ✓.

**Exemple 3 (décimal : complément à 10).** $755 - 430$ avec 3 chiffres : $-430 \to 10^3 - 430 = 570$ ; $755 + 570 = 1325$ ; on ignore la retenue : $325$ ✓.

### 7.3 Soustraction par complément en hexadécimal et en octal

**Hexadécimal.** $(2F3)_{16} - (1AE)_{16}$ sur 3 chiffres :

- $-(1AE)$ : $15 - 1 = E$, $15 - A = 5$, $15 - E = 1$ → $E51$, puis $+1$ → $E52$ ;
- $2F3 + E52 = 1145$ → on ignore la retenue → $(145)_{16}$ ✓.

**Octal.** $(345)_8 - (267)_8$ sur 3 chiffres :

- $-(267)_8 = (511)_8$ (voir 5.6) ;
- $345 + 511 = 1056$ → on ignore la retenue → $(056)_8$ ✓.

---

## 8. Retenue, dépassement et extension de signe

### 8.1 Retenue (carry) vs dépassement (overflow)

Ces deux notions sont **différentes** :

| Notion | Concerne | Se produit quand… |
|---|---|---|
| **Retenue** (*carry*) | les entiers **non signés** | il y a une retenue sortant du bit de poids fort : le résultat dépasse $2^n - 1$ |
| **Dépassement** (*overflow*) | les entiers **signés** (complément à 2) | le résultat sort de la plage $[-2^{n-1},\, 2^{n-1} - 1]$ |

**Règle pour détecter un dépassement en complément à 2.**

1. Additionner deux nombres **de même signe** donne un résultat **de signe opposé** → dépassement.
2. Additionner deux nombres de signes différents ne provoque **jamais** de dépassement.
3. Équivalent matériel : dépassement $\iff$ (retenue entrant dans le MSB) $\neq$ (retenue sortant du MSB).

**Exemple 1 (positifs).** $100 + 50$ sur 8 bits :

```
    0110 0100   ( 100)
  + 0011 0010   (  50)
  -----------
    1001 0110   → lu en signé : -106  ✗  (DÉPASSEMENT)
```

Le résultat réel ($150$) dépasse $127$. En non signé, $150 \leq 255$ est correct.

**Exemple 2 (négatifs).** $(-100) + (-50)$ sur 8 bits :

```
    1001 1100   (-100)
  + 1100 1110   ( -50)
  -----------
  1 0110 1010   → on ignore la retenue → 0110 1010 = +106  ✗  (DÉPASSEMENT)
```

**Exemple 3 (retenue sans dépassement).** $(-5) + (-3)$ de la section 6.5 génère une retenue finale, mais le résultat $-8$ est correct : **pas de dépassement**.

**Exemple 4 (4 bits).** $0111 + 0001$ ($7 + 1$) $= 1000$ : en non signé c'est $8$ (correct, pas de retenue) ; en signé c'est $-8$ (dépassement).

### 8.2 Extension de signe

Pour passer un nombre signé de $n$ bits à $m > n$ bits **sans changer sa valeur**, on **recopie le bit de signe** vers la gauche.

- $0101$ ($+5$ sur 4 bits) → $0000\,0101$ sur 8 bits ;
- $1011$ ($-5$ sur 4 bits) → $1111\,1011$ sur 8 bits → $1111\,1111\,1111\,1011$ sur 16 bits $= (FFFB)_{16}$.

Pour un nombre **non signé**, on complète par des zéros (extension par zéros). Confondre les deux est une erreur classique.

### 8.3 Décalages et multiplication par la base

- Décaler un nombre binaire de $k$ rangs vers la gauche le multiplie par $2^k$ ; vers la droite, il le divise (division entière) par $2^k$.
- De même, en octal et en hexadécimal, décaler de $k$ chiffres multiplie ou divise par $8^k$ ou $16^k$.
- Pour un nombre signé, le décalage à droite doit **conserver le bit de signe** (décalage arithmétique).

Exemple : $(0001\,0110)_2 = 22$ ; décalé à gauche d'un rang : $0010\,1100 = 44$ ✓.

---

## 9. Exercices corrigés

### Exercice 1 — Conversions

Convertir $(10110110)_2$ en décimal, en octal et en hexadécimal.

<details>
<summary><strong>Corrigé</strong></summary>

- Décimal : $128 + 32 + 16 + 4 + 2 = 182$.
- Hexadécimal : $1011 \,|\, 0110 \to B\,6$, donc $(B6)_{16}$ ; vérification : $11 \times 16 + 6 = 182$ ✓.
- Octal : $10 \,|\, 110 \,|\, 110 \to 2\,6\,6$, donc $(266)_8$ ; vérification : $2 \times 64 + 6 \times 8 + 6 = 182$ ✓.
</details>

### Exercice 2 — Conversions depuis le décimal

Écrire $(1000)_{10}$ en binaire, en octal et en hexadécimal.

<details>
<summary><strong>Corrigé</strong></summary>

- Binaire : $1000 = 512 + 256 + 128 + 64 + 32 + 8$, donc $(1111101000)_2$.
- Hexadécimal : $0011\,|\,1110\,|\,1000 \to 3\,E\,8$, donc $(3E8)_{16}$ ; vérification : $3 \times 256 + 14 \times 16 + 8 = 1000$ ✓.
- Octal : $001\,|\,111\,|\,101\,|\,000 \to 1\,7\,5\,0$, donc $(1750)_8$ ; vérification : $512 + 448 + 40 = 1000$ ✓.
</details>

### Exercice 3 — Nombres fractionnaires

Convertir $(0{,}1101)_2$ en décimal, puis $13{,}25$ en binaire.

<details>
<summary><strong>Corrigé</strong></summary>

- $(0{,}1101)_2 = 0{,}5 + 0{,}25 + 0{,}0625 = 0{,}8125$.
- $13 = (1101)_2$ et $0{,}25 \times 2 = 0{,}5 \to 0$ ; $0{,}5 \times 2 = 1{,}0 \to 1$, donc $0{,}25 = (0{,}01)_2$. Ainsi $13{,}25 = (1101{,}01)_2$.
</details>

### Exercice 4 — Complément à 2

Sur 8 bits, écrire $-37$ en complément à 2 (binaire et hexadécimal), puis calculer $93 + (-37)$.

<details>
<summary><strong>Corrigé</strong></summary>

- $37 = 0010\,0101$ ; inversion : $1101\,1010$ ; $+1$ : $1101\,1011$, soit $(DB)_{16}$ (vérification : $256 - 37 = 219 = DB$ ✓).
- $93 = 0101\,1101$.
- $0101\,1101 + 1101\,1011 = 1\,0011\,1000$ → on ignore la retenue → $0011\,1000 = 32 + 16 + 8 = 56$ ✓ ($93 - 37 = 56$).
</details>

### Exercice 5 — Lecture d'un nombre signé

Quelle est la valeur signée (complément à 2, 8 bits) de $(C8)_{16}$ ?

<details>
<summary><strong>Corrigé</strong></summary>

$(C8)_{16} = 1100\,1000$ : le bit de poids fort vaut $1$, donc le nombre est négatif.
$N = -128 + 64 + 8 = -56$ (ou : $200 - 256 = -56$).
</details>

### Exercice 6 — Addition hexadécimale et dépassement

Sur 8 bits, calculer $(7F)_{16} + (01)_{16}$ et $(50)_{16} + (70)_{16}$. Interpréter en non signé puis en signé.

<details>
<summary><strong>Corrigé</strong></summary>

- $7F + 01 = 80$. Non signé : $127 + 1 = 128$ (correct). Signé : $(80)_{16} = -128$, donc **dépassement** (deux positifs donnent un négatif).
- $50 + 70 = C0$ ($5 + 7 = 12 = C$). Non signé : $80 + 112 = 192$ (correct, pas de retenue). Signé : $(C0)_{16} = -64$, donc **dépassement**.
</details>

### Exercice 7 — Addition octale

Calculer $(777)_8 + (1)_8$.

<details>
<summary><strong>Corrigé</strong></summary>

$7 + 1 = 8 = 1 \times 8 + 0$ → écrire $0$, retenue $1$, et la retenue se propage dans les trois colonnes : $(1000)_8$.
Vérification : $511 + 1 = 512 = 8^3$ ✓.
</details>

### Exercice 8 — Soustraction en complément à 2

Calculer $(10100101)_2 - (00111100)_2$ en utilisant le complément à 2 sur 8 bits.

<details>
<summary><strong>Corrigé</strong></summary>

- $A = 1010\,0101 = 165$ et $B = 0011\,1100 = 60$.
- $-B$ : inversion $1100\,0011$, $+1$ : $1100\,0100$ ($= 196 = 256 - 60$).
- $A + (-B) = 1010\,0101 + 1100\,0100 = 1\,0110\,1001$ → on ignore la retenue → $0110\,1001 = 64 + 32 + 8 + 1 = 105$ ✓ ($165 - 60 = 105$).
</details>

### Exercice 9 — Soustraction hexadécimale

Calculer $(A3)_{16} - (5E)_{16}$ par la méthode directe, puis vérifier en décimal.
```
<details>
<summary><strong>Corrigé</strong></summary>

- colonne 0 : $3 - E < 0$ → $3 + 16 - 14 = 5$, emprunt $1$ ;
- colonne 1 : $A - 5 - 1 = 10 - 5 - 1 = 4$.

Résultat : $(45)_{16} = 69$.
Vérification : $163 - 94 = 69$ ✓.
</details>
```
## 10. Fiche de synthèse

### Conversions

| Je veux… | Je fais… |
|---|---|
| base $b$ → décimal | $\sum a_k\,b^k$ (ou méthode de Horner) |
| décimal → base $b$ | divisions successives par $b$, restes lus **de bas en haut** |
| fraction décimale → base $b$ | multiplications successives par $b$, parties entières lues **de haut en bas** |
| binaire ↔ hexadécimal | groupes de **4 bits** |
| binaire ↔ octal | groupes de **3 bits** |
| octal ↔ hexadécimal | passer par le **binaire** |

### Représentation des entiers sur $n$ bits

| Représentation | Plage | Opposé de $N$ | Particularité |
|---|---|---|---|
| Non signé | $0$ à $2^n - 1$ | — | pas de négatifs |
| Signe-valeur | $-(2^{n-1}-1)$ à $2^{n-1}-1$ | inverser le bit de signe | deux zéros |
| Complément à 1 | $-(2^{n-1}-1)$ à $2^{n-1}-1$ | inverser tous les bits | deux zéros |
| **Complément à 2** | $-2^{n-1}$ à $2^{n-1}-1$ | inverser puis $+1$ ($= 2^n - N$) | **un seul zéro, addition directe** |
| Excès $K$ | $-K$ à $2^n - 1 - K$ | $2K - $ code | utilisé pour les exposants flottants |

### Opérations

- **Addition** : colonne par colonne, retenue quand la somme atteint la base.
- **Soustraction** : emprunt direct, ou $A - B = A + \overline{B} + 1$ en complément à 2.
- **Complément à 2 en hexadécimal** : $15 - c$ sur chaque chiffre, puis $+1$.
- **Négatif en hexadécimal** : premier chiffre $\geq 8$.

### Retenue et dépassement

| | Non signé | Signé (complément à 2) |
|---|---|---|
| Condition d'erreur | retenue sortante = 1 | dépassement (overflow) |
| Détection | bit de retenue | deux opérandes de même signe, résultat de signe opposé |

### Pièges classiques

1. Confondre $(10)_2$, $(10)_8$, $(10)_{10}$, $(10)_{16}$ : **toujours préciser la base**.
2. Lire les restes des divisions **de haut en bas** au lieu de **de bas en haut**.
3. Grouper les bits à partir de la **gauche** pour passer en hexadécimal ; il faut commencer par la **droite** (partie entière).
4. Oublier le « $+1$ » dans le complément à 2.
5. Oublier que le complément à 2 dépend de la **largeur** $n$ : $1111$ vaut $-1$ sur 4 bits mais $+15$ sur 8 bits (`0000 1111`).
6. Confondre **retenue** (non signé) et **dépassement** (signé).
7. Étendre un nombre signé avec des zéros au lieu de recopier le **bit de signe**.
8. Chercher l'opposé de $-2^{n-1}$ : il n'existe pas dans la plage.
9. Croire que tout décimal a une écriture binaire finie ($0{,}1$ n'en a pas).

---

*Fin du cours.*
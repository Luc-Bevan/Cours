# Les nombres complexes — Cours complet perso

> **Niveau** : fin de lycée / début d'enseignement supérieur (Terminale spécialité maths expertes, Licence 1, classes préparatoires).
> **Notations** : $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$ désignent respectivement les ensembles des entiers naturels, relatifs, rationnels, réels et complexes.

---

## Sommaire

1. [Motivation et définition](#1-motivation-et-définition)
2. [Forme algébrique et opérations](#2-forme-algébrique-et-opérations)
3. [Conjugué et module](#3-conjugué-et-module)
4. [Représentation géométrique](#4-représentation-géométrique)
5. [Argument et forme trigonométrique](#5-argument-et-forme-trigonométrique)
6. [Forme exponentielle et formules d'Euler](#6-forme-exponentielle-et-formules-deuler)
7. [Formule de Moivre et applications](#7-formule-de-moivre-et-applications)
8. [Racines $n$-ièmes](#8-racines-n-ièmes)
9. [Équations du second degré](#9-équations-du-second-degré)
10. [Applications à la géométrie](#10-applications-à-la-géométrie)
11. [Transformations du plan](#11-transformations-du-plan)
12. [Polynômes complexes](#12-polynômes-complexes)
13. [Exercices corrigés](#13-exercices-corrigés)
14. [Fiche de synthèse](#14-fiche-de-synthèse)

---

## 1. Motivation et définition

### 1.1 Pourquoi les nombres complexes ?

Dans $\mathbb{R}$, l'équation $x^2 = -1$ n'a pas de solution, car un carré réel est toujours positif ou nul. Au XVIe siècle, les mathématiciens italiens (Cardan, Bombelli) rencontrent des racines carrées de nombres négatifs en résolvant des équations du troisième degré, même lorsque les solutions finales sont réelles. Ils introduisent alors un nombre « imaginaire » dont le carré vaut $-1$.

Les nombres complexes permettent :

- de résoudre **toutes** les équations polynomiales (théorème de d'Alembert-Gauss) ;
- de décrire élégamment les **rotations** et **similitudes** du plan ;
- de simplifier la **trigonométrie** ;
- de modéliser les phénomènes **oscillatoires** (électricité, mécanique quantique, traitement du signal).

### 1.2 Définition

> **Définition.** On admet l'existence d'un ensemble $\mathbb{C}$, appelé *ensemble des nombres complexes*, tel que :
>
> 1. $\mathbb{C}$ contient $\mathbb{R}$ ;
> 2. $\mathbb{C}$ est muni d'une addition et d'une multiplication qui prolongent celles de $\mathbb{R}$ et suivent les mêmes règles de calcul ;
> 3. $\mathbb{C}$ contient un nombre noté $i$ tel que $i^2 = -1$ ;
> 4. tout élément $z$ de $\mathbb{C}$ s'écrit de manière **unique** $z = a + ib$ *(on appelle i : j, quand on fais des maths avec de la physique)* avec $a, b \in \mathbb{R}$.

### 1.3 Construction rigoureuse (pour aller plus loin)

On peut construire $\mathbb{C}$ comme l'ensemble $\mathbb{R}^2$ des couples de réels, muni de :

$$(a, b) + (c, d) = (a + c,\; b + d)$$

$$(a, b) \times (c, d) = (ac - bd,\; ad + bc)$$

Le couple $(a, 0)$ s'identifie au réel $a$, et on pose $i = (0, 1)$. On vérifie alors que $i^2 = (0,1)(0,1) = (-1, 0) = -1$, et que $(a, b) = a + ib$.

---

## 2. Forme algébrique et opérations

### 2.1 Vocabulaire

Pour $z = a + ib$ avec $a, b \in \mathbb{R}$ :

| Terme | Notation | Valeur |
|---|---|---|
| Partie réelle | $\operatorname{Re}(z)$ | $a$ |
| Partie imaginaire | $\operatorname{Im}(z)$ | $b$ |

- $z$ est **réel** $\iff \operatorname{Im}(z) = 0$ ;
- $z$ est **imaginaire pur** $\iff \operatorname{Re}(z) = 0$ (par exemple $3i$) ;
- $0$ est à la fois réel et imaginaire pur.

> ⚠️ La partie imaginaire d'un complexe est un **réel** : $\operatorname{Im}(3 + 2i) = 2$, et non $2i$.

### 2.2 Égalité de deux complexes

$$a + ib = a' + ib' \iff a = a' \text{ et } b = b'$$

En particulier : $a + ib = 0 \iff a = b = 0$.

**Conséquence** : on ne peut pas ordonner $\mathbb{C}$ de façon compatible avec les opérations. Écrire $z_1 < z_2$ n'a aucun sens pour des complexes non réels.

### 2.3 Addition, soustraction, multiplication

Soient $z = a + ib$ et $z' = a' + ib'$.

$$z + z' = (a + a') + i(b + b')$$

$$z \times z' = (aa' - bb') + i(ab' + a'b)$$

**Exemple.** $(2 + 3i)(1 - 4i) = 2 - 8i + 3i - 12i^2 = 2 - 5i + 12 = 14 - 5i$.

On développe comme dans $\mathbb{R}$ en remplaçant $i^2$ par $-1$.

### 2.4 Puissances de $i$

Les puissances de $i$ sont périodiques de période 4 :

| $n \bmod 4$ | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| $i^n$ | $1$ | $i$ | $-1$ | $-i$ |

**Exemple.** $i^{2026}$ : $2026 = 4 \times 506 + 2$, donc $i^{2026} = i^2 = -1$.

### 2.5 Identités remarquables

Elles restent valides dans $\mathbb{C}$ :

- $(z + z')^2 = z^2 + 2zz' + z'^2$
- $(z - z')^2 = z^2 - 2zz' + z'^2$
- $z^2 - z'^2 = (z - z')(z + z')$
- $z^2 + z'^2 = (z - iz')(z + iz')$ — nouveauté dans $\mathbb{C}$ !
- Binôme de Newton : $(z + z')^n = \displaystyle\sum_{k=0}^{n} \binom{n}{k} z^k z'^{n-k}$
- $z^n - 1 = (z - 1)(1 + z + z^2 + \dots + z^{n-1})$

### 2.6 Inverse et quotient

Tout complexe non nul $z = a + ib$ possède un inverse. Pour le calculer, on multiplie numérateur et dénominateur par le **conjugué** :

$$\frac{1}{a + ib} = \frac{a - ib}{(a + ib)(a - ib)} = \frac{a - ib}{a^2 + b^2}$$

**Exemple.**
$$\frac{2 + i}{3 - 2i} = \frac{(2 + i)(3 + 2i)}{(3 - 2i)(3 + 2i)} = \frac{6 + 4i + 3i + 2i^2}{9 + 4} = \frac{4 + 7i}{13} = \frac{4}{13} + \frac{7}{13}i$$

### 2.7 Propriétés de structure

$(\mathbb{C}, +, \times)$ est un **corps commutatif** : l'addition et la multiplication sont associatives, commutatives, distributives l'une sur l'autre, ont des éléments neutres ($0$ et $1$), tout élément a un opposé et tout élément non nul a un inverse.

**Intégrité** : $zz' = 0 \iff z = 0$ ou $z' = 0$.

---

## 3. Conjugué et module

### 3.1 Conjugué

> **Définition.** Le **conjugué** de $z = a + ib$ est $\bar{z} = a - ib$.

**Propriétés.** Pour tous $z, z' \in \mathbb{C}$ et $n \in \mathbb{Z}$ :

1. $\overline{\bar{z}} = z$
2. $\overline{z + z'} = \bar{z} + \bar{z'}$
3. $\overline{zz'} = \bar{z}\,\bar{z'}$
4. $\overline{z^n} = (\bar{z})^n$ (avec $z \neq 0$ si $n < 0$)
5. $\overline{\left(\dfrac{z}{z'}\right)} = \dfrac{\bar{z}}{\bar{z'}}$ (avec $z' \neq 0$)

**Caractérisations utiles.**

$$\operatorname{Re}(z) = \frac{z + \bar{z}}{2} \qquad \operatorname{Im}(z) = \frac{z - \bar{z}}{2i}$$

$$z \in \mathbb{R} \iff z = \bar{z} \qquad z \in i\mathbb{R} \iff z = -\bar{z}$$

### 3.2 Module

> **Définition.** Le **module** de $z = a + ib$ est le réel positif $|z| = \sqrt{a^2 + b^2}$.

Remarque fondamentale :

$$\boxed{z\bar{z} = a^2 + b^2 = |z|^2}$$

Pour un réel, le module coïncide avec la valeur absolue.

**Propriétés.** Pour tous $z, z' \in \mathbb{C}$ :

1. $|z| = 0 \iff z = 0$
2. $|\bar{z}| = |-z| = |z|$
3. $|zz'| = |z|\,|z'|$
4. $|z^n| = |z|^n$
5. $\left|\dfrac{z}{z'}\right| = \dfrac{|z|}{|z'|}$ (avec $z' \neq 0$)
6. **Inégalité triangulaire** : $|z + z'| \leq |z| + |z'|$
7. **Seconde inégalité triangulaire** : $\big||z| - |z'|\big| \leq |z - z'|$

**Preuve de 3.** $|zz'|^2 = zz'\,\overline{zz'} = z\bar{z}\,z'\bar{z'} = |z|^2|z'|^2$, et on passe à la racine (module positif). $\square$

**Preuve de l'inégalité triangulaire.**
$$|z + z'|^2 = (z + z')(\bar{z} + \bar{z'}) = |z|^2 + |z'|^2 + 2\operatorname{Re}(z\bar{z'})$$
Or $\operatorname{Re}(z\bar{z'}) \leq |z\bar{z'}| = |z||z'|$, donc $|z + z'|^2 \leq (|z| + |z'|)^2$. $\square$

---

## 4. Représentation géométrique

### 4.1 Le plan complexe

Le plan est muni d'un repère orthonormé direct $(O; \vec{u}, \vec{v})$.

- Au complexe $z = a + ib$ on associe le point $M(a, b)$ : $z$ est l'**affixe** de $M$.
- Il est aussi l'affixe du vecteur $\vec{OM}$.
- L'axe des abscisses est l'**axe réel**, celui des ordonnées l'**axe imaginaire**.

### 4.2 Dictionnaire géométrie ↔ complexes

Soient $A$, $B$ d'affixes $z_A$, $z_B$ :

| Géométrie | Complexes |
|---|---|
| Vecteur $\vec{AB}$ | $z_B - z_A$ |
| Distance $AB$ | $\lvert z_B - z_A\rvert$ |
| Milieu de $[AB]$ | $\dfrac{z_A + z_B}{2}$ |
| Barycentre de $(A, \alpha), (B, \beta)$ | $\dfrac{\alpha z_A + \beta z_B}{\alpha + \beta}$ |
| Symétrique de $M(z)$ par rapport à l'axe réel | $\bar{z}$ |
| Symétrique de $M(z)$ par rapport à $O$ | $-z$ |
| Vecteur somme $\vec{u} + \vec{v}$ | $z_u + z_v$ |

### 4.3 Lieux géométriques

Soit $A$ d'affixe $a$ et $r > 0$.

- $|z - a| = r$ : **cercle** de centre $A$ et de rayon $r$.
- $|z - a| < r$ : **disque** ouvert.
- $|z - a| = |z - b|$ : **médiatrice** de $[AB]$.
- $\operatorname{Re}(z) = k$ : droite verticale ; $\operatorname{Im}(z) = k$ : droite horizontale.

---

## 5. Argument et forme trigonométrique

### 5.1 Argument

Soit $z \neq 0$ d'image $M$.

> **Définition.** Un **argument** de $z$ est une mesure (en radians) de l'angle orienté $(\vec{u}, \vec{OM})$. On le note $\arg(z)$.

L'argument est défini **à $2\pi$ près** :
$$\arg(z) \equiv \theta \pmod{2\pi}$$

Le complexe $0$ n'a pas d'argument.

**Cas particuliers.**

| $z$ | $\arg(z)$ |
|---|---|
| réel $> 0$ | $0 \pmod{2\pi}$ |
| réel $< 0$ | $\pi \pmod{2\pi}$ |
| imaginaire pur, $\operatorname{Im} > 0$ | $\dfrac{\pi}{2} \pmod{2\pi}$ |
| imaginaire pur, $\operatorname{Im} < 0$ | $-\dfrac{\pi}{2} \pmod{2\pi}$ |

### 5.2 Forme trigonométrique

> **Théorème.** Tout complexe non nul s'écrit $z = r(\cos\theta + i\sin\theta)$ avec $r = |z| > 0$ et $\theta = \arg(z)$.

**Passage de la forme algébrique à la forme trigonométrique.** Pour $z = a + ib \neq 0$ :

1. Calculer $r = \sqrt{a^2 + b^2}$.
2. Mettre en facteur : $z = r\left(\dfrac{a}{r} + i\dfrac{b}{r}\right)$.
3. Trouver $\theta$ tel que $\cos\theta = \dfrac{a}{r}$ et $\sin\theta = \dfrac{b}{r}$.

**Exemple.** $z = 1 + i\sqrt{3}$.

- $r = \sqrt{1 + 3} = 2$
- $\cos\theta = \frac{1}{2}$ et $\sin\theta = \frac{\sqrt{3}}{2}$, d'où $\theta = \frac{\pi}{3}$.
- $z = 2\left(\cos\frac{\pi}{3} + i\sin\frac{\pi}{3}\right)$.

**Passage inverse.** $a = r\cos\theta$, $b = r\sin\theta$.

> ⚠️ Ne jamais écrire $\theta = \arctan(b/a)$ sans réfléchir : la fonction $\arctan$ renvoie un angle dans $]-\frac{\pi}{2}, \frac{\pi}{2}[$ et ne distingue pas $z$ de $-z$. Il faut toujours vérifier le signe de $\cos\theta$ et $\sin\theta$ (le quadrant).

### 5.3 Valeurs remarquables

| $\theta$ | $0$ | $\frac{\pi}{6}$ | $\frac{\pi}{4}$ | $\frac{\pi}{3}$ | $\frac{\pi}{2}$ |
|---|---|---|---|---|---|
| $\cos\theta$ | $1$ | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{1}{2}$ | $0$ |
| $\sin\theta$ | $0$ | $\frac{1}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{3}}{2}$ | $1$ |

### 5.4 Opérations sur les arguments

Pour $z, z' \neq 0$ et $n \in \mathbb{Z}$, modulo $2\pi$ :

| Propriété | Formule |
|---|---|
| Produit | $\arg(zz') = \arg(z) + \arg(z')$ |
| Puissance | $\arg(z^n) = n\arg(z)$ |
| Inverse | $\arg\!\left(\dfrac{1}{z}\right) = -\arg(z)$ |
| Quotient | $\arg\!\left(\dfrac{z}{z'}\right) = \arg(z) - \arg(z')$ |
| Conjugué | $\arg(\bar{z}) = -\arg(z)$ |
| Opposé | $\arg(-z) = \arg(z) + \pi$ |

**Interprétation.** Multiplier par $z'$ revient à **multiplier les modules** et **additionner les angles**.

### 5.5 Argument et angles géométriques

Soient $A$, $B$, $C$, $D$ quatre points d'affixes $a, b, c, d$, avec $A \neq B$ et $C \neq D$ :

$$\left(\vec{AB}, \vec{CD}\right) \equiv \arg\!\left(\frac{d - c}{b - a}\right) \pmod{2\pi}$$

**Conséquences.**

- $A, B, C$ sont **alignés** $\iff \dfrac{c - a}{b - a} \in \mathbb{R}$.
- $(AB) \perp (AC) \iff \dfrac{c - a}{b - a} \in i\mathbb{R}$.
- $ABC$ est **isocèle en $A$** $\iff \left|\dfrac{c - a}{b - a}\right| = 1$.
- $ABC$ est **équilatéral** $\iff \dfrac{c - a}{b - a} = e^{\pm i\pi/3}$.

---

## 6. Forme exponentielle et formules d'Euler

### 6.1 Notation $e^{i\theta}$

> **Définition.** Pour tout réel $\theta$, on pose
> $$e^{i\theta} = \cos\theta + i\sin\theta$$

Cette notation est justifiée par la propriété fondamentale :

$$e^{i\theta} \cdot e^{i\theta'} = e^{i(\theta + \theta')}$$

qui découle des formules d'addition de $\cos$ et $\sin$ :
$$(\cos\theta + i\sin\theta)(\cos\theta' + i\sin\theta') = \cos(\theta + \theta') + i\sin(\theta + \theta')$$

(Elle est cohérente avec le prolongement de l'exponentielle à $\mathbb{C}$ par la série entière $e^z = \sum_{n \ge 0} \frac{z^n}{n!}$.)

### 6.2 Forme exponentielle

Tout complexe non nul s'écrit
$$z = r e^{i\theta}, \quad r = |z|, \; \theta = \arg(z).$$

**Exemples.**

- $1 = e^{0}$, $\;-1 = e^{i\pi}$, $\;i = e^{i\pi/2}$, $\;-i = e^{-i\pi/2}$.
- $1 + i = \sqrt{2}\,e^{i\pi/4}$.
- $-2 = 2e^{i\pi}$.

**Le produit devient trivial :**
$$re^{i\theta} \times r'e^{i\theta'} = rr'\,e^{i(\theta + \theta')} \qquad \frac{re^{i\theta}}{r'e^{i\theta'}} = \frac{r}{r'}\,e^{i(\theta - \theta')}$$

### 6.3 Propriétés de $e^{i\theta}$

Pour tous réels $\theta, \theta'$ et $n \in \mathbb{Z}$ :

- $|e^{i\theta}| = 1$
- $\overline{e^{i\theta}} = e^{-i\theta} = \dfrac{1}{e^{i\theta}}$
- $e^{i(\theta + 2\pi)} = e^{i\theta}$
- $e^{i\theta} = e^{i\theta'} \iff \theta \equiv \theta' \pmod{2\pi}$
- $\left(e^{i\theta}\right)^n = e^{in\theta}$

### 6.4 Formules d'Euler

$$\boxed{\cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2} \qquad \sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i}}$$

Ces formules, directement issues de $\cos\theta = \operatorname{Re}(e^{i\theta})$ et de $\sin\theta = \operatorname{Im}(e^{i\theta})$, sont l'outil central pour **linéariser** des expressions trigonométriques.

### 6.5 Identité d'Euler

En posant $\theta = \pi$ :
$$e^{i\pi} + 1 = 0$$

Elle relie les cinq constantes fondamentales $0$, $1$, $i$, $\pi$ et $e$.

### 6.6 Technique de l'angle moitié

Pour factoriser $1 + e^{i\theta}$ ou $1 - e^{i\theta}$ :

$$1 + e^{i\theta} = e^{i\theta/2}\left(e^{-i\theta/2} + e^{i\theta/2}\right) = 2\cos\frac{\theta}{2}\;e^{i\theta/2}$$

$$1 - e^{i\theta} = e^{i\theta/2}\left(e^{-i\theta/2} - e^{i\theta/2}\right) = -2i\sin\frac{\theta}{2}\;e^{i\theta/2}$$

> ⚠️ Si $\cos\frac{\theta}{2} < 0$, l'écriture $2\cos\frac{\theta}{2}\,e^{i\theta/2}$ n'est **pas** la forme exponentielle (le coefficient n'est pas positif) : le module est $2\left|\cos\frac{\theta}{2}\right|$ et l'argument change de $\pi$.

---

## 7. Formule de Moivre et applications

### 7.1 Formule de Moivre

$$\boxed{\forall n \in \mathbb{Z},\quad (\cos\theta + i\sin\theta)^n = \cos(n\theta) + i\sin(n\theta)}$$

ou encore $(e^{i\theta})^n = e^{in\theta}$.

**Preuve** par récurrence pour $n \geq 0$ en utilisant $e^{i\theta}e^{in\theta} = e^{i(n+1)\theta}$, puis passage aux entiers négatifs par inversion. $\square$

### 7.2 Calcul de puissances

**Exemple.** Calculer $(1 + i)^{10}$.

$1 + i = \sqrt{2}\,e^{i\pi/4}$, donc
$$(1 + i)^{10} = \left(\sqrt{2}\right)^{10} e^{i\,10\pi/4} = 32\,e^{i\,5\pi/2} = 32\,e^{i\pi/2} = 32i.$$

### 7.3 Expression de $\cos(n\theta)$ et $\sin(n\theta)$ en fonction de $\cos\theta$, $\sin\theta$

On développe $(\cos\theta + i\sin\theta)^n$ par le binôme et on identifie parties réelle et imaginaire.

**Exemple ($n = 3$).**
$$(\cos\theta + i\sin\theta)^3 = \cos^3\theta + 3i\cos^2\theta\sin\theta - 3\cos\theta\sin^2\theta - i\sin^3\theta$$

Donc :
$$\cos 3\theta = \cos^3\theta - 3\cos\theta\sin^2\theta = 4\cos^3\theta - 3\cos\theta$$
$$\sin 3\theta = 3\cos^2\theta\sin\theta - \sin^3\theta = 3\sin\theta - 4\sin^3\theta$$

### 7.4 Linéarisation

Linéariser, c'est transformer un produit/puissance de $\cos$ et $\sin$ en **somme** de $\cos(k\theta)$, $\sin(k\theta)$. On utilise Euler puis le binôme.

**Exemple.** Linéariser $\cos^3\theta$.

$$\cos^3\theta = \left(\frac{e^{i\theta} + e^{-i\theta}}{2}\right)^3 = \frac{1}{8}\left(e^{3i\theta} + 3e^{i\theta} + 3e^{-i\theta} + e^{-3i\theta}\right)$$

$$= \frac{1}{8}\left(2\cos 3\theta + 6\cos\theta\right) = \frac{\cos 3\theta + 3\cos\theta}{4}.$$

### 7.5 Calcul de sommes trigonométriques

**Exemple.** Calculer $S = \displaystyle\sum_{k=0}^{n}\cos(k\theta)$ avec $\theta \notin 2\pi\mathbb{Z}$.

On pose $C = \sum \cos(k\theta)$, $T = \sum \sin(k\theta)$ et $S' = C + iT = \sum_{k=0}^{n} e^{ik\theta}$ : c'est une somme géométrique de raison $e^{i\theta} \neq 1$.

$$S' = \frac{1 - e^{i(n+1)\theta}}{1 - e^{i\theta}} = \frac{e^{i(n+1)\theta/2}\,\left(-2i\sin\frac{(n+1)\theta}{2}\right)}{e^{i\theta/2}\left(-2i\sin\frac{\theta}{2}\right)} = \frac{\sin\frac{(n+1)\theta}{2}}{\sin\frac{\theta}{2}}\,e^{in\theta/2}.$$

On en déduit, en prenant la partie réelle :
$$\sum_{k=0}^{n}\cos(k\theta) = \frac{\sin\frac{(n+1)\theta}{2}}{\sin\frac{\theta}{2}}\cos\frac{n\theta}{2}.$$

---

## 8. Racines $n$-ièmes

### 8.1 Racines $n$-ièmes de l'unité

> **Théorème.** Pour $n \geq 1$, l'équation $z^n = 1$ possède exactement $n$ solutions dans $\mathbb{C}$ :
> $$\omega_k = e^{2ik\pi/n}, \quad k = 0, 1, \dots, n - 1.$$
> On note leur ensemble $\mathbb{U}_n$.

**Preuve.** Posons $z = re^{i\theta}$. Alors $z^n = r^ne^{in\theta} = 1$ donne $r^n = 1$ (donc $r = 1$) et $n\theta \equiv 0 \pmod{2\pi}$, c'est-à-dire $\theta = \frac{2k\pi}{n}$, $k \in \mathbb{Z}$. Seules $n$ valeurs distinctes de $k$ donnent des points différents. $\square$

**Propriétés.**

- Les images des racines $n$-ièmes de l'unité sont les sommets d'un **polygone régulier à $n$ côtés** inscrit dans le cercle unité, dont $1$ est un sommet.
- **Somme nulle** : pour $n \geq 2$, $\displaystyle\sum_{k=0}^{n-1}\omega_k = 0$.
- $\mathbb{U}_n$ est stable par produit et par inverse : c'est un groupe.
- Si on pose $\omega = e^{2i\pi/n}$, alors $\omega_k = \omega^k$ et $\mathbb{U}_n = \{1, \omega, \omega^2, \dots, \omega^{n-1}\}$.

**Cas usuels.**

| $n$ | Racines |
|---|---|
| 2 | $1,\; -1$ |
| 3 | $1,\; j = e^{2i\pi/3} = -\frac{1}{2} + i\frac{\sqrt{3}}{2},\; j^2 = \bar{j}$ |
| 4 | $1,\; i,\; -1,\; -i$ |
| 6 | $\pm 1,\; \pm\frac{1}{2} \pm i\frac{\sqrt{3}}{2}$ |

Le nombre $j$ vérifie $1 + j + j^2 = 0$ et $j^3 = 1$.

### 8.2 Racines $n$-ièmes d'un complexe non nul

> **Théorème.** Soit $a = \rho e^{i\alpha} \neq 0$. L'équation $z^n = a$ admet exactement $n$ solutions :
> $$z_k = \rho^{1/n}\,e^{i\left(\frac{\alpha}{n} + \frac{2k\pi}{n}\right)}, \quad k = 0, \dots, n - 1.$$

**Astuce.** Si $z_0$ est une solution particulière, les solutions sont $z_0\omega^k$ où $\omega^k$ décrit $\mathbb{U}_n$.

**Exemple.** Résoudre $z^3 = 8i$.

$8i = 8e^{i\pi/2}$, donc $z_k = 2e^{i(\pi/6 + 2k\pi/3)}$ pour $k = 0, 1, 2$ :

- $z_0 = 2e^{i\pi/6} = \sqrt{3} + i$
- $z_1 = 2e^{i5\pi/6} = -\sqrt{3} + i$
- $z_2 = 2e^{i3\pi/2} = -2i$

### 8.3 Racines carrées sous forme algébrique

Pour $Z = a + ib$, on cherche $z = x + iy$ tel que $z^2 = Z$. On écrit le système :

$$\begin{cases} x^2 - y^2 = a \\ x^2 + y^2 = |Z| = \sqrt{a^2 + b^2} \\ 2xy = b \end{cases}$$

Les deux premières équations donnent $x^2$ et $y^2$ ; la troisième fixe les signes relatifs de $x$ et $y$.

**Exemple.** Racines carrées de $Z = 3 + 4i$.

- $|Z| = 5$ ; $x^2 - y^2 = 3$ et $x^2 + y^2 = 5$ donnent $x^2 = 4$ et $y^2 = 1$.
- $2xy = 4 > 0$ : $x$ et $y$ ont même signe.
- Racines : $2 + i$ et $-2 - i$. Vérification : $(2 + i)^2 = 4 + 4i - 1 = 3 + 4i$ ✓.

---

## 9. Équations du second degré

### 9.1 Équation à coefficients réels

Soit $az^2 + bz + c = 0$ avec $a, b, c \in \mathbb{R}$, $a \neq 0$, et $\Delta = b^2 - 4ac$.

| Signe de $\Delta$ | Solutions |
|---|---|
| $\Delta > 0$ | $z = \dfrac{-b \pm \sqrt{\Delta}}{2a}$ (deux réels) |
| $\Delta = 0$ | $z = -\dfrac{b}{2a}$ (racine double) |
| $\Delta < 0$ | $z = \dfrac{-b \pm i\sqrt{-\Delta}}{2a}$ (deux complexes **conjugués**) |

**Exemple.** $z^2 - 2z + 5 = 0$ : $\Delta = 4 - 20 = -16$, donc $z = \dfrac{2 \pm 4i}{2} = 1 \pm 2i$.

### 9.2 Équation à coefficients complexes

Soit $az^2 + bz + c = 0$ avec $a, b, c \in \mathbb{C}$, $a \neq 0$, et $\Delta = b^2 - 4ac \in \mathbb{C}$.

On choisit $\delta \in \mathbb{C}$ tel que $\delta^2 = \Delta$ (voir 8.3). Alors les solutions sont :

$$z_{1,2} = \frac{-b \pm \delta}{2a}$$

(confondues si $\Delta = 0$).

**Exemple.** $z^2 - (3 + i)z + (2 + i) = 0$.

- $\Delta = (3 + i)^2 - 4(2 + i) = 8 + 6i - 8 - 4i = 2i$.
- $\delta = 1 + i$ car $(1 + i)^2 = 2i$.
- $z_1 = \dfrac{3 + i + 1 + i}{2} = 2 + i$, $\;z_2 = \dfrac{3 + i - 1 - i}{2} = 1$.

### 9.3 Relations coefficients-racines

Si $z_1, z_2$ sont les racines de $az^2 + bz + c$ :

$$z_1 + z_2 = -\frac{b}{a} \qquad z_1 z_2 = \frac{c}{a}$$

et $az^2 + bz + c = a(z - z_1)(z - z_2)$.

---

## 10. Applications à la géométrie

### 10.1 Nature d'un triangle

Pour déterminer la nature de $ABC$, on calcule le quotient $Q = \dfrac{c - a}{b - a}$ :

| $Q$ | Conclusion |
|---|---|
| $\lvert Q \rvert = 1$ | $AB = AC$ : isocèle en $A$ |
| $Q \in i\mathbb{R}^*$ | $\widehat{BAC} = \pm\frac{\pi}{2}$ : rectangle en $A$ |
| $Q = \pm i$ | rectangle isocèle en $A$ |
| $Q = e^{\pm i\pi/3}$ | équilatéral |

### 10.2 Alignement, parallélisme, orthogonalité

- $\vec{AB} \parallel \vec{CD} \iff \dfrac{d - c}{b - a} \in \mathbb{R}$.
- $\vec{AB} \perp \vec{CD} \iff \dfrac{d - c}{b - a} \in i\mathbb{R}$.

### 10.3 Parallélogrammes

$ABCD$ est un parallélogramme $\iff \vec{AB} = \vec{DC} \iff b - a = c - d$.

### 10.4 Points cocycliques

Quatre points distincts $A, B, C, D$ sont alignés ou cocycliques si et seulement si
$$\frac{(c - a)(d - b)}{(c - b)(d - a)} \in \mathbb{R}.$$

(C'est le critère du **birapport réel**.)

---

## 11. Transformations du plan

Soit $M$ d'affixe $z$ et $M'$ d'affixe $z'$ son image.

### 11.1 Translation de vecteur $\vec{w}$ (affixe $w$)

$$z' = z + w$$

### 11.2 Homothétie de centre $\Omega$ (affixe $\omega$) et de rapport $k \in \mathbb{R}^*$

$$z' - \omega = k(z - \omega)$$

### 11.3 Rotation de centre $\Omega$ et d'angle $\theta$

$$z' - \omega = e^{i\theta}(z - \omega)$$

**Exemple.** Rotation de centre $O$ et d'angle $\frac{\pi}{2}$ : $z' = iz$.

### 11.4 Similitude directe

Toute transformation $z \mapsto z' = az + b$ avec $a \in \mathbb{C}^*$ et $b \in \mathbb{C}$ est une **similitude directe** :

- si $a = 1$ : translation de vecteur $b$ ;
- si $a \neq 1$ : elle possède un unique point fixe $\omega = \dfrac{b}{1 - a}$ (le centre), et elle est la composée d'une rotation d'angle $\arg(a)$ et d'une homothétie de rapport $|a|$ de centre $\omega$.

### 11.5 Symétries et réflexions

- Symétrie centrale de centre $\Omega$ : $z' = 2\omega - z$.
- Réflexion d'axe $(Ox)$ : $z' = \bar{z}$.
- Inversion de centre $O$ et de rapport $1$ : $z' = \dfrac{1}{\bar{z}}$.

---

## 12. Polynômes complexes

### 12.1 Théorème de d'Alembert-Gauss

> **Théorème (admis).** Tout polynôme non constant à coefficients complexes admet au moins une racine dans $\mathbb{C}$.
>
> On dit que $\mathbb{C}$ est **algébriquement clos**.

**Conséquence.** Tout polynôme $P$ de degré $n \geq 1$ à coefficients complexes est **scindé** dans $\mathbb{C}$ :
$$P(z) = a_n(z - z_1)(z - z_2)\cdots(z - z_n)$$
où les $z_i$ sont les racines comptées avec multiplicité.

### 12.2 Polynômes à coefficients réels

Si $P \in \mathbb{R}[X]$ et $z_0 \in \mathbb{C}$ est racine de $P$, alors $\bar{z_0}$ est aussi racine de $P$, avec la même multiplicité.

**Conséquence.** Les polynômes irréductibles de $\mathbb{R}[X]$ sont de degré 1 ou de degré 2 (avec $\Delta < 0$).

### 12.3 Factorisation de $z^n - 1$

$$z^n - 1 = \prod_{k=0}^{n-1}\left(z - e^{2ik\pi/n}\right)$$

---

## 13. Exercices corrigés

### Exercice 1 — Forme algébrique

Écrire sous forme algébrique : $\;Z = \dfrac{(1 + 2i)^2}{3 - i} + \dfrac{1}{i}$.

<details>
<summary><strong>Corrigé</strong></summary>

- $(1 + 2i)^2 = 1 + 4i - 4 = -3 + 4i$.
- $\dfrac{-3 + 4i}{3 - i} = \dfrac{(-3 + 4i)(3 + i)}{10} = \dfrac{-9 - 3i + 12i - 4}{10} = \dfrac{-13 + 9i}{10}$.
- $\dfrac{1}{i} = -i$.

$$Z = -\frac{13}{10} + \frac{9}{10}i - i = -\frac{13}{10} - \frac{1}{10}i.$$
</details>

### Exercice 2 — Forme trigonométrique

Déterminer le module et un argument de $z = -\sqrt{3} + i$, puis de $z^{6}$.

<details>
<summary><strong>Corrigé</strong></summary>

- $|z| = \sqrt{3 + 1} = 2$.
- $\cos\theta = -\frac{\sqrt{3}}{2}$, $\sin\theta = \frac{1}{2}$, donc $\theta = \frac{5\pi}{6}$.
- $z = 2e^{5i\pi/6}$.
- $z^6 = 2^6e^{i\,5\pi} = 64e^{i\pi} = -64$. Module $64$, argument $\pi$.
</details>

### Exercice 3 — Lieu géométrique

Déterminer l'ensemble des points $M(z)$ tels que $\left|\dfrac{z - 1}{z + i}\right| = 1$.

<details>
<summary><strong>Corrigé</strong></summary>

Pour $z \neq -i$ : $|z - 1| = |z + i| \iff MA = MB$ avec $A(1)$ et $B(-i)$.

C'est la **médiatrice** du segment $[AB]$, c'est-à-dire la droite d'équation $y = -x$ (puisque $A(1, 0)$, $B(0, -1)$ ; vérification : $(x-1)^2 + y^2 = x^2 + (y+1)^2 \iff -2x + 1 = 2y + 1 \iff y = -x$).

Le point $B$ n'est pas sur cette droite, donc l'ensemble est la droite entière.
</details>

### Exercice 4 — Équation du second degré

Résoudre dans $\mathbb{C}$ : $\;z^2 - 2z\cos\theta + 1 = 0$ où $\theta \in \mathbb{R}$.

<details>
<summary><strong>Corrigé</strong></summary>

$\Delta' = \cos^2\theta - 1 = -\sin^2\theta = (i\sin\theta)^2$.

Les solutions sont $z = \cos\theta \pm i\sin\theta$, c'est-à-dire $z = e^{i\theta}$ et $z = e^{-i\theta}$.

(Vérification : produit $= 1$ ✓, somme $= 2\cos\theta$ ✓.)
</details>

### Exercice 5 — Racines de l'unité

Calculer $S = 1 + j + j^2 + \dots + j^{2026}$ où $j = e^{2i\pi/3}$.

<details>
<summary><strong>Corrigé</strong></summary>

Somme géométrique de raison $j \neq 1$ :
$$S = \frac{1 - j^{2027}}{1 - j}.$$
$2027 = 3 \times 675 + 2$, donc $j^{2027} = j^2$ et
$$S = \frac{1 - j^2}{1 - j} = 1 + j = -j^2 = e^{i\pi/3}.$$
</details>

### Exercice 6 — Linéarisation

Linéariser $\sin^4\theta$.

<details>
<summary><strong>Corrigé</strong></summary>

$$\sin^4\theta = \left(\frac{e^{i\theta} - e^{-i\theta}}{2i}\right)^4 = \frac{1}{16}\left(e^{4i\theta} - 4e^{2i\theta} + 6 - 4e^{-2i\theta} + e^{-4i\theta}\right)$$

$$= \frac{1}{16}\left(2\cos 4\theta - 8\cos 2\theta + 6\right) = \frac{\cos 4\theta - 4\cos 2\theta + 3}{8}.$$
</details>

### Exercice 7 — Géométrie

Soient $A(1)$, $B(3 + i)$ et $C(2 + 2i)$. Déterminer la nature du triangle $ABC$.

<details>
<summary><strong>Corrigé</strong></summary>

$$\frac{c - a}{b - a} = \frac{1 + 2i}{2 + i} = \frac{(1 + 2i)(2 - i)}{5} = \frac{2 - i + 4i + 2}{5} = \frac{4 + 3i}{5}.$$

Ce quotient a pour module $1$ : donc $AB = AC$, isocèle en $A$. Il n'est ni réel ni imaginaire pur et ne vaut pas $e^{\pm i\pi/3}$ : le triangle est **isocèle en $A$**, non rectangle, non équilatéral.
</details>

### Exercice 8 — Rotation

Donner l'écriture complexe de la rotation de centre $\Omega(1 + i)$ et d'angle $\dfrac{\pi}{3}$, puis l'image de $O$.

<details>
<summary><strong>Corrigé</strong></summary>

$z' - (1 + i) = e^{i\pi/3}\,(z - (1 + i))$.

Pour $z = 0$ : $z' = (1 + i) - e^{i\pi/3}(1 + i) = (1 + i)\left(1 - \frac{1}{2} - i\frac{\sqrt{3}}{2}\right) = (1 + i)\,\frac{1 - i\sqrt{3}}{2}$

$$z' = \frac{1 - i\sqrt{3} + i + \sqrt{3}}{2} = \frac{1 + \sqrt{3}}{2} + i\,\frac{1 - \sqrt{3}}{2}.$$
</details>

---

## 14. Fiche de synthèse

### Les trois formes d'un complexe non nul

| Forme | Écriture | Utile pour |
|---|---|---|
| Algébrique | $z = a + ib$ | additions, parties réelle et imaginaire |
| Trigonométrique | $z = r(\cos\theta + i\sin\theta)$ | passage entre formes |
| Exponentielle | $z = re^{i\theta}$ | produits, quotients, puissances |

### Formules à retenir

$$z\bar{z} = |z|^2 \qquad \operatorname{Re}(z) = \frac{z + \bar{z}}{2} \qquad \operatorname{Im}(z) = \frac{z - \bar{z}}{2i}$$

$$|zz'| = |z||z'| \qquad \arg(zz') = \arg z + \arg z'$$

$$e^{i\theta} = \cos\theta + i\sin\theta \qquad \cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2} \qquad \sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i}$$

$$(e^{i\theta})^n = e^{in\theta} \qquad e^{i\pi} = -1$$

$$z^n = 1 \iff z = e^{2ik\pi/n},\; k \in \{0, \dots, n-1\}$$

$$\arg\frac{d - c}{b - a} \equiv (\vec{AB}, \vec{CD}) \pmod{2\pi}$$

### Pièges classiques

1. Oublier que $\operatorname{Im}(z)$ est un **réel**.
2. Écrire une inégalité entre complexes non réels.
3. Utiliser $\arctan(b/a)$ sans tenir compte du quadrant.
4. Écrire $\sqrt{-4} = 2i$ **sans précaution** : on écrit plutôt « $z^2 = -4 \iff z = \pm 2i$ ». Le symbole $\sqrt{\ }$ est réservé aux réels positifs.
5. Appliquer $\sqrt{ab} = \sqrt{a}\sqrt{b}$ avec $a, b < 0$ : $\sqrt{(-1)(-1)} \ne \sqrt{-1}\sqrt{-1}$.
6. Donner un module négatif lors de la factorisation par l'angle moitié.
7. Oublier que l'argument est défini **modulo $2\pi$**.

### Méthodes types

| Je dois… | Je fais… |
|---|---|
| Calculer un quotient | Multiplier par le conjugué du dénominateur |
| Calculer $z^n$ | Passer en forme exponentielle |
| Prouver $z \in \mathbb{R}$ | Vérifier $z = \bar{z}$ ou $\arg z \equiv 0 \pmod \pi$ |
| Prouver $z \in i\mathbb{R}$ | Vérifier $z = -\bar{z}$ |
| Linéariser | Formules d'Euler + binôme |
| Exprimer $\cos n\theta$ | Moivre + binôme |
| Résoudre $z^n = a$ | Forme exponentielle de $a$ et racines $n$-ièmes |
| Étudier un triangle | Calculer $\dfrac{c - a}{b - a}$ |

---

*Fin du cours.*
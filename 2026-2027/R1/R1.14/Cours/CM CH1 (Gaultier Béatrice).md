---
aliases:
  - Cours 1.1.1
---
# WIMS - Inscription et exercices de trigonométrie

## Inscription sur WIMS

1. Aller sur **WIMS Côte d'Azur**.
2. Sélectionner l'établissement **IUT Roanne**.
3. Choisir la classe **RT2026**.
4. Cliquer sur **S'inscrire**.
5. Utiliser comme identifiant celui indiqué sur la **carte étudiant**.

---

## Exercice - Conversions et trigonométrie

### 1. Conversions degrés / radians

1. $87° \times \dfrac{\pi}{180} \approx 1{,}52 \text{ rad}$
2. $180°$
3. $585°$

> [!info] Correction
> $87 \times \dfrac{\pi}{180} \approx 1{,}5184$ rad, ce qui arrondit à **1,52 rad**, pas 1,51 rad. Les points 2 et 3 sont repris tels quels : l'énoncé exact des questions n'est pas présent dans les notes de départ pour pouvoir les revérifier indépendamment.

### 2. Valeurs de cos et sin

4. $\cos\left(\dfrac{\pi}{4{,}5}\right) = \cos\left(\dfrac{2\pi}{9}\right) \approx 0{,}766$
   $\sin\left(\dfrac{\pi}{4{,}5}\right) = \sin\left(\dfrac{2\pi}{9}\right) \approx 0{,}643$

5. $\cos(163°) = \cos\left(\dfrac{163\pi}{180}\right) \approx -0{,}956$
   $\sin(163°) = \sin\left(\dfrac{163\pi}{180}\right) \approx 0{,}292$

6. $\cos(20°) = \cos\left(\dfrac{\pi}{9}\right) \approx 0{,}940$
   $\sin(20°) = \sin\left(\dfrac{\pi}{9}\right) \approx 0{,}342$

> [!info] Correction de notation
> Les écritures "cos(π/180/163)" et "cos(π/180/20)" des notes de départ étaient ambiguës (lues comme une division en trop). La bonne écriture est $\dfrac{163\pi}{180}$ et $\dfrac{20\pi}{180} = \dfrac{\pi}{9}$, ce qui correspond bien aux résultats numériques donnés.

### 3. Valeurs pour des angles en multiples de π

7. $\cos(0{,}9\pi) \approx -0{,}95 \qquad \sin(0{,}9\pi) \approx 0{,}309$
   $\cos(4{,}91\pi) \approx -0{,}96 \qquad \sin(4{,}91\pi) \approx 0{,}278$

> [!info] Correction
> $\sin(0{,}9\pi)$ vaut environ **0,309** (et non 0,342, qui est en réalité la valeur de $\sin(20°)$ trouvée juste au-dessus — probablement une confusion entre deux lignes de calcul). Les trois autres valeurs de cette question étaient correctes.

### 4. Identité trigonométrique

$$
\begin{aligned}
1 + \tan^2(x) &= 1 + \frac{\sin^2(x)}{\cos^2(x)} \\
&= \frac{\cos^2(x)}{\cos^2(x)} + \frac{\sin^2(x)}{\cos^2(x)} \\
&= \frac{\cos^2(x) + \sin^2(x)}{\cos^2(x)} \\
&= \frac{1}{\cos^2(x)}
\end{aligned}
$$

en utilisant l'identité $\cos^2(x) + \sin^2(x) = 1$.

> [!info] Correction
> La première ligne écrivait "1 + tan(x)" sans le carré, alors que toute la suite de la démonstration utilise bien $\tan^2(x)$. L'identité démontrée ici est la relation classique $1 + \tan^2(x) = \dfrac{1}{\cos^2(x)}$.

## Points à vérifier avec le support de cours original

- Énoncés exacts des questions 2 et 3 de la partie 1 (non présents dans les notes de départ)
- Confirmer que la confusion sur $\sin(0{,}9\pi)$ vient bien d'une erreur de recopiage et pas d'un énoncé différent

---
title: "TP1 : signaux continus"
module: R104 - Fondamentaux des circuits électroniques
formation: BUT 1ère année S1
competences:
  - RT1 Administrer (coef. 8)
  - RT2 Connecter (coef. 5)
nom:
prenom:
groupe:
tags:
  - BUT1
  - R104
  - TP
  - electronique
  - signaux-continus
---

# Travaux Pratiques 1 : signaux continus

**BUT 1ère année S1 — R104 : Fondamentaux des circuits électroniques**

| Nom | Prénom | Groupe |
| --- | ------ | ------ |
|     |        |        |

## Compétences ciblées

- **RT1 Administrer** (coef. 8)
- **RT2 Connecter** (coef. 5)

## Apprentissages critiques

- Niveau 1 de la compétence RT1 (**AC0111**) : maîtriser les lois fondamentales de l'électricité afin d'intervenir sur des équipements de réseaux et télécommunications.
- Niveau 1 de la compétence RT2 (**AC0211**) : mesurer et analyser les signaux.

Les objectifs de la manipulation sont de vous familiariser avec les appareils de mesure avec lesquels vous allez travailler sur une dizaine de modules durant vos trois années à l'IUT.

---

## 1. Objectifs de la séance de manipulation

- Savoir utiliser un **ALS 6MC** (générateur de tension continue).
- Savoir utiliser un **multimètre**.
- Savoir mesurer une **tension continue** et un **courant continu**.

## Consignes du TP

> [!warning] Règles de validation
> **C1** : vous devez faire valider **2 questions Qn et Qn+1** par un enseignant.
> **C2** : vous ne pouvez passer à la question **Qn+2** que si C1 est remplie.

Les cases de validation sont notées `- [ ]`.

---

## 2. Présentation du matériel

| Appareil | Référence |
| --- | --- |
| Alimentation continue | **ALS 6MC** |
| Multimètre numérique | **FI 2803 MT** |
| Générateur basse fréquence (GBF) | **FI 5110** ou **GFG 2110** |
| Oscilloscope | **Tektronix TDS 2012B** |

> [!note] Photos du matériel
> Les photos des 4 appareils (ALS 6MC, FI 2803 MT, GBF FI 5110 / GFG 2110, TDS 2012B) sont à insérer ici : `![[ALS_6MC.png]]`, `![[FI2803MT.png]]`, `![[GBF.png]]`, `![[TDS2012B.png]]`.

### Q1 à Q4 — Les appareils et le multimètre

- [ ] **Q1.** Lister exhaustivement les 4 appareils à disposition (voir doc en annexe sur Moodle).

  **Réponse :**

  &nbsp;

- [ ] **Q2.** Identifier et donner les fonctions de chaque appareil.

  **Réponse :**

  &nbsp;

- [ ] **Q3.** Énumérer toutes les grandeurs physiques mesurables par le multimètre ?

  **Réponse :**

  &nbsp;

- [ ] **Q4.** Comment branche-t-on un voltmètre et un ampèremètre ?

  **Réponse :**

  &nbsp;

---

### Q5 à Q8 — Mesure du courant et alimentation ALS 6MC

- [ ] **Q5.** Dessiner le branchement du multimètre pour mesurer le courant $I$ en connectant la figure ci-dessous avec les dipôles résistance (R) et générateur (G) ?

  > [!note] Figure Q5
  > Le générateur **G** (avec ses bornes **+** et **−**) et la résistance **R** sont placés de part et d'autre du multimètre FI 2803 MT (bornes `10Amax`, `µAmA`, `HzΩ mV`, `COM`, `V`). Il faut relier les trois éléments.
  > `![[Q5_multimetre_G_R.png]]`

  **Réponse (schéma) :**

  &nbsp;

- [ ] **Q6.** En vous aidant de la documentation du multimètre sur **Moodle**, donner la valeur maximale du courant $I$ mesurable sur la position **mA** ?

  **Réponse :**

  &nbsp;

- [ ] **Q7.** Repérer sur la figure 1 ci-dessous (au stylo) les **4 zones** disponibles de l'alimentation. Cibler la zone de l'alimentation variable et indiquer les trois autres tensions fixes disponibles.

  > [!note] Fig. 1 — Face avant de l'ALS 6MC
  > Zones visibles sur la face avant : **30 V – 1 A**, **REFERENCES**, **± 15 V – 0,2 A**, **5 V – 1 A**.
  > `![[Fig1_ALS6MC.png]]`

  **Réponse :**

  &nbsp;

- [ ] **Q8.** Sur l'alimentation variable, régler une tension de **13,5 V** avec un courant de **0,5 A**.

---

### Q9 à Q11 — Mesures sur l'alimentation

- [ ] **Q9.** Mesurer les 5 tensions des 4 sorties de l'alimentation à l'aide du multimètre.

  | Sortie | Tension mesurée |
  | --- | --- |
  | Alimentation variable (30 V – 1 A) |  |
  | Références |  |
  | +15 V |  |
  | −15 V |  |
  | 5 V – 1 A |  |

- [ ] **Q10.** Que signifie l'indication **30V-1A** ?

  **Réponse :**

  &nbsp;

- [ ] **Q11.** Tracer la caractéristique idéale $U = f(I)$ en reprenant les valeurs de Q8.

  **Réponse (graphe) :**

  &nbsp;

---

### Q12 à Q14 — Résistances et plaque à trous

- [ ] **Q12.** En vous aidant du document ci-joint, indiquer le mode de fonctionnement du code des couleurs des résistances.

  **Réponse :**

  &nbsp;

- [ ] **Q13.** Donner le code des couleurs des résistances suivantes : $R_1 = 8{,}2\,\text{k}\Omega$ et $R_2 = 2{,}7\,\text{k}\Omega$.

  | Résistance | Valeur | Bande 1 | Bande 2 | Bande 3 | Tolérance |
  | --- | --- | --- | --- | --- | --- |
  | $R_1$ | 8,2 kΩ |  |  |  |  |
  | $R_2$ | 2,7 kΩ |  |  |  |  |

- [ ] **Q14.** À partir de la documentation en ligne sur **Moodle**, donner le fonctionnement d'une plaque à trous (appelée aussi plaque d'essai).

  **Réponse :**

  &nbsp;

---

### Q15 — Le diviseur de tension

- [ ] **Q15.** Soit le montage suivant (Fig. 2) :

  ```mermaid
  flowchart LR
      Ve(("Ve")) -->|"I"| R1["R1"]
      R1 --> N(("Vs"))
      N --> R2["R2"]
      R2 --> GND["Masse 0 V"]
      Ve -.-> GND
  ```

  > [!note] Fig. 2
  > Source $V_e$ → résistance $R_1$ (courant $I$) → nœud de sortie $V_s$ → résistance $R_2$ → masse. $V_s$ est la tension aux bornes de $R_2$.

  - **Q15.a.** Déterminer la relation liant $V_s$ à $V_e$, $R_1$ et $R_2$.

    **Réponse :**

    $$V_s = $$

  - **Q15.b.** Calculer $V_s$ dans les deux cas suivants :
    - $R_1 = 8{,}2\,\text{k}\Omega$ ; $R_2 = 2{,}7\,\text{k}\Omega$ ; $V_e = 8\,\text{V}$.
    - $R_1 = 1\,\text{M}\Omega$ ; $R_2 = 10\,\text{M}\Omega$ ; $V_e = 8\,\text{V}$.

    **Réponse :**

    &nbsp;

---

### Q16 à Q18 — Schéma expérimental et câblage

- [ ] **Q16.** Réaliser le schéma expérimental du montage de Q15 en plaçant le multimètre afin de mesurer $V_s$.

  **Réponse (schéma) :**

  &nbsp;

- [ ] **Q17.** Indiquer sur le schéma expérimental les deux bornes utilisées pour mesurer $V_s$. Quel mode **AC** ou **DC** convient à la mesure ?

  **Réponse :**

  &nbsp;

- [ ] **Q18.** Réaliser le câblage sur la plaque à trous en utilisant des petits fils pour connecter les composants entre eux :
  1. La borne **noire** sera la **masse (0 V)**.
  2. La borne **rouge** sera l'**entrée $V_e$**.
  3. La borne **verte** sera la **sortie $V_s$**.

---

### Q19 à Q20 — Mesures et résistance interne du multimètre

- [ ] **Q19.** Mesurer $V_s$ (pour $R_1 = 8{,}2\,\text{k}\Omega$ ; $R_2 = 2{,}7\,\text{k}\Omega$ ; $V_e = 8\,\text{V}$).

  $V_S = \_\_\_\_\_\_\_\_$

- **Q20.** Modifier le montage précédent en remplaçant seulement les résistances et en prenant $R_1 = 1\,\text{M}\Omega$ ; $R_2 = 10\,\text{M}\Omega$. On fixe maintenant $V_e = 8{,}5\,\text{V}$.

  - **Q20.a.** Mesurer $V_s$ à l'aide du multimètre.

    $V_S = \_\_\_\_\_\_\_\_$

  - **Q20.b.** Calculer $V_s$ avec la relation de Q15.a.

    **Réponse :**

    &nbsp;

  - **Q20.c.** Que constate-t-on par rapport à la valeur théorique de $V_s$ (Q20.b) ? Réaliser un schéma de câblage (cadre pointillé) en tenant compte du schéma interne simplifié des appareils, puis retrouver cette mesure par le calcul en tenant compte de la résistance interne du multimètre $R_E = 10\,\text{M}\Omega$.

    > [!important]
    > Vous devrez **relier le schéma de câblage aux deux points noirs de la résistance $R_E$**.

    > [!note] Fig. 3
    > Un cadre pointillé (zone de dessin à compléter) est relié par deux points noirs à la résistance $R_E$ située dans le bloc « Appareil de mesure ».

    **Constat :**

    &nbsp;

    **Schéma de câblage et calcul :**

    &nbsp;

---

### Q21 à Q30 — Pont de résistances

- [ ] **Q21.** On considère le montage (pont de résistances) suivant, alimenté en tensions symétriques $V_e = \pm 15\,\text{V}$. Vous utiliserez seulement deux bornes comme suit :

  | Borne | Tension |
  | --- | --- |
  | **Rouge** | $+15\,\text{V}$ |
  | **Bleue** | $-15\,\text{V}$ |
  | **Noire** | non utilisée |

  > [!note] Fig. 4
  > Trois résistances en série $R_1$, $R_2$, $R_3$ aux bornes de la tension $v_e$, traversées par le courant $i_e$.
  > $R_1 = R_2 = R_3 = 10\,\text{k}\Omega$, $\tfrac14\,\text{W}$.
  > L'alimentation $V_e$ fournit $+15\,\text{V}$ (borne du haut) et $-15\,\text{V}$ (borne du bas).

  ```mermaid
  flowchart TB
      P["+15 V (borne rouge)"] -->|"i_e"| R1["R1 = 10 kΩ"]
      R1 --> R2["R2 = 10 kΩ"]
      R2 --> R3["R3 = 10 kΩ"]
      R3 --> M["-15 V (borne bleue)"]
  ```

  Réaliser le schéma expérimental sur la figure 4 afin de mesurer le courant $i_e$.

  **Réponse (schéma) :**

  &nbsp;

- [ ] **Q22.** Indiquer les bornes de l'alimentation utilisées ainsi que celles du multimètre.

  **Réponse :**

  &nbsp;

- [ ] **Q23.** Réaliser le câblage de la Fig. 4 **hors tension** sur la plaque à trous. Faites-le valider par le professeur.

- [ ] **Q24.** Mesurer le courant $i_e$.

  $i_e = \_\_\_\_\_\_\_\_$

- [ ] **Q25.** Vérifier la loi d'Ohm pour chaque dipôle.

  **Réponse :**

  &nbsp;

- [ ] **Q26.** Réaliser le schéma expérimental pour mesurer la ddp (différence de potentiels) aux bornes de la résistance $R_2$ ($U_{R2}$).

  **Réponse (schéma) :**

  &nbsp;

- [ ] **Q27.** Mesurer la ddp aux bornes des dipôles $R_1$ et $R_3$, notées $U_{R1}$ et $U_{R3}$, et celle aux bornes des trois réunies. Vérifier la loi des mailles.

  | Grandeur | Valeur mesurée |
  | --- | --- |
  | $U_{R1}$ |  |
  | $U_{R2}$ |  |
  | $U_{R3}$ |  |
  | $U_{R1+R2+R3}$ |  |

  **Vérification de la loi des mailles :**

  &nbsp;

- [ ] **Q28.** Calculer la puissance totale par effet Joule du dipôle constitué des résistances $R_1$, $R_2$ et $R_3$.

  **Réponse :**

  &nbsp;

- [ ] **Q29.** En déduire la puissance par effet Joule d'une résistance.

  **Réponse :**

  &nbsp;

- [ ] **Q30.** La puissance calculée à la question précédente est-elle adaptée ?

  **Réponse :**

  &nbsp;

---

> [!tip] Rappels utiles
> - Loi d'Ohm : $U = R \cdot I$
> - Puissance par effet Joule : $P = U \cdot I = R \cdot I^2 = \dfrac{U^2}{R}$
> - Loi des mailles : la somme algébrique des tensions le long d'une maille fermée est nulle.
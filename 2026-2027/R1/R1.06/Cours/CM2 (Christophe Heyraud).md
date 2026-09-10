---
aliases:
  - Cours 1.1.1
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

---

## 3. Structure d'un microcontrôleur

*(à compléter)*

---

## 4. Langage de programmation

*(à compléter)*

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
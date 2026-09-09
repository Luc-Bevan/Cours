---
aliases:
  - Cours 1.1.1
---

# Habilitation électrique - Risques et prévention

*(Mettre le cours précédent ici)*

## 1. Électricité statique

L'électricité statique peut endommager facilement des cartes électroniques, donc il faut prendre des précautions, surtout par temps sec.

Il est donc nécessaire de se décharger en touchant la broche de terre des prises (la barre métallique) avant de manipuler du matériel sensible.

![[Pasted image 20260908151417.png|186]]

Entre nos mains et nos pieds, on considère généralement une résistance du corps humain de l'ordre de **1000 à 2000 ohms** (valeur qui varie fortement selon l'humidité de la peau et les conditions de contact — à confirmer avec la valeur exacte donnée en cours, car les sources varient parfois entre 1000 et 5000 ohms selon les conditions).

## 2. Info flash : PoE (Power over Ethernet)

Alimentation par le câble réseau : il est nécessaire d'avoir un switch PoE ou un routeur/injecteur PoE pour fournir l'alimentation électrique en même temps que les données.

## 3. Gravité des risques électriques

Les risques électriques comptent 1 mort pour 86 arrêts de travail, alors que pour l'ensemble des accidents du travail toutes causes confondues, on compte 1 mort pour 1237 arrêts de travail.

**Les risques électriques sont donc beaucoup plus graves que la moyenne des accidents du travail.**

## 4. Répartition des causes d'accidents

- 10 % : défaillance matérielle
- 14 % : défaut de formation
- 15 % : omission d'étape ou procédure inexacte
- 30 % : ignorance des risques
- 31 % : mode opératoire inapproprié ou dangereux

On retrouve le même constat qu'en cybersécurité : les risques sont principalement dus à l'erreur humaine ou à l'ignorance, plus qu'à une défaillance purement matérielle.

## 5. Analyse du risque électrique

L'analyse du risque électrique doit précéder toute opération d'ordre électrique ou non électrique, afin de définir et de mettre en place, lors des opérations, les mesures de prévention appropriées pour la protection des personnes et des biens. Cette analyse doit être menée en prenant en compte notamment les risques présentés *(phrase incomplète dans les notes de départ — probablement suivie de "par l'installation, l'environnement de travail, etc." : à compléter avec le support de cours).*

- L'évènement déclencheur est caractérisé par sa **probabilité d'apparition**.
- Le dommage est caractérisé par sa **gravité**.

## 6. Ouvrage vs installation

- **Ouvrage** : ligne appartenant à EDF, Enedis, RTE, ou à une collectivité locale (réseau public).
- **Installation** : tout le reste, c'est-à-dire le domaine privé.

*Correction : "Inédice" dans les notes de départ était une coquille pour Enedis (le gestionnaire du réseau de distribution électrique en France, anciennement ERDF).*

## 7. Types de résultats d'un danger

- Blessure superficielle sans arrêt
- Blessure grave avec arrêt de travail
- Blessure avec séquelle
- Décès

## 8. Processus d'apparition d'un dommage (exemple)

1. Tirer sur un câble
2. Travailler à proximité de pièces nues sous tension
3. Contact avec pièces nues sous tension
4. Résultant en une électrocution

*Correction : "2lectrocution" corrigé en "électrocution" (coquille de saisie).*

## 9. Contacts directs et indirects

En basse tension, pour être électrisé, il faut nécessairement un contact avec une pièce nue (contrairement à la haute tension, où un amorçage/arc électrique peut se produire à distance sans contact direct, voir section 10).

Il existe deux types de contacts :

- **Contact direct** : contact avec une pièce normalement sous tension (un conducteur nu, une borne, etc.).
- **Contact indirect** : contact avec une masse métallique qui n'est pas censée être sous tension, mais qui l'est devenue à cause d'un défaut d'isolement. Ce cas peut survenir même si la masse est reliée à la terre, s'il n'y a pas de protection différentielle pour couper l'alimentation à temps — l'installation n'est alors pas aux normes.

![[Pasted image 20260908153126.png|207]]

99 % des incidents mortels sont dus à des contacts directs.

Il est très rare d'avoir des incidents mortels par contact indirect, car on sait très bien s'en protéger, à condition que le lieu de l'incident soit aux normes (mise à la terre + protection différentielle fonctionnelle).

Si toutes les installations étaient aux normes, il ne devrait plus y avoir d'incidents par contact indirect. Néanmoins, le risque zéro n'existe pas.

*Correction grammaticale : "il ne devraient plus y avoir" corrigé en "il ne devrait plus y avoir" (le sujet est le "il" impersonnel, donc le verbe reste au singulier).*

Il existe des protections contre les contacts directs, telles que l'isolation des outils, ou une protection isolante du corps lui-même (gants isolants, tapis isolants, etc.).

## 10. Amorçage et tension de pas

Les amorçages surviennent lorsque la distance diminue : l'amorçage se produit dès que la distance dans l'air ne suffit plus à assurer l'isolement (le phénomène concerne surtout les situations à distance, typiquement en haute tension).

La **tension de pas** est la tension qui apparaît entre nos deux pieds lorsqu'un courant intense circule dans le sol (par exemple lors d'un défaut électrique important ou de la foudre), créant un gradient de potentiel entre les deux points d'appui au sol.

## Points à vérifier avec le support de cours original

- Valeur exacte de la résistance du corps humain donnée en cours (1000-2000 ohms proposé ici, à confirmer)
- Suite de la phrase sur l'analyse du risque électrique (section 5), coupée dans les notes de départ
- Contenu du cours précédent à insérer en haut de la note
- Source exacte des statistiques (1 mort pour 86 arrêts de travail, 99 % des incidents mortels par contact direct)
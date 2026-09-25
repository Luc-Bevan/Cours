---
aliases:
  - TD1.1.1
---
# R1.09 · Module 1 — Comment fonctionne le Web

*BUT R&T 1re année · Ressource R1.09 · Durée : environ 1h15 (TD)*

> [!tip] 🎯 Ce que vous saurez faire à la fin
> - Expliquer ce qui se passe entre le moment où vous tapez une adresse et le moment où la page s'affiche
> - Décortiquer une URL
> - Ouvrir les outils de développement d'un navigateur et retrouver dans le code n'importe quel élément visible
> - Reconnaître la structure commune à toutes les pages web
> - Dire pourquoi les accents deviennent parfois illisibles

## 1. Le modèle client-serveur

Un site web, ce sont des **fichiers** stockés sur une machine allumée en permanence : le **serveur**.

Votre navigateur est le **client**. Il demande, le serveur répond.

1. Vous tapez une adresse
2. Le navigateur cherche à quelle adresse IP correspond le nom de domaine (rôle du **DNS**)
3. Il envoie une **requête HTTP** à cette machine
4. Le serveur renvoie le **contenu des fichiers**, tel quel
5. Le navigateur lit ce contenu et **reconstruit** la page chez vous

> [!important] Point important
> La page que vous voyez n'existe nulle part sous cette forme. Elle est reconstruite sur votre poste, à chaque visite, à partir de fichiers texte.

> [!info] Conséquence directe
> Quand vous modifiez quelque chose dans les outils de développement, vous modifiez votre copie. Le serveur n'en sait rien. Un rafraîchissement de la page remet tout en place.

## 2. L'anatomie d'une URL

`https://www.exemple.fr:443/documents/index.html`

| Partie | Nom | Rôle |
|---|---|---|
| https | protocole | comment on parle au serveur |
| www.exemple.fr | nom de domaine | quelle machine (traduit en IP par le DNS) → *Domain Name System*, ou système de noms de domaine |
| 443 | port | quel service sur cette machine (souvent implicite) — :443 → https, :80 → http |
| /documents/index.html | chemin | quel fichier, dans quel dossier. Aussi appelé « ressource », un terme que vous reverrez plus tard |

Le chemin dans l'URL correspond à une **arborescence de dossiers** sur le serveur. C'est la même logique que sur votre disque dur.

## 3. Ce que le serveur envoie vraiment

Le raccourci **Ctrl+U** (ou **Cmd+U** pour mac) affiche le **code source** : exactement ce que le serveur a envoyé.

- Sur une page simple, tout ce que vous voyez à l'écran est lisible dans le code.
- Sur un gros site, le code est illisible. Trois raisons : il est **compressé** pour réduire la quantité de données transférées, il est **généré par des outils** plutôt que tapé à la main, et une partie de la page est **assemblée par le navigateur après coup**.

Un site illisible n'est pas d'une autre nature qu'une page simple. Il est juste plus rempli.

## 4. L'inspecteur : relier le visible au code

Allez sur [le site de l'UJM](https://www.univ-st-etienne.fr/fr/index.html)

Clic droit sur un élément de la page → **Inspecter**.

- Le panneau s'ouvre et **surligne tout seul** la ligne correspondante. Vous n'avez rien à déchiffrer : vous constatez.
- En survolant une ligne de code, la **zone correspondante s'allume** sur la page.
- L'outil de sélection (l'icône en forme de curseur, en haut à gauche du panneau) fait l'inverse : vous pointez, il vous emmène au code.

Ce que ça montre : **une page est faite de boîtes emboîtées dans d'autres boîtes**. Cette idée resservira pour l'architecture de vos pages et pour le CSS.

Attention à la différence :

- Ctrl+U montre **ce que le serveur a envoyé**
- L'inspecteur montre **ce que le navigateur a construit**

Sur une page simple, c'est identique. Sur un site moderne, non.

## 5. La structure commune à toutes les pages

Dans l'inspecteur, repliez tous les éléments. Il ne reste que ceci, sur n'importe quel site du monde :

```html
<!DOCTYPE html>
<html>
<head>
...
</head>
<body>
...
</body>
</html>
```

C'est la même logique qu'une **trame réseau** :

| Trame réseau | Page HTML |
|---|---|
| En-tête : pour les machines | head : pour le navigateur |
| Données : l'information utile | body : ce que voit l'humain |

Le head ne s'affiche jamais et pourtant rien ne fonctionne correctement sans lui.

Deux vérifications à faire vous-même dans l'inspecteur :

- modifiez le title → le nom de l'onglet change, la page ne bouge pas

## 6. L'encodage des caractères

Vous avez tous déjà reçu un mail, ouvert un fichier ou visité une page où les accents étaient remplacés par des symboles bizarres :

- Écrit : *Réservez votre place à l'événement*
- Lu : *RÃ©servez votre place Ã l'Ã©vÃ©nement*

Les octets sont **exactement les mêmes** dans les deux cas. Ce qui change, c'est la **table de correspondance** utilisée pour les relire. Celui qui a écrit et celui qui lit ne se sont pas mis d'accord.

Un texte, dans une machine, ce n'est pas « du texte » : ce sont des octets, plus une convention pour les interpréter. Exactement comme une trame lue avec le mauvais protocole.

D'où la ligne `<meta charset="UTF-8">` dans le head : elle annonce la convention utilisée, pour que le navigateur n'ait pas à deviner. **UTF-8 sait tout écrire** (accents, alphabets non latins, émojis) : c'est pour ça qu'il s'est imposé. On l'écrit toujours.

## 7. Pourquoi les noms de balises comptent

Les balises ne servent pas simplement à faire joli : elles donnent une **sémantique** au contenu, c'est-à-dire qu'elles lui **donnent du sens**. Elles permettent ainsi aux machines de comprendre la structure et le rôle des éléments d'une page sans avoir besoin de la « voir ».

- Un lecteur d'écran, utilisé par une personne avec une déficience visuelle, lit la structure
- Le mode Lecture du navigateur garde le contenu principal et jette le menu — il n'a pas *regardé* la page, il a lu les balises
- Un moteur de recherche fait la même chose pour comprendre de quoi parle la page (le title que vous avez modifié, c'est ce que Google affiche dans ses résultats)

`<nav>` annonce un menu, `<main>` le contenu principal, `<header>` l'en-tête → balises blocs.

`<h1>` annonce un titre, `<p>` un paragraphe, `<a>` un lien/ancre → balises en ligne.

`<div>` ne veut rien dire, mais est très utilisée pour former des boîtes (balise bloc).

**Le rendu à l'écran est identique : la différence n'existe que pour les machines.**

> [!info] À savoir
> L'accessibilité n'est pas une option, c'est une obligation légale pour les sites publics et les entreprises d'une certaine taille (référentiel RGAA en France). Vous la croiserez dans des cahiers des charges.

> [!success] ✅ À retenir en cinq phrases
> 1. Un site, ce sont des fichiers sur une machine ; le navigateur les demande et reconstruit la page chez vous.
> 2. Une URL décrit un protocole, une machine et un chemin de fichier.
> 3. Toute page a la même ossature : html contenant head et body.
> 4. Le head s'adresse aux machines, le body aux humains.
> 5. Un texte est une suite d'octets plus une convention de lecture : c'est l'encodage.

## 📂 Ressources

- [W3docs](https://fr.w3docs.com/learn-html/html-basic)
- [Référentiel RGAA](https://accessibilite.numerique.gouv.fr/)
- [Toute 1ère page du web (1991)](http://info.cern.ch/hypertext/WWW/TheProject.html)

---

# R1.09 · Module 2 — Écrire une page en HTML

*BUT R&T 1re année · Ressource R1.09 · Durée : 35 min de TD + TP 1 (2h)*

## Avant tout : HTML n'est pas de la programmation

HTML est un langage de **balisage**. Il n'y a ni variable, ni condition, ni boucle. Vous ne programmez pas : vous **décrivez**. « Ceci est un titre. Ceci est un paragraphe. Ceci est une image. »
C'est comme la mise en page d'un texte dans Word. On écrit le texte sans tenir compte de la présentation finale.

C'est une bonne nouvelle : il n'y a rien à calculer, il y a du vocabulaire à connaître.

## 1. La règle unique

`<balise>` ouvrante, `</balise>` fermante. Le `/` signale la fermeture.

```html
<p>Ceci est un paragraphe.</p>
```

Quelques balises n'ont pas de contenu et se ferment donc toutes seules : `<img>`, `<br>`, `<meta>`, `<link>`. On dit que ce sont des **balises orphelines**.

Les balises **s'emboîtent** mais ne se croisent jamais :

```html
<p>Un texte avec un <strong>mot important</strong> dedans.</p>
```

## 2. Les attributs

Un attribut est un **réglage** posé dans la balise ouvrante, sous la forme `nom="valeur"`.

```html
<a href="contact.html">Nous contacter</a>
<img src="images/baie.jpg" alt="Baie de brassage du bâtiment C">
```

- `href` : vers où va le lien
- `src` : quelle image afficher
- `alt` : quoi afficher (et quoi lire à voix haute) si l'image ne s'affiche pas

## 3. Le squelette d'une page

À recopier au début de chaque nouvelle page.

```html
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Titre affiché dans l'onglet</title>
</head>
<body>
</body>
</html>
```

- `<!DOCTYPE html>` : annonce au navigateur que ce qui suit est du HTML moderne. On l'écrit, on n'y revient plus.
- `lang="fr"` : dans quelle langue la page est écrite. Utile aux lecteurs d'écran et à la traduction automatique.
- `<meta charset="UTF-8">` : la convention d'encodage (voir module 1).
- `<title>` : le nom de l'onglet, le nom du favori, et ce que les moteurs de recherche affichent.

> [!info] Principe
> On n'ajoute une ligne dans le head qu'au moment où elle sert. Deux autres lignes viendront plus tard, quand vous en aurez besoin (feuille de style, affichage sur mobile).

## 4. Les balises de contenu

```html
<h1>Titre principal de la page</h1>
<h2>Sous-titre</h2>
<h3>Niveau en dessous</h3>
<p>Un paragraphe de texte.</p>
<ul>
<li>Un élément de liste</li>
<li>Un autre</li>
</ul>
<ol>
<li>Première étape</li>
<li>Deuxième étape</li>
</ol>
```

Règles à respecter :

- **un seul** `h1` **par page**, c'est le sujet de la page
- on ne saute pas de niveau : après un h1, un h2, pas un h3 (jusqu'à h6)
- les niveaux de titre décrivent le **plan** du document, pas la taille du texte (la taille, c'est le CSS)

## 5. Les images et le multimédia

```html
<img src="images/switch-c3.jpg" alt="Switch 24 ports installé en baie C3">
```

- rangez vos images dans un dossier `images/`
- l'attribut `alt` **décrit l'image**. `alt="image1"` ou `alt="photo.jpg"` ne sert à personne.
- pensez au poids : une photo de 4 Mo sortie d'un téléphone met plusieurs secondes à charger. Redimensionnez avant d'intégrer.

La vidéo et le son suivent la même logique que les images :

```html
<video src="videos/brassage.mp4" controls></video>
<audio src="audio/consigne.mp3" controls></audio>
```

- `controls` affiche les boutons lecture / pause. Sans lui, rien n'est cliquable.
- même vigilance que pour les images, en plus fort : une vidéo se compte en dizaines de Mo. Le format courant du web est **MP4**. Compressez, ou hébergez la vidéo ailleurs et faites un simple lien.

**D'où viennent vos images ?**

- Une image trouvée dans un moteur de recherche **n'est pas libre** : elle a un auteur et une licence.
- Utilisez des **banques d'images libres** — Unsplash, Pexels, Wikimedia Commons — ou vos propres photos.
- Dans tous les cas, **créditez** : une ligne « Crédits » dans vos mentions légales (auteur et source).
- Votre site est public : publier une image sans en avoir le droit est un problème réel, pas un point de règlement intérieur.

## 6. Les liens et les chemins

```html
<a href="index.html">Accueil</a>
<a href="pages/contact.html">Contact</a>
<a href="../index.html">Retour à l'accueil</a>
<a href="https://www.iut.fr">Site de l'IUT</a>
<a href="#materiel">Aller à la section Matériel</a>
```

- `dossier/fichier.html` : descendre dans un sous-dossier
- `../` : remonter d'un cran
- `#identifiant` : une **ancre**, qui saute à un endroit de la page portant cet id

C'est la première cause de pages cassées : un chemin faux et l'image ou le lien ne fonctionne plus. Le chemin est relatif **au fichier dans lequel vous écrivez**, pas à la racine du site.

## 7. Les balises sémantiques

Elles ne changent rien à l'affichage. Elles disent **à quoi sert** chaque zone.

```html
<body>
<header>
<nav>
<ul>
<li><a href="index.html">Accueil</a></li>
<li><a href="pages/fiche.html">Fiche équipement</a></li>
</ul>
</nav>
</header>
<main>
<section>
<h1>Titre de la page</h1>
<p>Contenu principal.</p>
</section>
</main>
<footer>
<p>Mentions légales</p>
</footer>
</body>
```

Utilisez `<div>` uniquement quand **aucune balise sémantique ne convient**.

## 8. Le formulaire (structure seulement)

```html
<form>
<label for="nom">Votre nom</label>
<input type="text" id="nom" name="nom" required>
<label for="mail">Votre e-mail</label>
<input type="email" id="mail" name="mail" required>
<label for="message">Votre demande</label>
<textarea id="message" name="message" rows="5"></textarea>
<button type="submit">Envoyer</button>
</form>
```

- chaque `label` est relié à son champ par `for` / `id` : sans ça, un lecteur d'écran ne sait pas à quoi correspond le champ
- `type="email"` déclenche une vérification automatique du navigateur
- `required` rend le champ obligatoire

**Ce formulaire n'envoie rien.** Le traitement d'un formulaire, c'est du code côté serveur : ce sera au programme du semestre 2.

## 9. Valider son code

Le validateur officiel : [validator.w3.org](https://validator.w3.org/)

Déposez votre fichier, l'outil liste les erreurs avec le numéro de ligne. Objectif : **zéro erreur**.

Ce n'est pas une coquetterie. Un code invalide s'affiche parfois correctement chez vous et se casse ailleurs (autre navigateur, autre écran, lecteur d'écran).

## Checklist de fin de TP

- [ ] Le squelette est complet : doctype, lang, charset, title
- [ ] Un seul h1 par page, niveaux de titre dans l'ordre
- [ ] Toutes les images ont un alt qui décrit vraiment l'image
- [ ] Tous les liens fonctionnent, y compris après avoir déplacé le dossier
- [ ] Aucun div là où une balise sémantique existe
- [ ] Zéro erreur au validateur W3C

## 📂 Ressources

- [W3docs](https://fr.w3docs.com/learn-html/html-basic)
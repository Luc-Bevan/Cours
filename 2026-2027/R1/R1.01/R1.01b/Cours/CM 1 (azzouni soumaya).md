---
aliases:
  - Cours 1.1.1
---
# R1.01b - Initiation au réseau d'entreprise

## 1. Modèle en couches (contexte général)

Avant de rentrer dans le détail, ce cours se situe surtout au niveau des couches suivantes du modèle TCP/IP (ou OSI) :

- **Couche 2 (liaison de données)** : adresses MAC, trames, ARP.
- **Couche 3 (réseau)** : adresses IP, routage, datagrammes/paquets.
- **Couche 4 (transport)** : TCP et UDP, ports, segments/datagrammes.
- **Couche application** : DNS, FTP, SSH, Telnet, SMTP, etc.

Retenir cet ordre aide à comprendre pourquoi ARP ne sort jamais du réseau local (couche 2) alors que l'IP peut être routée entre réseaux (couche 3).

## 2. Adressage : IP vs MAC

- **IP** = adresse logique, peut changer selon le réseau sur lequel se trouve la machine (une même machine peut avoir plusieurs IP selon les interfaces/réseaux).
- **MAC** = adresse physique, fixe, gravée sur la carte réseau (48 bits, notée en hexadécimal, ex : `00:1A:2B:3C:4D:5E`).
- Une adresse IP publique est **unique au monde** ; une adresse IP privée peut être réutilisée dans plusieurs réseaux locaux différents (voir section sur les plages privées).

### ARP (Address Resolution Protocol)

Sert à faire correspondre une adresse IP à une adresse MAC, puisque sur le réseau local, la transmission des trames se fait réellement via l'adresse MAC (pas l'IP).

Fonctionnement typique :
1. La machine A veut communiquer avec l'IP de la machine B, mais ne connaît pas son adresse MAC.
2. A envoie une requête ARP en broadcast (diffusion) sur le réseau local : "qui a cette IP ?"
3. La machine qui possède cette IP répond en unicast avec son adresse MAC.
4. A stocke l'association IP/MAC dans sa table ARP (cache) pour ne pas avoir à refaire la requête à chaque paquet.

Un protocole ARP ne communique pas au-delà du réseau local (non routable) : c'est une limitation propre à la couche 2. Si la machine cible est sur un autre réseau, c'est l'adresse MAC de la passerelle (routeur) qui sera résolue, pas celle de la machine distante.

### Unité de données selon le protocole

- UDP -> **datagramme**
- TCP -> **segment**

Remarque : dans le vocabulaire strict des couches réseau, on distingue :
- **trame** = unité de la couche 2 (liaison de données)
- **paquet / datagramme IP** = unité de la couche 3 (réseau)
- **segment (TCP) ou datagramme (UDP)** = unité de la couche 4 (transport)

Le cours emploie parfois "trame" pour désigner l'unité TCP, ce qui est un raccourci de langage à corriger si besoin avec le support original.

## 3. Rappel binaire

```
00000000 = 0
00000001 = 1
00000010 = 2
```

Un octet (8 bits) permet de représenter les valeurs de 0 à 255, ce qui explique pourquoi chaque partie d'une adresse IPv4 (notation décimale pointée) va de 0 à 255.

Exemple utile pour comprendre le masque : `255.255.255.0` en binaire donne `11111111.11111111.11111111.00000000`, soit 24 bits à 1 -> c'est un masque `/24`.

## 4. Organismes d'attribution des adresses IP

Hiérarchie de distribution des adresses IP dans le monde :

**IANA** (Internet Assigned Numbers Authority, échelle mondiale)
-> **RIR** (Regional Internet Registry, échelle régionale)
-> **LIR** (Local Internet Registry, échelle locale, généralement un FAI ou une grande organisation)

Les 5 RIR mondiaux :
- **RIPE NCC** : Europe, Moyen-Orient, Asie centrale
- **ARIN** : Amérique du Nord
- **APNIC** : Asie-Pacifique
- **LACNIC** : Amérique latine et Caraïbes
- **AFRINIC** : Afrique

## 5. Structure d'une adresse IP

- Partie réseau (Net ID) : identifie le réseau auquel appartient la machine.
- Partie hôte (Host ID) : identifie la machine précise sur ce réseau local (LAN).

### Calcul de l'adresse réseau

On applique un **ET logique (&)** entre le masque et l'adresse IP pour obtenir l'adresse réseau.

Règle : si un bit de l'IP et le bit correspondant du masque valent tous les deux 1, le résultat est 1. Sinon, le résultat est 0.

Exemple concret :
```
IP     : 192.168.10.130  -> 11000000.10101000.00001010.10000010
Masque : 255.255.255.0   -> 11111111.11111111.11111111.00000000
ET     : 192.168.10.0    -> 11000000.10101000.00001010.00000000
```
Résultat : l'adresse réseau est `192.168.10.0`.

### Notation CIDR

Une adresse s'écrit `IP/m`, où m est le nombre de bits réservés à la partie réseau (bits à 1 dans le masque). Exemple : `192.168.10.130/24` signifie que les 24 premiers bits (donc les 3 premiers octets) forment la partie réseau, et le dernier octet est la partie hôte.

Le masque et l'IP sont indissociables : une IP seule n'a pas de sens sans son masque, puisqu'on ne peut pas savoir où s'arrête la partie réseau et où commence la partie hôte.

## 6. Classes d'adresses IP

- **Classe A** : bits de poids fort `0.......`, 1er octet de 1 à 126, masque par défaut 255.0.0.0 (/8)
- **Classe B** : bits de poids fort `10......`, 1er octet de 128 à 191, masque par défaut 255.255.0.0 (/16)
- **Classe C** : bits de poids fort `110.....`, 1er octet de 192 à 223, masque par défaut 255.255.255.0 (/24)
- **Classe D** : bits de poids fort `1110....`, 1er octet de 224 à 239, réservée à la multidiffusion (multicast)
- **Classe E** : bits de poids fort `11110...`, 1er octet de 240 à 255, réservée à un usage expérimental/futur

Détail des plages hôtes :
- Classe A : réseaux `1.x.y.z` à `126.x.y.z`, plage hôte `x.0.0.1` à `x.255.255.254` (environ 16 millions d'hôtes par réseau)
- Classe B : réseaux `128.0.x.y` à `191.255.x.y` (environ 65 000 hôtes par réseau)
- Classe C : réseaux `192.0.0.x` à `223.255.255.x` (254 hôtes par réseau)

La plage `127.x.x.x` n'est pas utilisable comme classe A normale : elle est réservée entièrement au loopback, bien qu'elle se situe dans l'intervalle numérique de la classe A.

Remarque : ce découpage en classes (A/B/C/D/E) est l'ancien système d'adressage IPv4 ("classful"). En pratique aujourd'hui, l'adressage utilise le **CIDR** (adressage sans classe, "classless"), qui permet des masques de longueur variable (VLSM) plus flexibles que les classes fixes. Le découpage en classes reste utile pour comprendre les bases et les plages réservées.

## 7. Adresses particulières

- `127.0.0.0/8` = adresse de bouclage (loopback), la machine s'adresse à elle-même.
- `127.0.0.1` = localhost (l'adresse loopback la plus couramment utilisée).
- Host ID = 0 (ex : `192.168.1.0`) : impossible en tant qu'adresse de machine, c'est l'adresse du réseau lui-même.
- Host ID = 255 (ex : `192.168.1.255`) : impossible en tant qu'adresse de machine, c'est l'adresse de diffusion (broadcast) du réseau.
- `0.0.0.0` ne peut pas être utilisée comme adresse d'hôte (elle désigne "toutes les adresses" dans certains contextes, comme une route par défaut).

Règle générale : l'ID hôte doit être différent de 0 et de 255.

Le loopback utilise la pile TCP/IP et ne passe jamais par un médium physique (câble, carte réseau) : tout reste interne à la machine, ce qui permet par exemple de tester des services réseau localement sans matériel.

### Plages d'adresses privées (RFC 1918)

Ces plages ne sont pas routables sur Internet et peuvent être réutilisées librement dans des réseaux locaux différents :
- `10.0.0.0` à `10.255.255.255` (10.0.0.0/8)
- `172.16.0.0` à `172.31.255.255` (172.16.0.0/12)
- `192.168.0.0` à `192.168.255.255` (192.168.0.0/16)

Autre plage réservée utile à connaître : **APIPA** (`169.254.0.0/16`), attribuée automatiquement par une machine Windows quand aucun serveur DHCP ne répond.

*À revoir : slide 3.4 du cours pour le tableau complet des adresses à usage réservé, qui peut contenir d'autres plages spécifiques mentionnées par l'enseignant.*

## 8. Commandes de configuration réseau

- Windows : `ipconfig /all` (affiche IP, masque, passerelle, DNS, MAC, etc. pour toutes les interfaces)
- Linux : `ip -a` (affiche les mêmes informations, équivalent moderne de `ifconfig`)

## 9. Couche 3 (réseau) et transmission aux couches supérieures

Quand un datagramme arrive et que son adresse de destination correspond à l'IP locale, il est transmis à la couche supérieure indiquée par le numéro de protocole présent dans l'en-tête IP (champ "Protocol").

- 6 = TCP
- 17 = UDP
- 1 = ICMP (utilisé notamment par la commande `ping`)

Attention, ce ne sont pas des numéros de port : ce sont des numéros de protocole au niveau de la couche 3 (IP), qui permettent au système de savoir à quelle couche 4 remettre les données.

## 10. Numéros de port

Les applications ou processus utilisant la pile TCP/IP sont identifiés par des numéros de port, des valeurs codées sur **16 bits** (donc de 0 à 65535).

- **Ports < 256 ("well-known ports")** : réservés, définis dans la RFC Assigned Numbers. En pratique, la plage officiellement standardisée par l'IANA va de 0 à 1023.
- **Ports alloués dynamiquement (ports éphémères)** : utilisés côté client pour ouvrir une connexion, généralement au-dessus de 1023 (souvent dans la plage 49152-65535).

### Le socket

Le couple **adresse IP + numéro de port** est appelé un socket.

Notation : `IP:port` (exemple : `192.168.1.10:443`)

Dans une communication réseau, ce sont les **deux sockets** (celui du client et celui du serveur) qui définissent entièrement la session : la combinaison IP source/port source et IP destination/port destination.

### Table des ports classiques (corrigée)

- FTP données : TCP port 20
- FTP contrôle : TCP port 21
- SSH : TCP port 22
- Telnet : TCP port 23
- SMTP : TCP port 25
- DNS : UDP port 53 (TCP aussi pour les transferts de zone ou réponses volumineuses)
- HTTP : TCP port 80
- HTTPS : TCP port 443

*Note de correction : dans les notes de cours initiales, les ports étaient mal associés (SSH=21, Telnet=22, SMTP=23). Les bons ports sont ceux listés ci-dessus. HTTP/HTTPS ont été ajoutés pour référence même s'ils n'étaient pas mentionnés dans le cours.*

## 11. Protocole UDP

- Utilise l'adresse IP pour acheminer, d'un ordinateur à un autre, des datagrammes de manière **non fiable** (aucune garantie d'arrivée des paquets, aucune vérification).
- Ne réordonne pas les messages si ceux-ci arrivent dans le désordre.
- Pas de connexion préalable, pas d'accusé de réception : rapide, léger, mais peu fiable.
- Utilisé quand la vitesse prime sur la fiabilité (streaming, jeux vidéo en ligne, DNS, VoIP).

## 12. Protocole TCP

Établit une connexion préalable entre les deux machines, ce qui le rend fiable, car chaque envoi est confirmé par un accusé de réception (ACK).

Fournit un **service de flux d'octets orienté connexion et fiable**.

"Orienté connexion" signifie que les applications qui dialoguent à travers TCP sont considérées l'une comme un serveur, l'autre comme un client. Une vérification préalable a lieu : synchronisation, disponibilité, autorisation du transfert, via l'échange de messages spécifiques (le handshake).

### Mécanisme PAR

TCP utilise le mécanisme **PAR** (Positive Acknowledgement with Retransmission) :
- Si l'émetteur ne reçoit pas d'ACK positif dans un délai donné, il retransmet les données.
- Le récepteur effectue des contrôles sur les données reçues ; si tout est correct, il renvoie un ACK positif.

### Établissement de connexion (three-way handshake)

1. Le client envoie un segment **SYN** (Synchronize) au serveur.
2. Le serveur répond avec un segment **SYN + ACK**.
3. Le client répond avec un segment **ACK**.

![[1788938755927 1.jpg|243]]

La connexion est alors établie et le transfert de données peut commencer.

TCP utilise des **numéros de séquence** (deux compteurs, un par sens de communication) précisant le numéro d'ordre du premier octet de données du segment envoyé. Un **numéro d'acquittement** est attendu en retour pour confirmer la bonne réception.

### Fin de connexion

La libération de connexion se fait par une poignée de main **FIN** : chaque côté envoie un segment FIN pour signaler qu'il n'a plus de données à transmettre, confirmé par un ACK de l'autre côté.

## 13. Architecture Client-Serveur

- **Clients** : envoient des requêtes vers un serveur.
- **Serveurs** : répondent aux requêtes reçues.

Le logiciel client-serveur cache la localisation du serveur au(x) client(s) : le client n'a pas besoin de savoir précisément où se trouve physiquement le serveur, seulement comment le joindre (adresse/nom). Cette architecture est indépendante des plateformes matérielles et logicielles utilisées de part et d'autre.

### Les 3 parties d'une application client-serveur

1. Interface utilisateur (présentation)
2. Logique de traitement (métier)
3. Gestion des données (stockage, base de données)

- **Front-end** = parties 1 et 2, exécuté côté client.
- **Back-end** = partie 3, exécutée côté serveur.

### Avantages et inconvénients (à valider avec la slide 31 du cours)

Avantages généralement cités pour ce type d'architecture :
- Centralisation des données -> plus facile à sécuriser, sauvegarder et administrer.
- Plusieurs clients peuvent accéder simultanément au même serveur.
- Montée en charge possible en renforçant le serveur (matériel plus puissant) sans changer les clients.

Inconvénients généralement cités :
- Le serveur est un point de défaillance unique (single point of failure) : s'il tombe, tous les clients sont impactés.
- Coût de mise en place et de maintenance du serveur.
- Dépendance à la qualité du réseau entre client et serveur.

*Cette liste est une reconstruction standard à but pédagogique : à comparer et corriger avec le contenu exact de la slide 31 du cours.*

## 14. DNS (Domain Name System)

Traduit les noms de domaine lisibles (ex : `exemple.fr`) en adresses IP utilisables par les machines pour communiquer.

DNS utilise UDP (port 53) pour la majorité des requêtes classiques, car elles sont courtes et rapides. TCP est utilisé pour les transferts de zone entre serveurs DNS ou lorsque la réponse est trop volumineuse pour tenir dans un seul datagramme UDP.

Fonctionnement simplifié d'une résolution DNS :
1. La machine cliente interroge son serveur DNS configuré (souvent celui du FAI ou de l'entreprise) pour obtenir l'IP correspondant à un nom de domaine.
2. Si ce serveur ne connaît pas la réponse, il interroge d'autres serveurs DNS (racine, puis serveurs de la zone concernée) jusqu'à obtenir la réponse.
3. La réponse est renvoyée au client, qui peut alors initier la connexion vers l'IP obtenue.

*À revoir : pages 32 et 33 du support de cours pour les détails précis abordés en classe.*

## Points à vérifier ou compléter avec le support de cours original

- Slide 3.4 : tableau complet des adresses réservées (peut contenir des plages en plus de celles listées ici).
- Slide 31 : avantages/inconvénients client-serveur, à comparer avec la liste reconstruite ci-dessus.
- Pages 32-33 : détails DNS abordés en cours.
- L'exemple de socket mentionné en cours (anomalie signalée dans les notes originales) à revoir avec les slides.
- Schéma de la poignée de main (image du cours) à réinsérer dans la note si disponible.
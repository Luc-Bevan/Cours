---
aliases:
  - TD1.1.1
---

# TD2 : Vérification de connectivité et de configuration

## 1. Utilisation des résultats de la commande `ipconfig /all`

![[image1.png]]

- [ ] a) La machine est-elle configurée en DHCP ? OUI
- [ ] b) Quelle est son adresse MAC ?![[Pasted image 20260925144439.png]]
- [ ] c) Quelle est son adresse IP ? ![[Pasted image 20260925144521.png]]
- [ ] d) Quelle est l'adresse de sa passerelle ?![[Pasted image 20260925144538.png]]
- [ ] e) Quelle est l'adresse du serveur DNS ?![[Pasted image 20260925144612.png]]
- [ ] f) Quelle est l'adresse du serveur DHCP ?![[Pasted image 20260925144552.png]]
- [ ] g) Quel est l'état de la carte WIFI ?![[Pasted image 20260925144631.png]]

---

## 2. D'après le résultat de la commande `IPCONFIG /ALL`, la machine RIGEL est-elle correctement configurée ?

![[image2.png]]

Non, le serveur Wims a un octet à 260
---

## 3. D'après le résultat de la commande `IPCONFIG /ALL`, la machine RIGEL est-elle correctement configurée ?

![[image3.png]]
Non a cause du masque qui est de classe C
---

## 4. Vous intervenez sur le réseau suivant

![[image4.png]]

> [!info] Contexte
> **STATION** ne peut pas accéder à **SERVEUR**, bien que les autres machines du réseau y parviennent.
> **STATION** ping avec succès sur l'adresse locale du routeur, mais pas sur son interface distante (côté B).

Vous éditez la table de routage de **STATION** grâce à la commande `route print` :

| Adresse réseau  | Masque          | Passerelle   | Interface    | Métrique |
| --------------- | --------------- | ------------ | ------------ | -------- |
| 0.0.0.0         | 0.0.0.0         | 185.75.129.1 | 185.75.142.6 | 1        |
| 127.0.0.0       | 255.0.0.0       | 127.0.0.1    | 127.0.0.1    | 1        |
| 185.75.128.0    | 255.255.0.0     | 185.75.142.6 | 185.75.142.6 | 1        |
| 185.75.142.6    | 255.255.255.255 | 127.0.0.1    | 127.0.0.1    | 1        |
| 185.75.255.255  | 255.255.255.255 | 185.75.142.6 | 185.75.142.6 | 1        |
| 224.0.0.0       | 224.0.0.0       | 185.75.142.6 | 185.75.142.6 | 1        |
| 255.255.255.255 | 255.255.255.255 | 185.75.142.6 | 185.75.142.6 | 1        |

Après analyse de la table de routage, que pouvez-vous conclure sur :

- [ ] L'adresse IP de STATION est correcte ou incorrecte ? Justifier votre réponse.
-
- [ ] L'adresse IP du routeur sur le réseau B est correcte ou incorrecte ? Justifier votre réponse.
- Non car elle est sur le même réseau
- [ ] L'adresse de passerelle configurée sur STATION est correcte ou incorrecte ? Justifier votre réponse.
- Non elle a mi une adrresse de broadcast
- [ ] Le masque configuré sur STATION est correct ou incorrect ? Justifier votre réponse.
- 

---

## 5. Exercice

Soit le réseau suivant :

![[image5.png]]

**Qu'est-ce qu'un concentrateur ?**

> [!note]
> Un **concentrateur** est un élément matériel permettant de concentrer le trafic réseau provenant de plusieurs hôtes, et de régénérer le signal. Le concentrateur est ainsi une entité possédant un certain nombre de ports (il possède autant de ports qu'il peut connecter de machines entre elles, généralement 4, 8, 16 ou 32).
>
> Le concentrateur permet ainsi de connecter plusieurs machines entre elles, parfois disposées en étoile, ce qui lui vaut le nom de **hub** (signifiant *moyeu de roue* en anglais ; la traduction française exacte est *répartiteur*), pour illustrer le fait qu'il s'agit du point de passage des communications des différentes machines.

**Qu'est-ce qu'un commutateur (ou switch) ?**

> [!note]
> En informatique, un **switch** (ou commutateur) est un boîtier doté de quatre à plusieurs centaines de ports Ethernet, et qui sert à relier en réseau différents éléments du système informatique. Il permet notamment de créer différents circuits au sein d'un même réseau, de recevoir des informations et d'envoyer des données vers un destinataire précis en les transportant via le port adéquat. Le switch présente plusieurs avantages dans la gestion de votre parc informatique. Il contribue à la sécurité du réseau et à la protection des données échangées via le réseau.

**La différence entre commutateur, concentrateur et routeur :**

> [!note]
> Il est aisé de confondre switch et hub. Pourtant, les hubs réseaux ne filtrent pas les informations reçues et les diffusent à l'ensemble des postes du réseau sans distinction. Opter pour un switch plutôt qu'un hub permet, en triant les données, de libérer de la bande passante et de booster les performances de votre réseau informatique, surtout s'il comprend un grand nombre d'utilisateurs simultanés. Le routeur, quant à lui, a pour fonction de relier le réseau interne d'entreprise au réseau internet externe et à partager une même connexion internet à différents postes de travail.

Questions :

- [ ] Si un paquet ARP est émis par la machine A, quelles machines recevront ce paquet ?
- Toutes sauf A
- [ ] Si un paquet est émis par la machine A en direction de la machine C, quelles machines recevront ce paquet ?
- A B et C
- [ ] Si un paquet est émis par la machine A en direction de la machine E, quelles machines recevront ce paquet ?
- D et E

---

## 6. Le protocole DHCP

> [!note]
> DHCP permet d'affecter automatiquement des adresses IP, des masques de sous-réseau et d'autres informations de configuration à des ordinateurs clients du réseau local (passerelle, DNS...). Lorsqu'un serveur DHCP est disponible, les ordinateurs configurés pour obtenir automatiquement une adresse IP émettent une requête et reçoivent leur configuration de ce serveur DHCP à leur démarrage.
>
> Lorsqu'un serveur DHCP est indisponible, de tels clients adoptent automatiquement une configuration alternative ou une adresse APIPA (Automatic Private IP Addressing). La mise en œuvre d'un serveur DHCP nécessite l'installation du serveur, son autorisation, la configuration des étendues, des exclusions, des réservations et des options, puis l'activation des étendues et enfin la vérification de la configuration.

**Exemple :**

![[image6.png]]

Que pouvez-vous dire de la configuration de ce réseau, sachant que les étendues du serveur DHCP sont configurées comme suit ?

**Étendue 1 :**
- De 10.0.0.1 à 10.0.0.200
- Masque 255.0.0.0
- Option 003-routeur = 10.0.0.254

**Étendue 2 :**
- De 192.168.1.1 à 192.168.1.200
- Masque 255.255.255.0
- Option 003-routeur = 192.168.1.254

---

## 7. Choisir la connectique

Vous devez construire une architecture de réseau local dans une salle informatique contenant 15 postes de travail. Le réseau local choisi est un Ethernet à 10 Mbit/s.

Vous avez à votre disposition un extrait d'une documentation technique :

| Normes | Connecteurs | Câbles | Longueur max | Topologie | Coupleur réseau |
|---|---|---|---|---|---|
| 10Base T | RJ45 | Paire torsadée/UTP5 | 100m | Étoile | Carte TX |
| 10Base 2 | BNC | Coaxial fin | 185m | Bus | Carte BNC |
| 10Base 5 | Prise vampire | Coaxial épais | 500m | Bus | Carte AUI |

- [ ] Quel type de câblage préconiseriez-vous ?
- [ ] Calculez le nombre de segments de câbles nécessaires.

---

## 8. Compléter les champs manquants du protocole TCP

**La connexion :**

![[image7.png]]

La libération de la connexion se fait aussi par poignée de main, avec les segments **FIN** :

![[image8.png]]

---

## 9. Adressage (adresse MAC)

Voici un exemple d'adresse Ethernet (adresse MAC, 6 octets) :
`08:0:20:18:ba:40`

- [ ] Deux machines peuvent-elles posséder la même adresse Ethernet ? Pourquoi ?

**Voici la trace d'une communication point à point prélevée par un espion de ligne (SNIFFER) :**

```
ETHER: ---- Ether Header ----
ETHER: Packet 1 arrived at 18:29:10.10
ETHER: Packet size = 64 bytes
ETHER: Destination = 08:00:20:18:ba:40, Sun
ETHER: Source = aa:00:04:00:1f:c8, DEC (DECNET)
ETHER: Ethertype = 0800 (IP)
```

**À comparer avec une communication à un groupe :**

```
ETHER: ---- Ether Header ----
ETHER: Packet 1 arrived at 11:40:57.78
ETHER: Packet size = 60 bytes
ETHER: Destination = ff:ff:ff:ff:ff:ff, (broadcast)
ETHER: Source = 08:00:20:18:ba:40, Sun
ETHER: Ethertype = 0806 (ARP)
```

- [ ] Quel champ, par sa valeur, permet de différencier les deux types de traces pour les communications à un seul destinataire ou à plusieurs destinataires ?
- [ ] Comment un seul message peut-il parvenir à plusieurs destinataires simultanément ?

> [!tip] Réponse
> En utilisant le broadcast.

---

## 10. La couche Réseau, Adressage IPv4

> [!note]
> Une adresse IPv4 est définie sur 4 octets. L'adressage IPv4 (Internet) est hiérarchique. Un réseau IPv4 est identifié par son numéro de réseau. Une machine est identifiée par son numéro dans le réseau.
>
> L'adresse IPv4 d'une machine est donc composée d'un numéro de réseau et d'un numéro de machine (hôte).

- [ ] Si l'adresse IPv4 est `192.33.159.6`, donner l'adresse réseau et le numéro de la machine.
- [ ] Sur l'internet, deux machines à deux endroits différents peuvent-elles posséder la même adresse IPv4 ? Si oui, à quelle condition ?
- [ ] Dans le même réseau IPv4, deux machines différentes peuvent-elles posséder la même adresse IPv4 à deux moments différents ? Chercher un contexte d'utilisation.

---

## 11. Sous UNIX, étude des résultats de la commande `ifconfig`

Voici l'affichage de la commande UNIX `ifconfig` sur une machine :

```
le0: flags=863<UP, BROADCAST, NOTRAILERS, RUNNING, MULTICAST> mtu 1500
inet 192.33.159.212 netmask ffffff00 broadcast 192.33.159.255
ether 08:00:20:18:ba:40
```

- [ ] Indiquer toutes les informations que montre cette commande.

---

## 12. La couche Transport

On donne la structure de l'en-tête IP et la structure de l'en-tête TCP :

![[image9.png]]

**Trace d'une communication point à point :**

```
ETHER: ---- Ether Header ----
ETHER: Packet 3 arrived at 11:42:27.64
ETHER: Packet size = 64 bytes
ETHER: Destination = 8:0:20:18:ba:40, Sun
ETHER: Source = aa:0:4:0:1f:c8, DEC (DECNET)
ETHER: Ethertype = 0800 (IP)

IP: ---- IP Header ----
IP: Version = 4
IP: Header length = 20 bytes
IP: Type of service = 0x00
IP:   xxx. .... = 0 (precedence)
IP:   ...0 .... = normal delay
IP:   .... 0... = normal throughput
IP:   .... .0.. = normal reliability
IP: Total length = 40 bytes
IP: Identification = 41980
IP: Flags = 0x4
IP:   .1.. .... = do not fragment
IP:   ..0. .... = last fragment
IP: Fragment offset = 0 bytes
IP: Time to live = 63 seconds/hops
IP: Protocol = 6 (TCP)
IP: Header checksum = af63
IP: Source address = 163.173.32.65, papillon.cnam.fr
IP: Destination address = 163.173.128.212, jordan
IP: No options

TCP: ---- TCP Header ----
TCP: Source port = 1368
TCP: Destination port = 23 (TELNET)
TCP: Sequence number = 143515262
TCP: Acknowledgement number = 3128387273
TCP: Data offset = 20 bytes
TCP: Flags = 0x10
TCP:   ..0. .... = No urgent pointer
TCP:   ...1 .... = Acknowledgement
TCP:   .... 0... = No push
TCP:   .... .0.. = No reset
TCP:   .... ..0. = No Syn
TCP:   .... ...0 = No Fin
TCP: Window = 32120
TCP: Checksum = 0x3c30
TCP: Urgent pointer = 0
TCP: No options

TELNET: ---- TELNET ----
TELNET: ""
```

- [ ] À votre avis, à quoi correspondent les étiquettes TCP et TELNET ?
- [ ] Combien y a-t-il d'encapsulations successives ?

---

## 13. Adressage IPv4 de base (hiérarchisé à deux niveaux)

L'adressage IPv4 a été créé dans sa version de base en distinguant trois classes d'adresses associées à 3 classes de réseaux notées A, B et C.

- [ ] Comment est notée l'adresse d'un hôte et l'adresse d'un réseau ?
- [ ] Comment un ordinateur hôte ou un routeur reconnaît-il qu'une adresse de destination appartient à l'une des classes ?
- [ ] Quelle est la proportion relative du nombre d'adresses IPv4 affectées aux différentes classes A, B, C ? Pourquoi l'utilisation des adresses de classe A (ou B) est inefficace dans un réseau d'entreprise ?
- [ ] Quelle est l'opération effectuée sur une adresse de station pour déterminer son adresse de réseau ?
- [ ] Comment l'adresse d'un hôte destinataire est-elle utilisée pour le routage ?

---

## 14. Routage

![[image10.png]]

- [ ] Parmi les lignes du tableau suivant, quelle est la table de routage pour la machine B ?

![[image11.png]]

- [ ] Parmi les lignes du tableau suivant, quelle est la table de routage pour le routeur R2 ?
> [!info]
> R2 sera plus complexe parce qu'il est connecté à deux réseaux.

![[image12.png]]

---

## 15. Adresse IP de routeurs

![[image13.jpeg]]

Les postes F01, F02, ..., F99 et FServeur constituent le réseau **"FORMATION"**.

Les postes A01, A02, A03 et AServeur constituent le réseau **"ADMINISTRATION"**.

L'administrateur des réseaux doit avoir accès à toutes les ressources des deux réseaux à partir du réseau "ADMINISTRATION".

- [ ] Quel type de matériel sont « matériel 2 » et « matériel 3 », en justifiant brièvement votre choix ?
- [ ] Proposer un adressage IP possible pour le matériel_3.
- [ ] Expliquez à quoi sert une passerelle.
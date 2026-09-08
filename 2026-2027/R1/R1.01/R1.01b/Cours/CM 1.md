R1.01b  

Cours initiation au  réseau d'entreprise. 
Ip = addresse logique 
Mac = addresse physique 
addresse ip publique ->unique au monde. 
ARP : 3 address Resolution Protocol”  
le protocol envoi une ip, si un appareil le connais elle répond le mac 
un protocol arp ne communique pas au dela du réseau local. 
Un datagramme s’utilise pour le protocol UDP  
pour le protocol tcp on utilise une trame. 
Rappel: 
00000000 = 0 
00000001 = 1 
00000010 = 2 
à léchelle mondiale: IANA (international assigned numbers authority” 
puis à RIR  puis a  LOIR, celui pour le rir de l’europe se nomme Ripe NCC. 
La partie hote identifie la mavhine sur le réseau LAN. 
Le & (et logique –s'applique entre le masque et l’IP pour obtenir l’addresse Réseau. ( logic gate) 
DNS : Domain Name System 
127.0.0.0 => addresse de bouclage (loopback). Sert à la machine pour s’addresser à elle meme. 
A 0....... | [HOTE 
B 10...... | [HOTE 

C 110..... | [HOTE 
D 1110| [HOTE 
E 11110| [HOTE 

Classes:  
A 1.x.y.z à 126.x.y.z ,     x.0.0.1 à x.255.255.254 
B 

C 

D 

E 
La classe peux également permmettre de retrouver l’addresse de sous réseau) ou du réseau). 
255 dans id réseau est impossible car addressse de diffusion 
0.0.0.0 en id 0 ne peux exister 
ID hote différent de 0 ou 255. 
Loopback utilise TCP/IP 
127.0.0.0 avec masque 255.0.0.0 => loopback , donc 127.0.0.1 = localHost. 
Un loopback ne passe pas à travers un médium (=cable réseau= 
Regarder la Slide 3.4 Tableau des addresse à usage réservé.   
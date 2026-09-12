# TD1 : Exercices sur la conversion, les classes et la reconnaissance des adresses valides

## 1. Convertir les valeurs binaires suivantes en notation décimale (détailler le calcul)

- [ ] 11001100 : 204
- [ ] 10101010 : 170
- [ ] 11100011 : 227
- [ ] 10110011 : 179
- [ ] 00110101 : 53
- [ ] 11000111 : 199

---

## 2. Convertir les valeurs décimales suivantes en binaire (8 bits) (détailler la méthode)

- [ ] 48 : 00110000
- [ ] 222 : 11011110
- [ ] 119 : 01110111
- [ ] 135 : 10000111
- [ ] 60 : 00111100
- [ ] 184 :10111000

---

## 3. Convertir les adresses IP suivantes en binaire

- [ ] 145.32.59.24 : 10010001.00100000.00111011.00011000
- [ ] 200.42.129.16 :  11001000.00101010.10000001.00010000
- [ ] 14.82.19.54 : 00001110.01010010.00010011.00011110

---

## 4. Trouver la classe des adresses IP suivantes (donner la méthode)

- [ ] 10000000.00001010.11011000.00100111 : Classe B
- [ ] 11101101.10000011.00001110.01011111 :  Classe D
- [ ] 01001010.00011011.10001111.00010010 : Classe A
- [ ] 11001001.11011110.01000011.01110101 : Classe C
- [ ] 10000011.00011101.00000000.00000111 : Classe B

---

## 5. Écrire la classe des adresses suivantes et justifier

- [ ] 118.89.67.234 : Classe A
- [ ] 199.254.250.223 : Classe C
- [ ] 223.25.191.75 : Classe C
- [ ] 10.20.30.40 : Réservé
- [ ] 191.250.254.39 :classe B 
- [ ] 192.1.57.83 : Classe C
- [ ] 127.0.0.1 : Classe A
- [ ] 239.255.0.1 : Classe D
- [ ] 172.11.1.1 : Classe B
- [ ] 0.0.0.0 : réservé Classe A
- [ ] 128.192.224.1 : Classe B
- [ ] 255.255.255.255 : réservé Classe E

---

## 6. Pour chaque adresse, entourer la partie demandée (réseau ou hôte) et donner le masque de sous-réseau

| Partie réseau       | Masque de sous-réseau | Partie hôte         | Masque de sous-réseau |
| ------------------- | --------------------- | ------------------- | --------------------- |
| ==1==.102.45.177    | 255.0.0.0             | 196.22.177==.13==   | 255.255.255.0         |
| ==133.156==.55.102  | 255.255.0.0           | 221.252==.77.10==   | 255.255.255.0         |
| ==123==.12.45.77    | 255.0.0.0             | 126==.252.77.103==  | 255.0.0.0             |
| ==13==.1.255.102    | 255.0.0.0             | 171.242==.177.109== | 255.255.0.0           |
| ==193.156.155==.192 | 255.255.255.0         | 21==.52.177.188==   | 255.0.0.0             |
| ==77==.77.45.77     | 255.0.0.0             | 191==.252.77.13==   | 255.0.0.0             |
| ==191.15==.155.2    | 255.255.0.0           | 192.168==.25.0==    | 255.255.0.0           |

---

## 7. Exercice

L'adressage IP se fait grâce à un mot de 32 bits, séparé en 4 octets, codés en décimal pointé : W.X.Y.Z, et plusieurs classes sont proposées.

Pour chaque classe (A, B et C), donner le nombre de réseaux possibles puis utilisables et le nombre de machines sur ces réseaux, et justifier vos réponses :

**Classe A :** 255^3 = 16 581 375 machines, car il y a 3 octets laissés disponibles par le masque. et 255 réseaux.

**Classe B :** 255^2 = 65 025 machines, car il y a 3 octets laissés disponibles par le masque. et 65 025 réseaux.

**Classe C :** 255^1 = 255 machines, car il y a 3 octets laissés disponibles par le masque. et 255 réseaux et 16 581 375 réseaux.

---

## 8. Remplir le tableau (le masque est celui associé à la classe)

| Adresse IP      | Valide (Oui/Non) | Adresse réseau |
| --------------- | ---------------- | -------------- |
| 191.168.1.1     | Oui              | 191.168.0.0    |
| 127.0.0.1       | Non              | X              |
| 1.2.3.4         | Oui              | 1.0.0.0        |
| 224.0.0.2       | Non              | X              |
| 172.16.122.68   | Oui              | 172.16.0.0     |
| 0.137.250.17    | Non              | X              |
| 255.255.255.255 | Non              | X              |
| 192.252.19.4    | Oui              | 192.252.19.0   |
| 118.17.255.255  | Oui              | 118.0.0.0      |
| 224.0.0.9       | Non              | X              |
| 0.0.0.0         | Non              | X              |
| 127.131.208.51  | Non              | X              |
| 192.168.0.1     | Oui              | 192.168.0.0    |
| 168.192.226.13  | Oui              | 168.192.0.0    |
| 224.0.1.24      | Non              | X              |
| 172.32.14.172   | Oui              | 172.32.0.0     |
| 192.168.129.33  | Oui              | 192.168.129.0  |
| 1.0.0.127       | Oui              | 1.0.0.0        |

---

## 9. Indiquer si les adresses suivantes sont valides ou non pour un hôte TCP/IP

> Si une adresse est invalide, entourer la partie erronée et fournir une explication.
> Le masque est celui associé par défaut à la classe.

| Adresse IP      | Classe | Valide (Oui/Non) | Explication                                            |
| --------------- | ------ | ---------------- | ------------------------------------------------------ |
| 245.12.33.102   | E      | Non              | 1er octet 245 = classe E, réservée/expérimentale       |
| 123.123.123.123 | A      | Oui              | rien de spécial                                        |
| 199.23.107.255  | C      | Non              | dernier octet 255 = tout le champ hôte à 1 = broadcast |
| 199.23.107.0    | C      | Non              | dernier octet 0 = champ hôte à 0 = adresse réseau      |
| 156.266.12.103  | B      | Non              | 266 > 255, octet invalide (adresse mal formée)         |
| 99.0.0.12       | A      | Oui              | rien de spécial                                        |
| 153.0.0.0       | B      | Non              | 2 derniers octets à 0 = adresse réseau                 |
| 153.0.0.255     | B      | Oui              | rien de spécial                                        |
| 191.23.255.255  | B      | Non              | 2 derniers octets à 255 = broadcast                    |
| 33.255.255.0    | A      | Oui              | rien de spécial                                        |
| 12.0.0.0        | A      | Non              | 3 derniers octets à 0 = adresse réseau                 |
| 12.255.255.255  | A      | Non              | 3 derniers octets à 255 = broadcast                    |
| 12.0.0.255      | A      | Oui              | champ hôte ni tout à 0 ni tout à 255                   |
| 127.0.0.1       | —      | Non              | loopback (127.x.x.x)                                   |
| 127.23.109.122  | —      | Non              | loopback (127.x.x.x)                                   |
| 0.23.12.122     | —      | Non              | 1er octet 0 = réservé                                  |
| 192.12.255.102  | C      | Oui              | rien de spécial                                        |
| 191.105.0.0     | B      | Non              | 2 derniers octets à 0 = adresse réseau                 |

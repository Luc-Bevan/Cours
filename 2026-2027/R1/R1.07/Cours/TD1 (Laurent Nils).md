---
aliases:
  - TD1.1.1
---
![[R107.pdf]]


### Exercice 1:

```python
def echanger(a: float, b: float) -> tuple[float, float]:
    """ :sortie a: float 
    :sortie b: float 
    :post-cond: les valeurs de a et b sont échangées 
    """ 
    c = a
    a = b
    b = c
    # ou faire a, b = b, a
    return a, b
def main():
    résultat = echanger(float(input("entrez a: ")), float(input("entrez b: ")))
    print("échangés cela donne:", "a=", résultat[0], "b=", résultat[1])
if __name__ == "__main__":
    main()
```

### Exercice 2


```python
def verif(a: float,b: float) -> bool:
	""" :sortie a: float
	:sortie b: float
	:post-cond: a est supérieur à b pour Vrai
	"""
	a = a>=b
	print(a)
verif(5.0, 3.0)
```

### Quelle différence ? (A)

## If / elif / else — deux if séparés VS un seul bloc

### Cas 1 : deux `if` écrits l'un après l'autre (blocs indépendants)

```python
def ma_fonction():
    x = -1
    c = 0
    if x != 0:
        c = c + 1
    if x != 1:  # ce if est INDÉPENDANT du précédent (2 blocs séparés)
        c = c + 1
    else:  # se lance seulement si "x != 1" est False (pas lié au 1er if !)
        c = c + 1
    return c  # ici : le 1er if passe (+1) ET le 2e bloc if/else passe aussi (+1) → c = 2
```

> [!note] Point clé
> Deux `if` écrits l'un après l'autre = **deux blocs séparés et indépendants**. Le `else` ne se rattache **qu'au `if` juste au-dessus de lui**, jamais à un `if` plus loin. C'est pour ça que les deux blocs peuvent s'exécuter en même temps ici.

---

### Cas 2 : `if` / `elif` (un seul bloc)

```python
def ma_fonction():
    x = -1
    c = 0
    if x != 0:
        c = c + 1
    elif x != 1:  # ne sera même évalué QUE si le if au-dessus est False
        c = c + 1  # ne se lance jamais ici car le if au-dessus était True
    return c  # une seule branche s'exécute max → c = 1
```

> [!note] Point clé
> `if` / `elif` / `else` forment **un seul bloc**. Dès qu'une condition est vraie, Python exécute cette branche et **ignore tout le reste du bloc**, même si une condition suivante aurait aussi été vraie.

---

> [!tip] Règle générale à retenir
> - `if` puis un **nouveau** `if` (pas de `elif`/`else` collé) → blocs indépendants, plusieurs peuvent s'exécuter
> - `if` / `elif` / `else` → un seul bloc, **une seule branche max** s'exécute
> - un `else` (ou `elif`) se rattache toujours au `if` **immédiatement au-dessus**, jamais à un autre plus loin dans le code

| Structure | Combien de branches peuvent s'exécuter ? |
|---|---|
| `if` puis un autre `if` séparé | Chacun indépendamment → 0, 1 ou 2 peuvent s'exécuter |
| `if` / `elif` / `else` (un seul bloc) | Une seule, la première dont la condition est vraie |

### Quelle différence ? (B)

```python
def ma_fonction():
x = 1
c = 0
if x == 0:
	c = c + 1
c = c + 1
return c #c= c+2 ou c+1 (ici 1 ou 2)
```

```python
def ma_fonction():
x = 1
c = 0
if x == 0:
	c = c + 1
	c = c + 1
return c #c = c+1 (ici 1)
```

```python
def valeur_absolue(x: float) -> tuple[float, int]:
	""" 
	:sortie signe: int
	:post-cond y: valeur absolue de x
	:post-cond signe: signe de x
	"""
	if x >= 0:
		a=1
	else:
		x = -x
		a=-1
	return(x,a)
```


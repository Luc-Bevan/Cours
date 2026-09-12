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

```python
def ma_fonction():
 x = -1 
 c = 0 
 if x != 0: 
	 c = c + 1 
 if x != 1: #meme si le premier if est True, le deuxième se lance
	 c = c + 1 
 else: #si aucunes des conditions avant sont lancés, lui se lance
	 c = c + 1 
 return c #c est donc soit = c + 1 ou à c + 2 (ici il est égal à c+2 soit 2)

```python
def ma_fonction():
 x = -1 
 c = 0 
 if x != 0:
	 c = c + 1 
 elif x != 1: 
	 c = c + 1 #lui se lance seulement si le premier et false
	 #il n'y a pas d'action finale sur celui-ci, car il y aura nécessairement une condition True et une False.
 return c #c = c+1 peut importe x, donc c = 1
```

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

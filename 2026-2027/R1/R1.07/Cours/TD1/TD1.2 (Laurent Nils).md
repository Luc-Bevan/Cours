---
aliases:
  - TD1.1.1
---

![[TD1 (1).pdf]]

## Echange des variables
```python

def echange_var(a: int, b: int) -> tuple[int, int]:
	""" 
	:sortie a: int
	:sortie b: int
	:post-condition: b contient la valeur de a 
	:post-condition: a contient la valeur de b 
	a,b = b,a
	return(a,b)
	""
print(echange_var(1,2))
```

## Test de parité
```python
	def est_paire(a: int) -> bool:
	"""
	:sortie est_paire: bool
	:post-condition: "est_paire" contient vrai si a est paire, faux sinon """
```
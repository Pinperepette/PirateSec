---
layout: post
title:  "Sintassi di base: Variabili, tipi di dati, operatori"
date:   2024-09-08 11:30:00 +0200
categories: corso-python
tags: [python, variabili, tipi-di-dati, operatori]
---

# Sintassi di base: Variabili, tipi di dati, operatori

In questo articolo vedremo le basi della sintassi di Python, concentrandoci su tre concetti fondamentali: le variabili, i tipi di dati e gli operatori. Questi concetti rappresentano il fondamento su cui costruire il resto della nostra conoscenza di Python.

## Variabili

Le variabili sono lo strumento con cui immagazziniamo dati all'interno di un programma. In Python, non è necessario dichiarare il tipo di una variabile esplicitamente, poiché il linguaggio lo deduce automaticamente in base al valore che gli assegniamo.

Esempio:
```python
x = 10
nome = "Andrea"
pi_greco = 3.14
```

In questo esempio, `x` è un numero intero, `nome` è una stringa e `pi_greco` è un numero con la virgola mobile (float).

## Tipi di dati

Python supporta vari tipi di dati. Ecco alcuni dei più comuni:

- **Interi**: numeri interi (es. `1`, `10`, `-5`).
- **Float**: numeri decimali (es. `3.14`, `0.001`).
- **Stringhe**: sequenze di caratteri (es. `"ciao"`, `"Python"`).
- **Booleani**: valori di verità (`True` o `False`).
- **Liste**: collezioni ordinate di elementi (es. `[1, 2, 3]`, `["a", "b", "c"]`).
- **Tuple**: simili alle liste, ma immutabili (es. `(1, 2, 3)`).
- **Dizionari**: collezioni di coppie chiave-valore (es. `{"nome": "Andrea", "età": 25}`).

Esempio:
```python
eta = 25  # Intero
nome = "Giulia"  # Stringa
prezzo = 19.99  # Float
is_active = True  # Booleano
frutti = ["mela", "banana", "arancia"]  # Lista
```

## Operatori

Gli operatori sono simboli che ci permettono di eseguire operazioni sui valori. Python supporta vari tipi di operatori:

### Operatori aritmetici
- `+`: addizione
- `-`: sottrazione
- `*`: moltiplicazione
- `/`: divisione
- `%`: modulo (resto della divisione)
- `**`: esponenziazione
- `//`: divisione intera

Esempio:
```python
a = 10
b = 3
somma = a + b  # 13
differenza = a - b  # 7
moltiplicazione = a * b  # 30
divisione = a / b  # 3.3333
modulo = a % b  # 1
esponenziale = a ** b  # 1000
divisione_intera = a // b  # 3
```

### Operatori di confronto
- `==`: uguale a
- `!=`: diverso da
- `>`: maggiore di
- `<`: minore di
- `>=`: maggiore o uguale a
- `<=`: minore o uguale a

Esempio:
```python
x = 10
y = 5
print(x == y)  # False
print(x > y)   # True
```

### Operatori logici
- `and`: ritorna `True` se entrambe le condizioni sono vere.
- `or`: ritorna `True` se almeno una delle condizioni è vera.
- `not`: inverte il valore logico.

Esempio:
```python
x = True
y = False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

### Operatori di assegnazione
- `=`: assegna un valore a una variabile
- `+=`: incrementa il valore della variabile
- `-=`: decrementa il valore della variabile
- `*=`: moltiplica il valore della variabile
- `/=`: divide il valore della variabile

Esempio:
```python
x = 10
x += 5  # x ora vale 15
x *= 2  # x ora vale 30
```

### Operatori di appartenenza
- `in`: verifica se un valore è presente in una sequenza (lista, stringa, ecc.).
- `not in`: verifica se un valore non è presente in una sequenza.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
print("mela" in frutti)  # True
print("pera" not in frutti)  # True
```

## Conclusione

Abbiamo visto come utilizzare variabili, tipi di dati e operatori in Python. Questi concetti sono le basi del linguaggio e ti permetteranno di iniziare a scrivere programmi semplici ma potenti. Nel prossimo articolo, parleremo delle strutture di controllo come i cicli e le condizioni, che ti permetteranno di eseguire operazioni più complesse.

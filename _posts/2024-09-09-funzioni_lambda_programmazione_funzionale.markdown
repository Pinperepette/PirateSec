---
layout: post
title:  "Funzioni lambda e programmazione funzionale in Python"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, lambda, programmazione-funzionale, funzioni]
---

# Funzioni lambda e programmazione funzionale in Python

Le **funzioni lambda** e la **programmazione funzionale** sono due concetti potenti in Python che consentono di scrivere codice più conciso e espressivo. In questo articolo, esploreremo come funzionano le funzioni lambda e come Python supporta lo stile di programmazione funzionale.

## Funzioni lambda

Le funzioni **lambda** sono funzioni anonime, cioè funzioni che non hanno un nome e vengono definite in una sola riga. Sono utili quando hai bisogno di una funzione semplice e veloce per un'operazione temporanea.

### Sintassi delle funzioni lambda

La sintassi di una funzione lambda è:

```python
lambda parametri: espressione
```

Esempio:
```python
somma = lambda a, b: a + b
print(somma(3, 5))  # Stampa 8
```

Qui, abbiamo creato una funzione lambda che somma due numeri e l'abbiamo assegnata alla variabile `somma`.

### Quando usare le funzioni lambda?

Le funzioni lambda sono comunemente usate quando hai bisogno di passare una funzione come argomento a un'altra funzione, come nelle funzioni `map()`, `filter()`, e `sorted()`.

Esempio con `sorted()`:
```python
numeri = [(2, 'due'), (3, 'tre'), (1, 'uno')]
numeri_ordinati = sorted(numeri, key=lambda x: x[0])
print(numeri_ordinati)  # Stampa [(1, 'uno'), (2, 'due'), (3, 'tre')]
```

In questo esempio, la funzione `sorted()` utilizza una funzione lambda per ordinare i numeri in base al primo elemento della tupla.

## Programmazione funzionale

La **programmazione funzionale** è uno stile di programmazione che tratta le funzioni come oggetti di prima classe, il che significa che possono essere passate come argomenti, restituite da altre funzioni, e assegnate a variabili. Python supporta diversi concetti di programmazione funzionale.

### La funzione `map()`

La funzione `map()` applica una funzione a tutti gli elementi di un iterabile (come una lista) e restituisce un nuovo iteratore con i risultati.

Esempio:
```python
numeri = [1, 2, 3, 4]
quadrati = map(lambda x: x ** 2, numeri)
print(list(quadrati))  # Stampa [1, 4, 9, 16]
```

Qui, `map()` applica la funzione lambda a ogni elemento della lista `numeri`, elevando ogni numero al quadrato.

### La funzione `filter()`

La funzione `filter()` restituisce un iteratore contenente solo gli elementi dell'iterabile per cui la funzione passata come argomento restituisce `True`.

Esempio:
```python
numeri = [1, 2, 3, 4, 5, 6]
numeri_pari = filter(lambda x: x % 2 == 0, numeri)
print(list(numeri_pari))  # Stampa [2, 4, 6]
```

In questo esempio, `filter()` seleziona solo i numeri pari dalla lista `numeri`.

### La funzione `reduce()`

La funzione `reduce()`, che si trova nel modulo `functools`, applica una funzione a due argomenti cumulativamente a tutti gli elementi di un iterabile, riducendolo a un singolo valore.

Esempio:
```python
from functools import reduce

numeri = [1, 2, 3, 4]
somma_totale = reduce(lambda x, y: x + y, numeri)
print(somma_totale)  # Stampa 10
```

In questo esempio, `reduce()` somma tutti i numeri nella lista `numeri`.

### La funzione `zip()`

La funzione `zip()` combina più iterabili (liste, tuple, ecc.) in un singolo iteratore di tuple.

Esempio:
```python
nomi = ['Alice', 'Bob', 'Charlie']
voti = [85, 90, 78]
studenti = zip(nomi, voti)
print(list(studenti))  # Stampa [('Alice', 85), ('Bob', 90), ('Charlie', 78)]
```

In questo esempio, `zip()` combina la lista dei nomi con la lista dei voti.

### La funzione `lambda` all'interno di funzioni

Le funzioni lambda possono anche essere restituite da altre funzioni o passate come argomenti.

Esempio:
```python
def crea_moltiplicatore(fattore):
    return lambda x: x * fattore

moltiplica_per_due = crea_moltiplicatore(2)
print(moltiplica_per_due(5))  # Stampa 10
```

In questo esempio, la funzione `crea_moltiplicatore` restituisce una funzione lambda che moltiplica un numero per un determinato fattore.

## Vantaggi della programmazione funzionale

- **Codice più conciso**: Le funzioni lambda e le funzioni come `map()` e `filter()` permettono di scrivere codice breve e leggibile.
- **Migliore gestione della memoria**: L'uso di generatori e funzioni come `map()` e `filter()` che restituiscono iteratori aiuta a risparmiare memoria.
- **Migliore gestione delle operazioni complesse**: La programmazione funzionale permette di eseguire operazioni complesse su collezioni di dati in modo più elegante.

## Conclusione

Le funzioni lambda e la programmazione funzionale offrono un modo potente per scrivere codice conciso e efficiente in Python. Comprendere questi strumenti ti permette di approcciare la programmazione con uno stile più funzionale. Nel prossimo articolo esploreremo alcune delle librerie di terze parti più utili in Python, come **NumPy** e **Pandas**.

---
layout: post
title:  "Liste e Tuple: Manipolazione delle sequenze"
date:   2024-09-08 13:30:00 +0200
categories: corso-python
tags: [python, liste, tuple, sequenze]
---

# Liste e Tuple: Manipolazione delle sequenze

In Python, le **liste** e le **tuple** sono due tipi di sequenze che ci permettono di immagazzinare più valori in un'unica variabile. Sebbene siano simili, ci sono alcune differenze fondamentali tra loro, come la mutabilità. In questo articolo, vedremo come creare e manipolare liste e tuple.

## Liste

Le liste in Python sono collezioni ordinate e mutabili, il che significa che puoi modificare gli elementi dopo la creazione della lista. Gli elementi di una lista possono essere di qualsiasi tipo.

### Creare una lista

Una lista si crea usando le parentesi quadre `[]`, separando gli elementi con virgole.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
numeri = [1, 2, 3, 4, 5]
misti = [1, "ciao", 3.14, True]
```

### Accesso agli elementi

Puoi accedere a un elemento di una lista utilizzando il suo **indice**. Gli indici in Python partono da 0.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
print(frutti[0])  # Stampa "mela"
```

Puoi anche usare indici negativi per accedere agli elementi partendo dalla fine della lista.

Esempio:
```python
print(frutti[-1])  # Stampa "arancia"
```

### Modificare una lista

Poiché le liste sono mutabili, puoi modificare gli elementi direttamente.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
frutti[1] = "pera"
print(frutti)  # Stampa ["mela", "pera", "arancia"]
```

### Aggiungere e rimuovere elementi

Puoi aggiungere elementi a una lista con il metodo `append()` e rimuoverli con `remove()` o `pop()`.

Esempio:
```python
frutti = ["mela", "banana"]
frutti.append("kiwi")  # Aggiunge "kiwi" alla lista
print(frutti)  # Stampa ["mela", "banana", "kiwi"]

frutti.remove("banana")  # Rimuove "banana"
print(frutti)  # Stampa ["mela", "kiwi"]

frutti.pop()  # Rimuove l'ultimo elemento
print(frutti)  # Stampa ["mela"]
```

### Slicing

Con lo slicing, puoi ottenere una porzione di una lista.

Esempio:
```python
numeri = [0, 1, 2, 3, 4, 5]
print(numeri[1:4])  # Stampa [1, 2, 3]
```

### Cicli con le liste

Puoi iterare su una lista usando un ciclo `for`.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
for frutto in frutti:
    print(frutto)
```

## Tuple

Le tuple sono simili alle liste, ma con una differenza importante: sono **immutabili**, il che significa che una volta create, non possono essere modificate. Le tuple vengono create usando le parentesi tonde `()`.

### Creare una tupla

Esempio:
```python
tupla_frutti = ("mela", "banana", "arancia")
tupla_numeri = (1, 2, 3, 4, 5)
tupla_mista = (1, "ciao", 3.14, True)
```

### Accesso agli elementi

Come per le liste, puoi accedere agli elementi di una tupla tramite il loro indice.

Esempio:
```python
tupla_frutti = ("mela", "banana", "arancia")
print(tupla_frutti[1])  # Stampa "banana"
```

### Slicing delle tuple

Anche con le tuple puoi utilizzare lo slicing per ottenere una porzione.

Esempio:
```python
tupla_numeri = (0, 1, 2, 3, 4, 5)
print(tupla_numeri[1:4])  # Stampa (1, 2, 3)
```

### Convertire una tupla in una lista

Sebbene le tuple siano immutabili, puoi convertirle in liste se hai bisogno di modificarne gli elementi.

Esempio:
```python
tupla_frutti = ("mela", "banana", "arancia")
lista_frutti = list(tupla_frutti)  # Converte la tupla in una lista
lista_frutti.append("kiwi")
print(lista_frutti)  # Stampa ["mela", "banana", "arancia", "kiwi"]
```

## Differenze tra liste e tuple

- **Mutabilità**: Le liste sono mutabili, mentre le tuple sono immutabili.
- **Prestazioni**: Le tuple sono generalmente più veloci delle liste quando si tratta di accesso agli elementi, poiché non devono supportare operazioni di modifica.
- **Usi**: Le liste sono usate quando è necessario un insieme dinamico di dati, mentre le tuple sono utilizzate per rappresentare dati che non devono essere modificati.

## Conclusione

In questo articolo abbiamo visto come creare e manipolare liste e tuple in Python. Entrambe sono potenti strumenti per gestire collezioni di dati, ma con differenze significative che influenzano come e quando usarle. Nel prossimo articolo esploreremo i **dizionari** e gli **insiemi**, altre strutture dati importanti in Python.

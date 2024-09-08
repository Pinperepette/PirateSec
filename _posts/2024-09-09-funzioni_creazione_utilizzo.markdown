---
layout: post
title:  "Funzioni: Creazione e utilizzo di funzioni"
date:   2024-09-08 13:30:00 +0200
categories: corso-python
tags: [python, funzioni, creazione-funzioni, utilizzo-funzioni]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Funzioni: Creazione e utilizzo di funzioni

Le funzioni sono uno dei concetti fondamentali in Python, e permettono di suddividere il codice in blocchi riutilizzabili. Una funzione è un insieme di istruzioni che eseguono un compito specifico e può essere richiamata ogni volta che è necessario quel compito.

## Creazione di una funzione

In Python, una funzione viene definita usando la parola chiave `def`, seguita dal nome della funzione e, se necessario, dai parametri tra parentesi. Il blocco di codice della funzione è indentato.

Esempio:
```python
def saluta():
    print("Ciao, benvenuto!")
```

Qui abbiamo creato una semplice funzione chiamata `saluta`. Ogni volta che richiameremo questa funzione, stamperà il messaggio "Ciao, benvenuto!".

### Chiamare una funzione

Per chiamare una funzione, basta scriverne il nome seguito da parentesi.

Esempio:
```python
saluta()  # Questo stamperà "Ciao, benvenuto!"
```

## Funzioni con parametri

Le funzioni possono accettare parametri, che sono valori che possiamo passare alla funzione al momento della chiamata.

Esempio:
```python
def saluta_persona(nome):
    print(f"Ciao, {nome}!")
```

In questo esempio, la funzione `saluta_persona` accetta un parametro `nome`. Quando richiamiamo la funzione, possiamo passare un valore specifico per il parametro.

Esempio:
```python
saluta_persona("Andrea")  # Questo stamperà "Ciao, Andrea!"
```

### Parametri di default

Puoi anche definire parametri con valori di default. Se non viene passato alcun valore quando la funzione viene chiamata, il parametro assumerà il valore predefinito.

Esempio:
```python
def saluta_persona(nome="ospite"):
    print(f"Ciao, {nome}!")
```

Se ora chiamiamo la funzione senza passare un argomento, verrà utilizzato il valore predefinito.

Esempio:
```python
saluta_persona()  # Questo stamperà "Ciao, ospite!"
```

## Funzioni con più parametri

Puoi anche definire funzioni che accettano più di un parametro.

Esempio:
```python
def somma(a, b):
    return a + b
```

Questa funzione accetta due parametri `a` e `b` e restituisce la loro somma. Il valore restituito viene ottenuto con la parola chiave `return`.

Esempio:
```python
risultato = somma(3, 5)
print(risultato)  # Questo stamperà 8
```

## Valori di ritorno

Le funzioni possono restituire un valore usando la parola chiave `return`. Quando una funzione viene chiamata, può restituire un risultato che può essere utilizzato nel resto del programma.

Esempio:
```python
def moltiplica(a, b):
    return a * b

prodotto = moltiplica(4, 5)
print(prodotto)  # Questo stamperà 20
```

## Funzioni con un numero variabile di argomenti

Puoi anche definire funzioni che accettano un numero variabile di argomenti, utilizzando l'asterisco `*` per indicare che la funzione può ricevere un numero arbitrario di parametri.

Esempio:
```python
def stampa_frutti(*frutti):
    for frutto in frutti:
        print(frutto)
```

Esempio di chiamata della funzione:
```python
stampa_frutti("mela", "banana", "arancia")  # Stampa ogni frutto su una nuova riga
```

## Funzioni lambda

Python supporta anche funzioni anonime chiamate "lambda". Una funzione lambda è una funzione semplice che può avere un numero qualsiasi di parametri, ma un solo corpo di istruzioni.

Esempio:
```python
somma = lambda a, b: a + b
print(somma(3, 5))  # Questo stamperà 8
```

Le funzioni lambda sono spesso utilizzate quando hai bisogno di una funzione semplice e veloce in una sola riga.

## Conclusione

Le funzioni sono uno strumento fondamentale per organizzare e riutilizzare il codice in Python. Ti permettono di suddividere un programma in blocchi più piccoli e facili da gestire, aumentando la leggibilità e la manutenibilità del codice. Nel prossimo articolo parleremo delle liste e delle tuple, due importanti strutture dati in Python.

---
layout: post
title:  "Decoratori e generatori: Concetti avanzati in Python"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, decoratori, generatori, concetti-avanzati]
---

# Decoratori e generatori: Concetti avanzati in Python

I **decoratori** e i **generatori** sono due potenti strumenti avanzati in Python che permettono di scrivere codice più pulito, riutilizzabile e performante. In questo articolo esploreremo cosa sono i decoratori e i generatori e come possono essere utilizzati nei tuoi progetti Python.

## Decoratori

Un **decoratore** è una funzione che prende un'altra funzione come input, aggiunge una funzionalità ad essa e restituisce una nuova funzione con la funzionalità estesa. I decoratori sono utilizzati per modificare il comportamento delle funzioni o dei metodi senza cambiarne il codice sorgente.

### Creare un decoratore

Ecco un semplice esempio di un decoratore che aggiunge un messaggio prima e dopo l'esecuzione di una funzione:

Esempio:
```python
def decoratore_semplice(funzione):
    def wrapper():
        print("Esecuzione prima della funzione.")
        funzione()
        print("Esecuzione dopo la funzione.")
    return wrapper
```

Qui abbiamo creato una funzione `decoratore_semplice` che prende una funzione come argomento, la esegue e aggiunge del codice prima e dopo la sua esecuzione.

### Utilizzare un decoratore

Per applicare il decoratore a una funzione, possiamo usare il simbolo `@` prima della definizione della funzione:

Esempio:
```python
@decoratore_semplice
def saluta():
    print("Ciao!")

saluta()
```

Il risultato sarà:
```
Esecuzione prima della funzione.
Ciao!
Esecuzione dopo la funzione.
```

### Decoratori con argomenti

I decoratori possono anche accettare argomenti se la funzione decorata ne ha.

Esempio:
```python
def decoratore_con_argomenti(funzione):
    def wrapper(*args, **kwargs):
        print("Esecuzione prima della funzione.")
        risultato = funzione(*args, **kwargs)
        print("Esecuzione dopo la funzione.")
        return risultato
    return wrapper

@decoratore_con_argomenti
def somma(a, b):
    return a + b

print(somma(3, 5))
```

Questo stamperà:
```
Esecuzione prima della funzione.
Esecuzione dopo la funzione.
8
```

### Decoratori per classi

I decoratori possono essere utilizzati anche per le classi, per esempio, per modificare il comportamento di metodi o aggiungere funzionalità a tutte le istanze della classe.

Esempio:
```python
def decoratore_di_classe(funzione):
    def wrapper(self, *args, **kwargs):
        print("Metodo decorato.")
        return funzione(self, *args, **kwargs)
    return wrapper

class Ciao:
    @decoratore_di_classe
    def saluta(self):
        print("Ciao, mondo!")

ciao = Ciao()
ciao.saluta()
```

## Generatori

Un **generatore** è una funzione che restituisce un oggetto su cui possiamo iterare, un elemento alla volta. I generatori consentono di risparmiare memoria, poiché generano gli elementi solo quando necessario, invece di restituire l'intera sequenza in una volta.

### Creare un generatore

Un generatore viene definito come una normale funzione, ma invece di usare `return`, usa la parola chiave `yield` per restituire i valori uno alla volta.

Esempio:
```python
def conto_alla_rovescia(n):
    while n > 0:
        yield n
        n -= 1

for numero in conto_alla_rovescia(5):
    print(numero)
```

Il risultato sarà:
```
5
4
3
2
1
```

In questo esempio, `conto_alla_rovescia` è un generatore che restituisce i numeri da `n` a 1 uno alla volta.

### Perché usare i generatori?

I generatori sono utili quando si lavora con grandi quantità di dati, poiché generano gli elementi solo quando vengono richiesti, risparmiando memoria e migliorando le prestazioni. Sono particolarmente utili per lavorare con file di grandi dimensioni o per produrre flussi infiniti di dati.

### Generator expression

Simile alle list comprehension, possiamo creare generatori con una sintassi concisa, chiamata **generator expression**.

Esempio:
```python
numeri = (x * x for x in range(5))
for numero in numeri:
    print(numero)
```

Questo esempio genera il quadrato dei numeri da 0 a 4, ma lo fa in modo "pigro", generando ogni valore solo quando necessario.

## Conclusione

I decoratori e i generatori sono strumenti potenti che ti permettono di scrivere codice più efficiente e leggibile. I decoratori estendono il comportamento delle funzioni, mentre i generatori ti aiutano a risparmiare memoria e a lavorare con grandi quantità di dati in modo più efficiente. Nel prossimo articolo, esploreremo le **funzioni lambda** e la **programmazione funzionale** in Python.

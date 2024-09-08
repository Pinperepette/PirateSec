---
layout: post
title:  "Dizionari e Insiemi: Strutture di dati avanzate"
date:   2024-09-08 14:00:00 +0200
categories: corso-python
tags: [python, dizionari, insiemi, strutture-dati]
---

# Dizionari e Insiemi: Strutture di dati avanzate

Oltre a liste e tuple, Python offre altre due importanti strutture di dati: i **dizionari** e gli **insiemi**. Queste strutture ci permettono di memorizzare e manipolare collezioni di dati in modi particolari e molto utili per diverse applicazioni.

## Dizionari

I dizionari in Python sono collezioni non ordinate di coppie **chiave-valore**. Ogni chiave in un dizionario deve essere unica e immutabile (ad esempio, stringhe o numeri), mentre i valori possono essere di qualsiasi tipo e possono essere duplicati.

### Creare un dizionario

Un dizionario si crea utilizzando parentesi graffe `{}` con coppie chiave-valore separate da due punti.

Esempio:
```python
dizionario = {
    "nome": "Andrea",
    "età": 25,
    "città": "Roma"
}
```

### Accesso agli elementi

Puoi accedere al valore associato a una chiave specifica utilizzando la chiave stessa.

Esempio:
```python
print(dizionario["nome"])  # Stampa "Andrea"
```

### Modificare un dizionario

Puoi aggiungere nuove coppie chiave-valore o modificare i valori esistenti.

Esempio:
```python
dizionario["età"] = 26  # Modifica il valore associato a "età"
dizionario["professione"] = "Sviluppatore"  # Aggiunge una nuova coppia
print(dizionario)
```

### Metodi utili

I dizionari in Python hanno diversi metodi utili, come:

- `keys()`: restituisce una vista di tutte le chiavi.
- `values()`: restituisce una vista di tutti i valori.
- `items()`: restituisce una vista di tutte le coppie chiave-valore.

Esempio:
```python
print(dizionario.keys())  # Stampa tutte le chiavi
print(dizionario.values())  # Stampa tutti i valori
print(dizionario.items())  # Stampa tutte le coppie chiave-valore
```

### Verificare la presenza di una chiave

Puoi verificare se una chiave esiste in un dizionario usando l'operatore `in`.

Esempio:
```python
if "nome" in dizionario:
    print("La chiave 'nome' è presente nel dizionario.")
```

### Rimuovere elementi

Puoi rimuovere una coppia chiave-valore con il metodo `pop()` o eliminare tutte le coppie con `clear()`.

Esempio:
```python
dizionario.pop("età")  # Rimuove la chiave "età"
print(dizionario)
dizionario.clear()  # Rimuove tutte le coppie
print(dizionario)
```

## Insiemi

Gli insiemi sono collezioni non ordinate di elementi unici. Gli insiemi sono simili alle liste, ma non permettono duplicati e non hanno un ordine definito.

### Creare un insieme

Gli insiemi vengono creati usando le parentesi graffe `{}` o la funzione `set()`.

Esempio:
```python
insieme = {"mela", "banana", "arancia"}
insieme_vuoto = set()  # Crea un insieme vuoto
```

### Aggiungere e rimuovere elementi

Puoi aggiungere elementi a un insieme con il metodo `add()` e rimuoverli con `remove()` o `discard()`.

Esempio:
```python
insieme.add("kiwi")  # Aggiunge "kiwi" all'insieme
print(insieme)
insieme.remove("banana")  # Rimuove "banana"
print(insieme)
```

### Operazioni sugli insiemi

Gli insiemi supportano operazioni matematiche come **unione**, **intersezione** e **differenza**.

- **Unione**: restituisce un nuovo insieme contenente tutti gli elementi di entrambi gli insiemi.
- **Intersezione**: restituisce un nuovo insieme contenente solo gli elementi comuni a entrambi gli insiemi.
- **Differenza**: restituisce un nuovo insieme contenente gli elementi presenti solo nel primo insieme.

Esempio:
```python
frutti1 = {"mela", "banana", "arancia"}
frutti2 = {"banana", "kiwi", "uva"}

unione = frutti1.union(frutti2)
print(unione)  # Stampa {"mela", "banana", "arancia", "kiwi", "uva"}

intersezione = frutti1.intersection(frutti2)
print(intersezione)  # Stampa {"banana"}

differenza = frutti1.difference(frutti2)
print(differenza)  # Stampa {"mela", "arancia"}
```

### Verificare la presenza di un elemento

Puoi verificare se un elemento è presente in un insieme utilizzando l'operatore `in`.

Esempio:
```python
if "mela" in insieme:
    print("L'elemento 'mela' è presente nell'insieme.")
```

## Conclusione

I dizionari e gli insiemi sono strumenti potenti che ti permettono di gestire dati in modo efficiente e flessibile. I dizionari sono utili quando hai bisogno di una struttura di dati che associa chiavi a valori, mentre gli insiemi sono ideali per lavorare con collezioni di elementi unici. Nel prossimo articolo, parleremo di come gestire gli **errori** in Python.

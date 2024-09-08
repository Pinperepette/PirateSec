---
layout: post
title:  "Testing e debugging in Python"
date:   2024-09-08 19:00:00 +0200
categories: corso-python
tags: [python, testing, debugging, unittest]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Testing e debugging in Python

Scrivere codice senza errori è difficile, motivo per cui è importante utilizzare tecniche di **testing** e **debugging** per individuare e correggere i problemi nei nostri programmi. In questo articolo esploreremo gli strumenti di testing e debugging in Python, concentrandoci su come utilizzare il modulo **unittest** e il debugger integrato **pdb**.

## Testing

Il **testing** consiste nel verificare che il nostro codice funzioni come previsto. In Python esistono diversi strumenti per eseguire test automatici, tra cui il modulo **unittest**, che fa parte della libreria standard di Python.

### Creare test con unittest

Il modulo **unittest** permette di creare test per il nostro codice, organizzandoli in classi che estendono `unittest.TestCase`. Un test è una funzione che verifica un determinato comportamento del codice e fallisce se questo comportamento non è rispettato.

Esempio:
```python
import unittest

def somma(a, b):
    return a + b

class TestSomma(unittest.TestCase):
    def test_somma_positivi(self):
        self.assertEqual(somma(1, 2), 3)
    
    def test_somma_negativi(self):
        self.assertEqual(somma(-1, -1), -2)

if __name__ == "__main__":
    unittest.main()
```

In questo esempio, abbiamo creato due test per la funzione `somma()`. Il metodo `assertEqual()` verifica che il risultato sia quello previsto.

### Eseguire i test

Per eseguire i test, basta lanciare lo script come un normale programma Python. Il framework unittest eseguirà automaticamente tutti i test definiti.

### Altri metodi di unittest

Oltre a `assertEqual()`, unittest fornisce diversi metodi per verificare il comportamento del codice:

- `assertTrue()`/`assertFalse()`: verifica che una condizione sia vera o falsa.
- `assertRaises()`: verifica che venga sollevata una determinata eccezione.
- `assertIn()`: verifica che un elemento sia presente in una sequenza.

### Test parametrizzati con pytest

Oltre a unittest, esiste un'altra libreria molto popolare per il testing in Python chiamata **pytest**, che permette di scrivere test più concisi e leggibili. Offre anche funzionalità avanzate come i test parametrizzati.

Esempio di test con pytest:
```python
import pytest

def somma(a, b):
    return a + b

@pytest.mark.parametrize("a,b,risultato", [(1, 2, 3), (-1, -1, -2), (0, 0, 0)])
def test_somma(a, b, risultato):
    assert somma(a, b) == risultato
```

## Debugging

Il **debugging** consiste nell'individuare e risolvere i bug, cioè gli errori nel codice. Python offre vari strumenti per eseguire il debugging, incluso il debugger integrato **pdb**.

### Usare pdb per il debugging

Il modulo **pdb** (Python Debugger) permette di eseguire il codice passo passo, osservando il valore delle variabili e individuando esattamente dove si verifica un errore.

Esempio di utilizzo di pdb:
```python
import pdb

def somma(a, b):
    pdb.set_trace()  # Punto di interruzione
    return a + b

print(somma(3, 5))
```

Quando viene eseguito il programma, `pdb.set_trace()` mette in pausa l'esecuzione del codice e apre una sessione interattiva del debugger, dove puoi eseguire comandi come:

- `n`: esegui la prossima istruzione.
- `c`: continua fino al prossimo punto di interruzione.
- `p`: stampa il valore di una variabile (es. `p a`).
- `q`: esci dal debugger.

### Debugging con Visual Studio Code

Se preferisci un'interfaccia grafica, puoi usare il debugger integrato in Visual Studio Code. Ti permette di impostare punti di interruzione visivi, eseguire il codice passo passo e visualizzare le variabili in tempo reale.

### Gestione delle eccezioni con try-except

Un altro strumento fondamentale per il debugging è l'uso di **try-except** per gestire le eccezioni e prevenire che errori imprevisti interrompano il programma.

Esempio:
```python
def dividi(a, b):
    try:
        risultato = a / b
    except ZeroDivisionError:
        print("Errore: divisione per zero!")
        return None
    else:
        return risultato

print(dividi(10, 0))
```

In questo esempio, se si tenta di dividere per zero, il programma non si interrompe, ma gestisce l'errore e stampa un messaggio.

## Conclusione

Il testing e il debugging sono due aspetti essenziali della programmazione che ti aiutano a garantire che il tuo codice funzioni correttamente e sia privo di errori. Unittest e pdb sono strumenti potenti che ogni sviluppatore Python dovrebbe conoscere. Nel prossimo articolo, parleremo di come interagire con i **database** in Python utilizzando SQLite.

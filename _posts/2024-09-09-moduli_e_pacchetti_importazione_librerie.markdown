---
layout: post
title:  "Moduli e pacchetti: Importazione di librerie esterne"
date:   2024-09-08 16:00:00 +0200
categories: corso-python
tags: [python, moduli, pacchetti, librerie]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Moduli e pacchetti: Importazione di librerie esterne

Uno dei punti di forza di Python è la sua vasta gamma di moduli e pacchetti che consentono di estendere le funzionalità del linguaggio. In questo articolo, esploreremo come utilizzare i moduli e i pacchetti, come importarli e come crearne di propri per organizzare al meglio il nostro codice.

## Cos'è un modulo?

Un **modulo** è un file Python che contiene definizioni e istruzioni, come funzioni, classi o variabili, che possono essere riutilizzate in altri programmi Python. I moduli ci permettono di organizzare il codice in modo più leggibile e manutenibile.

### Importare un modulo

Per importare un modulo, utilizziamo la parola chiave `import` seguita dal nome del modulo.

Esempio:
```python
import math
```

In questo caso, abbiamo importato il modulo **math**, che contiene funzioni matematiche predefinite.

### Utilizzare le funzioni di un modulo

Una volta importato un modulo, possiamo utilizzare le sue funzioni o variabili usando la notazione punto.

Esempio:
```python
import math

risultato = math.sqrt(16)
print(risultato)  # Stampa 4.0
```

In questo esempio, stiamo utilizzando la funzione `sqrt()` del modulo **math** per calcolare la radice quadrata di 16.

### Importare solo alcune parti di un modulo

È possibile importare solo una parte specifica di un modulo utilizzando la sintassi `from`.

Esempio:
```python
from math import sqrt

print(sqrt(25))  # Stampa 5.0
```

In questo caso, abbiamo importato solo la funzione `sqrt()` dal modulo **math**.

### Dare un alias a un modulo

Per semplificare l'uso dei nomi dei moduli, possiamo assegnare loro un **alias** utilizzando la parola chiave `as`.

Esempio:
```python
import math as m

print(m.pi)  # Stampa 3.141592653589793
```

Qui, abbiamo assegnato al modulo **math** l'alias `m`, permettendoci di utilizzare `m` al posto di `math`.

## Creare un modulo personalizzato

Puoi anche creare il tuo modulo personalizzato salvando le funzioni in un file con estensione `.py`. Ad esempio, supponiamo di avere un file chiamato `mio_modulo.py` con il seguente contenuto:

```python
def saluta():
    print("Ciao dal mio modulo!")
```

Per utilizzare questo modulo in un altro script Python, basta importarlo come qualsiasi altro modulo:

```python
import mio_modulo

mio_modulo.saluta()  # Stampa "Ciao dal mio modulo!"
```

## Cos'è un pacchetto?

Un **pacchetto** è una raccolta di moduli organizzati in una directory con un file speciale chiamato `__init__.py`. Il file `__init__.py` può essere vuoto, ma la sua presenza indica a Python che quella directory è un pacchetto.

Esempio di struttura di un pacchetto:

```
mio_pacchetto/
    __init__.py
    modulo1.py
    modulo2.py
```

Puoi importare i moduli di un pacchetto come segue:

```python
import mio_pacchetto.modulo1
import mio_pacchetto.modulo2
```

## Installare pacchetti esterni con pip

Python ha una vasta libreria di pacchetti esterni che possono essere installati utilizzando **pip**, il gestore di pacchetti di Python. Per installare un pacchetto, esegui il seguente comando da terminale:

```bash
pip install nome_pacchetto
```

Ad esempio, per installare il pacchetto **requests**, utilizza:

```bash
pip install requests
```

Dopo aver installato il pacchetto, puoi importarlo nel tuo codice:

```python
import requests

response = requests.get("https://api.github.com")
print(response.status_code)
```

## Conclusione

L'uso di moduli e pacchetti ti permette di organizzare il tuo codice in modo modulare e di sfruttare la potenza della comunità Python attraverso migliaia di pacchetti disponibili. Nel prossimo articolo, parleremo della **programmazione orientata agli oggetti** in Python.

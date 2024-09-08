---
layout: post
title:  "Gestione degli errori: try-except e gestione delle eccezioni"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, gestione-errori, eccezioni, try-except]
---

# Gestione degli errori: try-except e gestione delle eccezioni

Durante l'esecuzione di un programma, possono verificarsi errori che ne causano l'interruzione. In Python, questi errori sono chiamati **eccezioni**. La gestione delle eccezioni permette di prevedere e gestire errori senza interrompere il flusso del programma. In questo articolo vedremo come utilizzare `try`, `except` e altre parole chiave correlate per gestire in modo efficace gli errori.

## Cos'è un'eccezione?

Un'eccezione si verifica quando Python non riesce a eseguire un'operazione e genera un errore. Ad esempio, se provi a dividere un numero per zero, Python solleva un'eccezione `ZeroDivisionError`.

Esempio:
```python
x = 10 / 0  # Questo solleva un errore ZeroDivisionError
```

Senza gestione degli errori, questo blocca il programma. Per prevenire tali blocchi, possiamo utilizzare il blocco `try-except`.

## Gestione delle eccezioni con `try-except`

Il blocco `try-except` consente di intercettare un'eccezione e gestirla senza interrompere l'esecuzione del programma.

Esempio:
```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Errore: divisione per zero!")
```

In questo caso, Python prova a eseguire il codice nel blocco `try`. Se si verifica un'eccezione (in questo caso, `ZeroDivisionError`), esegue il codice nel blocco `except`.

## Gestione di eccezioni multiple

Puoi gestire diversi tipi di eccezioni utilizzando più blocchi `except`.

Esempio:
```python
try:
    x = int(input("Inserisci un numero: "))
    y = 10 / x
except ZeroDivisionError:
    print("Errore: divisione per zero!")
except ValueError:
    print("Errore: valore non valido!")
```

In questo esempio, se l'utente inserisce un valore non numerico, viene sollevata un'eccezione `ValueError`. Se invece inserisce `0`, si verifica un `ZeroDivisionError`.

## Il blocco `else`

Il blocco `else` viene eseguito solo se non si verificano eccezioni nel blocco `try`.

Esempio:
```python
try:
    x = int(input("Inserisci un numero: "))
    y = 10 / x
except ZeroDivisionError:
    print("Errore: divisione per zero!")
except ValueError:
    print("Errore: valore non valido!")
else:
    print(f"Il risultato è: {y}")
```

Se non si verifica alcuna eccezione, il codice nel blocco `else` viene eseguito e viene stampato il risultato della divisione.

## Il blocco `finally`

Il blocco `finally` viene eseguito sempre, sia che si verifichi un'eccezione sia che non si verifichi. È utile per eseguire operazioni di pulizia, come chiudere file o connessioni di rete.

Esempio:
```python
try:
    x = int(input("Inserisci un numero: "))
    y = 10 / x
except ZeroDivisionError:
    print("Errore: divisione per zero!")
except ValueError:
    print("Errore: valore non valido!")
else:
    print(f"Il risultato è: {y}")
finally:
    print("Operazione completata.")
```

Il blocco `finally` verrà eseguito sempre, indipendentemente da come si concluda il `try-except`.

## Sollevare eccezioni con `raise`

In alcuni casi, potresti voler sollevare un'eccezione manualmente usando la parola chiave `raise`. Questo può essere utile per gestire errori personalizzati o condizioni specifiche nel tuo programma.

Esempio:
```python
x = -10
if x < 0:
    raise ValueError("Il numero non può essere negativo!")
```

Qui, abbiamo sollevato manualmente un'eccezione `ValueError` se il valore di `x` è negativo.

## Definire eccezioni personalizzate

Python permette anche di definire eccezioni personalizzate creando nuove classi che ereditano da `Exception`.

Esempio:
```python
class ErrorePersonalizzato(Exception):
    pass

try:
    raise ErrorePersonalizzato("Questo è un errore personalizzato!")
except ErrorePersonalizzato as e:
    print(e)
```

In questo caso, abbiamo definito una nuova eccezione chiamata `ErrorePersonalizzato` e l'abbiamo sollevata all'interno di un blocco `try`.

## Conclusione

La gestione degli errori è un aspetto essenziale nella scrittura di programmi robusti e sicuri. Utilizzando il blocco `try-except`, puoi prevenire che errori inattesi interrompano il tuo programma. Nel prossimo articolo esploreremo come lavorare con l'**input/output** per gestire file e altre operazioni.

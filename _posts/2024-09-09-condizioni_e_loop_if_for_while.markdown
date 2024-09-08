---
layout: post
title:  "Condizioni e loop: if, for, while"
date:   2024-09-08 13:00:00 +0200
categories: corso-python
tags: [python, condizioni, loop, if, for, while]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Condizioni e loop: if, for, while

In questo articolo esploreremo le strutture di controllo in Python, che ti permettono di eseguire blocchi di codice in base a condizioni specifiche e di ripetere operazioni con cicli. Vedremo le istruzioni `if`, i cicli `for` e `while`.

## Condizioni: if, elif, else

L'istruzione `if` viene utilizzata per eseguire del codice solo se una certa condizione è vera. Puoi anche combinare più condizioni con le parole chiave `elif` (altrimenti se) e `else` (altrimenti).

Esempio:
```python
x = 10
if x > 5:
    print("x è maggiore di 5")
elif x == 5:
    print("x è uguale a 5")
else:
    print("x è minore di 5")
```

In questo esempio, Python controlla la condizione `x > 5`. Se è vera, stampa "x è maggiore di 5". Altrimenti, controlla `x == 5`. Se nessuna delle condizioni è vera, esegue il blocco associato a `else`.

### Condizioni annidate

È possibile annidare le condizioni `if` per gestire casi più complessi.

Esempio:
```python
x = 10
y = 5
if x > 5:
    if y > 3:
        print("x è maggiore di 5 e y è maggiore di 3")
```

## Cicli: for

Il ciclo `for` in Python viene utilizzato per iterare su una sequenza (come una lista, una stringa, o un intervallo di numeri) e permette di eseguire un'operazione ripetuta per ogni elemento della sequenza.

Esempio:
```python
frutti = ["mela", "banana", "arancia"]
for frutto in frutti:
    print(frutto)
```

In questo caso, il ciclo `for` itera su ogni elemento della lista `frutti` e stampa ogni frutto a turno.

### La funzione `range()`

La funzione `range()` viene spesso utilizzata con `for` per generare una sequenza di numeri.

Esempio:
```python
for i in range(5):
    print(i)
```

Questo stamperà i numeri da 0 a 4. La funzione `range()` genera una sequenza che inizia da 0 e finisce a `n-1`, dove `n` è il valore passato come argomento.

## Cicli: while

Il ciclo `while` ripete un blocco di codice finché una condizione è vera. È utile quando non sai a priori quante volte eseguire il ciclo.

Esempio:
```python
i = 0
while i < 5:
    print(i)
    i += 1
```

In questo esempio, il ciclo continua a eseguire il blocco finché `i` è minore di 5. Dopo ogni iterazione, `i` viene incrementato di 1 con l'operatore `+=`.

## Parole chiave `break` e `continue`

- `break`: esce dal ciclo immediatamente.
- `continue`: salta l'iterazione corrente e passa alla successiva.

Esempio:
```python
for i in range(5):
    if i == 3:
        break  # Esce dal ciclo quando i è uguale a 3
    print(i)
```

In questo caso, il ciclo si interrompe quando `i` è uguale a 3.

Esempio con `continue`:
```python
for i in range(5):
    if i == 3:
        continue  # Salta l'iterazione quando i è uguale a 3
    print(i)
```

In questo esempio, `continue` salta l'iterazione quando `i` è uguale a 3, ma il ciclo continua con le altre iterazioni.

## Conclusione

Abbiamo visto come usare le condizioni `if`, `elif`, `else` e i cicli `for` e `while` per controllare il flusso del programma. Queste strutture ti permettono di prendere decisioni e ripetere operazioni in modo efficiente, due aspetti fondamentali per qualsiasi programma complesso. Nel prossimo articolo esploreremo le funzioni, che ti permetteranno di organizzare il tuo codice in blocchi riutilizzabili.

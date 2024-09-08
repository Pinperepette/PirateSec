---
layout: post
title:  "Input/Output: Gestione dei file"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, input-output, file, gestione-file]
---

# Input/Output: Gestione dei file

In Python, leggere da file e scrivere su file è un'operazione comune in molti programmi. L'input/output (I/O) con file ci permette di salvare dati, caricare informazioni da fonti esterne e molto altro. In questo articolo, vedremo come aprire, leggere, scrivere e chiudere file in Python.

## Aprire un file

Per aprire un file in Python, usiamo la funzione `open()`, che restituisce un oggetto file. È possibile aprire un file in diverse modalità:

- `"r"`: lettura (default).
- `"w"`: scrittura (sovrascrive il file se esiste).
- `"a"`: aggiunta (scrive alla fine del file senza sovrascriverlo).
- `"b"`: modalità binaria.
- `"x"`: crea un file nuovo, restituisce errore se esiste già.

Esempio:
```python
file = open("esempio.txt", "r")
```

Questo codice apre il file `esempio.txt` in modalità lettura.

## Leggere da un file

Esistono diversi metodi per leggere da un file:

- `read()`: legge l'intero contenuto del file.
- `readline()`: legge una riga alla volta.
- `readlines()`: legge tutte le righe e le restituisce come lista.

Esempio:
```python
file = open("esempio.txt", "r")
contenuto = file.read()  # Legge tutto il file
print(contenuto)
file.close()  # Chiude il file dopo aver finito di leggere
```

In alternativa, possiamo leggere una riga alla volta:
```python
file = open("esempio.txt", "r")
prima_riga = file.readline()
print(prima_riga)
file.close()
```

## Scrivere su un file

Per scrivere su un file, è necessario aprirlo in modalità scrittura (`"w"`) o aggiunta (`"a"`). Il metodo `write()` consente di scrivere stringhe nel file.

Esempio:
```python
file = open("esempio.txt", "w")  # Sovrascrive il file se esiste
file.write("Questo è un esempio.
")
file.write("Aggiungiamo un'altra riga.")
file.close()  # Ricordati di chiudere il file
```

## Usare il costrutto `with`

Il costrutto `with` è un modo conveniente per gestire file, poiché assicura che il file venga chiuso correttamente dopo essere stato aperto, anche in caso di eccezioni.

Esempio:
```python
with open("esempio.txt", "r") as file:
    contenuto = file.read()
    print(contenuto)
# Il file è stato automaticamente chiuso alla fine del blocco
```

Questo approccio elimina la necessità di chiamare manualmente `file.close()`.

## Modalità binaria

Quando si lavora con file non di testo, come immagini o file eseguibili, si usa la modalità binaria (`"b"`).

Esempio:
```python
with open("immagine.jpg", "rb") as file:
    dati = file.read()
```

In questo esempio, leggiamo un'immagine in modalità binaria.

## Spostarsi all'interno di un file

Puoi usare `seek()` per spostarti a una posizione specifica all'interno di un file.

Esempio:
```python
with open("esempio.txt", "r") as file:
    file.seek(5)  # Si sposta alla posizione 5
    print(file.read())
```

## Aggiungere a un file

Per aggiungere del testo alla fine di un file esistente, usa la modalità `"a"`.

Esempio:
```python
with open("esempio.txt", "a") as file:
    file.write("
Questa riga è stata aggiunta.")
```

## Gestire file grandi

Se il file è molto grande, potresti non voler leggere tutto il contenuto in una sola volta. Puoi leggere il file in blocchi di dati per gestire meglio la memoria.

Esempio:
```python
with open("file_grande.txt", "r") as file:
    for riga in file:
        print(riga)
```

In questo modo, Python legge una riga alla volta, il che è più efficiente per file di grandi dimensioni.

## Conclusione

La gestione dei file è una delle competenze fondamentali in Python. Abbiamo visto come aprire, leggere, scrivere e chiudere file, oltre a utilizzare il costrutto `with` per una gestione più sicura. Nel prossimo articolo esploreremo i **moduli e pacchetti**, che ti permetteranno di organizzare meglio il tuo codice e riutilizzare funzionalità in modo efficiente.

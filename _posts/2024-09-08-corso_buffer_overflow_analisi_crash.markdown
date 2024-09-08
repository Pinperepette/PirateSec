---
layout: post
title:  "Corso Buffer Overflow: Analisi del Crash"
date:   2024-09-08 13:00:00 +0200
categories: buffer-overflow
tags: [buffer-overflow, crash-analysis, exploit]
---

# Corso Buffer Overflow: Analisi del Crash

Nel primo articolo abbiamo esplorato il **fuzzing** e come utilizzarlo per causare il crash di un programma vulnerabile. Ora ci concentreremo sull'**analisi del crash**, per determinare l'offset corretto che ci permetterà di sovrascrivere l'**EIP (Instruction Pointer)** e, successivamente, di controllare il flusso di esecuzione.

## Strumenti richiesti

- **Immunity Debugger**: Un debugger gratuito per Windows che ti permette di analizzare i crash dei programmi.
- **mona.py**: Un plugin per Immunity Debugger che automatizza la ricerca dell'offset.

## Procedura

### 1. Caricamento del programma in Immunity Debugger

Per prima cosa, carica il programma vulnerabile in Immunity Debugger:

1. Apri Immunity Debugger.
2. Fai clic su `File` > `Open`, e seleziona il programma vulnerabile.

Avvia il programma in modalità di debug cliccando su **F9**.

### 2. Riprodurre il crash

Avvia lo script di fuzzing che abbiamo creato nella prima parte per inviare il payload che provoca il crash del programma. Una volta che il programma crasha, Immunity Debugger dovrebbe fermarsi e mostrarti che l'EIP è stato sovrascritto.

### 3. Trovare l'offset corretto con mona.py

Una volta che il programma è crashato, possiamo usare mona.py per trovare l'offset esatto che ha sovrascritto l'EIP.

1. Digita il seguente comando nella finestra dei comandi di Immunity:

    ```
    !mona findmsp
    ```

   Questo comando ti restituirà l'offset che ci indica la lunghezza del buffer necessaria per raggiungere l'EIP.

### 4. Generazione del pattern per confermare l'offset

Ora possiamo generare un pattern con mona.py per confermare l'offset corretto:

1. Usa il seguente comando per generare un pattern unico con lunghezza sufficientemente grande da causare l'overflow:

    ```
    !mona pattern_create 4000
    ```

2. Copia il pattern generato e modificalo nel tuo script Python come payload:

    ```python
    payload = "Aa0Aa1Aa2Aa3..."
    ```

3. Dopo aver causato il crash con questo nuovo payload, Immunity Debugger ti mostrerà il contenuto dell'EIP.

4. Usa mona.py per trovare l'offset esatto:

    ```
    !mona pattern_offset EIP_value
    ```

   Sostituisci `EIP_value` con il valore che vedi sovrascritto nell'EIP. Mona restituirà l'offset corretto che ti permetterà di sapere quanto deve essere lungo il buffer per controllare l'EIP.

## Prossimi Passi

Ora che conosciamo l'offset esatto, siamo pronti a creare un payload che sovrascrive l'EIP con un indirizzo specifico e ci permette di eseguire un shellcode. Nella prossima parte, ci concentreremo sulla **creazione del payload e shellcode**.


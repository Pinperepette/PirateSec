---
layout: post
title:  "Corso Heap Overflow: Allocazione e Struttura dell'Heap"
date:   2024-09-08 13:00:00 +0200
categories: heap-overflow
tags: [heap-overflow, heap, allocazione, exploit]
---

# Corso Heap Overflow: Allocazione e Struttura dell'Heap

Nella lezione precedente, abbiamo introdotto il concetto di heap overflow e discusso la sua differenza rispetto ai buffer overflow. In questa lezione, ci addentreremo più nel dettaglio sulla gestione dell'allocazione di memoria nell'heap e analizzeremo come funziona a livello tecnico. Capire questi dettagli è fondamentale per comprendere le vulnerabilità legate all'heap e sfruttarle in modo efficace.

## 1. Come Funziona l'Allocazione dell'Heap

L'heap viene utilizzato per allocare memoria dinamica a runtime. I programmi richiedono blocchi di memoria utilizzando funzioni come `malloc()` in C, che preleva una porzione di memoria dall'heap e la restituisce al programma. Quando il programma non ha più bisogno di quella memoria, la dealloca usando `free()`, liberando quel blocco di memoria per essere riutilizzato.

### Struttura Interna dell'Heap

L'heap è diviso in **chunk**, ognuno dei quali ha una struttura precisa. Ogni chunk ha un **header** che contiene informazioni sul chunk stesso e un'area dati chiamata **payload**.

#### Esempio di un Chunk:

```
+-------------------+
| Header (Metadati)  |
| - Dimensione      |
| - Stato (libero o allocato) |
+-------------------+
|   Payload (Dati)  |
+-------------------+
```

### Allocazione dell'Heap su Linux: ptmalloc

Su sistemi Linux, la maggior parte delle allocazioni dell'heap avviene tramite **ptmalloc**, una versione di **dlmalloc** (Doug Lea's malloc). È un'implementazione ottimizzata per le moderne librerie C e ha meccanismi complessi per la gestione della memoria. Alcuni concetti chiave includono:

- **Fastbins**: Liste di chunk piccoli che vengono liberati e riutilizzati rapidamente.
- **Unsorted Bins**: Quando un chunk viene liberato, viene inizialmente inserito in una lista di chunk non ordinati.
- **Small Bins**: Liste di chunk di dimensioni fisse che vengono ordinati per dimensione.
- **Large Bins**: Liste di chunk più grandi, anch'essi ordinati per dimensione.

Quando richiedi un blocco di memoria con `malloc()`, il sistema controlla se c'è un chunk di dimensioni appropriate già libero e disponibile in uno di questi bin. Se non esiste, il sistema alloca nuova memoria, espandendo l'heap.

### Allocazione su Windows: Windows Heap Manager

Su Windows, il gestore dell'heap funziona in modo simile a ptmalloc ma con alcune differenze architetturali. Ogni processo ha uno o più heap, gestiti tramite **HeapCreate**, **HeapAlloc**, e **HeapFree**.

- **Lookaside Lists**: Una struttura usata da Windows per tenere traccia dei blocchi di memoria piccoli e frequentemente allocati.
- **Heap Segments**: L'heap è suddiviso in segmenti, ciascuno dei quali contiene blocchi di memoria di diverse dimensioni.

### Chunk Header in ptmalloc

Per comprendere meglio come funziona la corruzione dell'heap, dobbiamo analizzare il **chunk header** in dettaglio. Un chunk nell'heap ha un'intestazione che include informazioni come la dimensione del chunk e lo stato (allocato o libero).

Un esempio semplificato di chunk header in ptmalloc potrebbe essere:

```
+-------------------+
| Precedente Size    |  (Solo se il chunk precedente è libero)
+-------------------+
| Size              |  (Contiene lo stato del chunk e la dimensione)
+-------------------+
| Forward Pointer   |  (Usato per i chunk liberi)
+-------------------+
| Backward Pointer  |  (Usato per i chunk liberi)
+-------------------+
| Payload (Dati)    |  (Memoria disponibile per il programma)
+-------------------+
```

Ogni chunk ha un puntatore al chunk successivo e a quello precedente nella lista. Quando un chunk viene liberato, viene reinserito nella lista dei chunk liberi e i puntatori vengono aggiornati per mantenerne il corretto ordinamento.

## 2. Heap Overflow: Sovrascrivere il Chunk Header

Quando avviene un heap overflow, il programma scrive più dati di quelli previsti nel payload di un chunk, causando la corruzione dell'header del chunk successivo. Questo può portare a sovrascrivere informazioni cruciali come la dimensione del chunk o i puntatori avanti e indietro.

### Esempio di Sovrascrittura dell'Header

Supponiamo di avere un programma vulnerabile che alloca due chunk consecutivi nell'heap:

```c
char *chunk1 = malloc(64);
char *chunk2 = malloc(64);
```

In uno scenario di heap overflow, un errore nel programma potrebbe causare la scrittura di troppi dati in `chunk1`, andando a sovrascrivere l'header di `chunk2`:

```c
strcpy(chunk1, "AAAAAAAA... (più di 64 byte)");
```

Se `chunk2` viene liberato e i puntatori dell'header sono corrotti, potresti riuscire a manipolare la gestione dell'heap per ottenere l'esecuzione di codice arbitrario.

## 3. Attacchi Classici Basati su Heap Overflow

Esistono diversi attacchi classici che sfruttano heap overflow, tra cui:

- **Unlink Attack**: Manipolazione dei puntatori avanti e indietro per sovrascrivere il flusso di controllo.
- **Fastbin Duplication**: Manipolazione dei fastbin per ottenere chunk duplicati e sovrascrivere aree di memoria critiche.

Nel prossimo capitolo, esploreremo più in dettaglio uno di questi attacchi e vedremo come sfruttare heap overflow in un ambiente controllato.


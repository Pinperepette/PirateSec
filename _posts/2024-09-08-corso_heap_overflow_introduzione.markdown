---
layout: post
title:  "Corso Heap Overflow: Introduzione"
date:   2024-09-08 12:00:00 +0200
categories: heap-overflow
tags: [heap-overflow, exploit, sicurezza, overflow]
---

# Corso Heap Overflow: Introduzione

## Cos'è un Heap Overflow?

Un **heap overflow** è una vulnerabilità che si verifica quando un programma scrive più dati di quelli previsti in un'area di memoria allocata dinamicamente, nota come **heap**. L'heap è una porzione di memoria utilizzata per l'allocazione dinamica, ovvero blocchi di memoria che vengono richiesti e liberati durante l'esecuzione del programma, a differenza dello stack che è gestito automaticamente dal sistema.

Quando si verifica un heap overflow, si possono corrompere strutture di dati critiche o sovrascrivere puntatori nell'heap, il che può portare all'esecuzione di codice arbitrario o all'interruzione del normale funzionamento del programma.

## Differenza tra Buffer Overflow e Heap Overflow

- **Buffer Overflow**: Di solito avviene nello stack e consente di sovrascrivere dati critici, come l'indirizzo di ritorno, per prendere il controllo del flusso di esecuzione.
- **Heap Overflow**: Avviene nell'heap e può essere utilizzato per corrompere le strutture di gestione della memoria o altre aree allocate dinamicamente.

## Come Funziona l'Allocazione dell'Heap

L'heap viene utilizzato dal programma per allocare memoria a runtime tramite funzioni come `malloc()` e `free()`. I principali concetti legati all'allocazione dell'heap includono:

- **Chunk**: Un blocco di memoria allocato nell'heap. Ogni chunk contiene informazioni come la dimensione del blocco e puntatori al chunk successivo o precedente.
- **Heap Memory Management**: Il sistema operativo (attraverso l'implementazione della libreria C) si occupa di gestire l'allocazione e deallocazione dell'heap. Ogni volta che viene richiesta memoria dinamica, questa viene prelevata dall'heap.

### Struttura del Chunk

Un chunk nell'heap è diviso in due parti principali:

1. **Header**: Contiene metadati come la dimensione del chunk e lo stato (allocato o libero).
2. **Payload**: La memoria effettiva utilizzata dal programma.

Ecco un esempio semplificato della struttura di un chunk:

```
+-------------------+
| Header (metadati) |
+-------------------+
|   Payload (dati)  |
+-------------------+
```

## Concetti Fondamentali di Heap Overflow

1. **Corruzione dell'Header del Chunk**: Gli overflow nell'heap possono corrompere l'header del chunk successivo, modificando i metadati, e consentendo al programma di comportarsi in modo inaspettato.
2. **Attacchi con Heap Overflow**: Gli attacchi più comuni con heap overflow coinvolgono lo sfruttamento di vulnerabilità come l'overwriting dei puntatori in un chunk libero per redirigere l'esecuzione.

Nel prossimo capitolo approfondiremo come sfruttare queste vulnerabilità e vedremo esempi pratici di heap overflow.


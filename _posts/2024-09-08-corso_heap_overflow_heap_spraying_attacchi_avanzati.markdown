---
layout: post
title:  "Corso Heap Overflow: Heap Spraying e Attacchi Avanzati"
date:   2024-09-08 17:00:00 +0200
categories: heap-overflow
tags: [heap-overflow, heap-spraying, attacchi-avanzati, exploit]
---

# Corso Heap Overflow: Heap Spraying e Attacchi Avanzati

Nelle lezioni precedenti, abbiamo esaminato come sfruttare vulnerabilità di heap overflow e tecniche di debugging. Ora approfondiremo un'altra tecnica fondamentale per aggirare protezioni come ASLR e DEP: **Heap Spraying**, oltre a esplorare alcuni attacchi avanzati che si possono eseguire sfruttando le vulnerabilità dell'heap.

## 1. Cos'è l'Heap Spraying?

L'**Heap Spraying** è una tecnica che prevede l'iniezione di grandi quantità di dati nell'heap per forzare la loro allocazione in posizioni prevedibili. L'obiettivo dell'heap spraying è di creare una zona dell'heap contenente codice controllato dall'attaccante, sperando che un exploit, come un heap overflow o una vulnerabilità use-after-free, possa redirigere il flusso di esecuzione verso una parte dell'heap che contiene codice malevolo.

### 1.1 Come Funziona l'Heap Spraying?

Durante un heap spray, si allocano ripetutamente grandi blocchi di dati controllati dall'attaccante nell'heap. Poiché l'allocazione di memoria dinamica è generalmente deterministica (con alcune variazioni introdotte da ASLR), riempire l'heap con dati noti aumenta la probabilità che parte di questi dati venga posizionata in un'area che può essere utilizzata per sfruttare una vulnerabilità.

#### Esempio di Heap Spraying in JavaScript

In un ambiente browser, ad esempio, l'heap spraying può essere eseguito utilizzando JavaScript per allocare grandi blocchi di stringhe contenenti shellcode:

```javascript
var heapSpray = unescape("%u9090%u9090...%uexploitcode");
var heapBlock = new Array();

for (var i = 0; i < 1000; i++) {
    heapBlock[i] = heapSpray + unescape("%u9090");
}
```

In questo caso, una vulnerabilità di heap overflow nel browser potrebbe essere utilizzata per indirizzare l'esecuzione verso il codice iniettato dall'attaccante nell'heap.

## 2. Attacchi Avanzati basati su Heap Overflow

### 2.1 House of Force

L'**House of Force** è una tecnica avanzata per manipolare l'allocazione dell'heap su Linux sfruttando vulnerabilità di heap overflow. L'obiettivo di House of Force è sovrascrivere il top chunk dell'heap (il chunk che viene utilizzato per le allocazioni future) in modo da forzare l'allocazione in una zona di memoria controllata dall'attaccante.

#### Passaggi per un Attacco House of Force:

1. **Overflow del Top Chunk**: Usare un heap overflow per sovrascrivere il campo size del top chunk.
2. **Manipolazione del Puntatore**: Quando il programma richiede una nuova allocazione, la dimensione del top chunk controllata dall'attaccante consente di allocare memoria in qualsiasi posizione desiderata.
3. **Sovrascrittura di Puntatori Sensibili**: Utilizzare l'allocazione controllata per sovrascrivere puntatori o variabili critiche nel programma, portando all'esecuzione di codice arbitrario.

### 2.2 House of Spirit

L'**House of Spirit** è un'altra tecnica avanzata che sfrutta vulnerabilità di heap overflow. In questo caso, l'attacco si concentra sull'inserimento di chunk falsi (detti **chunk spirit**) nell'heap. L'obiettivo è far sì che il gestore dell'heap tratti i chunk falsi come chunk validi e consenta l'esecuzione di codice malevolo.

#### Passaggi per un Attacco House of Spirit:

1. **Creazione di un Chunk Falso**: Creare manualmente un chunk nell'heap, definendone i campi come `size` e `flags`.
2. **Allocazione del Chunk**: Quando il programma richiede un'allocazione, manipolare il puntatore per far sì che il chunk falso venga utilizzato come parte dell'heap gestito.
3. **Esecuzione dell'Exploit**: Manipolare i metadati dell'heap per redirigere il flusso di esecuzione verso il chunk falso.

### 2.3 House of Lore

L'**House of Lore** sfrutta vulnerabilità nelle allocazioni **small bin** nell'heap. Gli attacchi si concentrano su chunk di piccole dimensioni che vengono gestiti in modo diverso rispetto a chunk più grandi. L'obiettivo è manipolare il processo di allocazione di chunk **small bin** per ottenere il controllo su aree di memoria sensibili.

### 2.4 Poison Null Byte

L'**attacco Poison Null Byte** consiste nel corrompere l'header di un chunk libero utilizzando un byte nullo (`0x00`). Questa corruzione può essere utilizzata per aggirare i controlli di sicurezza del gestore dell'heap e manipolare l'allocazione della memoria a favore dell'attaccante.

#### Passaggi:

1. **Overflow del Chunk**: Utilizzare un overflow per scrivere un byte nullo alla fine di un chunk.
2. **Corruzione del Puntatore**: Il byte nullo causa una corruzione del puntatore o del campo size del chunk successivo.
3. **Sfruttamento della Corruzione**: La corruzione consente di manipolare i metadati dell'heap e ottenere l'esecuzione di codice malevolo o l'accesso a dati sensibili.

## 3. Tecniche Avanzate di Heap Manipulation

### 3.1 Heap Feng Shui

**Heap Feng Shui** è una tecnica utilizzata per controllare in modo preciso l'allocazione dell'heap in un contesto di heap spraying. L'obiettivo è "modellare" l'heap per ottenere una distribuzione prevedibile delle allocazioni, massimizzando le probabilità di successo di un exploit.

### 3.2 Exploit Multi-Stage

Un exploit multi-stage prevede l'esecuzione di più fasi per sfruttare una vulnerabilità. Ad esempio, il primo stadio può essere un heap overflow che consente di bypassare una protezione, mentre il secondo stadio sfrutta un'altra vulnerabilità per ottenere l'esecuzione di codice.

## 4. Esercitazione Pratica: Heap Spraying e House of Force

### Obiettivo

In questa esercitazione, useremo **heap spraying** per riempire l'heap con codice controllato dall'attaccante e utilizzeremo la tecnica **House of Force** per manipolare l'allocazione della memoria.

### Passaggi

1. **Heap Spraying**: Scrivere un semplice programma che esegua un heap spraying su un'applicazione vulnerabile.
2. **Manipolazione del Top Chunk**: Utilizzare una vulnerabilità di heap overflow per corrompere il top chunk dell'heap.
3. **Allocazione Controllata**: Forzare il programma ad allocare memoria in una zona controllata dall'attaccante.
4. **Esecuzione dell'Exploit**: Eseguire codice arbitrario sovrascrivendo puntatori critici.

## Conclusione

L'heap spraying è una tecnica potente per sfruttare vulnerabilità di heap overflow e aggirare protezioni come ASLR. Inoltre, le tecniche avanzate come House of Force e House of Spirit offrono ulteriori possibilità di manipolare l'heap e controllare il flusso di esecuzione. Nella prossima lezione, esploreremo esercitazioni pratiche finali e simulazioni reali per consolidare le competenze apprese.

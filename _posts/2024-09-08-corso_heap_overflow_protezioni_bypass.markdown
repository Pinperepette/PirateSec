---
layout: post
title:  "Corso Heap Overflow: Protezioni Moderne e Tecniche di Bypass"
date:   2024-09-08 15:00:00 +0200
categories: heap-overflow
tags: [heap-overflow, protezioni, bypass, exploit]
---

# Corso Heap Overflow: Protezioni Moderne e Tecniche di Bypass

Nelle lezioni precedenti, abbiamo discusso delle vulnerabilità di heap overflow e delle tecniche di exploit utilizzate per sfruttarle. Tuttavia, i moderni sistemi operativi implementano diverse protezioni di sicurezza che rendono più difficile sfruttare queste vulnerabilità. In questa lezione, esploreremo le protezioni più comuni e le tecniche avanzate utilizzate per bypassarle.

## 1. Protezioni Moderne dell'Heap

I sistemi operativi moderni, come Linux, macOS e Windows, hanno introdotto una serie di mitigazioni per prevenire o ridurre l'efficacia degli attacchi basati su heap overflow. Ecco le principali protezioni:

### 1.1 ASLR (Address Space Layout Randomization)

**ASLR** randomizza gli indirizzi di memoria delle varie sezioni del processo, inclusi lo stack, l'heap e le librerie condivise, ogni volta che il programma viene eseguito. Questo rende difficile per un attaccante prevedere la posizione esatta dell'heap o del codice iniettato, riducendo la possibilità di sfruttare una vulnerabilità.

### 1.2 DEP (Data Execution Prevention)

**DEP** è una protezione che impedisce l'esecuzione di codice in sezioni di memoria destinate solo ai dati, come l'heap. Questo significa che, anche se un attaccante riesce a iniettare codice malevolo nell'heap, non potrà eseguirlo direttamente. DEP è implementato sia su hardware che su software ed è una delle principali difese contro gli attacchi di buffer overflow e heap overflow.

### 1.3 Stack Canaries

Anche se i **canarini di stack** sono più rilevanti per gli attacchi di stack overflow, possono essere utilizzati in combinazione con altre protezioni per monitorare e proteggere lo stack da attacchi indiretti.

### 1.4 Heap Integrity Checks

I gestori dell'heap, come ptmalloc su Linux, implementano **integrity checks** per rilevare la corruzione delle strutture di gestione della memoria. Ad esempio, ptmalloc verifica che i puntatori **forward** e **backward** dei chunk liberi siano coerenti prima di manipolare le liste di chunk. Questo riduce l'efficacia di attacchi come l'**unlink attack**.

### 1.5 Guard Pages

**Guard Pages** sono pagine di memoria non accessibili che vengono inserite tra le allocazioni di memoria per impedire overflow o underflow. Se un attaccante tenta di leggere o scrivere nella guard page, il sistema operativo genererà un'eccezione, prevenendo così l'attacco.

## 2. Tecniche di Bypass delle Protezioni

Sebbene le protezioni moderne abbiano reso più difficile l'exploit delle vulnerabilità, esistono diverse tecniche avanzate che consentono di bypassarle. Esploreremo alcune di queste tecniche.

### 2.1 Return-Oriented Programming (ROP)

**ROP** è una delle tecniche più efficaci per bypassare protezioni come DEP. Invece di iniettare codice direttamente nell'heap o nello stack, ROP sfrutta frammenti di codice esistente (chiamati **gadget**), che terminano con un'istruzione di ritorno (`ret`). Questi gadget possono essere concatenati per eseguire istruzioni arbitrarie, utilizzando il codice già presente nel programma o nelle librerie caricate.

#### Passaggi chiave per ROP:

1. **Individuare i gadget**: Usare strumenti come **ROPgadget** o **rp++** per identificare i gadget disponibili nelle sezioni di memoria eseguibili.
2. **Costruire una catena ROP**: Creare una sequenza di gadget che permetta di eseguire una funzione o di alterare lo stato della memoria.
3. **Redirigere il flusso di esecuzione**: Utilizzare una vulnerabilità come un heap overflow per sovrascrivere l'indirizzo di ritorno e far sì che punti alla catena ROP.

### 2.2 Heap Spraying

Come discusso nella lezione precedente, lo **heap spraying** è una tecnica utilizzata per aggirare ASLR. Consiste nel riempire grandi porzioni di heap con dati controllati dall'attaccante (ad esempio, codice shell), sperando che almeno una parte del codice venga mappata in una posizione prevedibile. In combinazione con un heap overflow, l'heap spraying può essere utilizzato per eseguire codice arbitrario.

### 2.3 Bypass di Integrity Checks

Alcune tecniche consentono di bypassare i controlli di integrità dell'heap. Ad esempio, è possibile sfruttare vulnerabilità come **double free** o **use-after-free** per corrompere i puntatori dell'heap senza essere rilevati dai controlli di integrità.

- **Double Free**: Si verifica quando lo stesso chunk di memoria viene liberato più di una volta. Ciò può portare a corruzione dell'heap e consente di manipolare i puntatori del chunk già liberato.
- **Use-After-Free**: Accade quando un programma continua a utilizzare un chunk di memoria anche dopo averlo liberato. Se il chunk viene riutilizzato da un altro processo, l'attaccante può sfruttare questa situazione per eseguire codice malevolo.

### 2.4 Partial Overwrite

Un'altra tecnica per bypassare le protezioni di sicurezza è il **partial overwrite**. Questa tecnica consiste nel sovrascrivere solo una parte di un puntatore o di una variabile critica, mantenendo intatti gli altri bit. Poiché molti controlli di sicurezza si basano sulla corrispondenza esatta di puntatori o indirizzi di memoria, un sovrascritto parziale può essere utilizzato per aggirare tali controlli e redirigere l'esecuzione del programma.

### 2.5 Fake Chunk Attacks

Questi attacchi consistono nel creare **chunk falsi** all'interno dell'heap, sfruttando la corruzione dell'header di un chunk legittimo. Manipolando i metadati dell'heap, un attaccante può far sì che il gestore dell'heap tratti il chunk falso come parte della gestione legittima, consentendo così di manipolare la memoria del programma a proprio vantaggio.

## 3. Esercitazione Pratica: Bypass delle Protezioni su Linux

### Obiettivo

In questa esercitazione, proveremo a bypassare le protezioni di ASLR e DEP utilizzando una combinazione di **heap overflow** e **ROP** su un sistema Linux vulnerabile.

### Passaggi

1. **Preparare l'ambiente**: Scarica una macchina virtuale vulnerabile o configura una distribuzione Linux con un'applicazione vulnerabile che utilizza ASLR e DEP.
2. **Esplorazione della vulnerabilità**: Esegui il fuzzing e il debugging dell'applicazione per identificare la vulnerabilità di heap overflow.
3. **Creare una catena ROP**: Usa **ROPgadget** o **rp++** per trovare gadget utili all'interno delle librerie del sistema. Crea una catena ROP che ti consenta di eseguire codice arbitrario.
4. **Heap Spraying**: Implementa uno script di heap spraying per aumentare le probabilità di successo dell'exploit.
5. **Esecuzione dell'exploit**: Combina il heap overflow con la catena ROP per bypassare ASLR e DEP ed eseguire codice arbitrario.

## Conclusione

Le protezioni moderne hanno reso più difficile sfruttare le vulnerabilità di heap overflow, ma tecniche come il ROP, il heap spraying e l'analisi approfondita dell'integrità dell'heap consentono ancora di ottenere exploit funzionanti. Nella prossima lezione, approfondiremo le tecniche di debugging e analisi di exploit su sistemi protetti.


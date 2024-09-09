---
layout: post
title:  "Corso Heap Overflow: Esercitazioni Pratiche e Simulazioni Reali"
date:   2024-09-08 18:00:00 +0200
categories: heap-overflow
tags: [heap-overflow, esercitazioni, simulazioni, exploit]
---

# Corso Heap Overflow: Esercitazioni Pratiche e Simulazioni Reali

In questa ultima lezione del corso su **Heap Overflow**, metteremo in pratica tutte le tecniche e le conoscenze apprese attraverso esercitazioni pratiche e simulazioni di attacchi reali. Questi esercizi ti aiuteranno a consolidare le competenze necessarie per individuare, analizzare e sfruttare vulnerabilità di heap overflow in ambienti reali.

## 1. Preparazione dell'Ambiente di Simulazione

Prima di iniziare, è fondamentale preparare un ambiente di test sicuro per eseguire le simulazioni di exploit. Si consiglia di utilizzare una **macchina virtuale (VM)** o un **container Docker** con una distribuzione Linux o Windows configurata per eseguire applicazioni vulnerabili.

### 1.1 Strumenti necessari

- **GDB** con **Pwndbg** (Linux/macOS)
- **Immunity Debugger** con **Mona.py** (Windows)
- **QEMU** o **VirtualBox** per emulare sistemi vulnerabili
- **Macchine vulnerabili** disponibili su piattaforme come **Hack The Box**, **VulnHub**, o l'uso di applicazioni vulnerabili open-source.

### 1.2 Configurazione del Sistema

Per evitare di compromettere il sistema host, esegui i test su una macchina virtuale con privilegi limitati. Assicurati di disabilitare protezioni come ASLR e DEP per rendere più semplici le prime fasi di analisi e debugging.

```bash
echo 0 | sudo tee /proc/sys/kernel/randomize_va_space  # Disabilita ASLR su Linux
```

## 2. Esercitazioni Pratiche di Exploit

### 2.1 Exploit di Heap Overflow su Linux (House of Force)

**Obiettivo**: Manipolare l'allocazione dell'heap utilizzando la tecnica **House of Force** per forzare l'allocazione in una zona di memoria controllata.

#### Passaggi:

1. **Preparare un'applicazione vulnerabile**: Utilizza un programma scritto in C che presenta una vulnerabilità di heap overflow.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char *buffer1 = malloc(64);
    char *buffer2 = malloc(64);
    strcpy(buffer1, "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"); // Overflow
    free(buffer2);
    return 0;
}
```

2. **Analizzare l'heap con GDB**: Carica il programma in GDB e osserva l'allocazione dell'heap. Imposta breakpoint prima della funzione `free()` per analizzare lo stato della memoria.

```bash
gdb ./heap_overflow_vuln
break free
run
heap chunks
```

3. **Sfruttare il Top Chunk**: Usa l'overflow del `buffer1` per corrompere il top chunk. Osserva come le allocazioni future possono essere manipolate.

4. **Manipolare l'allocazione**: Alloca nuovi chunk utilizzando `malloc()` e forzali a scrivere in zone di memoria controllate.

### 2.2 Exploit di Heap Overflow su Windows (Immunity Debugger)

**Obiettivo**: Eseguire un heap overflow su un programma Windows vulnerabile e analizzare il crash utilizzando Immunity Debugger.

#### Passaggi:

1. **Preparare un programma vulnerabile**: Scrivi un semplice programma C che alloca chunk di memoria e presenta un heap overflow.

2. **Caricare in Immunity Debugger**: Carica il programma in Immunity Debugger, imposta breakpoint nelle funzioni `malloc()` e `free()`, e utilizza **Mona.py** per analizzare lo stato dell'heap.

3. **Analizzare il Crash**: Dopo aver eseguito l'overflow, analizza il crash per vedere se è possibile sovrascrivere puntatori sensibili o l'**instruction pointer** (EIP).

```bash
!mona findmsp
```

4. **Ottimizzare l'Exploit**: Usa il crash come punto di partenza per scrivere un exploit più avanzato, come l'esecuzione di codice arbitrario.

## 3. Simulazione di Exploit Real-World

### 3.1 CVE-2016-0728: Exploit nel Keyring di Linux

**Obiettivo**: Sfruttare una vulnerabilità di heap overflow nel gestore dei keyring di Linux (CVE-2016-0728) per ottenere privilegi elevati.

#### Passaggi:

1. **Preparare il Sistema**: Usa una versione vulnerabile del kernel Linux in una macchina virtuale e configura i permessi in modo che l'attaccante abbia solo accesso limitato.

2. **Eseguire l'Exploit**: Analizza il PoC (proof of concept) pubblico disponibile per CVE-2016-0728 e adattalo per la tua VM.

3. **Esecuzione di Codice Arbitrario**: Utilizza l'exploit per ottenere l'accesso come utente root.

### 3.2 Exploit di Use-After-Free

Gli attacchi **Use-After-Free** sono comuni nelle vulnerabilità legate all'heap. In questa simulazione, analizzeremo una vulnerabilità UAF in un programma C.

#### Passaggi:

1. **Preparare il Programma**: Scrivi un programma che presenta una vulnerabilità UAF:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    char *buffer = malloc(64);
    free(buffer);
    printf("%s
", buffer);  // Use-After-Free
    return 0;
}
```

2. **Eseguire l'Exploit**: Utilizza un exploit UAF per manipolare il contenuto della memoria e far sì che il programma acceda a dati corrotti.

3. **Ottimizzare l'Exploit**: Analizza il crash e ottimizza l'exploit per ottenere l'esecuzione di codice arbitrario.

## 4. Tecniche Avanzate di Debugging e Analisi

Durante le simulazioni, è fondamentale avere familiarità con le tecniche di debugging avanzato. Di seguito, alcune delle tecniche chiave:

- **Analisi del Control Flow**: Monitora l'**instruction pointer** per determinare se l'exploit è riuscito a manipolare il flusso di esecuzione.
- **Monitoraggio della Heap Corruption**: Usa comandi come `heap chunks` in GDB per monitorare lo stato dell'heap e individuare chunk corrotti.
- **Breakpoints Condizionali**: Imposta breakpoint condizionali per interrompere l'esecuzione solo quando determinati criteri sono soddisfatti (ad esempio, quando un chunk viene allocato in una zona specifica).

## Conclusione

Le esercitazioni pratiche e le simulazioni reali ti consentono di mettere alla prova le tue conoscenze in contesti di exploit development. Queste simulazioni sono un'ottima opportunità per consolidare le tue competenze, migliorare le tue capacità di debugging e ottimizzare gli exploit per ambienti reali. Con la pratica costante, potrai affrontare con sicurezza vulnerabilità di heap overflow nel mondo reale.

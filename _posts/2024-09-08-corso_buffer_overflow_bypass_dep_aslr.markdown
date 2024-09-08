---
layout: post
title:  "Corso Buffer Overflow: Bypass di DEP e ASLR"
date:   2024-09-08 15:00:00 +0200
categories: buffer-overflow
tags: [buffer-overflow, exploit, dep, aslr]
---

# Corso Buffer Overflow: Bypass di DEP e ASLR

Nelle fasi precedenti, abbiamo visto come identificare un buffer overflow, analizzarne il crash, e creare un payload per sfruttarlo. Tuttavia, in ambienti più moderni, potresti trovarti di fronte a protezioni come **DEP (Data Execution Prevention)** e **ASLR (Address Space Layout Randomization)**, che rendono più difficile sfruttare le vulnerabilità.

In questa sezione, vedremo come riconoscere queste protezioni e quali tecniche possiamo utilizzare per **bypassare DEP** e **aggirare ASLR**.

## 1. DEP (Data Execution Prevention)

DEP è una tecnologia di protezione che impedisce l'esecuzione di codice in alcune aree di memoria, come lo stack. Questo significa che il nostro payload, iniettato nello stack attraverso un buffer overflow, non sarà eseguito se DEP è attivo.

### Come verificare se DEP è attivo

Puoi verificare se DEP è attivo per un programma specifico utilizzando **Immunity Debugger**. Dopo aver caricato il programma, fai clic su **View** > **SEH Chain**. Se vedi che **DEP** è abilitato, sarà necessario utilizzare una tecnica chiamata **ROP (Return Oriented Programming)** per bypassarlo.

## 2. Bypassare DEP con ROP

**Return Oriented Programming (ROP)** è una tecnica che consente di eseguire codice arbitrario anche con DEP abilitato. Invece di eseguire il codice iniettato direttamente, utilizziamo piccole sequenze di istruzioni già presenti nel programma (chiamate **gadget**), terminate da un `RET`, per costruire una catena di ritorno che esegua il nostro codice.

### Creazione di una ROP chain

Per creare una ROP chain, possiamo utilizzare uno strumento chiamato **ROPgadget**:

1. Scarica e installa **ROPgadget** (è scritto in Python).
2. Utilizza il seguente comando per analizzare il programma vulnerabile e trovare i gadget disponibili:

    ```bash
    ROPgadget --binary <nome_binario> --rop
    ```

3. **ROPgadget** elencherà una serie di gadget che possiamo utilizzare per costruire la nostra chain. Ad esempio, cerchiamo un gadget che ci permetta di impostare i registri necessari per chiamare `VirtualProtect`, una funzione di Windows che possiamo utilizzare per rendere eseguibile una porzione di memoria.

4. Una volta trovati i gadget, li collegheremo per creare la nostra ROP chain, che cambierà i permessi della memoria e poi eseguirà il nostro shellcode.

## 3. ASLR (Address Space Layout Randomization)

**ASLR** è una tecnica che randomizza gli indirizzi di memoria, rendendo difficile prevedere dove si trovano le librerie e le funzioni di sistema. Se ASLR è attivo, gli indirizzi in memoria cambiano ogni volta che il programma viene eseguito.

### Come aggirare ASLR

Per aggirare ASLR, possiamo cercare moduli che non utilizzano ASLR o che sono stati caricati in posizioni fisse (non randomizzate). Ad esempio, molti programmi caricano moduli come **msvcrt.dll** che non sono soggetti ad ASLR.

Utilizzando **Immunity Debugger** con il comando `!mona modules`, possiamo vedere quali moduli sono caricati senza ASLR.

Una volta individuato un modulo non soggetto a ASLR, possiamo sfruttarne gli indirizzi fissi per costruire il nostro exploit.

## 4. Esercizio Pratico

Per questo esercizio:

1. Verifica se DEP o ASLR sono attivi sul programma vulnerabile.
2. Crea una **ROP chain** per bypassare DEP e rendere eseguibile lo stack.
3. Trova un modulo senza ASLR e utilizza i suoi indirizzi per eseguire il tuo shellcode.

## Conclusione

Bypassare protezioni come DEP e ASLR richiede una comprensione più avanzata del funzionamento dei sistemi operativi e degli exploit. Tuttavia, con strumenti come **ROPgadget** e tecniche come il **Return Oriented Programming**, possiamo costruire exploit efficaci anche contro le più moderne protezioni di sicurezza.

Nel prossimo articolo ci concentreremo sull'**automazione di exploit** e su come renderli più affidabili utilizzando librerie come **pwntools**.


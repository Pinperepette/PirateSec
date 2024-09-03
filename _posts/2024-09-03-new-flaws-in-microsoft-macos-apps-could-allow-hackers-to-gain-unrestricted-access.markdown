---
layout: post
title: "Nuovi Difetti nelle App Microsoft per macOS Potrebbero Consentire agli Hacker di Ottenere Accesso Illimitato"
date: 2024-09-03
categories: [security, ransomware]
---

Sono state scoperte otto vulnerabilità nelle applicazioni Microsoft per macOS che un avversario potrebbe sfruttare per ottenere privilegi elevati o accedere a dati sensibili eludendo il modello di autorizzazioni del sistema operativo, che ruota attorno al framework di Trasparenza, Consenso e Controllo (TCC).

"Se l'attacco ha successo, l'avversario potrebbe ottenere qualsiasi privilegio già concesso alle applicazioni Microsoft interessate", ha dichiarato Cisco Talos. "Ad esempio, l'attaccante potrebbe inviare email dall'account dell'utente senza che quest'ultimo se ne accorga, registrare clip audio, scattare foto o registrare video senza alcuna interazione dell'utente."

Le carenze interessano varie applicazioni come Outlook, Teams, Word, Excel, PowerPoint e OneNote. La società di cybersecurity ha affermato che potrebbero essere iniettate librerie maligne in queste applicazioni e ottenere i loro diritti e le autorizzazioni concesse dall'utente, che potrebbero poi essere utilizzate per estrarre informazioni sensibili a seconda dell'accesso concesso a ciascuna di queste app.

TCC è un framework sviluppato da Apple per gestire l'accesso ai dati sensibili degli utenti su macOS, fornendo agli utenti una maggiore trasparenza su come i loro dati vengono accessi e utilizzati dalle diverse applicazioni installate sulla macchina. Ciò viene mantenuto sotto forma di un database crittografato che registra le autorizzazioni concesse dall'utente a ciascuna applicazione per garantire che le preferenze siano costantemente rispettate in tutto il sistema.

"TCC funziona in combinazione con la funzione di sandboxing delle applicazioni in macOS e iOS", sottolinea Huntress nelle sue note esplicative per TCC. "Il sandboxing limita l'accesso di un'app al sistema e ad altre applicazioni, aggiungendo un ulteriore strato di sicurezza. TCC garantisce che le app possano accedere solo ai dati per i quali hanno ricevuto il consenso esplicito dell'utente". Il sandboxing è anche una contromisura che protegge dall'iniezione di codice, che permette agli attaccanti con accesso a una macchina di inserire codice maligno in processi legittimi e accedere a dati protetti.

"L'iniezione di librerie, nota anche come Dylib Hijacking nel contesto di macOS, è una tecnica con la quale il codice viene inserito nel processo di esecuzione di un'applicazione", ha detto il ricercatore di Talos, Francesco Benvenuto. "macOS contrasta questa minaccia con funzionalità come il runtime rafforzato, che riduce la probabilità che un attaccante esegua codice arbitrario attraverso il processo di un'altra app".

Tuttavia, se un attaccante riuscisse a iniettare una libreria nello spazio di processo di un'applicazione in esecuzione, quella libreria potrebbe utilizzare tutte le autorizzazioni già concesse al processo, operando effettivamente per conto dell'applicazione stessa.

È importante notare che gli attacchi di questo tipo richiedono che l'attore minaccioso abbia già un certo livello di accesso all'host compromesso in modo che possa essere abusato per aprire un'app più privilegiata e iniettare una libreria maligna, concedendogli essenzialmente le autorizzazioni associate all'app sfruttata. In altre parole, se un'applicazione di fiducia fosse infiltrata da un attaccante, potrebbe essere sfruttata per abusare delle sue autorizzazioni e ottenere un accesso non autorizzato a informazioni sensibili senza il consenso o la conoscenza degli utenti. Questo tipo di violazione potrebbe verificarsi quando un'applicazione carica librerie da posizioni che l'attaccante potrebbe potenzialmente manipolare e ha disabilitato la convalida delle librerie attraverso un diritto rischioso (cioè, impostato su vero), che altrimenti limita il caricamento delle librerie a quelle firmate dallo sviluppatore dell'applicazione o da Apple.

"macOS si affida alle applicazioni per auto-controllare le loro autorizzazioni", ha osservato Benvenuto. "Un fallimento in questa responsabilità porta a una violazione dell'intero modello di autorizzazione, con le applicazioni che agiscono inavvertitamente come proxy per azioni non autorizzate, eludendo il TCC e compromettendo il modello di sicurezza del sistema". 

Microsoft, per la sua parte, considera i problemi identificati come "a basso rischio" e che le app sono tenute a caricare librerie non firmate per supportare i plugin. Tuttavia, l'azienda è intervenuta per risolvere il problema nelle sue app OneNote e Teams. 

"Le app vulnerabili lasciano la porta aperta agli avversari per sfruttare tutti i diritti delle app e, senza alcuna richiesta dell'utente, riutilizzare tutte le autorizzazioni già concesse all'app, fungendo effettivamente da intermediario delle autorizzazioni per l'attaccante", ha detto Benvenuto. "È importante anche sottolineare che non è chiaro come gestire in modo sicuro tali plugin all'interno del framework attuale di macOS. La notarizzazione dei plugin di terze parti è un'opzione, seppure complessa, e richiederebbe a Microsoft o Apple di firmare i moduli di terze parti dopo averne verificato la sicurezza".

Hai trovato interessante questo articolo? Seguici su Twitter e LinkedIn per leggere altro contenuto esclusivo che pubblichiamo.

![Nuovi Difetti nelle App Microsoft per macOS Potrebbero Consentire agli Hacker di Ottenere Accesso Illimitato](/PirateSec/assets/images/2024-09-03-new-flaws-in-microsoft-macos-apps-could-allow-hackers-to-gain-unrestricted-access.png)

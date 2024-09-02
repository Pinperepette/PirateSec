---
layout: post
title: "Malicious npm Packages Mimicking 'noblox.js' Compromise Roblox Developers’ Systems"
date: 2024-09-02
categories: [security, ransomware]
---

Gli sviluppatori di Roblox sono sotto attacco in una campagna persistente che cerca di compromettere i sistemi attraverso pacchetti npm falsi. Questo evidenzia ancora una volta come gli attori delle minacce continuino a sfruttare la fiducia nell'ecosistema open-source per distribuire malware.

"Gli aggressori, imitando la popolare libreria 'noblox.js', hanno pubblicato decine di pacchetti progettati per rubare dati sensibili e compromettere i sistemi", ha detto Yehuda Gelb, ricercatore di Checkmarx, in un rapporto tecnico.

Le prime informazioni sull'attività sono state documentate da ReversingLabs nell'agosto 2023, nell'ambito di una campagna che ha diffuso uno strumento di furto chiamato Luna Token Grabber. Questo strumento è stato descritto come "un replay di un attacco scoperto due anni prima", nel 2021.

Dall'inizio dell'anno, due altri pacchetti chiamati noblox.js-proxy-server e noblox-ts sono stati identificati come nocivi e hanno impersonato la popolare libreria Node.js per distribuire il malware e un trojan di accesso remoto denominato Quasar RAT.

"Gli aggressori di questa campagna hanno utilizzato tecniche come il brandjacking, il combosquatting e lo starjacking per creare un convincente alone di legittimità per i loro pacchetti maligni", ha detto Gelb.

In questo senso, i pacchetti vengono resi apparentemente legittimi denominandoli noblox.js-async, noblox.js-thread, noblox.js-threads e noblox.js-api, dando l'impressione agli sviluppatori incauti che queste librerie siano correlate al pacchetto legittimo "noblox.js".

Ecco le statistiche dei download dei pacchetti:

noblox.js-async (74 download)
noblox.js-thread (117 download)
noblox.js-threads (64 download)
noblox.js-api (64 download)

Un'altra tecnica utilizzata è lo starjacking, in cui i pacchetti fasulli elencano il repository di origine come quello della vera libreria noblox.js per sembrare più affidabili.

Il codice malevolo inserito nell'ultima iterazione funge da gateway per servire payload aggiuntivi ospitati su un repository di GitHub, mentre ruba contemporaneamente i token di Discord, aggiorna l'elenco delle esclusioni di Microsoft Defender Antivirus per eludere il rilevamento e imposta la persistenza tramite una modifica del Registro di Windows.

"Al centro dell'efficacia del malware c'è il suo approccio alla persistenza, sfruttando l'app Impostazioni di Windows per garantire un accesso continuo", ha sottolineato Gelb. "Di conseguenza, ogni volta che un utente tenta di aprire l'app Impostazioni di Windows, il sistema esegue involontariamente il malware".

L'obiettivo finale della catena di attacco è l'implementazione di Quasar RAT, che concede all'aggressore il controllo remoto del sistema infetto. Le informazioni raccolte vengono esfiltrate al server di comando e controllo (C2) dell'aggressore utilizzando un webhook di Discord.

Questi risultati indicano che continua a fluire un costante flusso di nuovi pacchetti, nonostante gli sforzi per la loro rimozione, rendendo essenziale che gli sviluppatori rimangano vigili di fronte a questa minaccia in corso. 

Hai trovato interessante questo articolo? Seguici su Twitter e LinkedIn per leggere altri contenuti esclusivi che pubblichiamo.

![Malicious npm Packages Mimicking 'noblox.js' Compromise Roblox Developers’ Systems](/PirateSec/assets/images/2024-09-02-malicious-npm-packages-mimicking-noblox-js-compromise-roblox-developers-systems.png)

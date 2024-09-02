---
layout: post
title: "Pacchetti npm malevoli che imitano 'noblox.js' compromettono i sistemi degli sviluppatori di Roblox"
date: 2024-09-02
categories: [security, ransomware]
---

Gli sviluppatori di Roblox sono al centro di una campagna persistente che mira a compromettere i sistemi attraverso pacchetti npm fasulli, evidenziando ancora una volta come gli autori di minacce continuino a sfruttare la fiducia nell'ecosistema open-source per diffondere malware.

"Imitando la popolare libreria 'noblox.js', gli aggressori hanno pubblicato decine di pacchetti progettati per rubare dati sensibili e compromettere i sistemi", ha affermato il ricercatore di Checkmarx, Yehuda Gelb, in un rapporto tecnico. 

I dettagli sull'attività sono stati documentati per la prima volta da ReversingLabs nell'agosto 2023 come parte di una campagna che ha diffuso uno strumento di furto chiamato Luna Token Grabber, descritto come "un ritorno di un attacco scoperto due anni fa" nell'ottobre 2021. 

Dall'inizio dell'anno, altri due pacchetti chiamati noblox.js-proxy-server e noblox-ts sono stati identificati come malevoli e hanno impersonato la popolare libreria Node.js per diffondere malware e un trojan di accesso remoto chiamato Quasar RAT.

"Gli aggressori di questa campagna hanno impiegato tecniche tra cui il brandjacking, il combosquatting e lo starjacking per creare un'illusione convincente di legittimità per i loro pacchetti malevoli", ha dichiarato Gelb. 

A tal fine, i pacchetti sono resi apparentemente legittimi denominandoli noblox.js-async, noblox.js-thread, noblox.js-threads e noblox.js-api, dando l'impressione agli sviluppatori ignari che queste librerie siano correlate al pacchetto legittimo "noblox.js". 

Ecco le statistiche dei download dei pacchetti:

noblox.js-async (74 download)
noblox.js-thread (117 download)
noblox.js-threads (64 download)
noblox.js-api (64 download)

Un'altra tecnica utilizzata è lo starjacking, in cui i pacchetti fasulli elencano il repository di origine come quello della vera libreria noblox.js per farla sembrare più affidabile.

Il codice malevolo incorporato nell'ultima iterazione funge da gateway per fornire ulteriori payload ospitati su un repository GitHub, mentre allo stesso tempo ruba i token Discord, aggiorna l'elenco di esclusioni dell'Antivirus Microsoft Defender per evitare il rilevamento e configura la persistenza attraverso una modifica del Registro di Windows.

"Al centro dell'efficacia del malware c'è il suo approccio alla persistenza, che sfrutta l'app Impostazioni di Windows per garantire l'accesso continuato", ha notato Gelb. "Di conseguenza, ogni volta che un utente tenta di aprire l'app Impostazioni di Windows, il sistema esegue involontariamente il malware."

L'obiettivo finale della catena di attacco è il dispiegamento del Quasar RAT che concede all'attaccante il controllo remoto sul sistema infetto. Le informazioni raccolte vengono esfiltrate al server di comando e controllo (C2) dell'attaccante utilizzando un webhook Discord.

Questi risultati indicano che un flusso costante di nuovi pacchetti continua ad essere pubblicato nonostante gli sforzi di rimozione, rendendo essenziale che gli sviluppatori rimangano vigili contro la minaccia in corso.

Hai trovato interessante questo articolo? Seguici su Twitter e LinkedIn per leggere altri contenuti esclusivi che pubblichiamo.

![Pacchetti npm malevoli che imitano 'noblox.js' compromettono i sistemi degli sviluppatori di Roblox](/PirateSec/assets/images/2024-09-02-malicious-npm-packages-mimicking-noblox-js-compromise-roblox-developers-systems.png)

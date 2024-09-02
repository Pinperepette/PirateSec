---
layout: post
title: "Il gruppo di ransomware RansomHub prende di mira 210 vittime in settori critici"
date: 2024-09-02
categories: [security, ransomware]
---

Gli attori della minaccia legati al gruppo di ransomware RansomHub hanno criptato e sottratto i dati di almeno 210 vittime dal suo inizio nel febbraio 2024, secondo quanto riferito dal governo degli Stati Uniti. Le vittime appartengono a settori diversi, tra cui acqua e servizi idrici, tecnologia dell'informazione, servizi e strutture governative, sanità e salute pubblica, servizi di emergenza, cibo e agricoltura, servizi finanziari, strutture commerciali, produzione critica, trasporti e infrastrutture critiche di comunicazione.

RansomHub è una variante del ransomware come servizio, precedentemente noto come Cyclops e Knight, che si è affermata come un modello di servizio efficiente e di successo, attirando recentemente affiliati di alto profilo da altre varianti prominenti come LockBit e ALPHV, come hanno affermato le agenzie governative.

Una variante di ransomware come servizio (RaaS) discendente da Cyclops e Knight, l'operazione e-criminale ha attirato affiliati di alto profilo da altre varianti importanti come LockBit e ALPHV (noto anche come BlackCat) a seguito di una recente ondata di azioni delle forze dell'ordine.

ZeroFox, in un'analisi pubblicata alla fine dello scorso mese, ha affermato che l'attività di RansomHub come proporzione di tutta l'attività di ransomware osservata dal fornitore di cybersecurity è in crescita, rappresentando circa il 2% di tutti gli attacchi nel primo trimestre del 2024, il 5,1% nel secondo trimestre e il 14,2% finora nel terzo trimestre.

"Circa il 34% degli attacchi di RansomHub ha preso di mira organizzazioni in Europa, rispetto al 25% nel panorama delle minacce", ha notato l'azienda.

Il gruppo è noto per utilizzare il modello di doppia estorsione per sottrarre dati e criptare i sistemi al fine di estorcere le vittime, che sono esortate a contattare gli operatori tramite un unico URL .onion. Le aziende bersaglio che rifiutano di acconsentire alla richiesta di riscatto vedono le loro informazioni pubblicate sul sito di perdita di dati per un periodo compreso tra tre e 90 giorni. L'accesso iniziale agli ambienti delle vittime è facilitato sfruttando vulnerabilità di sicurezza note in dispositivi Apache ActiveMQ (CVE-2023-46604), Atlassian Confluence Data Center e Server (CVE-2023-22515), Citrix ADC (CVE-2023-3519), F5 BIG-IP (CVE-2023-46747), Fortinet FortiOS (CVE-2023-27997) e Fortinet FortiClientEMS (CVE-2023-48788), tra gli altri.

Questo passaggio è seguito da affiliati che conducono attività di ricognizione e scansione della rete utilizzando programmi come AngryIPScanner, Nmap e altri metodi di sopravvivenza sul terreno (LotL). Gli attacchi di RansomHub coinvolgono inoltre la disattivazione del software antivirus utilizzando strumenti personalizzati per volare sotto il radar.

"Dopo l'accesso iniziale, gli affiliati di RansomHub hanno creato account utente per la persistenza, hanno riattivato gli account disabilitati e hanno utilizzato Mimikatz sui sistemi Windows per raccogliere le credenziali [T1003] ed elevare i privilegi a SYSTEM", si legge nell'avviso del governo degli Stati Uniti.

"Gli affiliati si sono poi spostati lateralmente all'interno della rete attraverso metodi che includono il protocollo di desktop remoto (RDP), PsExec, AnyDesk, Connectwise, N-Able, Cobalt Strike, Metasploit, o altri metodi di comando e controllo (C2) comunemente utilizzati". Un altro aspetto degno di nota degli attacchi di RansomHub è l'uso della crittografia intermittente per accelerare il processo, con l'esfiltrazione dei dati osservata attraverso strumenti come PuTTY, secchi Amazon AWS S3, richieste HTTP POST, WinSCP, Rclone, Cobalt Strike, Metasploit e altri metodi.

Questo sviluppo arriva mentre Palo Alto Networks Unit 42 ha esaminato le tattiche associate al ransomware ShinyHunters, che traccia come Bling Libra, evidenziando il suo passaggio all'estorsione delle vittime rispetto alla sua tattica tradizionale di vendita o pubblicazione di dati rubati. L'attore della minaccia è venuto alla luce nel 2020.

"Il gruppo acquisisce credenziali legittime, provenienti da repository pubblici, per ottenere un accesso iniziale all'ambiente di Amazon Web Services (AWS) di un'organizzazione", hanno detto i ricercatori di sicurezza Margaret Zimmermann e Chandni Vaya.

"Sebbene i permessi associati alle credenziali compromesse limitassero l'impatto della violazione, Bling Libra ha infiltrato l'ambiente AWS dell'organizzazione e ha condotto operazioni di ricognizione. Il gruppo di attori della minaccia ha utilizzato strumenti come il browser del servizio di archiviazione semplice Amazon (S3) e WinSCP per raccogliere informazioni sulle configurazioni dei secchi S3, accedere agli oggetti S3 e cancellare i dati."

Ciò segue anche una significativa evoluzione negli attacchi di ransomware, che sono andati oltre la crittografia dei file per impiegare strategie di estorsione complesse e multifaccettate, addirittura ricorrendo a schemi di estorsione tripla e quadrupla, secondo SOCRadar.

"L'estorsione tripla alza la posta in gioco, minacciando ulteriori mezzi di interruzione oltre la crittografia e l'esfiltrazione", ha detto l'azienda.

"Questo potrebbe comportare la conduzione di un attacco DDoS contro i sistemi della vittima o l'estensione di minacce dirette ai clienti, fornitori o altri associati della vittima per infliggere ulteriori danni operativi e reputazionali a coloro che sono infine presi di mira nello schema di estorsione."

L'estorsione quadrupla alza la posta in gioco contattando le terze parti che hanno rapporti commerciali con le vittime e estorcendo loro, o minacciando le vittime di esporre dati di terze parti per aumentare ulteriormente la pressione su una vittima per pagare.

La natura lucrativa dei modelli RaaS ha alimentato un aumento nelle nuove varianti di ransomware come Allarich, Cronus, CyberVolk, Datablack, DeathGrip, Hawk Eye e Insom. Ha anche portato gli attori statali iraniani a collaborare con gruppi noti come NoEscape, RansomHouse e BlackCat in cambio di una parte dei proventi illeciti. 

Se hai trovato interessante questo articolo, seguici su Twitter e LinkedIn per leggere altri contenuti esclusivi che pubblichiamo.

![Il gruppo di ransomware RansomHub prende di mira 210 vittime in settori critici](/PirateSec/assets/images/2024-09-02-ransomhub-ransomware-group-targets-210-victims-across-critical-sectors.png)

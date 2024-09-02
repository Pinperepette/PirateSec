---
layout: post
title: "RansomHub Ransomware Group Targets 210 Victims Across Critical Sectors"
date: 2024-09-02
categories: [security, ransomware]
---

Gli attori delle minacce collegati al gruppo di ransomware RansomHub hanno criptato ed esfiltrato dati da almeno 210 vittime dal suo avvio nel febbraio 2024, come dichiarato dal governo degli Stati Uniti. Le vittime provengono da diversi settori, tra cui acqua e servizi idrici, tecnologia dell'informazione, servizi governativi, strutture sanitarie, emergenze, cibo e agricoltura, servizi finanziari, strutture commerciali, produzione critica, trasporti e infrastrutture critiche delle comunicazioni.

RansomHub è una variante di ransomware-as-a-service, precedentemente conosciuta come Cyclops e Knight, che si è affermata come modello di servizio efficiente e di successo, attirando recentemente affiliati di alto profilo da altre varianti importanti come LockBit e ALPHV, secondo quanto riferito dalle agenzie governative.

Analizzando l'operazione e-criminale, che è un discendente di Cyclops e Knight, si nota che ha attirato affiliati di alto profilo da varianti importanti come LockBit e ALPHV (alias BlackCat) a seguito di una recente ondata di azioni di law enforcement. 

ZeroFox, in un'analisi pubblicata alla fine del mese scorso, ha affermato che l'attività di RansomHub in proporzione a tutta l'attività di ransomware osservata dal venditore di cybersecurity è in crescita, rappresentando circa il 2% di tutti gli attacchi nel primo trimestre del 2024, il 5,1% nel secondo trimestre e il 14,2% finora nel terzo trimestre.

"Il 34% circa degli attacchi di RansomHub ha preso di mira le organizzazioni in Europa, rispetto al 25% nel panorama delle minacce", ha sottolineato l'azienda.

Il gruppo è noto per utilizzare il modello di doppia estorsione per esfiltrare dati e criptare sistemi al fine di estorcere le vittime, che sono esortate a contattare gli operatori tramite un unico URL .onion. Le aziende bersaglio che rifiutano di accettare la richiesta di riscatto vedono le loro informazioni pubblicate sul sito di fuga dei dati per un periodo che varia dai tre ai 90 giorni. L'accesso iniziale agli ambienti delle vittime è facilitato sfruttando vulnerabilità di sicurezza note in dispositivi come Apache ActiveMQ, Atlassian Confluence Data Center e Server, Citrix ADC, F5 BIG-IP, Fortinet FortiOS e Fortinet FortiClientEMS, tra gli altri.

Questo passaggio è seguito da affiliati che conducono attività di ricognizione e scansione della rete utilizzando programmi come AngryIPScanner, Nmap e altri metodi di living-off-the-land (LotL). Gli attacchi di RansomHub comportano inoltre la disattivazione del software antivirus utilizzando strumenti personalizzati per passare inosservati.

"Dopo l'accesso iniziale, gli affiliati di RansomHub hanno creato account utente per la persistenza, riattivato account disabilitati e usato Mimikatz sui sistemi Windows per raccogliere credenziali e aumentare i privilegi a SYSTEM", si legge nel comunicato governativo.

"Gli affiliati si sono poi spostati lateralmente all'interno della rete tramite metodi tra cui il Protocollo Desktop Remoto (RDP), PsExec, AnyDesk, Connectwise, N-Able, Cobalt Strike, Metasploit o altri metodi di command-and-control (C2) ampiamente utilizzati". Un altro aspetto notevole degli attacchi di RansomHub è l'uso della crittografia intermittente per accelerare il processo, con l'esfiltrazione dei dati osservata attraverso strumenti come PuTTY, secchi AWS S3 di Amazon, richieste HTTP POST, WinSCP, Rclone, Cobalt Strike, Metasploit e altri metodi.

Questa evoluzione si verifica mentre la Unit 42 di Palo Alto Networks ha analizzato le tattiche associate al ransomware ShinyHunters, che traccia come Bling Libra, evidenziando il suo passaggio all'estorsione delle vittime rispetto alla sua tattica tradizionale di vendita o pubblicazione di dati rubati. L'attore della minaccia è emerso per la prima volta nel 2020.

"Il gruppo acquisisce credenziali legittime, provenienti da repository pubblici, per ottenere un accesso iniziale all'ambiente Amazon Web Services (AWS) di un'organizzazione", hanno detto i ricercatori di sicurezza Margaret Zimmermann e Chandni Vaya.

"Nonostante le autorizzazioni associate alle credenziali compromesse limitassero l'impatto della violazione, Bling Libra ha infiltrato l'ambiente AWS dell'organizzazione e ha condotto operazioni di ricognizione. Il gruppo di attori della minaccia ha utilizzato strumenti come Amazon Simple Storage Service (S3) Browser e WinSCP per raccogliere informazioni sulle configurazioni dei secchi S3, accedere agli oggetti S3 e cancellare i dati."

Questo avviene in seguito a una significativa evoluzione negli attacchi di ransomware, che sono passati oltre la crittografia dei file per impiegare strategie di estorsione complesse e multifaccettate, arrivando persino a schemi di estorsione tripla e quadrupla, secondo SOCRadar.

"L'estorsione tripla aumenta la posta in gioco, minacciando ulteriori mezzi di interruzione oltre alla crittografia e all'esfiltrazione", ha detto l'azienda.

"Potrebbe comportare la conduzione di un attacco DDoS contro i sistemi della vittima o l'estensione di minacce dirette ai clienti, fornitori o altri associati della vittima per infliggere ulteriori danni operativi e reputazionali a coloro che sono alla fine presi di mira nello schema di estorsione."

L'estorsione quadrupla aumenta la posta in gioco contattando terze parti che hanno relazioni commerciali con le vittime ed estorcendo loro, o minacciando le vittime di esporre dati di terze parti per esercitare ulteriore pressione su una vittima per pagare.

La natura lucrativa dei modelli RaaS ha alimentato un aumento nelle nuove varianti di ransomware come Allarich, Cronus, CyberVolk, Datablack, DeathGrip, Hawk Eye e Insom. Ha anche portato gli attori dello stato-nazione iraniano a collaborare con gruppi noti come NoEscape, RansomHouse e BlackCat in cambio di una percentuale dei proventi illeciti.

![RansomHub Ransomware Group Targets 210 Victims Across Critical Sectors](/assets/images/2024-09-02-ransomhub-ransomware-group-targets-210-victims-across-critical-sectors.png)

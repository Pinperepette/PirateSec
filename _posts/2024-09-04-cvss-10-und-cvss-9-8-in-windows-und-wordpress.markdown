---
layout: post
title: 'CVSS 10 e CVSS 9.8; Analisi delle Vulnerabilità in Windows e WordPress'
date: 2024-09-04
categories: [security, ransomware]
---

Lacune di Sicurezza Critiche: CVSS 10 e CVSS 9.8 in Windows e WordPress

04.09.2024


Durata lettura: 1 minuto

Gli esperti di sicurezza di G Data hanno individuato una pericolosa lacuna di sicurezza con un CVSS 10 in WordPress e una vulnerabilità con un CVSS 9.8 in Windows. Gli amministratori di sistema dovrebbero reagire prontamente ed effettuare l'aggiornamento del software.

Gli specialisti di G Data hanno individuato due criticità importanti sia in Windows che in WordPress. La più preoccupante riguarda il plugin di WordPress "GiveWP", che presenta un valore CVE di 10, il massimo sulla scala di criticità CVE. L'altra, con un valore CVE di 9.8, riguarda il sistema operativo Microsoft Windows e mette a rischio il suo stack di rete IPv6. Entrambe le vulnerabilità permettono agli hacker di ottenere accesso completo al sistema senza alcuna interazione da parte dell'utente e di eseguire codice arbitrario.

Tutte le versioni di Windows sono a rischio

La vulnerabilità in Microsoft Windows riguarda tutte le versioni del sistema operativo a partire da Windows Vista e consente agli aggressori di prendere il controllo totale di un sistema semplicemente inviando un pacchetto di dati IPv6 opportunamente modificato. Questo tipo di attacco non richiede alcuna interazione da parte dell'utente, rendendolo quindi una minaccia particolarmente critica. L'unico modo per difendersi è installare l'aggiornamento di sicurezza fornito da Microsoft, quindi è consigliabile aggiornare Windows all'ultima versione disponibile.

Tuttavia, Microsoft ha rilasciato questo aggiornamento di sicurezza solo per un numero limitato di sistemi operativi. Tra questi troviamo Windows Server 2008 SP2, Server 2008R2, Server 2016 e Server 2022, oltre a alcune versioni di Windows 10 e Windows 11. I sistemi operativi desktop più vecchi come Windows Vista, Windows 7 e Windows 8 restano vulnerabili, poiché non ricevono più aggiornamenti di sicurezza.

WordPress a rischio a causa di un plugin

Oltre al pericolo per i sistemi Windows, il plugin "GiveWP" di WordPress rappresenta una minaccia altrettanto critica. "GiveWP" è utilizzato da numerosi gestori di siti web per raccogliere donazioni per il mantenimento delle loro pagine. La lacuna di sicurezza in questo plugin consente agli aggressori di eseguire codice arbitrario sul server, cancellare o manipolare i dati. L'exploit di questa vulnerabilità potrebbe portare al controllo completo del sito web da parte dell'attaccante. Anche per questa lacuna di sicurezza esiste un aggiornamento, che dovrebbe essere installato urgentemente. (ID:50145800)

!['CVSS 10 e CVSS 9.8; Analisi delle Vulnerabilità in Windows e WordPress'](/PirateSec/assets/images/2024-09-04-cvss-10-und-cvss-9-8-in-windows-und-wordpress.png)

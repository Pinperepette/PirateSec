---
layout: post
title: '[local] SolarWinds Kiwi Syslog Server 9.6.7.1 - Unquoted Service Path' 
date: 2024-08-04
categories: [security, ransomware]
---

# [local] SolarWinds Kiwi Syslog Server 9.6.7.1 - Unquoted Service Path

## Introduzione
SolarWinds Kiwi Syslog Server 9.6.7.1 è affetto da una vulnerabilità conosciuta come "Unquoted Service Path". Questo tipo di vulnerabilità si verifica quando il percorso di un servizio contiene spazi e non è racchiuso tra virgolette. Può essere sfruttata per eseguire codice arbitrario con privilegi elevati.

## Dettagli della Vulnerabilità
La vulnerabilità si manifesta quando un attaccante riesce a inserire un file eseguibile in una delle cartelle che compongono il percorso del servizio non quotato. Quando il servizio viene avviato, il sistema operativo cercherà di eseguire prima il file dell'attaccante. La versione 9.6.7.1 di SolarWinds Kiwi Syslog Server è affetta da questa vulnerabilità.

## Esempio di Payload Semplice

Il comando originale è il seguente:

```bash
sc qc KiwiSyslogServer
```

## Conversione in Python del Payload Semplice

Possiamo raggiungere lo stesso risultato utilizzando il modulo `subprocess` in Python:

```python
import subprocess

subprocess.run(["sc", "qc", "KiwiSyslogServer"])
```

## Spiegazione Tecnica
Il comando originale `sc qc KiwiSyslogServer` interroga il servizio KiwiSyslogServer per ottenere le informazioni di configurazione. Il comando equivalente in Python utilizza il modulo `subprocess` per eseguire il comando come un nuovo processo.

## Procedura per Riprodurre la Vulnerabilità
Per riprodurre la vulnerabilità, esegui il comando di base o lo script Python. Se il percorso del servizio stampato non è racchiuso tra virgolette e contiene spazi, allora il sistema è vulnerabile.

## Impatto della Vulnerabilità
Un attaccante che sfrutta con successo questa vulnerabilità può eseguire codice arbitrario con privilegi elevati, compromettendo così l'integrità del sistema.

## Patch e Mitigazioni
Non sono state rilasciate patch per questa vulnerabilità. Tuttavia, è possibile mitigare manualmente la vulnerabilità racchiudendo il percorso del servizio tra virgolette.

## Conclusione
L'importanza di correggere questa vulnerabilità non può essere sottolineata a sufficienza. Essa permette un attacco molto semplice che può portare al compromesso completo del sistema. Ricordiamo di controllare sempre i percorsi dei servizi e di racchiuderli tra virgolette per evitare questo tipo di vulnerabilità.


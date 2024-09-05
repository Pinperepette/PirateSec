---
layout: post
title: '[local] Genexus Protection Server 9.7.2.10 - protsrvservice Unquoted Service Path' 
date: 2024-08-04
categories: [security, ransomware]
---

# [Local] Genexus Protection Server 9.7.2.10 - 'protsrvservice' Unquoted Service Path

## Introduzione

In questo articolo viene discussa una vulnerabilità identificata nel Genexus Protection Server versione 9.7.2.10. In particolare, il problema riguarda un percorso di servizio non quotato ('protsrvservice'), che se sfruttato da un attaccante, potrebbe portare ad un aumento dei privilegi sul sistema.

## Dettagli della Vulnerabilità

La vulnerabilità risiede nel fatto che il percorso di installazione del servizio 'protsrvservice' non è racchiuso tra virgolette. Questo può portare a un attacco di tipo 'Unquoted Service Path' in cui l'attaccante può inserire un file eseguibile con lo stesso nome di una delle directory presenti nel percorso del servizio. Se il servizio viene poi avviato con privilegi elevati, l'eseguibile dell'attaccante verrà eseguito, permettendogli di elevare i suoi privilegi sul sistema.

## Esempio di Payload Semplice
Il seguente comando può essere utilizzato per identificare la vulnerabilità sul sistema:
```bash
wmic service get name,displayname,pathname,startmode |findstr /i "auto" |findstr /i /v "c:\windows\\" |findstr /i /v """
```

## Conversione in Python del Payload Semplice
Il seguente script Python può essere utilizzato per identificare la vulnerabilità sul sistema:
```python
import os
os.system('wmic service get name,displayname,pathname,startmode |findstr /i "auto" |findstr /i /v "c:\windows\\" |findstr /i /v """')
```

## Spiegazione Tecnica
Sia il comando bash che lo script Python utilizzano il comando `wmic` per ottenere le informazioni su tutti i servizi installati sul sistema. Questo include il nome del servizio, il nome visualizzato, il percorso del servizio e il modo di avvio. Queste informazioni vengono poi filtrate per mostrare solo i servizi che sono impostati per avviarsi automaticamente e che non sono nel percorso di Windows. Infine, viene applicato un ulteriore filtro per mostrare solo i servizi che non hanno il percorso racchiuso tra virgolette.

## Procedura per riprodurre la vulnerabilità
La vulnerabilità può essere riprodotta seguendo questi passaggi:

1. Avviare il Genexus Protection Server versione 9.7.2.10.
2. Eseguire il comando bash o lo script Python fornito nella sezione 'Esempio di Payload Semplice' su un client che ha accesso al server.
3. Se il comando o lo script restituisce il servizio 'protsrvservice', significa che il percorso del servizio non è quotato e la vulnerabilità esiste sul sistema.

## Impatto della Vulnerabilità
Se questa vulnerabilità viene sfruttata, un attaccante può elevare i suoi privilegi sul sistema ed eseguire qualsiasi operazione desidera. Questo può portare a una varietà di problematiche, compresi il furto di dati, l'alterazione di dati e la disponibilità del sistema.

## Patch e Mitigazioni
Al momento della scrittura, non sono disponibili patch per questa vulnerabilità. Tuttavia, una possibile mitigazione è quella di aggiungere manualmente le virgolette al percorso del servizio 'protsrvservice' nelle proprietà del servizio.

## Conclusione
Questa vulnerabilità sottolinea l'importanza di seguire le migliori pratiche durante l'installazione dei servizi, incluso l'inserimento di virgolette nei percorsi dei servizi. Anche se questa vulnerabilità può sembrare minore, le sue potenziali conseguenze sono significative e dovrebbero essere affrontate con la massima serietà. Non appena sarà disponibile una patch, si consiglia di applicarla immediatamente.


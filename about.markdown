---
layout: page
title: About
permalink: /about/
---

# PirateSec - Blog Automation Project

## Overview

PirateSec è un blog automatizzato dedicato alla sicurezza informatica, con un focus particolare su ransomware e minacce digitali. Questo progetto sfrutta un'infrastruttura completamente automatizzata per generare e pubblicare contenuti, basandosi su feed RSS e tecnologie di intelligenza artificiale per la generazione di articoli.

## Tecnologie Utilizzate

### 1. **Python**
   - **Scraping & Parsing**: Utilizzo delle librerie `requests` e `BeautifulSoup` per estrarre contenuti dai feed RSS di The Hacker News e exploit-db.
   - **Automazione della Pubblicazione**: Script Python automatizzati gestiscono l'intero processo di scraping, traduzione e pubblicazione dei contenuti.

### 2. **OpenAI GPT-4**
   - **Generazione di Contenuti**: OpenAI GPT-4 viene utilizzato per tradurre e riscrivere gli articoli in italiano, mantenendo alta la qualità dei contenuti e arricchendo gli articoli con spiegazioni tecniche dettagliate.

### 3. **Git & GitHub**
   - **Version Control**: Git viene utilizzato per tracciare le modifiche al codice e al contenuto del blog.
   - **GitHub Pages**: Il blog è ospitato su GitHub Pages, che offre un hosting affidabile e scalabile per il sito statico.
   - **Deploy Automatizzato**: Ogni nuova pubblicazione viene automaticamente pushata su GitHub, aggiornando il sito senza intervento manuale.

### 4. **Jekyll**
   - **Generazione del Sito Statico**: Jekyll è il generatore di siti statici utilizzato per creare e gestire il blog. Con un design responsive e temi personalizzabili, Jekyll rende la gestione del blog semplice e efficiente.
   - **Temi Responsive**: Il blog utilizza un tema responsive per garantire un'ottima esperienza utente su qualsiasi dispositivo.

### 5. **Bash & Automazione Script**
   - **Automazione del Processo**: Gli script Bash vengono utilizzati per coordinare l'esecuzione degli script Python e il deployment su GitHub.

## Funzionalità del Progetto

- **Automazione Completa**: Una pipeline completamente automatizzata che gestisce il ciclo di vita degli articoli, dalla raccolta delle informazioni alla pubblicazione sul blog.
- **Contenuti Dinamici**: Gli articoli sono generati automaticamente in base agli ultimi feed RSS di fonti attendibili, assicurando che il blog sia sempre aggiornato con le ultime notizie e analisi.
- **Qualità del Contenuto**: Utilizzo di GPT-4 per riscrivere e migliorare gli articoli, garantendo un linguaggio fluido e tecnicamente accurato.

## Come Funziona

1. **Scraping del Feed RSS**: Gli script Python analizzano i feed RSS di The Hacker News per ottenere gli ultimi articoli.
2. **Generazione di Contenuti**: Ogni articolo viene tradotto e riscritto in italiano usando OpenAI GPT-4, mantenendo un alto livello di qualità.
3. **Pubblicazione Automatica**: Gli articoli generati vengono salvati in formato Markdown e pushati automaticamente su GitHub, dove Jekyll si occupa della pubblicazione su GitHub Pages.
4. **Deploy Continui**: Ogni nuova generazione di articoli viene automaticamente gestita e pubblicata, mantenendo il blog sempre aggiornato senza intervento manuale.

## Contattaci

Se hai domande o desideri maggiori informazioni su PirateSec e sulle tecnologie che utilizziamo, non esitare a contattarci.

---

Tutti i diritti riservati © 2024 PirateSec. Powered by Python, Jekyll, GitHub Pages, e OpenAI.

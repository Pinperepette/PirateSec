---
layout: post
title:  "Automatizzazione con script Python"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, automatizzazione, scripting]
---

# Automatizzazione con script Python

Uno degli usi più potenti di Python è la possibilità di **automatizzare** compiti ripetitivi, semplificando operazioni che altrimenti richiederebbero tempo e sforzo. In questo articolo vedremo come utilizzare Python per automatizzare attività comuni, come la gestione di file, l'invio di email, e l'interazione con API e servizi web.

## Gestione dei file

Python fornisce diversi strumenti per lavorare con file e directory, permettendoti di automatizzare attività come la creazione, la copia, lo spostamento e l'eliminazione di file.

### Creare, leggere e scrivere file

Ecco un esempio di come creare un file, scrivere del contenuto al suo interno e poi leggerlo:

Esempio:
```python
# Creare e scrivere su un file
with open("esempio.txt", "w") as file:
    file.write("Questo è un esempio di automatizzazione.
")

# Leggere il contenuto del file
with open("esempio.txt", "r") as file:
    contenuto = file.read()
    print(contenuto)
```

### Spostare e copiare file

Per spostare o copiare file, possiamo usare il modulo `shutil`, che offre diverse funzioni per manipolare i file e le directory.

Esempio:
```python
import shutil

# Copiare un file
shutil.copy("esempio.txt", "esempio_copia.txt")

# Spostare un file
shutil.move("esempio_copia.txt", "nuova_cartella/esempio_copia.txt")
```

### Automatizzare la gestione delle directory

Puoi creare script Python per eseguire operazioni automatiche su file e directory, come rinominare file in batch o organizzare documenti.

Esempio:
```python
import os

# Creare una nuova directory
os.mkdir("nuova_cartella")

# Rinominare un file
os.rename("esempio.txt", "esempio_rinominato.txt")
```

## Inviare email

Python può essere utilizzato per automatizzare l'invio di email, ad esempio per notifiche automatiche o report. Il modulo `smtplib` ti consente di connetterti a un server SMTP e inviare email.

Esempio:
```python
import smtplib
from email.mime.text import MIMEText

# Impostazioni del server email
smtp_server = "smtp.gmail.com"
smtp_port = 587
utente = "il_tuo_indirizzo@gmail.com"
password = "la_tua_password"

# Creare il messaggio
msg = MIMEText("Questo è un messaggio inviato automaticamente.")
msg["Subject"] = "Email automatica"
msg["From"] = utente
msg["To"] = "destinatario@example.com"

# Inviare l'email
with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.starttls()  # Avvia la crittografia
    server.login(utente, password)
    server.sendmail(utente, ["destinatario@example.com"], msg.as_string())
```

### Automatizzare l'invio di email con allegati

Ecco un esempio di come inviare un'email con un file allegato:

```python
from email.mime.multipart import MIMEMultipart
from email.mime.base import MIMEBase
from email import encoders

# Creare il messaggio multipart
msg = MIMEMultipart()
msg["From"] = utente
msg["To"] = "destinatario@example.com"
msg["Subject"] = "Email con allegato"

# Allegare il file
allegato = MIMEBase("application", "octet-stream")
with open("esempio.txt", "rb") as file:
    allegato.set_payload(file.read())
encoders.encode_base64(allegato)
allegato.add_header("Content-Disposition", "attachment", filename="esempio.txt")
msg.attach(allegato)

# Inviare l'email con allegato
with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.starttls()
    server.login(utente, password)
    server.sendmail(utente, ["destinatario@example.com"], msg.as_string())
```

## Automatizzare task di sistema

Python può essere utilizzato per eseguire comandi di sistema e script automatici, come la gestione di processi o l'automazione di operazioni a livello di sistema operativo.

### Eseguire comandi di sistema

Il modulo `subprocess` permette di eseguire comandi di sistema direttamente da uno script Python.

Esempio:
```python
import subprocess

# Eseguire un comando di sistema
subprocess.run(["ls", "-l"])
```

### Pianificare script

Per automatizzare l'esecuzione di uno script Python a intervalli regolari, puoi utilizzare strumenti come **cron** su Linux o **Task Scheduler** su Windows.

Esempio di cron su Linux:
```bash
# Esegui lo script ogni giorno alle 8:00
0 8 * * * /usr/bin/python3 /path/to/script.py
```

## Automazione con Selenium

Se devi interagire con applicazioni web in modo automatico, puoi usare **Selenium**, una libreria che permette di controllare un browser per automatizzare task come il login a un sito o la compilazione di moduli.

Esempio di login automatico con Selenium:
```python
from selenium import webdriver

# Impostare il driver del browser (ad esempio, Chrome)
driver = webdriver.Chrome()

# Aprire una pagina web
driver.get("https://www.example.com/login")

# Trovare gli elementi della pagina e interagire con essi
username = driver.find_element("name", "username")
password = driver.find_element("name", "password")

username.send_keys("il_tuo_username")
password.send_keys("la_tua_password")

# Inviare il modulo di login
password.submit()

# Chiudere il browser
driver.quit()
```

## Conclusione

Python è uno strumento estremamente potente per automatizzare operazioni ripetitive, risparmiando tempo e sforzo. Con le giuste librerie, puoi automatizzare quasi qualsiasi attività, dalla gestione dei file all'invio di email e all'interazione con API web. Nel prossimo articolo, esploreremo come creare **interfacce grafiche** in Python utilizzando Tkinter.

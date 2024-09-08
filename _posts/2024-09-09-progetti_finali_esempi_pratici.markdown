---
layout: post
title:  "Progetti finali: Esempi pratici e applicazioni complete"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, progetti, applicazioni, esempi-pratici]
---

# Progetti finali: Esempi pratici e applicazioni complete

Ora che abbiamo esplorato diversi concetti e strumenti in Python, è il momento di mettere in pratica ciò che abbiamo imparato attraverso alcuni **progetti finali**. Questi progetti combinano vari aspetti della programmazione Python, dall'automazione alla creazione di interfacce grafiche, e ti aiuteranno a consolidare le tue competenze.

## 1. Gestore di file automatico

### Obiettivo

Creare uno script Python che organizza automaticamente i file in una directory, spostandoli in sottocartelle in base al tipo di file (ad esempio, immagini, documenti, video, ecc.).

### Strumenti utilizzati
- `os` e `shutil` per la gestione dei file.
- Automazione dello spostamento e della rinominazione dei file.

### Esempio di codice:
```python
import os
import shutil

# Directory da organizzare
directory = "/path/to/your/directory"

# Estensioni per tipo di file
tipi_file = {
    "Immagini": [".jpg", ".jpeg", ".png", ".gif"],
    "Documenti": [".pdf", ".docx", ".txt"],
    "Video": [".mp4", ".mov", ".avi"],
}

# Creare sottocartelle se non esistono
for cartella in tipi_file.keys():
    cartella_path = os.path.join(directory, cartella)
    if not os.path.exists(cartella_path):
        os.mkdir(cartella_path)

# Spostare i file nelle cartelle appropriate
for filename in os.listdir(directory):
    file_path = os.path.join(directory, filename)
    if os.path.isfile(file_path):
        estensione = os.path.splitext(filename)[1].lower()
        for cartella, estensioni in tipi_file.items():
            if estensione in estensioni:
                shutil.move(file_path, os.path.join(directory, cartella, filename))
                break
```

## 2. Applicazione per to-do list con Tkinter

### Obiettivo

Creare una **to-do list** con interfaccia grafica che permetta agli utenti di aggiungere, visualizzare e cancellare compiti.

### Strumenti utilizzati
- **Tkinter** per la creazione dell'interfaccia grafica.
- Operazioni di base sui file per salvare i compiti.

### Esempio di codice:
```python
import tkinter as tk
from tkinter import messagebox

# Funzioni per gestire la lista
def aggiungi_compito():
    compito = input_field.get()
    if compito:
        listbox.insert(tk.END, compito)
        input_field.delete(0, tk.END)
    else:
        messagebox.showwarning("Input necessario", "Devi inserire un compito!")

def rimuovi_compito():
    try:
        indice = listbox.curselection()[0]
        listbox.delete(indice)
    except IndexError:
        messagebox.showwarning("Errore", "Seleziona un compito da rimuovere")

# Creare la finestra principale
root = tk.Tk()
root.title("To-Do List")

# Campo di input
input_field = tk.Entry(root, width=35)
input_field.pack(pady=10)

# Pulsante per aggiungere compito
add_button = tk.Button(root, text="Aggiungi compito", command=aggiungi_compito)
add_button.pack(pady=5)

# Lista di compiti
listbox = tk.Listbox(root, width=45, height=10)
listbox.pack(pady=10)

# Pulsante per rimuovere compito
remove_button = tk.Button(root, text="Rimuovi compito", command=rimuovi_compito)
remove_button.pack(pady=5)

# Avviare il loop principale
root.mainloop()
```

## 3. Applicazione di web scraping

### Obiettivo

Creare uno script Python che estrae informazioni da un sito web e le salva in un file CSV.

### Strumenti utilizzati
- **Requests** per inviare richieste HTTP.
- **BeautifulSoup** per l'analisi del codice HTML.

### Esempio di codice:
```python
import requests
from bs4 import BeautifulSoup
import csv

# URL da cui estrarre i dati
url = "https://quotes.toscrape.com/"

# Inviare una richiesta GET
response = requests.get(url)

# Analizzare il contenuto HTML
soup = BeautifulSoup(response.content, "html.parser")
quotes = soup.find_all("div", class_="quote")

# Creare un file CSV per salvare i dati
with open("quotes.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["Quote", "Author"])

    # Estrarre e scrivere le citazioni nel CSV
    for quote in quotes:
        text = quote.find("span", class_="text").get_text()
        author = quote.find("small", class_="author").get_text()
        writer.writerow([text, author])
```

## 4. Applicazione con API per il meteo

### Obiettivo

Creare un'applicazione Python che utilizza un'API per ottenere e mostrare le informazioni meteo di una città.

### Strumenti utilizzati
- **Requests** per interagire con l'API del meteo.
- **Tkinter** per visualizzare le informazioni meteo.

### Esempio di codice:
```python
import requests
import tkinter as tk

# Funzione per ottenere i dati meteo
def ottieni_meteo():
    città = input_field.get()
    api_key = "la-tua-api-key"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={città}&appid={api_key}&units=metric"

    response = requests.get(url)
    if response.status_code == 200:
        dati = response.json()
        temperatura = dati["main"]["temp"]
        meteo_label.config(text=f"La temperatura a {città} è {temperatura}°C")
    else:
        meteo_label.config(text="Errore: Città non trovata")

# Creare la finestra principale
root = tk.Tk()
root.title("Applicazione Meteo")

# Campo di input per la città
input_field = tk.Entry(root, width=35)
input_field.pack(pady=10)

# Pulsante per ottenere il meteo
meteo_button = tk.Button(root, text="Ottieni meteo", command=ottieni_meteo)
meteo_button.pack(pady=5)

# Etichetta per mostrare il meteo
meteo_label = tk.Label(root, text="")
meteo_label.pack(pady=10)

# Avviare il loop principale
root.mainloop()
```

## Conclusione

Questi progetti ti permettono di mettere in pratica le competenze acquisite durante il corso, combinando diverse tecnologie e concetti in Python. Ognuno di questi esempi rappresenta un'applicazione concreta e utile che puoi espandere e personalizzare ulteriormente. Buon coding!

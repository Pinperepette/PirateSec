---
layout: post
title:  "API e networking: Interazione con le API web"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, API, networking, requests]
---

# API e networking: Interazione con le API web

Le **API web** sono uno strumento fondamentale per consentire la comunicazione tra diverse applicazioni e servizi su Internet. In Python, il modulo **requests** rende semplice l'interazione con le API. In questo articolo vedremo come inviare richieste HTTP, gestire le risposte e lavorare con i dati restituiti da un'API.

## Cos'è un'API?

Un'**API** (Application Programming Interface) è un insieme di regole che permette a un'applicazione di interagire con un'altra. Le API web usano principalmente il protocollo HTTP per inviare e ricevere dati, spesso in formato **JSON**.

### Installare requests

Il modulo `requests` è una libreria molto popolare per inviare richieste HTTP in Python. Puoi installarla utilizzando `pip`:

```bash
pip install requests
```

### Eseguire una richiesta GET

Il tipo più comune di richiesta HTTP è la **GET**, che viene utilizzata per recuperare informazioni da un server.

Esempio:
```python
import requests

url = "https://jsonplaceholder.typicode.com/todos/1"
response = requests.get(url)

# Verificare lo stato della risposta
if response.status_code == 200:
    # Stampare i dati in formato JSON
    print(response.json())
else:
    print("Errore nella richiesta")
```

In questo esempio, inviamo una richiesta GET a un'API di esempio e stampiamo i dati JSON restituiti.

### Eseguire una richiesta POST

Le richieste **POST** vengono utilizzate per inviare dati al server. Solitamente, i dati sono inviati nel corpo della richiesta in formato JSON.

Esempio:
```python
import requests

url = "https://jsonplaceholder.typicode.com/posts"
dati = {
    "title": "Nuovo post",
    "body": "Questo è il contenuto del post.",
    "userId": 1
}

response = requests.post(url, json=dati)

if response.status_code == 201:
    print("Dati inviati con successo")
    print(response.json())
else:
    print("Errore nella richiesta POST")
```

In questo esempio, inviamo un oggetto JSON con una richiesta POST e stampiamo la risposta dal server.

### Gestire parametri di query

Le API spesso richiedono parametri di query per filtrare o modificare i dati restituiti. Questi parametri possono essere passati come un dizionario nella richiesta GET.

Esempio:
```python
url = "https://jsonplaceholder.typicode.com/posts"
parametri = {"userId": 1}

response = requests.get(url, params=parametri)

if response.status_code == 200:
    print(response.json())
else:
    print("Errore nella richiesta GET con parametri")
```

### Aggiungere intestazioni HTTP

Quando invii richieste a un'API, potrebbe essere necessario includere **intestazioni HTTP** per l'autenticazione o altre informazioni.

Esempio:
```python
url = "https://api.esempio.com/data"
headers = {"Authorization": "Bearer il-tuo-token"}

response = requests.get(url, headers=headers)

if response.status_code == 200:
    print(response.json())
else:
    print("Errore nell'invio dell'intestazione HTTP")
```

### Gestire gli errori

È importante gestire gli errori quando si lavora con le API, poiché le richieste possono fallire per vari motivi (ad esempio, problemi di rete, autorizzazione mancante, ecc.).

Esempio:
```python
try:
    response = requests.get("https://api.esempio.com/data")
    response.raise_for_status()  # Solleva un'eccezione se la richiesta fallisce
except requests.exceptions.HTTPError as err:
    print(f"Errore HTTP: {err}")
except requests.exceptions.ConnectionError:
    print("Errore di connessione")
except requests.exceptions.Timeout:
    print("Richiesta scaduta")
except requests.exceptions.RequestException as err:
    print(f"Errore nella richiesta: {err}")
```

### Parsing di dati JSON

La maggior parte delle API restituisce i dati in formato **JSON**. La libreria requests può gestire automaticamente il parsing di questi dati.

Esempio:
```python
import requests

url = "https://jsonplaceholder.typicode.com/todos/1"
response = requests.get(url)

if response.status_code == 200:
    dati = response.json()
    print(dati['title'])  # Accedere a un campo specifico nel JSON
```

### Eseguire richieste in modo asincrono

Per gestire più richieste contemporaneamente, è possibile utilizzare il modulo **aiohttp** per inviare richieste asincrone. Questo permette di migliorare le prestazioni, specialmente quando si lavora con più API.

Esempio:
```python
import aiohttp
import asyncio

async def fetch_data(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.json()

async def main():
    url = "https://jsonplaceholder.typicode.com/todos/1"
    dati = await fetch_data(url)
    print(dati)

asyncio.run(main())
```

### Invio di file con POST

Le API possono anche accettare file inviati attraverso una richiesta POST. Ecco come inviare un file a un server.

Esempio:
```python
url = "https://api.esempio.com/upload"
files = {"file": open("documento.txt", "rb")}

response = requests.post(url, files=files)

if response.status_code == 200:
    print("File caricato con successo")
else:
    print("Errore nel caricamento del file")
```

## Conclusione

L'interazione con le API è una competenza essenziale per costruire applicazioni moderne. Python, con il modulo `requests`, rende semplice inviare richieste HTTP e gestire le risposte. Nel prossimo articolo esploreremo come utilizzare Python per l'**automazione di script**, migliorando la produttività e semplificando le attività ripetitive.

---
layout: post
title:  "Database con Python: Introduzione a SQLite"
date:   2024-09-08 12:00:00 +0200
categories: corso-python
tags: [python, database, sqlite, SQL]
---

# Database con Python: Introduzione a SQLite

I **database** sono uno strumento essenziale per la memorizzazione e la gestione di grandi quantità di dati. Python offre diversi strumenti per interagire con i database, e uno dei più semplici da usare è **SQLite**, un database leggero che non richiede configurazione. In questo articolo vedremo come utilizzare SQLite in Python per creare e gestire database.

## Cos'è SQLite?

**SQLite** è un sistema di gestione di database relazionali leggero e incorporato. È ideale per piccoli progetti e per applicazioni che non necessitano di un database server come MySQL o PostgreSQL. Python include un modulo chiamato **sqlite3** che permette di interagire facilmente con i database SQLite.

### Creare una connessione a un database

Per iniziare a lavorare con SQLite in Python, dobbiamo prima creare una connessione a un database. Se il file del database non esiste, SQLite lo creerà automaticamente.

Esempio:
```python
import sqlite3

# Connessione a un database (o creazione se non esiste)
conn = sqlite3.connect('esempio.db')

# Creazione di un cursore
cursore = conn.cursor()

# Chiusura della connessione
conn.close()
```

### Creare una tabella

Una volta stabilita la connessione, possiamo creare tabelle utilizzando il linguaggio SQL. Ecco come creare una tabella per memorizzare informazioni sugli utenti:

Esempio:
```python
import sqlite3

conn = sqlite3.connect('esempio.db')
cursore = conn.cursor()

# Creare una tabella
cursore.execute('''
CREATE TABLE IF NOT EXISTS utenti (
    id INTEGER PRIMARY KEY,
    nome TEXT,
    età INTEGER
)
''')

conn.commit()
conn.close()
```

In questo esempio, la tabella `utenti` ha tre colonne: `id`, `nome` e `età`. La colonna `id` è la chiave primaria, che viene automaticamente incrementata.

### Inserire dati in una tabella

Per inserire dati in una tabella, possiamo utilizzare l'istruzione SQL `INSERT`.

Esempio:
```python
import sqlite3

conn = sqlite3.connect('esempio.db')
cursore = conn.cursor()

# Inserire dati nella tabella
cursore.execute("INSERT INTO utenti (nome, età) VALUES (?, ?)", ('Alice', 25))
cursore.execute("INSERT INTO utenti (nome, età) VALUES (?, ?)", ('Bob', 30))

conn.commit()
conn.close()
```

In questo esempio, abbiamo inserito due righe nella tabella `utenti`.

### Leggere dati da una tabella

Per leggere i dati da una tabella, possiamo usare l'istruzione SQL `SELECT`.

Esempio:
```python
import sqlite3

conn = sqlite3.connect('esempio.db')
cursore = conn.cursor()

# Leggere i dati dalla tabella
cursore.execute("SELECT * FROM utenti")
utenti = cursore.fetchall()

for utente in utenti:
    print(utente)

conn.close()
```

In questo esempio, `fetchall()` restituisce tutte le righe della tabella e le stampa.

### Aggiornare e cancellare dati

Per aggiornare e cancellare dati, usiamo rispettivamente le istruzioni SQL `UPDATE` e `DELETE`.

Esempio di aggiornamento:
```python
conn = sqlite3.connect('esempio.db')
cursore = conn.cursor()

# Aggiornare i dati
cursore.execute("UPDATE utenti SET età = ? WHERE nome = ?", (26, 'Alice'))

conn.commit()
conn.close()
```

Esempio di cancellazione:
```python
conn = sqlite3.connect('esempio.db')
cursore = conn.cursor()

# Cancellare un utente
cursore.execute("DELETE FROM utenti WHERE nome = ?", ('Bob',))

conn.commit()
conn.close()
```

### Query più complesse

SQLite supporta query SQL più complesse, come le **JOIN**, che permettono di combinare dati da più tabelle. Ecco un esempio di come eseguire una join su due tabelle:

```python
cursore.execute('''
SELECT utenti.nome, ordini.prodotto 
FROM utenti
JOIN ordini ON utenti.id = ordini.utente_id
''')
```

In questo esempio, recuperiamo il nome degli utenti e il prodotto associato da un'altra tabella chiamata `ordini`.

## Gestione delle eccezioni

Quando si lavora con database, è importante gestire le eccezioni per evitare che errori blocchino il programma. Possiamo utilizzare blocchi `try-except` per catturare eventuali errori durante le operazioni con SQLite.

Esempio:
```python
try:
    conn = sqlite3.connect('esempio.db')
    cursore = conn.cursor()
    # Eseguire alcune operazioni
except sqlite3.Error as e:
    print(f"Errore durante l'accesso al database: {e}")
finally:
    if conn:
        conn.close()
```

## Conclusione

SQLite è un ottimo strumento per iniziare a lavorare con i database in Python. Con il modulo `sqlite3`, puoi creare, leggere, aggiornare e cancellare dati in modo semplice utilizzando SQL. Nel prossimo articolo, parleremo di come interagire con le **API** e lavorare con dati esterni.

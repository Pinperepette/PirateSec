---
layout: post
title:  "Interfacce grafiche con Tkinter"
date:   2024-09-08 21:00:00 +0200
categories: corso-python
tags: [python, tkinter, interfacce-grafiche, GUI]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Interfacce grafiche con Tkinter

**Tkinter** è la libreria standard di Python per la creazione di **interfacce grafiche** (GUI). Fornisce strumenti semplici per costruire finestre, pulsanti, etichette e altri componenti grafici, permettendoti di creare applicazioni desktop interattive. In questo articolo esploreremo come utilizzare Tkinter per creare una GUI di base.

## Creare una finestra

Per iniziare con Tkinter, il primo passo è creare una finestra principale. Ecco un esempio di come farlo:

Esempio:
```python
import tkinter as tk

# Creare la finestra principale
root = tk.Tk()

# Impostare il titolo della finestra
root.title("La mia prima finestra")

# Impostare le dimensioni della finestra
root.geometry("400x300")

# Avviare il loop principale
root.mainloop()
```

In questo esempio, abbiamo creato una finestra vuota con il titolo "La mia prima finestra" e una dimensione di 400x300 pixel.

## Aggiungere etichette e pulsanti

Ora possiamo aggiungere componenti grafici come etichette (`Label`) e pulsanti (`Button`) alla finestra.

Esempio:
```python
import tkinter as tk

# Creare la finestra principale
root = tk.Tk()
root.title("Interfaccia semplice")
root.geometry("400x300")

# Aggiungere un'etichetta
etichetta = tk.Label(root, text="Ciao, benvenuto nella mia GUI!")
etichetta.pack(pady=20)

# Funzione per il pulsante
def saluta():
    etichetta.config(text="Hai cliccato il pulsante!")

# Aggiungere un pulsante
pulsante = tk.Button(root, text="Cliccami", command=saluta)
pulsante.pack(pady=10)

# Avviare il loop principale
root.mainloop()
```

In questo esempio, abbiamo aggiunto un'etichetta e un pulsante alla finestra. Quando l'utente clicca sul pulsante, il testo dell'etichetta cambia.

## Campi di testo e input utente

Tkinter permette di creare campi di testo per raccogliere input dagli utenti.

Esempio:
```python
import tkinter as tk

# Creare la finestra principale
root = tk.Tk()
root.title("Interfaccia con input")
root.geometry("400x300")

# Aggiungere un'etichetta
etichetta = tk.Label(root, text="Inserisci il tuo nome:")
etichetta.pack(pady=10)

# Aggiungere un campo di testo
input_nome = tk.Entry(root)
input_nome.pack(pady=10)

# Funzione per il pulsante
def mostra_nome():
    nome = input_nome.get()
    etichetta.config(text=f"Ciao, {nome}!")

# Aggiungere un pulsante
pulsante = tk.Button(root, text="Saluta", command=mostra_nome)
pulsante.pack(pady=10)

# Avviare il loop principale
root.mainloop()
```

In questo esempio, l'utente può inserire il proprio nome e, quando clicca sul pulsante, il programma lo saluta mostrando il nome inserito.

## Layout con Frame e grid

Tkinter offre vari strumenti per organizzare i componenti grafici nella finestra. Oltre al metodo `pack()`, possiamo usare il layout **grid**, che permette di posizionare gli elementi in una griglia.

Esempio:
```python
import tkinter as tk

root = tk.Tk()
root.title("Layout a griglia")
root.geometry("400x300")

# Creare etichette e pulsanti con il layout a griglia
for i in range(3):
    for j in range(3):
        tk.Button(root, text=f"Bottone {i},{j}").grid(row=i, column=j, padx=10, pady=10)

root.mainloop()
```

In questo esempio, abbiamo creato una griglia di 3x3 con pulsanti, posizionandoli in righe e colonne.

## Finestra di dialogo

Tkinter include anche finestre di dialogo predefinite per mostrare messaggi o chiedere conferme agli utenti.

Esempio di finestra di messaggio:
```python
import tkinter as tk
from tkinter import messagebox

root = tk.Tk()
root.title("Finestra di dialogo")
root.geometry("400x300")

# Funzione per mostrare un messaggio
def mostra_messaggio():
    messagebox.showinfo("Messaggio", "Questo è un messaggio di Tkinter!")

# Aggiungere un pulsante per aprire la finestra di dialogo
pulsante = tk.Button(root, text="Mostra messaggio", command=mostra_messaggio)
pulsante.pack(pady=20)

root.mainloop()
```

## Personalizzare la finestra

Puoi personalizzare la finestra della tua GUI cambiando il titolo, l'icona e aggiungendo menù.

### Aggiungere un menù

Esempio:
```python
root = tk.Tk()
root.title("Finestra con menù")
root.geometry("400x300")

# Creare il menù principale
menubar = tk.Menu(root)

# Aggiungere un menù a tendina
filemenu = tk.Menu(menubar, tearoff=0)
filemenu.add_command(label="Nuovo")
filemenu.add_command(label="Apri")
filemenu.add_command(label="Salva")
filemenu.add_separator()
filemenu.add_command(label="Esci", command=root.quit)

menubar.add_cascade(label="File", menu=filemenu)
root.config(menu=menubar)

root.mainloop()
```

In questo esempio, abbiamo aggiunto un menù a tendina con diverse opzioni.

## Conclusione

Tkinter offre un modo semplice e veloce per creare interfacce grafiche in Python. Con Tkinter puoi creare finestre, pulsanti, etichette e campi di testo, oltre a personalizzare la tua GUI con menù e finestre di dialogo. Nel prossimo articolo esploreremo alcuni progetti finali che combinano tutto ciò che abbiamo appreso finora.

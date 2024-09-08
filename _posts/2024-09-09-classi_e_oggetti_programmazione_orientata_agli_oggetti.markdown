---
layout: post
title:  "Programmazione orientata agli oggetti: Classi e oggetti"
date:   2024-09-08 16:30:00 +0200
categories: corso-python
tags: [python, programmazione-orientata-agli-oggetti, classi, oggetti]
---

# Programmazione orientata agli oggetti: Classi e oggetti

La **programmazione orientata agli oggetti** (OOP) è un paradigma di programmazione che organizza il codice attorno a "oggetti", che possono rappresentare entità del mondo reale o concetti astratti. In Python, la OOP è un modo efficace per scrivere codice più strutturato e riutilizzabile. In questo articolo, esploreremo i concetti di **classi** e **oggetti**.

## Cos'è una classe?

Una **classe** è un modello o un blueprint per creare oggetti. Una classe definisce le proprietà (attributi) e i comportamenti (metodi) degli oggetti. In Python, le classi si definiscono con la parola chiave `class`.

Esempio:
```python
class Cane:
    def __init__(self, nome, razza):
        self.nome = nome  # Attributo
        self.razza = razza  # Attributo

    def abbaia(self):  # Metodo
        print(f"{self.nome} sta abbaiando!")
```

In questo esempio, la classe `Cane` ha due attributi (`nome` e `razza`) e un metodo (`abbaia()`).

### Il metodo `__init__`

Il metodo `__init__()` è un metodo speciale chiamato automaticamente quando viene creato un nuovo oggetto della classe. È utilizzato per inizializzare gli attributi dell'oggetto.

## Creare un oggetto

Un **oggetto** è un'istanza di una classe. Una volta definita una classe, possiamo creare oggetti che rappresentano istanze specifiche di quella classe.

Esempio:
```python
mio_cane = Cane("Fido", "Labrador")
print(mio_cane.nome)  # Stampa "Fido"
print(mio_cane.razza)  # Stampa "Labrador"
mio_cane.abbaia()  # Stampa "Fido sta abbaiando!"
```

Qui, abbiamo creato un oggetto `mio_cane` della classe `Cane`. Abbiamo poi accesso ai suoi attributi e metodo.

## Attributi di istanza e di classe

Gli **attributi di istanza** sono specifici di ogni oggetto e definiti nel metodo `__init__()`. Gli **attributi di classe**, invece, sono condivisi da tutte le istanze della classe.

Esempio:
```python
class Cane:
    specie = "Mammifero"  # Attributo di classe

    def __init__(self, nome, razza):
        self.nome = nome  # Attributo di istanza
        self.razza = razza  # Attributo di istanza

mio_cane = Cane("Fido", "Labrador")
print(mio_cane.specie)  # Stampa "Mammifero"
```

Qui, `specie` è un attributo di classe e vale per tutti i cani, mentre `nome` e `razza` sono attributi specifici per ogni cane.

## Metodi

I **metodi** sono funzioni definite all'interno di una classe e che operano sugli oggetti di quella classe. Il primo parametro di ogni metodo deve essere `self`, che rappresenta l'istanza dell'oggetto stesso.

Esempio:
```python
class Cane:
    def __init__(self, nome, razza):
        self.nome = nome
        self.razza = razza

    def abbaia(self):
        print(f"{self.nome} sta abbaiando!")

mio_cane = Cane("Fido", "Labrador")
mio_cane.abbaia()  # Stampa "Fido sta abbaiando!"
```

## Ereditarietà

L'**ereditarietà** permette di definire una nuova classe basata su una classe esistente, ereditando attributi e metodi della classe genitore. La classe derivata può anche sovrascrivere metodi e aggiungere nuove funzionalità.

Esempio:
```python
class Animale:
    def __init__(self, nome):
        self.nome = nome

    def fai_suono(self):
        print(f"{self.nome} fa un suono.")

class Cane(Animale):  # Cane eredita da Animale
    def abbaia(self):
        print(f"{self.nome} sta abbaiando!")

mio_cane = Cane("Fido")
mio_cane.fai_suono()  # Stampa "Fido fa un suono."
mio_cane.abbaia()  # Stampa "Fido sta abbaiando!"
```

In questo esempio, la classe `Cane` eredita dalla classe `Animale` e può usare i suoi metodi.

## Polimorfismo

Il **polimorfismo** permette a oggetti di classi diverse di essere trattati allo stesso modo attraverso un'interfaccia comune.

Esempio:
```python
class Gatto(Animale):
    def fai_suono(self):
        print(f"{self.nome} miagola.")

animali = [Cane("Fido"), Gatto("Whiskers")]

for animale in animali:
    animale.fai_suono()
```

In questo esempio, sia la classe `Cane` che `Gatto` hanno un metodo `fai_suono()`, e possiamo trattarli nello stesso modo all'interno di una lista di oggetti `Animale`.

## Incapsulamento

L'**incapsulamento** è il principio di nascondere i dettagli interni di un oggetto e consentire l'accesso solo tramite metodi pubblici.

Esempio:
```python
class ContoBancario:
    def __init__(self, saldo):
        self.__saldo = saldo  # Attributo privato

    def deposita(self, importo):
        self.__saldo += importo

    def preleva(self, importo):
        if importo <= self.__saldo:
            self.__saldo -= importo
        else:
            print("Saldo insufficiente")

    def mostra_saldo(self):
        print(f"Il saldo è: {self.__saldo}")

conto = ContoBancario(100)
conto.deposita(50)
conto.mostra_saldo()  # Stampa "Il saldo è: 150"
```

In questo esempio, l'attributo `__saldo` è privato e può essere modificato solo tramite i metodi pubblici `deposita()`, `preleva()` e `mostra_saldo()`.

## Conclusione

La programmazione orientata agli oggetti è un paradigma potente per organizzare il codice in Python. Utilizzando classi e oggetti, puoi scrivere codice più modulare, manutenibile e riutilizzabile. Nel prossimo articolo parleremo di **ereditarietà e polimorfismo** in dettaglio.

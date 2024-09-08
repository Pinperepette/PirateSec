---
layout: post
title:  "Ereditarietà e polimorfismo: Concetti avanzati di OOP"
date:   2024-09-08 17:00:00 +0200
categories: corso-python
tags: [python, ereditarietà, polimorfismo, OOP, programmazione-orientata-agli-oggetti]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Ereditarietà e polimorfismo: Concetti avanzati di OOP

L'**ereditarietà** e il **polimorfismo** sono due concetti fondamentali nella programmazione orientata agli oggetti (OOP). L'ereditarietà permette di creare nuove classi basate su classi esistenti, mentre il polimorfismo consente di trattare oggetti di classi diverse in modo uniforme. In questo articolo, esploreremo questi concetti avanzati con esempi pratici.

## Ereditarietà

L'**ereditarietà** è il meccanismo attraverso il quale una classe figlia eredita attributi e metodi da una classe genitore. Questo ti permette di riutilizzare il codice e di estendere le funzionalità di una classe senza riscrivere tutto da zero.

### Classe base e classe derivata

Una **classe base** (o classe genitore) è una classe che viene estesa da una **classe derivata** (o classe figlia). La classe figlia eredita tutti i metodi e gli attributi della classe base, ma può anche aggiungere nuovi metodi o sovrascrivere quelli esistenti.

Esempio:
```python
class Animale:
    def __init__(self, nome):
        self.nome = nome

    def fai_suono(self):
        print(f"{self.nome} fa un suono.")

class Cane(Animale):  # Cane eredita da Animale
    def fai_suono(self):
        print(f"{self.nome} abbaia.")

class Gatto(Animale):  # Gatto eredita da Animale
    def fai_suono(self):
        print(f"{self.nome} miagola.")
```

In questo esempio, `Cane` e `Gatto` sono classi derivate da `Animale` e sovrascrivono il metodo `fai_suono()`.

### Il metodo `super()`

Quando si sovrascrive un metodo in una classe derivata, puoi ancora chiamare il metodo originale della classe genitore utilizzando la funzione `super()`.

Esempio:
```python
class Cane(Animale):
    def __init__(self, nome, razza):
        super().__init__(nome)  # Chiama il costruttore della classe base
        self.razza = razza

    def fai_suono(self):
        super().fai_suono()  # Chiama il metodo della classe base
        print(f"{self.nome} abbaia.")
```

In questo esempio, utilizziamo `super()` per chiamare il costruttore della classe `Animale` e inizializzare l'attributo `nome`. Lo stesso metodo viene utilizzato per estendere il comportamento del metodo `fai_suono()`.

## Polimorfismo

Il **polimorfismo** consente di trattare oggetti di classi diverse attraverso la stessa interfaccia, senza sapere esattamente a quale classe appartengano. Questo è possibile perché le classi derivate possono avere metodi con lo stesso nome della classe base.

Esempio:
```python
animali = [Cane("Fido"), Gatto("Whiskers")]

for animale in animali:
    animale.fai_suono()
```

In questo esempio, non ci interessa se `animale` è un `Cane` o un `Gatto`. Sappiamo solo che ogni animale ha un metodo `fai_suono()` che può essere chiamato, e il comportamento specifico verrà determinato dalla classe a cui l'oggetto appartiene.

## Ereditarietà multipla

In Python, una classe può ereditare da più di una classe base. Questo si chiama **ereditarietà multipla**.

Esempio:
```python
class Volante:
    def vola(self):
        print("L'animale può volare.")

class Camminante:
    def cammina(self):
        print("L'animale può camminare.")

class Pipistrello(Volante, Camminante):
    pass

pipistrello = Pipistrello()
pipistrello.vola()  # Stampa "L'animale può volare."
pipistrello.cammina()  # Stampa "L'animale può camminare."
```

In questo esempio, la classe `Pipistrello` eredita sia dalla classe `Volante` che dalla classe `Camminante`, quindi può utilizzare i metodi di entrambe le classi.

## Classi astratte e polimorfismo

In Python, possiamo usare classi astratte per definire un'interfaccia comune che deve essere implementata dalle classi derivate. Per fare questo, utilizziamo il modulo `abc` e definiamo metodi astratti con il decoratore `@abstractmethod`.

Esempio:
```python
from abc import ABC, abstractmethod

class Animale(ABC):
    @abstractmethod
    def fai_suono(self):
        pass

class Cane(Animale):
    def fai_suono(self):
        print("Il cane abbaia.")

class Gatto(Animale):
    def fai_suono(self):
        print("Il gatto miagola.")

animali = [Cane(), Gatto()]

for animale in animali:
    animale.fai_suono()
```

In questo esempio, la classe `Animale` è una classe astratta e impone alle classi derivate di implementare il metodo `fai_suono()`.

## Conclusione

L'ereditarietà e il polimorfismo sono concetti chiave della programmazione orientata agli oggetti che ti permettono di scrivere codice più flessibile e riutilizzabile. Nel prossimo articolo, esploreremo altri concetti avanzati, come i **decoratori** e i **generatori** in Python.

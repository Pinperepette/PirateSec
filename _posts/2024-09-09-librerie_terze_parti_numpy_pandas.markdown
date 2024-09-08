---
layout: post
title:  "Librerie di terze parti: NumPy, Pandas e altro"
date:   2024-09-08 18:30:00 +0200
categories: corso-python
tags: [python, numpy, pandas, librerie-di-terze-parti]
permalink: /PirateSec/corso-python/:year/:month/:day/:title.html
---

# Librerie di terze parti: NumPy, Pandas e altro

Uno dei motivi per cui Python è così popolare è la vasta gamma di **librerie di terze parti** disponibili, che estendono le funzionalità del linguaggio per affrontare problemi specifici. In questo articolo esploreremo alcune delle librerie più usate, come **NumPy** e **Pandas**, e vedremo come possono semplificare il lavoro con dati e calcoli complessi.

## NumPy

**NumPy** è una libreria fondamentale per il calcolo scientifico in Python. Offre supporto per array multidimensionali e funzioni matematiche di alto livello.

### Installare NumPy

Puoi installare NumPy utilizzando `pip`:

```bash
pip install numpy
```

### Array in NumPy

Il concetto principale di NumPy è l'**array**. Gli array NumPy sono simili alle liste Python, ma offrono prestazioni molto migliori quando si tratta di eseguire calcoli numerici su grandi quantità di dati.

Esempio:
```python
import numpy as np

# Creare un array NumPy
array = np.array([1, 2, 3, 4])
print(array)
```

### Operazioni con array

Uno dei punti di forza di NumPy è la capacità di eseguire operazioni vettoriali sugli array senza dover usare loop espliciti.

Esempio:
```python
array = np.array([1, 2, 3, 4])
print(array * 2)  # Moltiplica ogni elemento per 2
```

Questo restituirà:
```
[2 4 6 8]
```

### Array multidimensionali

NumPy supporta array multidimensionali, utili per rappresentare matrici e altre strutture di dati complessi.

Esempio:
```python
matrice = np.array([[1, 2, 3], [4, 5, 6]])
print(matrice)
```

Questo stamperà:
```
[[1 2 3]
 [4 5 6]]
```

## Pandas

**Pandas** è una libreria potente per l'analisi e la manipolazione dei dati. Utilizza due strutture principali: **Series** e **DataFrame**.

### Installare Pandas

Puoi installare Pandas utilizzando `pip`:

```bash
pip install pandas
```

### Series

Una **Series** è una struttura dati simile a un array, ma con etichette (indici) per ogni elemento.

Esempio:
```python
import pandas as pd

serie = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
print(serie)
```

### DataFrame

Un **DataFrame** è una struttura bidimensionale simile a una tabella, con etichette per righe e colonne.

Esempio:
```python
import pandas as pd

dati = {
    'Nome': ['Alice', 'Bob', 'Charlie'],
    'Età': [25, 30, 35]
}
df = pd.DataFrame(dati)
print(df)
```

Questo stamperà:
```
      Nome  Età
0    Alice   25
1      Bob   30
2  Charlie   35
```

### Lettura di file con Pandas

Una delle caratteristiche più utili di Pandas è la capacità di leggere dati da vari formati di file, come CSV e Excel.

Esempio:
```python
df = pd.read_csv('file.csv')
print(df)
```

## Matplotlib

**Matplotlib** è una libreria per la creazione di grafici e visualizzazioni. È ampiamente utilizzata per rappresentare graficamente i dati.

### Installare Matplotlib

Puoi installare Matplotlib utilizzando `pip`:

```bash
pip install matplotlib
```

### Creare un grafico semplice

Ecco come creare un grafico semplice utilizzando Matplotlib:

Esempio:
```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4]
y = [10, 20, 25, 30]

plt.plot(x, y)
plt.title('Grafico semplice')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()
```

## Scikit-learn

**Scikit-learn** è una libreria per l'apprendimento automatico. Contiene strumenti per la classificazione, la regressione, il clustering e molto altro.

### Installare Scikit-learn

Puoi installare Scikit-learn utilizzando `pip`:

```bash
pip install scikit-learn
```

### Esempio di classificazione

Ecco un esempio di come utilizzare Scikit-learn per addestrare un classificatore:

Esempio:
```python
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

# Carica il dataset iris
iris = datasets.load_iris()
X = iris.data
y = iris.target

# Dividi i dati in set di addestramento e test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)

# Addestra un classificatore Random Forest
clf = RandomForestClassifier()
clf.fit(X_train, y_train)

# Valutazione del modello
accuracy = clf.score(X_test, y_test)
print(f'Accuratezza: {accuracy}')
```

## Conclusione

Le librerie di terze parti come NumPy, Pandas, Matplotlib e Scikit-learn espandono notevolmente le capacità di Python, rendendolo uno strumento ideale per l'analisi dei dati, il calcolo scientifico e l'apprendimento automatico. Nel prossimo articolo, esploreremo come eseguire il **testing e il debugging** in Python per migliorare la qualità del nostro codice.

# L2 — Conosci il tuo dataset

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L02_conosci_il_dataset/L02_task.ipynb)

## Cosa sai fare dopo questa lezione

- Caricare un file Excel in Python
- Capire cos'è un DataFrame
- Distinguere metodi e attributi
- Fare a un dataset le domande di base prima di analizzarlo

## Le librerie

Una **libreria** è codice scritto da altri, pronto da usare. Nessuno scrive da zero il codice per leggere un file Excel: lo prendi da una libreria.

```python
import pandas as pd
```

- `import pandas` carica la libreria **pandas**, quella per le tabelle.
- `as pd` le dà un nome corto: da qui in poi scrivi `pd` invece di `pandas`.

In Colab le librerie più comuni sono già installate. Basta importarle.

## Caricare un file Excel

```python
url = "https://raw.githubusercontent.com/andrealorenzon/SIMA2026/main/dati/imprese.xlsx"
df = pd.read_excel(url)
```

Il file viene letto e messo nella variabile `df`. Il file originale non viene modificato: tutto quello che fai, lo fai sulla copia in memoria.

Per un file sul tuo computer: in Colab, carica il file con l'icona della cartella a sinistra, poi usa `pd.read_excel("nome_file.xlsx")`.

## Il DataFrame

Un **DataFrame** è una tabella, come un foglio Excel:
- ogni **riga** è un'osservazione (nel nostro caso: un'impresa in un anno);
- ogni **colonna** ha un nome e un tipo di dato;
- a sinistra c'è l'**indice**, il numero della riga, che parte da **0**.

Per prendere una colonna sola:

```python
df["regione"]
```

## Metodi e attributi

`df` è un **oggetto**: contiene i dati, più tutte le cose che puoi chiedergli. Il punto `.` collega l'oggetto a quello che gli chiedi.

| | Cos'è | Parentesi | Esempio |
|---|---|---|---|
| **Metodo** | un'azione | sì | `df.head(3)` |
| **Attributo** | un'informazione | no | `df.shape` |

Trucco: in Colab scrivi `df.` e premi **Tab** per vedere tutto quello che puoi chiedere.

## Le domande da fare sempre a un dataset

| Domanda | Comando |
|---|---|
| Che faccia ha? | `df.head()` |
| Quanto è grande? | `df.shape` |
| Di che tipo sono le colonne? | `df.dtypes` |
| Quanti valori diversi in una colonna? | `df["colonna"].nunique()` |
| Quali valori, e quante volte? | `df["colonna"].value_counts()` |
| Riepilogo delle colonne numeriche | `df.describe()` |

Non serve ricordare i comandi: serve ricordare **le domande**. I comandi si cercano.

## Cosa abbiamo trovato in `imprese.xlsx`

- Il **fatturato è letto come testo**: il file usa la virgola decimale italiana e contiene valori `n.d.`. La media dà errore; il massimo invece restituisce `'n.d.'`, perché confronta testi in ordine alfabetico.
- Ci sono **2.515 righe** invece delle 2.500 attese (500 imprese × 5 anni).
- La stessa **regione è scritta in modi diversi** (`Lombardia`, `lombardia`, `LOMBARDIA`, `Lombardia ` con uno spazio finale).
- C'è un'impresa con **addetti negativi**.

Solo uno di questi problemi ha prodotto un errore. Gli altri erano silenziosi. Li sistemiamo nella prossima lezione.

## Compito a casa

- [Kaggle Learn – Pandas](https://www.kaggle.com/learn/pandas): le prime due lezioni, **Creating, Reading and Writing** e **Indexing, Selecting & Assigning** (~40 min)

## Per approfondire

- [W3Schools – Pandas](https://www.w3schools.com/python/pandas/default.asp): prontuario da consultare
- [QuantEcon – Pandas](https://python-programming.quantecon.org/pandas.html): facoltativo

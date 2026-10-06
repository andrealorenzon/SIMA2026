# L2 — Conosci il tuo dataset

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L02_conosci_il_dataset/L02_task.ipynb)

## Cosa sai fare dopo questa lezione

- Caricare un file Excel in Python
- Capire cos'è un DataFrame
- Selezionare righe e colonne, e capire come funziona lo slicing
- Distinguere metodi e attributi
- Trovare da solo i metodi che ti servono nella documentazione
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

## Selezionare righe e colonne

| Cosa vuoi | Come | Esempio |
|---|---|---|
| una colonna | `df["nome"]` | `df["regione"]` |
| più colonne | `df[[...]]`: una lista di nomi, quindi doppie parentesi | `df[["regione", "anno"]]` |
| righe per posizione | `df.iloc[inizio:fine]` | `df.iloc[0:5]` |
| righe e colonne per posizione | `df.iloc[righe, colonne]` | `df.iloc[0:5, 0:3]` |
| righe che rispettano una condizione | `df[condizione]` | `df[df["anno"] == 2020]` |

Si possono combinare: `df.iloc[100:110][["id_impresa", "anno"]]` prende le righe dalla 100 alla 109 e solo due colonne.

## Slicing: come funzionano gli indici

Lo **slicing** (affettare) è il modo in cui Python prende un pezzo di una sequenza: una lista, un testo, le righe di un DataFrame. Funziona sempre allo stesso modo.

Le posizioni partono da **0**. Ma i numeri dentro `[inizio:fine]` vanno pensati come **tagli tra una casella e l'altra**, non come caselle:

```
 taglio:   0   1   2   3   4   5   6
           | A | B | C | D | E | F |
posizione:   0   1   2   3   4   5
dalla fine: -6  -5  -4  -3  -2  -1
```

`x[1:4]` taglia al 1 e al 4: prende **B, C, D**. Per questo:
- il primo numero è **incluso**, il secondo è **escluso**;
- fine − inizio = quanti elementi ottieni (4 − 1 = 3).

| Scrittura | Risultato | Significato |
|---|---|---|
| `x[1:4]` | B C D | dal taglio 1 al taglio 4 |
| `x[:3]` | A B C | dall'inizio al taglio 3 (i primi 3) |
| `x[3:]` | D E F | dal taglio 3 alla fine |
| `x[-2:]` | E F | gli ultimi 2 |
| `x[2]` | C | senza i due punti: **una casella sola**, la posizione 2 |

Funziona anche sui testi: `"Milano"[0:3]` dà `"Mil"`.

## iloc e Excel

`df.iloc[righe, colonne]` è come selezionare un intervallo in Excel, con tre differenze:

| | Excel | `iloc` |
|---|---|---|
| Prima riga di dati | 2 (la 1 è l'intestazione) | 0 |
| Fine dell'intervallo | inclusa | esclusa |
| Colonne | lettere: A, B, C | numeri: 0, 1, 2 |
| Ordine | colonna e poi riga (A2) | righe e poi colonne `[righe, colonne]` |

Esempio: l'intervallo Excel **A2:C6** (prime cinque righe di dati, prime tre colonne) corrisponde a `df.iloc[0:5, 0:3]`.

## Metodi e attributi

`df` è un **oggetto**: contiene i dati, più tutte le cose che puoi chiedergli. Il punto `.` collega l'oggetto a quello che gli chiedi.

| | Cos'è | Parentesi | Esempio |
|---|---|---|---|
| **Metodo** | un'azione | sì | `df.head(3)` |
| **Attributo** | un'informazione | no | `df.shape` |

## Come scoprire cosa sa fare un oggetto

Nessuno conosce tutti i metodi di un DataFrame: si cercano, ogni giorno, anche dopo anni di lavoro. Tre strade:

- **Tab**: in Colab scrivi `df.` e premi **Tab**. Compare l'elenco di tutto quello che puoi chiedere.
- **`help`**: `help(df.head)` mostra la spiegazione di un metodo, con i parametri e degli esempi.
- **La documentazione ufficiale**: l'[elenco completo dei metodi dei DataFrame](https://pandas.pydata.org/docs/reference/frame.html). Ogni metodo ha una pagina con cosa fa, i parametri, cosa restituisce e, in fondo, degli esempi: spesso la parte più utile.

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

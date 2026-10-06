# L3 — Pulire i dati

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L03_pulizia/L03_task.ipynb)

## Cosa sai fare dopo questa lezione

- Trovare ed eliminare righe duplicate
- Lavorare sulle colonne di testo
- Convertire testo in numeri senza perdere dati
- Modificare solo le righe che rispettano una condizione
- Correggere una singola cella in modo sicuro e documentato
- Riconoscere e contare i valori mancanti
- Verificare ogni correzione

## Pulire è decidere

Pulire un dataset non è un'operazione automatica: ogni correzione è una **decisione** (questo valore è un errore? lo correggo o lo elimino?). Il ciclo è sempre lo stesso:

1. **Trova** il problema
2. **Decidi** cosa fare, e perché
3. **Correggi**
4. **Verifica** che la correzione abbia fatto quello che volevi

Le decisioni vanno scritte: tra sei mesi non te le ricorderai, e chi legge il tuo lavoro deve poterle controllare.

## La regola: conta prima, conta dopo

Prima di ogni correzione, chiediti quanti valori ti aspetti di cambiare. Dopo, controlla.

```python
print(df.shape)          # prima
df = df.drop_duplicates()
print(df.shape)          # dopo: quante righe sono sparite? Sono quelle previste?
```

Molti errori di pulizia **non danno messaggi**: il codice gira e ti fa perdere dati in silenzio. L'unica difesa è contare.

## Riassegnare

Quasi tutti i comandi di pandas **non modificano** `df`: restituiscono una copia modificata. Per tenere la modifica devi salvarla:

```python
df.drop_duplicates()          # mostra il risultato, ma df non cambia
df = df.drop_duplicates()     # ora df è cambiato
```

Lo stesso vale per una colonna:

```python
df["citta"] = df["citta"].str.strip()
```

## Lavorare sul testo: `.str`

Le colonne di testo hanno un "cassetto" di comandi dedicati, a cui si accede con `.str`:

| Comando | Cosa fa | Esempio |
|---|---|---|
| `.str.strip()` | toglie gli spazi all'inizio e alla fine | `" Milano "` → `"Milano"` |
| `.str.lower()` | tutto minuscolo | `"MILANO"` → `"milano"` |
| `.str.title()` | iniziali maiuscole | `"milano"` → `"Milano"` |
| `.str.replace("a", "b")` | sostituisce un pezzo di testo | `"1-2"` → `"1/2"` con `("-", "/")` |

I comandi si possono **concatenare**: `df["citta"].str.strip().str.lower()`.

**Attenzione:** i comandi automatici come `.str.title()` sono comodi ma non conoscono le eccezioni della lingua. Controlla sempre il risultato.

Per sostituire valori interi (non pezzi di testo) c'è `.replace()` con un dizionario:

```python
df["citta"] = df["citta"].replace({"Milan": "Milano", "Roma Capitale": "Roma"})
```

## Da testo a numero

```python
pd.to_numeric(df["colonna"], errors="coerce")
```

Con `errors="coerce"`, tutto quello che non si riesce a convertire diventa un **valore mancante**, senza errori. È comodo, ed è pericoloso: se la conversione è sbagliata, perdi dati senza accorgertene. Dopo una conversione, conta sempre i valori mancanti.

## Modificare solo alcune righe: `.loc`

```python
condizione = df["prezzo"] < 0
df.loc[condizione, "prezzo"] = None
```

Si legge: "nelle righe dove la condizione è vera, nella colonna `prezzo`, metti un valore mancante". Una condizione è una colonna di `True`/`False`; con `.sum()` conti quante righe la rispettano.

## Correggere una cella a mano

A volte sai qual è il valore giusto (te l'ha detto chi ha raccolto i dati, l'hai controllato sulla fonte). In Excel clicchi sulla cella e lo scrivi; in Python lo scrivi **nel codice**, così la correzione resta documentata e si può rifare.

```python
riga = (df["cliente"] == "C042") & (df["anno"] == 2021)
print(riga.sum())                 # deve dare 1: una sola riga
df.loc[riga, "ordini"] = 12
```

Due regole:
- **Individua la riga per contenuto, non per numero.** `df.loc[500, "ordini"] = 12` funziona oggi, ma dopo un ordinamento o dopo aver tolto delle righe la riga 500 è un'altra: la correzione finisce nel posto sbagliato, senza errori.
- **Controlla prima di modificare**: `riga.sum()` deve dare 1. Se dà 0 la condizione è sbagliata; se dà di più stai per cambiare più celle.

Per unire due condizioni si usa `&` ("e"), e ogni condizione va tra parentesi. Per "oppure" si usa `|`.

## Valori mancanti

In pandas un valore mancante si chiama **NaN** (o `NA`). Per contarli:

```python
df.isna().sum()          # quanti mancanti in ogni colonna
```

Un valore mancante **non è uno zero**. Media di 10, mancante, 20:
- lasciando il mancante: (10 + 20) / 2 = **15**
- mettendo 0 al suo posto: (10 + 0 + 20) / 3 = **10**

I calcoli di pandas ignorano i valori mancanti. Riempirli con un numero inventato falsa i risultati.

## Cosa abbiamo trovato e deciso in `imprese.xlsx`

| Problema | Decisione | Verifica |
|---|---|---|
| 15 righe duplicate | eliminate con `drop_duplicates()` | 2.500 righe |
| fatturato come testo (`"1.032,9"`, `"n.d."`) | prima tolto il punto delle migliaia, poi virgola → punto, poi `to_numeric(errors="coerce")` | 50 mancanti, come i `"n.d."` |
| 5 fatturati inseriti in euro invece che in migliaia | valori oltre 200.000 divisi per 1.000 | massimo plausibile (circa 64.000) |
| regioni scritte in modi diversi | `str.strip()` e correzioni esplicite con `replace()` | 20 regioni |
| un'impresa con addetti negativi (IMP0253, 2019) | corretto a 12 su indicazione del collega, individuando la riga per impresa e anno | nessun negativo |
| valori mancanti in addetti, fatturato e spesa R&S | lasciati mancanti | `isna().sum()` |

**La trappola dell'ordine.** Se si sostituisce prima la virgola con il punto, `"1.032,9"` diventa `"1.032.9"`, che non è un numero: con `errors="coerce"` diventa mancante. Risultato: 1.621 valori mancanti invece di 50, e nessun messaggio di errore. Solo il conteggio dei mancanti lo rivela.

**La trappola di `title()`.** `str.title()` sistema le maiuscole ma trasforma `Valle d'Aosta` in `Valle D'Aosta` e lascia `Emilia Romagna` senza trattino: le regioni restano 21. Il problema si vedrebbe nella L5, unendo i dati con la tabella delle regioni.

## Compito a casa

- [Kaggle Learn – Pandas](https://www.kaggle.com/learn/pandas), lezione **Data Types and Missing Values** (~20 min)

## Per approfondire

- [W3Schools – Pandas, pulizia dei dati](https://www.w3schools.com/python/pandas/pandas_cleaning.asp): prontuario
- [QuantEcon – Pandas](https://python-programming.quantecon.org/pandas.html): facoltativo

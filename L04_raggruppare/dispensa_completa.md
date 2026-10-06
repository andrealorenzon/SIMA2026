# L4 — Raggruppare, riassumere, disegnare

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L04_raggruppare/L04_task.ipynb)

## Cosa sai fare dopo questa lezione

- Creare nuove colonne calcolate
- Riassumere i dati per gruppi (per anno, regione, settore)
- Scegliere tra media e mediana, e guardare quante osservazioni ci sono dietro un numero
- Disegnare un grafico a linea, a barre e un istogramma

## Da dove partiamo

Dalla L4 in poi si usa il dataset già pulito, `imprese_pulito.xlsx`: è il risultato della L3.

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel("https://raw.githubusercontent.com/andrealorenzon/SIMA2026/main/dati/imprese_pulito.xlsx")
```

## Nuove colonne

In Excel scrivi una formula nella prima cella e la trascini fino in fondo. In pandas scrivi l'operazione una volta, e vale per tutte le righe:

```python
df["ricavo"] = df["prezzo"] * df["quantita"]
```

Se in una riga manca uno dei due valori, il risultato di quella riga è mancante.

## Raggruppare: `groupby`

`groupby` fa tre cose: **divide** la tabella in gruppi, **calcola** qualcosa su ogni gruppo, **ricompone** i risultati in una tabella.

```python
df.groupby("anno")["fatturato"].mean()
```

Si legge: "per ogni anno, della colonna fatturato, calcola la media". È la tabella pivot di Excel, scritta.

Più statistiche insieme:

```python
df.groupby("anno")["fatturato"].agg(["mean", "median", "count"])
```

Con nomi scelti da te, e colonne diverse:

```python
df.groupby("regione").agg(
    media=("fatturato", "mean"),
    imprese=("id_impresa", "nunique"),
)
```

Statistiche utili: `mean` (media), `median` (mediana), `count` (valori non mancanti), `nunique` (valori diversi), `sum`, `min`, `max`, `std` (deviazione standard).

Il risultato è a sua volta una tabella: puoi ordinarla (`.sort_values()`), filtrarla, disegnarla.

## Media o mediana?

Cinque imprese fatturano 1, 2, 3, 4 e 100 milioni:
- la **media** è 22: un solo valore estremo la sposta molto;
- la **mediana** è 3: il valore che sta in mezzo, quando li metti in ordine.

Con dati **asimmetrici** (redditi, fatturati, patrimoni, prezzi delle case) la mediana descrive meglio il caso "tipico". La media resta utile, ma va letta sapendo che pochi valori grandi la tirano su.

E soprattutto: **guarda sempre quante osservazioni ci sono dietro un numero.** Una media calcolata su due casi non dice quasi niente.

## Grafici

pandas disegna usando la libreria **matplotlib**:

| Domanda | Grafico | Codice |
|---|---|---|
| Come cambia nel tempo? | linea | `serie.plot()` |
| Come si confrontano delle categorie? | barre | `serie.plot(kind="barh")` |
| Come sono distribuiti i valori? | istogramma | `colonna.plot(kind="hist", bins=50)` |

Per rendere un grafico presentabile:

```python
serie.plot(marker="o")
plt.title("Titolo che dice cosa si vede")
plt.xlabel("Anno")
plt.ylabel("Migliaia di euro")
plt.savefig("grafico.png", dpi=150, bbox_inches="tight")
plt.show()
```

Un grafico onesto ha un titolo, gli assi con le unità di misura, le barre in ordine. Se non si capisce senza spiegarlo a voce, non è finito.

## Cosa abbiamo trovato

**La regione più ricca?** Per fatturato **medio** è prima la Liguria (circa 7.000 migliaia di euro), ma solo grazie a una singola impresa enorme (IMP0370, quasi 58 milioni di euro l'anno in media): la sua mediana (circa 1.600) è nella norma. Per fatturato **mediano** è prima la Basilicata, ma con **2 imprese** in tutto. La risposta onesta: le differenze tra regioni sono piccole e in alcune regioni i dati sono pochissimi. Media, mediana e numero di osservazioni vanno guardati insieme.

**Il 2020.** Il fatturato mediano passa da circa 1.436 (2019) a circa 1.054 (2020): circa un quarto in meno. Nel 2021 torna ai livelli precedenti. Il grafico a linea lo mostra al primo sguardo.

**La distribuzione.** L'istogramma del fatturato è molto asimmetrico: tante imprese piccole e poche grandi. Per questo la media (circa 2.600) è molto più alta della mediana (circa 1.400). In scala logaritmica la forma diventa leggibile.

**La produttività.** Ha più valori mancanti del fatturato, perché basta che manchi uno dei due valori (fatturato o addetti). Il settore con la produttività mediana più alta è la manifattura.

## Compito a casa

- [Kaggle Learn – Pandas](https://www.kaggle.com/learn/pandas), lezione **Grouping and Sorting** (~20 min)

## Per approfondire

- [W3Schools – Pandas, grafici](https://www.w3schools.com/python/pandas/pandas_plotting.asp): prontuario
- [QuantEcon – Matplotlib](https://python-programming.quantecon.org/matplotlib.html): facoltativo

# L7 — Dati da internet e una regressione

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L07_internet_regressione/L07_task.ipynb)

## Cosa sai fare dopo questa lezione

- Caricare dati pubblicati online, direttamente dall'indirizzo web
- Capire cosa rappresenta ogni riga di un dataset che non hai preparato tu
- Stimare una regressione lineare e leggerne i risultati principali

## Dati da internet

Molti enti pubblicano dati scaricabili: [Our World in Data](https://ourworldindata.org/), Eurostat, ISTAT, Banca d'Italia, World Bank, OCSE. Se il file è online, `read_csv` e `read_excel` accettano direttamente l'indirizzo:

```python
url = "https://raw.githubusercontent.com/owid/co2-data/master/owid-co2-data.csv"
co2 = pd.read_csv(url)
```

**CSV** (valori separati da virgola) è il formato più diffuso per i dati pubblici: un file di testo, una riga per osservazione.

Vantaggio: rilanci il notebook e hai i dati aggiornati. Rischio: i dati cambiano, e con loro i tuoi risultati. Annota **quando** li hai scaricati, o salvane una copia.

## Prima di analizzare: cosa rappresenta una riga?

Ogni dataset serio ha una **descrizione delle colonne** (codebook): unità di misura, fonte, definizioni. Leggila prima di usare i dati. E chiediti sempre: cosa rappresenta una riga? Un paese in un anno? O anche un continente, un gruppo di paesi, il mondo intero?

Sono le stesse domande della L2, su dati che non hai preparato tu.

## Una regressione

Una **regressione lineare** (OLS, minimi quadrati) cerca la retta che descrive meglio come una variabile cambia al variare di un'altra. Con la libreria `statsmodels` si scrive come una formula:

```python
import statsmodels.formula.api as smf

modello = smf.ols("fatturato ~ addetti", data=df).fit()
print(modello.summary())
```

- `"y ~ x"` si legge "y in funzione di x";
- `"y ~ x + z"` aggiunge una variabile;
- `"np.log(y) ~ np.log(x)"` usa i logaritmi (serve `import numpy as np`).

Il riepilogo è lungo. Per ora bastano tre numeri:

| Cosa | Dove | Come si legge |
|---|---|---|
| coefficiente | `modello.params` | di quanto cambia y, in media, quando x aumenta di 1 (nelle unità di misura di x e y) |
| R² | `modello.rsquared` | quota della variabilità di y descritta dal modello, tra 0 e 1 |
| osservazioni | `modello.nobs` | su quante righe è stata stimata |

In una regressione **log-log** il coefficiente è un'**elasticità**: di quanti punti percentuali cambia y quando x cresce dell'1%.

**Attenzione alle osservazioni.** Le righe con anche un solo valore mancante nelle variabili usate vengono escluse **in silenzio**. Ogni volta che riporti una regressione, riporta su quante osservazioni è stata stimata.

**Associazione, non causa.** Una regressione dice che due variabili si muovono insieme, non che una causa l'altra. Per parlare di cause servono disegni di ricerca appositi: è il mestiere dei corsi di econometria.

## 🎯 Sfida

Quando sommerai le emissioni di tutto il mondo otterrai un numero sbagliato di parecchio, senza nessun errore. Trova perché. E quando leggerai la regressione, controlla su quante imprese è stata stimata davvero.

Le soluzioni sono disponibili dopo la lezione, ma leggerle prima ti toglie l'unica cosa che conta: arrivarci da solo.

## Compito a casa

- Pensa a una domanda a cui vorresti rispondere con i dati, per il mini-progetto finale.

## Per approfondire

- [Our World in Data – dati su CO₂ ed energia](https://github.com/owid/co2-data): il dataset e la descrizione delle colonne
- [Documentazione di statsmodels](https://www.statsmodels.org/stable/example_formulas.html): regressioni con le formule
- [QuantEcon – Pandas for Panel Data](https://python-programming.quantecon.org/pandas_panel.html): facoltativo

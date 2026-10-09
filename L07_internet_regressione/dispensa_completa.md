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

## Cosa abbiamo trovato

*I numeri sui dati di Our World in Data si riferiscono alla versione scaricata a ottobre 2026: se il dataset viene aggiornato possono cambiare leggermente.*

**Il mondo contato sei volte.** Sommando la colonna `co2` per il 2022 si ottengono circa 240.000 milioni di tonnellate, contro le circa 37.500 della riga `World`. La colonna `country` contiene anche **aggregati** (continenti, Unione europea, gruppi di reddito, il mondo intero), quindi gli stessi paesi vengono contati più volte. Gli aggregati non hanno `iso_code`: filtrando le righe con `iso_code` presente restano circa 218 paesi, che sommano circa 36.500 milioni di tonnellate. La differenza residua sono le emissioni di aviazione e navigazione internazionali, che non appartengono a nessun paese.

**La regressione fatturato ~ addetti.**
- Coefficiente di `addetti`: circa 140. Ogni addetto in più è associato, in media, a circa 140 mila euro di fatturato in più (il fatturato è in migliaia di euro).
- R²: circa 0,73.
- Osservazioni: 2.375, non 2.500. Le righe con fatturato o addetti mancanti sono escluse in silenzio.

**Aggiungendo la spesa in R&S** il coefficiente degli addetti scende a circa 116 e le osservazioni a 2.255 (ora basta che manchi uno di tre valori). Parte dell'associazione attribuita agli addetti era legata alla spesa in R&S. Attenzione: i due modelli sono stimati su campioni diversi.

**Associazione, non causa.** La regressione non dice che assumendo una persona un'impresa fattura 140 mila euro in più: dice che, tra imprese diverse, più addetti vanno insieme a più fatturato.

**Bonus: l'elasticità.** Tra i paesi, la regressione log-log della CO₂ pro capite sul PIL pro capite dà un coefficiente di circa 1 (su circa 164 paesi con il PIL disponibile): a un PIL pro capite più alto dell'1% corrispondono emissioni pro capite più alte di circa l'1%.

## Compito a casa

- **Obbligatorio prima della L8:** con il vostro gruppo da 3, scegliete la domanda e i dati per il mini-progetto finale e mandateli al docente in due righe. Alla L8 li controlliamo insieme.

## Per approfondire

- [Our World in Data – dati su CO₂ ed energia](https://github.com/owid/co2-data): il dataset e la descrizione delle colonne
- [Documentazione di statsmodels](https://www.statsmodels.org/stable/example_formulas.html): regressioni con le formule
- [QuantEcon – Pandas for Panel Data](https://python-programming.quantecon.org/pandas_panel.html): facoltativo

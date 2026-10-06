# L8 — Dal notebook allo script

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L08_script/L08_task.ipynb)

## Cosa sai fare dopo questa lezione

- Capire perché un notebook può dare risultati diversi a seconda dell'ordine di esecuzione
- Scrivere ed eseguire uno script `.py`
- Leggere codice scritto da altri (anche dall'AI) e verificare che faccia quello che dichiara
- Preparare un'analisi perché qualcun altro possa rifarla

## Notebook e script

| | Notebook (`.ipynb`) | Script (`.py`) |
|---|---|---|
| A cosa serve | esplorare: provare, guardare, correggere | rifare: ottenere sempre lo stesso risultato |
| Ordine di esecuzione | quello in cui lanci le celle | sempre dall'inizio alla fine |
| Memoria | ricorda tutto quello che hai eseguito prima | parte ogni volta da zero |
| Formato | testo + codice + risultati | solo testo |

Si esplora nel notebook, si consegna lo script.

## Il notebook ricorda

```python
capitale = 1000              # cella A
capitale = capitale * 1.1    # cella B
print(capitale)              # cella C
```

Eseguendo A, B, C si ottiene 1100. Eseguendo A, poi B tre volte, poi C, si ottiene 1331. Dopo un riavvio, eseguendo solo C si ottiene un errore. Stesso codice, risultati diversi: dipende dalla **storia** delle esecuzioni, che non è scritta da nessuna parte.

I numeri tra parentesi quadre accanto alle celle (`[1]`, `[2]`, ...) dicono in che ordine sono state eseguite. Prima di condividere un notebook, il test minimo è **Runtime → Riavvia ed esegui tutto**: se arriva in fondo senza errori e con gli stessi risultati, va bene.

## Uno script in Colab

```python
%%writefile analisi.py
import pandas as pd
df = pd.read_excel(URL)
print(df.shape)
```

- `%%writefile nome.py` all'inizio della cella: **salva** il contenuto in un file, senza eseguirlo.
- `!python nome.py`: **esegue** il file, dall'inizio alla fine, in una sessione pulita.

Sul tuo computer lo script si scrive con un editor (per esempio VS Code) e si lancia dal terminale con `python analisi.py`.

In cima a ogni script vale la pena scrivere: chi l'ha scritto, quando, quali dati usa, cosa fa.

## Leggere il codice degli altri

Generare codice è facile, soprattutto con l'AI. Verificarlo è il mestiere. Per ogni script:
1. **Cosa dice**: il commento, il nome della funzione, la richiesta fatta.
2. **Cosa fa**: riga per riga. Filtri, confronti (`>` o `>=`?), funzioni di riepilogo (media o mediana?).
3. **Coincidono?** Se no, ha ragione il codice: è lui che produce i numeri.

Uno script che gira senza errori non è uno script giusto.

## Rifare un'analisi

Perché qualcun altro (o tu, tra un anno) possa rifare la tua analisi servono:
- **i dati**, o dove scaricarli e in che data;
- **lo script**, che parte da zero e arriva al risultato;
- **le librerie**, elencate in un file `requirements.txt` (si installano con `pip install -r requirements.txt`);
- **le decisioni** prese durante la pulizia, scritte.

Il repository di questo corso è un esempio: dati, codice e istruzioni nello stesso posto.

## Cosa abbiamo trovato

**L'ordine conta.** Con A, B, C si ottiene 1100.0; con A, poi B tre volte, poi C, si ottiene 1331.0; dopo un riavvio, C da sola dà `NameError`. Lo script invece, eseguito con `!python analisi.py`, dà sempre lo stesso risultato anche dopo un riavvio, perché contiene tutto quello che serve.

**Lo script di Gemini.** Due differenze tra commento e codice:
1. "almeno 10 addetti" vuol dire `>= 10`, ma il codice usa `> 10`: nel 2022 escludeva le 21 imprese con esattamente 10 addetti.
2. Il commento chiede il fatturato **mediano**, il codice calcola la **media** (`mean()`): per l'agroalimentare 6.451 invece di 2.580 migliaia di euro.

Lo script girava senza errori e dava numeri plausibili: i due sbagli si trovano solo leggendolo. Sono gli stessi concetti della L1 (gli operatori di confronto) e della L4 (media e mediana), in un caso reale.

**Le dipendenze.** Lo script usa `pandas` e, per leggere e scrivere i file Excel, `openpyxl`. Con un file `requirements.txt` che le elenca, un collega le installa con `pip install -r requirements.txt`.

## Compito a casa

- Lavora al mini-progetto finale (E4): scegli la domanda e i dati.

## Per approfondire

- [QuantEcon – Writing Good Code](https://python-programming.quantecon.org/writing_good_code.html): facoltativo, buone pratiche per scrivere codice leggibile

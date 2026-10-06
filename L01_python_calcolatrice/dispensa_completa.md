# L1 — Python come calcolatrice intelligente

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L01_python_calcolatrice/L01_task.ipynb)

## Cosa sai fare dopo questa lezione

- Aprire un notebook in Colab ed eseguire codice
- Chiedere codice a Gemini e leggerlo
- Creare variabili e fare calcoli
- Distinguere `=` (assegnare) da `==` (confrontare)
- Riconoscere i tipi di dato principali
- Leggere un messaggio di errore e cercarlo online

## Colab in breve

Colab è un ambiente per scrivere ed eseguire Python nel browser. Non serve installare nulla: basta un account Google.

Un **notebook** è fatto di celle:
- **celle di codice** (grigie): si eseguono con **Shift + Invio**;
- **celle di testo**: spiegazioni e istruzioni.

Le celle si eseguono nell'ordine in cui le lanci, non nell'ordine in cui compaiono. Se qualcosa si comporta in modo strano, prova **Runtime → Riavvia ed esegui tutto**.

Per salvare il tuo lavoro: **File → Salva una copia in Drive**.

## Variabili

Una variabile è un'etichetta attaccata a un valore.

```python
capitale = 5000
tasso = 0.025
montante = capitale * (1 + tasso) ** 10
```

Il simbolo `=` non significa "uguale" come in matematica: significa "metti questo valore in questa etichetta".

### `=` e `==`

| Simbolo | Nome | Cosa fa | Esempio | Risultato |
|---|---|---|---|---|
| `=` | assegnazione | **mette** un valore in una variabile (un ordine) | `prezzo = 12.5` | nessuno: ora `prezzo` vale 12.5 |
| `==` | confronto | **chiede** se due cose sono uguali (una domanda) | `prezzo == 12.5` | `True` |

Altri confronti: `>` maggiore, `<` minore, `>=` maggiore o uguale, `<=` minore o uguale, `!=` diverso. Rispondono sempre `True` o `False`, cioè un valore di tipo `bool`.

**Attenzione:** scambiare `=` con `==` non dà errore. Scrivere `prezzo = 13` quando volevi chiedere `prezzo == 13` cambia il valore di `prezzo` in silenzio.

## Tipi di dato

| Tipo | Esempio | Cos'è |
|---|---|---|
| `int` | `5000` | numero intero |
| `float` | `0.025` | numero decimale |
| `str` | `"5000"` | testo (stringa), sempre tra virgolette |
| `bool` | `True`, `False` | vero o falso |

Per sapere il tipo di una variabile: `type(capitale)`.

**Attenzione:** in Python i decimali si scrivono con il punto (`0.025`), non con la virgola.

Lo stesso simbolo fa cose diverse a seconda del tipo:

```python
5000 * 2      # 10000
"5000" * 2    # "50005000"  <- ripete il testo!
```

Per convertire: `int("5000")`, `float("0.025")`, `str(5000)`.

## Operazioni utili

| Operazione | Simbolo | Esempio |
|---|---|---|
| somma, differenza | `+` `-` | `5000 + 125` |
| prodotto, divisione | `*` `/` | `5000 * 0.025` |
| potenza | `**` | `1.025 ** 10` |
| arrotondamento | `round()` | `round(6400.4227, 2)` |

## Stampare

```python
print(montante)
print(f"Dopo 10 anni Marco avrà {montante} euro")
```

La `f` prima delle virgolette (f-string) permette di inserire variabili nel testo con le `{}`.

## Gli errori

Quando qualcosa va storto, Python mostra un messaggio. **L'ultima riga è la più importante**: dice il tipo di errore e la causa.

```
TypeError: can only concatenate str (not "int") to str
```

Cosa fare:
1. Leggi l'ultima riga.
2. Copiala così com'è su Google.
3. Quasi sempre qualcuno ha già avuto lo stesso problema.

**Ma attenzione:** gli errori peggiori sono quelli che *non* danno messaggi. Il codice gira, il risultato è sbagliato. Verifica sempre che il risultato abbia senso.

## Lavorare con Gemini

- Chiedi in modo preciso: cosa hai, cosa vuoi ottenere.
- Leggi il codice che ti propone: capisci cosa fa ogni riga?
- Verifica il risultato: è plausibile?
- Se qualcosa non ti è chiaro, chiedi a Gemini di spiegarlo.

## Compito a casa

- [Kaggle Learn – Python](https://www.kaggle.com/learn/python), lezione **Hello, Python** (~30 min, serve un account gratuito)

## Per approfondire

- [W3Schools – Python](https://www.w3schools.com/python/): prontuario da consultare
- [QuantEcon – Python Programming for Economics and Finance](https://python-programming.quantecon.org/intro.html): facoltativo, per chi vuole andare oltre

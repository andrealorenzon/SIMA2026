# L1 — Python come calcolatrice intelligente

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L01_python_calcolatrice/L01_task.ipynb)

## Cosa sai fare dopo questa lezione

- Aprire un notebook in Colab ed eseguire codice
- Chiedere codice a Gemini e leggerlo
- Creare variabili e fare calcoli
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
prezzo = 12.5
quantita = 40
ricavo = prezzo * quantita
```

Il simbolo `=` non significa "uguale" come in matematica: significa "metti questo valore in questa etichetta".

## Tipi di dato

| Tipo | Esempio | Cos'è |
|---|---|---|
| `int` | `40` | numero intero |
| `float` | `12.5` | numero decimale |
| `str` | `"Milano"` | testo (stringa), sempre tra virgolette |
| `bool` | `True`, `False` | vero o falso |

Per sapere il tipo di una variabile: `type(prezzo)`.

**Attenzione:** in Python i decimali si scrivono con il punto (`12.5`), non con la virgola.

Python tratta i tipi in modo diverso, e lo stesso simbolo può fare cose diverse a seconda del tipo. Nel task lo scoprirai da solo.

## Operazioni utili

| Operazione | Simbolo |
|---|---|
| somma, differenza | `+` `-` |
| prodotto, divisione | `*` `/` |
| potenza | `**` |
| arrotondamento | `round()` |

## Stampare

```python
print(ricavo)
```

Per inserire una variabile dentro una frase esiste un modo comodo: cerca **f-string**.

## Gli errori

Quando qualcosa va storto, Python mostra un messaggio. **L'ultima riga è la più importante**: dice il tipo di errore e la causa.

```
NameError: name 'ricavi' is not defined
```

(Qui la variabile si chiamava `ricavo`, non `ricavi`.)

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

## 🎯 Sfida

Nel task ci sono **due trappole**: una dà un errore, l'altra no. Trovale e spiega perché succedono.

Le soluzioni sono disponibili dopo la lezione, ma leggerle prima ti toglie l'unica cosa che conta: arrivarci da solo.

## Compito a casa

- [Kaggle Learn – Python](https://www.kaggle.com/learn/python), lezione **Hello, Python** (~30 min, serve un account gratuito)

## Per approfondire

- [W3Schools – Python](https://www.w3schools.com/python/): prontuario da consultare
- [QuantEcon – Python Programming for Economics and Finance](https://python-programming.quantecon.org/intro.html): facoltativo, per chi vuole andare oltre

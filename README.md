# Informatica per economisti — SIMA 2026

Corso pratico di Python per dottorandi di economia. 16 ore di lezione + 8 di esercitazione, da novembre a gennaio.

Non serve nessuna esperienza di programmazione. Si lavora su **Google Colab** (nel browser, niente da installare) con l'aiuto di **Gemini**, l'assistente AI integrato.

## Come si lavora

Ogni incontro dura circa 2 ore:

1. **Spiegazione e demo**: come si fa
2. **Task**: un notebook a piccoli passi. Per ogni passo trovi cosa cercare su Google; Gemini è a disposizione
3. **Debrief**: come ha funzionato, e i concetti dietro il codice che hai scritto

Si lavora in **gruppi da 3**, con tre ruoli che ruotano a ogni passo: chi **scrive** (condivide lo schermo e scrive il codice), chi **cerca** (Google, Gemini, dispense), chi **controlla** (il risultato ha senso? il numero torna?).

L'obiettivo non è imparare tutto a memoria, ma saper cercare quello che serve e **verificare** che il codice (anche quello scritto dall'AI) faccia davvero ciò che deve.

## Prima del corso

Un mini tutorial da fare da soli, prima della prima lezione (circa 20 minuti): come usare Gemini in Colab, e come non fidarsi troppo.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/preparazione/00_gemini_colab.ipynb) [`preparazione/00_gemini_colab.ipynb`](preparazione/00_gemini_colab.ipynb)

## Le soluzioni

Le soluzioni di ogni lezione (notebook risolti, risposte, slide del debrief) sono in un'area separata, raggiungibile dal link **soluzioni** nella tabella del programma.

Sono lì per dopo la lezione. Leggerle prima ti toglie l'unica cosa che conta: arrivarci da solo.

## Cosa ti serve

- Un account Google (per Colab)
- Un account Kaggle gratuito (per i compiti a casa), da creare alla prima lezione

## Come aprire un notebook

Clicca il pulsante **Open in Colab** della lezione. Il notebook si apre nel browser.
Per salvare il tuo lavoro: **File → Salva una copia in Drive**.

## Programma

| Sett. | Incontro | Argomento | Materiali |
|---|---|---|---|
| 1 | L1 | Colab, Gemini, variabili e tipi, leggere un errore | [dispensa](lezioni/L01_python_calcolatrice/dispensa.md) · slide [pdf](lezioni/L01_python_calcolatrice/slide.pdf) / [pptx](lezioni/L01_python_calcolatrice/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L01_python_calcolatrice/L01_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L01_python_calcolatrice) |
| 1 | L2 | Caricare un file Excel, il DataFrame, ispezionare i dati | [dispensa](lezioni/L02_conosci_il_dataset/dispensa.md) · slide [pdf](lezioni/L02_conosci_il_dataset/slide.pdf) / [pptx](lezioni/L02_conosci_il_dataset/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L02_conosci_il_dataset/L02_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L02_conosci_il_dataset) |
| 2 | L3 | Pulizia dei dati e verifica | [dispensa](lezioni/L03_pulizia/dispensa.md) · slide [pdf](lezioni/L03_pulizia/slide.pdf) / [pptx](lezioni/L03_pulizia/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L03_pulizia/L03_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L03_pulizia) |
| 2 | E1 | Esercitazione: pulizia | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/esercitazioni/E1_pulizia/E1_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/E1_pulizia) |
| 3 | L4 | Raggruppare, riassumere, grafici | [dispensa](lezioni/L04_raggruppare/dispensa.md) · slide [pdf](lezioni/L04_raggruppare/slide.pdf) / [pptx](lezioni/L04_raggruppare/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L04_raggruppare/L04_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L04_raggruppare) |
| 3 | L5 | Unire tabelle | [dispensa](lezioni/L05_unire/dispensa.md) · slide [pdf](lezioni/L05_unire/slide.pdf) / [pptx](lezioni/L05_unire/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L05_unire/L05_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L05_unire) |
| 4 | E2 | Esercitazione: innovazione, ESG e performance | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/esercitazioni/E2_descrittive_unione/E2_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/E2_descrittive_unione) |
| 5 | L6 | Funzioni e cicli: automatizzare | [dispensa](lezioni/L06_funzioni_cicli/dispensa.md) · slide [pdf](lezioni/L06_funzioni_cicli/slide.pdf) / [pptx](lezioni/L06_funzioni_cicli/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L06_funzioni_cicli/L06_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L06_funzioni_cicli) |
| 5 | L7 | Dati da internet e una regressione | [dispensa](lezioni/L07_internet_regressione/dispensa.md) · slide [pdf](lezioni/L07_internet_regressione/slide.pdf) / [pptx](lezioni/L07_internet_regressione/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L07_internet_regressione/L07_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L07_internet_regressione) |
| 6 | E3 | Esercitazione: automatizzare l'analisi delle recensioni | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/esercitazioni/E3_automazione/E3_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/E3_automazione) |
| 6 | L8 | Dal notebook allo script `.py` | [dispensa](lezioni/L08_script/dispensa.md) · slide [pdf](lezioni/L08_script/slide.pdf) / [pptx](lezioni/L08_script/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L08_script/L08_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L08_script) |
| gennaio | E4 | Mini-progetto finale: lavoro a casa in gruppi da 3, poi la presentazione | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/esercitazioni/E4_progetto/E4_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/E4_progetto) |

## In cosa consiste ogni incontro

**L1 — Python come calcolatrice.** Primo contatto con Colab e Gemini. Variabili, numeri e testo, confronti (`=` e `==`), leggere un messaggio di errore. Il caso: quanto rendono 5.000 € investiti al 2,5%.

**L2 — Conosci il dataset.** Si carica un file Excel di 500 imprese italiane e si impara a guardarlo: dimensioni, tipi di dati, selezionare righe e colonne (lo slicing, `iloc`). Non si corregge niente: si prende nota di cosa non torna.

**L3 — Pulizia.** Si correggono i problemi trovati nella L2: duplicati, numeri scritti come testo, regioni scritte in più modi, valori impossibili o mancanti. La regola: dopo ogni correzione, si verifica.

**E1 — Esercitazione: pulizia.** Le stesse tecniche su un file nuovo, le esportazioni di un'azienda alimentare, con meno indicazioni.

**L4 — Raggruppare e disegnare.** Le prime domande da economisti: fatturato per anno, per regione, per settore. Media e mediana, quante osservazioni ci sono dietro un numero, i primi grafici.

**L5 — Unire tabelle.** Si aggiungono alle imprese le informazioni sulle regioni, come con `CERCA.VERT` in Excel. Dopo ogni unione si contano le righe: chi è sparito, e perché?

**E2 — Esercitazione: innovazione, ESG e performance.** Due domande di management: le imprese che investono di più in ricerca e sviluppo sono più produttive? Quelle con un punteggio ESG più alto vanno meglio? Si uniscono i dati, si confrontano i gruppi e si distingue un'associazione da un effetto.

**L6 — Funzioni e cicli.** Venti file, uno per regione: si scrive il procedimento una volta (una funzione) e lo si ripete su tutti (un ciclo).

**L7 — Dati da internet e una regressione.** Dati veri sulle emissioni di CO₂ e sul PIL di tutti i paesi, scaricati da Our World in Data. Una prima regressione, letta con attenzione: su quante osservazioni è stimata, e cosa non dice.

**E3 — Esercitazione: automatizzare l'analisi delle recensioni.** Una domanda di marketing: cosa apprezzano e cosa criticano i clienti di quattro marche? Una funzione e un ciclo contano le parole in centinaia di recensioni; poi alcune si leggono, per capire cosa vogliono dire.

**L8 — Dal notebook allo script.** Un'analisi che deve essere rifatta va messa in uno script `.py`, che gira da zero. Si impara anche a leggere, e a correggere, il codice scritto da Gemini. Si assegna il mini-progetto.

**E4 — Mini-progetto finale.** Un lavoro a casa, in gruppi da 3: una domanda, dei dati, un'analisi verificata, un grafico e uno script. Le tracce sono di management (innovazione, ESG) e di marketing (recensioni, un esperimento sui messaggi pubblicitari), oppure una domanda vostra. All'ultimo incontro ogni gruppo presenta il suo lavoro.

## Dati

La cartella [`dati/`](dati/) contiene i dataset sintetici usati nel corso:

- `imprese.xlsx`: 500 imprese italiane osservate dal 2019 al 2023, così come arrivano (da pulire)
- `imprese_pulito.xlsx`: lo stesso dataset dopo la pulizia della L3
- `per_regione/`: un file per regione (L6)
- `regioni.xlsx`: informazioni sulle regioni italiane
- `esportazioni.xlsx`: esportazioni di un'azienda immaginaria (E1)
- `esg.xlsx`: punteggio ESG delle imprese (E2, mini-progetto)
- `recensioni/`: recensioni online di quattro marche di caffè in capsule (E3, mini-progetto)
- `esperimento.xlsx`: un esperimento sui messaggi pubblicitari (mini-progetto)

La descrizione delle colonne è in [`dati/README.md`](dati/README.md).

I dati sono **inventati** e servono solo a scopo didattico.

Per caricarli in Colab senza scaricare nulla:

```python
import pandas as pd
url = "https://raw.githubusercontent.com/andrealorenzon/SIMA2026/main/dati/imprese.xlsx"
df = pd.read_excel(url)
```

## Risorse

- [Kaggle Learn – Python](https://www.kaggle.com/learn/python) e [Pandas](https://www.kaggle.com/learn/pandas): compiti a casa
- [W3Schools – Python](https://www.w3schools.com/python/): prontuario da consultare
- [QuantEcon](https://python-programming.quantecon.org/intro.html): approfondimenti facoltativi, Python per economisti

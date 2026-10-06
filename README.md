# Informatica per economisti — SIMA 2026

Corso pratico di Python per dottorandi di economia. 16 ore di lezione + 8 di esercitazione, in sei settimane.

Non serve nessuna esperienza di programmazione. Si lavora su **Google Colab** (nel browser, niente da installare) con l'aiuto di **Gemini**, l'assistente AI integrato.

## Come si lavora

Ogni incontro dura circa 2 ore:

1. **Spiegazione e demo**: come si fa
2. **Task**: un notebook a piccoli passi. Per ogni passo trovi cosa cercare su Google; Gemini è a disposizione
3. **Debrief**: come ha funzionato, e i concetti dietro il codice che hai scritto

L'obiettivo non è imparare tutto a memoria, ma saper cercare quello che serve e **verificare** che il codice (anche quello scritto dall'AI) faccia davvero ciò che deve.

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
| 2 | E1 | Esercitazione: pulizia | in preparazione |
| 3 | L4 | Raggruppare, riassumere, grafici | [dispensa](lezioni/L04_raggruppare/dispensa.md) · slide [pdf](lezioni/L04_raggruppare/slide.pdf) / [pptx](lezioni/L04_raggruppare/slide.pptx) · [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L04_raggruppare/L04_task.ipynb) · [soluzioni](https://github.com/andrealorenzon/SIMA2026/tree/soluzioni/L04_raggruppare) |
| 3 | L5 | Unire tabelle | in preparazione |
| 4 | E2 | Esercitazione: descrittive e unione | in preparazione |
| 4 | L6 | Funzioni e cicli: automatizzare | in preparazione |
| 5 | L7 | Dati da internet e una regressione | in preparazione |
| 5 | E3 | Esercitazione: automazione | in preparazione |
| 6 | L8 | Dal notebook allo script `.py` | in preparazione |
| 6 | E4 | Mini-progetto finale | in preparazione |

## Dati

La cartella [`dati/`](dati/) contiene i dataset sintetici usati nel corso:

- `imprese.xlsx`: 500 imprese italiane osservate dal 2019 al 2023
- `regioni.xlsx`: informazioni sulle regioni italiane

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

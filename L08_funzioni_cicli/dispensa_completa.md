# L8 — Funzioni e cicli: automatizzare

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L08_funzioni_cicli/L08_task.ipynb)

## Cosa sai fare dopo questa lezione

- Scrivere una funzione e usarla più volte
- Ripetere un'operazione con un ciclo `for`
- Far decidere al codice con `if` / `else`
- Capire cosa fa parte di un blocco, e leggere un `IndentationError`
- Elaborare tutti i file di una cartella
- Capire su quale file si ferma un ciclo, e perché

## Funzioni

Una funzione è una **ricetta**: le dai un nome, degli ingredienti (i parametri), e lei restituisce un risultato.

```python
def ricavo(prezzo, quantita):
    totale = prezzo * quantita
    return totale

ricavo(12.5, 40)     # 500.0
```

- `def` definisce la funzione; tra parentesi i **parametri**.
- Il **rientro** (4 spazi) indica cosa fa parte della funzione.
- `return` è il risultato. Una funzione senza `return` restituisce `None`, cioè niente: errore frequente.

Perché usarle: scrivi il procedimento una volta e lo riusi; se c'è un errore, lo correggi in un punto solo.

Un parametro può avere un **valore predefinito**, usato quando non lo indichi:

```python
def riepilogo(percorso, anno=None):
    ...
```

## Cicli

Un ciclo `for` ripete le stesse istruzioni per ogni elemento di una sequenza:

```python
for citta in ["Milano", "Roma", "Napoli"]:
    print(citta.upper())
```

Si legge: "per ogni città nella lista, stampala in maiuscolo". La variabile `citta` cambia valore a ogni giro. Anche qui è il rientro a dire cosa si ripete.

Per raccogliere i risultati, si parte da una lista vuota e si aggiunge un elemento a ogni giro:

```python
risultati = []
for f in file:
    risultati.append(riepilogo(f))
tab = pd.DataFrame(risultati)     # una lista di dizionari diventa una tabella
```

## Decidere: `if`

`if` esegue delle istruzioni **solo se** una condizione è vera. La condizione è un confronto come quelli della L1, che risponde `True` o `False`.

```python
imprese = 4
if imprese < 10:
    nota = "poco affidabile"
elif imprese < 30:
    nota = "da usare con cautela"
else:
    nota = "ok"
print(nota)       # poco affidabile
```

- Dopo la condizione ci vogliono i **due punti**, e le istruzioni vanno **rientrate**, come nelle funzioni e nei cicli.
- `elif` ("altrimenti, se…") ed `else` ("in tutti gli altri casi") sono facoltativi. Python controlla le condizioni in ordine e si ferma alla prima vera.

**`if` decide su un solo valore.** Per scegliere delle righe di una tabella non si usa `if` ma un filtro (L2, L3): `df[df["addetti"] < 10]`. Scrivere `if df["addetti"] < 10:` dà l'errore *The truth value of a Series is ambiguous*: Python non sa se intendi "tutte le righe" o "almeno una".

## Blocchi e rientro: la regola generale

Funzioni, cicli e `if` seguono la stessa regola: la riga che li apre finisce con i **due punti** (`:`), e le istruzioni che ne fanno parte sono **rientrate** di 4 spazi. Il blocco finisce alla prima riga che torna a sinistra.

```python
for f in file:
    d = pd.read_excel(f)        # dentro il ciclo: si ripete
    print(f.stem)               # dentro il ciclo: si ripete
print("fatto")                  # fuori dal ciclo: una volta sola, alla fine
```

I blocchi si possono mettere uno dentro l'altro: un `if` dentro un ciclo si rientra di altri 4 spazi.

```python
for f in file:
    d = pd.read_excel(f)
    if len(d) < 10:
        print(f.stem, "poco affidabile")
```

- In Colab il tasto **Tab** inserisce 4 spazi (Shift + Tab li toglie), e dopo i due punti Colab rientra da solo la riga successiva.
- Se il rientro è sbagliato, Python si ferma con `IndentationError` (rientro mancante o inatteso). Guarda la riga indicata e quella sopra: spesso mancano i due punti, o una riga è spostata di uno spazio.
- **Dentro le parentesi il rientro non conta.** Quando un comando lungo va a capo, come un `agg` o un dizionario, il rientro serve solo a leggere meglio: Python lo ignora finché la parentesi non si chiude.

```python
tab = df.groupby("regione").agg(
    imprese=("id_impresa", "nunique"),
    fatturato=("fatturato", "median"),
)
```

## Lavorare con i file di una cartella

```python
from pathlib import Path

cartella = Path("SIMA2026/dati/per_regione")
file = sorted(cartella.glob("*.xlsx"))     # tutti i file Excel, in ordine
for f in file:
    print(f.name, f.stem)                   # "Lazio.xlsx", "Lazio"
```

Con i percorsi la barra `/` non divide: **unisce** la cartella e il nome del file. `cartella / "Lazio.xlsx"` dà `SIMA2026/dati/per_regione/Lazio.xlsx`.

In Colab, per avere i file del corso:

```python
![ -d SIMA2026 ] || git clone -q --depth 1 https://github.com/andrealorenzon/SIMA2026.git   # solo se la cartella manca
```

I file compaiono nel pannello a sinistra (icona della cartella). Il `!` all'inizio dice a Colab di eseguire un comando del sistema, non Python.

## Dizionari (ripasso dalla L3)

Un **dizionario** associa delle chiavi a dei valori, tra parentesi graffe:

```python
r = {"regione": "Lazio", "imprese": 55}
r["imprese"]       # 55
```

È il modo comodo per far restituire più risultati a una funzione. Una lista di dizionari con le stesse chiavi diventa una tabella con `pd.DataFrame(...)`.

## Quando un ciclo si ferma

Se un ciclo si ferma con un errore, devi capire **su quale elemento**. Il trucco più semplice: stampare il nome dell'elemento all'inizio di ogni giro. L'ultimo nome stampato è quello che ha dato problemi. Poi apri quel file e guardalo: cosa ha di diverso dagli altri?

Un errore che ferma il ciclo è una buona notizia: ti sta dicendo che un file non è come pensavi.

## Cosa abbiamo trovato

**Il file diverso.** Il ciclo si ferma sul Molise con `KeyError: 'fatturato'`: in `Molise.xlsx` la colonna si chiama `Fatturato`, con la maiuscola. Stampando il nome del file all'inizio di ogni giro, l'ultimo nome stampato prima dell'errore è il colpevole.

**La correzione.** Appena letto il file, si portano tutti i nomi delle colonne in minuscolo:

```python
df.columns = df.columns.str.lower()
```

Così la funzione regge anche file scritti in modo leggermente diverso, e il ciclo elabora tutti i 20 file.

**Perché è una buona notizia.** In Excel avremmo cliccato sulla colonna giusta senza accorgerci di niente. Il codice si è fermato e ce l'ha detto: meglio un errore che un risultato sbagliato. Nel bonus B2, senza la correzione, `concat` avrebbe creato due colonne separate (`fatturato` e `Fatturato`), piene di valori mancanti.

## Compito a casa

- [Kaggle Learn – Python](https://www.kaggle.com/learn/python), lezioni **Functions and Getting Help** e **Loops and List Comprehensions** (~40 min)

## Per approfondire

- [W3Schools – Funzioni](https://www.w3schools.com/python/python_functions.asp) e [cicli for](https://www.w3schools.com/python/python_for_loops.asp): prontuario
- [QuantEcon – Functions](https://python-programming.quantecon.org/functions.html): facoltativo

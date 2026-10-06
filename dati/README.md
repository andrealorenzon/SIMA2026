# Dati del corso

Dataset **sintetici** (inventati), creati per il corso. Non rappresentano imprese reali.

## imprese.xlsx

Imprese italiane osservate ogni anno dal 2019 al 2023 (una riga per impresa e anno).

| Colonna | Descrizione |
|---|---|
| `id_impresa` | codice identificativo dell'impresa |
| `ragione_sociale` | nome dell'impresa |
| `regione` | regione della sede |
| `settore` | settore di attività |
| `data_costituzione` | data di costituzione |
| `anno` | anno di osservazione |
| `addetti` | numero di dipendenti |
| `fatturato` | fatturato, in migliaia di euro |
| `spesa_rs` | spesa in ricerca e sviluppo, in migliaia di euro |

Il file arriva "come da un collega": prima di usarlo, controllalo.

## imprese_pulito.xlsx

Lo stesso dataset dopo la pulizia della L3 (2.500 righe, 20 regioni, fatturato numerico). Si usa dalla L4 in poi.

## per_regione/

Un file Excel per ogni regione, con le stesse colonne di `imprese_pulito.xlsx` (tranne `regione`, che è nel nome del file). Si usa nella L6 e nell'esercitazione E3.

## esportazioni.xlsx

Esportazioni mensili (2022-2023) di un'azienda alimentare immaginaria, per paese e prodotto. Si usa nell'esercitazione E1. Anche questo arriva "come da un collega".

| Colonna | Descrizione |
|---|---|
| `mese` | mese e anno |
| `paese` | paese di destinazione |
| `prodotto` | prodotto esportato |
| `quantita` | unità vendute (negative: resi) |
| `valore` | valore in euro |

## regioni.xlsx

| Colonna | Descrizione |
|---|---|
| `regione` | nome della regione |
| `macroarea` | Nord-Ovest, Nord-Est, Centro, Sud, Isole |
| `popolazione_migliaia` | popolazione residente, in migliaia (valori indicativi) |

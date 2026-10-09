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

Un file Excel per ogni regione, con le stesse colonne di `imprese_pulito.xlsx` (tranne `regione`, che è nel nome del file). Si usa nella L6.

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

## esg.xlsx

Punteggio ESG (ambiente, società, governance) delle imprese di `imprese.xlsx`, una riga per impresa. Si usa nell'esercitazione E2 e nel mini-progetto.

| Colonna | Descrizione |
|---|---|
| `id_impresa` | codice identificativo dell'impresa (lo stesso di `imprese.xlsx`) |
| `punteggio_esg` | punteggio da 0 a 100; vuoto se l'impresa non è stata valutata |

## recensioni/

Recensioni online di quattro marche immaginarie di caffè in capsule, un file per marca (il nome del file è la marca). Si usa nell'esercitazione E3 e nel mini-progetto.

| Colonna | Descrizione |
|---|---|
| `data` | data della recensione |
| `voto` | da 1 (pessimo) a 5 (ottimo) |
| `cliente` | `nuovo` (primo acquisto) o `abituale` |
| `testo` | il testo della recensione |

## esperimento.xlsx

Un esperimento online: a ogni partecipante è stato mostrato, **a caso**, un annuncio dello stesso prodotto centrato sul risparmio o sull'impatto ambientale. Poi ha indicato quanto è probabile che lo compri. Si usa nel mini-progetto.

| Colonna | Descrizione |
|---|---|
| `id` | codice del partecipante |
| `condizione` | messaggio visto: `risparmio` o `ambiente` |
| `eta` | età in anni |
| `cliente_abituale` | `sì` se compra già prodotti della marca |
| `attenzione_ok` | `False` se il partecipante ha sbagliato la domanda di controllo dell'attenzione: le sue risposte non sono affidabili |
| `intenzione_acquisto` | da 1 (sicuramente no) a 7 (sicuramente sì) |


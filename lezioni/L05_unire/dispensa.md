# L5 — Unire tabelle

[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/andrealorenzon/SIMA2026/blob/main/lezioni/L05_unire/L05_task.ipynb)

## Cosa sai fare dopo questa lezione

- Unire due tabelle che hanno una colonna in comune
- Scegliere quali righe tenere (`inner` o `left`)
- Accorgerti quando un'unione perde o duplica righe
- Mettere in fila due tabelle con le stesse colonne

## Unire: `merge`

Spesso le informazioni che ti servono sono in tabelle diverse: le imprese in una, i dati sulle regioni in un'altra. `merge` le affianca usando una colonna in comune, la **chiave**. È come `CERCA.VERT` di Excel, applicato a tutte le righe insieme.

```python
unito = df.merge(regioni, on="regione", how="left")
```

- `on`: la colonna chiave, presente in entrambe le tabelle;
- `how`: quali righe tenere.

Le informazioni della seconda tabella vengono **copiate** su ogni riga corrispondente della prima: la macroarea del Lazio compare su ogni riga di ogni impresa del Lazio.

**La chiave deve essere scritta in modo identico** nelle due tabelle: maiuscole, spazi, trattini. Per Python `"Emilia-Romagna"` e `"Emilia Romagna"` sono due regioni diverse.

## Quali righe restano: `how`

| `how` | Cosa tiene | Cosa succede alle righe senza corrispondenza |
|---|---|---|
| `"inner"` (predefinito) | solo le righe presenti in entrambe | **spariscono**, senza avvisare |
| `"left"` | tutte le righe della tabella di sinistra | restano, con valori mancanti nelle colonne aggiunte |
| `"outer"` | tutte le righe di entrambe | restano, con valori mancanti dove serve |

Quando arricchisci una tabella con informazioni di un'altra, `how="left"` è quasi sempre la scelta giusta: la tabella principale non deve perdere righe.

Per vedere chi non ha trovato corrispondenza:

```python
prova = df.merge(regioni, on="regione", how="left", indicator=True)
prova["_merge"].value_counts()      # both, left_only, right_only
```

## La regola: conta le righe

Un'unione sbagliata quasi mai dà errore. Quindi:

```python
print(df.shape)
unito = df.merge(regioni, on="regione", how="left")
print(unito.shape)                       # deve essere uguale
print(unito["macroarea"].isna().sum())   # deve essere 0
```

- **Meno righe** (con `inner`): alcune chiavi non combaciano.
- **Più righe**: nella seconda tabella una chiave compare più volte, e le righe vengono duplicate. Per controllarlo in automatico: `validate="many_to_one"`.
- **Valori mancanti nelle colonne aggiunte** (con `left`): alcune chiavi non combaciano.

## Attenzione a cosa sommi

Dopo un'unione, i valori della tabella piccola sono **ripetuti** su molte righe. Se sommi una colonna come la popolazione dopo averla unita alle imprese, la conti tante volte quante sono le imprese. Regola: prima **aggrega** (una riga per regione), poi **unisci**.

```python
conteggi = df.groupby("regione")["id_impresa"].nunique().reset_index(name="imprese")
tab = conteggi.merge(regioni, on="regione", how="left")
```

## Mettere in fila: `concat`

Per mettere **una sotto l'altra** due tabelle con le stesse colonne (per esempio due anni, o due file con la stessa struttura):

```python
insieme = pd.concat([tabella_2022, tabella_2023])
```

`merge` affianca colonne, `concat` impila righe.

## 🎯 Sfida

La prima unione che farai perderà delle righe, senza nessun errore. Trova quante, e quali. Poi calcola quanti italiani ci sono: il numero che otterrai la prima volta potrebbe sorprenderti.

Le soluzioni sono disponibili dopo la lezione, ma leggerle prima ti toglie l'unica cosa che conta: arrivarci da solo.

## Compito a casa

- [Kaggle Learn – Pandas](https://www.kaggle.com/learn/pandas), lezione **Renaming and Combining** (~20 min)

## Per approfondire

- [W3Schools – Pandas](https://www.w3schools.com/python/pandas/default.asp): prontuario
- [Documentazione di pandas – merge](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html): tutti i parametri, con esempi in fondo

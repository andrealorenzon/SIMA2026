---
marp: true
theme: default
paginate: true
title: L1 — Python come calcolatrice intelligente
---

# L1 — Python come calcolatrice intelligente

Informatica per economisti · SIMA 2026

---

## Oggi

1. Cos'è un programma
2. Colab: il nostro ambiente di lavoro
3. Gemini: l'assistente
4. Gli errori (sono amici)
5. **Task**: il risparmio di Marco
6. Debrief

---

## Cos'è un programma

Una lista di **istruzioni**, eseguite **in ordine**, una dopo l'altra.

```python
capitale = 5000
tasso = 0.025
print(capitale * (1 + tasso))
```

Il computer non "capisce": esegue. Esattamente quello che scrivi.

---

## Colab

- Python nel browser, gratis, niente da installare
- Serve solo un account Google
- Un **notebook** = celle di testo + celle di codice
- **Shift + Invio** esegue la cella

> Demo: apriamo il notebook dal pulsante "Open in Colab" nel README

---

## Gemini in Colab

- Il pulsante ✨ apre l'assistente
- Gli chiedi cosa vuoi, lui scrive codice

> Demo: *"calcola l'interesse composto su 1000 euro al 3% per 10 anni"*

**Regola del corso:** il codice generato si **legge** e si **verifica**.
Che giri non vuol dire che sia giusto.

---

## Gli errori

```python
print(capitale
```

```
SyntaxError: '(' was never closed
```

- L'**ultima riga** dice cosa non va
- Copiala su Google: qualcuno ha già avuto lo stesso problema

> Demo: cerchiamo l'errore insieme

---

## Come si lavora nel task

- Passi piccoli, uno alla volta
- Per ogni passo: 🔎 **cosa cercare** su Google
- Gemini disponibile, ma prima prova a capire cosa ti serve
- Bloccato da più di 10 minuti? Chiedi

**Saper cercare** è metà del mestiere di programmare.

---

<!-- _class: lead -->

# Task: il risparmio di Marco

60 minuti

---

<!-- _class: lead -->

# Debrief

---

## Variabili

```python
capitale = 5000
```

- Un'**etichetta** attaccata a un valore
- Puoi cambiarle il valore quando vuoi
- Il nome lo scegli tu: meglio se dice cosa contiene

---

## Tipi

| Tipo | Esempio | Cos'è |
|---|---|---|
| `int` | `5000` | numero intero |
| `float` | `0.025` | numero decimale |
| `str` | `"5000"` | testo |
| `bool` | `True` | vero/falso |

`type(x)` ti dice il tipo di `x`.

⚠️ In Python i decimali si scrivono con il **punto**: `0.025`, non `0,025`.

---

## La trappola del passo 6

```python
capitale_testo = "5000"
print(capitale_testo * 2)
```

```
50005000
```

- Nessun errore, risultato **sbagliato**
- Python ha ripetuto il testo due volte

**Il codice che gira non è per forza giusto.**
È la lezione più importante del corso.

---

## Il passo 8

```python
print("Il capitale è " + capitale)
```

```
TypeError: can only concatenate str (not "int") to str
```

- Testo + numero: Python non sa cosa fare
- Soluzione: `str(capitale)`, oppure una f-string

```python
print(f"Il capitale è {capitale}")
```

---

## Prossima volta

I numeri arriveranno da un **file Excel**.
E il problema dei tipi tornerà fuori.

**Compito a casa:** Kaggle Learn – Python, lezione *Hello, Python* (~30 min)

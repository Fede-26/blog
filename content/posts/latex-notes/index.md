---
title: "Prendere appunti in LaTeX"
date: 2023-10-22
categories: "Posts"
tags:
    - Uni
    - Latex
    - Lectures
langs: "Italian"
draft: true
---

# Introduzione

In questo post vorrei spiegare i miei metodi per prendere appunti delle mie lezioni universitarie.
Facendo un corso di laurea prettamente tecnico (*CdL informatica*), i miei appunti sono molto schematici e contengono quasi tutto il materiale che viene spiegato in aula.

In aula, se non per svolgere gli esercizi, utilizzo il mio pc per riscrivere dettagliatamente ciò che il prof dice.
Questo mi permette di automatizzare molto del lavoro richiesto per formattare decentemente i testi.

# Prima fase: Markdown

Per scrivere gli appunti in tempo reale utilizzo il formato di testo **Markdown**.
Esso permette di formattare il testo utilizzando degli speciali simboli (`*italics*`, `**bold**`, ...).

Per inserire equazioni e altri simboli matematici utilizzo una funzione integrata in molti editor markdown chiamata KaTeX.
Con questa posso inserire delle equazioni molto facilmente utilizzando una sintassi latex:

```latex
$$
2 + 2 = 4
$$
```
L'unica pecca mancante sono dei box colorati, molto utili per separare definizioni, dimostrazioni, esempi e osservazioni negli appunti di Analisi Matematica.
Per risolvere il problema ho trovato degli script che permettono di creare degli *environment* (spiegati più avanti) latex in markdown, utilizzando la sintassi:

```markdown
::: def

**Def:** questa è una definizione.

:::
```

Dopo aver finito la stesura degli appunti, procedo con la *compilazione*.

# Seconda fase: LaTeX

Per trasformare questi file markdown in pdf leggibili da chiunque, devono essere compilati.
Come compilatore utilizzo **pandoc**, un tool molto potente che permette di convertire praticamente qualsiasi documento (word, pdf, html, markdown) in qualunque altro formato.

Io lo utilizzo principalmente per convertire markdown -> latex -> pdf.

Durante la conversione è possibile utilizzare filtri e template per trasformare il documento a nostro piacimento.

Come template principale utilizzo **eisvogel** (#editing: add link).
Esso però non contiene tutte le mie preferenze e dunque aggiungo dei miei comandi tramite un file `header`.

## Header LaTeX

#editing: Add text from headers.

## Filters

#editing: Add text about filters

- Environment
- Auto date

# Terza fase: Publishing

Uso un makefile.
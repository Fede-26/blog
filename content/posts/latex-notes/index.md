---
title: Prendere appunti in LaTeX con Obsidian
date: 2024-03-02
categories: Posts
tags:
  - Uni
  - Latex
  - Lectures
langs: Italian
draft: true
---

# Introduzione

In questo post vorrei spiegare i miei metodi per prendere appunti delle mie lezioni universitarie.
Facendo un corso di laurea prettamente tecnico (*CdL informatica*), i miei appunti sono molto schematici e contengono quasi tutto il materiale che viene spiegato in aula.

In aula, se non per svolgere gli esercizi, utilizzo il mio pc per riscrivere dettagliatamente ciò che il prof dice.
Questo mi permette di automatizzare molto del lavoro richiesto per formattare decentemente i testi.

Come editor utilizzo obsidian perchè al momento è quello più funzioni supportate.

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
Per risolvere il problema ho trovato degli script che permettono di creare degli *environment* (spiegati più avanti) latex in markdown, utilizzando la sintassi delle [callouts](https://help.obsidian.md/Editing+and+formatting/Callouts) in obsidian:

```markdown
> [!def] **Definizione**:
>
> questa è una definizione.
>
```

In generale preferisco tenere gli appunti in markdown leggibili (su obsidian) e molto simili a quelli compilati, dunque tramite il plugin [eth-p/obsidian-callout-manager](https://github.com/eth-p/obsidian-callout-manager) ho creato degli equivalenti degli environment creati con colori simili.

Gli environment che uso principalmente sono:

- Teorema: `[!teo]`
- Esempio: `[!es]`
- Esercizio: `[!ese]`
- Dimostrazione: `[!dim]`
- Definizione: `[!def]`
- Lemma (usa `newlemma` come env): `[!lemma]`
- Osservazione: `[!oss]`
- Warning: `[!warn]`

Dopo aver finito la stesura degli appunti, procedo con la *compilazione*.

# Seconda fase: LaTeX

Per trasformare questi file markdown in pdf leggibili da chiunque, devono essere compilati.
Come compilatore utilizzo **pandoc**, un tool molto potente che permette di convertire praticamente qualsiasi documento (word, pdf, html, markdown) in qualunque altro formato.

Io lo utilizzo principalmente per convertire markdown -> latex -> pdf.

Durante la conversione è possibile utilizzare filtri e template per trasformare il documento a nostro piacimento.

Come template principale utilizzo [**enhuiz/eisvogel**](https://github.com/enhuiz/eisvogel).
Esso però non contiene tutte le mie preferenze e dunque aggiungo dei miei comandi tramite un file `header`.

## Header LaTeX

#editing: Add text from headers.

## Filters

#editing: Add text about filters

- Environment
- Auto date
- Callout

# Terza fase: Publishing

Uso uno script in python da me scritto per gestire tutti i file e gli output generati.
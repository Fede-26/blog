---
title: Appunti di Analisi I
author:
  - Federico Zotti
date: 2023-09-30
anno-accademico: "1"
subtitle: Analisi Matematica - Informatica - 23/24
langs: Italian
categories: Notes
tags:
	- "Analisi"
	- "Uni"
draft: false
---
{{< katex >}}

{{< button href="https://pdfs.7-bit.xyz/uni/Appunti-di-Analisi-I.pdf" target="_blank" >}}
PDF
{{< /button >}}


# Insiemi

## Notazione

Per *elenco*:
Prima operazione, poi insieme di partenza

$$
\begin{aligned}
A=& \{\,1,2,3,4,5\,\}\\
B=& \{\,n^2 \,|\, n  \text{ naturale}\,\}
\end{aligned}
$$

Per *proprietà*:
Prima insieme che scelgo, poi la proprietà che verifico

$$
C=\{\,n \text{ naturale} \,|\, n \text{ è un quadrato}\,\}
$$

Altri simboli:

$$
\begin{aligned}
\text{appartiene} \rightarrow &\; a \in A \\
\text{non appartiene} \rightarrow & \;a \notin A \\
\text{è sottoinsieme} \rightarrow & \;A \subseteq B \\
\text{è sottoinsieme stretto} \rightarrow &\; A \subset B \\
\text{insieme vuoto} \rightarrow &\; \varnothing \\
\text{unione} \rightarrow &\; A \cup B \,|\, \vee \\
\text{intersezione} \rightarrow &\; A \cap B \,|\, \wedge \\
\text{sottrazione} \rightarrow &\; A \setminus B \\
\text{cardinalità} \rightarrow &\; |A|
\end{aligned}
$$


## Prodotto cartesiano

Dati due insiemi $A$ e $B$, il loro **prodotto cartesiano** è l'insieme delle coppie $(a,b)$ con $a \in A$, $b \in B$.

Si indica con $A \times B$.

$$
|A \times B| = |A| \cdot |B|
$$

### Esempio

$$
\begin{aligned}
A =& \, \{\,1,2,3\,\} \\
A \times A =& \, \{\,(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3)\,\}
\end{aligned}
$$

## Insieme delle parti

Dato $A$, $\mathcal{P}(A)$ è l'insieme di tutti i sottoinsiemi di $A$.

$$
|\mathcal{P}(A)| = 2^{|A|}
$$

### Esempio

$$
\begin{aligned}
A =&\, \{\,1,2\,\} \\
\mathcal{P}(A) =&\, \{\,\varnothing, A, \{\,0\,\}, \{\,1\,\}\,\}
\end{aligned}
$$

# Funzioni

Come si descrive una funzione:

1. Un insieme di partenza ($A$) (*dominio*);
2. Un insieme di arrivo ($B$) (*codominio*);
3. Una serie di regole che ad ogni elemento di $A$ associa un **unico** elemento di $f(a) \in B$.

$$
f : A \rightarrow B
$$

Il grafico di una funzione è:

$$
\begin{aligned}
g =&\, \{\,(a, f(a)) \in A \times B \,|\, a \in A\,\} \\
=&\, \{\,(a,b) \in A \times B \,|\, b = f(a)\,\}
\end{aligned}
$$

## Funzioni Iniettive e Suriettive

Sia $f:A \rightarrow B$ una funzione.

- $f$ si dice **iniettiva** se manda elementi distinti di $A$ in elementi distinti di $B$.

$$
a_1 \in A, a_2 \in A, a_1 \neq a_2 \Rightarrow f(a_1) \neq f(a_2)
$$

  ovvero se

$$
f(a_1) = f(a_2) \Rightarrow a_1 = a_2
$$

- $f$ si dice **suriettiva** se ogni elemento di $B$ è ottenuto da almeno un elemento di $A$ tramite $f$.

$$
\forall\, b \in B \,\exists\, a \in A \;\text{t.c.}\; f(a) = b
$$

Una funzione si dice **biunivoca** se è sia iniettiva che suriettiva.

Teorema: Una funzione $f:A \rightarrow B$ è biunivoca se e solo se è invertibile, cioè se e solo se esiste una funzione $g:B \rightarrow A \,\text{t.c.}\,$:

$$
\begin{aligned}
g(f(a)) =&\, a \,\forall\, a \in A \\
f(g(b)) =&\, b \,\forall\, b \in B
\end{aligned}
$$

Osservazione:

$$
f:A \rightarrow B
$$

- è iniettiva se ogni elemento di $B$ è ottenuto da al più un elemento di $A$ tramite $f$;
- è suriettiva se ogni elemento di $B$ è ottenuto da almeno un elemento di $A$ tramite $f$.

## Immagine e controimmagine

Sia $f:A \rightarrow B$ una funzione.

- Se $b=f(a) \text{ con } a \in A, b \in B$, si dice che *$b$ è immagine di $a$ tramite $f$*;
- Sia $C \subseteq A$ un sottoinsieme, si dice *immagine di $C$* tramite $f$ l'insieme degli elementi di $B$ che sono imamgine di elementi di $C$.
  $f(c) = \{\,f(a) : a \in C\,\} \subseteq B$
- Immagine di $A$: $f(A) = \{\,f(a): a\in A\,\}$
- Sia $D \subseteq B$ un sottoinsieme, si dice **controimmagine di $D$** tramite $f$ l'insieme di tutti gli elementi di $A$ che hanno immagine contenuta in $D$.
- Controimmagine di $D$: $f^{-1}(D) = \{\,a \in A : f(a) \in D\,\}$ (definita anche se $f$ non è invertibile).

# Numeri Reali

## Insiemi numerici

- **Naturali:** $\mathbb{N} = \{\,0,1,2,3,\dots\,\}$
- **Razionali:** $\mathbb{Z} = \{\, \frac{m}{n} : m \in \mathbb{Z}, n \in \mathbb{N}\setminus \{\,0\,\}\,\}$
- **Reali:** $\mathbb{R}$
- **Irrazionali:** $\mathbb{Q}$
- **Complessi:** $\mathbb{C}$ 

$$
\mathbb{N} \subset \mathbb{Z} \subset \mathbb{R} \subset \mathbb{Q} \subset \mathbb{C}
$$

## Proprietà dei numeri reali

Sono di tre tipi:

- Algebriche;
- Di Ordinamento;
- Assioma di Continuità.

### Algebriche

Sui numeri reali sono definite due operazioni $+$ e $\cdot$, dette somma e prodotto, con le seguenti proprietà:

- Relative alla somma:
	- **Commutativa:** $a+b = b+a \; \forall \, a,b \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Asociativa:** $(a+b)+c = a+(b+c)\; \forall\, a,b,c \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Elemento neutro somma:** $\exists\, 0 \in R \text{ t.c. } a+0 = a\; \forall \,a \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Esistenza dell'inverso:** $\forall \, a \in \mathbb{R} \;\exists \,b \in \mathbb{R} \text{ t.c. } a+b = 0$ *(z,q,r,c)*
- Relative al prodotto:
	- **Commutativa:** $a\cdot b = b \cdot a \;\forall \,a,b \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Associativa:** $(a \cdot b) \cdot c = a \cdot (b\cdot c) \;\forall \,a,b,c \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Elemento neutro prodotto:** $\exists 1 \in \mathbb{R} \text{ t.c. } a\cdot 1 = a \;\forall\, a \in \mathbb{R}$ *(n,z,q,r,c)*
	- **Esistenza dell'inverso:** $\forall\, a \in \mathbb{R}\; \exists\, b \in \mathbb{R} \text{ t.c. } a\cdot b = 1$ *(q,r,c)*
- **Distributiva:** $a \cdot (b + c) = ab + ac\; \forall \,a,b,c \in \mathbb{R}$ *(n,z,q,r,c)*

### Di Ordinamento

Dati due numeri reali $x$ e $y$, si ah sempre che $x \geq y$ oppure $x \leq y$.
Tale ordinamento ha le proprietà:

- **Riflessiva:** $x\geq x\; \forall \,x \in \mathbb{R}$
- **Antisimmetrica:** $\text{se } x \geq y \wedge y\geq x \text{, allora } x = y$
- **Transitiva:** $\text{se } x \geq y \wedge y\geq z \text{, allora } x \geq z$
<!-- -->
- $\text{se } x \geq y \text{, allora } x+z \geq y+z\; \forall\, z \in \mathbb{R}$
- $\text{se } x \geq y \text{, allora } x\cdot z \geq y \cdot z \;\forall\, z \in \mathbb{R} \text{ con } z \geq 0$

Queste valgono in $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$, ma non in $\mathbb{C}$.

### Assioma di Continuità

Dati $A, B \subseteq \mathbb{R}$ sottoinsiemi diversi da $\varnothing$.
Diciamo che $A$ sta tutto a sinistra di $B$ se $a \leq b \;\forall\, a \in A, \;\forall\, b \in B$.

L'assioma di continuità dice che se $A$ sta tutto a sinstra di $B$ allora esiste almeno un $c \in \mathbb{R} \text{ t.c. } c \geq a \;\forall\, a \in A; c \leq b \;\forall\, b \in B$.

> $c$ non è obbligato ad essere unico;
> $c$ può appartenere ad $A$, a $B$ o anche a entrambi (in questo caso è unico elemento "separatore").

#### Esempio

$$
\begin{aligned}
A &= \{\,x \in Q : x \geq 0 \wedge x^2 < 2\,\} \\
B &= \{\,x \in Q : x \geq 0 \wedge x^2 > 2\,\} \\
&\text{se } a \in A, b \in B \rightarrow a > b \\
c^2 &= 2
\end{aligned}
$$

Questo è impossibile in Q, quindi l'assioma di continuità non vale in Q.

Conclusione: sui numeri reali, $\sqrt{2}$ è l'elemento separatore tra $A$ e $B$ e si può dimostrare che è unico.

## Sottoinsiemi dei reali

$\left(a,b\right) \subseteq \mathbb{R}$ è l'intervallo separato da estremi $a,b \in \mathbb{R}$ (con $a<b$).

- $\left]a,b\right[ = (a,b) = \{\,x \in \mathbb{R} \text{ t.c. } a<x<b\,\}$
- $\left[a,b\right] = \{\,x \in \mathbb{R} \text{ t.c. } a\leq x \leq b\,\}$

# Inferiore, Superiore, Massimo e Minimo

Sia $A \subseteq \mathbb{R}$ un sottoinsieme *non vuoto*.

> $M \in \mathbb{R}$ si dice **maggiorante** di $A$ se $M\geq a \;\forall\, a \in A$

> $m \in \mathbb{R}$ si dice **minorante** di $A$ se $m \leq a \; \forall \, a \in A$

Minoranti e maggioranti non sono obbligati ad esistere.
Ad esempio $A = \mathbb{N}$ ha minoranti ma non ha maggioranti.

Se esiste un maggiorante invece, ne esistono infiniti.
Se $M$ è un maggiorante, anche $M+1$ lo è.
Lo stesso vale per i minoranti.

> $A \subseteq \mathbb{R}, A \neq \varnothing$ si dice **superiormente limitato** se ammette un maggiorante e **inferiormente limitato** se ammette un minorante.
> Si dice **limitato** se è contemporaneamente superiormente e inferiormente limitato.

Esempi:

- $A = \left ( 0, + \inf \right )$ è inferiormente limitato ma non superiormente
- $B = \{ \,\frac{1-n}{2} \,:\, n\in\mathbb{N}\,\}$ è superiormente limitato, ma non inferiormente
- $C = \left( 1,7\right]$ è limitato

> $M \in \mathbb{N}$ si dice **massimo** di $A$ (e si scrive $M = \max A$) se $M \in A \land M \geq a \;\forall\, a \in A$

> $m \in \mathbb{N}$ si dice **minimo** di $A$ (e si scrive $m = \min A$) se $m \in A \land m \leq a \;\forall\, a \in A$

$\max$ e $\min$ non sono obbligati ad esistere, nemmeno per insiemi limitati.

Esempio:

- $A = \left( 0,1 \right)$ non ha nè $\max$, nè $\min$

$\max$ e $\min$, se esistono, sono **unici**.

## Estremo superiore ed Estremo inferiore

Sia $A \subseteq \mathbb{R}, A \neq \varnothing$.

> Si dice che $\sup A = + \inf$ se $A$ non è superiormente limitato o $\sup A = L \in \mathbb{R}$ se lo è e $L$ è il minimo dei maggioranti.

> Si dice che $\inf A = - \inf$ se $A$ non è inferiormente limitato o $\inf A = l \in \mathbb{R}$ se lo è e $l$ è il massimo dei minoranti.

Esempi:

- $\sup \mathbb{N} = + \inf$
- $\inf \mathbb{N} = 0$
- $\sup \left( 0,1 \right) = 1$

> **Teo:** Se $A\subseteq \mathbb{R}, A \neq \varnothing$ è superiormente limitato, allora il minimo dei maggioranti esiste.

**Dimostrazione**:
Sia $B= \{\, x \in \mathbb{R} \,|\, x \geq a \;\forall\, a \in A \,\}$ l'insieme dei maggioranti.
Allora $A$ sta tutto a sinistra di $B$.
Per l'*assioma di continuità* c'è un elemento separatore $c \in \mathbb{R}$, ovvero $c \leq b \;\forall\, b \in B$ e $c \geq a \;\forall\, a \in A \implies c \in B$.
Quindi $c = \min B$.

**Esercizio per casa** #todo/compito:
Enunciare e dimostrare il teorema analogo per il massimo dei minoranti.

### Caratterizzazione di inf e sup

- $\sup A = + \inf$ se $\forall \, M \in \mathbb{R} \;\exists\, a \in A \text{ t.c. } a \geq M$ (*ovvero se posso trovare elementi di $A$ grandi quanto voglio*)
- $\inf A = - \inf$ se $\forall \, M \in \mathbb{R} \;\exists\, a \in A \text{ t.c. } a \leq M$
- $\sup A = L \in \mathbb{R}$ se
	- $a \leq L \;\forall\, a \in A$ (*$L$ è un maggiorante*)
	- $\forall\, \varepsilon > 0 \;\exists\, a \in A \text{ t.c. } a \geq L - \varepsilon$
- $\inf A = L \in \mathbb{R}$ se
	- $a \geq l \;\forall\, a \in A$ (*$l$ è un minorante*)
	- $\forall\, \varepsilon > 0 \;\exists\, a \in A \text{ t.c. } a \leq l + \varepsilon$

Se esiste $M=\max A$ allora $\sup A = M$.
Se esiste $m = \min A$ allora $\inf A = m$.
$\sup A$ non è obbligato ad appartenere ad $A$, ma se vi appartiene è il **massimo**.
Stessa cosa per $\inf A$.

# Funzioni reali

$f:\mathbb{R} \to \mathbb{R}$ oppure $f: A \to \mathbb{R}$.

Grafico di $f = \{\, (x,y) \in \mathbb{R}^2 : y = f(x)\,\}$ ($\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$).

Proprietà di simmetria:

- $f$ si dice **pari** se $f(x) = f(-x) \;\forall\, x \in \mathbb{R}$ (*simmetrica rispetto all'asse $y$*)
- $f$ si dice **dispari** se $f(x) = -f(-x) \;\forall\, x \in \mathbb{R}$ (*simmetrica rispetto all'origine*)
- $f$ si dice **periodica** se $\exists\, T > 0 \text{ t.c. } f(x+T) = f(x) \;\forall\, x \in \mathbb{R}$ (*il grafico si ottiene traslando il pezzo $\left[ 0, T\right]$ in $\left[ T, 2T\right]$, $\left[ T, 3T\right]$, ...*)

Se $f:\mathbb{R} \to \mathbb{R}$ è dispari, allora $f(0) = 0$.

Se $T$ è un periodo, anche $2T, 3T, 4T, \dots$ lo sono.
Il **minimo periodo** è il più piccolo $T$ (se esiste) per cui vale $f(x+T)= f(x) \;\forall\, T \in \mathbb{R}$.

Proprietà di **monotonia**:

- $f$ si dice **monotona**:
	- $f$ si dice **strettamente crescente** se $x>y \implies f(x) > f(y) \;\forall\, x, y \in \mathbb{R}$
	- $f$ si dice **strettamente decrescente** se $x>y \implies f(x) < f(y) \;\forall\, x, y \in \mathbb{R}$
- $f$ si dice **debolmente crescente** se $x>y \implies f(x) \geq f(y) \;\forall\, x, y \in \mathbb{R}$
- $f$ si dice **debolmente decrescente** se $x>y \implies f(x) \leq f(y) \;\forall\, x, y \in \mathbb{R}$

Se $f$ è strettamente crescente allora è anche debolmente crescente.
Se $f$ è strettamente decrescente allora è anche debolmente decrescente.

Se $f$ è sia deb. crescente che deb. decrescente allora è **costante**.

## Grafici, Iniettività e Suriettività

- Suriettiva $\iff$ in ogni elemento dell'insieme di arrivo termina *almeno* una freccia (*tutto l'asse $y$ è "coperto"*)
- Iniettiva $\iff$ in ogni elemento dell'insieme di arrivo termina *al più* ($0|1$) una freccia (*l'asse $y$ è "coperto" solo una volta*)
<!-- -->
- Retta orizzontale: $y = \lambda$
- Grafico di $f$: $y = f(x)$
- Intersezioni: $f(x) = \lambda$
$$
\begin{aligned}
f \text{ iniettiva} &\iff f(x) = \lambda \text{ ha al più una soluz. } \forall \, \lambda \in \mathbb{R} \\
f \text{ suriettiva} &\iff f(x) = \lambda \text{ ha almeno una soluz. } \forall \, \lambda \in \mathbb{R}
\end{aligned}
$$

Se $f$ è pari o periodica non è iniettiva.
Se $f$ è strettamente crescente o strettamente decrescente allora è iniettiva.


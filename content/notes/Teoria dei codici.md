---
title: "Teoria dei codici"
author: ["Federico Zotti"]
date: 2022-10-05
categories: Notes
tags: ["School", "TPS", "Cryptography"]
draft: true
---
{{< katex >}}

{{< alert >}}
**Warning!** Image links are broken!
{{< /alert >}}

# Probabilità in un testo

## Autoinformazione
- $I_s$: Autoinformazione;
- $P_s$: probabilità di $s$.

$$
I_s = -\log_2(P_s) = \log_2(\frac{1}{P_s})
$$

### Esempio:
|     | $n$  | $P$          | $I_s$ |
| --- | ---- | ------------ | ----- |
| A   | $8$  | $8/16 = 1/2$ | $1b$  |
| B   | $5$  | $5/16$       | ?     | 
| C   | $2$  | $2/16 = 1/8$ | $3b$  |
| D   | $1$  | $1/16$       | $4b$  |
| tot | $16$ |              |       |

## Entropia
- $H_s$: entropia di $s$;

$$
H_s = P_s \times I_s = P_s \times \log_2 (\frac{1}{P_s})
$$

Se la probabilità tende a $0$ l'entropia tende a ...

$$
P_s \to 0 \Rightarrow H_s = \lim_{x \to 0} x\log_2(\frac{1}{x})
$$

Deriviamo ...

$$
H'_x = - \log_2 (x) - \frac{x}{x\ln2}
$$

$$
H'_x = 0 \Leftrightarrow - \log_2 (x) - \frac{1}{\ln2} \Rightarrow \log_2 (x) = - \frac{1}{\ln2} \Leftrightarrow x = 2^{-\frac{1}{\ln2}} = 0.37
$$

Quindi ...

- $S$: sorgente;
- $\alpha \in S$: simbolo prodotto da S;

$$
H_S = \sum_{\alpha \in S}H_\alpha
$$

Con sorgente a 2 simboli:

- se $\alpha : P_\alpha =  x$
- $\rightarrow \beta : P_\beta =  1-x$

$$
H_S = x\log_2{\frac1x} + (1-x) \times log_2(\frac{1}{1-x})
$$

# Codifica Huffman

## Esempio 1
Abbiamo una stringa con 4 caratteri e con frequenza assoluta:

| Carattere | Frequenza |
| --------- | --------- |
| B         | 1         |
| D         | 3         |
| A         | 5         |
| C         | 6         |

![](Screenshot%20from%202022-10-06%2008-41-18%201.png)

Creiamo un albero con i primi due simboli:

| Carattere | Frequenza |
| --------- | --------- |
| B + D     | 4         |
| A         | 5         |
| C         | 6         |

![](Screenshot%20from%202022-10-06%2008-41-27.png)

| Carattere   | Frequenza |
| ----------- | --------- |
| (B + D) + A | 9         |
| C           | 6         |

![](Screenshot%20from%202022-10-06%2008-41-32.png)

| Carattere         | Frequenza |
| ----------------- | --------- |
| ((B + D) + A) + C | 15        |

![](Screenshot%20from%202022-10-06%2008-41-41.png)

Aggiungiamo i bit all'albero:

![](Screenshot%20from%202022-10-06%2008-48-26.png)

![](Screenshot%20from%202022-10-06%2008-48-35.png)

## Esempio 2

| Carattere | Frequenza |
| --------- | --------- |
| E         | 4         |
| A         | 5         |
| C         | 7         |
| F         | 12        |
| D         | 15        |
| B         | 25        |

| Carattere | Frequenza |
| --------- | --------- |
| C         | 7         |
| E + A     | 9         |
| F         | 12        |
| D         | 15        |
| B         | 25        |
|           |           |

| Carattere | Frequenza |
| --------- | --------- |
| F         | 12        |
| D         | 15        |
| C + (E+A) | 16        |
| B         | 25        |

| Carattere | Frequenza |
| --------- | --------- |
| C + (E+A) | 16        |
| B         | 25        |
| F + D     | 27        |

| Carattere | Frequenza |
| --------- | --------- |
| F + D     | 27        |
| (C+(E+A)) + B | 41        |

| Carattere             | Frequenza |
| --------------------- | --------- |
| (F+D) + ((C+(E+A))+B) | 68        |

| Carattere | Rappresentazione |
| --------- | ---------------- |
| F         | 00               |
| D         | 01               |
| B         | 11               |
| C         | 100              |
| E         | 1010             |
| A         | 1011             |

[https://en.wikipedia.org/wiki/Huffman_coding](https://en.wikipedia.org/wiki/Huffman_coding)

# Cifrari Monoalfabetici






































$$
a \approx b \mod H

{ x \in G : a + x \in H }
$$
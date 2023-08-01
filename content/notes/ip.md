---
title: "Basics of Internet Protocol"
author: ["Federico Zotti"]
date: 2021-05-11
categories: Notes
lastmod: 2021-05-18T12:54:16+02:00
tags: ["School", "IP", "Networking", "Basics of", "TPS"]
draft: false
---
{{< katex >}}

# Indirizzo IPv4

Indirizzo assegnato dal sistema operativo ad ogni scheda di rete (_NIC_).


## NIC

Le schede di rete possono essere:

-   Reali (eth0, wlo1, ...);
-   Virtuali (lo [loopback], virbr0, ...).


### loopback

La scheda `lo` è sempre associata a `127.0.0.1/8`.

Tutti gli indirizzi che iniziano con 127 sono loopback.


## Protocollo internet

Il protocollo internet (_internet protocol [IP]_) permette la comunicazioni di macchine in reti più reti.


# Struttura dell'indirizzo

È composto da un numero a 32 bit, 4 byte, con un totale di $2^{23}$ indirizzi.

**HOST**: computer dotato di indirizzo IP.


# Carrellata storica

All'inizio i primi bit rappresentavano una rete, mentre i successivi rappresentavano l'host all'interno della rete stessa.

Per permettere di distinguere le due parti di è creata la _subnet mask_.


## Subnet mask

La subnet mask (maschera di sottorete) è un metodo per definire gli indirizzi ip appartenenti ad una rete.

È possibile esprimerla in 2 modi:

-   In base ai bit che non cambiano nella rete:

    Nella rete con ip `192.168.1.0 - 192.168.1.255`, i bit dell indirizzo che non cambiano sono `255.255.255.0`.

-   Contando i bit che non cambiano:

    La stessa rete è possibile esprimerla come `192.168.1.0/24`, perchè i primi 24 byte non cambiano (questo metodo viene chiamato _CIDR_).


### Classi

-   Classe A: `/255.0.0.0` - `/8`
-   Classe B: `/255.255.0.0` - `/16`
-   Classe C: `/255.255.255.0` - `/24`

Inizialmente le maschere non erano connesse agli IP e venivano utilizzati i primi due bit dell'ip.

---

```text

IP ->       1 1 0 0 0 1 1 0 /3
SUBMA ->    1 1 1 0 0 0 0 0

RETE (and)  1 1 0 0 0 0 0 0     (indirizzo della rete)
BROADCAST   1 1 0 1 1 1 1 1     (mettendo tutti i bit dell'host a 1)
HOST        0 0 0 0 0 1 1 0     (indirizzo dell'host)

```

```text

IP ->       174 152  78  25
SUBMA ->    255 255   0   0     (classe B)

RETE (and)  174 152   0   0     (indirizzo della rete)
BROADCAST   174 152 255 255     (mettendo tutti i bit dell'host a 1)
HOST          0   0  78  25     (indirizzo dell'host)

```

---


# Classificazioni sottoreti IP


## Privati

Servono per costruire le _reti locali_ (LAN).

-   `10.0.0.0/8`: unica rete di classe A privata;
-   `172.16.0.0/12` [ `172.16.0.0/16` <-> `172.31.0.0/16` ]: reti di classe B private;
-   `192.168.0.0/16` [ `192.168.0.0/2` <-> `192.168.255.0/24` ]: reti di classe C private.


## Riservati

-   `127.0.0.0/8`;
-   `0.0.0.0/8`;
-   `169.254.0.0/16`: Riservata da win per collegamenti in link-local.


## Pubblici

Tutti gli altri indirizzi.
Sono raggiungibili da qualsiasi punto di internet.


# CIDR table

| cidr | std             | dim          |
|------|-----------------|--------------|
| 32   | 255.255.255.255 | $2^{0}$      |
| 31   | 255.255.255.254 | $2^{1}$      |
| 30   | 255.255.255.252 | $2^{2}$      |
| 29   | 255.255.255.248 | $2^{3}$      |
| 28   | 255.255.255.240 | $2^{4}$      |
| 27   | 255.255.255.224 | $2^{5}$      |
| 26   | 255.255.255.192 | $2^{6}$      |
| 25   | 255.255.255.128 | $2^{7}$      |
| 24   | 255.255.255.0   | $2^{8}$      |
| 23   | 255.255.254.0   | $2^{9}$      |
| 22   | 255.255.252.0   | $2^{10}$     |
| 21   | 255.255.248.0   | $2^{11}$     |
| 20   | 255.255.240.0   | $2^{12}$     |
| 19   | 255.255.224.0   | $2^{13}$     |
| 18   | 255.255.192.0   | $2^{14}$     |
| 17   | 255.255.128.0   | $2^{15}$     |
| 16   | 255.255.0.0     | $2^{16}$     |
| 15   | 255.254.0.0     | $2^{17}$     |
| 14   | 255.252.0.0     | $2^{18}$     |
| 13   | 255.248.0.0     | $2^{19}$     |
| 12   | 255.240.0.0     | $2^{20}$     |
| 11   | 255.224.0.0     | $2^{21}$     |
| 10   | 255.192.0.0     | $2^{22}$     |
| 9    | 255.128.0.0     | $2^{23}$     |
| 8    | 255.0.0.0       | $2^{24}$     |
| 7    | 254.0.0.0       | $2^{25}$     |
| 6    | 252.0.0.0       | $2^{26}$     |
| 5    | 248.0.0.0       | $2^{27}$     |
| 4    | 240.0.0.0       | $2^{28}$     |
| 3    | 224.0.0.0       | $2^{29}$     |
| 2    | 192.0.0.0       | $2^{30}$     |
| 1    | 128.0.0.0       | $2^{31}$     |
| 0    | 0.0.0.0         | $2^{32}$     |


# Indirizzo IPv6

È composto da 128 bit.


## Rappresentazione

È composto da 8 gruppi da 4 cifre esadecimali ciascuno.

Se all'inizio di un gruppo sono presenti 0, posso essere omessi.

Un solo insieme di 0 può essere rappresentato con `::`.

Esempio: `ACB0:013B::215` <-> `ACB0:013B:00...00:0215`


## Loopback

L'indirizzo di lo è `::1/128`.


## CIDR

Ogni sottorete può essere un multiplo di 4:

-   128
-   124
-   120
-   116
-   ...

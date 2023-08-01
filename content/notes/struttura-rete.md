---
title: "Stack ISO OSI"
author: ["Federico Zotti"]
date: 2021-09-29
tags: ["School", "TPS", "OSI", "Networking"]
categories: Notes
draft: false
---

# Stack ISO OSI

## Livello fisico
[ISO-OSI_Livello-fisico](/appunti/tps/ISO-OSI_Livello-fisico/)

## Livello datalink
Livello delle NIC.

Trasmette un agglomerato di bit (_frame_).

-   MAC.

## Livello network
Livello di rete/internet (OS).

Trasmette pacchetti.

-   IPv4/IPv6.

## Livello transport
Permette la trasmissione di dati tra due processi, anche su macchine diverse.

Trasmette dei segmenti.

## Gruppo applicazione

### Livello session
Poco usato.

### Livello presentation
Poco usato.

### Livello application
Scambio di dati tra applicazioni.

-   HTTP/HTTPS;
-   SSH.

# Schema

```
┌─────────────┐                     ┌─────────────┐
│             │                     │             │
│ ┌─────────┐ │                     │ ┌─────────┐ │
│ │Trasporto│ │                     │ │Trasporto│ │
│ └┬────────┘ │                     │ └┬────────┘ │
│  │          │                     │  │          │
│ ┌┴──────┐   │                     │ ┌┴──────┐   │
│ │Network│   │                     │ │Network│   │
│ └┬──────┘   │                     │ └┬──────┘   │
│  │          │                     │  │          │
│ ┌┴───────┐  │                     │ ┌┴───────┐  │
│ │Datalink│  │                     │ │Datalink│  │
│ └┬───────┘  │                     │ └┬───────┘  │
│  │          │                     │  │          │
│ ┌┴─────┐    │  segnale analogico  │ ┌┴─────┐    │
│ │Fisico├────┼─────────────────────┤►│Fisico│    │
│ └──────┘    │                     │ └──────┘    │
│             │                     │             │
└─────────────┘                     └─────────────┘
```
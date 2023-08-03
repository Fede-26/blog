---
title: "Basics of Networking"
date: 2021-04-22T15:02:08+02:00
categories: Notes
tags:
    - Networking
    - School
    - Basics of
    - TPS
langs: "Italian"
draft: false
---
{{< katex >}}

# Indirizzo IP

L'indirizzo IP è un indirizzo associato ad ogni macchina presente in una rete.

Nell'IPv4 è composto da 4 byte, con un totale di $2^{23}$ indirizzi; mentre nell'IPv6 è composto da 8 gruppi di 4 cifre esadecimali ciascuno, per un totale di $2^{128}$ indirizzi.


# Indirizzo MAC

È l'indirizzo fisico di ogni interfaccia di rete.
Normalmente non è possibile cambiarlo ed è assegnato dal produttore.


# Porta

Una porta è un passaggio tramite il quale un processo comunica con la rete esterna.
Per esempio il servizio `sshd` è in ascolto sulla porta 22 per un processo che inizializzi la connessione.
Per http la porta standard è la 80, mentre per https è la 433.


# Hostname

L'hostname è un nome facile da memorizzare associato ad un indirizzo IP.
Il compito di associarlo è quello del DNS.


# MulticastDNS

Il multicastDNS o mDNS è un metodo per condividere il proprio hostname in una rete locale.
Viene chiamato anche Bounjour perchè questo è il nome del programma di apple che lo gestisce.

Normalmente gli hostname definiti con mDNS finiscono per `.local`.


# DHCP

Il DHCP è il servizio che assegna ad ogni macchina appena collegata ad una rete un indirizzo IP per poter comunicare.


# Subnet mask

La subnet mask (maschera di sottorete) è un metodo per definire gli indirizzi ip appartenenti ad una rete.

È possibile esprimerla in 2 modi:

- In base ai bit che non cambiano nella rete:

  Nella rete con ip `192.168.1.0 - 192.168.1.255`, i bit dell indirizzo che non cambiano sono `255.255.255.0`.

- Contando i bit che non cambiano:

  La stessa rete è possibile esprimerla come `192.168.1.0/24`, perchè i primi 24 byte non cambiano.


# Gateway

Dispositivo che collega la rete locale con un'altra.

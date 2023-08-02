---
title: "Matrix: la chat del futuro"
date: 2021-01-14
categories: "Guides"
tags:
    - IM
draft: false
---



# Introduzione

Visto il recente cambio di policy da parte di WhatsApp, molti utenti si stanno spostando verso piattaforme più sicure.

Una piattaforma che adoro e consiglio di utilizzare è [Matrix](https://matrix.org/), un protocollo di chat decentralizzato, crittografato, multipiattaforma e multiprotocollo.



# Decentralizzato

Il punto di forza di Matrix è la decentralizzazione, cioè l'assenza di una piattaforma centrale che gestisce tutti i nostri messaggi, ma invece la presenza di una moltitudine di server (anche il tuo se vuoi) in cui ci si può registrare.

Questo però non complica le cose, visto che i messaggi vengono inviati automaticamente al server appropriato.

Generalmente se si è poco esperti o si vuole fare poca fatica ci si può iscrivere all'_homeserver_(è cosi che vengono chiamati i server in cui risiedi) predefinito di matrix.

Tutto ciò vuol dire che una organizzazione non potrà mai bloccare Matrix per te o per gli altri.



# Crittografato

Matrix supporta la crittografia E2E (end to end) che permette di criptare i messaggi che invii e decriptarli solo alla ricezione del destinatario giusto.

Questo impedisce ai server di leggere e memorizzare i tuoi messaggi.

Inoltre implementa la verifica incrociata: per i nuovi dispositivi e contatti che si collegano si può verificare se la chat è davvero sicura o è stata compremessa.



# Multipiattaforma

Matrix in se è solo un protocollo, una lingua, ed ha dunque bisogno di client, chi la parla.

Esistono una moltitudine di [client](https://matrix.org/clients/) per Matrix, compreso uno per il Nintendo 3DS!

Il client consigliato si chiama [Element](https://element.io/) ed è disponibile per android, iOS, Windows e Web.

L'interfaccia è molto intuitiva (molto simile a whatsapp) e facile.



# Multiprotocollo

Questo particolare potrebbe interessare a molti o a molto pochi: Matrix supporta i [bridge](https://matrix.org/bridges/)!

I bridge sono programmi che permettono di "fare da ponte" tra più piattaforme: permettono per esempio di collegare un gruppo discord o telegram con una _stanza_(si chiamano così i gruppi).



# Dettagli tecnici

Per le persone più tecniche sono di seguito riportati dei dettagli di Matrix:

## Nome utente

I nomi utente sono composti da un nome personale (scelto al momento della registrazione) e dall'homeserver.

> `@nome:matrix.org`

Non è possibile cambiare nome dopo la registrazione, ma è possibile creare un secondo account.

Inoltre è possibile che esistano nomi utente uguali con diversi homeserver.

## crittografia E2E disabilitata

In matrix tutte le comunicazioni avvengono in stanze, anche quelle con solo 2 utenti.

Per le stanze con solo 2 utenti la crittografia è attivata in automatico, mentre per le altre deve essere attivata manualmente.

Ciò non vuol dire che Matrix non sia sicuro, ma che alcuni gruppi, per ragioni particolari, non avranno attiva la crittografia.

## Presenza di bot

Ci sono i bot!

I bot sono programmi rispondono a determinati comandi o eventi e mandano un messaggio come risposta.

Un esempio è il bot per i promemoria: se in gruppo mandi il comando `!promemoria andare a fare la spesa`, il bot te lo ricorderà inviando un messaggio.

I bot vanno ovviamente attivati manualmente per ragioni di sicurezza, ma è possibile svilupparli molto facilmente.

## Moltissimi comandi predefiniti

Nel client element sono implementati moltissimi comandi, tra cui uno per formattare in HTML o far nevicare in chat.

## Integrazione con IRC out of the box

Se si utilizza matrix.org come homeserver, si avrà la possibilità di accedere ai canali IRC dei server:

- Freenode
- OFTC
- Snoonet
- W3C

## Creazione di stanze pubbliche o private

È in oltre da notare la possibilità di creare stanze sia private (quindi con utilizzo di invito) che pubbliche.

Queste ultime sono raggiungibili da chiunque abbia un account su Matrix e possono essere utilizzate come metodo di comunicazione per progetti pubblici.
---
title: "Esperienza PCTO"
date: 2022-02-11T15:10:21+01:00
categories: "Posts"
tags:
    - Scuola
    - PCTO
    - Frontend
langs: "Italian"
draft: false
---

# Sintesi
Questa è la mia esperienza durante le due settimane di PCTO nel quale ho usato angular e typescript per creare una webapp.

# I tutorial
[Angular](https://angular.io/)<sup>[1]</sup> è un framework per creare applicazioni web (frontend) con [typescript](https://www.typescriptlang.org/)<sup>[2]</sup>.
Quest'ultimo è un superset di javascript che aggiunge i tipi statici alle variabili, riducendo gli errori derivati dalla confusione e casting implicito che ne derivano.
Dunque se si dichiara una variabile `let a: string;`, quella variabile potrà soltanto essere una stringa.
Rimangono comunque i tipi `any` per consentire la tipizzazione dinamica.

Per imparare i concetti fondamentali di angular e typescript ho seguito alcuni video tutorial e il corso ufficiale su angular:
- [youtu.be/ahCwqrYpIuM](https://youtu.be/ahCwqrYpIuM)
- [youtu.be/G0bBLvWXBvc](https://youtu.be/G0bBLvWXBvc)
- [angular.io/tutorial](https://angular.io/tutorial)

Avendo acquisito le basi di angular, mi è stato assegnato il compito di creare una calcolatrice.

---

# Organizzazione dei progetti
Per organizzare e tenere salvati le varie versioni dei programmi utilizzo [Git](https://git-scm.com/)<sup>[3]</sup>, un sistema di controllo versioni distribuito.
Git permette di salvare ogni modifica effettuata ad un file e recuperare le versioni più vecchie.
Si può quindi usare sia come strumento di "backup" che come strumento di collaborazione, perchè permette l'unione di modifiche diverse sullo stesso file.
È possibile usare un servizio online come GitLab per la sincronizzazione del repository git.

---

# La calcolatrice
[https://gitlab.com/pcto-fede/calcolatrice](https://gitlab.com/pcto-fede/calcolatrice)

Comincio con il creare un nuovo progetto tramite `ng-cli`, e creo subito un componente contenente la logica della calcolatrice.

## RPN
Per creare questa calcolatrice ho deciso di iniziare con una di tipo [RPN](https://it.wikipedia.org/wiki/Notazione_polacca_inversa)<sup>[4]</sup>.

### La logica
La logica si basa su un semplice stack.
Schiacciando il tasto push si aggiunge il numero allo stack e utilizzando uno dei quattro operatori è possibile eseguire un'operazione con i primi due numeri dello stack.

Sono anche implementati dei controlli base per evitare errori, come lo stack troppo piccolo.

### La grafica
Per la parte grafica vengono usati dei `<button>` in una tabella, a sua volta in una tabella contenente anche il display e lo stack.
Ogni pulsante esegue una funzione che aggiunge il numero o esegue un'operazione.
Ho in seguito cambiato il font per assomigliare ad un display a 7 segmenti.

![](/img/Screenshot_20220202_133947.png)

## Non RPN
Avanzandomi tempo, decido di scrivere un ulteriore componente per una calcolatrice a notazione infix (come le calcolatrici comuni).

### La logica
Si basa sempre su uno stack, ma in esso vengono salvati anche gli operatori.
Premendo il tasto `=` vengono presi gli ultimi tre elementi (due numeri e un operatore) e viene eseguita l'operazione.

### La grafica
La grafica è la stessa dell'altra calcolatrice.

Per visualizzarle entrambe, utilizzo flexbox in modo da avere un interfaccia un minimo responsive.

![](/img/Screenshot_20220203_091244.png)

## L'API esterna
Come compito aggiuntivo mi viene chiesto di implementare un'api esterna che può eseguire le operazioni.
Utilizzo quindi [mathjs](https://api.mathjs.org/)<sup>[5]</sup> e implemento delle chiamate GET con la relativa sintassi.

### Risposte asincrone
Qui cominciano a sorgere i problemi, perchè la funzione per effettuare richieste HTTP con angular è asincrona (quindi non blocca il programma in attesa della risposta) e ritorna un oggetto chiamato `Observable`, a cui le funzioni si possono "iscrivere" per eseguire funzioni all'arrivo dei dati.
Questo metodo di eseguire le funzioni mi è nuovo, ma riesco a implementarlo comunque.

### Switch offline | online
Implemento un metodo per scegliere se eseguire le operazioni in locale oppure effettuando una chiamata all'API.
Tramite un semplice switch con un po' di css, è possibile cambiare una variabile che segnala al servizio quale operazione fare.

---

#  Il meteo
[https://gitlab.com/pcto-fede/weather-webapp](https://gitlab.com/pcto-fede/weather-webapp)

Dopo il completamento della calcolatrice, mi vengono proposte alcune API gratis da cui posso recuperare dei dati e che possono essere spunto per un'applicazione web da scrivere.

## Il mockup
Prima di programmare effettivamente l'applicazione, bisogna creare un mockup con le funzionalità che si vogliono implementare.
Questo è un metodo per capire e ragionare su tutte le funzioni possibili e di come esse interagiscono tra di loro.

Per crearlo ho usato [Figma](https://www.figma.com)<sup>[6]</sup>, un servizio gratuito online che permette di creare dei mockup.

![](/img/Screenshot_20220211_172134.png)
![](/img/Screenshot_20220211_172146.png)
![](/img/Screenshot_20220211_172203.png)

## L' API
Scelgo [OpenWeather](https://openweathermap.org/api)<sup>[7]</sup> perchè mi sembrava quella più completa e con la quale poter scrivere un programma più completo.

Per raccogliere i dati è necessario fare una chiamata a [_Current weather data_](https://openweathermap.org/current)<sup>[8]</sup>, che fortunatamente permette di eseguire il geocoding in automatico, quindi è possibile inserire il nome di una città al posto delle coordinate.

Questa però non contiene le previsioni, ma solo i dati attuali.
Bisogna chiamare dunque [_One call API_](https://openweathermap.org/api/one-call-api)<sup>[9]</sup>, la quale non fa geocoding, ma ritorna tutti i dati con una sola richiesta.

## Organizzazione del progetto
Per cominciare divido il progetto in un componente per la ricerca delle città e uno per la visualizzazione delle preview delle città cercate.
Creo poi un servizio per le richieste HTTP che restituisce gli observable con i dati delle risposte.

## La ricerca città
Per la richiesta delle città basta scrivere il nome della città nel form, che viene salvato in automatico in una variabile (grazie al data binding di angular).
Schiacciando il tasto cerca vengono fatte  le richieste a OpenWeather e i dati vengono visualizzati tramite il componente preview.

## I dettagli delle città
Nella preview non sono disponibili molti dati, ma cliccandola è possibile spostarsi in un'altra pagina (grazie ad angular routing) che permette di visualizzare i dettagli, come la temperatura, l'umidità e la velocità del vento attuale e le previsioni.

In questa pagina ho utilizzato flexbox per organizzare delle "card" contenenti i dati.

Ho voluto anche aggiungere una mappa tramite [mapbox](https://www.mapbox.com/)<sup>[10]</sup> e un plugin per angular.
Essa prende le coordinate e semplicemente centra la mappa con la città scelta.

Per comunicare alla pagina dei dettagli quale città visualizzare è presente un id nell'url, il quale è sostituibile al nome della città al momento della chiamata.

L'unico problema è che l'API viene richiamata ogni qualvolta ci si sposta dalla pagina di ricerca a quella dei dettagli.
Per ovviare a questi problemi ho creato un nuovo servizio per il salvataggio dei dati delle risposte.
Solo nel caso che l'id della città non corrisponda a quello salvato viene chiamata l'API.

## Il CSS
Non essendo molto bravo nel design e nel frontend in generale, il sito a questo punto era molto brutto.

![](/img/Screenshot_20220211_172005.png)
![](/img/Screenshot_20220211_172016.png)

Sono però riuscito a migliorarlo di molto utilizzando una delle tante librerie disponibili.

Io ho usato [PrimeNG](https://www.primefaces.org/primeng/)<sup>[11]</sup>, il quale permette di aggiungere dei veri e propri tag html per creare ad esempio dei menù dropdown o delle finestre di input.

Ho quindi racchiuso ogni gruppo di dati in una "card", e ho utilizzato un tema coerente con tutto il sito.

![](/img/Screenshot_20220211_172804.png)
![](/img/Screenshot_20220211_172815.png)

## I grafici
Grazie a PrimeNG sono riuscito ad implementare dei grafici per le previsioni.
Questi sono visualizzabili cliccando sulla tabella dei dati delle previsioni, che grazie alla direttiva `*ngIf`, viene sostituita da un'altra card con i grafici.

All'inizio ho avuto dei problemi con i grafici, perchè non avevo i dati delle API durante la creazione, quindi ho dovuto cambiare leggermente i servizi e registrare la funzione che aggiorna il grafico all'arrivo dei dati.

![](/img/Screenshot_20220211_172847.png)

## I preferiti
Ho poi deciso di aggiungere i preferiti, in modo da poter salvare le città e vederle in modo più rapido.
È stato quindi aggiunto un pulsante per il salvataggio vicino alla città cercata e uno per l'eliminazione vicino alle città salvate.
Il salvataggio avviene nel _local storage_, in modo da non cancellarsi alla chiusura del browser.

Al caricamento della pagina il _local storage_ viene letto e vengono visualizzati i preferiti con la direttiva `*ngFor`.

## L'autocompletamento
Questa è una funzione che avrei voluto implementare, ma che non sono riuscito a realizzare per la mancanza di tempo che la difficoltà.

Volevo creare un menù dropdown con il quale si poteva selezionare la città simile alla query inserita.
Per farlo bisogna chiamare l'api per l'autocompletamento ogni volta che si inserisce una lettera, ricevere i risultati e visualizzarli con `*ngFor` in modalità asincrona nel dropdown.

---

# Vue
Per concludere l'esperienza ho anche guardato un tutorial di [Vue](https://vuejs.org/)<sup>[12]</sup>, un'altro framework javascript per la creazione di web, insieme a React sono i tre principali usati nella maggior parte dei siti.

Vue, a differenza di React e Angular non è sviluppato da grandi multinazionali (Facebook e Google).

Vue non impone una divisione in componenti e servizi, ma invece contiene il template HTML e lo script nello stesso file (`.vue`).
Contiene le stesse direttive di angular.

È molto più leggero e performante rispetto ad angular.

---

# Riferimenti
1. [angular.io](https://angular.io/);
2. [typescriptlang.org](https://www.typescriptlang.org/);
3. [git-scm.com](https://git-scm.com);
4. [it.wikipedia.org/wiki/Notazione_polacca_inversa](https://it.wikipedia.org/wiki/Notazione_polacca_inversa);
5. [api.mathjs.org](https://api.mathjs.org/);
6. [www.figma.com](https://www.figma.com);
7. [openweathermap.org/api](https://openweathermap.org/api);
8. [openweathermap.org/current](https://openweathermap.org/current);
9. [openweathermap.org/api/one-call-api](https://openweathermap.org/api/one-call-api);
10. [www.mapbox.com](https://www.mapbox.com/);
11. [www.primefaces.org/primeng](https://www.primefaces.org/primeng/);
12. [vuejs.org](https://vuejs.org/).
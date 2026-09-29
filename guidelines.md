---
source-git-commit: bdc8e76125282ab294e34c5216311524e015c175
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 1%
---
# Linee guida per contribuire alla documentazione dei servizi Adobe Consulting

## Filosofia della documentazione

Sappiamo che gli utenti di Adobe Experience Manager lavorano in ambienti altamente competitivi per creare esperienze digitali che li distinguano dalla concorrenza. Pertanto, è fondamentale che, quando ACS offre nuovi strumenti avanzati per AEM, questi siano integrati da una documentazione accurata e chiara che consenta al cliente di sfruttare immediatamente il proprio investimento AEM e massimizzare il ROI.

L’obiettivo della documentazione ACS è di renderla disponibile agli utenti di AEM il prima possibile. Pertanto, diamo priorità a una documentazione accurata e fruibile, che ci impegniamo ad aggiornare e migliorare continuamente.

## Contributi alla documentazione

Al fine di migliorare continuamente la documentazione di ACS, apprezziamo il contributo dell’intera community di utenti di AEM. I miglioramenti apportati alla documentazione, che derivino da richieste o segnalazioni di problemi, possono essere correzioni, chiarimenti, ampliamenti ed esempi aggiuntivi.

## Standard della documentazione

Pur accogliendo con favore i contributi alla documentazione di AEM, qualsiasi contributo, sotto forma di richiesta o segnalazione di un problema, deve essere conforme ai nostri standard in merito a tali contributi.

I contributi che non soddisfano tali standard possono essere rifiutati.

### Documentiamo i casi d’uso standard.

La documentazione ACS riguarda i casi di utilizzo standard. I casi di utilizzo che esulano dall’ambito di installazione e utilizzo standard del prodotto non rientrano nella documentazione di ACS.

### In genere non documentiamo i bug o le loro soluzioni.

La documentazione ACS riguarda i casi di utilizzo standard. Per questo motivo, i bug, gli effetti causati da bug e le soluzioni alternative per i bug non sono generalmente documentati.

Fanno eccezione le note sulla versione, in cui possono essere elencati i problemi noti con possibili soluzioni approvate dal team di gestione dei prodotti AEM.

### I contributi alla documentazione non devono essere usati per rispondere a domande tecniche.

È gradita come contributo qualsiasi idea che punti al miglioramento della documentazione ACS. Tuttavia, commenti, problemi e richieste sono destinati solo a *contributi*. L’obiettivo non è di rispondere a domande sull’utilizzo di AEM, su come implementare un progetto AEM o risolvere problemi tecnici.

Eventuali domande sull&#39;utilizzo di AEM o su errori tecnici possono essere segnalate attraverso il normale processo di assistenza tramite il [portale di assistenza Enterprise Support di Experience Cloud](https://helpx.adobe.com/it/contact/enterprise-support.ec.html) o discusse nella [community di Experience Manager](https://forums.adobe.com/community/experience-cloud/marketing-cloud/experience-manager).

***I contributi alla documentazione ACS non sostituiscono l&#39;Assistenza clienti Adobe***. Tutti i contributi che richiedono risposte a domande correlate al supporto verranno rifiutati.

### I contributi devono fare riferimento in modo chiaro alle pagine della documentazione interessate.

Se apri una segnalazione problema per suggerire miglioramenti alla documentazione, devi includere i collegamenti alle pagine interessate. Se apri una segnalazione problema utilizzando il collegamento **Modifica pagina** in una pagina della documentazione, il problema verrà creato automaticamente con un collegamento alla pagina.

Ciò non si applica alle richieste pull, che per loro natura fanno riferimento alle pagine interessate.

## Linee guida per la documentazione

Chiediamo che qualsiasi contributo alla nostra documentazione segua determinate linee guida di stile.

L’aderenza a queste linee guida semplifica la revisione del tuo contributo e ne velocizza quindi l’integrazione nella documentazione.

### Lingua e stile

#### Lingua

* La documentazione ACS è creata e mantenuta in inglese americano.
* Usa frasi quanto più semplici possibile.
* Usa un linguaggio chiaro e conciso.

Ricorda che i lettori della documentazione di ACS sono di tutto il mondo e non ci si può aspettare che siano di madrelingua inglese o che parlino correntemente inglese. Evita i colloquialismi e usa un linguaggio chiaro e semplice.

#### Segui il manuale di stile di Microsoft

[Il Manuale di stile di Microsoft](https://docs.microsoft.com/en-us/style-guide/welcome/) è una guida di stile per la documentazione disponibile gratuitamente, specifica per la documentazione di software. La documentazione di AEM segue questa guida quando possibile.

### Formattazione

| Elemento | Stile |
|---|---|
| Elemento o opzione dell’interfaccia utente | **grassetto** |
| Nome file, percorso, input utente, valori parametro | `monospaced` |
| Codice, riga di comando | ```Code Block``` |

### Schermate

Le schermate devono essere utilizzate con cautela e solo quando una descrizione testuale è insufficiente.

Nelle schermate non devono essere utilizzati marcatori o altre annotazioni (come riquadri rossi, frecce o testo). In questo modo le schermate possono essere riutilizzate o replicate più facilmente nelle versioni localizzate della documentazione.

### Riferimenti a specifiche versioni

Se possibile, cerca di evitare riferimenti diretti a una versione specifica in tutto il contenuto della documentazione. Questo rende la documentazione più flessibile ed estensibile per le versioni future.

### Utilizzo di Day, AEM, CQ, CRX

Per la prima volta in un articolo, il prodotto deve sempre essere indicato con il suo nome completo **Adobe Experience Manager**; successivamente può essere usato **AEM**.

Day, Day Software, CQ e CRX non devono essere utilizzati a meno che non sia inevitabile ad esempio nei nomi delle classi o in riferimenti alla storia di AEM.
---
title: Panoramica sull'integrazione di Veeva Vault
description: Panoramica sull'integrazione di Veeva Vault
exl-id: 52cc7290-b7e1-4476-877f-48934e6daf68
source-git-commit: 4d27e7ecca662b2082a18621becb0b8ec7735824
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# Introduzione a Veeva Vault PromoMats e integrazione con Adobe Experience Manager

Questa integrazione consente di gestire i contenuti, applicare i diritti e garantire la conformità, sfruttando al contempo la distribuzione di esperienze di prima classe.

Questa integrazione richiede almeno le seguenti versioni del software:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

>[!NOTE]
>
>Gli utenti del servizio e le autorizzazioni appropriate sono necessari in entrambi i sistemi per l’integrazione.
>

>[!IMPORTANT]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. L’implementazione richiede un contratto di manutenzione Adobe Consulting. Per ulteriori informazioni, contatta il rappresentante del tuo Adobe.
>

## Principi e caratteristiche

Questa integrazione è progettata per supportare due casi d’uso principali:

1. Approvazione dei contenuti: quando vengono creati nuovi contenuti o se ne è stato modificato di esistenti in AEM, i contenuti devono essere approvati per l’utilizzo in VVPM a supporto del processo di approvazione medico, legale, normativo (MLR) per le scienze biologiche.

2. Gestione dei contenuti: fornisce visibilità sull’utilizzo delle risorse stabilendo relazioni in PromoMats tra le tattiche digitali (ad esempio e-mail, presentazioni, siti web) e i loro elementi (ad esempio loghi, fotografie, grafici) creati in AEM per i documenti provenienti dall’AEM.

I vantaggi includono:

* Mantenere un’unica fonte di verità per risorse e contenuti senza duplicazioni negli archivi digitali.
* Utilizzo di Veeva Vault per la gestione dei diritti e della conformità e di AEM per la creazione e la distribuzione di contenuti e risorse di livello superiore.
* Consente di automatizzare i contenuti e i metadati in movimento tra AEM e Veeva Vault.
* Riduce l’impegno manuale nell’invio di contenuti a Veeva per i flussi di lavoro di approvazione.
* Ogni sistema viene utilizzato per i suoi punti di forza e il connettore aiuta a spostare automaticamente i contenuti tra i sistemi per velocizzare i tempi di commercializzazione.

Che funzione svolge l’integrazione?

* Supporta l&#39;invio di pagine del sito AEM, risorse, frammenti di contenuto e frammenti di esperienza a VPM. Le pagine AEM, i frammenti di contenuto e i frammenti di esperienza possono essere inviati come PDF di schermata o immagini. I file binari di AEM Assets vengono inviati così come sono.
* Supporta la sincronizzazione manuale e automatizzata di determinati elementi di metadati configurabili da AEM a VPM.
* Supporta la sincronizzazione manuale e automatizzata di alcuni elementi di metadati configurabili da VVPM a AEM.
* Supporta le relazioni tra pagine del sito AEM, risorse, frammenti di contenuto e frammenti di esperienza in VVPM per automatizzare le relazioni tra i contenuti.
* Supporta la generazione di rendering per più tipi di dispositivi.

>[!NOTE]
>
>Per ulteriori dettagli sulle opzioni di configurazione, consulta la documentazione sull’utilizzo dell’integrazione.
>

Quali operazioni NON vengono eseguite dal connettore?

* Non replica i processi e le funzionalità dell’AEM in Veeva o viceversa.
* Non esegue MLR da sola. Aiuta nell’automazione dell’invio di contenuti a Veeva dove avviene MLR.
* Non deve essere utilizzato per creare una configurazione identica tra AEM e Veeva. Non tutti i contenuti devono essere spostati tra le due piattaforme.


>[!IMPORTANT]
>
>Questa integrazione considera attualmente l’AEM come la fonte di verità per la sincronizzazione dei contenuti.
>

## Ottenere l’integrazione

Per eseguire il provisioning di questa integrazione, segui i passaggi indicati di seguito.

Per richiedere e configurare l’integrazione, segui i dettagli del diagramma di flusso e del diagramma di flusso riportati di seguito.

![Richiedi accesso](assets/integration-request.png)

Dettagli del diagramma di flusso (mappa ai passaggi precedenti):

* **Passaggio 1** - Si presume che l&#39;utente disponga già di una licenza per Veeva Vault PromoMats e per Adobe Experience Manager o che sia in procinto di ottenerla.
* **Passaggio 2** - Per sfruttare i vantaggi dell&#39;integrazione, sarà necessario firmare un nuovo ordine di vendita (SO) che delinei un contratto di manutenzione con Adobe Consulting.
* **Passaggio 3** : installa, attiva e configura il pacchetto di integrazione.

## Supporto

Di seguito viene descritto come contattare e segnalare un problema con il team di supporto.

### Richiesta di integrazione o supporto Adobe Experience Manager

I ticket di supporto possono essere registrati con l’Assistenza clienti di Adobe. L&#39;amministratore di Adobe Experience Cloud dovrà effettuare l&#39;accesso a [Adobe Admin Console](https://adminconsole.adobe.com/), fare clic sulla scheda supporto e creare una controversia. Per qualsiasi problema relativo all’integrazione, assicurati di includere le seguenti informazioni:

* **Titolo processo**: `AEM - Veeva Vault Integration`
* **Proprietario processo**: `Data Engineering`
* **Descrizione**: `Description of the issue`
* **Punto di contatto**: `The email address(es) for relavant AEM point of contacts for your organization.`
* **URL istanza AEM**: `Place the Adobe Experience Manager instance url here.`
* **URL istanza Veeva**: `Place the Veeva Vault PromoMats instance url here.`

### Richiesta di supporto per Veeva Vault PromoMats

A volte, il problema che si verifica è un problema con il funzionamento dell&#39;istanza Veeva Vault PromoMats. In questo caso, l’amministratore Veeva Vault PromoMats potrebbe essere invitato a creare un ticket di supporto con [Supporto Veeva](http://support.veeva.com/). Lo stato dell’istanza Veeva può essere visualizzato passando a [Veeva Trust](http://trust.veeva.com/).

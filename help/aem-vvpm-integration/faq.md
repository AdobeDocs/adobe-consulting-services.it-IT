---
title: Domande frequenti sull'integrazione di Veeva Vault
description: Domande frequenti sull'integrazione di Veeva Vault
exl-id: c308ebb3-7881-4094-9f35-c67a96fb5ab1
source-git-commit: e4a5e55ac9b79a8de7dfa8ddd3d0ad99560917b8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Domande frequenti

**Quali metadati devono essere sincronizzati con Veeva?**

È importante comprendere i metadati in base al tipo di contenuto (ad esempio, promozioni) nel portale Veeva. Dopo aver esaminato il portale Veeva, crea lo schema di metadati dei contenuti in AEM per contenere tutti i metadati rilevanti per ciascuna risorsa/pagina e configura l’integrazione per mappare i metadati tra i due sistemi.

**L&#39;integrazione supporta i documenti collegati a Veeva? In caso contrario, quali tipi di relazione sono supportati?**

No. Consulta la [documentazione di Veeva](https://vaulthelp2.vod309.com/wordpress/admin-user-help/documents-admin-user-help/about-document-relationships/). Il documento Collegato (tipo di relazione di riferimento) è uno dei tipi di relazione standard che non è possibile creare o eliminare tramite API a causa di un comportamento speciale di Vault. I componenti, i documenti di supporto e tutti gli altri non presenti in questo elenco devono essere in grado di configurare tramite la configurazione di AEM Veeva Cloud.

**L&#39;integrazione supporta il contenuto modulare AEM?**

Sì, l’integrazione supporta i frammenti di contenuto e i frammenti di esperienza dell’AEM.

**L&#39;integrazione supporta il contenuto modulare Veeva?**

No, non in questo momento.

**L&#39;integrazione sincronizza le annotazioni visive Veeva con AEM?**

No, non in questo momento. Le annotazioni visive sono accessibili solo tramite API come PDF.

**Come si impostano le autorizzazioni per i documenti VVPM sincronizzati dall&#39;integrazione?**

L’integrazione utilizza un utente del servizio per caricare i documenti tramite l’API.  Le regole di impostazione predefinita e le regole di sostituzione dei documenti (ruoli predefiniti nei documenti) sono supportate solo nell&#39;interfaccia utente di VPM e non vengono applicate quando si utilizza l&#39;API. Si consiglia di utilizzare l&#39;applicazione livello dati (Dynamic Access Control, DAC) per le assegnazioni di ruolo. Il DAC viene applicato tramite tutti i punti di contatto, inclusa l’API. [Consulta la documentazione qui.](http://vaulthelp2.vod309.com/wordpress/admin-user-help/ah-user-permissions-access-control/about-dynamic-access-control-for-documents/)

**L&#39;integrazione supporta più istanze VPM?**

L’integrazione utilizza un approccio di configurazione cloud che consente di configurare più endpoint Veeva da un’istanza AEM.

**L&#39;integrazione supporta la pubblicazione AEM?**

No, questa integrazione funziona solo con l’autore dell’AEM. Ha lo scopo di facilitare i cicli di revisione MLR prima che il contenuto venga pubblicato.

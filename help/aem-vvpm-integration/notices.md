---
title: Avvisi sull'integrazione di Veeva Vault
description: Avvisi sull'integrazione di Veeva Vault
exl-id: 1a188671-d123-4475-a607-65743ba0dadd
source-git-commit: 07eab1e439626bd3bb3416c9e7d0c1666927a7aa
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Best practice, guardrail e avvisi

## Versioni

Questa integrazione richiede almeno le seguenti versioni del software:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

## Privacy dei dati

Questa integrazione è progettata per trasferire contenuti tra Adobe Experience Manager e Veeva Vault PromoMats. In qualità di titolare del trattamento dei dati, la tua azienda è responsabile del rispetto di tutte le leggi e le normative sulla privacy applicabili alla raccolta e all’utilizzo dei dati.

## Frequenza di sincronizzazione contenuti

Il contenuto e i metadati dell’AEM vengono sincronizzati dall’AEM a VVPN quando viene attivato il flusso di lavoro di integrazione. Questa operazione può essere eseguita automaticamente o manualmente. I metadati VPM vengono sincronizzati da VVPM a AEM. Questa operazione può essere eseguita automaticamente tramite una pianificazione o manualmente mediante un clic sul pulsante.

## Limitazioni dell’integrazione e best practice e guardrail

Quando utilizzi questa integrazione, considera le seguenti limitazioni:

* Durante la sincronizzazione dei metadati sono supportati solo i seguenti tipi di dati: &quot;Testo&quot; e &quot;Testo su più righe&quot;.
* L’integrazione supporta i contenuti modulari AEM (frammenti di contenuto e frammenti di esperienza), ma non i contenuti modulari VVPM.
* I documenti collegati VPM non sono supportati.
* La sincronizzazione delle annotazioni visive VVPM da VPM a AEM non è supportata.
* L’integrazione non importa il contenuto da VPM a AEM.
* Convalida dei metadati non supportata.
* Il numero di documenti è limitato in base alla licenza Veeva. Consulta [Limitazioni di licenza](#veeva-license-limitations).
* Il numero di chiamate API è limitato in base alla licenza Veeva. Per ulteriori informazioni, consulta [Limitazioni API](https://developer.veevavault.com/docs/#what-are-rate-limits). Consulta [Limitazioni di licenza](#veeva-license-limitations).

## Limitazioni delle licenze Veeva

È possibile monitorare i limiti delle istanze passando alle impostazioni generali di VVPM.

![Limiti Veeva](assets/veeva-limits.png)

---
product: adobe experience manager
solution: Experience Manager
description: Documentazione di Consulting Experience Manager
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.it-IT
index: y
source-git-commit: e2dac4b36fb94d72b72ef6f73a77e3f566539444
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 54%

---


# Metadati per uso interno

I metadati nel sistema di authoring GitHub sono gerarchici e sono definiti in base ai seguenti livelli crescenti di precedenza.

1. metadata.md
1. Sommario
1. Articolo

I metadati definiti nel file metadata.md si applicano all’intero archivio, ma possono essere ignorati a livello di sommario e articolo. Eventuali esclusioni dei metadati devono essere eseguite al livello più basso possibile.

metadata.md

* `product`
* `git-repo`
* `index: y`

Sommario

* `sub-product`
* `user-guide-title`

Articolo

* `title`
* `description`

Ulteriori informazioni sui metadati sono disponibili nella sezione [guida all’authoring interno](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).

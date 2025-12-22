---
product: adobe experience manager
solution: Experience Manager
description: Consulenza Documentazione di Experience Manager
type: Documentation
git-repo: https://github.com/Adobe-Enterprise-Docs/adobe-consulting-services.it-IT
index: y
author: Anon
source-git-commit: ac36c3ae49021c2b66234c8664df0969995aba62
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

Ulteriori informazioni sui metadati sono disponibili nella [guida all&#39;authoring interno](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).

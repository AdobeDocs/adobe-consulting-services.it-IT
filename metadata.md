---
product: adobe experience manager
solution: Experience Manager
description: Consulenza Documentazione di Experience Manager
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.en
index: true
source-git-commit: f491b48a151904f13becc146beab52600c9cef46
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 2%

---


# Metadati per uso interno

I metadati nel sistema di authoring GitHub sono gerarchici e sono definiti in base ai seguenti livelli crescenti di precedenza.

1. metadata.md
1. ToC
1. Articolo

I metadati definiti nel file metadata.md si applicano all’intero archivio, ma possono essere ignorati a livello di sommario e di articolo. Eventuali esclusioni dei metadati devono essere eseguite al livello più basso possibile.

metadata.md

* `product`
* `git-repo`
* `index: y`

ToCs

* `sub-product`
* `user-guide-title`

Articolo

* `title`
* `description`

Ulteriori informazioni sui metadati sono disponibili nella [guida all&#39;authoring interno](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).

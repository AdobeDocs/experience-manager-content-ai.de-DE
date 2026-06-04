---
cloud: Experience Cloud
solution: Experience Manager
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
usetq: true
type: Documentation
git-repo: https://github.com/AdobeDocs/experience-manager-content-ai.en
index: true
recommendations: noDisplay
source-git-commit: a47559544a9e972285ba570f16a38272b35794a8
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 2%

---


# Metadaten für die interne Verwendung

Metadaten im GitHub-Authoring-System sind hierarchisch und werden in den folgenden zunehmenden Präzedenzfällen definiert.

1. metadata.md
1. toC
1. Artikel

Metadaten, die in der Datei „metadata.md“ definiert sind, gelten für das gesamte Repository, können jedoch auf der Inhaltsverzeichnis- und Artikelebene überschrieben werden. Jede Überschreibung der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

Die Metadaten im Repository „experience-manager-content-ai.en“ sind das erforderliche Minimum.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

toCS

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`

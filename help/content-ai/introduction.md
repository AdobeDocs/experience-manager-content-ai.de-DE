---
title: Content-KI für AEM – Überblick
description: Erfahren Sie, was Content-KI für AEM ist, warum die Komponente wichtig ist und wie Sie mit der Aktivierung und Steuerung für Ihre AEM as a Cloud Service-Umgebung beginnen.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: Content-KI für AEM, Überblick, Inhaltsquelle, semantische Suche, Erfassung, Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 75%

---


# Content-KI für AEM – Einführung

## Intelligente Inhalte – von Grund auf KI-optimiert {#ai-ready}

Kunden beginnen damit, Marken über KI zu begegnen, bevor sie jemals auf eine Website treffen. Chatassistenten, KI-Übersichten, Agenten, Konversationssuche, KI-Concierges - alle rufen Markeninhalte im Namen der Marke ab, fassen sie zusammen und stellen sie dar. Was sie sagen, ist nur so genau, aktuell und markenintern wie die Inhalte, die sie erreichen können.
Für diese Verschiebung ist die AEM Content-KI konzipiert. Sie behandelt Markeninhalte als die Grundwahrheit, auf der KI-Erlebnisse ausgeführt werden - und gibt AEM-Kunden die Tools an die Hand, um diese Grundwahrheit auf Autorenseite schneller zu erstellen und sie für verbraucherorientierte KI-gesteuerte Erlebnisse auf Veröffentlichungsseite sauber bereitzustellen.

**Auf der Autorenseite** verankert Content-KI für AEM die Erstellung in freigegebenen Markenquellen. KI-gestützte Inhaltserstellung, das Finden von Inhalten mittels natürlicher Sprache über bestehende Seiteninhalte, Fragmente und Assets hinweg sowie eine markenkonforme Generierung ermöglichen es Teams, Varianten für neue Zielgruppen, Regionen und Kanäle zu erstellen – direkt in AEM und ohne von bereits freigegebenen Inhalten abzuweichen.

**Bei der Veröffentlichung** ist derselbe Inhalt so strukturiert, gesteuert und adressierbar, dass er von KI erfasst werden kann. Fragmente, Metadaten, Taxonomien und freigegebene Quellen werden in Strukturen bereitgestellt, die von Abrufsystemen, Agenten und dialogbasierten Schnittstellen verlässlich genutzt werden können – damit die KI die Marke authentisch widerspiegelt, wenn sie für sie spricht.

### Was dies für AEM-Kundinnen und -Kunden bedeutet {#what-it-means}

Genehmigte Inhalte sind die Verteidigung der Marke gegen Halluzinationen. Wenn KI auf regulierten AEM-Inhalten basiert, bleiben Antworten standardmäßig korrekt, aktuell und markenintern.
Die Inhaltserstellung hält mit der Nachfrage im KI-Zeitalter Schritt. Teams generieren Kopien und Bilder für weitere Zielgruppen und Momente innerhalb des Authoring-Erlebnisses - aus genehmigten Quellen, anstatt leer zu beginnen.
Entdeckung funktioniert so, wie Menschen und Maschinen tatsächlich fragen. Die zielbasierte Suche in natürlicher Sprache nach Assets, Fragmenten, Seiten und Formularen wandelt vorhandene Inhalte in eine wiederverwendbare Quelle um.
Personalization skaliert durch Wiederverwendung, nicht durch Duplizierung. Gesteuerte Komponenten werden zu Varianten neu kombiniert, anstatt sich zu nicht verfolgten Kopien zu vermehren.
Veröffentlichungskanäle enthalten jetzt KI-Oberflächen. Inhalte werden in Formen bereitgestellt, die Menschen, Agenten und KI-vermittelte Erlebnisse alle konsumieren können - ohne separate Pipelines für jede Konfiguration.

**Der entscheidende Punkt: Bestehende, vertrauenswürdige Markeninhalte sind heute wertvoller als je zuvor. Jedes freigegebene Fragment, jedes Asset und jede Seite, die sich bereits in AEM befinden, werden zur „Ground Truth“ (der verlässlichen Datenbasis), auf die KI-gestützte Erlebnisse angewiesen sind – und Content-KI für AEM sorgt dafür, dass diese Bibliothek wiederverwendbar, auffindbar und bereit ist, die Zukunft zu gestalten.**

## Content-KI für AEM auf einen Blick {#at-a-glance}

Content-KI für AEM ist als vierschichtiger Stack aufgebaut – dabei baut jede Ebene auf der darunter liegenden auf, vom vertrauenswürdigen Inhalt als Fundament bis hin zu den Agent-basierten Erlebnissen ganz oben.

![Diagramm des vierschichtigen Architektur-Stacks von Content-KI für AEM: Content-KI-Quellen als Fundament, grundlegende Content-KI-Dienste, Agent-basierte Inhaltsorchestrierung und Agent-basierte Erlebnisorchestrierung ganz oben](../assets/content-ai-four-layer-architecture-stack.png)

*Lesen Sie den Stack von unten nach oben – vom vertrauenswürdigen Inhalt als Fundament bis hin zu den Agent-basierten Erlebnissen ganz oben, die dieser Inhalt ermöglicht.*

1. Content-KI-Quellen
Inhaltsquellen sind verwaltete Entitäten in Content-KI für AEM, die eine Verbindung zu einer vertrauenswürdigen Datenbasis herstellen. Eine Inhaltsquelle kann auf einen von AEM gesteuerten Inhaltstyp wie Assets, Inhaltsfragmente, Seiten, Formulare, Metadaten und Taxonomien verweisen, ebenso wie auf Nicht-AEM-Quellen wie Websites von Drittanbietern, Wissensdatenbanken oder Dokumentationsportale. Jede Inhaltsquelle wird automatisch vektorisiert und semantisch angereichert, um den Abruf, die Faktenverankerung und dialogbasierte KI-Erlebnisse zu unterstützen. Definieren Sie Inhaltsquellen einmal und verwenden Sie sie über Content-KI-APIs hinweg wieder, mit integrierter automatischer Aktualisierung.

1. Grundlegende Content-KI-Dienste
Die APIs und Dienste, die semantische Intelligenz und generative KI im Kontext von Markeninhalten ermöglichen. Aufbauend auf den Content-KI-Quellen unterstützen diese Dienste den Abruf, die Generierung, markenkonforme Varianten und die Optimierung – alles verankert in den freigegebenen Inhalten des Kunden.

1. Agent-basierte Inhaltsorchestrierung
MCPs und Agenten, die anwendungsfallspezifische Inhaltsanforderungen durch natürliche Sprache in koordinierte Aktionen umsetzen. Diese Ebene ermöglicht es Autorinnen und Autoren sowie anderen Agenten, ihre Anforderungen in natürlicher Sprache zu beschreiben und die passenden grundlegenden Dienste orchestrieren zu lassen, um diese zu erfüllen.

1. Agent-basierte Erlebnisorchestrierung
Die innovativen Anwendungsfälle, die entstehen, wenn intelligente Markeninhalte in großem Maßstab auf KI treffen. AEM-Lösungen selbst basieren auf diesen grundlegenden Diensten – und Kundinnen und Kunden können dieselben APIs direkt nutzen, um ihre eigenen Agent-basierten Erlebnisse auf Basis ihrer eigenen Inhalte zu erstellen. Von KI-gestützten Inhaltslieferketten bis hin zu dialogbasierten Benutzer-Journeys – auf dieser Ebene werden gesteuerte Inhalte zu einem echten Wettbewerbsvorteil.

Diese Ebenen sind von Grund auf miteinander vernetzt: Jeder KI-Dienst greift auf das Inhaltsfundament zu, und alle erzeugten Ergebnisse fließen in dasselbe gesteuerte System zurück – sodass die Erstellung auf Autorenseite und die Bereitstellung bei der Veröffentlichung auf ein und dieselbe Single Source of Truth zurückgreifen.

## Content-KI für AEM in der Praxis {#action}

Der Weg zu einer funktionierenden Content-KI-Integration umfasst zwei Aufgaben:

### &#x200B;1. Aktivieren von Content-KI für Ihre AEM-Umgebung {#enable}

**Voraussetzung:** Bevor Sie mit der Nutzung von Content-KI beginnen können, benötigen Sie API-Anmeldedaten, die für Ihre AEM as a Cloud Service-Umgebung konfiguriert sind. Siehe [Einrichten eines Projekts in der Adobe Developer Console](setup-adc-project.md).

### &#x200B;2. Steuern von Content-KI-Quellen {#control}

Richten Sie Ihre Inhalts-KI-Quellen ein und verwalten Sie sie, um KI-basierte Erlebnisse zu aktivieren. Weitere Informationen finden [ unter „Steuern ](contentsources.md) Inhaltsquellen“.

## Informationen zu Content-KI-APIs  {#apis}

Entdecken Sie die funktionale Bandbreite von Content-KI für AEM – die APIs zeigen das volle Potenzial der Plattform. Siehe [Content AI-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).

---
title: Content-KI für AEM – Überblick
description: Erfahren Sie, was Content-KI für AEM ist, warum die Komponente wichtig ist und wie Sie mit der Aktivierung und Steuerung für Ihre AEM as a Cloud Service-Umgebung beginnen.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: Content-KI für AEM, Überblick, Inhaltsquelle, semantische Suche, Erfassung, Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: ht
source-wordcount: '885'
ht-degree: 100%

---


# Content-KI für AEM – Einführung

## Intelligente Inhalte – von Grund auf KI-optimiert {#ai-ready}

Kundinnen und Kunden kommen inzwischen über KI mit Marken in Kontakt, bevor sie deren Website besuchen. Chat-Assistenten, KI-Überblicke, Agents, dialogorientierte Suche, KI-Concierges – all diese Funktionen rufen Markeninhalte für die Marke ab, fassen sie zusammen und stellen sie dar.Was sie wiedergeben, ist nur so korrekt, aktuell und markenkonform, wie die Inhalte, die sie erfassen können.
Für diese Verschiebung ist die Content-KI von AEM konzipiert. Markeninhalte werden als die Grundwahrheit behandelt, basierend auf der KI-Erlebnisse ausgeführt werden. Dies stattet AEM-Kundinnen und -Kunden mit den Tools aus, mit denen sie diese Grundwahrheit auf Autorenseite schneller erstellen und sie für verbraucherorientierte KI-gesteuerte Erlebnisse auf Veröffentlichungsseite reibungslos bereitstellen können.

**Auf der Autorenseite** verankert Content-KI für AEM die Erstellung in freigegebenen Markenquellen. KI-gestützte Inhaltserstellung, das Finden von Inhalten mittels natürlicher Sprache über bestehende Seiteninhalte, Fragmente und Assets hinweg sowie eine markenkonforme Generierung ermöglichen es Teams, Varianten für neue Zielgruppen, Regionen und Kanäle zu erstellen – direkt in AEM und ohne von bereits freigegebenen Inhalten abzuweichen.

**Bei der Veröffentlichung** ist derselbe Inhalt so strukturiert, gesteuert und adressierbar, dass er von KI erfasst werden kann. Fragmente, Metadaten, Taxonomien und freigegebene Quellen werden in Strukturen bereitgestellt, die von Abrufsystemen, Agenten und dialogbasierten Schnittstellen verlässlich genutzt werden können – damit die KI die Marke authentisch widerspiegelt, wenn sie für sie spricht.

### Was dies für AEM-Kundinnen und -Kunden bedeutet {#what-it-means}

Genehmigte Inhalte sind die Mittel einer Marke gegen Halluzinationen. Wenn KI auf regulierte AEM-Inhalte zurückgreift, bleiben Antworten standardmäßig korrekt, aktuell und markenkonform.
Das Authoring hält mit der Nachfrage im KI-Zeitalter Schritt. Teams generieren Kopien und Bilder für weitere Zielgruppen und Momente innerhalb des Authoring-Erlebnisses. Dabei stützen sie sich auf genehmigte Quellen anstatt von null anzufangen.
Auffindbarkeit funktioniert basierend auf der Art und Weise wie Personen und Maschinen tatsächlich Fragen stellen. Die auf Absicht basierte Suche in natürlicher Sprache über Assets, Fragmente, Seiten und Formulare hinweg verwandelt bestehende Inhalte in wiederverwendbares Material.
Personalisierung wird durch Wiederverwendung skaliert, nicht durch Duplizierung. Gesteuerte Komponenten werden zu Varianten neu kombiniert, anstatt zu nicht verfolgten Kopien multipliziert zu werden.
Veröffentlichungskanäle enthalten jetzt KI-Oberflächen. Inhalte werden in Formen bereitgestellt, die Menschen, Agents und KI-vermittelte Erlebnisse konsumieren können – ohne separate Pipelines für jede Form.

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

Weitere Informationen zum Einrichten und Verwalten Ihrer Content-KI-Quellen für KI-basierte Erlebnisse finden Sie unter [Steuern von Inhaltsquellen](contentsources.md).

## Informationen zu Content-KI-APIs  {#apis}

Entdecken Sie die funktionale Bandbreite von Content-KI für AEM – die APIs zeigen das volle Potenzial der Plattform. Siehe [Content-KI-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).

---
title: Erste Schritte mit AEM Content-KI-Suchen
description: In diesem Handbuch wird erläutert, wie Sie die Suche auf Ihrer Site mit Content-KI aktivieren - Verbinden Sie Ihre Inhalte und wählen Sie dann eine Suchkomponente aus, um sie Besuchern zu präsentieren.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content-KI, AEM Content-KI-Suchen, GenSearch, Schnellsuche, Content-KI-Quellen, Akquise, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 6%

---


# Erste Schritte mit AEM Content-KI-Suchen

Die herkömmliche Site-Suche gleicht die Wörter, die ein Besucher eingibt, mit den Wörtern in Ihrem Inhalt ab. Dies funktioniert gut, wenn Besucher dieselbe Terminologie verwenden wie Ihre Inhalte - aber es zerlegt den Moment, in dem sie eine Frage stellen, eine Absicht äußern oder einfach Dinge anders formulieren. Die Suche ist eines der deutlichsten Anzeichen für die Besucherabsicht auf einer Website, sodass eine fehlgeschlagene Übereinstimmung oft eine fehlgeschlagene Journey bedeutet: Inhalte werden nicht entdeckt, Interaktionen werden reduziert und Konversionen gehen verloren. Besucher erwarten zunehmend, dass die Suche versteht, was sie bedeuten, und nicht nur, was sie getippt haben - und dass dieselbe vorsätzliche Grundlage überhaupt generative Antworten ermöglicht.

AEM Content-KI-Suchen ersetzen nicht das Sucherlebnis Ihrer Site - sie entwickeln sich weiter, vom Abgleichen von Keywords über das Verständnis von Bedeutung und Absicht bis hin zur direkten Beantwortung von Fragen. Die semantische Suche fügt zusätzlich zu Ihrem vorhandenen Sucherlebnis ein absichtsorientiertes Abrufen hinzu, sodass relevante Inhalte angezeigt werden, auch wenn eine Abfrage nicht den genauen Wortlaut des Inhalts teilt. Die generative Suche baut auf derselben Grundlage für den Abruf auf, um kontextbezogene, generierte Antworten zu generieren, die auf dem Inhalt Ihrer Website basieren - ein spezieller Schritt, nicht dasselbe wie der semantische Abruf.

Für Besucher bedeutet dies eine bessere Relevanz, Unterstützung in natürlicher Sprache, weniger Suchen ohne Ergebnis und schnellere Antworten. Für Ihr Unternehmen bedeutet dies einen besseren Abgleich der Absichten, eine bessere Erkennung von Inhalten und eine KI-fähige Suchgrundlage - ohne dass Sie Ihr Sucherlebnis von Grund auf neu aufbauen müssen. Und für Ihr Team ist es eine inkrementelle Aktualisierung: Ihre bestehende Suchkomponente kann Schritt für Schritt von lexikalischen, semantischen zu generativen Funktionen wechseln, anstatt eine völlig neue Implementierung zu erfordern.

Um dorthin zu gelangen, müssen Sie zwei Entscheidungen treffen: Wie Ihre Inhalte in die Content-KI gelangen und welche Komponente sie für Besucher bzw. Besucherinnen bereithält. Verbinden Sie Ihre Inhalte und fügen Sie dann eine Suchkomponente zu einer Seite hinzu. Ihre Site ist dann bereit, Besuchern die relevantesten Ergebnisse und absichtsbasierten Antworten zu geben.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Bedingungen erfüllt sind:

* Sie verfügen über ein aktives Cloud Manager-Programm mit mindestens einer AEM as a Cloud Service-Umgebung.
* Ihre Person wird dem Produktprofil **[!UICONTROL AEM-Benutzer]** (zum Anzeigen von Inhaltsquellen) und/oder **[!UICONTROL AEM-Administratoren]** (zum Erstellen und Bearbeiten) zugewiesen, die auf der **Publish**-Ebene - Content AI indiziert veröffentlichte Inhalte, nicht erstellte Inhalte. Unter [Zuweisen eines Benutzers zu einem AEM-Produktprofil](contentsources.md#assign-product-profile) finden Sie das vollständige Verfahren.
* Das Produktprofil der Umgebung wurde in **Adobe Admin Console bereitgestellt**.

>[!NOTE]
>
>Der Zugriff auf Cloud Manager allein reicht nicht aus. Ein Benutzer benötigt außerdem ein auf der Veröffentlichungsebene zugewiesenes AEM-Produktprofil, um Inhaltsquellen anzeigen oder verwalten zu können.

## Schritt 1a - Vorhandenen Index verbinden {#option-a}

Vorhandene Repository-Indizes werden automatisch in der Liste der Inhaltsquellen als Source-Typ AEM angezeigt, angezeigt durch das, was sie indizieren, z. B. Seiten, Assets oder Inhaltsfragmente. Sie beginnen **Eingeschränkt** und gesperrt, noch nicht über Content-KI durchsuchbar.

1. Melden Sie sich bei [Cloud Manager](https://my.cloudmanager.adobe.com/) an, wählen Sie Ihr Programm aus und öffnen Sie die Registerkarte **[!UICONTROL Content-KI]** Konfiguration) für die Umgebung, die Sie konfigurieren möchten.
1. Suchen Sie die Quelle, nach der Sie suchen möchten (z. B **„Seiten**) und klicken Sie auf das zugehörige Schlosssymbol. Dies können nur Benutzer mit dem Produktprofil **[!UICONTROL AEM]** Administratoren/-innen. **[!UICONTROL AEM]** Benutzer/-innen können Inhaltsquellen anzeigen, aber ihre Durchsuchbarkeit nicht ändern.
1. Lesen Sie die **Quelle durchsuchbar machen?** Seien Sie vorsichtig. Sie warnt davor, dass Apache Oak-Zugriffssteuerungslisten (ACLs) für diesen Index nicht erzwungen werden, sobald er durchsuchbar ist - jeder authentifizierte Benutzer kann seinen gesamten Inhalt abrufen. Überprüfen Sie **Ich verstehe, dass Zugriffssteuerungen (ACLs) nicht erzwungen werden und alle Inhalte in dieser Quelle durchsuchbar sind** und wählen Sie dann **Durchsuchbar machen** aus.
1. Bestätigen Sie die Statusänderungen in **Verfügbar**. Ein Warnsymbol bleibt neben der Quelle, um Sie daran zu erinnern, dass ACLs dafür umgangen werden.
1. Führen Sie eine Testsuche durch, um zu überprüfen, ob die Ergebnisse korrekt zurückgegeben werden.

>[!WARNING]
>
>Wenn Sie einen vorhandenen Index auf diese Weise durchsuchbar machen, werden Apache Oak-ACLs für diese Quelle vollständig umgangen. Jeder authentifizierte Benutzer kann seinen gesamten Inhalt über die Suche abrufen, unabhängig von seinen normalen Repository-Berechtigungen. Tun Sie dies nur für Quellen, bei denen Sie sich wohl fühlen, sie vollständig freizulegen.

>[!NOTE]
>
>Dieser Pfad passt gut, wenn Sie bereits über einen Index mit dem Inhalt Ihrer Site verfügen - zum Beispiel Ihren Seiteninhalt. Verwenden Sie diesen Index, anstatt einen separaten crawlen-Mechanismus einzurichten.

## Schritt 1b - Website Crawlen {#option-b}

Verwenden Sie diesen Pfad, wenn Sie noch keinen Suchindex für Ihre Site haben. Die Crawler von Content AI erstellt und aktualisiert eine für Sie. Dieser crawlen wird in Cloud Manager und **Handbuch auch als** bezeichnet.

1. Öffnen Sie **[!UICONTROL Registerkarte]** Content-KI-Konfiguration“ wie in Schritt 1a.
1. Wählen **[!UICONTROL Source erstellen]** aus und füllen Sie die Felder aus. Nur Benutzende mit dem Produktprofil **[!UICONTROL AEM-]** können neue Inhaltsquellen hinzufügen.

   | Feld | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Name der Content-KI-Konfiguration]** | Eine eindeutige Kennung für diese Quelle. Kann nach der Erstellung nicht mehr geändert werden. |
   | **[!UICONTROL Website-Adresse]** | Die zu crawlen Stamm-URL, z. B. `https://www.example.com/`. |
   | **[!UICONTROL Ausschließen von URLs]** | *(Optional)* URL-Muster, die beim Crawlen übersprungen werden sollen. |
   | **[!UICONTROL Aktualisierungshäufigkeit]** | Wöchentlich, Täglich, Täglich 4×, 60 Min. oder 15 Min. |

1. Wählen Sie **[!UICONTROL Quelle erstellen]** aus. Die Erfassung wird automatisch gestartet und die Quelle wechselt zu **Indizierung**.
1. Überwachen Sie den Status, bis er **Verfügbar**:

   | Status | Bedeutung |
   | --- | --- |
   | **Neu** | Source wurde gerade erstellt. Die automatische Akquise hat noch nicht begonnen. |
   | **Indizierung** | Crawlen und Indizierung werden ausgeführt. |
   | **Verfügbar** | Indizierung abgeschlossen - Bereit, Suchabfragen zu liefern. |

1. Wählen Sie das **search**-Symbol neben der Quelle aus und führen Sie eine Testabfrage aus, um zu bestätigen, dass Ihr Inhalt korrekt indiziert wurde.

>[!CAUTION]
>
>Eine Quelle steckt in **[!UICONTROL Indizierung]**? Die Akquise zuerst aus dem Menü (…) wiederholen. Wenn er immer noch nicht vorankommt, bestätigen Sie, dass die Website-Adresse öffentlich erreichbar ist und dass Ihre **[!UICONTROL URLs ausschließen]**-Muster nicht jede Seite herausfiltern.

## Schritt 2: Wählen Sie eine Such-Komponente {#choose-component}

Es gibt zwei Komponenten, die eine Suche auf eine Seite stellen können und auf verschiedenen Grundlagen basieren:

| | Schnellsuche (v3) mit semantischer Suche | AEM Content-KI-Suchen |
| --- | --- | --- |
| Fundament | Vorhandene Kernkomponente „Schnellsuche“, aktualisiert auf Version 3 | Neue, eigenständige Komponente - ruft die Content APIs direkt auf |
| Inhaltsquelle | Vorhandener Site-Inhalt, bereits in einem Index, für semantischen Abgleich angereichert | A Content AI Source (Schritt 1a oder 1b) |
| Generative Antwort | Nein - verbessert nur die Übereinstimmungsqualität der vorhandenen Ergebnisliste | Ja - optionale KI-generierte Zusammenfassung mit Quellen und Haftungsausschluss |
| Beste Anpassung | Sites, die bereits eine Schnellsuche verwenden und ein leichteres, inkrementelles Upgrade wünschen | Die vorgeschlagene Komponente für die gesamte Palette der Content-KI-Funktionen - semantische Suche, generative Suche und Suche in natürlicher Sprache (NLS) |

## Schnellsuche (v3) mit semantischer Suche {#quicksearch}

Wenn Ihre Site bereits die klassische [!DNL AEM] Schnellsuch-Komponente verwendet, fügt v3 einen **Opt-in-Umschalter KI-Suche** hinzu, Besuchende einschalten können - keine neue Komponente, kein Proxy oder Content Source erforderlich.

* Die Suche wird weiterhin über denselben JCR-/QueryBuilder-Pfad ausgeführt wie heute - es ändert sich nichts am Ergebnis-Servlet oder daran, wie Ergebnisse gerendert werden.
* Wenn ein Besucher den Umschalter aktiviert, stellt die Komponente der Abfrage einen speziellen Marker voran, der sie an die semantische Übereinstimmung weiterleitet, anstatt an den einfachen Keyword-Volltext.
* Es gibt keine Zusammenfassung einer Antwort auf diese Frage. Die Übereinstimmungsqualität der vorhandenen Ergebnisliste wird verbessert. Es wird keine generative KI-Antwort hinzugefügt.
* **Schritt 1 (Onboarding von Content-KI) gilt nicht für diesen Pfad.** Es gibt keinen Content Source zum Erstellen oder Verbinden - diese Komponente fragt Ihren vorhandenen Seitenindex direkt ab.

>[!NOTE]
>
>Wenn die semantische Suche nach dem Aktivieren des Umschalters nicht wie erwartet funktioniert, erstellen Sie ein Support-Ticket.

Dieser Pfad eignet sich gut, wenn Sie ein inkrementelles Upgrade für die semantische Suche wünschen, ohne eine neue Komponente oder Inhaltsquellen zu übernehmen. Es ist nicht der richtige Weg, wenn Sie ein Erlebnis mit generativen Antworten wünschen. Verwenden Sie dazu AEM-Inhaltsdaten.

## AEM Content-KI-Suchen {#gensearch}

AEM-Inhaltsfragmente sind eine [!DNL AEM] Kernkomponente, mit der Besuchende eine Inhalts-Source direkt von einer Seite aus durchsuchen können. Sie bietet sowohl semantische KI-Suchen als auch generative Suchfunktionen.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Generative Suchfunktionen werden separat über eine KI-SKU erworben. Wenden Sie sich an Ihren Adobe-Vertriebsmitarbeiter, um sie für Ihr Konto zu aktivieren.

### Voraussetzungen {#gensearch-prerequisites}

* [!DNL AEM] in Ihrem Projekt installierten Kernkomponenten.
* Mindestens ein Content Source wurde bereits erstellt und befindet **im Status** Verfügbar“.
* Der **AEM Content AI Client** OSGi-Konfiguration (`ContentAIClientImpl`), die sowohl in der Autoren- als auch in der Veröffentlichungsinstanz eingerichtet ist, verfügt über gültige API-Anmeldeinformationen und eine standardmäßige Content Source.

Das vollständige Setup-Handbuch - Bereitstellung der Komponente für Autoren, Verkabelung der Client-Bibliothek und Konfiguration des Dialogfelds - finden Sie in der [Kernkomponenten-Dokumentation](https://www.adobe.com/go/aem_cmp_library_de).

## Herzlichen Glückwunsch! {#congratulations}

Sie haben Ihre semantischen und generativen Suchfunktionen erfolgreich eingerichtet.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Nächste Schritte {#next-steps}

* [Adobe Developer Console-Projekt einrichten](setup-adc-project.md) - Erstellen Sie das ADC-Projekt und die Anmeldedaten, die Sie zum direkten Aufrufen der Content AI-API benötigen.
* [Content AI-API-Referenz](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Abfragen indizierter Inhalte mithilfe semantischer, generativer oder hybrider Suchendpunkte.
* [Dokumentation zu Kernkomponenten](https://www.adobe.com/go/aem_cmp_library_de) - Weitere Informationen zu Proxy-Komponenten und Vorlagenrichtlinien.

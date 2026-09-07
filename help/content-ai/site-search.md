---
title: Erste Schritte mit der AEM-Content-KI-Suche
description: In diesem Handbuch wird erläutert, wie Sie die Suche mit Content-KI in Ihrer Website aktivieren. Verbinden Sie Ihre Inhalte und wählen Sie dann eine Suchkomponente aus, um sie Besuchenden anzuzeigen.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM-Content-KI, AEM-Content-KI-Suche, GenSearch, Schnellsuche, Content-KI-Quellen, Akquise, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: ht
source-wordcount: '1487'
ht-degree: 100%

---


# Erste Schritte mit der AEM-Content-KI-Suche

Die herkömmliche Site-Suche gleicht die Wörter, die eine Besucherin bzw. ein Besucher eingibt, mit den Wörtern in Ihrem Inhalt ab. Dies funktioniert gut, wenn Besuchende dieselbe Terminologie verwenden wie Ihre Inhalte – aber es versagt in dem Moment, in dem sie eine Frage stellen, eine Absicht zum Ausdruck bringen oder etwas einfach anders formulieren. Die Suche ist eines der deutlichsten Signale für die Besucherabsicht auf einer Website, sodass eine fehlgeschlagene Übereinstimmung oft eine fehlgeschlagene Journey bedeutet: Inhalte werden nicht gefunden, Interaktionen werden reduziert und Konversionen gehen verloren. Besuchende erwarten zunehmend, dass die Suchfunktion versteht, was sie meinen, und nicht nur was sie eingegeben haben – und genau diese absichtsorientierte Grundlage macht generative Antworten überhaupt erst möglich.

Die AEM-Content-KI-Suche ersetzt die Suchfunktion Ihrer Website nicht – sie entwickelt sie weiter: vom Abgleich von Schlüsselwörtern über das Verstehen von Bedeutung und Absicht bis hin zur direkten Beantwortung von Fragen. Die semantische Suche ergänzt Ihre bestehende Suchfunktion um eine absichtsorientierte Suche und zeigt relevante Inhalte auch dann an, wenn die Suchanfrage nicht genau mit dem Wortlaut des Inhalts übereinstimmt. Die generative Suche baut auf derselben Suchgrundlange auf, um kontextbezogene, generierte Antworten zu erzeugen, die auf dem Inhalt Ihrer Website basieren – ein spezieller Schritt, der nicht mit dem semantischen Abruf gleichzusetzen ist.

Für Besuchende bedeutet dies eine bessere Relevanz, Unterstützung in natürlicher Sprache, weniger Suchvorgänge ohne Ergebnis und schnellere Antworten. Für Ihr Unternehmen bedeutet dies eine bessere Abstimmung der Suchabsicht, eine verbesserte Auffindbarkeit von Inhalten und eine KI-fähige Suchgrundlage – ohne dass Sie Ihr Sucherlebnis von Grund auf neu aufbauen müssen. Und für Ihr Team ist es eine inkrementelle Aktualisierung: Ihre bestehende Suchkomponente kann Schritt für Schritt von lexikalischen zu semantischen und dann zu generativen Funktionen wechseln, und es ist keine völlig neue Implementierung erforderlich.

Um dorthin zu gelangen, müssen Sie zwei Entscheidungen treffen: Wie Ihre Inhalte in die Content-KI gelangen und welche Komponente sie für Besucher bzw. Besucherinnen bereithält. Verbinden Sie Ihre Inhalte und fügen Sie dann eine Suchkomponente zu einer Seite hinzu. Ihre Site ist dann bereit, Besuchenden die relevantesten Ergebnisse und absichtsbasierte Antworten zu geben.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Bedingungen erfüllt sind:

* Sie verfügen über ein aktives Cloud Manager-Programm mit mindestens einer AEM as a Cloud Service-Umgebung.
* Ihrem Benutzer bzw. Ihrer Benutzerin ist das Produktprofil **[!UICONTROL AEM-Benutzende]** (zum Anzeigen von Inhaltsquellen) und/oder **[!UICONTROL AEM-Admins]** (zum Erstellen und Bearbeiten dieser Quellen) zugewiesen, und zwar auf der Ebene **Veröffentlichen** – Content-KI indiziert veröffentlichte Inhalte, nicht jedoch erstellte Inhalte. Das vollständige Verfahren finden Sie unter [Zuweisen einer Benutzerin bzw. eines Benutzers zu einem AEM-Produktprofil](contentsources.md#assign-product-profile).
* Das Produktprofil der Umgebung wurde in der **Adobe Admin Console** bereitgestellt.

>[!NOTE]
>
>Der Zugriff auf Cloud Manager allein reicht nicht aus. Ein Benutzer bzw. eine Benutzerin benötigt außerdem ein auf der Veröffentlichungsebene zugewiesenes AEM-Produktprofil, um Inhaltsquellen anzeigen oder verwalten zu können.

## Schritt 1a – Verbinden eines vorhandenen Index {#option-a}

Vorhandene Repository-Indizes werden automatisch in der Liste „Inhaltsquellen“ als „Quellentyp AEM“ angezeigt – gekennzeichnet durch das, was sie indizieren, z. B. Seiten, Assets oder Inhaltsfragmente. Sie beginnen als **Eingeschränkt** und gesperrt, noch nicht über Content-KI durchsuchbar.

1. Melden Sie sich bei [Cloud Manager](https://my.cloudmanager.adobe.com/) an, wählen Sie Ihr Programm aus und öffnen Sie die Registerkarte **[!UICONTROL Content-KI-Konfiguration]** für die Umgebung, die Sie konfigurieren möchten.
1. Ermitteln Sie die Quelle, in der Sie suchen möchten (z. B. **Seiten**) und klicken Sie auf das zugehörige Schlosssymbol. Nur Benutzende mit dem Produktprofil **[!UICONTROL AEM-Admins]** können diesen Vorgang ausführen – **[!UICONTROL AEM-Benutzende]** können Inhaltsquellen anzeigen, ihre Durchsuchbarkeit aber nicht ändern.
1. Lesen Sie die Informationen im Dialogfeld **Quelle durchsuchbar machen?** sorgfältig. Es wird darauf hingewiesen, dass die Zugriffskontrolllisten (ACLs) von Apache Oak für diesen Index nicht mehr erzwungen werden, sobald er durchsuchbar ist – alle authentifizierten Benutzenden können dann auf den gesamten Inhalt zugreifen. Aktivieren Sie die Option **Ich verstehe, dass Zugriffssteuerungen (ACLs) nicht erzwungen werden und alle Inhalte in dieser Quelle durchsuchbar sind** und wählen Sie dann **Durchsuchbar machen** aus.
1. Bestätigen Sie die Statusänderungen auf **Verfügbar**. Neben der Quelle wird weiterhin ein Warnsymbol angezeigt, um Sie daran zu erinnern, dass ACLs dafür umgangen werden.
1. Führen Sie eine Testsuche durch, um zu überprüfen, ob die Ergebnisse korrekt zurückgegeben werden.

>[!WARNING]
>
>Wenn Sie einen vorhandenen Index auf diese Weise durchsuchbar machen, werden Apache Oak-ACLs für diese Quelle vollständig umgangen. Alle authentifizierten Benutzenden können ihren gesamten Inhalt über die Suche abrufen, unabhängig von ihren normalen Repository-Berechtigungen. Gehen Sie so nur für Quellen vor, bei denen Sie sich wohl damit führen, sie vollständig offenzulegen.

>[!NOTE]
>
>Dieser Weg eignet sich gut, wenn Sie bereits über einen Index mit dem Inhalt Ihrer Site verfügen – zum Beispiel Ihren Seiteninhalt. Verwenden Sie diesen Index, anstatt einen separaten Crawling-Mechanismus einzurichten.

## Schritt 1b – Crawlen einer Website {#option-b}

Nutzen Sie diesen Weg, wenn Sie noch keinen Suchindex für Ihre Site haben. Der Crawler von Content-KI erstellt und aktualisiert einen für Sie. Dieser Crawling-Prozess wird überall in Cloud Manager und in diesem Handbuch auch als **Akquise** bezeichnet.

1. Öffnen Sie die Registerkarte **[!UICONTROL Content-KI-Konfiguration]** (wie in Schritt 1a).
1. Wählen Sie **[!UICONTROL Quelle erstellen]** aus und füllen Sie die Felder aus. Nur Benutzende mit dem Produktprofil **[!UICONTROL AEM-Admins]** können neue Inhaltsquellen hinzufügen.

   | Feld | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Name der Content-KI-Konfiguration]** | Eine eindeutige Kennung für diese Quelle. Kann nach der Erstellung nicht mehr geändert werden. |
   | **[!UICONTROL Website-Adresse]** | Die Stamm-URL, die gecrawlt werden soll, zum Beispiel `https://www.example.com/`. |
   | **[!UICONTROL Ausschließen von URLs]** | *(Optional)* URL-Muster, die beim Crawlen übersprungen werden sollen. |
   | **[!UICONTROL Aktualisierungshäufigkeit]** | Wöchentlich, Täglich, Täglich 4×, 60 Min. oder 15 Min. |

1. Wählen Sie **[!UICONTROL Quelle erstellen]** aus. Die Erfassung wird automatisch gestartet und die Quelle wechselt zu **Indizierung**.
1. Überwachen Sie den Status, bis er **Verfügbar** ist:

   | Status | Bedeutung |
   | --- | --- |
   | **Neu** | Quelle gerade erstellt; die automatische Akquise wurde noch nicht gestartet. |
   | **Indizierung** | Crawlen und Indizierung werden ausgeführt. |
   | **Verfügbar** | Indizierung abgeschlossen – bereit, Suchabfragen zu liefern. |

1. Wählen Sie das Symbol für die **Suche** neben der Quelle aus und führen Sie eine Testabfrage aus, um zu bestätigen, dass Ihr Inhalt korrekt indiziert wurde.

>[!CAUTION]
>
>Eine Quelle, die bei der **[!UICONTROL Indizierung]** hängen geblieben ist? Wiederholen Sie die Akquise zuerst über das Menü mit den drei Punkten (…). Wenn weiterhin kein Fortschritt verzeichnet werden kann, überprüfen Sie, ob die Adresse der Website öffentlich erreichbar ist und ob Ihre Muster für **[!UICONTROL URLs ausschließen]** nicht jede Seite herausfiltern.

## Schritt 2: – Auswählen einer Suchkomponente {#choose-component}

Es gibt zwei Komponenten, mit denen eine Suchfunktion auf einer Seite eingebunden werden kann, die auf verschiedenen Grundlagen basieren:

| | Schnellsuche (v3) mit semantischer Suche | Content-KI-Suche für AEM |
| --- | --- | --- |
| Fundament | Vorhandene Kernkomponente „Schnellsuche“, aktualisiert auf Version 3 | Neue, eigenständige Komponente – ruft die Content-KI-APIs direkt auf |
| Inhaltsquelle | Vorhandener Website-Inhalt, bereits in einem Index, für semantischen Abgleich angereichert | Eine Content-KI-Quelle (Schritt 1a oder 1b) |
| Generative Antwort | Nein – verbessert nur die Übereinstimmungsqualität der vorhandenen Ergebnisliste | Ja – optionale KI-generierte Zusammenfassung mit Quellen und Haftungsausschluss |
| Am besten geeignet | Website, bei denen bereits die Schnellsuche verwendet wird und die ein leichteres, inkrementelles Upgrade wünschen | Die vorgeschlagene Komponente für die gesamte Palette der Content-KI-Funktionen – semantische Suche, generative Suche und Suche in natürlicher Sprache (NLS) |

## Schnellsuche (v3) mit semantischer Suche {#quicksearch}

Wenn Ihre Website bereits die klassische Schnellsuchkomponente von [!DNL AEM] verwendet, fügt v3 einen Opt-in-Umschalter für die **KI-Suche** hinzu, den Besuchende aktivieren können – eine neue Komponente, ein Proxy oder eine Inhaltsquelle sind nicht erforderlich.

* Die Suche wird weiterhin über denselben JCR-/QueryBuilder-Pfad ausgeführt wie bisher – es ändert sich nichts am Ergebnis-Servlet oder daran, wie Ergebnisse gerendert werden.
* Wenn ein Besucher bzw. eine Besucherin den Umschalter aktiviert, stellt die Komponente der Abfrage einen speziellen Marker voran, der sie an die semantische Übereinstimmung weiterleitet, anstatt an den einfachen Keyword-Volltext.
* Dabei gibt es keine Zusammenfassung einer Antwort auf diese Frage. Die Übereinstimmungsqualität der vorhandenen Ergebnisliste wird verbessert. Es wird keine generative KI-Antwort hinzugefügt.
* **Schritt 1 (Onboarding von Content-KI) gilt nicht für diesen Weg.** Es muss keine Inhaltsquelle erstellt oder verbunden werden – diese Komponente fragt Ihren vorhandenen Seitenindex direkt ab.

>[!NOTE]
>
>Wenn die semantische Suche nach dem Aktivieren des Umschalters nicht wie erwartet funktioniert, erstellen Sie ein Support-Ticket.

Dieser Weg eignet sich gut, wenn Sie ein inkrementelles Upgrade für die semantische Suche wünschen, ohne eine neue Komponente oder Inhaltsquellen zu übernehmen. Es ist nicht der richtige Weg, wenn Sie ein Erlebnis mit generativen Antworten wünschen. Verwenden Sie dazu die Content-KI-Suche für AEM.

## Content-KI-Suche für AEM {#gensearch}

Die Content-KI-Suche für AEM ist eine Kernkomponente von [!DNL AEM], mit der Besuchende eine Inhaltsquelle direkt von einer Seite aus durchsuchen können. Sie bietet sowohl semantische als auch generative Suchfunktionen.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Generative Suchfunktionen werden separat über eine KI-SKU erworben. Wenden Sie sich an Ihre Adobe-Vertriebsmitarbeitenden, um diese für Ihr Konto zu aktivieren.

### Voraussetzungen {#gensearch-prerequisites}

* In Ihrem Projekt installierte Kernkomponenten von [!DNL AEM].
* Mindestens eine Inhaltsquelle wurde bereits erstellt und weist den Status **Verfügbar** auf.
* Die OSGi-Konfiguration des **Content-KI-Clients für AEM** (`ContentAIClientImpl`), die sowohl in der Autoren- als auch in der Veröffentlichungsinstanz eingerichtet ist, verfügt über gültige API-Anmeldedaten und eine standardmäßige Inhaltsquelle.

Das vollständige Setup-Handbuch – Bereitstellung der Komponente für Autorinnen und Autoren, Einbinden der Client-Bibliothek und Konfiguration des Dialogfelds – finden Sie in der [Dokumentation zu den Kernkomponenten](https://www.adobe.com/go/aem_cmp_library_de).

## Herzlichen Glückwunsch! {#congratulations}

Sie haben Ihre semantischen und generativen Suchfunktionen erfolgreich eingerichtet.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Nächste Schritte {#next-steps}

* [Einrichten eines Projekts in der Adobe Developer Console](setup-adc-project.md) – Erstellen Sie das ADC-Projekt und die Anmeldedaten, die Sie für den direkten Aufruf der Content-KI-API benötigen.
* [Referenz zur Content-KI-API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) – Fragen Sie Ihre indizierten Inhalte mithilfe semantischer, generativer oder hybrider Suchendpunkte ab.
* [Dokumentation zu Kernkomponenten](https://www.adobe.com/go/aem_cmp_library_de) – Weitere Informationen zu Proxy-Komponenten und Vorlagenrichtlinien.

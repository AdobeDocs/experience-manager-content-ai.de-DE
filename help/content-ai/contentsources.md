---
title: Einrichten und Verwalten von Content-KI-Quellen
description: Erfahren Sie, wie Sie Content-KI für AEM in Cloud Manager konfigurieren, indem Sie Ihre erste Inhaltsquelle einrichten und die Erfassung auslösen.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: Content-KI für AEM, Content-KI-Quellen, Erfassung, Cloud Manager, Adobe Developer Console
source-git-commit: d40fcb4a41c717ef4e6c82d95a36976b1f4de825
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 61%

---


# Einrichten und Verwalten von Content-KI-Quellen

Dieses Handbuch führt Sie durch die Einrichtung von Content-KI-Quellen in Cloud Manager – von der Erfüllung der Voraussetzungen über die Erstellung einer Inhaltsquelle bis hin zur Bestätigung, dass diese indiziert und verfügbar ist.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Bedingungen erfüllt sind:

* Sie verfügen über ein aktives Cloud Manager-Programm mit mindestens einer AEM as a Cloud Service-Umgebung.
* Ihre Benutzerin bzw. Ihr Benutzer ist dem Produktprofil **AEM-** für die Zielumgebung zugewiesen, über das die Benutzerin bzw. der Benutzer Inhaltsquellen anzeigen kann.
* Ihre Benutzerin bzw. Ihr Benutzer ist dem Produktprofil **AEM-** für die Zielumgebung zugewiesen, mit dem die Benutzerin bzw. der Benutzer Inhaltsquellen erstellen und bearbeiten kann. Der Zugriff auf Cloud Manager allein ist nicht ausreichend - siehe [Zuweisen eines Benutzers zu einem AEM-Produktprofil](#assign-product-profile) unten.
* Das Umgebungs-Produktprofil wurde in **Adobe Admin Console bereitgestellt**.

## Zuweisen eines Benutzers zu einem AEM-Produktprofil {#assign-product-profile}

Gehen Sie wie folgt vor, um einem Benutzer Zugriff auf [!DNL Adobe Experience Manager] as a Cloud Service für eine bestimmte Umgebung zu gewähren. Weisen Sie das Profil zu, das dem Zugriff entspricht, den der Benutzer benötigt:

* **[!UICONTROL AEM-]**: Inhaltsquellen anzeigen.
* **[!UICONTROL AEM-]**: Erstellen und Bearbeiten von Inhaltsquellen.

>[!NOTE]
>
>Benutzer müssen einem AEM-Produktprofil angehören, z. B. **[!UICONTROL AEM-]** oder **[!UICONTROL AEM-]**, um auf AEM zugreifen zu können. Der Zugriff auf Cloud Manager allein reicht nicht aus.

Um diese Profile zuzuweisen, müssen Sie Systemadministrator mit dem Cloud Manager-Produktprofil [!UICONTROL Geschäftsinhaber] sein. Halten Sie den Namen und die E-Mail-Adresse des Benutzers bereit.

1. Navigieren Sie in [&#128279;](https://my.cloudmanager.adobe.com/) zu Ihrem Programm und wählen Sie &quot;**[!UICONTROL verwalten“]** die Zielumgebung aus. Für diese Umgebung wird eine neue Registerkarte [!DNL Adobe Admin Console].
1. Wählen Sie das Produktprofil **[!UICONTROL AEM-]** oder **[!UICONTROL AEM-]** für die **Veröffentlichungs** Ebene aus, z. B. `AEM Administrators - publish - Program 12345 - Environment 67890`. Content AI indiziert veröffentlichte Inhalte, sodass das Profil auf Veröffentlichungsebene zugewiesen werden muss, nicht auf der Autorenebene.
1. Wählen Sie **[!UICONTROL Benutzende hinzufügen]** aus.
1. Geben Sie den Namen und die E-Mail-Adresse des Benutzers ein und speichern Sie dann die Änderung. Der Benutzer wird dem Produktprofil hinzugefügt.

Wiederholen Sie diese Schritte für jede Umgebung, in der der Benutzer Zugriff benötigt, z. B. Entwicklung, Staging oder Produktion.

>[!CAUTION]
>
>Die Standardproduktprofile mit den Namen **[!UICONTROL AEM-Administratoren oder {]**} AEM-Benutzer dürfen nicht bearbeitet oder gelöscht **.** Beim Umbenennen von **[!UICONTROL AEM]** Administratoren werden Administratorrechte von allen ihnen zugewiesenen entfernt.

### Zuweisung überprüfen {#verify-assignment}

So überprüfen Sie, ob die Zuweisung erfolgreich war:

1. Öffnen Sie [!DNL Admin Console] das von Ihnen zugewiesene Produktprofil erneut.
1. Bestätigen Sie, dass der Benutzer in der Mitgliederliste angezeigt wird.

Wenn Sie Zugriffs- oder Token-Probleme beheben möchten, vergewissern Sie sich, dass der Benutzer direkt zum Produktprofil hinzugefügt wird und nicht nur über eine Gruppe.

## Schritt 1: Öffnen der Registerkarte für die Content-KI-Konfiguration {#open-tab}

1. Melden Sie sich bei [Cloud Manager](https://my.cloudmanager.adobe.com/) an und wählen Sie Ihr Programm aus.

   ![Cloud Manager-Startseite mit der Programmkarte](../assets/content-ai-onboarding-step-1.png)

1. Suchen Sie auf der Seite **[!UICONTROL Programmüberblick]** den Abschnitt **[!UICONTROL Umgebungen]** und wählen Sie die Umgebung aus, die Sie konfigurieren möchten.

   ![Programmüberblick mit einer hervorgehobenen Produktionsumgebung](../assets/content-ai-onboarding-step-2.png)

1. Wählen Sie auf der Detailseite der Umgebung die Registerkarte **[!UICONTROL Content-KI-Konfiguration]** aus.

   ![Detailseite der Umgebung mit hervorgehobener Registerkarte „Content-KI-Konfiguration“](../assets/content-ai-onboarding-step-3.png)

## Schritt 2: Erstellen einer Content-KI-Quelle {#create-source}

Eine Inhaltsquelle definiert die Website, die von Content-KI gecrawlt und indiziert wird.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Content-KI-Konfiguration]** die Option **[!UICONTROL Quelle erstellen]** aus.

   ![Registerkarte „Content-KI-Konfiguration“ mit der Schaltfläche „Quelle erstellen“](../assets/content-ai-onboarding-step-4.png)

1. Füllen Sie im Dialogfeld **[!UICONTROL Neue Content-KI-Quelle erstellen/hinzufügen]** die folgenden Felder aus:

   | Feld | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Name der Content-KI-Konfiguration]** | Eine eindeutige Kennung für diese Quelle (z. B. `my-site-index`). Kann nach der Erstellung nicht mehr geändert werden. |
   | **[!UICONTROL Beschreibung]** | *(Optional)* Eine kurze Beschreibung der Inhaltsquelle. |
   | **[!UICONTROL Website-Adresse]** | Die Stamm-URL der zu crawlenden Website (z. B. `https://www.example.com/`). |
   | **[!UICONTROL Ausschließen von URLs]** | *(Optional)* URL-Muster, die beim Crawlen übersprungen werden sollen. |
   | **[!UICONTROL Aktualisierungshäufigkeit]** | Wie oft Content-KI die Quelle erneut crawlt: Wöchentlich, Täglich, Täglich (4×), Alle 60 Min. oder Alle 15 Min. |

   ![Dialogfeld „Content-KI-Quelle erstellen“ mit ausgefüllten Feldern für Name und Website-Adresse und hervorgehobener Schaltfläche „Quelle erstellen“](../assets/content-ai-onboarding-step-5-0.png)

   ![Dropdown-Menü „Aktualisierungshäufigkeit“ mit den verfügbaren Optionen](../assets/content-ai-onboarding-step-5-1.png)

1. Wählen Sie **[!UICONTROL Quelle erstellen]** aus. Die Akquise wird automatisch gestartet und die Quelle wechselt zu **Indizierung**.

   ![Liste der Inhaltsquellen, in der die neu erstellte Quelle im Indizierungsstatus angezeigt wird](../assets/content-ai-onboarding-step-6.png)

## &#x200B;3. Schritt - Akquise erneut ausführen {#trigger-acquisition}

Die Akquise wird automatisch ausgeführt, wenn Sie eine Quelle erstellen, und dann nach dem Zeitplan, der durch die **[!UICONTROL Aktualisierungshäufigkeit“ festgelegt]**. Sie können eine Ausführung auch jederzeit manuell als Trigger festlegen, z. B. um die Indizierung sofort nach der Veröffentlichung neuer Inhalte neu durchzuführen.

1. Wählen Sie in der Quellenliste das Symbol **Weitere Aktionen** (…) neben Ihrer Quelle aus und anschließend **[!UICONTROL Erfassung auslösen]**.

   ![Content-KI-Quellenliste mit geöffnetem Menü „Weitere Aktionen“ und hervorgehobener Option „Erfassung auslösen“](../assets/content-ai-onboarding-step-7.png)

1. Überprüfen Sie im Dialogfeld **[!UICONTROL Erfassung auslösen]** die Quelldetails – **[!UICONTROL Inhaltsquelle]**, **[!UICONTROL Letzte Ausführung]** und **[!UICONTROL Nächste geplante Ausführung]** – und wählen Sie **[!UICONTROL Auslösen]** aus.

   ![Bestätigungsdialogfeld „Erfassung auslösen“](../assets/content-ai-onboarding-step-8.png)

## Schritt 4: Überwachen des Indizierungsstatus {#monitor-status}

Nach dem Beginn der Erfassung wird der Quellenstatus in Echtzeit aktualisiert.

| Status | Bedeutung |
| --- | --- |
| **Neu** | Source hat gerade erstellt. Die automatische Akquise hat noch nicht begonnen. Dieser Status ist kurz. |
| **Indizierung** | Erfassung läuft; Inhalte werden gecrawlt und indiziert. |
| **Verfügbar** | Indizierung abgeschlossen; die Quelle ist bereit für Suchabfragen. |

![Liste der Inhaltsquellen mit dem Indizierungsstatus](../assets/content-ai-onboarding-step-9.png)

![Liste der Inhaltsquellen mit dem Status „Verfügbar“](../assets/content-ai-onboarding-step-10.png)

Warten Sie, bis der Status **Verfügbar** erreicht, bevor Sie den Index durchsuchen oder die API testen.

## Schritt 5: Durchsuchen indizierter Inhalte {#search-content}

Sobald der Quellenstatus **Verfügbar** lautet, können Sie Suchabfragen direkt in Cloud Manager ausführen, um zu überprüfen, ob die Inhalte korrekt indiziert wurden.

1. Wählen Sie in der Quellliste das Symbol **Suchen** (Lupe) neben Ihrer Quelle aus.

   ![Liste der Inhaltsquellen mit hervorgehobenem Suchsymbol in einer verfügbaren Quelle](../assets/content-ai-onboarding-step-13.png)

1. Geben Sie eine Abfrage in das Suchfeld ein. Die Ergebnisse zeigen eine Liste übereinstimmender Elemente mit einem Übereinstimmungswert und dem Inhaltstyp (z. B. **PAGE** oder **PDF**). Wenn Sie ein Ergebnis auswählen, wird rechts eine Vorschau geöffnet.

   ![Suchbereich mit einer Abfrage, übereinstimmenden Ergebnissen mit Übereinstimmungswerten und einem Vorschaufenster für das Top- Ergebnis](../assets/content-ai-onboarding-step-14.png)

## Ändern oder Löschen einer Quelle {#modify-source}

### Ändern einer Quelle {#modify}

So aktualisieren Sie eine Quellenkonfiguration nach der Erstellung:

1. Wählen Sie in der Quellenliste das Symbol **Weitere Aktionen** (…) neben der Quelle aus und anschließend **[!UICONTROL Bearbeiten]**.

   ![Liste der Inhaltsquellen mit geöffnetem Menü „Weitere Aktionen“ und hervorgehobener Option „Bearbeiten“](../assets/content-ai-onboarding-step-11.png)

1. Aktualisieren Sie im Dialogfeld **[!UICONTROL Content-KI-Quelle ändern]** nach Bedarf die **[!UICONTROL Beschreibung]**, die **[!UICONTROL Website-Adresse]**, **[!UICONTROL auszuschließende URLs]** oder die **[!UICONTROL Aktualisierungshäufigkeit]**. Der **[!UICONTROL Name der Content-KI-Konfiguration]** ist schreibgeschützt und kann nicht geändert werden.

   ![Das Dialogfeld „Content AI Source ändern“ mit hervorgehobenen bearbeitbaren Feldern](../assets/content-ai-onboarding-step-12.png)

1. Wählen **[!UICONTROL Speichern]**, um die Änderungen anzuwenden. Die Quellenliste wird mit Ihren Änderungen aktualisiert.

### Löschen einer Quelle {#delete}

1. Wählen Sie in der Quellliste das Symbol **Mehr Aktionen** (…) neben der Quelle aus und klicken Sie dann auf **[!UICONTROL Löschen]**.

   >[!WARNING]
   >
   >Das Löschen einer Quelle ist dauerhaft. Alle indizierten Inhalte für diese Quelle werden entfernt und stehen für Suchabfragen nicht mehr zur Verfügung.

Nach dem Löschen wird die Quelle nicht mehr in der Liste angezeigt.

## Nächste Schritte {#next-steps}

* [Einrichten eines Projekts in der Adobe Developer Console](setup-adc-project.md) – Erstellen Sie das ADC-Projekt und die Anmeldeinformationen, die Sie für den Aufruf der API benötigen.
* [Referenzieren der Content-KI-API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) – Fragen Sie Ihre indizierten Inhalte über Endpunkte für die semantische Suche, die Volltextsuche oder die Hybridsuche ab.

## Fehlerbehebung {#troubleshooting}

* **Die Quelle verbleibt über einen längeren Zeitraum im Status [!UICONTROL Indizierung].** Wiederholen Sie die Erfassung über das Menü mit den drei Punkten (…). Wenn der Status nach einer zweiten Ausführung nicht voranschreitet, überprüfen Sie, ob die **[!UICONTROL Website-Adresse]** öffentlich erreichbar ist und die Muster unter **[!UICONTROL URLs ausschließen]** nicht alle Seiten herausfiltern.
* **Die Quelle wechselt nach einer Ausführung wieder in den Status [!UICONTROL Neu].** Der Crawler konnte keine Seiten von der konfigurierten Stamm-URL abrufen. Stellen Sie sicher, dass die URL mit `200 OK` antwortet und die Website automatisierte Anfragen nicht blockiert.
* **[!UICONTROL Suchen] liefert keine Ergebnisse für eine Quelle im Status [!UICONTROL Verfügbar].** Die Indizierung war erfolgreich, aber es stimmten keine Inhalte mit der Abfrage überein. Versuchen Sie es mit einer allgemeineren Abfrage oder überprüfen Sie, ob die gecrawlten URLs die von Ihnen erwarteten Seiten enthalten.

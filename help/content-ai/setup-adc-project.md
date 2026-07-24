---
title: Einrichten eines Projekts in der Adobe Developer Console für Content-KI für AEM
description: Erfahren Sie, wie Sie ein Projekt in der Adobe Developer Console einrichten und API-Aufrufe an Dienste der Content-KI für AEM mithilfe von Server-zu-Server- oder API-Schlüsselauthentifizierung authentifizieren.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: Content-KI für AEM, Adobe Developer Console, Authentifizierung, Server-zu-Server, API-Schlüssel, Zugriffstoken
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: ht
source-wordcount: '714'
ht-degree: 100%

---


# Einrichten eines Projekts in der Adobe Developer Console {#configure-adc-project}

Um die Services-API der Content-KI für AEM aufzurufen, benötigen Sie Anmeldedaten, die von einem Projekt in der Adobe Developer Console (ADC) ausgestellt wurden. Diese Seite führt Sie durch die Erstellung des Projekts, die Auswahl einer Authentifizierungsmethode und die Generierung der Anmeldedaten, die Sie bei jeder API-Anfrage angeben.

Wechseln Sie zur [Adobe Developer Console](https://developer.adobe.com/console/) Ihrer Organisation, um zu beginnen.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* Sie haben Zugriff auf die [Adobe Developer Console](https://developer.adobe.com/console/) für Ihre Organisation.
* Ihnen ist die Rolle **Entwickler** im Produktprofil für die Dienste der Content-KI für AEM in der **Adobe Admin Console** zugewiesen. Ohne diese Rolle wird die **[!UICONTROL API-Karte der Content-KI-Dienste für AEM]** als deaktiviert angezeigt und die Authentifizierungsoption **[!UICONTROL Server-zu-Server]** ist ausgeblendet.
* Sie kennen die Programm- und Umgebungsnummern für das Produktprofil, das Sie auswählen möchten (z. B. `AEM User - publish - Program 12345 - Environment 67890`).
* Ihnen ist die Rolle **[Systemadmin](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-admin-console/admin-roles)** in der Admin Console für das Programm zugewiesen. In dieser Rolle können Sie Produktprofile verwalten und Benutzende der Umgebung zuweisen.

## Auswählen einer Authentifizierungsmethode {#choose-auth}

Die Dienste der Content-KI für AEM unterstützen zwei Authentifizierungsmethoden. Wählen Sie die Methode aus, die Ihrer Integration entspricht:

| Methode | Am besten geeignet für |
| --- | --- |
| [Server-zu-Server](#s2s-auth) | Backend-Dienste, die die API ohne Benutzerinteraktion aufrufen. Gibt ein kurzlebiges Zugriffstoken zurück. |
| [API-Schlüssel](#api-key-auth) | Client-seitige oder Browser-basierte Integrationen, die die API direkt aufrufen. Gibt einen langlebigen Schlüssel zurück, dessen Zugriffsbereich auf zulässige Domains beschränkt ist. |

## Server-zu-Server-Authentifizierung {#s2s-auth}

1. Wählen Sie **[!UICONTROL APIs und Dienste]** und anschließend **[!UICONTROL APIs]** aus.

   ![Developer Console mit APIs und Diensten](../assets/e2e-env-setup-28.png)

1. Filtern Sie nach **Content-KI-Diensten für AEM** und wählen Sie dann **[!UICONTROL Projekt erstellen]** aus, um ein neues Projekt zu starten, oder **[!UICONTROL API hinzufügen]**, wenn Sie den Dienst zu einem bestehenden Projekt hinzufügen.

   >[!NOTE]
   >
   >Wenn die API-Karte mit der Meldung „Lizenz erforderlich“ deaktiviert ist, ist Ihre AEM as a Cloud Service-Umgebung möglicherweise nicht modernisiert. Siehe [Modernisieren der AEM as a Cloud Service-Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?lang=de#modernization-of-aem-as-a-cloud-service-environment).

1. Wählen Sie im Dialogfeld **[!UICONTROL API konfigurieren]** die Authentifizierungsmethode **[!UICONTROL Server-zu-Server]** aus.

   ![Konfigurieren der API im Dialogfeld mit ausgewählter Option „Server-zu-Server“](../assets/e2e-env-setup-29.png)

   >[!TIP]
   >
   >Wenn die Option „Server-zu-Server“ nicht verfügbar ist, wurde der Person, die die Integration einrichtet, im Produktprofil keine Entwicklungsrolle zugewiesen. Siehe [Aktivieren der Server-zu-Server-Authentifizierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

1. Benennen Sie die Anmeldedaten bei Bedarf um. Wählen Sie **[!UICONTROL Weiter]** aus.

   ![Schritt in der Adobe Developer Console zum Umbenennen der neuen Server-zu-Server-Anmeldedaten vor der Auswahl von „Weiter“](../assets/e2e-env-setup-30.png)

1. Wählen Sie das Produktprofil **[!UICONTROL AEM User - publish - Program XXX - Environment XXX]** und/oder **[!UICONTROL AEM User - author - Program XXX - Environment XXX]** aus und klicken Sie anschließend auf **[!UICONTROL Speichern]**.

   ![Produktprofilauswahl mit den AEM-Benutzerprofilen „publish“ und „author“ für das Zielprogramm und die Zielumgebung](../assets/e2e-env-setup-31.png)

1. Überprüfen Sie die API- und Authentifizierungskonfiguration.

   ![Überprüfungsbildschirm mit einer Zusammenfassung der ausgewählten API, der Authentifizierungsmethode und des Namens der Anmeldedaten](../assets/e2e-env-setup-33.png)

   ![Detailansicht des Überprüfungsbildschirms mit den zugewiesenen Produktprofilen für die Anmeldedaten](../assets/e2e-env-setup-34.png)

### Generieren eines Zugriffstokens {#generate-token}

1. Wechseln Sie in Ihrem ADC-Projekt zu **[!UICONTROL Anmeldedaten]** und wählen Sie **[!UICONTROL Zugriffstoken generieren]** aus.

   ![Seite für Anmeldedaten mit hervorgehobener Schaltfläche „Zugriffstoken generieren“](../assets/e2e-env-setup-32.png)

1. Fügen Sie das Token in den Header `Authorization` jeder API-Anfrage ein:

   ```http
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

   >[!WARNING]
   >
   >Speichern Sie das Token sicher. Es läuft ab und muss regelmäßig neu generiert werden.

## Authentifizierung per API-Schlüssel {#api-key-auth}

1. Wenn Sie die API für die Dienste der Content-KI für AEM zu Ihrem Projekt hinzufügen, wählen Sie im Dialogfeld **[!UICONTROL Authentifizierungsmethode auswählen]** die Option **[!UICONTROL API-Schlüssel]** aus.

   ![Auswählen der Authentifizierungsmethode „API-Schlüssel“](../assets/onboarding-api-key-01.png)

1. Bestätigen Sie die Anmeldedaten für den API-Schlüssel.

   ![Hinzufügen der Anmeldedaten für den API-Schlüssel](../assets/onboarding-api-key-02.png)

1. Um einzuschränken, welche Ursprünge den Schlüssel verwenden können, konfigurieren Sie zulässige Domains.

   ![Konfigurieren zulässiger Domains](../assets/onboarding-api-key-03.png)

1. Ihr API-Schlüssel (Client-ID) wird unter **[!UICONTROL Verbundene Anmeldedaten]** angezeigt. Wählen Sie **[!UICONTROL Kopieren]**.

   ![Kopieren des API-Schlüssels aus den verbundenen Anmeldedaten](../assets/onboarding-api-key-04.png)

1. Fügen Sie den Schlüssel in jede API-Anfrage ein:

   ```http
   x-api-key: YOUR_API_KEY
   ```

   Ihr Projekt ist jetzt bereit. Verwenden Sie den Schlüssel bei jeder Anfrage an die Dienste der Content-KI für AEM.

## Nächste Schritte {#next-steps}

* [Steuern von Inhaltsquellen](contentsources.md) – Konfigurieren Sie eine Inhaltsquelle in Cloud Manager und lösen Sie die Erfassung aus.
* [Referenzieren der Content-KI-API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) – Verwenden Sie Ihr Zugriffstoken oder Ihren API-Schlüssel, um den indizierten Inhalt abzufragen.

---
title: Goedkeuring implementeren voor Platform Mobile SDK-implementaties
description: Leer hoe u toestemming implementeert in een mobiele app.
feature: Mobile SDK,Consent
jira: KT-14629
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Goedkeuring uitvoeren

Leer hoe u toestemming implementeert in een mobiele app.

Met de mobiele extensie Adobe Experience Platform Consent kunt u de verzameling met voorkeuren voor toestemming vanuit uw mobiele app inschakelen wanneer u de Adobe Experience Platform Mobile SDK en de Edge Network-extensie gebruikt. Meer informatie over de [Toegestane extensie](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/) in de documentatie.

## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Vraag de gebruiker om toestemming.
* Werk de extensie bij op basis van de gebruikersreactie.
* Leer hoe u de huidige status van toestemming krijgt.

## Goedkeuring aanvragen

Als u de zelfstudie vanaf het begin hebt gevolgd, zult u zich wellicht herinneren dat u de standaardtoestemming in de extensie Goedkeuring hebt ingesteld op **[!UICONTROL In behandeling - de gebeurtenissen van de Rij die voorkomen alvorens de gebruiker toestemmingsvoorkeur verstrekt.]**

Om met het verzamelen van gegevens te beginnen, moet u toestemming van de gebruiker krijgen. In een echte app wilt u de beste praktijken voor uw regio raadplegen. In deze zelfstudie krijgt u toestemming van de gebruiker door er gewoon om te vragen met een waarschuwing:

1. U wilt de gebruiker slechts eenmaal om toestemming vragen. U kunt dit doen door de toestemming van Mobile SDK met de vereiste vergunning voor het volgen te combineren gebruikend Apple [Transparantie-framework voor toepassingscontrole](https://developer.apple.com/documentation/apptrackingtransparency). In deze app gaat u ervan uit dat wanneer de gebruiker toestemming geeft om gebeurtenissen te volgen, deze toestemming geeft om gebeurtenissen te verzamelen.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator.

   Deze code toevoegen aan de `updateConsent` functie.

   ```swift
   // Update consent
   let collectConsent = ["collect": ["val": value]]
   let currentConsents = ["consents": collectConsent]
   Consent.update(with: currentConsents)
   MobileCore.updateConfigurationWith(configDict: currentConsents)
   ```

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL DisclaimerView]** in de projectnavigator van Xcode, die de mening is die na het installeren van of het opnieuw installeren van de toepassing en het beginnen van app voor de eerste keer wordt getoond. De gebruiker wordt gevraagd het bijhouden van gegevens te autoriseren per Apple [Transparantie-framework voor toepassingscontrole](https://developer.apple.com/documentation/apptrackingtransparency). Als de gebruiker autoriseert, werkt u ook de toestemming bij.

   Voeg de volgende code toe aan de `ATTrackingManager.requestTrackingAuthorization { status in` sluiting.

   ```swift
   // Add consent based on authorization
   if status == .authorized {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "y")
   }
   else {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "n")
   }
   ```

## Huidige status van toestemming ophalen

De mobiele extensie voor toestemming onderdrukt automatisch het bijhouden van wijzigingen / breidt deze uit op basis van de huidige waarde voor toestemming. U kunt ook zelf toegang krijgen tot de huidige staat van toestemming:

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Xcode&#39;s Project navigator.

   Voeg de volgende code toe aan de `getConsents` functie:

   ```swift
   // Get consents
   Consent.getConsents { consents, error in
      guard error == nil, let consents = consents else { return }
      guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
      guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
      Logger.aepMobileSDK.info("Consent getConsents: \(jsonStr)")
   }
   ```

2. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL HomeView]** in Xcode&#39;s Project navigator.

   Voeg de volgende code toe aan de `.task` modifier:

   ```swift
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

In het bovenstaande voorbeeld registreert u gewoon de toestemmingsstatus aan de console in Xcode. In een echt scenario, zou u het kunnen gebruiken om te wijzigen welke menu&#39;s of opties aan de gebruiker worden getoond.

## Valideren met betrouwbaarheid

1. Verwijder de toepassing van het apparaat of de simulator om het bijhouden en goedkeuren correct opnieuw in te stellen en te initialiseren.
1. Als u uw simulator of apparaat wilt aansluiten op Betrouwbaarheid, raadpleegt u de [installatie-instructies](assurance.md#connecting-to-a-session) sectie.
1. Wanneer u de app verplaatst van **[!UICONTROL Home]** scherm naar **[!UICONTROL Producten]** scherm en terug naar **[!UICONTROL Home]** scherm, moet u een **[!UICONTROL Respons voor constanten ophalen]** gebeurtenis in de betrouwbaarheidsinterface.
   ![toestemming valideren](assets/consent-update.png)


>[!SUCCESS]
>
>U hebt nu de toepassing ingeschakeld om de gebruiker bij de eerste start na de installatie (of herinstallatie) te vragen toestemming te geven met de SDK van Adobe Experience Platform Mobile.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Levenscyclusgegevens verzamelen](lifecycle-data.md)**

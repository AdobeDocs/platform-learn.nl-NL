---
title: Goedkeuring implementeren voor Platform Mobile SDK-implementaties
description: Leer hoe u toestemming implementeert in een mobiele app.
feature: Mobile SDK,Consent
jira: KT-14629
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# Goedkeuring uitvoeren

Leer hoe u toestemming implementeert in een mobiele app.

Met de mobiele extensie Adobe Experience Platform Consent kunt u de verzameling met voorkeuren voor toestemming vanuit uw mobiele app inschakelen wanneer u de Adobe Experience Platform Mobile SDK en de extensie Edge Network gebruikt. Leer meer over de [ uitbreiding van de Toestemming ](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/) in de documentatie.

## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Vraag de gebruiker om toestemming.
* Werk de extensie bij op basis van de gebruikersreactie.
* Leer hoe u de huidige status van toestemming krijgt.

## Goedkeuring aanvragen

Als u de zelfstudie vanaf het begin hebt gevolgd, zult u zich wellicht herinneren dat u de standaardtoestemming in de extensie Goedkeuring hebt ingesteld op **[!UICONTROL Pending - Queue events that occur before the user provides consent preferences.]**

Om met het verzamelen van gegevens te beginnen, moet u toestemming van de gebruiker krijgen. In een echte app wilt u de beste praktijken voor uw regio raadplegen. In deze zelfstudie krijgt u toestemming van de gebruiker door er gewoon om te vragen met een waarschuwing:

1. U wilt de gebruiker slechts eenmaal om toestemming vragen. U kunt dit doen door de Mobiele toestemming van SDK met de vereiste vergunning voor het volgen te combineren gebruikend het van Apple [ gebruiken het Traceren van het Kader van de Transparantie van de Toepassing ](https://developer.apple.com/documentation/apptrackingtransparency). In deze app gaat u ervan uit dat wanneer de gebruiker toestemming geeft om gebeurtenissen te volgen, deze toestemming geeft om gebeurtenissen te verzamelen.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator.

   Voeg deze code toe aan de functie `updateConsent` .

   ```swift
   // Update consent
   let collectConsent = ["collect": ["val": value]]
   let currentConsents = ["consents": collectConsent]
   Consent.update(with: currentConsents)
   MobileCore.updateConfigurationWith(configDict: currentConsents)
   ```

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL DisclaimerView]** in de projectnavigator van Xcode. Dit is de weergave die wordt weergegeven na het installeren of opnieuw installeren van de toepassing en het voor het eerst starten van de toepassing. De gebruiker wordt ertoe aangezet om het volgen per Apple [ app het Volgen van het kader van de Transparantie ](https://developer.apple.com/documentation/apptrackingtransparency) toe te staan. Als de gebruiker autoriseert, werkt u ook de toestemming bij.

   Voeg de volgende code toe aan de `ATTrackingManager.requestTrackingAuthorization { status in` closure.

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

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in de projectnavigator van Xcode.

   Voeg de volgende code toe aan de functie `getConsents` :

   ```swift
   // Get consents
   Consent.getConsents { consents, error in
      guard error == nil, let consents = consents else { return }
      guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
      guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
      Logger.aepMobileSDK.info("Consent getConsents: \(jsonStr)")
   }
   ```

2. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL HomeView]** in de projectnavigator van Xcode.

   Voeg de volgende code toe aan de modifier `.task` :

   ```swift
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

In het bovenstaande voorbeeld registreert u gewoon de toestemmingsstatus aan de console in Xcode. In een echt scenario, zou u het kunnen gebruiken om te wijzigen welke menu&#39;s of opties aan de gebruiker worden getoond.

## Valideren met betrouwbaarheid

1. Verwijder de toepassing van het apparaat of de simulator om het bijhouden en goedkeuren correct opnieuw in te stellen en te initialiseren.
1. Om uw simulator of apparaat aan Verzekering aan te sluiten, herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session).
1. Wanneer u de app verplaatst van het scherm **[!UICONTROL Home]** naar het scherm **[!UICONTROL Products]** en terug naar het scherm **[!UICONTROL Home]** , wordt een **[!UICONTROL Get Consents Response]** -gebeurtenis weergegeven in de gebruikersinterface van Verzekering.
   ![ bevestigt toestemming ](assets/consent-update.png)


>[!SUCCESS]
>
>U hebt nu de toepassing ingeschakeld om de gebruiker bij de eerste start na de installatie (of herinstallatie) te vragen toestemming te geven met de SDK van Adobe Experience Platform Mobile.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van de Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[verzamel levenscyclusgegevens](lifecycle-data.md)**

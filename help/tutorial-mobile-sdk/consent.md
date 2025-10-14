---
title: Goedkeuring implementeren voor Platform Mobile SDK-implementaties
description: Leer hoe u toestemming implementeert in een mobiele app.
feature: Mobile SDK,Consent
jira: KT-14629
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# Goedkeuring uitvoeren

Leer hoe u toestemming implementeert in een mobiele app.

Met de mobiele extensie Adobe Experience Platform Consent kunt u een verzameling voorkeuren voor toestemming vanuit uw mobiele app inschakelen wanneer u de Adobe Experience Platform Mobile SDK en de Edge Network-extensie gebruikt. Leer meer over de [&#x200B; uitbreiding van de Toestemming &#x200B;](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/) in de documentatie.

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

>[!BEGINTABS]

>[!TAB  iOS ]

1. U wilt de gebruiker slechts eenmaal om toestemming vragen. U combineert de Mobiele toestemming van SDK met de vereiste toestemming voor het volgen gebruikend het kader van de Transparantie van de Toepassing van Apple [&#x200B; het Traceren van het Kader van de Transparantie &#x200B;](https://developer.apple.com/documentation/apptrackingtransparency). In deze app gaat u ervan uit dat wanneer de gebruiker toestemming geeft om gebeurtenissen te volgen, deze toestemming geeft om gebeurtenissen te verzamelen.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator.

   Voeg deze code toe aan de functie `updateConsent` .

   ```swift
   // Update consent
   let collectConsent = ["collect": ["val": value]]
   let currentConsents = ["consents": collectConsent]
   Consent.update(with: currentConsents)
   MobileCore.updateConfigurationWith(configDict: currentConsents)
   ```

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL DisclaimerView]** in de projectnavigator van Xcode. De projectnavigator van Xode is de mening die na het installeren van of het opnieuw installeren van de toepassing en het beginnen van app voor de eerste keer wordt getoond. De gebruiker wordt ertoe aangezet om het volgen per Apple [&#x200B; app het Volgen van het kader van de Transparantie &#x200B;](https://developer.apple.com/documentation/apptrackingtransparency) toe te staan. Als de gebruiker autoriseert, werkt u ook de toestemming bij.

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

>[!TAB  Android ]

1. U wilt de gebruiker slechts eenmaal om toestemming vragen. In deze app gaat u ervan uit dat wanneer de gebruiker toestemming geeft om gebeurtenissen te volgen, deze toestemming geeft om gebeurtenissen te verzamelen.

1. Navigeer naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** in de Android Studio-navigator.

   Voeg deze code toe aan de functie `updateConsent(value: String)` .

   ```kotlin
   // Update consent
   val collectConsent = mapOf("collect" to mapOf("val" to value))
   val currentConsents = mapOf("consents" to collectConsent)
   Consent.update(currentConsents)
   MobileCore.updateConfiguration(currentConsents)
   ```

1. Navigeer naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL DisclaimerView.kt]** in de Android Studio-navigator.

   Voeg de volgende code toe aan de functie `DisclaimerView(navController: NavController)` eronder `// Set content to yes` en `// Set content to no` .

   ```kotlin
   // Add consent based on authorization
   if (status) {
      showPersonalizationWarning = false
   
      // Set consent to yes
      MobileSDK.shared.updateTrackingStatus(TrackingStatus.AUTHORIZED)
      MobileSDK.shared.updateConsent("y")
   } else {
      Toast.makeText(
            context,
            "You will not receive offers and location tracking will be disabled.",
            Toast.LENGTH_LONG
      ).show()
      showPersonalizationWarning = true
   
      // Set consent to no
      MobileSDK.shared.updateTrackingStatus(TrackingStatus.DENIED)
      MobileSDK.shared.updateConsent("n")
   }
   ```

>[!ENDTABS]

## Huidige status van toestemming ophalen

De mobiele extensie voor toestemming onderdrukt automatisch het bijhouden van wijzigingen / breidt deze uit op basis van de huidige waarde voor toestemming. U kunt ook zelf toegang krijgen tot de huidige staat van toestemming:

>[!BEGINTABS]

>[!TAB  iOS ]

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

>[!TAB  Android ]

1. Navigeer naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** in de Android Studio-navigator.

   Voeg de volgende code toe aan de functie `getConsents()` :

   ```kotlin
   // Get consents
   Consent.getConsents { callback ->
      if (callback != null) {
            val jsonStr = JSONObject(callback).toString(4)
            Log.i("MobileSDK", "Consent getConsents: $jsonStr")
      }
   }
   ```

1. Navigeer naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL HomeView.kt]** in de Android Studio-navigator.

   Voeg de volgende code toe aan `LaunchedEffect(unit)` :

   ```kotlin
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

In het bovenstaande voorbeeld, registreert u eenvoudig de toestemmingsstatus aan de console in Android Studio. In een echt scenario, zou u het kunnen gebruiken om te wijzigen welke menu&#39;s of opties aan de gebruiker worden getoond.

>[!ENDTABS]

## Valideren met Assurance

1. Verwijder de toepassing van het apparaat of de simulator om het bijhouden van gegevens en de toestemming opnieuw in te stellen en te initialiseren.
1. Om uw simulator of apparaat met Assurance te verbinden, herzie de [&#x200B; sectie van opstellingsinstructies &#x200B;](assurance.md#connecting-to-a-session).
1. Wanneer u de toepassing verplaatst van het **[!UICONTROL Home]** -scherm naar het **[!UICONTROL Products]** -scherm en terug naar het **[!UICONTROL Home]** -scherm, wordt een **[!UICONTROL Get Consents Response]** -gebeurtenis weergegeven in de gebruikersinterface van Assurance.
   ![&#x200B; bevestigt toestemming &#x200B;](assets/consent-update.png){zoomable="yes"}


>[!SUCCESS]
>
>U hebt uw toepassing nu ingeschakeld om de gebruiker bij de eerste start na de installatie (of herinstallatie) te vragen toestemming te geven met de Adobe Experience Platform Mobile SDK.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [&#x200B; Communautaire besprekingspost van Experience League &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[verzamel levenscyclusgegevens](lifecycle-data.md)**

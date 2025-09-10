---
title: A/B-tests uitvoeren in mobiele apps met Target en Platform Mobile SDK
description: Leer hoe u een Target A/B-test kunt gebruiken in uw mobiele app met Platform Mobile SDK en Adobe Target.
solution: Data Collection,Target
feature-set: Target
feature: A/B Tests
jira: KT-14641
exl-id: 87546baa-2d8a-4cce-b531-bec3782d2e90
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '1961'
ht-degree: 1%

---

# Optimaliseren en aanpassen met Adobe Target

Leer hoe u de ervaringen in uw mobiele apps kunt optimaliseren en aanpassen met Platform Mobile SDK en Adobe Target.

Het doel biedt alles wat u moet aanpassen en aanpassen aan de ervaringen van uw klanten. Met Doel kunt u uw omzet maximaliseren op uw website en mobiele sites, apps, sociale media en andere digitale kanalen. Het doel kan tests A/B, multivariate tests uitvoeren, producten en inhoud, doelinhoud adviseren, inhoud auto-personalize met AI, en veel meer. De nadruk in deze les is op de A/B testfunctionaliteit van Doel. Zie het [ overzicht van de Test A/B ](https://experienceleague.adobe.com/en/docs/target/using/activities/abtest/test-ab) voor meer informatie.

![Architectuur](assets/architecture-at.png){zoomable="yes"}

Voordat u A/B-tests kunt uitvoeren met Target, moet u ervoor zorgen dat de juiste configuraties en integratie zijn geïnstalleerd.

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Adobe Target-gebruikers die A/B-tests willen uitvoeren.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Toegang tot Adobe Target met [ toestemmingen, behoorlijk gevormde rollen, werkruimten, en eigenschappen ](https://experienceleague.adobe.com/en/docs/target/using/administer/manage-users/enterprise/property-channel).


## Leerdoelstellingen

In deze les zult u:

* Werk uw gegevensstroom bij voor integratie van het Doel.
* Werk de eigenschap tag bij met de extensie Offer Decisioning en Target.
* Werk uw schema bij om aanvraaggebeurtenissen vast te leggen.
* Instellingen valideren in Assurance.
* Maak een eenvoudige A/B-test in Doel.
* Werk uw app bij om de extensie Optimizer te registreren.
* Implementeer de A/B-test in uw app.
* Implementatie valideren in Assurance.


## Instellen

>[!TIP]
>
>Als u opstelling uw app reeds als deel van [ Journey Optimizer aanbiedingen ](journey-optimizer-offers.md) les hebt, zou u sommige stappen in deze opstellingssectie reeds kunnen reeds uitgevoerd.

### Gegevensstroomconfiguratie bijwerken

#### Adobe Target

Om ervoor te zorgen dat gegevens die u van uw mobiele app naar Experience Platform Edge Network verzendt, naar Adobe Target worden doorgestuurd, moet u de configuratie van de gegevensstroom bijwerken.

1. Selecteer **[!UICONTROL Datastreams]** in de gebruikersinterface voor gegevensverzameling en selecteer de gegevensstroom, bijvoorbeeld **[!DNL Luma Mobile App]** .
1. Selecteer **[!UICONTROL Add Service]** en selecteer **[!UICONTROL Adobe Target]** in de lijst **[!UICONTROL Service]** .
1. Als u een Target Premium-klant bent en eigenschapstokens wilt gebruiken, voert u de waarde Target **[!UICONTROL Property Token]** in die u voor deze integratie wilt gebruiken. Target Standard-gebruikers kunnen deze stap overslaan.

   U kunt de eigenschappen vinden in de doelinterface, in **[!UICONTROL Administration]** > **[!UICONTROL Properties]** . Selecteer ![ Code ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) om het bezitstoken voor het bezit te openbaren u wilt gebruiken. De eigenschapstoken heeft een indeling zoals `"at_property": "xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx"` ; u moet alleen de waarde `xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx` invoeren.

   U kunt ook een doel-omgeving-id opgeven. Het doel gebruikt omgevingen om uw sites en pre-productieomgevingen te organiseren voor eenvoudig beheer en afzonderlijke rapportering. De vooraf ingestelde omgevingen zijn onder andere Productie, Staging en Ontwikkeling. Zie [ Milieu ](https://experienceleague.adobe.com/en/docs/target/using/administer/environments) en [ identiteitskaart van het Milieu van het Doel ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/applications-setup/setup-target) voor meer informatie.

   U kunt desgewenst een naamruimte van een externe doelid opgeven ter ondersteuning van profielsynchronisatie op een naamruimte van een identiteit (bijvoorbeeld CRM-id). Zie [ identiteitskaart van de Derde van het Doel namespace ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/applications-setup/setup-target) voor meer informatie.

1. Selecteer **[!UICONTROL Save]**.

   ![ voegt Doel aan datastream ](assets/edge-datastream-target.png){zoomable="yes"} toe


#### Adobe Journey Optimizer

Om ervoor te zorgen dat gegevens die u van uw mobiele app naar de Edge Network verzendt, naar Journey Optimizer - Beslissingsbeheer worden doorgestuurd, werkt u de configuratie van uw gegevensstroom bij.

1. Selecteer **[!UICONTROL Datastreams]** in de gebruikersinterface voor gegevensverzameling en selecteer de gegevensstroom, bijvoorbeeld **[!DNL Luma Mobile App]** .
1. Selecteer ![ Meer ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) voor **[!UICONTROL Experience Platform]** en selecteer ![ uitgeven ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit]** van het contextmenu.
1. In **[!UICONTROL Datastreams]** > ![ Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) > **[!UICONTROL Adobe Experience Platform]** scherm, zorg ervoor dat **[!UICONTROL Offer Decisioning]**, **[!UICONTROL Edge Segmentation]**, en **[!UICONTROL Personalization Destinations]** worden geselecteerd. Als u ook de Journey Optimizer-lessen volgt, selecteert u **[!UICONTROL Adobe Journey Optimizer]** . Zie {de montages van 0} Adobe Experience Platform [ voor meer informatie.](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
1. Selecteer **[!UICONTROL Save]** om de configuratie van de gegevensstroom op te slaan.

   ![ de gegevensstroomconfiguratie van AEP ](assets/datastream-aep-configuration-target.png){zoomable="yes"}


### Offer Decisioning- en Target-tagextensie installeren

Hoewel deze les over tests A/B in Doel is, wordt het resultaat van een test gezien als een aanbieding en in de infrastructuur van Adobe uitgevoerd gebruikend de de markeringen van Adobe Offer Decisioning en van het Doel uitbreiding. Deze extensie werkt met zowel Journey Optimizer- als Target-aanbiedingen.

1. Navigeer naar **[!UICONTROL Tags]** , zoek de eigenschap mobile tag en open de eigenschap.
1. Selecteer **[!UICONTROL Extensions]**.
1. Selecteer **[!UICONTROL Catalog]**.
1. Zoek naar de extensie **[!UICONTROL Offer Decisioning and Target]** .
1. De extensie installeren. Voor de extensie is geen aanvullende configuratie vereist.

   ![ voeg Offer Decisioning en de uitbreiding van het Doel toe ](assets/tag-add-decisioning-extension.png){zoomable="yes"}



### Uw schema bijwerken

1. Navigeer naar de interface voor gegevensverzameling en selecteer **[!UICONTROL Schemas]** in de linkertrack.
1. Selecteer **[!UICONTROL Browse]** in de bovenste balk.
1. Selecteer het schema om het te openen.
1. In de schemaredacteur, voegt de uitgezochte ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) toe **[!UICONTROL Add]** naast **[!UICONTROL Field groups]**.
1. Zoek in het dialoogvenster **[!UICONTROL Add field groups]** naar `proposition` , selecteer **[!UICONTROL Experience Event - Proposition Interactions]** en selecteer **[!UICONTROL Add field groups]** .
   ![ Voorstelling ](assets/schema-fieldgroup-proposition.png){zoomable="yes"}
1. Selecteer **[!UICONTROL Save]** om de wijzigingen in het schema op te slaan.


### Instellingen valideren in Assurance

Uw instellingen valideren in Assurance:

1. Ga naar de gebruikersinterface van Assurance.
1. Selecteer **[!UICONTROL Configure]** in linkerspoor en selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Validate Setup]** onder **[!UICONTROL OFFER DECISIONING AND TARGET]**.
1. Selecteer **[!UICONTROL Save]**.
1. Selecteer **[!UICONTROL Validate Setup]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
   ![ AJO Beslissende bevestiging ](assets/ajo-decisioning-validation.png){zoomable="yes"}

## Een A/B-test maken

Er zijn vele soorten activiteiten die u kunt maken in Adobe Target en implementeren in een mobiele app, zoals vermeld in de inleiding. Voor deze les, voert u een test A/B uit.

1. Selecteer in de interface Doel de optie **[!UICONTROL Activities]** in de bovenste balk.
1. Selecteer **[!UICONTROL Create Activity]** en **[!UICONTROL A/B Test]** in het contextmenu.
1. Selecteer **[!UICONTROL Create A/B Test Activity]** als **[!UICONTROL Mobile]** in het dialoogvenster **[!UICONTROL Type]** en selecteer een werkruimte in de lijst **[!UICONTROL Choose Workspace]** . Selecteer uw eigenschap in de lijst **[!UICONTROL Choose property]** als u een Target Premium-klant bent en een eigenschapstoken hebt opgegeven in de gegevensstroom.
1. Selecteer **[!UICONTROL Create]**.
   ![ creeer de activiteit van het Doel ](assets/target-create-activity1.png){zoomable="yes"}

1. In het **[!UICONTROL Untitled Activity]** -scherm voert u bij de **[!UICONTROL Experiences]** -stap het volgende uit:

   1. Voer `luma-mobileapp-abtest` in **[!UICONTROL Select Location]** onder **[!UICONTROL Location 1]** in. Deze locatienaam (vaak mbox genoemd) wordt later gebruikt in de app-implementatie.
   1. Selecteer ![ Meer ](/help/assets/icons/More.svg) naast **[!UICONTROL Content]** en selecteer **[!UICONTROL Create JSON Offer]** van het contextmenu.
   1. Plak de volgende JSON in het dialoogvenster **[!UICONTROL Create JSON Offer]** .

      ```json
      { 
          "title": "Luma Anaolog Watch",
          "text": "Designed to stand up to your active lifestyle, this women's Luma Analog Watch features a tasteful brushed chrome finish and a stainless steel, water-resistant construction for lasting durability.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Luma_Analog_Watch.jpg" 
      }
      ```

      ![ Ervaring A ](assets/target-create-activity-experienceA.png){zoomable="yes"}

      Selecteer **[!UICONTROL Create]**.

   1. Selecteer **[!UICONTROL +]** naast **[!UICONTROL Experiences]** om toe te voegen **[!UICONTROL Experience B]** .



   1. Herhaal stap b en c voor Ervaring B, maar gebruik in plaats daarvan `Aim Analog Watch` als de titel en plak de volgende JSON:

      ```json
      { 
          "title": "Aim Analog Watch",
          "text": "The flexible, rubberized strap is contoured to conform to the shape of your wrist for a comfortable all-day fit. The face features three illuminated hands, a digital read-out of the current time, and stopwatch functions.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Aim_Watch.jpg" 
      }
      ```


1. Controleer in de stap **[!DNL Targeting]** de instelling van uw A/B-test. Beide aanbiedingen worden standaard in gelijke mate toegewezen aan alle bezoekers. Selecteer **[!UICONTROL Next]** om door te gaan.

   ![ gericht ](assets/target-targeting.png){zoomable="yes"}

1. In de stap **[!UICONTROL Goals & Settings]** :

   1. Wijzig de naam van de activiteit zonder naam, bijvoorbeeld in `Luma Mobile SDK Tutorial - A/B Test Example` .
   1. Voer bijvoorbeeld **[!UICONTROL Objective]** in voor de A/B-test `A/B Test for Luma mobile app tutorial` .
   1. Selecteer **[!UICONTROL Conversion]** , **[!UICONTROL Viewed an mbox]** in de tegel **[!UICONTROL Goal Metric]** > **[!UICONTROL MY PRIMARY GOAL]** en voer de naam van uw locatie (mbox) in, bijvoorbeeld `luma-mobileapp-abtest` .
   1. Selecteer **[!UICONTROL Save & Close]**.

      ![ Montages van Doelen ](assets/target-goals.png){zoomable="yes"}

1. Terug in het **[!UICONTROL All Activities]** scherm:

   1. Selecteer ![ Meer ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) bij uw activiteit.
   1. Selecteer ![ Spel ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) **[!UICONTROL Activate]** om uw test te activeren A/B.

   ![ activeer ](assets/target-activate.png){zoomable="yes"}


## Doel implementeren in uw app

Zoals in vorige lessen is besproken, biedt het installeren van een extensie voor mobiele tags alleen de configuratie. Vervolgens moet u de Optimize SDK installeren en registreren. Als deze stappen niet duidelijk zijn, herzie [ installeer SDKs ](install-sdks.md) sectie.

>[!NOTE]
>
>Als u [ voltooide installeerde SDKs ](install-sdks.md) sectie, dan is SDK reeds geïnstalleerd en u kunt deze stap overslaan.
>

>[!BEGINTABS]

>[!TAB  iOS ]

1. In Xcode, zorg ervoor dat [ AEP optimaliseert ](https://github.com/adobe/aepsdk-messaging-ios) aan de lijst van pakketten in de Afhankelijkheden van het Pakket wordt toegevoegd. Zie {de Manager van het Pakket van 0} Swift [.](install-sdks.md#swift-package-manager)
1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL AppDelegate]** in de Xcode-projectnavigator.
1. Controleer of `AEPOptimize` deel uitmaakt van uw lijst met importbewerkingen.

   `import AEPOptimize`

1. Controleer of `Optimize.self` deel uitmaakt van de array met extensies die u registreert.

   ```swift
   let extensions = [
       AEPIdentity.Identity.self,
       Lifecycle.self,
       Signal.self,
       Edge.self,
       AEPEdgeIdentity.Identity.self,
       Consent.self,
       UserProfile.self,
       Places.self,
       Messaging.self,
       Optimize.self,
       Assurance.self
   ]
   ```

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** in de Xcode-projectnavigator. Zoek de functie ` func updatePropositionAT(ecid: String, location: String) async` . Voeg de volgende code toe:

   ```swift
   // set up the XDM dictionary, define decision scope and call update proposition API
   Task {
       let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
       let identityMap = ["identityMap" : ecid]
       let xdmData = ["xdm" : identityMap]
       let decisionScope = DecisionScope(name: location)
       Optimize.clearCachedPropositions()
       Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData) { data, error in
           if let error = error {
               Logger.aepMobileSDK.error("MobileSDK - updatePropositionsAT: Error updating propositions: \(error.localizedDescription)")
           }
       }
   }
   ```

   Deze functie:

   * stelt een XDM-woordenboek `xdmData` in met de ECID om het profiel te identificeren waarvoor u de A/B-test moet presenteren, en
   * definieert een `decisionScope` , een array met locaties waarop de A/B-test moet worden gepresenteerd.

   Dan roept de functie twee APIs: [`Optimize.clearCachedPropositions` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions) en [`Optimize.updatePropositions` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). Met deze functies worden alle in de cache opgeslagen voorstellingen gewist en worden de voorstellingen voor dit profiel bijgewerkt. Een voorstel in deze context is de ervaring (aanbieding) die van de activiteit van het Doel (uw test A/B) wordt geselecteerd en die u in [ creeerde een test A/B ](#create-an-ab-test).

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Personalization]** > **[!DNL TargetOffersView]** in de Xcode-projectnavigator. Zoek de functie `func onPropositionsUpdateAT(location: String) async {` en inspecteer de code van deze functie. Het belangrijkste deel van deze functie is de [`Optimize.onPropositionsUpdate` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API vraag, die:
   * wint de voorstellen voor het huidige profiel terug dat op het beslissingswerkingsgebied wordt gebaseerd (die de plaats is u in de A/B Test hebt bepaald);
   * het aanbod uit het voorstel ophaalt;
   * de inhoud van de aanbieding opheft, zodat deze correct in de app kan worden weergegeven, en
   * activeert de `displayed()` -actie op de aanbieding die een gebeurtenis terugstuurt naar Platform Edge Network op de hoogte dat de aanbieding wordt weergegeven.

1. Nog steeds in **[!DNL TargetOffersView]** , voeg de volgende code aan de `.onFirstAppear` bepaling toe. Deze code zorgt ervoor dat callback voor het bijwerken van de aanbiedingen slechts eenmaal wordt geregistreerd.

   ```swift
   // Invoke callback for offer updates
   Task {
       await self.onPropositionsUpdateAT(location: location)
   }
   ```

1. Nog steeds in **[!DNL TargetOffersView]** , voeg de volgende code aan de `.task` bepaling toe. Met deze code worden de aanbiedingen bijgewerkt wanneer de weergave wordt vernieuwd.

   ```swift
   // Clear and update offers
   await self.updatePropositionsAT(ecid: currentEcid, location: location)
   ```

>[!TAB  Android ]

1. In de Studio van Android, zorg ervoor dat [ aepsdk-optimize-android ](https://github.com/adobe/aepsdk-optimize-android) deel van de gebiedsdelen in **[!UICONTROL build.gradle.kts]** in **[!UICONTROL Android]** ![ ChevronDown ](/help/assets/icons/ChevronDown.svg) > **[!UICONTROL Gradle Scripts]** uitmaakt. Zie [ Gradle ](install-sdks.md#gradle).
1. Navigeer naar **[!DNL app]** > **[!DNL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL MainActivity]** in de Android Studio-navigator.
1. Controleer of `Optimize` deel uitmaakt van uw lijst met importbewerkingen.

   ```kotlin
   import com.adobe.marketing.mobile.optimize.Optimize
   ```

1. Controleer of `Optimize.EXTENSION` deel uitmaakt van de array met extensies die u registreert.

   ```kotlin
   val extensions = listOf(
      Identity.EXTENSION,
      Lifecycle.EXTENSION,
      Signal.EXTENSION,
      Edge.EXTENSION,
      Consent.EXTENSION,
      UserProfile.EXTENSION,
      Places.EXTENSION,
      Messaging.EXTENSION,
      Optimize.EXTENSION,
      Assurance.EXTENSION
   )
   ```

1. Navigeer aan **[!UICONTROL Android]** ![ ChevronDown ](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!DNL models]** > **[!UICONTROL MobileSDK]** in de navigator van Android Studio. Zoek de functie ` suspend fun updatePropositionsAT(ecid: String, location: String)` . Voeg de volgende code toe:

   ```kotlin
   // set up the XDM dictionary, define decision scope and call update proposition API
   withContext(Dispatchers.IO) {
       val ecidMap = mapOf("ECID" to mapOf("id" to ecid, "primary" to true))
       val identityMap = mapOf("identityMap" to ecidMap)
       val xdmData = mapOf("xdm" to identityMap)
       val decisionScope = DecisionScope(location)
       Optimize.clearCachedPropositions()
       Optimize.updatePropositions(listOf(decisionScope), xdmData, null, object :
           AdobeCallbackWithOptimizeError<MutableMap<DecisionScope?, OptimizeProposition?>?> {
           override fun fail(optimizeError: AEPOptimizeError?) {
               val responseError = optimizeError
               Log.i("MobileSDK", "updatePropositionsAT error: ${responseError}")
           }
           override fun call(propositionsMap: MutableMap<DecisionScope?, OptimizeProposition?>?) {
               val responseMap = propositionsMap
               Log.i("MobileSDK", "updatePropositionsOD call: ${responseMap}")
           }
       })
   }
   ```

   Deze functie:

   * stelt een XDM-woordenboek `xdmData` in met de ECID om het profiel te identificeren waarvoor u de A/B-test moet presenteren, en
   * definieert een `decisionScope` , een array met locaties waarop de A/B-test moet worden gepresenteerd.

   Dan roept de functie twee API&#39;s: [`Optimize.clearCachedPropositions` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions) en [`Optimize.updatePropositions` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). Met deze functies worden alle in de cache opgeslagen voorstellingen gewist en worden de voorstellingen voor dit profiel bijgewerkt. Een voorstel in deze context is de ervaring (aanbieding) die van de activiteit van het Doel (uw test A/B) wordt geselecteerd en die u in [ creeerde een test A/B ](#create-an-ab-test).

1. Navigeer naar **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!DNL views]** > **[!DNL TargetOffers.kt]** in de Android Studio-navigator. Zoek de functie `fun onPropositionsUpdateAT(location: String): List<OfferItem>` en inspecteer de code van deze functie. Het belangrijkste deel van deze functie is de [`Optimize.onPropositionsUpdate` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API vraag, die:
   * wint de voorstellen voor het huidige profiel terug dat op het beslissingswerkingsgebied wordt gebaseerd (die de plaats is u in de A/B Test hebt bepaald);
   * het aanbod uit het voorstel ophaalt;
   * de inhoud van de aanbieding opheft, zodat deze correct in de app kan worden weergegeven, en
   * retourneert het voorstel.

1. Voeg nog steeds in **[!DNL TargetOffers.kt]** de functie `LaunchedEffect` toe om ervoor te zorgen dat de aanbiedingen worden vernieuwd wanneer u het tabblad Personalization start.

   ```kotlin
   // recompose the view when the number of received offers changes
   LaunchedEffect(offersAT.count()) {
       updatePropositionsAT(currentEcid, MobileSDK.shared.targetLocation.value)
       offersAT = onPropositionsUpdateAT(MobileSDK.shared.targetLocation.value)
   }
   ```

>[!ENDTABS]

U kunt extra parameters van het Doel (zoals mbox, profiel, product, of ordeparameters) in een verzoek van de verpersoonlijkingsvraag naar het netwerk van de Ervaring Edge verzenden, door hen in een gegevenswoordenboek toe te voegen wanneer het roepen van [`Optimize.updatePropositions` ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions) API. Zie voor meer informatie [ Parameters van het Doel ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/#target-parameters).



## Valideren met de app

>[!BEGINTABS]

>[!TAB  iOS ]

1. Rebuild en stel app in werking in de simulator of op een fysiek apparaat van Xcode, gebruikend ![ Spel ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Ga naar het tabblad **[!UICONTROL Personalization]**.

1. Schuif omlaag naar de onderkant en u ziet een van de twee aanbiedingen die u hebt gedefinieerd in de A/B-test die wordt weergegeven in de **[!UICONTROL TARGET]** -tegel.

   <img src="assets/target-app-offer.png" width="300">


>[!TAB  Android ]

1. Rebuild en stel app in werking in de simulator of op een fysiek apparaat van de Studio van Android, gebruikend ![ Spel ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Ga naar het tabblad **[!DNL Personalization]**.

1. U ziet een van de twee aanbiedingen die u in de A/B-test hebt gedefinieerd, in het onderste vak van de **[!UICONTROL TARGET]** -tegel worden weergegeven.

   <img src="assets/ajo-app-offers-android.png" width="300">


>[!ENDTABS]

## Implementatie valideren in Assurance

De A/B-test in Assurance valideren:

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat met Assurance te verbinden.
1. Selecteer **[!UICONTROL Configure]** in linkerspoor en selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Review & Simulate]** onder **[!UICONTROL OFFER DECSIONING AND TARGET]**.
1. Selecteer **[!UICONTROL Save]**.
1. Selecteer **[!UICONTROL Review & Simulate]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
1. Selecteer **[!UICONTROL Requests]** op de bovenste balk. Uw **[!DNL Target]** -aanvragen worden weergegeven.
   ![ AJO Beslissende bevestiging ](assets/assurance-decisioning-requests.png){zoomable="yes"}

1. U kunt de tabbladen **[!UICONTROL Simulate]** en **[!UICONTROL Event List]** raadplegen voor extra functionaliteit waarmee u de instellingen van uw doelaanbiedingen kunt valideren.

## Volgende stappen

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing meer A/B-tests of andere doelactiviteiten (zoals Experience Targeting, Multivariate Test) aan uw app toe te voegen. Er is meer diepgaande informatie beschikbaar in de [ reactie GitHub voor de Optimize uitbreiding ](https://github.com/adobe/aepsdk-optimize-ios) waar u een verbinding aan een specifieke [ leerprogramma ](https://opensource.adobe.com/aepsdk-optimize-ios/#/tutorials/README) op kunt ook vinden hoe te om aanbiedingen van Adobe Target te volgen.

>[!SUCCESS]
>
>U hebt de app voor A/B-tests ingeschakeld en de resultaten van een A/B-test met de Offer Decisioning- en Target-extensie voor de Adobe Experience Platform Mobile SDK weergegeven.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[Conclusie en volgende stappen](conclusion.md)**

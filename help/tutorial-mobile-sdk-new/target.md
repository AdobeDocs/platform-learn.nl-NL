---
title: A/B-tests uitvoeren met doel
description: Leer hoe u een Target A/B-test gebruikt in uw mobiele app met Platform Mobile SDK en Adobe Target.
solution: Data Collection,Target
feature-set: Target
feature: A/B Tests
hide: true
exl-id: 87546baa-2d8a-4cce-b531-bec3782d2e90
source-git-commit: d7410a19e142d233a6c6597de92f112b961f5ad6
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 0%

---

# Optimaliseren en aanpassen met Adobe Target

Leer hoe u de ervaringen in uw mobiele apps kunt optimaliseren en aanpassen met Platform Mobile SDK en Adobe Target.

Het doel biedt alles wat u moet aanpassen en aanpassen aan de ervaringen van uw klanten. Met Doel kunt u uw omzet maximaliseren op uw website en mobiele sites, apps, sociale media en andere digitale kanalen. Het doel kan tests A/B, multivariate tests uitvoeren, producten en inhoud, doelinhoud adviseren, inhoud auto-personalize met AI, en veel meer. De nadruk in deze les is op de A/B testfunctionaliteit van Doel.  Zie de [A/B-testoverzicht](https://experienceleague.adobe.com/docs/target/using/activities/abtest/test-ab.html?lang=en) voor meer informatie .

![Architectuur](assets/architecture-at.png)

Voordat u A/B-tests kunt uitvoeren met Target, moet u ervoor zorgen dat de juiste configuraties en integratie zijn geïnstalleerd.

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Adobe Target-gebruikers die A/B-tests willen uitvoeren.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Toegang tot Adobe Target met machtigingen, correct geconfigureerde rollen, werkruimten en eigenschappen zoals beschreven [hier](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/property-channel.html?lang=en).


## Leerdoelstellingen

In deze les zult u:

* Werk uw gegevensstroom bij voor integratie van het Doel.
* Werk de eigenschap tag bij met de extensie Journey Optimizer - Decisioning.
* Werk uw schema bij om aanvraaggebeurtenissen vast te leggen.
* Valideer installatie in Betrouwbaarheid.
* Maak een eenvoudige A/B-test in Doel.
* Werk uw app bij om de extensie Optimizer te registreren.
* Implementeer de A/B-test in uw app.
* Implementatie valideren in Betrouwbaarheid.


## Instellen

>[!TIP]
>
>Als u uw app al hebt ingesteld als onderdeel van het [Journey Optimizer-aanbiedingen](journey-optimizer-offers.md) les, zou u sommige stappen in deze opstellingssectie reeds kunnen reeds uitgevoerd hebben.

### Gegevensstroomconfiguratie bijwerken

#### Adobe Target

Om ervoor te zorgen dat gegevens die u van uw mobiele app naar Edge Network van Experience Platform verzendt, naar Adobe Target worden doorgestuurd, moet u de configuratie van de gegevensstroom bijwerken.

1. Selecteer in de gebruikersinterface voor gegevensverzameling de optie **[!UICONTROL Gegevensstromen]** en selecteert u bijvoorbeeld uw gegevensstroom **[!DNL Luma Mobile App]**.
1. Selecteren **[!UICONTROL Service toevoegen]** en selecteert u **[!UICONTROL Adobe Target]** van de **[!UICONTROL Service]** lijst.
1. Als u een klant van de Premium van het Doel bent en bezitstokens wilt gebruiken, ga het Doel in **[!UICONTROL Eigenschapstoken]** waarde die u voor deze integratie wilt gebruiken. Gebruikers van de doelstandaard kunnen deze stap overslaan.

   U kunt uw eigenschappen in het Doel UI, in vinden **[!UICONTROL Administratie]** > **[!UICONTROL Eigenschappen]**. Selecteren ![Code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) om het bezitstoken voor het bezit te openbaren u wilt gebruiken. De eigenschap token heeft een vergelijkbare indeling `"at_property": "xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx"`; u mag alleen de waarde invoeren `xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx`.

   U kunt ook een doel-omgeving-id opgeven. Het doel gebruikt omgevingen om uw sites en pre-productieomgevingen te organiseren voor eenvoudig beheer en gescheiden rapportage. De vooraf ingestelde omgevingen zijn onder andere Productie, Staging en Ontwikkeling. Zie [Omgevingen](https://experienceleague.adobe.com/docs/target/using/administer/environments.html?lang=en) en [Id van doelomgeving](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-environment-id) voor meer informatie .

   U kunt desgewenst een naamruimte van een externe doelid opgeven ter ondersteuning van profielsynchronisatie op een naamruimte van een identiteit (bijvoorbeeld CRM-id). Zie [Naamruimte derde partij doel](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-third-party-id-namespace) voor meer informatie .

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Doel toevoegen aan gegevensstroom](assets/edge-datastream-target.png)


#### Adobe Journey Optimizer

Om ervoor te zorgen dat gegevens die u van uw mobiele app naar het Edge Network verzendt, naar Journey Optimizer - Beslissingsbeheer worden doorgestuurd, werkt u de configuratie van uw gegevensstroom bij.

1. Selecteer in de gebruikersinterface voor gegevensverzameling de optie **[!UICONTROL Gegevensstromen]** en selecteert u bijvoorbeeld uw gegevensstroom **[!DNL Luma Mobile App]**.
1. Selecteren ![Meer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) for **[!UICONTROL Experience Platform]** en selecteert u ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Bewerken]** in het contextmenu.
1. In de **[!UICONTROL Gegevensstromen]** > ![Map](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** scherm, controleren **[!UICONTROL Offer decisioning]**, **[!UICONTROL Randsegmentatie]**, en **[!UICONTROL Aanpassingsdoelen]** zijn geselecteerd. Als u ook de Journey Optimizer-lessen volgt, selecteert u **[!UICONTROL Adobe Journey Optimizer]** ook. Zie [Adobe Experience Platform-instellingen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) voor meer informatie .
1. Als u de configuratie van de gegevensstroom wilt opslaan, selecteert u **[!UICONTROL Opslaan]** .

   ![AEP-configuratie gegevensstroom](assets/datastream-aep-configuration-target.png)


### Adobe Journey Optimizer installeren - extensie voor beslissingstags

1. Navigeren naar **[!UICONTROL Tags]**, zoek de eigenschap mobile tag en open de eigenschap.
1. Selecteren **[!UICONTROL Extensies]**.
1. Selecteren **[!UICONTROL Catalogus]**.
1. Zoeken naar **[!UICONTROL Adobe Journey Optimizer - Beslissing]** extensie.
1. De extensie installeren. Voor de extensie is geen aanvullende configuratie vereist.

   ![Decisitie-extensie toevoegen](assets/tag-add-decisioning-extension.png)


### Uw schema bijwerken

1. Navigeer naar de interface voor gegevensverzameling en selecteer **[!UICONTROL Schemas]** van de linkerspoorstaaf.
1. Selecteren **[!UICONTROL Bladeren]** in de bovenste balk.
1. Selecteer het schema om het te openen.
1. Selecteer in de Schema-editor de optie ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** naast **[!UICONTROL Veldgroepen]**.
1. Zoek in het dialoogvenster Veldgroepen toevoegen naar `proposition`, selecteert u **[!UICONTROL Experience Event - Propositie-interacties]** en selecteert u **[!UICONTROL Veldgroepen toevoegen]**.
   ![Voorstelling](assets/schema-fieldgroup-proposition.png)
1. Selecteer **[!UICONTROL Opslaan]**.


### Setup valideren bij Betrouwbaarheid

Uw instellingen valideren in Betrouwbaarheid:

1. Ga naar de betrouwbaarheidsinterface.
1. Selecteren **[!UICONTROL Configureren]** in linkerspoor en selecteer ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Instellingen valideren]** ondergronds **[!UICONTROL ADOBE JOURNEY OPTIMIZER-BESLISSING]**.
1. Selecteren **[!UICONTROL Opslaan]**.
1. Selecteren **[!UICONTROL Instellingen valideren]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
   ![Validatie van AJO-beslissingen](assets/ajo-decisioning-validation.png)

## Een A/B-test maken

Er zijn vele soorten activiteiten die u kunt maken in Adobe Target en implementeren in een mobiele app, zoals vermeld in de inleiding. Voor deze les, zult u zich op het creëren van een het uitvoeren van een test A/B concentreren.

1. Selecteer in de interface Doel de optie **[!UICONTROL Activiteiten]** in de bovenste balk.
1. Selecteren **[!UICONTROL Activiteit maken]** en **[!UICONTROL A/B-test]** in het contextmenu.
1. In de **[!UICONTROL Testactiviteit A/B maken]** dialoogvenster, selecteren **[!UICONTROL Mobiel]** als de **[!UICONTROL Type]**, selecteert u een werkruimte in het menu **[!UICONTROL Werkruimte kiezen]** en selecteert u de eigenschap in het menu **[!UICONTROL Eigenschap kiezen]** lijst als u een klant van de Premium van het Doel bent en een bezitstoken in de gegevensstroom specificeerde.
1. Selecteer **[!UICONTROL Maken]**.
   ![Doelactiviteit maken](assets/target-create-activity1.png)

1. In de **[!UICONTROL Naamloze activiteit]** scherm, op **[!UICONTROL Ervaringen]** stap:

   1. Enter `luma-mobileapp-abtest` in **[!UICONTROL Locatie selecteren]** ondergronds **[!UICONTROL LOCATIE 1]**. Deze locatienaam (vaak mbox genoemd) wordt later gebruikt in de app-implementatie.
   1. Selecteren ![Chrevron omlaag](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) naast **[!UICONTROL Standaardinhoud]** en selecteert u **[!UICONTROL JSON-aanbieding maken]** in het contextmenu.
   1. Kopieer de volgende JSON naar **[!UICONTROL Een geldig JSON-object invoeren]**.

      ```json
      { 
          "title": "Luma Anaolog Watch",
          "text": "Designed to stand up to your active lifestyle, this women's Luma Analog Watch features a tasteful brushed chrome finish and a stainless steel, water-resistant construction for lasting durability.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Luma_Analog_Watch.jpg" 
      }
      ```

   1. Selecteren **[!UICONTROL + Ervaring toevoegen]**.

      ![Ervaring A](assets/target-create-activity-experienceA.png)

   1. Herhaal stap b en c voor Ervaring B, maar gebruik in plaats daarvan het volgende JSON:

      ```json
      { 
          "title": "Aim Analog Watch",
          "text": "The flexible, rubberized strap is contoured to conform to the shape of your wrist for a comfortable all-day fit. The face features three illuminated hands, a digital read-out of the current time, and stopwatch functions.", 
          "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Aim_Watch.jpg" 
      }
      ```

   1. Selecteren **[!UICONTROL Volgende]**.

      ![Ervaring B](assets/target-create-activity-experienceB.png)

1. In de **[!DNL Targeting]** de opstelling van uw A/B-test. Beide aanbiedingen worden standaard gelijkelijk over alle bezoekers verdeeld. Selecteren **[!UICONTROL Volgende]** om door te gaan.

   ![Targeting](assets/taget-targeting.png)

1. In de **[!UICONTROL Doelstellingen en instellingen]** stap:

   1. De naam van uw activiteit zonder naam wijzigen, bijvoorbeeld in `Luma Mobile SDK Tutorial - A/B Test Example`.
   1. Voer een **[!UICONTROL Doelstelling]** voor uw A/B test bijvoorbeeld `A/B Test for Luma mobile app tutorial`.
   1. Selecteren **[!UICONTROL Conversie]**, **[!UICONTROL Een box weergegeven]** in de **[!UICONTROL Goal Metric]** > **[!UICONTROL MIJN PRIMAIRE GOAL]** tegel en voer de naam van uw locatie (mbox) in, bijvoorbeeld `luma-mobileapp-abtest`.
   1. Selecteren **[!UICONTROL Opslaan en sluiten]**.

      ![Instellingen voor doelen](assets/target-goals.png)

1. Terug in de **[!UICONTROL Alle activiteiten]** scherm:

   1. Selecteren ![Meer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) op uw activiteit.
   1. Selecteren ![Afspelen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) **[!UICONTROL Activeren]** om uw A/B-test te activeren.

   ![Activeren](assets/target-activate.png)


## Doel implementeren in uw app

Zoals in vorige lessen is besproken, biedt het installeren van een extensie voor mobiele tags alleen de configuratie. Vervolgens moet u de Optimize SDK installeren en registreren. Als deze stappen niet duidelijk zijn, herzie [SDK&#39;s installeren](install-sdks.md) sectie.

>[!NOTE]
>
>Als u het [SDK&#39;s installeren](install-sdks.md) is de SDK al geïnstalleerd en kunt u deze stap overslaan.
>

1. Controleer in Xcode of [AEP optimaliseren](https://github.com/adobe/aepsdk-messaging-ios.git) wordt toegevoegd aan de lijst met pakketten in Pakketafhankelijke onderdelen. Zie [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL AppDelegate]** in de Xcode-projectnavigator.
1. Zorgen `AEPOptimize` maakt deel uit van uw lijst met importbewerkingen.

   `import AEPOptimize`

1. Zorgen `Optimize.self` maakt deel uit van de array met extensies die u registreert.

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

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** in de Xcode-projectnavigator. Zoek de ` func updatePropositionAT(ecid: String, location: String) async` functie. Voeg de volgende code toe:

   ```swift
   // set up the XDM dictionary, define decision scope and call update proposition API
   Task {
       let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
       let identityMap = ["identityMap" : ecid]
       let xdmData = ["xdm" : identityMap]
       let decisionScope = DecisionScope(name: location)
       Optimize.clearCachedPropositions()
       Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData)
   }
   ```

   Deze functie:

   * Hiermee wordt een XDM-woordenboek ingesteld `xdmData`, met de ECID om het profiel te identificeren waarvoor u de A/B-test moet presenteren, en
   * definieert een `decisionScope`, een array van locaties waar de A/B-test moet worden gepresenteerd.

   Vervolgens roept de functie twee API&#39;s aan: [`Optimize.clearCachedPropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions) en [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). Met deze functies worden alle in de cache opgeslagen voorstellingen gewist en worden de voorstellingen voor dit profiel bijgewerkt. Een voorstel in deze context is de ervaring (aanbieding) die is geselecteerd uit de doelactiviteit (uw A/B-test) en die u hebt gedefinieerd in [Een A/B-test maken](#create-an-ab-test).

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Personalization]** > **[!DNL TargetOffersView]** in de Xcode-projectnavigator. Zoek de `func onPropositionsUpdateAT(location: String) async {` en inspecteer de code van deze functie. Het belangrijkste onderdeel van deze functie is de  [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API-aanroep, die:
   * wint de voorstellen voor het huidige profiel terug dat op het beslissingswerkingsgebied wordt gebaseerd (die de plaats is u in de A/B Test hebt bepaald);
   * het aanbod uit het voorstel ophaalt;
   * de inhoud van de aanbieding opheft, zodat deze correct in de app kan worden weergegeven, en
   * activeert de `displayed()` actie op de aanbieding die een gebeurtenis terug naar het Edge Network zal sturen om het aanbod te informeren, wordt weergegeven.

1. Nog steeds in **[!DNL TargetOffersView]** voegt u de volgende code toe aan de `.onFirstAppear` modifier. Deze code zorgt ervoor dat de callback voor het bijwerken van de aanbiedingen slechts eenmaal wordt geregistreerd.

   ```swift
   // Invoke callback for offer updates
   Task {
       await self.onPropositionsUpdateAT(location: location)
   }
   ```

1. Nog steeds in **[!DNL TargetOffersView]** voegt u de volgende code toe aan de `.task` modifier. Met deze code worden de aanbiedingen bijgewerkt wanneer de weergave wordt vernieuwd.

   ```swift
   // Clear and update offers
   await self.updatePropositionsAT(ecid: currentEcid, location: location)
   ```

U kunt extra parameters van het Doel (zoals mbox, profiel, product, of ordeparameters) in een verzoek van de verpersoonlijkingsvraag naar het netwerk van de Rand van de Ervaring verzenden, door hen in een gegevenswoordenboek toe te voegen wanneer het roepen van [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions) API. Zie voor meer informatie [Doelparameters](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/#target-parameters).


## Valideren met de app

1. De app opnieuw samenstellen en uitvoeren in de simulator of op een fysiek apparaat van Xcode met ![Afspelen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Ga naar de **[!UICONTROL Personalisatie]** tab.

1. Schuif omlaag naar de onderkant en u ziet een van de twee aanbiedingen die u in de A/B-test hebt gedefinieerd die in het dialoogvenster **[!UICONTROL DOEL]** tegel.

   <img src="assets/target-app-offer.png" width="300">


## Implementatie valideren bij Betrouwbaarheid

Om de A/B-test in betrouwbaarheid te valideren:

1. Controleer de [installatie-instructies](assurance.md#connecting-to-a-session) om de simulator of het apparaat aan te sluiten op Betrouwbaarheid.
1. Selecteren **[!UICONTROL Configureren]** in linkerspoor en selecteer ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Reviseren en simuleren]** ondergronds **[!UICONTROL ADOBE JOURNEY OPTIMIZER-BESLISSING]**.
1. Selecteren **[!UICONTROL Opslaan]**.
1. Selecteren **[!UICONTROL Reviseren en simuleren]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
1. Selecteren **[!UICONTROL Verzoeken]** op de bovenste balk. U ziet uw **[!DNL Target]** verzoeken.
   ![Validatie van AJO-beslissingen](assets/assurance-decisioning-requests.png)

1. U kunt **[!UICONTROL Simuleren]** en **[!UICONTROL Gebeurtenislijst]** tabbladen voor meer functionaliteit die uw installatie voor Target-aanbiedingen controleren.

## Volgende stappen

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing meer A/B-tests of andere doelactiviteiten (zoals Experience Targeting, Multivariate Test) aan uw app toe te voegen. Er is meer uitgebreide informatie beschikbaar in het dialoogvenster [Github repo voor de extensie Optimaliseren](https://github.com/adobe/aepsdk-optimize-ios) waar u ook een verbinding aan een specifiek kunt vinden [zelfstudie](https://opensource.adobe.com/aepsdk-optimize-ios/#/tutorials/README) op hoe je aanbiedingen van Adobe Target kunt volgen.

>[!SUCCESS]
>
>U hebt de app voor A/B-tests ingeschakeld en de resultaten van een A/B-test met Adobe Target en de Adobe Journey Optimizer - Decisioning-extensie voor de Adobe Experience Platform Mobile SDK weergegeven.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Conclusie en volgende stappen](conclusion.md)**

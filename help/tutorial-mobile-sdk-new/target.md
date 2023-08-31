---
title: A/B-tests uitvoeren met doel
description: Leer hoe u een Target A/B-test gebruikt in uw mobiele app met Platform Mobile SDK en Adobe Target.
solution: Data Collection,Target
feature-set: Target
feature: A/B Tests
hide: true
source-git-commit: 593dcce7d1216652bb0439985ec3e7a45fc811de
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---


# A/B-tests uitvoeren met doel

Leer hoe u A/B-tests kunt uitvoeren in uw mobiele apps met Platform Mobile SDK en Adobe Target.

Het doel biedt alles wat u moet aanpassen en aanpassen aan de ervaringen van uw klanten. Met Doel kunt u uw omzet maximaliseren op uw website en mobiele sites, apps, sociale media en andere digitale kanalen. In deze zelfstudie wordt de nadruk gelegd op de A/B-testfunctionaliteit van Target. Zie de [A/B-testoverzicht](https://experienceleague.adobe.com/docs/target/using/activities/abtest/test-ab.html?lang=en) voor meer informatie .

Voordat u A/B-tests kunt uitvoeren met Target, moet u ervoor zorgen dat de juiste configuraties en integratie zijn geïnstalleerd.

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Adobe Target-gebruikers die A/B-tests willen uitvoeren.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Toegang tot Adobe Target Premium met rechten, correct geconfigureerde rollen, werkruimten en eigenschappen zoals beschreven [hier](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/property-channel.html?lang=en).
U zou de Norm van het Doel ook moeten kunnen gebruiken, maar het leerprogramma gebruikt sommige geavanceerde concepten (bijvoorbeeld de eigenschappen van het Doel) die aan de Premium van het Doel uniek zijn.


## Leerdoelstellingen

In deze les zult u

* Werk uw Edge-configuratie bij voor integratie met Doel.
* Werk de eigenschap tag bij met de extensie Journey Optimizer - Decisioning.
* Werk uw schema bij om aanvraaggebeurtenissen vast te leggen.
* Valideer installatie in Betrouwbaarheid.
* Maak een eenvoudige A/B-test in Doel.
* Werk uw app bij om de extensie Optimizer op te nemen.
* Implementeer de A/B-test in uw app.
* Implementatie valideren in Betrouwbaarheid.


## Uw app instellen

>[!TIP]
>
>Als u de app al hebt ingesteld als onderdeel van de [Journey Optimizer-aanbiedingen](journey-optimizer-offers.md) zelfstudie,

### Edge-configuratie bijwerken

Om ervoor te zorgen dat gegevens die u van uw mobiele app naar het Edge-netwerk verzendt, naar Adobe Target worden doorgestuurd, moet u de Edge-configuratie bijwerken.

1. Selecteer in de gebruikersinterface voor gegevensverzameling de optie **[!UICONTROL Gegevensstromen]** en selecteert u bijvoorbeeld uw gegevensstroom **[!UICONTROL Luma Mobile-toepassing]**.
1. Selecteren **[!UICONTROL Service toevoegen]** en selecteert u **[!UICONTROL Adobe Target]** van de **[!UICONTROL Service]** lijst.
1. Voer het doel in **[!UICONTROL Eigenschapstoken]** waarde die u voor deze integratie wilt gebruiken.

   U kunt uw eigenschappen in het Doel UI, in vinden **[!UICONTROL Administratie]** > **[!UICONTROL Eigenschappen]**. Selecteren ![Code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) om het bezitstoken voor het bezit te openbaren u wilt gebruiken. De eigenschap token heeft een vergelijkbare indeling `"at_property": "xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx"`; u moet alleen de waarde invoeren `xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx`.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Doel toevoegen aan gegevensstroom](assets/edge-datastream-target.png)


### Adobe Journey Optimizer installeren - extensie voor beslissingstags

1. Navigeren naar **[!UICONTROL Tags]** en zoekt u de eigenschap voor de mobiele tag en opent u deze.
1. Selecteren **[!UICONTROL Extensies]**.
1. Selecteren **[!UICONTROL Catalogus]**.
1. Zoeken naar **[!UICONTROL Adobe Journey Optimizer - Beslissing]** extensie.
1. De extensie installeren. Voor de extensie is geen aanvullende configuratie vereist.

   ![Decisitie-extensie toevoegen](assets/tag-add-decisioning-extension.png)


### Uw schema bijwerken

1. Navigeer naar UI voor gegevensverzameling en selecteer Schema&#39;s in de linkertrack.
1. Selecteren **[!UICONTROL Bladeren]** in de bovenste balk.
1. Selecteer het schema om het te openen.
1. Selecteer in de Schema-editor de optie ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** naast **[!UICONTROL Veldgroepen]**.
1. Zoek in het dialoogvenster Veldgroepen toevoegen naar `proposition`, selecteert u **[!UICONTROL Experience Event - Propositie-interacties]** en selecteert u **[!UICONTROL Veldgroepen toevoegen]**.
   ![Voorstelling](assets/schema-fieldgroup-proposition.png)
1. om de wijzigingen in uw schema op te slaan, selecteert u **[!UICONTROL Opslaan]** .


### Setup valideren bij Betrouwbaarheid

Uw instellingen valideren in Betrouwbaarheid:

1. Ga naar de betrouwbaarheidsinterface.
1. Selecteren **[!UICONTROL Configureren]** in linkerspoor en selecteer ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Instellingen valideren]** ondergronds **[!UICONTROL ADOBE JOURNEY OPTIMIZER-BESLISSING]**.
1. Selecteren **[!UICONTROL Opslaan]**.
1. Selecteren **[!UICONTROL Instellingen valideren]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
   ![Validatie van AJO-beslissingen](assets/ajo-decisioning-validation.png)

## Een A/B-test maken

1. Selecteer in de interface Doel de optie **[!UICONTROL Activiteiten]** in de bovenste balk.
1. Selecteren **[!UICONTROL Activiteit maken]** en **[!UICONTROL A/B-test]** in het contextmenu.
1. In de **[!UICONTROL Testactiviteit A/B maken]** modal, selecteer **[!UICONTROL Mobiel]** als de **[!UICONTROL Type]**, selecteert u een werkruimte in het menu **[!UICONTROL Werkruimte kiezen]** en selecteert u de eigenschap in het menu **[!UICONTROL Eigenschap kiezen]** lijst.
1. Selecteer **[!UICONTROL Maken]**.
   ![Doelactiviteit maken](assets/target-create-activity1.png)

1. In de **[!UICONTROL Naamloze activiteit]** scherm, op **[!UICONTROL Ervaringen]** stap:

   1. Enter `luma-mobileapp-abtest` in **[!UICONTROL Locatie selecteren]** onder L**[!UICONTROL OCATIE 1]**.
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

1. In de **[!UICONTROL Targeting]** de opstelling van uw A/B-test. Beide aanbiedingen worden standaard gelijkelijk over alle bezoekers verdeeld. Selecteren **[!UICONTROL Volgende]** om door te gaan.

   ![Targeting](assets/taget-targeting.png)

1. In de **[!UICONTROL Doelstellingen en instellingen]** stap:

   1. De naam van uw activiteit zonder naam wijzigen, bijvoorbeeld in `Luma Mobile SDK Tutorial - A/B Test Example`.
   1. Voer een **[!UICONTROL Doelstelling]** voor uw A/B test bijvoorbeeld `A/B Test for Luma mobile app tutorial`.
   1. Selecteren **[!UICONTROL Conversie]**, **[!UICONTROL Klikken op mbox]** in de **[!UICONTROL Goal Metric]** > **[!UICONTROL MIJN PRIMAIRE GOAL]** tegel en voer de naam van uw locatie (mbox) in, bijvoorbeeld `luma-mobileapp-abtest`.
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
1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL AppDelegate]** in de Xcode-projectnavigator.
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

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator. Zoek de ` func updatePropositionAT(ecid: String, location: String) async` functie. De code die wordt ingesteld Inspect
   * een XDM-woordenboek `xdmData`, met de ECID om het profiel te identificeren waarvoor u de A/B-test moet presenteren, en
   * de `decisionScope`, een array van locaties waar de A/B-test moet worden gepresenteerd.

   Vervolgens roept de functie twee API&#39;s aan: [`Optimize.clearCachePropositions`](https://support.apple.com/en-ie/guide/mac-help/mchlp1015/mac)  en [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). Met deze functies worden alle in de cache opgeslagen voorstellingen gewist en worden de voorstellingen voor dit profiel bijgewerkt.

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Weergaven]** > **[!UICONTROL Personalisatie]** > **[!UICONTROL TargetOffersView]** in de Xcode-projectnavigator. Zoek de `func getPropositionAT(location: String) async` en inspecteer de code van deze functie. Het belangrijkste onderdeel van deze functie is de  [`Optimize.getPropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#getpropositions) API-aanroep, welke
   * Hiermee worden de voorstellen voor het huidige profiel opgehaald op basis van het beslissingsbereik (de locatie die u in de A/B-test hebt gedefinieerd) en
   * geeft het resultaat weer in inhoud die op de juiste wijze in de app kan worden weergegeven.

1. Nog steeds in **[!UICONTROL TargetOffersView]**, zoek de f`unc updatePropositions(location: String) async` en voeg de volgende code toe:

   ```swift
       Task {
           await self.updatePropositionAT(
               ecid: currentEcid,
               location: location
           )
       }
       try? await Task.sleep(seconds: 2.0)
       Task {
           await self.getPropositionAT(
               location: location
           )
       }
   ```

   Deze code zorgt ervoor dat u de voorstellen bijwerkt en de resultaten vervolgens ophaalt met de functies die in stap 5 en 6 worden beschreven.


## Valideren met de app

1. Open uw app op een apparaat of in de simulator.

1. Ga naar de **[!UICONTROL Personalisatie]** tab.

1. Selecteren **[!UICONTROL Edge-personalisatie]**.

1. Schuif omlaag naar de onderkant en u ziet een van de twee aanbiedingen die u in de A/B-test hebt gedefinieerd die in het dialoogvenster **[!UICONTROL DOEL]** tegel.

   <img src="assets/target-app-offer.png" width="300">


## Implementatie valideren bij Betrouwbaarheid

Om de A/B-test in betrouwbaarheid te valideren:

1. Ga naar de betrouwbaarheidsinterface.
1. Selecteren **[!UICONTROL Configureren]** in linkerspoor en selecteer ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast **[!UICONTROL Reviseren en simuleren]** ondergronds **[!UICONTROL ADOBE JOURNEY OPTIMIZER-BESLISSING]**.
1. Selecteren **[!UICONTROL Opslaan]**.
1. Selecteren **[!UICONTROL Reviseren en simuleren]** in het linkerspoor. Zowel de gegevensstroomopstelling wordt bevestigd als de opstelling van SDK in uw toepassing.
1. Selecteren **[!UICONTROL Verzoeken]** op de bovenste balk. U ziet uw **[!UICONTROL Doel]** verzoeken.
   ![Validatie van AJO-beslissingen](assets/assurance-decisioning-requests.png)

1. U kunt de tabbladen Simuleren en Gebeurtenissenlijst bekijken voor meer functionaliteit bij het controleren van de instellingen voor de aanbiedingen van Target.

## Volgende stappen

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing meer A/B-tests of andere doelactiviteiten (zoals Experience Targeting, Multivariate Test) toe te voegen aan de Luma-app.

>[!SUCCESS]
>
>U hebt de app voor A/B-tests ingeschakeld en de resultaten van een A/B-test met Adobe Target en de Adobe Journey Optimizer - Decisioning-extensie voor de Adobe Experience Platform Mobile SDK weergegeven.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Conclusie en volgende stappen](conclusion.md)**

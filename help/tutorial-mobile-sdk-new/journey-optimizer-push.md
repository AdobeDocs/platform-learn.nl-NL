---
title: Adobe Journey Optimizer-pushberichten
description: Leer hoe u pushberichten kunt maken voor een mobiele app met Platform Mobile SDK en Adobe Journey Optimizer.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Push
hide: true
source-git-commit: e119e2bdce524c834cdaf43ed9eb9d26948b0ac6
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 0%

---

# Adobe Journey Optimizer-pushberichten

Leer hoe u pushberichten voor mobiele apps kunt maken met Platform Mobile SDK en Adobe Journey Optimizer.

Met Journey Optimizer kunt u uw reizen maken en berichten sturen naar doelgroepen. Voordat u pushmeldingen verzendt met Journey Optimizer, moet u ervoor zorgen dat de juiste configuraties en integratie zijn geïnstalleerd. Als u de gegevensstroom van pushmeldingen in Adobe Journey Optimizer wilt begrijpen, raadpleegt u [de documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-gs.html).

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Adobe Journey Optimizer-gebruikers die pushberichten willen verzenden.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Toegang tot Adobe Journey Optimizer en voldoende toegangsrechten zoals beschreven [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). Ook hebt u voldoende rechten nodig voor de volgende Adobe Journey Optimizer-functies.
   * Maak een toepassingsoppervlak.
   * Een journey maken
   * Maak een bericht.
   * Voorinstellingen voor berichten maken.
* Apple-ontwikkelaarsaccount is betaald met voldoende toegang om certificaten, id&#39;s en sleutels te maken.
* Fysiek iOS-apparaat of simulator voor testen.

## Leerdoelstellingen

In deze les zult u:

* Registreer app-id bij APN (Apple Push Notification service).
* Een **[!UICONTROL App Surface]** in AJO.
* Werk uw **[!UICONTROL schema]** om velden voor pushberichten op te nemen.
* Installeer en configureer de **[!UICONTROL Adobe Journey Optimizer]** tagextensie.
* Werk uw app bij om de AJO-tagextensie op te nemen.
* Valideer installatie in Betrouwbaarheid.
* Een testbericht verzenden.
* Definieer uw eigen pushmelding voor een Journey Optimizer.
* Verzend uw eigen pushmelding vanuit de app.


## Toepassings-id registreren met APN

De volgende stappen zijn niet Adobe Experience Cloud-specifiek en zijn ontworpen om u door de configuratie van APN te begeleiden.

### Een persoonlijke sleutel maken

1. Navigeer in de Apple Developer Portal naar **[!UICONTROL Toetsen]**.
1. Selecteer **[!UICONTROL +]**.
   ![nieuwe sleutel maken](assets/mobile-push-apple-dev-new-key.png)

1. Geef een **[!UICONTROL Sleutelnaam]**.
1. Selecteer de **[!UICONTROL APN]** selectievakje.
1. Selecteren **[!UICONTROL Doorgaan]**.
   ![nieuwe sleutel configureren](assets/mobile-push-apple-dev-config-key.png)
1. Configuratie controleren en selecteren **[!UICONTROL Registreren]**.
1. Download de `.p8` persoonlijke sleutel. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
1. Noteer de [!UICONTROL Sleutel-id]. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
1. Noteer de [!UICONTROL Team-id]. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
   ![Belangrijkste details](assets/push-apple-dev-key-details.png)

Aanvullende documentatie kan [hier gevonden](https://help.apple.com/developer-account/#/devcdfbb56a3).

## Uw pushreferenties voor de app toevoegen in Gegevensverzameling

1. Van de [Interface voor gegevensverzameling](https://experience.adobe.com/data-collection/), selecteert u **[!UICONTROL Toepassingsoppervlakken]** in het linkerdeelvenster.
1. Als u een configuratie wilt maken, selecteert u **[!UICONTROL App-oppervlakken maken]**.
   ![startpagina van app](assets/push-app-surface.png)
1. Voer een **[!UICONTROL Naam]** voor de configuratie, bijvoorbeeld `Luma App Tutorial`  .
1. Selecteer in Mobiele toepassingsconfiguratie **[!UICONTROL Apple iOS]**.
1. Voer de bundel-id voor mobiele apps in het veld App ID (iOS Bundle ID) in. Als u samen met de Luma-app de waarde volgt, is `com.adobe.luma.tutorial.swiftui`.
1. Schakel de **[!UICONTROL Credentials duwen]** om uw referenties toe te voegen.
1. Sleep uw `.p8` **Apple Push Notification Authentication Key** bestand.
1. Geef de **[!UICONTROL Sleutel-id]**, een tekenreeks van 10 tekens die is toegewezen tijdens het maken van `p8` auth key. Het is te vinden onder **[!UICONTROL Toetsen]** tab in **Certificaten, id&#39;s en profielen** pagina&#39;s van de Apple Developer-portal.
1. Geef de **[!UICONTROL Team-id]**. De team-id is een waarde die u kunt vinden onder de **Lidmaatschap** of boven aan de pagina&#39;s van de Apple Developer-portal.
1. Selecteren **[!UICONTROL Opslaan]**.

   ![configuratie toepassingsoppervlak](assets/push-app-surface-config.png)

## Adobe Journey Optimizer-extensie installeren

1. Navigeren naar **[!UICONTROL Tags]** > **[!UICONTROL Extensies]** > **[!UICONTROL Catalogus]**,
1. De eigenschap openen, bijvoorbeeld **[!UICONTROL Zelfstudie voor Luma Mobile-app]**.
1. Selecteren **[!UICONTROL Catalogus]**.
1. Zoeken naar **[!UICONTROL Adobe Journey Optimizer]** extensie.
1. De extensie installeren.
1. In de **[!UICONTROL Extensie installeren]** dialoogvenster
   1. Selecteer bijvoorbeeld een omgeving **[!UICONTROL Ontwikkeling]**.
   1. Selecteer de **[!UICONTROL Dataset voor AJO-gebeurtenis voor het bijhouden van push]** gegevensset van de **[!UICONTROL Gebeurtenisgegevens]** vervolgkeuzelijst.
      ![AJO-extensie-instellingen](assets/push-tags-ajo.png)
   1. Selecteren **[!UICONTROL Opslaan in bibliotheek en samenstellen]**.

>[!NOTE]
>
>Als u het niet ziet `AJO Push Tracking Experience Event Dataset` als optie, contacteer klantenzorg.
>

## Adobe Journey Optimizer implementeren in de app

Zoals in vorige lessen is besproken, biedt het installeren van een extensie voor mobiele tags alleen de configuratie. Daarna moet u het overseinen SDK installeren en registreren. Als deze stappen niet duidelijk zijn, herzie [SDK&#39;s installeren](install-sdks.md) sectie.

>[!NOTE]
>
>Als u het [SDK&#39;s installeren](install-sdks.md) , is de SDK al geïnstalleerd en kunt u stap #7 overslaan.
>

1. Controleer in Xcode of [AEP-berichten](https://github.com/adobe/aepsdk-messaging-ios.git) wordt toegevoegd aan de lijst met pakketten in Pakketafhankelijke onderdelen. Zie [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL AppDelegate]**.
1. Zorgen `AEPMessaging` maakt deel uit van uw lijst met importbewerkingen.

   `import AEPMessaging`

1. Zorgen `Messaging.self` maakt deel uit van de array met extensies die u registreert.

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

1. Voeg de `MobileCore.setPushIdentifier` aan de `func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data)` functie.

   ```swift
   // Send push token to Experience Platform
   MobileCore.setPushIdentifier(deviceToken)
   ```

   Deze functie haalt het apparaattoken op dat uniek is voor het apparaat waarop de toepassing is geïnstalleerd. Vervolgens stelt u het token voor de levering van pushberichten in met behulp van de configuratie die u hebt ingesteld en die afhankelijk is van APNS (Push Notification Service) van Apple.

## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md) sectie.
1. Installeer de toepassing op het fysieke apparaat of op de simulator.
1. Start de app met de gegenereerde URL voor Betrouwbaarheid.
1. Selecteer in de betrouwbaarheidsinterface de optie **[!UICONTROL Configureren]**.
   ![configureren, klik](assets/push-validate-config.png)
1. Selecteer de ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knop naast **[!UICONTROL Push Debug]**.
1. Selecteren **[!UICONTROL Opslaan]**.
   ![opslaan](assets/push-validate-save.png)
1. Selecteren **[!UICONTROL Push Debug]** in de linkernavigatie.
1. Selecteer de **[!UICONTROL Instellingen valideren]** tab.
1. Selecteer het apparaat in het menu **[!UICONTROL Client]** lijst.
1. Bevestig dat u geen fouten krijgt.
   ![validate](assets/push-validate-confirm.png)
1. Selecteer de **[!UICONTROL Test Push verzenden]** tab.
1. (optioneel) Wijzig de standaarddetails voor **[!UICONTROL Titel]** en **[!UICONTROL Lichaam]**
1. Selecteren ![Bug](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bug_18_N.svg) **[!UICONTROL Melding van proefdruk verzenden]**.
1. Controleer de **[!UICONTROL Testresultaten]**.
1. De pushmelding wordt weergegeven in uw app.

   <img src="assets/luma-app-push.png" width="300" />


## Uw eigen pushmelding maken

Als u uw eigen pushmelding wilt maken, moet u een gebeurtenis in Journey Optimizer definiëren die een rit start die zorgt voor het verzenden van een pushmelding.

### Een gebeurtenis definiëren

1. Selecteer in de gebruikersinterface van Journey Optimizer **[!UICONTROL Configuraties]** van de linkerspoorstaaf.

1. In de **[!UICONTROL Dashboard]** scherm, selecteert u de **[!UICONTROL Beheren]** in de **[!UICONTROL Gebeurtenissen]** tegel.

1. In de **[!UICONTROL Gebeurtenissen]** scherm, selecteren **[!UICONTROL Gebeurtenis maken]**.

1. In de **[!UICONTROL Gebeurtenis 1 bewerken]** deelvenster:

   1. Enter `LumaTestEvent` als de **[!UICONTROL Naam]** van het evenement.
   1. Geef een **[!UICONTROL Beschrijving]** bijvoorbeeld `Test event to trigger push notifications in Luma app`.

   1. Selecteer het gebeurtenissenschema voor de mobiele app-ervaring dat u eerder hebt gemaakt in [Een XDM-schema maken](create-schema.md) van de **[!UICONTROL Schema]** lijst, bijvoorbeeld **[!UICONTROL Luma Mobile App Event-schema v.1]**.
   1. Selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) naast de lijst Velden.

      ![Gebeurtenisstap 1 bewerken](assets/ajo-edit-event1.png)

      In de **[!UICONTROL Velden]** selecteert u de volgende velden (boven op de standaardvelden die altijd zijn geselecteerd (_id, id en tijdstempel)). U kunt in de vervolgkeuzelijst schakelen tussen **[!UICONTROL Geselecteerd]**, **[!UICONTROL Alles]** en **[!UICONTROL Primair]** of de ![Zoeken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) veld.

      * **[!UICONTROL Toepassing geïdentificeerd (id)]**,
      * **[!UICONTROL Type gebeurtenis (eventType)]**,
      * **[!UICONTROL Primair (primair)]**.

      ![Gebeurtenisvelden bewerken](assets/ajo-event-fields.png)

      Selecteer vervolgens **[!UICONTROL OK]**.

   1. Selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) naast de **[!UICONTROL Voorwaarde van id van gebeurtenis]** veld.

      1. In de **[!UICONTROL Voorwaarde voor een gebeurtenis-id toevoegen]** dialoogvenster, slepen en neerzetten **[!UICONTROL Id van toepassing (id)]** ondergronds **[!UICONTROL Toepassing (toepassing)]** op **[!UICONTROL Een element hier slepen en neerzetten]**.
      1. Voer in de pop-up bijvoorbeeld uw bundel-id uit Xcode in `com.adobe.luma.tutorial.swiftui` in het veld naast **[!UICONTROL gelijk aan]**.
      1. Klikken **[!UICONTROL OK]**.
      1. Klikken **[!UICONTROL OK]**.
         ![Gebeurtenisvoorwaarde bewerken](assets/ajo-edit-condition.png)

   1. Selecteren **[!UICONTROL ECID]** van de **[!UICONTROL Naamruimte]** lijst. Automatisch de **[!UICONTROL Profiel-id]** veld is gevuld met **[!UICONTROL De id van het eerste element van de sleutel-ECID voor de map identityMap]**.
   1. Selecteren **[!UICONTROL Opslaan]**.
      ![Gebeurtenisstap 2 bewerken](assets/ajo-edit-event2.png)

U hebt zojuist een gebeurtenisconfiguratie gemaakt die is gebaseerd op het gebeurtenissenschema voor mobiele apps dat u eerder hebt gemaakt in het kader van deze zelfstudie. Met deze gebeurtenisconfiguratie worden inkomende ervaringsgebeurtenissen gefilterd met uw id voor de mobiele app. U zorgt er dus voor dat alleen gebeurtenissen die vanuit uw mobiele app worden geïnitieerd, de reis activeren die u in de volgende stap maakt.

### De reis maken

Uw volgende stap is het maken van de reis die het verzenden van de pushmelding activeert wanneer de juiste gebeurtenis wordt ontvangen.

1. Selecteer in de gebruikersinterface van Journey Optimizer **[!UICONTROL Reizen]** van de linkerspoorstaaf.
1. Selecteren **[!UICONTROL Reis maken]**.
1. In de **[!UICONTROL Reiseigenschappen]** paneel:

   1. Voer een **[!UICONTROL Naam]** bijvoorbeeld voor de reis `Luma - Test Push Notification Journey`.
   1. Voer een **[!UICONTROL Beschrijving]** bijvoorbeeld voor de reis `Journey for test push notifications in Luma mobile app`.
   1. Zorgen **[!UICONTROL Hernieuwde toegang toestaan]** is geselecteerd en ingesteld **[!UICONTROL Wachttijd bij terugkeer]** tot **[!UICONTROL 30]** **[!UICONTROL Seconden]**.
   1. Selecteren **[!UICONTROL OK]**.
      ![Journeyeigenschappen](assets/ajo-journey-properties.png)

1. Terug op het reiscanvas, van **[!UICONTROL EVENTS]**, sleept u uw ![Gebeurtenis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Globe_18_N.svg) **[!UICONTROL LumaTestEvent]** op het canvas waar het leest **[!UICONTROL Selecteer een entry-gebeurtenis of een lezen-publieksactiviteit]**.

   * In de gebeurtenissen: **[!UICONTROL LumaTestEvent]** in, voert u een **[!UICONTROL Label]** bijvoorbeeld `Luma Test Event`.

1. Van de **[!UICONTROL ACTIES]** vervolgkeuzelijst, slepen en neerzetten ![Push](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PushNotification_18_N.svg) **[!UICONTROL Push]** op de ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) die net **[!UICONTROL LumaTestEvent]** activiteit. In de **[!UICONTROL Handelingen: Push]** deelvenster:

   1. Geef een **[!UICONTROL Label]** bijvoorbeeld `Luma Test Push Notification`een **[!UICONTROL Beschrijving]** bijvoorbeeld `Test push notification for Luma mobile app`, selecteert u **[!UICONTROL Transactioneel]** van de **[!UICONTROL Categorie]** lijst en selecteer **[!UICONTROL Luminantie]** van de **[!UICONTROL Push-oppervlak]**.
   1. Selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Inhoud bewerken]** om de werkelijke pushmelding te bewerken.
      ![Push-eigenschappen](assets/ajo-push-properties.png)

      In de **[!UICONTROL Pushmelding]** editor:

      1. Voer een **[!UICONTROL Titel]** bijvoorbeeld `Luma Test Push Notification` en voert u een **[!UICONTROL Lichaam]** bijvoorbeeld `Test push notification for Luma mobile app`.
      1. Om de redacteur te bewaren en te verlaten, selecteer ![Chevron left](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronLeft_18_N.svg).
         ![Push-editor](assets/ajo-push-editor.png)

   1. Als u de definitie van het pushbericht wilt opslaan en voltooien, selecteert u **[!UICONTROL OK]**.

1. Je reis moet er hieronder uitzien. Selecteren **[!UICONTROL Publiceren]** om uw reis te publiceren en te activeren.
   ![Voltooide reis](assets/ajo-journey-finished.png)


## De pushmelding activeren

U hebt alle ingrediënten op zijn plaats om een pushmelding te verzenden. Wat overblijft, is hoe deze pushmelding wordt geactiveerd. In wezen is het hetzelfde als u eerder hebt gezien: verzend gewoon een ervaringsgebeurtenis met de juiste lading.

Dit keer wordt de ervaringsgebeurtenis die u op het punt staat te verzenden, niet samengesteld als een eenvoudig XDM-woordenboek. U gaat een instructie gebruiken die een payload van een pushmelding vertegenwoordigt. Het bepalen van een specifiek gegevenstype is een alternatieve manier op hoe te om het construeren gebeurtenislading in uw toepassing uit te voeren.

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Model]** > **[!UICONTROL XDM]** > **[!UICONTROL TestPushPayload]** en inspecteer de code.

   ```swift
   import Foundation
   
   // MARK: - TestPush
   struct TestPushPayload: Codable {
      let application: Application
      let eventType: String
   }
   
   // MARK: - Application
   struct Application: Codable {
      let id: String
   }
   ```

   De code is een representatie van de volgende eenvoudige lading die u gaat verzenden om de reis van de testpushmelding te activeren

   ```json
   {
      "eventType": string,
      "application" : [
          "id": string
      ]
   }
   ```

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in Xcode Project navigator en voeg de volgende code toe aan `func sendTestPushEvent(applicationId: String, eventType: String)`:

   ```swift
   Task {
       let testPushPayload = TestPushPayload(
           application: Application(
               id: applicationId
           ),
           eventType: eventType
       )
       // send the final experience event
       await sendExperienceEvent(
           xdm: testPushPayload.asDictionary() ?? [:]
       )
   }
   ```

   Deze code maakt een `testPushPayload` instantie die de parameters gebruikt die aan de functie worden verstrekt (`applicationId` en `eventType`) en vervolgens aanroepen `sendExperienceEvent` tijdens het omzetten van de lading in een woordenboek. Deze code, deze keer, neemt ook de asynchrone aspecten van het roepen van SDK van Adobe Experience Platform in aanmerking door het gelijktijdig valutamodel van Swift te gebruiken dat op wordt gebaseerd `await` en `async`.

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Weergaven]** > **[!UICONTROL Algemeen]** > **[!UICONTROL ConfigView]** in Xcode Project navigator. Voeg in de definitie van Knop voor pushmeldingen de volgende code toe om de lading van de testpushmelding tijdens de gebeurtenisbeleving te verzenden, zodat de rit wordt geactiveerd wanneer op die knop wordt getikt.

   ```swift
   // Setting parameters and calling function to send push notification
   let eventType = "mobileapp.testpush"
   let applicationId = Bundle.main.bundleIdentifier ?? "No bundle id found"
   await MobileSDK.shared.sendTestPushEvent(applicationId: applicationId, eventType: eventType)   
   ```


## Valideren met uw app

1. Open uw app op een apparaat of in de simulator.

1. Ga naar de **[!UICONTROL Instellingen]** tab.

1. Tikken **[!UICONTROL Pushmelding]**. De pushmelding wordt weergegeven in uw app.
   <img src="assets/ajo-test-push.png" width="300" />


## Implementeren in uw app

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing pushmeldingen toe te voegen aan de Luma-app. Bijvoorbeeld, verwelkomend de gebruiker wanneer het registreren in app, of wanneer het naderen van een specifieke geolocatie.

>[!SUCCESS]
>
>U hebt de app voor pushberichten nu ingeschakeld met Adobe Journey Optimizer en de Adobe Journey Optimizer-extensie voor de Adobe Experience Platform Mobile SDK.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[In-app berichten met Journey Optimizer](journey-optimizer-inapp.md)**


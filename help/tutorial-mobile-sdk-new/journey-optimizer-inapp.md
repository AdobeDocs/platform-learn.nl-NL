---
title: Adobe Journey Optimizer in-app messaging
description: Leer hoe u in-app berichten voor een mobiele app maakt met Platform Mobile SDK en Adobe Journey Optimizer.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: In App
hide: true
source-git-commit: ae1e05b3f93efd5f2a9b48dc10761dbe7a84fb1e
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---

# Journey Optimizer in-app messaging

Leer hoe u in-app berichten voor mobiele apps maakt met Experience Platform Mobile SDK en Journey Optimizer.

Met Journey Optimizer kunt u campagnes maken om in-app berichten naar bepaalde doelgroepen te verzenden. Campagnes in Journey Optimizer worden gebruikt om via verschillende kanalen eenmalige inhoud aan een specifiek publiek te leveren. Met campagnes, worden de acties uitgevoerd gelijktijdig, of onmiddellijk, of gebaseerd op een gespecificeerd programma. Als u reizen gebruikt (zie de [Journey Optimizer-pushberichten](journey-optimizer-push.md) les), worden handelingen op volgorde uitgevoerd.

![Architectuur](assets/architecture-ajo.png)

Voordat u in-app berichten verzendt met Journey Optimizer, moet u ervoor zorgen dat de juiste configuraties en integratie aanwezig zijn. Voor meer informatie over de gegevensstroom in de app in Journey Optimizer raadpleegt u [de documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/in-app/inapp-configuration.html?lang=en).

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Journey Optimizer-gebruikers die in-app berichten willen verzenden.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Stel de app in voor Adobe Experience Platform.
* Toegang tot Journey Optimizer en voldoende toegangsrechten zoals beschreven [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). U hebt ook voldoende machtigingen nodig voor de volgende Journey Optimizer-functies.
   * Campagnes beheren.
* Apple-ontwikkelaarsaccount is betaald met voldoende toegang om certificaten, id&#39;s en sleutels te maken.
* Fysiek iOS-apparaat of simulator voor testen.
* Geregistreerde toepassings-id met Apple Push Notification Service
* Uw pushgegevens voor de app toegevoegd in Gegevensverzameling
* Extensie Journey Optimizer-tags geïnstalleerd
* Journey Optimizer geïmplementeerd in de app


## Leerdoelstellingen

In deze les zult u

* Registreer de toepassings-id bij de APN (Apple Push Notification service).
* Maak een App Surface in AJO.
* De Journey Optimizer-tagextensie installeren en configureren.
* Werk uw app bij om de Journey Optimizer-tagextensie te registreren.
* Valideer installatie in Betrouwbaarheid.
* Definieer uw eigen campagne en berichtervaring in de app in Journey Optimizer.
* Verzend uw eigen in-app-bericht vanuit de app.

## Instellen

>[!TIP]
>
>Als u uw omgeving al hebt ingesteld als onderdeel van het [Journey Optimizer-pushberichten](journey-optimizer-push.md) Deze zelfstudie kunt u overslaan.

### Toepassings-id registreren bij APNS

De volgende stappen zijn niet Adobe Experience Cloud-specifiek en zijn ontworpen om u door de configuratie van APNS te begeleiden.

### Een persoonlijke sleutel maken

1. Navigeer in de Apple Developer Portal naar **[!UICONTROL Toetsen]**.
1. Selecteer **[!UICONTROL +]**.
   ![nieuwe sleutel maken](assets/mobile-push-apple-dev-new-key.png)

1. Geef een **[!UICONTROL Sleutelnaam]**.
1. Selecteer de **[!UICONTROL Apple Push Notification-service] (APN&#39;s)** selectievakje.
1. Selecteren **[!UICONTROL Doorgaan]**.
   ![nieuwe sleutel configureren](assets/mobile-push-apple-dev-config-key.png)
1. Controleer de configuratie en selecteer **[!UICONTROL Registreren]**.
1. Download de `.p8` persoonlijke sleutel. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
1. Noteer de **[!UICONTROL Sleutel-id]**. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
1. Noteer de **[!UICONTROL Team-id]**. Het wordt gebruikt in de configuratie van de Oppervlakte van de App.
   ![Belangrijkste details](assets/push-apple-dev-key-details.png)

Aanvullende documentatie kan [hier gevonden](https://help.apple.com/developer-account/#/devcdfbb56a3).

### Uw pushreferenties voor de app toevoegen in Gegevensverzameling

1. Van de [Interface voor gegevensverzameling](https://experience.adobe.com/data-collection/), selecteert u **[!UICONTROL Toepassingsoppervlakken]** in het linkerdeelvenster.
1. Als u een configuratie wilt maken, selecteert u **[!UICONTROL App-oppervlak maken]**.
   ![startpagina van app](assets/push-app-surface.png)
1. Voer een **[!UICONTROL Naam]** voor de configuratie, bijvoorbeeld `Luma App Tutorial`  .
1. Van **[!UICONTROL Configuratie van mobiele toepassingen]**, selecteert u **[!UICONTROL Apple iOS]**.
1. Voer de bundel-id voor de mobiele app in het dialoogvenster **[!UICONTROL Toepassings-id (iOS-bundel-id)]** veld. Bijvoorbeeld,  `com.adobe.luma.tutorial.swiftui`.
1. Schakel de **[!UICONTROL Credentials duwen]** schakelen om uw referenties toe te voegen.
1. Sleep uw `.p8` **Apple Push Notification Authentication Key** bestand.
1. Geef de **[!UICONTROL Sleutel-id]**, een tekenreeks van 10 tekens die is toegewezen tijdens het maken van `p8` auth key. Het bestand is te vinden onder de **[!UICONTROL Toetsen]** in de **Certificaten, id&#39;s en profielen** pagina&#39;s van de Apple Developer-portal. Zie ook [Een persoonlijke sleutel maken](#create-a-private-key).
1. Geef de **[!UICONTROL Team-id]**. De team-id is een waarde die u kunt vinden onder de **Lidmaatschap** of boven aan de pagina Apple Developer Portal. Zie ook [Een persoonlijke sleutel maken](#create-a-private-key).
1. Selecteren **[!UICONTROL Opslaan]**.

   ![configuratie toepassingsoppervlak](assets/push-app-surface-config.png)

### Journey Optimizer-extensie installeren

Uw app werkt alleen met Journey Optimizer als u de eigenschap tag bijwerkt.

1. Navigeren naar **[!UICONTROL Tags]** > **[!UICONTROL Extensies]** > **[!UICONTROL Catalogus]**.
1. De eigenschap openen, bijvoorbeeld **[!UICONTROL Zelfstudie voor Luma Mobile-app]**.
1. Selecteren **[!UICONTROL Catalogus]**.
1. Zoeken naar **[!UICONTROL Adobe Journey Optimizer]** extensie.
1. De extensie installeren.
1. In de **[!UICONTROL Extensie installeren]** dialoogvenster
   1. Selecteer bijvoorbeeld een omgeving **[!UICONTROL Ontwikkeling]**.
   1. Selecteer de **[!UICONTROL Dataset voor AJO-gebeurtenis voor het bijhouden van push]** gegevensset van de **[!UICONTROL Gebeurtenisgegevens]** lijst.
   1. Selecteren **[!UICONTROL Opslaan in bibliotheek en samenstellen]**.
      ![AJO-extensie-instellingen](assets/push-tags-ajo.png)

>[!NOTE]
>
>Als u het niet ziet `AJO Push Tracking Experience Event Dataset` als optie, contacteer klantenzorg.
>

### Journey Optimizer implementeren in de app

Zoals in vorige lessen is besproken, biedt het installeren van een extensie voor mobiele tags alleen de configuratie. Vervolgens moet u de SDK voor berichten installeren en registreren. Als deze stappen niet duidelijk zijn, herzie [SDK&#39;s installeren](install-sdks.md) sectie.

>[!NOTE]
>
>Als u het [SDK&#39;s installeren](install-sdks.md) is de SDK al geïnstalleerd en kunt u deze stap overslaan.
>

1. Controleer in Xcode of [AEP-berichten](https://github.com/adobe/aepsdk-messaging-ios.git) wordt toegevoegd aan de lijst met pakketten in Pakketafhankelijke onderdelen. Zie [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL AppDelegate]** in de Xcode-projectnavigator.
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


## Setup valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md) sectie.
1. Installeer de toepassing op het fysieke apparaat of op de simulator.
1. Start de app met de gegenereerde URL voor Betrouwbaarheid.
1. Selecteer in de betrouwbaarheidsinterface de optie **[!UICONTROL Configureren]**.
   ![configureren, klik](assets/push-validate-config.png)
1. Selecteer de ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knop naast **[!UICONTROL In-app berichten]**.
1. Selecteren **[!UICONTROL Opslaan]**.
   ![opslaan](assets/assurance-in-app-config.png)
1. Selecteren **[!UICONTROL In-app berichten]** in de linkernavigatie.
1. Selecteer de **[!UICONTROL Validatie]** tab. Bevestig dat u geen fouten krijgt.

   ![Validatie in de toepassing](assets/assurance-in-app-validate.png)


## Uw eigen bericht in de app maken

Als u uw eigen bericht in de app wilt maken, moet u een campagne in Journey Optimizer definiëren die een bericht in de app activeert op basis van gebeurtenissen die plaatsvinden. Deze gebeurtenissen kunnen zijn:

* naar Adobe Experience Platform verzonden gegevens;
* kern volgende gebeurtenissen, zoals actie, of staat of inzameling van PII- gegevens, door Mobile Core generische APIs;
* levenscyclusgebeurtenissen van toepassingen, zoals starten, installeren, upgraden, sluiten of vastlopen,
* gebeurtenissen voor geolocatie, zoals het betreden of afsluiten van een interessant punt.

In deze zelfstudie gaat u de generieke API&#39;s van de Mobile Core en de API&#39;s die onafhankelijk zijn van de extensie gebruiken (zie [Algemene mobiele kern-API&#39;s](https://developer.adobe.com/client-sdks/documentation/mobile-core/#mobile-core-generic-apis)) om het bijhouden van gebeurtenissen van gebruikersschermen, handelingen en PII-gegevens te vergemakkelijken. Gebeurtenissen die door deze API&#39;s worden gegenereerd, worden gepubliceerd naar de SDK-gebeurtenishub en zijn beschikbaar voor gebruik door extensies. De SDK-gebeurtenishub biedt de basisgegevensstructuur die aan alle AEP Mobile SDK-extensies is gekoppeld, een lijst met geregistreerde extensies en interne modules, een lijst met geregistreerde gebeurtenislisteners en een database met gedeelde statussen.
De SDK-gebeurtenishub publiceert en ontvangt gebeurtenisgegevens van geregistreerde extensies om de integratie met Adobe en oplossingen van derden te vereenvoudigen. Wanneer bijvoorbeeld de extensie Optimize is geïnstalleerd, worden alle verzoeken en interacties met de aanbiedingsengine van Journey Optimizer - Decision Management afgehandeld door de gebeurtenishub.

1. Selecteer in de gebruikersinterface van Journey Optimizer **[!UICONTROL Campagnes]** van de linkerspoorstaaf.
1. Selecteren **[!UICONTROL Campagne maken]**.
1. In de **[!UICONTROL Campagne maken]** scherm:
   1. Selecteren **[!UICONTROL Bericht in de app]** en selecteer een toepassingsoppervlak in het menu **[!UICONTROL App-oppervlak]** lijst, bijvoorbeeld **[!UICONTROL Luma Mobile-toepassing]**.
   1. Selecteer **[!UICONTROL Maken]**
      ![Campagneigenschappen](assets/ajo-campaign-properties.png)
1. In het scherm Campagne-definitie, op **[!UICONTROL Eigenschappen]**, voert u een **[!UICONTROL Naam]** bijvoorbeeld voor de campagne `Luma - In-App Messaging Campaign`en **[!UICONTROL Beschrijving]** bijvoorbeeld `In-app messaging campaign for Luma app`.
   ![Campagneraam](assets/ajo-campaign-properties-name.png)
1. Omlaag schuiven naar **[!UICONTROL Handeling]** en selecteert u **[!UICONTROL Inhoud bewerken]**.
1. In de **[!UICONTROL Bericht in de app]** scherm:
   1. Selecteren **[!UICONTROL Modal]** als de **[!UICONTROL Berichtlay-out]**.
   2. Enter `https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png` voor de **[!UICONTROL Media-URL]**.
   3. Voer een **[!UICONTROL Koptekst]** bijvoorbeeld `Welcome to this Luma In-App Message` en voert u een **[!UICONTROL Lichaam]** bijvoorbeeld `Triggered by pushing that button in the app...`.
   4. Enter **[!UICONTROL Afwijzen]** als de **[!UICONTROL Knop #1 tekst (primair)]**.
   5. De voorvertoning wordt bijgewerkt.
   6. Selecteren **[!UICONTROL Controleren om te activeren]**.
      ![Editor in app](assets/ajo-in-app-editor.png)
1. In de **[!UICONTROL Controleren om te activeren (Luma - Berichtencampagne in de app)]** scherm, selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) in de **[!UICONTROL Schema]** tegel.
   ![Plan voor revisie selecteren](assets/ajo-review-select-schedule.png)
1. Terug in de **[!UICONTROL Luma - in-app berichtcampagne]** scherm, selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Triggers bewerken]**.
1. In de **[!UICONTROL In-app berichttrigger]** configureren, configureert u de details van de trackactie die het bericht in de app activeert:
   1. Om te verwijderen **[!UICONTROL Gebeurtenis voor starten van toepassing]**, selecteert u ![Sluiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Close_18_N.svg) .
   1. Gebruiken ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Voorwaarde toevoegen]** herhaaldelijk de volgende logica maken voor **[!UICONTROL Bericht weergeven als]**.
   1. Klikken **[!UICONTROL Gereed]**.
      ![Triggerlogica](assets/ajo-trigger-logic.png)

   U hebt een handeling track gedefinieerd, waarbij de **[!UICONTROL Handeling]** equals `in-app` en de **[!UICONTROL Contextgegevens]** met de handeling is een sleutelwaardepaar van `"showMessage" : "true"`.

1. Terug in de **[!UICONTROL Luma - in-app berichtcampagne]** scherm, selecteren **[!UICONTROL Controleren om te activeren]**.
1. In de **[!UICONTROL Controleren om te activeren (Luma - Berichtencampagne in de app)]** scherm, selecteren **[!UICONTROL Activeren]**.
1. U ziet uw **[!UICONTROL Luma - in-app berichtcampagne]** met status **[!UICONTROL Live]** in de **[!UICONTROL Campagnes]** lijst.
   ![Lijst met campagnes](assets/ajo-campaign-list.png)


## Het bericht in de app activeren

U beschikt over alle ingrediënten om een bericht in de app te verzenden. Dit bericht in de app blijft in de app geactiveerd.

1. Ga naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator. Zoek de `func sendTrackAction(action: String, data: [String: Any]?)` en voegt de volgende code toe, die de [`MobileCore.track`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) functie, gebaseerd op de parameters `action` en `data`.


   ```swift
   // Send trackAction event
   MobileCore.track(action: action, data: data)
   ```

1. Ga naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Weergaven]** > **[!UICONTROL Algemeen]** > **[!UICONTROL ConfigView]** in de Xcode-projectnavigator. Zoek de code voor de knoop van het Bericht in-App en voeg de volgende code toe:

   ```swift
   // Setting parameters and calling function to send in-app message
   Task {
       AEPService.shared.sendTrackAction(action: "in-app", data: ["showMessage": "true"])
   }
   ```

## Valideren met uw app

1. Open uw app op een apparaat of in de simulator.

1. Ga naar de **[!UICONTROL Instellingen]** tab.

1. Tikken **[!UICONTROL Bericht in de app]**. Het bericht in de app wordt weergegeven in uw app.

   <img src="assets/ajo-in-app-message.png" width="300" />


## Implementatie valideren bij Betrouwbaarheid

U kunt uw in-app berichten in de UI van de Verzekering bevestigen.

1. Selecteren **[!UICONTROL In-app berichten]**.
1. Selecteren **[!UICONTROL Gebeurtenislijst]**.
1. Selecteer een **[!UICONTROL Bericht weergeven]** vermelding.
1. Inspect the raw event, vooral the `html`, die de volledige lay-out en inhoud van het bericht in de app bevat.
   ![Betrouwbaarheid in app-bericht](assets/assurance-in-app-display-message.png)


## Volgende stappen

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing in-app berichten toe te voegen.  Zo kunt u bijvoorbeeld producten promoten op basis van specifieke interacties die u in uw app bijhoudt.

>[!SUCCESS]
>
>U hebt de app voor berichten in de app ingeschakeld en een berichtencampagne in de app toegevoegd met Journey Optimizer en de Journey Optimizer-extensie voor de Experience Platform Mobile SDK.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Aanbiedingen weergeven met Journey Optimizer](journey-optimizer-offers.md)**

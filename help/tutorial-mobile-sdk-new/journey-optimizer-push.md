---
title: Adobe Journey Optimizer-pushberichten
description: Leer hoe u pushberichten kunt maken voor een mobiele app met Platform Mobile SDK en Adobe Journey Optimizer.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Push
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '942'
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
* Fysiek iOS-apparaat om te testen.

## Leerdoelstellingen

In deze les zult u:

* Registreer app-id bij APN (Apple Push Notification service).
* Een **[!UICONTROL App Surface]** in AJO.
* Werk uw **[!UICONTROL schema]** om velden voor pushberichten op te nemen.
* Installeer en configureer de **[!UICONTROL Adobe Journey Optimizer]** tagextensie.
* Werk uw app bij om de AJO-tagextensie op te nemen.
* Valideer installatie in Betrouwbaarheid.
* Een testbericht verzenden.


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
1. Xcode openen en naar **[!UICONTROL AppDelegate]**.
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

1. Voeg de `MobileCore.setPushIdentifier` aan de `application(_, didRegisterForRemoteNotificationsWithDeviceToken)` functie.

   ```swift {highlight="7"}
   func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data) {
       // Required to log the token
       let tokenParts = deviceToken.map { data in String(format: "%02.2hhx", data) }
       let token = tokenParts.joined()
       Logger.notifications.info("didRegisterForRemoteNotificationsWithDeviceToken - device token: \(token)")
   
       // Send push token to Experience Platform
       MobileCore.setPushIdentifier(deviceToken)
       currentDeviceToken = token
   }
   ```

   Deze functie haalt het apparaattoken op dat uniek is voor het apparaat waarop de app is geïnstalleerd en verzendt het token naar Adobe Apple voor het verzenden van pushberichten.

## Valideren door een testpushbericht te verzenden

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


>[!SUCCESS]
>
>U hebt de app voor pushberichten nu ingeschakeld met de Adobe Journey Optimizer-extensie voor de Adobe Experience Platform Mobile SDK.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Conclusie en volgende stappen](conclusion.md)**

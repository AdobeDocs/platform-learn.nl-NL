---
title: Adobe Journey Optimizer in-app messaging
description: Leer hoe u in-app berichten voor een mobiele app maakt met Platform Mobile SDK en Adobe Journey Optimizer.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
hide: true
source-git-commit: 4fa65f2e39d3fa7b8b77f5d06d51f10235474b36
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---

# Adobe Journey Optimizer in-app messaging

Leer hoe u in-app berichten voor mobiele apps maakt met Platform Mobile SDK en Adobe Journey Optimizer.

Met Journey Optimizer kunt u uw reizen maken en in-app berichten naar bepaalde doelgroepen sturen. Voordat u in-app berichten verzendt met Journey Optimizer, moet u ervoor zorgen dat de juiste configuraties en integratie aanwezig zijn. Voor meer informatie over de gegevensstroom in de app in Adobe Journey Optimizer raadpleegt u [de documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/in-app/inapp-configuration.html?lang=en).

>[!NOTE]
>
>Deze les is optioneel en is alleen van toepassing op Adobe Journey Optimizer-gebruikers die in-app berichten willen verzenden.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* Toegang tot Adobe Journey Optimizer en voldoende toegangsrechten zoals beschreven [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/configuration-message/push-config/push-configuration.html?lang=en). Ook hebt u voldoende rechten nodig voor de volgende Adobe Journey Optimizer-functies.
   * Een campagne maken.
* Apple-ontwikkelaarsaccount is betaald met voldoende toegang om certificaten, id&#39;s en sleutels te maken.
* Fysiek iOS-apparaat of simulator voor testen.
* [Geregistreerde toepassings-id met APN](journey-optimizer-push.md#register-app-id-with-apn)
* [Uw pushgegevens voor de app toegevoegd in Gegevensverzameling](journey-optimizer-push.md#add-your-app-push-credentials-in-data-collection)
* [Extensie Adobe Journey Optimizer-tags geïnstalleerd](journey-optimizer-push.md#install-adobe-journey-optimizer-tags-extension)
* [Adobe Journey Optimizer geïmplementeerd in de app](journey-optimizer-push.md#implement-adobe-journey-optimizer-in-the-app)


## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md) sectie.
1. Installeer de toepassing op het fysieke apparaat of op de simulator.
1. Start de app met de gegenereerde URL voor Betrouwbaarheid.
1. Selecteer in de betrouwbaarheidsinterface de optie **[!UICONTROL Configureren]**.
   ![configureren, klik](assets/push-validate-config.png)
1. Selecteer de ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knop naast **[!UICONTROL In-app berichten]**.
1. Selecteren **[!UICONTROL Opslaan]**.
   ![opslaan](assets/assurance-in-app-config.png)
1. Selecteren **[!UICONTROL In-app berichten]** in de linkernavigatie.
1. Selecteer de **[!UICONTROL Validatie]** tab.
1. Bevestig dat u geen fouten krijgt.
   ![Validatie in de toepassing](assets/assurance-in-app-validate.png)


## Uw eigen bericht in de app maken

Als u uw eigen bericht in de app wilt maken, moet u een campagne in Journey Optimizer definiëren die een bericht in de app activeert op basis van gebeurtenissen die plaatsvinden. Deze gebeurtenissen kunnen zijn:

* naar Adobe Experience Platform verzonden gegevens;
* kern volgende gebeurtenissen, zoals actie, of staat of inzameling van PII gegevens, door de Mobile Core generische APIs;
* levenscyclusgebeurtenissen van toepassingen, zoals starten, installeren, upgraden, sluiten of vastlopen,
* gebeurtenissen voor geolocatie, zoals het betreden of afsluiten van een interessant punt.

In deze zelfstudie gaat u de generieke API&#39;s en onafhankelijke API&#39;s voor de mobiele kern gebruiken om het bijhouden van gebeurtenissen van gebruikersschermen, handelingen en PII-gegevens te vergemakkelijken. Gebeurtenissen die door deze API&#39;s worden gegenereerd, worden gepubliceerd naar de SDK-gebeurtenishub en zijn beschikbaar voor gebruik door extensies. Wanneer bijvoorbeeld de extensie Analytics is geïnstalleerd, worden alle gebruikersacties en toepassingsschermen met gebeurtenisgegevens verzonden naar de desbetreffende eindpunten voor Analytics-rapportage.

1. Selecteer in de gebruikersinterface van Journey Optimizer **[!UICONTROL Campagnes]** van de linkerspoorstaaf.
1. Selecteren **[!UICONTROL Campagne maken]**.
1. In de **[!UICONTROL Campagne maken]** scherm:
   1. Selecteren **[!UICONTROL Bericht in de app]** en selecteert u **[!UICONTROL Luma Mobile-toepassing]** van de **[!UICONTROL App-oppervlak]** lijst.
   1. Selecteer **[!UICONTROL Maken]**
      ![Campagneigenschappen](assets/ajo-campaign-properties.png)
1. In het scherm Campagne-definitie, op **[!UICONTROL Eigenschappen]**, voert u een **[!UICONTROL Naam]** bijvoorbeeld voor de campagne `Luma - In-App Messaging Campaign`en **[!UICONTROL Beschrijving]** bijvoorbeeld `In-app messaging campaign for Luma app`.
   ![Campagneraam](assets/ajo-campaign-properties-name.png)
1. Omlaag schuiven naar **[!UICONTROL Handeling]** en selecteert u **[!UICONTROL Inhoud bewerken]**.
1. In de **[!UICONTROL Bericht in de app]** scherm:
   1. Selecteren **[!UICONTROL Modal]** als de **[!UICONTROL Berichtlay-out]**.
   1. Enter `https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png` for **[!UICONTROL Media-URL]**.
   1. Voer een **[!UICONTROL Koptekst]** bijvoorbeeld `Welcome to this Luma In-App Message` en voert u een **[!UICONTROL Lichaam]** bijvoorbeeld `Triggered by pushing that button in the app...`.
   1. Enter **[!UICONTROL Afwijzen]** als de **[!UICONTROL Knop #1 tekst (primair)]**.
   1. De voorvertoning wordt bijgewerkt.
   1. Selecteren **[!UICONTROL Controleren om te activeren]**.
      ![Editor in app](assets/ajo-in-app-editor.png)
1. In de **[!UICONTROL Controleren om te activeren (Luma - Berichtencampagne in de app)]** scherm, selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) in de **[!UICONTROL Schema]** tegel.
   ![Plan voor revisie selecteren](assets/ajo-review-select-schedule.png)
1. Terug in de **[!UICONTROL Luma - in-app berichtcampagne]** scherm, selecteren ![Bewerken](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Triggers bewerken]**.
1. In de **[!UICONTROL In-app berichttrigger]** configureren, configureert u de details van de trackactie die het bericht in de app activeert:
   1. Om te verwijderen **[!UICONTROL Gebeurtenis voor starten van toepassing]**, selecteert u ![Sluiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Close_18_N.svg) .
   1. Gebruiken ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Voorwaarde toevoegen]** herhaaldelijk de volgende logica maken voor **[!UICONTROL Bericht weergeven als]**.
   1. Klikken **[!UICONTROL Gereed]**.
      ![Triggerlogica](assets/ajo-trigger-logic.png)

   U hebt een handeling track gedefinieerd, waarbij de **[!UICONTROL Handeling]** equals `in-app` en de **[!UICONTROL Contextgegevens]** met de handeling is een sleutelwaardepaar van `showMessage = true`.

1. Terug in de **[!UICONTROL Luma - in-app berichtcampagne]** scherm, selecteren **[!UICONTROL Controleren om te activeren]**.
1. In de **[!UICONTROL Controleren om te activeren (Luma - Berichtencampagne in de app)]** scherm, selecteren **[!UICONTROL Activeren]**.
1. U ziet uw **[!UICONTROL Luma - in-app berichtcampagne]** met status **[!UICONTROL Live]** in de **[!UICONTROL Campagnes]** lijst.
   ![Lijst met campagnes](assets/ajo-campaign-list.png)


## Het bericht in de app activeren

U beschikt over alle ingrediënten om een bericht in de app te verzenden. Dit bericht in de app blijft in de code staan.

1. Ga naar Luma > Luminantie > Hulpmiddelen > MobileSDK in Xcode Project navigator, zoek de `func sendTrackAction(action: String, data: [String: Any]?)` en voegt de volgende code toe, die de `MobileCore.track` functie, gebaseerd op de parameters `action` en `data`.


   ```
   // send trackAction event
   MobileCore.track(action: action, data: data)
   ```

1. Ga naar Luma > Luminantie > Weergaven > Algemeen > ConfigView in Xcode Project Navigator. Zoek de code voor de knoop van het Bericht in-App en voeg de volgende code toe:

   ```
   Task {
       AEPService.shared.sendTrackAction(action: "in-app", data: ["showMessage": "true"])
   }
   ```

## Valideren met uw app

1. Open uw app op een apparaat of in de simulator.

1. Ga naar de **[!UICONTROL Instellingen]** tab.

1. Tikken **[!UICONTROL Bericht in de app]**. Het bericht in de app wordt weergegeven in uw app.
   <img src="assets/ajo-in-app-message.png" width="300" />


## Valideren bij Betrouwbaarheid

U kunt uw in-app berichten in de UI van de Verzekering bevestigen.

1. Selecteren **[!UICONTROL In-app berichten]**.
1. Selecteren **[!UICONTROL Gebeurtenislijst]**.
1. Selecteer een **[!UICONTROL Bericht weergeven]** vermelding.
1. Inspect the raw event, vooral the `html`, die de volledige lay-out en inhoud van het bericht in de app bevat.
   ![Betrouwbaarheid in app-bericht](assets/assurance-in-app-display-message.png)


## Implementeren in uw app

U moet nu over alle gereedschappen beschikken om waar nodig en van toepassing pushmeldingen toe te voegen aan de Luma-app. Bijvoorbeeld, verwelkomend de gebruiker wanneer het registreren in app, of wanneer het naderen van een specifieke geolocatie.

>[!SUCCESS]
>
>U hebt nu de app voor berichten in de app ingeschakeld en een berichtencampagne in de app toegevoegd met Adobe Journey Optimizer en de Adobe Journey Optimizer-extensie voor de Adobe Experience Platform Mobile SDK.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Conclusie en volgende stappen](conclusion.md)**

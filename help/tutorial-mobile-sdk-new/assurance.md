---
title: Betrouwbaarheid instellen
description: Leer hoe u de betrouwbaarheidsextensie implementeert in een mobiele app.
feature: Mobile SDK,Assurance
hide: true
source-git-commit: e119e2bdce524c834cdaf43ed9eb9d26948b0ac6
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Betrouwbaarheid

Leer hoe u Adobe Experience Platform Assurance instelt in een mobiele app.

De borging, die formeel Project Griffon wordt genoemd, wordt ontworpen om u te helpen inspecteren, beproeven, simuleren, en bevestigen hoe u gegevens verzamelt of ervaringen in uw mobiele app dient.

Met de optie Betrouwbaarheid kunt u onbewerkte SDK-gebeurtenissen controleren die zijn gegenereerd door de Adobe Experience Platform Mobile SDK. Alle gebeurtenissen die door de SDK worden verzameld, zijn beschikbaar voor inspectie. SDK-gebeurtenissen worden geladen in een lijstweergave, gesorteerd op tijd. Elke gebeurtenis heeft een gedetailleerde weergave met meer details. Er worden ook extra weergaven geboden voor het bladeren in de SDK-configuratie, gegevenselementen, Gedeelde statussen en SDK-extensieversies. Meer informatie over de [Betrouwbaarheid](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html) in de productdocumentatie.


## Vereisten

* De app is geïnstalleerd en geconfigureerd met SDK&#39;s.

## Leerdoelstellingen

In deze les zult u:

* Bevestig dat uw organisatie toegang heeft (en verzoek het als u niet).
* Stel de basis-URL in.
* Voeg de vereiste iOS-specifieke code toe.
* Maak verbinding met een sessie.

## Toegang bevestigen

Bevestig dat uw organisatie toegang tot Verzekering heeft door de volgende stappen te voltooien:

1. Bezoek [https://experience.adobe.com/assurance](https://experience.adobe.com/assurance{target="_blank"}).
1. Meld u aan met uw Adobe ID-referenties voor het Experience Cloud.
1. Als u de **[!UICONTROL Sessies]** , hebt u toegang. Als u de toegangspagina (bèta) ziet, selecteert u **[!UICONTROL Registreren]** om te registreren.

## Implementeren

Naast de algemene [SDK-installatie](install-sdks.md), die u in de vorige les hebt voltooid, vereist iOS ook de volgende toevoeging om de betrouwbaarheidssessie voor uw app te starten.

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL SceneDelegate]** in de projectnavigator van uw Xcode.

1. De volgende code toevoegen aan `func scene(_ scene: UIScene, openURLContexts URLContexts: Set<UIOpenURLContext>`:

   ```swift
   // Called when the app in background is opened with a deep link.
   if let deepLinkURL = URLContexts.first?.url {
       // Start the Assurance session
       Assurance.startSession(url: deepLinkURL)
   }
   ```

Meer informatie is beschikbaar op [hier](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/api-reference/{target="_blank"}).

## Ondertekenen

Voordat u de toepassing voor de eerste keer uitvoert in Xcode, moet u de ondertekening bijwerken.

1. Open het project in Xcode.
1. Selecteren **[!UICONTROL Luminantie]** in de Navigator.
1. Selecteer de **[!UICONTROL Luminantie]** doel.
1. Selecteer de **Ondertekenen en mogelijkheden** tab.
1. Configureren **[!UICONTROL Automatisch ondertekenen beheren]**, **[!UICONTROL Team]**, en **[!UICONTROL Bundel-id]**.

   ![Xcode-ondertekeningsmogelijkheden](assets/xcode-signing-capabilities.png)

## Een basis-URL instellen

1. Ga naar uw project in Xcode.
1. Selecteren **[!UICONTROL Luminantie]** in de Navigator.
1. Selecteer de **[!UICONTROL Luminantie]** doel.
1. Selecteer de **Info** tab.
1. Als u een basis-URL wilt toevoegen, schuift u omlaag naar **URL-typen** en selecteert u de **+** knop.
1. Set **Id** aan de bundel-id waarin u zich hebt geconfigureerd [Ondertekenen](#signing) (bijvoorbeeld `com.adobe.luma.tutorial.swiftui`) en **URL-schema&#39;s** tot `lumatutorialswiftui`.

   ![verzekerings-URL](assets/assurance-url-type.png)

Voor meer informatie over URL-schema&#39;s in iOS raadpleegt u [Apple-documentatie](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app{target="_blank"}).

De verzekering werkt door een URL, of via browser of QR code te openen. Die URL begint met de basis-URL die de app opent en aanvullende parameters bevat. Deze unieke parameters worden gebruikt om de sessie te verbinden.


## Verbinding maken met een sessie

1. Voer de toepassing uit in de simulator of op een aangesloten fysiek apparaat.
1. Selecteren **[!UICONTROL Betrouwbaarheid]** van de linkerspoorlijn in de UI van de Inzameling van Gegevens.
1. Selecteren **[!UICONTROL Sessie maken]**.
1. Selecteren **[!UICONTROL Start]**.
1. Geef een **[!UICONTROL Naam van sessie]** zoals `Luma Mobile App Session` en de **[!UICONTROL Basis-URL]**, dit zijn de URL-schema&#39;s die u hebt ingevoerd in Xcode, gevolgd door `://`. Bijvoorbeeld: `lumatutorialswiftui://`.
1. Selecteren **[!UICONTROL Volgende]**.
   ![betrouwbaarheidssessie maken](assets/assurance-create-session.png)
1. In de **[!UICONTROL Nieuwe sessie maken]** modale dialoog:

   Als u een fysiek apparaat gebruikt:

   * Selecteren **[!UICONTROL QR-code scannen]**. Gebruik uw camera op uw fysieke apparaat om de QR-code te scannen en tik op de koppeling om de app te openen.

     ![betrouwbaarheidsQA-code](assets/assurance-qr-code.png)

   Als u een simulator gebruikt:

   1. Selecteren **[!UICONTROL Koppeling kopiëren]**.
   1. De diepe koppeling kopiëren met de kopie ![Kopiëren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) en gebruik de diepe koppeling om de app met Safari in de simulator te openen.
      ![Koppeling naar kopie voor controle](assets/assurance-copy-link.png)

1. Wanneer de app wordt geladen, ziet u een modaal dialoogvenster waarin u wordt gevraagd de pincode in te voeren die in stap 7 wordt getoond.

   <img src="assets/assurance-enter-pin.png" width="300">

   Voer de pincode in en selecteer **[!UICONTROL Verbinden]**.


1. Als de verbinding tot stand is gebracht, ziet u:
   * Er zweeft een verzekeringspictogram boven op uw app.

   <img src="assets/assurance-modal.png" width="300">

   * De updates van het Experience Cloud die door in Assurance web-based UI komen, die tonen:

      1. Ervaar gebeurtenissen die afkomstig zijn uit de app.
      1. Details van een geselecteerde gebeurtenis.
      1. Het apparaat en de tijdlijn.

     ![betrouwbaarheidsgebeurtenissen](assets/assurance-events.png)

Als u problemen ondervindt, kunt u de [technisch](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/{target="_blank"}) en [algemene documentatie](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html{target="_blank"}).

>[!SUCCESS]
>
>U hebt nu een app ingesteld om Verzekering te gebruiken voor de rest van de zelfstudie.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)


Volgende: **[Toestemming](consent.md)**

---
title: Betrouwbaarheid instellen
description: Leer hoe u de betrouwbaarheidsextensie implementeert in een mobiele app.
feature: Mobile SDK,Assurance
hide: true
exl-id: 49d608e7-e9c4-4bc8-8a8a-5195f8e2ba42
source-git-commit: d7410a19e142d233a6c6597de92f112b961f5ad6
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 0%

---

# Betrouwbaarheid instellen

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

Bevestig dat uw organisatie toegang tot Verzekering heeft. U moet als gebruiker aan het profiel voor Adobe Experience Platform worden toegevoegd. Zie [Toegang van gebruikers](https://experienceleague.adobe.com/docs/experience-platform/assurance/user-access.html?lang=en) in de handleiding voor verzekeringen voor meer informatie.

## Implementeren

Naast de algemene [SDK-installatie](install-sdks.md), die u in de vorige les hebt voltooid, vereist iOS ook de volgende toevoeging om de betrouwbaarheidssessie voor uw app te starten.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** in de projectnavigator van uw Xcode.

1. De volgende code toevoegen aan `func scene(_ scene: UIScene, openURLContexts URLContexts: Set<UIOpenURLContext>`:

   ```swift
   // Called when the app in background is opened with a deep link.
   if let deepLinkURL = URLContexts.first?.url {
       // Start the Assurance session
       Assurance.startSession(url: deepLinkURL)
   }
   ```

   Met deze code wordt een verzekeringssessie gestart wanneer de app op de achtergrond wordt uitgevoerd en met een diepe koppeling wordt geopend.

Meer informatie is beschikbaar op [hier](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/api-reference/){target="_blank"}.

## Ondertekenen

Voordat u de toepassing voor de eerste keer uitvoert in Xcode, moet u de ondertekening bijwerken.

1. Open het project in Xcode.
1. Selecteren **[!DNL Luma]** in de projectnavigator.
1. Selecteer de **[!DNL Luma]** doel.
1. Selecteer de **Ondertekenen en mogelijkheden** tab.
1. Configureren **[!UICONTROL Automatisch ondertekenen beheren]**, **[!UICONTROL Team]**, en **[!UICONTROL Bundel-id]** of gebruik uw specifieke Apple-ontwikkelinrichtingsgegevens.

   >[!IMPORTANT]
   >
   >Zorg ervoor dat u een _uniek_ bundel-id en vervang de `Luma` bundel-id, aangezien elke bundel-id uniek moet zijn. Gewoonlijk gebruikt u een omgekeerde DNS-indeling voor bundle ID-tekenreeksen, zoals `com.organization.brand.uniqueidentifier`. De voltooide versie van deze zelfstudie gebruikt bijvoorbeeld `com.adobe.luma.tutorial.swiftui`.


   ![Xcode-ondertekeningsmogelijkheden](assets/xcode-signing-capabilities.png){zoomable=&quot;yes&quot;}

## Een basis-URL instellen

1. Ga naar uw project in Xcode.
1. Selecteren **[!DNL Luma]** in de projectnavigator.
1. Selecteer de **[!DNL Luma]** doel.
1. Selecteer de **Info** tab.
1. Als u een basis-URL wilt toevoegen, schuift u omlaag naar **URL-typen** en selecteert u de **+** knop.
1. Set **Id** aan de bundel-id waarin u zich hebt geconfigureerd [Ondertekenen](#signing) (bijvoorbeeld `com.adobe.luma.tutorial.swiftui`) en stelt een **URL-schema&#39;s** bijvoorbeeld `lumatutorialswiftui`.

   ![verzekerings-URL](assets/assurance-url-type.png)

Voor meer informatie over URL-schema&#39;s in iOS raadpleegt u [Apple-documentatie](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app){target="_blank"}.

De verzekering werkt door een URL, of via browser of QR code te openen. Die URL begint met de basis-URL die de app opent en aanvullende parameters bevat. Deze unieke parameters worden gebruikt om de sessie te verbinden.


## Verbinding maken met een sessie

1. De app opnieuw samenstellen en uitvoeren in de simulator of op een fysiek apparaat van Xcode met ![Afspelen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).
1. Selecteren **[!UICONTROL Betrouwbaarheid]** van de linkerspoorlijn in de UI van de Inzameling van Gegevens.
1. Selecteren **[!UICONTROL Sessie maken]**.
1. Selecteren **[!UICONTROL Start]**.
1. Geef een **[!UICONTROL Naam van sessie]** zoals `Luma Mobile App Session` en de **[!UICONTROL Basis-URL]**, dit zijn de URL-schema&#39;s die u hebt ingevoerd in Xcode, gevolgd door `://` Bijvoorbeeld: `lumatutorialswiftui://`
1. Selecteren **[!UICONTROL Volgende]**.
   ![betrouwbaarheidssessie maken](assets/assurance-create-session.png)
1. In de **[!UICONTROL Nieuwe sessie maken]** modale dialoog:

   Als u een fysiek apparaat gebruikt:

   * Selecteren **[!UICONTROL QR-code scannen]**. Gebruik uw camera op uw fysieke apparaat om de QR-code te scannen en tik op de koppeling om de app te openen.

     ![betrouwbaarheidsQA-code](assets/assurance-qr-code.png)

   Als u een simulator gebruikt:

   1. Selecteren **[!UICONTROL Koppeling kopiëren]**.
   1. De diepe koppeling kopiëren met ![Kopiëren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)  en gebruik de diepe koppeling om de app met Safari in de simulator te openen.
      ![Koppeling naar kopie voor controle](assets/assurance-copy-link.png)

1. Wanneer de app wordt geladen, ziet u een modaal dialoogvenster waarin u wordt gevraagd de pincode in te voeren die in stap 7 wordt getoond.

   <img src="assets/assurance-enter-pin.png" width="300">

   Voer de pincode in en selecteer **[!UICONTROL Verbinden]**.


1. Als de verbinding tot stand is gebracht, ziet u:
   * Er zweeft een verzekeringspictogram boven op uw app.

     <img src="assets/assurance-modal.png" width="300">

   * De updates van het Experience Cloud die door in Assurance UI komen, die tonen:

      1. Ervaar gebeurtenissen die afkomstig zijn uit de app.
      1. Details van een geselecteerde gebeurtenis.
      1. Het apparaat en de tijdlijn.

         ![betrouwbaarheidsgebeurtenissen](assets/assurance-events.png)

Als u problemen ondervindt, kunt u de [technisch](https://developer.adobe.com/client-sdks/documentation/platform-assurance-sdk/){target="_blank"} and [general documentation](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html){target="_blank"}.


## Extensies verifiëren

Om te controleren of uw app de meest actuele extensies gebruikt:

1. Selecteren **[!UICONTROL Configureren]**.

1. Selecteren ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) for ![123](https://spectrum.adobe.com/static/icons/workflow_18/Smock_123_18_N.svg) **[!UICONTROL Extensieversies]**.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Extensieversies configureren](assets/assurance-configure-extension-versions.png)

1. Selecteren ![123](https://spectrum.adobe.com/static/icons/workflow_18/Smock_123_18_N.svg) **[!UICONTROL Extensieversies]**. Er wordt een overzicht weergegeven van de meest recente beschikbare extensies en de extensies die worden gebruikt in uw versie van de app.

   ![Extensies](assets/assurance-extension-versions.png)

1. De extensieversies bijwerken (bijvoorbeeld **[!UICONTROL Berichten]** en **[!UICONTROL Optimaliseren]**), in Xcode, voor de specifieke extensies die een upgrade nodig hebben, selecteert u het pakket (extensie) van **[!UICONTROL Pakketafhankelijke onderdelen]** (bijvoorbeeld **[!UICONTROL AEPMessaging]**) en in het contextmenu selecteert u **[!UICONTROL Pakket bijwerken]**. Xcode werkt de pakketafhankelijkheden bij.


>[!NOTE]
>
>Wanneer u de extensies (pakketten) in Xcode hebt bijgewerkt, moet u de huidige sessie sluiten en verwijderen en alle stappen uit [Verbinding maken met een sessie](#connecting-to-a-session) en [Extensies verifiëren](#verify-extensions) om ervoor te zorgen dat de verzekering de juiste extensies in een nieuwe betrouwbaarheidssessie meldt.





>[!SUCCESS]
>
>U hebt nu een app ingesteld om Verzekering te gebruiken voor de rest van de zelfstudie.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)


Volgende: **[Goedkeuring implementeren](consent.md)**

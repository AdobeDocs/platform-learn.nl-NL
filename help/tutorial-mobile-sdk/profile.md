---
title: Profielgegevens verzamelen met Platform Mobile SDK
description: Leer hoe u profielgegevens kunt verzamelen in een mobiele app.
jira: KT-14634
exl-id: 97717611-04d9-45e3-a443-ea220a13b57c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# Profielgegevens verzamelen

Leer hoe u profielgegevens kunt verzamelen in een mobiele app.

U kunt de extensie Profiel gebruiken om kenmerken van de gebruiker op de client op te slaan. Deze informatie kan later worden gebruikt om berichten tijdens online of off-line scenario&#39;s te richten en te personaliseren, zonder het moeten met een server voor optimale prestaties verbinden. De extensie Profiel beheert het Client-Side Operation Profile (CSOP), biedt een manier om op API&#39;s te reageren, werkt gebruikersprofielkenmerken bij en deelt de gebruikersprofielkenmerken met de rest van het systeem als een gegenereerde gebeurtenis.

De profielgegevens worden door andere extensies gebruikt om acties met betrekking tot profielen uit te voeren. Een voorbeeld is de uitbreiding van de Motor van Regels die de profielgegevens verbruikt en regels in werking stelt die op de profielgegevens worden gebaseerd. Leer meer over de [ uitbreiding van het Profiel ](https://developer.adobe.com/client-sdks/documentation/profile/) in de documentatie

>[!IMPORTANT]
>
>De functionaliteit Profiel die in deze les wordt beschreven is los van de Real-Time functionaliteit van het Profiel van de Klant in Adobe Experience Platform en Platform-based toepassingen.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Gebruikerskenmerken instellen of bijwerken.
* Gebruikerskenmerken ophalen.


## Gebruikerskenmerken instellen en bijwerken

Het zou handig zijn als u zich richt op en/of personalisatie in de app om snel te weten of een gebruiker in het verleden of onlangs een aankoop heeft gedaan. Laten we dat instellen in de Luma-app.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** in de Xcode Project navigator en zoek de `func updateUserAttribute(attributeName: String, attributeValue: String)` functie. Voeg de volgende code toe:

   ```swift
   // Create a profile map, add attributes to the map and update profile using the map
   var profileMap = [String: Any]()
   profileMap[attributeName] = attributeValue
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

   Deze code:

   1. Hiermee wordt een leeg woordenboek met de naam `profileMap` ingesteld.

   1. Hiermee voegt u een element aan het woordenboek toe met `attributeName` (bijvoorbeeld `isPaidUser` ) en `attributeValue` (bijvoorbeeld `yes` ).

   1. Gebruikt het `profileMap` woordenboek als waarde aan de `attributeDict` parameter van de [`UserProfile.updateUserAttributes` ](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattributes) API vraag.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!DNL ProductView]** in de Xcode Project navigator en zoek de aanroep naar `updateUserAttributes` (in de code voor Aankopen) <img src="assets/purchase.png" width="15" /> ). Voeg de volgende code toe:

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttribute(attributeName: "isPaidUser", attributeValue: "yes")
   ```


## Gebruikerskenmerken ophalen

Nadat u het kenmerk van een gebruiker hebt bijgewerkt, is het beschikbaar voor andere Adobe-SDK&#39;s, maar u kunt kenmerken ook expliciet ophalen, zodat de toepassing zich naar wens gedraagt.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!DNL HomeView]** in de Xcode-projectnavigator en zoek de optie `.onAppear` . Voeg de volgende code toe:

   ```swift
   // Get attributes
   UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
       if attributes?.count ?? 0 > 0 {
           if attributes?["isPaidUser"] as? String == "yes" {
               showBadgeForUser = true
           }
           else {
               showBadgeForUser = false
           }
       }
   }
   ```

   Deze code:

   1. Roept de [`UserProfile.getUserAttributes` ](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes) API met de `isPaidUser` attribuutnaam als enig element in de `attributeNames` serie.
   1. Vervolgens wordt gecontroleerd op de waarde van het kenmerk `isPaidUser` en wanneer `yes` een badge op het tabblad <img src="assets/paiduser.png" width="20" /> in de werkbalk rechtsboven.

De extra documentatie kan [ hier ](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes) worden gevonden.

## Valideren met betrouwbaarheid

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat aan Verzekering te verbinden.
1. Voer de app uit om u aan te melden en te communiceren met een product.

   1. Verplaats het pictogram Verzekering naar links.
   1. Selecteer **[!UICONTROL Home]** in de tabbalk.
   1. Als u het aanmeldingsblad wilt openen, selecteert u de optie <img src="assets/login.png" width="15" /> .

      <img src="./assets/mobile-app-events-1.png" width="300">

   1. Als u een willekeurige e-mail en een klant-id wilt invoegen, selecteert u de <img src="assets/insert.png" width="15" /> .
   1. Selecteer **[!UICONTROL Login]**.

      <img src="./assets/mobile-app-events-2.png" width="300">

   1. Selecteer **[!DNL Products]** in de tabbalk.
   1. Selecteer één product.
   1. Selecteren <img src="assets/saveforlater.png" width="15" />.
   1. Selecteren <img src="assets/addtocart.png" width="20" />.
   1. Selecteren <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">

   1. Ga terug naar **[!UICONTROL Home]** screen. Je moet zien dat er een badge is toegevoegd <img src="assets/person-badge-icon.png" width="15" />.

      <img src="./assets/personbadges.png" width="300">



1. In de gebruikersinterface van Verzekering worden **[!UICONTROL UserProfileUpdate]** - en **[!UICONTROL getUserAttributes]** -gebeurtenissen met de bijgewerkte `profileMap` -waarde weergegeven.
   ![ bevestigt profiel ](assets/profile-validate.png)

>[!SUCCESS]
>
>U hebt nu uw app ingesteld om kenmerken van profielen in de Edge Network bij te werken en (wanneer deze is ingesteld) met Adobe Experience Platform.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van de Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[Plaatsen van het Gebruik](places.md)**

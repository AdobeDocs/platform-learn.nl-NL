---
title: Profielgegevens verzamelen
description: Leer hoe u profielgegevens kunt verzamelen in een mobiele app.
hide: true
exl-id: 6ce02ccc-6280-4a1f-a96e-1975f8a0220a
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Profielgegevens verzamelen

Leer hoe u profielgegevens kunt verzamelen in een mobiele app.

U kunt de extensie Profiel gebruiken om kenmerken van de gebruiker op de client op te slaan. Deze informatie kan later worden gebruikt om berichten tijdens online of off-line scenario&#39;s te richten en te personaliseren, zonder het moeten met een server voor optimale prestaties verbinden. De extensie Profiel beheert het Client-Side Operation Profile (CSOP), biedt een manier om op API&#39;s te reageren, werkt gebruikersprofielkenmerken bij en deelt de gebruikersprofielkenmerken met de rest van het systeem als een gegenereerde gebeurtenis.

De profielgegevens worden door andere extensies gebruikt om acties met betrekking tot profielen uit te voeren. Een voorbeeld is de uitbreiding van de Motor van Regels die de profielgegevens verbruikt en regels in werking stelt die op de profielgegevens worden gebaseerd. Meer informatie over de [Profielextensie](https://developer.adobe.com/client-sdks/documentation/profile/) in de documentatie

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

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** >  **[!DNL MobileSDK]** in de Xcode-projectnavigator en zoek de `func updateUserAttributes(attributeName: String, attributeValue: String)` functie. Voeg de volgende code toe:

   ```swift
   // Create a profile map, add attributes to the map and update profile using the map
   var profileMap = [String: Any]()
   profileMap[attributeName] = attributeValue
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

   Deze code:

   1. Hiermee wordt een leeg woordenboek ingesteld met de naam `profileMap`.

   1. Hiermee wordt een element aan het woordenboek toegevoegd met `attributeName` (bijvoorbeeld `isPaidUser`), en `attributeValue` (bijvoorbeeld `yes`).

   1. Gebruikt de `profileMap` woordenboek als een waarde voor de `attributeDict` parameter van de [`UserProfile.updateUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattributes) API-aanroep.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!DNL ProductView]** in de navigator van het Project van Xcode en vind de vraag aan `updateUserAttributes` (binnen de code voor de aankopen <img src="assets/purchase.png" width="15" /> ). Voeg de volgende code toe:

   ```swift
   // Update attributes
   MobileSDK.shared.updateUserAttributes(attributeName: "isPaidUser", attributeValue: "yes")
   ```


## Gebruikerskenmerken ophalen

Nadat u het kenmerk van een gebruiker hebt bijgewerkt, is het beschikbaar voor andere Adobe-SDK&#39;s, maar u kunt kenmerken ook expliciet ophalen, zodat de toepassing zich naar wens gedraagt.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!DNL HomeView]** in de Xcode-projectnavigator en zoek de `.onAppear` modifier. Voeg de volgende code toe:

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

   1. roept de [`UserProfile.getUserAttributes`](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes) API met de `iPaidUser` kenmerknaam als één element in het dialoogvenster `attributeNames` array.
   1. Vervolgens wordt gecontroleerd op de waarde van de optie `isPaidUser` kenmerk en wanneer `yes`, plaatst een badge op de <img src="assets/paiduser.png" width="20" /> in de werkbalk rechtsboven.

Aanvullende documentatie is te vinden [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md#connecting-to-a-session) om de simulator of het apparaat aan te sluiten op Betrouwbaarheid.
1. Voer de app uit om u aan te melden en te communiceren met een product.

   1. Verplaats het pictogram Verzekering naar links.
   1. Selecteren **[!UICONTROL Home]** in de tabbalk.
   1. Als u het aanmeldingsblad wilt openen, selecteert u de optie <img src="assets/login.png" width="15" /> knop.

      <img src="./assets/mobile-app-events-1.png" width="300">

   1. Als u een willekeurige e-mail en een klant-id wilt invoegen, selecteert u de <img src="assets/insert.png" width="15" /> knop .
   1. Selecteren **[!UICONTROL Aanmelden]**.

      <img src="./assets/mobile-app-events-2.png" width="300">

   1. Selecteren **[!DNL Products]** in de tabbalk.
   1. Selecteer één product.
   1. Selecteer <img src="assets/saveforlater.png" width="15" />.
   1. Selecteer <img src="assets/addtocart.png" width="20" />.
   1. Selecteer <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">

   1. Terug naar **[!UICONTROL Home]** scherm. Je moet zien dat er een badge is toegevoegd <img src="assets/person-badge-icon.png" width="15" />.

      <img src="./assets/personbadges.png" width="300">



1. In de UI van de Verzekering, zou u een **[!UICONTROL UserProfileUpdate]** en **[!UICONTROL getUserAttributes]** gebeurtenissen met de bijgewerkte `profileMap` waarde.
   ![profiel valideren](assets/profile-validate.png)

>[!SUCCESS]
>
>U hebt nu uw app ingesteld om kenmerken van profielen in het Edge-netwerk bij te werken en (wanneer deze is ingesteld) met Adobe Experience Platform.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Plaatsen gebruiken](places.md)**

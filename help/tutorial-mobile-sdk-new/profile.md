---
title: Profiel
description: Leer hoe u profielgegevens kunt verzamelen in een mobiele app.
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Profiel

Leer hoe u profielgegevens kunt verzamelen in een mobiele app.

U kunt de extensie Profiel gebruiken om kenmerken van de gebruiker op de client op te slaan. Deze informatie kan later worden gebruikt om berichten tijdens online of off-line scenario&#39;s te richten en te personaliseren, zonder het moeten met een server voor optimale prestaties verbinden. De extensie Profiel beheert het Client-Side Operation Profile (CSOP), biedt een manier om op API&#39;s te reageren, werkt gebruikersprofielkenmerken bij en deelt de gebruikersprofielkenmerken met de rest van het systeem als een gegenereerde gebeurtenis.

De profielgegevens worden door andere extensies gebruikt om acties met betrekking tot profielen uit te voeren. Een voorbeeld is de uitbreiding van de Motor van Regels die de profielgegevens verbruikt en regels in werking stelt die op de profielgegevens worden gebaseerd. Meer informatie over de [Profielextensie](https://developer.adobe.com/client-sdks/documentation/profile/) in de documentatie

>[!IMPORTANT]
>
>De functionaliteit Profiel die in deze les wordt beschreven is los van de Real-Time functionaliteit van het Profiel van de Klant in Adobe Experience Platform en Platform-based toepassingen.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.
* De SDK van het profiel is geïmporteerd.

  ```swift
  import AEPUserProfile
  ```

## Leerdoelstellingen

In deze les zult u:

* Gebruikerskenmerken instellen of bijwerken.
* Gebruikerskenmerken ophalen.


## Instellen en bijwerken

Het zou handig zijn als u zich richt op en/of personalisatie om snel te weten of een gebruiker al eerder een aankoop heeft gedaan in de app. Laten we dat instellen in de Luma-app.

1. Navigeren naar **[!UICONTROL ProductView]** (in **[!UICONTROL Weergaven]** > **[!UICONTROL Producten]**) in het app-project Xcode Luma en zoek naar `updateUserAttributes` (in de knop Aankopen):

   ```swift {highlight="8-9"}
   Button {
       Task {
           if ATTrackingManager.trackingAuthorizationStatus == .authorized {
               // Send purchase commerce experience event
               MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
               // Update attributes
               MobileSDK.shared.updateUserAttributes(attributeName: "isPaidUser", attributeValue: "yes")
           }
       }
       showPurchaseDialog.toggle()
   } label: {
       Label("", systemImage: "creditcard")
   }
   .alert(isPresented: $showPurchaseDialog, content: {
       Alert(title: Text( "Purchases"), message: Text("The selected item is purchased…"))
   })
   ```

2. Navigeren naar **[!UICONTROL MobileSDK]** en de `updateUserAttributes` functie. Voeg de volgende gemarkeerde code toe:

   ```swift {highlight="2-4"}
   func updateUserAttributes(attributeName: String, attributeValue: String) {
       var profileMap = [String: Any]()
       profileMap[attributeName] = attributeValue
       UserProfile.updateUserAttributes(attributeDict: profileMap)
   }
   ```

   Deze code:

   1. Hiermee wordt een leeg woordenboek ingesteld met de naam `profileMap`.

   1. Hiermee wordt een element aan het woordenboek toegevoegd met `attributeName` (bijvoorbeeld `isPaidUser`), en `attributeValue` (bijvoorbeeld `yes`).

   1. Gebruikt de `profileMap` woordenboek als een waarde voor de `attributeDict` parameter van de `UserProfile.updateUserAttributes` API-aanroep.


Extra `updateUserAttributes` documentatie is te vinden [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattribute).

## Get

Zodra u het attribuut van een gebruiker hebt bijgewerkt, is het beschikbaar aan andere Adobe SDKs maar u kunt attributen ook uitdrukkelijk terugwinnen.

1. Navigeren naar **[!UICONTROL HomeView]** (in **[!UICONTROL Weergaven]** > **[!UICONTROL Algemeen]**) en de `.onAppear` modifier. Voeg de volgende code toe:

   ```swift {highlight="3-11"}
   .onAppear {
       // Track view screen
       MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: home")
       // Get attributes
       UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
           if attributes?["isPaidUser"] as! String == "yes" {
               showBadgeForUser = true
           }
           else {
               showBadgeForUser = false
           }
       }
   }
   ```

   Deze code:

   1. roept de `UserProfile.getUserAttributes` sluiting met de `iPaidUser` kenmerknaam als één element in het dialoogvenster `attributeNames` array.
   1. Vervolgens wordt gecontroleerd op de waarde van de optie `isPaidUser` kenmerk en wanneer `yes`, plaatst u een badge op het pictogram Person rechtsboven.

Extra `getUserAttributes` documentatie is te vinden [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md) sectie.
1. Installeer de toepassing.
1. Start de app met de gegenereerde URL voor Betrouwbaarheid.
1. Voer de app uit om u aan te melden en te communiceren met een product.

   1. Verplaats het pictogram Verzekering naar links.
   1. Selecteren **[!UICONTROL Home]** in de tabbalk.
   1. Als u het aanmeldingsblad wilt openen, selecteert u de optie **[!UICONTROL Aanmelden]** knop.
   1. Als u een willekeurige e-mail en een klant-id wilt invoegen, selecteert u de **[!UICONTROL A|]** knop .
   1. Selecteren **[!UICONTROL Aanmelden]**.
   1. Selecteren **[!UICONTROL Producten]** in de tabbalk.
   1. Selecteer één product.
   1. Selecteren **[!UICONTROL Opslaan voor later]**.
   1. Selecteren **[!UICONTROL Toevoegen aan winkelwagentje]**.
   1. Selecteren **[!UICONTROL Aanschaffen]**.
   1. Terug naar **[!UICONTROL Home]** scherm. U zou een bijgewerkte Login knoop moeten zien.

      <img src="./assets/mobile-app-events-1.png" width="200"> <img src="./assets/mobile-app-events-2.png" width="200"> <img src="./assets/mobile-app-events-3.png" width="200"> <img src="./assets/personbadges.png" width="200">

1. U dient een **[!UICONTROL UserProfileUpdate]** en **[!UICONTROL getUserAttributes]** gebeurtenissen in de betrouwbaarheidsinterface met de bijgewerkte versie `profileMap` waarde.
   ![profiel valideren](assets/profile-validate.png)

>[!SUCCESS]
>
>U hebt nu uw app ingesteld om kenmerken van profielen in het Edge-netwerk bij te werken en (wanneer deze is ingesteld) met Adobe Experience Platform.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Gegevens toewijzen aan Adobe Analytics](analytics.md)**

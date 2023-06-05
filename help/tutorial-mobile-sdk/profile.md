---
title: Profiel
description: Leer hoe u profielgegevens kunt verzamelen in een mobiele app.
exl-id: 97717611-04d9-45e3-a443-ea220a13b57c
source-git-commit: b2e1bf08d9fb145ba63263dfa078c96258342708
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 1%

---

# Profiel

Leer hoe u profielgegevens kunt verzamelen in een mobiele app.

U kunt de extensie Profiel gebruiken om kenmerken van de gebruiker op de client op te slaan. Deze informatie kan later worden gebruikt om berichten tijdens online of off-line scenario&#39;s te richten en te personaliseren, zonder het moeten met een server voor optimale prestaties verbinden. De extensie Profiel beheert het Client-Side Operation Profile (CSOP), biedt een manier om op API&#39;s te reageren, werkt gebruikersprofielkenmerken bij en deelt de gebruikersprofielkenmerken met de rest van het systeem als een gegenereerde gebeurtenis.

De profielgegevens worden door andere extensies gebruikt om acties met betrekking tot profielen uit te voeren. Een voorbeeld is de uitbreiding van de Motor van Regels die de profielgegevens verbruikt en regels in werking stelt die op de profielgegevens worden gebaseerd. Meer informatie over de [Profielextensie](https://developer.adobe.com/client-sdks/documentation/profile/) in de documentatie

>[!IMPORTANT]
>
>De functionaliteit Profiel die in deze les wordt beschreven is los van de functionaliteit Real-Time Klantprofiel in Adobe Experience Platform en op Platform gebaseerde toepassingen.


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

Het zou handig zijn als u zich richt op en/of personalisatie om snel te weten of een gebruiker eerder een aankoop in de app heeft gedaan. Laten we dat instellen in de Luma-app.

1. Ga naar `Cart.swift`

1. Voeg de onderstaande code toe aan de `processOrder() `functie.

   ```swift
   var profileMap = [String: Any]()
   profileMap["isPaidUser"] = "yes"
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

Het verpersoonlijkingsteam zou ook kunnen willen richten gebaseerd op het loyaliteitsniveau van de gebruiker. Laten we dat instellen in de Luma-app.

1. Ga naar `Account.swift`

1. Voeg de onderstaande code toe aan de `showUserInfo()` functie.

   ```swift
   var profileMap = [String: Any]()
   profileMap["loyaltyLevel"] = loyaltyLevel
   UserProfile.updateUserAttributes(attributeDict: profileMap)
   ```

Extra `updateUserAttributes` documentatie is te vinden [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattribute).

## Get

Zodra u het attribuut van een gebruiker hebt bijgewerkt, zal het aan andere Adobe SDKs beschikbaar zijn maar u kunt attributen ook uitdrukkelijk terugwinnen.

```swift
UserProfile.getUserAttributes(attributeNames: ["isPaidUser","loyaltyLevel"]){
    attributes, error in
    print("Profile: getUserAttributes: ",attributes as Any)
}
```

Extra `getUserAttributes` documentatie is te vinden [hier](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md) sectie.
1. Installeer de toepassing.
1. Start de app met de gegenereerde URL voor Betrouwbaarheid.
1. Selecteer het accountpictogram en selecteer Aanmelden. Opmerking: u hebt geen geloofsbrieven verstrekt.
1. Sluit de aanmeldingsmenu&#39;s en selecteer vervolgens opnieuw het accountpictogram. Dit brengt u aan het scherm van rekeningsdetails waar `loyaltyLevel` is ingesteld.
1. U dient een **[!UICONTROL UserProfileUpdate]** gebeurtenis in de betrouwbaarheidsinterface met de bijgewerkte `profileMap` waarde.
   ![profiel valideren](assets/mobile-profile-validate.png)

Volgende: **[Gegevens toewijzen aan Adobe Analytics](analytics.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
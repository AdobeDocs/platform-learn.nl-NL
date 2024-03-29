---
title: Webweergaven afhandelen met Platform Mobile SDK
description: Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# WebViews verwerken

Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.

## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Begrijp waarom u speciale aandacht voor WebViews in uw app moet houden.
* Begrijp de code die wordt vereist om volgende kwesties te verhinderen.

## Mogelijke problemen met bijhouden

Als u gegevens verzendt vanuit het native gedeelte van de app en vanuit een WebView in de app, genereert elk zijn eigen Experience Cloud-id (ECID), wat leidt tot verbroken resultaten en opgeblazen bezoek-/bezoekersgegevens. Meer informatie over de ECID vindt u in de [ECID-overzicht](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=en).

Om die ongewenste situatie op te lossen, is het belangrijk om de ECID van de gebruiker van het inheemse gedeelte van uw app tot een WebView over te gaan u in uw app zou kunnen willen gebruiken.

De uitbreiding van de Identiteit van de Rand AEP binnen WebView wordt gebruikt verzamelt huidige ECID en voegt het aan URL toe in plaats van het verzenden van een verzoek naar Adobe voor een nieuwe identiteitskaart die. De implementatie gebruikt deze ECID vervolgens om de URL aan te vragen.

## Implementatie

Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]** en zoek de `func loadUrl()` in de `final class SwiftUIWebViewModel: ObservableObject` klasse. Voeg de volgende vraag toe om de Webmening te behandelen:

```swift
// Handle web view
AEPEdgeIdentity.Identity.getUrlVariables {(urlVariables, error) in
    if let error = error {
        print("Error with Webview", error)
        return;
    }
    
    if let urlVariables: String = urlVariables {
        urlString.append("?" + urlVariables)
        guard let url = URL(string: urlString) else {
            return
        }
        DispatchQueue.main.async {
            self.webView.load(URLRequest(url: url))
        }
    }
    Logger.aepMobileSDK.info("Successfully retrieved urlVariables for WebView, final URL: \(urlString)")
}
```

De [`AEPEdgeIdentity.Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API stelt de variabelen voor URL in zodat deze alle relevante informatie bevatten, zoals ECID, en meer. In het voorbeeld gebruikt u een lokaal bestand, maar op externe pagina&#39;s zijn dezelfde concepten van toepassing.

Meer informatie over de `Identity.getUrlVariables` API in de [Identiteit voor Edge Network Extension API-naslaggids](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables).

## Valideren

De code uitvoeren:

1. Controleer de [installatie-instructies](assurance.md#connecting-to-a-session) om de simulator of het apparaat aan te sluiten op Betrouwbaarheid.
1. Ga naar de **[!UICONTROL Instellingen]** in de app
1. Tik op de knop **[!DNL View...]** om de **[!DNL Terms of Use]**.

   <img src="./assets/tou1.png" width="300" /> <img src="./assets/tou2.png" width="300" />

1. In Verzekering UI, zoek naar **[!UICONTROL URL-variabelen van Edge Identity Response]** gebeurtenis van de **[!UICONTROL com.adobe.griffon.mobile]** leverancier.
1. Selecteer de gebeurtenis en bekijk de **[!UICONTROL urlvariable]** in het veld **[!UICONTROL ACPExtensionEventData]** -object, waarbij de volgende parameters worden bevestigd, aanwezig zijn in de URL: `adobe_mc`, `mcmid`, en `mcorgid`.

   ![webweergave valideren](assets/webview-validation.png)

   Een monster `urvariables` het veld is hieronder te vinden :

   * Origineel (met escape-tekens)

     ```html
     adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg
     ```

   * Mooi

     ```html
     adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
     ```

Jammer genoeg, is het zuiveren van de Webzitting beperkt. U kunt bijvoorbeeld het Adobe Experience Platform Debugger in uw browser niet gebruiken om de webweergavesessie te blijven opsporen.

>[!NOTE]
>
>Bezoekerstitching via deze URL-parameters wordt ondersteund in de Platform Web SDK (versies 2.11.0 of hoger) en bij gebruik van `VisitorAPI.js`.


>[!SUCCESS]
>
>U hebt uw app nu ingesteld om inhoud weer te geven op basis van een URL in een webweergave met dezelfde ECID als de ECID die al is uitgegeven door de Adobe Experience Platform Mobile SDK.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Identiteit](identity.md)**

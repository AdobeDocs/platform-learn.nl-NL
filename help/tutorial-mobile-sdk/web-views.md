---
title: Webweergaven afhandelen met Platform Mobile SDK
description: Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '462'
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

Als u gegevens verzendt vanuit het native gedeelte van de app en vanuit een WebView in de app, genereert elk zijn eigen Experience Cloud-id (ECID), wat leidt tot verbroken resultaten en opgeblazen bezoek-/bezoekersgegevens. Meer informatie over ECID kan in het [ overzicht ECID ](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=nl-NL) worden gevonden.

Om die ongewenste situatie op te lossen, is het belangrijk om de ECID van de gebruiker van het inheemse gedeelte van uw app tot een WebView over te gaan u in uw app zou kunnen willen gebruiken.

De AEP Edge Identity-extensie die in de WebView wordt gebruikt, verzamelt de huidige ECID en voegt deze toe aan de URL in plaats van een aanvraag naar de Adobe voor een nieuwe id te verzenden. De implementatie gebruikt deze ECID vervolgens om de URL aan te vragen.

## Implementatie

Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]** en zoek de functie `func loadUrl()` in de klasse `final class SwiftUIWebViewModel: ObservableObject` . Voeg de volgende vraag toe om de Webmening te behandelen:

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

De [`AEPEdgeIdentity.Identity.getUrlVariables` ](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API plaatst - omhoog de variabelen voor URL om alle relevante informatie, zoals ECID, en meer te bevatten. In het voorbeeld gebruikt u een lokaal bestand, maar op externe pagina&#39;s zijn dezelfde concepten van toepassing.

U kunt meer over `Identity.getUrlVariables` API in de [ Identiteit voor de verwijzingsgids van de uitbreiding van de Edge Network API ](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) leren.

## Valideren

De code uitvoeren:

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat aan Verzekering te verbinden.
1. Ga naar de **[!UICONTROL Settings]** in de app
1. Tik op de knop **[!DNL View...]** om de **[!DNL Terms of Use]** weer te geven.

   <img src="./assets/tou1.png" width="300" /> <img src="./assets/tou2.png" width="300" />

1. Zoek in de gebruikersinterface voor verzekeringen naar de gebeurtenis **[!UICONTROL Edge Identity Response URL Variables]** van de **[!UICONTROL com.adobe.griffon.mobile]** -leverancier.
1. Selecteer de gebeurtenis en bekijk het veld **[!UICONTROL urlvariable]** in het **[!UICONTROL ACPExtensionEventData]** -object, waarbij de volgende parameters worden bevestigd: `adobe_mc` , `mcmid` en `mcorgid` .

   ![ webview bevestiging ](assets/webview-validation.png)

   Hieronder ziet u een voorbeeldveld `urvariables` :

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
>Bezoekersstitching via deze URL-parameters wordt ondersteund in de Platform Web SDK (versies 2.11.0 of hoger) en bij gebruik van `VisitorAPI.js` .


>[!SUCCESS]
>
>U hebt uw app nu ingesteld om inhoud weer te geven op basis van een URL in een webweergave met dezelfde ECID als de ECID die al is uitgegeven door de Adobe Experience Platform Mobile SDK.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van de Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[Identiteit](identity.md)**

---
title: WebViews afhandelen met Platform Mobile SDK
description: Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: 49d8c53d2ba2f9dcecf2470d855ad22f44763f6f
workflow-type: tm+mt
source-wordcount: '554'
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

Afzonderlijke (Experience Cloud Identity) ECID&#39;s worden gegenereerd wanneer u gegevens verzendt vanuit het native gedeelte van uw app en vanuit een WebView in de app. Deze afzonderlijke ECID&#39;s leiden tot ongekoppelde treffers en tot opgeblazen bezoek- en bezoekersgegevens. Meer informatie over ECID kan in het [&#x200B; overzicht ECID &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/features/ecid) worden gevonden.

Als u de verbroken resultaten en opgepompte gegevens wilt oplossen, moet u de ECID van de gebruiker doorgeven van het native gedeelte van uw app naar een WebView die u wellicht wilt gebruiken in uw app.

De AEP Edge Identity-extensie die in de WebView wordt gebruikt, verzamelt de huidige ECID en voegt deze toe aan de URL in plaats van een aanvraag voor een nieuwe id naar Adobe te verzenden. De implementatie gebruikt deze ECID vervolgens om de URL aan te vragen.

## Implementatie

De webweergave implementeren:

>[!BEGINTABS]

>[!TAB  iOS ]

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

De [`AEPEdgeIdentity.Identity.getUrlVariables` &#x200B;](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API plaatst - omhoog de variabelen voor URL om alle relevante informatie, zoals ECID, en meer te bevatten. In het voorbeeld gebruikt u een lokaal bestand, maar op externe pagina&#39;s zijn dezelfde concepten van toepassing.

U kunt meer over `Identity.getUrlVariables` API in de [&#x200B; Identiteit voor de verwijzingsgids van de uitbreiding van Edge Network API &#x200B;](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) leren.


>[!TAB  Android ]

Navigeer aan **[!UICONTROL Android]** ![&#x200B; ChevronDown &#x200B;](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!DNL views]** > **[!DNL WebViewModel]**, en bepaal de plaats van de `fun loadUrl()` functie in `class WebViewModel: ViewModel()`. Voeg de volgende vraag toe om de Webmening te behandelen:

```kotlin
// Handle web view
Identity.getUrlVariables {
    urlVariables = it
    val baseUrl = getHtmlFileUrl("tou.html")

    val finalUrl = if (urlVariables.isNotEmpty()) {
        "$baseUrl?$urlVariables"
    } else {
        baseUrl
    }

    Handler(Looper.getMainLooper()).post {
        webView.loadUrl(finalUrl)
    }
    MobileSDK.shared.logInfo("TermsOfServiceSheet - loadUrl: Successfully loaded WebView with URL: $finalUrl")
}
```

De [`Identity.getUrlVariables` &#x200B;](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API plaatst - omhoog de variabelen voor URL om alle relevante informatie, zoals ECID, en meer te bevatten. In het voorbeeld gebruikt u een lokaal bestand, maar op externe pagina&#39;s zijn dezelfde concepten van toepassing.

U kunt meer over `Identity.getUrlVariables` API in de [&#x200B; Identiteit voor de verwijzingsgids van de uitbreiding van Edge Network API &#x200B;](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) leren.

>[!ENDTABS]

## Valideren in de app

De code uitvoeren:

1. Herzie de [&#x200B; sectie van opstellingsinstructies &#x200B;](assurance.md#connecting-to-a-session) om uw simulator of apparaat met Assurance te verbinden.
1. Ga naar de **[!UICONTROL Settings]** in de app
1. Tik op de knop **[!DNL View...]** om de **[!DNL Terms of Use]** weer te geven.

>[!BEGINTABS]

>[!TAB  iOS ]

<img src="./assets/tou1.png" width="300"> <img src="./assets/tou2.png" width="300">

>[!TAB  Android ]

<img src="./assets/tou1-android.png" width="300"> <img src="./assets/tou2-android.png" width="300">

>[!ENDTABS]


## Valideren met Assurance

1. Zoek in de gebruikersinterface van Assurance naar de gebeurtenis **[!UICONTROL Edge Identity Response URL Variables]** van de **[!UICONTROL com.adobe.griffon.mobile]** -leverancier.
1. Selecteer de gebeurtenis en bekijk het veld **[!UICONTROL urlvariable]** in het **[!UICONTROL ACPExtensionEventData]** -object, waarbij de volgende parameters worden bevestigd: `adobe_mc` , `mcmid` en `mcorgid` .

   ![&#x200B; webview bevestiging &#x200B;](assets/webview-validation.png){zoomable="yes"}

   Hieronder ziet u een voorbeeldveld `urvariables` :

   * Origineel (met escape-tekens)

     ```html
     adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg
     ```

   * Mooi

     ```html
     adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
     ```

Jammer genoeg, is het zuiveren van de Webzitting beperkt. U kunt bijvoorbeeld de Adobe Experience Platform Debugger in uw browser niet gebruiken om de foutopsporing voor de webweergavesessie voort te zetten.

>[!NOTE]
>
>Bezoekersstitching via deze URL-parameters wordt ondersteund in Platform Web SDK (versies 2.11.0 of hoger) en bij gebruik van `VisitorAPI.js` .


>[!SUCCESS]
>
>U hebt uw app nu ingesteld om inhoud weer te geven op basis van een URL in een webweergave met dezelfde ECID als de ECID die al is uitgegeven door de Adobe Experience Platform Mobile SDK.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [&#x200B; Communautaire besprekingspost van Experience League &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[Identiteit](identity.md)**

---
title: WebViews verwerken
description: Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.
kt: 6987
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# WebViews verwerken

Leer hoe u gegevensverzameling kunt verwerken met WebViews in een mobiele app.

## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Begrijp waarom u speciale overwegingen voor WebViews moet nemen.
* Begrijp de code die wordt vereist om volgende kwesties te verhinderen.

## Mogelijke problemen met bijhouden

Als u gegevens verzendt van het native gedeelte van de app en een WebView, genereert elk hun eigen Experience Cloud-id (ECID). Dit leidt tot ongekoppelde treffers en opgeblazen bezoek-/bezoekersgegevens. Meer informatie over de ECID vindt u in de [ECID-overzicht](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=en).

Om voor die ongewenste situatie op te lossen, is het belangrijk om ECID van de gebruiker van het inheemse gedeelte tot WebView over te gaan.

De Experience Cloud ID Service JavaScript-extensie in de WebView extraheert de ECID uit de URL in plaats van een aanvraag naar Adobe voor een nieuwe id te verzenden. De id-service gebruikt deze ECID om de bezoeker bij te houden.

## Implementatie

Zoek in de voorbeeldtoepassing Luma naar de `TermsOfService.swift` bestand (in het `Intro-Login_SignUp` en zoek de volgende code:

```swift
// Show tou.html
let url = Bundle.main.url(forResource: "tou", withExtension: "html")
let myRequest = URLRequest(url: url!)
self.webView.load(myRequest)
```

Dit is een eenvoudige manier om een WebView te laden. In dit geval is het een lokaal bestand, maar zijn dezelfde concepten van toepassing op externe pagina&#39;s.

Verwijs de webweergavecode als volgt:

```swift
let url = Bundle.main.url(forResource: "tou", withExtension: "html")
if var urlString = url?.absoluteString {
    // Adobe Experience Platform - Handle Web View
    AEPEdgeIdentity.Identity.getUrlVariables {(urlVariables, error) in
        if let error = error {
            self.simpleAlert("\(error.localizedDescription)")
            return;
        }

        if let urlVariables: String = urlVariables {
            urlString.append("?" + urlVariables)
        }

        DispatchQueue.main.async {
            self.webView.load(URLRequest(url: URL(string: urlString)!))
        }
        print("Successfully retrieved urlVariables for WebView, final URL: \(urlString)")
    }
} else {
    self.simpleAlert("Failed to create URL for webView")
}
```

Meer informatie over de `Identity.getUrlVariables` API in de [Identiteit voor Edge Network Extension API-naslaggids](https://aep-sdks.gitbook.io/docs/foundation-extensions/identity-for-edge-network/api-reference#geturlvariables).

## Validatie

Nadat u de [installatie-instructies](assurance.md) en het aansluiten van uw simulator of apparaat aan Verzekering, laadt WebView en zoekt naar `Edge Identity Response URL Variables` gebeurtenis van de `com.adobe.griffon.mobile` leverancier.

Als u de WebView wilt laden, gaat u naar het beginscherm van de Luma-app en selecteert u het pictogram &quot;Account&quot;, gevolgd door &quot;Gebruiksvoorwaarden&quot; in de voettekst.

Na het laden van de WebView, selecteer de gebeurtenis en herzie `urlvariables` in het `ACPExtensionEventData` -object, waarbij de volgende parameters worden bevestigd, aanwezig zijn in de URL: `adobe_mc`, `mcmid`, en `mcorgid`.

![webweergave valideren](assets/mobile-webview-validation.png)

Een monster `urvariables` het veld is hieronder te vinden :

```html
// Original (with escaped characters)
adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg

// Beautified
adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
```

>[!NOTE]
>
>Bezoekersstitching via deze URL-parameters wordt momenteel ondersteund in de Web SDK van het Platform (versies 2.11.0 of hoger) en `VisitorAPI.js`.


Volgende: **[Identiteit](identity.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
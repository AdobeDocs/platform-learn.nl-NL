---
title: Analysetoewijzing
description: Leer hoe u gegevens voor Adobe Analytics kunt verzamelen in een mobiele app.
solution: Data Collection,Experience Platform,Analytics
hide: true
source-git-commit: ae1e05b3f93efd5f2a9b48dc10761dbe7a84fb1e
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# Analysetoewijzing

Leer hoe u mobiele gegevens kunt toewijzen aan Adobe Analytics.

De [event](events.md) gegevens die u in eerdere lessen hebt verzameld en naar Platform Edge Network hebt verzonden, worden doorgestuurd naar de services die in uw gegevensstroom zijn geconfigureerd, waaronder Adobe Analytics. U brengt de gegevens aan de correcte variabelen in uw rapportreeks in kaart.

![Architectuur](assets/architecture-aa.png)

## Vereisten

* Inzicht in het bijhouden van ExperienceEvent.
* XDM-gegevens worden naar uw voorbeeld-app verzonden.
* DataStream geconfigureerd voor Adobe Analytics

## Leerdoelstellingen

In deze les zult u:

* Begrijp automatisch in kaart brengen van de variabelen van de Analyse.
* Stel verwerkingsregels in om XDM-gegevens toe te wijzen aan analytische variabelen.

## Automatische toewijzing

Veel standaard XDM-velden worden automatisch toegewezen aan analytische variabelen. Zie de volledige lijst [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html?lang=en).

### Voorbeeld 1 - s.products

Een goed voorbeeld is de [productvariabele](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=en) die niet kunnen worden gevuld met verwerkingsregels. Met een implementatie XDM, gaat u alle noodzakelijke gegevens binnen over `productListItems` en `s.products` worden automatisch ingevuld via Analytics-toewijzing.

Dit object:

```swift
"productListItems": [
    [
      "name":  "Yoga Mat",
      "SKU": "5829",
      "priceTotal": "49.99",
      "quantity": 1
    ],
    [
      "name":  "Water Bottle",
      "SKU": "9841",
      "priceTotal": "30.00",
      "quantity": 3
    ]
]
```

resulteert in:

```
s.products = ";Yoga Mat;1;49.99,;Water Bottle,3,30.00"
```

>[!NOTE]
>
>Momenteel `productListItems[N].SKU` wordt genegeerd door automatische toewijzing.


### Voorbeeld 2 - scAdd

Als u goed kijkt, hebben alle gebeurtenissen twee velden `value` (vereist) en `id` (optioneel). De `value` wordt gebruikt om het aantal gebeurtenissen te verhogen. De `id` het gebied wordt gebruikt voor rangschikking.

Dit object:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1
  }
}
```

resulteert in:

```
s.events = "scAdd"
```

Dit object:

```swift
"commerce" : {
  "productListAdds" : {
    "value" : 1,
    "id": "321435"
  }
}
```

resulteert in:

```
s.events = "scAdd:321435"
```

## Valideren met betrouwbaarheid

Met de [Betrouwbaarheid](assurance.md) u kunt bevestigen dat u een ervaringsgebeurtenis verzendt, zijn de gegevens XDM correct en de afbeelding van Analytics gebeurt zoals verwacht. Bijvoorbeeld:

1. Verzend een productListAdds-gebeurtenis.

1. Bekijk de ExperienceEvent hit.

   ![analyse xdm hit](assets/analytics-assurance-experiencevent.png)

1. Controleer het XDM-gedeelte van de JSON.

   ```json
   "xdm" : {
     "productListItems" : [ {
       "SKU" : "LLWS05.1-XS",
       "name" : "Desiree Fitness Tee",
       "priceTotal" : 24
     } ],
   "timestamp" : "2023-08-04T12:53:37.662Z",
   "eventType" : "commerce.productListAdds",
   "commerce" : {
     "productListAdds" : {
       "id" : "LLWS05.1-XS",
       "value" : 1
     }
   }
   // ...
   ```

1. Controleer de **[!UICONTROL analytics.mapping]** gebeurtenis.

   ![analyse xdm hit](assets/analytics-assurance-mapping.png)

Neem nota van het volgende in de afbeelding van Analytics:

* **[!UICONTROL gebeurtenissen]** zijn gevuld met `scAdd` gebaseerd op `commerce.productListAdds`.
* **[!UICONTROL pl]** (productvariabele) wordt gevuld met een samengevoegde waarde gebaseerd op `productListItems`.
* Er is andere interessante informatie in deze gebeurtenis, waaronder alle contextgegevens.


## Toewijzing met contextgegevens

XDM-gegevens die naar Analytics worden doorgestuurd, worden omgezet in [contextgegevens](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=en) inclusief zowel standaard- als aangepaste velden.

De sleutel van contextgegevens wordt samengesteld volgens deze syntaxis:

```
a.x.[xdm path]
```

Bijvoorbeeld:

```
// Standard Field
a.x.commerce.saveforlaters.value

// Custom Field
a.x._techmarketingdemos.appinformationa.appstatedetails.screenname
```

>[!NOTE]
>
>Aangepaste velden worden onder de Org-id van het Experience Cloud geplaatst.
>
>`_techmarketingdemos` wordt vervangen door de unieke waarde van uw organisatie.


Zo ziet een verwerkingsregel met deze gegevens eruit:

* U **[!UICONTROL Waarde overschrijven van]** (1) **[!UICONTROL Schermnaam van app (eVar2)]** (2) met de waarde van **[!UICONTROL a.x_techmarketingdemo.appinformation.appstatedetails.screenname]** (3) **[!UICONTROL a.x_techmarketingdemo.appinformation.appstatedetails.screenname]** (4) **[!UICONTROL is ingesteld]** (5)

* U **[!UICONTROL Gebeurtenis instellen]** (6) **[!UICONTROL Toevoegen aan Wishlist (gebeurtenis 3)]** (7) tot **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8) **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL is ingesteld]** 10.

![regels voor analytische verwerking](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Sommige automatisch toegewezen variabelen zijn mogelijk niet beschikbaar voor gebruik in verwerkingsregels.
>
>
>De eerste keer u aan een verwerkingsregel in kaart brengt, toont de interface u niet de variabelen van contextgegevens van het voorwerp XDM. Als u een waarde wilt selecteren, slaat u Opslaan en keert u terug om te bewerken. Alle XDM-variabelen moeten nu worden weergegeven.


Aanvullende informatie over verwerkingsregels en contextgegevens is te vinden [hier](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>In tegenstelling tot de vorige implementaties van mobiele apps, is er geen onderscheid tussen een pagina/het scherm meningen en andere gebeurtenissen. In plaats daarvan kunt u de **[!UICONTROL Paginaweergave]** metrisch door te plaatsen **[!UICONTROL Paginanaam]** dimensie in een verwerkingsregel. Aangezien u de aangepaste `screenName` in de zelfstudie wordt het ten zeerste aanbevolen de schermnaam toe te wijzen aan **[!UICONTROL Paginanaam]** in een verwerkingsregel.

>[!SUCCESS]
>
>U hebt uw app zo ingesteld dat uw Experience Edge XDM-objecten worden toegewezen aan Adobe Analytics-variabelen, waardoor de Adobe Analytics-service in uw gegevensstroom kan worden gebruikt en waar van toepassing verwerkingsregels kunnen worden gebruikt.<br/> Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Experience Platform](platform.md)**

---
title: Analysetoewijzing
description: Leer hoe u gegevens voor Adobe Analytics kunt verzamelen in een mobiele app.
solution: Data Collection,Experience Platform,Analytics
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: adbe8f4476340abddebbf9231e3dde44ba328063
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# Analysetoewijzing

Leer hoe u mobiele gegevens kunt toewijzen aan Adobe Analytics.

De [event](events.md) de gegevens die u verzamelde en naar het Netwerk van de Rand van het Platform in vroegere lessen verzendt worden door:sturen aan de diensten die in uw gegevensstroom, met inbegrip van Adobe Analytics worden gevormd. U moet enkel de gegevens aan de correcte variabelen in uw rapportreeks in kaart brengen.

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

Een goed voorbeeld is de [productvariabele](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/products.html?lang=en) die niet kunnen worden gevuld met verwerkingsregels. Met een implementatie XDM, gaat u alle noodzakelijke gegevens in productListItems en s.products automatisch door via afbeelding Analytics.

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

Dit resulteert in het volgende:

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

Dit resulteert in het volgende:

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

Dit resulteert in het volgende:

```
s.events = "scAdd:321435"
```

## Valideren met betrouwbaarheid

Met de [Gereedschap KA controleren](assurance.md) U kunt bevestigen dat u een ExperienceEvent verzendt, zijn de XDM gegevens correct en de afbeelding van Analytics gebeurt zoals verwacht. Bijvoorbeeld:

1. Verzend een productListAdds-gebeurtenis.

   ```swift
   var xdmData: [String: Any] = [
     "eventType": "commerce.productListAdds",
     "commerce": [
       "productListAdds": [
         "value": 1
       ]
     ],
     "productListItems": [
       [
         "name": "neve studio dance jacket - (blue)",
         "SKU": "test-sku",
         "priceTotal": 69
       ]
     ]
   ]
   let addToCartEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: addToCartEvent)
   ```

1. Bekijk de ExperienceEvent hit.

   ![analyse xdm hit](assets/mobile-analytics-assurance-xdm.png)

1. Controleer het XDM-gedeelte van de JSON.

   ```json
     "xdm" : {
       "productListItems" : [ {
         "priceTotal" : 69,
         "SKU" : "test-sku",
         "name" : "neve studio dance jacket - (blue)"
       } ],
       "timestamp" : "2021-10-22T22:03:37Z",
       "commerce" : {
         "productListAdds" : {
           "value" : 1
         }
       },
       "eventType" : "commerce.productListAdds",
       //...
     }
   ```

1. Controleer de `analytics.mapping` gebeurtenis.

   ![analyse xdm hit](assets/mobile-analytics-assurance-mapping.png)

Neem nota van het volgende in de afbeelding van Analytics:

* &#39;events&#39; is gevuld met &#39;scAdd&#39; op `commerce.productListAdds`.
* &#39;pl&#39; (productvariabele) werd gevuld met een samengevoegde waarde gebaseerd op `productListItems`.
* Er is andere interessante informatie in deze gebeurtenis, waaronder alle contextgegevens.


## Toewijzing met contextgegevens

XDM-gegevens die naar Analytics worden doorgestuurd, worden omgezet in [contextgegevens](https://experienceleague.adobe.com/docs/mobile-services/ios/getting-started-ios/proc-rules.html?lang=en) inclusief zowel standaard- als aangepaste velden.

De sleutel van contextgegevens wordt samengesteld volgens deze syntaxis:

```
a.x.[xdm path]
```

Bijvoorbeeld:

```
//Standard Field
a.x.commerce.saveforlaters.value

//Custom Field
a.x._techmarketingdemos.appinformationa.appstatedetails.screenname
```

>[!NOTE]
>
>Aangepaste velden worden onder de Experience Cloud Org-id geplaatst.
>
>&quot;_techmarketingdemos&quot; wordt vervangen door de unieke waarde van uw organisatie.

Zo ziet een verwerkingsregel met deze gegevens eruit:

![regels voor analytische verwerking](assets/mobile-analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Sommige automatisch toegewezen variabelen zijn mogelijk niet beschikbaar voor gebruik in verwerkingsregels.
>
>
>De eerste keer u aan een verwerkingsregel in kaart brengt UI toont u niet de variabelen van contextgegevens van het voorwerp XDM. Als u een waarde wilt selecteren, slaat u Opslaan en keert u terug om te bewerken. Alle XDM-variabelen moeten nu worden weergegeven.


Extra informatie over verwerkingsregels en contextgegevens is te vinden [hier](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>In tegenstelling tot de vorige implementaties van mobiele apps is er geen onderscheid tussen een pagina/scherm-weergave en andere gebeurtenissen. In plaats daarvan kunt u de **[!UICONTROL Paginaweergave]** metrisch door te plaatsen **[!UICONTROL Paginanaam]** dimensie in een verwerkingsregel. Aangezien u de aangepaste `screenName` in de zelfstudie wordt het ten zeerste aanbevolen dit toe te wijzen aan **[!UICONTROL Paginanaam]** in een verwerkingsregel.


Volgende: **[Experience Platform](platform.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
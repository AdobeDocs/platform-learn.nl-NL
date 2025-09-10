---
title: Gegevens die zijn verzameld met Platform Mobile SDK toewijzen aan Adobe Analytics
description: Leer hoe u gegevens voor Adobe Analytics kunt verzamelen en toewijzen in een mobiele app.
solution: Data Collection,Experience Platform,Analytics
jira: KT-14636
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Analysegegevens verzamelen en toewijzen

Leer hoe u mobiele gegevens kunt toewijzen aan Adobe Analytics.

De [ gebeurtenis ](events.md) gegevens die u verzamelde en naar Platform Edge Network in vroegere lessen verzendt door:sturen aan de diensten die in uw datastream, met inbegrip van Adobe Analytics worden gevormd. U brengt de gegevens aan de correcte variabelen in uw rapportreeks in kaart.

![Architectuur](assets/architecture-aa.png){zoomable="yes"}

## Vereisten

* Inzicht in het bijhouden van ExperienceEvent.
* XDM-gegevens worden naar uw voorbeeld-app verzonden.
* Een Adobe Analytics-rapportsuite die u kunt gebruiken voor deze les.

## Leerdoelstellingen

In deze les zult u:

* Configureer uw gegevensstroom met de Adobe Analytics-service.
* Begrijp automatisch in kaart brengen van de variabelen van de Analyse.
* Stel verwerkingsregels in om XDM-gegevens toe te wijzen aan analytische variabelen.

## Adobe Analytics-datastreamservice toevoegen

Om uw gegevens XDM van Edge Network naar Adobe Analytics te verzenden, vormt u de dienst van Adobe Analytics aan de datastream u opstelling als deel van [ creeert een datastream ](create-datastream.md).

1. Selecteer **[!UICONTROL Datastreams]** en uw gegevensstroom in de gebruikersinterface voor gegevensverzameling.

1. Dan selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]**.

1. Voeg **[!UICONTROL Adobe Analytics]** toe uit de lijst [!UICONTROL Service] ,

1. Voer de naam in van de rapportsuite van Adobe Analytics die u in **[!UICONTROL Report Suite ID]** wilt gebruiken.

1. Schakel **[!UICONTROL Enabled]** in om de service in te schakelen.

1. Selecteer **[!UICONTROL Save]**.

   ![ voegt Adobe Analytics als datastreamdienst ](assets/datastream-service-aa.png){zoomable="yes"} toe


## Automatische toewijzing

Veel standaard XDM-velden worden automatisch toegewezen aan analytische variabelen. Zie de [ volledige lijst ](https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/xdm-var-mapping).

### Voorbeeld 1 - s.products

Een goed voorbeeld is de [ productvariabele ](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/products) die niet kan worden bevolkt gebruikend verwerkingsregels. Met een XDM-implementatie geeft u alle benodigde gegevens door in `productListItems` en `s.products` wordt automatisch ingevuld via Analytics-toewijzing.

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
s.products = ";5829;1;49.99,9841;3;30.00"
```

>[!NOTE]
>
>Als `productListItems[].SKU` en `productListItems[].name` beide gegevens bevatten, wordt de waarde in `productListItems[].SKU` gebruikt. Zie [ veranderlijke afbeelding van Analytics in de Ervaring Edge van Adobe ](https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/xdm-var-mapping) voor meer informatie.


### Voorbeeld 2 - scAdd

Als u goed kijkt, hebben alle gebeurtenissen twee velden: `value` (vereist) en `id` (optioneel). Het veld `value` wordt gebruikt om het aantal gebeurtenissen te verhogen. Het veld `id` wordt gebruikt voor serienummering.

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

## Valideren met Assurance

Gebruikend [ Assurance ](assurance.md) kunt u bevestigen dat u een ervaringsgebeurtenis verzendt, is het XDM- gegeven correct en de afbeelding van Analytics gebeurt zoals verwacht.

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat met Assurance te verbinden.

1. Verzend een **[!UICONTROL productListAdds]** -gebeurtenis (voeg een product toe aan uw mandje).

1. Bekijk de ExperienceEvent hit.

   ![ Analytics xdm hit ](assets/analytics-assurance-experiencevent.png){zoomable="yes"}

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
       "value" : 1
     }
   }
   // ...
   ```

1. Controleer de **[!UICONTROL analytics.mapping]** -gebeurtenis.

   ![ Analytics xdm hit ](assets/analytics-assurance-mapping.png){zoomable="yes"}

Neem nota van het volgende in de afbeelding van Analytics:

* **[!UICONTROL events]** wordt gevuld met `scAdd` gebaseerd op `commerce.productListAdds` .
* **[!UICONTROL pl]** (productvariabele) wordt gevuld met een samengevoegde waarde op basis van `productListItems` .
* Er is andere interessante informatie in deze gebeurtenis, waaronder alle contextgegevens.


## Toewijzing met contextgegevens

De gegevens XDM die aan Analytics door:sturen worden omgezet in [ contextgegevens ](https://github.com/Adobe-Marketing-Cloud/mobile-services/blob/master/docs/ios/getting-started/proc-rules.md?lang=en) met inbegrip van zowel standaard als douanegebieden.

De sleutel van contextgegevens wordt samengesteld volgens deze syntaxis:

```
a.x.[xdm path]
```

Bijvoorbeeld:

```
// Standard Field
a.x.commerce.saveforlaters.value

// Custom Field
a.x._techmarketingdemos.appinformation.appstatedetails.screenname
```

>[!NOTE]
>
>Aangepaste velden worden onder de Experience Cloud Org-id geplaatst.
>
De huurdersnaam `_techmarketingdemos` wordt vervangen door de unieke waarde van uw organisatie.



Om deze XDM contextgegevens aan uw gegevens van Analytics in uw rapportreeks in kaart te brengen, kunt u:

### Een veldgroep gebruiken

* Voeg de **[!UICONTROL Adobe Analytics ExperienceEvent Full Extension]** veldgroep toe aan uw schema.

  ![ het gebiedsgroep van ExperienceEvent FullExtension ](assets/schema-analytics-extension.png){zoomable="yes"}

* Bouw XDM nuttige lasten in uw app, die aan de het gebiedsgroep van de Uitbreiding van Adobe Analytics ExperienceEvent Volledige in overeenstemming zijn, gelijkend op wat u in de [ les van de Gegevens van de Gebeurtenis van het 0} Spoor {hebt gedaan, of](events.md)
* Bouw regels in uw bezit van Markeringen die regelacties gebruiken om gegevens aan de het gebiedsgroep van de Uitbreiding van Adobe Analytics ExperienceEvent Volledige toe te voegen of te wijzigen. Zie voor meer details [ gegevens vastmaken aan de gebeurtenissen van SDK ](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/) of [ gegevens in de gebeurtenissen van SDK wijzigen ](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/).


### Merchandising Vars

Als u [ merchandising eVars ](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/merchandising-evars) in uw opstelling van Analytics gebruikt, moet u uw nuttige lading uitbreiden XDM die u in [ de gebeurtenisgegevens van het Spoor ](events.md) bepaalde om die het verhandelen informatie te vangen. Voorbeeld van een handelswaar var is `evar1` waar u de kleur van producten wilt vastleggen, bijvoorbeeld `&&products = ...;evar1=red;event10=50,...;evar1=blue;event10=60`

* In JSON:

  ```json
  {
    "productListItems": [
        {
            "SKU": "LLWS05.1-XS",
            "name": "Desiree Fitness Tee",
            "priceTotal": 24,
            "_experience": {
                "analytics": {
                    "events1to100": {
                        "event10": {
                            "value": 50
                        }
                    },
                    "customDimensions": {
                        "eVars": {
                            "eVar1": "red",
                        }
                    }
                }
            }
        }
    ],
    "eventType": "commerce.productListAdds",
    "commerce": {
        "productListAdds": {
            "value": 1
        }
    }
  }
  ```

* In code:

  ```swift
  var xdmData: [String: Any] = [
    "productListItems": [
      [
        "name":  productName,
        "SKU": sku,
        "priceTotal": priceString,
        "_experience" : [
          "analytics": [
            "events1to100": [
              "event10": [
                "value:": value
              ]
            ],
            "customDimensions": [
              "eVars": [
                "eVar1": color
              ]
            ]
          ]
        ]
      ]
    ],
    "eventType": "commerce.productViews",
    "commerce": [
      "productViews": [
        "value": 1
      ]
    ]
  ]
  ```


### Verwerkingsregels gebruiken

Zo ziet een verwerkingsregel met deze gegevens eruit:

* U **[!UICONTROL Overwrite value of]** (1) **[!UICONTROL App Screen Name (eVar2)]** (2) met de waarde **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (3) if **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (4) **[!UICONTROL is set]** (5).

* U **[!UICONTROL Set event]** (6) **[!UICONTROL Add to Wishlist (Event 3)]** (7) tot **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8) als **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL is set]** (10).

![ analytische verwerkingsregels ](assets/analytics-processing-rules.png){zoomable="yes"}

>[!IMPORTANT]
>
>
>Sommige automatisch toegewezen variabelen zijn mogelijk niet beschikbaar voor gebruik in verwerkingsregels.
>
>
>De eerste keer u aan een verwerkingsregel in kaart brengt, toont de interface u niet de variabelen van contextgegevens van het voorwerp XDM. Als u een waarde wilt selecteren, slaat u Opslaan en keert u terug om te bewerken. Alle XDM-variabelen moeten nu worden weergegeven.


Zie [ contextData variabelen van de Kaart in steunen en eVars met verwerkingsregels ](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules).

>[!TIP]
>
>In tegenstelling tot de vorige implementaties van mobiele apps, is er geen onderscheid tussen een pagina/het scherm meningen en andere gebeurtenissen. In plaats daarvan kunt u de metrische waarde van **[!UICONTROL Page View]** verhogen door de **[!UICONTROL Page Name]** -dimensie in te stellen in een verwerkingsregel. Aangezien u het aangepaste veld `screenName` in de zelfstudie verzamelt, wordt het ten zeerste aanbevolen de schermnaam toe te wijzen aan **[!UICONTROL Page Name]** in een verwerkingsregel.

## Migreren vanuit mobiele extensie Analytics

Als u uw mobiele toepassing gebruikend de [ mobiele uitbreiding van Adobe Analytics ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/#add-analytics-to-your-application) hebt ontwikkeld, hebt u hoogstwaarschijnlijk [`MobileCore.trackAction` ](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction) en [`MobileCore.trackState` ](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate) API vraag gebruikt.

Als u besluit te migreren om de aanbevolen Edge Network te gebruiken, hebt u wel de volgende opties:

* Voer de [ uitbreiding van Edge Network ](configure-tags.md#extension-configuration) uit en gebruik [`Edge.sendEvent` ](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent) APIs, zoals geïllustreerd in de les op hoe te [ de gebeurtenisgegevens van het Spoor ](events.md). Deze zelfstudie richt zich op deze implementatie.
* Voer de [ uitbreiding van Edge Bridge ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension) uit, en gebruik uw [`MobileCore.trackAction` ](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackaction) en [`MobileCore.trackState` ](https://developer.adobe.com/client-sdks/home/base/mobile-core/api-reference/#trackstate) API vraag. Zie [ de uitbreiding van Edge Bridge ](https://developer.adobe.com/client-sdks/solution/adobe-analytics/migrate-to-edge-network/#implement-the-edge-bridge-extension) voor meer details en een afzonderlijk leerprogramma uitvoeren.




>[!SUCCESS]
>
>U hebt uw app zo ingesteld dat uw Experience Edge XDM-objecten worden toegewezen aan Adobe Analytics-variabelen door de Adobe Analytics-service in uw gegevensstroom in te schakelen. en in voorkomend geval met gebruikmaking van verwerkingsvoorschriften.<br/> Bedankt dat u hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[verzendt gegevens naar Experience Platform](platform.md)**

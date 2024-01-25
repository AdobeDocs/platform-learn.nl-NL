---
title: Gegevens die zijn verzameld met Platform Mobile SDK toewijzen aan Adobe Analytics
description: Leer hoe u gegevens voor Adobe Analytics kunt verzamelen en toewijzen in een mobiele app.
solution: Data Collection,Experience Platform,Analytics
jira: KT-14636
exl-id: 406dc687-643f-4f7b-a8e7-9aad1d0d481d
source-git-commit: 30dd0142f1f5220f30c45d58665b710a06c827a8
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Analysegegevens verzamelen en toewijzen

Leer hoe u mobiele gegevens kunt toewijzen aan Adobe Analytics.

De [event](events.md) gegevens die u in eerdere lessen hebt verzameld en naar Platform Edge Network hebt verzonden, worden doorgestuurd naar de services die in uw gegevensstroom zijn geconfigureerd, waaronder Adobe Analytics. U brengt de gegevens aan de correcte variabelen in uw rapportreeks in kaart.

![Architectuur](assets/architecture-aa.png)

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

Als u uw XDM-gegevens van het Edge-netwerk naar Adobe Analytics wilt verzenden, configureert u de Adobe Analytics-service naar de gegevensstroom die u instelt als onderdeel van [Een gegevensstroom maken](create-datastream.md).

1. Selecteer in de gebruikersinterface voor gegevensverzameling de optie **[!UICONTROL Gegevensstromen]** en uw gegevensstroom.

1. Selecteer vervolgens ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Service toevoegen]**.

1. Toevoegen **[!UICONTROL Adobe Analytics]** van de [!UICONTROL Service] lijst,

1. Voer de naam in van de rapportsuite van Adobe Analytics waarin u wilt gebruiken **[!UICONTROL ID van rapportsuite]**.

1. Laat de dienst door omschakeling toe **[!UICONTROL Ingeschakeld]** op.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Adobe Analytics toevoegen als datastreamservice](assets/datastream-service-aa.png)


## Automatische toewijzing

Veel standaard XDM-velden worden automatisch toegewezen aan analytische variabelen. Zie de volledige lijst [hier](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en).

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
s.products = ";5829;1;49.99,9841;3;30.00"
```

>[!NOTE]
>
>Indien `productListItems[].SKU` en `productListItems[].name` beide bevatten gegevens, de waarde in `productListItems[].SKU` wordt gebruikt. Zie [Variabeletoewijzing analyseren in Adobe Experience Edge](https://experienceleague.adobe.com/docs/analytics/implementation/aep-edge/variable-mapping.html?lang=en) voor meer informatie .


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

Met de [Betrouwbaarheid](assurance.md) u kunt bevestigen dat u een ervaringsgebeurtenis verzendt, zijn de gegevens XDM correct en de afbeelding van Analytics gebeurt zoals verwacht.

1. Controleer de [installatie-instructies](assurance.md#connecting-to-a-session) om de simulator of het apparaat aan te sluiten op Betrouwbaarheid.

1. Een **[!UICONTROL productListAdds]** (voeg een product toe aan uw mandje).

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
a.x._techmarketingdemos.appinformation.appstatedetails.screenname
```

>[!NOTE]
>
>Aangepaste velden worden onder de Org-id van het Experience Cloud geplaatst.
>
>`_techmarketingdemos` wordt vervangen door de unieke waarde van uw organisatie.



Om deze XDM contextgegevens aan uw gegevens van Analytics in uw rapportreeks in kaart te brengen, kunt u:

### Een veldgroep gebruiken

* Voeg de **[!UICONTROL Adobe Analytics ExperienceEvent Volledige extensie]** veldgroep aan uw schema.

  ![Analytics ExperienceEvent FullExtension, veldgroep](assets/schema-analytics-extension.png)

* XDM-ladingen maken in uw app, conform de Adobe Analytics ExperienceEvent Full Extension field group, vergelijkbaar met wat u in het dialoogvenster [Gebeurtenisgegevens bijhouden](events.md) les, of
* Bouw regels in uw bezit van Markeringen die regelacties gebruiken om gegevens aan de het gebiedsgroep van de Uitbreiding van Adobe Analytics ExperienceEvent Volledige toe te voegen of te wijzigen. Zie voor meer informatie [Gegevens koppelen aan SDK-gebeurtenissen](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/) of [Gegevens wijzigen in SDK-gebeurtenissen](https://developer.adobe.com/client-sdks/documentation/user-guides/attach-data/).


### Merchandising-eVars

Als u [merchandising Vars](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/merchandising-evars.html?lang=en) in uw analyseprogramma, bijvoorbeeld om de kleur van producten vast te leggen, zoals `&&products = ...;evar1=red;event10=50,...;evar1=blue;event10=60`, moet u de XDM-lading uitbreiden die u in [Gebeurtenisgegevens bijhouden](events.md) om die informatie over de handel vast te leggen.

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
>U hebt uw app zo ingesteld dat uw Experience Edge XDM-objecten worden toegewezen aan Adobe Analytics-variabelen, waardoor de Adobe Analytics-service in uw gegevensstroom kan worden gebruikt en waar van toepassing verwerkingsregels kunnen worden gebruikt.<br/> Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com:443/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Gegevens naar Experience Platform verzenden](platform.md)**

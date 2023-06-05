---
title: Gebeurtenissen
description: Leer hoe u gebeurtenisgegevens kunt verzamelen in een mobiele app.
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
source-git-commit: b2e1bf08d9fb145ba63263dfa078c96258342708
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# Gebeurtenissen

Leer hoe u gebeurtenissen in een mobiele app kunt bijhouden.

De uitbreiding van het Netwerk van Edge verstrekt API om de Gebeurtenissen van de Ervaring naar het Netwerk van de Rand van het Platform te verzenden. Een Experience Event is een object dat gegevens bevat die voldoen aan de XDM ExperienceEvent-schemadefinitie. Meer eenvoudig, vangen zij wat mensen in uw mobiele app doen. Zodra het gegeven door het Netwerk van de Rand van het Platform wordt ontvangen, kan het aan toepassingen en de diensten door:sturen die in uw gegevensstroom, zoals Adobe Analytics en Experience Platform worden gevormd. Meer informatie over de [Experience Events](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in de productdocumentatie.

## Vereisten

* PodFile is bijgewerkt met vereiste SDK&#39;s.
* Geregistreerde extensies in AppDelegate.
* MobileCore is geconfigureerd om uw ontwikkelings-appId te gebruiken.
* Geïmporteerde SDK&#39;s.
* App met bovenstaande wijzigingen gemaakt en uitgevoerd.

## Leerdoelstellingen

In deze les zult u:

* Begrijp hoe te om XDM gegevens te structureren die op een schema worden gebaseerd.
* Verzend een XDM-gebeurtenis op basis van een standaardveldgroep.
* Verzend een XDM-gebeurtenis op basis van een aangepaste veldgroep.
* Verzend een XDM-aankoopgebeurtenis.
* Valideren met betrouwbaarheid.

## Een ervaringsgebeurtenis maken

De Adobe Experience Platform Edge-extensie kan gebeurtenissen die een eerder gedefinieerd XDM-schema volgen, verzenden naar Adobe Experience Platform Edge Network.

Het proces gaat als volgt...

1. Identificeer de mobiele toepassingsinteractie die u probeert te volgen.

1. Controleer uw schema en identificeer de aangewezen gebeurtenis.

1. Controleer uw schema en identificeer om het even welke extra gebieden die zouden moeten worden gebruikt om de gebeurtenis te beschrijven.

1. Hiermee wordt het gegevensobject samengesteld en gevuld.

1. Maak en verzend gebeurtenis.

1. Valideren.

Laten we naar een paar voorbeelden kijken.

### Voorbeeld 1 - standaardveldgroepen

Controleer het volgende voorbeeld zonder te proberen om het in steekproefapp uit te voeren:

1. In uw schema, identificeer de gebeurtenis u probeert te verzamelen, in dit voorbeeld volgen wij een productmening.
   ![productweergaveschema](assets/mobile-datacollection-prodView-schema.png)

1. Beginnen met het samenstellen van het object:

   ```swift
   var xdmData: [String: Any] = [
       "eventType": "commerce.productViews",
       "commerce": [
           "productViews": [
           "value": 1
           ]
       ]
   ]
   ```

   * eventType: Beschrijft de gebeurtenis die voorkwam, gebruik a [bekende waarde](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) indien mogelijk.
   * commerce.productViews.value: Geef de numerieke waarde van de gebeurtenis op. Als het een Booleaanse waarde (of &quot;Teller&quot; in Adobe Analytics) is, is de waarde altijd 1. Als het een numerieke of valutagebeurtenis is, kan de waarde > 1 zijn.

1. In uw schema, identificeer om het even welke extra gegevens verbonden aan de gebeurtenis. In dit voorbeeld neemt u `productListItems` Dit is een standaardset velden die worden gebruikt voor aan handel gerelateerde gebeurtenissen:
   ![productlijstitemschema](assets/mobile-datacollection-prodListItems-schema.png)
   * Let op: `productListItems` is een array, zodat er meerdere producten kunnen worden geleverd.

1. Breid uw xdmData-object uit om aanvullende gegevens op te nemen:

   ```swift
   var xdmData: [String: Any] = [
       "eventType": "commerce.productViews",
           "commerce": [
           "productViews": [
               "value": 1
           ]
       ],
       "productListItems": [
           [
               "name":  productName,
               "SKU": sku,
               "priceTotal": priceString,
               "quantity": 1
           ]
       ]
   ]
   ```

1. De gegevensstructuur gebruiken om een `ExperienceEvent`:

   ```swift
   let productViewEvent = ExperienceEvent(xdm: xdmData)
   ```

1. Verzend de gebeurtenis en de gegevens naar het Netwerk van de Rand van het Platform:

   ```swift
   Edge.sendEvent(experienceEvent: productViewEvent)
   ```

### Voorbeeld 2 - aangepaste veldgroepen

Controleer het volgende voorbeeld zonder te proberen om het in steekproefapp uit te voeren:

1. In uw schema, identificeer de gebeurtenis u probeert te verzamelen. In dit voorbeeld volgt u een &quot;App Interaction&quot; die bestaat uit een App Action-gebeurtenis en -naam.
   ![interactieschema app](assets/mobile-datacollection-appInteraction-schema.png)

1. Beginnen met het samenstellen van het object.

   >[!NOTE]
   >
   >  Standaardveldgroepen beginnen altijd in de hoofdmap van het object.
   >
   >  Groepen met aangepaste velden beginnen altijd onder een object dat uniek is voor uw Experience Cloud Org, &quot;_techmarketingdemos&quot; in dit voorbeeld.

   ```swift
   var xdmData: [String: Any] = [
   "_techmarketingdemos": [
       "appInformation": [
           "appInteraction": [
               "name": actionName,
               "appAction": [
                   "value": 1
                   ]
               ]
           ]
       ]
   ]
   ```

   Of anders...

   ```swift
   var xdmData: [String: Any] = [:]
   xdmData["_techmarketingdemos"] = [
       "appInformation": [
           "appInteraction": [
               "name": actionName,
               "appAction": [
                   "value": 1
               ]
           ]
       ]
   ]
   ```

1. De gegevensstructuur gebruiken om een `ExperienceEvent`.

   ```swift
   let appInteractionEvent = ExperienceEvent(xdm: xdmData)
   ```

1. Verzend de gebeurtenis en de gegevens naar het Netwerk van de Rand van het Platform.

   ```swift
   Edge.sendEvent(experienceEvent: appInteractionEvent)
   ```

### Schermweergave bijhouden toevoegen aan de Luma-app

In de bovenstaande voorbeelden wordt het denkproces hopelijk uitgelegd bij het samenstellen van een XDM-gegevensobject. Vervolgens voegen we schermweergave-tracking toe in de app Luma.

1. Ga naar `Home.swift`.
1. De volgende code toevoegen aan `viewDidAppear(...)`.

   ```swift
           let stateName = "luma: content: ios: us: en: home"
           var xdmData: [String: Any] = [:]
           //Page View
           xdmData["_techmarketingdemos"] = [
               "appInformation": [
                   "appStateDetails": [
                       "screenType": "App",
                       "screenName": stateName,
                       "screenView": [
                           "value": 1
                       ]
                   ]
               ]
           ]
           let experienceEvent = ExperienceEvent(xdm: xdmData)
           Edge.sendEvent(experienceEvent: experienceEvent)
   ```

1. Herhaal deze bewerking voor elk scherm in de app. `stateName` terwijl je gaat.



### Validatie

1. Controleer de [installatie-instructies](assurance.md) en sluit de simulator of het apparaat aan op Betrouwbaarheid.
1. Voer de actie uit en zoek naar `hitReceived` gebeurtenis van de `com.adobe.edge.konductor` leverancier.
1. Selecteer de gebeurtenis en bekijk de XDM-gegevens in het dialoogvenster `messages` object.
   ![gegevensverzamelingsvalidatie](assets/mobile-datacollection-validation.png)

### Voorbeeld 3 - aankoop

In dit voorbeeld gaat u ervan uit dat de gebruiker de volgende aankoop heeft uitgevoerd:

* Product nr. 1 - Yoga Mat.
   * $ 49,99 x 1
   * SKU: 5829
* Product nr. 2 - Waterfles.
   * $ 10,00 x 3
   * SKU: 9841
* Totaal bestelling: $ 79,99
* Unieke bestelling-id: 298234720
* Betalingstype: Visa Creditcard
* Unieke betalingstransactie-ID: 847361

#### Schema

Hier zijn de verwante schemagebieden aan gebruik:

* eventType: &quot;commerce.purchase&quot;
* commerce.purchases
* commerce.order
* productsListItems
* _techmarketingdemos.appStateDetails (aangepast)

>[!TIP]
>
>Aangepaste veldgroepen worden altijd onder de Experience Cloud Org-id geplaatst.
>
>&quot;_techmarketingdemos&quot; wordt vervangen door de unieke waarde van uw organisatie.

![koopschema](assets/mobile-datacollection-purchase-schema.png)


#### Code

Hieronder wordt beschreven hoe u het XDM-object in de app maakt en verzendt.

```swift
let stateName = "luma: content: ios: us: en: orderconfirmation"
let currencyCode = "USD"
let orderTotal = "79.99"
let paymentType = "Visa Credit Card"
let orderId = "298234720"
let paymentTransactionId = "847361"
var xdmData: [String: Any] = [
  "eventType": "commerce.purchases",
  "commerce": [
    "purchases": [
      "value": 1
    ],
    "order": [
      "currencyCode": currencyCode,
      "priceTotal": orderTotal,
      "purchaseID": orderId,
      "purchaseOrderNumber": orderId,
      "payments": [ //Assuming only 1 payment type is used
        [
          "currencyCode": currencyCode,
          "paymentAmount": orderTotal,
          "paymentType": paymentType,
          "transactionID": paymentTransactionId
        ]
      ]
    ]
  ],
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
]

//Custom field group
xdmData["_techmarketingdemos"] = [
  "appInformation": [
    "appStateDetails": [
      "screenType": "App",
      "screenName": stateName,
      "screenView": [
        "value": 1
      ]
    ]
  ]
]
let experienceEvent = ExperienceEvent(xdm: xdmData)
Edge.sendEvent(experienceEvent: experienceEvent)
```

>[!NOTE]
>
>Voor de duidelijkheid zijn alle waarden hardcoded. In een realiteit zouden de waarden dynamisch worden gevuld.


### Implementeren in de Luma-app

U moet over alle gereedschappen beschikken om gegevensverzameling toe te voegen aan de voorbeeldapp Luma. Hieronder vindt u een lijst met hypothetische traceervereisten die u kunt volgen.

* Houd elke schermweergave bij.
   * Schemavelden: screenType, screenName, screenView
* Handelingen voor niet-commerciële transacties volgen.
   * Schemavelden: appInteraction.name, appAction
* Handelingen in de handel:
   * Productpagina: productViews
   * Toevoegen aan winkelwagentje: productListAdds
   * Verwijderen uit winkelwagentje: productListRemovals
   * Afhandeling beginnen: kassa
   * Winkelwagentje weergeven: productListViews
   * Toevoegen aan Wishlist: saveForLaters
   * Aankoop: aankopen, bestellen

>[!TIP]
>
>Controleer de [volledig geïmplementeerde app](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) voor meer voorbeelden .

### Validatie

1. Controleer de [installatie-instructies](assurance.md) en sluit de simulator of het apparaat aan op Betrouwbaarheid.

1. Voer de actie uit en zoek naar `hitReceived` gebeurtenis van de `com.adobe.edge.konductor` leverancier.

1. Selecteer de gebeurtenis en bekijk de XDM-gegevens in het dialoogvenster `messages` object.
   ![gegevensverzamelingsvalidatie](assets/mobile-datacollection-validation.png)

## Gebeurtenissen verzenden naar Analytics en Platform

Nu u de gebeurtenissen hebt verzameld en naar het Netwerk van de Rand van het Platform verzonden, zullen zij naar de toepassingen en de diensten worden verzonden die in uw worden gevormd [datastream](create-datastream.md). In latere lessen wijst u deze gegevens toe aan [Adobe Analytics](analytics.md) en [Adobe Experience Platform](platform.md).

Volgende: **[WebViews](web-views.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)
---
title: Gebeurtenissen
description: Leer hoe u gebeurtenisgegevens kunt verzamelen in een mobiele app.
hide: true
source-git-commit: e119e2bdce524c834cdaf43ed9eb9d26948b0ac6
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 1%

---

# Gebeurtenissen

Leer hoe u gebeurtenissen in een mobiele app kunt bijhouden.

De uitbreiding van het Netwerk van Edge verstrekt API om de Gebeurtenissen van de Ervaring naar het Netwerk van de Rand van het Platform te verzenden. Een Experience Event is een object dat gegevens bevat die voldoen aan de XDM ExperienceEvent-schemadefinitie. Meer eenvoudig, vangen zij wat mensen in uw mobiele app doen. Zodra de gegevens door het Netwerk van de Rand van het Platform worden ontvangen, kan het aan toepassingen en de diensten door:sturen die in uw gegevensstroom, zoals Adobe Analytics en Experience Platform worden gevormd. Meer informatie over de [Experience Events](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in de productdocumentatie.

## Vereisten

* Alle pakketgebiedsdelen op zijn plaats in het project van Xcode.
* Geregistreerde extensies in AppDelegate.
* MobileCore is geconfigureerd om uw ontwikkelings-appId te gebruiken.
* Geïmporteerde SDK&#39;s.
* App met bovenstaande wijzigingen is gemaakt en uitgevoerd.

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

1. Herzie uw schema en identificeer de aangewezen gebeurtenis.

1. Controleer uw schema en identificeer om het even welke extra gebieden die zouden moeten worden gebruikt om de gebeurtenis te beschrijven.

1. Hiermee wordt het gegevensobject samengesteld en gevuld.

1. Maak en verzend gebeurtenis.

1. Valideren.


### Standaardveldgroepen

Voor de standaardveldgroepen ziet het proces er als volgt uit:

* In uw schema, identificeer de gebeurtenissen die u probeert te verzamelen. In dit voorbeeld volgt u de gebeurtenissen van de handelservaring, bijvoorbeeld een productmening (**[!UICONTROL productViews]**).

  ![productweergaveschema](assets/datacollection-prodView-schema.png)

* Als u een object wilt maken dat de ervaringsgebeurtenisgegevens in uw app bevat, gebruikt u de volgende code:

  ```swift
  var xdmData: [String: Any] = [
      "eventType": "commerce.productViews",
      "commerce": [
          "productViews": [
            "id": sku,
            "value": 1
          ]
      ]
  ]
  ```

   * `eventType`: Beschrijft de gebeurtenis die voorkwam, gebruik a [bekende waarde](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) indien mogelijk.
   * `commerce.productViews.id`: een tekenreekswaarde die de SKU van het product vertegenwoordigt
   * `commerce.productViews.value`: Geef de numerieke waarde van de gebeurtenis op. Als het een Booleaanse waarde (of &quot;Teller&quot; in Adobe Analytics) is, wordt de waarde altijd ingesteld op 1. Als het een numerieke of valutagebeurtenis is, kan de waarde > 1 zijn.

* In uw schema, identificeer om het even welke extra gegevens verbonden aan de gebeurtenis van de de meningsmening van het handelsproduct. In dit voorbeeld neemt u **[!UICONTROL productListItem]** Dit is een standaardset velden die worden gebruikt voor aan handel gerelateerde gebeurtenissen:

  ![productlijstitemschema](assets/datacollection-prodListItems-schema.png)
   * Let op: **[!UICONTROL productListItems]** is een array, zodat er meerdere producten kunnen worden geleverd.

* Als u deze gegevens wilt toevoegen, vouwt u uw `xdmData` object dat aanvullende gegevens moet bevatten:

```swift
var xdmData: [String: Any] = [
    "eventType": "commerce.productViews",
        "commerce": [
        "productViews": [
            "id": sku,
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

* U kunt deze gegevensstructuur nu gebruiken om een `ExperienceEvent`:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* En verzend de gebeurtenis en de gegevens naar het Netwerk van de Rand van het Platform gebruikend `sendEvent` API:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

U gaat nu eigenlijk deze code in uw project van Xcode uitvoeren.
U hebt verschillende acties met betrekking tot handelsproducten in uw app en u wilt gebeurtenissen verzenden die op deze acties zijn gebaseerd zoals die door de gebruiker worden uitgevoerd:

* weergave: komt voor wanneer gebruikers een specifiek product bekijken,
* toevoegen aan winkelwagentje: wanneer gebruikers tapps <img src="assets/addtocart.png" width="20" /> in een productdetailscherm,
* opslaan voor later: wanneer de gebruiker op tikt <img src="assets/saveforlater.png" width="15" /> in het detailscherm van het product,
* aankoop: wanneer de gebruiker op de knop tikt <img src="assets/purchase.png" width="20" /> in het detailscherm van het product.

Het verzenden van ervaringsgebeurtenissen structureren:

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in Xcode Project Navigator, en voeg het volgende aan toe `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` functie. Deze functie neemt de gebeurtenis en het product van de handelservaring als parameters:

   ```swift
   let xdmData: [String: Any] = [
       "eventType": "commerce." + commerceEventType,
       "commerce": [
           commerceEventType: [
               "id": product.sku,
               "value": 1
           ]
       ],
       "productListItems": [
           [
               "name": product.name,
               "priceTotal": product.price,
               "SKU": product.sku
           ]
       ]
   ]
   
   Logger.viewCycle.info("About to send commerce experience event of type  \(commerceEventType)..."
   let commerceExperienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: commerceExperienceEvent)
   ```

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Weergaven]** > **[!UICONTROL Producten]** > **[!UICONTROL ProductView]** en voeg diverse vraag aan toe `sendCommerceExperienceEvent` functie:

   1. Bij de `.task` modifier, binnen de `ATTrackingManager.trackingAuthorizationStatus` sluiting. Dit `.task` De bepaling wordt geroepen wanneer de productmening wordt geïnitialiseerd en getoond, zodat wilt u een gebeurtenis van de productmening op dat specifieke ogenblik verzenden.

      ```swift
      // Send commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productView", product: product)
      ```

   1. Voor elk van de knoppen (<img src="assets/saveforlater.png" width="15" />, <img src="assets/addtocart.png" width="20" /> en <img src="assets/purchase.png" width="20" />) in de werkbalk de desbetreffende oproep toevoegen binnen de `ATTrackingManager.trackingAuthorizationStatus == .authorized` sluiting:

      1. Voor <img src="assets/saveforlater.png" width="15" />:

         ```swift
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Voor <img src="assets/addtocart.png" width="20" />:

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Voor <img src="assets/purchase.png" width="20" />:

         ```swift
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

### Aangepaste veldgroepen

Stel dat u schermweergaven en interacties wilt bijhouden in de app zelf. U hebt een aangepaste veldgroep voor dit type gebeurtenissen gedefinieerd.

* In uw schema, identificeer de gebeurtenissen u probeert te verzamelen.
  ![interactieschema app](assets/datacollection-appInteraction-schema.png)

* Constructie van het object beginnen.

  >[!NOTE]
  >
  >* Standaardveldgroepen beginnen altijd in de hoofdmap van het object.
  >
  >* Groepen aangepaste velden beginnen altijd onder een object dat uniek is voor uw Experience Cloud Org. `_techmarketingdemos` in dit voorbeeld.

  Voor de toepassingsinteractiegebeurtenis maakt u een object als:

  ```swift
  let xdmData: [String: Any] = [
    "eventType": "application.interaction",
    "_techmarketingdemos": [
      "appInformation": [
          "appInteraction": [
              "name": "login",
              "appAction": [
                  "value": 1
                  ]
              ]
          ]
      ]
  ]
  ```

  Voor de gebeurtenis screen tracking zou u een object maken zoals:

  ```swift
  var xdmData: [String: Any] = [
    "eventType": "application.scene",
    "_techmarketingdemos": [
        "appInformation": [
            "appStateDetails": [
                "screenType": "App",
                    "screenName": "luma: content: ios: us: en: login",
                    "screenView": [
                        "value": 1
                    ]
                ]
            ] 
        ]
  ]
  ```


* U kunt deze gegevensstructuur nu gebruiken om een `ExperienceEvent`.

  ```swift
  let event = ExperienceEvent(xdm: xdmData)
  ```

* Verzend de gebeurtenis en de gegevens naar het Netwerk van de Rand van het Platform.

  ```swift
  Edge.sendEvent(experienceEvent: event)
  ```


Nogmaals, laten eigenlijk deze code in uw project van Xcode uitvoeren.

1. Voor het gemak definieert u twee functies in **[!UICONTROL MobileSDK]**. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Utils]** > **[!UICONTROL MobileSDK]** in uw Xcode-projectnavigator.

   1. Een voor app-interacties. Deze code toevoegen aan de `func sendAppInteractionEvent(actionName: String)` functie:

      ```swift
      let xdmData: [String: Any] = [
          "eventType": "application.interaction",
          tenant : [
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
      let appInteractionEvent = ExperienceEvent(xdm: xdmData)
      Edge.sendEvent(experienceEvent: appInteractionEvent)
      ```

   1. En één voor het volgen van het scherm. Deze code toevoegen aan de `func sendTrackScreenEvent(stateName: String) ` functie:

      ```swift
      let xdmData: [String: Any] = [
          "eventType": "application.scene",
          tenant : [
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
      ]
      let trackScreenEvent = ExperienceEvent(xdm: xdmData)
      Edge.sendEvent(experienceEvent: trackScreenEvent)
      ```

1. Navigeren naar **[!UICONTROL Luminantie]** > **[!UICONTROL Luminantie]** > **[!UICONTROL Weergaven]** > **[!UICONTROL Algemeen]** > **[!UICONTROL Aanmeldingsblad]**.

   1. Voeg de volgende gemarkeerde code toe aan de knop Aanmelden:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      dismiss()
      ```

   1. De volgende gemarkeerde code toevoegen aan `onAppear` modifier:

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

### Validatie

1. Controleer de [installatie-instructies](assurance.md) en sluit de simulator of het apparaat aan op Betrouwbaarheid.
1. Voer de app uit om u aan te melden en te communiceren met een product.

   1. Verplaats het pictogram Verzekering naar links.
   1. Selecteren **[!UICONTROL Home]** in de tabbalk.
   1. Selecteer het <img src="assets/login.png" width="15" /> om het aanmeldingsblad te openen.
   1. Selecteer het <img src="assets/insert.png" width="15" /> om een willekeurige e-mail en een klant-id in te voegen.
   1. Selecteren **[!UICONTROL Aanmelden]**.
   1. Selecteren **[!UICONTROL Producten]** in de tabbalk.
   1. Selecteer een product.
   1. Selecteer <img src="assets/saveforlater.png" width="15" />.
   1. Selecteer <img src="assets/addtocart.png" width="20" />.
   1. Selecteer <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-1.png" width="200"> <img src="./assets/mobile-app-events-2.png" width="200"> <img src="./assets/mobile-app-events-3.png" width="200">


1. In Verzekering UI, zoek naar **[!UICONTROL hitReceived]** gebeurtenissen van de **[!UICONTROL com.adobe.edge.konductor]** leverancier.
1. Selecteer de gebeurtenis en bekijk de XDM-gegevens in het dialoogvenster **[!UICONTROL berichten]** object.
   ![gegevensverzamelingsvalidatie](assets/datacollection-validation.png)


### Implementeren in de Luma-app

U moet nu over alle gereedschappen beschikken om gegevensverzameling toe te voegen aan de Luma-app. U kunt meer informatie toevoegen aan de manier waarop de gebruiker met uw producten werkt en u kunt meer oproepen voor interactie tussen apps en het bijhouden van schermen toevoegen aan uw app:

* Implementeer bestelling, kassa, lege mand en andere functionaliteit in de app en voeg relevante gebeurtenissen over ervaringen met handel toe aan deze functionaliteit.
* Herhaal de oproep om `sendAppInteractionEvent` met de juiste parameter om andere toepassingsinteracties van de gebruiker bij te houden.
* Herhaal de oproep om `sendTrackScreenEvent` met de juiste parameter om schermen bij te houden die door de gebruiker in de app worden weergegeven.

>[!TIP]
>
>Controleer de [volledig geïmplementeerde app](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) voor meer voorbeelden .


## Gebeurtenissen verzenden naar Analytics en Platform

Nu u de gebeurtenissen hebt verzameld en naar het Netwerk van de Rand van het Platform hebt verzonden, worden zij verzonden naar de toepassingen en de diensten die in uw worden gevormd [datastream](create-datastream.md). In latere lessen wijst u deze gegevens toe aan [Adobe Analytics](analytics.md) en [Adobe Experience Platform](platform.md).

>[!SUCCESS]
>
>U hebt uw app nu ingesteld om gebeurtenissen op het gebied van handel, interactie tussen apps en schermtracering bij te houden naar het Adobe Experience Platform Edge-netwerk en alle services die u in uw gegevensstroom hebt gedefinieerd.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[WebViews](web-views.md)**

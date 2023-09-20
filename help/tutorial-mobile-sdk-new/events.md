---
title: Gebeurtenisgegevens verzamelen
description: Leer hoe u gebeurtenisgegevens kunt verzamelen in een mobiele app.
hide: true
source-git-commit: a2788110b1c43d24022672bb5ba0f36af66d962b
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---

# Gebeurtenisgegevens verzamelen

Leer hoe u gebeurtenissen in een mobiele app kunt bijhouden.

De uitbreiding van het Netwerk van Edge verstrekt API om de Gebeurtenissen van de Ervaring naar het Netwerk van de Rand van het Platform te verzenden. Een Experience Event is een object dat gegevens bevat die voldoen aan de XDM ExperienceEvent-schemadefinitie. Meer eenvoudig, vangen zij wat mensen in uw mobiele app doen. Zodra de gegevens door het Netwerk van de Rand van het Platform worden ontvangen, kan het aan toepassingen en de diensten door:sturen die in uw gegevensstroom, zoals Adobe Analytics en Experience Platform worden gevormd. Meer informatie over de [Experience Events](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in de productdocumentatie.

## Vereisten

* Alle pakketgebiedsdelen zijn op zijn plaats in uw project van Xcode.
* Registreerde extensies in **[!UICONTROL AppDelegate]**.
* De geconfigureerde MobileCore-extensie om uw ontwikkeling te gebruiken `appId`.
* Geïmporteerde SDK&#39;s.
* De app is gemaakt en uitgevoerd met de bovenstaande wijzigingen.

## Leerdoelstellingen

In deze les zult u

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
   * `commerce.productViews.value`: de numerieke of Booleaanse waarde van de gebeurtenis. Als het een Booleaanse waarde (of &quot;Teller&quot; in Adobe Analytics) is, wordt de waarde altijd ingesteld op 1. Als het een numerieke of valutagebeurtenis is, kan de waarde > 1 zijn.

* In uw schema, identificeer om het even welke extra gegevens verbonden aan de gebeurtenis van de de meningsmening van het handelsproduct. In dit voorbeeld neemt u **[!UICONTROL productListItems]** Dit is een standaardset velden die worden gebruikt bij elke handelsgerelateerde gebeurtenis:

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
U hebt verschillende acties met betrekking tot handelsproducten in uw app en u wilt gebeurtenissen verzenden op basis van deze acties die door de gebruiker worden uitgevoerd:

* weergave: vindt plaats wanneer een gebruiker een specifiek product weergeeft,
* toevoegen aan winkelwagentje: wanneer een gebruiker tikt <img src="assets/addtocart.png" width="20" /> in een productdetailscherm,
* opslaan voor later: wanneer een gebruiker op tikt <img src="assets/saveforlater.png" width="15" /> in een productdetailscherm,
* aankoop: wanneer een gebruiker tikt <img src="assets/purchase.png" width="20" /> in een productdetailscherm.

Om het verzenden van aan handel gerelateerde ervaringsgebeurtenissen op een herbruikbare manier uit te voeren, gebruikt u een specifieke functie:

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Xcode Project navigator, en voeg het volgende aan toe `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` functie.

   ```swift
   // Set up a data dictionary, create an experience event and send the event.
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
   
   let commerceExperienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: commerceExperienceEvent)
   ```

   Deze functie neemt het type en het product van de handelservaring als parameters en

   * stelt de XDM-payload in als een woordenboek, waarbij de parameters van de functie worden gebruikt;
   * stelt een ervaringsgebeurtenis op met behulp van het woordenboek;
   * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** in de navigator van het Project van Xcode en voeg diverse vraag aan toe `sendCommerceExperienceEvent` functie:

   1. Bij de `.task` modifier, binnen de `ATTrackingManager.trackingAuthorizationStatus` sluiting. Dit `.task` De bepaling wordt geroepen wanneer de productmening wordt geïnitialiseerd en getoond, zodat wilt u een gebeurtenis van de productmening op dat specifieke ogenblik verzenden.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```

   1. Voor elk van de knoppen (<img src="assets/saveforlater.png" width="15" />, <img src="assets/addtocart.png" width="20" /> en <img src="assets/purchase.png" width="20" />) in de werkbalk de desbetreffende oproep toevoegen binnen de `ATTrackingManager.trackingAuthorizationStatus == .authorized` sluiting:

      1. Voor <img src="assets/saveforlater.png" width="15" />:

         ```swift
         // Send saveForLaters commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Voor <img src="assets/addtocart.png" width="20" />:

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Voor <img src="assets/purchase.png" width="20" />:

         ```swift
         // Send purchases commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

>[!TIP]
>
>Gebruik Kaart (`java.util.Map`) als de basisinterface voor het samenstellen van uw XDM-payload.


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

1. Voor het gemak definieert u twee functies in **[!UICONTROL MobileSDK]**. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in uw Xcode-projectnavigator.

   1. Een voor app-interacties. Deze code toevoegen aan de `func sendAppInteractionEvent(actionName: String)` functie:

      ```swift
      // Set up a data dictionary, create an experience event and send the event.
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

      Deze functie gebruikt de naam van de handeling als parameter en

      * stelt de XDM-payload in als een woordenboek, waarbij de parameter van de functie wordt gebruikt;
      * stelt een ervaringsgebeurtenis op met behulp van het woordenboek;
      * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.


   1. En één voor het volgen van het scherm. Deze code toevoegen aan de `func sendTrackScreenEvent(stateName: String) ` functie:

      ```swift
      // Set up a data dictionary, create an experience event and send the event.
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

      Deze functie gebruikt de statusnaam als parameter en

      * stelt de XDM-payload in als een woordenboek, waarbij de parameter van de functie wordt gebruikt;
      * stelt een ervaringsgebeurtenis op met behulp van het woordenboek;
      * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL Aanmeldingsblad]**.

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

## Validatie

1. Controleer de [installatie-instructies](assurance.md) en sluit de simulator of het apparaat aan op Betrouwbaarheid.
1. Voer de app uit, meld u aan en communiceer met een product.

   1. Verplaats het pictogram Verzekering naar links.
   1. Selecteren **[!UICONTROL Home]** in de tabbalk en controleer of er een **[!UICONTROL ECID]**, **[!UICONTROL E-mail]** en **[!UICONTROL CRM-id]** in het Startscherm.
   1. Selecteren **[!DNL Products]** in de tabbalk.
   1. Selecteer een product.
   1. Selecteer <img src="assets/saveforlater.png" width="15" />.
   1. Selecteer <img src="assets/addtocart.png" width="20" />.
   1. Selecteer <img src="assets/purchase.png" width="15" />.

      <img src="./assets/mobile-app-events-3.png" width="300">


1. In Verzekering UI, zoek naar **[!UICONTROL hitReceived]** gebeurtenissen van de **[!UICONTROL com.adobe.edge.konductor]** leverancier.
1. Selecteer de gebeurtenis en bekijk de XDM-gegevens in het dialoogvenster **[!UICONTROL berichten]** object.
   ![gegevensverzamelingsvalidatie](assets/datacollection-validation.png)


## Volgende stappen

U moet nu over alle gereedschappen beschikken om gegevensverzameling aan uw app toe te voegen. U kunt meer informatie toevoegen over de manier waarop de gebruiker in de app met uw producten werkt en u kunt meer oproepen voor interactie tussen de apps en het bijhouden van schermen toevoegen aan de app:

* Implementeer de opdracht, kassa, lege mand en andere functionaliteit van de app en voeg relevante gebeurtenissen uit de handelservaring toe aan deze functionaliteit.
* Herhaal de oproep om `sendAppInteractionEvent` met de juiste parameter om andere toepassingsinteracties van de gebruiker bij te houden.
* Herhaal de oproep om `sendTrackScreenEvent` met de juiste parameter om schermen bij te houden die door de gebruiker in de app worden weergegeven.

>[!TIP]
>
>Controleer de [voltooide app](https://git.corp.adobe.com/rmaur/Luma) voor meer voorbeelden .


## Gebeurtenissen verzenden naar Analytics en Platform

Nu u de gebeurtenissen hebt verzameld en naar het Netwerk van de Rand van het Platform hebt verzonden, worden zij verzonden naar de toepassingen en de diensten die in uw worden gevormd [datastream](create-datastream.md). In latere lessen wijst u deze gegevens toe aan [Adobe Analytics](analytics.md) en [Adobe Experience Platform](platform.md).

>[!SUCCESS]
>
>U hebt uw app nu ingesteld om gebeurtenissen op het gebied van handel, interactie tussen apps en schermtracering bij te houden naar het Adobe Experience Platform Edge-netwerk en alle services die u in uw gegevensstroom hebt gedefinieerd.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[WebViews](web-views.md)**

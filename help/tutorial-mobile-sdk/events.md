---
title: Gebeurtenisgegevens bijhouden in mobiele apps met Platform Mobile SDK
description: Leer hoe u gebeurtenisgegevens kunt bijhouden in een mobiele app.
jira: KT-14631
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
source-git-commit: afb15c561179386e7846e8cd8963f67820af09f1
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---

# Gebeurtenisgegevens bijhouden

Leer hoe u gebeurtenissen in een mobiele app kunt bijhouden.

De extensie Edge Network biedt een API om Experience Events naar Platform Edge Network te verzenden. Een Experience Event is een object dat gegevens bevat die voldoen aan de XDM ExperienceEvent-schemadefinitie. Meer eenvoudig, vangen zij wat mensen in uw mobiele app doen. Zodra het gegeven door de Edge Network van het Platform wordt ontvangen, kan het aan toepassingen en de diensten door:sturen die in uw gegevensstroom, zoals Adobe Analytics en Experience Platform worden gevormd. Leer meer over de [ Gebeurtenissen van de Ervaring ](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in de productdocumentatie.

## Vereisten

* Alle pakketgebiedsdelen zijn op zijn plaats in uw project van Xcode.
* Geregistreerde extensies in **[!UICONTROL AppDelegate]** .
* De geconfigureerde MobileCore-extensie voor gebruik van uw ontwikkeling `appId`.
* Geïmporteerde SDK&#39;s.
* De app is gemaakt en uitgevoerd met de bovenstaande wijzigingen.

## Leerdoelstellingen

In deze les zult u

* Begrijp hoe te om XDM gegevens te structureren die op een schema worden gebaseerd.
* Verzend een XDM-gebeurtenis op basis van een standaardveldgroep.
* Verzend een XDM-gebeurtenis op basis van een aangepaste veldgroep.
* Verzend een XDM-aankoopgebeurtenis.
* Valideren met Assurance.

## Een ervaringsgebeurtenis maken

De extensie Adobe Experience Platform Edge kan gebeurtenissen die een eerder gedefinieerd XDM-schema volgen, naar Adobe Experience Platform Edge Network verzenden.

Het proces gaat als volgt...

1. Identificeer de mobiele toepassingsinteractie die u probeert te volgen.

1. Herzie uw schema en identificeer de aangewezen gebeurtenis.

1. Controleer uw schema en identificeer om het even welke extra gebieden die zouden moeten worden gebruikt om de gebeurtenis te beschrijven.

1. Hiermee wordt het gegevensobject samengesteld en gevuld.

1. Maak en verzend gebeurtenis.

1. Valideren.


### Standaardveldgroepen

Voor de standaardveldgroepen ziet het proces er als volgt uit:

* In uw schema, identificeer de gebeurtenissen die u probeert te verzamelen. In dit voorbeeld volgt u de gebeurtenissen van de handelservaring, bijvoorbeeld een gebeurtenis van de productmening (**[!UICONTROL productViews]**).

  ![ schema van de productmening ](assets/datacollection-prodView-schema.png)

* Als u een object wilt maken dat de ervaringsgebeurtenisgegevens in uw app bevat, gebruikt u de volgende code:

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

   * `eventType`: Beschrijft de gebeurtenis die voorkwam, gebruik a [ bekende waarde ](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) wanneer mogelijk.
   * `commerce.productViews.value` : de numerieke of Booleaanse waarde van de gebeurtenis. Als het een Booleaanse waarde (of &quot;Teller&quot; in Adobe Analytics) is, wordt de waarde altijd ingesteld op 1. Als het een numerieke of valutagebeurtenis is, kan de waarde > 1 zijn.

* In uw schema, identificeer om het even welke extra gegevens verbonden aan de gebeurtenis van de de meningsmening van het handelsproduct. In dit voorbeeld neemt u **[!UICONTROL productListItems]** op. Dit is een standaardset velden die worden gebruikt met aan handel gerelateerde gebeurtenissen:

  ![ schema van de punten van de productlijst ](assets/datacollection-prodListItems-schema.png)
   * **[!UICONTROL productListItems]** is een array, zodat meerdere producten kunnen worden geleverd.

* Als u deze gegevens wilt toevoegen, vouwt u het `xdmData` -object uit om aanvullende gegevens op te nemen:

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

* U kunt deze gegevensstructuur nu gebruiken om een `ExperienceEvent` te maken:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* En verzend de gebeurtenis en de gegevens naar de Edge Network van het Platform gebruikend `sendEvent` API:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

De [`Edge.sendEvent` ](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API is het equivalent van AEP Mobile SDK aan de [`MobileCore.trackAction` ](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) en [`MobileCore.trackState` ](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackstate) API vraag. Zie [ migreren van Mobiele uitbreiding van Analytics aan de Edge Network van Adobe Experience Platform ](https://developer.adobe.com/client-sdks/documentation/adobe-analytics/migrate-to-edge-network/) voor meer informatie.

U gaat nu eigenlijk deze code in uw project van Xcode uitvoeren.
U hebt verschillende acties met betrekking tot handelsproducten in uw app en u wilt gebeurtenissen verzenden op basis van deze acties die door de gebruiker worden uitgevoerd:

* weergave: vindt plaats wanneer een gebruiker een specifiek product weergeeft,
* toevoegen aan winkelwagentje: wanneer een gebruiker tikt <img src="assets/addtocart.png" width="20"/> in een productdetailscherm,
* opslaan voor later: wanneer een gebruiker op tikt <img src="assets/saveforlater.png" width="15"/> in een productdetailscherm,
* aankoop: wanneer een gebruiker tikt <img src="assets/purchase.png" width="20"/> in een productdetailscherm.

Om het verzenden van aan handel gerelateerde ervaringsgebeurtenissen op een herbruikbare manier uit te voeren, gebruikt u een specifieke functie:

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Xcode Project navigator en voeg het volgende toe aan de `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` functie.

   ```swift
   // Set up a data dictionary, create an experience event and send the event.
   let xdmData: [String: Any] = [
       "eventType": "commerce." + commerceEventType,
       "commerce": [
           commerceEventType: [
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
   * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent` ](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** in de Xcode-projectnavigator en voeg verschillende aanroepen toe aan de functie `sendCommerceExperienceEvent` :

   1. Bij de `.task` -modifier, binnen de `ATTrackingManager.trackingAuthorizationStatus` -closure. Deze optie `.task` wordt aangeroepen wanneer de productweergave wordt geïnitialiseerd en weergegeven, zodat u op dat specifieke moment een productweergave-gebeurtenis wilt verzenden.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```

   1. Voor elk van de knoppen (<img src="assets/saveforlater.png" width="15"/> , <img src="assets/addtocart.png" width="20"/> en <img src="assets/purchase.png" width="20"/>) voegt u in de werkbalk de relevante aanroep toe in de map `ATTrackingManager.trackingAuthorizationStatus == .authorized` closure:

      1. Voor <img src="assets/saveforlater.png" width="15"/>:

         ```swift
         // Send saveForLater commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
         ```

      1. Voor <img src="assets/addtocart.png" width="20"/>:

         ```swift
         // Send productListAdds commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
         ```

      1. Voor <img src="assets/purchase.png" width="20"/>:

         ```swift
         // Send purchase commerce experience event
         MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
         ```

>[!TIP]
>
>Voor het geval u voor Android™ ontwikkelt, gebruik Kaart (`java.util.Map`) als stichtingsinterface om uw nuttige lading XDM te construeren.


### Aangepaste veldgroepen

Stel dat u schermweergaven en interacties wilt bijhouden in de app zelf. U hebt een aangepaste veldgroep voor dit type gebeurtenissen gedefinieerd.

* In uw schema, identificeer de gebeurtenissen u probeert te verzamelen.
  ![ schema van de toepassingsinteractie ](assets/datacollection-appInteraction-schema.png)

* Constructie van het object beginnen.

  >[!NOTE]
  >
  >* Standaardveldgroepen beginnen altijd in de hoofdmap van het object.
  >
  >* Groepen aangepaste velden beginnen altijd onder een object dat uniek is voor uw Experience Cloud Org, `_techmarketingdemos` in dit voorbeeld.

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


* U kunt deze gegevensstructuur nu gebruiken om een `ExperienceEvent` te maken.

  ```swift
  let event = ExperienceEvent(xdm: xdmData)
  ```

* Verzend de gebeurtenis en de gegevens naar de Edge Network van het Platform.

  ```swift
  Edge.sendEvent(experienceEvent: event)
  ```


Nogmaals, laten eigenlijk deze code in uw project van Xcode uitvoeren.

1. Voor het gemak definieert u twee functies in **[!UICONTROL MobileSDK]** . Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in de Xcode-projectnavigator.

   1. Een voor app-interacties. Voeg deze code toe aan de functie `func sendAppInteractionEvent(actionName: String)` :

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
      * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent` ](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.


   1. En één voor het volgen van het scherm. Voeg deze code toe aan de functie `func sendTrackScreenEvent(stateName: String) ` :

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
      * verzendt de ervaringsgebeurtenis gebruikend [`Edge.sendEvent` ](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]** .

   1. Voeg de volgende gemarkeerde code toe aan de knop Aanmelden:

      ```swift
      // Send app interaction event
      MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
      ```

   1. Voeg de volgende gemarkeerde code toe aan de optie `onAppear` :

      ```swift
      // Send track screen event
      MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
      ```

## Validatie

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat met Assurance te verbinden.

   1. Het Assurance-pictogram naar links verplaatsen.
   1. Selecteer **[!UICONTROL Home]** in de tabbalk en controleer of de **[!UICONTROL ECID]** , **[!UICONTROL Email]** en **[!UICONTROL CRM ID]** in het scherm Home worden weergegeven.
   1. Selecteer **[!DNL Products]** in de tabbalk.
   1. Selecteer een product.
   1. Selecteren <img src="assets/saveforlater.png" width="15"/>.
   1. Selecteren <img src="assets/addtocart.png" width="20"/>.
   1. Selecteren <img src="assets/purchase.png" width="15"/>.

      <img src="./assets/mobile-app-events-3.png" width="300">


1. Zoek in de gebruikersinterface van Assurance naar de **[!UICONTROL hitReceived]** -gebeurtenissen van de **[!UICONTROL com.adobe.edge.konductor]** -leverancier.
1. Selecteer de gebeurtenis en bekijk de XDM-gegevens in het **[!UICONTROL messages]** -object. Alternatief, kunt u ![ Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) gebruiken **[!UICONTROL Copy Raw Event]** en een tekst of coderedacteur van uw voorkeur gebruiken om de gebeurtenis te kleven en te inspecteren.

   ![ de bevestiging van de gegevensinzameling ](assets/datacollection-validation.png)


## Volgende stappen

U moet nu over alle gereedschappen beschikken om gegevensverzameling aan uw app toe te voegen. U kunt meer informatie toevoegen over de manier waarop de gebruiker in de app met uw producten werkt en u kunt meer oproepen voor interactie tussen de apps en het bijhouden van schermen toevoegen aan de app:

* Implementeer de opdracht, kassa, lege mand en andere functionaliteit van de app en voeg relevante gebeurtenissen uit de handelservaring toe aan deze functionaliteit.
* Herhaal de aanroep van `sendAppInteractionEvent` met de juiste parameter om andere toepassingsinteracties van de gebruiker bij te houden.
* Herhaal de aanroep van `sendTrackScreenEvent` met de juiste parameter om schermen bij te houden die door de gebruiker in de app worden weergegeven.

>[!TIP]
>
>Herzie [ voltooide app ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) voor meer voorbeelden.


## Gebeurtenissen verzenden naar Analytics en Platform

Nu u de gebeurtenissen hebt verzameld en hen verzonden naar de Edge Network van het Platform, worden zij verzonden naar de toepassingen en de diensten die in uw [ worden gevormd datastream ](create-datastream.md). In recentere lessen, brengt u deze gegevens in kaart aan [ Adobe Analytics ](analytics.md), [ Adobe Experience Platform ](platform.md), en andere oplossingen van Adobe Experience Cloud zoals [ Adobe Target ](target.md) en Adobe Journey Optimizer.

>[!SUCCESS]
>
>U hebt nu uw app ingesteld om gebeurtenissen op het gebied van handel, interactie tussen apps en schermtracering bij te houden voor de Adobe Experience Platform-Edge Network en alle services die u in uw gegevensstroom hebt gedefinieerd.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van de Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[Handle WebViews](web-views.md)**

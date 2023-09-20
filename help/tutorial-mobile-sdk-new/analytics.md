---
title: Gegevens toewijzen aan analysegegevens
description: Leer hoe u gegevens voor Adobe Analytics kunt verzamelen en toewijzen in een mobiele app.
solution: Data Collection,Experience Platform,Analytics
hide: true
source-git-commit: 5f178f4bd30f78dff3243b3f5bd2f9d11c308045
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Analysegegevens verzamelen en toewijzen

Leer hoe u mobiele gegevens kunt toewijzen aan Adobe Analytics.

De [event](events.md) gegevens die u in eerdere lessen hebt verzameld en naar Platform Edge Network hebt verzonden, worden doorgestuurd naar de services die in uw gegevensstroom zijn geconfigureerd, waaronder Adobe Analytics. U brengt de gegevens aan de correcte variabelen in uw rapportreeks in kaart.

![Architectuur](assets/architecture-aa.png)

## Vereisten

* Inzicht in het bijhouden van ExperienceEvent.
* XDM-gegevens worden naar uw voorbeeld-app verzonden.
* DataStream geconfigureerd voor Adobe Analytics

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
a.x._techmarketingdemos.appinformation.appstatedetails.screenname
```

>[!NOTE]
>
>Aangepaste velden worden onder de Org-id van het Experience Cloud geplaatst.
>
>`_techmarketingdemos` wordt vervangen door de unieke waarde van uw organisatie.

Om deze XDM contextgegevens aan uw gegevens van Analytics in uw rapportreeks in kaart te brengen, kunt u:

* Voeg de **[!UICONTROL Adobe Analytics ExperienceEvent Volledige extensie]** veldgroep aan uw schema.

  ![Analytics ExperienceEvent FullExtension, veldgroep](assets/schema-analytics-extension.png)
* Stel regels samen in de eigenschap Tags om de contextgegevens toe te wijzen aan de velden in de veldgroep Volledige extensie van Adobe Analytics ExperienceEvent. Bijvoorbeeld, map `_techmarketingdemo.appinformation.appstatedetails.screenname` tot `_experience.analytics.customDimensions.eVars.eVar2`.

<!-- Old processing rules section
Here is what a processing rule using this data might look like:

* You **[!UICONTROL Overwrite value of]** (1) **[!UICONTROL App Screen Name (eVar2)]** (2) with the value of **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (3) if **[!UICONTROL a.x._techmarketingdemo.appinformation.appstatedetails.screenname]** (4) **[!UICONTROL is set]** (5).

* You **[!UICONTROL Set event]** (6) **[!UICONTROL Add to Wishlist (Event 3)]** (7) to **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (8) if **[!UICONTROL a.x.commerce.saveForLaters.value(Context)]** (9) **[!UICONTROL is set]** (10).

![analytics processing rules](assets/analytics-processing-rules.png)

>[!IMPORTANT]
>
>
>Some of the automatically mapped variables may not be available for use in processing rules.
>
>
>The first time you map to a processing rule, the interface does not show you the context data variables from the XDM object. To fix that select any value, Save, and come back to edit. All XDM variables should now appear.


Additional information about processing rules and context data can be found [here](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/map-contextdata-variables-into-props-and-evars-with-processing-rules.html?lang=en).

>[!TIP]
>
>Unlike previous mobile app implementations, there is no distinction between a page / screen views and other events. Instead you can increment the **[!UICONTROL Page View]** metric by setting the **[!UICONTROL Page Name]** dimension in a processing rule. Since you are collecting the custom `screenName` field in the tutorial, it is highly recommended to map screen name to **[!UICONTROL Page Name]** in a processing rule.

-->

>[!SUCCESS]
>
>U hebt uw app zo ingesteld dat uw Experience Edge XDM-objecten worden toegewezen aan Adobe Analytics-variabelen, waardoor de Adobe Analytics-service in uw gegevensstroom kan worden gebruikt en waar van toepassing verwerkingsregels kunnen worden gebruikt.<br/> Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Gegevens naar Experience Platform verzenden](platform.md)**

---
title: Parameters verzenden - Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe te om mbox, profiel, en entiteitsparameters naar Adobe Target te verzenden gebruikend het Web SDK van het Experience Platform.
exl-id: 7916497b-0078-4651-91b1-f53c86dd2100
source-git-commit: 0697c6d13272182432e11fdb9d84a752d39527b6
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 0%

---

# Parameters verzenden naar doel met gebruik van Platform Web SDK

De doelimplementaties verschillen per website vanwege de sitearchitectuur, de zakelijke vereisten en de gebruikte functies. De meeste doelimplementaties bevatten het doorgeven van verschillende parameters voor contextuele informatie, doelgroepen en aanbevelingen voor inhoud.

Laten we een eenvoudige pagina met productdetails en een pagina met orderbevestiging gebruiken om de verschillen tussen de bibliotheken aan te tonen bij het doorgeven van parameters aan Doel.

Stel dat de volgende twee voorbeeldpagina&#39;s at.js gebruiken:

+++at.js op een pagina van de Details van het Product:

```HTML
<!doctype html>
<html>
<head>
  <title>Product Details - Men's Shirt</title>
  <!--Target parameters -->
  <script>
    targetPageParams = function() {
      return {
        // Property token
        "at_property": "5a0fd9bb-67de-4b5a-0fd7-9cc09f50a58d",
        // Mbox parameters
        "pageName": "product detail",
        // Profile parameters
        "profile.gender": "male",
        "user.categoryId": "clothing",
        // Entity parameters for Target Recomendations
        "entity.id": "SKU-00001-LARGE",
        "entity.categoryId": "clothing,shirts",
        "entity.customEntity": "some value",
        "cartIds": "SKU-00002,SKU-00003",
        "excludedIds": "SKU-00001-SMALL",
        // Customer ID for cross-device profile synching and Customer Attributes
        "mbox3rdPartyId": "TT8675309",
      };
    };
  </script>
  <!--Target at.js library loaded asynchonously-->
  <script src="/libraries/at.js" async></script>
</head>
<body>
  <h1 id="title">Men's Large Shirt</h1>
  <p>SKU: SKU-00001-LARGE</p>
</body>
</html>
```

+++


+++at.js op een pagina voor bevestiging van bestelling:

```HTML
<!doctype html>
<html>
<head>
  <title>Order Confirmation</title>-->
  <!--Target parameters -->
  <script>
    targetPageParams = function() {
      return {
        // Property token
        "at_property": "5a0fd9bb-67de-4b5a-0fd7-9cc09f50a58d",
        // Order confirmation parameters
        "orderId": "ABC123",
        "productPurchasedId": "SKU-00002,SKU-00003",
        "orderTotal": 1337.89,
        // Customer ID for cross-device profile synching and Customer Attributes
        "mbox3rdPartyId": "TT8675309",
      };
    };
  </script>
  <!--Target at.js library loaded asynchonously-->
  <script src="/libraries/at.js" async></script>
</head>
<body>
  <h1 id="title">Order Confirmation</h1>
  <p>Thank you for your order</p>
</body>
</html>
```

+++


## Overzicht van parametertoewijzing

De parameters van het Doel voor deze pagina&#39;s worden anders verzonden gebruikend het Web SDK van het Platform. Er zijn veelvoudige manieren om parameters tot Doel over te gaan gebruikend at.js:

- Instellen met functie `targetPageParams()` voor de gebeurtenis load van de pagina (wordt gebruikt in de voorbeelden op deze pagina)
- Instellen met functie `targetPageParamsAll()` voor alle doelaanvragen op de pagina
- Parameters rechtstreeks verzenden met de functie `getOffer()` voor één locatie
- Parameters rechtstreeks verzenden met de functie `getOffers()` voor een of meer locaties


De SDK van het Web van het Platform verstrekt één enkele verenigbare manier om gegevens zonder de behoefte aan extra functies te verzenden. Alle parameters moeten in de lading met het `sendEvent` bevel worden overgegaan en onder twee categorieën vallen:

- Automatisch toegewezen via het `xdm` -object
- Handmatig worden doorgegeven met het object `data.__adobe.target`

In de onderstaande tabel wordt beschreven hoe de voorbeeldparameters opnieuw worden toegewezen met gebruik van Platform Web SDK:

| Voorbeeld van parameter at.js | Platform Web SDK, optie | Notities |
| --- | --- | --- |
| `at_property` | N.v.t. | De tokens van het bezit worden gevormd in [&#x200B; datastream &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html?lang=nl-NL#target) en kunnen niet in de `sendEvent` vraag worden geplaatst. |
| `pageName` | `xdm.web.webPageDetails.name` | Alle parameters van Target mbox moeten worden doorgegeven als onderdeel van het `xdm` -object en moeten in overeenstemming zijn met een schema met behulp van de XDM ExperienceEvent-klasse. Mbox-parameters kunnen niet worden doorgegeven als onderdeel van het `data` -object. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle parameters van het doelprofiel moeten worden doorgegeven als onderdeel van het `data` -object en vooraf ingesteld met `profile.` om correct te worden toegewezen. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Gereserveerde parameter die wordt gebruikt voor de functie Categorie-affiniteit van Doel die moet worden doorgegeven als onderdeel van het `data` -object. |
| `entity.id` | `data.__adobe.target.entity.id` <br> OF <br> `xdm.productListItems[0].SKU` | Identiteitskaart van de entiteit wordt gebruikt voor het gedrag van Recommendations van het Doel tellers. Deze entiteit-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object of automatisch worden toegewezen vanuit het eerste item in de `xdm.productListItems` -array als die veldgroep door de implementatie wordt gebruikt. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Identiteitscategorie-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Parameters voor aangepaste entiteiten worden gebruikt voor het bijwerken van de Recommendations-productcatalogus. Deze aangepaste parameters moeten worden doorgegeven als onderdeel van het object `data` . |
| `cartIds` | `data.__adobe.target.cartIds` | Wordt gebruikt voor op kaarten gebaseerde aanbevelingen-algoritmen van Target. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wordt gebruikt om te voorkomen dat bepaalde id&#39;s van entiteiten terugkeren in een ontwerp met aanbevelingen. |
| `mbox3rdPartyId` | Instellen in het object `xdm.identityMap` | Wordt gebruikt voor het synchroniseren van doelprofielen op verschillende apparaten en klantkenmerken. Namespace voor klantidentiteitskaart te gebruiken moet in de [&#x200B; configuratie van het Doel van de datastream &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html?lang=nl-NL) worden gespecificeerd. |
| `orderId` | `xdm.commerce.order.purchaseID` | Wordt gebruikt voor het identificeren van een unieke volgorde voor het bijhouden van doelconversie. |
| `orderTotal` | `xdm.commerce.order.priceTotal` | Wordt gebruikt voor het bijhouden van ordertotalen voor doelconversie- en optimalisatiedoelstellingen. |
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br> OF <br> `xdm.productListItems[0-n].SKU` | Wordt gebruikt voor het bijhouden van doelconversie en aanbevelingen. Verwijs naar de [&#x200B; sectie van entiteitparameters &#x200B;](#entity-parameters) hieronder voor details. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Gebruikt voor het [&#x200B; douane die &#x200B;](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html?lang=nl-NL) activiteitendoel scoren. |

{style="table-layout:auto"}

## Aangepaste parameters

Aangepaste mbox-parameters moeten als XDM-gegevens worden doorgegeven met de opdracht `sendEvent` . Het is belangrijk om ervoor te zorgen dat het schema XDM alle gebieden omvat die voor uw implementatie van het Doel worden vereist.

bij.js-voorbeeld met `targetPageParams()` :

```JavaScript
targetPageParams = function() {
  return {
    "pageName": "product detail"
  };
};
```

Platform Web SDK JavaScript voorbeelden met de opdracht `sendEvent` :

>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("sendEvent", {
  "xdm": {
    "web": {
      "webPageDetails": {
        // Other attributes included according to xdm schema
        "name": "product detail"
      }
    }
  }
});
```

>[!TAB  Markeringen ]

Gebruik in tags eerst een gegevenselement [!UICONTROL XDM object] om toe te wijzen aan het XDM-veld:

![&#x200B; Toewijzing aan een XDM gebied in een XDM gegevenselement van Objecten &#x200B;](assets/params-tags-pageName.png){zoomable="yes"}

En dan omvat uw [!UICONTROL XDM object] in uw [!UICONTROL Send event] [!UICONTROL action] (het veelvoud [!UICONTROL XDM objects] kan [&#x200B; worden samengevoegd &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/core/overview.html?lang=nl-NL#merged-objects)):

![&#x200B; die een XDM objecten gegevenselement in een Send gebeurtenis &#x200B;](assets/params-tags-sendEvent.png){zoomable="yes"} omvat

>[!ENDTABS]


>[!NOTE]
>
>Omdat aangepaste mbox-parameters deel uitmaken van `xdm` -object, moet u alle soorten publiek-, activiteiten- of profielscripts die naar deze mbox-parameters verwijzen, bijwerken met hun nieuwe naam. Zie het [&#x200B; publiek van het Doel van de Update en profielmanuscripten voor de verenigbaarheid van SDK van het Web van het Platform &#x200B;](update-audiences.md) pagina van dit leerprogramma voor meer informatie.


## Profielparameters

Doelprofielparameters moeten worden doorgegeven onder het `data.__adobe.target` -object in de opdrachtpayload van de opdracht Platform Web SDK `sendEvent` .

Net als bij at.js moeten alle profielparameters ook vooraf met `profile.` worden opgeslagen om de waarde als blijvend doelprofielkenmerk correct te kunnen opslaan. De gereserveerde `user.categoryId` -parameter voor de Categorie-affiniteit van Doel wordt vooraf ingesteld door `user.` .

bij.js-voorbeeld met `targetPageParams()` :

```JavaScript
targetPageParams = function() {
  return {
    "profile.gender": "male",
    "user.categoryId": "clothing"
  };
};
```

Voorbeelden van Platform Web SDK met de opdracht `sendEvent` :

>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("sendEvent", {
  "data": {
    "__adobe": {
      "target": {
        "profile.gender": "male",
        "user.categoryId": "clothing"
      }
    }
  }
});
```

>[!TAB  Markeringen ]

Maak in tags eerst een gegevenselement om het object `data.__adobe.target` te definiëren:

![&#x200B; die uw gegevensvoorwerp in een gegevenselement bepalen &#x200B;](assets/params-tags-dataObject.png){zoomable="yes"}

En dan omvat uw gegevensvoorwerp in uw [!UICONTROL Send event] [!UICONTROL action] (het veelvoud [!UICONTROL objects] kan [&#x200B; worden samengevoegd &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/core/overview.html?lang=nl-NL#merged-objects)):

![&#x200B; Omvat een gegevensvoorwerp in een Send gebeurtenis &#x200B;](assets/params-tags-sendEvent-withData.png){zoomable="yes"}

>[!ENDTABS]

## Parameters entiteit

Entiteitsparameters worden gebruikt om gedragsgegevens en aanvullende catalogusinformatie voor Target Recommendations door te geven. Alle [&#x200B; entiteitparameters &#x200B;](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html?lang=nl-NL) die door at.js worden gesteund worden ook gesteund door het Web SDK van het Platform. Net als profielparameters moeten alle entiteitsparameters worden doorgegeven onder het `data.__adobe.target` -object in de opdrachtpayload van de opdracht Platform Web SDK `sendEvent` .

Entiteiteits-parameters voor een specifiek item moeten vooraf met `entity.` worden vastgelegd om de gegevens correct vast te leggen. De gereserveerde `cartIds` - en `excludedIds` -parameters voor aanbevelingen-algoritmen mogen niet vooraf worden ingesteld en de waarde voor beide moet een door komma&#39;s gescheiden lijst met entiteit-id&#39;s bevatten.

bij.js-voorbeeld met `targetPageParams()` :

```JavaScript
targetPageParams = function() {
  return {
    "entity.id": "SKU-00001-LARGE",
    "entity.categoryId": "clothing,shirts",
    "entity.customEntity": "some value",
    "cartIds": "SKU-00002,SKU-00003",
    "excludedIds": "SKU-00001-SMALL"
  };
};
```

Voorbeelden van Platform Web SDK met de opdracht `sendEvent` :

>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("sendEvent", {
  "data": {
    "__adobe": {
      "target": {
        "entity.id": "SKU-00001-LARGE",
        "entity.categoryId": "clothing,shirts",
        "entity.customEntity": "some value",
        "cartIds": "SKU-00002,SKU-00003",
        "excludedIds": "SKU-00001-SMALL"
      }
    }
  }
});
```

>[!TAB  Markeringen ]

Maak in tags eerst een gegevenselement om het object `data.__adobe.target` te definiëren:

![&#x200B; die uw gegevensvoorwerp in een gegevenselement bepalen &#x200B;](assets/params-tags-dataObject-entities.png){zoomable="yes"}

En dan omvat uw gegevensvoorwerp in uw [!UICONTROL Send event] [!UICONTROL action] (het veelvoud [!UICONTROL objects] kan [&#x200B; worden samengevoegd &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/core/overview.html?lang=nl-NL#merged-objects)):

![&#x200B; Omvat een gegevensvoorwerp in een Send gebeurtenis &#x200B;](assets/params-tags-sendEvent-withData.png){zoomable="yes"}

>[!ENDTABS]

>[!NOTE]
>
>Als de veldgroep `commerce` wordt gebruikt en de array `productListItems` is opgenomen in de XDM-payload, wordt de eerste `SKU` -waarde in deze array toegewezen aan `entity.id` voor het verhogen van de productweergave.


## Aankoopparameters

De parameters van de aankoop worden overgegaan op een de bevestigingspagina van het orde na een succesvolle orde en voor de omzettings en optimalisatiedoelstellingen van het Doel gebruikt. Met een implementatie van het Web SDK van het Platform, deze parameters en automatisch in kaart gebracht van gegevens XDM die als deel van de `commerce` gebiedsgroep worden overgegaan.

bij.js-voorbeeld met `targetPageParams()` :

```JavaScript
targetPageParams = function() {
  return {
    "orderId": "ABC123",
    "productPurchasedId": "SKU-00002,SKU-00003"
    "orderTotal": 1337.89
  };
};
```

Aankoopgegevens worden doorgegeven aan Target wanneer voor de veldgroep `commerce` `purchases.value` is ingesteld op `1` . De bestellings-id en het totaal van de bestellingen worden automatisch toegewezen aan het `order` -object. Als de array `productListItems` aanwezig is, worden de waarden `SKU` gebruikt voor `productPurchasedId` .

Voorbeeld van Platform Web SDK met `sendEvent` :

>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("sendEvent", {
  "xdm": {
    "commerce": {
      "order": {
        "purchaseID": "ABC123",
        "priceTotal": 1337.89
      },
      "purchases": {
        "value": 1
      }
    },
    "productListItems": [{
      "SKU": "SKU-00002"
    }, {
      "SKU": "SKU-00003"
    }],
      "_experience": {
          "decisioning": {
              "propositions": [{
                  "scope": "<your_mbox>"
              }],
              "propositionEventType": {
                  "display": 1
              }
          }
      }
  }
});
```

>[!TAB  Markeringen ]

Gebruik in tags eerst een gegevenselement [!UICONTROL XDM object] om toe te wijzen aan de vereiste XDM-velden (zie het JavaScript-voorbeeld) en een optioneel aangepast bereik:

![&#x200B; Toewijzing aan een XDM gebied in een XDM gegevenselement van Objecten &#x200B;](assets/params-tags-purchase.png){zoomable="yes"}

En dan omvat uw [!UICONTROL XDM object] in uw [!UICONTROL Send event] [!UICONTROL action] (het veelvoud [!UICONTROL XDM objects] kan [&#x200B; worden samengevoegd &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/core/overview.html?lang=nl-NL#merged-objects)):

![&#x200B; die een XDM objecten gegevenselement in een Send gebeurtenis &#x200B;](assets/params-tags-sendEvent-purchase.png){zoomable="yes"} omvat

>[!ENDTABS]

>[!IMPORTANT]
>
> `_experience.decisioning.propositionEventType` moet met `display: 1` worden geplaatst om de vraag te gebruiken om metrisch van het Doel te verhogen.

>[!NOTE]
>
> Als u bijvoorbeeld een aangepaste naam voor de locatie of het selectievakje wilt gebruiken in de definitie van het doel, `orderConfirmPage` , vult u de array `_experience.decisioning.propositions` met een aangepast bereik, zoals in het bovenstaande voorbeeld.

>[!NOTE]
>
>De waarde `productPurchasedId` kan ook worden doorgegeven als een door komma&#39;s gescheiden lijst met entiteit-id&#39;s onder het object `data` .


## Klant-id (mbox3rdPartyId)

Het doel staat profielsynchronisatie over apparaten en systemen toe gebruikend één enkele klant ID. Met at.js, kon dit als `mbox3rdPartyId` in het verzoek van het Doel worden geplaatst of als eerste klantenidentiteitskaart die naar de Dienst van de Identiteit van het Experience Cloud wordt verzonden. In tegenstelling tot at.js, staat een implementatie van SDK van het Web van het Platform u toe om te specificeren welke klantenidentiteitskaart aan gebruik als `mbox3rdPartyId` als er veelvoudige zijn. Bijvoorbeeld, als uw zaken een globale klant identiteitskaart en afzonderlijke klant IDs voor verschillende lijnen van zaken hebben, kunt u vormen welk Doel van identiteitskaart zou moeten gebruiken.

Er zijn een paar stappen aan opstellingsidentiteitskaart die voor dwars-apparaat en de het gebruikscituaties van Attributen van de Klant synchroniseert:

1. Maak een **[!UICONTROL identity namespace]** voor de klant-id in het **[!UICONTROL Identities]** -scherm van gegevensverzameling of -platform
1. Zorg ervoor dat **[!UICONTROL alias]** in Klantkenmerken overeenkomt met de **[!UICONTROL identity symbol]** van uw naamruimte
1. Geef de **[!UICONTROL identy symbol]** op als de **[!UICONTROL Target Third Party ID Namespace]** in de configuratie Doel van de gegevensstroom
1. Een opdracht `sendEvent` uitvoeren met de veldgroep `identityMap`

bij.js-voorbeeld met `targetPageParams()` :

```JavaScript
targetPageParams = function() {
  return {
    "mbox3rdPartyId": "TT8675309"
  };
};
```

Voorbeelden van Platform Web SDK met de opdracht `sendEvent` :

>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("sendEvent", {
  "xdm": {
    "identityMap": {
      "GLOBAL_CUSTOMER_ID": [{
        "id": "TT8675309",
        "authenticatedState": "authenticated",
        "primary": true
      }]
    }
  }
});
```

>[!TAB  Markeringen ]

De [!UICONTROL ID] value [!UICONTROL Authenticated state] en [!UICONTROL Namespace] worden vastgelegd in een [!UICONTROL Identity map] data-element:
![&#x200B; het gegevenselement van de Kaart van de Identiteit die klantenidentiteitskaart &#x200B;](assets/params-tags-customerIdDataElement.png){zoomable="yes"} vangen

Het gegevenselement [!UICONTROL Identity map] wordt vervolgens gebruikt om het [!UICONTROL identityMap] veld in het gegevenselement [!UICONTROL XDM object] in te stellen:
![&#x200B; het gegevenselement van de Kaart van de Identiteit dat in XDM objecten gegevenselement &#x200B;](assets/params-tags-customerIdInXDMObject.png){zoomable="yes"} wordt gebruikt

[!UICONTROL XDM object] wordt vervolgens opgenomen in de [!UICONTROL Send event] -handeling van een regel:

![&#x200B; die een XDM objecten gegevenselement in een Send gebeurtenis &#x200B;](assets/params-tags-sendEvent-xdm.png){zoomable="yes"} omvat

In de Adobe Target-service van uw gegevensstroom moet u de [!UICONTROL Target Third Party ID Namespace] instellen op dezelfde naamruimte als in het gegevenselement [!UICONTROL Identity map] :
![&#x200B; plaats identiteitskaart Namespace van de Derde van het Doel in de datastream &#x200B;](assets/params-tags-customerIdNamespaceInDatastream.png){zoomable="yes"}

>[!ENDTABS]

>[!NOTE]
>
> Adobe raadt aan naamruimten die een persoon vertegenwoordigen, zoals geverifieerde identiteiten, als primaire identiteit te verzenden.



## Platform Web SDK, voorbeeld

Nu u begrijpt hoe de verschillende parameters van het Doel gebruikend het Web SDK van het Platform in kaart worden gebracht, zouden onze twee voorbeeldpagina&#39;s van at.js aan het Web SDK van het Platform zoals hieronder getoond kunnen worden gemigreerd. De voorbeeldpagina&#39;s omvatten het volgende:

- Voorverborgen fragment voor asynchrone bibliotheekimplementatie als doel
- De basiscode van de SDK van het Web Platform
- De Platform Web SDK JavaScript-bibliotheek
- Een opdracht `configure` om de bibliotheek te initialiseren
- Een opdracht `sendEvent` om gegevens te verzenden en om te vragen dat doelinhoud moet worden gerenderd

+++Web SDK op een pagina van de Details van het Product:

```HTML
<!doctype html>
<html>
<head>
  <title>Product Details - Men's Shirt</title>

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

  <!--Platform Web SDK base code-->
  <script>
    !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
    []).push(o),n[o]=function(){var u=arguments;return new Promise(
    function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
    (window,["alloy"]);
  </script>

  <!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
  <script src="https://cdn1.adoberesources.net/alloy/2.6.4/alloy.min.js" async></script>

  <!--Configure Platform Web SDK and send event-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
    alloy("sendEvent", {
      "renderDecisions": true,
      "xdm": {
        "identityMap": {
          "GLOBAL_CUSTOMER_ID": [{
            "id": "TT8675309",
            "authenticatedState": "authenticated",
            "primary": true
          }]
        },
        "web": {
          "webPageDetails": {
            // Other attributes included according to XDM schema
            "pageName": "product detail"
          }
        }
      },
      "data": {
        "__adobe": {
          "target": {
            "profile.gender": "male",
            "user.categoryId": "clothing",
            "entity.id": "SKU-00001-LARGE",
            "entity.categoryId": "clothing,shirts",
            "entity.customEntity": "some value",
            "cartIds": "SKU-00002,SKU-00003",
            "excludedIds": "SKU-00001-SMALL"
          }
        }
      }
    });
  </script>
</head>
<body>
  <h1 id="title">Men's Large Shirt</h1>
  <p>SKU: SKU-00001-LARGE</p>
</body>
</html>
```

+++

+++Web SDK op een pagina van de Bevestiging van de Orde:

```HTML
<!doctype html>
<html>
<head>
  <title>Order Confirmation</title>


  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->

  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

  <!--Platform Web SDK base code-->

  <script>
    !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
    []).push(o),n[o]=function(){var u=arguments;return new Promise(
    function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
    (window,["alloy"]);
  </script>
  <!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
  <script src="https://cdn1.adoberesources.net/alloy/2.6.4/alloy.min.js" async></script>

  <!--Configure Platform Web SDK and send event-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
    alloy("sendEvent", {
      "xdm": {
        "identityMap": {
          "GLOBAL_CUSTOMER_ID": [{
            "id": "TT8675309",
            "authenticatedState": "authenticated",
            "primary": true
          }]
        },
        "commerce": {
          "order": {
            "purchaseID": "ABC123",
            "priceTotal": 1337.89
          },
          "purchases": {
            "value": 1
          }
        },
        "productListItems": [{
          "SKU": "SKU-00002"
        }, {
          "SKU": "SKU-00003"
        }],
        "_experience": {
            "decisioning": {
                "propositions": [{
                    "scope": "<your_mbox>"
                }],
                "propositionEventType": {
                    "display": 1
                }
            }
        }
      }
    });
  </script>
</head>
<body>
  <h1 id="title">Order Confirmation</h1>
  <p>Thank you for your order</p>
</body>
</html>
```

+++

Daarna, leer hoe te [&#x200B; de omzettingsgebeurtenissen van het spoordoel &#x200B;](track-events.md) met het Web SDK van het Platform.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=nl#M463) te posten.

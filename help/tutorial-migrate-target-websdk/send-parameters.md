---
title: Parameters verzenden | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe te om mbox, profiel, en entiteitsparameters naar Adobe Target te verzenden gebruikend het Web SDK van het Experience Platform.
source-git-commit: cc958fdbf438943ba4fd5ca8974a8408b2bf624f
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 0%

---

# Parameters naar doel verzenden met Platform Web SDK

De doelimplementaties verschillen per website vanwege de sitearchitectuur, de zakelijke vereisten en de gebruikte functies. De meeste doelimplementaties bevatten het doorgeven van verschillende parameters voor contextuele informatie, doelgroepen en aanbevelingen voor inhoud.

Laten we een eenvoudige pagina met productdetails en een pagina met orderbevestiging gebruiken om de verschillen tussen de bibliotheken aan te tonen bij het doorgeven van parameters aan Doel.

Stel dat de volgende voorbeeldpagina at.js gebruikt:

<!--Assume the following two example pages using at.js:-->

Productgegevens:

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
        "siteSection": "product details",
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



Bevestiging bestelling:

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


## Overzicht van parametertoewijzing

De parameters van het Doel die op deze twee voorbeeldpagina&#39;s worden gebruikt moeten een beetje verschillend worden verzonden gebruikend het Web SDK van het Platform. Er zijn veelvoudige manieren om parameters tot Doel over te gaan gebruikend at.js:

- Instellen met `targetPageParams()` functie voor de gebeurtenis page load
- Instellen met `targetPageParamsAll()` functie voor alle aanvragen van het Doel op de pagina
- Parameters rechtstreeks verzenden met de `getOffer()` functie voor één locatie
- Parameters rechtstreeks verzenden met de `getOffers()` functie voor een of meer locaties

In dit voorbeeld wordt de `targetPageParams()` wordt gebruikt.

SDK van het Web van het Platform vereenvoudigt dit door één enkele verenigbare manier te verstrekken om gegevens zonder de behoefte aan extra functies te verzenden. Alle parameters moeten in de lading met worden overgegaan `sendEvent` gebruiken.

Parameters die met het Web SDK van het Platform worden overgegaan `sendEvent` de lading valt onder twee categorieën :

1. Automatisch toegewezen via het dialoogvenster `xdm` object
1. Handmatig worden doorgegeven met het gereedschap `data.__adobe.target` object

De lijst hieronder schetst hoe de voorbeeldparameters zouden worden opnieuw in kaart gebracht gebruikend het Web SDK van het Platform:

| Voorbeeld van parameter at.js | Platform Web SDK, optie | Notities |
| --- | --- | --- |
| `at_property` | N.v.t. | Eigenschap-tokens worden geconfigureerd in het dialoogvenster [datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) en kan niet worden ingesteld in het dialoogvenster `sendEvent` vraag. |
| `siteSection` | `xdm.web.webPageDetails.siteSection` | Alle parameters van het Doel moeten als deel van worden overgegaan `xdm` object en conform een schema met de klasse XDM ExperienceEvent. Mbox-parameters kunnen niet worden doorgegeven als onderdeel van de `data` object. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle parameters voor het doelprofiel moeten worden doorgegeven als onderdeel van het dialoogvenster `data` object en vooraf ingesteld met `profile.` op passende wijze in kaart te brengen. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Gereserveerde parameter die wordt gebruikt voor de categorie-affiniteit van het doel en die moet worden doorgegeven als onderdeel van de `data` object. |
| `entity.id` | `data.__adobe.target.entity.id` <br>OF<br> `xdm.productListItems[0].SKU` | Identiteitskaart van de entiteit wordt gebruikt voor het gedrag van Recommendations van het Doel tellers. Deze entiteit-id&#39;s kunnen worden doorgegeven als onderdeel van de `data` object of automatisch toegewezen uit het eerste item in het deelvenster `xdm.productListItems` array als uw implementatie die veldgroep gebruikt. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | ID&#39;s van de categorie Entiteiten kunnen worden doorgegeven als onderdeel van de `data` object. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Parameters voor aangepaste entiteiten worden gebruikt voor het bijwerken van de Recommendations-productcatalogus. Deze aangepaste parameters moeten worden doorgegeven als onderdeel van het dialoogvenster `data` object. |
| `cartIds` | `data.__adobe.target.cartIds` | Wordt gebruikt voor op kaarten gebaseerde aanbevelingen-algoritmen van Target. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wordt gebruikt om te voorkomen dat bepaalde id&#39;s van entiteiten terugkeren in een ontwerp met aanbevelingen. |
| `mbox3rdPartyId` | In de identityMap instellen. Zie [Profielen synchroniseren met een klant-id](#synching-profiles-with-a-customer-id) | Wordt gebruikt voor het synchroniseren van doelprofielen op verschillende apparaten en klantkenmerken. De naamruimte die voor de klant-id moet worden gebruikt, moet worden opgegeven in het dialoogvenster [Doelconfiguratie van de gegevensstroom](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html). |
| `orderId` | `xdm.commerce.order.purchaseID` | Wordt gebruikt voor het identificeren van een unieke volgorde voor het bijhouden van doelconversie. |
| `orderTotal` | `xdm.commerce.order.priceTotal` | Wordt gebruikt voor het bijhouden van ordertotalen voor doelconversie- en optimalisatiedoelstellingen. |
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br>OF<br> `xdm.productListItems[0-n].SKU` | Wordt gebruikt voor het bijhouden van doelconversie en aanbevelingen. Zie de [entiteitsparameters](#entity-parameters) voor meer informatie. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Gebruikt voor de [aangepaste scoring](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) doel van activiteit. |

{style=&quot;table-layout:auto&quot;}

## Aangepaste parameters

Alle aangepaste mbox-parameters moeten als XDM-gegevens worden doorgegeven met de `sendEvent` gebruiken. Het is belangrijk om ervoor te zorgen dat het schema XDM alle gegevenspunten omvat die voor uw implementatie van het Doel worden vereist.

at.js, voorbeeld met `targetPageParams()`:

```JavaScript
targetPageParams = function() {
  return {
    "siteSection": "product detail"
  };
};
```

Platform Web SDK-voorbeeld gebruiken `sendEvent` opdracht:

```JavaScript
alloy("sendEvent", {
  "xdm": {
    "web": {
      "webPageDetails": {
        // Other attributes included according to xdm schema
        "siteSection": "product detail"
      }
    }
  }
});
```

>[!NOTE]
>
>Omdat aangepaste mbox-parameters moeten worden verzonden als onderdeel van `xdm` object in het `sendEvent` bevel, om het even welke mbox parameters die in uw at.js implementatie van het Doel worden gebruikt moeten aan een equivalent XDM worden opnieuw toegewezen. Dit betekent u om het even welk publiek, activiteiten, of profielmanuscripten moet bijwerken die deze mbox parameters van verwijzingen voorzien.


## Profielparameters

Doelprofielparameters moeten worden doorgegeven onder `data.__adobe.target` object in de Web SDK van Platform `sendEvent` opdrachtlading.

Net als bij at.js, moeten alle profielparameters ook vooraf worden ingesteld op `profile.` voor de waarde die correct moet worden opgeslagen als een blijvend doelprofielkenmerk. De gereserveerde `user.categoryId` parameter voor de Categorie-affiniteit van Target is vooraf ingesteld op `user.`.

at.js, voorbeeld met `targetPageParams()`:

```JavaScript
targetPageParams = function() {
  return {
    "profile.gender": "male",
    "user.categoryId": "clothing"
  };
};
```

Platform Web SDK-voorbeeld gebruiken `sendEvent` opdracht:

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

## Parameters entiteit

Entiteitsparameters worden gebruikt om gedragsgegevens en aanvullende catalogusinformatie voor Target Recommendations door te geven. Net als profielparameters moeten alle entiteitsparameters worden doorgegeven onder de `data.__adobe.target` object in de Web SDK van Platform `sendEvent` opdrachtlading.

Entiteitsparameters voor een specifiek item moeten vooraf worden ingesteld met `entity.` voor het correct vastleggen van gegevens. De gereserveerde `cartIds` en `excludedIds` parameters voor aanbevelingen mogen niet worden voorafgegaan door algoritmen en de waarde voor elke parameter moet een door komma&#39;s gescheiden lijst van entiteit-id&#39;s bevatten.

at.js, voorbeeld met `targetPageParams()`:

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

Platform Web SDK-voorbeeld gebruiken `sendEvent` opdracht:

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

Alles [entiteitsparameters](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) gesteund door at.js wordt ook gesteund door het Web SDK van het Platform.

>[!NOTE]
>
>Als de `commerce` de veldgroep wordt gebruikt en `productListItems` -array is opgenomen in de XDM-payload, daarna de eerste `SKU` waarde in deze array wordt toegewezen aan `entity.id` om de productweergave te vergroten.


## Aankoopparameters

De parameters van de aankoop worden overgegaan op een de bevestigingspagina van het orde na een succesvolle orde en voor de omzettings en optimalisatiedoelstellingen van het Doel gebruikt. Met een implementatie van SDK van het Web van het Platform, worden deze parameters en automatisch in kaart gebracht van gegevens XDM die als deel van worden overgegaan `commerce` veldgroep.

at.js, voorbeeld met `targetPageParams()`:

```JavaScript
targetPageParams = function() {
  return {
    "orderId": "ABC123",
    "productPurchasedId": "SKU-00002,SKU-00003"
    "orderTotal": 1337.89
  };
};
```

Aankoopgegevens worden doorgegeven aan Target wanneer de `commerce` veldgroep heeft `puchases.value` instellen op `1`. De bestellings-id en het ordertotaal worden automatisch toegewezen aan de `order` object. Als de `productListItems` array aanwezig is, dan de `SKU` waarden worden gebruikt voor `productPurchasedId`.

Platform Web SDK-voorbeeld gebruiken `sendEvent` opdracht:

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
    }]
  }
});
```

>[!NOTE]
>
>De `productPurchasedId` kan ook worden doorgegeven als een door komma&#39;s gescheiden lijst met id&#39;s van entiteiten onder de `data` object.


## Profielen synchroniseren met een klant-id

Met Doel kunt u met één klant-id synchroniseren tussen apparaten en systemen. Met at.js, kon dit als `mbox3rdPartyId` in het verzoek van het Doel of als eerste klantenidentiteitskaart die naar de Dienst van de Identiteit van Experience Cloud wordt verzonden. In tegenstelling tot at.js, staat een implementatie van SDK van het Web van het Platform u toe om te specificeren welke klant identiteitskaart aan gebruik als `mbox3rdPartyId` als er meerdere zijn. Bijvoorbeeld, als uw zaken een globale klant identiteitskaart en afzonderlijke klant IDs voor verschillende lijnen van zaken hebben, kunt u vormen welk Doel van identiteitskaart zou moeten gebruiken.

Er zijn een paar stappen aan opstellingsidentiteitskaart die voor het dwars-apparaat van het Doel en de het gebruikscituaties van de Attributen van de Klant synchroniseert:

1. Een **[!UICONTROL naamruimte identity]** voor de klant-id in **[!UICONTROL Identiteiten]** scherm van de Inzameling of het Platform van Gegevens
1. Zorg ervoor dat de **[!UICONTROL alias]** in Klantkenmerken komt overeen met de **[!UICONTROL identiteitssymbool]** van uw naamruimte
1. Geef de **[!UICONTROL identy-symbool]** als de **[!UICONTROL Naamruimte derde partij doel]** in de configuratie Doel van de gegevensstroom
1. Een `sendEvent` gebruiken `identityMap` veldgroep

at.js, voorbeeld met `targetPageParams()`:

```JavaScript
targetPageParams = function() {
  return {
    "mbox3rdPartyId": "TT8675309"
  };
};
```

Platform Web SDK-voorbeeld gebruiken `sendEvent` opdracht:

```JavaScript
alloy("sendEvent", {
  "xdm": {
    "identityMap": {
      "GLOBAL_CUSTOMER_ID": [{
        "id": "TT8675309",
        "authenticatedState": "authenticated"
      }]
    }
  }
});
```


## Platform Web SDK-voorbeeld

Nu u begrijpt hoe de verschillende parameters van het Doel gebruikend het Web SDK van het Platform in kaart worden gebracht, zouden onze twee voorbeeldpagina&#39;s van at.js aan het Web SDK van het Platform zoals hieronder getoond kunnen worden gemigreerd. De voorbeeldpagina&#39;s omvatten het volgende:

- Doel voor het vooraf verbergen van een fragment voor een asynchrone bibliotheekimplementatie
- De SDK-basiscode van het Platform Web
- De Platform Web SDK JavaScript-bibliotheek
- A `configure` om de bibliotheek te initialiseren
- A `sendEvent` bevel om gegevens te verzenden en de inhoud van het verzoekDoel te verzoeken om terug te geven

Productgegevens:

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
            "authenticatedState": "authenticated"
          }]
        },
        "web": {
          "webPageDetails": {
            // Other attributes included according to XDM schema
            "siteSection": "product detail"
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


Bevestiging bestelling:

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
            "authenticatedState": "authenticated"
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
        }]
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

Leer nu hoe u [Conversiegebeurtenissen volgen](track-events.md) met het Web SDK van het Platform.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).

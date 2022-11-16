---
title: Een gegevenslaag op een productpagina implementeren
description: Een gegevenslaag op een productpagina implementeren
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: a72011a5-ea9c-45df-a0f3-5eb40bc99d3f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Een gegevenslaag op een productpagina implementeren

Voor dit leerprogramma, zult u de Laag van Gegevens van de Cliënt van Adobe voor een typische e-commercewebsite uitvoeren. Indien u dit nog niet hebt gedaan, gelieve te lezen [Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken](how-to-use-the-adobe-client-data-layer.md) eerst om te begrijpen hoe de Laag van Gegevens van de Cliënt van Adobe werkt.

Laten we aannemen dat de gebruiker door uw producten bladert en op een schuimrol klikt om meer te leren. De gebruiker landt op de detailpagina van het product van de schuimrol.

Hier is de HTML voor uw eenvoudige productdetailpagina:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      // Code will go here.
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

Zoals u misschien hebt opgemerkt, bevindt de `<head>` -tag er is een `<script>` tag. Hier plaatst u uw JavaScript-code. Het is niet nodig om de `<script>` tag binnen `<head>`Als u echter zo snel mogelijk gegevens naar de gegevenslaag duwt, zorgt u ervoor dat de markeerteken deze snel naar Adobe Experience Platform kan verzenden voordat de gebruiker de pagina verlaat.

Binnen de `<script>` tag, begint u met het maken van de `adobeDataLayer` array en vervolgens de juiste gebeurtenis- en gegevensinformatie naar de array verplaatsen. De gegevens zijn in overeenstemming met het XDM-schema [u eerder hebt gemaakt](../configure-the-server/create-a-schema.md).

```js
window.adobeDataLayer = window.adobeDataLayer || [];
window.adobeDataLayer.push({
  "event": "pageViewed",
  "web": {
    "webPageDetails": {
      "name": "Foam Roller",
      "siteSection": "Equipment"
    },
  }
});
window.adobeDataLayer.push({
  "event": "productViewed",
  "productListItems": [
    {
      "SKU": "eqfr08",
      "currencyCode": "USD",
      "name": "Foam Roller",
      "priceTotal": 18.95
    }
  ]
});
```

In dit voorbeeld, hebt u twee duwen aan de gegevenslaag gemaakt, elk die een `event` toets. Met inbegrip van een `event` Met Key wordt niet alleen gemeld welke gebeurtenis op de pagina heeft plaatsgevonden, maar wordt het ook eenvoudiger voor de markering om de juiste regels te maken binnen Adobe Experience Platform-tags.

De eerste duw aan de gegevenslaag deelt luisteraars (de regels van Markeringen) mee dat de gebruiker de pagina heeft bekeken. De paginanaam en de sitesectie worden ook toegevoegd aan de gegevenslaag.

De tweede duw aan de gegevenslaag deelt luisteraars (de regels van Markeringen) mee dat de gebruiker een product heeft bekeken. Het voegt ook productinformatie aan de gegevenslaag toe.

## Toevoegen aan winkelwagentje

U wilt waarschijnlijk ook bijhouden wanneer de gebruiker op de knop [!UICONTROL Toevoegen aan winkelwagentje] knop.

Hiertoe maakt u een functie die wordt aangeroepen wanneer de gebruiker op de knop [!UICONTROL Toevoegen aan winkelwagentje] knop.

```js
window.onAddToCartClick = function() {
  // In a real implementation, you would change this condition to 
  // only pass if a cart doesn't already exist. You would typically 
  // do this by checking a cookie or variable value.
  if (true) {
    window.adobeDataLayer.push({
      "event": "cartOpened",
    });
  }
  window.adobeDataLayer.push({
    "event": "productAddedToCart"
  });
};
```

Wanneer deze functie wordt aangeroepen, controleert deze eerst of er al een winkelwagentje voor een gebruiker bestaat. Dit wordt doorgaans gedaan door te controleren of een bepaalde cookie of variabele bestaat. Als het winkelwagentje niet bestaat, duw je op een `cartOpened` in de gegevenslaag. Daarna duw je op een `productAddedToCart` in de gegevenslaag. De productinformatie bestaat reeds in de gegevenslaag, zodat te hoeven u niet het opnieuw toe te voegen.

Een `onclick` aan de [!UICONTROL Toevoegen aan winkelwagentje] knoop die uw nieuwe roept `onAddToCartClick` functie.

Het resultaat van de pagina HTML moet er als volgt uitzien:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download">Download the app</a>
  </body>
</html>
```

## De app downloaden

Een laatste ding om te doen is volgen wanneer de gebruiker klikt _[!UICONTROL De app downloaden]_ koppeling.

Hiertoe maakt u een functie die wordt aangeroepen wanneer de gebruiker op de knop _[!UICONTROL De app downloaden]_ koppeling.

```js
window.onDownloadAppClick = function(event) {
  window.adobeDataLayer.push({
    "event": "downloadAppClicked",
    "eventInfo": {
      "web": {
        "webInteraction": {
          "URL": "https://example.com/download",
          "name": "App Download",
          "type": "download"
        }
      }
    }
  });
};
```

In dit geval wordt de informatie over de koppeling opgenomen in een `eventInfo` toets. Zoals besproken in [Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken](how-to-use-the-adobe-client-data-layer.md), vertelt dit de gegevenslaag om deze gegevens samen met de gebeurtenis mee te delen, maar aan _niet_ de gegevens in de gegevenslaag behouden. Voor een verbindingsklik, is het niet nuttig om informatie over de geklikte verbinding aan de gegevenslaag toe te voegen omdat het niet tot de pagina als geheel behoort en niet op andere gebeurtenissen van toepassing is die kunnen voorkomen.

Een `onclick` aan de [!UICONTROL De app downloaden] verbinding die uw nieuw roept `onDownloadAppClick` functie.

Het resultaat van de pagina HTML moet er als volgt uitzien:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Product Page</title>
    <script>
      window.adobeDataLayer = window.adobeDataLayer || [];
      window.adobeDataLayer.push({
        "event": "pageViewed",
        "web": {
          "webPageDetails": {
            "name": "Foam Roller",
            "siteSection": "Equipment"
          },
        },
        "productListItems": [
          {
            "SKU": "eqfr08",
            "currencyCode": "USD",
            "name": "Foam Roller",
            "priceTotal": 18.95
          }
        ]
      });
      window.adobeDataLayer.push({
        "event": "productViewed"
      });
      window.onAddToCartClick = function() {
        // In a real implementation, you would change this condition to 
        // only pass if a cart doesn't already exist. You would typically 
        // do this by checking a cookie or variable value.
        if (true) {
          window.adobeDataLayer.push({
            "event": "cartOpened",
          });
        }
        window.adobeDataLayer.push({
          "event": "productAddedToCart"
        });
      };
      window.onDownloadAppClick = function() {
        window.adobeDataLayer.push({
          "event": "downloadAppClicked",
          "eventInfo": {
            "web": {
              "webInteraction": {
                "URL": "https://example.com/download",
                "name": "App Download",
                "type": "download"
              }
            }
          }
        });
      };
    </script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download" onclick="onDownloadAppClick()">Download the app</a>
  </body>
</html>
```

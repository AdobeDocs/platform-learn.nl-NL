---
title: Een gegevenslaag op een productpagina implementeren
description: Een gegevenslaag op een productpagina implementeren
exl-id: 0debf34a-48d4-4029-b790-7fd78865c334
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# Een gegevenslaag op een productpagina implementeren

Voor dit leerprogramma, implementeert u de Laag van Gegevens van de Cliënt van Adobe voor een typische e-commercewebsite. Indien u dit nog niet hebt gedaan, gelieve te lezen [Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken](how-to-use-the-adobe-client-data-layer.md) eerst om de Laag van Gegevens van de Cliënt van Adobe te begrijpen.

Laten we aannemen dat de gebruiker door uw producten bladert en op een schuimrol klikt om meer te leren. De gebruiker landt op de detailpagina van het product van de schuimrol.

## Een eenvoudige pagina met productdetails maken

1. Kopieer en plak de volgende code in een nieuw HTML-bestand en sla dit op uw computer op.

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

Binnen de `<head>` -tag er is een `<script>` tag. Hier plaatst u uw JavaScript-code. Hoewel het niet wordt vereist om te plaatsen `<script>` tag in de `<head>` wordt aanbevolen. Dit zorgt ervoor dat de gegevens zo snel mogelijk beschikbaar zijn in de gegevenslaag om een verscheidenheid aan gebruiksgevallen te ondersteunen.

## De gegevenslaag Adobe toevoegen

1. Binnen de `<script>` -tag, voegt u deze code toe waarmee de `adobeDataLayer` -array en plaatst vervolgens de juiste gebeurtenis- en gegevensinformatie in de array. De gegevens zijn in overeenstemming met het XDM-schema [u eerder hebt gemaakt](../configure-the-server/create-a-schema.md).

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

In dit voorbeeld, hebt u twee duwen aan de gegevenslaag gemaakt, elk die een `event` toets. Met inbegrip van een `event` Met Key wordt niet alleen gemeld welke gebeurtenis op de pagina heeft plaatsgevonden, maar wordt het ook eenvoudiger voor de markering om de juiste regels binnen tags te maken.

De eerste duw aan de gegevenslaag deelt luisteraars (markeringsregels) mee dat de gebruiker de pagina heeft bekeken. De paginanaam en de sitesectie worden ook toegevoegd aan de gegevenslaag.

De tweede duw aan de gegevenslaag meldt luisteraars (markeringen regels) dat de gebruiker een product heeft bekeken. Het voegt ook productinformatie aan de gegevenslaag toe.

## Code toevoegen voor tekstspatiëring toevoegen

Voor deze zelfstudie houdt u bij wanneer de gebruiker op de knop [!UICONTROL Toevoegen aan winkelwagentje] knop.

1. Kopieer en plak deze code na de code voor de gegevenslaag. De functie wordt aangeroepen wanneer de gebruiker op de knop [!UICONTROL Toevoegen aan winkelwagentje] knop.

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

Deze functie controleert eerst of er al een winkelwagentje bestaat voor een gebruiker.  Als het winkelwagentje niet bestaat, drukt u op een `cartOpened` aan de gegevenslaag. Later duw je op een `productAddedToCart` in de gegevenslaag. De productinformatie bestaat reeds in de gegevenslaag, zodat te hoeven u niet het opnieuw toe te voegen.

## Kenmerk toevoegen aan winkelwagentje

1. Een `onclick` aan de [!UICONTROL Toevoegen aan winkelwagentje] knoop die uw nieuwe roept `onAddToCartClick` functie.

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

## Code toevoegen voor het bijhouden van downloads voor apps

Een laatste ding om te volgen is wanneer de gebruiker klikt _[!UICONTROL De app downloaden]_ koppeling.

1. Hiervoor kopieert en plakt u deze code onder het winkelwagentje en voegt u code toe. Deze functie wordt aangeroepen wanneer de gebruiker op de knop _[!UICONTROL De app downloaden]_ koppeling.

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

## Kenmerk toevoegen om toepassingskoppeling te downloaden

1. Een `onclick` aan de [!UICONTROL De app downloaden] verbinding die uw nieuw roept `onDownloadAppClick` functie.

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

[Volgende: ](create-a-tags-property-and-install-extensions.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

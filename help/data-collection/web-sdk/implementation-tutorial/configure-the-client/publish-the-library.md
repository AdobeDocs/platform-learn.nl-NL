---
title: De bibliotheek publiceren
description: De bibliotheek publiceren
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
jira: KT-10447
hide: true
hidefromtoc: true
exl-id: 2fc072df-24f2-4fea-848f-0a973deca2f8
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# De bibliotheek publiceren

Nu is het tijd om de tagbibliotheek op uw website te implementeren.

## Een bibliotheek maken

Eerst moet u een bibliotheek maken die de extensies, regels en gegevenselementen bevat die u hebt gemaakt. Als u een bibliotheek wilt maken, selecteert u [!UICONTROL Publishing Flow] in het linkermenu.

Selecteren [!UICONTROL Bibliotheek toevoegen].

De weergave voor het maken van de bibliotheek wordt weergegeven.

![tagbibliotheek maken](../../../assets/implementation-strategy/tags-library-creation.png)

Geef de bibliotheek een naam, zoals _Demo_. Selecteren [!UICONTROL Ontwikkeling] in de [!UICONTROL Omgeving] vervolgkeuzelijst. Klik vervolgens op [!UICONTROL Alle gewijzigde bronnen toevoegen].

U moet nu al uw extensies, regels en gegevenselementen bekijken die onder [!UICONTROL Bronwijzigingen]. Klikken [!UICONTROL Opslaan en samenstellen tot ontwikkeling].

## Voeg de insluitcode toe aan uw HTML

Nu moet u een scripttag toevoegen aan de HTML van de productpagina die de nieuw gebouwde tagbibliotheek laadt.

Starten door te klikken [!UICONTROL Omgevingen] in het linkermenu. Er moeten drie verschillende omgevingen worden vermeld.

![Labels-omgevingen](../../../assets/implementation-strategy/tags-environments.png)

Klik op het pictogram van het pakket op het tabblad [!UICONTROL Ontwikkeling] omgevingsrij. Instructies voor het installeren van het bibliotheekscript voor Starten op de pagina worden weergegeven.

![Installatie-instructies voor tags](../../../assets/implementation-strategy/tags-installation-instructions.png)

Kopieer de scripttag (er is een knop Kopiëren naar klembord voor het gemak). Open de productpagina HTML en voeg de scripttag in voor de `</head>` tag. Uw laatste HTML moet er als volgt uitzien:

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
    <!--Swap this script tag with your own-->
    <script src="https://assets.adobedtm.com/xxxxxxxxxxxx/xxxxxxxxxxxx/launch-xxxxxxxxxxxx-development.min.js" async></script>
  </head>
  <body>
    <h1>Foam Roller</h1>
    <p>This foam roller is composed of durable material that holds its shape and delivers deep tissue therapy. Purchase now for only $18.95!</p>
    <button type="button" onclick="onAddToCartClick()">Add to cart</button>
    <a href="https://example.com/download" onclick="onDownloadAppClick()">Download the app</a>
  </body>
</html>
```

Kijk uit de [publiceren, documentatie voor tags](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) als u meer wilt weten over het publicatieproces.

Vervolgens test u de nieuwe implementatie!

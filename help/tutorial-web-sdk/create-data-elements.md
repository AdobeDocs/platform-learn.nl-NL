---
title: Gegevenselementen maken voor Platform Web SDK
description: Leer hoe u een XDM-object maakt en er gegevenselementen aan toewijst in tags. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Tags
jira: KT-15401
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
source-git-commit: 070fc02801d3403bf65ca732323338481e25b581
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Gegevenselementen maken

Leer hoe te om gegevenselementen in markeringen voor inhoud, handel, en identiteitsgegevens op de [ de demowebsite van de Luma ](https://luma.enablementadobe.com) tot stand te brengen. Vul vervolgens velden in uw XDM-schema.



## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Begrijp verschillende benaderingen om een gegevenslaag aan XDM in kaart te brengen
* Gegevenselementen maken om gegevens vast te leggen
* Gegevenselementen toewijzen aan een XDM-object


## Vereisten

U hebt inzicht in wat een gegevenslaag is en de vorige lessen in het leerprogramma voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap tag](install-web-sdk.md)


>[!IMPORTANT]
>
>De gegevens voor deze les komen uit de `[!UICONTROL adobeDataLayer]` gegevenslaag op de [ plaats van de Luma ](https://luma.enablementadobe.com). Als u de gegevenslaag wilt weergeven, opent u de ontwikkelaarsconsole en typt u in `[!UICONTROL adobeDataLayer]` om de volledige beschikbare gegevenslaag weer te geven.![ adobeDataLayer gegevenslaag ](assets/data-element-data-layer-new.png)


## Datalaagbenaderingen

Er zijn meerdere manieren om gegevens van uw gegevenslaag toe te wijzen aan XDM gebruikend de markeringsfunctionaliteit van Adobe Experience Platform. Hieronder volgen een paar voor- en nadelen van drie verschillende benaderingen. Indien gewenst kunnen benaderingen worden gecombineerd:

1. XDM in de gegevenslaag implementeren
1. Toewijzen aan XDM in tags
1. Toewijzen aan XDM in de gegevensstroom

>[!NOTE]
>
>De voorbeelden in deze zelfstudie volgen de Tagbenadering Kaart aan XDM.


### XDM in de gegevenslaag implementeren

In deze aanpak implementeren webontwikkelaars een volledig gedefinieerd XDM-object als de structuur voor de gegevenslaag. Vervolgens wijst u gewoon de volledige gegevenslaag toe aan een XDM-object in tags. Als uw implementatie geen markeringsmanager gebruikt, kan deze benadering ideaal zijn omdat u gegevens naar XDM direct van uw toepassing kunt verzenden gebruikend het [ XDM sendEvent bevel ](https://experienceleague.adobe.com/en/docs/experience-platform/edge/fundamentals/tracking-events#sending-xdm-data). Als u wel tags gebruikt, kunt u een aangepast code-gegevenselement maken waarmee de gehele gegevenslaag als een pass-through JSON-object wordt vastgelegd op de XDM. Vervolgens wijst u de pass-through JSON toe aan het XDM-objectveld in de Send Event-handeling.

Hieronder ziet u hoe de gegevenslaag eruit zou zien als u de indeling Adobe Client Data Layer zou gebruiken:

+++XDM in voorbeeld gegevenslaag

```JSON
window.adobeDataLayer.push({
"eventType": "web.webPageDetails.pageViews",
"web":{
         "webInteraction":{
            "linkClicks":{
               "id":"",
               "value":""
            },
            "URL":"",
            "name":"",
            "region":"",
            "type":""
         },
         "webPageDetails":{
            "pageViews":{
               "id":"",
               "value":"1"
            },
            "URL":"https://luma.enablementadobe.com/",
            "isErrorPage":"",
            "isHomePage":"",
            "name":"luma:home",
            "server":"enablementadobe.com",
            "siteSection":"home",
            "viewName":""
         },
         "webReferrer":{
            "URL":"",
            "type":""
         }
      }
});
```

+++

Pros

* Elimineert extra stappen die aan de variabelen van de gegevenslaag opnieuw aan XDM worden toegewezen
* Mogelijk is de implementatie sneller als uw webontwikkelingsteam ook eigenaar is van de codering van digitaal gedrag

Cons

* Volledige afhankelijkheid van ontwikkelingsteam en ontwikkelingscyclus voor het bijwerken van welke gegevens naar XDM gaan
* Beperkte flexibiliteit omdat XDM de exacte lading van de gegevenslaag ontvangt
* Kan ingebouwde tagfuncties, zoals plakken, persistentie, functies voor snelle implementatie niet gebruiken
* Harder om de gegevenslaag voor derdepixel te gebruiken (maar u zou deze pixel aan [ gebeurtenis kunnen willen bewegen door:sturen ](setup-event-forwarding.md)!)
* Kan de gegevens niet transformeren tussen de gegevenslaag en XDM

### Toewijzen aan XDM in tags

Deze benadering omvat het in kaart brengen van individuele gegevenslaagvariabelen aan gegevenselementen in markeringen en uiteindelijk aan XDM. Dit is de traditionele benadering van implementatie gebruikend een systeem van het markeringsbeheer.

#### Pros

* De meest flexibele benadering zoals u individuele variabelen kunt controleren en gegevens omzetten alvorens het XDM krijgt
* Kan Adobe-tagtriggers en -plakfuncties gebruiken om gegevens door te geven aan XDM
* Gegevenselementen kunnen worden toegewezen aan client-side pixels van derden

#### Cons

* Het duurt even om de gegevenslaag te reconstrueren als de elementen van markeringsgegevens


>[!IMPORTANT]
>
>Zoals eerder vermeld, volgen de voorbeelden in deze zelfstudie de optie Toewijzen aan XDM in de tagaanpak.

### Toewijzen aan XDM in de gegevensstroom

Deze benadering gebruikt functionaliteit die in de configuratie van de gegevensstroom [ wordt ingebouwd Prep van Gegevens voor de Inzameling van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/data-prep) en slaat de variabelen van de kaartgegevenslaag aan XDM in markeringen over.

#### Pros

* Flexibele toewijzing van individuele variabelen aan XDM in een punt-en-klik UI
* Capaciteit om [ nieuwe waarden ](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/functions) of [ transformatie gegevenstypes ](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling) van een gegevenslaag gegevens uit te werken alvorens het naar XDM gaat

#### Cons

* Kan gegevenslaagvariabelen niet als gegevenselementen voor cliënt-kant derdepixel gebruiken, maar kan hen gebruiken met gebeurtenis het door:sturen
* Kan de functie voor plakken niet gebruiken in codes
* De complexiteit van onderhoud neemt toe als de gegevenslaag zowel in tags als in gegevensstroom wordt toegewezen


>[!TIP]
>
> Google-gegevenslaag
> 
> Als uw organisatie reeds Google Analytics gebruikt en het traditionele Google dataLayer voorwerp op uw website heeft, kunt u de [ uitbreiding van de Laag van Gegevens van Google ](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/google-data-layer/overview) in markeringen gebruiken. Hierdoor kunt u sneller Adobe-technologie implementeren zonder dat u ondersteuning van uw IT-team nodig hebt. Als u de Google-gegevenslaag toewijst aan XDM, worden dezelfde stappen uitgevoerd als hierboven.


## Gegevenselementen maken om de gegevenslaag vast te leggen

Voordat u XDM-velden vult, legt u eerst de gegevenspunten vast die u nodig hebt als gegevenselementen voor tags:

1. Ga naar **[!UICONTROL Data Elements]** en selecteer **[!UICONTROL Add Data Element]** (of **[!UICONTROL Create New Data Element]** als de eigenschap tag geen bestaande gegevenselementen bevat)

   ![ creeer het Element van Gegevens ](assets/data-element-create.png)

1. Naam van het gegevenselement `Page Name`
1. Gebruik **[!UICONTROL JavaScript Variable]** **[!UICONTROL Data Element type]** om naar de waarde in de gegevenslaag van Luma te wijzen: `adobeDataLayer.0.page.name`

1. Schakel de selectievakjes voor **[!UICONTROL Force lowercase value]** en **[!UICONTROL Clean text]** in om het hoofdlettergebruik te standaardiseren en overbodige spaties te verwijderen

1. Laat `None` staan als de instelling **[!UICONTROL Storage Duration]** omdat deze waarde op elke pagina anders is

1. Selecteren **[!UICONTROL Save]**

   ![ het Element van Gegevens van de Naam van de Pagina ](assets/data-element-pageName.png)

Maak deze aanvullende gegevenselementen door dezelfde stappen uit te voeren:

* **`User Id`** toegewezen aan
  `adobeDataLayer.0.user.id`

* **`User Logged In`** toegewezen aan
  `adobeDataLayer.0.user.loggedIn`

* **`Ecommerce Product Id`** toegewezen aan `adobeDataLayer.0.ecommerce.detail.products.0.id`
* **`Ecommerce Product Name`** toegewezen aan `adobeDataLayer.0.ecommerce.detail.products.0.name`
* **`Ecommerce Purchase Id`** toegewezen aan `adobeDataLayer.0.ecommerce.purchase.actionField.id`
* **`Ecommerce Product Category`** gebruiken van **[!UICONTROL Custom Code]** **[!UICONTROL Data Element type]** en de volgende douanecode:

  ```javascript
  return adobeDataLayer[0].ecommerce.detail.products[0].category+":"+adobeDataLayer[0].ecommerce.detail.products[0].subcategory;
  ```

* **`Ecommerce Cart Products`** gebruiken van de volgende douanecode:

  ```javascript
  const cartProducts = adobeDataLayer
  .flatMap(evt => Array.isArray(evt?.ecommerce?.cart?.items) ? evt.ecommerce.cart.items : [])
  .filter(item => item && item.id && item.name && item.brand)
  .map(({ id, name, brand }) => ({ id, name, brand }));
  
  return cartProducts;
  ```

* **`Ecommerce Purchase Products`** gebruiken van de volgende douanecode:

  ```javascript
  const purchaseEvent = adobeDataLayer.find(e => e.event === "purchase");
  
  const currencyCode = purchaseEvent?.ecommerce?.currencyCode ?? "USD";
  
  const purchasedProducts = (purchaseEvent?.ecommerce?.purchase?.products || []).map(p => {
     const unitPrice = parseFloat(String(p.price).replace(/[^0-9.-]/g, "")) || 0;
     const qty = Number(p.quantity) || 0;
  
     return {
     SKU: p.id,                       // id -> SKU
     name: p.name,                    // name -> name
     quantity: qty,                   // quantity -> quantity
     priceTotal: unitPrice * qty,     // price -> priceTotal (unit price × quantity)
     currencyCode                     // "USD" -> currencyCode (from ecommerce.currencyCode)
     };
  });
  
  return(purchasedProducts);
  ```


>[!CAUTION]
>
>Het [!UICONTROL JavaScript variable] type van gegevenselement behandelt serieverwijzingen als punten in plaats van haakjes, zodat zal het van verwijzingen voorzien van het element van gebruikersnaamelementen zoals `adobeDataLayer[0].page.name` **niet** werken.

## Variabele-gegevenselementen maken voor XDM- en gegevensobjecten

De gegevenselementen u enkel creeerde zullen worden gebruikt om een voorwerp XDM (voor de toepassingen van het Platform) en een gegevensvoorwerp (voor Analytics, Doel, en Audience Manager) te bouwen. Deze objecten hebben hun eigen speciale gegevenselementen, **[!UICONTROL Variable]** gegevenselementen, die u heel gemakkelijk kunt maken.

Om het Variabele gegevenselement voor XDM tot stand te brengen, koppelt u het aan het schema u in [ creeerde vormt een schema ](configure-schemas.md) les:

1. Selecteren **[!UICONTROL Add Data element]**
1. Geef uw gegevenselement een naam `XDM Variable`. Het wordt aanbevolen om de gegevenselementen die specifiek zijn voor XDM, vooraf in te stellen op &quot;XDM&quot; om de eigenschap tag beter te organiseren
1. Selecteer **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Extension]**
1. Selecteer **[!UICONTROL Variable]** als **[!UICONTROL Data Element Type]**
1. Selecteer **[!UICONTROL XDM]** als de **[!UICONTROL property]**
1. Selecteer de **[!UICONTROL Sandbox]** waarin u het schema hebt gemaakt
1. Selecteer in dit geval de juiste **[!UICONTROL Schema]** `Luma Web Event Data` .
1. Selecteren **[!UICONTROL Save]**

   ![ Variabel gegevenselement voor XDM ](assets/analytics-tags-data-element-xdm-variable.png)

Maak vervolgens het gegevenselement Variabele voor het gegevensobject:

1. Selecteren **[!UICONTROL Add Data element]**
1. Geef uw gegevenselement een naam `Data Variable`.
1. Selecteer **[!UICONTROL Adobe Experience Platform Web SDK]** als **[!UICONTROL Extension]**
1. Selecteer **[!UICONTROL Variable]** als **[!UICONTROL Data Element Type]**
1. Selecteer **[!UICONTROL data]** als de **[!UICONTROL property]**
1. Selecteer de Experience Cloud-oplossingen die u wilt implementeren als onderdeel van deze zelfstudie
1. Selecteren **[!UICONTROL Save]**

   ![ Variabel gegevenselement voor gegevensvoorwerp ](assets/data-element-data-variable.png)


Aan het einde van deze stappen moeten de volgende gegevenselementen worden gemaakt:

| Core Extension Data Elements | Platform Web SDK Extension Data Elements |
| ----------------------------- | ------------------------------- |
| `Ecommerce Cart Products` | `Data Variable` |
| `Ecommerce Product Category` | `XDM Variable` |
| `Ecommerce Product Id` | |
| `Ecommerce Product Name` | |
| `Ecommerce Purchase Id` | |
| `Ecommerce Purchase Products` | |
| `Page Name` | |
| `User Id` | |
| `User Logged In` | |

Met deze gegevenselementen op zijn plaats, bent u bereid om gegevens naar Platform Edge Network met een markeringsregel te beginnen verzenden. Maar eerst, leer over het verzamelen van identiteiten met Web SDK.

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van Experience League te delen ](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)

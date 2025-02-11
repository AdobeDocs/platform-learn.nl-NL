---
title: Parameters verzenden - Migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie beslissen
description: Leer hoe u parameters mbox, profile en entity naar Adobe Target verzendt met Experience Platform Web SDK.
exl-id: 927d83f9-c019-4a6b-abef-21054ce0991b
source-git-commit: 314f0279ae445f970d78511d3e2907afb9307d67
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Parameters naar doel verzenden met de extensie Adobe Journey Optimizer - Mobiele beslissingen nemen

De doelimplementaties verschillen per website vanwege de sitearchitectuur, de zakelijke vereisten en de gebruikte functies. De meeste doelimplementaties bevatten het doorgeven van verschillende parameters voor contextuele informatie, doelgroepen en aanbevelingen voor inhoud.

Met de extensie Doel zijn alle doelparameters doorgegeven via de functie `TargetParameters` .

Met de extensie Decisioning:

* Parameters die bestemd zijn voor meerdere Adobe-toepassingen kunnen worden doorgegeven in het XDM-object
* Parameters die alleen voor Doel zijn bedoeld, kunnen worden doorgegeven in het object `data.__adobe.target`


>[!IMPORTANT]
>
> Met de uitbreiding van het Besluit, zijn de parameters die in een verzoek worden verzonden op alle werkingsgebied in het verzoek van toepassing. Als u verschillende parameters voor verschillende werkingsgebieden moet plaatsen, moet u extra verzoeken doen.

## Aangepaste parameters

Aangepaste mbox-parameters zijn de eenvoudigste manier om gegevens door te geven aan Target en kunnen worden doorgegeven in de XDM- of `data.__adobe.target` -objecten.

## Profielparameters

Profielparameters slaan gegevens gedurende een langere periode op in het doelprofiel van de gebruiker en moeten worden doorgegeven in het `data.__adobe.target` -object.

## Parameters entiteit

[ de parameters van de Entiteit ](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) worden gebruikt om gedragsgegevens en aanvullende catalogusinformatie voor de Aanbevelingen van het Doel over te gaan. Net als profielparameters moeten alle entiteitsparameters onder het `data.__adobe.target` -object worden doorgegeven.

Entiteiteits-parameters voor een specifiek item moeten vooraf met `entity.` worden vastgelegd om de gegevens correct vast te leggen. De gereserveerde `cartIds` - en `excludedIds` -parameters voor aanbevelingen-algoritmen mogen niet vooraf worden ingesteld en de waarde voor beide moet een door komma&#39;s gescheiden lijst met entiteit-id&#39;s bevatten.

## Aankoopparameters

De parameters van de aankoop worden overgegaan op een de bevestigingspagina van het orde na een succesvolle orde en voor de omzettings en optimalisatiedoelstellingen van het Doel gebruikt. Met een Platform Mobile SDK-implementatie die de extensie Decisioning gebruikt, worden deze parameters en automatisch toegewezen aan XDM-gegevens die worden doorgegeven als onderdeel van de veldgroep `commerce` .

Aankoopgegevens worden doorgegeven aan Target wanneer voor de veldgroep `commerce` `purchases.value` is ingesteld op `1` . De bestellings-id en het totaal van de bestellingen worden automatisch toegewezen aan het `order` -object. Als de array `productListItems` aanwezig is, worden de waarden `SKU` gebruikt voor `productPurchasedId` .

Als u geen `commerce` -velden doorgeeft in het XDM-object, kunt u de ordergegevens doorgeven om als doel in te stellen met de velden `data.__adobe.target.orderId` , `data.__adobe.target.orderTotal` en `data.__adobe.target.productPurchasedId` .

## Klant-id (mbox3rdPartyId)

Met Doel is het synchroniseren van profielen tussen apparaten en systemen mogelijk met één id van de klant. Deze klant-id moet worden doorgegeven in het veld `identityMap` van het XDM-object en worden toegewezen aan het veld Id van derde doelpartij in de gegevensstroom.

## Tabel

| Voorbeeld van parameter at.js | Platform Web SDK, optie | Notities |
| --- | --- | --- |
| `at_property` | N.v.t. | De tokens van het bezit worden gevormd in [ datastream ](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) en kunnen niet in de `sendEvent` vraag worden geplaatst. |
| `pageName` | `xdm.web.webPageDetails.name` | Alle parameters van Target mbox moeten worden doorgegeven als onderdeel van het `xdm` -object en moeten in overeenstemming zijn met een schema met behulp van de XDM ExperienceEvent-klasse. Mbox-parameters kunnen niet worden doorgegeven als onderdeel van het `data` -object. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle parameters van het doelprofiel moeten worden doorgegeven als onderdeel van het `data` -object en vooraf ingesteld met `profile.` om correct te worden toegewezen. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Gereserveerde parameter die wordt gebruikt voor de functie Categorie-affiniteit van Doel die moet worden doorgegeven als onderdeel van het `data` -object. |
| `entity.id` | `data.__adobe.target.entity.id` <br> OF <br> `xdm.productListItems[0].SKU` | Identiteitskaart van de entiteit wordt gebruikt voor het gedrag van tellers van de Aanbevelingen van het Doel. Deze entiteit-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object of automatisch worden toegewezen vanuit het eerste item in de `xdm.productListItems` -array als die veldgroep door de implementatie wordt gebruikt. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Identiteitscategorie-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | De parameters van de douaneentiteit worden gebruikt voor het bijwerken van de het productcatalogus van Aanbevelingen. Deze aangepaste parameters moeten worden doorgegeven als onderdeel van het object `data` . |
| `cartIds` | `data.__adobe.target.cartIds` | Wordt gebruikt voor op kaarten gebaseerde aanbevelingen-algoritmen van Target. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wordt gebruikt om te voorkomen dat bepaalde id&#39;s van entiteiten terugkeren in een ontwerp met aanbevelingen. |
| `mbox3rdPartyId` | Instellen in het object `xdm.identityMap` | Wordt gebruikt voor het synchroniseren van doelprofielen op verschillende apparaten en klantkenmerken. Namespace voor klantidentiteitskaart te gebruiken moet in de [ configuratie van het Doel van de datastream ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html) worden gespecificeerd. |
| `orderId` | `xdm.commerce.order.purchaseID`<br> (wanneer `commerce.purchases.value` is ingesteld op `1` ) | Wordt gebruikt voor het identificeren van een unieke volgorde voor het bijhouden van doelconversie. |
| `orderTotal` | `xdm.commerce.order.priceTotal`<br> (wanneer `commerce.purchases.value` is ingesteld op `1` ) | Wordt gebruikt voor het bijhouden van ordertotalen voor doelconversie- en optimalisatiedoelstellingen. |
| `productPurchasedId` | `xdm.productListItems[0-n].SKU`<br> (wanneer `commerce.purchases.value` aan `1` wordt geplaatst) <br> OF <br> `data.__adobe.target.productPurchasedId` | Wordt gebruikt voor het bijhouden van doelconversie en aanbevelingen. Verwijs naar de [ sectie van entiteitparameters ](#entity-parameters) hieronder voor details. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Gebruikt voor het [ douane die ](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) activiteitendoel scoren. |

{style="table-layout:auto"}


## Voorbeelden van parameters doorgeven

Gebruik een eenvoudig voorbeeld om de verschillen tussen de uitbreidingen aan te tonen wanneer het overgaan van parameters aan Doel.

### Android

>[!BEGINTABS]

>[!TAB  Doel SDK ]

```Java
Map<String, String> mboxParameters = new HashMap<String, String>();
mboxParameters1.put("status", "platinum");
 
Map<String, String> profileParameters = new HashMap<String, String>();
profileParameters1.put("gender", "male");
 
List<String> purchasedProductIds = new ArrayList<String>();
purchasedProductIds.add("ppId1");
TargetOrder targetOrder = new TargetOrder("id1", 1.0, purchasedProductIds);
 
TargetProduct targetProduct = new TargetProduct("pId1", "cId1");
 
TargetParameters targetParameters = new TargetParameters.Builder()
                                    .parameters(mboxParameters)
                                    .profileParameters(profileParameters)
                                    .product(targetProduct)
                                    .order(targetOrder)
                                    .build();
```

>[!ENDTABS]

### iOS

>[!BEGINTABS]

>[!TAB  Doel SDK ]

```Swift
let mboxParameters = [
                        "status": "platinum"
                     ]
 
let profileParameters = [
                            "gender": "male"
                        ]
 
let order = TargetOrder(id: "id1", total: 1.0, purchasedProductIds: ["ppId1"])
 
let product = TargetProduct(productId: "pId1", categoryId: "cId1")
 
let targetParameters = TargetParameters(parameters: mboxParameters, profileParameters: profileParameters, order: order, product: product))
```


>[!ENDTABS]






Daarna, leer hoe te [ de omzettingsgebeurtenissen van het spoordoel ](track-events.md) met het Web SDK van het Platform.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

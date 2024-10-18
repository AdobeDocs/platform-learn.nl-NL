---
title: Parameters verzenden - Migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie beslissen
description: Leer hoe te om mbox, profiel, en entiteitsparameters naar Adobe Target te verzenden gebruikend het Web SDK van het Experience Platform.
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Parameters naar doel verzenden met de extensie Adobe Journey Optimizer - Mobiele beslissingen nemen

De doelimplementaties verschillen per website vanwege de sitearchitectuur, de zakelijke vereisten en de gebruikte functies. De meeste doelimplementaties bevatten het doorgeven van verschillende parameters voor contextuele informatie, doelgroepen en aanbevelingen voor inhoud.

Laten we een eenvoudige pagina met productdetails en een pagina met orderbevestiging gebruiken om de verschillen tussen de extensies aan te tonen wanneer we parameters aan Target doorgeven.


| Voorbeeld van parameter at.js | Platform Web SDK, optie | Notities |
| --- | --- | --- |
| `at_property` | N.v.t. | De tokens van het bezit worden gevormd in [ datastream ](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) en kunnen niet in de `sendEvent` vraag worden geplaatst. |
| `pageName` | `xdm.web.webPageDetails.name` | Alle parameters van Target mbox moeten worden doorgegeven als onderdeel van het `xdm` -object en moeten in overeenstemming zijn met een schema met behulp van de XDM ExperienceEvent-klasse. Mbox-parameters kunnen niet worden doorgegeven als onderdeel van het `data` -object. |
| `profile.gender` | `data.__adobe.target.profile.gender` | Alle parameters van het doelprofiel moeten worden doorgegeven als onderdeel van het `data` -object en vooraf ingesteld met `profile.` om correct te worden toegewezen. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Gereserveerde parameter die wordt gebruikt voor de functie Categorie-affiniteit van Doel die moet worden doorgegeven als onderdeel van het `data` -object. |
| `entity.id` | `data.__adobe.target.entity.id` <br> OF <br> `xdm.productListItems[0].SKU` | Identiteitskaart van de entiteit wordt gebruikt voor het gedrag van Recommendations van het Doel tellers. Deze entiteit-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object of automatisch worden toegewezen vanuit het eerste item in de `xdm.productListItems` -array als die veldgroep door de implementatie wordt gebruikt. |
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Identiteitscategorie-id&#39;s kunnen worden doorgegeven als onderdeel van het `data` -object. |
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Parameters voor aangepaste entiteiten worden gebruikt voor het bijwerken van de Recommendations-productcatalogus. Deze aangepaste parameters moeten worden doorgegeven als onderdeel van het object `data` . |
| `cartIds` | `data.__adobe.target.cartIds` | Wordt gebruikt voor op kaarten gebaseerde aanbevelingen-algoritmen van Target. |
| `excludedIds` | `data.__adobe.target.excludedIds` | Wordt gebruikt om te voorkomen dat bepaalde id&#39;s van entiteiten terugkeren in een ontwerp met aanbevelingen. |
| `mbox3rdPartyId` | Instellen in het object `xdm.identityMap` | Wordt gebruikt voor het synchroniseren van doelprofielen op verschillende apparaten en klantkenmerken. Namespace voor klantidentiteitskaart te gebruiken moet in de [ configuratie van het Doel van de datastream ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html) worden gespecificeerd. |
| `orderId` | `xdm.commerce.order.purchaseID` | Wordt gebruikt voor het identificeren van een unieke volgorde voor het bijhouden van doelconversie. |
| `orderTotal` | `xdm.commerce.order.priceTotal` | Wordt gebruikt voor het bijhouden van ordertotalen voor doelconversie- en optimalisatiedoelstellingen. |
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br> OF <br> `xdm.productListItems[0-n].SKU` | Wordt gebruikt voor het bijhouden van doelconversie en aanbevelingen. Verwijs naar de [ sectie van entiteitparameters ](#entity-parameters) hieronder voor details. |
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Gebruikt voor het [ douane die ](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) activiteitendoel scoren. |

{style="table-layout:auto"}

## Aangepaste parameters

Aangepaste mbox-parameters moeten als XDM worden doorgegeven of het gegevensobject met de opdracht `sendEvent` gebruiken. Het is belangrijk om ervoor te zorgen dat het schema XDM alle gebieden omvat die voor uw implementatie van het Doel worden vereist.


## Profielparameters

Parameters voor het doelprofiel moeten worden doorgegeven...

## Parameters entiteit

Entiteitsparameters worden gebruikt om gedragsgegevens en aanvullende catalogusinformatie voor Target Recommendations door te geven. Alle [ entiteitparameters ](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) die door at.js worden gesteund worden ook gesteund door het Web SDK van het Platform. Net als profielparameters moeten alle entiteitsparameters worden doorgegeven onder het `data.__adobe.target` -object in de opdrachtpayload van de opdracht Platform Web SDK `sendEvent` .

Entiteiteits-parameters voor een specifiek item moeten vooraf met `entity.` worden vastgelegd om de gegevens correct vast te leggen. De gereserveerde `cartIds` - en `excludedIds` -parameters voor aanbevelingen-algoritmen mogen niet vooraf worden ingesteld en de waarde voor beide moet een door komma&#39;s gescheiden lijst met entiteit-id&#39;s bevatten.



## Aankoopparameters

De parameters van de aankoop worden overgegaan op een de bevestigingspagina van het orde na een succesvolle orde en voor de omzettings en optimalisatiedoelstellingen van het Doel gebruikt. Met een Platform Mobile SDK-implementatie die de extensie Decisioning gebruikt, worden deze parameters en automatisch toegewezen aan XDM-gegevens die worden doorgegeven als onderdeel van de veldgroep `commerce` .


Aankoopgegevens worden doorgegeven aan Target wanneer voor de veldgroep `commerce` `purchases.value` is ingesteld op `1` . De bestellings-id en het totaal van de bestellingen worden automatisch toegewezen aan het `order` -object. Als de array `productListItems` aanwezig is, worden de waarden `SKU` gebruikt voor `productPurchasedId` .


## Klant-id (mbox3rdPartyId)

Het doel staat profielsynchronisatie over apparaten en systemen toe gebruikend één enkele klant ID.



Daarna, leer hoe te [ de omzettingsgebeurtenissen van het spoordoel ](track-events.md) met het Web SDK van het Platform.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

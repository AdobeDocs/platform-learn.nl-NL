---
title: Vergelijking van de extensie Doel met de extensie Optimaliseren
description: Leer over de verschillen tussen at.js 2.x en het Web SDK van het Platform met inbegrip van eigenschappen, functies, montages, en gegevensstroom.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Vergelijking van de extensie Doel met de extensie Optimaliseren

De zelfstandige Adobe Target at.js-bibliotheek verschilt aanzienlijk van Platform Web SDK. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie at.js, zou u het volgende moeten kunnen begrijpen:

- Welke eigenschappen van het Doel door het Web SDK van het Platform worden gesteund
- Welke functies at.js hebben de equivalenten van SDK van het Web van het Platform
- Hoe de montages van het Doel met het Web SDK van het Platform worden toegepast
- Hoe de gegevensstroom van at.js en het Web SDK van het Platform verschillen

Als u aan het Web SDK van het Platform nieuw bent, maak u geen zorgen - de punten hieronder zijn behandeld meer in detail door dit leerprogramma.

## Functievergelijking

| | Doelextensie | Extensie optimaliseren (Doel via Edge) | AJO Code-based Ervaringen (Berichten SDK) |
|---|---|---|---|
| Prefetmodus | Ondersteund | Ondersteund | Ondersteund |
| Uitvoeren, modus | Ondersteund | Niet ondersteund | Niet ondersteund |
| Aangepaste parameters | Ondersteund | Parameters per box worden niet ondersteund | Niet ondersteund |
| Toegangspubliek | Ondersteund | Ondersteund | Ondersteund via het campagnepubliek en holdout-instellingen voor experimenten |
| Segmentering van het publiek met meetgegevens van mobiele levenscyclus | Ondersteund | Ondersteund via regels voor gegevensverzameling | Gericht op ervaring wordt momenteel niet ondersteund |
| thirdPartyId (mbox3rdPartyId) | Ondersteund via Identity Map- en namespace-configuratie in de gegevensstroom | Niet ondersteund |
| Meldingen (weergeven, klikken) | Ondersteund | Ondersteund | Ondersteund |
| Reactietokens | Ondersteund | Ondersteund | Geen equivalent voor het retourneren van specifieke metagegevens voor campagne buiten de inhoud |
| Dynamische aanbiedingen | Ondersteund | Ondersteund | De symbolische weergave van profiel- en beslissingsitems in inhoud wordt ondersteund |
| Analyses voor doel (A4T) | Alleen client | Client en server | Niet ondersteund |
| Mobiele voorvertoningen (QA-modus) | Ondersteund | Beperkte ondersteuning | In uitvoering |



## Aanbiedingswaardige callouts

>[!NOTE]
>
>Migrating Target to Platform Web SDK while keeping an existing AppMeasurement Adobe Analytics implementation for a given page is not supported.
>
> Het is mogelijk om uw implementatie at.js (en AppMeasurement.js) aan het Web SDK van het Platform één pagina tegelijk te migreren. Als u deze benadering gebruikt, is het best om [`idMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) en [`targetMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) opties aan `true` met het `configure` bevel te plaatsen.

## Doelextensiefuncties en equivalente extensies optimaliseren

Veel functies voor doelextensies hebben een equivalente aanpak met de extensie Optimaliseren die in de onderstaande tabel wordt beschreven. Voor meer details over de [ functies ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), verwijs naar de Gids van de Ontwikkelaar van Adobe Target.

| Doelextensie | Extensie optimaliseren |
| --- | --- | 
| |  |

## Instellingen voor doelextensies en equivalente extensies optimaliseren

De uitbreiding van het Doel kan met diverse montages in worden gevormd en worden gedownload...

| Doelextensie | Extensie optimaliseren |
| --- | --- | 
| |  |


## Vergelijking systeemdiagram

De volgende diagrammen zouden u moeten helpen de verschillen van de gegevensstroom tussen een implementatie van het Doel begrijpen gebruikend at.js en een implementatie gebruikend het Web SDK van het Platform.

### Doeluitbreidingssysteemdiagram



### Het diagram van het extensiesysteem optimaliseren




>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de extensie Doel naar de extensie Optimaliseren. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

---
title: Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding
description: Leer over de verschillen tussen de uitbreiding van het Doel aan de uitbreiding van het Besluit met inbegrip van eigenschappen, functies, montages, en gegevensstroom.
source-git-commit: e727fbfc82dea9ab6244b669b2f06c47987db1b1
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding

De Adobe Journey Optimizer - beslissingsextensie verschilt van de Adobe Target-extensie voor mobiele apps. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie van de uitbreiding van het Doel, zou u het volgende moeten kunnen begrijpen:

- Welke doelfuncties door Adobe Journey Optimizer worden ondersteund - Beslissing
- Welke Adobe Target-extensiefuncties hebben Adobe Journey Optimizer-beslissingsequivalenten
- Hoe de montages van het Doel met Adobe Journey Optimizer worden toegepast - Beslissing
- De verschillen in de gegevensstroom van de Adobe Target-extensie en de Adobe Journey Optimizer-beslissingsextensie

Als u aan het Web SDK van het Platform nieuw bent, maak u geen zorgen - de punten hieronder zijn behandeld meer in detail door dit leerprogramma.

## Functievergelijking

| | Doelextensie | Decisioning-extensie (Doel via Edge) |
|---|---|---|---|
| Prefetmodus | Ondersteund | Ondersteund |
| Uitvoeren, modus | Ondersteund | Niet ondersteund |
| Aangepaste parameters | Ondersteund | Parameters per box worden niet ondersteund |
| Toegangspubliek | Ondersteund | Ondersteund |
| Segmentering van het publiek met meetgegevens van mobiele levenscyclus | Ondersteund | Ondersteund via regels voor gegevensverzameling |
| thirdPartyId (mbox3rdPartyId) | Ondersteund via Identity Map- en namespace-configuratie in de gegevensstroom |
| Meldingen (weergeven, klikken) | Ondersteund | Ondersteund |
| Reactietokens | Ondersteund | Ondersteund |
| Dynamische aanbiedingen | Ondersteund | Ondersteund |
| Analyses voor doel (A4T) | Alleen client | Client en server |
| Mobiele voorvertoningen (QA-modus) | Ondersteund | Beperkte ondersteuning |



## Aanbiedingswaardige callouts

>[!NOTE]
>
>Migrating Target to Platform Web SDK while keeping an existing AppMeasurement Adobe Analytics implementation for a given page is not supported.
>
> Het is mogelijk om uw implementatie at.js (en AppMeasurement.js) aan het Web SDK van het Platform één pagina tegelijk te migreren. Als u deze benadering gebruikt, is het best om [`idMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) en [`targetMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) opties aan `true` met het `configure` bevel te plaatsen.

## Doelextensiefuncties en equivalente beslissingsextensies

Vele functies van de uitbreiding van het Doel hebben een gelijkwaardige benadering gebruikend de uitbreiding van het Besluit die in de lijst hieronder wordt geschetst. Voor meer details over de [ functies ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), verwijs naar de Gids van de Ontwikkelaar van Adobe Target.

| Doelextensie | Decisitie-extensie |
| --- | --- | 
| |  |

## Instellingen voor doelextensies en equivalente beslissingsextensies

De uitbreiding van het Doel kan met diverse montages in worden gevormd en worden gedownload...

| Doelextensie | Decisitie-extensie |
| --- | --- | 
| |  |


## Vergelijking systeemdiagram

De volgende diagrammen zouden u moeten helpen de verschillen van de gegevensstroom tussen een implementatie van het Doel begrijpen gebruikend Adobe Journey Optimizer - beslissende uitbreiding en een implementatie gebruikend de uitbreiding van Adobe Target.

### Doeluitbreidingssysteemdiagram



### Schema voor extensiesysteem voor besluitvorming




>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

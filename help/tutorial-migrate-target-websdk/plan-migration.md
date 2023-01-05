---
title: Planning | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u uw Adobe Target-implementatie kunt plannen van at.js 2.x naar Adobe Experience Platform Web SDK.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Plan de migratie van at.js aan het Web SDK van het Platform

Alvorens aan het Web SDK van het Platform op uw plaats te bevorderen, zou u uw huidige implementatie moeten beoordelen.

## Huidige implementatie van at.js evalueren

De eerste stap naar een geslaagde migratie is een duidelijk inzicht te krijgen in uw huidige implementatie van at.js Target. Er zijn eigenschappen, functies, en douanecode u kunt gebruiken die updates vereisen. Houd rekening met het volgende als u dit beoordeelt:

### Welke functies worden ondersteund?

SDK van het Web van het Platform is onder ononderbroken actieve ontwikkeling en de eigenschappen en de verhogingen worden regelmatig toegevoegd. Als u uw huidige implementatie at.js evalueert, raadpleegt u de [ondersteunde gebruiksgevallen](https://github.com/orgs/adobe/projects/18/views/1) voor de meest recente informatie.

### Welke functies gebruikt u vandaag?

SDK van het Web van het Platform is een nieuwe bibliotheek die alle oplossingen van de Adobe voor de websites in één enkele SDK consolideert. Dit maakt een nauwere integratie mogelijk en maakt nieuwe mogelijkheden mogelijk die uniek zijn voor Adobe Experience Platform. Nochtans, betekent dit ook functies at.js niet achterwaarts compatibel compatibel met het Web SDK van het Platform zijn. Let op het volgende terwijl u de huidige implementatie evalueert:

- at.js-functies zoals `getOffer()` en `applyOffer()`
- Wijzigingen in de algemene instellingen van Target
- Integratie met Adobe Analytics
- Gebruik van een flikkeronderdrukkingsscript
- Gebruik van reactietokens
- Het gebruik van mbox-, profiel- en entiteitsparameters
- Aangepaste code die uniek is voor uw implementatie

### Welke migratiebenadering gaat u kiezen?

Zodra u uw implementatie at.js hebt herzien, moet u een migratiebenadering bepalen. Er zijn twee opties:

- Alle Adobe-toepassingen tegelijk migreren op de gehele site
- Per pagina migreren

Omdat het Web SDK van het Platform veelvoudige toepassingen van Adobe combineert en toelaat, moet u de migratie van het Doel van andere toepassingen van Adobe zoals Analytics en Audience Manager coördineren. Alle Adobe-bibliotheken op een bepaalde pagina moeten tegelijkertijd worden gemigreerd. Een gemengde implementatie van Platform Web SDK voor Doel en AppMeasurement voor Analytics op een bepaalde pagina wordt niet gesteund. Nochtans, wordt een gemengde implementatie over verschillende pagina&#39;s gesteund, bijvoorbeeld het Web SDK van het Platform op pagina A, en at.js met AppMeasurement op pagina B.

Tijdens het migreren moet u het proces van uw bedrijf volgen om nieuwe code te testen en vrij te geven en om zaken zoals ontwikkeling, qa, en het opvoeren milieu&#39;s te gebruiken alvorens u aan productie vrijgeeft.

>[!CAUTION]
>
>Aanbiedingen doorsturen wordt niet ondersteund voor migraties van pagina voor pagina als de omleiding plaatsvindt van een pagina met één bibliotheek naar een pagina met een andere bibliotheek


Controleer vervolgens de gedetailleerde [vergelijking van at.js met het Web SDK van het Platform](detailed-comparison.md) een beter inzicht te krijgen in de technische verschillen en gebieden aan te wijzen die extra aandacht behoeven .

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).

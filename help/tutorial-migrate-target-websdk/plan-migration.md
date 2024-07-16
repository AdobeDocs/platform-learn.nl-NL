---
title: Planning | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u uw Adobe Target-implementatie kunt plannen van at.js 2.x naar Adobe Experience Platform Web SDK.
exl-id: 0e8f9cde-f361-4f69-886d-aad3074cd9b2
source-git-commit: 4690d41f92c83fe17eda588538d397ae1fa28af0
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# De migratie van at.js naar Platform Web SDK plannen

Voordat u een upgrade uitvoert naar de Platform Web SDK op uw site, moet u uw huidige implementatie beoordelen.

## Huidige implementatie van at.js evalueren

De eerste stap naar een geslaagde migratie is een duidelijk inzicht te krijgen in uw huidige implementatie van at.js Target. Er zijn eigenschappen, functies, en douanecode u kunt gebruiken die updates vereisen. Houd rekening met het volgende als u dit beoordeelt:

### Welke functies worden ondersteund?

De SDK van het Web van het platform is onder ononderbroken actieve ontwikkeling en de eigenschappen en de verhogingen worden regelmatig toegevoegd. Aangezien u uw huidige implementatie at.js evalueert, verwijs naar de [ gesteunde gebruikscase ](https://github.com/orgs/adobe/projects/18/views/1) pagina voor de recentste informatie.

### Welke functies gebruikt u vandaag?

Platform Web SDK is een nieuwe bibliotheek die alle oplossingen van de Adobe voor de websites in één enkele SDK consolideert. Dit maakt een nauwere integratie mogelijk en maakt nieuwe mogelijkheden mogelijk die uniek zijn voor Adobe Experience Platform. Nochtans, betekent dit ook de functies at.js niet achterwaarts compatibel met het Web SDK van het Platform zijn. Let op het volgende terwijl u de huidige implementatie evalueert:

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

Omdat het Web SDK van het Platform veelvoudige toepassingen van de Adobe combineert en toelaat, moet u de migratie van het Doel van andere toepassingen van de Adobe zoals Analytics en Audience Manager coördineren. Alle bibliotheken met Adoben op een bepaalde pagina moeten tegelijkertijd worden gemigreerd. Een gemengde implementatie van Platform Web SDK voor Doel en AppMeasurement voor Analytics op een bepaalde pagina wordt niet gesteund. Nochtans, wordt een gemengde implementatie over verschillende pagina&#39;s gesteund, bijvoorbeeld het Web SDK van het Platform op pagina A, en at.js met AppMeasurement op pagina B.

Tijdens het migreren moet u het proces van uw bedrijf volgen om nieuwe code te testen en vrij te geven en om zaken zoals ontwikkeling, qa, en het opvoeren milieu&#39;s te gebruiken alvorens u aan productie vrijgeeft.

>[!CAUTION]
>
>Aanbiedingen doorsturen wordt niet ondersteund voor migraties van pagina voor pagina als de omleiding plaatsvindt van een pagina met één bibliotheek naar een pagina met een andere bibliotheek


Daarna, herzie de gedetailleerde [ vergelijking van at.js aan het Web SDK van het Platform ](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

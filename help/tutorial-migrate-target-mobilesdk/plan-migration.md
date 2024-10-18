---
title: Planning - Migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie beslissen
description: Leer hoe u uw Adobe Target-implementatie kunt plannen van at.js 2.x naar Adobe Experience Platform Web SDK.
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Plan de migratie van het Doel naar de uitbreiding van het Beslissen

Voordat u Target upgradet van de doelextensie naar de beslissingsextensie in uw mobiele app, moet u de huidige implementatie beoordelen.

## Huidige implementatie van doelextensie beoordelen

De eerste stap naar een geslaagde migratie is een duidelijk inzicht te krijgen in uw huidige implementatie van de doelextensie. Er zijn eigenschappen, functies, en douanecode u kunt gebruiken die updates vereisen. Houd rekening met het volgende als u dit beoordeelt:

### Welke functies worden ondersteund?

<!--Platform Web SDK is under continuous active development and features and enhancements are added regularly. As you evaluate your current at.js implementation, refer to the [supported use cases](https://github.com/orgs/adobe/projects/18/views/1) page for the latest information.-->

### Welke functies gebruikt u vandaag?

<!--Platform Web SDK is a new library that consolidates all Adobe solutions for the websites into a single SDK. This enables tighter integration and enables new capabilities unique to Adobe Experience Platform. However, this also means at.js functions are not backwards compatible with Platform Web SDK. As you evaluate your current implementation, make note of the following:

- at.js functions such as `getOffer()` and `applyOffer()`
- Modifications to Target's global settings
- Integration with Adobe Analytics
- Use of a flicker mitigation script
- Use of response tokens
- Use of mbox, profile, and entity parameters
- Custom code unique to your implementation-->

### Welke migratiebenadering gaat u kiezen?

<!--Once you have revisited your at.js implementation, you need to determine a migration approach. There are two options:

- Migrate all Adobe applications at once across the entire site
- Migrate on a page-by-page basis

Because Platform Web SDK combines and enables multiple Adobe applications, you must coordinate the Target migration of other Adobe applications like Analytics and Audience Manager. All Adobe libraries on a given page should be migrated at the same time. A mixed implementation of Platform Web SDK for Target and AppMeasurement for Analytics on a particular page is not supported. However, a mixed implementation across different pages is supported, for example Platform Web SDK on page A, and at.js with AppMeasurement on page B.

As you migrate, you should plan on following your company's process for testing and releasing new code and use things like development, qa, and staging environments before you release to production.-->

<!--
>[!CAUTION]
>
>Redirect offers are not supported in page-by-page migrations if redirecting from a page with one library to a page with a different library
-->


Daarna, herzie de gedetailleerde [ vergelijking van de uitbreiding van het Doel en de Decisioning uitbreiding ](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

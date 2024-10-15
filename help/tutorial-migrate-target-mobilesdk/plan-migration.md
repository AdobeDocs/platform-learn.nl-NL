---
title: Planning - Migratie van doel in mobiele toepassingen van de extensie Doel naar de extensie Optimaliseren
description: Leer hoe u uw Adobe Target-implementatie kunt plannen van at.js 2.x naar Adobe Experience Platform Web SDK.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# De migratie van het Doel plannen naar de extensie Optimaliseren

Voordat u Target upgradet van de doelextensie naar de extensie Optimaliseren in uw mobiele app, moet u uw huidige implementatie evalueren.

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


Daarna, herzie de gedetailleerde [ vergelijking van de uitbreiding van het Doel en optimaliseer uitbreiding ](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de extensie Doel naar de extensie Optimaliseren. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

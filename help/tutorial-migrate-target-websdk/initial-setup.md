---
title: Aanvankelijke opstelling - Migreer Doel van at.js 2.x aan Web SDK
description: Leer over en opstelling de belangrijke die basiselementen voor uw implementatie van SDK van het Web van het Platform worden vereist
exl-id: dbf9683b-1cfc-474a-9c38-432cad4d1533
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# De eerste instellingen voor gegevensverzameling uitvoeren

Het migreren van at.js aan het Web SDK van het Platform vereist een aanvankelijke opstelling om juiste gegevensvangst, eigenschappen, en functies van het Web SDK van het Platform toe te laten. De volgende stappen van het [&#x200B; de implementatieleerprogramma van SDK van het Web van het Platform &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=nl-NL) moeten worden voltooid alvorens om het even welke veranderingen van de websiteimplementatie plaatsvinden:

- [&#x200B; vorm de aangewezen toestemmingen &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-web-sdk/overview#prerequisites){target="_blank"}  in Adobe Admin Console voor de Inzameling van Gegevens
- [&#x200B; vorm een schema XDM &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html?lang=nl-NL){target="_blank"}  voor het overgaan van gestructureerde gegevens tot de Edge Network
- [&#x200B; vorm een identiteit namespace &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html?lang=nl-NL){target="_blank"}  voor cross-device verpersoonlijking en mbox3rdPartyId functionaliteit
- [&#x200B; creeer een datastream &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html?lang=nl-NL){target="_blank"}  om het door:sturen van gegevens van Edge Network toe te laten
- [&#x200B; vorm de datastream &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=nl-NL#configure-the-datastream){target="_blank"}  om het door:sturen van gegevens aan Adobe Target toe te laten

>[!CAUTION]
>
>Houd er rekening mee dat deze ontwerpaspecten moeten worden gecoördineerd op verschillende manieren: Doel, Analyse en Audience Manager.

Zodra de aanvankelijke configuratie volledig is, zou de functionaliteit van het Doel moeten worden toegelaten gebruikend de Edge Network van Adobe Experience Platform.

Daarna, leer hoe te [&#x200B; de bibliotheek at.js vervangen en opstelling een basisimplementatie van SDK van het Web van het Platform &#x200B;](replace-library.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

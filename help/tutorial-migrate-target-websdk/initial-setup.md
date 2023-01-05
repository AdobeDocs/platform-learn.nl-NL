---
title: Eerste configuratie | Doel migreren van at.js 2.x naar Web SDK
description: Leer over en opstelling de belangrijke stichtingselementen die voor uw implementatie van SDK van het Web van Platforms worden vereist
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# De eerste instellingen voor gegevensverzameling uitvoeren

Het migreren van at.js aan het Web SDK van het Platform vereist een aanvankelijke opstelling om juiste gegevensvangst, eigenschappen, en functies van het Web SDK van het Platform toe te laten. De volgende stappen van de [Zelfstudie over de implementatie van Platform Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html) moet worden voltooid voordat wijzigingen in de implementatie van websites plaatsvinden:

- [Configureer de juiste machtigingen](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-permissions.html){target=&quot;_blank&quot;} in de Adobe Admin Console for Data Collection
- [Een XDM-schema configureren](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html){target=&quot;_blank&quot;} voor het doorgeven van gestructureerde gegevens aan het Edge-netwerk
- [Naamruimte configureren](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html){target=&quot;_blank&quot;} voor personalisatie tussen apparaten en mbox3rdPartyId-functionaliteit
- [Een gegevensstroom maken](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html){target=&quot;_blank&quot;} om het doorsturen van gegevens van Edge Network mogelijk te maken
- [De gegevensstroom configureren](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html#configure-the-datastream){target=&quot;_blank&quot;} om het doorsturen van gegevens naar Adobe Target mogelijk te maken

>[!CAUTION]
>
>Herinner dat deze ontwerpaspecten van het Web SDK over Doel, Analytics, en de migraties van de Audience Manager moeten worden gecoördineerd.

Zodra de eerste configuratie is voltooid, moet de doelfunctionaliteit zijn ingeschakeld met het Adobe Experience Platform Edge Network.

Leer nu hoe u [vervang de bibliotheek at.js en opstelling een basisimplementatie van SDK van het Platform Web](replace-library.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).

---
title: 'Eerste configuratie: de Adobe Target-implementatie in uw mobiele app migreren naar de Offer Decisioning- en Target-extensie'
description: Meer informatie over en stel de belangrijke basiselementen in die vereist zijn voor uw Web SDK-implementatie voor het platform
exl-id: dfc5abc8-0e79-454a-b1bb-6a42b1219771
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# De eerste instellingen voor gegevensverzameling uitvoeren

Voor het migreren van Target SDK naar Optimize SDK is een eerste installatie nodig om het vastleggen van gegevens, de functies en functies van Optimize SDK te kunnen uitvoeren. De volgende stappen moeten worden uitgevoerd voordat eventuele wijzigingen in de implementatie van mobiele apps plaatsvinden:

- [&#x200B; vorm de aangewezen toestemmingen &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-web-sdk/overview#permissions){target="_blank"} in Adobe Admin Console voor de Inzameling van Gegevens
- [&#x200B; vorm een schema XDM &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-schema){target="_blank"} voor het overgaan van gestructureerde gegevens tot Edge Network
- [&#x200B; vorm het schema &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-your-schema){target="_blank"} om de gegevens van Adobe Target te ontvangen
- [&#x200B; vorm een identiteit namespace &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/app-implementation/identity#set-up-a-custom-identity-namespace){target="_blank"} voor dwars-apparatenverpersoonlijking en mbox3rdPartyId functionaliteit
- [&#x200B; creeer een datastream &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-datastream){target="_blank"} om het door:sturen van gegevens van Edge Network toe te laten
- [&#x200B; vorm de datastream &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-datastream-configuration){target="_blank"} om het door:sturen van gegevens aan Adobe Target toe te laten
- [&#x200B; vorm het bezit van de Markering &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#install-adobe-journey-optimizer---decisioning-tags-extension){target="_blank"} voor Offer Decisioning en de uitbreiding van het Doel

## Extensieconfiguratie

>[!BEGINTABS]

>[!TAB  Offer Decisioning en de uitbreiding van het Doel ]

Extensies labelen die zijn geïnstalleerd wanneer de extensie Offer Decisioning en Target wordt gebruikt:

1. Offer Decisioning en Target
1. Adobe Experience Platform Edge Network
1. Mobiele kern
1. Profiel
1. Toestemming
1. Identiteit
1. AEP Assurance (optioneel, vereist voor foutopsporing)

![&#x200B; geïnstalleerde uitbreidingen van de Markering wanneer het gebruiken van de uitbreiding van Offer Decisioning en van het Doel &#x200B;](assets/tag-extensions-decisioning.png)

>[!TAB  uitbreiding van het Doel ]

Extensies labelen die zijn geïnstalleerd wanneer de extensie Doel wordt gebruikt:

1. Adobe Target
1. Mobiele kern
1. Profiel
1. Adobe Analytics (optioneel, vereist als Adobe Analytics wordt gebruikt als rapportagebron voor Adobe Target-activiteiten)

![&#x200B; geïnstalleerde uitbreidingen van de Markering wanneer het gebruiken van de uitbreiding van het Doel &#x200B;](assets/tag-extensions-target.png)

>[!ENDTABS]

## Configuratie DataStream

De uitbreiding van het Doel heeft [&#x200B; configureerbare montages &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) die met de uitbreiding van het Besluit [&#x200B; in de datastream &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup) worden gevormd.

| Doelextensie | Offer Decisioning en Target-extensie | Notities |
| --- | --- | --- | 
| Clientcode | nvt | Automatisch aan de rand instellen met de details van de IMS-organisatie |
| Milieu-id | Id van doelomgeving | Gevormd in de datastream |
| Doel Workspace-eigenschap | Eigenschapstoken | Gevormd in de datastream |
| Time-out | Time-out | Configureerbaar in de extensie Offer Decisioning en Target en in de SDK optimaliseren. De standaardtime-out is 10 seconden. |
| Serverdomein | Edge Network-domein | Instellen in de Adobe Experience Platform Edge Network-extensie |

Daarna, leer hoe te [&#x200B; het Doel SDK &#x200B;](replace-sdk.md) vervangen.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de doelextensie naar de Offer Decisioning en de doelextensie. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) te posten.

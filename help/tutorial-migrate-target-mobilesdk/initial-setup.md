---
title: Eerste configuratie - De Adobe Target-implementatie in uw mobiele app migreren naar de Adobe Journey Optimizer - De extensie voor beslissingen
description: Meer informatie over en stel de belangrijke basiselementen in die vereist zijn voor uw Web SDK-implementatie voor het platform
exl-id: dfc5abc8-0e79-454a-b1bb-6a42b1219771
source-git-commit: 45a47cde8bb5ac3baba24d7527fc4029ca3d6596
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 1%

---

# De eerste instellingen voor gegevensverzameling uitvoeren

Voor het migreren van Target SDK naar Optimize SDK is een eerste installatie nodig om het vastleggen van gegevens, de functies en functies van Optimize SDK te kunnen uitvoeren. De volgende stappen moeten worden uitgevoerd voordat wijzigingen in de implementatie van websites plaatsvinden:

- [ vorm de aangewezen toestemmingen ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#permissions) {target="_blank"} in Adobe Admin Console voor de Inzameling van Gegevens
- [ vorm een schema XDM ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-schema) {target="_blank"} voor het overgaan van gestructureerde gegevens tot Edge Network
- [ vorm het schema ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-your-schema) {target="_blank"} om de gegevens van Adobe Target te ontvangen
- [ vorm een identiteit namespace ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/app-implementation/identity#set-up-a-custom-identity-namespace) {target="_blank"} voor cross-device verpersoonlijking en mbox3rdPartyId functionaliteit
- [ creeer een datastream ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-datastream) {target="_blank"} om het door:sturen van gegevens van Edge Network toe te laten
- [ vorm de datastream ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-datastream-configuration) {target="_blank"} om het door:sturen van gegevens aan Adobe Target toe te laten
- [ vorm het bezit van de Markering ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#install-adobe-journey-optimizer---decisioning-tags-extension) {target="_blank"} voor Beslissende uitbreiding

## Extensieconfiguratie

>[!BEGINTABS]

>[!TAB  Beslissende uitbreiding ]

Extensies labelen die zijn geïnstalleerd bij gebruik van de extensie Decisioning:

1. Adobe Journey Optimizer - Beslissing
1. Adobe Experience Platform Edge Network
1. Mobiele kern
1. Profiel
1. Toestemming
1. Identiteit
1. AEP Assurance (optioneel, vereist voor foutopsporing)

![ geïnstalleerde uitbreidingen van de Markering wanneer het gebruiken van de Decisioning uitbreiding ](assets/tag-extensions-decisioning.png)

>[!TAB  uitbreiding van het Doel ]

Extensies labelen die zijn geïnstalleerd wanneer de extensie Doel wordt gebruikt:

1. Adobe Target
1. Mobiele kern
1. Profiel
1. Adobe Analytics (optioneel, vereist als Adobe Analytics wordt gebruikt als rapportagebron voor Adobe Target-activiteiten)

![ geïnstalleerde uitbreidingen van de Markering wanneer het gebruiken van de uitbreiding van het Doel ](assets/tag-extensions-target.png)

>[!ENDTABS]

## Configuratie DataStream

De uitbreiding van het Doel heeft [ configureerbare montages ](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) die met de uitbreiding van het Besluit [ in de datastream ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup) worden gevormd.

| Doelextensie | Decisitie-extensie | Notities |
| --- | --- | --- | 
| Clientcode | nvt | Automatisch aan de rand instellen met de details van de IMS-organisatie |
| Milieu-id | Id van doelomgeving | Gevormd in de datastream |
| Doel Workspace-eigenschap | Eigenschapstoken | Gevormd in de datastream |
| Time-out | Time-out | Configureerbaar in de extensie Beslissing en in de SDK Optimaliseren. De standaardtime-out is 10 seconden. |
| Serverdomein | Edge Network-domein | Instellen in de Adobe Experience Platform Edge Network-extensie |

Daarna, leer hoe te [ het Doel SDK ](replace-sdk.md) vervangen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

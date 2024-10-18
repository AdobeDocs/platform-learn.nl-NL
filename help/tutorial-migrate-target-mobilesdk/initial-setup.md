---
title: Eerste configuratie - Migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie kiezen
description: Leer over en opstelling de belangrijke die basiselementen voor uw implementatie van SDK van het Web van het Platform worden vereist
source-git-commit: afbc8248ad81a5d9080a4fdba1167e09bbf3b33d
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# De eerste instellingen voor gegevensverzameling uitvoeren

Het migreren van at.js aan het Web SDK van het Platform vereist een aanvankelijke opstelling om juiste gegevensvangst, eigenschappen, en functies van het Web SDK van het Platform toe te laten. De volgende stappen van het [ de implementatieleerprogramma van SDK van het Web van het Platform ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html) moeten worden voltooid alvorens om het even welke veranderingen van de websiteimplementatie plaatsvinden:

- [ vorm de aangewezen toestemmingen ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#prerequisites) {target="_blank"} in Adobe Admin Console voor de Inzameling van Gegevens
- [ vorm een schema XDM ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html) {target="_blank"} voor het overgaan van gestructureerde gegevens tot de Edge Network
- [ vorm een identiteit namespace ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html) {target="_blank"} voor cross-device verpersoonlijking en mbox3rdPartyId functionaliteit
- [ creeer een datastream ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html) {target="_blank"} om het door:sturen van gegevens van Edge Network toe te laten
- [ vorm de datastream ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html#configure-the-datastream) {target="_blank"} om het door:sturen van gegevens aan Adobe Target toe te laten

>[!CAUTION]
>
>Houd er rekening mee dat deze ontwerpaspecten moeten worden gecoördineerd op verschillende manieren: Doel, Analyse en Audience Manager.

Zodra de aanvankelijke configuratie volledig is, zou de functionaliteit van het Doel moeten worden toegelaten gebruikend de Edge Network van Adobe Experience Platform.

Daarna, leer hoe te [ de bibliotheek at.js vervangen en opstelling een basisimplementatie van SDK van het Web van het Platform ](replace-library.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

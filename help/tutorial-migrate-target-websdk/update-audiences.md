---
title: Publiek- en profielscripts bijwerken - Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u het Adobe Target-publiek en profielscripts kunt bijwerken voor compatibiliteit met Web SDK van Experience Platform.
exl-id: 2c0f85f7-6e8c-4d0b-8ed5-53897d06e563
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Doelpubliek en profielscripts bijwerken voor compatibiliteit met Platform Web SDK

Nadat u de technische updates hebt voltooid om Doel te migreren naar de Platform Web SDK, moet u mogelijk een aantal van uw publiek, profielscripts en activiteiten bijwerken om een vloeiende overgang te garanderen.

Alle parameters van het Doel mbox moeten in formaat XDM met een implementatie van SDK van het Web van het Platform worden overgegaan. Voordat u uw wijzigingen in de productie publiceert, moet u:

* Soorten publiek dat mbox-parameters gebruikt bijwerken
* Profielscripts bijwerken die mbox-parameters gebruiken
* Werk eventuele aanbiedingen en activiteiten bij met parametertoken-vervanging voor mbox (bijvoorbeeld `${mbox.parameter_name}`)

## Soorten publiek aanpassen

Om het even welk publiek dat douanembox parameters gebruikt zou moeten worden bijgewerkt om de nieuwe XDM parameternamen te gebruiken. Een aangepaste parameter voor `page_name` wordt bijvoorbeeld waarschijnlijk toegewezen aan `web.webpagedetails.pageName` .

Eén methode om compatibiliteit met zowel at.js als Platform Web SDK te garanderen, is het bijwerken van relevante doelgroepen zodat `OR` -voorwaarden worden gebruikt, zoals hieronder wordt getoond:

![&#x200B; hoe te om update een publiek van het Doel voor de verenigbaarheid van SDK van het Web van het Platform te bekijken &#x200B;](assets/target-audience-update.png){zoomable="yes"}

## Profielscripts bewerken

Profielscripts moeten worden bijgewerkt om naar nieuwe XDM-parameternamen te verwijzen, net als publiek. Naast de verandering van mbox parameternamen, is er geen verschil in de manier de manuscripten van het profiel tussen at.js en een implementatie van SDK van het Web van het Platform werken.

U kunt er bijvoorbeeld voor zorgen dat de compatibiliteit het gebruik van `OR` -voorwaarden in uw profielscriptcode is.

Voorbeeldprofielscript:

```Javascript
if(mbox.param('pageName') == 'Product Details'){
  return true
}
```

Bijgewerkt profielscript voor compatibiliteit van Platform Web SDK:

```Javascript
if((mbox.param('pageName') == 'Product Details') || (mbox.param('web.webPageDetails.pageName') =='Product Details')){
  return true
}
```

Voor meer informatie en beste praktijken, verwijs naar de specifieke documentatie over [&#x200B; profielmanuscripten &#x200B;](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html?lang=nl-NL).

## Parametertokens bijwerken voor dynamische inhoud

Als u om het even welke aanbiedingen, aanbevelingen ontwerpen, of activiteiten hebt die [&#x200B; dynamische inhoudsvervanging &#x200B;](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html?lang=nl-NL) gebruiken, kunnen zij dienovereenkomstig moeten worden bijgewerkt om voor de nieuwe XDM parameternamen rekening te houden.

Afhankelijk van hoe u symbolische vervanging voor mbox parameters gebruikt, kunt u uw bestaande opstelling aan rekening voor zowel oude als nieuwe parameternamen kunnen verbeteren. In situaties waarin aangepaste JavaScript-code niet mogelijk is, zoals in JSON-aanbiedingen, moet u echter kopieën maken en updates uitvoeren nadat de migratie is voltooid en live op uw productiesite gaat.

Voorbeeld JSON-aanbieding:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Voorbeeld JSON-aanbieding met parameternamen van Platform Web SDK:

```JSON
{
  "pageName" : "${mbox.web.webPagedDetails.pageName}",
  "layoutVariation" : "grid"
}
```

Als u na de migratie aanpassingen wilt aanbrengen om rekening te houden met de nieuwe namen van XDM-box-parameters, moet u tijdens de migratiegebeurtenis alle betrokken activiteiten pauzeren om te voorkomen dat er weergavefouten optreden voor bezoekers.

Daarna, leer hoe te [&#x200B; de implementatie van het Doel &#x200B;](validate.md) bevestigen.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=nl#M463) te posten.

---
title: Soorten publiek en profielscripts bijwerken | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u het Adobe Target-publiek en profielscripts kunt bijwerken voor compatibiliteit met Web SDK van Experience Platform.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# Doelpubliek en profielscripts bijwerken voor compatibiliteit met SDK van Platform Web

Nadat u de technische updates hebt voltooid om Doel te migreren naar de SDK van het Web van de Platform, kunt u sommige van uw publiek, profielmanuscripten, en activiteiten moeten bijwerken om een vlotte overgang te verzekeren.

Alle parameters van het Doel mbox moeten in formaat XDM met een implementatie van SDK van het Web van het Platform worden overgegaan. Voordat u uw wijzigingen in de productie publiceert, moet u:

* Soorten publiek dat mbox-parameters gebruikt bijwerken
* Profielscripts bijwerken die mbox-parameters gebruiken
* Werk om het even welke aanbiedingen en activiteiten bij gebruiken mbox parametersymbolenvervanging (bijvoorbeeld `${mbox.parameter_name}`)

## Soorten publiek aanpassen

Om het even welk publiek dat douanembox parameters gebruikt zou moeten worden bijgewerkt om de nieuwe XDM parameternamen te gebruiken. Een aangepaste parameter voor `page_name` wordt waarschijnlijk toegewezen aan `web.webpagedetails.pageName`.

Één benadering om verenigbaarheid met zowel at.js als het Web SDK van het Platform te verzekeren moet om het even welk relevant publiek bijwerken zodat `OR` er worden voorwaarden gebruikt, zoals hieronder aangegeven:

![Hoe te om update een publiek van het Doel voor de verenigbaarheid van SDK van het Web van het Platform te bekijken](assets/target-audience-update.png)

## Profielscripts bewerken

Profielscripts moeten worden bijgewerkt om naar nieuwe XDM-parameternamen te verwijzen, net als publiek. Naast de verandering van mbox parameternamen, is er geen verschil in de manier de manuscripten van het profiel tussen at.js en een implementatie van SDK van het Web van Platforms werken.

Eén aanpak om ervoor te zorgen dat compatibiliteit wordt gebruikt `OR` voorwaarden in uw profielscriptcode.

Voorbeeldprofielscript:

```Javascript
if(mbox.param('pageName') == 'Product Details'){
  return true
}
```

Bijgewerkt profielscript voor Platform Web SDK-compatibiliteit:

```Javascript
if((mbox.param('pageName') == 'Product Details') || (mbox.param('page.webpagedetails.pageName') =='Product Details')){
  return true
}
```

Raadpleeg de documentatie over [profielscripts](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html).

## Parametertokens bijwerken voor dynamische inhoud

Als u aanbiedingen, aanbevelingen, ontwerpen of activiteiten hebt die [dynamische inhoudvervanging](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html), moeten ze mogelijk dienovereenkomstig worden bijgewerkt om rekening te houden met de nieuwe XDM-parameternamen.

Afhankelijk van hoe u symbolische vervanging voor mbox parameters gebruikt, kunt u uw bestaande opstelling aan rekening voor zowel oude als nieuwe parameternamen kunnen verbeteren. In situaties waarin aangepaste JavaScript-code niet mogelijk is, zoals in JSON-aanbiedingen, moet u echter kopieën maken en updates uitvoeren nadat de migratie is voltooid en live op uw productiesite gaat.

Voorbeeld JSON-aanbieding:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Voorbeeld JSON-aanbieding met parameternamen van SDK van Platform Web:

```JSON
{
  "pageName" : "${mbox.web.webpagedetails.pageName}",
  "layoutVariation" : "grid"
}
```

Als u na de migratie aanpassingen wilt aanbrengen om rekening te houden met de nieuwe namen van XDM-box-parameters, moet u tijdens de migratiegebeurtenis alle betrokken activiteiten pauzeren om te voorkomen dat er weergavefouten optreden voor bezoekers.

Leer nu hoe u [De doelimplementatie valideren](validate.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
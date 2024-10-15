---
title: Interdomeinondersteuning inschakelen - Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u Adobe Target voor interdomein- en mobiele app configureert voor webbrowserscenario's met gebruik van Web SDK van Experience Platform.
source-git-commit: 009548969b88d1bfa6eac23f65b1ca2144f27c34
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Profielen voor interdomeinbezoekers inschakelen

De SDK van het Web van het Platform steunt bezoekersidentiteitskaart delend mogelijkheden die klanten toelaten om gepersonaliseerde ervaringen over uw domeinen nauwkeuriger te leveren. Met deze functie kunt u consistente personalisatie op verschillende domeinen aanbieden en de nauwkeurigheid van de rapportage van bezoekersactiviteiten verbeteren, zonder dat u hiervoor cookies van derden nodig hebt.

## Vereisten

Als u id&#39;s voor andere domeinen wilt delen, moet u Platform Web SDK versie 2.11.0 of hoger gebruiken. Deze functie is ook compatibel met VisitorAPI.js versie 1.7.0 of hoger.

Het delen van verschillende domeinen-id&#39;s werkt door een speciale `adobe_mc` query-tekenreeksparameter toe te voegen aan de URL van het doeldomein. Deze parameter wordt gebruikt voor het specificeren van bezoekersidentiteitskaart in plaats van het produceren van een nieuwe identiteitskaart of het gebruiken van een bestaande identiteitskaart

Het doeldomein moet een van deze bibliotheken gebruiken voor het delen van een domeinoverschrijdende id om de parameter `adobe_mc` te verwerken en de bezoekersidentiteitskaart correct te delen.

## Benaderingsvergelijking

Voordat u gaat implementeren, moet u eerst bepalen of uw bestaande implementatie de functie `visitor.appendVisitorIDsTo()` gebruikt. Om het even welke douanecode die deze functie gebruikt zou moeten worden bijgewerkt om het nieuwe `appendIdentityToUrl` bevel van SDK van het Web te gebruiken.

| VisitorAPI.js | Platform Web SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` | `alloy("appendIdentityToUrl", { url: *url* })` |

## De opdracht `appendIdentityToURL` gebruiken

Voor het delen van verschillende domeinen-id&#39;s voegt Web SDK-versie 2.11.0 ondersteuning toe voor de opdracht `appendIdentityToUrl` . Wanneer deze opdracht wordt gebruikt, wordt de parameter voor de queryreeks `adobe_mc` gegenereerd.

De opdracht accepteert een object met één eigenschap, `url` , en retourneert een object met de eigenschaps-URL.

Deze opdracht wacht niet op een toestemmingsupdate. Als er geen toestemming is gegeven, wordt de URL ongewijzigd geretourneerd.

Als er geen ECID is opgegeven, wordt het eindpunt `/acquire` aangeroepen om een ECID te genereren.

Hieronder ziet u hoe u het delen van verschillende domeinen-id&#39;s kunt implementeren.

Deze code voegt een gebeurtenislistener toe voor alle klikken op de pagina. Als de klik zich op een koppeling naar een overeenkomend domein bevond, in dit geval adobe.com of behance.com, wordt de identiteit aan de URL toegevoegd en wordt de gebruiker daar omgeleid.

```Javascript
document.addEventListener("click", event => {
  const anchor = event.target.closest("a");
  if (!anchor || !anchor.href) {
    return;
  }
  const url = new URL(anchor.href);
  if (!url.hostname.endsWith("adobe.com") && !url.hostname.endsWith("behance.com")) {
    return;
  }
  event.preventDefault();
  alloy("appendIdentityToUrl", { url: anchor.href }).then(result => {
    document.location = result.url;
  });
});
```

>[!TIP]
>
>Wanneer het gebruiken van de markeringseigenschap (vroeger Lancering) om Web SDK uit te voeren, kan het delen van dwars-domeinidentiteitskaart zonder douanecode worden verwezenlijkt. Verwijs naar de [ specifieke documentatie ](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension) voor meer details.

>[!NOTE]
>
>De Platform Web SDK steunt ook mobiel-aan-Web ID het delen voor inheemse mobiele toepassingsgebruiksgevallen. Voor meer informatie, verwijs naar de specifieke documentatie over [ mobiel-aan-web en het delen van dwars-domeinidentiteitskaart ](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Daarna, leer hoe te [ bijwerk publiek en profielmanuscripten ](update-audiences.md) om verenigbaarheid met het Web SDK van het Platform te verzekeren.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de extensie Doel naar de extensie Optimaliseren. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

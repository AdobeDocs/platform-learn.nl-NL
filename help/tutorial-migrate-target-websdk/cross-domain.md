---
title: Ondersteuning voor verschillende domeinen inschakelen | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u Adobe Target voor interdomeingebruik en mobiele app configureert voor webbrowserscenario's met gebruik van Experience Platform Web SDK.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Profielen voor interdomeinbezoekers inschakelen

De SDK van het Web van de Platform steunt bezoekersidentiteitskaart delend mogelijkheden die klanten toelaten om gepersonaliseerde ervaringen over uw domeinen nauwkeuriger te leveren. Met deze functie kunt u consistente personalisatie op verschillende domeinen aanbieden en de nauwkeurigheid van de rapportage van bezoekersactiviteiten verbeteren, zonder dat u hiervoor cookies van derden nodig hebt.

## Vereisten

Als u id&#39;s voor andere domeinen wilt delen, moet u Platform Web SDK versie 2.11.0 of hoger gebruiken. Deze functie is ook compatibel met VisitorAPI.js versie 1.7.0 of hoger.

Het delen van verschillende id&#39;s werkt door een speciale koppeling toe te voegen `adobe_mc` de parameter van het vraagkoord aan URL van het bestemmingsdomein. Deze parameter wordt gebruikt voor het specificeren van bezoekersidentiteitskaart in plaats van het produceren van een nieuwe identiteitskaart of het gebruiken van een bestaande identiteitskaart

Het doeldomein moet een van deze bibliotheken gebruiken voor het delen van een domeinoverschrijdende id om het `adobe_mc` en deel de bezoeker-id op de juiste wijze.

## Benaderingsvergelijking

Voordat u de implementatie uitvoert, moet u eerst bepalen of uw bestaande implementatie de `visitor.appendVisitorIDsTo()` functie. Elke aangepaste code die deze functie gebruikt, moet worden bijgewerkt om de nieuwe `appendIdentityToUrl` Web SDK, opdracht.

| VisitorAPI.js | Platform Web SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` | `alloy("appendIdentityToUrl", { url: *url* })` |

## Met de `appendIdentityToURL` command

Voor het delen van verschillende domeinen-id&#39;s voegt SDK van het Web versie 2.11.0 steun voor `appendIdentityToUrl` gebruiken. Wanneer gebruikt, produceert dit bevel `adobe_mc` querytekenreeksparameter.

De opdracht accepteert een object met één eigenschap. `url`en retourneert een object met de eigenschaps-URL.

Deze opdracht wacht niet op een toestemmingsupdate. Als er geen toestemming is gegeven, wordt de URL ongewijzigd geretourneerd.

Als er geen ECID is opgegeven, `/acquire` Het eindpunt wordt aangeroepen om een ECID te genereren.

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
>Wanneer het gebruiken van de markeringseigenschap (vroeger Lancering) om Web SDK uit te voeren, kan het delen van dwars-domeinidentiteitskaart zonder douanecode worden verwezenlijkt. Zie de [speciale documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension) voor meer informatie .

>[!NOTE]
>
>De SDK van het Web Platform ondersteunt ook het delen van mobiele-naar-web-id&#39;s voor gebruik van native mobiele apps. Raadpleeg de desbetreffende documentatie over [delen van mobiele-naar-web- en interdomein-id&#39;s](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Leer nu hoe u [publiek- en profielscripts bijwerken](update-audiences.md) om verenigbaarheid met Platform Web SDK te verzekeren.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
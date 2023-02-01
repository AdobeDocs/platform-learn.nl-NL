---
title: Oplossing voor prefetch | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een tijdelijke oplossing implementeert voor het doorgeven van parameters met een prefetch
source-git-commit: d061d2492d6d5e8e7a8a6e03ce63b9b6cd3793d8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Oplossing voor prefetch

Alle klanten van het Doel die niet met het Web SDK van het Experience Platform vóór 1 Oktober, 2022 produceerden dienen een verzoek aan Doel van het Netwerk van de Rand van het Experience Platform gebruikend &quot;prefetch&quot;wijze. Met Prefetch kan de browser de Target-aanbiedingen vooraf laden en in de cache opslaan, zodat deze klaar zijn om te worden toegepast wanneer de bezoeker de juiste status van de pagina heeft bereikt. Dit is voordelig in Toepassingen van de Enige Pagina (SPA) aangezien de gewenste gebruikerservaring zo snel mogelijk, zonder extra netwerkverzoeken kan worden teruggegeven. Er zijn echter belangrijke implicaties voor zowel SPA als niet-SPA implementaties.

In plaats van een bezoeker te tellen in een activiteit wanneer de aanbiedingsinhoud in het netwerkverzoek wordt geleverd, worden bezoekers nu geteld in activiteiten wanneer een `propositionDisplay` sendEvent verzoek wordt gemaakt door Web SDK. Deze verzoeken worden gemaakt automatisch door de Visual Experience Composer (VEC) activiteiten wanneer renderDecisions aan waar wordt geplaatst en wanneer de ervaring met succes op de pagina is teruggegeven. Met douanewerkingsgebied en wanneer renderDecisions aan vals wordt geplaatst, moeten de propositionDisplay verzoeken opzettelijk door de uitvoerder in werking worden gesteld. Ook, _alle parameters die voor andere doeleinden dan de directe kwalificatie van de activiteit worden gebruikt, moeten via een `propositionDisplay`  event_.

## Waarom is de oplossing nodig?

In vele implementaties van het Doel, worden de belangrijke netwerkverzoeken soms gemaakt zonder een verwachting van een activiteit die wordt geleverd. Bijvoorbeeld:

* Omzettingen recordvolgorde
* Profielparameters instellen
* Scripts voor triggerprofielen
* Entiteitsparameters verzenden om de Recommendations-catalogus te vullen

Jammer genoeg, in prefetch wijze, gedragen deze zich niet zoals verwacht. In de prefetch-modus worden deze gegevens alleen opgenomen als ze deel uitmaken van een `propositionDisplay`.

## Wat is de oplossing?

De oplossing bestaat uit drie onderdelen:

1. Definieer een aangepast bereik als onderdeel van uw `sendEvent`
1. Het aangepaste bereik gebruiken in een op formulieren gebaseerde activiteit (de activiteit kan als standaardinhoud fungeren)
1. Een reactiehandler gebruiken om een andere te maken `sendEvent` voor propositionDisplay en neem de parameters op die u nodig hebt om de volgorde vast te leggen, stel de profielparameters in, activeer het profielscript, verzend de entiteitsparameters, enzovoort.

Hier ziet u bijvoorbeeld hoe u de tijdelijke oplossing kunt gebruiken om een profielparameter te verzenden:


```JavaScript
var data = {
    "__adobe": {
        "target": {
            "profile.gender": "male"
        }
    }
};
// Send the initial event with the data object and custom decision scope
alloy("sendEvent", {
    "renderDecisions": true,
    data,
    decisionScopes: ['profile-param-example']
}).then(function(result) {
    var propositions = result.propositions;
    var ctaProposition;
    if (propositions) {
        // Find the discount proposition, if it exists.
        for (var i = 0; i < propositions.length; i++) {
            var proposition = propositions[i];
            if (proposition.scope === "profile-param-example") {
                ctaProposition = proposition;
                break;
            }
        }
    }
    if (ctaProposition) {
        // Send a "decisioning.propositionDisplay" event signaling that the proposition has been rendered, and includes the data object again
        alloy("sendEvent", {
            xdm: {
                eventType: "decisioning.propositionDisplay",
                _experience: {
                    decisioning: {
                        propositions: [{
                            id: ctaProposition.id,
                            scope: ctaProposition.scope,
                            scopeDetails: ctaProposition.scopeDetails
                        }]
                    }
                }
            },
            data
        });
    }
});
```

Wanneer het profiel is ingesteld als onderdeel van de propositionDisplay, wordt het opgeslagen naar het profiel van de bezoeker en is het beschikbaar in volgende aanvragen. Dezelfde aanpak kan worden gebruikt om gegevens over orderomzetting en parameters van entiteiten te rapporteren.

In labels gebruikt u het gebeurtenistype Send Event Complete om een gebeurtenis te activeren die de extra sendEvent bevat.

## Hoe weet ik of mijn implementatie de prefetch-modus gebruikt?

U moet een ticket voor de klantenservice openen om te weten te komen of uw account de prefetch-modus gebruikt.


>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
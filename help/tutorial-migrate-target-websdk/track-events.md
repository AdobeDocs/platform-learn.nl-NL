---
title: Gebeurtenissen bijhouden | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe te om de omzettingsgebeurtenissen van Adobe Target te volgen gebruikend het Web SDK van het Experience Platform.
source-git-commit: 8209b13b745dbea418003b133a6834825947950e
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# De omzettingsgebeurtenissen van het Doel van het spoor gebruikend het Web SDK van het Platform

Conversiegebeurtenissen voor Doel kunnen met het Web SDK van het Platform gelijkend op at.js worden gevolgd. Conversiegebeurtenissen behoren meestal tot de volgende categorieën:

* Automatisch bijgehouden gebeurtenissen waarvoor geen configuratie vereist is
* Aankoop conversiegebeurtenissen die moeten worden aangepast voor een Web SDK-implementatie van het Platform Best Practice
* Niet-aankoopconversiegebeurtenissen waarvoor code-updates vereist zijn

## Objectspatiëring vergelijken

De volgende lijst vergelijkt hoe de gebeurtenissen van de de spooromzetting van het Web SDK van at.js en van het Platform

| Activiteitsdoelstelling | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Conversie > Pagina&#39;s weergeven | Automatisch bijgehouden. Gebaseerd op de waarde van `context.address.url` in de aanvraag at.js. | Automatisch bijgehouden. Gebaseerd op de waarde van `xdm.web.webPageDetails.URL` in de `sendEvent` payload |
| Conversie > Een box weergegeven | Wordt bijgehouden met de aanvraag voor een locatie van een weergavekader of een melding met `trackEvent()` of `sendNotifications()` met een `type` waarde van `display`. | Bijgehouden met een Platform Web SDK `sendEvent` met de `eventType` van `decisioning.propositionDisplay`. |
| Conversie > Op een element klikken | Automatisch bijgehouden voor VEC-activiteiten. Wordt weergegeven als een netwerkaanroep van at.js met een `notifications` object in de aanvraag en een `type` waarde van `click`. | Automatisch bijgehouden voor VEC-activiteiten. Verschijnt als SDK van het Web van het Platform `sendEvent` met de `eventType` van `decisioning.propositionInteract`. |
| Betrokkenheid > Paginaweergaven | Automatisch bijgehouden | Automatisch bijgehouden |
| Betrokkenheid > Tijd op site | Automatisch bijgehouden | Automatisch bijgehouden |

<!--
| Revenue > RPV, AOV, or Total Sales | Tracked based on the `orderTotal` parameter values for the specified mbox(es) | Tracked based on the `xdm.commerce.order.priceTotal` values. Its best to use the "any mbox" option in the goal setup. |
| Revenue > Orders | Tracked based on the unique `orderId` parameter values for the specified mbox(es) | Tracked based on the unique values for `xdm.commerce.order.purchaseID`. Its best to use the "any mbox" option in the goal setup. |
| Engagement > Custom Scoring | Tracked with the `mboxPageValue` parameter. Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) for more details. | Tracked with `data.__adobe.target.mboxPageValue` in the `sendEvent` payload |
-->

## Automatisch bijgehouden gebeurtenissen

Voor de volgende omzettingsdoelstellingen zijn geen specifieke aanpassingen in uw implementatie vereist:

* Conversie > Pagina&#39;s weergeven
* Conversie > Op een element klikken
* Betrokkenheid > Paginaweergaven
* Betrokkenheid > Tijd op site

>[!NOTE]
>
>SDK van het Web van het Platform staat grotere controle over de waarden toe die in de verzoeklading worden overgegaan. Als u ervoor wilt zorgen dat doelfuncties zoals URL&#39;s met kwaliteitscontrole en conversiedoelstellingen voor Pagina&#39;s goed werken, controleert u of de conversiedoelstellingen `xdm.web.webPageDetails.URL` De waarde bevat de volledige pagina-URL met het juiste hoofdlettergebruik.

<!--
## Purchase conversion events

The following conversion goals are based on the order details information passed in the Platform Web SDK `sendEvent` payload:

* Revenue > Revenue per Visit (RPV)
* Revenue > Average Order Value (AOV)
* Revenue > Total Sales
* Revenue > Orders

Target at.js implementations typically use an order confirmation mbox with the `trackEvent()` or `sendNotifications()` functions to pass the order ID, order total, and a list of product IDs purchased. These methods are specific to Target.

The Platform Web SDK is a shared library for all Adobe applications and you may have other applications such as Adobe Analytics to consider. Because of this shared nature, its best send a single order confirmation call using the appropriate commerce XDM field group.

For more information and an example, refer to the tutorial section about [sending purchase parameters to Target](send-parameters.md#purchase-parameters). 
-->

## Aangepaste gebeurtenissen

De implementaties van het doel gebruiken over het algemeen de gebeurtenissen van de douaneomzetting om kliks voor op vorm-gebaseerde activiteiten te volgen, om een omzetting in een stroom te betekenen, of parameters over te gaan zonder om nieuwe inhoud te vragen.

De lijst hieronder schetst de at.js benadering en het equivalent van SDK van het Web van het Platform voor een paar gemeenschappelijke omzetting-volgende gebruiksgevallen.

| Gebruiksscenario | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Houd een klikomzettingsgebeurtenis voor een mbox plaats (werkingsgebied) bij | Uitvoeren `trackEvent()` of `sendNotifications()` met een `type` waarde van `click` voor een specifieke mbox-locatie | Een `sendEvent` gebruiken met een gebeurtenistype van `decisioning.propositionInteract` |
| Een aangepaste conversiegebeurtenis bijhouden die mogelijk ook aanvullende gegevens bevat, zoals doelprofielparameters | Uitvoeren `trackEvent()` of `sendNotifications()` met een `type` waarde van `display` voor een specifieke mbox-locatie | Een `sendEvent` gebruiken met een gebeurtenistype van `decisioning.propositionDisplay` |

>[!NOTE]
>
>Hoewel `decisioning.propositionDisplay` wordt het meest gebruikt voor het verhogen van indrukkingen voor specifieke werkingsgebieden, zou het ook als directe vervanging voor at.js moeten worden gebruikt `trackEvent()` meestal. De `trackEvent()` functie is standaard ingesteld op een type `display` indien niet opgegeven. Controleer uw implementatie om ervoor te zorgen dat u het juiste gebeurtenistype gebruikt voor aangepaste conversies die u hebt gedefinieerd.

Raadpleeg de speciale documentatie van at.js voor meer informatie over het gebruik van [`trackEvent()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-trackevent/) en [`sendNotifications()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-sendnotifications-atjs-21/) voor het bijhouden van Target-gebeurtenissen.

at.js, voorbeeld met `trackEvent()` om een klik op een mbox-locatie bij te houden:

```JavaScript
adobe.target.trackEvent({
  "type": "click",
  "mbox": "homepage_hero"
});
```

Met een implementatie van SDK van het Web van het Platform, kunt u gebeurtenissen en gebruikersacties volgen door te roepen `sendEvent` opdracht, vullen `_experience.decisioning.propositions` XDM gebiedsgroep, en het plaatsen van `eventType` tot één van twee waarden:

* `decisioning.propositionDisplay`: Geeft aan dat de doelactiviteit wordt gerenderd.
* `decisioning.propositionInteract`: Geeft een gebruikersinteractie met de activiteit aan, zoals een muisklik.

De `_experience.decisioning.propositions` XDM-veldgroep is een array met objecten. De eigenschappen van elk object worden afgeleid van de `result.propositions` die wordt geretourneerd in het dialoogvenster `sendEvent` opdracht: `{ id, scope, scopeDetails }`

```JavaScript
alloy("sendEvent", {
  xdm: { ...},
  decisionScopes: ["hero-banner"]
}).then(function (result) {
  var propositions = result.propositions;

  if (propositions) {
    // Find the discount proposition, if it exists.
    for (var i = 0; i < propositions.length; i++) {
      var proposition = propositions[i];
      for (var j = 0; j < proposition.items; j++) {
        var item = proposition.items[j];

        if (item.schema === "https://ns.adobe.com/personalization/measurement") {
          // add metric to the DOM element
          const button = document.getElementById("form-based-click-metric");

          button.addEventListener("click", event => {
            const executedPropositions = [
              {
                id: proposition.id,
                scope: proposition.scope,
                scopeDetails: proposition.scopeDetails
              }
            ];
            // send the click track event
            alloy("sendEvent", {
              "xdm": {
                "eventType": "decisioning.propositionInteract",
                "_experience": {
                  "decisioning": {
                    "propositions": executedPropositions
                  }
                }
              }
            });
          });
        }
      }
    }
  }
});
```

Leer nu hoe u [delen van verschillende domeinen-id&#39;s inschakelen](cross-domain.md) voor consistente bezoekersprofielen.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
---
title: De gebeurtenissen van het spoor - migreren Doel van at.js 2.x aan Web SDK
description: Leer hoe te om de omzettingsgebeurtenissen van Adobe Target te volgen gebruikend het Web SDK van het Experience Platform.
exl-id: 5da772bc-de05-4ea9-afbd-3ef58bc7f025
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# De omzettingsgebeurtenissen van het Doel van het spoor gebruikend Platform Web SDK

Conversiegebeurtenissen voor Doel kunnen met het Web SDK van het Platform gelijkend op at.js worden gevolgd. Conversiegebeurtenissen behoren meestal tot de volgende categorieën:

* Automatisch bijgehouden gebeurtenissen waarvoor geen configuratie vereist is
* Aankoop conversiegebeurtenissen die moeten worden aangepast voor een Web SDK-implementatie van het platform voor best practices
* Niet-aankoopconversiegebeurtenissen waarvoor code-updates vereist zijn

## Objectspatiëring vergelijken

De volgende lijst vergelijkt hoe de de spooromzettingsgebeurtenissen van at.js en van SDK van het Web van het Platform

| Activiteitsdoelstelling | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Conversie > Pagina&#39;s weergeven | Automatisch bijgehouden. Gebaseerd op de waarde van `context.address.url` in de aanvraag at.js payload. | Automatisch bijgehouden. Gebaseerd op de waarde van `xdm.web.webPageDetails.URL` in de `sendEvent` payload |
| Conversie > Een box weergegeven | Wordt bijgehouden met de aanvraag voor een locatie van een weergavekader of een melding met `trackEvent()` of `sendNotifications()` met de waarde `type` `display` . | Wordt gevolgd door een Platform Web SDK `sendEvent` -aanroep met de lus `eventType` of `decisioning.propositionDisplay` . |
| Conversie > Op een element klikken | Automatisch bijgehouden voor VEC-activiteiten. Wordt weergegeven als een netwerkaanroep van at.js met een `notifications` -object in de payload in aanvraag en een `type` waarde van `click` . | Automatisch bijgehouden voor VEC-activiteiten. Wordt weergegeven als een Platform Web SDK `sendEvent` -aanroep met `eventType` van `decisioning.propositionInteract` . |
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
>De het Web SDK van het Platform staat grotere controle over de waarden toe die in de verzoeklading worden overgegaan. Om ervoor te zorgen dat doelfuncties zoals URL&#39;s met kwaliteitscontrole en conversiedoelstellingen voor Pagina&#39;s goed werken, controleert u of de waarde van `xdm.web.webPageDetails.URL` de volledige pagina-URL bevat met het juiste hoofdlettergebruik.

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

In de onderstaande tabel worden de benadering at.js en het equivalent van Platform Web SDK voor een paar algemene gevallen van conversie-tracking-gebruik beschreven.

| Gebruiksscenario | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Houd een klikomzettingsgebeurtenis voor een mbox plaats (werkingsgebied) bij | Voer `trackEvent()` of `sendNotifications()` met een `type` waarde `click` uit voor een specifieke locatie van het selectievakje | Een opdracht `sendEvent` uitvoeren met het gebeurtenistype `decisioning.propositionInteract` |
| Een aangepaste conversiegebeurtenis bijhouden die mogelijk ook aanvullende gegevens bevat, zoals doelprofielparameters | Voer `trackEvent()` of `sendNotifications()` met een `type` waarde `display` uit voor een specifieke locatie van het selectievakje | Een opdracht `sendEvent` uitvoeren met het gebeurtenistype `decisioning.propositionDisplay` |

>[!NOTE]
>
>Hoewel `decisioning.propositionDisplay` het meest wordt gebruikt voor het verhogen van indrukkingen voor specifiek werkingsgebied, zou het ook als directe vervanging voor at.js `trackEvent()` gewoonlijk moeten worden gebruikt. De functie `trackEvent()` heeft als standaardwaarde een type `display` als dat niet is opgegeven. Controleer uw implementatie om ervoor te zorgen dat u het juiste gebeurtenistype gebruikt voor aangepaste conversies die u hebt gedefinieerd.

Verwijs naar de specifieke documentatie at.js voor meer informatie over hoe te om [`trackEvent()` ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-trackevent/) en [`sendNotifications()` ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-sendnotifications-atjs-21/) voor het volgen gebeurtenissen van het Doel te gebruiken.

in.js-voorbeeld met `trackEvent()` om een klik op een locatie van een box bij te houden:

```JavaScript
adobe.target.trackEvent({
  "type": "click",
  "mbox": "homepage_hero"
});
```

Met een Platform Web SDK implementatie, kunt u gebeurtenissen en gebruikersacties volgen door het `sendEvent` bevel te roepen, de `_experience.decisioning.propositions` XDM gebiedsgroep te bevolken, en `eventType` aan één van twee waarden te plaatsen:

* `decisioning.propositionDisplay`: hiermee wordt de rendering van de doelactiviteit aangegeven.
* `decisioning.propositionInteract`: hiermee wordt een gebruikersinteractie met de activiteit aangegeven, zoals een muisklik.

De `_experience.decisioning.propositions` XDM gebiedsgroep is een serie van voorwerpen. De eigenschappen van elk object worden afgeleid van de `result.propositions` die wordt geretourneerd in de `sendEvent` command: `{ id, scope, scopeDetails }`

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

Daarna, leer hoe te [ om het delen van dwars-domeinidentiteitskaart ](cross-domain.md) voor verenigbare bezoekersprofielen toe te laten.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

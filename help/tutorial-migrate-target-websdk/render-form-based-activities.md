---
title: Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een Adobe Target-implementatie migreert van at.js 2.x naar Adobe Experience Platform Web SDK. De onderwerpen omvatten bibliotheekoverzicht, implementatieverschillen, en andere opmerkelijke callouts.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Doelactiviteiten renderen die gebruikmaken van de op formulieren gebaseerde composer

Sommige doelimplementaties gebruiken mogelijk regionale selectievakjes (nu bekend als &quot;bereik&quot;) om inhoud te leveren van activiteiten die gebruikmaken van de op formulieren gebaseerde Experience Composer. Als uw at.js Implementatie van het Doel mboxes gebruikt, dan moet u het volgende doen:

* Werk om het even welke verwijzingen van uw at.js implementatie bij die gebruiken `getOffer()` of `getOffers()` aan de gelijkwaardige methodes van SDK van het Web van het Platform.
* Code toevoegen om een trigger te maken `propositionDisplay` zodat een indruk wordt geteld.

## Inhoud aanvragen en op aanvraag toepassen

Activiteiten die zijn gemaakt met behulp van de op formulieren gebaseerde composer van Target en die zijn geleverd aan regionale vakken, kunnen niet automatisch worden gerenderd door de Web SDK van het Platform. Gelijkaardig aan at.js, moeten de aanbiedingen die aan specifieke plaatsen van het Doel worden geleverd op bestelling worden teruggegeven.

at.js Voorbeeld gebruiken `getOffer()` en `applyOffer()`:

1. Uitvoeren `getOffer()` om een voorstel voor een plaats aan te vragen
1. Uitvoeren `applyOffer()` om de aanbieding aan een gespecificeerde selecteur terug te geven
1. Een activiteitsindruk wordt automatisch vergroot op het moment van het `getOffer()` verzoek

```JavaScript
// Retrieve an offer for the homepage-hero location
adobe.target.getOffer({
  "mbox": "homepage_hero",

  // Render offer to the #hero-banner selector
  "success": function(offers) {
    adobe.target.applyOffer({
      "mbox": "homepage_hero",
      "selector": "#hero-banner",
      "offer": offers
    });
  },
  "error": {
    console.log(error);
  },
  "timeout": 3000
});
```

Platform Web SDK equivalent gebruiken `applyPropositions` opdracht:

1. Uitvoeren `sendEvent` bevel om aanbiedingen (voorstellen) voor één of meerdere plaatsen (werkingsgebied) te verzoeken
1. Uitvoeren `applyPropositions` bevel met meta-gegevensvoorwerp dat instructies voor verstrekt hoe te om inhoud op de pagina voor elk werkingsgebied toe te passen
1. Uitvoeren `sendEvent` command met eventType van `decisioning.propositionDisplay` om een indruk te volgen

```JavaScript
// Retrieve propositions for homepage_hero location (scope)
alloy("sendEvent", {
  "decisionScopes": ["homepage_hero"]
}).then(function(result) {
  var retrievedPropositions = result.propositions;
    
  // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
  return alloy("applyPropositions", {
    "propositions": retrievedPropositions,
    "metadata": {
      // Specify each regional mbox or scope name along with a selector and actionType
      "homepage_hero": {
        "selector": "#hero-banner",
        "actionType": "setHtml"
      }
    }
  }).then(function(applyPropositionsResult) {
    var renderedPropositions = applyPropositionsResult.propositions;

    // Send the display notifications via sendEvent command
    alloy("sendEvent", {
      "xdm": {
        "eventType": "decisioning.propositionDisplay",
        "_experience": {
          "decisioning": {
            "propositions": renderedPropositions
          }
        }
      }
    });
  });
});
```

Het Web SDK van het Platform biedt grotere controle voor het toepassen van op vorm-gebaseerde activiteiten op de pagina gebruikend aan `applyPropositions` gebruiken met een `actionType` gespecificeerd:

| `actionType` | Beschrijving | at.js `applyOffer()` | Platform Web SDK `applyPropositions` |
| --- | --- | --- | --- |
| `setHtml` | Wis de inhoud van de container, dan voeg de aanbieding aan de container toe | Ja (altijd gebruikt) | Ja |
| `replaceHtml` | De container verwijderen en vervangen door de aanbieding | Nee | Ja |
| `appendHtml` | Hiermee wordt het aanbod toegevoegd na de opgegeven kiezer | Nee | Ja |

Zie de [speciale documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) over het renderen van inhoud met de SDK van het Web Platform voor extra renderopties en voorbeelden.

## Voorbeeld van implementatie

De onderstaande voorbeeldpagina bouwt verder op de implementatie die in de vorige sectie wordt beschreven, maar voegt alleen extra bereik toe aan de `sendEvent` gebruiken.

```HTML
<!doctype html>
<html>
<head>
  <title>Example page</title>
  <!--Data Layer to enable rich data collection and targeting-->
  <script>
    var digitalData = { 
      // Data layer information goes here
    };
  </script>

  <!--Third party libraries that may be used by Target offers and modifications-->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>

  <!--Prehiding snippet for Target with asynchronous deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

  <!--Platform Web SDK base code-->
  <script>
    !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
    []).push(o),n[o]=function(){var u=arguments;return new Promise(
    function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
    (window,["alloy"]);
  </script>

  <!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
  <script src="https://cdn1.adoberesources.net/alloy/2.6.4/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK then send event-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
    alloy("sendEvent", {
      // Request and render VEC-based activities
      "renderDecisions": true,
      // Request content for form-based activities using the "homepage_hero" scope
      "decisionScopes": ["homepage_hero"]
    }).then(function(result) {
      var retrievedPropositions = result.propositions;
        
      // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
      return alloy("applyPropositions", {
        "propositions": retrievedPropositions,
        "metadata": {
          // Specify each regional mbox or scope name along with a selector and actionType
          "homepage_hero": {
            "selector": "#hero-banner",
            "actionType": "setHtml"
          }
        }
      }).then(function(applyPropositionsResult) {
        var renderedPropositions = applyPropositionsResult.propositions;

        // Send the display notifications via sendEvent command
        alloy("sendEvent", {
          "xdm": {
            "eventType": "decisioning.propositionDisplay",
            "_experience": {
              "decisioning": {
                "propositions": renderedPropositions
              }
            }
          }
        });
      });
    });
  </script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div id="homepage-hero">Homepage Hero Banner Content</div>
</body>
</html>
```

Leer nu hoe u [Geef de parameters van het Doel gebruikend het Web SDK van het Platform door](send-parameters.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
---
title: Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een Adobe Target-implementatie migreert van at.js 2.x naar Adobe Experience Platform Web SDK. De onderwerpen omvatten bibliotheekoverzicht, implementatieverschillen, en andere opmerkelijke callouts.
exl-id: 43b9ae91-4524-4071-9eb4-12a0a8aec242
source-git-commit: 4690d41f92c83fe17eda588538d397ae1fa28af0
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Doelactiviteiten renderen die gebruikmaken van de op formulieren gebaseerde composer

Sommige doelimplementaties gebruiken mogelijk regionale selectievakjes (nu bekend als &quot;bereik&quot;) om inhoud te leveren van activiteiten die gebruikmaken van de op formulieren gebaseerde Experience Composer. Als uw at.js Implementatie van het Doel mboxes gebruikt, dan moet u het volgende doen:

* Werk alle verwijzingen van uw at.js-implementatie die `getOffer()` of `getOffers()` gebruiken, bij naar de equivalente Web SDK-methoden van het Platform.
* Voeg code toe om een `propositionDisplay` -gebeurtenis te activeren, zodat een indruk wordt geteld.

## Inhoud aanvragen en op aanvraag toepassen

Activiteiten die zijn gemaakt met behulp van de op formulieren gebaseerde composer van Target en die worden geleverd aan regionale boxes, kunnen niet automatisch worden gerenderd door de Platform Web SDK. Gelijkaardig aan at.js, moeten de aanbiedingen die aan specifieke plaatsen van het Doel worden geleverd op bestelling worden teruggegeven.


+++at.js Voorbeeld met `getOffer()` en `applyOffer()` :

1. Uitvoeren `getOffer()` om een voorstel voor een locatie aan te vragen
1. Uitvoeren `applyOffer()` om de aanbieding te renderen naar een opgegeven kiezer
1. Een activiteitsindruk wordt automatisch verhoogd op het moment van het `getOffer()` -verzoek

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

+++

+++Platform Web SDK equivalent gebruikend het `applyPropositions` bevel:

1. Voer `sendEvent` bevel uit om aanbiedingen (voorstellen) voor één of meerdere plaatsen (werkingsgebied) te verzoeken
1. Opdracht uitvoeren `applyPropositions` met object metadata dat instructies biedt voor het toepassen van inhoud op de pagina voor elk bereik
1. Voer de opdracht `sendEvent` uit met eventType van `decisioning.propositionDisplay` om een indruk te volgen

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

+++

De SDK van het Web van het Platform biedt grotere controle voor het toepassen van op vorm-gebaseerde activiteiten op de pagina gebruikend het `applyPropositions` bevel met `actionType` gespecificeerd:

| `actionType` | Beschrijving | at.js `applyOffer()` | Platform Web SDK `applyPropositions` |
| --- | --- | --- | --- |
| `setHtml` | Wis de inhoud van de container, dan voeg de aanbieding aan de container toe | Ja (altijd gebruikt) | Ja |
| `replaceHtml` | De container verwijderen en vervangen door de aanbieding | Nee | Ja |
| `appendHtml` | Hiermee wordt het aanbod toegevoegd na de opgegeven kiezer | Nee | Ja |

Verwijs naar de [&#x200B; specifieke documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=nl-NL) over het teruggeven van inhoud gebruikend het Web SDK van het Platform voor extra het teruggeven opties en voorbeelden.

## Voorbeeld van implementatie

De voorbeeldpagina hieronder bouwt verder op de implementatie die in de vorige sectie wordt geschetst, slechts voegt het extra werkingsgebied aan het `sendEvent` bevel toe.

+++Platform Web SDK voorbeeld met veelvoudige werkingsgebied

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

Daarna, leer hoe te [&#x200B; parameters overgaan van het Doel gebruikend het Web SDK van het Platform &#x200B;](send-parameters.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

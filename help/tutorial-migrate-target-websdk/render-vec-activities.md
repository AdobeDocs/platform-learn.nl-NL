---
title: Geef VEC Activiteiten terug - Migreer Doel van at.js 2.x aan Web SDK
description: Leer hoe u composer-activiteiten voor visuele beleving ophaalt en toepast met een Web SDK-implementatie van Adobe Target.
exl-id: bbbbfada-e236-44de-a7bf-5c63ff840db4
source-git-commit: d4308b68d6974fe47eca668dd16555d15a8247c9
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Adobe Target Visual Experience Composer (VEC)-activiteiten renderen

De doelactiviteiten worden opstelling gebruikend of Visual Experience Composer (VEC) of op vorm-gebaseerde composer. De het Web SDK van het Platform kan op VEC-Gebaseerde activiteiten op de pagina enkel zoals at.js terugwinnen en toepassen. Voor dit onderdeel van de migratie gaat u als volgt te werk:

* De extensie van de browser Visual Editing Helper installeren
* Voer een `sendEvent` vraag met het Web SDK van het Platform uit om activiteiten te verzoeken.
* Werk alle verwijzingen van uw at.js-implementatie bij die `getOffers()` gebruiken om een Target `pageLoad` -aanvraag uit te voeren.

## Visuele bewerkingshulpprogramma voor browsers

Met de Adobe Experience Cloud Visual Editing Helper-browserextensie voor Google Chrome kunt u websites betrouwbaar laden binnen de Adobe Target Visual Experience Composer (VEC) voor een snelle auteur en QA-webbeleving.

De visuele het Uitgeven browser van Helper uitbreiding werkt met websites die at.js of het Web SDK van het Platform gebruiken.

### Vraag de Visual Editing Helper aan en installeer deze

1. Navigeer aan [&#x200B; Adobe Experience Cloud Visuele het Uitgeven Helper browser uitbreiding in de Opslag van het Web van Chrome &#x200B;](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
1. Klik toevoegen aan **Chrome** > **Uitbreiding** toevoegen.
1. Open VEC in Doel.
1. Om de uitbreiding te gebruiken, klik het Visuele het Uitgeven de browser van de Helper browser van de Helper pictogram ![&#x200B; Visuele het Uitgeven van het pictogram van de Uitbreiding &#x200B;](assets/VEC-Helper.png){zoomable="yes"} in uw browser van Chrome terwijl op de Wijze VEC of QA.

De visuele het Uitgeven Helper wordt automatisch toegelaten wanneer een website in het Doel VEC aan macht authoring wordt geopend. De extensie heeft geen voorwaardelijke instellingen. De extensie verwerkt automatisch alle instellingen, inclusief de instellingen voor SameSite-cookies.

Verwijs naar de specifieke documentatie voor meer informatie over de [&#x200B; Visuele het Uitgeven uitbreiding van de Helper &#x200B;](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html?lang=nl-NL) en [&#x200B; het oplossen van problemen de Visuele Composer van de Ervaring &#x200B;](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/troubleshoot-composer.html?lang=nl-NL).

>[!IMPORTANT]
>
>De nieuwe [&#x200B; Visuele het Uitgeven uitbreiding van de Helper &#x200B;](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) vervangt de vorige [&#x200B; de Browser van de Helper van het Doel VEC uitbreiding &#x200B;](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html?lang=nl-NL). Als de oudere uitbreiding van de Helper VEC geïnstalleerd is, zou het moeten worden verwijderd of worden onbruikbaar gemaakt alvorens de Visuele Uitgevende uitbreiding van de Helper te gebruiken.

## Inhoud automatisch aanvragen en toepassen

Nadat SDK van het Web van het Platform op de pagina wordt gevormd, kunt u inhoud van Doel verzoeken. In tegenstelling tot at.js die kan worden gevormd om inhoud automatisch te verzoeken wanneer de bibliotheek laadt, vereist het Web SDK van het Platform u uitdrukkelijk om een bevel uit te voeren.

Als voor uw at.js-implementatie de `pageLoadEnabled` -instelling is ingesteld op `true` , die automatische rendering van VEC-gebaseerde activiteiten mogelijk maakt, voert u de volgende `sendEvent` -opdracht uit met de Platform Web SDK:

>[!BEGINTABS]

>[!TAB  JavaScript ]

```Javascript
alloy("sendEvent", {
  "renderDecisions": true
});
```

>[!TAB  Markeringen ]

Gebruik in tags het actietype [!UICONTROL Send event] met de optie [!UICONTROL Render visual personalization decisions] geselecteerd:

![&#x200B; verzend een gebeurtenis met Render visuele verpersoonlijkingsbesluiten die in markeringen &#x200B;](assets/vec-sendEvent-renderTrue.png){zoomable="yes"} worden geselecteerd

>[!ENDTABS]

<!--
When the Platform Web SDK renders an activity to the page with `renderDecisions` set to `true`, an additional notification call fires automatically to increment an impression and attribute the visitor to the activity. This call uses an event type with the value `decisioning.propositionDisplay`.

![Platform Web SDK call incrementing a Target impression](assets/target-impression-call.png){zoomable="yes"}
-->

## Inhoud aanvragen en op aanvraag toepassen

Sommige implementaties van het Doel vereisen één of andere douaneverwerking van aanbiedingen VEC alvorens hen op de pagina toe te passen. Of, vragen zij veelvoudige plaatsen in één enkele vraag. In een at.js-implementatie kunt u dit doen door `pageLoadEnabled` in te stellen op `false` en de `getOffers()` functie te gebruiken om een `pageLoad` request uit te voeren.

+++ at.js-voorbeeld met `getOffers()` en `applyOffers()` om VEC-gebaseerde activiteiten handmatig te renderen

```JavaScript
adobe.target.getOffers({
  request: {
    execute: {
      pageLoad: {}
    }
  }
}).
then(response => adobe.target.applyOffers({ response: response }));
```

+++

De Platform Web SDK heeft geen specifieke `pageLoad` -gebeurtenis. Alle aanvragen voor doelinhoud worden beheerd met de optie `decisionScopes` met de opdracht `sendEvent` . Het `__view__` bereik dient voor het doel van de `pageLoad` aanvraag.

+++ Een equivalente Web SDK van het Platform `sendEvent` benadering:

1. Een opdracht `sendEvent` uitvoeren die het `__view__` beslissingsbereik bevat
1. De geretourneerde inhoud met de opdracht `applyPropositions` toepassen op de pagina
1. Een opdracht `sendEvent` uitvoeren met het gebeurtenistype en de propositiegegevens van `decisioning.propositionDisplay` om de indruk te vergroten

```Javascript
alloy("sendEvent", {
  // Request the special "__view__" scope for target-global-mbox / pageLoad
  decisionScopes: ["__view__"]
}).then(function(result) {
  // Check if content (propositions) were returned
  if (result.propositions) {
    var retrievedPropositions = result.propositions;
    // Apply propositions to the page
    return alloy("applyPropositions", {
      propositions: retrievedPropositions
    }).then(function(applyPropositionsResult) {
      var renderedPropositions = applyPropositionsResult.propositions;
      // Send a display notification with the sendEvent command
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
  }
});
```

+++

>[!NOTE]
>
>Het is mogelijk om [&#x200B; manueel wijzigingen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=nl-NL#manually-rendering-content) terug te geven die in de Visuele Composer van de Ervaring worden gemaakt. Handmatige rendering van op VEC gebaseerde wijzigingen komt niet vaak voor. Controleer of uw at.js-implementatie de functie `getOffers()` gebruikt om handmatig een Target `pageLoad` -aanvraag uit te voeren zonder `applyOffers()` te gebruiken om de inhoud op de pagina toe te passen.

De SDK van het Web van het Platform biedt ontwikkelaars heel wat flexibiliteit met het vragen van en het teruggeven van inhoud aan. Verwijs naar de [&#x200B; specifieke documentatie over het teruggeven van gepersonaliseerde inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=nl-NL) voor extra opties en details.

## Voorbeeld van implementatie

De basisimplementatie van Web SDK van het Platform is nu voltooid.

>[!BEGINTABS]

>[!TAB  JavaScript ]

JavaScript-voorbeeld met automatische rendering van Target-inhoud:

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

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
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
    
    // Send an event to the Adobe edge network and render Target content automatically 
    alloy("sendEvent", {
      "renderDecisions": true
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


>[!TAB  Markeringen ]

Hiermee wordt de voorbeeldpagina gecodeerd met de automatische rendering van Target-inhoud:


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

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

    <!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
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

Voeg de extensie Adobe Experience Platform Web SDK toe aan tags:

![&#x200B; voeg de uitbreiding van SDK van het Web van Adobe Experience Platform &#x200B;](assets/library-tags-addExtension.png){zoomable="yes"} toe

Voeg de gewenste configuraties toe:
![&#x200B; vormend de de migratieopties van de de marktextensie van SDK van het Web &#x200B;](assets/tags-config-migration.png){zoomable="yes"}

Maak een regel met een [!UICONTROL Send event] -handeling en [!UICONTROL Render visual personalization decisions] geselecteerd:
![&#x200B; verzend een gebeurtenis met Render Personalizations die in markeringen worden geselecteerd &#x200B;](assets/vec-sendEvent-renderTrue.png){zoomable="yes"}

>[!ENDTABS]

Daarna, leer hoe te om te verzoeken en [&#x200B; vorm-gebaseerde activiteiten van het Doel &#x200B;](render-form-based-activities.md) teruggeven.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=nl#M463) te posten.

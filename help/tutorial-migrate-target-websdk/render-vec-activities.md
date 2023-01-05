---
title: VEC-activiteiten renderen | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u composer-activiteiten voor visuele beleving ophaalt en toepast met een Web SDK-implementatie van Adobe Target.
feature: Visual Experience Composer (VEC),Implement Client-side,APIs/SDKs,at.js,AEP Web SDK, Web SDK,Implementation
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 0%

---

# Adobe Target Visual Experience Composer (VEC)-activiteiten renderen

De doelactiviteiten worden opstelling gebruikend of Visual Experience Composer (VEC) of op vorm-gebaseerde composer. De SDK van het Web van het Platform kan op VEC-Gebaseerde activiteiten op de pagina enkel zoals at.js terugwinnen en toepassen. Voor dit onderdeel van de migratie gaat u als volgt te werk:

* Installeer indien nodig de Visual Editing Helper-browserextensie
* Een `sendEvent` vraag met het Web SDK van het Platform om activiteiten te verzoeken.
* Werk om het even welke verwijzingen van uw at.js implementatie bij die gebruiken `getOffers()` om een Doel uit te voeren `pageLoad` verzoek.

## Visuele bewerkingsfunctie voor de browserextensie van Helper

Met de Adobe Experience Cloud Visual Editing Helper-browserextensie voor Google Chrome kunt u websites betrouwbaar laden binnen de Adobe Target Visual Experience Composer (VEC) voor een snelle auteur en QA-webbeleving.

De visuele het Uitgeven browser van Helper uitbreiding werkt met websites die at.js of het Web SDK van het Platform gebruiken.

>[!IMPORTANT]
>
>De nieuwe Visuele het Uitgeven uitbreiding van de Helper vervangt vorige [Doel VEC Helper-browserextensie](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html). Als de oudere uitbreiding van de Helper VEC geïnstalleerd is, zou het moeten worden verwijderd of worden onbruikbaar gemaakt alvorens de Visuele Uitgevende uitbreiding van de Helper te gebruiken.

### Vraag de Visual Editing Helper aan en installeer deze

1. Ga naar de [Adobe Experience Cloud Visual Editing Helper-browserextensie in de Chrome Web Store](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
1. Klik op Toevoegen aan **Chroom** > **Extensie toevoegen**.
1. Open VEC in Doel.
1. Als u de extensie wilt gebruiken, klikt u op het pictogram voor de extensie van de browser van de visuele bewerkingshulp ![Pictogram Visuele bewerkingsextensie](assets/VEC-Helper.png) in de werkbalk van uw Chrome-browser in de modus VEC of QA.

De visuele het Uitgeven Helper wordt automatisch toegelaten wanneer een website in het Doel VEC aan macht authoring wordt geopend. De extensie heeft geen voorwaardelijke instellingen. De extensie verwerkt automatisch alle instellingen, inclusief de instellingen voor SameSite-cookies.

Raadpleeg de speciale documentatie voor meer informatie over de [De extensie Visuele bewerkingshulp](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html) en [het oplossen van problemen de Visuele Composer van de Ervaring](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/troubleshoot-composer.html).

## Inhoud automatisch aanvragen en toepassen

Nadat SDK van het Web van het Platform op de pagina wordt gevormd, kunt u inhoud van Doel verzoeken. In tegenstelling tot at.js die kan worden gevormd om inhoud automatisch te verzoeken wanneer de bibliotheek laadt, vereist het Web SDK van het Platform u uitdrukkelijk om een bevel uit te voeren.

Als uw at.js-implementatie de `pageLoadEnabled` instellen op `true` die automatische teruggave van op VEC-Gebaseerde activiteiten toelaat, dan zou u het volgende uitvoeren `sendEvent` bevel met het Web SDK van het Platform:

```Javascript
alloy("sendEvent", {
  "renderDecisions": true
});
```

>[!TIP]
>
> Wanneer het gebruiken van de markeringseigenschap (vroeger Lancering) om Web SDK uit te voeren, &quot;sendEvent&quot;bevelen voor VEC activiteiten kan in een regel worden uitgevoerd gebruikend [!UICONTROL Gebeurtenis Send] actietype met de [!UICONTROL Besluiten over visuele personalisatie renderen] geselecteerd.

Wanneer SDK van het Web van het Platform een activiteit aan de pagina met teruggeeft `renderDecisions` instellen op `true`Een extra meldingsaanroep wordt automatisch geactiveerd om een indruk te wekken en de bezoeker aan de activiteit toe te wijzen. Deze vraag gebruikt een gebeurtenistype met de waarde `decisioning.propositionDisplay`.

![De vraag van SDK van het Web van het Platform verhogend een impositie van het Doel](assets/target-impression-call.png)

## Inhoud aanvragen en op aanvraag toepassen

Sommige Target at.js-implementaties hebben mogelijk `pageLoadEnabled` instellen op `false` en gebruikt in plaats daarvan de `getOffers()` functie om een `pageLoad` verzoek. Dit type opstelling wordt gebruikt als uw implementatie extra verwerking van vereist `getOffers()` antwoord alvorens inhoud op de pagina toe te passen of om inhoud voor veelvoudige plaatsen in één enkele vraag te verzoeken.

De volgende code gebruikt `getOffers()` en `applyOffers()` om VEC-gebaseerde activiteiten op verzoek toe te passen in plaats van automatisch bij het laden van de bibliotheek.

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

De SDK van het Web Platform heeft geen specifieke `pageLoad` gebeurtenis. Alle aanvragen voor doelinhoud worden beheerd met de `decisionScopes` met de `sendEvent` gebruiken. De `__view__` het toepassingsgebied dient het doel van `pageLoad` verzoek. Een equivalente Platform Web SDK `sendEvent` de aanpak zou als volgt zijn :

1. Een `sendEvent` bevat de opdracht `__view__` beslissingsbereik
1. De geretourneerde inhoud met de opdracht `applyPropositions` command
1. Een `sendEvent` gebruiken met de `decisioning.propositionDisplay` gebeurtenistype en propositiegegevens om een indruk te vergroten

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

>[!NOTE]
>
>Het is mogelijk [wijzigingen handmatig renderen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content) gemaakt in Visual Experience Composer. Handmatige rendering van op VEC gebaseerde wijzigingen komt niet vaak voor. Controleren of de implementatie van uw at.js gebruikmaakt van de `getOffers()` functie om een Doel manueel uit te voeren `pageLoad` aanvraag zonder gebruik te maken van `applyOffers()` om de inhoud toe te passen op de pagina.

De SDK van het Web van de Platform biedt ontwikkelaars een grote flexibiliteit met het vragen van en het teruggeven van inhoud aan. Zie de [speciale documentatie over het renderen van gepersonaliseerde inhoud](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) voor aanvullende opties en details.

## Voorbeeld van implementatie

De basisimplementatie van SDK van het Web SDK van het Platform is nu volledig. Onze basisvoorbeeldpagina met automatische functionaliteit voor het renderen van doelinhoud moet er als volgt uitzien:

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

>[!TIP]
>
> Wanneer het gebruiken van de markeringseigenschap (vroeger Lancering) om Web SDK uit te voeren, vervangt de markeringen bedden code de basiscode van het Web SDK van het Platform, &quot;het Web SDK van het Platform dat asynchroon wordt geladen&quot;, en &quot;vormt het Web SDK van het Platform&quot;secties hierboven. De opdracht &#39;sendEvent&#39; wordt uitgevoerd in een regel met de opdracht [!UICONTROL Gebeurtenis Send] actietype met de [!UICONTROL Besluiten over visuele personalisatie renderen] geselecteerd.

## De activiteiten van de bouw met de Visuele het Uitgeven browser van de Helper uitbreiding

Met de Adobe Experience Cloud Visual Editing Helper-browserextensie voor Google Chrome kunt u websites betrouwbaar laden binnen de Adobe Target Visual Experience Composer (VEC) voor een snelle auteur en QA-webbeleving.

De visuele het Uitgeven browser van Helper uitbreiding werkt met websites die at.js of het Web SDK van het Platform gebruiken.

>[!IMPORTANT]
>
>De nieuwe Visuele het Uitgeven uitbreiding van de Helper vervangt vorige [Doel VEC Helper-browserextensie](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html). Als de oudere uitbreiding van de Helper VEC geïnstalleerd is, zou het moeten worden verwijderd of worden onbruikbaar gemaakt alvorens de Visuele Uitgevende uitbreiding van de Helper te gebruiken.

### Vraag de Visual Editing Helper aan en installeer deze

1. Ga naar de [Adobe Experience Cloud Visual Editing Helper-browserextensie in de Chrome Web Store](https://chrome.google.com/webstore/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
1. Klik op Toevoegen aan **Chroom** > **Extensie toevoegen**.
1. Open VEC in Doel.
1. Als u de extensie wilt gebruiken, klikt u op het pictogram van de extensie van de browser van de visuele bewerkingsfunctie (het pictogram voor het bewerken van extensies) op de werkbalk van de Chrome-browser terwijl u zich in de modus VEC of QA bevindt.

De visuele het Uitgeven Helper wordt automatisch toegelaten wanneer een website in het Doel VEC wordt geopend om auteursrecht te steunen. De extensie heeft geen voorwaardelijke instellingen. De extensie verwerkt automatisch alle instellingen, inclusief de instellingen voor SameSite-cookies.

Raadpleeg de speciale documentatie voor meer informatie over de [De extensie Visuele bewerkingshulp](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html) en [het oplossen van problemen de Visuele Composer van de Ervaring](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/troubleshoot-composer.html).

Leer nu hoe u kunt aanvragen en [formuliergebaseerde doelactiviteiten weergeven](render-form-based-activities.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).

---
title: De bibliotheek vervangen | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een Adobe Target-implementatie migreert van at.js 2.x naar Adobe Experience Platform Web SDK. De onderwerpen omvatten bibliotheekoverzicht, implementatieverschillen, en andere opmerkelijke callouts.
exl-id: dfafa132-376a-475d-a467-9bc2f0a414cf
source-git-commit: 07c3c5b3f45eeb02e94a25dbd164b7397cb7869d
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---

# Vervang de bibliotheek at.js met Platform Web SDK

Leer hoe u uw on-page Adobe Target-implementatie kunt vervangen om te migreren van at.js naar Platform Web SDK. Een basisvervanging bestaat uit de volgende stappen:

* Controleer uw beheerinstellingen voor Doel en noteer uw IMS-organisatie-id
* Vervang de bibliotheek at.js met het Web SDK van het Platform
* Het vooraf verbergende fragment bijwerken voor synchrone bibliotheekimplementaties
* Vorm de SDK van het Web van het Platform

>[!NOTE]
>
>De gegeven voorbeelden zijn ter illustratie en uw daadwerkelijke implementatie van het Doel kan variëren. Als uw bestaande implementatie van het Doel de markeringsmanager van de Inzameling van Gegevens van de Adobe gebruikt, kunt u ook naar het [ de implementatieleerprogramma van het Doel van het Web SDK van het Platform ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html) voor extra informatie verwijzen.


## Doelbeheerinstellingen controleren

De eerste stap om Doel naar het Web SDK van het Platform te migreren is uw montages in de sectie van het Doel te herzien **[!UICONTROL Administration]** van de interface.

### [!UICONTROL Implementation]

#### [!UICONTROL Account details]

* **[!UICONTROL IMS Organization Id]** - Maak nota van deze waarde aangezien het wordt vereist om het Web SDK van het Platform te vormen.
* **[!UICONTROL On-Device Decisioning]** - Deze functie wordt niet ondersteund door de Platform Web SDK. Deze instelling kan worden uitgeschakeld nadat u hebt gemigreerd en als u niet meer at.js gebruikt op een van uw websites of als er op de server geen gevallen zijn waarin het apparaat wordt gebruikt voor het bepalen van het apparaat.

#### [!UICONTROL Implementation methods]

Alle bewerkbare instellingen in de sectie **[!UICONTROL Implementation methods]** zijn alleen van toepassing op at.js. Deze montages worden gebruikt om een aangepaste bibliotheek te produceren at.js voor uw implementatie. Controleer deze instellingen om te controleren of u aangepaste code hebt of cookies van de eerste en derde partij instelt voor gebruik in andere domeinen.

De instelling **[!UICONTROL Profile Lifetime]** kan alleen worden gewijzigd via de Adobe Klantenservice. De levensduur van het profiel Doelbezoeker wordt niet beïnvloed door uw implementatiebenadering. Zowel at.js als Platform Web SDK gebruiken het zelfde leven van het bezoekersprofiel.

#### [!UICONTROL Privacy]

* **[!UICONTROL Obfuscate Visitor IP addresses]** - Deze instelling is van invloed op de oriëntatiemogelijkheden. Zowel gebruiken at.js als de SDK van het Web van het Platform de zelfde achterste IP verduisteringsmontages voor het groeperen.

### [!UICONTROL Environments]

De SDK van het Web van het Platform gebruikt een configuratie van de gegevensstroom die u toestaat om [!UICONTROL Environment ID] voor afzonderlijke ontwikkeling, het opvoeren, en de stromen van productiegegevens uitdrukkelijk te bepalen. Het belangrijkste gebruiksgeval voor deze configuratie is voor mobiele app-implementaties waar URL&#39;s niet bestaan om omgevingen gemakkelijk te onderscheiden. De instelling is optioneel, maar kan worden gebruikt om ervoor te zorgen dat alle aanvragen correct worden gekoppeld aan de opgegeven omgeving. Dit verschilt van een implementatie at.js waar u de milieu&#39;s van het Doel moet toewijzen die op domeinen en de regels van de gastheergroep worden gebaseerd.

>[!NOTE]
>
>Als identiteitskaart van het Milieu niet in de gegevensstroomconfiguratie wordt gespecificeerd, dan gebruikt het Doel de domein-aan-milieu afbeelding zoals die in de **wordt gespecificeerd Gastheren** sectie.

Voor meer informatie, verwijs naar de ](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) gids van de de configuratie van de 0} datastream en van het Doel [ Gastheren ](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html) documentatie.[

## De SDK van het Web Platform implementeren

De functionaliteit van het doel wordt verstrekt door zowel at.js als Platform Web SDK. Als beide bibliotheken tegelijkertijd worden gebruikt, kan het zijn dat er problemen optreden bij het renderen en bijhouden van bibliotheken. Om met succes aan het Web SDK van het Platform te migreren, moet de eerste stap at.js verwijderen en het vervangen met het Web SDK van het Platform (alloy.js).

Veronderstel een eenvoudige implementatie van het Doel met at.js:

* Een gegevenslaag dichtbij de bovenkant van de pagina verstrekt informatie voor Doel en andere toepassingen
* Een of meer hulpbibliotheken van derden waarvan de mogelijkheden kunnen worden gebruikt in doelactiviteiten (bijvoorbeeld jQuery)
* Een voorverborgen fragment om flikkering te beperken
* De bibliotheek Doel at.js laadt asynchroon met standaardinstellingen om activiteiten automatisch aan te vragen en weer te geven:

+++at.js voorbeeldimplementatie op een HTML-pagina

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
  <!--prehiding snippet for Target with asynchronous deployment-->
  <script>
    ;(function(win, doc, style, timeout) {
      var STYLE_ID = 'at-body-style';

      function getParent() {
        return doc.getElementsByTagName('head')[0];
      }

      function addStyle(parent, id, def) {
        if (!parent) {
          return;
        }
        var style = doc.createElement('style');
        style.id = id;
        style.innerHTML = def;
        parent.appendChild(style);
      }

      function removeStyle(parent, id) {
        if (!parent) {
          return;
        }
        var style = doc.getElementById(id);
        if (!style) {
          return;
        }
        parent.removeChild(style);
      }
      addStyle(getParent(), STYLE_ID, style);
      setTimeout(function() {
        removeStyle(getParent(), STYLE_ID);
      }, timeout);
    }(window, document, "body {opacity: 0 !important}", 3000));
  </script>
  <!--Target at.js library loaded asynchonously-->
  <script src="/libraries/at.js" async></script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div>Homepage Hero Banner Content</div>
</body>
</html>
```

+++

Om Doel te bevorderen om het Web SDK van het Platform te gebruiken, verwijder eerst at.js:

```HTML
<!--Target at.js library loaded asynchonously-->
<script src="/libraries/at.js" async></script>
```

En vervang dit door een geldige JavsScript-bibliotheek of door uw tags insluitcode en de Adobe Experience Platform Web SDK-extensie:

>[!BEGINTABS]

>[!TAB  JavaScript ]

```HTML
<!--Platform Web SDK base code-->
<script>
  !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
  []).push(o),n[o]=function(){var u=arguments;return new Promise(
  function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
  (window,["alloy"]);
</script>
<!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
<script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
```

>[!TAB  Markeringen ]

```HTML
<!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
<script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
```

Voeg in de eigenschap tag de extensie Adobe Experience Platform Web SDK toe:

![ voeg de uitbreiding van SDK van het Web van Adobe Experience Platform ](assets/library-tags-addExtension.png){zoomable="yes"} toe


>[!ENDTABS]

Voor de vooraf samengestelde zelfstandige versie is een &quot;basiscode&quot; vereist die rechtstreeks aan de pagina wordt toegevoegd en die een algemene functie met de naam legering maakt. Gebruik deze functie om te communiceren met de SDK. Als u de algemene functie een andere naam wilt geven, wijzigt u de naam `alloy` .

Verwijs naar [ Installerend de 1} documentatie van SDK van het Web van het Platform {voor extra details en plaatsingsopties.](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)


## Inhoud vooraf verbergen-benadering bijwerken

De implementatie van SDK van het Web van het Platform kan een prehide fragment vereisen afhankelijk van of de bibliotheek asynchroon of synchroon wordt geladen.

### Asynchrone implementatie

Net als bij at.js, als de bibliotheek van SDK van het Web van het Platform asynchroon laadt, kan de pagina beëindigen teruggevend alvorens het Doel een inhoudsruil heeft uitgevoerd. Dit gedrag kan leiden tot wat &quot;flikkering&quot;wordt genoemd waar de standaardinhoud kort toont alvorens door de gepersonaliseerde inhoud wordt vervangen die door Doel wordt gespecificeerd. Als u dit flikkering wilt vermijden, raadt de Adobe aan een speciaal prehide fragment toe te voegen vlak vóór de asynchrone scriptverwijzing of -tags van het Web SDK van het Platform.

Als uw implementatie asynchroon is, zoals in de bovenstaande voorbeelden, vervangt u het voorverborgen fragment at.js door de onderstaande versie die compatibel is met de Platform Web SDK:

```HTML
<!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
<script>
  !function(e,a,n,t){var i=e.head;if(i){
  if (a) return;
  var o=e.createElement("style");
  o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
  (document, document.location.href.indexOf("mboxEdit") !== -1, "body { opacity: 0 !important }", 3000);
</script>
```

Het voorverbergende fragment maakt een stijltag in de kop van de pagina met de CSS-definitie van uw keuze. Deze stijlmarkering wordt verwijderd wanneer een reactie van Doel wordt ontvangen, of de onderbreking wordt bereikt.

Het gedrag voor het voorverbergen wordt bepaald door twee configuraties helemaal aan het einde van het fragment.

* `body { opacity: 0 !important }` geeft de CSS-definitie op die moet worden gebruikt voor het voorverbergen totdat Doel wordt geladen. Standaard is de hele pagina verborgen. U kunt deze definitie bijwerken naar de kiezers die u vooraf wilt verbergen en naar de manier waarop u deze wilt verbergen. U kunt meerdere definities opnemen, aangezien deze waarde eenvoudig is wat er in de voorverborgen stijltag wordt ingevoegd. Als u een gemakkelijk identificeerbaar containerelement hebt dat de inhoud onder uw navigatie verpakt, kunt u deze instelling gebruiken om het vooraf verbergen tot dat containerelement te beperken.

* `3000` geeft de time-out op in milliseconden voor het voorverbergen. Als een reactie van Target niet vóór de time-out wordt ontvangen, wordt de vooraf verborgen stijltag verwijderd. Het bereiken van deze time-out moet zeldzaam zijn.

>[!IMPORTANT]
>
>Ben zeker om het correcte fragment voor het Web SDK van het Platform te gebruiken aangezien het een verschillende stijlidentiteitskaart van `alloy-prehiding` gebruikt. Als het voorverborgen fragment voor at.js wordt gebruikt, werkt het mogelijk niet correct.

### Synchrone implementatie

De Adobe adviseert asynchroon het uitvoeren van het Web SDK van het Platform voor de beste algemene paginaprestaties. Als de insluitcode van de bibliotheek alloy.js of -tags echter synchroon wordt geladen, is het voorverborgen fragment niet vereist. In plaats daarvan, wordt de prehide stijl gespecificeerd in de configuratie van SDK van het Web van het Platform.

De prehide stijl voor synchrone implementaties kan worden gevormd gebruikend de [`prehidingStyle` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) optie. De configuratie van SDK van het Web van het platform is behandeld in de volgende sectie.

Om meer over te leren hoe SDK van het Web van het Platform flikkering kan beheren, kunt u naar de gidsensectie verwijzen: [ die flicker voor gepersonaliseerde ervaringen beheert ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/manage-flicker.html)

## Vorm de SDK van het Web van het Platform

De SDK van het Web van het Platform moet op elke paginading worden gevormd. Het volgende voorbeeld veronderstelt dat de volledige plaats aan het Web SDK van het Platform in één enkele plaatsing wordt bevorderd:

>[!BEGINTABS]

>[!TAB  JavaScript ]

De opdracht `configure` moet altijd de eerste aangeroepen SDK-opdracht zijn. De `edgeConfigId` is de [!UICONTROL Datastream ID]

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
});
```

>[!TAB  Markeringen ]

In labels-implementaties worden veel velden automatisch ingevuld of kunnen deze worden geselecteerd in vervolgkeuzemenu&#39;s. U kunt verschillende platforms [!UICONTROL sandboxes] en [!UICONTROL datastreams] selecteren voor elke omgeving. De gegevensstroom wordt gewijzigd op basis van de status van de tagbibliotheek tijdens het publicatieproces.

![ vormend de de markeringsuitbreiding van SDK van het Web ](assets/tags-config.png){zoomable="yes"}
>[!ENDTABS]

Als u van om van at.js aan het Web SDK van het Platform op een pagina-door-pagina basis van plan bent te migreren, dan worden de volgende configuratieopties vereist:


>[!BEGINTABS]

>[!TAB  JavaScript ]

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg",
  "targetMigrationEnabled":true,
  "idMigrationEnabled":true
});
```

>[!TAB  Markeringen ]

![ vormend de de migratieopties van de de marktextensie van SDK van het Web ](assets/tags-config-migration.png){zoomable="yes"}

>[!ENDTABS]

De belangrijkste configuratieopties met betrekking tot Target worden hieronder beschreven:

| Optie | Beschrijving | Voorbeeldwaarde |
| --- | --- | --- |
| `edgeConfigId` | De gegevensstroom-id | `ebebf826-a01f-4458-8cec-ef61de241c93` |
| `orgId` | Adobe Experience Cloud-organisatie-id | `ADB3LETTERSANDNUMBERS@AdobeOrg` |
| `targetMigrationEnabled` | Gebruik deze optie om de SDK van het Web toe te laten om de erfenis mbox en mboxEdgeCluster koekjes te lezen en te schrijven die door at.js worden gebruikt. Dit helpt u het bezoekersprofiel houden terwijl het bewegen van een pagina die SDK van het Web aan een pagina gebruikt die de bibliotheek at.js en de tegenovergestelde manier gebruikt. | `true` |
| `idMigrationEnabled` | Indien waar (true), leest de SDK oude AMCV-cookies en stelt deze in. Deze optie helpt met het overstappen aan het gebruiken van het Web SDK van het Platform terwijl sommige delen van de plaats misschien nog Visitor.js gebruiken. | `true` |
| `thirdPartyCookiesEnabled` | Hiermee schakelt u het instellen van cookies van derden voor de Adobe in. De SDK kan de bezoekersidentiteitskaart in een derdecontext voortzetten om de zelfde bezoekersidentiteitskaart toe te laten om over plaatsen worden gebruikt. Gebruik deze optie als u meerdere sites hebt, maar deze optie is soms niet gewenst vanwege privacyredenen. | `true` |
| `prehidingStyle` | Wordt gebruikt om een CSS-stijldefinitie te maken die inhoudsgebieden van uw webpagina verbergt terwijl gepersonaliseerde inhoud van de server wordt geladen. Dit wordt slechts gebruikt met synchrone plaatsingen van SDK. | `body { opacity: 0 !important }` |

Voor een volledige lijst van opties, verwijs naar [ vormend de gids van SDK van het Web van het Platform ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html).

## Voorbeeld van implementatie

Zodra het Web SDK van het Platform behoorlijk op zijn plaats is, zou de voorbeeldpagina als dit kijken.

>[!BEGINTABS]

>[!TAB  JavaScript ]

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
  <script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
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

Paginacode:

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

![ voeg de uitbreiding van SDK van het Web van Adobe Experience Platform ](assets/library-tags-addExtension.png){zoomable="yes"} toe

Voeg de gewenste configuraties toe:
![ vormend de de migratieopties van de de marktextensie van SDK van het Web ](assets/tags-config-migration.png){zoomable="yes"}


>[!ENDTABS]



Het is belangrijk om op te merken dat eenvoudig het omvatten van en het vormen van de bibliotheek van SDK van het Web van het Platform zoals hierboven getoond geen netwerkvraag aan het Netwerk van Adobe Edge uitvoert.

Daarna, leer hoe te [ verzoeken en op VEC-Gebaseerde activiteiten ](render-vec-activities.md) op de pagina toepassen.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

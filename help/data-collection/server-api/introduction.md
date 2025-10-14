---
title: Basisinleiding tot API's
description: Een inleiding aan de Interfaces van de Programmering van de Toepassing
activity: understand
doc-type: article
feature-set: Experience Platform
feature: Server API,API,Data Collection,Integrations
level: Beginner
role: User, Data Engineer, Developer
solution: Data Collection
topic: Integrations
exl-id: 9607e641-b0d5-49c1-b319-32ed0720e715
source-git-commit: ac07d62cf4bfb6a9a8b383bbfae093304d008b5f
workflow-type: tm+mt
source-wordcount: '2086'
ht-degree: 0%

---

# API 101 - Een basisinleiding voor API&#39;s

API staat voor Application Programming Interface. Het betekent enkel wat het zegt-er interfaces tussen programma&#39;s zijn en deze interfaces staan die programma&#39;s toe om te communiceren. Wanneer programmeurs softwaretoepassingen ontwikkelen, hebben zij vaak hun software nodig om met andere software of hardware te communiceren. De API bepaalt wat, hoe, wanneer, waar, en waarom voor die mededelingen en interactie.

API&#39;s zijn een manier om zakelijke uitdagingen met software op te lossen. In de meeste bedrijven is dat een gezamenlijke inspanning. Samenwerken is altijd gemakkelijker met een gedeeld begrip van zeer belangrijke termijnen, concepten, en stappen.

Als u nadenkt over het klikken op een koppeling op een webpagina, gebruikt de browser heel wat API&#39;s wanneer u op de koppeling klikt. De browser herkent de klik, vraagt om de pagina die u wilt bezoeken, haalt de pagina op via internet en geeft deze vervolgens weer op uw scherm. Er zijn veel kleinere tussenliggende stappen, maar uw browser is software die communiceert en interageert met verschillende API&#39;s, alleen om u een webpagina te laten zien. In dit artikel zullen we termen, concepten en stappen markeren die belangrijk zijn bij het gebruik van of het bespreken van API&#39;s.

Aan het einde van dit artikel hebt u een duidelijk inzicht in deze grondbegrippen, concepten en stappen nodig. API-documentatie kan uitgebreid zijn en discussies over het gebruik van API&#39;s voor het aanpakken van specifieke gebruiksgevallen kunnen zeer gedetailleerd worden. Het navigeren van documentatie en het bespreken van APIs is gemakkelijker en productiever met duidelijke grondbeginselen en gedeeld begrip.

>[!NOTE]
>
> Terwijl er veel API&#39;s zijn, is de focus hier op API&#39;s voor het web en de browser: in feite wanneer een softwaretoepassing via internet met een andere toepassing communiceert.

## API Voorwaarden en concepten

Wat betekent een woord of uitdrukking, en hoe kan ik er eenvoudig over denken? In een API betekent het &quot;toepassings&quot;deel een softwaretoepassing, of programma. In het gedeelte &quot;Programmeerinterface&quot; wordt aangegeven hoe en waar een toepassing voor bepaalde doeleinden met een andere toepassing communiceert. Wanneer u in ons voorbeeld van de webpagina op een koppeling klikt, verzendt de browser een aanvraag naar een server voor de webpagina.

![&#x200B; Beeld van hyperlink met bestemmingsURL &#x200B;](../assets/api101-link-destination.png)

In dit schermafbeelding zweeft de muiscursor boven de Adobe Experience Platform-koppeling. Onderaan ziet u de statusbalk van de webbrowser met het &quot;adres&quot; van de pagina die de browser krijgt. Met andere woorden, als je op de Adobe Experience Platform link klikt, vertelt de browser dat ze die pagina voor mij krijgt zodat ik hem hier op mijn scherm kan zien.

Wanneer op een koppeling wordt geklikt, vraagt de browser een server om een pagina op te halen. Dit is een `GET` -aanvraag, een van de aanvraagmethoden die veel worden gebruikt voor web-API&#39;s. Eén ding dat de browser aan het verzoek moet voldoen, is het adres van de pagina - waar bevindt het zich op het web?

### Delen van een URL

![&#x200B; Browser adresbar met URL &#x200B;](../assets/api101-address-bar.png)

De meeste browsers hebben een &quot;adresbar&quot;die sommige of al &quot;adres&quot;voor een Web-pagina toont. Wanneer browser &quot;krijgt&quot;de pagina voor de verbinding wij klikte, toont het het &quot;adres&quot;van de pagina in deze adresbar. Wat is het &quot;adres&quot; van een webpagina?

Dat `https://business.adobe.com/products/experience-platform/adobe-experience-platform.html` hierboven is het adres van een pagina op het web. Het wordt een URL of Uniform Resource Locator genoemd. URL&#39;s kunnen verwijzen naar pagina&#39;s zoals deze, afbeeldingsbestanden, video&#39;s of andere bestandstypen.

![&#x200B; Delen van een URL &#x200B;](../assets/api101-url-parts.jpg)

Dit adres, de URL, bevat specifieke onderdelen die erg relevant zijn voor API&#39;s voor het web en de browser.

**Regeling**

De bovenstaande `scheme` wordt ook een `protocol` met web-API&#39;s genoemd en is doorgaans ofwel `http` ofwel `https` . HTTP of HyperText Transfer Protocol is hoe bronnen zoals webpagina&#39;s worden overgebracht van een webserver naar een webbrowser. HTTPS is de veilige versie, waarbij de overdracht via internet plaatsvindt met behulp van beveiliging die bedoeld is om interferentie met de overdracht van de bron te voorkomen. Het is gebruikelijk om een klein slotpictogram in de browser adresbar te zien wanneer het bekijken van een pagina over HTTPS.

Voor web-API&#39;s gebeurt de overdracht van deze bronnen via HTTP-aanvragen, met andere woorden via HTTP.

**Gastheren en Domeinen**

`business.adobe.com` is de host van de bron die wordt aangevraagd. Wanneer op de voorbeeldkoppeling wordt geklikt, gebruikt de browser dit gedeelte van de URL om de server te zoeken waarop de pagina wordt gehost. Het is niet altijd precies het zelfde als de Webserver, maar op een basisniveau kunnen wij het als server zien waar browser de pagina zal krijgen wij vroegen.

De namen van het domein maken deel uit van het Systeem van de Naam van het Domein, beter gekend als DNS. De meeste mensen denken aan `adobe.com` of `example.com` als een &quot;domeinnaam&quot;, maar er zijn onderdelen die relevant zijn voor API&#39;s. `www.adobe.com` en `business.adobe.com` kunnen domeinnamen worden genoemd, maar de onderdelen `www.` en `business.` worden subdomeinen genoemd. API&#39;s werken vaak samen met een URL die een subdomein zoals `api.example.com` of `sub.www.example.com` bevat.

Het is zeer gemeenschappelijk om de termijn _gastheer_ te zien verwijzen naar een volledige domeinnaam met inbegrip van om het even welk subdomein zoals `business.adobe.com`. Het is ook gemeenschappelijk om de termijnen _domein_ of _domeinnaam_ te zien wanneer het verwijzen naar een gastheer zonder subdomain als `adobe.com`. Het is hier niet van belang de specifieke voorwaarden voor elk onderdeel en elke variant van een host te herkennen. Maar bewust zijn van dat deze termijnen algemeen worden gebruikt is belangrijk zodat kunt u om het even welke relevante details voor uw zaken en besprekingen verduidelijken.

**Oorsprong**

Oorsprong is een andere term om te weten dat die nauw verwant is aan de delen van een URL. Op basisniveau is een oorsprong ruwweg de `scheme` plus de `host` plus de `domain` as `https://business.adobe.com` . Verschillende waarden vertegenwoordigen vaak verschillende oorsprong, zoals `https://business.adobe.com` en `http://business.adobe.com` , zijn niet dezelfde oorsprong omdat ze verschillende schema&#39;s hebben. `https://www.adobe.com` en `https://business.adobe.com` zijn in veel toepassingen ook niet dezelfde oorsprong vanwege de verschillende subdomeinen.

**Weg**

Het laatste beetje in het URL voorbeeld hierboven is `path` aan het middel-pagina in ons voorbeeld. Het `/products/experience-platform/` -onderdeel vertegenwoordigt doorgaans mappen of mappen op de webserver. Net als op onze computers mappen of mappen voor documenten en foto&#39;s staan er ook mappen op webservers voor het ordenen van inhoud. Tot slot is het `/adobe-experience-platform.html` -onderdeel de naam van het bestand, de webpagina.

Er zijn andere meer gedetailleerde delen van een URL die in het volgende deel van deze reeks zullen worden benadrukt.

### API&#39;s van derden

Web API&#39;s worden soms API&#39;s van derden genoemd. Denk aan dit soort zaken als de partijen die bij een transactie betrokken zijn. In ons koppelingsvoorbeeld, bent u-of meer specifiek, uw browser-de eerste partij in het verzoek om de pagina. De webserver is de tweede partij. Waar is de derde?

Het is gebruikelijk dat een webpagina inhoud of bronnen van andere hosts of bronnen bevat. In die gevallen, wanneer uw browser begint de pagina te tonen, doet het een andere reeks verzoeken aan die andere gastheren, of &quot;derden&quot;, die die middelen ontvangen. Dit komt vaak voor, vooral bij media-inhoud zoals video&#39;s of afbeeldingen, maar ook voor gegevens die moeten worden bijgewerkt op het moment dat ze worden weergegeven of gebruikt. Het krijgen van de huidige tijd van dag, het huidige weer, of een gepersonaliseerd welkomstbericht voor een specifieke persoon zijn allen voorbeelden waar een derde API de juiste middelen op het juiste ogenblik kan leveren. Deze aanvragen komen vaak van deze externe API&#39;s.

## Veelvoorkomende toepassingen voor web-API&#39;s

Naast de tijd van de dag, het weer, of gepersonaliseerde inhoud, zijn er vele toepassingen voor Web APIs. Sociaal-mediaplatforms als Twitter, TikTok, Facebook, LinkedIn, Snapchat, Pinterest en andere beschikken over een groot aantal API&#39;s die programmeurs kunnen gebruiken voor hun toepassingen. En natuurlijk, heeft de Adobe ook [&#x200B; een grote verscheidenheid van APIs &#x200B;](https://developer.adobe.com/apis) die de programmeurs gebruiken zodat kan hun software met de producten en de diensten van de Adobe in wisselwerking staan. Softwareproducten en -services hebben via deze API&#39;s toegang tot andere softwareproducten en -services.

## Voorbeeld-API&#39;s

Browser APIs staat programmeurs toe om met eigenschappen van browser direct in wisselwerking te staan. Met de batterij-API kan de software de batterijstatus van een apparaat controleren, zodat het u kan waarschuwen als dat nodig is. Met de klembordAPI kan software kopiëren of plakken met het klembord van uw apparaat. Met de API Volledig scherm kan software de optie presenteren om de weergave op het volledige scherm van het apparaat uit te breiden, zoals YouTube.

Adobe Experience Platform Data Access-API is een web-API waarmee programmeurs toegang hebben tot gegevenssetbestanden van Adobe Experience Platform en deze kunnen downloaden, zodat ze de gegevens van het klantprofiel in hun eigen programma&#39;s kunnen gebruiken. API&#39;s als deze maken vaak deel uit van een softwareautomatiseringsproces waarbij software is geprogrammeerd om een reeks stappen uit te voeren in combinatie met verschillende API&#39;s. Dit kan vaak een aanzienlijke kostenbesparing opleveren in vergelijking met het handmatig uitvoeren van dezelfde stappen.

## API-eindpunten

Wanneer programmeurs een browser of web-API in hun programma&#39;s &#39;gebruiken&#39;, doen ze doorgaans aanvragen om bronnen te verzenden of te ontvangen, zoals onze voorbeeldbrowser die een webpagina aanvraagt. In API-documentatie wordt vaak &quot;eindpunten&quot; voor deze aanvragen vermeld, bijvoorbeeld: `https://platform.adobe.io/data/foundation/export/files/{dataSetFileId}` . Dit is het specifieke patroon of het &quot;eindpunt&quot;van de Toegang API van de Gegevens van het Platform een programmeur zal gebruiken om een datasetdossier te krijgen.

De `{dataSetFileId}` die door deze accolades wordt omringd, vertegenwoordigt een waarde die de programmeur in de aanvraag moet verzenden. De URL in de eigenlijke API-aanvraag zou er dus ongeveer als volgt uitzien: `xyz123brb` moet een geldige id zijn van het gegevensbestand dat de programmeur wil ontvangen.`https://platform.adobe.io/data/foundation/export/files/xyz123brb`

Met andere woorden, net zoals browser een pagina bij een specifieke URL krijgt, krijgen de API verzoeken middelen van, of verzenden middelen naar, een specifiek eindpunt zoals dit datasetvoorbeeld.

## Methoden van HTTP-aanvragen

Op dit punt moet duidelijk zijn dat web-API&#39;s verzoeken indienen voor bronnen zoals webpagina&#39;s of gegevenssets. Zoals de meeste softwareconcepten, volgen deze HTTP- verzoeken herhaalbare patronen. Een verzoek wordt verzonden van een softwaretoepassing naar een andere softwaretoepassing die het verzoek evalueert en dan antwoordt: browser vraagt een pagina van een Webserver en antwoordt met de pagina inhoud.

Het hele proces van verzoek tot antwoord omvat vele kleinere en zeer gedetailleerde stappen, maar de verzoekmethodes zijn duidelijk. De verzoekmethodes bepalen de verrichting die wordt gevraagd.

**`GET`**

De aanvraagmethode `GET` wordt gebruikt bij het aanvragen van een antwoord dat een bron levert, zoals de voorbeelden van onze webpagina en dataset. Wanneer we op een koppeling in een browser klikken of op een koppeling op een mobiel apparaat tikken, vragen we achter de schermen een `GET` -aanvraag.

**`POST`**

De methode `POST` verzendt gegevens met de aanvraag. Het kan vreemd klinken dat een &quot;verzoek&quot;gegevens verzendt, maar het idee is dat het maken van het API verzoek het eindpunt-ontvangende software-vraagt om het verzoek goed te keuren, en in het geval van a `POST`, om de gegevens ook goed te keuren die worden verzonden. De verzonden gegevens worden doorgaans als een database of bestand naar een gegevensopslagruimte geschreven, zodat deze kunnen worden opgeslagen.

**`PUT`**

De aanvraagmethode `PUT` is vergelijkbaar met `POST` omdat deze gegevens verzendt, maar als de gegevens die worden verzonden al op het eindpunt bestaan, werkt a `PUT` de bestaande gegevens bij door deze te vervangen. Een `POST` wordt niet bijgewerkt, het verzendt gewoon, zodat kunnen veelvoudige `POST` verzoeken veelvoudige verslagen van de verzonden gegevens tot stand brengen, in plaats van het bijwerken van om het even welk bestaand verslag.

**`PATCH`**

De aanvraagmethode `PATCH` wordt gebruikt om gegevens te verzenden die een deel van een bestaande record bijwerken, zoals wanneer we ons adres wijzigen door ons accountprofiel bij te werken. Met een `POST` -aanvraag kan een extra profiel worden gemaakt. Met een `PUT` kan het bestaande profiel worden vervangen. Met de `PATCH` -methode werkt u echter gewoon het relevante deel van de bestaande record bij, zoals ons adres.

**`DELETE`**

De aanvraagmethode `DELETE` verwijdert een bron die in de aanvraag is opgegeven, net als wanneer we op een koppeling klikken om ons accountprofiel volledig te verwijderen.

Er zijn verschillende andere methoden, maar dit is een lijst met de meest gebruikte methoden bij het werken met API&#39;s.

### Voorbeeld aanvragen

Nu u de basistermen, concepten en stappen hebt die met API&#39;s samenhangen, kunnen we in de praktijk naar een voorbeeld-API-verzoek kijken.

De pagina in ons browservoorbeeld heeft de URL `https://business.adobe.com/products/experience-platform/adobe-experience-platform.html` . Wanneer op de Adobe Experience Platform-koppeling wordt geklikt, vraagt de browser `GET` om deze pagina. Omdat we de browser hebben om het werk voor ons te doen, hoeven we alleen maar te klikken, maar als een programmeur dat verzoek in een softwaretoepassing wil uitvoeren, moet hij alle vereiste details verstrekken om de API-aanvraag succesvol te kunnen uitvoeren.

Hier is hoe dat in de code zou kunnen kijken:

```js
fetch(
  "https://business.adobe.com/products/experience-platform/adobe-experience-platform.html",
  {
    headers: {
      accept:
        "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
      "accept-language": "en-US,en;q=0.9",
      "sec-ch-ua":
        '" Not A;Brand";v="99", "Chromium";v="101", "Microsoft Edge";v="101"',
      "sec-fetch-dest": "document",
      "sec-fetch-mode": "navigate",
      "sec-fetch-site": "none",
      "sec-fetch-user": "?1",
      "upgrade-insecure-requests": "1",
    },
    referrerPolicy: "strict-origin-when-cross-origin",
    body: null,
    method: "GET",
    mode: "cors",
    credentials: "include",
  }
);
```

In de bovenstaande code ziet u de `URL` -code die de browser aanvraagt, en onderaan ziet u de aanvraagmethode `method: "GET"` . De andere coderegels zijn ook onderdelen van het verzoek, maar vallen buiten het bereik van dit artikel.


*[ API ]: De Interface van de Programmering van de toepassing
*[ URL ]: Het unieke Merkteken van het Middel
*[ HTTP ]: Het Protocol van de Overdracht HyperText
*[ DNS ]: Het Systeem van de Naam van het domein

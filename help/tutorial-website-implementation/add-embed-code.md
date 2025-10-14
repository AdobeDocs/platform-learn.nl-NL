---
title: De insluitcode toevoegen
description: Leer hoe u de insluitcodes van de eigenschap tag ophaalt en deze implementeert in uw website. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: a2959553-2d6a-4c94-a7df-f62b720fd230
source-git-commit: 277f5f2c07bb5818e8c5cc129bef1ec93411c90d
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 0%

---

# De insluitcode toevoegen

In deze les, zult u asynchrone inbedcode van de milieu van de Ontwikkeling van uw markeringsbezit uitvoeren. Tijdens het gebruik leert u over twee belangrijke concepten van tags: omgevingen en insluitingscodes.

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * Platform launch (de Kant van de Cliënt) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * De Server zijde van de platform launch is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=nl-NL)**
> * De configuraties van Edge zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=nl-NL)**

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Haal de insluitcode voor de eigenschap tag op
* Begrijp het verschil tussen een Ontwikkeling, het Opvoeren, en het milieu van de Productie
* Code voor het insluiten van tags toevoegen aan een HTML-document
* Beschrijf de optimale locatie van de code voor het insluiten van tags ten opzichte van andere code in de `<head>` van een HTML-document

## De insluitcode kopiëren

De insluitcode is een `<script>` -tag die u op uw webpagina&#39;s plaatst om de logica die u in tags maakt te laden en uit te voeren. Als u de bibliotheek asynchroon laadt, blijft de browser de pagina laden, wordt de tagbibliotheek opgehaald en parallel uitgevoerd. In dit geval is er slechts één insluitcode die u in `<head>` plaatst. (Wanneer tags synchroon worden geïmplementeerd, zijn er twee insluitcodes die u in de `<head>` plaatst en een andere die u vóór de `</body>` plaatst.)

Klik in het scherm Overzicht van de eigenschap op **[!UICONTROL Environments]** in de linkernavigatie om naar de pagina met omgevingen te gaan. Merk op dat de milieu&#39;s van de Ontwikkeling, van het Staging, en van de Productie voor u vooraf zijn gecreeerd.

![&#x200B; klik Milieu&#39;s in hoogste nav &#x200B;](images/launch-environments.png)

De ontwikkeling, het Staging, en de milieu&#39;s van de Productie beantwoorden aan de typische milieu&#39;s in het codeontwikkeling en versieproces. De code wordt eerst geschreven door een ontwikkelaar in een milieu van de Ontwikkeling. Wanneer zij hun werk hebben voltooid, sturen zij het naar een het Opvoeren milieu voor QA en andere teams om te herzien. Zodra de kwaliteitscontrole en andere teams tevreden zijn, wordt de code vervolgens gepubliceerd naar de productieomgeving. Dit is de openbare omgeving die uw bezoekers ervaren wanneer ze naar uw website komen.

De markeringen staan extra milieu&#39;s van de Ontwikkeling toe, die in grote organisaties nuttig zijn waarin de veelvoudige ontwikkelaars aan verschillende projecten tezelfdertijd werken.

Dit zijn de enige omgevingen die we nodig hebben om de zelfstudie te voltooien. Met omgevingen kunt u verschillende werkversies van uw tagbibliotheken gebruiken die op verschillende URL&#39;s worden gehost, zodat u veilig nieuwe functies kunt toevoegen en beschikbaar kunt maken voor de juiste gebruikers (zoals ontwikkelaars, QA-technici, het publiek, enz.) op het juiste moment.

Kopieer nu de insluitcode:

1. In de **[!UICONTROL Development]** rij, klik het Install pictogram ![&#x200B; installeren pictogram &#x200B;](images/launch-installIcon.png) om modaal te openen.

1. Merk op dat de markeringen aan de asynchrone insluitcodes zullen gebrek

1. Klik het pictogram van het Exemplaar ![&#x200B; pictogram van het Exemplaar &#x200B;](images/launch-copyIcon.png) om de ingebedde code aan uw klembord te kopiëren.

1. Klik op **[!UICONTROL Close]** om het modaal te sluiten.

   ![&#x200B; installeer pictogram &#x200B;](images/launch-copyInstallCode.png)

## De insluitcode implementeren in de `<head>` van de HTML-voorbeeldpagina

De insluitcode moet worden geïmplementeerd in het element `<head>` van alle HTML-pagina&#39;s die de eigenschap delen. U hebt mogelijk een of meerdere sjabloonbestanden die de `<head>` globaal op de site beheren, waardoor het eenvoudig is tags toe te voegen.

Kopieer de HTML-voorbeeldpaginacode en plak deze in een code-editor als u dat nog niet hebt gedaan. [&#x200B; Haakjes &#x200B;](https://brackets.io/) is een vrije, open bronredacteur als u nodig hebt.

+++HTML-voorbeeldcode

```html
<!doctype html>
<html lang="en">
<head>
    <title>Tags: Sample HTML Page</title>
    <!--Preconnect and DNS-Prefetch to improve page load time. REPLACE "techmarketingdemos" WITH YOUR OWN AAM PARTNER ID, TARGET CLIENT CODE, AND ANALYTICS TRACKING SERVER-->
    <link rel="preconnect" href="//dpm.demdex.net">
    <link rel="preconnect" href="//fast.techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//cm.everesttech.net">
    <link rel="preconnect" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="preconnect" href="//techmarketingdemos.sc.omtrdc.net">
    <link rel="dns-prefetch" href="//dpm.demdex.net">
    <link rel="dns-prefetch" href="//fast.techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//cm.everesttech.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.sc.omtrdc.net">
    <!--/Preconnect and DNS-Prefetch-->
    <!--Data Layer to enable rich data collection and targeting-->
    <script>
    var digitalData = {
        "page": {
            "pageInfo" : {
                "pageName": "Home"
                }
            }
    };
    </script>
    <!--/Data Layer-->
    <!--jQuery or other helper libraries-->
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <!--/jQuery-->
    <!--Tags Header Embed Code: REPLACE THE NEXT LINE WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
    <!--/Tags Header Embed Code-->
</head>
<body>
    <h1>Tags: Sample HTML Page</h1>
    <p>This is a very simple page to demonstrate basic implementation concepts of Tags</p>
    <p>See <a href="https://docs.adobe.com/content/help/nl-NL/experience-cloud/implementing-in-websites-with-launch/index.html">Implementing the Experience Cloud in Websites with Tags</a> for the complete tutorial</p>
</body>
</html>
```

+++

Vervang de bestaande insluitcode op of rond regel 34 door de code op het klembord en sla de pagina op. Open de pagina nu in een webbrowser. Als u de pagina laadt met het protocol `file://` , moet u &quot;https:&quot; toevoegen aan het begin van de insluitcode-URL in uw code-editor). Regels 33-36 van de voorbeeldpagina kunnen er ongeveer als volgt uitzien:

```html
    <!--Tags Header Embed Code: REPLACE LINE 39 WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="https://assets.adobedtm.com/launch-ENa21cfed3f06f4ddf9690de8077b39e81-development.min.js" async></script>
    <!--/Tags Header Embed Code-->
```

Open de ontwikkelaarsgereedschappen van uw webbrowser en ga naar het tabblad Netwerk. Op dit punt wordt een fout van 404 weergegeven voor de URL van de tagomgeving:
![&#x200B; 404 fout &#x200B;](images/samplepage-404.png)

De fout 404 wordt verwacht omdat u nog geen bibliotheek in deze milieu van Markeringen hebt gebouwd. Dat zult u in de volgende les doen. Als u een &#39;&#39;failed&#39;&#39;-bericht ziet in plaats van een 404-fout, bent u waarschijnlijk vergeten het `https://` -protocol toe te voegen aan de insluitcode. U hoeft het `https://` -protocol alleen op te geven als u de voorbeeldpagina laadt met het `file://` -protocol. Breng deze wijziging aan en laad de pagina opnieuw totdat de fout 404 wordt weergegeven.

## Aanbevolen werkwijzen voor implementatie van tags

Neem even de tijd om enkele best practices bij de implementatie van Codes te bekijken die op de voorbeeldpagina worden getoond:

* **Laag van Gegevens**:

   * Wij *adviseren sterk* creërend een gegevenslaag op uw plaats die alle attributen bevat nodig om variabelen in Analytics, Doel, en andere marketing oplossingen te bevolken. Deze voorbeeldpagina bevat alleen een zeer eenvoudige gegevenslaag, maar een echte gegevenslaag kan veel meer details bevatten over de pagina, de bezoeker, hun winkelwagendetails, enzovoort. Voor meer info over gegevenslagen, gelieve te zien [&#x200B; de Ervaring Digitale Laag van Gegevens 1.0 van de Klant &#x200B;](https://www.w3.org/2013/12/ceddl-201312.pdf)

   * Definieer de gegevenslaag vóór de code voor het insluiten van tags om te maximaliseren wat u kunt doen met oplossingen voor Experiencen Cloud.

* **de helperbibliotheken van JavaScript**: Als u reeds een bibliotheek als JQuery hebt die in `<head>` van uw pagina&#39;s wordt uitgevoerd, laad het vóór markeringen om zijn syntaxis in markeringen en Doel te hefboomwerking

* **HTML5 doctype**: Het HTML5 documenttype wordt vereist door Doel

* **preconnect en dns-prefetch**: Gebruik preconnect en dns-prefetch om de tijd van de paginading te verbeteren. Zie ook: [&#x200B; https://w3c.github.io/resource-hints/](https://w3c.github.io/resource-hints/)

* **pre-verbergend fragment voor asynchrone implementaties van het Doel**: U zult meer over dit in de les van het Doel leren, maar wanneer het Doel via asynchrone markering wordt opgesteld bed codes in, zou u een pre-verbergend fragment op uw pagina&#39;s vóór de markering moeten hardcoderen bed codes in om inhoudflikkering te beheren

Hier volgt een overzicht van hoe deze beste praktijken in de voorgestelde orde eruit zien. Houd er rekening mee dat er enkele plaatsaanduidingen zijn voor accountspecifieke details:

```html
<!doctype html>
<html lang="en">
<head>
    <title>Basic Demo</title>
    <!--Preconnect and DNS-Prefetch to improve page load time. REPLACE "techmarketingdemos" WITH YOUR OWN AAM PARTNER ID, TARGET CLIENT CODE, AND ANALYTICS TRACKING SERVER-->
    <link rel="preconnect" href="//dpm.demdex.net">
    <link rel="preconnect" href="//fast.techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//cm.everesttech.net">
    <link rel="preconnect" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="preconnect" href="//techmarketingdemos.sc.omtrdc.net">
    <link rel="dns-prefetch" href="//dpm.demdex.net">
    <link rel="dns-prefetch" href="//fast.techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//cm.everesttech.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.sc.omtrdc.net">
    <!--/Preconnect and DNS-Prefetch-->
    <!--Data Layer to enable rich data collection and targeting-->
    <script>
    var digitalData = {
        "page": {
            "pageInfo" : {
                "pageName": "Home"
                }
            }
    };
    </script>
    <!--/Data Layer-->
    <!--jQuery or other helper libraries-->
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <!--/jQuery-->
    <!--prehiding snippet for Adobe Target with asynchronous tags deployment-->
    <script>
        (function(g,b,d,f){(function(a,c,d){if(a){var e=b.createElement("style");e.id=c;e.innerHTML=d;a.appendChild(e)}})(b.getElementsByTagName("head")[0],"at-body-style",d);setTimeout(function(){var a=b.getElementsByTagName("head")[0];if(a){var c=b.getElementById("at-body-style");c&&a.removeChild(c)}},f)})(window,document,"body {opacity: 0 !important}",3E3);
    </script>
    <!--/prehiding snippet for Adobe Target with asynchronous tags deployment-->
    <!--Tags Header Embed Code: REPLACE LINE 39 WITH THE INSTALL CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
    <!--/Tags Header Embed Code-->
</head>
<body>
    <h1>Tags Basic Demo</h1>
    <p>This is a very simple page to demonstrate basic concepts of tags</p>
</body>
</html>
```

Nu weet u hoe u de code voor het insluiten van tags aan uw site kunt toevoegen!

[Volgende &quot;Voeg een gegevenselement, een regel en een bibliotheek toe&quot; >](add-data-elements-rules.md)

---
title: De insluitcode toevoegen
description: Leer hoe u de insluitcodes van de eigenschap tag ophaalt en deze implementeert in uw website. Deze les maakt deel uit van de zelfstudie Experience Cloud in websites implementeren.
exl-id: a2959553-2d6a-4c94-a7df-f62b720fd230
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---

# De insluitcode toevoegen

In deze les, zult u asynchrone inbedcode van de milieu van de Ontwikkeling van uw markeringsbezit uitvoeren. Tijdens het gebruik leert u over twee belangrijke concepten van tags: omgevingen en insluitingscodes.

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * platform launch (clientzijde) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * platform launch Server-zijde is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-configuraties zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**


## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Haal de insluitcode voor de eigenschap tag op
* Begrijp het verschil tussen een Ontwikkeling, het Opvoeren, en het milieu van de Productie
* Code voor het insluiten van tags toevoegen aan een HTML-document
* Beschrijf de optimale locatie van de code voor het insluiten van tags ten opzichte van andere code in het dialoogvenster `<head>` van een HTML-document

## De insluitcode kopiëren

De insluitcode is een `<script>` -tags die u op uw webpagina&#39;s plaatst om de logica die u in tags maakt te laden en uit te voeren. Als u de bibliotheek asynchroon laadt, blijft de browser de pagina laden, wordt de tagbibliotheek opgehaald en parallel uitgevoerd. In dit geval is er slechts één insluitcode die u in de `<head>`. (Wanneer tags synchroon worden geïmplementeerd, zijn er twee insluitcodes die u in het dialoogvenster `<head>` en een ander punt dat u aan de `</body>`).

Van het scherm van het Overzicht van het bezit, klik **[!UICONTROL Omgevingen]** in de linkernavigatie om naar de milieu&#39;s pagina te gaan. Merk op dat de milieu&#39;s van de Ontwikkeling, van het Staging, en van de Productie voor u vooraf zijn gecreeerd.

![Klik op Omgevingen in de bovenste nav](images/launch-environments.png)

De ontwikkeling, het Staging, en de milieu&#39;s van de Productie beantwoorden aan de typische milieu&#39;s in het codeontwikkeling en versieproces. De code wordt eerst geschreven door een ontwikkelaar in een milieu van de Ontwikkeling. Wanneer zij hun werk hebben voltooid, sturen zij het naar een het Opvoeren milieu voor QA en andere teams om te herzien. Zodra de kwaliteitscontrole en andere teams tevreden zijn, wordt de code vervolgens gepubliceerd naar de productieomgeving. Dit is de openbare omgeving die uw bezoekers ervaren wanneer ze naar uw website komen.

De markeringen staan extra milieu&#39;s van de Ontwikkeling toe, die in grote organisaties nuttig zijn waarin de veelvoudige ontwikkelaars aan verschillende projecten tezelfdertijd werken.

Dit zijn de enige omgevingen die we nodig hebben om de zelfstudie te voltooien. Met omgevingen kunt u verschillende werkversies van uw tagbibliotheken gebruiken die op verschillende URL&#39;s worden gehost, zodat u veilig nieuwe functies kunt toevoegen en beschikbaar kunt maken voor de juiste gebruikers (zoals ontwikkelaars, QA-technici, het publiek, enz.) op het juiste moment.

Kopieer nu de insluitcode:

1. In de **[!UICONTROL Ontwikkeling]** rij, klik het Install pictogram ![Installatiepictogram](images/launch-installIcon.png) om het modaal te openen.

1. Merk op dat de markeringen aan de asynchrone insluitcodes zullen gebrek

1. Klik op het pictogram Kopiëren ![Pictogram Kopiëren](images/launch-copyIcon.png) om de insluitcode naar het klembord te kopiëren.

1. Klikken **[!UICONTROL Sluiten]** om het modaal te sluiten.

   ![Installatiepictogram](images/launch-copyInstallCode.png)

## Implementeer de ingesloten code in het dialoogvenster `<head>` van de HTML-voorbeeldpagina

De insluitcode moet worden geïmplementeerd in het dialoogvenster `<head>` -element van alle HTML-pagina&#39;s die de eigenschap delen. U hebt mogelijk een of meer sjabloonbestanden die de `<head>` over de hele site heen. Hierdoor is het eenvoudig tags toe te voegen.

Als u dit nog niet hebt gedaan, downloadt u [de HTML-voorbeeldpagina](https://www.enablementadobe.com/multi/web/basic-sample.html) (Klik met de rechtermuisknop op deze koppeling en klik op &quot;Koppeling opslaan als&quot;) en open deze in een code-editor. [Haakjes](https://brackets.io/) is een vrije, open bronredacteur als u nodig hebt.

Vervang de bestaande insluitcode op of rond regel 34 door de code op het klembord en sla de pagina op. Open de pagina nu in een webbrowser. Als u de pagina laadt met de `file://` moet u &quot;https:&quot; toevoegen aan het begin van de insluitcode-URL in de code-editor). Regels 33-36 van de voorbeeldpagina kunnen er ongeveer als volgt uitzien:

```html
    <!--Tags Header Embed Code: REPLACE LINE 39 WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="https://assets.adobedtm.com/launch-ENa21cfed3f06f4ddf9690de8077b39e81-development.min.js" async></script>
    <!--/Tags Header Embed Code-->
```

Open de ontwikkelaarsgereedschappen van uw webbrowser en ga naar het tabblad Netwerk. Op dit punt wordt een fout van 404 weergegeven voor de URL van de tagomgeving:
![404-fout](images/samplepage-404.png)

De fout 404 wordt verwacht omdat u nog geen bibliotheek in deze milieu van Markeringen hebt gebouwd. Dat zult u in de volgende les doen. Als u een &quot;ontbroken&quot;bericht in plaats van een 404 fout ziet, bent u waarschijnlijk vergeten om toe te voegen `https://` protocol in de insluitcode. Opnieuw hoeft u alleen de `https://` protocol als u de steekproefpagina gebruikend `file://` protocol. Breng deze wijziging aan en laad de pagina opnieuw totdat de fout 404 wordt weergegeven.

## Aanbevolen werkwijzen voor implementatie van tags

Neem even de tijd om enkele best practices bij de implementatie van Codes te bekijken die op de voorbeeldpagina worden getoond:

* **Gegevenslaag**:

   * Wij *krachtig* adviseer het creëren van een gegevenslaag op uw plaats die alle attributen nodig bevat om variabelen in Analytics, Doel, en andere marketing oplossingen te bevolken. Deze voorbeeldpagina bevat alleen een zeer eenvoudige gegevenslaag, maar een echte gegevenslaag kan veel meer details bevatten over de pagina, de bezoeker, hun winkelwagendetails, enzovoort. Voor meer informatie over gegevenslagen raadpleegt u [Klantenervaring met digitale gegevenslaag 1.0](https://www.w3.org/2013/12/ceddl-201312.pdf)

   * Definieer de gegevenslaag vóór de code voor het insluiten van tags om te maximaliseren wat u kunt doen met Experience Cloud-oplossingen.

* **JavaScript-hulplijnbibliotheken**: Als u al een bibliotheek zoals JQuery hebt geïmplementeerd in het dialoogvenster `<head>` van uw pagina&#39;s, laad het voor markeringen om zijn syntaxis in markeringen en Doel te gebruiken

* **HTML5-doctype**: Het documenttype HTML5 wordt vereist door Doel

* **preconnect en dns-prefetch**: Gebruik preconnect en dns-prefetch om de laadtijd van de pagina te verbeteren. Zie ook: [https://w3c.github.io/resource-hints/](https://w3c.github.io/resource-hints/)

* **het pre-verbergen van fragment voor asynchrone implementaties van het Doel**: U zult meer over dit in de les van het Doel leren, maar wanneer het Doel via asynchrone markering wordt opgesteld bed codes in, zou u een pre-verbergend fragment op uw pagina&#39;s vóór de markering inbedt codes moeten hard coderen om inhoudflikkering te beheren

Hier volgt een overzicht van hoe deze beste praktijken in de voorgestelde orde eruit zien. Let op: er zijn enkele tijdelijke aanduidingen voor accountspecifieke details:

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

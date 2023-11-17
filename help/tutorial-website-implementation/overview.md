---
title: Het Experience Cloud implementeren in websites met tags
description: Implementeer het Experience Cloud op websites met tags is het perfecte startpunt voor professionele ontwikkelaars of technische marketers die willen leren hoe ze de Adobe Experience Cloud-oplossingen op hun website kunnen implementeren.
recommendations: catalog, noDisplay
exl-id: 1b95f0b2-3062-49d1-9b0b-e6824a54008f
source-git-commit: 8c3b487691c95b16da2a270b7d71cfd3bab1f0eb
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 2%

---

# Overzicht

_Het Experience Cloud implementeren in websites met tags_ is het perfecte startpunt voor front-end ontwikkelaars of technische marketers die willen leren hoe ze de Adobe Experience Cloud-oplossingen op hun website kunnen implementeren.

Elke les bevat hoe te oefeningen en fundamentele informatie om u te helpen het Experience Cloud uitvoeren en zijn waarde begrijpen.  De plaatsen van de manifestatie worden verstrekt voor u om het leerprogramma te voltooien, zodat kunt u de onderliggende technieken in een veilige milieu leren. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via de tags op uw eigen website.

>[!INFO]
>
>Deze zelfstudie gebruikt toepassingsspecifieke extensies en bibliotheken (AppMeasurement.js voor Adobe Analytics, at.js voor Adobe Target). Als u Adobe Experience Platform Web SDK wilt implementeren, raadpleegt u de [Adobe Experience Cloud implementeren met Web SDK](/help/tutorial-web-sdk/overview.md) zelfstudie.


Nadat u dit hebt voltooid, kunt u:

* Een tag-eigenschap maken

* Een eigenschap van een tag op een website installeren

* Voeg de volgende Adobe Experience Cloud-oplossingen toe:
   * **[Adobe Experience Platform Identity Service](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* Creeer regels en gegevenselementen om gegevens naar de oplossingen van de Adobe te verzenden

* De implementatie valideren met de Adobe Experience Cloud Debugger

* Wijzigingen publiceren via ontwikkelings-, staging- en productieomgevingen

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * Platform launch (clientzijde) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * Platform launch Server-zijde is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-configuraties zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**

>[!NOTE]
>
>Er zijn ook vergelijkbare zelfstudies voor meerdere oplossingen beschikbaar voor [Web SDK](../tutorial-web-sdk/overview.md) en [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Vereisten

In deze lessen wordt aangenomen dat u een Adobe-id en de vereiste machtigingen hebt om de oefeningen te voltooien. Als dat niet het geval is, moet u mogelijk contact opnemen met de beheerder van het Experience Cloud om toegang aan te vragen.

* Voor tags moet u gemachtigd zijn om omgevingen te ontwikkelen, goed te keuren, te publiceren, te beheren en te beheren. Voor meer informatie over de toestemmingen van de markeringsgebruiker, zie [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).
* Voor Adobe Analytics moet u weten welke trackingserver u gebruikt om deze zelfstudie te voltooien.
* Voor Audience Manager, moet u uw Audience Manager Subdomain (ook gekend als &quot;Partner Naam&quot;identiteitskaart van de Partner,&quot;of &quot;Partner Subdomain&quot;) kennen

Ook wordt aangenomen dat u bekend bent met de ontwikkelingstalen aan de voorzijde, zoals HTML en JavaScript. U hoeft geen expert in deze talen te zijn om de lessen te voltooien, maar u krijgt er meer uit als u de code comfortabel kunt lezen en begrijpen.

## Tags

De tagfunctie van Adobe Experience Platform is de volgende generatie van websitetags en beheermogelijkheden voor mobiele SDK&#39;s van Adobe. Met tags kunnen klanten eenvoudig alle analytische, marketing- en advertentieoplossingen implementeren en beheren die nodig zijn om relevante klantervaringen te stimuleren. Er zijn geen extra kosten voor tags. Het is beschikbaar voor elke Adobe Experience Cloud-klant.

Met tags voor websites kunt u alle JavaScript-code voor analytische, marketing- en advertentieoplossingen die op uw bureaublad en mobiele sites worden gebruikt, centraal beheren. Als u bijvoorbeeld Adobe Analytics implementeert, worden tags gebruikt voor het beheer van de JavaScript-bibliotheek van het AppMeasurement, het invullen van variabelen en brandverzoeken.

De inhoud van de container wordt geminiatuurd, inclusief de aangepaste code. Alles is modulair. Als u geen punt nodig hebt, is het niet inbegrepen in uw bibliotheek. Het resultaat is een snelle en compacte implementatie.

Tags zijn ook een platform waarmee externe leveranciers extensies kunnen maken, zodat hun oplossingen eenvoudig kunnen worden geïmplementeerd via tags. Een extensie is een pakket code (JavaScript, HTML en CSS) dat de taginterface en de clientfunctionaliteit uitbreidt. U kunt tags beschouwen als een besturingssysteem en extensies zijn de toepassingen die u gebruikt om uw taken uit te voeren.

## Informatie over de lessen

In deze lessen implementeert u de Adobe Experience Cloud in een nep-detailhandelswebsite met de naam Luma. De [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html) heeft een rijke gegevenslaag en functionaliteit die u zullen toestaan om een realistische implementatie te bouwen. U zult uw eigen markeringsbezit, in uw eigen organisatie van het Experience Cloud bouwen, en het in kaart brengen aan onze ontvangen plaats van de Luma gebruikend het Experience Cloud Debugger.

[![Luma-website](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## De gereedschappen ophalen

1. Omdat u bepaalde browserspecifieke extensies gaat gebruiken, raden we u aan de zelfstudie te voltooien met de opdracht [Chrome-webbrowser](https://www.google.com/chrome/)
1. Voeg de [Adobe Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) extensie voor uw Chrome-browser
1. De HTML-voorbeeldpaginacode kopiëren

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
       <p>See <a href="https://docs.adobe.com/content/help/en/experience-cloud/implementing-in-websites-with-launch/index.html">Implementing the Experience Cloud in Websites with Tags</a> for the complete tutorial</p>
   </body>
   </html>
   ```

+++

1. Hiermee krijgt u een teksteditor waarin u wijzigingen kunt aanbrengen in de HTML-voorbeeldpagina. (Als je er geen hebt, raden we je aan om het te proberen [Haakjes](https://brackets.io/))
1. Bladwijzer [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html)

>[!NOTE]
>
>U vindt het misschien eenvoudiger om deze zelfstudie uit te voeren met de site Luma geopend in Chrome, terwijl u deze zelfstudie leest en de interfacestappen voor gegevensverzameling uitvoert in een andere browser.

Laten we beginnen!

[Volgende &quot;Een eigenschap tag maken&quot; >](create-a-property.md)

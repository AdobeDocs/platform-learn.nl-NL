---
title: De Experience Cloud op websites implementeren met tags
description: Implementeer de Experience Cloud op websites met tags is het perfecte startpunt voor professionele ontwikkelaars of technische marketers die willen leren hoe ze de Adobe Experience Cloud-oplossingen op hun website kunnen implementeren.
recommendations: catalog, noDisplay
exl-id: 1b95f0b2-3062-49d1-9b0b-e6824a54008f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 2%

---

# Overzicht

_De Experience Cloud op websites implementeren met tags_ is het perfecte startpunt voor front-end ontwikkelaars of technische marketers die willen leren hoe ze de Adobe Experience Cloud-oplossingen op hun website kunnen implementeren.

Elke les bevat hoe te oefeningen en fundamentele informatie om u te helpen de Experience Cloud uitvoeren en zijn waarde begrijpen.  De plaatsen van de manifestatie worden verstrekt voor u om het leerprogramma te voltooien, zodat kunt u de onderliggende technieken in een veilige milieu leren. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via de tags op uw eigen website.

>[!INFO]
>
>In deze zelfstudie worden toepassingsspecifieke extensies en bibliotheken gebruikt (AppMeasurement.js voor Adobe Analytics, at.js voor Adobe Target). Als u Adobe Experience Platform Web SDK wilt implementeren, raadpleegt u de [Adobe Experience Cloud implementeren met Web SDK](/help/tutorial-web-sdk/overview.md) zelfstudie.


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
> * platform launch (clientzijde) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * platform launch Server-zijde is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-configuraties zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**


>[!NOTE]
>
>Er zijn ook vergelijkbare zelfstudies voor meerdere oplossingen beschikbaar voor [Web SDK](../tutorial-web-sdk/overview.md) en [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Vereisten

In deze lessen wordt aangenomen dat u een Adobe-id en de vereiste machtigingen hebt om de oefeningen te voltooien. Als dat niet het geval is, moet u mogelijk contact opnemen met de beheerder van de Experience Cloud om toegang aan te vragen.

* Voor tags moet u gemachtigd zijn om omgevingen te ontwikkelen, goed te keuren, te publiceren, te beheren en te beheren. Voor meer informatie over de toestemmingen van de markeringsgebruiker, zie [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).
* Voor Adobe Analytics moet u weten welke trackingserver u gebruikt om deze zelfstudie te voltooien
* Voor Audience Manager, moet u uw Audience Manager Subdomain (ook gekend als &quot;Partner Naam&quot;identiteitskaart van de Partner,&quot;of &quot;Partner Subdomain&quot;) kennen.

Ook wordt aangenomen dat u bekend bent met de ontwikkelingstalen aan de voorzijde, zoals HTML en JavaScript. U hoeft geen expert in deze talen te zijn om de lessen te voltooien, maar u krijgt er meer uit als u de code comfortabel kunt lezen en begrijpen.

## Tags

De tagfunctie van Adobe Experience Platform is de volgende generatie websitetags en beheermogelijkheden voor mobiele SDK&#39;s van Adobe. Met tags kunnen klanten op eenvoudige wijze alle analytische, marketing- en advertentieoplossingen implementeren en beheren die nodig zijn om relevante klantervaringen te stimuleren. Er zijn geen extra kosten voor tags. Het is beschikbaar voor elke Adobe Experience Cloud-klant.

Met tags voor websites kunt u alle JavaScript-code voor analytische, marketing- en advertentieoplossingen die op uw bureaublad en mobiele sites worden gebruikt, centraal beheren. Als u bijvoorbeeld Adobe Analytics implementeert, worden met tags de JavaScript-bibliotheek AppMeasurement beheerd, worden variabelen gevuld en worden brandverzoeken verzonden.

De inhoud van de container wordt geminiatuurd, inclusief de aangepaste code. Alles is modulair. Als u geen punt nodig hebt, is het niet inbegrepen in uw bibliotheek. Het resultaat is een snelle en compacte implementatie.

Tags zijn ook een platform waarmee externe leveranciers extensies kunnen maken, zodat hun oplossingen eenvoudig kunnen worden geïmplementeerd via tags. Een extensie is een pakket code (JavaScript, HTML en CSS) dat de taginterface en de clientfunctionaliteit uitbreidt. U kunt tags beschouwen als een besturingssysteem en extensies zijn de toepassingen die u gebruikt om uw taken uit te voeren.

## Over de lessen

In deze lessen implementeert u de Adobe Experience Cloud in een nep-detailhandelswebsite met de naam Luma. De [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html) heeft een rijke gegevenslaag en functionaliteit die u zullen toestaan om een realistische implementatie te bouwen. U zult uw eigen markeringsbezit, in uw eigen organisatie van de Experience Cloud bouwen, en het toewijzen aan onze ontvangen plaats van de Luma gebruikend de Experience Cloud Debugger.

[![Luma-website](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## De gereedschappen ophalen

1. Omdat u bepaalde browserspecifieke extensies gaat gebruiken, raden we u aan de zelfstudie te voltooien met de opdracht [Chrome-webbrowser](https://www.google.com/chrome/)
1. Voeg de [Adobe Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) extensie voor uw Chrome-browser
1. Download de [HTML-voorbeeldpagina](https://www.enablementadobe.com/multi/web/basic-sample.html) (klik met de rechtermuisknop op deze koppeling en klik op Koppeling opslaan als)
1. Hiermee krijgt u een teksteditor waarin u wijzigingen kunt aanbrengen in de HTML-voorbeeldpagina. (Als je er geen hebt, raden we je aan om het te proberen [Haakjes](https://brackets.io/))
1. Bladwijzer [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html)

>[!NOTE]
>
>U vindt het misschien eenvoudiger om deze zelfstudie uit te voeren met de site Luma geopend in Chrome, terwijl u deze zelfstudie leest en de interfacestappen voor gegevensverzameling uitvoert in een andere browser.

Laten we beginnen!

[Volgende &quot;Een eigenschap tag maken&quot; >](create-a-property.md)

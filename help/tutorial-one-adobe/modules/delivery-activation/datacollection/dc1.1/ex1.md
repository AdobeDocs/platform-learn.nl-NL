---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - het Verklaren van de Inzameling van Gegevens van Adobe Experience Platform
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - het Verklaren van de Inzameling van Gegevens van Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 1f5dd730-d84a-4d3a-b5ef-2be3e089c7fd
source-git-commit: 9c4d585d99920f0cdfd9de083c3f020f0d8171ab
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 1.1.1 Adobe Experience Platform-gegevensverzameling

## Context

De Inzameling van Gegevens van Adobe Experience Platform wordt gebruikt door merken voor een aantal gebruiksgevallen. Het is een Tag Management System (TMS) van de volgende generatie dat klanten een eenvoudige manier biedt om alle benodigde analyse-, marketing- en advertentieoplossingen te implementeren en te beheren om de relevante ervaringen van klanten te verbeteren. Er zijn geen extra kosten voor Adobe Experience Platform Data Collection en het is beschikbaar voor om het even welke klant van Adobe Experience Cloud. Een merk kan Adobe Experience Platform Data Collection gebruiken om:

- Implementeer Adobe Experience Cloud-toepassingen en Adobe Experience Platform.
- Beheer de verschillende vereisten van verschillende delen van de organisatie door elk van hun eigen **Bezit** te voorzien om te leiden.
- Testen en levenscyclusbeheer toestaan.
- Injecteer aangepaste JavaScript en tags van derden, allemaal op één plaats beheerd.

## De gebruikersinterface verkennen

Ga naar [ de Inzameling van Gegevens van Adobe Experience Platform ](https://experience.adobe.com/#/data-collection/). Zorg ervoor dat u de juiste omgeving gebruikt, die `--aepImsOrgName--` moet zijn.

>[!NOTE]
>
>Dit leerprogramma wordt gedocumenteerd gebruikend het milieu **Internationale Experience Platform**. Uw milieunaam is waarschijnlijk verschillend, zodat wanneer u de naam **Experience Platform Internationaal** in een schermafbeelding ziet, zou u dat door de naam van uw eigen milieu moeten vervangen, dat `--aepImsOrgName--` zou moeten zijn.

![ Mening van Eigenschappen van de Lancering ](./images/launch0.png)

Ga naar **Markeringen**. U ziet nu de weergave **[!UICONTROL Properties]** . De eigenschappen die hier worden vermeld zijn voor zelfstudiemanagement. Deze eigenschappen vertegenwoordigen:

- Toepassings- en webinigenschappen
- Verschillende websites die klanten op verschillende manieren bedienen. Luma Retail zou bijvoorbeeld één eigenschap hebben, Luma Travel een andere.
- Oudere en huidige websites
- Een specifiek Adobe Analytics-ontwerp dat door meerdere verschillende websites wordt gebruikt
- Interne intranetpagina&#39;s naast externe sites

![ Mening van Eigenschappen van de Lancering ](./images/launch1.png)

Kijk nu naar de linkerspoorlijn.

![ Begin Linkerspoor ](./images/launch2.png)

- **[!UICONTROL Tags]** geeft een overzicht van alle eigenschappen aan de clientzijde
- **[!UICONTROL App Surfaces]** geeft een overzicht van alle App Configurations om pushmeldingen in te schakelen (wordt gebruikt/ingeschakeld in combinatie met Project Sierra)
- **[!UICONTROL Datastreams]** worden verkend in de [ volgende oefening ](./ex2.md)
- **[!UICONTROL Event Forwarding]** geeft een overzicht van alle server-zijeigenschappen die in [ Module 2.5 - de Verbindingen van Real-Time CDP worden verkend: Gebeurtenis door:sturen ](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-5/aep-data-collection-ssf.md)
- **[!UICONTROL Monitoring]** geeft een overzicht van het inkomende en uitgaande gebeurtenisverkeer via Event Forwarding
- **[!UICONTROL Assurance]** biedt toegang tot foutopsporing voor een implementatie met de Adobe Debugger
- **[!UICONTROL Places]** biedt toegang tot het beheer van inhoud die toegankelijk wordt voor op locatie gebaseerde personalisatie in mobiele toepassingen
- **[!UICONTROL Schemas]** biedt toegang tot de Adobe Experience Platform-schemaeditor
- **[!UICONTROL Identities]** biedt toegang tot Adobe Experience Platform Identity Graph Setup

## Aanvullende informatie

Adobe Experience Platform Data Collection is een zeer geavanceerd hulpmiddel dat werkingsgebied voorbij een zelfstudie van Adobe Experience Platform heeft. Organisaties gebruiken Adobe Experience Platform Data Collection niet voor zijn mogelijkheden van het markeringsbeheer en in plaats daarvan gebruiken niet-Adobe oplossingen van het markeringsbeheer voor het injecteren van code en het beheren van markeringen. Adobe en Adobe Professional Services ondersteunen het gebruik van een niet-Adobe-oplossing voor tagbeheer.
Hieronder vindt u wat meer lezingen voor degenen die geïnteresseerd zijn in het begrijpen van Adobe Experience Platform-gegevensverzameling.

- [ Gids van de Gebruiker van de Verzameling van Gegevens van Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
- [ voer Adobe Experience Cloud met het Web SDK leerprogramma uit ](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html?lang=nl-NL)
- [ de gebruikerstoestemmingen van de opstelling ](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=nl-NL)
- [ API documentatie ](https://developer.adobelaunch.com/api/)

## Volgende stappen

Ga naar [ 1.1.2 Edge Network, Gegevensstromen en de Inzameling van Gegevens van de Server Zijde ](./ex2.md){target="_blank"}

Ga terug naar [ Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de de markeringsuitbreiding van SDK van het Web ](./data-ingestion-launch-web-sdk.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

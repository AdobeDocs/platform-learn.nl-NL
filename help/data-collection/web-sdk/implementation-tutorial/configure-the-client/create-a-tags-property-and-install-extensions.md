---
title: Een Adobe Experience Platform-tageigenschap maken en extensies installeren
description: Een Adobe Experience Platform-tageigenschap maken en extensies installeren
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 7403059f-b34c-48e0-9efe-b2db7a9afb27
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---

# Een Adobe Experience Platform-tageigenschap maken en extensies installeren

Nu de gegevens en de gebeurtenissen van de op-pagina code in de gegevenslaag duwen, is het tijd voor de teller om de gegevens van de gegevenslaag te lezen en deze gegevens naar Adobe Experience Platform te verzenden. Hiervoor zijn meestal twee JavaScript-bibliotheken nodig:

* Gegevenslaag Adobe-client: In vorige stappen hebt u een array met gegevenslagen gemaakt en hebt u er objecten in gedrukt. Om tot gegevens toegang te hebben, moet u de bibliotheek van JavaScript van de Laag van Gegevens van de Cliënt van de Adobe laden, die manieren verstrekt om van veranderingen en gebeurtenissen van de gegevenslaag op de hoogte te worden gebracht en ook eenvoudige manieren verstrekt om tot de gegevens toegang te hebben.
* Adobe Experience Platform Web SDK: Deze JavaScript-bibliotheek communiceert met Adobe Experience Platform Edge Network. SDK behandelt identiteit, toestemming, gegevensinzameling, verpersoonlijking, publiek, en meer.

Hoewel u deze afzonderlijke bibliotheken op uw website kunt laden en rechtstreeks kunt gebruiken, raden we u aan [Adobe Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl). Met Markeringen, kunt u één enkel manuscript in uw HTML inbedden en het gebruikersinterface van Markeringen gebruiken om zowel de Laag van Gegevens van de Cliënt van de Adobe als SDK van het Web SDK van Adobe Experience Platform op te stellen. Met tags kunt u onder andere regels maken voor het verzenden van gegevens. Deze zelfstudie gebruikt hiervoor labels en gaat ervan uit dat u een basiskennis hebt van de werking van tags.

## Een eigenschap maken in tags

Als je dat nog niet hebt gedaan, [een eigenschap maken binnen tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html#create-or-configure-a-property).

## De extensie Gegevenslaag Adobe-client installeren

Installeer de Adobe Client Data Layer-extensie door naar de extensiecatalogus te navigeren, de extensie te zoeken en op de respectievelijke extensie te klikken [!UICONTROL Installeren] knop. U zou een configuratiescherm moeten zien.

![Adobe Client Data Layer-extensie-installatie](../../../assets/implementation-strategy/acdl-extension-installation.png)

Voor deze zelfstudie hoeft u de standaardwaarden niet te wijzigen. Klikken [!UICONTROL Opslaan].

## De extensie Adobe Experience Platform Web SDK installeren

Installeer vervolgens de SDK-extensie voor Adobe Experience Platform Web door de extensie te zoeken in de extensiecatalogus en op de respectievelijke extensies te klikken [!UICONTROL Installeren] knop. U zou een configuratiescherm moeten zien.

![Installatie van Adobe Experience Platform Web SDK-extensie](../../../assets/implementation-strategy/web-sdk-extension-installation.png)

In [Een gegevensstroom maken](../configure-the-server/create-a-datastream.md)hebt u een gegevensstroom gemaakt waarnaar Adobe Experience Platform Edge Network verwijst om te bepalen waar u de binnenkomende gegevens naartoe wilt sturen. Wanneer het doen van verzoeken van het Web SDK van Adobe Experience Platform aan het Netwerk van de Rand, moet u wijzen op welk gegevensstroom het Netwerk van de Rand zou moeten van verwijzingen voorzien.

Om dit te doen, vind [!UICONTROL DataStream] en selecteer de gegevensstroom die u eerder hebt gemaakt. U krijgt dezelfde gegevensstroomomgevingen te zien waarin u [Een gegevensstroom maken](../configure-the-server/create-a-datastream.md).

![Gegevensstroom selecteren](../../../assets/implementation-strategy/web-sdk-datastream-selection.png)

Zoals besproken in [Een gegevensstroom maken](../configure-the-server/create-a-dataset.md), hebben deze datasetmilieu&#39;s een verband met de milieu&#39;s van Markeringen. Stel dat u de installatie van de SDK-extensie voor Adobe Experience Platform Web hebt voltooid, maak een tagbibliotheek met de extensie en publiceer de bibliotheek vervolgens naar een ontwikkelomgeving voor tags. Wanneer de tagbibliotheek op uw webpagina is geladen en de Adobe Experience Platform Web SDK-extensie een aanvraag naar Edge Network indient, bevat de extensie de extensie [!UICONTROL Ontwikkelingsomgeving] DataStream-omgeving-id. Het Netwerk van de rand, beurtelings, gebruikt die identiteitskaart om de configuratie van te lezen [!UICONTROL Ontwikkelingsomgeving] gegevensstroomomgeving en gegevens doorsturen naar de juiste Adobe-producten.

Op dit moment hebt u slechts één ontwikkelingdatastreamomgeving, één testomgeving voor gegevensstroom en één productiegegevensstroomomgeving. Daarom toont het gebruikersinterface van de uitbreidingsconfiguratie hen allen pre-geselecteerd en unchangeable. Het is echter mogelijk om meerdere ontwikkelomgevingen voor gegevensstromen te maken (één voor u en één voor uw collega, misschien) met behulp van de gegevensstroomgebruikersinterface. Als u meerdere ontwikkelgegevensstroomomgevingen had, kunt u selecteren welke voor deze tag-eigenschap u wilt gebruiken.

Tot slot, scrol neer en uncheck [!UICONTROL Klikgegevensverzameling inschakelen]. Standaard houdt de SDK koppelingen automatisch bij. In deze zelfstudie, echter, zullen wij aantonen hoe u uw eigen verbindingsklikken kunt volgen gebruikend de informatie van de douaneverbinding.

Klik op de knop [!UICONTROL Opslaan] om de installatie van de Adobe Experience Platform Web SDK-extensie te voltooien.

De juiste extensies zijn geïnstalleerd. Het is tijd om regels en gegevenselementen te maken.

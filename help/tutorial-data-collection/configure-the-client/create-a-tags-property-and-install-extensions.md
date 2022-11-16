---
title: Een Adobe Experience Platform-tageigenschap maken en extensies installeren
description: Een Adobe Experience Platform-tageigenschap maken en extensies installeren
exl-id: d0fe82b5-a036-4e13-bae1-d1fee78d0084
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---

# Een Adobe Experience Platform maken [!DNL Tags] eigenschap en extensies installeren

Nu de gegevens en de gebeurtenissen van de op-pagina code in de gegevenslaag duwen, is het tijd voor de teller om de gegevens van de gegevenslaag te lezen en deze gegevens naar Adobe Experience Platform te verzenden. Hiervoor zijn meestal twee JavaScript-bibliotheken nodig:

* Gegevenslaag Adobe-client: In vorige stappen hebt u een array met gegevenslagen gemaakt en hebt u er objecten in gedrukt. Om tot deze gegevens toegang te hebben, moet u de bibliotheek van JavaScript van de Laag van Gegevens van de Cliënt van de Adobe laden. Deze bibliotheek bevat meldingen voor gebeurtenissen en wijzigingen in de gegevenslaag, en eenvoudige toegang tot de gegevens.
* Adobe Experience Platform Web SDK: Deze JavaScript-bibliotheek communiceert met de [Adobe Experience Platform Edge Network](https://business.adobe.com/products/experience-platform/experience-platform-edge-network.html). SDK behandelt identiteit, toestemming, gegevensinzameling, verpersoonlijking, publiek, en meer.

Hoewel u deze afzonderlijke bibliotheken op uw website kunt laden en rechtstreeks kunt gebruiken, raden we u aan [Adobe Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl). Met Markeringen, kunt u één enkel manuscript in uw HTML inbedden en het gebruikersinterface van Markeringen gebruiken om zowel de Laag van Gegevens van de Cliënt van de Adobe als SDK van het Web SDK van Adobe Experience Platform op te stellen. Met tags kunt u onder andere regels maken voor het verzenden van gegevens. Deze zelfstudie gebruikt hiervoor labels en gaat ervan uit dat u een basiskennis hebt van de werking van tags.

## Een eigenschap maken in tags

1. [Een eigenschap maken in tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html#create-or-configure-a-property).

## De extensie Gegevenslaag Adobe-client installeren

Installeer de Adobe Client Data Layer-extensie:

1. Selecteren **[!UICONTROL Extensies]** in de linkerzijnavigatie in het bezit van de Markering dat u voor dit leerprogramma gebruikt.
1. Selecteer **[!UICONTROL Catalogus]** koppelen boven aan en zoeken naar &#39;gegevenslaag&#39;.
1. Zodra de Gegevens van de Cliënt van Adobe in de resultaten toont, klik op **[!UICONTROL Installeren]** knop. U zou een configuratiescherm moeten zien. Voor deze zelfstudie hoeft u de standaardwaarden niet te wijzigen.
1. Klikken **[!UICONTROL Opslaan]**.
   ![Adobe Client Data Layer-extensie-installatie](../assets/acdl-extension-installation.png)


## De extensie Adobe Experience Platform Web SDK installeren

Installeer vervolgens de extensie Adobe Experience Platform Web SDK:

1. Zoeken naar de extensie in de extensiecatalogus en klikken op de respectievelijke **[!UICONTROL Installeren]** knop. U zou het configuratiescherm moeten zien:
   ![Installatie van Adobe Experience Platform Web SDK-extensie](../assets/web-sdk-extension-installation.png)
1. In de [!UICONTROL DataStream] , selecteert u de gegevensstroom die u eerder hebt gemaakt. U wordt voorgesteld met de zelfde gegevensstroommilieu&#39;s die u in zag [Een gegevensstroom maken](../configure-the-server/create-a-datastream.md).
   ![Gegevensstroom selecteren](../assets/web-sdk-datastream-selection.png)
1. Verder in het configuratiescherm, vind en uncheck **[!UICONTROL Klikgegevensverzameling inschakelen]**. Standaard houdt de SDK koppelingen automatisch bij. In deze zelfstudie, echter, tonen wij hoe u uw eigen verbindingskliks kunt volgen gebruikend de informatie van de douaneverbinding.
1. Klik op de knop **[!UICONTROL Opslaan]** om de installatie van de Adobe Experience Platform Web SDK-extensie te voltooien.

>[!TIP]
>
>De datasetmilieu&#39;s hebben een verband met de milieu&#39;s van Markeringen. Stel dat u de installatie van de SDK-extensie voor Adobe Experience Platform Web hebt voltooid, maak een tagbibliotheek met de extensie en publiceer de bibliotheek vervolgens naar een ontwikkelomgeving voor tags. Wanneer de tagbibliotheek op uw webpagina is geladen en de Adobe Experience Platform Web SDK-extensie een aanvraag naar Edge Network indient, bevat de extensie de extensie [!UICONTROL Ontwikkelingsomgeving] DataStream-omgeving-id. Het Netwerk van de rand, beurtelings, gebruikt die identiteitskaart om de configuratie van te lezen [!UICONTROL Ontwikkelingsomgeving] gegevensstroomomgeving en gegevens doorsturen naar de juiste Adobe-producten.
>
>Op dit moment hebt u slechts één ontwikkelingdatastreamomgeving, één testomgeving voor gegevensstroom en één productiegegevensstroomomgeving. Het is mogelijk om veelvoudige milieu&#39;s van de gegevensstroomontwikkeling (voor u en voor uw medewerker, misschien) tot stand te brengen gebruikend de datastream gebruikersinterface. Als u meerdere ontwikkelgegevensstroomomgevingen had, kunt u selecteren welke voor deze tag-eigenschap u wilt gebruiken.


De juiste extensies zijn geïnstalleerd. Het is tijd om regels en gegevenselementen te maken.

[Volgende: ](create-rules-for-tracking-page-view-and-commerce-events.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

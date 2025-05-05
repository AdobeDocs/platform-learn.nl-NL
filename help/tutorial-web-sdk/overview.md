---
title: Tutorial voor Adobe Experience Cloud met Web SDK implementeren
description: Leer hoe te om de toepassingen van het Experience Cloud uit te voeren gebruikend het Web SDK van Adobe Experience Platform.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: 8602110d2b2ddc561e45f201e3bcce5e6a6f8261
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 2%

---

# Tutorial voor Adobe Experience Cloud met Web SDK implementeren

Leer hoe te om de toepassingen van het Experience Cloud uit te voeren gebruikend het Web SDK van Adobe Experience Platform.

Het Web SDK van het Experience Platform is een cliënt-kant bibliotheek van JavaScript die klanten van Adobe Experience Cloud toestaat om met zowel Adobe toepassingen als derdediensten door de Edge Network van Adobe Experience Platform in wisselwerking te staan. Zie [ het Overzicht van SDK van het Web van Adobe Experience Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/edge/home) voor meer gedetailleerde informatie.

{de architectuur van SDK van het Web van 0} Experience Platform ![&#128279;](assets/dc-websdk.png)

Deze zelfstudie begeleidt u door de implementatie van de Platform Web SDK op een voorbeeldwebsite in de detailhandel met de naam Luma. De [ plaats van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) heeft een rijke gegevenslaag en functionaliteit die u een realistische implementatie laat bouwen. Voor deze zelfstudie:

* Maak in uw eigen account uw eigen eigenschap voor tags met een Platform Web SDK-implementatie voor de Luma-website.
* Vorm alle eigenschappen van de gegevensinzameling voor de implementaties van SDK van het Web zoals gegevensstromen, schema&#39;s, en identiteitsnamespaces.
* Voeg de volgende Adobe Experience Cloud-toepassingen toe:
   * **[Adobe Experience Platform](setup-experience-platform.md)** (en toepassingen die op Platform zoals Adobe Real-time Customer Data Platform, Adobe Journey Optimizer, en Adobe Customer Journey Analytics worden gebouwd)
   * **[Adobe Analytics](setup-analytics.md)**
   * **[Adobe Audience Manager](setup-audience-manager.md)**
   * **[Adobe Target](setup-target.md)**
* Voer gebeurtenis door:sturen uit om de gegevens te verzenden die door Web SDK aan niet-Adobe bestemmingen worden verzameld.
* Valideer uw eigen implementatie van SDK van het Web van het Platform gebruikend Foutopsporing en Verzekering van het Experience Platform.

Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingtoepassingen implementeren via Platform Web SDK op uw eigen website!


>[!NOTE]
>
>Een gelijkaardige multi-oplossingsleerprogramma is beschikbaar voor [ Mobiele SDK ](../tutorial-mobile-sdk/overview.md).

## Vereisten

Alle klanten van het Experience Cloud kunnen Platform Web SDK gebruiken. Het is geen vereiste om een op platform-gebaseerde toepassing zoals Real-time Customer Data Platform of Journey Optimizer vergunning te geven om Web SDK te gebruiken.

In deze lessen wordt aangenomen dat u een Adobe-account en de vereiste machtigingen hebt om de lessen te voltooien. Als niet, moet u uit naar een Beheerder van het Experience Cloud bij uw bedrijf om toegang te verkrijgen.

* Voor **de Inzameling van Gegevens**, moet u hebben:
   * **[!UICONTROL Platforms]** - machtiging voor **[!UICONTROL Web]** en, indien gelicentieerd, **[!UICONTROL Edge]**
   * **[!UICONTROL Property Rights]** - toestemming voor **[!UICONTROL Approve]** , **[!UICONTROL Develop]** , **[!UICONTROL Edit Property]** , **[!UICONTROL Manage Environments]** , **[!UICONTROL Manage Extensions]** en **[!UICONTROL Publish]** ,
   * **[!UICONTROL Company Rights]** : toestemming voor **[!UICONTROL Manage Properties]**

     Voor meer informatie betreffende markeringstoestemmingen, zie [ de documentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/tags/admin/user-permissions).

* Voor **Experience Platform**, moet u hebben:

   * Toegang tot de **standaardproductie**, **&quot;Prod&quot;** zandbak.
   * Toegang tot **[!UICONTROL Manage Schemas]** en **[!UICONTROL View Schemas]** under **[!UICONTROL Data Modeling]** .
   * Toegang tot **[!UICONTROL Manage Identity Namespaces]** en **[!UICONTROL View Identity Namespaces]** under **[!UICONTROL Identity Management]** .
   * Toegang tot **[!UICONTROL Manage Datastreams]** en **[!UICONTROL View Datastreams]** under **[!UICONTROL Data Collection]** .
   * Als u een klant van een op platform-gebaseerde toepassing bent en de [ Experience Platform van de Opstelling ](setup-experience-platform.md) les zult voltooien, zou u ook moeten hebben:
      * Toegang tot de zandbak van de a **ontwikkeling**.
      * Alle machtigingsitems onder **[!UICONTROL Data Management]** en **[!UICONTROL Profile Management]** :

     De vereiste functies moeten beschikbaar zijn voor alle klanten van het Experience Cloud, zelfs als u geen klant bent van een platformgebaseerde toepassing zoals Real-Time CDP.

     Voor meer informatie over de toegangscontrole van het Platform, zie [ de documentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home).

* Voor de facultatieve **les van 0&rbrace; Adobe Analytics &lbrace;, moet u [ beheerdertoegang hebben tot de Montages van de Reeks van het Rapport, de Regels van de Verwerking, en Analysis Workspace ](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-console/home)**

* Voor de facultatieve **Adobe Target** les, moet u [ Redacteur of de toegang van de fiatteur ](https://experienceleague.adobe.com/en/docs/target/using/administer/manage-users/enterprise/properties-overview#section_8C425E43E5DD4111BBFC734A2B7ABC80) hebben.

* Voor de facultatieve **les van de Audience Manager 0&rbrace; &lbrace;, moet u toegang hebben tot creeer, lees, en schrijf sporen, segmenten, en bestemmingen.** Voor meer informatie, verwijs naar het leerprogramma op [ op rol-Gebaseerde Controle van de Toegang van de Audience Manager ](https://experienceleague.adobe.com/en/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control).


>[!NOTE]
>
>Men veronderstelt dat u met front-end ontwikkelingstalen zoals HTML en JavaScript vertrouwd bent. U hoeft geen expert in deze talen te zijn, maar u kunt meer uit deze zelfstudie halen als u code kunt lezen en begrijpen.

## Updates

* 24 april 2024: belangrijke updates, waaronder toevoeging van Set Variable/Update Variable, split personalization and analytics request, Journey Optimizer lessen

## De Luma-website laden

Laad de [ website van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) {target="blank"} in een afzonderlijk browser lusje en referentie het zodat kunt u het gemakkelijk laden wanneer nodig tijdens het leerprogramma. U hebt geen andere aanvullende toegang tot Luma nodig dan de gehoste productiesite te kunnen laden.

[![ Website Luma ](assets/old-overview-luma.png) ](https://luma.enablementadobe.com/content/luma/us/en.html) {target="blank"}

Laten we beginnen!

[Volgende: ](configure-schemas.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van de Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

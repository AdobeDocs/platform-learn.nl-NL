---
title: Vorm een gegevensstroom voor het Web SDK van het Platform
description: Leer hoe te om een gegevensstroom toe te laten en de oplossingen van het Experience Cloud te vormen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Datastreams
jira: KT-15399
exl-id: 20f770d1-eb0f-41a9-b451-4069a0a91fc4
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Een gegevensstroom configureren

Leer hoe te om een gegevensstroom voor het Web SDK van Adobe Experience Platform te vormen.

[ Datastreams ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview) vertelt de Edge Network van Adobe Experience Platform waar te om gegevens te verzenden die door het Web SDK van het Platform worden verzameld. In de configuratie van gegevensstromen, laat u uw toepassingen van het Experience Cloud, uw rekening van het Experience Platform, en gebeurtenis toe door:sturen.

![ SDK van het Web, gegevensstromen, en het diagram van de Edge Network ](assets/dc-websdk-datastreams.png)

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een gegevensstroom maken
* Aan de slag met gegevensstroomoverschrijvingen

## Vereisten

Voordat u de gegevensstroom configureert, moet u de volgende lessen al hebben voltooid:

* [Een schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)

## Een gegevensstroom maken

Nu, kunt u een gegevensstroom tot stand brengen om de Edge Network van het Platform te vertellen waar te om gegevens te verzenden die door Web SDK worden verzameld.

**om een gegevensstroom tot stand te brengen:**

1. Open de [ interface van de Inzameling van Gegevens ](https://launch.adobe.com/) {target="_blank"}
1. Zorg ervoor dat u zich in de juiste sandbox bevindt

   >[!NOTE]
   >
   >Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP of Journey Optimizer, raden we u aan een ontwikkelingssandbox voor deze zelfstudie te gebruiken. Als u dat niet doet, gebruikt u de **[!UICONTROL Prod]** -sandbox.

1. Ga naar **[!UICONTROL Datastreams]** in de linkernavigatie
1. Selecteren **[!UICONTROL New Datastream]**
1. Voer `Luma Web SDK: Development Environment` in als de **[!UICONTROL Name]** . Deze naam wordt van verwijzingen voorzien later wanneer u de uitbreiding van SDK van het Web in uw markeringsbezit vormt.
1. Selecteren **[!UICONTROL Save]**

   ![ creeer de datastream ](assets/datastream-create-new-datastream.png)

   >[!NOTE]
   >
   >U hoeft geen schema te selecteren. Een schemaselectie wordt slechts vereist als u [ Prep van Gegevens voor de eigenschap van de Inzameling van Gegevens ](/help/data-collection/edge/data-prep.md) gebruikt.

Op het volgende scherm, kunt u de diensten zoals de toepassingen van de Adobe aan de datastream toevoegen, nochtans zult u geen diensten op dit punt toevoegen. U zult dit later in de lessen [ Experience Platform van de Opstelling ](setup-experience-platform.md) doen, [ Opstelling Analytics ](setup-analytics.md), [ Opstelling Audience Manager ](setup-audience-manager.md), [ het Doel van de Opstelling ](setup-target.md), of [ Gebeurtenis door:sturen ](setup-event-forwarding.md).

>[!NOTE]
>
>Wanneer u Platform Web SDK op uw eigen website implementeert, moet u drie gegevensstreams maken om toe te wijzen aan uw drie labelomgevingen (ontwikkeling, werkgebied en productie). Als u Platform Web SDK met op platform-gebaseerde toepassingen zoals Adobe Real-time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken van het Platform tot stand te brengen.

## Een gegevensstroom overschrijven

[ DataStream treedt ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides) met voeten staat u toe om extra configuraties voor uw gegevensstroom te bepalen en dan uw standaardconfiguratie onder bepaalde voorwaarden met voeten te treden.

De configuratieopheffing van gegevensstroom is een proces in twee stappen:

1. Eerst, bepaalt u gegevensstroom met voeten treedt in de configuratie van de datastream dienst. Bijvoorbeeld, zou u afwisselende het rapportreeksen van Analytics, de werkruimten van het Doel, of de datasets van het Platform kunnen bepalen om als met voeten te treden.
1. Dan, verzendt u de met voeten treedt naar de Edge Network of met SDK van het Web verzendt gebeurtenisactie, of door een configuratie in de de markeringsuitbreiding van SDK van het Web.

In de ](setup-analytics.md) les van de Opstelling Adobe Analytics [ {, treedt u de rapportreeks voor een pagina met voeten gebruikend het Web SDK van het Platform verzendt de Actie van de Gebeurtenis.

U bent nu klaar om de uitbreiding van SDK van het Web van het Platform in uw markeringsbezit te installeren!

[Volgende: ](install-web-sdk.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van de Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

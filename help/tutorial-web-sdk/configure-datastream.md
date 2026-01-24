---
title: Een gegevensstroom configureren voor Platform Web SDK
description: Leer hoe u een datastream inschakelt en Experience Cloud-oplossingen configureert. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Datastreams
jira: KT-15399
exl-id: 20f770d1-eb0f-41a9-b451-4069a0a91fc4
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Een gegevensstroom configureren

Leer hoe u een gegevensstroom voor Adobe Experience Platform Web SDK configureert.

[&#x200B; gegevensstromen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/overview) vertellen Adobe Experience Platform Edge Network waar te om gegevens te verzenden die door het Web SDK van het Platform worden verzameld. In de configuratie van gegevensstromen, laat u uw toepassingen van Experience Cloud, uw rekening van Experience Platform, en gebeurtenis toe die door:sturen.

![&#x200B; SDK van het Web, gegevensstromen, en het diagram van Edge Network &#x200B;](assets/dc-websdk-datastreams.png)

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een gegevensstroom maken
* Aan de slag met gegevensstroomoverschrijvingen

## Vereisten

Voordat u de gegevensstroom configureert, moet u de volgende lessen al hebben voltooid:

* [Een schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)

## Een gegevensstroom maken

Nu, kunt u een gegevensstroom tot stand brengen om Platform Edge Network te vertellen waar te om gegevens te verzenden die door Web SDK worden verzameld.

**om een gegevensstroom tot stand te brengen:**

1. Open de [&#x200B; interface van de Inzameling van Gegevens &#x200B;](https://experience.adobe.com/data-collection/){target="_blank"}
1. Zorg ervoor dat u zich in de juiste sandbox bevindt

   >[!NOTE]
   >
   >Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP of Journey Optimizer, raden we u aan een ontwikkelingssandbox voor deze zelfstudie te gebruiken. Als u dat niet doet, gebruikt u de **[!UICONTROL Prod]** -sandbox.

1. Ga naar **[!UICONTROL Datastreams]** in de linkernavigatie
1. Selecteren **[!UICONTROL New Datastream]**
1. Voer `Luma Web SDK: Development Environment` in als de **[!UICONTROL Name]** . Deze naam wordt van verwijzingen voorzien later wanneer u de uitbreiding van SDK van het Web in uw markeringsbezit vormt.
1. Selecteren **[!UICONTROL Save]**

   ![&#x200B; creeer de datastream &#x200B;](assets/datastream-create-new-datastream.png)

   >[!NOTE]
   >
   >U hoeft geen schema te selecteren. Een schemaselectie wordt slechts vereist als u [&#x200B; Prep van Gegevens voor de eigenschap van de Inzameling van Gegevens &#x200B;](/help/data-collection/edge/data-prep.md) gebruikt.

Op het volgende scherm kunt u services, zoals Adobe-toepassingen, aan de gegevensstroom toevoegen, maar op dit moment kunt u geen services toevoegen. U zult dit later in de lessen [&#x200B; Opstelling Experience Platform &#x200B;](setup-experience-platform.md), [&#x200B; Opstelling Analytics &#x200B;](setup-analytics.md), [&#x200B; Opstelling Audience Manager &#x200B;](setup-audience-manager.md), [&#x200B; het Doel van de Opstelling &#x200B;](setup-target.md), of [&#x200B; Gebeurtenis door:sturen &#x200B;](setup-event-forwarding.md) doen.

>[!NOTE]
>
>Wanneer u Platform Web SDK op uw eigen website implementeert, moet u drie gegevensstreams maken om toe te wijzen aan uw drie tagomgevingen (ontwikkeling, werkgebied en productie). Als u Platform Web SDK met op platform-gebaseerde toepassingen zoals Adobe Real-Time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken van het Platform tot stand te brengen.

## Een gegevensstroom overschrijven

[&#x200B; DataStream treedt &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/overrides) met voeten staat u toe om extra configuraties voor uw gegevensstroom te bepalen en dan uw standaardconfiguratie onder bepaalde voorwaarden met voeten te treden.

De configuratieopheffing van gegevensstroom is een proces in twee stappen:

1. Eerst, bepaalt u gegevensstroom met voeten treedt in de configuratie van de datastream dienst. Bijvoorbeeld, zou u afwisselende het rapportreeksen van Analytics, de werkruimten van het Doel, of de datasets van het Platform kunnen bepalen om als met voeten te treden.
1. Dan, verzendt u de met voeten treedt naar Edge Network of met een SDK van het Web verzendt gebeurtenisactie, of door een configuratie in de de markeringsuitbreiding van SDK van het Web.

In de [&#x200B; les van de Opstelling Adobe Analytics &#x200B;](setup-analytics.md) &lbrace;, treedt u de rapportreeks voor een pagina met voeten gebruikend SDK van het Web van het Platform verzendt de Actie van de Gebeurtenis.

U kunt nu de extensie Platform Web SDK installeren in de eigenschap Tag.

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996?profile.language=nl)

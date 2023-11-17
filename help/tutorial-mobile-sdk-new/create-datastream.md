---
title: Een gegevensstroom configureren
description: Leer hoe u een gegevensstroom in Experience Platform maakt.
feature: Mobile SDK,Datastreams
hide: true
exl-id: d8b9df3d-49ee-4578-92c6-0f920a86fe7e
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# Een gegevensstroom maken

Leer hoe u een gegevensstroom in Experience Platform maakt.

Een gegevensstroom is een server-zijconfiguratie op het Netwerk van de Rand van het Platform. De gegevensstroom zorgt ervoor dat de inkomende gegevens aan het Netwerk van de Rand van het Platform aan de toepassingen en de diensten van Adobe Experience Cloud geschikt worden verpletterd. Zie de klasse [documentatie](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) of dit [video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html).

![Architectuur](assets/architecture.png)

## Vereisten

Om een gegevensstroom tot stand te brengen, moet uw organisatie provisioned voor deze eigenschap in de interface van de Inzameling van Gegevens (vroeger [!UICONTROL Starten]) en u moet gebruikersmachtigingen hebben voor het beheren en weergeven van gegevensstromen.

## Leerdoelstellingen

In deze les zult u:

* Weet wanneer u een gegevensstroom wilt gebruiken.
* Maak een gegevensstroom.
* Configureer een gegevensstroom.

## Een gegevensstroom maken

Gegevensstromen kunnen worden gemaakt in het dialoogvenster [!UICONTROL Gegevensverzameling] interface die de [!UICONTROL DataStream] configuratieprogramma. Een gegevensstroom maken:

1. Zorg ervoor dat u zich in de juiste sandbox met Experience Platforms bevindt, aangezien gegevensstreams op sandboxniveau zijn gedefinieerd.
1. Selecteren **[!UICONTROL Gegevensstromen]** in het linkerspoor.
1. Selecteren **[!UICONTROL Nieuwe DataStream]**.

   ![datastreams home](assets/datastream-new.png)

1. Geef een **[!UICONTROL Naam]** bijvoorbeeld `Luma Mobile App` en **[!UICONTROL Beschrijving]** bijvoorbeeld `Datastream for Luma Mobile App`.

   >[!NOTE]
   >
   >Laatste herinnering: als u deze zelfstudie doorloopt met meerdere personen in één sandbox of als u een gedeelde account gebruikt, kunt u overwegen een identificatie toe te voegen of voor te bereiden als onderdeel van uw naamgevingsconventies. Gebruik bijvoorbeeld `Luma Mobile App Event Dataset - Joe Smith` in plaats van `Luma Mobile App Event Dataset`. Zie ook de opmerking in [Overzicht](overview.md).

1. Selecteer het schema dat u in de vorige les van het **Gebeurtenisschema** lijst.
1. Selecteren **[!UICONTROL Opslaan]**.

   ![nieuwe gegevensstromen](assets/datastream-name.png)


## Services toevoegen

Wanneer u door (facultatief) gaat [Analyse](analytics.md) en [Experience Platform](platform.md) de lessen in dit leerprogramma, voegt u de diensten aan uw gegevensstroom toe zodat de gegevens die naar het Netwerk van de Rand van het Platform worden verzonden door:sturen naar deze toepassingen.

<!--

### Adobe Analytics

1. Select **[!UICONTROL Add Service]**.

1. Add **[!UICONTROL Adobe Analytics]** from the [!UICONTROL Service] list, 

1. Enter the name of the report site that you want to use in **[!UICONTROL Report Suite ID]**.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Analytics as datastream service](assets/datastream-service-aa.png)


### Adobe Experience Platform

You might also want to enable the Adobe Experience Platform service. 

>[!IMPORTANT]
>
>You can only enable the Adobe Experience Platform service when having created an event dataset. If you don't already have an event dataset created, follow the instructions [here](platform.md).

1. Click ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]** to add another service.

1. Select **[!UICONTROL Adobe Experience Platform]** from the [!UICONTROL Service] list.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select the **[!UICONTROL Event Dataset]** that you created as part of the [Create a dataset](platform.md#create-a-dataset) instructions, for example **Luma Mobile App Event Dataset**

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Experience Platform as a datastream service](assets/datastream-service-aep.png)
1. The final configuration should look something like this.
   
   ![datastream settings](assets/datastream-settings.png)

-->


>[!NOTE]
>
>Als u alle services inschakelt die uw organisatie gebruikt, zorgt u ervoor dat gegevens die in de mobiele app zijn verzameld, overal kunnen worden gebruikt. Raadpleeg de documentatie voor meer informatie over gegevensstroominstellingen [hier](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

Wanneer u Platform Mobile SDK implementeert in uw eigen app, moet u uiteindelijk drie gegevensstreams maken om toe te wijzen aan uw drie tagomgevingen (ontwikkeling, werkgebied en productie). Als u Platform Mobile SDK met op platform-gebaseerde toepassingen zoals Adobe Real-time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken tot stand te brengen.

>[!SUCCESS]
>
>U hebt nu een gegevensstroom voor de rest van de zelfstudie te gebruiken.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Een eigenschap voor een tag configureren](configure-tags.md)**

---
title: Een gegevensstroom configureren
description: Leer hoe u een gegevensstroom in Experience Platform maakt.
feature: Mobile SDK,Datastreams
hide: true
source-git-commit: 7de7c7e13ea6d02f1193620e0cc35299e07d59e5
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---


# Een gegevensstroom maken

Leer hoe u een gegevensstroom in Experience Platform maakt.

Een gegevensstroom is een server-zijconfiguratie op het Netwerk van de Rand van het Platform. De gegevensstroom zorgt ervoor dat de inkomende gegevens aan het Netwerk van de Rand van het Platform aan de toepassingen en de diensten van Adobe Experience Cloud geschikt worden verpletterd. Zie de klasse [documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) of dit [video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html).

## Vereisten

Om een gegevensstroom tot stand te brengen, moet uw organisatie provisioned voor deze eigenschap in de interface van de Inzameling van Gegevens (vroeger [!UICONTROL Starten]) en u moet over gebruikersmachtigingen beschikken voor [!UICONTROL Experience Platform] > [!UICONTROL Gegevensverzameling] > **[!UICONTROL Gegevensstromen beheren]** en **[!UICONTROL Gegevensstromen weergeven]**.

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
1. Selecteer het schema dat u in de vorige les van het **Gebeurtenisschema** een lijst.
1. Selecteren **[!UICONTROL Opslaan]**.

   ![nieuwe gegevensstromen](assets/datastream-name.png)


## Services toevoegen

Vervolgens sluit u de services van uw Experience Cloud aan op uw gegevensstroom. Wanneer Platform Mobile SDK gegevens naar Edge Network verzendt, verzendt de datastream de gegevens naar deze services:

1. Selecteren **[!UICONTROL Service toevoegen]**.

1. Toevoegen **[!UICONTROL Adobe Analytics]** van de [!UICONTROL Service] lijst,

1. Ga de naam van de rapportplaats in die u binnen wilt gebruiken **[!UICONTROL ID van rapportsuite]**.

1. Laat de dienst door omschakeling toe **[!UICONTROL Ingeschakeld]** op.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Adobe Analytics toevoegen als DataStream-service](assets/datastream-service-aa.png)

Mogelijk wilt u ook de Adobe Experience Platform-service inschakelen.

>[!IMPORTANT]
>
>U kunt de dienst van Adobe Experience Platform slechts toelaten wanneer het hebben tot een gebeurtenisdataset geleid. Als u nog geen gemaakte gebeurtenisdataset hebt, volgt u de instructies [hier](platform.md).

1. Klikken ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Service toevoegen]** om een andere service toe te voegen.

1. Selecteren **[!UICONTROL Adobe Experience Platform]** van de [!UICONTROL Service] lijst.

1. Laat de dienst door omschakeling toe **[!UICONTROL Ingeschakeld]** op.

1. Selecteer de **[!UICONTROL Gebeurtenisgegevens]** die u hebt gemaakt als onderdeel van de [Een gegevensset maken](platform.md#create-a-dataset) instructie, bijvoorbeeld **Dataset voor Luma Mobile-toepassingsgebeurtenis**

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Adobe Experience Platform toevoegen als DataStream-service](assets/datastream-service-aep.png)
1. De uiteindelijke configuratie moet er ongeveer zo uitzien.

   ![gegevensstroominstellingen](assets/datastream-settings.png)


>[!NOTE]
>
>Als u alle services inschakelt die uw organisatie gebruikt, zorgt u ervoor dat gegevens die in de mobiele app zijn verzameld, overal kunnen worden gebruikt. Raadpleeg de documentatie voor meer informatie over gegevensstroominstellingen [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html#adobe-experience-platform-settings).

Wanneer u Platform Mobile SDK implementeert in uw eigen app, moet u drie gegevensstreams maken om toe te wijzen aan uw drie tagomgevingen (ontwikkeling, werkgebied en productie). Als u Platform Mobile SDK met op platform-gebaseerde toepassingen zoals Adobe Real-time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken van het Platform tot stand te brengen.

>[!SUCCESS]
>
>U hebt nu een gegevensstroom voor de rest van de zelfstudie te gebruiken.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Tags configureren](configure-tags.md)**

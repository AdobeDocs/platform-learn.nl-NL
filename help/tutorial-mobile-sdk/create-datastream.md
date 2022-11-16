---
title: Een gegevensstroom configureren
description: Leer hoe u een gegevensstroom in Experience Platform maakt.
exl-id: 7b83f834-d1fb-45d1-8bcf-bc621f94725c
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Een gegevensstroom maken

Leer hoe u een gegevensstroom in Experience Platform maakt.

Een gegevensstroom is een server-zijconfiguratie op het Netwerk van de Rand van het Platform.  De gegevensstroom zorgt ervoor dat de inkomende gegevens aan het Netwerk van de Rand van het Platform aan de toepassingen en de diensten van Adobe Experience Cloud geschikt worden verpletterd. Zie voor meer informatie de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) of dit [video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html).

## Vereisten

Om een gegevensstroom tot stand te brengen, moet uw organisatie voor deze eigenschap in de interface van de Inzameling van Gegevens (vroeger) worden provisioned [!UICONTROL Starten]) en u moet over gebruikersmachtigingen beschikken voor [!UICONTROL Experience Platform] > [!UICONTROL Gegevensverzameling] > **[!UICONTROL Gegevensstromen beheren]** en **[!UICONTROL Gegevensstromen weergeven]**.

## Leerdoelstellingen

In deze les zult u:

* Weet wanneer u een gegevensstroom wilt gebruiken.
* Maak een gegevensstroom.
* Configureer een gegevensstroom.

## Een gegevensstroom maken

Gegevensstromen kunnen worden gemaakt in het dialoogvenster [!UICONTROL Gegevensverzameling] interface gebruiken [!UICONTROL DataStream] configuratieprogramma. Een gegevensstroom maken:

1. Zorg ervoor dat u zich in de juiste sandbox met Platforms bevindt.
1. Selecteren **[!UICONTROL Nieuwe DataStream]**.

   ![datastreams home](assets/mobile-datastream-new.png)

1. Geef bijvoorbeeld een naam op `Luma App`.
1. Selecteer het schema u in de vorige les creeerde.
1. Selecteren **[!UICONTROL Opslaan]**.

   ![nieuwe gegevensstromen](assets/mobile-datastream-name.png)


## Services toevoegen

Vervolgens kunt u uw Experience Cloud-services verbinden met uw gegevensstroom. Wanneer Platform Mobile SDK gegevens naar Edge Network verzendt, verzendt de gegevensstroom de gegevens naar deze services:

1. Toevoegen **[!UICONTROL Adobe Analytics]** en een rapportsuite.

1. Inschakelen **[!UICONTROL Adobe Audience Manager]** (optioneel).

1. Inschakelen **[!UICONTROL Adobe Experience Platform]** en een **[!UICONTROL gegevensset]** (optioneel).
   * Als u nog geen dataset hebt gemaakt, volgt u de instructies [hier](platform.md).

1. De uiteindelijke configuratie moet er ongeveer zo uitzien.
   ![gegevensstroominstellingen](assets/mobile-datastream-settings.png)


>[!NOTE]
>
>Als u alle services inschakelt die uw organisatie gebruikt, zorgt u ervoor dat gegevens die in de mobiele app zijn verzameld, overal kunnen worden gebruikt. Meer informatie over gegevensstroominstellingen vindt u in de documentatie [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html#adobe-experience-platform-settings).

Wanneer u Platform Mobile SDK implementeert op uw eigen website, moet u drie gegevensstreams maken om deze toe te wijzen aan uw drie labelomgevingen (ontwikkeling, werkgebied en productie). Als u Platform Mobile SDK met op Platform-gebaseerde toepassingen zoals Adobe Real-time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken van het Platform tot stand te brengen.

Volgende: **[Tags configureren](configure-tags.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

---
title: Een gegevensstroom configureren
description: Leer hoe te om een gegevensstroom toe te laten en Experience Cloud oplossingen te vormen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Datastreams
exl-id: ca28374a-9fe0-44de-a7ac-0aa046712515
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Een gegevensstroom configureren

Leer hoe te om een gegevensstroom toe te laten en Experience Cloud oplossingen te vormen.

De gegevensstromen vertellen het Netwerk van Adobe Experience Platform Edge waar te om gegevens te verzenden die door het Web SDK van het Platform worden verzameld. In de configuratie van gegevensstromen, laat u uw toepassingen van de Experience Cloud, uw rekening van het Experience Platform, en gebeurtenis toe door:sturen. Zie de [Grondbeginselen van het Vormen van een DataStream](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=en) voor meer gedetailleerde informatie.

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een gegevensstroom maken
* Uw Experience Cloud-toepassingen inschakelen
* Experience Platform inschakelen

## Vereisten

Voordat u de gegevensstroom configureert, moet u de volgende lessen al hebben voltooid:

* [Machtigingen configureren](configure-permissions.md)
* [Een schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)

## Een gegevensstroom maken

Nu kunt u een gegevensstroom tot stand brengen om het Netwerk van de Rand van het Platform te vertellen waar te om gegevens te verzenden die door SDK van het Web worden verzameld.

**Een gegevensstroom maken:**

1. Open de [Interface voor gegevensverzameling](https://launch.adobe.com/){target=&quot;_blank&quot;}
1. Zorg ervoor dat u zich in de juiste sandbox bevindt

   >[!NOTE]
   >
   >Als u de klant van een op Platform-gebaseerde toepassing zoals in real time CDP bent, adviseren wij het gebruiken van een ontwikkelingszandbak voor dit leerprogramma.

1. Ga naar **[!UICONTROL DataStreams]** in de linkernavigatie
1. Selecteren **[!UICONTROL Nieuwe DataStream]** aan de rechterkant van het scherm.
1. Enter `Luma Web SDK` als de **[!UICONTROL Naam]**. Deze naam wordt van verwijzingen voorzien later wanneer u de uitbreiding van SDK van het Web in uw markeringsbezit vormt.
1. Selecteer uw `Luma Web Event Data` als de **[!UICONTROL Gebeurtenisschema]**
1. Selecteren **[!UICONTROL Opslaan]**

   ![De gegevensstroom maken](assets/datastream-create-datastream.png)

   >[!AVAILABILITY]
   >
   >De toewijzingsfunctie wordt later in deze zelfstudie opgenomen.




Op het volgende scherm, kunt u de diensten zoals de toepassingen van Adobe aan de datastream toevoegen, nochtans zult u geen diensten op dit punt in het leerprogramma toevoegen. U zult dit later doen in de lessen [Experience Platform instellen](setup-experience-platform.md), [Analyses instellen](setup-analytics.md), [Audience Manager instellen](setup-audience-manager.md), [Doel instellen](setup-target.md), of [Gebeurtenis doorsturen](setup-event-forwarding.md).

>[!NOTE]
>
>Wanneer u SDK van Platform Web op uw eigen website implementeert, moet u drie gegevensstromen maken om toe te wijzen aan uw drie tagomgevingen (ontwikkeling, werkgebied en productie). Als u het Web SDK van het Platform met op Platform-gebaseerde toepassingen zoals Adobe Real-time Customer Data Platform of Adobe Journey Optimizer gebruikt, zou u zeker moeten zijn om die gegevensstromen in de aangewezen zandbakken van het Platform tot stand te brengen.

U bent nu klaar om de uitbreiding van SDK van het Web van het Platform in uw markeringsbezit te installeren!

[Volgende: ](install-web-sdk.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
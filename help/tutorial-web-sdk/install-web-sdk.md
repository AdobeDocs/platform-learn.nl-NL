---
title: De tagextensie Adobe Experience Platform Web SDK installeren en configureren
description: Leer hoe te om de de markeringsuitbreiding van SDK van het Web van het Platform in de interface van de Inzameling van Gegevens te installeren en te vormen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK
exl-id: f30a44bb-99d7-476e-873a-b7802a0fe6aa
source-git-commit: aeff30f808fd65370b58eba69d24e658474a92d7
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Adobe Experience Platform Web SDK-tagextensie installeren

Leer om de de marktextensie van SDK van het Web van het Platform te installeren en te vormen. De gemakkelijkste manier om Web SDK uit te voeren is het gebruiken van de markeringsmanager van de Adobe, markeringen (vroeger die als Lancering wordt bekend). De tagextensie van Platform Web SDK is _alleen tagextensie_ vereist om gegevens te verzenden naar _alle Adobe Experience Cloud-toepassingen_, inclusief [Analyse](setup-analytics.md), [Doel](setup-target.md), [Audience Manager](setup-audience-manager.md), Real-time Customer Data Platform, en [Journey Optimizer](setup-web-channel.md)!

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een tageigenschap maken in de interface voor gegevensverzameling
* De tagextensie Platform Web SDK installeren
* Uw eerder gemaakte gegevensstroom toewijzen aan de extensie

## Vereisten

U moet de vorige lessen in deze zelfstudie hebben voltooid:

* [Een gegevensstroom configureren](configure-datastream.md)

## Experience Platform Web SDK-extensie installeren

### Een eigenschap toevoegen

Eerst moet u een eigenschap tag hebben. Een eigenschap is een container voor alle JavaScript, regels en andere functies die vereist zijn om gegevens van een webpagina te verzamelen en naar verschillende locaties te verzenden.

Een nieuwe eigenschap voor tags maken voor de zelfstudie:

1. Open de [Interface voor gegevensverzameling](https://launch.adobe.com/){target="_blank"}
1. Selecteren **[!UICONTROL Tags]** in de linkernavigatie
1. Selecteer de **[!UICONTROL New Property]** knop
   ![Een nieuwe eigenschap toevoegen](assets/websdk-property-addNewProperty.png)
1. Als de **[!UICONTROL Name]**, enter `Web SDK Course` (voeg uw naam aan het eind toe, als de veelvoudige mensen van uw bedrijf dit leerprogramma nemen)
1. Als de **[!UICONTROL Domains]**, enter `enablementadobe.com` (later toegelicht)
1. Selecteren **[!UICONTROL Save]**
   ![Eigendomsdetails](assets/websdk-property-propertyDetails.png)

## De Web SDK-extensie toevoegen

Met uw XDM-schema, gegevensstroom en markeringseigenschap die nu zijn gemaakt, kunt u de extensie Platform Web SDK installeren:

1. De nieuwe eigenschap tag openen
1. Ga naar **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**
1. Zoeken naar `Adobe Experience Platform Web SDK`
1. Selecteren **[!UICONTROL Install]**

   ![Web SDK-extensie installeren](assets/extension-platform-web-sdk.png)


## De SDK van het Web van het Platform van de verbinding aan uw gegevensstroom

Laat de meeste standaardinstellingen ongewijzigd en werk deze indien nodig later bij. Het enige wat u nu moet doen is de uitbreiding met uw gegevensstroom verbinden:

1. Onder **[!UICONTROL Datastreams]**, selecteert u de **[!UICONTROL Choose from list]** invoermethode
1. Selecteer de gegevensstroom u vroeger creeerde, `Luma Web SDK`
1. Selecteren **[!UICONTROL Save]**

   >[!NOTE]
   >
   > Als u uw gegevensstroom niet kunt vinden, ga naar [Een gegevensstroom configureren](configure-datastream.md) les en volg de stappen om één te creëren

   ![Gegevensstroom selecteren](assets/extension-luma-web-sdk-datastream-extension.png)

Nu u het Web SDK van het Platform hebt geïnstalleerd en het aan de datastream associeerde, bent u klaar om gegevenselementen aan een voorwerp van XDM met het schema te beginnen in kaart te brengen u creeerde.

>[!NOTE]
>
>Tijdens deze zelfstudie configureert u slechts één gegevensstroom en koppelt u deze aan alle labelomgevingen (ontwikkeling, werkgebied en productie). Wanneer u Platform Web SDK op uw eigen website implementeert, moet u een aparte gegevensstroom voor elke omgeving configureren en deze toewijzen aan uw tagomgevingen.

>[!NOTE]
>
>Terwijl u geen CNAME in [!UICONTROL Edge domain] het plaatsen in deze les, adviseert de Adobe u een CNAME gebruikt wanneer u het Web SDK van het Platform op uw eigen website uitvoert. Terwijl een implementatie CNAME geen voordelen in termen van koekjesleven verstrekt, kunnen er sommige andere voordelen zijn. Deze voordelen zijn onder andere adverteerders en minder gangbare browsers die voorkomen dat gegevens worden verzonden naar domeinen die ze als trackers classificeren. In deze gevallen kunt u met een CNAME voorkomen dat de gegevensverzameling wordt onderbroken voor gebruikers die deze gereedschappen gebruiken.

Voor meer informatie over elke sectie van de uitbreiding, zie [De extensie Adobe Experience Platform Web SDK configureren](https://experienceleague.adobe.com/en/docs/experience-platform/edge/extension/web-sdk-extension-configuration)



[Volgende: ](create-data-elements.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

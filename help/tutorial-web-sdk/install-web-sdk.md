---
title: De extensie Adobe Experience Platform Web SDK installeren en configureren
description: Leer hoe te om de de markeringsuitbreiding van SDK van het Web van het Platform in de interface van de Inzameling van Gegevens te installeren en te vormen. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK, Tags
jira: KT-15404
exl-id: f30a44bb-99d7-476e-873a-b7802a0fe6aa
source-git-commit: e0359d1bade01f79d0f7aff6a6e69f3e4d0c3b62
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# Adobe Experience Platform Web SDK-tagextensie installeren

Leer hoe u de Adobe Experience Platform Web SDK-tagextensie installeert en configureert. De eenvoudigste manier om Web SDK te implementeren is het gebruik van Adobe-tagbeheer, -tags (voorheen Launch genoemd). De de markeringsuitbreiding van SDK van het Platform is de _slechts markeringsuitbreiding_ wordt vereist om gegevens naar _alle toepassingen van Adobe Experience Cloud_, met inbegrip van [ Analytics ](setup-analytics.md), [ Doel ](setup-target.md), [ Audience Manager ](setup-audience-manager.md), Real-Time Customer Data Platform, en [ Journey Optimizer ](setup-web-channel.md) te verzenden!

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een tageigenschap maken in de interface voor gegevensverzameling
* De extensie Platform Web SDK installeren
* Uw eerder gemaakte gegevensstroom toewijzen aan de extensie

## Vereisten

U moet de vorige lessen in deze zelfstudie hebben voltooid:

* [Een gegevensstroom configureren](configure-datastream.md)

### Een eigenschap voor een tag toevoegen

Eerst moet u een eigenschap tag hebben. Een eigenschap is een container voor alle JavaScript, regels en andere functies die zijn vereist voor het verzamelen van gegevens van een webpagina en het verzenden ervan naar verschillende locaties.

Een nieuwe eigenschap voor tags maken voor de zelfstudie:

1. Open de [ interface van de Inzameling van Gegevens ](https://experience.adobe.com/data-collection/){target="_blank"}
1. Selecteren **[!UICONTROL Tags]** in de linkernavigatie
1. Selecteer de knop **[!UICONTROL New Property]**
   ![ voeg een nieuw bezit ](assets/websdk-property-addNewProperty.png) toe
1. Als **[!UICONTROL Name]**, ga `Web SDK Course` in (voeg uw naam aan het eind toe, als de veelvoudige mensen van uw bedrijf deze zelfstudie nemen)
1. Als **[!UICONTROL Domains]** voert u `enablementadobe.com` in (zoals verderop wordt uitgelegd)
1. Selecteren **[!UICONTROL Save]**
   ![ de details van het Bezit ](assets/websdk-property-propertyDetails.png)

## De extensie Web SDK toevoegen

Met uw XDM-schema, gegevensstroom en markeringseigenschap die nu zijn gemaakt, kunt u de extensie Platform Web SDK installeren:

1. De nieuwe eigenschap tag openen
1. Ga naar **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**
1. Zoeken naar `Adobe Experience Platform Web SDK`
1. Selecteren **[!UICONTROL Install]**

   ![ installeer de Uitbreiding van SDK van het Web ](assets/extension-platform-web-sdk.png)


## De extensie koppelen aan uw gegevensstroom

Laat de meeste standaardinstellingen ongewijzigd en werk deze indien nodig later bij. Het enige wat u nu moet doen is de uitbreiding met uw gegevensstroom verbinden:

1. Selecteer onder **[!UICONTROL Datastreams]** de invoermethode **[!UICONTROL Choose from list]**
1. Selecteer de sandbox waarin u het schema, de naamruimte en de gegevensstroom hebt gemaakt
1. Selecteer de gegevensstroom die u eerder hebt gemaakt, `Luma Web SDK`
1. Selecteren **[!UICONTROL Save]**

   >[!NOTE]
   >
   > Als u niet uw gegevensstroom kunt vinden, ga naar [ een datastream ](configure-datastream.md) les vormen en de stappen volgen om te creëren

   ![ selectie DataStream ](assets/extension-luma-web-sdk-datastream-extension.png)

Voor meer informatie over elke sectie van de uitbreiding, zie [ de uitbreiding van SDK van het Web van Adobe Experience Platform ](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/client/web-sdk/web-sdk-extension-configuration) vormen.

>[!NOTE]
>
>Hoewel u geen CNAME in het [!UICONTROL Edge domain] plaatsen in deze les vormde, adviseert Adobe u een CNAME te gebruiken wanneer u het Web SDK van het Platform op uw eigen website uitvoert. Terwijl een implementatie CNAME geen voordelen in termen van koekjesleven verstrekt, kunnen er sommige andere voordelen zijn. Deze voordelen zijn onder andere adverteerders en minder gangbare browsers die voorkomen dat gegevens worden verzonden naar domeinen die ze als trackers classificeren. In deze gevallen kunt u met een CNAME voorkomen dat de gegevensverzameling wordt onderbroken voor gebruikers die deze gereedschappen gebruiken.

>[!NOTE]
>
>Tijdens deze zelfstudie configureert u slechts één gegevensstroom en koppelt u deze aan alle labelomgevingen (ontwikkeling, werkgebied en productie). Wanneer u het Web SDK van het Platform op uw eigen website uitvoert, zou u een afzonderlijke gegevensstroom voor elk milieu moeten vormen en hen dienovereenkomstig in de uitbreidingsconfiguratie in kaart brengen.

Nu u Platform Web SDK hebt geïnstalleerd en het met de datastream hebt geassocieerd, bent u klaar om te beginnen gegevens te verzamelen.

[Volgende: ](create-data-elements.md)

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

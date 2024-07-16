---
title: Een tag-eigenschap maken
description: Leer hoe u zich aanmeldt bij de interface Gegevensverzameling en een eigenschap tag maakt. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: f83d374a-a831-4598-b9d3-6f183224b589
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Een tag-eigenschap maken

In deze les zult u uw eerste markeringsbezit tot stand brengen.

Een eigenschap is in feite een container die u vult met extensies, regels, gegevenselementen en bibliotheken wanneer u tags op uw site implementeert.

## Vereisten

Als u de volgende lessen wilt voltooien, moet u toestemming hebben om ontwikkelings-, goedkeurings-, Publish-, beheer- en beheeromgevingen in tags te ontwikkelen. Als u geen van deze stappen kunt uitvoeren omdat de gebruikersinterfaceopties niet beschikbaar zijn, vraagt u de beheerder van het Experience Cloud om toegang. Voor meer informatie over de toestemmingen van de markeringsgebruiker, zie [ de documentatie ](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * Platform launch (de Kant van de Cliënt) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * De Server zijde van de platform launch is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * De configuraties van Edge zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Aanmelden bij de gebruikersinterface voor gegevensverzameling
* Een nieuwe eigenschap voor tags maken
* Een eigenschap voor een tag configureren

## Ga naar de interface voor gegevensverzameling

**om aan de Inzameling van Gegevens te krijgen**

1. Logboek in [ Adobe Experience Cloud ](https://experiencecloud.adobe.com)

1. Klik het ](images/launch-solutionSwitcher.png) pictogram van de Schakelaar van de Oplossing van 0} {om app schakelaar te openen![

1. Selecteer **[!UICONTROL Launch/Data Collection]** van het menu ![ Open de oplossingsschakelaar gebruikend het pictogram en klik de Inzameling van de Lancering/van Gegevens ](images/launch-solutionSwitcherActivation.png)

U moet nu het scherm `Tags Properties` zien (als er geen eigenschappen in de account zijn gemaakt, is dit scherm mogelijk leeg):

![ het Scherm van Eigenschappen ](images/launch-propertiesScreen.png)

## Een eigenschap maken

Een eigenschap is in feite een container die u vult met extensies, regels, gegevenselementen en bibliotheken wanneer u tags op uw site implementeert. Een eigenschap kan elke groepering van een of meer domeinen en subdomeinen zijn. U kunt deze elementen op dezelfde manier beheren en bijhouden. Stel dat u meerdere websites hebt die op één sjabloon zijn gebaseerd en dat u dezelfde elementen op alle websites wilt bijhouden. U kunt één eigenschap toepassen op meerdere domeinen. Voor meer informatie bij het creëren van eigenschappen, zie [ &quot;Bedrijven en Eigenschappen&quot;](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html) in de productdocumentatie.

**om een Bezit** te creëren

1. Klik op de knop **[!UICONTROL New Property]** :

   ![ klik Nieuw Bezit ](images/launch-addNewProperty.png)

1. Geef de eigenschap een naam (bijvoorbeeld `Luma Tutorial` of `Luma Tutorial - Daniel` )
1. Voer `enablementadobe.com` in als domein, aangezien dit het domein is waar de Luma-demosite wordt gehost. Hoewel het veld &quot;Domein&quot; is vereist, werkt de eigenschap tag op elk domein waarin deze is geïmplementeerd. Het belangrijkste doel van dit gebied is menuopties in de Bouwer van de Regel vooraf in te vullen.
1. Vouw de sectie **[!UICONTROL Advanced Options]** uit en schakel het selectievakje in op **[!UICONTROL Run rule components in sequence]**
1. Klik op de knop **[!UICONTROL Save]**

   ![ creeer een nieuw Bezit ](images/launch-newProperty.png)

De nieuwe eigenschap moet worden weergegeven op de pagina Eigenschappen. Als u het vakje naast de eigenschapsnaam inschakelt, worden opties voor **[!UICONTROL Configure]** of **[!UICONTROL Delete]** de eigenschap boven de eigenschappenlijst weergegeven. Klik op de naam van de eigenschap (bijvoorbeeld `Luma Tutorial` ) om het scherm `Overview` te openen.
![ klik de naam van het bezit om het ](images/launch-openProperty.png) te openen

[Volgende &quot;Voeg de Insluitcode toe&quot; >](add-embed-code.md)

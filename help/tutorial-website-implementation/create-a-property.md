---
title: Een tag-eigenschap maken
description: Leer hoe u zich aanmeldt bij de interface Gegevensverzameling en een eigenschap tag maakt. Deze les maakt deel uit van de zelfstudie Experience Cloud in websites implementeren.
exl-id: f83d374a-a831-4598-b9d3-6f183224b589
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 1%

---

# Een tag-eigenschap maken

In deze les zult u uw eerste markeringsbezit creëren.

Een eigenschap is in feite een container die u vult met extensies, regels, gegevenselementen en bibliotheken wanneer u tags op uw site implementeert.

## Vereisten

Als u de volgende lessen wilt voltooien, moet u gemachtigd zijn om omgevingen in tags te ontwikkelen, goedkeuren, publiceren, beheren en beheren. Als u geen van deze stappen kunt uitvoeren omdat de gebruikersinterfaceopties niet beschikbaar zijn, vraagt u de beheerder van de Experience Cloud om toegang. Voor meer informatie over de toestemmingen van de markeringsgebruiker, zie [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * platform launch (clientzijde) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * platform launch Server-zijde is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-configuraties zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**


## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Aanmelden bij de gebruikersinterface voor gegevensverzameling
* Een nieuwe eigenschap voor tags maken
* Een eigenschap voor een tag configureren

## Ga naar de interface voor gegevensverzameling

**Ga naar Gegevensverzameling**

1. Aanmelden bij [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Klik op de knop ![Pictogram voor wisselen van oplossingen](images/launch-solutionSwitcher.png) pictogram om de app-switch te openen

1. Selecteren **[!UICONTROL Starten/gegevensverzameling]** in het menu ![Open de oplossingsschakelaar gebruikend het pictogram en klik Lancering/de Inzameling van Gegevens](images/launch-solutionSwitcherActivation.png)

U moet nu de `Tags Properties` scherm (als er geen eigenschappen in de account zijn gemaakt, is dit scherm mogelijk leeg):

![Scherm Eigenschappen](images/launch-propertiesScreen.png)

## Een eigenschap maken

Een eigenschap is in feite een container die u vult met extensies, regels, gegevenselementen en bibliotheken wanneer u tags op uw site implementeert. Een eigenschap kan elke groepering van een of meer domeinen en subdomeinen zijn. U kunt deze elementen op dezelfde manier beheren en bijhouden. Stel dat u meerdere websites hebt die op één sjabloon zijn gebaseerd en dat u dezelfde elementen op alle websites wilt bijhouden. U kunt één eigenschap toepassen op meerdere domeinen. Zie voor meer informatie over het maken van eigenschappen [&quot;Bedrijven en eigenschappen&quot;](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html) in de productdocumentatie.

**Een eigenschap maken**

1. Klik op de knop **[!UICONTROL Nieuwe eigenschap]** knop:

   ![Klik op Nieuwe eigenschap](images/launch-addNewProperty.png)

1. Geef de eigenschap een naam (bijvoorbeeld `Luma Tutorial` of `Luma Tutorial - Daniel`)
1. Als domein voert u `enablementadobe.com` aangezien dit het domein is waar de Luma demo plaats wordt ontvangen. Hoewel het veld &quot;Domein&quot; is vereist, werkt de eigenschap tag op elk domein waarin deze is geïmplementeerd. Het belangrijkste doel van dit gebied is menuopties in de Bouwer van de Regel vooraf in te vullen.
1. Breid uit **[!UICONTROL Geavanceerde opties]** en schakel het selectievakje in naar **[!UICONTROL Regelcomponenten op volgorde uitvoeren]**
1. Klik op de knop **[!UICONTROL Opslaan]** knop

   ![Een nieuwe eigenschap maken](images/launch-newProperty.png)

De nieuwe eigenschap moet worden weergegeven op de pagina Eigenschappen. Als u het selectievakje naast de naam van de eigenschap inschakelt, kunt u **[!UICONTROL Configureren]** of **[!UICONTROL Verwijderen]** de eigenschap wordt boven de eigenschappenlijst weergegeven. Klik op de naam van de eigenschap (bijvoorbeeld `Luma Tutorial`) om de `Overview` scherm.
![Klik op de naam van de eigenschap om deze te openen](images/launch-openProperty.png)

[Volgende &quot;Voeg de Insluitcode toe&quot; >](add-embed-code.md)

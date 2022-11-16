---
title: Een schema maken
description: Een schema maken
exl-id: 0256b358-0c2c-4c59-ab23-5fe0d38880d6
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# Een schema maken

Zoals besproken in [Gegevens structureren](../structuring-your-data.md)Gegevens die naar Adobe Experience Platform worden verzonden, moeten in XDM staan. Meer specifiek moeten uw gegevens overeenkomen met een _schema_. Een schema is in feite een beschrijving van hoe de gegevens eruit moeten zien. Hierin worden de namen van de velden beschreven en wordt aangegeven waar deze zich in de gegevens moeten bevinden. Het beschrijft ook het type waarde dat elk veld moet hebben (bijvoorbeeld een booleaanse waarde, een tekenreeks met een lengte van 12 tekens, een array van getallen).

Adobe Experience Platform biedt een aantal bouwstenen die buiten de doos liggen en die bekend staan als veldgroepen die in de branche veel voorkomen. Voor de financiële dienstensector zijn er bijvoorbeeld veldgroepen voor saldooverdrachten en kredietaanvragen. Voor de reis- en gastindustrie zijn er veldgroepen voor vluchten en reserveringen.

Wij adviseren u de ingebouwde gebiedsgroepen waar mogelijk te gebruiken wanneer het creëren van uw schema. We begrijpen ook dat u velden nodig hebt die specifiek zijn voor uw eigen bedrijf. Daarom kunt u uw eigen aangepaste veldgroepen maken die u kunt gebruiken binnen de schema&#39;s die u maakt.

Laten we doorlopen met het maken van een schema voor een typische e-commercewebsite.

1. Selecteren **[!UICONTROL Schemas]** krachtens [!UICONTROL Gegevensbeheer] in het linkerzijmenu in de Adobe Experience Platform-interface.
1. Selecteren **[!UICONTROL Schema maken]** in de rechterbovenhoek, en **[!UICONTROL XDM ExperienceEvent]** in de keuzelijst.

U bent nu op het canvas van de schemabouwer.
![Schemaweergave](../assets/schemas-view.png)

## Veldgroepen toevoegen

1. In de **[!UICONTROL Veldgroepen]** aan de linkerkant van het dialoogvenster **[!UICONTROL Structuur]** gebied, selecteert u de **[!UICONTROL + Toevoegen]** koppeling. Op dit punt, zal een modaal tonen om de gebiedsgroepen te kiezen aan uw schema toe te voegen.
1. Selecteer eerst de veldgroep met de naam **[!UICONTROL AEP Web SDK ExperienceEvent]**. Deze veldgroep voegt een set velden toe waarin automatisch gegevens worden opgenomen die door Adobe Experience Platform Web SDK worden verzameld.
   ![Mengsel van AEP Web SDK](../assets/aep-web-sdk-mixin.png)
1. Aangezien de website voor deze zelfstudie een e-commercewebsite is, selecteert u vervolgens de **[!UICONTROL Handelsgegevens]** veldgroep. Met deze veldgroep kunt u typische gegevens verzenden, zoals de producten die worden weergegeven, aan de winkelwagen worden toegevoegd en worden aangeschaft.
1. Selecteer **[!UICONTROL Veldgroepen toevoegen]** rechtsboven in het dialoogvenster.
   ![Mengsel van handelsdetails](../assets/commerce-details-mixin.png)
1. Op dit punt, zou u de structuur van uw schema moeten zien.
   ![Schema met mengsels](../assets/schema-with-mixins.png)

## Het schema opslaan

1. Geef als laatste een naam en een beschrijving op aan de rechterkant van het scherm en selecteer **[!UICONTROL Opslaan]**.
   ![Schema met naam en beschrijving](../assets/schema-name-description.png)

Uw schema is gemaakt. Daarna, leren hoe te om een dataset tot stand te brengen om uw gegevens op te slaan.

Voor meer informatie over het creëren van schema&#39;s, zie [Schema&#39;s maken](/help/platform/schemas/create-schemas.md).

[Volgende: ](create-a-dataset.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

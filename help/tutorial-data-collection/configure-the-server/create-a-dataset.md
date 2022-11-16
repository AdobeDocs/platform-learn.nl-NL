---
title: Een gegevensset maken
description: Een gegevensset maken
exl-id: 19a60087-2f78-4510-b127-b1007a6b7a56
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Een gegevensset maken

Naast het beschrijven van de gegevens die u naar Adobe Experience Platform verzendt, hebt u een plaats nodig om de gegevens te handhaven. In Adobe Experience Platform worden deze emmers waar u gegevens kunt plaatsen, gegevenssets genoemd.

>[!NOTE]
>
>Datasets worden niet vereist als u het Web SDK van het Platform slechts gebruikt om gegevens naar Adobe Analytics, Adobe Target, en Adobe Audience Manager te verzenden of het gebruiken van Gebeurtenis door:sturen. Als u Web SDK voor die doeleinden slechts gebruikt, kunt u deze pagina van het leerprogramma overslaan.

1. Selecteren **[!UICONTROL Gegevenssets]** krachtens [!UICONTROL Gegevensbeheer] in het linkerzijmenu in Adobe Experience Platform.
1. Selecteer vervolgens de **[!UICONTROL Gegevensset maken]** in de rechterbovenhoek.
   ![Gegevens, weergave](../assets/datasets-view.png)

## Een gegevensset maken op basis van een schema

1. Van de [!UICONTROL Workflow] interface, selecteert u de eerste tegel; **[!UICONTROL Gegevensset maken van schema]**.
1. Zoeken naar [het schema dat u eerder hebt gemaakt](create-a-schema.md) en selecteert u deze.
   ![Schema selecteren](../assets/schema-selection.png)
1. Selecteren **[!UICONTROL Volgende]** en geef een naam en een beschrijving.
   ![Naam en beschrijving van gegevensset](../assets/dataset-name-description.png)
1. Selecteren **[!UICONTROL Voltooien]**. Uw dataset is gecreeerd en is klaar om gegevens te ontvangen.

Terwijl u gegevens naar een gegevensset gaat verzenden, controleert Adobe Experience Platform of de gegevens die u in de gegevensset wilt plaatsen, overeenkomen met het toegepaste schema. Als de gegevens niet met het schema in overeenstemming zijn, worden de gegevens verworpen en niet geplaatst in de dataset. Als gevolg van deze valideringsstap kunnen de gebruikers van de gegevensset (Adobe-producten, derden of uw eigen bedrijf) enige mate van zekerheid hebben met betrekking tot de structuur en de zuiverheid van de gegevens in de gegevensset.

Voor meer informatie over het creëren van datasets, zie [Gegevenssets maken en gegevens opnemen](/help/platform/data-ingestion/create-datasets-and-ingest-data.md).

[Volgende: ](create-a-datastream.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)


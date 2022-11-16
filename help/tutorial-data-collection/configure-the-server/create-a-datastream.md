---
title: Een gegevensstroom maken
description: Een gegevensstroom maken
exl-id: 4a33a7f3-8bd8-4d28-9ae4-a0609444485f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Een gegevensstroom maken

De gegevens die u van uw website met het Web SDK van het Platform verzendt bereiken een reeks servers van Adobe genoemd [Adobe Experience Platform Edge Network](https://business.adobe.com/products/experience-platform/experience-platform-edge-network.html). Dit netwerk kan uw gegevens naar [Adobe Experience Platform-gegevensset die u eerder hebt gemaakt](create-a-schema.md) en andere producten in Adobe Experience Cloud. Deze Adobe-producten reageren mogelijk ook met gegevens op uw webpagina. Edge Network kan bijvoorbeeld personalisatie-inhoud uit Adobe Target retourneren.

Om te vormen welke de producten van de Rand van het Netwerk van de Adobe gegevens aan en van, u een gegevensstroom moet creëren. Wanneer Edge Network gegevens van uw webpagina ontvangt, raadpleegt het de gegevensstroom die u hebt gemaakt, leest het zijn configuratie en stuurt het vervolgens gegevens door naar de juiste Adobe-producten.

![Productconfiguratie DataStream](../assets/datastream-diagram.png)

1. Als u een gegevensstroom wilt maken, moet u eerst naar de gebruikersinterface van Gegevensverzameling navigeren. Klik in de rechterbovenhoek van het Platform op de knop **[!UICONTROL Toepassingskiezer]** en selecteert u **[!UICONTROL Gegevensverzameling]** in het keuzemenu.
   ![Menu Gegevensverzameling](../assets/data-collection-menu.png)
1. Zodra de interface van de Inzameling van Gegevens toont, selecteer **[!UICONTROL DataStreams]** in de linkernavigatie, en dan **[!UICONTROL Nieuwe DataStream]** in de rechterbovenhoek.
1. Geef een naam op voor de gegevensstroom. Selecteer [het schema dat u eerder hebt gemaakt](create-a-schema.md) als de **[!UICONTROL Gebeurtenisgegevens]** en selecteert u **[!UICONTROL Opslaan]** (Toewijzing wordt later behandeld).
   ![Naam en beschrijving van gegevensstroom](../assets/datastream-name-description.png)

## Service toevoegen aan gegevensstroom

In het volgende scherm kunt u toevoegen welke Adobe-producten en -services de gegevens moeten ontvangen die u van uw website verzendt.

1. Selecteer **[!UICONTROL Service toevoegen]** gebruiken. Schakel in deze zelfstudie alleen Adobe Experience Platform in en selecteer [de dataset u eerder creeerde](create-a-dataset.md) en selecteert u **[!UICONTROL Opslaan]** in de rechterbovenhoek. Uw gegevensstroom is gemaakt.
   ![Productconfiguratie DataStream](../assets/datastream-product-configuration.png)

## DataStream-omgevingen

Bedrijven hebben doorgaans een promotiepad voor updates van websites. Iemand bij het bedrijf (een marketeer of ingenieur, afhankelijk van de veranderingen) test typisch hun veranderingen in een ontwikkelomgeving die slechts die persoon gebruikt. Zodra ze zich vertrouwd voelen met de veranderingen, worden de veranderingen bevorderd tot een het opvoeren milieu waar zij verdere tests ontvangen. Tot slot worden de wijzigingen gepubliceerd naar de productiewebsite die gebruikers zien. Dit promotiepatroon wordt ondersteund door gegevensstromen.

Als u op Platform-gebaseerde toepassingen zoals in real time CDP, Journey Optimizer, of Customer Journey Analytics steunt, moeten de extra gegevensstromen in de afzonderlijke zandbakken van het Platform worden gecreeerd die aan deze milieu&#39;s beantwoorden.

Als u geen klant van het Platform bent, kunt u veelvoudige gegevensstromen in één enkele zandbak tot stand brengen en de eigenschap van de gegevensstroomkopie gebruiken om montages te dupliceren.

De server is nu volledig geconfigureerd voor het ontvangen van gegevens van uw webpagina.

[Volgende: ](../configure-the-client/whats-a-data-layer.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

---
title: Het kader voor gegevensbeheer toepassen
seo-title: Apply the data governance framework | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Het kader voor gegevensbeheer toepassen
description: In deze les, zult u het kader van het gegevensbeheer op de gegevens toepassen u in uw zandbak hebt opgenomen.
role: Data Architect
feature: Data Governance
kt: 4348
thumbnail: 4348-apply-data-governance-framework.jpg
exl-id: 3cc3c794-5ffd-41bf-95d8-be5bca2e3a0f
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 1%

---

# Het kader voor gegevensbeheer toepassen

<!--15min-->

In deze les, zult u het kader van het gegevensbeheer op de gegevens toepassen u in uw zandbak hebt opgenomen.

Met Adobe Experience Platform Data Governance kunt u klantgegevens beheren en ervoor zorgen dat de regels, beperkingen en beleidsregels die van toepassing zijn op gegevensgebruik worden nageleefd. Het speelt een sleutelrol binnen Experience Platform op diverse niveaus, met inbegrip van het controleren van het gebruik van gegevens.

Bekijk voordat u de oefeningen start de volgende korte video&#39;s over gegevensbeheer:
>[!VIDEO](https://video.tv.adobe.com/v/36653?quality=12&learn=on)

>[!VIDEO](https://video.tv.adobe.com/v/29708?quality=12&learn=on)

<!--
## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson, specifically:

* Permission items **[!UICONTROL Data Governance]** > **[!UICONTROL Manage Usage Labels]**, **[!UICONTROL Manage Data Usage Policies]** and **[!UICONTROL View Data Usage Policies]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` Product Profile
-->

## Bedrijfscenario

Luma doet een belofte aan leden van hun Loyalty-programma, dat Loyalty-gegevens niet met derden zullen worden gedeeld. Wij zullen dit scenario in de rest van de les uitvoeren.

## Labels voor gegevensbeheer toepassen

De eerste stap in het gegevensbeheerproces is het toepassen van governancelabels op uw gegevens. Voordat we dat doen, moeten we even kijken naar de labels die beschikbaar zijn:

1. Selecteer in de gebruikersinterface van het Platform de optie **[!UICONTROL Beleid]** in de linkernavigatie
1. Ga naar de **[!UICONTROL Labels]** om alle labels in de account weer te geven.

Er zijn veel out-of-the-box-labels en bovendien kunt u uw eigen labels maken via de [!UICONTROL Label maken] knop. Er zijn drie hoofdtypen: [!UICONTROL Contractlabels], [!UICONTROL Identiteitslabels], en [!UICONTROL Gevoelige labels] die overeenkomen met gemeenschappelijke redenen kunnen gegevens beperkt zijn . Elk label heeft een [!UICONTROL Vriendschappelijke naam] en een korte [!UICONTROL Naam] Dit is slechts een afkorting van het type en een getal. De [!DNL C1] Het label is voor &quot;Geen export van derden&quot;, wat we nodig hebben voor ons Loyalty-beleid.

![Label voor gegevensbeheer](assets/governance-policies.png)

Nu is het tijd om de gegevens te etiketteren waarvan gebruik wij willen beperken:

1. Selecteer in de gebruikersinterface van het Platform de optie **[!UICONTROL Gegevenssets]** in de linkernavigatie
1. Open de `Luma Loyalty Dataset`
1. Ga naar de **[!UICONTROL Gegevensbeheer]** tab
1. U kunt labels toepassen op afzonderlijke velden of deze toepassen op de gehele gegevensset. Wij zullen het etiket op de volledige dataset toepassen. Klik op het potloodpictogram. Als u het pictogram niet ziet, probeert u uw browser breder te maken of het middelste deelvenster naar rechts te schuiven.
   ![Data Governance](assets/governance-dataset.png)
1. Vouw in het modale **[!UICONTROL Labels verkleinen]** en de **[!UICONTROL C2]** label
1. Selecteer **[!UICONTROL Wijzigingen opslaan]** knop
   ![Data Governance](assets/governance-applyLabel.png)
1. Terugkeren naar hoofdmap [!UICONTROL Gegevensbeheer] scherm, met de **[!UICONTROL Overerfde labels tonen]** schakelt, kunt u zien hoe het etiket op alle gebieden in de dataset is toegepast.
   ![Data Governance](assets/governance-labelsAdded.png)


<!--adding extra, unnecessary fields from field groups makes it harder to see which fields really need labels-->
<!--Are there any best practices for applying governance labels-->

## Beleid voor gegevensbeheer maken

Nu onze gegevens gelabeld zijn, kunnen we een beleid maken.

1. Selecteer in de gebruikersinterface van het Platform de optie **[!UICONTROL Beleid]** in de linkernavigatie
1. Op het Browse lusje, is er reeds een uit-van-de-doos beleid genoemd &quot;de uitvoerbeperking van de derde partij&quot;die het C2 etiket met de marketing actie associeert [!UICONTROL Exporteren naar derde partij]—precies wat we nodig hebben!
1. Selecteer het beleid en schakel het vervolgens in via het dialoogvenster **[!UICONTROL Beleidstatus]** schakelen
   ![Data Governance](assets/governance-enablePolicy.png)

U kunt uw eigen beleid maken door de **[!UICONTROL Beleid maken]** knop. Hierdoor wordt een wizard geopend waarmee u meerdere labels en beperkingen voor marketingacties kunt combineren.

## Beleid inzake governance afdwingen

Handhaving van het governancebeleid is duidelijk een essentieel onderdeel van het kader. De handhaving gebeurt stroomafwaarts wanneer gegevens worden geactiveerd en uit Platform worden verzonden, met name met de Real-time Customer Data Platform, die u al dan niet in licentie geeft. Hoe dan ook, het valt buiten het bereik van deze zelfstudie. Maar dus je blijft niet hangen, je kunt meer leren over hoe beleid wordt afgedwongen in deze video, die ik in de rij heb gezet voor het relevante gedeelte. Het zal u ook tonen wat gebeurt wanneer een beleid wordt geschonden.

>[!VIDEO](https://video.tv.adobe.com/v/33631/?t=151&quality=12&learn=on)


## Aanvullende bronnen

* [Documentatie gegevensbeheer](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html)
* [Referentie voor DataSet Service API](https://www.adobe.io/experience-platform-apis/references/dataset-service/)
* [API-naslaggids voor beheerbeleid](https://www.adobe.io/experience-platform-apis/references/policy-service/)

Laten we nu verdergaan [queryservice](run-queries.md).

---
title: De extensie Web SDK toevoegen en configureren
description: Leer om de uitbreiding van SDK van het Web aan uw bezit van Markeringen toe te voegen en te vormen, om u de functionaliteit te geven u in verdere lessen nodig hebt om de migratie te voltooien.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16758
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# De extensie Web SDK toevoegen en configureren

Leer om de uitbreiding van SDK van het Web in uw bezit van Markeringen toe te voegen en te vormen, om u de functionaliteit te geven u in verdere lessen nodig hebt om de migratie te voltooien.
Voer de volgende stappen uit om de extensie toe te voegen en te configureren:

1. Navigeer naar de gegevensverzameling van het Experience Platform. Dit kan op twee manieren worden verwezenlijkt:
   1. Ga naar de [ interface van Adobe Experience Platform ](https://platform.adobe.com/), dan uitgezocht **[!UICONTROL Tags]** dichtbij de bodem van de linkernavigatie.

      ![ Tags 1 van de Toegang ](assets/access-tags-1.jpg)
   1. Als u geen toegang tot Platform hebt, kunt u de toepassingsschakelaar (9 punten) bij het hoogste recht van het venster gebruiken en de Inzameling van Gegevens selecteren (na het hebben het programma geopend in Experience.Adobe.com).

      ![ Tags 2 van de Toegang ](assets/access-tags-2.jpg)
1. Zoek en selecteer de eigenschap tag die u naar de Web SDK migreert.
1. Selecteer **[!UICONTROL Extensions]** in de linkernavigatie van de eigenschap tag.
1. Selecteer **[!UICONTROL Catalog]** boven in het scherm om een lijst met alle beschikbare extensies weer te geven.
1. Zoek en selecteer de extensie **[!UICONTROL Adobe Experience Platform Web SDK]** en klik vervolgens op **[!UICONTROL Install]** aan de rechterkant.

   ![ vind de Uitbreiding van SDK van het Web ](assets/find-the-websdk-extension.jpg){style="border:1px solid lightslategray"}

1. De instellingen voor de extensieconfiguratie worden weergegeven. Zoek de sectie DataStreams en stel de sandbox Experience Platform in die u voor deze migratie wilt gebruiken (vervolgkeuzelijst Omgeving voor alle drie omgevingen). Als u slechts Adobe Analytics migreert en geen gegevens naar Adobe Experience Platform zult verzenden, kies de **zandbak van de Productie**. Als u deze gedragsanalysegegevens naar het Experience Platform wilt verzenden voor gebruik in de toepassingen daar, kiest u de sandbox die u daarvoor wilt gebruiken. U zult waarschijnlijk eerst een ontwikkelingszandbak willen selecteren tot u met migratie wordt gedaan en klaar bent toevoegend/testend uw dienst van het Platform.
1. Heel belangrijk, verbind uw code en montages hier in Markeringen met de Edge door de gegevensstromen te selecteren die u in de vorige stap voor de milieu&#39;s van de Productie, het Staging, en van de Ontwikkeling creeerde.

   ![ selectie DataStream ](assets/choose-datastreams.jpg){style="border:1px solid lightslategray"}

1. De rol neer en merkt op dat de **montages van de Identiteit** door gebrek worden geselecteerd. Laat deze selectievakjes ingeschakeld, omdat deze helpen uw sitebezoekers op de juiste wijze te identificeren wanneer u naar de SDK van het Web migreert. Meer informatie is beschikbaar in de documentatie, die hieronder aan wordt gekoppeld.

1. Selecteer **[!UICONTROL Save]**.

>[!NOTE]
>
>Uw bezit van Markeringen heeft nu een basisinstallatie en configuratie van de uitbreiding van SDK van het Web. Wij zullen delen van de uitbreiding van SDK van het Web gebruiken aangezien wij gegevenselementen en regels tijdens dit migratieleerprogramma creëren of wijzigen, maar wij zullen niet meer van de punten van de uitbreidingsconfiguratie in het leerprogramma veranderen. Extra configuratiepunten kunnen en moeten voor extra gebruiksgevallen worden gebruikt. Voor gedetailleerde documentatie betreffende deze configuraties, zie [ de de markeringsuitbreiding van SDK van het Web ](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/web-sdk-extension-configuration) vormen.

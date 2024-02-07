---
title: Valideer de implementaties van SDK van het Web met de Verzekering van het Experience Platform
description: Leer hoe u uw Platform Web SDK-implementatie met Adobe Experience Platform Assurance kunt valideren. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Assurance
source-git-commit: 4361d8e688ff2c2f3b5472f2cfff246efa627c7f
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Valideer de implementaties van SDK van het Web met de Verzekering van het Experience Platform


## Een betrouwbaarheidssessie starten

Adobe Experience Platform Assurance is een product van Adobe Experience Cloud dat u helpt bij het inspecteren, testen, simuleren en valideren van de manier waarop u gegevens verzamelt of ervaringen opdoet.

Meer informatie over [Adobe Assurance](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=en).

Telkens wanneer u Edge Trace inschakelt, wordt een Assurance-sessie gestart op de achtergrond.

U kunt als volgt de betrouwbaarheidssessie weergeven:

1. Als Edge Trace is ingeschakeld, ziet u bovenaan een pictogram voor uitgaande koppelingen. Selecteer het pictogram om Verzekering te openen. Er wordt een nieuw tabblad in de browser geopend.

   ![Beginnen met betrouwbaarheidssessie](assets/validate-debugger-start-assurnance.png)

1. Selecteer de rij met de gebeurtenis genoemd de Handgreep van de Reactie van de Adobe.
1. Rechts wordt een menu weergegeven. Selecteer de `+` ondertekenen naast `[!UICONTROL ACPExtensionEvent]`
1. Omlaag boven door `[!UICONTROL payload > 0 > payload > 0 > namespace]`. De id die wordt weergegeven onder de laatste `0` komt overeen met de `ECID`. U weet dat met de waarde die onder verschijnt `namespace` overeenkomst `ECID`

   ![Betrouwbaarheid valideren ECID](assets/validate-assurance-ecid.png)

   >[!CAUTION]
   >
   >Mogelijk wordt een ingekorte ECID-waarde weergegeven vanwege de breedte van het venster. Selecteer gewoon de greep in de interface en sleep naar links om de volledige ECID weer te geven.

In toekomstige lessen, gebruikt u Verzekering om volledig verwerkte nuttige lasten te bevestigen die een Adobe toepassing bereiken die in uw gegevensstroom wordt toegelaten.

Met een voorwerp XDM dat nu op een pagina, en met de kennis van hoe te om uw gegevensinzameling te bevestigen vuurt, bent u klaar aan opstelling de individuele toepassingen van de Adobe gebruikend het Web SDK van het Platform.
---
title: Valideer de implementaties van SDK van het Web met de Verzekering van het Experience Platform
description: Leer hoe u uw Platform Web SDK-implementatie met Adobe Experience Platform Assurance kunt valideren. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Assurance
jira: KT-15406
exl-id: 31e381ea-fbaf-495f-a6e9-2ff6c0d36939
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Valideer de implementaties van SDK van het Web met de Verzekering van het Experience Platform

Adobe Experience Platform Assurance is een functie waarmee u kunt controleren, testen, simuleren en valideren hoe u gegevens verzamelt of ervaringen opdoet. Lees meer over [ Verzekering van de Adobe ](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home).


## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een betrouwbaarheidssessie starten
* Verzoeken weergeven die van en naar de Edge Network Platform worden verzonden

## Vereisten

U bent vertrouwd met de markeringen van de Inzameling van Gegevens en de [ plaats van de de demo van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) {target="_blank"} en hebt de vorige lessen in het leerprogramma voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)
* [Een labelregel maken](create-tag-rule.md)
* [Valideren met foutopsporing](validate-with-debugger.md)


## Een betrouwbaarheidssessie starten en weergeven

Er zijn verschillende manieren om een betrouwbaarheidssessie te starten.

### Een betrouwbaarheidssessie starten in Foutopsporing

Telkens wanneer u Edge Trace in Adobe Experience Platform Debugger inschakelt, wordt een Assurance-sessie gestart op de achtergrond.

In de les Foutopsporing bekijken hoe we dit deden:

1. Ga naar de [ plaats van de de demo van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) en gebruik debugger om [ het markeringsbezit op de plaats aan uw eigen ontwikkelingeigenschap ](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property) te schakelen
1. In de linkernavigatie van **[!UICONTROL Experience Platform Debugger]** select **[!UICONTROL Logs]**
1. Selecteer de tab **[!UICONTROL Edge]** en selecteer **[!UICONTROL Connect]**

   ![ verbindt het Spoor van Edge ](assets/analytics-debugger-edgeTrace.png)
1. Als Edge Trace is ingeschakeld, ziet u bovenaan een uitgaande koppelingspictogram. Selecteer het pictogram om Verzekering te openen.

   ![ de zitting van de Verzekering van het Begin ](assets/validate-debugger-start-assurnance.png)

1. Er wordt een nieuw browsertabblad geopend met de interface voor Betrouwbaarheid.

### Een Assurance-sessie starten vanuit de interface voor Betrouwbaarheid

1. Open de [ interface van de Inzameling van Gegevens ](https://experience.adobe.com/#/data-collection/home) {target="_blank"}
1. Selecteer Betrouwbaarheid in de linkernavigatie
1. Sessie maken selecteren
   ![ creeer een zitting van de Verzekering ](assets/assurance-create-session.png)
1. Begin selecteren
1. Geef de sessie een naam, bijvoorbeeld `Luma Web SDK validation`
1. Als **[!UICONTROL Base URL]** enter `https://luma.enablementadobe.com/`
   ![ Naam de zitting van de Verzekering ](assets/assurance-name-session.png)
1. Selecteer **[!UICONTROL Copy Link]** in het volgende scherm
1. Selecteer het pictogram om de koppeling naar het klembord te kopiëren
1. Plak de URL in uw browser, die de Luma-website opent met een speciale URL-parameter `adb_validation_sessionid` en de sessie start
1. In de interface van de Verzekering, zou u een bericht moeten zien erop wijzen dat u met succes met de zitting hebt verbonden en u zou gebeurtenissen moeten zien die in de interface van de Verzekering worden gevangen.
   ![ de zitting van de Verzekering heeft verbonden ](assets/assurance-success.png)

## Valideer de huidige staat van uw implementatie van SDK van het Web

Er is beperkte informatie om in deze fase van uw implementatie te bekijken. Één waarde wij kunnen zien is uw Experience Cloud identiteitskaart (ECID) die op de Edge Network van het Platform wordt geproduceerd:

1. Selecteer de rij met de gebeurtenis `Alloy Response Handle` .
1. Rechts wordt een menu weergegeven. Selecteer het `+` -teken naast `[!UICONTROL ACPExtensionEventData]`
1. Selecteer `[!UICONTROL payload > 0 > payload > 0 > namespace]` om omlaag te gaan. De id die onder de laatste `0` wordt weergegeven, komt overeen met de `ECID` . U weet dat aan de hand van de waarde die wordt weergegeven onder `namespace` Overeenkomende `ECID`

   ![ de Verzekering bevestigt ECID ](assets/validate-assurance-ecid.png)

   >[!CAUTION]
   >
   >Mogelijk wordt een ingekorte ECID-waarde weergegeven vanwege de breedte van het venster. Selecteer gewoon de greep in de interface en sleep naar links om de volledige ECID weer te geven.

In toekomstige lessen, gebruikt u Verzekering om volledig verwerkte nuttige lasten te bevestigen die een Adobe toepassing bereiken die in uw gegevensstroom wordt toegelaten.

Met een voorwerp XDM dat nu op een pagina, en met de kennis van hoe te om uw gegevensinzameling te bevestigen vuurt, bent u klaar aan opstellings Experience Platform en de individuele toepassingen van de Adobe gebruikend het Web SDK van het Platform.

[Volgende: ](setup-experience-platform.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van de Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

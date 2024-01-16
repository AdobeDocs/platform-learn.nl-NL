---
title: Valideer de implementaties van SDK van het Web met Foutopsporing van het Experience Platform
description: Leer hoe te om uw implementatie van SDK van het Web van het Platform met Adobe Experience Platform Debugger te bevestigen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Debugger
source-git-commit: 904581df85df5d8fc4f36a4d47a37b03ef92d76f
workflow-type: tm+mt
source-wordcount: '1465'
ht-degree: 0%

---

# Valideer de implementaties van SDK van het Web met Foutopsporing van het Experience Platform

Leer hoe te om uw implementatie van SDK van het Web van het Platform met Adobe Experience Platform Debugger te bevestigen.

Foutopsporing voor Experience Platforms is een extensie die beschikbaar is voor Chrome- en Firefox-browsers en waarmee u de Adobe-technologie kunt bekijken die in uw webpagina&#39;s is geïmplementeerd. Download de versie voor uw voorkeursbrowser:

* [Firefox-extensie](https://addons.mozilla.org/nl/firefox/addon/adobe-experience-platform-dbg/)
* [Chrome-extensie](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Als u foutopsporing nooit eerder hebt gebruikt—en deze is anders dan de oudere Adobe Experience Cloud Debugger—kunt u deze overzichtsvideo van vijf minuten bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/32156?learn=on)

In deze les gebruikt u de opdracht [Adobe Experience Cloud Debugger-extensie](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) om de eigenschap tag te vervangen die op de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) met uw eigen eigenschap.

Deze techniek wordt omgevingsomschakeling genoemd en is later handig wanneer u met tags op uw eigen website werkt. U kunt uw productiewebsite in uw browser, maar met uw *ontwikkeling* tagomgeving. Hierdoor kunt u op een betrouwbare manier wijzigingen in tags doorvoeren en valideren, onafhankelijk van uw reguliere code-releases. Per slot van rekening is deze scheiding van marketing markeringsversies van uw regelmatige codeversies één van de belangrijkste redenen klanten in de eerste plaats labels gebruiken!

## Leerdoelstellingen

Aan het eind van deze les, zult u debugger kunnen gebruiken om:

* Een alternatieve tagbibliotheek laden
* Valideer de client-side XDM-gebeurtenis vangt gegevens op en verzendt deze naar verwachting naar Platform Edge Network
* Edge Trace inschakelen om verzoeken aan de serverzijde te bekijken die door Platform Edge Network worden verzonden
* Een Adobe Experience Platform Assurance-sessie starten om een Experience Cloud-id weer te geven die is gegenereerd door Platform Edge Network

## Vereisten

U bent vertrouwd met de tags voor gegevensverzameling en de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} en hebben in de zelfstudie de volgende lessen getrokken:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)
* [Een labelregel maken](create-tag-rule.md)

## Alternatieve tagbibliotheken laden met Foutopsporing

Deze zelfstudie gebruikt een openbaar gehoste versie van het dialoogvenster [Luma-demo-website](https://luma.enablementadobe.com/content/luma/us/en.html). Open de startpagina en bladwijzer.

![Luminantiepage](assets/validate-luma-site.png)

Foutopsporing op Experience Platform heeft een coole functie waarmee u een bestaande tagbibliotheek kunt vervangen door een andere. Deze techniek is nuttig voor bevestiging en staat ons toe om vele implementatiestappen in dit leerprogramma over te slaan.

1. Zorg ervoor dat de Luminasite is geopend en selecteer het extensiepictogram Experience Platform debugger
1. Foutopsporing opent en toont sommige details van de hard-gecodeerde implementatie, die met dit leerprogramma niet verwant is (u kunt de plaats van de Luma na het openen van Debugger moeten opnieuw laden)
1. Controleer of Foutopsporing &quot;**[!UICONTROL Verbonden met luminantie]**&quot; zoals hieronder wordt weergegeven en selecteer vervolgens &quot;**[!UICONTROL vergrendelen]**&quot; pictogram om Foutopsporing te vergrendelen op de Luministensite.
1. Selecteer de **[!UICONTROL Aanmelden]** en meld je aan bij Adobe Experience Cloud met je Adobe-id.
1. Ga nu naar **[!UICONTROL Experience Platform-tags]** in de linkernavigatie

   ![Tagscherm Foutopsporing](assets/validate-launch-screen.png)

1. Selecteer de **[!UICONTROL Configuratie]** tab
1. Rechts van waar het u toont **[!UICONTROL Pagina-insluitcodes]**, opent u de **[!UICONTROL Handelingen]** vervolgkeuzelijst en selecteer **[!UICONTROL Vervangen]**

   ![Handelingen selecteren > Vervangen](assets/validate-switch-environment.png)

1. Aangezien u voor authentiek wordt verklaard, zal Foutopsporing uw beschikbare markeringseigenschappen en milieu&#39;s trekken. Selecteer de eigenschap; in dit geval `Web SDK Course 3`
1. Selecteer uw `Development` milieu
1. Selecteer de **[!UICONTROL Toepassen]** knop

   ![De eigenschap Alternatieve tag selecteren](assets/validate-switch-selection.png)

1. De Luma-website wordt nu opnieuw geladen _met uw eigen tag-eigenschap_.

   ![tag, eigenschap is vervangen](assets/validate-switch-success.png)

Aangezien u het leerprogramma voortzet, gebruikt u deze techniek om de plaats van de Luma aan uw eigen markeringsbezit in kaart te brengen om uw implementatie van SDK van het Web van het Platform te bevestigen. Wanneer u labels gaat gebruiken op uw productiewebsite, kunt u met dezelfde techniek wijzigingen valideren.

## Valideer client-side netwerkverzoeken met Foutopsporing van Experience Platform

U kunt Debugger gebruiken om cliënt-zijbakens te bevestigen die van uw implementatie van SDK van het Web van het Platform worden teweeggebracht om de gegevens te bekijken die naar het Netwerk van de Rand van het Platform worden verzonden:

1. Ga naar **[!UICONTROL Samenvatting]** in de linkernavigatie, om de details van uw markeringsbezit te zien

   ![Tabblad Samenvatting](assets/validate-summary.png)

1. Ga nu naar **[!UICONTROL Experience Platform Web SDK]** in de linkernavigatie om de **[!UICONTROL Netwerkverzoeken]**
1. Open de **[!UICONTROL gebeurtenissen]** rij

   ![Adobe Experience Platform Web SDK-verzoek](assets/validate-aep-screen.png)

1. Let op hoe u de `web.webpagedetails.pageView` gebeurtenistype dat u in uw [!UICONTROL Variabele bijwerken] handeling en andere variabelen die zich aan de `AEP Web SDK ExperienceEvent` veldgroep

   ![Gebeurtenisdetails](assets/validate-event-pageViews.png)

1. Omlaag schuiven naar de `web` -object, selecteert u deze om het te openen en inspecteert het `webPageDetails.name`, `webPageDetails.server`, en `webPageDetails.siteSection`. Deze moeten overeenkomen met de overeenkomstige `digitalData` gegevenslaagvariabelen op de startpagina

>[!TIP]
>
> Als u de `digitalData` gegevenslaag op de startpagina:
>
> 1. Open de browsergereedschappen voor ontwikkelaars op de startpagina van Luma. In het geval van Chrome selecteert u de knop `F12` op uw toetsenbord
> 1. Selecteer de **[!UICONTROL Console]** tab
> 1. Enter `digitalData` en selecteert u `Enter` op uw toetsenbord om de waarden van de gegevenslaag te verhogen

![Het tabblad Netwerk](assets/validate-xdm-content.png)

U kunt ook de identiteitskaartgegevens valideren:

1. Meld u aan bij de Luministensite met de referenties `test@adobe.com`/`test`

1. Terugkeren naar de [Luminantiepage](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Open de **[!UICONTROL Experience Platform Web SDK]** sectie in de linkernavigatie

   ![Web SDK in Foutopsporing](assets/identity-debugger-websdk-dark.png)

1. Selecteer de **[!UICONTROL gebeurtenissen]** rij voor het openen van details in een pop-up

   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-dark.png)

1. Zoeken naar **identityMap** in het pop-upvenster. Hier ziet u `lumaCrmId` met drie sleutels van authenticatedState, id, en primair:
   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)

### Clientverzoeken valideren met de hulpprogramma&#39;s voor het ontwikkelen van browsers

Deze typen aanvraagdetails zijn ook zichtbaar in de webontwikkelaarsgereedschappen van de browser **Netwerk** tabblad (ervan uitgaande dat de website uw tagbibliotheek laadt).

1. De webontwikkelaarsgereedschappen van de browser openen **Netwerk** en laadt de pagina opnieuw. Filter voor aanroepen met `/ee` om van de vraag de plaats te bepalen, het te selecteren, en dan in te kijken **Kopteksten** en **Payload** tab

   ![Het tabblad Netwerk](assets/validate-dev-console.png)

1. Ga naar de **Antwoord** en noteer hoe de ECID-waarde wordt opgenomen in het antwoord. Deze waarde kopiëren zoals u deze gebruikt om de profielgegevens in de volgende exercitie te valideren

   ![Het tabblad Netwerk](assets/validate-dev-console-ecid.png)


## Valideer server-zijnetwerkverzoeken met Foutopsporing van het Experience Platform

Zoals u in [Een gegevensstroom configureren](configure-datastream.md) les, het Web SDK van het Platform verzendt eerst gegevens van uw digitaal bezit naar het Netwerk van de Rand van het Platform. Dan, doet het Netwerk van de Rand van het Platform extra server-zijverzoeken aan de overeenkomstige diensten die in uw datastream worden toegelaten.

U kunt verzoeken aan de serverzijde valideren door Edge Trace in te schakelen in Foutopsporing. Bovendien kunt u de volledig verwerkte lading ook bevestigen nadat het een toepassing van de Adobe door te gebruiken bereikt [Adobe Experience Platform Assurance](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=en).

In de volgende twee oefeningen, laat u het Spoor van de Rand toe en bekijkt identiteitskaart van het Experience Cloud die van het Netwerk van de Rand van het Platform door Verzekering wordt geproduceerd te gebruiken.

### Randovertrekken inschakelen

Het Edge-overtrekken inschakelen

1. In de linkernavigatie van **[!UICONTROL Foutopsporing Experience Platform]** selecteren **[!UICONTROL Logboeken]**
1. Selecteer de **[!UICONTROL Rand]** en selecteert u **[!UICONTROL Verbinden]**

   ![Edge-overtrekken aansluiten](assets/analytics-debugger-edgeTrace.png)

1. Het is nu leeg

   ![Verbonden randspoor](assets/analytics-debugger-edge-connected.png)

1. Vernieuw de [Luminagestartpagina](https://luma.enablementadobe.com/) en controle **[!UICONTROL Foutopsporing Experience Platform]** om de data weer te zien komen.

   ![Analysebaken Edge Trace](assets/validate-edge-trace.png)

Op dit punt, kunt u geen verzoeken van het Netwerk van de Rand van het Platform bekijken die naar een toepassing van de Adobe gaan omdat u geen om het even welk in de gegevensstroom hebt toegelaten. In toekomstige lessen, gebruikt u het Spoor van de Rand om de uitgaande server-zijverzoeken aan de toepassingen van de Adobe te bekijken. Nochtans, gebruikend Verzekering kunt u nog bekijken identiteitskaart van het Experience Cloud door het Netwerk van de Rand van het Platform wordt geproduceerd.

### Een betrouwbaarheidssessie starten

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

[Volgende: ](setup-experience-platform.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
---
title: Valideer de implementaties van SDK van het Web met Foutopsporing van het Experience Platform
description: Leer hoe te om uw implementatie van SDK van het Web van het Platform met Adobe Experience Platform Debugger te bevestigen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Debugger
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
source-git-commit: 100a6a9ac8d580b68beb7811f99abcdc0ddefd1a
workflow-type: tm+mt
source-wordcount: '1165'
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
* Valideer de client-side XDM-gebeurtenis vangt gegevens op en verzendt deze naar de Edge Network Platform
* Laat het Spoor van de Rand toe om server-zijverzoeken te bekijken die door de Edge Network van het Platform worden verzonden

## Vereisten

U bent vertrouwd met de tags voor gegevensverzameling en de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} en hebben de vorige lessen in de zelfstudie voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)
* [Tagregels maken](create-tag-rule.md)

## Alternatieve tagbibliotheken laden met Foutopsporing

Foutopsporing op Experience Platform heeft een coole functie waarmee u een bestaande tagbibliotheek kunt vervangen door een andere. Deze techniek is nuttig voor bevestiging en staat ons toe om vele implementatiestappen in dit leerprogramma over te slaan.

1. Zorg ervoor dat u de [Luma-demo-website](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} Het extensiepictogram Foutopsporing Experience Platform openen en selecteren
1. Foutopsporing opent en toont sommige details van de hard-gecodeerde implementatie (u kunt de plaats van de Luma na het openen van Debugger moeten opnieuw laden)
1. Controleer of Foutopsporing &quot;**[!UICONTROL Connected to Luma]**&quot; zoals hieronder wordt weergegeven en selecteer vervolgens &quot;**[!UICONTROL lock]**&quot; pictogram om Foutopsporing te vergrendelen op de Luministensite.
1. Selecteer de **[!UICONTROL Sign In]** en meld je aan bij Adobe Experience Cloud met je Adobe-id.
1. Ga nu naar **[!UICONTROL Experience Platform Tags]** in de linkernavigatie

   ![Tagscherm Foutopsporing](assets/validate-launch-screen.png)

1. Selecteer de **[!UICONTROL Configuration]** tab
1. Rechts van waar het u toont **[!UICONTROL Page Embed Codes]**, opent u de **[!UICONTROL Actions]** vervolgkeuzelijst en selecteer **[!UICONTROL Replace]**

   ![Handelingen selecteren > Vervangen](assets/validate-switch-environment.png)

1. Aangezien u voor authentiek wordt verklaard, zal Foutopsporing uw beschikbare markeringseigenschappen en milieu&#39;s trekken. Selecteer de eigenschap; in dit geval `Web SDK Course 3`
1. Selecteer uw `Development` milieu
1. Selecteer de **[!UICONTROL Apply]** knop

   ![De eigenschap Alternatieve tag selecteren](assets/validate-switch-selection.png)

1. De Luma-website wordt nu opnieuw geladen _met uw eigen tag-eigenschap_.

   ![tag, eigenschap is vervangen](assets/validate-switch-success.png)

Aangezien u het leerprogramma voortzet, gebruikt u deze techniek om de plaats van de Luma aan uw eigen markeringsbezit in kaart te brengen om uw implementatie van SDK van het Web van het Platform te bevestigen. Wanneer u labels gaat gebruiken op uw productiewebsite, kunt u met deze techniek wijzigingen valideren terwijl u deze aanbrengt in de ontwikkelomgeving van labels.

## Valideer client-side netwerkverzoeken met Foutopsporing van Experience Platform

U kunt Debugger gebruiken om cliënt-zijbakens te bevestigen die van uw implementatie van SDK van het Web van het Platform worden teweeggebracht om de gegevens te bekijken die naar de Edge Network van het Platform worden verzonden:

1. Ga naar **[!UICONTROL Summary]** in de linkernavigatie, om de details van uw markeringsbezit te zien

   ![Tabblad Samenvatting](assets/validate-summary.png)

1. Ga nu naar **[!UICONTROL Experience Platform Web SDK]** in de linkernavigatie om de **[!UICONTROL Network Requests]**
1. Open de **[!UICONTROL events]** rij

   ![Adobe Experience Platform Web SDK-verzoek](assets/validate-aep-screen.png)

1. Let op hoe u de `web.webpagedetails.pageView` gebeurtenistype dat u in uw [!UICONTROL Update variable] handeling en andere variabelen die zich aan de `AEP Web SDK ExperienceEvent` veldgroep

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

1. Selecteer de **[!UICONTROL events]** rij voor het openen van details in een pop-up

   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-dark.png)

1. Zoeken naar **identityMap** in het pop-upvenster. Hier ziet u `lumaCrmId` met drie sleutels van authenticatedState, id, en primair:
   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)

### Clientverzoeken valideren met de hulpprogramma&#39;s voor het ontwikkelen van browsers

Deze typen aanvraagdetails zijn ook zichtbaar in de webontwikkelaarsgereedschappen van de browser **Netwerk** tabblad (ervan uitgaande dat de website uw tagbibliotheek laadt).

1. De webontwikkelaarsgereedschappen van de browser openen **Netwerk** en laadt de pagina opnieuw. Filter voor aanroepen met `/ee` om van de vraag de plaats te bepalen, het te selecteren, en dan in te kijken **Kopteksten** en **Payload** tab

   ![Het tabblad Netwerk](assets/validate-dev-console.png)

1. Ga naar de **Antwoord** en noteer hoe de ECID-waarde wordt opgenomen in het antwoord. Deze waarde kopiëren zoals u deze gebruikt om de profielgegevens in de volgende exercitie te valideren

   ![Het tabblad Netwerk](assets/validate-dev-console-ecid.png)

   >[!NOTE]
   >
   > De waarde ECID is zichtbaar in de netwerkreactie. Het is niet opgenomen in de `identityMap` deel van het netwerkverzoek, noch wordt het opgeslagen in dit formaat in een koekje.

## Valideer server-zijnetwerkverzoeken met Foutopsporing van het Experience Platform

Zoals u in [Een gegevensstroom configureren](configure-datastream.md) les, het Web SDK van het Platform verzendt eerst gegevens van uw digitaal bezit naar de Edge Network van het Platform. Dan, maakt de Edge Network van het Platform extra server-zijverzoeken aan de overeenkomstige diensten die in uw datastream worden toegelaten. U kunt de server-zijverzoeken bevestigen die door het Netwerk van de Rand van het Platform door het Spoor van de Rand in Debugger worden gemaakt te gebruiken.

<!--Furthermore, you can also validate the fully processed payload after it reaches an Adobe application by using [Adobe Experience Platform Assurance](https://experienceleague.adobe.com/docs/experience-platform/assurance/home.html?lang=en). -->


### Randovertrekken inschakelen

U schakelt Edge Trace als volgt in:

1. In de linkernavigatie van **[!UICONTROL Experience Platform Debugger]** selecteren **[!UICONTROL Logs]**
1. Selecteer de **[!UICONTROL Edge]** en selecteert u **[!UICONTROL Connect]**

   ![Edge-overtrekken aansluiten](assets/analytics-debugger-edgeTrace.png)

1. Het is nu leeg

   ![Verbonden randspoor](assets/analytics-debugger-edge-connected.png)

1. Vernieuw de [Luminagestartpagina](https://luma.enablementadobe.com/) en controle **[!UICONTROL Experience Platform Debugger]** om de data weer te zien komen.

   ![Analysebaken Edge Trace](assets/validate-edge-trace.png)

Op dit punt, kunt u geen verzoeken bekijken van de Edge Network van het Platform die naar een toepassingen van de Adobe gaan omdat u geen om het even welk in de datastream hebt toegelaten. In toekomstige lessen, gebruikt u het Spoor van de Rand om de uitgaande server-zijverzoeken aan de toepassingen van de Adobe en gebeurtenis te bekijken door:sturen. Maar eerst, leer over een ander hulpmiddel om server-zijverzoeken te bevestigen die door Platform Edge Network-Adobe Experience Platform Assurance worden gemaakt!

[Volgende: ](validate-with-assurance.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

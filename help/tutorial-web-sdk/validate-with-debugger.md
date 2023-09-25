---
title: Valideer de implementaties van SDK van het Web met Foutopsporing van het Experience Platform
description: Leer hoe te om uw implementatie van SDK van het Web van het Platform met Adobe Experience Platform Debugger te bevestigen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Debugger
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 1%

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
* Bevestig het voorwerp XDM vangt en verzendt gegevens zoals verwacht het Netwerk van de Rand

## Vereisten

U bent vertrouwd met de tags voor gegevensverzameling en de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} en hebben in de zelfstudie de volgende lessen getrokken:

* [Machtigingen configureren](configure-permissions.md)
* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
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

1. Aangezien u voor authentiek wordt verklaard, zal Foutopsporing uw beschikbare markeringseigenschappen en milieu&#39;s trekken. Selecteer uw `Web SDK Course` eigenschap
1. Selecteer uw `Development` milieu
1. Selecteer de **[!UICONTROL Toepassen]** knop

   ![De eigenschap Alternatieve tag selecteren](assets/validate-switch-selection.png)

1. De Luma-website wordt nu opnieuw geladen _met uw tag-eigenschap_.

   ![tag, eigenschap is vervangen](assets/validate-switch-success.png)

Aangezien u het leerprogramma voortzet, zult u deze techniek gebruiken om de plaats van de Luma aan uw eigen markeringsbezit in kaart te brengen om uw implementatie van SDK van het Web van het Platform te bevestigen. Wanneer u labels gaat gebruiken op uw productiewebsite, kunt u met dezelfde techniek wijzigingen valideren.

## Implementatie valideren in Foutopsporing Experience Platform

U kunt Debugger gebruiken om uw implementatie van SDK van het Web van het Platform te bevestigen en de gegevens te bekijken die naar het Netwerk van de Rand van het Platform worden verzonden:

1. Ga naar **[!UICONTROL Samenvatting]** in de linkernavigatie, om de details van uw markeringsbezit te zien

   ![Tabblad Samenvatting](assets/validate-summary.png)

1. Ga nu naar **[!UICONTROL Experience Platform Web SDK]** in de linkernavigatie om de **[!UICONTROL Netwerkverzoeken]**
1. Open de **[!UICONTROL gebeurtenissen]** rij (maak geen zorgen als dit schermafbeelding meer verzoeken dan van u toont, omvat het verzoeken uit toekomstige lessen en u kunt nu negeren)

   ![Adobe Experience Platform Web SDK-verzoek](assets/validate-aep-screen.png)

1. Let op hoe we de `web.webpagedetails.pageView` gebeurtenistype dat we in onze [!UICONTROL Gebeurtenis verzenden] handeling en andere variabelen die zich aan de `AEP Web SDK ExperienceEvent Mixin` format

   ![Gebeurtenisdetails](assets/validate-event-pageViews.png)

1. Omlaag schuiven naar de `web` -object, selecteert u deze om het te openen en inspecteert het `webPageDetails.name`, `webPageDetails.server`, en `webPageDetails.siteSection`. Ze moeten overeenkomen met de overeenkomstige digitaleData-gegevenslaagvariabelen op de startpagina

   ![Het tabblad Netwerk](assets/validate-xdm-content.png)

U kunt ook de identiteitskaartgegevens valideren:

1. Log in op de Luministensite met de referenties `test@adobe.com`/`test`

1. Terugkeren naar de [Luminantiepage](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Open de **[!UICONTROL Experience Platform Web SDK]** sectie in de linkernavigatie

   ![Web SDK in Foutopsporing](assets/identity-debugger-websdk-dark.png)

1. Selecteer de **[!UICONTROL gebeurtenissen]** rij voor het openen van details in een pop-up

   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-dark.png)

1. Zoeken naar **identityMap** in het pop-upvenster. Hier ziet u `lumaCrmId` met drie sleutels van authenticatedState, id, en primair:
   ![Web SDK in Foutopsporing](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)


## Valideren met ontwikkelgereedschappen voor browsers

Deze typen aanvraagdetails zijn ook zichtbaar in de webontwikkelaarsgereedschappen van de browser **Netwerk** tabblad (ervan uitgaande dat de website uw tagbibliotheek laadt).

1. De webontwikkelaarsgereedschappen van de browser openen **Netwerk** en laadt de pagina opnieuw. Filter voor aanroepen met `/ee` om van de vraag de plaats te bepalen, het te selecteren, en dan in te kijken **Kopteksten** en **Payload** tab

   ![Het tabblad Netwerk](assets/validate-dev-console.png)

1. Ga naar de **Antwoord** en noteer hoe de ECID-waarde wordt opgenomen in het antwoord. Deze waarde kopiëren zoals u deze gebruikt om de profielgegevens in de volgende exercitie te valideren

   ![Het tabblad Netwerk](assets/validate-dev-console-ecid.png)

   >[!NOTE]
   >
   >    U kunt niet de zelfde hoeveelheid ladingsverzoeken zien zoals in het het schermschot hierboven. Deze ongelijkheid komt omdat toekomstige lessen voor [Doel instellen](setup-target.md) zijn voltooid op het moment dat de screenshot wordt gemaakt. U kunt dit verschil nu negeren.

Met een voorwerp XDM dat nu op een pagina, en met de kennis van hoe te om uw gegevensinzameling te bevestigen vuurt, bent u klaar aan opstelling de individuele toepassingen van de Adobe gebruikend het Web SDK van het Platform.

[Volgende: ](setup-experience-platform.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

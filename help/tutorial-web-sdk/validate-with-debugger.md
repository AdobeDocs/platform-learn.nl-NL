---
title: Web SDK-implementaties valideren met Experience Platform Debugger
description: Leer hoe u uw Platform Web SDK-implementatie met Adobe Experience Platform Debugger kunt valideren. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Debugger
jira: KT-15405
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
source-git-commit: d70d5df8b11c8500dbe4764b08e2627893f436f0
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 0%

---

# Web SDK-implementaties valideren met Experience Platform Debugger

Leer hoe u uw Adobe Experience Platform Web SDK-implementatie met Adobe Experience Platform Debugger kunt valideren.

De Experience Platform Debugger is een extensie die beschikbaar is voor Chrome en waarmee u de Adobe-technologie kunt bekijken die in uw webpagina&#39;s is geïmplementeerd:

* [&#x200B; de uitbreiding van Chrome &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Als u debugger nooit eerder hebt gebruikt, zou u deze vijf-minieme overzichtsvideo kunnen willen letten:

>[!VIDEO](https://video.tv.adobe.com/v/32156?learn=on&enablevpops)

In deze les, gebruikt u de [&#x200B; uitbreiding van Adobe Experience Platform Debugger &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) om het markeringsbezit te vervangen dat op de [&#x200B; Luma demo plaats &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html) met uw eigen bezit wordt hard gecodeerd.

Deze techniek wordt omgevingsomschakeling genoemd en is later handig wanneer u met tags op uw eigen website werkt. Het staat u toe om uw productiewebsite in uw browser te laden, maar met uw *ontwikkeling* de tagbibliotheek. Hierdoor kunt u op een betrouwbare manier wijzigingen in tags doorvoeren en valideren, onafhankelijk van uw reguliere code-releases. Per slot van rekening is deze scheiding van marketing markeringsversies van uw regelmatige codeversies één van de belangrijkste redenen klanten in de eerste plaats labels gebruiken!

## Leerdoelstellingen

Aan het eind van deze les, zult u debugger kunnen gebruiken om:

* Een alternatieve tagbibliotheek laden
* Valideren van de client-side XDM-gebeurtenis vangt gegevens op en verzendt deze naar het Platform Edge Network
* Edge Trace inschakelen om verzoeken van Platform Edge Network op de server weer te geven

## Vereisten

U bent vertrouwd met de markeringen van de Inzameling van Gegevens en de [&#x200B; de demomoeplaats van de Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} en hebt de vorige lessen in het leerprogramma voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)
* [Tagregels maken](create-tag-rule.md)

## Alternatieve tagbibliotheken laden met Foutopsporing

De Experience Platform Debugger beschikt over een coole functie waarmee u een bestaande tagbibliotheek kunt vervangen door een andere. Deze techniek is nuttig voor bevestiging en staat ons toe om vele implementatiestappen in dit leerprogramma over te slaan.

1. Zorg ervoor u de [&#x200B; de demowebsite van de Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} open hebt en selecteert het Debugger van Experience Platform uitbreidingspictogram
1. Foutopsporing opent en toont sommige details van de hard-gecodeerde implementatie (u kunt de plaats van de Luma na het openen van Debugger moeten opnieuw laden)
1. Bevestig dat Debugger &quot;**[!UICONTROL Connected to Luma]**&quot;zoals hieronder afgebeeld is en selecteer dan het &quot;**[!UICONTROL lock]**&quot;pictogram is om Debugger aan de plaats van de Luma te sluiten.
1. Selecteer de knop **[!UICONTROL Sign In]** en meld u aan bij Adobe Experience Cloud met uw Adobe-id.
1. Ga nu naar **[!UICONTROL Experience Platform Tags]** in de linkernavigatie

   ![&#x200B; Debugger de markeringsscherm &#x200B;](assets/validate-launch-screen.png)

1. Selecteer de tab **[!UICONTROL Configuration]**
1. Open rechts van waar de **[!UICONTROL Page Embed Codes]** wordt weergegeven het vervolgkeuzemenu **[!UICONTROL Actions]** en selecteer **[!UICONTROL Replace]**

   ![&#x200B; Uitgezochte Acties > vervangen &#x200B;](assets/validate-switch-environment.png)

1. Aangezien u voor authentiek wordt verklaard, zal Foutopsporing uw beschikbare markeringseigenschappen en milieu&#39;s trekken. Selecteer uw eigenschap
1. Selecteer uw `Development` -omgeving
1. Selecteer de knop **[!UICONTROL Apply]**

   ![&#x200B; selecteer het afwisselende markeringsbezit &#x200B;](assets/validate-switch-selection.png)

1. De website van de Luma zal _met uw eigen markeringsbezit_ nu opnieuw laden.

   ![&#x200B; vervangen markeringsbezit &#x200B;](assets/validate-switch-success.png)

Terwijl u de zelfstudie voortzet, gebruikt u deze techniek om de Luministoewijzing toe te wijzen aan uw eigen tageigenschap om de implementatie van Platform Web SDK te valideren. Wanneer u tags op uw eigen website gebruikt, kunt u dezelfde techniek gebruiken om bibliotheken met ontwikkelingslabels op uw productiewebsite te valideren.

## Clientnetwerkaanvragen valideren met Experience Platform Debugger

U kunt Foutopsporing gebruiken om cliënt-zijbakens te bevestigen die van uw implementatie van het Web SDK van het Platform worden teweeggebracht om de gegevens te bekijken die naar Platform Edge Network worden verzonden:

1. Ga naar **[!UICONTROL Summary]** in de linkernavigatie om de details van uw markeringseigenschap te zien

   ![&#x200B; Samenvatting tabel &#x200B;](assets/validate-summary.png)

1. Ga nu naar **[!UICONTROL Experience Platform Web SDK]** in de linkernavigatie om de **[!UICONTROL Network Requests]** te zien
1. De rij **[!UICONTROL events]** openen

   ![&#x200B; SDK van het Web van Adobe Experience Platform verzoek &#x200B;](assets/validate-aep-screen.png)

1. Let op hoe u het gebeurtenistype `web.webpagedetails.pageView` kunt zien dat u in de [!UICONTROL Update variable] -handeling hebt opgegeven, en andere variabelen die zich buiten het vak bevinden en die aan de `AEP Web SDK ExperienceEvent` -veldgroep voldoen.

   ![&#x200B; de details van de Gebeurtenis &#x200B;](assets/validate-event-pageViews.png)

1. Schuif omlaag naar het `web` -object, selecteer dit om het te openen en inspecteer de `webPageDetails.name` , `webPageDetails.server` en `webPageDetails.siteSection` . Deze moeten overeenkomen met de overeenkomstige gegevenslaagvariabelen voor `digitalData` op de startpagina

>[!TIP]
>
> U kunt als volgt de gegevenslaag `digitalData` op de startpagina weergeven en vergelijken:
>
> 1. Open de browsergereedschappen voor ontwikkelaars op de startpagina van Luma. In het geval van Chrome selecteert u de knop `F12` op het toetsenbord
> 1. Selecteer de tab **[!UICONTROL Console]**
> 1. Voer `digitalData` in en selecteer `Enter` op het toetsenbord om de waarden van de gegevenslaag weer te geven

![&#x200B; lusje van het Netwerk &#x200B;](assets/validate-xdm-content.png)

U kunt ook de identiteitskaartgegevens valideren:

1. Meld u aan bij de Luministensite met de referenties `test@test.com`/`test`

1. Terugkeer aan de [&#x200B; homepage van Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html)

1. De sectie **[!UICONTROL Experience Platform Web SDK]** openen in de linkernavigatie

   ![&#x200B; SDK van het Web in Debugger &#x200B;](assets/identity-debugger-websdk-dark.png)

1. Selecteer de rij **[!UICONTROL events]** om details in een pop-up te openen

   ![&#x200B; SDK van het Web in Debugger &#x200B;](assets/identity-deugger-websdk-event-dark.png)

1. Onderzoek naar **identityMap** binnen pop-up. Hier ziet u `lumaCrmId` met drie toetsen voor authenticatedState, id en primary:
   ![&#x200B; SDK van het Web in Debugger &#x200B;](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)

### Clientverzoeken valideren met de hulpprogramma&#39;s voor het ontwikkelen van browsers

Deze types van verzoekdetails zijn ook zichtbaar in de hulpmiddelen van de Webontwikkelaar van browser **Netwerk** tabel (het veronderstellen van de website laadt uw markeringsbibliotheek).

1. Open het 1&rbrace; lusje van het Netwerk **van de de Webontwikkelaar van browser hulpmiddelen &lbrace;en laad de pagina opnieuw.** Filter voor vraag met `/ee` om van de vraag de plaats te bepalen, het te selecteren, en dan in de **Kopballen** tabel te kijken, en **nuttige lading** tabel

   ![&#x200B; lusje van het Netwerk &#x200B;](assets/validate-dev-console.png)

1. Ga naar het **lusje van de Reactie** en neem nota hoe de ECID waarde in de reactie inbegrepen is.

   ![&#x200B; lusje van het Netwerk &#x200B;](assets/validate-dev-console-ecid.png)

   >[!NOTE]
   >
   > De waarde ECID is zichtbaar in de netwerkreactie. Het is niet inbegrepen in het `identityMap` gedeelte van het netwerkverzoek, noch wordt het opgeslagen in dit formaat in een koekje.

## Netwerkaanvragen op de server valideren met Experience Platform Debugger

Zoals u in [&#x200B; leerde vormen een datastream &#x200B;](configure-datastream.md) les, verzendt het Web SDK van het Platform eerst gegevens van uw digitaal bezit naar Platform Edge Network. Vervolgens doet Platform Edge Network aanvullende verzoeken aan de serverzijde aan de overeenkomstige services die in uw datastream zijn ingeschakeld. U kunt de verzoeken aan de serverzijde die door Platform Edge Network worden gemaakt bevestigen door het Spoor van Edge in Debugger te gebruiken.

<!--Furthermore, you can also validate the fully processed payload after it reaches an Adobe application by using [Adobe Experience Platform Assurance](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home). -->


### Edge-trace inschakelen

Edge-trace inschakelen:

1. In de linkernavigatie van **[!UICONTROL Experience Platform Debugger]** select **[!UICONTROL Logs]**
1. Selecteer de tab **[!UICONTROL Edge]** en selecteer **[!UICONTROL Connect]**

   ![&#x200B; verbindt het Spoor van Edge &#x200B;](assets/analytics-debugger-edgeTrace.png)

1. Het is nu leeg

   ![&#x200B; Verbonden het Spoor van Edge &#x200B;](assets/analytics-debugger-edge-connected.png)

1. Vernieuw de [&#x200B; homepage van de Luma &#x200B;](https://luma.enablementadobe.com/) en controleer **[!UICONTROL Experience Platform Debugger]** opnieuw, om gegevens te zien door komen.

   ![&#x200B; het baken van Edge van de Analyse &#x200B;](assets/validate-edge-trace.png)

Op dit moment kunt u geen Platform Edge Network-aanvragen weergeven die naar Adobe-toepassingen gaan omdat u in de gegevensstroom geen toepassingen hebt ingeschakeld. In toekomstige lessen gebruikt u Edge Trace om de uitgaande serververzoeken aan Adobe-toepassingen en het doorsturen van gebeurtenissen weer te geven. Maar eerst, leer over een ander hulpmiddel om server-zijverzoeken te bevestigen die door Platform Edge Network-Adobe Experience Platform Assurance worden gemaakt!

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

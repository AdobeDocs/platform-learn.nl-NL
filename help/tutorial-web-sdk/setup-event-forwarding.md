---
title: Opstelling een gebeurtenis door:sturen met de gegevens van het Web SDK van het Platform
description: Leer hoe te om gebeurtenis-door:sturen bezit te gebruiken gebruikend de gegevens van SDK van het Web van Experience Platform. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Event Forwarding
jira: KT-15414
exl-id: 5a306609-2c63-42c1-8beb-efa412b8efe4
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '1785'
ht-degree: 0%

---

# Gebeurtenis die met de gegevens van SDK van het Web van het Platform door:sturen

Leer hoe u gebeurtenissen kunt doorsturen met Adobe Experience Platform Web SDK-gegevens.

Het door:sturen van de gebeurtenis is een nieuw type van bezit beschikbaar in de Inzameling van Gegevens. Door gebeurtenissen door:sturen kunt u gegevens rechtstreeks vanuit Adobe Experience Platform Edge Network naar andere leveranciers dan Adobe verzenden in plaats van naar de traditionele clientbrowser. Kom meer over de voordelen van gebeurtenis te weten door:sturen in de [ Gebeurtenis die overzicht ](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/overview) door:sturen.


![ SDK van het Web en gebeurtenis die diagram ](assets/dc-websdk-eventforwarding.png) door:sturen

Als u gebeurtenissen wilt doorsturen in Adobe Experience Platform, moeten gegevens eerst naar Adobe Experience Platform Edge Network worden verzonden met een of meer van de volgende drie opties:

* [Adobe Experience Platform Web SDK](overview.md)
* [ Adobe Experience Platform Mobile SDK ](https://developer.adobe.com/client-sdks/home/)
  <!--* [Server-to-Server API](https://experienceleague.adobe.com/nl/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-s2s)-->


>[!NOTE]
>Het Platform Web SDK en Platform Mobile SDK vereisen geen implementatie via tags, maar het wordt aanbevolen om tags te gebruiken voor de implementatie van deze SDK&#39;s.

Nadat u de vorige lessen in deze zelfstudie hebt voltooid, verzendt u gegevens naar Platform Edge Network met behulp van Web SDK. Zodra de gegevens in Platform Edge Network zijn, kunt u gebeurtenis toelaten door:sturen en een gebeurtenis-door:sturen bezit gebruiken om gegevens naar oplossingen te verzenden niet-Adobe.

## Leerdoelstellingen

Aan dit eind van deze les, zult u kunnen:

* Een eigenschap voor het doorsturen van gebeurtenissen maken
* Koppel een gebeurtenis-door:sturen bezit aan een gegevensbestand van SDK van het Web van het Platform
* Begrijp de verschillen tussen de gegevenselementen en de regels van het markeringsbezit en gebeurtenis-door:sturen bezitsgegevenselementen en regels
* Een gegevenselement voor het doorsturen van gebeurtenissen maken
* Vorm een gebeurtenis-door:sturen regel
* Valideer een gebeurtenis-door:sturen bezit met succes verzendt gegevens


## Vereisten

* Een softwarelicentie die het doorsturen van gebeurtenissen omvat. Het doorsturen van gebeurtenissen is een betaalde eigenschap van de Inzameling van Gegevens. Neem contact op met uw Adobe-accountteam voor meer informatie.
* Het door:sturen van gebeurtenissen wordt toegelaten in uw organisatie van Experience Cloud.
* Gebruikersmachtiging voor het doorsturen van gebeurtenissen. (In [ Admin Console ](https://adminconsole.adobe.com/), onder het product van Adobe Experience Platform Launch, toestemmingspunten voor [!UICONTROL Platforms] > [!UICONTROL Edge] en allen [!UICONTROL Property Rights]). Als deze eenmaal is toegekend, ziet u [!UICONTROL Event Forwarding] in de linkernavigatie van de interface voor gegevensverzameling:
  ![ Gebeurtenis door:sturen eigenschappen ](assets/event-forwarding-menu.png)

* Adobe Experience Platform Web of Mobile SDK is geconfigureerd om gegevens naar Edge Network te verzenden. U moet de volgende lessen uit deze zelfstudie hebben geleerd:

   * Eerste configuratie

      * [Een XDM-schema configureren](configure-schemas.md)
      * [Naamruimte configureren](configure-identities.md)
      * [Een gegevensstroom configureren](configure-datastream.md)

   * Configuratie van tags

      * [Web SDK-extensie installeren](install-web-sdk.md)
      * [Gegevenselementen maken](create-data-elements.md)
      * [Identiteiten maken](create-identities.md)
      * [Tagregels maken](create-tag-rule.md)
      * [Valideren met Adobe Experience Platform Debugger](validate-with-debugger.md)


## Een eigenschap voor het doorsturen van gebeurtenissen maken

Begin door een gebeurtenis-door:sturen bezit te creëren:

1. Open de [ interface van de Inzameling van Gegevens ](https://experience.adobe.com/#/data-collection)
1. Selecteer **[!UICONTROL Event Forwarding]** in de linkernavigatie
1. Selecteer **[!UICONTROL New Property]**.
   ![ Gebeurtenis door:sturen eigenschappen ](assets/event-forwarding-new.png)

1. Geef de eigenschap een naam. In dit geval, `Server-Side - Web SDK Course`

1. Selecteer **[!UICONTROL Save]**.
   ![ gebeurtenis-door:sturen bezit sparen ](assets/event-forwarding-save.png)

## De gegevensstroom configureren

Voor gebeurtenis door:sturen om de gegevens te gebruiken die u naar Platform Edge Network verzendt, moet u het nieuwe gebeurtenis-door:sturen bezit aan de zelfde gegevensstroom verbinden die wordt gebruikt om gegevens naar de oplossingen van Adobe te verzenden.

Om Doel in de gegevensstroom te vormen:

1. Ga naar [ interface van de Inzameling van 0&rbrace; Gegevens](https://experience.adobe.com/#/data-collection){target="blank"}
1. Selecteer **[!UICONTROL Datastreams]** bij de linkernavigatie
1. Selecteer de eerder gemaakte `Luma Web SDK: Development Environment` datastream

   ![ selecteer de datastream van SDK van het Web van Luma ](assets/datastream-luma-web-sdk-development.png)

1. Selecteren **[!UICONTROL Add Service]**
   ![ voegt de dienst aan de datastream ](assets/event-forwarding-datastream-addService.png) toe
1. Selecteer **[!UICONTROL Event Forwarding]** als de **[!UICONTROL Service]**

1. Selecteer onder het vervolgkeuzemenu **[!UICONTROL Property ID]** de naam die u aan de eigenschap voor het doorsturen van gebeurtenissen hebt gegeven, in dit geval `Server-Side - Web SDK Course`

1. Selecteer onder het vervolgkeuzemenu **[!UICONTROL Environment ID]** de tagomgeving waarnaar u de omgeving voor het doorsturen van gebeurtenissen koppelt, in dit geval `Development`

   >[!TIP]
   >
   >    Als u gegevens wilt verzenden naar een omgeving voor het doorsturen van gebeurtenissen buiten de Adobe-org, selecteert u **[!UICONTROL Manually enter IDs]** en plakt u deze in een id. Identiteitskaart wordt verstrekt wanneer u een gebeurtenis-door:sturen bezit creeert.

1. Selecteer **[!UICONTROL Save]**.

   ![ Gebeurtenis door:sturen DataStream Enablement ](assets/event-forwarding-datastream-enable.png)

Herhaal deze stappen voor het opvoeren en productie gegevensstromen wanneer u bereid bent om uw veranderingen door de het publiceren stroom te bevorderen.

## Gegevens van Platform Edge Network doorsturen naar een niet-Adobe oplossing

In deze oefening leert u hoe te opstelling een gebeurtenis-door:sturen gegevenselement, vormt een gebeurtenis-door:sturen regel, en bevestigt het gebruiken van een derdedeel hulpmiddel genoemd [ Webhaak.site ](https://webhook.site/).

>[!NOTE]
>
>Een webhaak is een manier om verschillende systemen in halfreal-time te integreren. [ WebHaak.site ](https://webhook.site/) is een derdehulpmiddel dat u gemakkelijk (met de visuele Bouwer van de Acties van de Douane, of WebHaakScript) om het even welke inkomende HTTP- verzoek of e-mail laat inspecteren, testen en automatiseren.

>[!IMPORTANT]
>
>U moet reeds gegevenselementen en in kaart gebrachte gegevenselementen aan een Voorwerp XDM, evenals gevormde markeringsregels hebben gecreeerd en die veranderingen binnen een bibliotheek aan een markeringsmilieu bouwt om verder te werk te gaan. Als u niet hebt, verwijs naar de **stappen van de Configuratie van 0&rbrace; Codes in de** eerste vereisten [ sectie. ](setup-event-forwarding.md#prerequisites) Die stappen zorgen ervoor dat het gegeven wordt verzonden naar het Platform Edge Network, en van daar kunt u een gebeurtenis-door:sturen bezit vormen om gegevens aan een niet-Adobe oplossing door:sturen.


### Een gegevenselement voor het doorsturen van gebeurtenissen maken

Het XDM voorwerp u eerder gebruikend de de markeringsuitbreiding van SDK van het Web van het Platform vormde de gegevensbron voor gegevenselementen in een gebeurtenis-door:sturen bezit. U gebruikt de zelfde gegevens die u reeds in het markeringsbezit als gegevensbron voor gebeurtenis-door:sturen hebt gevormd.

>[!IMPORTANT]
>
>Er is één zeer belangrijk syntaxisverschil wanneer het van verwijzingen voorzien van gebieden XDM in gebeurtenis door:sturen tegenover andere contexten. Als u wilt verwijzen naar gegevens in een eigenschap voor het doorsturen van gebeurtenissen, moet het pad naar het gegevenselement het voorvoegsel `arc.event` bevatten:
>
> * `arc` staat voor Adobe Response Context.
> * Bijvoorbeeld: `arc.event.xdm.web.webPageDetails.URL`
>
>Als dit pad onjuist is opgegeven, worden geen gegevens verzameld.

In deze oefening, zult u de browser viewport hoogte en identiteitskaart van Experience Cloud van het Voorwerp XDM aan een webhaak door:sturen. Het XDM gebiedspad wordt bepaald door het schema XDM dat tijdens [ wordt gecreeerd vormt een XDM schema ](configure-schemas.md) les.

>[!TIP]
>
>U kunt de XDM objecten weg ook vinden door uw hulpmiddelen van het Webbrowser netwerk te gebruiken, die voor `/ee` verzoeken filtreren, die de baken [!UICONTROL **Payload**] openen en neer aan veranderlijk boren u zoekt. Klik vervolgens met de rechtermuisknop en selecteer &quot;Pad eigenschap kopiëren&quot;. Hier volgt een voorbeeld voor de Viewport-hoogte van de browser:
>&#x200B;> ![Event Forwarding XDM Path ](assets/event-forwarding-xdm-path.png)

1. Ga naar de eigenschap **[!UICONTROL Event Forwarding]** die u onlangs hebt gemaakt

1. Selecteer **[!UICONTROL Data Elements]** bij de linkernavigatie

1. Selecteren tot **[!UICONTROL Create New Data Element]**

   ![ Gebeurtenis door:sturen het Nieuwe Element van Gegevens ](assets/event-forwarding-new-dataelement.png)

1. **[!UICONTROL Name]** the data element `environment.browserDetails.viewportHeight`

1. Onder **[!UICONTROL Extension]** laat u `CORE` achter

1. Onder **[!UICONTROL Data Element Type]** selecteert u `Path`

1. Typ het XDM-objectpad dat de weergavehoogte van de browser bevat `arc.event.xdm.environment.browserDetails.viewportHeight`

1. Selecteren **[!UICONTROL Save]**

   ![ Gebeurtenis door:sturen ECID weg ](assets/event-forwarding-browser-viewpoirt-height.png)


1. Een ander gegevenselement maken

1. **[!UICONTROL Name]** it `ecid`

1. Onder **[!UICONTROL Extension]** laat u `CORE` achter

1. Onder **[!UICONTROL Data Element Type]** selecteert u `Path`

1. Typ het XDM-objectpad dat de Experience Cloud-id bevat `arc.event.xdm.identityMap.ECID.0.id`

1. Selecteren **[!UICONTROL Save]**

   ![ Gebeurtenis door:sturen ECID weg ](assets/event-forwarding-ecid.png)

   >[!CAUTION]
   >
   > Zorg ervoor dat u het voorvoegsel `arc.event.` in het pad opneemt. Zorg er ook voor dat u de exacte hoofdletter van het veld XDM-object volgt. De naamruimte ECID moet zich in alle hoofdletters bevinden.


   >[!TIP]
   >
   >Wanneer het werken met uw eigen website, kunt u de XDM objecten weg met uw hulpmiddelen van het Webbrowser netwerk vinden, die voor `/ee` verzoeken filtreren, die het baken [!UICONTROL **Payload**] openen en neer aan de variabele boren u zoekt. Klik vervolgens met de rechtermuisknop en selecteer &quot;Pad eigenschap kopiëren&quot;. Hier volgt een voorbeeld voor de Viewport-hoogte van de browser:
   > ![ Gebeurtenis door:sturen XDM Weg ](assets/event-forwarding-xdm-path.png)

### De extensie Adobe Cloud Connector installeren

Als u gegevens naar locaties van derden wilt verzenden, moet u eerst de extensie [!UICONTROL Adobe Cloud Connector] installeren.

1. Selecteer **[!UICONTROL Extensions]** bij de linkernavigatie

1. Selecteer de tab **[!UICONTROL Catalog]**

1. Zoek naar **[!UICONTROL Adobe Cloud Connector]**, uitgezocht **[!UICONTROL Install]**

   ![ Gebeurtenis door:sturen ECID weg ](assets/event-forwarding-adobe-cloud-connector.png)

Er is geen extensieconfiguratie nodig. Met deze extensie kunt u nu gegevens doorsturen naar een niet-Adobe-oplossing!

### Creeer een gebeurtenis-door:sturen regel

Er zijn een paar belangrijkste verschillen tussen het vormen regels in een markeringsbezit en een regel in een gebeurtenis-door:sturen bezit:

* **[!UICONTROL Events]&amp;[!UICONTROL Conditions]** :

   * **Markeringen**: Alle regels worden teweeggebracht door een Gebeurtenis die in de regel moet worden gespecificeerd, bijvoorbeeld, `Library Loaded - Page Top`. Voorwaarden zijn optioneel.
   * **Gebeurtenis door:sturen**: Men veronderstelt dat elke gebeurtenis die naar Platform Edge Network wordt verzonden een trekker is om gegevens door:sturen. Daarom zijn er geen [!UICONTROL Events] die in gebeurtenis-door:sturen regels moet worden geselecteerd. Om te beheren welke gebeurtenissen een gebeurtenis-door:sturen regel teweegbrengen, moet u voorwaarden vormen.

* **het element van Gegevens kenization**:

   * **Markeringen**: De namen van het gegevenselement worden samengevoegd met a `%` aan het begin en eind van de naam van het gegevenselement wanneer gebruikt in een regel. Bijvoorbeeld `%viewportHeight%` .

   * **Gebeurtenis door:sturen**: De namen van het gegevenselement worden samengevoegd met `{{` aan het begin en `}}` aan het eind van de naam van het gegevenselement wanneer gebruikt in een regel. Bijvoorbeeld `{{viewportHeight}}` .

* **Opeenvolging van regelacties**:

   * De sectie van Acties van een gebeurtenis die regel door:sturen wordt altijd opeenvolgend uitgevoerd. Zorg ervoor dat de volgorde van de handelingen correct is wanneer u een regel opslaat. Deze uitvoeringsvolgorde kan niet asynchroon worden uitgevoerd, zoals met tags.

<!--
  * **Tags**: Rule actions can easily be reordered using drag-and-drop functionality.
  * **Event forwarding**: Rule actions are always executed sequentially. Make sure the order of actions is correct when you save a rule.
-->

Om een regel te vormen om gegevens aan uw webhaak door:sturen, moet u uw persoonlijke webhaak eerst verkrijgen:

1. Ga naar [ WebHaak.site ](https://webhook.site)

1. Vind **Uw unieke URL**, gebruikt u dit als verzoek URL in uw gebeurtenis-door:sturen regel

1. Selecteren **[!UICONTROL Copy to clipboard]**

1. Laat dit venster open aangezien u de gebeurtenis kunt bevestigen die gegevens in real time door:sturen die door Webhaak wordt gevangen

   ![ Webhaak URL van het Exemplaar ](assets/event-forwarding-webhook.png)

1. Ga terug **[!UICONTROL Data Collection]** > **[!UICONTROL Event Forwarding]** > **[!UICONTROL Rules]** van de linkernavigatie

1. Selecteren **[!UICONTROL Create New Rule]**

   ![ Gebeurtenis die Nieuwe regel door:sturen ](assets/event-forwarding-new-rules.png)

1. Naam geven `all events - ad cloud connector - webhook`

1. Een handeling toevoegen

1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Cloud Connector]**

1. Onder **[!UICONTROL Action Type]** selecteert u **[!UICONTROL Make Fetch Call]**

1. Plak de URL van uw webhaak in het veld **[!UICONTROL URL]**

   ![ Webhaak URL van het Exemplaar ](assets/event-forwarding-rule.png)

1. Onder **[de Params van de Vraag]**, zult u beide gegevenselementen toevoegen u vroeger creeerde.

1. Op het **[!UICONTROL Key]** kolomtype in `viewPortHeight` . Voer in de kolom **[!UICONTROL Value]** het gegevenselement `{{environment.browserDetails.viewportHeight}}` in door het in te voeren of te selecteren met het pictogram voor de gegevenselementkiezer

1. Selecteer [!UICONTROL **+ Voeg nog een**] toe om een andere vraagparameter toe te voegen

1. Op het **[!UICONTROL Key]** kolomtype in `ecid` . Voer in de kolom Waarde het gegevenselement `{{ecid}}` in

1. Selecteren **[!UICONTROL Keep Changes]**

   ![ voeg vraagparameter ](assets/event-forwarding-rule-query-parameter.png) toe

1. Je regel moet er hieronder uitzien

1. Selecteren **[!UICONTROL Save]**

   ![ sparen gebeurtenis-door:sturen regel ](assets/event-forwarding-rule-save.png)

### De bibliotheek maken en bouwen

Creeer een bibliotheek en bouw alle veranderingen in uw gebeurtenis-door:sturen ontwikkelomgeving zoals u normaal in een markeringsbezit zou doen.

>[!NOTE]
>
>Als u het Staging en de productie gebeurtenis-door:sturen eigenschappen aan uw gegevensstroom niet hebt verbonden, zult u het milieu van de Ontwikkeling als enige optie zien om een bibliotheek aan te bouwen.

![ sparen gebeurtenis-door:sturen regel ](assets/event-forwarding-initial-build.png)

## Valideer gebeurtenis-door:sturen regel

Nu kunt u uw gebeurtenis-door:sturen bezit bevestigen gebruikend de Debugger van het Platform, en WebHaak.site:

1. Volg de stappen aan [ schakelaar de markeringsbibliotheek ](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) op de [ plaats van de Demo van de Luma ](https://luma.enablementadobe.com/content/luma/us/en/men.html) aan het de markeringsbezit van SDK van het Web waaraan u uw gebeurtenis-door:sturen bezit in de datastream in kaart bracht.

1. Voordat u de pagina opnieuw laadt, opent u **[!UICONTROL Logs]** in Experience Platform Debugger vanuit de linkernavigatie

1. Selecteer het tabblad **[!UICONTROL Edge]** en selecteer vervolgens **[!UICONTROL Connect]** om de Edge Network-verzoeken voor het platform weer te geven

   ![ Gebeurtenis die de zitting van het randnetwerk door:sturen ](assets/event-forwarding-edge-session.png)

1. De pagina opnieuw laden

1. U zult extra verzoeken zien die u zicht in de server-zijverzoeken geven die door het Platform Edge Network aan WebHook worden verzonden

1. De aanvraag om validatie te activeren is de aanvraag die de volledig samengestelde URL weergeeft die door het Edge-netwerk wordt verzonden

   ![ Gebeurtenis door:sturen debugger ](assets/event-forwarding-debugger.png)


1. Noteer de parameters viewPortHeight en ecid voor de queryreeks

   ![ Gebeurtenis door:sturen bevestigt vraagkoorden ](assets/event-forwarding-validate-data.png)

1. Ze komen overeen met de gegevens in het XDM-object

   ![ Gebeurtenis door:sturen passende gegevens ](assets/event-forwarding-matching-data.png)

1. Ten slotte, bevestig de gegevensgelijken in [ Webhaak.site ](https://webhook.site) eveneens door uw open venster van Webhaak te bekijken

   ![ Gebeurtenis die websitegegevens door:sturen webhaak ](assets/event-forwarding-webhook-data.png)

Gefeliciteerd! U hebt gebeurtenis gevormd door:sturen!

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

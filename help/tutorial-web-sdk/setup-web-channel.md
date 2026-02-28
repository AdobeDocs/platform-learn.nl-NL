---
title: Journey Optimizer-webkanaal instellen met Platform Web SDK
description: Leer hoe u Journey Optimizer-webkanaal implementeert met Platform Web SDK. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
solution: Data Collection,Experience Platform,Journey Optimizer
feature-set: Journey Optimizer
feature: Web Channel,Web SDK
jira: KT-15411
exl-id: ab83ce56-7f54-4341-8750-b458d0db0239
source-git-commit: 1feddab414a8a7e49f04b8886c275d06516d0114
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 0%

---


# Journey Optimizer-webkanaal instellen met Web SDK

Leer hoe te om het Webkanaal van Adobe Journey Optimizer [&#x200B; uit te voeren &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/web/get-started-web) gebruikend het Web SDK van Adobe Experience Platform. Deze les behandelt de fundamentele vereisten van het Webkanaal, gedetailleerde stappen voor configuratie, en een diepe duik in een gebruiksgeval dat op loyaliteitsstatus wordt gecentreerd.

In deze les zijn Journey Optimizer-gebruikers uitgerust om het webkanaal te gebruiken voor geavanceerde onlinepersonalisatie met de Journey Optimizer-webontwerper.



![&#x200B; SDK van het Web en het diagram van Adobe Analytics &#x200B;](assets/dc-websdk-ajo.png)

## Leerdoelen

Aan het einde van deze les kunt u het volgende doen:

* Begrijp de functie en de betekenis van Web SDK bij het leveren van de ervaring van het Webkanaal.
* Begrijp het proces van het creëren van een campagne van het Webkanaal van begin tot eind gebruikend het voorbeeld Luma Loyalty Rewards gebruiksgeval.
* Vorm campagneeigenschappen, acties, en programma&#39;s binnen de interface.
* Begrijp de functionaliteit en de voordelen van de extensie Adobe Experience Cloud Visual Editing Helper.
* Leer met de webontwerper de inhoud van webpagina&#39;s te bewerken, inclusief afbeeldingen, kopteksten en andere elementen.
* Leer hoe u voorstellen op een webpagina invoegt met de beslissingscomponent Voorstel.
* U vertrouwd maken met de beste praktijken om de kwaliteit en het succes van een webkanaalcampagne te garanderen.

## Vereisten

Om de lessen in deze sectie te voltooien, moet u eerst:

* Voltooi alle lessen voor aanvankelijke configuratie van het Web SDK van het Platform, met inbegrip van vestiging gegevenselementen en regels.
* Zorg ervoor dat de extensie Adobe Experience Platform Web SDK 2.16 of hoger is.
* Voltooi de Experience Platform-les instellen, inclusief de oefening om het `Luma Loyalty Rewards – Gold Status` -publiek te maken.
* Gedownload en laat [&#x200B; Adobe Experience Cloud Visual Editing Helper browser uitbreiding &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) toe.
* Als u de Journey Optimizer-webontwerper gebruikt om uw webkanaalervaring te ontwerpen, moet u controleren of u de Google Chrome- of Microsoft® Edge-browsers gebruikt.
* Zorg ervoor dat cookies van derden zijn toegestaan in uw browser. Het kan nodig zijn om ook eventuele advertentieblokkers in uw browser uit te schakelen.

  >[!CAUTION]
  >
  > In de Journey Optimizer-webontwerper kunnen bepaalde websites om een van de volgende redenen niet betrouwbaar worden geopend:
  > 
  > 1. De website heeft een streng beveiligingsbeleid.
  > 1. De website is ingesloten in een iframe.
  > 1. De QA- of werkgebiedsite van de klant is niet extern toegankelijk (het is een interne site).

* Wanneer het creëren van Webervaringen en met inbegrip van inhoud van de bibliotheek van de Hoofdzaak van de Activa van de Manager van de Ervaring van Adobe, is het noodzakelijk om [&#x200B; subdomain voor het publiceren van deze inhoud &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/web/configure-web-channel/web-delegated-subdomains) te vormen.
* Als het gebruiken van de eigenschap van de inhoudstest, zorg ervoor dat uw Webdataset ook inbegrepen in uw rapporteringsconfiguratie is.
* Momenteel worden twee typen implementaties ondersteund voor het maken en leveren van webkanaalcampagnes op uw wegeigenschappen:
   * Alleen client: als u uw website wilt wijzigen, moet u de Adobe Experience Platform Web SDK implementeren.
   * Hybride modus: u kunt de Platform Edge Network Server-API gebruiken om de personalisatie op de server aan te vragen. De reactie van de API wordt vervolgens doorgegeven aan de Adobe Experience Platform Web SDK voor het renderen van wijzigingen op de client. Raadpleeg de documentatie bij de Adobe Experience Platform Edge Network Server API voor meer informatie. In dit blogbericht vindt u meer details en implementatiemonsters voor de hybride modus.

  >[!NOTE]
  >
  >Implementatie alleen op de server wordt momenteel niet ondersteund.




## Terminologie

Ten eerste moet u de terminologie begrijpen die in webkanaalcampagnes wordt gebruikt.

* **kanaal van het Web**: Een middel voor mededeling of de levering van inhoud via het Web. In de context van deze handleiding verwijst het naar het mechanisme waarmee gepersonaliseerde inhoud wordt geleverd aan websitebezoekers die de Platform Web SDK, in Adobe Journey Optimizer gebruiken.
* **oppervlakte van het Web**: Verwijs naar een Webbezit dat door URL wordt geïdentificeerd waar de inhoud wordt geleverd. Het kan één of meerdere Web-pagina&#39;s omvatten.
* **het Webontwerper van Journey Optimizer**: Een specifiek hulpmiddel of een interface binnen Journey Optimizer waar de gebruikers hun ervaringen van het Webkanaal kunnen ontwerpen.
* **Adobe Experience Cloud Visuele het Uitgeven Helper**: Een browser uitbreiding die in visueel het uitgeven van en het ontwerpen van de ervaringen van het Webkanaal bijstaat.
* **Datastream**: Een configuratie binnen de dienst van Adobe Experience Platform die ervoor zorgt dat de ervaringen van het Webkanaal kunnen worden geleverd.
* **beleid van de Fusie**: Een configuratie die de nauwkeurige activering en de publicatie van binnenkomende campagnes verzekert.
* **Publiek**: Een specifiek segment van gebruikers of plaatsbezoekers die aan bepaalde criteria voldoen.
* **ontwerper van het Web**: Een interface of een hulpmiddel dat in visueel het uitgeven van en het ontwerpen van Webervaringen zonder diep in code te duiken helpt.
* **de redacteur van de Uitdrukking**: Een hulpmiddel binnen de Webontwerper dat gebruikers toestaat om verpersoonlijking aan webinhoud toe te voegen, potentieel gebaseerd op gegevensattributen of andere criteria.
* **de besluitvormingscomponent van de Aanbieding**: Een component in de Webontwerper die in het beslissen helpt welke aanbieding het meest geschikt is om aan een specifieke bezoeker te worden getoond die op besluitvormingsbeheer wordt gebaseerd.
* **experiment van de Inhoud**: Een methode om verschillende inhoudsvariaties te testen om te weten te komen welke het best in termen van gewenste metrisch, zoals binnenkomende kliks presteert.
* **Behandeling**: In de context van inhoudexperimenten, verwijst een behandeling naar een specifieke variatie van inhoud die tegen een andere wordt getest.
* **Simulatie**: Een voorproefmechanisme om de ervaring van het Webkanaal te visualiseren alvorens het voor levend publiek te activeren.

## De gegevensstroom configureren

U hebt de Adobe Experience Platform-service al toegevoegd aan uw gegevensstroom. Nu moet u de optie Adobe Journey Optimizer inschakelen zodat u webkanaalervaringen kunt aanbieden.

Adobe Journey Optimizer configureren in de gegevensstroom:

1. Ga naar de [&#x200B; interface van de Inzameling van Gegevens &#x200B;](https://experience.adobe.com/#/data-collection){target="blank"}.
1. Selecteer **[!UICONTROL Datastreams]** bij de linkernavigatie.
1. Selecteer de eerder gemaakte Luma Web SDK-gegevensstroom.

   ![&#x200B; Uitgezochte datastream &#x200B;](assets/web-channel-select-datastream.png)

1. Selecteer **[!UICONTROL Edit]** in Adobe Experience Platform.

   ![&#x200B; geef datastream &#x200B;](assets/web-channel-edit-datastream.png) uit

1. Schakel het selectievakje **[!UICONTROL Adobe Journey Optimizer]** in.

1. **[!UICONTROL Save]** de bijgewerkte configuratie.

   ![&#x200B; de doos van AJO van de Controle &#x200B;](assets/web-channel-check-ajo-box.png)


Dit zorgt ervoor dat binnenkomende gebeurtenissen voor Journey Optimizer correct worden afgehandeld door de Adobe Experience Platform Edge Network.

## Het samenvoegbeleid configureren

Zorg ervoor dat er een samenvoegbeleid is gedefinieerd met de optie **[!UICONTROL Active-On-Edge Merge Policy]** ingeschakeld. Deze optie van het fusiebeleid wordt gebruikt door de inkomende kanalen van Journey Optimizer om de nauwkeurige activering en de publicatie van binnenkomende campagnes op de rand te verzekeren.

De optie configureren in het samenvoegbeleid:

1. Ga naar de pagina **[!UICONTROL Customer]** > **[!UICONTROL Profiles]** in de Experience Platform- of Journey Optimizer-interface.
1. Zorg ervoor dat u zich in de sandbox bevindt die voor de zelfstudie wordt gebruikt
1. Selecteer het tabblad **[!UICONTROL Merge Policies]**. 
1. Selecteer het beleid (u kunt het beste het [!UICONTROL Default Timebased] beleid gebruiken) en schakel de optie **[!UICONTROL Active-On-Edge Merge Policy]** in de stap **[!UICONTROL Configure]** in of uit.

   ![&#x200B; knevel fusiebeleid &#x200B;](assets/web-channel-active-on-edge-merge-policy.png)

## De webdataset configureren voor het experimenteren met inhoud

Als u inhoudstests wilt gebruiken in webkanaalcampagnes, moet u ervoor zorgen dat de gebruikte webdataset ook wordt opgenomen in uw rapportconfiguratie. Het Journey Optimizer-rapportagesysteem gebruikt de dataset op een alleen-lezen manier om rapporten voor het experimenteren met inhoud buiten de box te vullen.

[&#x200B; het Toevoegen van datasets voor inhoudexperiment het melden is gedetailleerd in deze sectie &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/reporting/channel-report/reporting-configuration#add-datasets).

## Hoofdletters gebruiken - Loyalty&#39;s

In deze les, wordt een geval van het de gebruiks van de beloningen van de steekproefLoyalty gebruikt om implementatie van een Webkanaalervaring te detailleren gebruikend het Web SDK.

Met dit gebruiksgeval kunt u beter begrijpen hoe Journey Optimizer uw klanten de beste binnenkomende ervaringen kan bieden, door gebruik te maken van Journey Optimizer-campagnes en de webontwerper.

Aangezien deze zelfstudie gericht is op implementatoren, is het vermeldenswaard dat deze les substantieel interfacewerk in Journey Optimizer impliceert. Hoewel dergelijke interfacetaken doorgaans door marketers worden afgehandeld, kan het voor implementatoren gunstig zijn om insight in het proces te betrekken, zelfs als ze gewoonlijk niet verantwoordelijk zijn voor het maken van een webkanaalcampagne.

### Loyalty Rewards-campagne maken

Nu u onze gegevens van de steekproefloyaliteit hebt gegeten en ons segment creeerde, creeer de het Webkanaalcampagne van Loyalty Rewards in Adobe Journey Optimizer.

De voorbeeldcampagne maken:

1. Open [&#x200B; Journey Optimizer &#x200B;](https://experience.adobe.com/journey-optimizer/home){target="_blank"} interface

   >[!NOTE]
   >
   > Het schema, de datasets, en het publiek kunnen ook in de interface van Journey Optimizer worden gebouwd aangezien zij allen gemeenschappelijke constructs van Experience Platform zijn.

1. Ga naar **[!UICONTROL Journey Management]** > **[!UICONTROL Campaigns]** in de linkernavigatie
1. Klik op **[!UICONTROL Create campaign]** rechtsboven.
1. Kies het type campagne. Voor het de gebruikscase van de Beloningen van de Loyalty, kies **Gepland - Op de markt brengend**.

   ![&#x200B; Geplande campagne &#x200B;](assets/web-channel-campaign-properties-scheduled.png)

1. Voeg enkele aanvullende details toe aan de nieuwe webkanaalcampagne. Geef eerst de naam van de campagne. Roep het `Luma Loyalty Rewards – Gold Status` aan. U kunt desgewenst een beschrijving aan de campagne toevoegen. Voeg ook **[!UICONTROL Tags]** toe om de algemene campagnetaxonomie te verbeteren.

   ![&#x200B; Naam de campagne &#x200B;](assets/web-channel-campaign-name.png)

1. Ga naar de tab **[!UICONTROL Actions]**
1. Kies de **[!UICONTROL Web]** als de **[!UICONTROL Action name]** .
1. Selecteer **[!UICONTROL Create new configuration]** als de **[!UICONTROL Web configuration]** .
1. Voer de volgende gegevens in als de kanaalconfiguratie:
   1. `LumaHomepage` als de **[!UICONTROL Name]** .
   1. **[!UICONTROL Web]** als de **[!UICONTROL Channel]** .
   1. **[!UICONTROL Onsite Personalization]** als de **[!UICONTROL Marketing action]** .
   1. **[!UICONTROL Single page]** als de **[!UICONTROL Web settings]** .
   1. `https://newluma.enablementadobe.com/index.html` als de **[!UICONTROL Page URL]** .
1. **[!UICONTROL Submit]** de nieuwe kanaalconfiguratie

   ![&#x200B; vorm het Kanaal van het Web &#x200B;](assets/web-channel-configuration.png)
1. Selecteer de nieuwe `LumaHomepage` configuratie op het browsertabblad met uw campagne

   >[!TIP]
   >
   > Als de nieuwe configuratie niet in het vervolgkeuzemenu wordt weergegeven, gaat u naar het tabblad [!UICONTROL Properties] en gaat u terug naar het tabblad [!UICONTROL Actions] en controleert u het vervolgkeuzemenu opnieuw.


## Experimenteer met Loyalty Rewards-inhoud

Nu u [!UICONTROL Web configuration] hebt geselecteerd, kunt u in de sectie **[!UICONTROL Action]** optioneel een experiment maken om te testen welke inhoud het beste werkt voor het publiek van `Luma Loyalty Rewards – Gold Status` . Laten we twee behandelingen maken en testen als onderdeel van de configuratie van de campagne.

U kunt als volgt het inhoudexperiment maken:

1. Klik op **[!UICONTROL Create experiment]**.

   ![&#x200B; creeer experiment &#x200B;](assets/web-channel-create-content-experiment.png)

1. Kies eerst een **[!UICONTROL Success metric]** . Dit is de maatstaf voor het bepalen van de doeltreffendheid van inhoud. Kies **[!UICONTROL Unique Clicks]** om te zien welke inhoudsbehandeling meer klikken op het web genereert.

1. U kunt desgewenst een **[!UICONTROL Holdout]** aanwijzen die geen van beide behandelingen ontvangt. Laat dit nu ongecontroleerd.

1. Kies desgewenst ook **[!UICONTROL Distribute evenly]** . Schakel deze optie in om ervoor te zorgen dat de splitsingen van de behandeling altijd gelijkmatig zijn verdeeld.

1. Selecteer **[!UICONTROL Add treatment]** zodat het experiment twee behandelingen bevat.

1. Selecteer **[!UICONTROL Create]**.

   ![&#x200B; kies metrisch succes &#x200B;](assets/web-channel-content-experiment-metric.png)


[&#x200B; Leer meer over inhoudsexperimenten in het Webkanaal van Adobe Journey Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/content-management/content-experiment/get-started-experiment).



### Inhoud bewerken met de visuele hulp

Nu, auteur de ervaring van het Webkanaal. Eerst, installeer [&#x200B; Adobe Experience Cloud Visual Editing Helper &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) browser uitbreiding voor Google Chrome en Microsoft® Edge, als u niet reeds hebt. Ga na installatie verder met de stappen in de Journey Optimizer-interface:

1. Selecteer **[!UICONTROL Edit Content]** (of navigeer naar het tabblad Inhoud van de campagne). Aangezien u één pagina-URL hebt ingevoerd als het oppervlak, kunt u beter beginnen te werken in de composer.

   ![Content bewerken](assets/web-channel-edit-content.png)

1. Klik nu op **[!UICONTROL Edit web page]** om te beginnen met het ontwerpen van Behandeling A van uw ervaring.

   ![&#x200B; geef Web-pagina &#x200B;](assets/web-channel-edit-web-page.png) uit

1. Begin door sommige elementen te bewerken met de webcomposer. Gebruik het contextmenu om de koptekst van de hoofdafbeelding van de Luma te bewerken. Pas de stijl van het contextafhankelijke venster aan de rechterkant aan.

   ![&#x200B; voeg contextafhankelijke uitgeeft toe &#x200B;](assets/web-channel-some-contextual-edit.png)



1. Voeg ook personalisatie aan de container toe gebruikend **[!UICONTROL Expression editor]**.

   ![&#x200B; Open de uitdrukkingsredacteur &#x200B;](assets/web-channel-open-expression-editor.png)
   ![&#x200B; voeg verpersoonlijking &#x200B;](assets/web-channel-add-basic-personalization.png) toe

1. Zorg ervoor dat de ervaring correct voor kliks wordt gevolgd. Kies **[!UICONTROL Click track element]** in het contextmenu.

   ![&#x200B; klik spoor &#x200B;](assets/web-channel-click-tracking.png)

Er zijn vele opties beschikbaar om het overseinen te personaliseren.

### HTML-ontwerpwijzigingen

Er zijn een paar beschikbare methodes als u geavanceerdere, of douaneveranderingen in de plaats als component van de campagne van de Beloning van de Loyaliteit wilt aanbrengen. Een aantal hiervan ontdekken in Behandeling B.

Gebruik het deelvenster **[!UICONTROL Components]** om HTML of andere inhoud rechtstreeks toe te voegen aan de Luministensite.

![&#x200B; Onderzoek de componentenruit &#x200B;](assets/web-channel-components-pane.png)

Voeg een nieuwe HTML-component toe boven aan de pagina. Open **[!UICONTROL expression editor]** opnieuw om de HTML te bewerken.

![&#x200B; Open de uitdrukkingsredacteur &#x200B;](assets/web-channel-open-expression-editor-html.png)


U kunt ook HTML-bewerkingen toevoegen vanuit het deelvenster **[!UICONTROL Modifications]** . In dit deelvenster kunt u een component op de pagina selecteren en deze bewerken vanuit de ontwerpinterface.

Voeg in de editor de HTML voor het publiek van `Luma Loyalty Rewards – Gold Status` toe. Selecteer **[!UICONTROL Validate]**.

![&#x200B; bevestigt HTML &#x200B;](assets/web-channel-add-custom-html-validate.png)

Bekijk nu de nieuwe aangepaste HTML-component om deze passend te maken.

### De campagne richten op een publiek

Standaard is de campagne actief voor alle sitebezoekers. Voor de toepassing van dit gebruiksgeval mogen alleen leden met een goudstatus de ervaring zien. De inhoud als doel instellen voor dit publiek:

1. Ga naar het tabblad **[!UICONTROL Audience]**

1. Selecteer in het veld **[!UICONTROL Identity namespace]** de naamruimte voor het identificeren van personen binnen het gekozen segment. Aangezien u de campagne op de plaats van de Luma opstelt, kunt u ECID namespace kiezen. Profielen in het publiek van `Luma Loyalty Rewards – Gold Status` die de ECID-naamruimte tussen hun verschillende identiteiten niet hebben, worden niet aangeroepen door de webkanaalcampagne.

1. **[!UICONTROL Select audience]**

   ![&#x200B; Uitgezochte publiek &#x200B;](assets/web-channel-select-audience.png)

1. Kies het `Luma Loyalty Rewards - Gold Status` publiek u in de [&#x200B; Opstelling Experience Platform &#x200B;](setup-experience-platform.md) les creeerde.
1. **[!UICONTROL Save]** het publiek voor de campagne

   ![Doelgroep opslaan](assets/web-channel-save-audience.png)


<!--
### Simulate Loyalty Rewards Content

Look at a preview of the modified web page before activating the campaign. Keep in mind that you must have test profiles configured to simulate web channel experiences.

To simulate the experience:

1. Select **[!UICONTROL Simulate content]** within the campaign.

    ![Simulate content](assets/web-channel-simulate-content.png)

1. Choose a test profile to receive the simulation. Keep in mind that the test profile should be in the `Luma Loyalty Rewards – Gold Status` audience to receive the proper treatment.

1. The preview is displayed for the test profile.

1. Select the [!UICONTROL Content] tab

1. Choose the **[!UICONTROL Page URL]** web surface option to deploy the experience on one page for this campaign. Enter the URL for the Luma page, `https://newluma.enablementadobe.com`

1. Once the web surface is defined, select **[!UICONTROL Create]**.

    ![Select web surface](assets/web-channel-web-surface.png)
-->

### De campagne plannen

Standaard worden campagnes gestart en gestopt wanneer u ze handmatig activeert en deactiveert. U kunt deze echter plannen om op bepaalde datums en tijden te starten en te stoppen. Verlaat de standaardmontages en selecteer **Overzicht om** te activeren:

![&#x200B; Programma van de Campagne &#x200B;](assets/web-channel-campaign-schedule.png)

>[!NOTE]
>
>Houd er rekening mee dat voor webkanaalcampagnes de webervaring wordt weergegeven wanneer de bezoeker de pagina opent. In tegenstelling tot andere typen campagnes in Adobe Journey Optimizer, kan de sectie **[!UICONTROL Action triggers]** daarom niet worden geconfigureerd.



### De Loyalty Rewards-campagne activeren

U wordt gevraagd de details van de campagne een laatste keer te bevestigen. Selecteer **[!UICONTROL Activate]**. Het kan tot 15 minuten duren voordat de campagne live gaat op de site.

![&#x200B; activeer de campagne &#x200B;](assets/web-channel-campaign-activate.png)

### Loyalty Rewards QA

Er zijn een paar logins die u kunt gebruiken om gebruikers met de status &quot;goud&quot; te simuleren en in aanmerking te komen voor uw campagne. U moet de steekproefgegevens in de [&#x200B; Opstelling Experience Platform &#x200B;](setup-experience-platform.md) hebben geüpload en rekeningen creëren gebruikend deze geloofsbrieven op de website voor deze te werken.

1. `cleavlandeuler@emailsim.io`/`test`
1. `leftybeagen@emailsim.io`/`test`
1. `jenimartinho@emailsim.io`/`test`

U kunt het beste de campagnestatistieken van **[!UICONTROL Web]** volgen in het scherm met het campagneoverzicht nadat u de campagne hebt gestart of op **[!UICONTROL Reports]** klikken voor een uitgebreidere rapportage:

![&#x200B; het Webrapport van de Mening &#x200B;](assets/web-channel-web-report.png)

### Webkanaalvalidatie met Adobe Experience Platform Debugger

Met de extensie Adobe Experience Platform Debugger, die beschikbaar is voor zowel Chrome als Firefox, worden uw webpagina&#39;s geanalyseerd om problemen vast te stellen bij de implementatie van Adobe Experience Cloud-oplossingen.

Met het foutopsporingsprogramma op de Luminasite kunt u de ervaring met het webkanaal tijdens de productie valideren. Dit is beste praktijken zodra de het gebruiksgeval van de Beloningen van de Loyalty in werking is, om ervoor te zorgen dat alles correct wordt gevormd.

[&#x200B; Leer hoe te om debugger in uw browser te vormen gebruikend de gids hier &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/data-collection/debugger/overview).

De validatie starten met de foutopsporing:

1. Navigeer met de webkanaalervaring naar de Luma-webpagina.
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. Open de knop **[!UICONTROL Adobe Experience Platform Debugger]** terwijl u zich op de webpagina bevindt.
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. Navigeer aan **Samenvatting**. Controleer of de **[!UICONTROL Datastream ID]** overeenkomt met de **[!UICONTROL datastream]** in **[!UICONTROL Adobe Data Collection]** waarvoor u Adobe Journey Optimizer hebt ingeschakeld.
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. U kunt zich dan bij de plaats met diverse Luma loyaliteitsrekeningen aanmelden, en debugger gebruiken om de verzoeken te bevestigen die naar Adobe Experience Platform Edge Network worden verzonden.
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. Navigeer onder **[!UICONTROL Solutions]** naar de map **[!UICONTROL Experience Platform Web SDK]** .
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. Binnen het **lusje van de Configuratie**, knevel **[!UICONTROL Enable Debugging]**. Hierdoor wordt het aanmelden voor de sessie binnen een **[!UICONTROL Adobe Experience Platform Assurance]** -sessie ingeschakeld.
   <!--
    ![ADD SCREENSHOT](#)
    -->
1. Meld u met verschillende Luma-loyaliteitsaccounts aan bij de site en gebruik foutopsporing om de aanvragen te valideren die naar de **[!UICONTROL Adobe Experience Platform Edge network]** zijn verzonden. Al deze aanvragen moeten in **[!UICONTROL Assurance]** worden vastgelegd voor het bijhouden van logbestanden.
<!--
   ![ADD SCREENSHOT](#)
-->

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848?profile.language=nl)

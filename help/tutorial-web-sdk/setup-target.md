---
title: Adobe Target instellen met Platform Web SDK
description: Leer hoe te om Adobe Target uit te voeren gebruikend het Web SDK van het Platform. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
solution: Data Collection, Target
exl-id: 9084f572-5fec-4a26-8906-6d6dd1106d36
source-git-commit: 13f2c87d7c4cfe21f04a945b9e11dc64e9bf6e0c
workflow-type: tm+mt
source-wordcount: '3801'
ht-degree: 0%

---

# Adobe Target instellen met Platform Web SDK

Leer hoe te om Adobe Target uit te voeren gebruikend het Web SDK van het Platform. Leer hoe u ervaringen kunt bieden en hoe u extra parameters aan Target kunt doorgeven.

[Adobe Target](https://experienceleague.adobe.com/docs/target/using/target-home.html) is de Adobe Experience Cloud-toepassing die alles biedt wat u nodig hebt om de ervaring van uw klanten op maat te maken en aan te passen, zodat u uw omzet kunt maximaliseren op uw websites en mobiele sites, apps en andere digitale kanalen.


## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Begrijp hoe te om het Platform Web SDK toe te voegen die fragment vooraf verbergt om flikkering te verhinderen wanneer het gebruiken van Doel met asynchrone markering bed codes in
* Een gegevensstroom configureren om de functionaliteit Doel in te schakelen
* Weergavebeslissingen voor visuele personalisatie renderen wanneer de pagina wordt geladen (voorheen de algemene mbox)
* Geef XDM-gegevens door aan Doel en begrijp de toewijzing aan Doelparameters
* Aangepaste gegevens aan doel doorgeven, zoals profiel- en entiteitsparameters
* Valideer een implementatie van het Doel met het Web SDK van het Platform

>[!TIP]
>
>Zie onze [Doel migreren van at.js 2.x aan het Web SDK van het Platform](/help/tutorial-migrate-target-websdk/introduction.md) zelfstudie voor een stapsgewijze handleiding voor het migreren van uw bestaande implementatie at.js.


## Vereisten

Om de lessen in deze sectie te voltooien, moet u eerst:

* Voltooi alle lessen voor aanvankelijke configuratie van het Web SDK van het Platform, met inbegrip van opstellings gegevenselementen en regels.
* Zorg ervoor dat u beschikt over een [De rol Editor of fiatteur](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80).
* Installeer de [Helpextensie Visual Experience Composer](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html) als u de Google Chrome-browser gebruikt.
* Weet hoe u activiteiten in Target kunt instellen. Als u een herhaling nodig hebt, zijn de volgende zelfstudies en hulplijnen handig voor deze les:
   * [De extensie Visual Experience Composer (VEC) gebruiken](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html)
   * [De Visual Experience Composer gebruiken](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html)
   * [De Form-Based Experience Composer gebruiken](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html)
   * [Gericht op ervaring maken](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html)

## Beperking flikkering toevoegen

Bepaal voordat u begint of er een extra oplossing voor flikkering nodig is, afhankelijk van de manier waarop de tagbibliotheek is geladen.

>[!NOTE]
>
>Deze zelfstudie gebruikt de [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html) die een asynchrone implementatie van tags en flikkermitigatie heeft. Deze sectie is voor verwijzing om te begrijpen hoe de het flikkeren matiging met het Web SDK van het Platform werkt.


### Asynchrone implementatie

Wanneer een tagbibliotheek asynchroon wordt geladen, is de rendering van de pagina mogelijk voltooid voordat door Target een inhoudswisseling is uitgevoerd. Dit gedrag kan leiden tot wat &quot;flikkering&quot;wordt genoemd waar de standaardinhoud kort toont alvorens door de gepersonaliseerde inhoud wordt vervangen die door Doel wordt gespecificeerd. Als u deze flikkering wilt vermijden, raadt Adobe u aan een speciaal vooraf verborgen fragment toe te voegen vlak voor de asynchrone code voor het insluiten van tags.

Dit fragment is al aanwezig op de Luma-site, maar laten we eens nader kijken om te begrijpen wat deze code doet:

```html
<script>
  !function(e,a,n,t){var i=e.head;if(i){
  if (a) return;
  var o=e.createElement("style");
  o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
  (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
</script>
```

Het vooraf verborgen fragment maakt een stijltag in de kop van de pagina met de CSS-definitie van uw keuze. Deze stijlmarkering wordt verwijderd wanneer een reactie van Doel wordt ontvangen, of de onderbreking wordt bereikt.

Het gedrag voor het voorverbergen wordt bepaald door twee configuraties helemaal aan het einde van het fragment.

* `body { opacity: 0 !important }` geeft de CSS-definitie aan die moet worden gebruikt voor de voorverbergen totdat Doel wordt geladen. Standaard is de hele pagina verborgen. U kunt deze definitie bijwerken naar de kiezers die u wilt voorverbergen en naar de manier waarop u deze wilt verbergen. U kunt meerdere definities opnemen, aangezien deze waarde eenvoudig is wat wordt ingevoegd in de stijl die u vooraf verbergt. Als u een gemakkelijk identificeerbaar containerelement hebt dat de inhoud onder uw navigatie verpakt, kunt u deze instelling gebruiken om het vooraf verbergen tot dat containerelement te beperken.
* `3000` geeft de time-out op in milliseconden voor het voorverbergen. Als een reactie van Target niet vóór de time-out wordt ontvangen, wordt de stijltag die voor de gebeurtenis werd verborgen, verwijderd. Het bereiken van deze time-out moet zeldzaam zijn.

>[!NOTE]
>
>Het pre-verbergende fragment voor het Web SDK van het Platform is lichtjes verschillend van dat gebruikt met het Doel at.js bibliotheek. Ben zeker om het correcte fragment voor het Web SDK van het Platform te gebruiken aangezien het een verschillende stijlidentiteitskaart van gebruikt `alloy-prehiding`. Als het voorverborgen fragment voor at.js wordt gebruikt, werkt het mogelijk niet correct.

Het voorverborgen fragment is ook beschikbaar binnen tags:

1. Ga naar de **[!UICONTROL Extensies]** sectie van tags
1. Selecteren **[!UICONTROL Configureren]** voor de Adobe Experience Platform Web SDK-extensie
1. Selecteer **[!UICONTROL Voorverberg-fragment kopiëren naar klembord]** knop

   ![Doel voor vooraf verbergen van fragment voor asynchrone implementaties](assets/target-flicker-async.png)

   >[!NOTE]
   >
   >Het standaard pre-verbergende die fragment van de uitbreiding van SDK van het Web van het Platform wordt gekopieerd kan een CSS definitie omvatten die niet op uw plaats, zoals bestaat `.personalization-container { opacity: 0 !important }`. Controleer en wijzig het vooraf verborgen fragment op de juiste wijze voor uw site.

### Synchrone implementatie

Adobe raadt u aan tags asynchroon te implementeren, zoals wordt aangetoond op de Luminasite. Als de tagbibliotheek echter synchroon wordt geladen, is het vooraf verborgen fragment niet vereist. In plaats daarvan, wordt de pre-verbergende stijl gespecificeerd in de de uitbreidingsmontages van SDK van het Web van het Platform.

De pre-verbergende stijl voor synchrone implementaties kan als volgt worden gevormd:

1. Ga naar de **[!UICONTROL Extensies]** sectie van tags
1. Selecteer **[!UICONTROL Configureren]** knoop voor de uitbreiding van SDK van het Web van het Platform
1. Selecteer **[!UICONTROL Stijl vóór verbergen bewerken]** knop

   ![Doel voor vooraf verbergen van fragment voor asynchrone implementaties](assets/target-flicker-sync.png)

1. Wijzig CSS om de selecteurs te omvatten en methodes te verbergen u, bijvoorbeeld zou willen gebruiken: `body { opacity: 0 !important }` als u de hele hoofdtekst van de pagina wilt voorverbergen.
1. Uw wijzigingen opslaan en bouwen naar een bibliotheek

>[!NOTE]
>
>De vooraf verborgen stijlinstelling is alleen bedoeld voor synchrone implementaties. Deze stijl moet leeg zijn of er moet commentaar op worden toegevoegd als u een asynchrone implementatie van tags gebruikt.

Voor meer informatie over hoe de Platform Web SDK flikkering kan beheren, kunt u naar de geleidingssectie verwijzen: [flikkering beheren voor persoonlijke ervaringen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/manage-flicker.html).


## De gegevensstroom configureren

Het doel moet in de gegevensstroomconfiguratie worden toegelaten alvorens om het even welke activiteiten van het Doel door het Web SDK van het Platform kunnen worden geleverd.

Om Doel in de gegevensstroom te vormen:

1. Ga naar [Gegevensverzameling](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Selecteer in de linkernavigatie de optie **[!UICONTROL DataStreams]**
1. Selecteer de eerder gemaakte `Luma Web SDK` datastream

   ![Selecteer de Luma Web SDK-gegevensstroom](assets/datastream-luma-web-sdk.png)

1. Selecteren **[!UICONTROL Service toevoegen]**

   ![Een service toevoegen aan de gegevensstroom](assets/target-datastream-addService.png)
1. Selecteren **[!UICONTROL Adobe Target]** als de **[!UICONTROL Service]**
1. Voer desgewenst de optionele details over uw doelimplementatie in volgens de onderstaande richtlijnen.
1. Selecteren **[!UICONTROL Opslaan]**

   ![Doelconfiguratie gegevensstroom](assets/target-datastream.png)

### Eigenschappentoken

Klanten van Target Premium hebben de mogelijkheid om gebruikersmachtigingen te beheren met eigenschappen. Met de doeleigenschappen kunt u grenzen vaststellen waar gebruikers doelactiviteiten kunnen uitvoeren. Zie de [Bedrijfsmachtigingen](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html) in de documentatie van Target voor meer informatie.

Als u eigenschapstokens wilt instellen of zoeken, navigeert u naar **Adobe Target** > **[!UICONTROL Beheer]** > **[!UICONTROL Eigenschappen]**. De `</>` geeft de implementatiecode weer. De `at_property` value is het eigenschapstoken dat u in uw datastream zou gebruiken.

![Eigenschap-token doel](assets/target-admin-properties.png)

>[!NOTE]
>
>Per datastream kan slechts één eigenschapstoken worden opgegeven.


### Id van doelomgeving

[Omgevingen](https://experienceleague.adobe.com/docs/target/using/administer/environments.html) in Target Help kunt u uw implementatie in alle ontwikkelingsstadia beheren. Deze optionele instelling geeft aan welke doelomgeving u voor elke gegevensstroom wilt gebruiken.

Adobe raadt u aan de id van de doelomgeving voor elk van uw ontwikkelings-, staging- en productiegegevensstreams anders in te stellen om de zaken eenvoudig te houden.

Navigeer naar Omgeving-id&#39;s om deze in te stellen of te zoeken **Adobe Target** > **[!UICONTROL Beheer]** > **[!UICONTROL Omgevingen]**.

![Doelomgevingen](assets/target-admin-environments.png)

>[!NOTE]
>
>Als geen identiteitskaart van het Milieu van het Doel wordt gespecificeerd, dan wordt het milieu van het productieDoel verondersteld.

### Doelnaamruimte voor id van derden

Met deze optionele instelling kunt u opgeven welk identiteitssymbool moet worden gebruikt voor de doel-id van derden. Doel ondersteunt alleen profielsynchronisatie op één identiteitssymbool of naamruimte. Voor meer informatie kunt u naar de [Real-Time profielsynchronisatie voor mbox3rdPartyId](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/3rd-party-id.html) van de doelhandleiding.

De identiteitssymbolen staan in de lijst met identiteiten onder **Gegevensverzameling** > **[!UICONTROL Klant]** > **[!UICONTROL Identiteiten]**.

![Identiteitslijst](assets/target-identities.png)

In deze zelfstudie gebruikt u de site Luma en gebruikt u het identiteitssymbool `lumaCrmId` opstelling tijdens de les over [Identiteiten](configure-identities.md).


## Besluiten over visuele personalisatie renderen

Eerst, zou u de terminologie moeten begrijpen die in het Doel wordt gebruikt en etiketteert interfaces.

* **Activiteit**: Een reeks ervaringen voor een of meer doelgroepen. Een eenvoudige A/B-test kan bijvoorbeeld een activiteit zijn met twee ervaringen.
* **Ervaring**: Een reeks acties die op één of meerdere plaatsen, of besluitvormingswerkingsgebied worden gericht.
* **Beslissingsbereik**: Een locatie waar een doelervaring wordt geleverd. Beslissingsbereik is gelijk aan &quot;box&quot; als u bekend bent met oudere versies van Target.
* **Personeelsbesluit**: Een handeling die de server bepaalt, moet worden toegepast. Deze beslissingen kunnen gebaseerd zijn op publiekscriteria en prioritering van doelactiviteiten.
* **Voorstel**: Het resultaat van besluiten die door de server worden genomen die in de reactie van SDK van het Web van het Platform worden geleverd. Bijvoorbeeld, zou het ruilen van een bannerbeeld een voorstel zijn.

### De regel voor het laden van de pagina bijwerken

De visuele verpersoonlijkingsbesluiten van Doel worden geleverd door het Web SDK van het Platform, als het Doel in de datastream wordt toegelaten. Maar _ze worden niet automatisch gerenderd_. U moet de algemene regel voor het laden van pagina&#39;s wijzigen om automatische rendering in te schakelen.

1. In de [Gegevensverzameling](https://experience.adobe.com/#/data-collection){target="blank"} interface, open het markeringsbezit u voor dit leerprogramma gebruikt
1. Open de `all pages - library load - AA & AT` regel
1. Selecteer `Adobe Experience Platform Web SDK - Send event` action
1. Inschakelen **[!UICONTROL Besluiten over visuele personalisatie renderen]** met het selectievakje

   ![Renderen van beslissingen over visuele personalisatie inschakelen](assets/target-rule-enable-visual-decisions.png)

1. Uw wijzigingen opslaan en vervolgens samenstellen in uw bibliotheek

Renderen visuele verpersoonlijkingsbesluiten die tot het Web SDK van het Platform automatisch om het even welke wijzigingen toepassen die gebruikend Composer van de Ervaring van het Doel Visuele of &quot;globale mbox&quot;werden gespecificeerd.

>[!NOTE]
>
>De [!UICONTROL Besluiten over visuele personalisatie renderen] Deze instelling mag alleen worden ingeschakeld voor één verzendactie per volledige paginalading. Als deze instelling is ingeschakeld voor meerdere Send Event-acties, worden daaropvolgende renderaanvragen genegeerd.

Als u deze beslissingen liever zelf rendert of activeert met behulp van aangepaste code, kunt u de optie [!UICONTROL Besluiten over visuele personalisatie renderen] instellen uitgeschakeld. De SDK van het Web van het Platform is flexibel en verstrekt dit vermogen om u volledige controle te geven. U kunt de handleiding raadplegen voor meer informatie over [handmatig gepersonaliseerde inhoud renderen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html).

### Opstelling een activiteit van het Doel met Visuele Composer van de Ervaring

Nu het basisgedeelte van de implementatie volledig is, creeer een Ervaring richtend (XT) activiteit in Doel om te bevestigen dat alles correct werkt. U kunt de zelfstudie Doel raadplegen voor [het creëren van Ervaring richt activiteiten](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html) als u hulp nodig hebt.

>[!NOTE]
>
>Als u Google Chrome als browser gebruikt, wordt [Helperextensie Visual Experience Composer (VEC)](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html?lang=en) is vereist om de site correct te laden voor bewerking in de VEC.

1. Naar doel navigeren
1. Een &#39;Experience Targeting&#39;-activiteit maken met de Luma-homepage voor de activiteit-URL

   ![Nieuwe XT-activiteit maken](assets/target-xt-create-activity.png)

1. De pagina wijzigen, bijvoorbeeld de tekst op de homepagebanner wijzigen

   ![Doel VEC-wijziging](assets/target-xt-vec-modification.png)

1. Kies Adobe Analytics als rapporteringsbron met de aangewezen rapportreeks en de metrische Orden als doel

   >[!NOTE]
   >
   >Als u Adobe Analytics niet gebruikt, selecteert u Doel als rapportbron en kiest u een andere maatstaf, bijvoorbeeld **Betrokkenheid > Paginaweergaven** in plaats daarvan. Een doel metrisch wordt vereist om de activiteit te bewaren en voor te vertonen.

1. De activiteit opslaan
1. Als u op de hoogte bent van uw wijzigingen, kunt u uw activiteit activeren. Als u de ervaring wilt voorvertonen zonder deze te activeren, kunt u de opdracht [URL kwaliteitscontrole](https://experienceleague.adobe.com/docs/target/using/activities/activity-qa/activity-qa.html).
1. Laad de startpagina van de luminantie en u ziet dat de wijzigingen zijn toegepast
1. Na een paar uur, zou u de activiteitsgegevens en omzettingen van het Doel in Adobe Analytics moeten kunnen zien. Raadpleeg de doelgids voor meer informatie over [Analyses voor doelrapportage (A4T)](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/reporting.html?lang=en).



### Valideren met Foutopsporing

Als u een activiteit instelt, wordt de inhoud weergegeven op de pagina. Nochtans zelfs als geen activiteiten levend zijn, kunt u de Send het netwerkvraag van de Gebeurtenis ook bekijken om te bevestigen dat het Doel behoorlijk wordt gevormd.

>[!CAUTION]
>
>Als u Google Chrome gebruikt en de [Helperextensie Visual Experience Composer (VEC)](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/vec-helper-browser-extension.html?lang=en) geïnstalleerd, zorg ervoor de **Doelbibliotheken injecteren** instellen is uitgeschakeld. Als u deze instelling inschakelt, worden er extra aanvragen voor het doel ingediend.

1. De Adobe Experience Platform Debugger-browserextensie openen
1. Ga naar de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) en gebruik foutopsporing om [schakelen van de markeringseigenschap op de site naar uw eigen ontwikkeleigenschap](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)
1. De pagina opnieuw laden
1. Selecteer **[!UICONTROL Netwerk]** in de foutopsporing
1. Filteren op **[!UICONTROL Adobe Experience Platform Web SDK]**
1. Selecteer de waarde in de gebeurtenisrij voor de eerste aanroep

   ![Netwerkaanroep in Adobe Experience Platform Debugger](assets/target-debugger-network.png)

1. Er zijn toetsen onder `query` > `personalization` en  `decisionScopes` heeft een waarde van `__view__`. Dit bereik is gelijk aan het &#39;global mbox&#39; van Target. Deze vraag van SDK van het Web van Platform verzocht om besluiten van Doel.

   ![__weergave__ DecisionScope-verzoek](assets/target-debugger-view-scope.png)

1. Sluit de bedekking en selecteer de gebeurtenisdetails voor de tweede netwerkvraag. Deze vraag is slechts aanwezig als het Doel een activiteit terugkeerde.
1. U ziet dat er details zijn over de activiteit en ervaring die door Target zijn geretourneerd. Deze vraag van SDK van het Web van Platform verzendt een bericht dat een activiteit van het Doel aan de gebruiker werd teruggegeven en verhoogt een indruk.

   ![Weergave doelactiviteit](assets/target-debugger-activity-impression.png)

## Een aangepast beslissingsbereik instellen en maken

Het besluitvormingswerkingsgebied van de douane (vroeger genoemd geworden &quot;mboxes&quot;) kan worden gebruikt om HTML of inhoud JSON op een gestructureerde manier te leveren gebruikend de Vorm-Gebaseerde Composer van de Ervaring van het Doel. De inhoud die aan één van deze douanewerkingsgebied wordt geleverd wordt niet automatisch teruggegeven door het Web SDK van het Platform.

### Een bereik toevoegen aan de regel voor het laden van de pagina

Wijzig de regel voor het laden van de pagina om een aangepast beslissingsbereik toe te voegen:

1. Open de `all pages - library load - AA & AT` regel
1. Selecteer `Adobe Experience Platform Web SDK - Send Event` action
1. Voeg een of meer bereiken toe die u wilt gebruiken. In dit voorbeeld kunt u `homepage-hero`.

   ![Aangepast bereik](assets/target-rule-custom-scope.png)

1. Uw wijzigingen opslaan en samenstellen in uw bibliotheek

>[!TIP]
>
>In deze zelfstudie gebruikt u één handmatig gedefinieerd bereik voor demonstratiedoeleinden. Als u besluit om verscheidene besluitvormingswerkingsgebied te gebruiken dat voor specifieke pagina&#39;s bedoeld is, dan zou u moeten overwegen gebruikend een gegevenselement dat een serie van werkingsgebied afhankelijk van de paginappad voorwaardelijk terugkeert. Deze benadering helpt uw implementatie eenvoudig en schaalbaar te houden.

### De reactie van Doel verwerken

Nu u SDK van het Web van het Platform hebt gevormd om inhoud voor te verzoeken `homepage-hero` bereik, moet je iets doen met het antwoord. De de markeringsuitbreiding van SDK van het Web van het Platform verstrekt een [!UICONTROL Gebeurtenis verzenden voltooid] gebeurtenis die kan worden gebruikt om onmiddellijk een nieuwe regel te activeren wanneer een reactie van een [!UICONTROL Gebeurtenis verzenden] actie ontvangen.

1. Een aangeroepen regel maken `homepage - send event complete - render homepage-hero`.
1. Voeg een gebeurtenis aan de regel toe. Gebruik de **Adobe Experience Platform Web SDK** en de **[!UICONTROL Gebeurtenis verzenden voltooid]** gebeurtenistype.
1. Voeg een voorwaarde toe om de regel tot de homepage van Luma (weg zonder vraagkoordgelijken te beperken) `/content/luma/us/en.html`).
1. Voeg een handeling aan de regel toe. Gebruik de **Kern** uitbreiding en **Aangepaste code** actietype.

   ![Herdenkingsregel homepage weergeven](assets/target-rule-render-hero.png)

   >[!TIP]
   >
   >Geef uw regelgebeurtenissen, -voorwaarden en -handelingen beschrijvende namen in plaats van de standaardnamen te gebruiken. De robuuste namen van de regelcomponent maken de onderzoeksresultaten veel nuttiger.

1. Ga douanecode in om te lezen en actie op de voorstellen te doen die van de reactie van SDK van het Web van het Platform zijn teruggekeerd. De aangepaste code in dit voorbeeld gebruikt de aanpak die in de handleiding wordt beschreven voor [handmatig gepersonaliseerde inhoud renderen](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html?lang=en#manually-rendering-content). De code is aangepast voor de `homepage-hero` voorbeeldbereik met behulp van een handeling van de tagregel.

   ```javascript
   var propositions = event.propositions;
   
   var heroProposition;
   if (propositions) {
      // Find the hero proposition, if it exists.
      for (var i = 0; i < propositions.length; i++) {
         var proposition = propositions[i];
         if (proposition.scope === "homepage-hero") {
            heroProposition = proposition;
            break;
         }
      }
   }
   
   var heroHtml;
   if (heroProposition) {
      // Find the item from proposition that should be rendered.
      // Rather than assuming there a single item that has HTML
      // content, find the first item whose schema indicates
      // it contains HTML content.
      for (var j = 0; j < heroProposition.items.length; j++) {
         var heroPropositionItem = heroProposition.items[j];
         if (heroPropositionItem.schema === "https://ns.adobe.com/personalization/html-content-item") {
            heroHtml = heroPropositionItem.data.content;
            break;
         }
      }
   }
   
   if (heroHtml) {
      // Hero HTML exists. Time to render it.
      var heroElement = document.querySelector(".heroimage");
      heroElement.innerHTML = heroHtml;
      // For this example, we assume there is only a signle place to update in the HTML.
   }
   
   // Send a "display" event 
   alloy("sendEvent", {
      xdm: {
         eventType: "propositionDisplay",
         _experience: {
            decisioning: {
               propositions: [
                  {
                     id: heroProposition.id,
                     scope: heroProposition.scope,
                     scopeDetails: heroProposition.scopeDetails
                  }
               ]
            }
         }
      }
   });
   ```

1. Uw wijzigingen opslaan en samenstellen in uw bibliotheek
1. Laad de Luminantiepagina een paar keer, wat voldoende zou moeten zijn om de nieuwe pagina te maken `homepage-hero` register van het beslissingswerkingsgebied in de interface van het Doel.

### Een doelactiviteit instellen met de Form-based Experience Composer

Nu u een regel hebt om een gebied van de douanebeslissing manueel terug te geven, kunt u een andere Ervaring creëren richtend (XT) activiteit in Doel. Dit keer gebruikt u de Form-Based Experience Composer.

1. Openen [Adobe Target](https://experience.adobe.com/target)
1. De activiteit deactiveren die voor de vorige les wordt gebruikt
1. Een Experience Targeting-activiteit (XT) maken met de optie Form-based Experience Composer

   ![Nieuwe XT-activiteit maken](assets/target-xt-create-form-activity.png)

1. Selecteer **`homepage-hero`** locatie in het vervolgkeuzemenu voor de locatie en **[!UICONTROL HTML-voorstel maken]** in het vervolgkeuzemenu Inhoud. Als de locatie niet beschikbaar is, kunt u deze typen. Het doel vult periodiek nieuwe plaatsnamen na het ontvangen van verzoeken voor die plaats of werkingsgebied.

   ![Nieuwe XT-activiteit maken](assets/target-xt-form-activity.png)

1. Plak de volgende code in het inhoudsvak. Deze code is een standaardhoofdbanner met een andere achtergrondafbeelding:

   ```html
   <div class="we-HeroImage jumbotron" style="background-image: url('/content/luma/us/en/women/_jcr_content/root/hero_image.coreimg.jpeg');">
      <div class="container cq-dd-image">
         <div class="we-HeroImage-wrapper">
            <p class="h3">New Luma Yoga Collection</p>
            <strong class="we-HeroImage-title h1">Be active with style&nbsp;</strong>
            <p>
               <a class="btn btn-primary btn-action" href="/content/luma/us/en/products.html" role="button">Shop Now</a>
            </p>
         </div>
      </div>
   </div>
   ```

1. Op de [!UICONTROL Doelstellingen en instellingen] kiest u Adobe Target als bron voor de rapportage en [!UICONTROL Betrokkenheid] > [!UICONTROL Paginaweergaven] als doel
1. De activiteit opslaan
1. Als u op de hoogte bent van uw wijzigingen, kunt u uw activiteit activeren. Als u de ervaring wilt voorvertonen zonder deze te activeren, kunt u de opdracht [URL kwaliteitscontrole](https://experienceleague.adobe.com/docs/target/using/activities/activity-qa/activity-qa.html).
1. Laad de startpagina van de luminantie en u ziet dat de wijzigingen zijn toegepast

>[!NOTE]
>
>Het doel van de conversie &#39;Aangeklikt op mbox&#39; werkt niet automatisch. Omdat het Web SDK van het Platform niet automatisch douanewerkingsgebied teruggeeft, volgt het geen kliks aan plaatsen u verkiest om de inhoud toe te passen. U kunt uw eigen klik het volgen voor elk werkingsgebied tot stand brengen gebruikend &quot;klik&quot; `eventType` met toepassing van `_experience` details die `sendEvent` handeling.

### Valideren met Foutopsporing

Als u uw activiteit hebt geactiveerd, wordt de inhoud weergegeven op de pagina. Maar zelfs als er geen activiteiten actief zijn, kunt u ook kijken naar de [!UICONTROL Gebeurtenis verzenden] netwerkvraag om te bevestigen dat het Doel inhoud voor uw douanewerkingsgebied verzoekt.

1. De Adobe Experience Platform Debugger-browserextensie openen
1. Ga naar de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) en gebruik foutopsporing om [schakelen van de markeringseigenschap op de site naar uw eigen ontwikkeleigenschap](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)
1. De pagina opnieuw laden
1. Selecteer **[!UICONTROL Netwerk]** in de foutopsporing
1. Filteren op **[!UICONTROL Adobe Experience Platform Web SDK]**
1. Selecteer de waarde in de gebeurtenisrij voor de eerste aanroep

   ![Netwerkaanroep in Adobe Experience Platform Debugger](assets/target-debugger-network.png)

1. Er zijn toetsen onder `query` > `personalization` en  `decisionScopes` heeft een waarde van `__view__` zoals voorheen , maar nu is er ook een `homepage-hero` toepassingsgebied opgenomen. Deze vraag van SDK van het Web van Platform verzocht om besluiten van Doel voor veranderingen die worden aangebracht gebruikend VEC en specifiek `homepage-hero` locatie.

   ![__weergave__ DecisionScope-verzoek](assets/target-debugger-view-scope.png)

1. Sluit de bedekking en selecteer de gebeurtenisdetails voor de tweede netwerkvraag. Deze vraag is slechts aanwezig als het Doel een activiteit terugkeerde.
1. U ziet dat er details zijn over de activiteit en ervaring die door Target zijn geretourneerd. Deze vraag van SDK van het Web van Platform verzendt een bericht dat een activiteit van het Doel aan de gebruiker werd teruggegeven en verhoogt een indruk.

   ![Weergave doelactiviteit](assets/target-debugger-activity-impression.png)

## Extra gegevens aan doel doorgeven

In deze sectie, zult u specifiek doel-specifieke gegevens overgaan en een dichtere blik nemen bij hoe de gegevens XDM aan de parameters van het Doel in kaart worden gebracht.

Er zijn enkele gegevenspunten die nuttig kunnen zijn voor Doel en die niet zijn toegewezen vanuit het XDM-object. Deze speciale doelparameters omvatten:

* [Profielkenmerken](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/methods/in-page-profile-attributes.html?lang=en)
* [Kenmerken Recommendations-entiteit](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html?lang=en)
* [Voor Recommendations gereserveerde parameters](https://experienceleague.adobe.com/docs/target/using/recommendations/plan-implement.html?lang=en#pass-behavioral)
* Categoriewaarden voor [categorie-affiniteit](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/category-affinity.html?lang=en)

### Gegevenselementen maken voor doelparameters

Eerst stelt u een aantal extra gegevenselementen in voor een profielkenmerk, entiteitskenmerk, categoriewaarde en vervolgens stelt u het `data` object dat wordt gebruikt om niet-XDM-gegevens door te geven:

* **`target.entity.id`** toegewezen aan `digitalData.product.0.productInfo.sku`
* **`target.entity.name`** toegewezen aan `digitalData.product.0.productInfo.title`
* **`target.user.categoryId`** door de volgende aangepaste code te gebruiken om de site-URL voor de categorie op hoofdniveau te parseren:

   ```javascript
   var cat = location.pathname.split(/[/.]+/);
   if (cat[5] == 'products') {
      return (cat[6]);
   } else if (cat[5] != 'html') { 
      return (cat[5]);
   }
   ```

* **`data.content`** de volgende aangepaste code gebruiken:

   ```javascript
   var data = {
      __adobe: {
         target: {
            "entity.id": _satellite.getVar("target.entity.id"),
            "entity.name": _satellite.getVar("target.entity.name"),
            "profile.loggedIn": _satellite.getVar("user.profile.attributes.loggedIn"),
            "user.categoryId": _satellite.getVar("target.user.categoryId")
         }
      }
   }
   return data;
   ```

### De regel voor het laden van de pagina bijwerken

Als u aanvullende gegevens voor Doel buiten het XDM-object wilt doorgeven, moet u alle toepasselijke regels bijwerken. In dit voorbeeld hoeft u alleen de nieuwe **data.content** gegevenselement aan de generische de regel van de paginading en de meningsregel van de productpagina.

1. Open de `all pages - library load - AA & AT` regel
1. Selecteer `Adobe Experience Platform Web SDK - Send event` action
1. Voeg de `data.content` gegevenselement naar het veld Gegevens

   ![Doelgegevens aan regel toevoegen](assets/target-rule-data.png)

1. Uw wijzigingen opslaan en samenstellen in uw bibliotheek
1. Herhaal stap 1 tot en met 4 voor de **productweergave - laden bibliotheek - AA** regel

>[!NOTE]
>
>In het bovenstaande voorbeeld wordt een `data` -object dat niet op alle paginatypen volledig is ingevuld. Deze situatie wordt op de juiste wijze afgehandeld door labels en er worden sleutels weggelaten met een ongedefinieerde waarde. Bijvoorbeeld: `entity.id` en `entity.name` niet op pagina&#39;s worden doorgestuurd, behalve op productdetails.

### Valideren met foutopsporing

Nu de regels worden bijgewerkt, kunt u bevestigen als het gegeven correct gebruikend Debugger van de Adobe wordt overgegaan.

1. Ga naar de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) en aanmelden met de e-mail `test@adobe.com` en wachtwoord `test`
1. Naar de pagina met productdetails gaan
1. Open de browserextensie van Adobe Experience Platform Debugger en [schakel de eigenschap tag over naar uw eigen ontwikkeleigenschap](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)
1. De pagina opnieuw laden
1. Selecteer **Netwerk** in Foutopsporing en filteren op **Adobe Experience Platform Web SDK**
1. Selecteer de waarde in de gebeurtenisrij voor de eerste aanroep
1. Er zijn toetsen onder `data` > `__adobe` > `target` en worden ze gevuld met informatie over het product, de categorie en de aanmeldingsstatus.

   ![__weergave__ DecisionScope-verzoek](assets/target-debugger-data.png)

### Valideren in de interface van het Doel

Daarna, kijk in de interface van het Doel om te bevestigen dat de gegevens werden ontvangen en beschikbaar om in publiek en activiteiten te gebruiken zijn. XDM-gegevens worden automatisch toegewezen aan aangepaste doelparameters. U kunt controleren of XDM-gegevens door Target zijn ontvangen en beschikbaar zijn door een publiek te maken.

1. Openen [Adobe Target](https://experience.adobe.com/target)
1. Ga naar de **[!UICONTROL Soorten publiek]** sectie
1. Maak een publiek en kies de optie **[!UICONTROL Aangepast]** kenmerktype
1. Zoeken in **[!UICONTROL Parameter]** veld voor `web`. In het vervolgkeuzemenu moeten alle XDM-velden worden ingevuld die betrekking hebben op de details van de webpagina.

Controleer vervolgens of het kenmerk voor het profiel van de aanmeldingsstatus is geslaagd.

1. Kies de optie **[!UICONTROL Bezoekerprofiel]** kenmerktype
1. Zoeken naar `loggedIn`. Als het kenmerk beschikbaar is in het vervolgkeuzemenu, wordt het kenmerk op de juiste wijze aan Doel doorgegeven. Het kan enkele minuten duren voordat nieuwe kenmerken beschikbaar zijn in de doelinterface.

Als u Target Premium hebt, kunt u ook controleren of de eenheidgegevens correct zijn doorgegeven en de productgegevens naar de Recommendations-productcatalogus zijn geschreven.

1. Ga naar de **[!UICONTROL Recommendations]** sectie
1. Selecteren **[!UICONTROL Catalogus zoeken]** links navigeren
1. Zoek naar product SKU of productnaam u eerder op de plaats van de Luma bezocht. Het product moet worden weergegeven in de productcatalogus. Het kan enige minuten duren voordat nieuwe producten doorzoekbaar zijn in de Recommendations-productcatalogus.

Nu u deze les hebt voltooid zou u een werkende implementatie van Adobe Target moeten hebben gebruikend het Web SDK van het Platform.

[Volgende: ](setup-consent.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

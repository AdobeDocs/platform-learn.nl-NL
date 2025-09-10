---
title: Een XDM-schema maken voor Platform Mobile SDK-implementaties
description: Leer hoe u een XDM-schema maakt voor mobiele toepassingsgebeurtenissen.
feature: Mobile SDK,Schemas
jira: KT-14624
exl-id: c6b0d030-437a-4afe-b7d5-5a7831877983
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 1%

---

# Een XDM-schema maken

Leer hoe u een XDM-schema maakt voor mobiele toepassingsgebeurtenissen.

Standaardisering en interoperabiliteit zijn de belangrijkste concepten achter Adobe Experience Platform. Het Model van Gegevens van de ervaring (XDM), dat door Adobe wordt gedreven, is een inspanning om de gegevens van de klantenervaring te standaardiseren en schema&#39;s voor het beheer van de klantenervaring te bepalen.

## Wat zijn XDM-schema&#39;s?

XDM is een openbaar gedocumenteerde specificatie die wordt ontworpen om de macht van digitale ervaringen te verbeteren. Het verstrekt gemeenschappelijke structuren en definities die om het even welke toepassing toestaan om met de diensten van het Platform te communiceren. Door zich aan de normen van XDM te houden, kunnen alle gegevens van de klantenervaring in een gemeenschappelijke vertegenwoordiging worden opgenomen die inzichten op een snellere, meer geïntegreerde manier kan leveren. U krijgt waardevolle inzichten van klantenacties, bepaalt klantenpubliek door segmenten, en gebruikt klantenattributen voor verpersoonlijkingsdoeleinden.

Experience Platform gebruikt schema&#39;s om de gegevensstructuur op een consistente en herbruikbare manier te beschrijven. Door gegevens consistent in verschillende systemen te definiëren, wordt het eenvoudiger om betekenis te behouden en zo waarde te verkrijgen van gegevens.

Voordat gegevens in Platform kunnen worden opgenomen, moet een schema worden samengesteld om de gegevensstructuur te beschrijven en beperkingen te bieden aan het type gegevens dat binnen elk veld kan worden opgenomen. De schema&#39;s bestaan uit een basisklasse en nul of meer groepen van het schemagebied.

Voor meer informatie over het model van de schemacompositie, met inbegrip van ontwerpprincipes, en beste praktijken, zie de [ grondbeginselen van schemacompositie ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/composition) of playlist [ Model Uw Gegevens van de Ervaring van de Klant met XDM ](https://experienceleague.adobe.com/nl/playlists/experience-platform-model-your-customer-experience-data-with-xdm).

>[!TIP]
>
>Als u met de Verwijzing van het Ontwerp van de Oplossing van de Analyse vertrouwd bent (SDRs), kunt u aan een schema als robuustere SDR denken. Zie [ creëren en handhaven een Document van het Ontwerp van de Oplossing van de Verwijzing (SDR) ](https://experienceleague.adobe.com/nl/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr) voor meer informatie.

## Vereisten

U moet toestemming hebben om een Experience Platform-schema te maken om de les te voltooien.

## Leerdoelstellingen

In deze les zult u:

* Een schema maken in de interface voor gegevensverzameling
* Een standaardveldgroep toevoegen aan het schema
* Een aangepaste veldgroep maken en aan het schema toevoegen

## Naar schema&#39;s navigeren

1. Log in bij de Adobe Experience Cloud.

1. Zorg ervoor dat u zich in de Experience Platform-sandbox bevindt die u voor deze zelfstudie gebruikt.

1. Open app schakelaar ![ Schakelaar van de App ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) (bij het hoogste recht),

1. Selecteer **[!UICONTROL Data Collection]** in het menu.

   ![ Login aan Experience Cloud ](assets/experiencecloud-login.png){zoomable="yes"}

   >[!NOTE]
   >
   > Klanten van platformgebaseerde toepassingen zoals Real-Time CDP dienen een ontwikkelingssandbox te gebruiken voor deze zelfstudie. Andere klanten gebruiken de standaardproductiestandaard.


1. Selecteer ![ Schema&#39;s ](/help/assets/icons/Schemas.svg) **[!UICONTROL Schemas]** onder **[!UICONTROL Data management]** in het linkerspoor.

   ![ markeringen huisscherm ](assets/mobile-schema-navigate.png){zoomable="yes"}

U bevindt zich nu op de pagina met hoofdschema&#39;s en krijgt een lijst met bestaande schema&#39;s te zien. U kunt ook tabbladen zien die overeenkomen met de kernelementen van een schema:

* **de groepen van het Gebied** zijn herbruikbare componenten die één of meerdere gebieden bepalen om specifieke gegevens, zoals persoonlijke details, hotelvoorkeur, of adres te vangen.
* **de Klassen** bepalen de gedragsaspecten van de gegevens die het schema bevat. `XDM ExperienceEvent` legt bijvoorbeeld tijdreeksen, gebeurtenisgegevens vast en `XDM Individual Profile` legt kenmerkgegevens over een individu vast.
* **de types van Gegevens** worden gebruikt als types van verwijzingsgebied in klassen of gebiedsgroepen op de zelfde manier zoals fundamentele letterlijke gebieden.

De bovenstaande beschrijvingen zijn een overzicht op hoog niveau. Voor meer details, zie de [ bouwstenen van het Schema ](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorials/schemas/schema-building-blocks) video of lees [ Grondbeginselen van schemacompositie ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/composition) in de productdocumentatie.

In deze zelfstudie gebruikt u de vervolgkeuzelijst Consumer Experience Event en maakt u een aangepaste les om het proces aan te tonen.

>[!NOTE]
>
>Adobe blijft meer standaardveldgroepen toevoegen en deze moeten waar mogelijk worden gebruikt. Deze gebieden worden impliciet begrepen door de diensten van Experience Platform en verstrekken grotere consistentie wanneer gebruikt over de componenten van het Platform. Het gebruik van standaardveldgroepen biedt tastbare voordelen, zoals automatische toewijzing in Analytics en AI-functies in Platform.

## Luma-toepassingsschemaarchitectuur

In een echt scenario, zou het proces van het schemaontwerp als dit kunnen kijken:

* Verzamel bedrijfsvereisten.
* Vooraf samengestelde veldgroepen zoeken die zoveel mogelijk vereisten dekken.
* Maak aangepaste veldgroepen voor eventuele tussenruimten.

Voor leerdoeleinden gebruikt u vooraf gebouwde en aangepaste veldgroepen.

* **de Gebeurtenis van de Ervaring van de Consument**: Prebuilt gebiedsgroep die vele gemeenschappelijke gebieden heeft.
* **de Informatie van de Toepassing**: De het gebiedsgroep van de douane die wordt ontworpen om concepten TrackState/TrackAction te simuleren analyseert.

<!--Later in the tutorial, you can [update the schema](lifecycle-data.md) to include the **[!UICONTROL AEP Mobile Lifecycle Details]** field group.-->

## Een schema maken

1. Selecteer ![ AddCircle ](/help/assets/icons/AddCircle.svg) **[!UICONTROL Create Schema]**.

1. Selecteer **[!UICONTROL Create a schema]** in het dialoogvenster **[!UICONTROL Manual]** . Gebruik **[!UICONTROL Select]** om door te gaan.

   ![ handboek van het Schema ](assets/schema-manual.png){zoomable="yes"}

1. Selecteer **[!UICONTROL Select a class]** onder **[!UICONTROL Create schema]** in de stap **[!UICONTROL Experience Event]** van de wizard **[!UICONTROL Select a base class for this schema]** .

1. Selecteer **[!UICONTROL Next]**.

   ![ de basisklasse van de Tovenaar van 0&rbrace; Schema](assets/schema-wizard-base-class.png){zoomable="yes"}

1. Voer in de stap **[!UICONTROL Name and review]** van de wizard **[!UICONTROL Create schema]** een **[!UICONTROL Schema display name]** in, bijvoorbeeld `Luma Mobile Event Schema` en een [!UICONTROL Description] , bijvoorbeeld `Schema for Luma mobile app experience events` .

   >[!NOTE]
   >
   >Als u deze zelfstudie doorloopt met meerdere personen in één sandbox of als u een gedeelde account gebruikt, kunt u overwegen een identificatie toe te voegen of vooraf in te stellen als onderdeel van uw naamgevingsconventies. Gebruik bijvoorbeeld `Luma Mobile App Event Schema` in plaats van `Luma Mobile App Event Schema - Joe Smith` . Zie ook de nota in [ Overzicht ](overview.md).

1. Selecteer **[!UICONTROL Finish]** om de wizard te voltooien.

   ![ naam en overzicht van het Schema ](assets/schema-wizard-name-and-review.png){zoomable="yes"}


1. Selecteer ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **toevoegen** naast **[!UICONTROL Field groups]**.

   ![ voeg gebiedsgroep ](assets/add-field-group.png){zoomable="yes"} toe

1. Zoeken naar `Consumer Experience Event` .

1. Selecteer ![ Voorproef ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Preview_18_N.svg) om de gebieden te voorproef en/of de beschrijving voor meer details te lezen alvorens een gebiedsgroep te selecteren.

1. Selecteer **de Gebeurtenis van de Consumentenervaring**.

1. Selecteer **[!UICONTROL Add field groups]**.

   ![ Selecterend gebiedsgroep ](assets/schema-select-field-groups.png){zoomable="yes"}

   U wordt teruggebracht naar het hoofdscherm van de schemacompositie waar u alle beschikbare gebieden kunt zien.

1. Selecteer **[!UICONTROL Save]**.
1. Selecteer ![ Schema&#39;s ](/help/assets/icons/Schemas.svg) **[!UICONTROL Schemas]** onder **[!UICONTROL Data management]** om aan de belangrijkste **[!UICONTROL Schemas]** interface terug te keren.

>[!NOTE]
>
>Houd er rekening mee dat u niet alle velden in een groep hoeft te gebruiken. U kunt ook velden verwijderen om het schema beknopt en begrijpelijk te houden. Als het nuttig is, kunt u aan een schema als lege gegevenslaag denken. In uw app vult u de relevante waarden op het juiste moment in.

De veldgroep [!UICONTROL Consumer Experience Event] heeft een gegevenstype met de naam [!UICONTROL Web information] , dat gebeurtenissen zoals paginaweergave en koppelingsklikken beschrijft. Op het moment van schrijven is er geen pariteit voor mobiele apps aan deze functie, dus gaat u uw eigen functie maken.

## Een aangepast gegevenstype maken


Eerst maakt u een aangepast gegevenstype waarin de twee gebeurtenissen worden beschreven:

* Schermweergave
* Toepassingsinteractie

1. Selecteer het tabblad **[!UICONTROL Data types]**. 

1. Selecteer **[!UICONTROL Create data type]**.

   ![ Selecterend gegevenstype menu ](assets/schema-datatype-create.png){zoomable="yes"}

1. Geef een **[!UICONTROL Display name]** en **[!UICONTROL Description]** op, bijvoorbeeld `App Information` en `Custom data type describing "Screen Views" & "App Actions"`

   ![ verstrekkend naam &amp; beschrijving ](assets/schema-datatype-name.png){zoomable="yes"}

   >[!TIP]
   >
   > Gebruik altijd leesbare, beschrijvende [!UICONTROL display names] voor uw aangepaste velden. Deze praktijk maakt douanevelden toegankelijker voor marketers wanneer de gebieden in de stroomafwaartse diensten zoals de segmentbouwer weggaan.


1. Om een gebied toe te voegen, selecteer ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knoop.


1. Dit veld is een containerobject voor toepassingsinteractie, dus geef een kamelcase **[!UICONTROL Field name]** `appInteraction` , **[!UICONTROL Display name]** `App Interaction` op en selecteer `Object` in de lijst **[!UICONTROL Type]** .

1. Selecteer **[!UICONTROL Apply]**.

   ![ Toevoegend nieuwe gebeurtenis van de toepassingsactie ](assets/schema-datatype-app-action.png){zoomable="yes"}

1. Om te meten hoe vaak een actie is voorgekomen, voeg een gebied toe door ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knoop naast het **[!UICONTROL appInteraction]** voorwerp te selecteren u creeerde.

1. Geef het een kamelenhoofdletter **[!UICONTROL Field name]** `appAction` , **[!UICONTROL Display name]** van `App Action` en **[!UICONTROL Type]** `Measure` .

   Deze stap zou het equivalent zijn van een succesgebeurtenis in Adobe Analytics.

1. Selecteer **[!UICONTROL Apply]**.

   ![ Toevoegend het gebied van de actienaam ](assets/schema-datatype-action-name.png){zoomable="yes"}

1. Voeg een gebied toe beschrijvend het type van interactie door ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knoop naast het **[!UICONTROL appInteraction]** voorwerp te selecteren.

1. Geef deze de waarde **[!UICONTROL Field name]** `name` , **[!UICONTROL Display name]** van `Name` en **[!UICONTROL Type]** `String` .

   Deze stap is het equivalent van een dimensie in Adobe Analytics.

   ![ het Selecteren is van toepassing ](assets/schema-datatype-apply.png){zoomable="yes"}

1. Blader naar de onderkant van de rechtertrack en selecteer **[!UICONTROL Apply]** .

1. Als u een `appStateDetails` -object wilt maken dat een **[!UICONTROL Measure]** veld met de naam `screenView` en twee **[!UICONTROL String]** velden met de naam `screenName` en `screenType` bevat, voert u dezelfde stappen uit als bij het maken van het **[!UICONTROL appInteraction]** -object.

1. Selecteer **[!UICONTROL Save]**.

   ![ Definitieve staat van gegevenstype ](assets/schema-datatype-final.png){zoomable="yes"}

## Een aangepaste veldgroep toevoegen

Voeg nu een aangepaste veldgroep toe met behulp van het aangepaste gegevenstype:

1. Open het schema dat u eerder in deze les creeerde.

1. Selecteer ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** naast **[!UICONTROL Field groups]**.

   ![ Toevoegend nieuwe gebiedsgroep ](assets/schema-fieldgroup-add.png){zoomable="yes"}

1. Selecteer **[!UICONTROL Create new field group]**.

1. Geef een **[!UICONTROL Display name]** en **[!UICONTROL Description]** op, bijvoorbeeld `App Interactions` en `Fields for app interactions` .

1. Selecteer **toevoegen gebiedsgroepen**.

   ![ verstrekkend naam &amp; beschrijving ](assets/schema-fieldgroup-name.png){zoomable="yes"}

1. Van het belangrijkste samenstellingsscherm, uitgezochte **&#x200B; [!UICONTROL App Interactions**].

1. Voeg een gebied aan de wortel van het schema toe door ![ plus ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knoop naast de schemanaam te selecteren.

1. Geef in de rechtertrack een **[!UICONTROL Field name]** van `appInformation` , een **[!UICONTROL Display name]** van `App Information` en een **[!UICONTROL Type]** van `App Information` op.

1. Selecteer **[!UICONTROL App Interactions]** in de vervolgkeuzelijst **[!UICONTROL Field Group]** om de velden toe te wijzen aan uw nieuwe veldgroep.

1. Selecteer **[!UICONTROL Apply]**.

1. Selecteer **[!UICONTROL Save]**.

   ![ het Selecteren is van toepassing ](assets/schema-fieldgroup-apply.png){zoomable="yes"}

>[!NOTE]
>
>Aangepaste veldgroepen worden altijd onder de Experience Cloud Org-id geplaatst.


>[!SUCCESS]
>
>U hebt nu een schema voor de rest van de zelfstudie te gebruiken.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[creeer a[!UICONTROL datastream]](create-datastream.md)**

---
title: Een XDM-schema maken voor de implementatie van Platform Mobile SDK
description: Leer hoe u een XDM-schema maakt voor mobiele toepassingsgebeurtenissen.
feature: Mobile SDK,Schemas
jira: KT-14624
exl-id: c6b0d030-437a-4afe-b7d5-5a7831877983
source-git-commit: 25f0df2ea09bb7383f45a698e75bd31be7541754
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 0%

---

# Een XDM-schema maken

Leer hoe u een XDM-schema maakt voor mobiele toepassingsgebeurtenissen.

Standaardisering en interoperabiliteit zijn de belangrijkste concepten achter Adobe Experience Platform. Het Model van Gegevens van de ervaring (XDM), die door Adobe wordt gedreven, is een inspanning om de gegevens van de klantenervaring te standaardiseren en schema&#39;s voor het beheer van de klantenervaring te bepalen.

## Wat zijn XDM-schema&#39;s?

XDM is een openbaar gedocumenteerde specificatie die wordt ontworpen om de macht van digitale ervaringen te verbeteren. Het verstrekt gemeenschappelijke structuren en definities die om het even welke toepassing toestaan om met de diensten van het Platform te communiceren. Door zich aan de normen van XDM te houden, kunnen alle gegevens van de klantenervaring in een gemeenschappelijke vertegenwoordiging worden opgenomen die inzichten op een snellere, meer geïntegreerde manier kan leveren. U krijgt waardevolle inzichten van klantenacties, bepaalt klantenpubliek door segmenten, en gebruikt klantenattributen voor verpersoonlijkingsdoeleinden.

Het Experience Platform gebruikt schema&#39;s om de structuur van gegevens op een verenigbare en herbruikbare manier te beschrijven. Door gegevens consistent in verschillende systemen te definiëren, wordt het eenvoudiger om betekenis te behouden en zo waarde te verkrijgen van gegevens.

Voordat gegevens in Platform kunnen worden opgenomen, moet een schema worden samengesteld om de gegevensstructuur te beschrijven en beperkingen te bieden aan het type gegevens dat binnen elk veld kan worden opgenomen. De schema&#39;s bestaan uit een basisklasse en nul of meer groepen van het schemagebied.

Voor meer informatie over het model van de schemacompositie, met inbegrip van ontwerpprincipes, en beste praktijken, zie [grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en) of de cursus [Uw klantgegevens modelleren met XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm).

>[!TIP]
>
>Als u met de Verwijzing van het Ontwerp van de Oplossing van de Analyse vertrouwd bent (SDRs), kunt u aan een schema als robuustere SDR denken. Zie [Creeer en handhaaf een Document van de Verwijzing van het Ontwerp van de Oplossing (SDR)](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr.html?lang=en) voor meer informatie .

## Vereisten

Om de les te voltooien, moet u toestemming hebben om een schema van het Experience Platform tot stand te brengen.

## Leerdoelstellingen

In deze les zult u:

* Een schema maken in de interface voor gegevensverzameling
* Een standaardveldgroep toevoegen aan het schema
* Een aangepaste veldgroep maken en aan het schema toevoegen

## Naar schema&#39;s navigeren

1. Log in bij de Adobe Experience Cloud.

1. Zorg ervoor dat u zich in de sandbox Experience Platform bevindt die u voor deze zelfstudie gebruikt.

1. App-schakeloptie openen ![App Switcher](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg)  (rechtsboven),

1. Selecteren **[!UICONTROL Gegevensverzameling]** in het menu.

   ![Aanmelden bij Experience Cloud](assets/experiencecloud-login.png)

   >[!NOTE]
   >
   > Klanten van platformgebaseerde toepassingen zoals Real-Time CDP dienen een ontwikkelingssandbox te gebruiken voor deze zelfstudie. Andere klanten gebruiken de standaardproductiestandaard.


1. Selecteren **[!UICONTROL Schemas]** krachtens **[!UICONTROL Gegevensbeheer]** in het linkerspoor.

   ![tags home screen](assets/mobile-schema-navigate.png)

U bevindt zich nu op de pagina met hoofdschema&#39;s en krijgt een lijst met bestaande schema&#39;s te zien. U kunt ook tabbladen zien die overeenkomen met de kernelementen van een schema:

* **Veldgroepen** zijn herbruikbare componenten die een of meer velden definiëren voor het vastleggen van specifieke gegevens, zoals persoonlijke gegevens, hotelvoorkeuren of adres.
* **Klassen** definieert de gedragsaspecten van de gegevens die het schema bevat. Bijvoorbeeld: `XDM ExperienceEvent` legt tijdreeksen, gebeurtenisgegevens en `XDM Individual Profile` vangt kenmerkgegevens over een individu.
* **Gegevenstypen** worden op dezelfde manier als letterlijke basisvelden gebruikt als referentieveldtypen in klassen of veldgroepen.

De bovenstaande beschrijvingen zijn een overzicht op hoog niveau. Zie voor meer informatie de [Bouwstenen voor schema](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/schema-building-blocks.html) video of lezen [Basisbeginselen van de schemacompositie](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en) in de productdocumentatie.

In deze zelfstudie gebruikt u de vervolgkeuzelijst Consumer Experience Event en maakt u een aangepaste les om het proces aan te tonen.

>[!NOTE]
>
>De Adobe blijft meer standaardveldgroepen toevoegen en zij zouden waar mogelijk moeten worden gebruikt aangezien deze gebieden impliciet door de diensten van het Experience Platform worden begrepen en grotere consistentie verstrekken wanneer gebruikt over de componenten van het Platform. Het gebruik van standaardveldgroepen biedt tastbare voordelen, zoals automatische toewijzing in Analytics en AI-functies in Platform.

## Luma-toepassingsschemaarchitectuur

In een echt scenario, zou het proces van het schemaontwerp als dit kunnen kijken:

* Verzamel bedrijfsvereisten.
* Vooraf samengestelde veldgroepen zoeken die zoveel mogelijk vereisten dekken.
* Maak aangepaste veldgroepen voor eventuele tussenruimten.

Voor leerdoeleinden gebruikt u vooraf gebouwde en aangepaste veldgroepen.

* **Consumentenervaringsgebeurtenis**: Geïntegreerde veldgroep met veel voorkomende velden.
* **Toepassingsgegevens**: De veldgroep van de douane wordt ontworpen om concepten te simuleren TrackState/TrackAction Analytics die.

<!--Later in the tutorial, you can [update the schema](lifecycle-data.md) to include the **[!UICONTROL AEP Mobile Lifecycle Details]** field group.-->

## Een schema maken

1. Selecteren **[!UICONTROL Schema maken]**.

1. In de **[!UICONTROL Een klasse selecteren]** van de **[!UICONTROL Schema maken]** wizard, selecteert u **[!UICONTROL Experience Event]** ondergronds **[!UICONTROL Selecteer een basisklasse voor dit schema]**.

1. Selecteren **[!UICONTROL Volgende]**.

   ![Basisklasse Schema Wizard](assets/schema-wizard-base-class.png)

1. In de **[!UICONTROL Naam en revisie]** van de **[!UICONTROL Schema maken]** wizard, voert u een **[!UICONTROL Weergavenaam schema]** bijvoorbeeld `Luma Mobile Event Schema` en [!UICONTROL Beschrijving]bijvoorbeeld `Schema for Luma mobile app experience events`.

   >[!NOTE]
   >
   >Als u deze zelfstudie doorloopt met meerdere personen in één sandbox of als u een gedeelde account gebruikt, kunt u overwegen een identificatie toe te voegen of vooraf in te stellen als onderdeel van uw naamgevingsconventies. In plaats van `Luma Mobile App Event Schema`, gebruik `Luma Mobile App Event Schema - Joe Smith`. Zie ook de opmerking in [Overzicht](overview.md).

1. Selecteren **[!UICONTROL Voltooien]** om de wizard te voltooien.

   ![Naam schema en revisie](assets/schema-wizard-name-and-review.png)


1. Selecteren ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Toevoegen** naast **[!UICONTROL Veldgroepen]**.

   ![Veldgroep toevoegen](assets/add-field-group.png)

1. Zoeken naar `Consumer Experience Event`.

1. Selecteren ![Voorvertoning](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Preview_18_N.svg) om een voorvertoning van de velden weer te geven en/of de beschrijving voor meer informatie te lezen voordat u een veldgroep selecteert.

1. Selecteren **Consumentenervaringsgebeurtenis**.

1. Selecteren **[!UICONTROL Veldgroepen toevoegen]**.

   ![Veldgroep selecteren](assets/schema-select-field-groups.png)

   U wordt teruggebracht naar het hoofdscherm van de schemacompositie waar u alle beschikbare gebieden kunt zien.

1. Selecteren **[!UICONTROL Opslaan]**.

>[!NOTE]
>
>Houd er rekening mee dat u niet alle velden in een groep hoeft te gebruiken. U kunt ook velden verwijderen om het schema beknopt en begrijpelijk te houden. Als het nuttig is, kunt u aan een schema als lege gegevenslaag denken. In uw app vult u de relevante waarden op het juiste moment in.

De [!UICONTROL Consumentenervaringsgebeurtenis] veldgroep heeft een gegevenstype genaamd [!UICONTROL Webinformatie], waarin gebeurtenissen zoals paginaweergave en koppelingsklikken worden beschreven. Op het moment van schrijven is er geen pariteit voor mobiele apps aan deze functie, dus gaat u uw eigen functie maken.

## Een aangepast gegevenstype maken

Eerst maakt u een aangepast gegevenstype waarin de twee gebeurtenissen worden beschreven:

* Schermweergave
* Toepassingsinteractie

1. Selecteer de **[!UICONTROL Gegevenstypen]** tab.

1. Selecteren **[!UICONTROL Gegevenstype maken]**.

   ![Het menu Gegevenstype selecteren](assets/schema-datatype-create.png)

1. Geef een **[!UICONTROL Weergavenaam]** en **[!UICONTROL Beschrijving]** bijvoorbeeld `App Information` en `Custom data type describing "Screen Views" & "App Actions"`

   ![Naam en beschrijving opgeven](assets/schema-datatype-name.png)

   >[!TIP]
   >
   > Altijd leesbaar, beschrijvend gebruiken [!UICONTROL weergavenamen] voor uw douanegebieden, aangezien deze praktijk hen toegankelijker voor marketers maakt wanneer de gebieden in de stroomafwaartse diensten zoals de segmentbouwer overstijgen.


1. Als u een veld wilt toevoegen, selecteert u de ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) knop.


1. Dit veld is een containerobject voor toepassingsinteractie, dus een kamelcase **[!UICONTROL Veldnaam]** `appInteraction`, **[!UICONTROL Weergavenaam]** `App Interaction`en selecteert u `Object` van de **[!UICONTROL Type]** lijst.

1. Selecteren **[!UICONTROL Toepassen]**.

   ![Nieuwe gebeurtenis voor app-actie toevoegen](assets/schema-datatype-app-action.png)

1. Als u wilt meten hoe vaak een actie is uitgevoerd, voegt u een veld toe door de ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast de knop **[!UICONTROL appInteraction]** door u gemaakt object.

1. Geef het een kamelentcase **[!UICONTROL Veldnaam]** `appAction`, **[!UICONTROL Weergavenaam]** van `App Action` en **[!UICONTROL Type]** `Measure`.

   Deze stap zou het equivalent zijn van een succesgebeurtenis in Adobe Analytics.

1. Selecteren **[!UICONTROL Toepassen]**.

   ![Veld voor handelingnaam toevoegen](assets/schema-datatype-action-name.png)

1. Voeg een gebied toe beschrijvend het type van interactie door te selecteren ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast de knop **[!UICONTROL appInteraction]** object.

1. Geef het een **[!UICONTROL Veldnaam]** `name`, **[!UICONTROL Weergavenaam]** van `Name` en **[!UICONTROL Type]** `String`.

   Deze stap is het equivalent van een dimensie in Adobe Analytics.

   ![Selecteren toepassen](assets/schema-datatype-apply.png)

1. Schuif naar de onderkant van de rechterrail en selecteer **[!UICONTROL Toepassen]**.

1. Om een `appStateDetails` object dat een **[!UICONTROL Meetlat]** veld aangeroepen `screenView` en twee **[!UICONTROL String]** velden aangeroepen `screenName` en `screenType`Volg dezelfde stappen als bij het maken van de **[!UICONTROL appInteraction]** object.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Eindstaat van gegevenstype](assets/schema-datatype-final.png)

## Een aangepaste veldgroep toevoegen

Voeg nu een aangepaste veldgroep toe met behulp van het aangepaste gegevenstype:

1. Open het schema dat u eerder in deze les creeerde.

1. Selecteren ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** naast **[!UICONTROL Veldgroepen]**.

   ![Nieuwe veldgroep toevoegen](assets/schema-fieldgroup-add.png)

1. Selecteren **[!UICONTROL Nieuwe veldgroep maken]**.

1. Geef een **[!UICONTROL Weergavenaam]** en **[!UICONTROL Beschrijving]**, bijvoorbeeld `App Interactions` en `Fields for app interactions`.

1. Selecteren **Veldgroepen toevoegen**.

   ![Naam en beschrijving opgeven](assets/schema-fieldgroup-name.png)

1. Van het belangrijkste samenstellingsscherm, uitgezochte **[!UICONTROL Interacties met toepassingen**].

1. Voeg een gebied aan de wortel van het schema toe door te selecteren ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) naast de schemanaam.

1. Geef in de rechterspoorlijn een **[!UICONTROL Veldnaam]** van `appInformation`, **[!UICONTROL Weergavenaam]** van `App Information`en **[!UICONTROL Type]** van `App Information`.

1. Selecteren **[!UICONTROL Interacties tussen toepassingen]** van de **[!UICONTROL Veldgroep]** vervolgkeuzelijst om de velden toe te wijzen aan uw nieuwe veldgroep.

1. Selecteren **[!UICONTROL Toepassen]**.

1. Selecteren **[!UICONTROL Opslaan]**.

   ![Selecteren toepassen](assets/schema-fieldgroup-apply.png)

>[!NOTE]
>
>Aangepaste veldgroepen worden altijd onder uw Experience Cloud-Org-id geplaatst.


>[!SUCCESS]
>
>U hebt nu een schema voor de rest van de zelfstudie te gebruiken.
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Een [!UICONTROL datastream]](create-datastream.md)**

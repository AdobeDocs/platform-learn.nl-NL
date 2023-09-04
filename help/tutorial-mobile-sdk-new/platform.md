---
title: Gegevens verzenden naar Adobe Experience Platform
description: Leer hoe u gegevens naar Adobe Experience Platform verzendt.
solution: Data Collection,Experience Platform
feature: Mobile SDK,Data Ingestion
hide: true
source-git-commit: 7435a2758bdd8340416b70faf8337e33167a7193
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Gegevens verzenden naar Adobe Experience Platform

Leer hoe u gegevens naar Adobe Experience Platform verzendt.

Deze optionele les is relevant voor alle klanten van Real-time Customer Data Platform (Real-Time CDP), Journey Optimizer en Customer Journey Analytics. Experience Platform, de stichting van de producten van het Experience Cloud, is een open systeem dat al uw gegevens (Adobe en niet-Adobe) in robuuste klantenprofielen omzet. Deze profielen van klanten werken in real time bij en gebruiken AI-gedreven inzichten om u te helpen om de juiste ervaringen over elk kanaal te leveren.

De [event](events.md), [levenscyclus](lifecycle-data.md), en [identiteit](identity.md) gegevens die u in eerdere lessen hebt verzameld en naar Platform Edge Network hebt verzonden, worden doorgestuurd naar de services die in uw gegevensstroom zijn geconfigureerd, waaronder Adobe Experience Platform.


## Vereisten

Uw organisatie moet zijn voorzien en toestemmingen voor Adobe Experience Platform worden verleend.

Als u geen toegang hebt, kunt u [deze les overslaan](install-sdks.md).

## Leerdoelstellingen

In deze les zult u:

* Maak een gegevensset voor Experience Platforms.
* Valideer gegevens in de dataset.
* Laat uw schema en dataset voor het Profiel van de Klant in real time toe.
* Gegevens valideren in realtime-klantprofiel.
* Gegevens in de identiteitsgrafiek valideren.


## Een gegevensset maken

Alle gegevens die met succes in Adobe Experience Platform worden opgenomen, blijven binnen het datumpeer als datasets voortbestaan. Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens (typisch een lijst) die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan. Zie de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html) ter informatie.

1. Navigeer naar de interface Experience Platform door deze te selecteren in de toepassingen ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) in de rechterbovenhoek.


1. Selecteren **[!UICONTROL Gegevenssets]** in het navigatiemenu aan de linkerkant.

1. Selecteren ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Gegevensset maken]**.

1. Selecteren **[!UICONTROL Gegevensset maken van schema]**.
   ![gegevensbank](assets/dataset-create.png)

1. Zoek naar uw schema. bijvoorbeeld `Luma Mobile` in het zoekveld.
1. Selecteer bijvoorbeeld uw schema **[!UICONTROL Gebeurtenisschema Luma Mobile App]**.

1. Selecteren **[!UICONTROL Volgende]**.
   ![gegevensset configureren](assets/dataset-configure.png)

1. Geef een **[!UICONTROL Naam]** bijvoorbeeld `Luma Mobile App Events Dataset` en **[!UICONTROL Beschrijving]**.

1. Selecteren **[!UICONTROL Voltooien]**.
   ![gegevensset voltooien](assets/dataset-finish.png)

## De gegevensstroom bijwerken

Zodra u uw dataset hebt gecreeerd, ben zeker om [uw gegevensstroom bijwerken](create-datastream.md#adobe-experience-platform) Adobe Experience Platform toevoegen. Deze update zorgt voor gegevensstromen naar Platform.

## Gegevens in de gegevensset valideren

Nu u een dataset hebt gecreeerd en uw gegevensstroom bijgewerkt om gegevens naar Experience Platform te verzenden, worden alle gegevens XDM die naar het Netwerk van de Rand van het Platform verzenden door:sturen naar Platform en landen in de dataset.

Open de app en navigeer naar schermen waar u gebeurtenissen bijhoudt. U kunt levenscyclusmetriek ook teweegbrengen.

Open uw dataset in de interface van het Platform. U zou de gegevens moeten zien aankomend in partijen aan de dataset

![gegevensreeksen voor gegevenstransportplatform valideren](assets/platform-dataset-batches.png)

U moet ook voorbeeldrecords en velden kunnen zien met de opdracht **[!UICONTROL Gegevensset voorvertoning]** functie:
![levenscyclus valideren die naar de gegevensset Platform is verzonden](assets/lifecycle-platform-dataset.png)

Platform is een robuuster hulpmiddel voor het valideren van gegevens [queryservice](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html).

## Klantprofiel in realtime inschakelen

Het Echte Profiel van de Klant van het Experience Platform staat u toe om een holistische mening van elke individuele klant te bouwen die gegevens van veelvoudige kanalen, met inbegrip van online, off-line, CRM, en derdegegevens combineert. Het profiel staat u toe om uw ongelijke klantengegevens in een verenigde mening te consolideren die een actionable, timestamped rekening van elke klanteninteractie aanbiedt.

### Het schema inschakelen

1. Open bijvoorbeeld uw schema **[!UICONTROL Gebeurtenisschema Luma Mobile App]**.
1. Inschakelen **[!UICONTROL Profiel]**.
1. Selecteren **[!UICONTROL De gegevens voor dit schema zullen een primaire identiteit op het identityMap gebied bevatten.]** in het dialoogvenster.
1. **[!UICONTROL Opslaan]** het schema.

   ![het schema inschakelen voor profiel](assets/platform-profile-schema.png)

### De gegevensset inschakelen

1. Open uw gegevensset, bijvoorbeeld **[!UICONTROL Dataset voor Luma Mobile-toepassingsgebeurtenis]**.
1. Inschakelen **[!UICONTROL Profiel]**.

   ![de dataset voor profiel inschakelen](assets/platform-profile-dataset.png)

### Gegevens in profiel valideren

Open de app en navigeer naar schermen waar u gebeurtenissen bijhoudt, bijvoorbeeld: meld u aan bij de app Luma en schaf een aankoop.

Gebruik Verzekering om een van de identiteiten te vinden die in identityMap zijn doorgegeven (Email, lumaCrmId of ECID), bijvoorbeeld de CRM-id.

![identiteitswaarde vastleggen](assets/platform-identity.png)

In de interface van het Platform,

1. Navigeren naar **[!UICONTROL Profielen]** en selecteert u **[!UICONTROL Bladeren]** in de bovenste balk.
1. Geef de identiteitsgegevens op die u net hebt opgehaald, bijvoorbeeld `Luma CRM ID` for **[!UICONTROL Naamruimte identiteit]** en de waarde waarvoor u hebt gekopieerd **[!UICONTROL Identiteitswaarde]**. Selecteer vervolgens **[!UICONTROL Weergave]**.
1. Selecteer het profiel om details weer te geven.

![identiteitswaarde opzoeken](assets/platform-profile-lookup.png)

Op de **[!UICONTROL Detail]** scherm, kunt u basisinformatie over de gebruiker zien, met inbegrip van **[!UICONTROL ** gekoppelde identiteiten **]**:
![profieldetails](assets/platform-profile-details.png)

Op de **[!UICONTROL Gebeurtenissen]** kunt u de gebeurtenissen zien die bij uw mobiele app-implementatie voor deze gebruiker zijn verzameld:

![profielgebeurtenissen](assets/platform-profile-events.png)


Van het scherm van profieldetails:

1. Als u de identiteitsgrafiek wilt weergeven, klikt u op de koppeling of navigeert u naar **[!UICONTROL Identiteiten]** selecteert u vervolgens **[!UICONTROL Naamgrafiek]** in de bovenste balk.
1. Als u de identiteitswaarde wilt opzoeken, geeft u `Luma CRM ID` als de **[!UICONTROL Naamruimte identiteit]** en de gekopieerde waarde als de **[!UICONTROL Identiteitswaarde]**. Selecteer vervolgens **[!UICONTROL Weergave]**.

   Deze visualisatie toont u alle identiteiten die samen in een profiel en hun oorsprong verbonden zijn. Hier ziet u een voorbeeld van een identiteitsgrafiek die is samengesteld uit gegevens die zijn verzameld tijdens het voltooien van deze zelfstudie voor Mobile SDK (gegevensbron 2) en de [Zelfstudie over Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html) (Gegevensbron 1):

   ![identiteitswaarde vastleggen](assets/platform-profile-identitygraph.png)


## Volgende stappen

Marketers en analytici kunnen nog veel meer doen met gegevens die in Experience Platform zijn vastgelegd, waaronder het analyseren ervan in de Customer Journey Analytics en de bouwsegmenten in Real-time Customer Data Platform. Je bent klaar om te beginnen!


>[!SUCCESS]
>
>U hebt uw app nu zo ingesteld dat gegevens niet alleen naar het Edge-netwerk, maar ook naar Adobe Experience Platform worden verzonden.<br>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Push messaging (Push messaging) met Journey Optimizer](journey-optimizer-push.md)**

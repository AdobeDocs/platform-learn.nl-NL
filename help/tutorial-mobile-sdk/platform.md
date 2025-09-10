---
title: Gegevens verzenden naar Experience Platform met Platform Mobile SDK
description: Leer hoe u gegevens naar Experience Platform verzendt.
solution: Data Collection,Experience Platform
feature: Mobile SDK,Data Ingestion
jira: KT-14637
exl-id: fdd2c90e-8246-4d75-a6db-df3ef31946c4
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---

# Gegevens verzenden naar Experience Platform

Leer hoe u gegevens van mobiele apps naar Adobe Experience Platform verzendt.

Deze optionele les is relevant voor alle klanten van Real-Time Customer Data Platform (Real-Time CDP), Journey Optimizer en Customer Journey Analytics. Experience Platform, de basis van Experience Cloud-producten, is een open systeem dat al uw gegevens (Adobe en niet-Adobe) omzet in robuuste klantprofielen. Deze profielen van klanten werken in real time bij en gebruiken AI-gedreven inzichten om u te helpen om de juiste ervaringen over elk kanaal te leveren.

De [ gebeurtenis ](events.md), [ levenscyclus ](lifecycle-data.md), en [ identiteit ](identity.md) gegevens die u verzamelde en naar Platform Edge Network in vroegere lessen verzond wordt door:sturen aan de diensten die in uw gegevensstroom, met inbegrip van Adobe Experience Platform worden gevormd.

![Architectuur](assets/architecture-aep.png){zoomable="yes"}


## Vereisten

Uw organisatie moet zijn voorzien en toestemmingen voor Adobe Experience Platform worden verleend.

Als u geen toegang hebt, kunt u [ deze les ](install-sdks.md) overslaan.

## Leerdoelstellingen

In deze les zult u:

* Maak een Experience Platform-gegevensset.
* Configureer uw gegevensstroom om gegevens door te sturen naar Experience Platform.
* Valideer gegevens in de dataset.
* Laat uw schema en dataset voor het Profiel van de Klant in real time toe.
* Gegevens valideren in realtime-klantprofiel.
* Gegevens in de identiteitsgrafiek valideren.


## Een gegevensset maken

Alle gegevens die met succes in Adobe Experience Platform worden opgenomen, blijven binnen het datumpeer als datasets voortbestaan. Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens (typisch een lijst) die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan. Zie de [ documentatie ](https://experienceleague.adobe.com/nl/docs/experience-platform/catalog/datasets/overview) voor meer informatie.

1. Navigeer naar de gebruikersinterface van Experience Platform. Selecteer **[!UICONTROL Experience Platform]** van Apps ![ Apps ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) menu in het hoogste recht.


1. Selecteer **[!UICONTROL Datasets]** in het navigatiemenu links.

1. Selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Create dataset]**.

1. Selecteer **[!UICONTROL Create dataset from schema]**.
   ![ datasethuis ](assets/dataset-create.png){zoomable="yes"}

1. Zoek naar uw schema. bijvoorbeeld `Luma Mobile` gebruiken in het zoekveld.
1. Selecteer het schema, bijvoorbeeld **[!DNL Luma Mobile App Event Schema]** .

1. Selecteer **[!UICONTROL Next]**.
   ![ dataset vormt ](assets/dataset-configure.png){zoomable="yes"}

1. Geef een **[!UICONTROL Name]** op, bijvoorbeeld `Luma Mobile App Events Dataset` en een **[!UICONTROL Description]** .

1. Selecteer **[!UICONTROL Finish]**.
   ![ dataset eindigt ](assets/dataset-finish.png){zoomable="yes"}


## Adobe Experience Platform-datastreamservice toevoegen

Om uw gegevens XDM van Edge Network naar Adobe Experience Platform te verzenden, voeg de dienst van Adobe Experience Platform aan de datastream toe u opstelling als deel van [ creeer een datastream ](create-datastream.md).

>[!IMPORTANT]
>
>U kunt de dienst van Adobe Experience Platform slechts toelaten wanneer het hebben tot een gebeurtenisdataset geleid.

1. Selecteer **[!UICONTROL Datastreams]** en uw gegevensstroom in de gebruikersinterface voor gegevensverzameling.

1. Dan selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]**.

1. Selecteer **[!UICONTROL Adobe Experience Platform]** in de lijst [!UICONTROL Service] .

1. Schakel **[!UICONTROL Enabled]** in om de service in te schakelen.

1. Selecteer de **[!UICONTROL Event Dataset]** die u eerder hebt gemaakt, bijvoorbeeld **[!DNL Luma Mobile App Event Dataset]** .

1. Selecteer **[!UICONTROL Save]**.

   ![ voegt Adobe Experience Platform als datastreamdienst ](assets/datastream-service-aep.png){zoomable="yes"} toe
1. De uiteindelijke configuratie moet er ongeveer zo uitzien.

   ![ gegevensstroommontages ](assets/datastream-settings.png){zoomable="yes"}


## Gegevens in de gegevensset valideren

Nu u een dataset hebt gecreeerd en uw gegevensstroom bijgewerkt om gegevens naar Experience Platform te verzenden, worden alle gegevens XDM die naar Platform Edge Network worden verzonden door:sturen aan Platform en landen in de dataset.

Open de app en navigeer naar schermen waar u gebeurtenissen bijhoudt. U kunt levenscyclusmetriek ook teweegbrengen.

Open uw dataset in de interface van het Platform. U zou de gegevens moeten zien aankomend in partijen aan de dataset. De gegevens worden gewoonlijk om de 15 minuten in microbatches weergegeven, zodat u de gegevens mogelijk niet meteen ziet.

![ bevestigt gegevens die de gegevensreeksen van het Platform landen ](assets/platform-dataset-batches.png){zoomable="yes"}

U ziet ook voorbeeldrecords en velden met de functie **[!UICONTROL Preview dataset]** :
![ bevestigt levenscyclus die naar de dataset van het Platform wordt verzonden ](assets/lifecycle-platform-dataset.png){zoomable="yes"}

Een robuuster hulpmiddel om gegevens te bevestigen is de de vraagdienst van het Platform [&#128279;](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorials/queries/explore-data).

## Klantprofiel in realtime inschakelen

Met het Experience Platform-profiel voor realtime klanten kunt u een holistische weergave van elke afzonderlijke klant maken waarin gegevens van meerdere kanalen worden gecombineerd, waaronder online-, offline-, CRM- en andere gegevens. Het profiel staat u toe om uw ongelijke klantengegevens in een verenigde mening te consolideren die een actionable, timestamped rekening van elke klanteninteractie aanbiedt.

### Het schema inschakelen

1. Open uw schema, bijvoorbeeld **[!DNL Luma Mobile App Event Schema]** .
1. Schakel **[!UICONTROL Profile]** in.
1. Selecteer **[!UICONTROL Data for this schema contains a primary identity in the identityMap field.]** in het dialoogvenster.
1. **[!UICONTROL Save]** het schema.

   ![ laat het schema voor profiel ](assets/platform-profile-schema.png){zoomable="yes"} toe

### De gegevensset inschakelen

1. Open uw dataset, bijvoorbeeld **[!DNL Luma Mobile App Event Dataset]**.
1. Schakel **[!UICONTROL Profile]** in.

   ![ laat de dataset voor profiel ](assets/platform-profile-dataset.png){zoomable="yes"} toe

### Gegevens in profiel valideren

Open de app en navigeer naar schermen waar u gebeurtenissen bijhoudt, bijvoorbeeld: meld u aan bij de app Luma en schaf een aankoop.

Gebruik Assurance om een van de identiteiten te zoeken die zijn doorgegeven in de identityMap (Email, lumaCrmId of ECID), bijvoorbeeld de CRM-id.

![ greep een identiteitswaarde ](assets/platform-identity.png){zoomable="yes"}

In de interface van het Platform,

1. Navigeer naar **[!UICONTROL Profiles]** en selecteer **[!UICONTROL Browse]** in de bovenste balk.
1. Geef de identiteitsgegevens op die u net hebt opgehaald, bijvoorbeeld `Luma CRM ID` for **[!UICONTROL Identity namespace]** en de waarde die u hebt gekopieerd voor **[!UICONTROL Identity value]** . Selecteer vervolgens **[!UICONTROL View]** .
1. Selecteer het profiel om details weer te geven.

![ kijkt omhoog een identiteitswaarde ](assets/platform-profile-lookup.png){zoomable="yes"}

Op het **[!UICONTROL Detail]** scherm, kunt u basisinformatie over de gebruiker, met inbegrip van de **[!UICONTROL **&#x200B; verbonden identiteiten &#x200B;**]** zien:
![ profieldetails ](assets/platform-profile-details.png){zoomable="yes"}

In het **[!UICONTROL Events]** vindt u de gebeurtenissen die zijn verzameld in uw mobiele app-implementatie voor deze gebruiker:

![ profielgebeurtenissen ](assets/platform-profile-events.png){zoomable="yes"}


Van het scherm van profieldetails:

1. Als u de identiteitsgrafiek wilt weergeven, klikt u op de koppeling of navigeert u naar **[!UICONTROL Identities]** en selecteert u **[!UICONTROL Identity Graph]** in de bovenste balk.
1. Als u de identiteitswaarde wilt opzoeken, geeft u `Luma CRM ID` op als de **[!UICONTROL Identity namespace]** en de gekopieerde waarde als de **[!UICONTROL Identity value]** . Selecteer vervolgens **[!UICONTROL View]** .

   Deze visualisatie toont u de identiteiten die samen in een profiel en hun oorsprong verbonden zijn. Hier is een voorbeeld van een identiteitsgrafiek die van gegevens wordt geconstrueerd die van de voltooiing van zowel dit Mobiele zelfstudie van SDK (Gegevens Source 2) worden verzameld en het [ Web SDK leerprogramma ](https://experienceleague.adobe.com/nl/docs/platform-learn/implement-web-sdk/overview) (Gegevens Source 1):

   ![ greep een identiteitswaarde ](assets/platform-profile-identitygraph.png){zoomable="yes"}


## Volgende stappen

Marketers en analytici kunnen nog veel meer doen met gegevens die in Experience Platform zijn vastgelegd, waaronder het analyseren ervan in Customer Journey Analytics en het opbouwen van segmenten in Real-Time Customer Data Platform. Je bent klaar om te beginnen!


>[!SUCCESS]
>
>U hebt nu een app ingesteld om gegevens niet alleen naar de Edge Network, maar ook naar Adobe Experience Platform te verzenden.<br> Dank u voor het investeren van uw tijd in het leren over Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.
>

Volgende: **[creeer en verzend dupberichten](journey-optimizer-push.md)**

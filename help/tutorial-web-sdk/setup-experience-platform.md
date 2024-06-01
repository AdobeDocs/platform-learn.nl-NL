---
title: Gegevens streamen naar Adobe Experience Platform met Platform Web SDK
description: Leer hoe u webgegevens kunt streamen naar Adobe Experience Platform met Web SDK. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
jira: KT-15407
exl-id: 4d749ffa-e1c0-4498-9b12-12949807b369
source-git-commit: a8431137e0551d1135763138da3ca262cb4bc4ee
workflow-type: tm+mt
source-wordcount: '1994'
ht-degree: 0%

---

# Gegevens streamen naar Experience Platform met Web SDK

Leer hoe u webgegevens kunt streamen naar Adobe Experience Platform met Platform Web SDK.

Experience Platform is de ruggengraat van alle nieuwe Experience Cloud toepassingen, zoals Adobe Real-time Customer Data Platform, Adobe Customer Journey Analytics en Adobe Journey Optimizer. Deze toepassingen worden ontworpen om het Web SDK van het Platform als hun optimale methode van Webgegevensinzameling te gebruiken.

![WebSDK en Adobe Experience Platform-diagram](assets/dc-websdk-aep.png)

Experience Platform gebruikt hetzelfde XDM-schema dat u eerder hebt gemaakt om gebeurtenisgegevens van de Luma-website vast te leggen. Wanneer die gegevens naar de Edge Network van het Platform worden verzonden, kan de configuratie van de gegevensstroom het aan Experience Platform door:sturen.

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een gegevensset maken in Adobe Experience Platform
* Vorm de gegevensstroom om de gegevens van SDK van het Web naar Adobe Experience Platform te verzenden
* Streaming webgegevens inschakelen voor realtime klantprofiel
* Bevestig de gegevens zowel in de dataset van het Platform als in het Profiel van de Klant in real time zijn geland
* De gegevens van het steekproefloyaliteitsprogramma in Platform opnemen
* Een eenvoudig platformpubliek maken

## Vereisten

Om deze les te voltooien, moet u eerst:

* Toegang hebben tot een Adobe Experience Platform-toepassing zoals Real-time Customer Data Platform, Journey Optimizer of Customer Journey Analytics
* Voltooi de vroegere lessen in de Aanvankelijke secties van de Configuratie van de Configuratie en van de Markeringen van dit leerprogramma.

>[!NOTE]
>
>Als u geen toepassingen van het Platform hebt, kunt u deze les overslaan of lezen.

## Een gegevensset maken

Alle gegevens die met succes in Adobe Experience Platform worden opgenomen, blijven binnen het datumpeer als datasets voortbestaan. A [gegevensset](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview) is een opslag en beheersconstructie voor een inzameling van gegevens, typisch een lijst die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan.

Stel een gegevensset in voor uw Luma-webgebeurtenisgegevens:


1. Ga naar de [Experience Platform](https://experience.adobe.com/platform/) of [Journey Optimizer](https://experience.adobe.com/journey-optimizer/) interface
1. Bevestig dat u zich in de ontwikkelingssandbox bevindt die u voor deze zelfstudie gebruikt
1. Openen **[!UICONTROL Data Management > Datasets]** van de linkernavigatie
1. Selecteren **[!UICONTROL Create dataset]**

   ![Schema maken](assets/experience-platform-create-dataset.png)

1. Selecteer de **[!UICONTROL Create dataset from schema]** option

   ![Gegevensset maken van schema](assets/experience-platform-create-dataset-schema.png)

1. Selecteer de `Luma Web Event Data` schema gemaakt in het dialoogvenster [eerdere les](configure-schemas.md) en selecteer vervolgens **[!UICONTROL Next]**

   ![Gegevensset, schema selecteren](assets/experience-platform-create-dataset-schema-selection.png)

1. Geef een **[!UICONTROL Name]** en optioneel **[!UICONTROL Description]** voor de gegevensset. Voor deze oefening, gebruik `Luma Web Event Data`selecteert u vervolgens **[!UICONTROL Finish]**

   ![Naam gegevensset ](assets/experience-platform-create-dataset-schema-name.png)

Een dataset wordt nu gevormd beginnen gegevens van uw implementatie van SDK van het Web van het Platform te verzamelen.

## De gegevensstroom configureren

Nu kunt u uw [!UICONTROL datastream] gegevens verzenden naar [!UICONTROL Adobe Experience Platform]. De gegevensstroom is het verband tussen uw markeringsbezit, de Edge Network van het Platform, en de dataset van het Experience Platform.

1. Open de [Gegevensverzameling](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Selecteren **[!UICONTROL Datastreams]** van de linkernavigatie
1. Open de gegevensstroom die u in het dialoogvenster [Een gegevensstroom configureren](configure-datastream.md) les, `Luma Web SDK`

   ![Selecteer de Luma Web SDK-gegevensstroom](assets/datastream-luma-web-sdk-development.png)

1. Selecteren **[!UICONTROL Add Service]**
   ![Een service toevoegen aan de gegevensstroom](assets/experience-platform-addService.png)
1. Selecteren **[!UICONTROL Adobe Experience Platform]** als de **[!UICONTROL Service]**
1. Selecteren `Luma Web Event Data` als de **[!UICONTROL Event Dataset]**

1. Selecteren **[!UICONTROL Save]**.

   ![DataStream Config](assets/experience-platform-datastream-config.png)

Terwijl u verkeer op de [Luma-demo-site](https://luma.enablementadobe.com/content/luma/us/en.html) Aan uw markeringsbezit in kaart gebracht, bevolkt de gegevens de dataset in Experience Platform!

## De gegevensset valideren

Deze stap is essentieel om ervoor te zorgen dat de gegevens in de dataset zijn geland. Er zijn twee aspecten van het valideren van gegevens die naar de dataset worden verzonden.

* Valideren met [!UICONTROL Experience Platform Debugger]
* Valideren met [!UICONTROL Preview Dataset]
* Valideren met [!UICONTROL Query Service]

### Experience Platform Debugger

Deze stappen zijn min of meer hetzelfde als wat u in het dialoogvenster [Foutopsporingsles](validate-with-debugger.md). Aangezien gegevens echter alleen naar Platform worden verzonden nadat u deze in de gegevensstroom hebt ingeschakeld, moet u nog enkele voorbeeldgegevens genereren:

1. Open de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) en selecteert u de [!UICONTROL Experience Platform Debugger] extensiepictogram

1. Foutopsporing configureren om de eigenschap tag toe te wijzen aan *uw* Ontwikkelomgeving, zoals beschreven in de [Valideren met foutopsporing](validate-with-debugger.md) les

   ![Uw ontwikkelomgeving voor Starten wordt weergegeven in Foutopsporing](assets/experience-platform-debugger-dev.png)

1. Log in op de Luministensite met de referenties `test@adobe.com`/`test`

1. Terugkeren naar de [Luminantiepage](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Binnen de het netwerkbakens van SDK van het Web van het Platform die door debugger worden getoond, selecteer de &quot;gebeurtenissen&quot;rij om details in een pop-up uit te breiden

   ![Web SDK in Foutopsporing](assets/experience-platform-debugger-dev-eventType.png)

1. Zoek naar &quot;identityMap&quot;binnen pop-up. Hier moet u lumaCrmId zien met drie sleutels van authenticatedState, id en primaire
   ![Web SDK in Foutopsporing](assets/experience-platform-debugger-dev-idMap.png)

Gegevens moeten nu worden ingevuld in het dialoogvenster `Luma Web Event Data` dataset en klaar voor de bevestiging van de Dataset van de Voorproef.

### Een voorvertoning van de gegevensset weergeven

Om te bevestigen dat de gegevens in het datumpigment van Platform zijn geland, is het snel mogelijk om de **[!UICONTROL Preview dataset]** gebruiken. De gegevens van SDK van het Web zijn micro-gebatcheerd aan het gegevens meer en op periodieke basis verfrist in de interface van het Platform. Het kan 10 tot 15 minuten duren om de gegevens te zien die u hebt gegenereerd.

1. In de [Experience Platform](https://experience.adobe.com/platform/) interface, selecteren **[!UICONTROL Data Management > Datasets]** in de linkernavigatie om het dialoogvenster **[!UICONTROL Datasets]** dashboard.

   Het dashboard maakt een lijst van alle beschikbare datasets voor uw organisatie. De details worden getoond voor elke vermelde dataset, met inbegrip van zijn naam, het schema de dataset zich aan, en status van de meest recente versiereeks houdt.

1. Selecteer uw `Luma Web Event Data` dataset om zijn te openen **[!UICONTROL Dataset activity]** scherm.

   ![Webgebeurtenis DataSet Luma](assets/experience-platform-dataset-validation-lumaSDK.png)

   Het activiteitenscherm omvat een grafiek die het tarief visualiseert van berichten die worden verbruikt evenals een lijst van succesvolle en ontbroken partijen.

1. Van de **[!UICONTROL Dataset activity]** scherm, selecteren **[!UICONTROL Preview dataset]** in de rechterbovenhoek van het scherm om maximaal 100 rijen met gegevens voor te vertonen. Als de dataset leeg is, wordt de voorproefverbinding gedeactiveerd.

   ![Voorvertoning gegevensset](assets/experience-platform-dataset-preview.png)

   In het voorproefvenster, wordt de hiërarchische mening van het schema voor de dataset getoond op het recht.

   ![Dataset Voorvertoning 1](assets/experience-platform-dataset-preview-1.png)


### De gegevens opvragen

1. In de [Experience Platform](https://experience.adobe.com/platform/) interface, selecteren **[!UICONTROL Data Management > Queroes]** in de linkernavigatie om het dialoogvenster **[!UICONTROL Queries]** scherm.
1. Selecteren **[!UICONTROL Create query]**
1. Eerst, stel een vraag in werking om alle namen van de lijsten in het gegevensmeer te zien. Enter `SHOW TABLES` in de vraagredacteur en klik het playbackpictogram om de vraag in werking te stellen.
1. In de resultaten ziet u hoe de naam van de tabel eruit ziet `luma_web_event_data`
1. Vraag nu de lijst met een eenvoudige vraag die naar uw lijst van verwijzingen voorzien (merk op dat door gebrek de vraag tot 100 resultaten zal worden beperkt): `SELECT * FROM "luma_web_event_data"`
1. Na een paar ogenblikken ziet u voorbeeldrecords van uw webgegevens.

>[!ERROR]
>
>Als er een fout optreedt met de instelling &quot;Tabel niet voorzien&quot;, controleert u de naam van de tabel nogmaals. Het kan ook zijn dat de micropartij gegevens nog niet in het datumpeer is geland. Probeer het over 10-15 minuten opnieuw.

>[!INFO]
>
>  Zie voor meer informatie over de Adobe Experience Platform-queryservice [Gegevens verkennen](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/queries/explore-data) in de sectie Platform-zelfstudies.


## De dataset en het schema voor het Profiel van de Klant in real time inschakelen

Voor klanten van Real-time Customer Data Platform en Journey Optimizer, is de volgende stap de dataset en het schema voor het Profiel van de Klant in real time toe te laten. Gegevens die van SDK van het Web stromen zullen één van vele gegevensbronnen zijn die in Platform stromen en u wilt zich bij uw Webgegevens met andere gegevensbronnen aansluiten om klantenprofielen van 360 graads te bouwen. Bekijk deze korte video voor meer informatie over Real-Time Customer Profile:

>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on&captions=eng)

>[!CAUTION]
>
>Wanneer we met uw eigen website en gegevens werken, raden we u aan gegevens robuuster te valideren voordat u deze inschakelt voor het realtime-klantprofiel.


**Om de dataset toe te laten:**

1. Open de gegevensset die u hebt gemaakt, `Luma Web Event Data`

1. Selecteer de **[!UICONTROL Profile Toggle]** om het aan te zetten

   ![Profiel in-/uitschakelen](assets/setup-experience-platform-profile.png)

1. Bevestigen dat u wilt **[!UICONTROL Enable]** de dataset

   ![Schakelen tussen profielen inschakelen](assets/setup-experience-platform-profile-enable.png)

**Het schema inschakelen:**

1. Open het schema dat u hebt gemaakt, `Luma Web Event Data`

1. Selecteer de **[!UICONTROL Profile Toggle]** om het aan te zetten

   ![Profiel in-/uitschakelen](assets/setup-experience-platform-profile-schema.png)

1. Selecteren **[!UICONTROL Data for this schema will contain a primary identity in the identityMap field.]**

   >[!IMPORTANT]
   >
   >    Primaire id&#39;s zijn vereist voor elk record dat wordt verzonden naar het Real-Time Klantprofiel. Identiteitsvelden worden doorgaans gelabeld in het schema. Als u identiteitskaarten gebruikt, zijn de identiteitsvelden echter niet zichtbaar binnen het schema. In dit dialoogvenster kunt u bevestigen dat u een primaire identiteit voor ogen hebt en dat u deze in een identiteitsoverzicht opgeeft wanneer u uw gegevens verzendt. Zoals u weet, gebruikt SDK van het Web een identiteitskaart met Experience Cloud identiteitskaart (ECID) als standaard primaire identiteit en voor authentiek verklaarde identiteitskaart als primaire identiteit wanneer beschikbaar.


1. Selecteren **[!UICONTROL Enable]**

   ![Schakelen tussen profielen inschakelen](assets/setup-experience-platform-profile-schema-enable.png)

1. Selecteren **[!UICONTROL Save]** het bijgewerkte schema opslaan

Het schema is nu ook ingeschakeld voor het profiel.

>[!IMPORTANT]
>
>    Als een schema eenmaal is ingeschakeld voor Profiel, kan het niet worden uitgeschakeld of verwijderd zonder de volledige sandbox opnieuw in te stellen of te verwijderen. Ook kunnen velden na dit punt niet uit het schema worden verwijderd.
>
>   
> Als u met uw eigen gegevens werkt, is het raadzaam de volgende handelingen uit te voeren:
> 
> * Eerst, ga sommige gegevens in uw datasets in.
> * Oplossen van problemen die zich tijdens het invoeren van gegevens voordoen (bijvoorbeeld problemen met gegevensvalidatie of -toewijzing).
> * Uw gegevenssets en schema&#39;s voor profiel inschakelen
> * Voer de gegevens opnieuw in, indien nodig


### Een profiel valideren

U kunt een klantprofiel opzoeken in de interface Platform (of Journey Optimizer-interface) om te bevestigen dat de gegevens zijn geland in het Real-Time Klantprofiel. Zoals de naam suggereert, bevolken de profielen in real time, zodat is er geen vertraging zoals met het bevestigen van gegevens in de dataset.

Eerst moet u meer voorbeeldgegevens genereren. Herhaal de stappen uit eerdere versies in deze les om u aan te melden bij de Luma-website wanneer deze is toegewezen aan uw tag-eigenschap. Inspect het verzoek van SDK van het Web van het Platform om ervoor te zorgen het gegevens met verzendt `lumaCRMId`.

1. In de [Experience Platform](https://experience.adobe.com/platform/) interface, selecteren **[!UICONTROL Customer]** > **[!UICONTROL Profiles]** in de linkernavigatie

1. Als de **[!UICONTROL Identity namespace]** gebruiken `lumaCRMId`
1. De waarde van de opdracht kopiëren en plakken `lumaCRMId` overgegaan in de vraag die u in Debugger van het Experience Platform inspecteerde, in dit geval `112ca06ed53d3db37e4cea49cc45b71e`.

   ![Profiel](assets/experience-platform-validate-dataset-profile.png)

1. Als het profiel een geldige waarde bevat voor `lumaCRMId`, vult een profiel-id in de console:

   ![Profiel](assets/experience-platform-validate-dataset-profile-set.png)

1. Als u de volledige **[!UICONTROL Customer Profile]** Selecteer voor elke id de optie **[!UICONTROL Profile ID]** in het hoofdvenster.

   >[!NOTE]
   >
   >U kunt de hyperlink van de profiel-id selecteren of als u de rij selecteert, wordt een rechts menu geopend waarin u de hyperlink Profiel-id kunt selecteren
   > ![Klantprofiel](assets/experience-platform-select-profileId.png)

   Hier kunt u alle identiteiten zien verbonden aan `lumaCRMId`, zoals de `ECID`.

   ![Klantprofiel](assets/experience-platform-validate-dataset-custProfile.png)

U hebt nu Platform Web SDK voor Experience Platform ingeschakeld (En Real-Time CDP! En Journey Optimizer! En Customer Journey Analytics!).

### Een kwaliteitsschema maken en voorbeeldgegevens invoeren

Deze exercitie zal naar verwachting worden voltooid voor klanten van Real-time Customer Data Platform en Journey Optimizer.

Wanneer de gegevens van SDK van het Web in Adobe Experience Platform worden opgenomen, kan het door andere gegevensbronnen worden verrijkt u in Platform hebt ingebed. Bijvoorbeeld, wanneer een gebruiker zich bij de plaats van de Luma aanmeldt, wordt een identiteitsgrafiek gebouwd in Experience Platform en alle andere profiel-toegelaten datasets kunnen potentieel samen worden samengevoegd om de Profielen van de Klant in real time te bouwen. Om dit in actie te zien, creeer snel een andere dataset in Adobe Experience Platform met wat gegevens van de steekproefloyaliteit zodat u de Profielen van de Klant in real time met Real-time Customer Data Platform en Journey Optimizer kunt gebruiken. Aangezien u reeds soortgelijke oefeningen hebt uitgevoerd, zullen de instructies kort zijn.

Maak het loyaliteitsschema:

1. Een nieuw schema maken
1. Kies **[!UICONTROL Individual Profile]** als de [!UICONTROL base class]
1. Geef het schema een naam `Luma Loyalty Schema`
1. Voeg de [!UICONTROL Loyalty Details] veldgroep
1. Voeg de [!UICONTROL Demographic Details] veldgroep
1. Selecteer de `Person ID` veld en markeren als een [!UICONTROL Identity] en [!UICONTROL Primary identity] met de `Luma CRM Id` [!UICONTROL Identity namespace].
1. Het schema inschakelen voor [!UICONTROL Profile]. Als u de schakeloptie Profiel niet kunt vinden, klikt u op de schemanaam linksboven.
1. Het schema opslaan

   ![Loyaliteitsschema](assets/web-channel-loyalty-schema.png)

Om de dataset tot stand te brengen en de steekproefgegevens in te gaan:

1. Maak een nieuwe dataset van de `Luma Loyalty Schema`
1. De gegevensset een naam geven `Luma Loyalty Dataset`
1. De gegevensset inschakelen voor [!UICONTROL Profile]
1. Het voorbeeldbestand downloaden [luma-loyalty-forWeb.json](assets/luma-loyalty-forWeb.json)
1. Sleep het bestand naar uw gegevensset en zet het neer
1. Bevestig dat de gegevens correct zijn ingevoerd

   ![Loyaliteitsschema](assets/web-channel-loyalty-dataset.png)

### Een publiek maken

Groepprofielen van soorten publiek worden gecombineerd rond algemene kenmerken. Bouw een snel publiek u in uw Webcampagne kunt gebruiken:

1. Ga in de interface Experience Platform of Journey Optimizer naar **[!UICONTROL Customer]** > **[!UICONTROL Audiences]** in de linkernavigatie
1. Selecteren **[!UICONTROL Create audience]**
1. Selecteren **[!UICONTROL Build rule]**
1. Selecteren **[!UICONTROL Create]**

   ![Een publiek maken](assets/web-campaign-create-audience.png)

1. Selecteren **[!UICONTROL Attributes]**
1. Zoek de **[!UICONTROL Loyalty]** > **[!UICONTROL Tier]** en sleep het naar het **[!UICONTROL Attributes]** sectie
1. Het publiek definiëren als gebruikers van wie `tier` is `gold`
1. Naam van het publiek `Luma Loyalty Rewards – Gold Status`
1. Selecteren **[!UICONTROL Edge]** als de **[!UICONTROL Evaluation method]**
1. Selecteren **[!UICONTROL Save]**

   ![Het publiek definiëren](assets/web-campaign-define-audience.png)

Aangezien dit een zeer eenvoudig publiek is, kunnen wij de de evaluatiemethode van de Rand gebruiken. Het publiek van de rand evalueert op de rand, zodat in het zelfde verzoek dat door SDK van het Web aan de Edge Network van het Platform wordt gemaakt, kunnen wij de publieksdefinitie evalueren en onmiddellijk bevestigen als de gebruiker zal kwalificeren.


[Volgende: ](setup-analytics.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)

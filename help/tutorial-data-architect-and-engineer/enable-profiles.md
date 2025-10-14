---
title: Klantprofielen in realtime inschakelen
seo-title: Enable Real-Time Customer Profiles | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Klantprofielen in realtime inschakelen
description: In deze les, zult u uw schema's en datasets voor het Profiel van de Klant in real time toelaten.
role: Data Architect
feature: Profiles
jira: KT-4348
thumbnail: 4348-enable-profiles.jpg
exl-id: b05f1af1-a599-42f2-8546-77453a578b92
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# Klantprofielen in realtime inschakelen

<!-- 15min-->
In deze les, zult u uw schema&#39;s en datasets voor het Profiel van de Klant in real time toelaten.

Oké, ik heb gelogen toen ik zei dat de datasetles de kortste les in dit leerprogramma was—dit zou nog minder tijd moeten vergen! Letterlijk is het enige wat je gaat doen, een heleboel knevels omdraaien. Maar wat gebeurt wanneer u deze knevels omdraait is _echt_ belangrijk zodat wilde ik een volledige pagina aan het wijden.

Met het Profiel van de Klant in real time, kunt u een holistische mening van elke individuele klant zien die gegevens van veelvoudige kanalen, met inbegrip van online, off-line, CRM, en derdegegevens combineert. Het profiel staat u toe om uw ongelijke klantengegevens in een verenigde mening te consolideren die een actionable, timestamped rekening van elke klanteninteractie aanbiedt.

Zo verbazend zoals al dat klinkt, te hoeven u niet om *elk van uw gegevens* voor profiel te activeren. In feite, zou u slechts de gegevens moeten toelaten u voor activeringsgebruiksgevallen nodig hebt. Laat gegevens toe die u voor de gevallen van het marketinggebruik wilt gebruiken, vraag centrumintegratie, etc., waar u snelle toegang tot een robuust klantenprofiel nodig hebt. Als u gegevens alleen uploadt voor analyse, moet dit waarschijnlijk niet worden ingeschakeld voor profiel.

Er zijn belangrijke [&#x200B; garanties voor de gegevens van het Profiel van de Klant in real time &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL) die u zou moeten herzien wanneer het beslissen welke van uw eigen gegevens u voor profiel zou moeten toelaten.

<!--is this accurate. Are there other considerations to point out? -->

**Architecten van Gegevens** zullen het Profiel van de Klant in real time buiten dit leerprogramma moeten toelaten.

Voordat u met de oefeningen begint, bekijkt u deze korte video voor meer informatie over Real-Time Klantprofiel:
>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on&enablevpops)

## Vereiste machtigingen

In [&#x200B; vorm toestemmingen &#x200B;](configure-permissions.md) les, u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.


<!--* Permission items **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Schema&#39;s inschakelen voor realtime klantprofiel met behulp van de gebruikersinterface van het platform

Laten we beginnen met de eenvoudige taak om een schema in te schakelen:

1. In het gebruikersinterface van het Platform, open het **Schema van het Loyalty van de Luma**
1. In **[!UICONTROL Schema Properties]**, knevel de **schakelaar van het Profiel**
1. Druk in het bevestigingsmodaal op de knop **[!UICONTROL Enable]** om te bevestigen
1. Selecteer de knop **[!UICONTROL Save]** om uw wijzigingen op te slaan

   >[!IMPORTANT]
   >
   >Als een schema eenmaal is ingeschakeld voor Profiel, kan het niet worden uitgeschakeld of verwijderd. Ook kunnen velden na dit punt niet uit het schema worden verwijderd. Deze implicaties zijn belangrijk om later in mening te houden wanneer u met uw eigen gegevens in uw milieu van de Productie werkt. In deze zelfstudie moet u een ontwikkelingssandbox gebruiken die u op elk gewenst moment kunt verwijderen.
   >
   >In het gecontroleerde milieu van dit leerprogramma, zult u uw schema&#39;s en datasets voor profiel toelaten, _alvorens om het even welke gegevens_ in te voeren. Als u met uw eigen gegevens werkt, is het raadzaam de volgende handelingen uit te voeren:
   >
   > 1. Eerst, ga sommige gegevens in uw datasets in.
   > 1. Oplossen van problemen die zich tijdens het invoeren van gegevens voordoen (bijvoorbeeld problemen met gegevensvalidatie of -toewijzing).
   > 1. Uw gegevenssets en schema&#39;s voor profiel inschakelen
   > 1. De gegevens opnieuw invoeren


   ![&#x200B; Wisselen van het Profiel &#x200B;](assets/profile-loyalty-enableSchema.png)

Eenvoudig, niet? Herhaal bovenstaande stappen voor dit andere schema:

1. Luminageproductcatalogusschema
1. Luma-schema voor offlineaankoopgebeurtenissen
1. Het Schema van de Gebeurtenissen van het Web van Luma (op bevestigingsmodaal, controleer de doos &quot;Gegevens voor dit schema zullen een primaire identiteit op het identityMap gebied bevatten.&quot;)

## Schema&#39;s inschakelen voor realtime klantprofiel met behulp van platform-API

Nu is het tijd om de `Luma CRM Schema` in te schakelen met de API. Als u deze oefening wilt overslaan en enkel het in het gebruikersinterface toelaten, ga onmiddellijk.

### Haal de meta:altId van het schema op

Laten we eerst de `meta:altId` van de `Luma CRM Schema` ophalen:

1. Openen [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteer **verzend** om een nieuw toegangstoken aan te vragen, enkel zoals u in de [!DNL Postman] les deed.
1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Selecteer **verzenden** knoop
1. Je moet 200 reacties krijgen
1. Zoek in het antwoord op het item `Luma CRM Schema` en kopieer de waarde `meta:altId` .
   ![&#x200B; Exemplaar meta:altIid &#x200B;](assets/profile-crm-getMetaAltId.png)

### Het schema inschakelen

Nu wij meta:altId van het schema hebben, kunnen wij het voor profiel toelaten:

1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Update one or more attributes of a custom schema specified by ID.]**
1. In de **Params** kleef uw `meta:altId` waarde als `SCHEMA_ID` paramwaarde
1. In het **Lichaam** lusje, kleef de volgende code

   ```json
   [{
       "op": "add",
       "path": "/meta:immutableTags",
       "value": ["union"]
   }]
   ```

1. Selecteer **verzenden** knoop
1. Je moet 200 reacties krijgen

   ![&#x200B; laat het schema van CRM voor profiel met uw douanemeta toe:altIid die als param SCHEMA_ID wordt gebruikt &#x200B;](assets/profile-crm-enableProfile.png)

U moet in de gebruikersinterface kunnen zien dat alle vijf schema&#39;s zijn ingeschakeld voor Profiel (u moet mogelijk SHIFT opnieuw laden om te zien of `Luma CRM Schema` is ingeschakeld):
![&#x200B; Alle toegelaten schema&#39;s &#x200B;](assets/profile-allSchemasEnabled.png)


## Gegevenssets inschakelen voor realtime klantprofiel met behulp van de gebruikersinterface van het platform

De datasets moeten ook voor Profiel worden toegelaten, en het proces is nog eenvoudiger:

1. Open in de gebruikersinterface van Platform de `Luma Loyalty Dataset`
1. Schakelen tussen de schakeloptie **[!UICONTROL Profile]**
1. Druk in het bevestigingsmodaal op de knop **[!UICONTROL Enable]** om te bevestigen

   ![&#x200B; Profiel in-/uitschakelen &#x200B;](assets/profile-loyalty-enableDataset.png)

Herhaal bovenstaande stappen voor deze andere datasets:

1. Gegevensset van productcatalogus met luminantie
1. Dataset voor offline aanschafgebeurtenissen voor Luminantie
1. Dataset Luminagegebeurtenissen web

>[!NOTE]
>
>In tegenstelling tot schema&#39;s, kunt u datasets van Profiel onbruikbaar maken, nochtans zullen alle eerder opgenomen gegevens in Profiel blijven.

## Gegevenssets inschakelen voor realtime klantprofiel met behulp van platform-API

Nu zult u een dataset voor Profiel toelaten gebruikend API. Nogmaals, als u het via de gebruikersinterface wilt toelaten gebruikend de hierboven vermelde methode, is dat ook prima.

### Krijg identiteitskaart van de dataset

Eerst moeten we de `id` van de `Luma CRM Dataset` ophalen:

1. Openen [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteer **verzend** om een nieuw toegangstoken aan te vragen, enkel zoals u in de [!DNL Postman] les deed.
1. De aanvraag openen **[!DNL Catalog Service API > Datasets > Retrieve a list of datasets.]**
1. Selecteer **verzenden** knoop
1. Je moet 200 reacties krijgen
1. Zoek in de reactie voor het `Luma CRM Dataset` -item en kopieer de id:
   ![&#x200B; Exemplaar identiteitskaart &#x200B;](assets/profile-crm-copyDatasetId.png)

### De gegevensset inschakelen

Nu wij identiteitskaart van de dataset hebben, kunnen wij het voor profiel toelaten:

1. De aanvraag openen **[!DNL Catalog Service API > Datasets > Update one or more attributes of a dataset specified by ID.]**
1. In **Params** werk de `DATASET_ID` waarde aan uw bij
1. In het **Lichaam** lusje, kleef de volgende code. De eerste twee waarden zijn vooraf bestaande tags die zichtbaar zijn in de vorige reactie. Zij moeten in het lichaam worden opgenomen, naast de twee nieuwe tags die wij toevoegen:

   ```json
   {
       "tags":{
           "adobe/pqs/table":["luma_crm_dataset"],
           "adobe/siphon/table/format":["parquet"],
           "unifiedProfile":["enabled:true"],
           "unifiedIdentity":["enabled:true"]
           }
   }
   ```

1. Selecteer **verzenden** knoop
1. Je moet 200 reacties krijgen

   ![&#x200B; laat de dataset van CRM voor profiel toe, die ervoor zorgen om uw identiteitskaart van de douanedataset als param te gebruiken DATASET_ID &#x200B;](assets/profile-crm-enableDataset.png)

U kunt ook bevestigen dat de gebruikersinterface de toegelaten dataset toont:
![&#x200B; bevestigt &#x200B;](assets/profile-crm-confirmEnabled.png)

>[!IMPORTANT]
>
> Als u gegevens vóór het toelaten van het schema en de dataset voor profiel ingaat, zult u die gegevens na opnieuw moeten opnemen.

## Aanvullende bronnen

* [&#x200B; Real-Time documentatie van het Profiel van de Klant &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=nl)
* [&#x200B; Real-Time API van het Profiel van de Klant verwijzing &#x200B;](https://www.adobe.io/experience-platform-apis/references/profile/)


**Ingenieurs van Gegevens** zouden aan [&#x200B; moeten blijven aan de gebeurtenissen van de gegevensopname &#x200B;](subscribe-to-data-ingestion-events.md) les abonneren.
**_de Architecten van Gegevens 0&rbrace; &lbrace;kunnen vooruit_ overslaan en naar de [&#x200B; partij ingesliples &#x200B;](ingest-batch-data.md) gaan.**

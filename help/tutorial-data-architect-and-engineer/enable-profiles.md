---
title: Klantprofielen in realtime inschakelen
seo-title: Enable Real-time Customer Profiles | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Klantprofielen in realtime inschakelen
description: In deze les, zult u uw schema's en datasets voor het Profiel van de Klant in real time toelaten.
role: Data Architect
feature: Profiles
kt: 4348
thumbnail: 4348-enable-profiles.jpg
exl-id: b05f1af1-a599-42f2-8546-77453a578b92
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 1%

---

# Klantprofielen in realtime inschakelen

<!-- 15min-->
In deze les, zult u uw schema&#39;s en datasets voor het Profiel van de Klant in real time toelaten.

Oké, ik heb gelogen toen ik zei dat de datasetles de kortste les in dit leerprogramma was—dit zou nog minder tijd moeten vergen! Letterlijk is het enige wat je gaat doen, een heleboel knevels omdraaien. Maar wat er gebeurt als je deze schakelingen omdraait, is _echt_ belangrijk, dus ik wilde er een hele pagina aan wijden.

Met het Profiel van de Klant in real time, kunt u een holistische mening van elke individuele klant zien die gegevens van veelvoudige kanalen, met inbegrip van online, off-line, CRM, en derdegegevens combineert. Het profiel staat u toe om uw ongelijke klantengegevens in een verenigde mening te consolideren die een actionable, timestamped rekening van elke klanteninteractie aanbiedt.

Hoe verbazingwekkend al dat klinkt, je hoeft niet te activeren *alle gegevens* voor profiel. In feite, zou u slechts de gegevens moeten toelaten u voor activeringsgebruiksgevallen nodig hebt. Laat gegevens toe die u voor de gevallen van het marketinggebruik wilt gebruiken, vraag centrumintegratie, etc., waar u snelle toegang tot een robuust klantenprofiel nodig hebt. Als u gegevens alleen uploadt voor analyse, moet dit waarschijnlijk niet worden ingeschakeld voor profiel.

Er zijn belangrijke [handleidingen voor gegevens in realtime klantprofiel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) die u moet controleren wanneer u bepaalt welke van uw eigen gegevens u voor profiel moet inschakelen.

<!--is this accurate. Are there other considerations to point out? -->

**Gegevensarchitecten** zal het Profiel van de Klant in real time buiten deze zelfstudie moeten toelaten.

Voordat u met de oefeningen begint, bekijkt u deze korte video voor meer informatie over het profiel van de Klant in real time:
>[!VIDEO](https://video.tv.adobe.com/v/27251?quality=12&learn=on)

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.


<!--* Permission items **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Schema&#39;s voor realtime klantprofiel inschakelen met de gebruikersinterface van het Platform

Laten we beginnen met de eenvoudige taak om een schema in te schakelen:

1. Open in de gebruikersinterface van het Platform de **Luma Loyalty Schema**
1. In **[!UICONTROL Schema-eigenschappen]**, schakelt u de **Profiel** switch
1. Druk in het bevestigingsmodaal op **[!UICONTROL Inschakelen]** te bevestigen knop
1. Selecteer **[!UICONTROL Opslaan]** knop om uw wijzigingen op te slaan

   >[!IMPORTANT]
   >
   >Als een schema eenmaal is ingeschakeld voor Profiel, kan het niet worden uitgeschakeld of verwijderd. Ook kunnen velden na dit punt niet uit het schema worden verwijderd. Deze implicaties zijn belangrijk om later in mening te houden wanneer u met uw eigen gegevens in uw milieu van de Productie werkt. In deze zelfstudie moet u een ontwikkelingssandbox gebruiken die u op elk gewenst moment kunt verwijderen.
   >
   >In het gecontroleerde milieu van dit leerprogramma, zult u uw schema&#39;s en datasets voor profiel toelaten, _voordat gegevens worden ingevoerd_. Als u met uw eigen gegevens werkt, is het raadzaam de volgende handelingen uit te voeren:
   >
   > 1. Eerst, ga sommige gegevens in uw datasets in.
   > 1. Oplossen van problemen die zich tijdens het invoeren van gegevens voordoen (bijvoorbeeld problemen met gegevensvalidatie of -toewijzing).
   > 1. Uw gegevenssets en schema&#39;s voor profiel inschakelen
   > 1. De gegevens opnieuw invoeren



   ![Profiel in-/uitschakelen](assets/profile-loyalty-enableSchema.png)

Eenvoudig, niet? Herhaal bovenstaande stappen voor dit andere schema:

1. Luminageproductcatalogusschema
1. Luma-schema voor offlineaankoopgebeurtenissen
1. Het Schema van de Gebeurtenissen van het Web van Luma (op bevestigingsmodaal, controleer de doos &quot;Gegevens voor dit schema zullen een primaire identiteit op het identityMap gebied bevatten.&quot;)

## Schema&#39;s inschakelen voor realtime klantprofiel met Platform-API

Nu is het tijd om de `Luma CRM Schema` met de API. Als u deze oefening wilt overslaan en enkel het in het gebruikersinterface toelaten, ga onmiddellijk.

### Haal de meta:altId van het schema op

Laten we eerst de `meta:altId` van de `Luma CRM Schema`:

1. Open [!DNL Postman]
1. Als je de afgelopen 24 uur geen aanvraag hebt ingediend, zijn je autorisatietokens waarschijnlijk verlopen. De aanvraag openen **[!DNL Adobe I/O Access Token Generation > Local Signing (Non-production use-only) > IMS: JWT Generate + Auth via User Token]** en selecteert u **Verzenden** om nieuwe JWT en Tokens van de Toegang aan te vragen, enkel zoals u in [!DNL Postman] les.
1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Selecteer **Verzenden** knop
1. Je moet 200 reacties krijgen
1. Kijk in de reactie voor de `Luma CRM Schema` en kopieer het `meta:altId` value
   ![Meta:altIid kopiëren](assets/profile-crm-getMetaAltId.png)

### Het schema inschakelen

Nu wij meta:altId van het schema hebben, kunnen wij het voor profiel toelaten:

1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Update one or more attributes of a custom schema specified by ID.]**
1. In de **Params** plakken `meta:altId` waarde als de `SCHEMA_ID` parabijwaarde
1. In de **Lichaam** , plakt u de volgende code

   ```json
   [{
       "op": "add",
       "path": "/meta:immutableTags",
       "value": ["union"]
   }]
   ```

1. Selecteer **Verzenden** knop
1. Je moet 200 reacties krijgen

   ![Laat het schema van CRM voor profiel met uw douanemeta:altIid toe die als param SCHEMA_ID wordt gebruikt](assets/profile-crm-enableProfile.png)

U zou in het gebruikersinterface moeten kunnen zien dat alle vijf schema&#39;s voor Profiel worden toegelaten (u zou kunnen moeten SHIFT-opnieuw laden om te zien dat `Luma CRM Schema` is ingeschakeld):
![Alle schema&#39;s ingeschakeld](assets/profile-allSchemasEnabled.png)


## Gegevenssets inschakelen voor realtime klantprofiel met behulp van de gebruikersinterface van het Platform

De datasets moeten ook voor Profiel worden toegelaten, en het proces is nog eenvoudiger:

1. Open in de gebruikersinterface van het Platform de `Luma Loyalty Dataset`
1. Schakelen tussen **[!UICONTROL Profiel]** switch
1. Druk in het bevestigingsmodaal op **[!UICONTROL Inschakelen]** te bevestigen knop

   ![ Profiel in-/uitschakelen](assets/profile-loyalty-enableDataset.png)

Herhaal bovenstaande stappen voor deze andere datasets:

1. Gegevensset van productcatalogus met luminantie
1. Dataset voor offline aanschafgebeurtenissen voor Luminantie
1. Dataset Luminagegebeurtenissen web

>[!NOTE]
>
>In tegenstelling tot schema&#39;s, kunt u datasets van Profiel onbruikbaar maken, nochtans zullen alle eerder opgenomen gegevens in Profiel blijven.

## Gegevenssets inschakelen voor realtime klantprofiel met Platform-API

Nu zult u een dataset voor Profiel toelaten gebruikend API. Nogmaals, als u het via de gebruikersinterface wilt toelaten gebruikend de hierboven vermelde methode, is dat ook prima.

### Krijg identiteitskaart van de dataset

Eerst moeten we de `id` van de `Luma CRM Dataset`:

1. Openen [!DNL Postman]
1. Als je de afgelopen 24 uur geen aanvraag hebt ingediend, zijn je autorisatietokens waarschijnlijk verlopen. De aanvraag openen **[!DNL Adobe I/O Access Token Generation > Local Signing (Non-production use-only) > IMS: JWT Generate + Auth via User Token]** en selecteert u **Verzenden** om nieuwe JWT en Tokens van de Toegang aan te vragen, enkel zoals u in [!DNL Postman] les.
1. De aanvraag openen **[!DNL Catalog Service API > Datasets > Retrieve a list of datasets.]**
1. Selecteer **Verzenden** knop
1. Je moet 200 reacties krijgen
1. Kijk in de reactie voor de `Luma CRM Dataset` -item en kopieer de id:
   ![De id kopiëren](assets/profile-crm-copyDatasetId.png)

### De gegevensset inschakelen

Nu wij identiteitskaart van de dataset hebben, kunnen wij het voor profiel toelaten:

1. De aanvraag openen **[!DNL Catalog Service API > Datasets > Update one or more attributes of a dataset specified by ID.]**
1. In de **Params** de update `DATASET_ID` waarde voor u
1. In de **Lichaam** plakken, plakt u de volgende code. De eerste twee waarden zijn vooraf bestaande tags die zichtbaar zijn in de vorige reactie. Zij moeten in het lichaam worden opgenomen, naast de twee nieuwe tags die wij toevoegen:

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

1. Selecteer **Verzenden** knop
1. Je moet 200 reacties krijgen

   ![Laat de dataset van CRM voor profiel toe, ervoor zorgend om uw identiteitskaart van de douanedataset als param te gebruiken DATASET_ID](assets/profile-crm-enableDataset.png)

U kunt ook bevestigen dat de gebruikersinterface de toegelaten dataset toont:
![Bevestigen](assets/profile-crm-confirmEnabled.png)

>[!IMPORTANT]
>
> Als u gegevens vóór het toelaten van het schema en de dataset voor profiel ingaat, zult u die gegevens na opnieuw moeten opnemen.

## Aanvullende bronnen

* [Documentatie bij real-timeklantprofiel](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=nl)
* [Real-time verwijzing API voor klantprofiel](https://www.adobe.io/experience-platform-apis/references/profile/)


**Gegevensengineers** de [Abonneren op gebeurtenissen voor gegevensinvoer](subscribe-to-data-ingestion-events.md) les.
**Gegevensarchitecten** _kan vooruit overslaan_ en ga naar de [batch-opname les](ingest-batch-data.md).

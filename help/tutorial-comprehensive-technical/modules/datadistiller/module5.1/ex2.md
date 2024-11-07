---
title: De Dienst van de vraag - Gebruikend de Dienst van de Vraag
description: De Dienst van de vraag - Gebruikend de Dienst van de Vraag
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 5.1.2 Het gebruiken van de Dienst van de Vraag

## Doelstelling

- Gegevensbestanden zoeken en verkennen
- Leer hoe te om de voorwerpen en de attributen van de Modellen van Gegevens van de Ervaring in uw vragen te richten

## Context

In dit zult u leren hoe te om PSQL te gebruiken om informatie over de beschikbare datasets terug te winnen, hoe te om vragen voor het Model van Gegevens van de Ervaring (XDM) te schrijven, en uw eerste eenvoudige rapporteringsvragen te schrijven gebruikend de Dienst van de Vraag en de Datasets van het Signaal van Citi.

## 5.1.2.1 Basisquery&#39;s

In dit zult u over de methodes leren om informatie over de beschikbare datasets terug te winnen en hoe te om gegevens met een vraag van een dataset behoorlijk terug te winnen XDM.

Alle datasets die wij via Adobe Experience Platform in het begin van 1 hebben onderzocht, zijn ook beschikbaar voor toegang via een SQL interface als lijsten. Om van die lijsten een lijst te maken kunt u **gebruiken toont lijsten;** bevel.

Uitvoeren **toont lijsten;** in uw **bevel-lijn PSQL interface**. (vergeet niet uw opdracht te beëindigen met een puntkomma).

Kopieer het bevel **tonen lijsten;** en kleef het bij de herinnering:

![ bevel-herinnering-show-tables.png ](./images/command-prompt-show-tables.png)

Het volgende resultaat wordt weergegeven:

```text
aepenablementfy21:all=> show tables;
                            name                            |        dataSetId         |                            dataSet                             | description | resolved 
------------------------------------------------------------+--------------------------+----------------------------------------------------------------+-------------+----------
 demo_system_event_dataset_for_call_center_global_v1_1      | 5fd1a9dea30603194baeea43 | Demo System - Event Dataset for Call Center (Global v1.1)      |             | false
 demo_system_event_dataset_for_mobile_app_global_v1_1       | 5fd1a9de250e4f194bec84cd | Demo System - Event Dataset for Mobile App (Global v1.1)       |             | false
 demo_system_event_dataset_for_voice_assistants_global_v1_1 | 5fd1a9de49ee76194b85f73c | Demo System - Event Dataset for Voice Assistants (Global v1.1) |             | false
 demo_system_event_dataset_for_website_global_v1_1          | 5fd1a9dee3224d194cdfe786 | Demo System - Event Dataset for Website (Global v1.1)          |             | false
 demo_system_profile_dataset_for_loyalty_global_v1_1        | 5fd1a9de250e4f194bec84cc | Demo System - Profile Dataset for Loyalty (Global v1.1)        |             | false
 demo_system_profile_dataset_for_ml_predictions_global_v1_1 | 5fd1a9de241f58194b0cb117 | Demo System - Profile Dataset for ML Predictions (Global v1.1) |             | false
 demo_system_profile_dataset_for_mobile_app_global_v1_1     | 5fd1a9deddf353194a2e00b7 | Demo System - Profile Dataset for Mobile App (Global v1.1)     |             | false
 demo_system_profile_dataset_for_website_global_v1_1        | 5fd1a9de42a61c194dd7b810 | Demo System - Profile Dataset for Website (Global v1.1)        |             | false
 journey_step_events                                        | 5fd1a7f30268c5194bbb7e5e | Journey Step Events                                            |             | false
```

Druk op de dubbelepunten op de spatiebalk om de volgende pagina van de resultaatset te zien of voer `q` in om terug te keren naar de opdrachtprompt.

Elke dataset in Platform heeft zijn overeenkomstige lijst van de Dienst van de Vraag. U kunt de lijst van een dataset via de Datasets ui vinden:

![ ui-dataset-tablename.png ](./images/ui-dataset-tablename.png)

De tabel `demo_system_event_dataset_for_website_global_v1_1` is de tabel Query Service die overeenkomt met de gegevensset `Demo System - Event Schema for Website (Global v1.1)` .

Om sommige informatie over te vragen waar een product werd bekeken, zullen wij de **geo** informatie selecteren.

Kopieer de verklaring hieronder en kleef het bij de herinnering in uw **bevel-lijn PSQL interface** en de slag gaat binnen:

```sql
select placecontext.geo
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

In uw vraagresultaat, zult u opmerken dat de kolommen in het Model van de Gegevens van de Ervaring (XDM) complexe types en niet alleen scalaire types kunnen zijn. In de vraag hierboven zouden wij geografische plaatsen willen identificeren waar a **commerce.productViews** voorkwam. Om a **commerce.productViews** te identificeren moeten wij door het model navigeren XDM gebruikend **.** (punt) notatie.

```text
aepenablementfy21:all=> select placecontext.geo
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
                  geo                   
----------------------------------------
 ("(57.4694803,-3.1269422)",Tullich,GB)
(1 row)
```

U ziet dat het resultaat een vlak object is in plaats van een enkele waarde? Het {**voorwerp 0} placecontext.geo bevat vier attributen: schema, land en stad.** Wanneer een object wordt gedeclareerd als een kolom, retourneert dit het gehele object als een tekenreeks. Het schema XDM kan complexer zijn dan wat u vertrouwd met bent maar het is zeer krachtig en is ontworpen om vele oplossingen, kanalen, en gebruiksgevallen te steunen.

Gebruik **om de afzonderlijke eigenschappen van een object te selecteren.** (punt) notatie.

Kopieer de verklaring hieronder en kleef het bij de herinnering in uw **bevel-lijn PSQL interface**:

```sql
select placecontext.geo._schema.longitude
      ,placecontext.geo._schema.latitude
      ,placecontext.geo.city
      ,placecontext.geo.countryCode
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Het resultaat van de bovenstaande query moet er als volgt uitzien.
Het resultaat is nu een set eenvoudige waarden:

```text
aepenablementfy21:all=> select placecontext.geo._schema.longitude
aepenablementfy21:all->       ,placecontext.geo._schema.latitude
aepenablementfy21:all->       ,placecontext.geo.city
aepenablementfy21:all->       ,placecontext.geo.countryCode
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
 longitude  |  latitude  |  city   | countrycode 
------------+------------+---------+-------------
 -3.1269422 | 57.4694803 | Tullich | GB
(1 row)
```

Maak u geen zorgen, er is een gemakkelijke manier om de weg naar een specifiek bezit te verkrijgen. In het volgende gedeelte leert u hoe u dit kunt doen.

U zult een vraag moeten uitgeven, zodat openen eerst een redacteur.

Op Windows

Klik het **pictogram van het 0} onderzoek {in de vensterswerkbalk, type** notepad **in het** onderzoek **gebied, klik het** notebookpad **resultaat:**

![ windows-start-notepad.png ](./images/windows-start-notepad.png)

Op Mac

Installeer [ Haakjes ](https://github.com/adobe/brackets/releases/download/release-1.14/Brackets.Release.1.14.dmg) of gebruik een andere Redacteur van de Tekst van keus als u het geïnstalleerd niet hebt en de instructies volgt. Na installatie, onderzoek naar **Haakjes** via het spotlightonderzoek van Mac en open het.

Kopieer de volgende instructie naar het toetsenblok of de vierkante haakjes:

```sql
select your_attribute_path_here
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Ga terug naar uw Adobe Experience Platform UI (zou open in uw browser moeten zijn) of aan [ https://platform.adobe.com ](https://platform.adobe.com) navigeren.

Selecteer **Schema&#39;s**, ga `Demo System - Event Schema for Website (Global v1.1)` op het **onderzoek** gebied in en selecteer `Demo System - Event Schema for Website (Global v1.1) Schema` van de lijst.

![ browse-schema.png ](./images/browse-schema.png)

Onderzoek het model XDM voor **Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1)**, door op een voorwerp te klikken. Breid de boom voor **placecontext**, **geo** en **schema** uit. Wanneer u de daadwerkelijke attributen **lengtegraad** selecteert, zult u de volledige weg in de benadrukte rode doos zien. Als u het pad van het kenmerk wilt kopiëren, klikt u op het pictogram van het kopieerpad.

![ onderzoek-schema-voor-weg.png ](./images/explore-schema-for-path.png)

De schakelaar aan uw notitieblok/steunen en verwijdert **your_attribute_path_here** uit de eerste lijn. Plaats uw curseur na **uitgezocht** op de eerste lijn en deeg (CTRL-V).

Kopieer de gewijzigde verklaring van nota&#39;s/steunen en kleef het bij de herinnering in uw **PSQL bevel-lijn interface** en slag gaat binnen.

Het resultaat moet er als volgt uitzien:

```text
aepenablementfy21:all=> select placeContext.geo._schema.longitude
aepenablementfy21:all-> from   demo_system_event_dataset_for_website_global_v1_1
aepenablementfy21:all-> where  eventType = 'commerce.productViews'
aepenablementfy21:all-> and placecontext.geo.countryCode <> ''
aepenablementfy21:all-> limit 1;
 longitude  
------------
 -3.1269422
```

Volgende Stap: [ 5.1.3 Vragen, vragen, vragen... en koordanalyse ](./ex3.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

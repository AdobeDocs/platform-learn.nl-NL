---
title: De Dienst van de vraag - Gebruikend de Dienst van de Vraag
description: De Dienst van de vraag - Gebruikend de Dienst van de Vraag
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: dbf19991-cb09-43cf-887c-52996dfd2986
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---

# 4.2 Het gebruiken van de Dienst van de Vraag

## Doelstelling

- Gegevensbestanden zoeken en verkennen
- Leer hoe te om de voorwerpen en de attributen van de Modellen van Gegevens van de Ervaring in uw vragen te richten

## Context

In dit zult u leren hoe te om PSQL te gebruiken om informatie over de beschikbare datasets terug te winnen, hoe te om vragen voor het Model van Gegevens van de Ervaring (XDM) te schrijven, en uw eerste eenvoudige rapporteringsvragen te schrijven gebruikend de Dienst van de Vraag en de Datasets van het Signaal van Citi.

## 4.2.1 Basisvragen

In dit zult u over de methodes leren om informatie over de beschikbare datasets terug te winnen en hoe te om gegevens met een vraag van een dataset behoorlijk terug te winnen XDM.

Alle datasets die wij via Adobe Experience Platform in het begin van 1 hebben onderzocht, zijn ook beschikbaar voor toegang via een SQL interface als lijsten. Als u die tabellen wilt weergeven, kunt u de opdracht **tabellen tonen;** gebruiken.

Uitvoeren **tabellen tonen;** in uw **PSQL-opdrachtregelinterface**. (vergeet niet uw opdracht te beëindigen met een puntkomma).

De opdracht kopiëren **tabellen tonen;** en plak het op de vraag:

![command-prompt-show-tables.png](./images/command-prompt-show-tables.png)

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

Druk op de dubbelepunten op de spatiebalk om de volgende pagina van de resultatenset weer te geven, of typ `q` om aan de bevelherinnering terug te keren.

Elke dataset in Platform heeft zijn overeenkomstige lijst van de Dienst van de Vraag. U kunt de lijst van een dataset via de Datasets ui vinden:

![ui-dataset-tablename.png](./images/ui-dataset-tablename.png)

De `demo_system_event_dataset_for_website_global_v1_1` de lijst is de lijst van de Dienst van de Vraag die met de `Demo System - Event Schema for Website (Global v1.1)` dataset.

Als u informatie wilt opvragen over de weergavelocatie van een product, selecteert u de optie **geo** informatie.

Kopieer de onderstaande instructie en plak deze achter de prompt in uw **PSQL-opdrachtregelinterface** en druk op Enter:

```sql
select placecontext.geo
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

In uw vraagresultaat, zult u opmerken dat de kolommen in het Model van de Gegevens van de Ervaring (XDM) complexe types en niet alleen scalaire types kunnen zijn. In de bovenstaande query willen we geografische locaties identificeren waar een **commerce.productViews** heeft plaatsgevonden. Om een **commerce.productViews** we moeten door het XDM-model navigeren met het **.** (punt) notatie.

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

U ziet dat het resultaat een vlak object is in plaats van een enkele waarde? De **placecontext.geo** object bevat vier kenmerken: schema, land en stad. Wanneer een object wordt gedeclareerd als een kolom, retourneert dit het gehele object als een tekenreeks. Het schema XDM kan complexer zijn dan wat u vertrouwd met bent maar het is zeer krachtig en is ontworpen om vele oplossingen, kanalen, en gebruiksgevallen te steunen.

Als u de afzonderlijke eigenschappen van een object wilt selecteren, gebruikt u de opdracht **.** (punt) notatie.

Kopieer de onderstaande instructie en plak deze achter de prompt in uw **PSQL-opdrachtregelinterface**:

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

Maak u geen zorgen, er is een gemakkelijke manier om de weg naar een specifiek bezit te verkrijgen. In het volgende gedeelte leert u hoe.

U zult een vraag moeten uitgeven, zodat openen eerst een redacteur.

Op Windows

Klik op de knop **zoeken** pictogram in de vensterwerkbalk, typt u **laptop** in de **zoeken** veld, klikt u op de knop **laptop** resultaat:

![windows-start-notepad.png](./images/windows-start-notepad.png)

Op Mac

Installeren [Haakjes](https://github.com/adobe/brackets/releases/download/release-1.14/Brackets.Release.1.14.dmg) of gebruik een andere teksteditor als u deze niet hebt geïnstalleerd en volg de instructies. Na de installatie zoekt u naar **Haakjes** via de zoekfunctie van Mac.

Kopieer de volgende instructie naar het toetsenblok of de vierkante haakjes:

```sql
select your_attribute_path_here
from   demo_system_event_dataset_for_website_global_v1_1
where  eventType = 'commerce.productViews'
and placecontext.geo.countryCode <> ''
limit 1;
```

Ga terug naar de gebruikersinterface van Adobe Experience Platform (moet geopend zijn in uw browser) of navigeer naar [https://platform.adobe.com](https://platform.adobe.com).

Selecteren **Schemas**, enter `Demo System - Event Schema for Website (Global v1.1)` in de **zoeken** veld en selecteer `Demo System - Event Schema for Website (Global v1.1) Schema` in de lijst.

![browse-schema.png](./images/browse-schema.png)

Ontdek het XDM-model voor **Demosysteem - Gebeurtenisschema voor website (Global v1.1)** door op een object te klikken. De structuur uitvouwen voor **kalmeren**, **geo** en **schema**. Wanneer u het eigenlijke kenmerk selecteert **lengtegraad** wordt het volledige pad weergegeven in het gemarkeerde rode vak. Als u het pad van het kenmerk wilt kopiëren, klikt u op het pictogram van het kopieerpad.

![exploratieschema-for-path.png](./images/explore-schema-for-path.png)

Schakel over naar uw laptop/haakjes en verwijder **your_attribute_path_here** vanaf de eerste regel. Plaats de cursor na **selecteren** op de eerste regel en plak (CTRL-V).

Kopieer de gewijzigde instructie van de notedop/vierkante haakjes en plak deze achter de opdrachtprompt in uw **PSQL-opdrachtregelinterface** en druk op Enter.

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

Volgende stap: [4.3 Vragen, query&#39;s, query&#39;s... en kurkanalyse](./ex3.md)

[Ga terug naar module 4](./query-service.md)

[Terug naar alle modules](../../overview.md)

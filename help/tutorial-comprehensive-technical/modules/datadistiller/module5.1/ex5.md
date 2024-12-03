---
title: Query-service - Power BI/Tableau
description: Query-service - Power BI/Tableau
kt: 5342
doc-type: tutorial
exl-id: c4e4f5f9-3962-4c8f-978d-059f764eee1c
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# 5.1.5 Genereer een dataset van een vraag

## Doelstelling

Leer hoe te om datasets van vraagresultaten te produceren
Microsoft Power BI Desktop/Tableau rechtstreeks verbinden met de Query Service
Een rapport maken in Microsoft Power BI Desktop/Tableau Desktop

## Lessoncontext

Een interface van de bevellijn aan vraaggegevens is opwindend maar het presenteert niet goed. In deze les, zullen wij u door een geadviseerde werkschema voor hoe u Microsoft Power BI Desktop/Tableau direct de Dienst van de Vraag kunt gebruiken om visuele rapporten voor uw belanghebbenden tot stand te brengen.

## Een dataset maken van een SQL-query

De ingewikkeldheid van uw vraag zal beïnvloeden hoe lang het voor de Dienst van de Vraag duurt om resultaten terug te keren. En wanneer het vragen direct van de bevellijn of andere oplossingen zoals Microsoft Power BI/Tableau wordt de Dienst van de Vraag gevormd met een miniem onderbreking 5 (600 seconden). En in bepaalde gevallen zullen deze oplossingen met kortere onderbrekingen worden gevormd. Om grotere vragen in werking te stellen en voorladen de tijd het neemt om resultaten terug te keren bieden wij een eigenschap aan om een dataset van de vraagresultaten te produceren. Deze functie gebruikt de standaard SQL eigenschap die als Create Lijst als Uitgezochte (CTAS) wordt bekend. Het is beschikbaar in Platform UI van de Lijst van de Vraag en ook beschikbaar om direct van de bevellijn met PSQL te worden in werking gesteld.

In vorige u **hebt vervangen ga uw naam** met uw eigen ldap in alvorens het in PSQL uit te voeren.

```sql
select /* enter your name */
       e.--aepTenantId--.identification.core.ecid as ecid,
       e.placeContext.geo.city as city,
       e.placeContext.geo._schema.latitude latitude,
       e.placeContext.geo._schema.longitude longitude,
       e.placeContext.geo.countryCode as countrycode,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callFeeling as callFeeling,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callTopic as callTopic,
       c.--aepTenantId--.interactionDetails.core.callCenterAgent.callContractCancelled as contractCancelled,
       l.--aepTenantId--.loyaltyDetails.level as loyaltystatus,
       l.--aepTenantId--.loyaltyDetails.points as loyaltypoints,
       l.--aepTenantId--.identification.core.loyaltyId as crmid
from   demo_system_event_dataset_for_website_global_v1_1 e
      ,demo_system_event_dataset_for_call_center_global_v1_1 c
      ,demo_system_profile_dataset_for_loyalty_global_v1_1 l
where  e.--aepTenantId--.demoEnvironment.brandName IN ('Luma Telco', 'Citi Signal')
and    e.web.webPageDetails.name in ('Cancel Service', 'Call Start')
and    e.--aepTenantId--.identification.core.ecid = c.--aepTenantId--.identification.core.ecid
and    l.--aepTenantId--.identification.core.ecid = e.--aepTenantId--.identification.core.ecid;
```

Navigeer aan Adobe Experience Platform UI - [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform)

U zoekt naar de uitgevoerde instructie in de gebruikersinterface van de Adobe Experience Platform-query door uw LDAP in te voeren in het zoekveld:

Selecteer **Vragen**, ga naar **Logboek** en ga uw ldap op het onderzoeksgebied in.

![ onderzoek-vraag-voor-ctas.png ](./images/search-query-for-ctas.png)

Selecteer uw vraag en klik **Dataset van de Output**.

![ onderzoek-vraag-voor-ctas.png ](./images/search-query-for-ctasa.png)

Ga `--aepUserLdap-- Callcenter Interaction Analysis` als naam en beschrijving voor de dataset in en druk de **knoop van de Vraag van de Looppas**

![ create-ctas-dataset.png ](./images/create-ctas-dataset.png)

Dientengevolge, zult u een nieuwe vraag met een status **Voorgelegd** zien.

![ ctas-query-submitted.png ](./images/ctas-query-submitted.png)

Op voltooiing, zult u een nieuwe ingang voor **Gemaakte Dataset** zien (u zou de pagina kunnen moeten verfrissen).

![ ctas-dataset-created.png ](./images/ctas-dataset-created.png)

Zodra uw dataset wordt gecreeerd (die 5-10 minuten kan vergen), kunt u de oefening voortzetten.

Volgende Stap - Optie A: [ 5.1.6 de Dienst en Power BI van de Vraag ](./ex6.md)

Volgende Stap - Optie B: [ 5.1.7 de Dienst van de Vraag en Tableau ](./ex7.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

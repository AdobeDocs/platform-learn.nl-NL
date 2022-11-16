---
title: Query-service - Power BI/Tableau
description: Query-service - Power BI/Tableau
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 11525d05-1c19-4d41-8f47-4feb3e8aed66
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 4.4 Genereer een dataset van een vraag

## Doelstelling

Leer hoe u gegevenssets kunt genereren op basis van zoekresultaten Connect Microsoft Power BI Desktop/Tableau rechtstreeks naar de Query Service. Een rapport wordt gemaakt in Microsoft Power BI Desktop/Tableau Desktop

## Lesson-context

Een interface van de bevellijn aan vraaggegevens is opwindend maar het presenteert niet goed. In deze les, zullen wij u door een geadviseerde werkschema voor hoe u Microsoft Power BI Desktop/Tableau direct de Dienst van de Vraag kunt gebruiken om visuele rapporten voor uw belanghebbenden tot stand te brengen.

## 4.4.1 Creeer een dataset van een SQL vraag

De ingewikkeldheid van uw vraag zal beïnvloeden hoe lang het voor de Dienst van de Vraag duurt om resultaten terug te keren. En wanneer het vragen direct van de bevellijn of andere oplossingen zoals Microsoft Power BI/Tableau wordt de Dienst van de Vraag gevormd met een miniem onderbreking 5 (600 seconden). En in bepaalde gevallen zullen deze oplossingen met kortere onderbrekingen worden gevormd. Om grotere vragen in werking te stellen en voorladen de tijd het neemt om resultaten terug te keren bieden wij een eigenschap aan om een dataset van de vraagresultaten te produceren. Deze functie gebruikt de standaard SQL eigenschap die als Create Lijst als Uitgezochte (CTAS) wordt bekend. Het is beschikbaar in het Platform UI van de Lijst van de Vraag en ook beschikbaar om direct van de bevellijn met PSQL te worden in werking gesteld.

In de vorige **Voer uw naam in** met uw eigen ldap voordat deze in PSQL wordt uitgevoerd.

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

Navigeren naar de gebruikersinterface van Adobe Experience Platform - [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

U zoekt naar de uitgevoerde instructie in de gebruikersinterface van de Adobe Experience Platform-query door uw LDAP in te voeren in het zoekveld:

Selecteren **Zoekopdrachten**, ga naar **Logboek** en voer uw index in het zoekveld in.

![search-query-for-ctas.png](./images/search-query-for-ctas.png)

Selecteer uw query en klik op **Uitvoergegevensset**.

![search-query-for-ctas.png](./images/search-query-for-ctasa.png)

Enter `--demoProfileLdap-- Callcenter Interaction Analysis` als naam en beschrijving voor de dataset en druk op **Query uitvoeren** knop

![create-ctas-dataset.png](./images/create-ctas-dataset.png)

Dientengevolge zult u een nieuwe vraag met een status zien **Verzonden**.

![ctas-query-submitted.png](./images/ctas-query-submitted.png)

Na voltooiing ziet u een nieuwe ingang voor **Gegevensset gemaakt** (Mogelijk moet u de pagina vernieuwen).

![ctas-dataset-created.png](./images/ctas-dataset-created.png)

Zodra uw dataset wordt gecreeerd (die 5-10 minuten kan vergen), kunt u de oefening voortzetten.

Volgende stap - optie A: [4.5 Query-service en -Power BI](./ex5.md)

Volgende stap - optie B: [4.6 Query-service en Tableau](./ex6.md)

[Ga terug naar module 4](./query-service.md)

[Terug naar alle modules](../../overview.md)

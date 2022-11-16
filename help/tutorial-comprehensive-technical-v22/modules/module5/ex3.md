---
title: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
description: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 57d6c714-5d41-4ac1-8e60-3000da45b76e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 1%

---

# 5.3 AI van de Klant - Score en Segmentatie (Voorspelling en actie ondernemen)

Zodra uw exemplaar van de Klant AI een modellooppas voltooit, zal het u toelaten om de volheidsscore visualiseren die wordt geëvalueerd om een klant te voorspellen die een aankoop in de volgende 30 dagen uitvoert.

![AI](./images/caimodels.png)

>[!NOTE]
>
>Alleen een Customer AI-exemplaar met de status **Succes** Hiermee kunt u de inzichten van de service voorvertonen.

## 5.3.1 Propensiteitsvoorspelling

Laten we nu de voorspelde eigenschappen bekijken die worden gegenereerd door het AI-instantiemodel van de klant. Klik op de instantienaam om het dashboard weer te geven.

![AI](./images/caimodels1.png)

Het AI-dashboard van de Klant geeft een overzicht van de score, de verdeling van de populatie en de invloedrijke factoren voor het model dat moet worden geëvalueerd.

![AI-beschrijving](./images/caidescription.png)

![Overzicht van dashboard](./images/caidashboard.png)

Houd de invloedrijke factoren aan om de verdere uitsplitsing van de gegevensdistributie te bekijken.

![Invloed factoren](./images/caiinfluencefactors.png)

## 5.3.2 Handelingen

### 5.3.2.1 Klanten segmenteren

Met het AI-dashboard van de Klant kunt u segmenten definiëren met één klik. Klik op de knop **Segment maken** op de proxykaarten.

![Een segment maken](./images/caiinfluencefactors1.png)

U zult zien dat een segmentdefinitie automatisch wordt gecreeerd.

![Segmentregel](./images/caicreatesegment.png)

Geef uw segment een naam volgens deze naamgevingsconventie: `--demoProfileLdap-- - Customer AI High Propensity`. Klikken **Opslaan**.

![Segmentregel](./images/caicreatesegment1.png)

U kunt dit segment nu gebruiken voor het opgeven van doelen, bijvoorbeeld Real-time CDP, Journey Orchestration en Adobe Target.

### 5.3.2.2 Profieloverzicht

Aangezien de AI-garantiescore van de Klant onderdeel wordt van het Real-time Klantprofiel, kunt u de score van de individuele klant bekijken.

Ga in Adobe Experience Platform naar **Profielen** in het linkermenu en selecteer **Bladeren**.

Zoeken naar een profiel met een van de id&#39;s, zoals bijvoorbeeld **E-MAIL hbirkenshawa@businessweek.com**, die beschikbaar zijn in het JSON-bestand dat u hebt ingevoerd. Klik op de knop **Profiel-id** om het profiel te openen.

![Profiel](./images/profile1.png)

U zult dan dit zien:

![Profiel](./images/profile2.png)

Ga naar **Attributen**, die de uitvoer van uw AI-model van de klant bevat.

![Profiel](./images/profile3.png)

Schuif omlaag om de score voor volheid te zien, zoals deze wordt berekend door uw AI-model van de klant.

![Profiel](./images/profile4.png)

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 5](./intelligent-services.md)

[Terug naar alle modules](./../../overview.md)

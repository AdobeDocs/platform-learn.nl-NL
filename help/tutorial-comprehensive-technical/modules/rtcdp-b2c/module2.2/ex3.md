---
title: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
description: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# 2.2.3 AI van de Klant - Scoring dashboard en segmentatie (Voorspelling en actie ondernemen)

Zodra uw exemplaar van de Klant AI een modellooppas voltooit, zal het u toelaten om de volheidsscore visualiseren die wordt geëvalueerd om een klant te voorspellen die een aankoop in de volgende 30 dagen uitvoert.

![ AI ](./images/caimodels.png)

>[!NOTE]
>
>Slechts zal een instantie van AI van de Klant met een status van **Succes** u toestaan om de inzichten van de dienst voor te vertonen.

## 2.2.3.1 Propensiteitsvoorspelling

Laten we nu de voorspelde eigenschappen bekijken die worden gegenereerd door het AI-instantiemodel van de klant. Klik op de instantienaam om het dashboard weer te geven.

![ AI ](./images/caimodels1.png)

Het AI-dashboard van de Klant geeft een overzicht van de score, de verdeling van de populatie en de invloedrijke factoren voor het model dat moet worden geëvalueerd.

![ AI Beschrijving ](./images/caidescription.png)

![ Overzicht van het Dashboard ](./images/caidashboard.png)

Houd de invloedrijke factoren aan om de verdere uitsplitsing van de gegevensdistributie te bekijken.

![ de factoren van de Gevolgen ](./images/caiinfluencefactors.png)

## 2.2.3.2 Handelingen

### 2.2.3.2.1 Klanten segmenteren

Met het AI-dashboard van de Klant kunt u segmenten definiëren met één klik. Klik op **creeer de knoop van het Segment** op de bezitskaarten.

![ creeer een segment ](./images/caiinfluencefactors1.png)

U zult zien dat een segmentdefinitie automatisch wordt gecreeerd.

![ de regel van het Segment ](./images/caicreatesegment.png)

Geef het segment een naam die volgt op de naamgevingsconventie: `--aepUserLdap-- - Customer AI High Propensity` . Klik **sparen**.

![ de regel van het Segment ](./images/caicreatesegment1.png)

U kunt dit segment nu gebruiken voor het gebruiken van bijvoorbeeld Real-time CDP, Journey Orchestration en Adobe Target.

### 2.2.3.2.2 Profieloverzicht

Aangezien de AI-garantiescore van de Klant onderdeel wordt van het Real-time Klantprofiel, kunt u de score van de individuele klant bekijken.

In Adobe Experience Platform, ga naar **Profielen** in het linkermenu en selecteer **doorbladeren**.

Onderzoek naar een profiel gebruikend om het even welke herkenningstekens, zoals bijvoorbeeld **E-MAIL hbirkenshawa@businessweek.com**, die in het JSON- dossier beschikbaar zijn dat u hebt opgenomen. Klik **identiteitskaart van het Profiel** om het profiel te openen.

![Profiel](./images/profile1.png)

U zult dan dit zien:

![Profiel](./images/profile2.png)

Ga naar **Attributen**, die de output van uw model van de Klant AI bevat.

![Profiel](./images/profile3.png)

Schuif omlaag om de score voor volheid te zien, zoals deze wordt berekend door uw AI-model van de klant.

![Profiel](./images/profile4.png)

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 2.2](./intelligent-services.md)

[Terug naar alle modules](./../../../overview.md)

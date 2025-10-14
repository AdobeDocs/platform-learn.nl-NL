---
title: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
description: AI van de klant - Scoredashboard en segmentatie (Voorspelling en actie ondernemen)
kt: 5342
doc-type: tutorial
exl-id: a6df3ff1-f907-4185-8189-f0b39c67c943
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 2.2.3 AI van de Klant - Scoring dashboard en segmentatie (Voorspelling en actie ondernemen)

Zodra uw exemplaar van de Klant AI een modellooppas voltooit, zal het u toelaten om de volheidsscore visualiseren die wordt geëvalueerd om een klant te voorspellen die een aankoop in de volgende 30 dagen uitvoert.

![&#x200B; AI &#x200B;](./images/caiinstancesummary1.png)

>[!NOTE]
>
>Slechts zal een instantie van AI van de Klant met een status van **Succes** u toestaan om de inzichten van de dienst voor te vertonen.

## Propensiteitsvoorspelling

Laten we nu de voorspelde eigenschappen bekijken die worden gegenereerd door het AI-instantiemodel van de klant. Klik op de instantienaam om het dashboard weer te geven.

![&#x200B; AI &#x200B;](./images/caimodels1.png)

Het AI-dashboard van de Klant geeft een overzicht van de score, de verdeling van de populatie en de invloedrijke factoren voor het model dat moet worden geëvalueerd.

![&#x200B; AI Beschrijving &#x200B;](./images/caidescription.png)

Houd de invloedrijke factoren aan om de verdere uitsplitsing van de gegevensdistributie te bekijken.

![&#x200B; de factoren van de Gevolgen &#x200B;](./images/caiinfluencefactors.png)

## Handelingen

### Klanten segmenteren

Met het AI-dashboard van de Klant kunt u segmenten definiëren met één klik. Klik op **creeer de knoop van het Segment** op de bezitskaarten.

![&#x200B; creeer een segment &#x200B;](./images/caiinfluencefactors1.png)

U zult zien dat een segmentdefinitie automatisch wordt gecreeerd.

![&#x200B; de regel van het Segment &#x200B;](./images/caicreatesegment.png)

Geef het segment een naam die volgt op de naamgevingsconventie: `--aepUserLdap-- - Customer AI High Propensity` . Klik **publiceren**.

![&#x200B; de regel van het Segment &#x200B;](./images/caicreatesegment1.png)

U kunt dit segment nu gebruiken voor de doelversie, bijvoorbeeld Real-time CDP, Journey Optimizer en Adobe Target.

## Opschonen

Om ervoor te zorgen dat er geen onnodige demo-gegevens in uw omgeving worden bewaard, moet u de gegevensset `--aepUserLdap-- - Demo System - Customer Experience Event Dataset` verwijderen nadat u deze bewerking hebt voltooid. Als u de demo-gegevens niet verwijdert, heeft dit een invloed op de kosten van uw AEP-instantie.

![Profiel](./images/cleanup.png)

## Volgende stappen

Ga naar [&#x200B; Samenvatting en voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; Intelligente Diensten &#x200B;](./intelligent-services.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

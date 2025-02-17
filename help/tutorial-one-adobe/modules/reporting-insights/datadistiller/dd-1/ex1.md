---
title: Query-service - Vereisten
description: Query-service - Vereisten
kt: 5342
doc-type: tutorial
exl-id: e9e4d478-cb8d-42a9-87a3-319e5a8b8522
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# 2.1.1 Vereisten

## Hulpprogramma PSQL-opdrachtregel installeren

Volg de instructies in de documentatie van Adobe Experience Platform om de psql cliënt te installeren:
[ PSQL installeert Gids ](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html)

Zodra u PSQL hebt geïnstalleerd, kunt u uw **PAD** moeten bijwerken door het hieronder bevel in een eindvenster in werking te stellen:

Voor macOS (vervang XX in de onderstaande opdracht door het versienummer van de PSQL die u hebt geïnstalleerd):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Power BI installeren

Alleen voor Windows-gebruikers

[ installeer Microsoft Power BI ](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html)

Zorg ervoor dat u de nauwkeurige versie van **npgsql** zoals vermeld op het document installeert, anders zult u geen Power BI met de Dienst van de Vraag van Adobe Experience Platform kunnen verbinden.

## Tableau installeren

Voor Windows- of Mac-gebruikers

[ installeer de Desktop van Tableau ](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html) zoals per de documentatie.

Tableau geeft u automatisch een proefperiode van 14 dagen.

Als u Tableau langer dan die 14 dagen wilt gebruiken, hebt u een licentiecode nodig.

## Volgende stappen

Ga naar [ 2.1.2 Begonnen ](./ex2.md){target="_blank"}

Ga terug naar [ Dienst van de Vraag ](./query-service.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

---
title: Query-service - Vereisten
description: Query-service - Vereisten
kt: 5342
doc-type: tutorial
exl-id: b8a404d1-7796-46e3-b245-553acdc753ae
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# 5.1.1 Vereisten

## Hulpprogramma PSQL-opdrachtregel installeren

Volg de instructies in de documentatie van Adobe Experience Platform om de psql cliënt te installeren:
[&#x200B; PSQL installeert Gids &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html?lang=nl-NL)

Zodra u PSQL hebt geïnstalleerd, kunt u uw **PAD** moeten bijwerken door het hieronder bevel in een eindvenster in werking te stellen:

Voor macOS (vervang XX in de onderstaande opdracht door het versienummer van de PSQL die u hebt geïnstalleerd):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Power BI installeren

Alleen voor Windows-gebruikers

[&#x200B; installeer Microsoft Power BI &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html?lang=nl-NL)

Zorg ervoor dat u de nauwkeurige versie van **npgsql** zoals vermeld op het document installeert, anders zult u geen Power BI met de Dienst van de Vraag van Adobe Experience Platform kunnen verbinden.

## Tableau installeren

Voor Windows- of Mac-gebruikers

[&#x200B; installeer de Desktop van Tableau &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html?lang=nl-NL) zoals per de documentatie.

Tableau geeft u automatisch een proefperiode van 14 dagen.

Als u Tableau langer dan die 14 dagen wilt gebruiken, hebt u een licentiecode nodig.

Volgende Stap: [&#x200B; 5.1.2 Begonnen het worden &#x200B;](./ex2.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

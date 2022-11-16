---
title: Query-service
description: Query-service
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 74943e52-8a7e-4db7-9407-7deeab008fa7
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# 4. Query-service

**Auteurs: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module, zult u een hands-on voorproef van de Dienst van de Vraag van Adobe Experience Platform krijgen. De Dienst van de vraag laat u omnichannel vragen over alle de toepassingsgegevens van Adobe Experience Cloud uitvoeren, die zich bij en het analyseren van gegevens over Adobe Campaign, Analytics, Audience Manager, Doel, en Advertising Cloud aansluiten en andere klantengegevens die in Adobe Experience Platform worden geladen/worden opgenomen.

De Dienst van de vraag is een serverloos hulpmiddel. Het steunt SQL vragen en connectiviteit van veelvoudige cliënttoepassingen door zijn verenigbaarheid PostgreSQL.
Wij zullen gegevens gebruiken die in platform zijn ingespoten gebruikend of de Gegevens van de Interactie van het Web, de Interacties van het Centrum van de Vraag in combinatie met de Gegevens van de Loyalty van de Klant die in platform worden geupload.

## Leerdoelen

- Bekend worden met de gebruikersinterface van Adobe Experience Platform
- Verbinding maken met Query Service en uw SQL-query&#39;s uitvoeren
- Gegevenssets verkennen in Adobe Experience Platform
- Verbind Tableau of Power BI met de Dienst van de Vraag van Adobe Experience Platform om visualisaties en rapporten tot stand te brengen

## Vereisten

- Enige kennis van SQL wordt geprefereerd, maar niet vereist
- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datasets (dataset die tijdens laboratorium wordt gebruikt, voorgeladen voor u)
- PostgreSQL
- Tableau of Microsoft Power BI Desktop
- **Deze middelen downloaden**:
   - [JSON - Voorbeeldgegevens: Interacties op website](./../../assets/json/ee.json)
   - [JSON - Voorbeeldgegevens: Interacties tussen callcenter](./../../assets/json/callcenter.json)
   - [JSON - Voorbeeldgegevens: Loyalty](./../../assets/json/loyalty.json)

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem7.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--module7sandbox--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[4.0 Vereisten](./ex0.md)

U zult PSQL moeten installeren om de vragen in deze enablement oefening uit te voeren. Afhankelijk van uw besturingssysteem moet u Microsoft Power BI of Tableau installeren. Windows-gebruikers kunnen kiezen tussen Power BI of Tableau. Mac-gebruikers moeten Tableau installeren.

[4.1 Aan de slag](./ex1.md)

In deze oefening zult u de Gebruikersinterface van de Dienst van de Vraag van Adobe Experience Platform onderzoeken, over gegevensreeksen leren, uw vragen vinden en tenslotte een verbinding van PSQL opzetten.

[4.2 Het gebruiken van de Dienst van de Vraag](./ex2.md)

In deze oefening zult u over de basissyntaxis van de Dienst van de Vraag leren en u kunt de attributen van het schema XDM in uw vraag identificeren.

[4.3 Vragen, query&#39;s, query&#39;s... en kurkanalyse](./ex3.md)

In deze oefening zult u vragen doen, zult u over de Adobe bepaalde Functies leren terwijl het doen van één of andere kinalyse. Aan het eind van dit zult u een vraag schrijven om een dataset voor gebruik in de Power BI van Microsoft voor te bereiden.

[4.4 Genereer een dataset van een vraag](./ex4.md)

In deze oefening zult u een dataset van een vraag produceren die in het vorige wordt uitgevoerd en u zult deze dataset in de volgende oefeningen gebruiken.

[4.5 Query-service en -Power BI](./ex5.md)

In deze oefening, zult u Power BI met Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie uit te voeren Callcenter.

[4.6 Query-service en Tableau](./ex6.md)

In deze oefening, zult u Tableau aan Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie uit te voeren Callcenter.

[4.7 API voor zoekservice](./ex7.md)

In deze oefening zult u de dienst API van de Vraag gebruiken om vraagmalplaatjes en vraagprogramma&#39;s te beheren.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)

---
title: Query-service
description: Query-service
kt: 5342
doc-type: tutorial
exl-id: 6eb65de3-d0e8-49d4-a702-5c9d6a1952b7
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 1%

---

# 5.1 Query-service

**Auteurs: [ Marc Meewis ](https://www.linkedin.com/in/marcmeewis/), [ Wouter Van Geluwe ](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module, zult u een hands-on voorproef van de Dienst van de Vraag van Adobe Experience Platform krijgen. De Dienst van de vraag laat u omnichannel vragen over alle de toepassingsgegevens van Adobe Experience Cloud uitvoeren, die zich bij en het analyseren van gegevens over Adobe Campaign, Analytics, Audience Manager, Doel, en Advertising Cloud en andere klantengegevens aansluiten geladen/opgenomen in Adobe Experience Platform.

De Dienst van de vraag is een serverloos hulpmiddel. Het steunt SQL vragen en connectiviteit van veelvoudige cliënttoepassingen door zijn verenigbaarheid PostgreSQL.
Wij zullen gegevens gebruiken die in platform zijn ingespoten gebruikend of de Gegevens van de Interactie van het Web, de Interacties van het Centrum van de Vraag in combinatie met de Gegevens van de Loyalty van de Klant die in platform worden geupload.

## Leerdoelen

- Bekend worden met de gebruikersinterface van Adobe Experience Platform
- Verbinding maken met Query Service en uw SQL-query&#39;s uitvoeren
- Gegevenssets verkennen in Adobe Experience Platform
- Connect Tableau of Power BI aan de Adobe Experience Platform Query Service om visualisaties en rapporten te maken

## Vereisten

- Enige vertrouwdheid met SQL wordt geprefereerd maar vereist
- Toegang tot Adobe Experience Platform: [ https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datasets (dataset die tijdens laboratorium wordt gebruikt, voorgeladen voor u)
- PostgreSQL
- Tableau of Microsoft Power BI Desktop
- **Download deze activa**:
   - [JSON - Voorbeeldgegevens: interacties website](./../../../assets/json/ee.json)
   - [JSON - Voorbeeldgegevens: Interacties tussen callcenter](./../../../assets/json/callcenter.json)
   - [JSON - Voorbeeldgegevens: Loyalty](./../../../assets/json/loyalty.json)

>[!NOTE]
>
>Vergeet niet om de Uitbreiding van Chrome te installeren, te vormen en te gebruiken zoals die in [ wordt van verwijzingen voorzien installeer de uitbreiding van Chrome voor de documentatie van het Experience League ](../../gettingstarted/gettingstarted/ex1.md)

## Uitoefening

[5.1.0 Vereisten](./ex0.md)

U zult PSQL moeten installeren om de vragen in deze enablement oefening uit te voeren. Afhankelijk van uw besturingssysteem moet u Microsoft Power BI of Tableau installeren. Windows-gebruikers kunnen kiezen tussen Power BI of Tableau. Mac-gebruikers moeten Tableau installeren.

[5.1.1 Aan de slag](./ex1.md)

In deze oefening zult u de Gebruikersinterface van de Dienst van de Vraag van Adobe Experience Platform onderzoeken, over gegevensreeksen leren, uw vragen vinden en tenslotte een verbinding van PSQL opzetten.

[5.1.2 Het gebruiken van de Dienst van de Vraag](./ex2.md)

In deze oefening zult u over de basissyntaxis van de Dienst van de Vraag leren en u kunt de attributen van het schema XDM in uw vraag identificeren.

[5.1.3 Vragen, query&#39;s, query&#39;s... en churn-analyse](./ex3.md)

In deze oefening zult u vragen doen, zult u over de Adobe Gedefinieerde Functies leren terwijl het doen van één of andere kinalyse. Aan het eind van dit zult u een vraag schrijven om een dataset voor gebruik in de Power BI van Microsoft voor te bereiden.

[5.1.4 Genereer een dataset van een vraag](./ex4.md)

In deze oefening zult u een dataset van een vraag produceren die in het vorige wordt uitgevoerd en u zult deze dataset in de volgende oefeningen gebruiken.

[5.1.5 Query-service en -Power BI](./ex5.md)

In deze oefening, zult u Power BI met Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie uit te voeren Callcenter.

[5.1.6 Query-service en Tableau](./ex6.md)

In deze oefening, zult u Tableau aan Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie van Callcenter uit te voeren.

[5.1.7 API voor Query Service](./ex7.md)

In deze oefening zult u de dienst API van de Vraag gebruiken om vraagmalplaatjes en vraagprogramma&#39;s te beheren.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](../../../overview.md)

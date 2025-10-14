---
title: Query-service
description: Query-service
kt: 5342
doc-type: tutorial
exl-id: 881dcff5-3637-4b67-9e61-88690babe83b
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 1%

---

# 2.1 Query-service

In deze module, zult u een hands-on voorproef van de Dienst van de Vraag van Adobe Experience Platform krijgen. Met Query Service kunt u zoeken in volledige kanalen uitvoeren voor alle Adobe Experience Cloud-toepassingsgegevens, gegevens samenvoegen en analyseren in Adobe Campaign, Analytics, Audience Manager, Target en de Advertising Cloud en andere klantgegevens die in Adobe Experience Platform zijn geladen/ingevoegd.

De Dienst van de vraag is een serverloos hulpmiddel. Het steunt SQL vragen en connectiviteit van veelvoudige cliënttoepassingen door zijn verenigbaarheid PostgreSQL.
Wij zullen gegevens gebruiken die in platform zijn ingespoten gebruikend of de Gegevens van de Interactie van het Web, de Interacties van het Centrum van de Vraag in combinatie met de Gegevens van de Loyalty van de Klant die in platform worden geupload.

## Leerdoelen

- Bekend worden met de gebruikersinterface van Adobe Experience Platform
- Verbinding maken met Query Service en uw SQL-query&#39;s uitvoeren
- Gegevenssets verkennen in Adobe Experience Platform
- Connect Tableau of Power BI aan de Adobe Experience Platform Query Service koppelen om visualisaties en rapporten te maken

## Vereisten

- Enige vertrouwdheid met SQL wordt geprefereerd maar vereist
- Toegang tot Adobe Experience Platform: [&#x200B; https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Datasets (dataset die tijdens laboratorium wordt gebruikt, voorgeladen voor u)
- PostgreSQL
- Tableau of Microsoft Power BI Desktop
- **Download deze activa**:
   - [JSON - Voorbeeldgegevens: interacties website](./../../../../assets/json/ee.json)
   - [JSON - Voorbeeldgegevens: Interacties tussen callcenter](./../../../../assets/json/callcenter.json)
   - [JSON - Voorbeeldgegevens: Loyalty](./../../../../assets/json/loyalty.json)

>[!NOTE]
>
>Vergeet niet om de Uitbreiding van Chrome te installeren, te vormen en te gebruiken zoals die in [&#x200B; wordt van verwijzingen voorzien installeer de uitbreiding van Chrome voor de documentatie van Experience League &#x200B;](../../../getting-started/gettingstarted/ex1.md)

## Uitoefening

[2.1.1 Vereisten](./ex1.md)

U zult PSQL moeten installeren om de vragen in deze enablement oefening uit te voeren. Afhankelijk van uw besturingssysteem moet u Microsoft Power BI of Tableau installeren. Windows-gebruikers kunnen kiezen tussen Power BI of Tableau. Mac-gebruikers moeten Tableau installeren.

[2.1.2 Aan de slag](./ex2.md)

In deze oefening zult u de Gebruikersinterface van de Dienst van de Vraag van Adobe Experience Platform onderzoeken, over gegevensreeksen leren, uw vragen vinden en tenslotte een verbinding van PSQL opzetten.

[2.1.3 Het gebruiken van de Dienst van de Vraag](./ex3.md)

In deze oefening zult u over de basissyntaxis van de Dienst van de Vraag leren en u kunt de attributen van het schema XDM in uw vraag identificeren.

[2.1.4 Vragen, query&#39;s, query&#39;s... en churn-analyse](./ex4.md)

In deze oefening zult u vragen doen, zult u over de Adobe Gedefinieerde Functies leren terwijl het doen van één of andere kinalyse. Aan het eind van dit zult u een vraag schrijven om een dataset voor gebruik in Microsoft Power BI voor te bereiden.

[2.1.5 Genereer een dataset van een vraag](./ex5.md)

In deze oefening zult u een dataset van een vraag produceren die in het vorige wordt uitgevoerd en u zult deze dataset in de volgende oefeningen gebruiken.

[2.1.6 Query-service en Power BI](./ex6.md)

In deze oefening, zult u Power BI met Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie uit te voeren Callcenter.

[2.1.7 Query-service en Tableau](./ex7.md)

In deze oefening, zult u Tableau aan Adobe Experience Platform en de Dienst van de Vraag verbinden om Analyse van de Interactie van Callcenter uit te voeren.

[2.1.8 API voor Query Service](./ex8.md)

In deze oefening zult u de dienst API van de Vraag gebruiken om vraagmalplaatjes en vraagprogramma&#39;s te beheren.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

![&#x200B; Indexen van de Tech &#x200B;](./../../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](./../../../../overview.md)

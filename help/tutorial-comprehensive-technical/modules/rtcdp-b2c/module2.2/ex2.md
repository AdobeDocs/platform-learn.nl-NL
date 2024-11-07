---
title: 'Intelligente services - Klantenservice: AI maakt een nieuw exemplaar (configureren)'
description: Klant-AI - Een nieuwe instantie maken (configureren)
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 2.2.2 Klantenservice-AI - Een nieuw exemplaar maken (configureren)

De AI van de klant werkt door bestaande gegevens van de Gebeurtenis van de Consumentenervaring te analyseren om karn of de scores van de omzetneigheidswaarde te voorspellen. Door een nieuwe AI-instantie van de klant te maken, kunnen marketeers doelstellingen en maatregelen definiëren.

## 2.2.2.1 Een nieuwe AI-instantie van een klant instellen

In Adobe Experience Platform, klik **Diensten** in het linkermenu. De **browser van de Diensten** verschijnt en toont alle beschikbare diensten bij uw beschikking. In de kaart voor Klant AI, klik **Open**.

![ navigatie van de Dienst ](./images/navigatetoservice.png)

Klik **creëren instantie**.

![ creeer nieuwe instantie ](./images/createnewinstance.png)

Dan zie je dit.

![ creeer nieuwe instantie ](./images/custai1.png)

Voer de vereiste gegevens voor de AI-instantie van de Klant in:

- Naam: gebruik `--demoProfileLdap-- Product Purchase Propensity`
- Beschrijving: gebruik: **voorspelt de waarschijnlijkheid voor klanten om een product** te kopen
- Type van Eigenschap: uitgezochte **Omzetting**

![ pagina 1 van de Opstelling ](./images/setuppage1.png)

Klik **daarna**.

![ pagina 1 van de Opstelling ](./images/next.png)

Dan zie je dit. Selecteer de dataset u in de vorige oefening creeerde die `--demoProfileLdap - Demo System - Customer Experience Event Dataset` wordt genoemd. Klik **daarna**.

![ pagina 1 van de Opstelling ](./images/custai2.png)

Selecteer **zal voorkomen** en het gebied **commerce.purchase.value** als doelvariabele bepalen.

![ die het Doel van CAI bepalen ](./images/caidefinegoal.png)

Klik **daarna**.

![ pagina 1 van de Opstelling ](./images/next.png)

Daarna, plaats uw programma om **wekelijks** in werking te stellen en de tijd zo dicht mogelijk aan uw huidige tijd te plaatsen. Zorg ervoor dat de knevel **scores voor Profiel** toelaat wordt toegelaten.

![ bepalen CAI vooruit ](./images/caiadvancepage.png)

Klik **Afwerking**.

![ pagina 1 van de Opstelling ](./images/finish.png)

Dan zie je deze popup. Klik **OK**.

![ pagina 1 van de Opstelling ](./images/finish1.png)

Nadat u het exemplaar vormt, kunt u het in de de instantielijst van de KlantAI zien en ook voorproef de samenvatting van de opstelling en uitvoeringsdetails door op de de instantielijst van de KlantAI te klikken. In het deelvenster Samenvatting worden ook foutgegevens weergegeven voor het geval er fouten zijn gevonden.

![ overzicht van de de opstellingsopstelling van de Instantie ](./images/caiinstancesummary.png)

>[!NOTE]
>
>U kunt om het even welke definitie of attribuut wijzigen zolang de status van uw instantie van de Klant AI of **wachtende opleiding** of **Fout** is

Volgende Stap: [ 2.2.3 Klant AI - het Scoren Dashboard en de Segmentatie (Voorkeur &amp; neem Actie) ](./ex3.md)

[Terug naar module 2.2](./intelligent-services.md)

[Terug naar alle modules](./../../../overview.md)

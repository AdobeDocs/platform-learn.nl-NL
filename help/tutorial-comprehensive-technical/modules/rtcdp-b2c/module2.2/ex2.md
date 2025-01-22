---
title: 'Intelligente services - Klantenservice: AI maakt een nieuw exemplaar (configureren)'
description: Klant-AI - Een nieuwe instantie maken (configureren)
kt: 5342
doc-type: tutorial
exl-id: 067f3fa2-5c1e-4861-b26a-4315cad73a85
source-git-commit: 58e60ad8c83dcd25996e06f11c75f68eae35ef20
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# 2.2.2 Klantenservice-AI - Een nieuw exemplaar maken (configureren)

De AI van de klant werkt door bestaande gegevens van de Gebeurtenis van de Consumentenervaring te analyseren om karn of de scores van de omzetneigheidswaarde te voorspellen. Door een nieuwe AI-instantie van de klant te maken, kunnen marketeers doelstellingen en maatregelen definiëren.

## Nieuwe Customer AI-instantie instellen

In Adobe Experience Platform, klik **Diensten** in het linkermenu. De **browser van de Diensten** verschijnt en toont alle beschikbare diensten bij uw beschikking. In de kaart voor Klant AI, klik **Open**.

![ navigatie van de Dienst ](./images/navigatetoservice.png)

Klik **creëren instantie**.

![ creeer nieuwe instantie ](./images/createnewinstance.png)

Dan zie je dit.

![ creeer nieuwe instantie ](./images/custai1.png)


Voer de vereiste gegevens voor de AI-instantie van de Klant in:

- Naam: gebruik `--aepUserLdap-- Product Purchase Propensity`
- Beschrijving: gebruik: **voorspelt de waarschijnlijkheid voor klanten om een product** te kopen
- Type van Eigenschap: uitgezochte **Omzetting**

Klik **sparen en ga** verder.

![ pagina 1 van de Opstelling ](./images/setuppage1.png)

Dan zie je dit. Selecteer de dataset u in de vorige oefening creeerde die `--aepUserLdap-- - Demo System - Customer Experience Event Dataset` wordt genoemd. Klik **toevoegen**.

![ pagina 1 van de Opstelling ](./images/custai2.png)

Dan zie je dit. u moet het **gebied van de Identiteit** bepalen. Klik **niets**.

![ pagina 1 van de Opstelling ](./images/custai2a.png)

In popup, uitgezochte **Identiteitskaart (identityMap)** en selecteer dan het namespace **Systeem van de Demo - CRMID (crmId)**. Daarna, klik **sparen**.

![ pagina 1 van de Opstelling ](./images/custai2b.png)

Klik **sparen en ga** verder.

![ pagina 1 van de Opstelling ](./images/custai2c.png)

Selecteer **zal voorkomen** in uw specifieke dataset, en bepaalt het gebied **commerce.purchase.value** als doelvariabele.

![ die het Doel van CAI bepalen ](./images/caidefinegoal.png)

Daarna, plaats uw programma om **wekelijks** in werking te stellen en de tijd zo dicht mogelijk aan uw huidige tijd te plaatsen. Zorg ervoor dat de knevel **scores voor Profiel** toelaat wordt toegelaten. Klik **sparen en ga** verder.

![ bepalen CAI vooruit ](./images/caiadvancepage.png)

Nadat u het exemplaar vormt, kunt u het in de de dienstlijst van AI van de Klant zien en u kunt de samenvatting van de opstelling en uitvoeringsdetails ook voorproef door op de de instantielijst van de KlantAI te klikken. In het deelvenster Samenvatting worden ook foutgegevens weergegeven voor het geval er fouten zijn gevonden.

![ overzicht van de de opstellingsopstelling van de Instantie ](./images/caiinstancesummary.png)

>[!NOTE]
>
>U kunt om het even welke definitie of attribuut wijzigen zolang de status van uw instantie van de Klant AI of **wachtende opleiding** of **Fout** is

Als je model eenmaal is uitgevoerd, zie je dit.

![ overzicht van de de opstellingsopstelling van de Instantie ](./images/caiinstancesummary1.png)


Volgende Stap: [ 2.2.3 Klant AI - het Scoren Dashboard en de Segmentatie (Voorkeur &amp; neem Actie) ](./ex3.md)

[Terug naar module 2.2](./intelligent-services.md)

[Terug naar alle modules](./../../../overview.md)

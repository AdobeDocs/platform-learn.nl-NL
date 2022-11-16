---
title: De Dienst van de vraag - Onderzoek de dataset met Power BI
description: De Dienst van de vraag - Onderzoek de dataset met Power BI
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 0f9e6719-056b-4858-8c86-04b3beaa950e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 4.5 Query-service en -Power BI

Open Microsoft Power BI Desktop.

![start-power-bi.png](./images/start-power-bi.png)

Klikken **Gegevens ophalen**.

![power-bi-get-data.png](./images/power-bi-get-data.png)

Zoeken naar **postzegels** (1) selecteert u **Postgres** , lid 2, van de lijst en **Verbinden** (3)

![power-bi-connect-progress.png](./images/power-bi-connect-progress.png)

Ga naar Adobe Experience Platform, naar **Zoekopdrachten** en **Credentials**.

![query-service-credentials.png](./images/query-service-credentials.png)

Van de **Credentials** pagina in Adobe Experience Platform, kopieer de **Host** en plak deze in het dialoogvenster **Server** en kopieer de **Database** en plak deze in het dialoogvenster **Database** in PowerBI en klik vervolgens op OK (2).

>[!IMPORTANT]
>
>Zorg ervoor dat u de poort opneemt **:80** aan het eind van de waarde van de Server omdat de Dienst van de Vraag momenteel niet de standaard haven PostgreSQL van 5432 gebruikt.

![power-bi-connect-server.png](./images/power-bi-connect-server.png)

In het volgende dialoogvenster vult u de gebruikersnaam en het wachtwoord in met uw gebruikersnaam en wachtwoord in het dialoogvenster **Credentials** van query&#39;s in Adobe Experience Platform.

![query-service-credentials.png](./images/query-service-credentials.png)

Plaats uw **LDAP** in het onderzoeksgebied (1) om van uw datasets CTAS de plaats te bepalen en het vakje naast elk (2) te controleren. Klik vervolgens op Laden (3).

![power-bi-load-churn-data.png](./images/power-bi-load-churn-data.png)

Zorg ervoor dat de **Rapport** tab (1) is geselecteerd.

![power-bi-report-tab.png](./images/power-bi-report-tab.png)

Selecteer de kaart (1) en vergroot de kaart (2) nadat deze aan het rapportcanvas is toegevoegd.

![power-bi-select-map.png](./images/power-bi-select-map.png)

Vervolgens moeten de maatregelen en de afmetingen worden gedefinieerd. U doet dit door velden te slepen van de **velden** op de bijbehorende plaatsaanduidingen (onder **visualisatie**) zoals hieronder aangegeven:

![power-bi-drag-lat-lon.png](./images/power-bi-drag-lat-lon.png)

Als maatstaf gebruiken we een telling van **customerId**. Sleep de **crmid** veld van **velden** in de **Grootte** tijdelijke aanduiding:

![power-bi-drag-crmid.png](./images/power-bi-drag-crmid.png)

Tot slot, om wat te doen **callTopic** analyse, laten wij slepen **callTopic** aan de **Filters op paginaniveau** plaatsaanduiding (u moet mogelijk in het dialoogvenster **visualisatie** deel);

![power-bi-drag-calltopic.png](./images/power-bi-drag-calltopic.png)

Selecteren/deselecteren **callTopics** om te onderzoeken:

![power-bi-report-select-calltopic.png](./images/power-bi-report-select-calltopic.png)

Je hebt deze oefening nu afgerond.

Volgende stap: [4.7 API voor zoekservice](./ex7.md)

[Ga terug naar module 4](./query-service.md)

[Terug naar alle modules](../../overview.md)

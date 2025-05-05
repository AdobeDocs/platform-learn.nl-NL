---
title: De Dienst van de vraag - Onderzoek de dataset met Power BI
description: De Dienst van de vraag - Onderzoek de dataset met Power BI
kt: 5342
doc-type: tutorial
exl-id: c27abd0e-e563-4702-a243-1aec84ce6116
source-git-commit: f843c50af04d744a7d769f320b5b55a5e6d25ffd
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 5.1.6 Query-service en -Power BI

Open Microsoft Power BI Desktop.

![ start-power-bi.png ](./images/startpowerbi.png)

Klik **krijgen Gegevens**.

![ macht-bi-get-data.png ](./images/powerbigetdata.png)

Onderzoek naar **postgres** (1), uitgezochte **Postgres** (2) van de lijst en **verbindt** (3).

![ macht-bi-connect-progress.png ](./images/powerbiconnectprogress.png)

Ga naar Adobe Experience Platform, aan **Vragen** en aan **Geloofsbrieven**.

![ vraag-dienst-credentials.png ](./images/queryservicecredentials.png)

Van de **pagina van Referenties** in Adobe Experience Platform, kopieer de **Gastheer** en kleef het op het **gebied van de Server**, en kopieer het **Gegevensbestand** en kleef het in het **Gegevensbestand** gebied in PowerBI, dan klik O.K. (2).

>[!IMPORTANT]
>
>Zorg ervoor om haven **te omvatten:80** aan het eind van de waarde van de Server omdat de Dienst van de Vraag momenteel niet de standaard haven PostgreSQL van 5432 gebruikt.

![ macht-bi-connect-server.png ](./images/powerbiconnectserver.png)

In de volgende dialoog bevolkt de naam en het Wachtwoord van de Gebruiker met uw Gebruikersnaam en Wachtwoord dat in **wordt gevonden Referenties** van Vragen in Adobe Experience Platform.

![ vraag-dienst-credentials.png ](./images/queryservicecredentials.png)

In de dialoog van de Navigator, zet uw **LDAP** op het onderzoeksgebied (1) om van uw datasets CTAS de plaats te bepalen en de doos naast elk (2) te controleren. Klik vervolgens op Laden (3).

![ macht-bi-lading-churn-data.png ](./images/powerbiloadchurndata.png)

Zorg ervoor het **lusje van het 0&rbrace; Rapport** (1) wordt geselecteerd.

![ macht-bi-rapport-tab.png ](./images/powerbireporttab.png)

Selecteer de kaart (1) en vergroot de kaart (2) nadat deze aan het rapportcanvas is toegevoegd.

![ macht-bi-select-map.png ](./images/powerbiselectmap.png)

Daarna moeten wij de maatregelen en de afmetingen bepalen, doet u dit door gebieden van de **gebieden** sectie op de overeenkomstige placeholders (die onder **worden gevestigd visualisaties**) te slepen zoals hieronder vermeld:

![ macht-bi-belemmering-lat-lon.png ](./images/powerbidraglatlon.png)

Als maatregel zullen wij een telling van **customerId** gebruiken. Sleep het **midden** gebied van de **gebieden** sectie in **placeholder van de Grootte**:

![ macht-bi-belemmering-crmid.png ](./images/powerbidragcrmid.png)

Tot slot om wat **callTopic** analyse te doen, versleep het **callTopic** gebied op **de filters van het paginaniveau** placeholder (u zou in de **visualisaties** sectie kunnen moeten scrollen);

![ macht-bi-belemmering-calltopic.png ](./images/powerbidragcalltopic.png)

Selecteer/unselect **callTopics** om te onderzoeken:

![ macht-bi-rapport-select-calltopic.png ](./images/powerbireportselectcalltopic.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 5.1.8 de Dienst API van de Vraag ](./ex8.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

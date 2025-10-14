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

![&#x200B; start-power-bi.png &#x200B;](./images/startpowerbi.png)

Klik **krijgen Gegevens**.

![&#x200B; macht-bi-get-data.png &#x200B;](./images/powerbigetdata.png)

Onderzoek naar **postgres** (1), uitgezochte **Postgres** (2) van de lijst en **verbindt** (3).

![&#x200B; macht-bi-connect-progress.png &#x200B;](./images/powerbiconnectprogress.png)

Ga naar Adobe Experience Platform, aan **Vragen** en aan **Geloofsbrieven**.

![&#x200B; vraag-dienst-credentials.png &#x200B;](./images/queryservicecredentials.png)

Van de **pagina van Referenties** in Adobe Experience Platform, kopieer de **Gastheer** en kleef het op het **gebied van de Server**, en kopieer het **Gegevensbestand** en kleef het in het **Gegevensbestand** gebied in PowerBI, dan klik O.K. (2).

>[!IMPORTANT]
>
>Zorg ervoor om haven **te omvatten:80** aan het eind van de waarde van de Server omdat de Dienst van de Vraag momenteel niet de standaard haven PostgreSQL van 5432 gebruikt.

![&#x200B; macht-bi-connect-server.png &#x200B;](./images/powerbiconnectserver.png)

In de volgende dialoog bevolkt de naam en het Wachtwoord van de Gebruiker met uw Gebruikersnaam en Wachtwoord dat in **wordt gevonden Referenties** van Vragen in Adobe Experience Platform.

![&#x200B; vraag-dienst-credentials.png &#x200B;](./images/queryservicecredentials.png)

In de dialoog van de Navigator, zet uw **LDAP** op het onderzoeksgebied (1) om van uw datasets CTAS de plaats te bepalen en de doos naast elk (2) te controleren. Klik vervolgens op Laden (3).

![&#x200B; macht-bi-lading-churn-data.png &#x200B;](./images/powerbiloadchurndata.png)

Zorg ervoor het **lusje van het 0&rbrace; Rapport** (1) wordt geselecteerd.

![&#x200B; macht-bi-rapport-tab.png &#x200B;](./images/powerbireporttab.png)

Selecteer de kaart (1) en vergroot de kaart (2) nadat deze aan het rapportcanvas is toegevoegd.

![&#x200B; macht-bi-select-map.png &#x200B;](./images/powerbiselectmap.png)

Daarna moeten wij de maatregelen en de afmetingen bepalen, doet u dit door gebieden van de **gebieden** sectie op de overeenkomstige placeholders (die onder **worden gevestigd visualisaties**) te slepen zoals hieronder vermeld:

![&#x200B; macht-bi-belemmering-lat-lon.png &#x200B;](./images/powerbidraglatlon.png)

Als maatregel zullen wij een telling van **customerId** gebruiken. Sleep het **midden** gebied van de **gebieden** sectie in **placeholder van de Grootte**:

![&#x200B; macht-bi-belemmering-crmid.png &#x200B;](./images/powerbidragcrmid.png)

Tot slot om wat **callTopic** analyse te doen, versleep het **callTopic** gebied op **de filters van het paginaniveau** placeholder (u zou in de **visualisaties** sectie kunnen moeten scrollen);

![&#x200B; macht-bi-belemmering-calltopic.png &#x200B;](./images/powerbidragcalltopic.png)

Selecteer/unselect **callTopics** om te onderzoeken:

![&#x200B; macht-bi-rapport-select-calltopic.png &#x200B;](./images/powerbireportselectcalltopic.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [&#x200B; 5.1.8 de Dienst API van de Vraag &#x200B;](./ex8.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

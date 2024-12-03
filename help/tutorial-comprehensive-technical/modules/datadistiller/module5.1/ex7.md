---
title: De Dienst van de vraag - Onderzoek de dataset met Tableau
description: De Dienst van de vraag - Onderzoek de dataset met Tableau
kt: 5342
doc-type: tutorial
exl-id: 29525740-fe1f-4770-bcc9-f2ad499a2cb5
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 5.1.7 Query-service en Tableau

Open Tabel.

![ start-tableau.png ](./images/start-tableau.png)

In **verbind met een Server** uitgezocht **PostgreSQL**:

![ tableau-connect-postgress.png ](./images/tableau-connect-postgress.png)

Ga naar Adobe Experience Platform, aan **Vragen** en aan **Geloofsbrieven**.

![ vraag-dienst-credentials.png ](./images/query-service-credentials.png)

Van de **Credentials** pagina in Adobe Experience Platform, kopieer de **Gastheer** en kleef het in het **gebied van de Server**, kopieer het **Gegevensbestand** en kleef het in het **Gegevensbestand** gebied in Tableau, kopieer de **Haven** en kleef het op het gebied **in Tableau, doe het zelfde voor** Gebruikersnaam **en** Wachtwoord **.** Daarna, klik **Teken binnen**.

Aanmelden:

![ tableau-connection-dialog.png ](./images/tableau-connection-dialog.png)

Klik onderzoek (1) en ga uw **ldap** in het onderzoeksgebied in, identificeer u lijst van de resultaatreeks en sleep (3) het op de plaats genoemd **hier van de Belemmering lijsten**. Wanneer gebeëindigd, klik op **Blad 1** (3).

![ tableau-drag-table.png ](./images/tableau-drag-table.png)

Om onze gegevens op de kaart zichtbaar te maken, moeten we lengte en breedte in dimensies omzetten. In **Maatregelen** selecteer **Breedte** (1) en open dropdown van het gebied en selecteer **Bekeerling in Dimension** (2). Doe het zelfde voor de **maatregel van de Lengte 0} {.**

![ tableau-convert-Dimension.png ](./images/tableau-convert-dimension.png)

Sleep de **maatregel van de Lengte** {aan de **Kolommen** en de **5} maatregel van de Breedte {aan** Rijen **.** Automatisch zal de kaart van **België** met weinig punten verschijnen die de steden in uit gegevensreeks vertegenwoordigen.

![ tableau-drag-lon-lat.png ](./images/tableau-drag-lon-lat.png)

Selecteer **Namen van de Maatregel** (1), open dropdown en selecteer **toevoegen aan Blad** (2):

![ tab-select-maatregel-names.png ](./images/tableau-select-measure-names.png)

Nu heb je een kaart met puntjes van verschillende grootten. De grootte wijst op het aantal interactie van het vraagcentrum voor die specifieke stad. Om de grootte van de punten te variëren, navigeer aan het juiste paneel en open **Waarden van de Maatregel** (gebruikend het drop-down pictogram). Van de drop-down lijst uitgezocht **geeft Grootte** uit. Speel rond met verschillende grootten.

![ tableau-variatie-size-dots.png ](./images/tableau-vary-size-dots.png)

Om de gegevens per **Onderwerp van de Vraag** verder te tonen, sleep (1) de **3} dimensie van het Onderwerp van de Vraag {op** Pagina&#39;s **.** Navigeer door de verschillende **onderwerpen van de Vraag** gebruikend het **Onderwerp van de Vraag** (2) op de rechterkant van het scherm:

![ tableau-call-topic-navigation.png ](./images/tableau-call-topic-navigation.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 5.1.8 de Dienst API van de Vraag ](./ex8.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

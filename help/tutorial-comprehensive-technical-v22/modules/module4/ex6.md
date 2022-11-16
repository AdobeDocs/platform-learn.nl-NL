---
title: De Dienst van de vraag - Onderzoek de dataset met Tableau
description: De Dienst van de vraag - Onderzoek de dataset met Tableau
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 04209eb4-b054-4a2e-885e-61f601c3fc2c
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 4.6 Query-service en Tableau

Open Tableau.

![start-tableau.png](./images/start-tableau.png)

In **Verbinding maken met een server** selecteren **PostgreSQL**:

![tableau-connect-postgress.png](./images/tableau-connect-postgress.png)

Ga naar Adobe Experience Platform, naar **Zoekopdrachten** en **Credentials**.

![query-service-credentials.png](./images/query-service-credentials.png)

Van de **Credentials** pagina in Adobe Experience Platform, kopieer de **Host** en plak deze in het dialoogvenster **Server** veld, kopieert u de **Database** en plak deze in het dialoogvenster **Database** in Tableau, kopieer de **Poort** en plak deze in het veld **Poort** in Tableau, doe het zelfde voor **Gebruikersnaam** en **Wachtwoord**. Klik op Volgende **Aanmelden**.

Aanmelden:

![tableau-connection-dialog.png](./images/tableau-connection-dialog.png)

Klik op Zoeken (1) en voer uw **ldap** in het zoekveld, identificeer u de tabel uit de resultatenset en sleep deze (3) naar de benoemde locatie **Tabellen hierheen slepen**. Klik op Als u klaar bent **Blad 1** (3)

![tableau-drag-table.png](./images/tableau-drag-table.png)

Om onze gegevens op de kaart zichtbaar te maken, moeten we lengte en breedte in dimensies omzetten. In **Maatregelen** selecteren **Breedte** (1) en opent u het vervolgkeuzemenu van het veld en selecteert u **Omzetten in Dimension** (2) Doe het zelfde voor **Lengtegraad** meten.

![tableau-convert-dimensie.png](./images/tableau-convert-dimension.png)

Sleep de **Lengtegraad** aan de **Kolommen** en de **Breedte** meten tot **Rijen**. Automatisch de kaart van **België** worden weergegeven met kleine puntjes die de steden in de gegevensset weergeven.

![tableau-drag-lon-lat.png](./images/tableau-drag-lon-lat.png)

Selecteren **Namen meten** (1), opent u het vervolgkeuzemenu en selecteert u **Toevoegen aan werkblad** (2)

![tableau-select-measurement-names.png](./images/tableau-select-measure-names.png)

Nu heb je een kaart met puntjes van verschillende grootten. De grootte wijst op het aantal interactie van het vraagcentrum voor die specifieke stad. Als u de grootte van de stippen wilt wijzigen, navigeert u naar het rechterdeelvenster en opent u **Waarden meten** (met het vervolgkeuzepictogram). Selecteer in de vervolgkeuzelijst de optie **Grootten bewerken**. Speel rond met verschillende grootten.

![table-variate-size-dots.png](./images/tableau-vary-size-dots.png)

De gegevens verder weergeven per **Het Onderwerp van de vraag**, sleep (1) de **Het Onderwerp van de vraag** dimensie op **Pagina&#39;s**. Navigeren door de verschillende **Onderwerpen bellen** met de **Het Onderwerp van de vraag** (2) aan de rechterkant van het scherm:

![tableau-call-topic-navigation.png](./images/tableau-call-topic-navigation.png)

Je hebt deze oefening nu afgerond.

Volgende stap: [4.7 API voor zoekservice](./ex7.md)

[Ga terug naar module 4](./query-service.md)

[Terug naar alle modules](../../overview.md)

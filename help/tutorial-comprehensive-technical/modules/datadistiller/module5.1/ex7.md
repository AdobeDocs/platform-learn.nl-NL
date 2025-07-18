---
title: De Dienst van de vraag - Onderzoek de dataset met Tableau
description: De Dienst van de vraag - Onderzoek de dataset met Tableau
kt: 5342
doc-type: tutorial
exl-id: 29525740-fe1f-4770-bcc9-f2ad499a2cb5
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 5.1.7 Query-service en Tableau

Open Tabel.

![ start-tableau.png ](./images/starttableau.png)

In **verbind met een Server**, klik **Meer** en klik dan **PostgreSQL**.

![ tableau-connect-postgress.png ](./images/tableauconnectpostgress.png)

Als u PostgeSQL nog niet met Tableau hebt gebruikt, kunt u dit zien. Klik **Bestuurder van de Download**.

![ tableau-connect-postgress.png ](./images/tableauconnectpostgress1.png)

Volg de instructies om het PostgreSQL-stuurprogramma te downloaden en installeren.

![ tableau-connect-postgress.png ](./images/tableauconnectpostgress2.png)

Als u klaar bent met de installatie van het stuurprogramma, sluit u Tableau Desktop af en start u deze opnieuw. Dan na het nieuwe begin, ga **met een Server** opnieuw verbinden, klik **Meer** en klik dan **PostgreSQL** opnieuw.

![ tableau-connect-postgress.png ](./images/tableauconnectpostgress.png)

Dan zie je dit.

![ tableau-connect-postgress.png ](./images/tableauconnectpostgress3.png)

Ga naar Adobe Experience Platform, aan **Vragen** en aan **Geloofsbrieven**.

![ vraag-dienst-credentials.png ](./images/queryservicecredentials.png)

Van de **Credentials** pagina in Adobe Experience Platform, kopieer de **Gastheer** en kleef het in het **gebied van de Server**, kopieer het **Gegevensbestand** en kleef het in het **Gegevensbestand** gebied in Tableau, kopieer de **Haven** en kleef het op het gebied **in Tableau, doe het zelfde voor** Gebruikersnaam **en** Wachtwoord **.** Daarna, klik **Teken binnen**.

![ tableau-connection-dialog.png ](./images/tableauconnectiondialog.png)

Zoek in de lijst met beschikbare tabellen de tabel die u in de vorige exercitie hebt gemaakt. Deze tabel wordt `--aepUserLdap--_callcenter_interaction_analysis` genoemd. Sleep het naar het canvas.

![ tableau-drag-table.png ](./images/tableaudragtable.png)

Dan zie je dit. Klik **Update nu**.

![ tableau-drag-table.png ](./images/tableaudragtable1.png)

Vervolgens ziet u de gegevens van AEP beschikbaar komen in Tableau. Klik **Blad 1** beginnen met het werken met de gegevens.

![ tableau-drag-table.png ](./images/tableaudragtable2.png)

Om uw gegevens op de kaart zichtbaar te maken, moet u lengte en breedte in dimensies omzetten. In **Maatregelen**, klik **Breedte** met de rechtermuisknop aan, uitgezochte **Bekeerling in Dimension** in het menu. Doe het zelfde voor de **maatregel van de Lengte 0&rbrace; &lbrace;.**

![ tableau-convert-Dimension.png ](./images/tableauconvertdimension.png)

Sleep de **maatregel van de Lengte** {aan de **Kolommen** en de **5} maatregel van de Breedte &lbrace;aan** Rijen **.** Automatisch zal de kaart van **België** met weinig punten verschijnen die de steden in uit gegevensreeks vertegenwoordigen.

![ tableau-drag-lon-lat.png ](./images/tableaudraglonlat.png)

Selecteer **Namen van de Maatregel**, klik **toevoegen aan Blad**.

![ tab-select-maatregel-names.png ](./images/selectmeasurenames.png)

Nu heb je een kaart met puntjes van verschillende grootten. De grootte wijst op het aantal interactie van het vraagcentrum voor die specifieke stad. Om de grootte van de punten te variëren, navigeer aan het juiste paneel en open **Waarden van de Maatregel** (gebruikend het drop-down pictogram). Van de drop-down lijst uitgezocht **geeft Grootte** uit. Speel rond met verschillende grootten.

![ tableau-variatie-size-dots.png ](./images/tableauvarysizedots.png)

Om de gegevens per **Onderwerp van de Vraag** verder te tonen, sleep het **Onderwerp van de Vraag** dimensie op **Pagina&#39;s**. Navigeer door de verschillende **onderwerpen van de Vraag** gebruikend het **Onderwerp van de Vraag** op de rechterkant van het scherm:

![ tableau-call-topic-navigation.png ](./images/tableaucalltopicnavigation.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 5.1.8 de Dienst API van de Vraag ](./ex8.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)

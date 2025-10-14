---
title: De Dienst van de vraag - Onderzoek de dataset met Tableau
description: De Dienst van de vraag - Onderzoek de dataset met Tableau
kt: 5342
doc-type: tutorial
exl-id: 33ab854d-fad7-497c-affa-f58e4299c0b3
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# 2.1.7 Query-service en Tableau

Open Tabel.

![&#x200B; start-tableau.png &#x200B;](./images/starttableau.png)

In **verbind met een Server**, klik **Meer** en klik dan **PostgreSQL**.

![&#x200B; tableau-connect-postgress.png &#x200B;](./images/tableauconnectpostgress.png)

Als u PostgeSQL nog niet met Tableau hebt gebruikt, kunt u dit zien. Klik **Bestuurder van de Download**.

![&#x200B; tableau-connect-postgress.png &#x200B;](./images/tableauconnectpostgress1.png)

Volg de instructies om het PostgreSQL-stuurprogramma te downloaden en installeren.

![&#x200B; tableau-connect-postgress.png &#x200B;](./images/tableauconnectpostgress2.png)

Als u klaar bent met de installatie van het stuurprogramma, sluit u Tableau Desktop af en start u deze opnieuw. Dan na het nieuwe begin, ga **met een Server** opnieuw verbinden, klik **Meer** en klik dan **PostgreSQL** opnieuw.

![&#x200B; tableau-connect-postgress.png &#x200B;](./images/tableauconnectpostgress.png)

Dan zie je dit.

![&#x200B; tableau-connect-postgress.png &#x200B;](./images/tableauconnectpostgress3.png)

Ga naar Adobe Experience Platform, aan **Vragen** en aan **Geloofsbrieven**.

![&#x200B; vraag-dienst-credentials.png &#x200B;](./images/queryservicecredentials.png)

Van de **Credentials** pagina in Adobe Experience Platform, kopieer de **Gastheer** en kleef het in het **gebied van de Server**, kopieer het **Gegevensbestand** en kleef het in het **Gegevensbestand** gebied in Tableau, kopieer de **Haven** en kleef het op het gebied **in Tableau, doe het zelfde voor** Gebruikersnaam **en** Wachtwoord **.** Daarna, klik **Teken binnen**.

![&#x200B; tableau-connection-dialog.png &#x200B;](./images/tableauconnectiondialog.png)

Zoek in de lijst met beschikbare tabellen de tabel die u in de vorige exercitie hebt gemaakt. Deze tabel wordt `--aepUserLdap--_callcenter_interaction_analysis` genoemd. Sleep het naar het canvas.

![&#x200B; tableau-drag-table.png &#x200B;](./images/tableaudragtable.png)

Dan zie je dit. Klik **Update nu**.

![&#x200B; tableau-drag-table.png &#x200B;](./images/tableaudragtable1.png)

Vervolgens ziet u de gegevens van AEP beschikbaar komen in Tableau. Klik **Blad 1** beginnen met het werken met de gegevens.

![&#x200B; tableau-drag-table.png &#x200B;](./images/tableaudragtable2.png)

Om uw gegevens op de kaart zichtbaar te maken, moet u lengte en breedte in dimensies omzetten. In **Maatregelen**, klik **Breedte** met de rechtermuisknop aan, uitgezochte **Bekeerling aan Dimension** in het menu. Doe het zelfde voor de **maatregel van de Lengte 0&rbrace; &lbrace;.**

![&#x200B; tableau-convert-Dimension.png &#x200B;](./images/tableauconvertdimension.png)

Sleep de **maatregel van de Lengte** {aan de **Kolommen** en de **5} maatregel van de Breedte &lbrace;aan** Rijen **.** Automatisch zal de kaart van **België** met weinig punten verschijnen die de steden in uit gegevensreeks vertegenwoordigen.

![&#x200B; tableau-drag-lon-lat.png &#x200B;](./images/tableaudraglonlat.png)

Selecteer **Namen van de Maatregel**, klik **toevoegen aan Blad**.

![&#x200B; tab-select-maatregel-names.png &#x200B;](./images/selectmeasurenames.png)

Nu heb je een kaart met puntjes van verschillende grootten. De grootte wijst op het aantal interactie van het vraagcentrum voor die specifieke stad. Om de grootte van de punten te variëren, navigeer aan het juiste paneel en open **Waarden van de Maatregel** (gebruikend het drop-down pictogram). Van de drop-down lijst uitgezocht **geeft Grootte** uit. Speel rond met verschillende grootten.

![&#x200B; tableau-variatie-size-dots.png &#x200B;](./images/tableauvarysizedots.png)

Om de gegevens per **Onderwerp van de Vraag** verder te tonen, sleep het **Onderwerp van de Vraag** dimensie op **Pagina&#39;s**. Navigeer door de verschillende **onderwerpen van de Vraag** gebruikend het **Onderwerp van de Vraag** op de rechterkant van het scherm:

![&#x200B; tableau-call-topic-navigation.png &#x200B;](./images/tableaucalltopicnavigation.png)

Je hebt deze oefening nu afgerond.

## Volgende stappen

Ga naar [&#x200B; 2.1.8 API van de Dienst van de Vraag &#x200B;](./ex8.md){target="_blank"}

Ga terug naar [&#x200B; Dienst van de Vraag &#x200B;](./query-service.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

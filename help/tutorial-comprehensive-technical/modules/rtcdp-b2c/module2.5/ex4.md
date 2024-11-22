---
title: Gegevensverzameling en doorsturen aan serverzijde in realtime - Een Google Cloud-functie maken en configureren
description: Google Cloud Function maken en configureren
kt: 5342
doc-type: tutorial
exl-id: ee73ce3a-baaa-432a-9626-249be9aaeff2
source-git-commit: c0537545e4a5d1f1ca21a13d934eb965a4f3aa66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 2.5.4 Voorwaartse gebeurtenissen naar GCP Pub/Sub

>[!NOTE]
>
>Hiervoor hebt u toegang nodig tot een Google Cloud Platform-omgeving. Als u nog geen toegang hebt tot GCP, maakt u een nieuw account met uw persoonlijke e-mailadres.

## Een Google Cloud Pub/Subonderwerp maken

Ga naar [ https://console.cloud.google.com/ ](https://console.cloud.google.com/). Typ `pub/sub` in de zoekbalk. Klik het onderzoeksresultaat **Pub/Sub - Globaal overseinen in real time**.

![ GCP ](./images/gcp1.png)

Dan zie je dit. Klik **CREËREN ONDERWERP**.

![ GCP ](./images/gcp2.png)

Dan zie je dit. Gebruik `--aepUserLdap---event-forwarding` voor uw onderwerpid. Klik **creëren**.

![ GCP ](./images/gcp6.png)

Uw onderwerp is nu gemaakt. Klik identiteitskaart van het Abonnement van het onderwerp ****.

![ GCP ](./images/gcp7.png)

Dan zie je dit. Kopieer de **naam van het Onderwerp** aan uw klembord en sla het op, aangezien u het in de volgende oefeningen zult nodig hebben.

![ GCP ](./images/gcp8.png)

Laten we nu naar Adobe Experience Platform Data Collection Event Forwarding gaan om uw Event Forwarding-eigenschap bij te werken om gebeurtenissen naar Pub/Sub door:sturen.


## Werk uw Event Forwarding-eigenschap bij: geheimen

**Geheimen** in Gebeurtenis Door:sturen eigenschappen worden gebruikt om geloofsbrieven op te slaan die zullen worden gebruikt om tegen externe API&#39;s voor authentiek te verklaren. In dit voorbeeld moet u een geheim configureren voor het opslaan van het OAuth-token van het Google Cloud-platform. Dit wordt gebruikt voor verificatie bij het gebruik van Pub/Sub voor het streamen van gegevens naar GCP.

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/) en ga naar **Geheimen**. Klik **creëren Nieuw Geheim**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret1.png)

Dan zie je dit. Volg deze instructies:

- Naam: gebruik `--aepUserLdap---gcp-secret`
- Het Milieu van het doel: uitgezochte **Ontwikkeling**
- Type: **Google OAuth 2**
- Controle checkbox voor **Pub/Sub**

Klik **creeer Geheim**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret2.png)

Na het klikken **creeer Geheim**, zult u popup aan opstelling zien de authentificatie tussen het geheim van uw Gebeurtenis door:sturen bezit en Google. Klik **creeer en geef geheim `--aepUserLdap---gcp-secret` met Google** toe.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret3.png)

Klik om je Google-account te selecteren.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret4.png)

Klik **verdergaan**.

>[!NOTE]
>
>Het pop-upbericht kan afwijken. Toestaan of geef de gevraagde toegang om door te gaan met de oefening.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret5.png)

Na succesvolle authentificatie, zult u dit zien.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret6.png)

Uw geheim wordt nu met succes gevormd en kan in een gegevenselement worden gebruikt.

## Werk uw Event Forwarding-eigenschap bij: Data Element

Om uw geheim in uw Gebeurtenis te gebruiken die bezit door:sturen, moet u een gegevenselement tot stand brengen dat de waarde van het geheim zal opslaan.

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/) en ga naar **Gebeurtenis door:sturen**. Zoek in de eigenschap Event Forwarding en klik erop om deze te openen.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/prop1.png)

In het linkermenu, ga naar **Elementen van Gegevens**. Klik **toevoegen het Element van Gegevens**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/de1gcp.png)

Configureer uw gegevenselement als volgt:

- Naam: **Geheime GCP**
- Uitbreiding: **Kern**
- Het Type van Element van gegevens: **Geheim**
- Ontwikkelingsgeheim: selecteer het geheim dat u hebt gemaakt en dat de naam `--aepUserLdap---gcp-secret` heeft

Klik **sparen**

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/secret7.png)

## Update your Event Forwarding property: Extension

Als uw Geheim en Gegevenselement zijn geconfigureerd, kunt u nu de extensie voor Google Cloud Platform instellen in uw eigenschap voor het doorsturen van gebeurtenissen.

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/), ga **Gebeurtenis door:sturen** en open uw Gebeurtenis door:sturen bezit.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/prop1.png)

Daarna, ga naar **Uitbreidingen**, aan **Catalogus**. Klik de **uitbreiding van het Platform van de Wolk van Google** en klik **installeren**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/gext2.png)

Dan zie je dit. Klik op het pictogram Gegevenselement.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/gext3.png)

Selecteer het gegevenselement u in de vorige oefening creeerde, die **Geheime GCP** wordt genoemd. Klik **Uitgezocht**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/gext4.png)

Dan zie je dit. Klik **sparen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/gext5.png)

## Werk uw Gebeurtenis door:sturen bezit bij: Werk een Regel bij

Nu uw uitbreiding van het Platform van Google Cloud wordt gevormd, kunt u een regel bepalen beginnen gebeurtenisgegevens aan uw Pub/Subtopic door:sturen. Om dat te doen, zult u uw **Alle Pagina&#39;s** regel moeten bijwerken die u in één van de vorige oefeningen creeerde.

In het linkermenu, ga naar **Regels**. In de vorige oefening, creeerde u de regel **Alle Pagina&#39;s**. Klik op die regel om deze te openen.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl1gcp.png)

Dan ga je dit doen. Klik **+** pictogram onder **Acties** om een nieuwe actie toe te voegen.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl2gcp.png)

Dan zie je dit. Maak de volgende selectie:

- Selecteer de **Uitbreiding**: **Google Cloud Platform**.
- Selecteer het **Type van Actie**: **verzend Gegevens naar Wolk Pub/Sub**.

Dat zou u deze **Naam** moeten geven: **de Cloudplatform van Google - verzend Gegevens naar de Wolk Pub/Sub**. U zou nu dit moeten zien:

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl5gcp.png)

U moet nu het Pub/Subonderwerp vormen dat u vroeger creeerde.

U kunt de **naam van het Onderwerp** hier vinden, het kopiëren.

![ GCP ](./images/gcp8.png)

Plak de **naam van het Onderwerp** in uw configuratie van de Regel. Daarna, klik het pictogram van het Element van Gegevens naast het **(vereiste) Gegevens** gebied.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl6gcp.png)

Selecteer **Gebeurtenis XDM** en klik **Uitgezocht**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl7gcp.png)

Dan zie je dit. Klik **houden Veranderingen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl8gcp.png)

Klik **sparen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl9gcp.png)

Dan zie je dit.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl10gcp.png)

## Je wijzigingen Publish

Uw configuratie is nu voltooid. Ga naar **het Publiceren Stroom** om uw veranderingen te publiceren. Open uw bibliotheek van de Ontwikkeling **Belangrijkste** door **te klikken geef** zoals vermeld uit.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl12gcp.png)

Klik **toevoegen Alle Gewijzigde Middelen** knoop, waarna zult u uw Regel en Element van Gegevens in deze bibliotheek zien verschijnen. Daarna, klik **sparen &amp; bouwt voor Ontwikkeling**. Uw wijzigingen worden nu geïmplementeerd.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl13gcp.png)

Na een paar minuten zult u zien dat de implementatie klaar is en klaar om te worden getest.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl14.png)

## Uw configuratie testen

Ga naar [ https://dsn.adobe.com ](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![ DSN ](./../../datacollection/module1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](../../gettingstarted/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](../../gettingstarted/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](../../gettingstarted/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](../../gettingstarted/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](../../gettingstarted/gettingstarted/images/web7.png)

Schakelaar uw mening aan uw Google Cloud Pub/Sub en ga naar **BERICHTEN**. Klik **PULL** en na een paar seconden zult u sommige berichten in de lijst zien. Klik op een bericht om de inhoud te visualiseren.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook3gcp.png)

U kunt de XDM-lading van uw gebeurtenis nu zien in Google Pub/Sub. U hebt nu met succes gegevens verzonden die door de Inzameling van Gegevens van Adobe Experience Platform, in real time, aan een PoB/Subeindpunt van de Wolk van Google werden verzameld. Vanaf dat punt kunnen die gegevens worden gebruikt door elke Google Cloud Platform-toepassing, zoals BigQuery voor opslag en rapportage of voor de gebruiksgevallen van Machine Learning.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook4gcp.png)

Volgende Stap: [ 2.5.5 door:sturen gebeurtenissen aan AWS Kinesis &amp; AWS S3 ](./ex5.md)

[Ga terug naar Module 2.5](./aep-data-collection-ssf.md)

[Terug naar alle modules](./../../../overview.md)


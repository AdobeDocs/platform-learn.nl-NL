---
title: Real-time CDP - Bouw een segment en neem actie - Bouw een segment
description: Real-time CDP - Bouw een segment en neem actie - Bouw een segment
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# 2.3.1 Een segment maken

In deze oefening, zult u een segment tot stand brengen door gebruik te maken van de bouwer van het segment van Adobe Experience Platform.

## 2.3.1.1 Context

In de wereld van vandaag, moet het antwoorden op het gedrag van een klant in real time zijn. Één van de manieren om aan klantengedrag in real time te antwoorden is door een segment te gebruiken, op voorwaarde dat het segment in real time kwalificeert. In deze oefening, moet u een segment opbouwen, rekening houdend met echte activiteit op de website die wij hebben gebruikt.

## 2.3.1.2 Identificeer het gedrag waarop u wilt reageren

Ga naar [ https://builder.adobedemo.com/projects ](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web8.png)

U kunt nu de onderstaande workflow volgen om toegang te krijgen tot de website. Klik **Integraties**.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web1.png)

Op de **pagina van de Integraties**, moet u het bezit van de Inzameling van Gegevens selecteren dat in oefening 0.1 werd gecreeerd.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web2.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web7.png)

In dit voorbeeld wilt u reageren op een specifieke klant die een specifiek product weergeeft.
Van de **homepage 0} Luma {, ga naar** Mannen **, en klik het product** PROTEUS FITNESS JACKSHIRT **.**

![ Ingestie van Gegevens ](./images/homenadia.png)

Dus wanneer iemand de productpagina voor **PROTEUS FITNESS JACKSHIRT** bezoekt, wilt u actie kunnen nemen. Het eerste wat je moet doen om actie te ondernemen, is een segment definiëren.

![ Ingestie van Gegevens ](./images/homenadiapp.png)

## 2.3.1.3 Het segment creëren

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het menu op de linkerkant, ga naar **Segmenten** en ga dan naar **doorbladeren** waar u een overzicht van alle bestaande segmenten kunt zien. Klik op **creeer de knoop van het Segment** beginnen een nieuw segment te creëren.

![Segmentatie](./images/menuseg.png)

Zoals hierboven vermeld, moet u een segment uit alle klanten bouwen die het product **JACKSHIRT van de FITNESS van PROTEUS** hebben bekeken.

Om dit segment op te bouwen, moet u een gebeurtenis toevoegen. U kunt alle gebeurtenissen vinden door op het **pictogram van Gebeurtenissen** in de **3} menubar van Segmenten te klikken.**

Daarna, zult u het hoogste niveau **XDM ExperienceEvent** knoop zien.

Om klanten te vinden die het **product van de FITNESS JACKSHIRT van 0} PROTEUS hebben bezocht, klik op** XDM ExperienceEvent **.**

![Segmentatie](./images/findee.png)

De rol neer aan **Punten van de Lijst van het Product** en klikt het.

![Segmentatie](./images/see.png)

Selecteer **Naam** en sleep en laat vallen het **voorwerp van de Naam** van de linker **Punten van de Lijst van het Product** menu op het canvas van de segmentbouwer in de **sectie van Gebeurtenissen**.

![Segmentatie](./images/eewebpdtlname1.png)

De vergelijkingsparameter zou **gelijken** moeten zijn en op het inputgebied, ga `PROTEUS FITNESS JACKSHIRT` binnen.

![Segmentatie](./images/pv.png)

Uw **Regels van de Gebeurtenis** zouden nu als dit moeten kijken. Telkens als u een element aan de segmentbouwer toevoegt, kunt u **klikken verfrist schatten** knoop om een nieuwe schatting van de bevolking in uw segment te krijgen.

![Segmentatie](./images/ldap4.png)

Tot slot geven wij uw segment een naam en bewaren het.

Gebruik als naamgevingsconventie:

- `--aepUserLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`

De segmentnaam moet er als volgt uitzien:
`vangeluw - Interest in PROTEUS FITNESS JACKSHIRT`

Daarna, klik **sparen en sluit** knoop om uw segment te bewaren.

![Segmentatie](./images/segmentname.png)

U wordt nu teruggezet naar de pagina van het segmentoverzicht.

![Segmentatie](./images/savedsegment.png)

Volgende Stap: [ 2.3.2 Overzicht hoe te om Doel DV360 te vormen gebruikend Doelen ](./ex2.md)

[Terug naar module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../../overview.md)

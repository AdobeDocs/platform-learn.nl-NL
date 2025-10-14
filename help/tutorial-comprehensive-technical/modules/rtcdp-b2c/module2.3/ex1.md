---
title: CDP in real time - Bouw een publiek en neem actie - Bouw een publiek
description: CDP in real time - Bouw een publiek en neem actie - Bouw een publiek
kt: 5342
doc-type: tutorial
exl-id: a46b1640-769d-4fb3-97e6-beaf9706efbf
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 1%

---

# 2.3.1 Een publiek maken

In deze oefening, zult u een publiek creëren door gebruik te maken van Adobe Experience Platform het publiek bouwer.

## Context

Reageren op de interesse van een klant moet realtime zijn. Één van de manieren om aan klantengedrag in real time te antwoorden is door een publiek te gebruiken, op voorwaarde dat het publiek in real time kwalificeert. In deze oefening, moet u een publiek opbouwen, rekening houdend met echte activiteit op de website die wij hebben gebruikt.

## Bepaal het gedrag waarop u wilt reageren

Ga naar [&#x200B; https://dsn.adobe.com &#x200B;](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![&#x200B; DSN &#x200B;](./../../datacollection/module1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web7.png)

In dit voorbeeld wilt u reageren op een specifieke klant die een specifiek product weergeeft.
Van de **homepage van het Signaal 0&rbrace; Citi, ga** Telefoons &amp; apparaten **, en klik het product** Galaxy S24 **.**

![&#x200B; Ingestie van Gegevens &#x200B;](./images/homegalaxy.png)

Dus wanneer iemand de productpagina voor **Galaxy S24** bezoekt, wilt u actie kunnen nemen. Het eerste wat je moet doen om actie te ondernemen, is een publiek definiëren.

![&#x200B; Ingestie van Gegevens &#x200B;](./images/homegalaxy1.png)

## Het publiek maken

Ga naar [&#x200B; Adobe Experience Platform &#x200B;](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/sb1.png)

In het menu op de linkerkant, ga naar **Soorten publiek** en ga dan naar **doorbladeren** waar u een overzicht van alle bestaande wijzen kunt zien. Klik op **creeer de knoop van het Publiek** beginnen een nieuw publiek te creëren.

![Segmentatie](./images/menuseg.png)

Selecteer **bouwt Regel** en klik **creeer**.

![Segmentatie](./images/menuseg1.png)

Zoals hierboven vermeld, moet u een publiek uit alle klanten bouwen die het product **Galaxy S24** hebben bekeken.

U moet een gebeurtenis toevoegen om dit publiek op te bouwen. U kunt alle gebeurtenissen vinden door op het **pictogram van Gebeurtenissen** in de **publiek** menubar te klikken.

Daarna, zult u het hoogste niveau **XDM ExperienceEvent** knoop zien.

Om klanten te vinden die het **Galaxy S24** product hebben bezocht, klik op **XDM ExperienceEvent**.

![Segmentatie](./images/findee.png)

De rol neer aan **Punten van de Lijst van het Product** en klikt het.

![Segmentatie](./images/see.png)

Selecteer **Naam** en sleep en laat vallen het **voorwerp van de Naam** van de linker **Punten van de Lijst van het Product** menu op het canvas van de publieksbouwer in de **sectie van Gebeurtenissen**.

![Segmentatie](./images/eewebpdtlname1.png)

De vergelijkingsparameter zou **gelijken** moeten zijn en op het inputgebied, ga `Galaxy S24` binnen.

![Segmentatie](./images/pv.png)

Uw **Regels van de Gebeurtenis** zouden nu als dit moeten kijken. Telkens als u een element aan de publieksbouwer toevoegt, kunt u **klikken verfrist Schatting** knoop om een nieuwe schatting van de bevolking in uw publiek te krijgen.

![Segmentatie](./images/ldap4.png)

Geef uw publiek een naam en plaats de **Methode van de Evaluatie** aan **Edge**.

Gebruik als naamgevingsconventie:

- `--aepUserLdap-- - Interest in Galaxy S24`

Daarna, klik de **knoop van Publish** om uw publiek te bewaren.

![Segmentatie](./images/segmentname.png)

U gaat nu terug naar de overzichtspagina van het publiek.

![Segmentatie](./images/savedsegment.png)

Volgende Stap: [&#x200B; 2.3.2 Overzicht hoe te om Doel DV360 te vormen gebruikend Doelen &#x200B;](./ex2.md)

[Terug naar module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../../overview.md)

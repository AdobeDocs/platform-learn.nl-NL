---
title: Stichting - de Ingestie van Gegevens - vorm Datasets
description: Stichting - de Ingestie van Gegevens - vorm Datasets
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# 1.2.3 Gegevensbestanden configureren

In deze oefening, zult u de vereiste datasets vormen om profielinformatie en klantengedrag te vangen en op te slaan. Elke dataset die u in dit creeert zal één van de schema&#39;s gebruiken die u in de vorige stap bouwde.

## Artikel

Na het bepalen van wat het antwoord op de vragen **Who deze klant is?** en **wat doet deze klant?** moet er als volgt uitzien: u moet nu een emmertje maken dat die informatie gebruikt om gegevens te ontvangen en te valideren die naar Adobe Experience Platform zijn verzonden.

## 1.2.3.1 - Datasets maken

U moet nu twee datasets tot stand brengen:

- 1 dataset om de informatie te vangen die **beantwoordt wie deze klant is?** - vraag.
- 1 dataset om de informatie te vangen die **beantwoordt wat deze klant doet?** - vraag.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Selecteer een **[!UICONTROL sandbox]** voordat u verdergaat. De te selecteren sandbox krijgt de naam ``--module2sandbox--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./images/sb1.png)

Klik in Adobe Experience Platform op **[!UICONTROL Datasets]** in het menu aan de linkerkant van het scherm.  U zult dan dit zien:

![ Ingestie van Gegevens ](./images/menudatasets.png)

Laten we beginnen met het maken van de gegevensset om de registratiegegevens van de website vast te leggen.

U zou een nieuwe dataset moeten creëren. Als u een nieuwe gegevensset wilt maken, klikt u op de knop **[!UICONTROL + Create Dataset]** .

![ Ingestie van Gegevens ](./images/createdataset.png)

Nadat u op de knop **[!UICONTROL + Create Dataset]** hebt geklikt, wordt het volgende scherm weergegeven.

![ Ingestie van Gegevens ](./images/datasetsetup.png)

U moet een dataset van het schema bepalen dat u in de vorige stap bepaalde. Klik op de optie **[!UICONTROL Create Dataset from Schema]** -.

![ Ingestie van Gegevens ](./images/datasetfromschema.png)

In het volgende scherm, moet u het schema selecteren dat u in 1 creeerde, `--demoProfileLdap-- - Demo System - Profile Schema for Website`.

![ Ingestie van Gegevens ](./images/schemaselection.png)

Klik op **[!UICONTROL Next]** nadat u het schema hebt geselecteerd om door te gaan.

![ Ingestie van Gegevens ](./images/next.png)

Geef een naam aan uw dataset.

Als naam voor onze dataset, gebruik dit:

`--demoProfileLdap-- - Demo System - Profile Dataset for Website`

Voor LDAP **[!UICONTROL vangeluw]** moet dit bijvoorbeeld de naam van het schema zijn:

**[!UICONTROL vangeluw - Demo System - Profile Dataset for Website]**

Dat zou je iets dergelijks moeten geven:

![ Ingestie van Gegevens ](./images/datasetname.png)

Klik op **[!UICONTROL Finish]** om de configuratie van de gegevensset te voltooien.

![ Ingestie van Gegevens ](./images/finish.png)

U ziet nu het volgende:

![ Ingestie van Gegevens ](./images/dsoverview1.png)

Ga terug naar het overzicht [!UICONTROL Datasets] . U zult nu de dataset zien u pop - omhoog in het overzicht creeerde.

![ Ingestie van Gegevens ](./images/dsoverview2.png)

Daarna, zult u een tweede dataset vormen om websiteinteractie te vangen.

U zou een nieuwe dataset moeten creëren. Als u een nieuwe gegevensset wilt maken, klikt u op de knop **[!UICONTROL + Create Dataset]** .

![ Ingestie van Gegevens ](./images/createdataset.png)

Nadat u op de knop **[!UICONTROL + Create Dataset]** hebt geklikt, wordt het volgende scherm weergegeven.

![ Ingestie van Gegevens ](./images/datasetsetup.png)

U moet een dataset van het schema bepalen dat u in de vorige stap bepaalde. Klik op de optie **[!UICONTROL Create Dataset from Schema]** -.

![ Ingestie van Gegevens ](./images/datasetfromschema.png)

In het volgende scherm, moet u het schema selecteren dat u in 2.2 creeerde, `--demoProfileLdap-- - Demo System - Event Schema for Website`.

![ Ingestie van Gegevens ](./images/schemaselectionee.png)

Klik op **[!UICONTROL Next]** nadat u het schema hebt geselecteerd om door te gaan.

![ Ingestie van Gegevens ](./images/next.png)

Geef een naam aan uw dataset.

Als naam voor onze dataset, zullen wij dit gebruiken:

`--demoProfileLdap-- - Demo System - Event Dataset for Website`

Voor LDAP **[!UICONTROL vangeluw]** moet dit bijvoorbeeld de naam van het schema zijn:

**[!UICONTROL vangeluw - Demo System - Event Dataset for Website]**

Dat zou je iets dergelijks moeten geven:

![ Ingestie van Gegevens ](./images/datasetnameee.png)

Klik op **[!UICONTROL Finish]** om de configuratie van de gegevensset te voltooien.

![ Ingestie van Gegevens ](./images/finish.png)

U zult dan dit zien:

![ Ingestie van Gegevens ](./images/finish1.png)

Ga terug naar het [!UICONTROL Datasets] overzichtsscherm.

![ Ingestie van Gegevens ](./images/datasetsoverview.png)

U moet nu uw datasets toelaten om deel van Adobe Experience Platform in real time het Profiel van de Klant te maken.

Open uw dataset `--demoProfileLdap--` - demosysteem - de Dataset van het Profiel voor Website door het te klikken.

Zoek het schakelpictogram [!UICONTROL Profile] aan de rechterkant van het scherm.

![ Ingestie van Gegevens ](./images/ds1.png)

Klik op de schakeloptie [!UICONTROL Profile] om deze gegevensset in te schakelen voor [!UICONTROL Profile] .

![ Ingestie van Gegevens ](./images/ds2.png)

Klik op **[!UICONTROL Enable]** .

![ Ingestie van Gegevens ](./images/ds3.png)

Uw gegevensset is nu ingeschakeld voor [!UICONTROL Profile] .

Ga terug naar het overzicht van datasets en open uw dataset `--demoProfileLdap-- - Demo System - Event Dataset` voor Website door het te klikken.

Zoek het schakelpictogram [!UICONTROL Profile] aan de rechterkant van het scherm.

![ Ingestie van Gegevens ](./images/ds4.png)

Klik op de schakeloptie [!UICONTROL Profile] om [!UICONTROL Profile] in te schakelen.

![ Ingestie van Gegevens ](./images/ds2.png)

Klik op **[!UICONTROL Enable]**.

![ Ingestie van Gegevens ](./images/ds5.png)

Uw gegevensset is nu ingeschakeld voor [!UICONTROL Profile] .

Volgende Stap: [ 1.2.4 Ingestie van Gegevens van Off-line Bronnen ](./ex4.md)

[Terug naar module 1.2](./data-ingestion.md)

[Terug naar alle modules](../../../overview.md)

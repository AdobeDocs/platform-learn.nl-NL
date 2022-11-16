---
title: Real-time CDP - Bouw een segment en neem actie - Bouw een segment
description: Real-time CDP - Bouw een segment en neem actie - Bouw een segment
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: c0778e81-4282-433d-9e02-37e32bf370ef
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 1%

---

# 6.1 Een segment maken

In deze oefening, zult u een segment tot stand brengen door gebruik te maken van de bouwer van het segment van Adobe Experience Platform.

## 6.1.1 Context

In de wereld van vandaag, moet het antwoorden op het gedrag van een klant in real time zijn. Één van de manieren om aan klantengedrag in real time te antwoorden is door een segment te gebruiken, op voorwaarde dat het segment in real time kwalificeert. In deze oefening, moet u een segment opbouwen, rekening houdend met echte activiteit op de website die wij hebben gebruikt.

## 6.1.2 Bepaal het gedrag waarop u wilt reageren

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![DSN](../module0/images/web8.png)

U kunt nu de onderstaande workflow volgen om toegang te krijgen tot de website. Klikken **Integraties**.

![DSN](../module0/images/web1.png)

Op de **Integraties** pagina, moet u het bezit van de Inzameling van Gegevens selecteren dat in oefening 0.1 werd gecreeerd.

![DSN](../module0/images/web2.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![DSN](../module0/images/web3.png)

Open een nieuw Incognito-browservenster.

![DSN](../module0/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![DSN](../module0/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![DSN](../module0/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![DSN](../module0/images/web7.png)

In dit voorbeeld wilt u reageren op een specifieke klant die een specifiek product weergeeft.
Van de **Luminantie** homepage, ga naar **Mannen** en klik op het product **PROTEUS FITNESS JACKSHIRT**.

![Gegevensinname](./images/homenadia.png)

Dus als iemand de productpagina bezoekt **PROTEUS FITNESS JACKSHIRT**, wilt u actie kunnen ondernemen. Het eerste wat je moet doen om actie te ondernemen, is een segment definiëren.

![Gegevensinname](./images/homenadiapp.png)

## 6.1.3 Het segment maken

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](../module2/images/sb1.png)

Ga in het menu aan de linkerkant naar **Segmenten** en ga vervolgens naar **Bladeren** Hier ziet u een overzicht van alle bestaande segmenten. Klik op de knop **Segment maken** om een nieuw segment te maken.

![Segmentering](./images/menuseg.png)

Zoals hierboven vermeld, moet u een segment maken van alle klanten die het product hebben bekeken **PROTEUS FITNESS JACKSHIRT**.

Om dit segment op te bouwen, moet u een gebeurtenis toevoegen. U kunt alle gebeurtenissen vinden door op de knop **Gebeurtenissen** in het deelvenster **Segmenten** menubalk.

Vervolgens ziet u het hoogste niveau **XDM ExperienceEvent** knooppunt.

Om klanten te vinden die hebben bezocht **PROTEUS FITNESS JACKSHIRT** product, klik op **XDM ExperienceEvent**.

![Segmentering](./images/findee.png)

Omlaag schuiven naar **Objecten in de productlijst** en klik erop.

![Segmentering](./images/see.png)

Selecteren **Naam** en sleep de **Naam** object van links **Objecten in de productlijst** menu op het gesegmenteerde canvas van de bouwer in **Gebeurtenissen** sectie.

![Segmentering](./images/eewebpdtlname1.png)

De vergelijkingsparameter moet **equals** en in het invoerveld typt u `PROTEUS FITNESS JACKSHIRT`.

![Segmentering](./images/pv.png)

Uw **Gebeurtenisregels** zou er nu zo moeten uitzien. Telkens als u een element aan de segmentbouwer toevoegt, kunt u klikken **Offerte vernieuwen** om een nieuwe schatting van de bevolking in uw segment te krijgen.

![Segmentering](./images/ldap4.png)

Tot slot geven wij uw segment een naam en bewaren het.

Gebruik als naamgevingsconventie:

- `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`

Uw segmentnaam moet er als volgt uitzien:
`vangeluw - Interest in PROTEUS FITNESS JACKSHIRT`

Klik op de knop **Opslaan en sluiten** om uw segment op te slaan.

![Segmentering](./images/segmentname.png)

U wordt nu teruggezet naar de pagina van het segmentoverzicht.

![Segmentering](./images/savedsegment.png)

Volgende stap: [6.2 Overzicht hoe te om DV360 Bestemming te vormen gebruikend Doelen](./ex2.md)

[Ga terug naar module 11](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../overview.md)

---
title: Segmentactivering naar Microsoft Azure Event Hub - Actie
description: Segmentactivering naar Microsoft Azure Event Hub - Actie
kt: 5342
doc-type: tutorial
source-git-commit: c6ba1f751f18afe39fb6b746a62bc848fa8ec9bf
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# 2.4.6 Eindscenario

## 2.4.6.1 Start Azure Event Hub trigger

Om de nuttige lading te tonen die door Adobe Experience Platform in real time CDP naar onze Azure Hub van de Gebeurtenis op segmentkwalificatie wordt verzonden, moeten wij onze eenvoudige Azure de trekkerfunctie van de Hub van de Gebeurtenis beginnen. Deze functie zal eenvoudig &quot;stortplaats&quot;de nuttige lading aan de console in de Code van Visual Studio. Maar denk eraan dat deze functie op elke manier kan worden uitgebreid om met allerlei omgevingen te communiceren met behulp van specifieke API&#39;s en protocollen.

### De Code van Visual Studio van de lancering en beginproject

Zorg ervoor dat uw geopend en lopend project van de Code van Visual Studio hebt

Om uw functie van Azure in de Code van Visual Studio te beginnen/te stoppen/opnieuw te beginnen, verwijs naar de volgende oefeningen:

- [Oefening 13.5.4 - Start Azure Project](./ex5.md)
- [Oefening 13.5.5 - Stop Azure Project](./ex5.md)

Uw Eind van de Code van Visual Studio **** zou iets gelijkend op dit moeten vermelden:

```code
[2022-02-23T05:03:41.429Z] Worker process started and initialized.
[2022-02-23T05:03:41.484Z] Debugger attached.
[2022-02-23T05:03:46.401Z] Host lock lease acquired by instance ID '000000000000000000000000D90C881B'.
```

![ 6-01-vsc-ready.png ](./images/vsc31.png)

## 2.4.6.2 Uw Luma-website laden

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

## 2.4.6.3 Geschikt voor uw interesse in het segment Apparatuur

Navigeer aan de **pagina van het Materiaal** eens, en **herlaad of vernieuw het**. Deze actie zou u voor uw `--demoProfileLdap-- - Interest in Equipment` segment moeten kwalificeren.

![ 6-04-luma-telco-nav-sports.png ](./images/luma1.png)

Open het deelvenster Profielviewer om dit te verifiëren. U moet nu lid zijn van de `--demoProfileLdap-- - Interest in Equipment` . Als uw segmentlidmaatschappen nog niet zijn bijgewerkt in het deelvenster Profielviewer, klikt u op de knop Opnieuw laden.

![ 6-05-luma-telco-nav-breedband.png ](./images/luma2.png)

De schakelaar terug naar de Code van Visual Studio en bekijkt uw **TERMINAL** lusje, zou u een lijst van segmenten voor uw specifiek **ECID** moeten zien. Deze activeringslading wordt geleverd aan uw gebeurtenishub zodra u voor het `--demoProfileLdap-- - Interest in Equipment` segment kwalificeert.

Wanneer u een dichtere blik bij de segmentlading neemt, kunt u zien dat `--demoProfileLdap-- - Interest in Equipment` in status **gerealiseerde** is.

Een segmentstatus van **realiseerde** betekent dat ons profiel enkel het segment is ingegaan. Terwijl de **bestaande** status betekent dat ons profiel in het segment blijft.

![ 6-06-vsc-activatie-gerealiseerde.png ](./images/luma3.png)

## 2.4.6.4 Bezoek de pagina Apparatuur voor een tweede keer

Doe hard van de **pagina van het Materiaal** verfrissen.

![ 6-07-back-to-sports.png ](./images/luma1.png)

Nu, schakelaar terug naar de Code van Visual Studio en verifieer uw **TERMINAL** tabel. U zult zien dat wij nog uw segment hebben, maar nu in status **bestaand** wat betekent dat ons profiel in het segment blijft.

![ 6-08-vsc-activation-existing.png ](./images/luma4.png)

## 2.4.6.5 Bezoek de pagina Sport voor een derde keer

Als u de **pagina van Sporten** voor de derde keer zou terugkomen, zal geen activering plaatsvinden, omdat er geen staatsverandering van een segmentstandpunt is.

Segmentactities worden alleen uitgevoerd wanneer de status van het segment verandert:

![ 6-09-segment-staat-verandering.png ](./images/6-09-segment-state-change.png)

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)

---
title: Werk uw Configuratie-id bij en test uw reis
description: Werk uw Configuratie-id bij en test uw reis
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# 3.1.3 Werk uw bezit van de Inzameling van Gegevens bij en test uw reis

## 3.1.3.1 Werk uw bezit van de Gegevensverzameling bij

Ga naar [ de Inzameling van Gegevens van Adobe Experience Platform ](https://experience.adobe.com/launch/) en selecteer **Markeringen**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![ pagina van Eigenschappen ](./../../../modules/datacollection/module1.1/images/launch1.png)

In module 0 heeft het demosysteem twee Client-eigenschappen voor u gemaakt: een voor de website en een voor de mobiele app. Zoek naar `--aepUserLdap--` in het vak **[!UICONTROL Search]** . Klik om het **bezit te openen 0} van het Web {.**

![ vakje van het Onderzoek ](./../../../modules/datacollection/module1.1/images/property6.png)

Dan zie je dit.

![ Opstelling van de Lancering ](./images/rule1.png)

In het linkermenu, ga **Regels** en onderzoek naar het profiel van het regel **Register**. Klik het profiel van het regel **Register** om het te openen.

![ Opstelling van de Lancering ](./images/rule2.png)

U zult dan de details van deze regel zien. Klik om de actie **te openen verzend &quot;Gebeurtenis van de Registratie&quot;aan AEP - trekker JO**.

![ Opstelling van de Lancering ](./images/rule3.png)

U zult dan zien dat wanneer deze actie wordt teweeggebracht, een specifiek gegevenselement wordt gebruikt om de XDM gegevensstructuur te bepalen. U moet dat gegevenselement bijwerken, en u moet **identiteitskaart van de Gebeurtenis** van de gebeurtenis bepalen die u in [ Uitoefening 7.1 ](./ex1.md) vormde.

![ Opstelling van de Lancering ](./images/rule4.png)

U moet nu gaan bijwerken het gegevenselement **XDM - de Gebeurtenis van de Registratie**. Om dit te doen, ga naar **Elementen van Gegevens**. Onderzoek naar **XDM - de Gebeurtenis van de Registratie** en klik om dat gegevenselement te openen.

![ Opstelling van de Lancering ](./images/rule5.png)

U zult dan dit zien:

![ Opstelling van de Lancering ](./images/rule6.png)

Navigeer naar het veld `_experience.campaign.orchestration.eventID` . Verwijder de huidige waarde en plak de eventID daar.

Als herinnering, identiteitskaart van de Gebeurtenis kan in Adobe Journey Optimizer onder **Configuraties > Gebeurtenissen** worden gevonden en u zult gebeurtenistidentiteitskaart in de steekproeflading van uw even vinden, die als dit kijkt: `"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`.

![ ACOP ](./images/payloadeventID.png)

Na het plakken van eventID, zou uw scherm als dit moeten kijken. Daarna, klik **sparen** of **sparen aan Bibliotheek**.

![ Opstelling van de Lancering ](./images/rule7.png)

Tot slot moet u uw wijzigingen publiceren. Ga naar **het Publiceren Stroom** in het linkermenu.

![ Opstelling van de Lancering ](./images/rule8.png)

Klik **toevoegen Alle Gewijzigde Middelen** en klik dan **sparen &amp; bouwen aan Ontwikkeling**.

![ Opstelling van de Lancering ](./images/rule9.png)

Uw bibliotheek wordt dan bijgewerkt en na 1-2 minuten kunt u uw configuratie testen.

## 3.1.3.2 Uw reis testen

Ga naar [ https://builder.adobedemo.com/projects ](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![ DSN ](./../../../modules/gettingstarted/gettingstarted/images/web8.png)

Op de **Screens** pagina, klik **Looppas**.

![ DSN ](./../../../modules/datacollection/module1.1/images/web2.png)

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

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv1.png)

Heb een blik bij het paneel van de Kijker van het Profiel en het Profiel van de Klant in real time met **identiteitskaart van het Experience Cloud** als primaire herkenningsteken voor deze momenteel onbekende klant.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv2.png)

Ga naar de pagina Registreren/Aanmelden. Klik **CREËREN EEN ACCOUNT**.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv9.png)

Vul uw details in en klik **Register** waarna u aan de vorige pagina opnieuw zult worden gericht.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv10.png)

Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv11.png)

1 minuut nadat je je account hebt gemaakt, ontvang je een e-mail over het aanmaken van je account van Adobe Journey Optimizer.

![ Opstelling van de Lancering ](./images/email.png)

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 3.1](./journey-orchestration-create-account.md)

[Terug naar alle modules](../../../overview.md)

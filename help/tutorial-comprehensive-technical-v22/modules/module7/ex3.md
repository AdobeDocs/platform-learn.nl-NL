---
title: Module 7 Werk uw identiteitskaart van de Configuratie bij en test uw Weg
description: Werk uw Configuratie-id bij en test uw reis
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: d3ceb676-d7f5-4f52-85a4-deaa5ef24034
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 7.3 Werk uw bezit van de Inzameling van Gegevens bij en test uw reis

## 7.3.1 Werk uw bezit van de Inzameling van Gegevens bij

Ga naar [Adobe Experience Platform-gegevensverzameling](https://experience.adobe.com/launch/) en selecteert u **Tags**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![Pagina Eigenschappen](../module1/images/launch1.png)

In module 0, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: één voor de website en één voor de mobiele app. Zoeken naar `--demoProfileLdap--` in de **[!UICONTROL Zoeken]** doos. Klik om het dialoogvenster **Web** eigenschap.

![Zoekvak](../module1/images/property6.png)

Dan zie je dit.

![Starten](./images/rule1.png)

Ga in het linkermenu naar **Regels** en zoek naar de regel **Profiel registreren**. Klik op de regel **Profiel registreren** om het te openen.

![Starten](./images/rule2.png)

U zult dan de details van deze regel zien. Klik om de handeling te openen **&quot;Registratiegebeurtenis&quot; naar AEP verzenden - trigger JO**.

![Starten](./images/rule3.png)

U zult dan zien dat wanneer deze actie wordt teweeggebracht, een specifiek gegevenselement wordt gebruikt om de XDM gegevensstructuur te bepalen. U moet dat gegevenselement bijwerken, en u moet bepalen **Gebeurtenis-id** van de gebeurtenis waarin u hebt geconfigureerd [Oefening 7.1](./ex1.md).

![Starten](./images/rule4.png)

U moet nu het gegevenselement bijwerken **XDM - Registratiegebeurtenis**. Ga hiertoe naar **Gegevenselementen**. Zoeken naar **XDM - Registratiegebeurtenis** en klik om dat gegevenselement te openen.

![Starten](./images/rule5.png)

U zult dan dit zien:

![Starten](./images/rule6.png)

Naar het veld navigeren `_experience.campaign.orchestration.eventID`. Verwijder de huidige waarde en plak de eventID daar.

De gebeurtenis-id is te vinden in Adobe Journey Optimizer onder **Configuraties > Gebeurtenissen** en u zult gebeurtenisidentiteitskaart in de steekproeflading van uw even vinden, die als dit kijkt: `"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`.

![ACOP](./images/payloadeventID.png)

Na het plakken van eventID, zou uw scherm als dit moeten kijken. Klik op Volgende **Opslaan** of **Opslaan in bibliotheek**.

![Starten](./images/rule7.png)

Tot slot moet u uw wijzigingen publiceren. Ga naar **Publishing Flow** in het linkermenu.

![Starten](./images/rule8.png)

Klikken **Alle gewijzigde bronnen toevoegen** en klik vervolgens op **Opslaan en samenstellen tot ontwikkeling**.

![Starten](./images/rule9.png)

Uw bibliotheek wordt dan bijgewerkt en na 1-2 minuten kunt u uw configuratie testen.

## 7.3.2 Test uw reis

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![DSN](../module0/images/web8.png)

Op de **Schermen** pagina, klikt u op **Uitvoeren**.

![DSN](../module1/images/web2.png)

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

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![Demo](../module2/images/pv1.png)

Bekijk het deelvenster Profielviewer en het realtime klantprofiel met de **Experience Cloud-id** als primaire identificator voor deze momenteel onbekende klant.

![Demo](../module2/images/pv2.png)

Ga naar de pagina Registreren/Aanmelden. Klikken **EEN ACCOUNT MAKEN**.

![Demo](../module2/images/pv9.png)

Vul uw gegevens in en klik op **Registreren** waarna u naar de vorige pagina wordt omgeleid.

![Demo](../module2/images/pv10.png)

Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![Demo](../module2/images/pv11.png)

1 minuut nadat je je account hebt gemaakt, ontvang je een e-mail over het aanmaken van je account van Adobe Journey Optimizer.

![Starten](./images/email.png)

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 7](./journey-orchestration-create-account.md)

[Terug naar alle modules](../../overview.md)

---
title: Werk uw Configuratie-id bij en test uw reis
description: Werk uw Configuratie-id bij en test uw reis
kt: 5342
doc-type: tutorial
exl-id: da018975-7421-4d70-b04d-ad8b0597f460
source-git-commit: d19bd2e39c7ff5eb5c99fc7c747671fb80e125ee
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# 3.1.3 Werk uw bezit van de Inzameling van Gegevens bij en test uw reis

## 3.1.3.1 De eigenschap Gegevensverzameling bijwerken

Ga naar [&#x200B; de Inzameling van Gegevens van Adobe Experience Platform &#x200B;](https://experience.adobe.com/data-collection/home) en selecteer **Markeringen**.

![&#x200B; pagina van Eigenschappen &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.1/images/launch1.png)

In **Aan de slag**, leidde het Systeem van de Demo daarna tot een paar eigenschappen van Markeringen voor u, met inbegrip van voor de website en voor mobiele app. Zoek naar `--aepUserLdap-- - One Adobe` in het vak **[!UICONTROL Search]** . Klik om het **bezit te openen 0&rbrace; van het Web &lbrace;.**

![&#x200B; vakje van het Onderzoek &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.1/images/property6.png)

Dan zie je dit.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule1.png)

In het linkermenu, ga naar **Regels** en onderzoek naar de regel **Create rekening**. Klik de regel **creeer rekening** om het te openen.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule2.png)

U zult dan de details van deze regel zien. Klik om de actie **te openen verzend de Gebeurtenis van de Ervaring van de Registratie**.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule3.png)

U zult dan zien dat wanneer deze actie wordt teweeggebracht, een specifiek gegevenselement wordt gebruikt om de XDM gegevensstructuur te bepalen. U moet dat gegevenselement bijwerken, en u moet **identiteitskaart van de Gebeurtenis** van de gebeurtenis bepalen die u in [&#x200B; Uitoefening 3.1.1 &#x200B;](./ex1.md) vormde.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule4.png)

U moet nu gaan bijwerken het gegevenselement **XDM - de Gebeurtenis van de Registratie**. Om dit te doen, ga naar **Elementen van Gegevens**. Onderzoek naar **XDM - Registratie** en klik om dat gegevenselement te openen.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule5.png)

U zult dan dit zien:

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule6.png)

Navigeer naar het veld `_experience.campaign.orchestration.eventID` . Verwijder de huidige waarde en plak de eventID daar.

Als herinnering, identiteitskaart van de Gebeurtenis kan in Adobe Journey Optimizer onder **Configuraties > Gebeurtenissen** worden gevonden en u zult gebeurtenistidentiteitskaart in de steekproeflading van uw even vinden, die als dit kijkt: `"eventID": "d40815dbcd6ffd813035b4b590b181be21f5305328e16c5b75e4f32fd9e98557"`.

![&#x200B; ACOP &#x200B;](./images/payloadeventID.png)

Na het plakken van eventID, zou uw scherm als dit moeten kijken. Daarna, klik **sparen** of **sparen aan Bibliotheek**.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule7.png)

Tot slot moet u uw wijzigingen publiceren. Ga naar **het Publiceren Stroom** in het linkermenu en klik om uw **Belangrijkste** bibliotheek te openen.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule8.png)

Klik **toevoegen Alle Gewijzigde Middelen** en klik dan **sparen &amp; bouwen aan Ontwikkeling**.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/rule9.png)

Uw bibliotheek wordt dan bijgewerkt en na 1-2 minuten kunt u uw configuratie testen.

## 3.1.3.2 Uw reis testen

Ga naar [&#x200B; https://dsn.adobe.com &#x200B;](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![&#x200B; DSN &#x200B;](./../../datacollection/dc1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![&#x200B; DSN &#x200B;](../../../getting-started/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![&#x200B; DSN &#x200B;](../../../getting-started/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![&#x200B; DSN &#x200B;](../../../getting-started/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![&#x200B; DSN &#x200B;](../../../getting-started/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![&#x200B; DSN &#x200B;](../../../getting-started/gettingstarted/images/web7.png)

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![&#x200B; Demo &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv1.png)

Heb een blik bij het paneel van de Kijker van het Profiel en het Profiel van de Klant in real time met **identiteitskaart van Experience Cloud** als primaire herkenningsteken voor deze momenteel onbekende klant. Klik **Teken binnen**.

![&#x200B; Demo &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv2.png)

Klik **CREËREN EEN ACCOUNT**.

![&#x200B; Demo &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv9.png)

Vul uw details in en klik **Register** waarna u aan de vorige pagina opnieuw zult worden gericht.

![&#x200B; Demo &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv10.png)

Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![&#x200B; Demo &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv11.png)

1 minuut nadat je je account hebt gemaakt, ontvang je een e-mail over het aanmaken van je account van Adobe Journey Optimizer.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/email.png)

Je ziet ook de reis en de vooruitgang door de reis op het dashboard van de reis in Journey Optimizer.

![&#x200B; Opstelling van de Lancering &#x200B;](./images/emaildash.png)

## Volgende stappen

Ga naar [&#x200B; Samenvatting en voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Journey Optimizer: Orchestratie &#x200B;](./journey-orchestration-create-account.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

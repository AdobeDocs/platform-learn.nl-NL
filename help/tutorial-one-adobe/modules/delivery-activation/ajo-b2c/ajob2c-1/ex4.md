---
title: Werk uw Configuratie-id bij en test uw reis
description: Werk uw Configuratie-id bij en test uw reis
kt: 5342
doc-type: tutorial
exl-id: da018975-7421-4d70-b04d-ad8b0597f460
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# 3.1.3 Werk uw bezit van de Inzameling van Gegevens bij en test uw reis

## 3.1.3.1 Werk uw bezit van de Gegevensverzameling bij

Ga naar [ de Inzameling van Gegevens van Adobe Experience Platform ](https://experience.adobe.com/launch/) en selecteer **Markeringen**.

![ pagina van Eigenschappen ](./../../../../modules/delivery-activation/datacollection/dc1.1/images/launch1.png)

In **Aan de slag**, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: voor de website en voor mobiele app. Zoek naar `--aepUserLdap--` in het vak **[!UICONTROL Search]** . Klik om het **bezit te openen 0} van het Web {.**

![ vakje van het Onderzoek ](./../../../../modules/delivery-activation/datacollection/dc1.1/images/property6.png)

Dan zie je dit.

![ Opstelling van de Lancering ](./images/rule1.png)

In het linkermenu, ga naar **Regels** en onderzoek naar de regel **Create rekening**. Klik de regel **creeer rekening** om het te openen.

![ Opstelling van de Lancering ](./images/rule2.png)

U zult dan de details van deze regel zien. Klik om de actie **te openen verzend de Gebeurtenis van de Ervaring van de Registratie**.

![ Opstelling van de Lancering ](./images/rule3.png)

U zult dan zien dat wanneer deze actie wordt teweeggebracht, een specifiek gegevenselement wordt gebruikt om de XDM gegevensstructuur te bepalen. U moet dat gegevenselement bijwerken, en u moet **identiteitskaart van de Gebeurtenis** van de gebeurtenis bepalen die u in [ Uitoefening 3.1.1 ](./ex1.md) vormde.

![ Opstelling van de Lancering ](./images/rule4.png)

U moet nu gaan bijwerken het gegevenselement **XDM - de Gebeurtenis van de Registratie**. Om dit te doen, ga naar **Elementen van Gegevens**. Onderzoek naar **XDM - Registratie** en klik om dat gegevenselement te openen.

![ Opstelling van de Lancering ](./images/rule5.png)

U zult dan dit zien:

![ Opstelling van de Lancering ](./images/rule6.png)

Navigeer naar het veld `_experience.campaign.orchestration.eventID` . Verwijder de huidige waarde en plak de eventID daar.

Als herinnering, identiteitskaart van de Gebeurtenis kan in Adobe Journey Optimizer onder **Configuraties > Gebeurtenissen** worden gevonden en u zult gebeurtenistidentiteitskaart in de steekproeflading van uw even vinden, die als dit kijkt: `"eventID": "5ae9b8d3f68eb555502b0c07d03ef71780600c4bd0373a4065c692ae0bfbd34d"`.

![ ACOP ](./images/payloadeventID.png)

Na het plakken van eventID, zou uw scherm als dit moeten kijken. Daarna, klik **sparen** of **sparen aan Bibliotheek**.

![ Opstelling van de Lancering ](./images/rule7.png)

Tot slot moet u uw wijzigingen publiceren. Ga naar **het Publiceren Stroom** in het linkermenu en klik om uw **Belangrijkste** bibliotheek te openen.

![ Opstelling van de Lancering ](./images/rule8.png)

Klik **toevoegen Alle Gewijzigde Middelen** en klik dan **sparen &amp; bouwen aan Ontwikkeling**.

![ Opstelling van de Lancering ](./images/rule9.png)

Uw bibliotheek wordt dan bijgewerkt en na 1-2 minuten kunt u uw configuratie testen.

## 3.1.3.2 Uw reis testen

Ga naar [ https://dsn.adobe.com ](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![ DSN ](./../../datacollection/dc1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](../../../getting-started/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](../../../getting-started/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](../../../getting-started/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](../../../getting-started/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](../../../getting-started/gettingstarted/images/web7.png)

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv1.png)

Heb een blik bij het paneel van de Kijker van het Profiel en het Profiel van de Klant in real time met **identiteitskaart van Experience Cloud** als primaire herkenningsteken voor deze momenteel onbekende klant. Klik **Teken binnen**.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv2.png)

Klik **CREËREN EEN ACCOUNT**.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv9.png)

Vul uw details in en klik **Register** waarna u aan de vorige pagina opnieuw zult worden gericht.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv10.png)

Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv11.png)

1 minuut nadat je je account hebt gemaakt, ontvang je een e-mail over het aanmaken van je account van Adobe Journey Optimizer.

![ Opstelling van de Lancering ](./images/email.png)

Je ziet ook de reis en de vooruitgang door de reis op het dashboard van de reis in Journey Optimizer.

![ Opstelling van de Lancering ](./images/emaildash.png)

## Volgende stappen

Ga naar [ Samenvatting en voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer: Orchestratie ](./journey-orchestration-create-account.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

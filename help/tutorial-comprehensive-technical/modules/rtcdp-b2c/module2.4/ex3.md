---
title: Segmentactivering naar Microsoft Azure Event Hub - Een streaming segment maken
description: Segmentactivering naar Microsoft Azure Event Hub - Een streaming segment maken
kt: 5342
doc-type: tutorial
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# 2.4.3 Een segment maken

## 2.4.3.1 Inleiding

U maakt een eenvoudig segment:

- **Interesse in Apparatuur** waarvoor de klantenprofielen zullen kwalificeren wanneer zij de **pagina van het Apparaat** van de de demowebsite van de Luma bezoeken.

### Goed om te weten

In real time CDP zal een activering aan een bestemming teweegbrengen wanneer u voor een segment kwalificeert dat deel van de activeringslijst van die bestemming uitmaakt. Wanneer dat het geval is, zal de segmentkwalificatielading die naar die bestemming zal worden verzonden **alle segmenten bevatten waarvoor uw profiel** kwalificeert.

Het doel van deze module is te tonen dat de het segmentkwalificatie van het Profiel van uw Klant wordt verzonden naar **uw** bestemming van de gebeurtenishub in real time.

### Segmentstatus

Een segmentkwalificatie in Adobe Experience Platform heeft altijd a **status** - bezit en kan één van het volgende zijn:

- **gerealiseerde**: dit wijst op een nieuwe segmentkwalificatie
- **bestaand**: dit wijst op een bestaande segmentkwalificatie
- **verlaten**: dit wijst erop dat het profiel niet meer voor het segment kwalificeert

## 2.4.3.2 Het segment opbouwen

De bouw van een segment wordt verklaard in detail in [ Module 2.3 ](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md).

### Segment maken

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxId--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

Ga naar **Segmenten**. Klik op de knop **+ Segment maken** .

![ Ingestie van Gegevens ](./images/seg.png)

Geef het segment een naam `--demoProfileLdap-- - Interest in Equipment` en voeg de ervaringsgebeurtenis voor de paginanaam toe:

Klik op **Gebeurtenissen**, en belemmering en laat vallen **XDM ExperienceEvent > Web > Web-pagina details > Naam**. Ga **materiaal** als waarde in:

![ 4-05-create-ee-2.png ](./images/4-05-create-ee-2.png)

De belemmering en laat vallen **XDM ExperienceEvent > `--aepTenantIdSchema--` > demoEnvironment > brandName**. Ga `--demoProfileLdap--` als waarde in, plaats de vergelijkingsparameter aan **bevat** en klik **sparen**:

![ 4-05-create-ee-2-brand.png ](./images/4-05-create-ee-2-brand.png)

### PQL Definition

De PQL van uw segment ziet er als volgt uit:

```code
CHAIN(xEvent, timestamp, [C0: WHAT(web.webPageDetails.name.equals("equipment", false) and _experienceplatform.demoEnvironment.brandName.contains("--demoProfileLdap--", false))])
```

Volgende Stap: [ 2.4.4 activeer segment ](./ex4.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)

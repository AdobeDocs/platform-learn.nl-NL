---
title: Segmentactivering naar Microsoft Azure Event Hub - Een streaming segment maken
description: Segmentactivering naar Microsoft Azure Event Hub - Een streaming segment maken
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: de3824bd-553c-4281-8edf-29abcc28a8e7
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# 13.3 Een segment maken

## 13.3.1 Inleiding

U maakt een eenvoudig segment:

- **Belang van apparatuur** waarvoor klantprofielen in aanmerking komen wanneer zij de **Apparatuur** pagina van de Luma-demonstratiewebsite.

### Goed te weten

In real time CDP zal een activering aan een bestemming teweegbrengen wanneer u voor een segment kwalificeert dat deel van de activeringslijst van die bestemming uitmaakt. Wanneer dat het geval is, zal de segmentkwalificatielading die naar die bestemming zal verzenden bevatten **alle segmenten waarvoor uw profiel in aanmerking komt**.

Het doel van deze module is om aan te tonen dat de segmentkwalificatie van het profiel van uw Klant wordt verzonden naar **uw** doel van gebeurtenishub in real time.

### Segmentstatus

Een segmentkwalificatie in Adobe Experience Platform heeft altijd een **status**-property en kan een van de volgende zijn:

- **gereed**: dit wijst op een nieuw segmentkwalificatie
- **bestaand**: dit wijst op een bestaand segmentkwalificatie
- **verlaten**: dit geeft aan dat het profiel niet langer in aanmerking komt voor het segment

## 13.3.2 Het segment opbouwen

De bouw van een segment wordt in detail uitgelegd [Module 6](../module6/real-time-cdp-build-a-segment-take-action.md).

### Segment maken

Meld u aan bij Adobe Experience Platform door naar deze URL te gaan: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![Gegevensinname](../module2/images/sb1.png)

Ga naar **Segmenten**. Klik op de knop **+ Segment maken** knop.

![Gegevensinname](./images/seg.png)

Geef uw segment een naam `--demoProfileLdap-- - Interest in Equipment` en voeg de ervaringsgebeurtenis voor de paginanaam toe:

Klikken op **Gebeurtenissen** en slepen en neerzetten **XDM ExperienceEvent > Web > Web page details > Name**. Enter **uitrusting** als waarde:

![4-05-create-ee-2.png](./images/4-05-create-ee-2.png)

Slepen en neerzetten **XDM ExperienceEvent > `--aepTenantIdSchema--` > demoEnvironment > brandName**. Enter `--demoProfileLdap--` als waarde, stel de vergelijkingsparameter in op **contains** en klik op **Opslaan**:

![4-05-create-ee-2-brand.png](./images/4-05-create-ee-2-brand.png)

### PQL-definitie

De PQL van uw segment ziet er als volgt uit:

```code
CHAIN(xEvent, timestamp, [C0: WHAT(web.webPageDetails.name.equals("equipment", false) and _experienceplatform.demoEnvironment.brandName.contains("--demoProfileLdap--", false))])
```

Volgende stap: [13.4 Segment activeren](./ex4.md)

[Ga terug naar module 13](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../overview.md)

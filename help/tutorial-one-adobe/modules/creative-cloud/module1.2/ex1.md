---
title: Aan de slag met Firefly Services
description: Aan de slag met Firefly Services
kt: 5342
doc-type: tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
source-git-commit: a0c16a47372d322a7931578adca30a246b537183
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# 1.2.1 Aan de slag met Workfront Fusion

In deze oefening, zult u Workfront Fusion en Adobe I/O gebruiken om de Diensten APIs van de Adobe Firefly te vragen.

## 1.2.1.1 Nieuwe scenario&#39;s maken

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik om **de Fusie van Workfront** te openen.

![ WF Fusion ](./images/wffusion1.png)

Dan moet je dit zien. Ga naar **Scenario&#39;s**.

![ WF Fusion ](./images/wffusion2.png)

Klik **creëren nieuw scenario**.

![ WF Fusion ](./images/wffusion3.png)

U zult dan een leeg scenario zien. Klik het **hulpmiddelen** pictogram en selecteer **Vastgestelde veelvoudige variabelen**.

![ WF Fusion ](./images/wffusion4.png)

U moet nu het **klok** pictogram op de onlangs toegevoegde **Reeks veelvoudige variabelen** bewegen.

![ WF Fusion ](./images/wffusion5.png)

Dan zie je dit.

![ WF Fusion ](./images/wffusion6.png)

Dan, klik op het vraagteken met de rechtermuisknop aan en selecteer **module van de Schrapping**.

![ WF Fusion ](./images/wffusion7.png)

Daarna, klik op het **Vastgestelde veelvoudige variabelen** voorwerp met de rechtermuisknop aan en selecteer **Montages**.

![ WF Fusion ](./images/wffusion8.png)

## 1.2.1.2 Adobe I/O-verificatie configureren

U moet nu de variabelen vormen die nodig zijn om tegen Adobe I/O voor authentiek te verklaren. In de vorige oefening, creeerde u een project van Adobe I/O. De variabelen van dat Adobe I/O-project moeten nu worden gedefinieerd in Workfront Fusion.

De volgende variabelen moeten worden gedefinieerd:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `CONST_client_id` | uw Adobe I/O project Client-id |
| `CONST_client_secret` | uw Adobe I/O project Client Secret |
| `CONST_scope` | bereik van uw Adobe I/O-project |

U kunt deze variabelen vinden door [ https://developer.adobe.com/console/projects ](https://developer.adobe.com/console/projects) te gaan en uw Adobe I/O project te openen, dat `--aepUserLdap-- Firefly` wordt genoemd.

![ WF Fusion ](./images/wffusion9.png)

In uw project, klik **OAuth server-Server** om de waarden voor de bovengenoemde sleutels te zien.

![ WF Fusion ](./images/wffusion10.png)

Met de bovengenoemde sleutels en de waarden, kunt u **vormen Vastgestelde veelvoudige variabelen** voorwerp. Klik **toevoegen punt**.

![ WF Fusion ](./images/wffusion11.png)

Ga de **Veranderlijke naam** in: **CONST_client_id** en zijn **Veranderlijke waarde**, klik **toevoegen**.

![ WF Fusion ](./images/wffusion12.png)

Klik **toevoegen punt**.

![ WF Fusion ](./images/wffusion13.png)

Ga de **Veranderlijke naam** in: **CONST_client_geheime** en zijn **Veranderlijke waarde**, klik **toevoegen**.

![ WF Fusion ](./images/wffusion14.png)

Klik **toevoegen punt**.

![ WF Fusion ](./images/wffusion15.png)

Ga de **Veranderlijke naam** in: **CONST_scope** en zijn **Veranderlijke waarde**, klik **toevoegen**.

![ WF Fusion ](./images/wffusion16.png)

Klik **OK**.

![ WF Fusion ](./images/wffusion17.png)

Beweeg over uw **Vastgestelde veelvoudige variabelen** voorwerp en klik het grote **+** pictogram om een andere module toe te voegen.

![ WF Fusion ](./images/wffusion18.png)

Dan moet je dit zien.

![ WF Fusion ](./images/wffusion19.png)

In de onderzoeksbar, ga **http** in. Selecteer **HTTP** om het te openen.

![ WF Fusion ](./images/wffusion21.png)

en selecteer dan **maak een verzoek**.

![ WF Fusion ](./images/wffusion20.png)

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `URL` | `https://ims-na1.adobelogin.com/ims/token/v3` |
| `Method` | `POST` |
| `Body Type` | `x-www-form-urlencoded` |

Klik **toevoegen punt**.

![ WF Fusion ](./images/wffusion22.png)

Voeg items toe voor elk van de onderstaande waarden:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `client_id` | de vooraf gedefinieerde variabele voor `CONST_client_id` |
| `client_secret` | de vooraf gedefinieerde variabele voor `CONST_client_secret` |
| `scope` | de vooraf gedefinieerde variabele voor `CONST_scope` |
| `grant_type` | `client_credentials` |

Configuratie voor `client_id` .

![ WF Fusion ](./images/wffusion23.png)

Configuratie voor `client_secret` .

![ WF Fusion ](./images/wffusion25.png)

Configuratie voor `scope` .

![ WF Fusion ](./images/wffusion26.png)

Configuratie voor `grant_type` .

![ WF Fusion ](./images/wffusion28.png)

Overzicht van configuratie. De rol neer en controleert checkbox voor **ontleedt reactie**. Klik **OK**.

![ WF Fusion ](./images/wffusion27.png)

Dan moet je dit zien. Klik **Looppas eens**.

![ WF Fusion ](./images/wffusion29.png)

Zodra het scenario is gelopen, zou u dit moeten zien.

![ WF Fusion ](./images/wffusion30.png)

Klik het **vraagteken** pictogram op het **Vastgestelde veelvoudige variabelen** voorwerp om te zien wat gebeurde toen dat voorwerp in werking werd gesteld.

![ WF Fusion ](./images/wffusion31.png)

Klik het **vraagteken** pictogram op **HTTP - doe een verzoek** voorwerp om te zien wat gebeurde toen dat voorwerp in werking werd gesteld. In **OUTPUT**, zult u **access_token** zien die door Adobe I/O wordt teruggekeerd.

![ WF Fusion ](./images/wffusion32.png)

Beweeg over **HTTP - doe een verzoek** voorwerp en klik **+** pictogram om een andere module toe te voegen.

![ WF Fusion ](./images/wffusion33.png)

Zoek in de zoekbalk naar `tools` . Selecteer **Hulpmiddelen**.

![ WF Fusion ](./images/wffusion34.png)

Selecteer **Vastgestelde veelvoudige variabelen**.

![ WF Fusion ](./images/wffusion35.png)

Selecteer **toevoegen punt**.

![ WF Fusion ](./images/wffusion36.png)

Plaats de **naam van de Variabele** aan `bearer_token`. Selecteer `access_token` als dynamische **Variabele waarde**. CLick **voegt** toe.

![ WF Fusion ](./images/wffusion37.png)

Dan moet je dit hebben. Klik **OK**.

![ WF Fusion ](./images/wffusion38.png)

Klik **Looppas eens** opnieuw.

![ WF Fusion ](./images/wffusion39.png)

Zodra het scenario in werking is gesteld, klik het **vraagteken** pictogram op het laatste **Vastgestelde veelvoudige variabelen** voorwerp. Vervolgens moet u zien dat het access_token wordt opgeslagen in de variabele `bearer_token` .

![ WF Fusion ](./images/wffusion40.png)

Daarna, klik met de rechtermuisknop op het eerste voorwerp **plaats veelvoudige waarden** en selecteer **anders noemen**.

![ WF Fusion ](./images/wffusion41.png)

Plaats de naam aan **initialiseert Constanten**. Klik **OK**.

![ WF Fusion ](./images/wffusion42.png)

Wijzig de naam van het tweede voorwerp en plaats de naam aan **voor authentiek verklaren aan Adobe I/O**. Klik **OK**.

![ WF Fusion ](./images/wffusion43.png)

Wijzig de naam van het derde voorwerp en plaats de naam aan **plaats Token van de Drager**. Klik **OK**.

![ WF Fusion ](./images/wffusion44.png)

Dan moet je dit hebben.

![ WF Fusion ](./images/wffusion45.png)

Wijzig vervolgens de naam van het scenario in `--aepUSerLdap-- - Adobe I/O Authentication` .

![ WF Fusion ](./images/wffusion46.png)

Klik **sparen**.

![ WF Fusion ](./images/wffusion47.png)

Volgende Stap: [ 1.2.2 Gebruik Adobe APIs binnen de Fusie van Workfront ](./ex2.md)

[Terug naar module 1.2](./automation.md)

[Terug naar alle modules](./../../../overview.md)

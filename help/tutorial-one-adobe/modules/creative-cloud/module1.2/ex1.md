---
title: Aan de slag met Workfront Fusion
description: Leer hoe u Workfront Fusion en Adobe I/O kunt gebruiken om query's uit te voeren op Adobe Firefly Services-API's
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
source-git-commit: 53ff5158eec2693703b20e7841fffbec72288210
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Aan de slag met Workfront Fusion

Leer hoe u Workfront Fusion en Adobe I/O kunt gebruiken om query&#39;s uit te voeren op Adobe Firefly Services API&#39;s.

## Nieuw scenario maken

1. Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Open **de Fusie van Workfront**.

   ![ WF Fusion ](./images/wffusion1.png)

1. Ga naar **Scenario&#39;s**.

   ![ WF Fusion ](./images/wffusion2.png)

1. Selecteer **creeer nieuw scenario**.

   ![ WF Fusion ](./images/wffusion2a.png)

1. Noem de omslag `--aepUserLdap--` en selecteer **sparen**.

   ![ WF Fusion ](./images/wffusion2b.png)

1. Selecteer uw omslag, en selecteer dan **nieuw scenario** creëren.

   ![ WF Fusion ](./images/wffusion3.png)

1. Een leeg scenario verschijnt, selecteert **hulpmiddelen** en selecteert **Vastgestelde veelvoudige variabelen**.

   ![ WF Fusion ](./images/wffusion4.png)

1. Verplaats het **klok** pictogram op de onlangs toegevoegde **Vastgestelde veelvoudige variabelen**.

   ![ WF Fusion ](./images/wffusion5.png)

   Het scherm moet er zo uitzien.

   ![ WF Fusion ](./images/wffusion6.png)

1. Klik op het vraagteken met de rechtermuisknop aan en selecteer **module van de Schrapping**.

   ![ WF Fusion ](./images/wffusion7.png)

1. Daarna, klik op **plaats veelvoudige variabelen** met de rechtermuisknop aan en selecteer **Montages**.

   ![ WF Fusion ](./images/wffusion8.png)

## Adobe I/O-verificatie configureren

U moet nu de variabelen vormen die nodig zijn om tegen Adobe I/O voor authentiek te verklaren. In de vorige oefening, creeerde u een project van Adobe I/O. De variabelen van dat Adobe I/O-project moeten nu worden gedefinieerd in Workfront Fusion.

De volgende variabelen moeten worden gedefinieerd:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `CONST_client_id` | uw Adobe I/O project Client-id |
| `CONST_client_secret` | uw Adobe I/O project Client Secret |
| `CONST_scope` | bereik van uw Adobe I/O-project |

1. Vind deze variabelen door naar [ https://developer.adobe.com/console/projects ](https://developer.adobe.com/console/projects) te gaan en uw Adobe I/O project te openen, dat `--aepUserLdap-- Firefly` wordt genoemd.

   ![ WF Fusion ](./images/wffusion9.png)

1. In uw project, uitgezochte **OAuth server-Server** om de waarden voor de bovengenoemde sleutels te zien.

   ![ WF Fusion ](./images/wffusion10.png)

1. Gebruikend de bovengenoemde sleutels en de waarden, kunt u **vormen Vastgestelde veelvoudige variabelen** voorwerp. Selecteer **toevoegen punt**.

   ![ WF Fusion ](./images/wffusion11.png)

1. Ga de **Veranderlijke naam** in: **CONST_client_id** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

   ![ WF Fusion ](./images/wffusion12.png)

1. Selecteer **toevoegen punt**.

   ![ WF Fusion ](./images/wffusion13.png)

1. Ga **Veranderlijke naam** in: **CONST_client_geheime** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

   ![ WF Fusion ](./images/wffusion14.png)

1. Selecteer **toevoegen punt**.

   ![ WF Fusion ](./images/wffusion15.png)

1. Ga **Veranderlijke naam** in: **CONST_scope** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

   ![ WF Fusion ](./images/wffusion16.png)

1. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion17.png)

1. Plaats over **veelvoudige variabelen** en selecteer het grote **+** pictogram om een andere module toe te voegen.

   ![ WF Fusion ](./images/wffusion18.png)

   Het scherm moet er zo uitzien.

   ![ WF Fusion ](./images/wffusion19.png)

1. In de onderzoeksbar, ga **http** in. Selecteer **HTTP** om het te openen.

   ![ WF Fusion ](./images/wffusion21.png)

1. Selecteer **maak een verzoek**.

   ![ WF Fusion ](./images/wffusion20.png)

   | Sleutel | Waarde |
   |:-------------:| :---------------:| 
   | `URL` | `https://ims-na1.adobelogin.com/ims/token/v3` |
   | `Method` | `POST` |
   | `Body Type` | `x-www-form-urlencoded` |

1. Selecteer **toevoegen punt**.

   ![ WF Fusion ](./images/wffusion22.png)

1. Voeg items toe voor elk van de onderstaande waarden:

   | Sleutel | Waarde |
   |:-------------:| :---------------:| 
   | `client_id` | de vooraf gedefinieerde variabele voor `CONST_client_id` |
   | `client_secret` | de vooraf gedefinieerde variabele voor `CONST_client_secret` |
   | `scope` | de vooraf gedefinieerde variabele voor `CONST_scope` |
   | `grant_type` | `client_credentials` |

1. Configuratie voor `client_id`:

   ![ WF Fusion ](./images/wffusion23.png)

1. Configuratie voor `client_secret` .

   ![ WF Fusion ](./images/wffusion25.png)

1. Configuratie voor `scope` .

   ![ WF Fusion ](./images/wffusion26.png)

1. Configuratie voor `grant_type` .

   ![ WF Fusion ](./images/wffusion28.png)

1. De rol neer en controleert de doos voor **ontleedt reactie**. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion27.png)

1. Het scherm moet er zo uitzien. Selecteer **Looppas eens**.

   ![ WF Fusion ](./images/wffusion29.png)

   Nadat het scenario is uitgevoerd, moet uw scherm er als volgt uitzien:

   ![ WF Fusion ](./images/wffusion30.png)

1. Selecteer het **vraagteken** pictogram op het **Vastgestelde veelvoudige variabelen** voorwerp om te zien wat gebeurde toen dat voorwerp liep.

   ![ WF Fusion ](./images/wffusion31.png)

1. Selecteer het **vraagteken** pictogram op **HTTP - doe een verzoek** voorwerp om te zien wat gebeurde toen dat voorwerp liep. In **OUTPUT**, zie **access_token** die door Adobe I/O wordt teruggekeerd.

   ![ WF Fusion ](./images/wffusion32.png)

1. Beweeg over **HTTP - doe een verzoek** en selecteer **+** pictogram om een andere module toe te voegen.

   ![ WF Fusion ](./images/wffusion33.png)

1. Zoek in de zoekbalk naar `tools` . Selecteer **Hulpmiddelen**.

   ![ WF Fusion ](./images/wffusion34.png)

1. Selecteer **Vastgestelde veelvoudige variabelen**.

   ![ WF Fusion ](./images/wffusion35.png)

1. Selecteer **toevoegen punt**.

   ![ WF Fusion ](./images/wffusion36.png)

1. Plaats **Veranderlijke naam** aan `bearer_token`. Selecteer `access_token` als dynamische **Variabele waarde**. Selecteer **toevoegen**.

   ![ WF Fusion ](./images/wffusion37.png)

1. Het scherm moet er zo uitzien. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion38.png)

1. Selecteer **nogmaals Looppas**.

   ![ WF Fusion ](./images/wffusion39.png)

1. Zodra het scenario loopt, selecteer het **vraagteken** pictogram op het laatste **Vastgestelde veelvoudige variabelen** voorwerp. Let op: het access_token wordt opgeslagen in de variabele `bearer_token` .

   ![ WF Fusion ](./images/wffusion40.png)

1. Daarna, klik met de rechtermuisknop op het eerste voorwerp **plaats veelvoudige waarden** en selecteer **anders noemen**.

   ![ WF Fusion ](./images/wffusion41.png)

1. Plaats de naam aan **initialiseert Constanten**. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion42.png)

1. Wijzig de naam van het tweede voorwerp aan **voor authentiek verklaren aan Adobe I/O**. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion43.png)

1. Verander de naam van het derde voorwerp aan **plaats Token van de Drager**. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion44.png)

   Uw scherm moet er als volgt uitzien:

   ![ WF Fusion ](./images/wffusion45.png)

1. Wijzig vervolgens de naam van het scenario in `--aepUSerLdap-- - Adobe I/O Authentication` .

   ![ WF Fusion ](./images/wffusion46.png)

1. Selecteer **sparen**.

   ![ WF Fusion ](./images/wffusion47.png)

## Volgende stappen

Ga naar [ Gebruik Adobe APIs binnen de Fusie van Workfront ](./ex2.md){target="_blank"}

Ga terug naar [ Automating de Diensten van de Adobe Firefly ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

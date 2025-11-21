---
title: Aan de slag met Workfront Fusion
description: Leer hoe u Workfront Fusion en Adobe I/O kunt gebruiken om Adobe Firefly Services API's te zoeken
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
source-git-commit: d4cb1ff51c9367fd0d249806e50b676d8a83c557
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# 1.2.1 Aan de slag met Workfront Fusion

Leer hoe u Workfront Fusion en Adobe I/O kunt gebruiken om Adobe Firefly Services API&#39;s te zoeken.

## 1.2.1.1 Nieuw scenario maken

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/){target="_blank"}. Open **de Fusie van Workfront**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion1.png)

Ga naar **Scenario&#39;s**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion2.png)

Klik op het pictogram **+** om een nieuwe map voor uw werk te maken.

![&#x200B; WF Fusion &#x200B;](./images/wffusion2a.png)

Noem de omslag `--aepUserLdap--` en selecteer **sparen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion2b.png)

Selecteer uw omslag, en selecteer dan **nieuw scenario** creëren.

![&#x200B; WF Fusion &#x200B;](./images/wffusion3.png)

Een leeg scenario verschijnt, selecteert **hulpmiddelen** en selecteert **Vastgestelde veelvoudige variabelen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion4.png)

Verplaats het **klok** pictogram op de onlangs toegevoegde **Vastgestelde veelvoudige variabelen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion5.png)

Het scherm moet er zo uitzien.

![&#x200B; WF Fusion &#x200B;](./images/wffusion6.png)

Klik op het vraagteken met de rechtermuisknop aan en selecteer **module van de Schrapping**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion7.png)

Daarna, klik op **plaats veelvoudige variabelen** met de rechtermuisknop aan en selecteer **Montages**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion8.png)

## 1.2.1.2 Adobe I/O-verificatie configureren

U moet nu de variabelen vormen die nodig zijn om tegen Adobe I/O voor authentiek te verklaren. In de vorige oefening, creeerde u een project van Adobe I/O. De variabelen van dat Adobe I/O-project moeten nu worden gedefinieerd in Workfront Fusion.

De volgende variabelen moeten worden gedefinieerd:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `CONST_client_id` | uw Adobe I/O-project Client-id |
| `CONST_client_secret` | uw Adobe I/O-project clientgeheim |
| `CONST_scope` | Adobe I/O-projectbereik |

Vind deze variabelen door naar [&#x200B; https://developer.adobe.com/console/projects &#x200B;](https://developer.adobe.com/console/projects){target="_blank"} te gaan en uw project van Adobe I/O te openen, dat `--aepUserLdap-- One Adobe tutorial` wordt genoemd.

![&#x200B; WF Fusion &#x200B;](./images/wffusion9.png)

In uw project, uitgezochte **OAuth server-Server** om de waarden voor de bovengenoemde sleutels te zien.

![&#x200B; WF Fusion &#x200B;](./images/wffusion10.png)

Gebruikend de bovengenoemde sleutels en de waarden, kunt u **vormen Vastgestelde veelvoudige variabelen** voorwerp. Selecteer **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion11.png)

Ga de **Veranderlijke naam** in: **`CONST_client_id`** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

![&#x200B; WF Fusion &#x200B;](./images/wffusion12.png)

Selecteer **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion13.png)

Ga **Veranderlijke naam** in: **`CONST_client_secret`** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

![&#x200B; WF Fusion &#x200B;](./images/wffusion14.png)

Selecteer **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion15.png)

Ga **Veranderlijke naam** in: **`CONST_scope`** en zijn **Veranderlijke waarde**, uitgezocht **voeg** toe.

![&#x200B; WF Fusion &#x200B;](./images/wffusion16.png)

Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion17.png)

Plaats over **veelvoudige variabelen** en selecteer het grote **+** pictogram om een andere module toe te voegen.

![&#x200B; WF Fusion &#x200B;](./images/wffusion18.png)

Het scherm moet er zo uitzien.

![&#x200B; WF Fusion &#x200B;](./images/wffusion19.png)

In de onderzoeksbar, ga **http** in. Selecteer **HTTP** om het te openen.

![&#x200B; WF Fusion &#x200B;](./images/wffusion21.png)

Selecteer **maak een verzoek**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion20.png)

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `URL` | `https://ims-na1.adobelogin.com/ims/token/v3` |
| `Method` | `POST` |
| `Body Type` | `x-www-form-urlencoded` |

Selecteer **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion22.png)

Voeg items toe voor elk van de onderstaande waarden:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `client_id` | de vooraf gedefinieerde variabele voor `CONST_client_id` |
| `client_secret` | de vooraf gedefinieerde variabele voor `CONST_client_secret` |
| `scope` | de vooraf gedefinieerde variabele voor `CONST_scope` |
| `grant_type` | `client_credentials` |

Configuratie voor `client_id`:

![&#x200B; WF Fusion &#x200B;](./images/wffusion23.png)

Configuratie voor `client_secret` .

![&#x200B; WF Fusion &#x200B;](./images/wffusion25.png)

Configuratie voor `scope` .

![&#x200B; WF Fusion &#x200B;](./images/wffusion26.png)

Configuratie voor `grant_type` .

![&#x200B; WF Fusion &#x200B;](./images/wffusion28.png)

De rol neer en controleert de doos voor **ontleedt reactie**. Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion27.png)

Het scherm moet er zo uitzien. Selecteer **Looppas eens**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion29.png)

Nadat het scenario is uitgevoerd, moet uw scherm er als volgt uitzien:

![&#x200B; WF Fusion &#x200B;](./images/wffusion30.png)

Selecteer het **vergrootglas** pictogram op het **Vastgestelde veelvoudige variabelen** voorwerp om te zien wat gebeurde toen dat voorwerp liep.

![&#x200B; WF Fusion &#x200B;](./images/wffusion31.png)

Selecteer het **vergrootglas** pictogram op **HTTP - doe een verzoek** voorwerp om te zien wat gebeurde toen dat voorwerp liep. In **OUTPUT**, zie **access_token** die door Adobe I/O wordt teruggekeerd.

![&#x200B; WF Fusion &#x200B;](./images/wffusion32.png)

Beweeg over **HTTP - doe een verzoek** en selecteer **+** pictogram om een andere module toe te voegen.

![&#x200B; WF Fusion &#x200B;](./images/wffusion33.png)

Zoek in de zoekbalk naar `tools` . Selecteer **Hulpmiddelen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion34.png)

Selecteer **Vastgestelde veelvoudige variabelen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion35.png)

Selecteer **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion36.png)

Plaats **Veranderlijke naam** aan `bearer_token`. Selecteer `access_token` als dynamische **Variabele waarde**. Selecteer **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion37.png)

Het scherm moet er zo uitzien. Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion38.png)

Selecteer **nogmaals Looppas**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion39.png)

Zodra het scenario loopt, selecteer het **vergrootglas** pictogram op het laatste **Vastgestelde veelvoudige variabelen** voorwerp. Let op: het access_token wordt opgeslagen in de variabele `bearer_token` .

![&#x200B; WF Fusion &#x200B;](./images/wffusion40.png)

Daarna, klik met de rechtermuisknop op het eerste voorwerp **plaats veelvoudige waarden** en selecteer **anders noemen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion41.png)

Plaats de naam aan **initialiseert Constanten**. Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion42.png)

Wijzig de naam van het tweede voorwerp aan **voor authentiek verklaren aan Adobe I/O**. Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion43.png)

Verander de naam van het derde voorwerp aan **plaats Token van de Drager**. Selecteer **O.K.**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion44.png)

Uw scherm moet er als volgt uitzien:

![&#x200B; WF Fusion &#x200B;](./images/wffusion45.png)

Wijzig vervolgens de naam van het scenario in `--aepUserLdap-- - Firefly + Photoshop` .

![&#x200B; WF Fusion &#x200B;](./images/wffusion46.png)

Selecteer **sparen**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion47.png)

## Volgende stappen

Ga naar [&#x200B; Automatisering gebruikend Schakelaars &#x200B;](./ex4.md){target="_blank"}

Ga terug naar [&#x200B; de Automatisering van het Werkschema van Creative met Workfront Fusion &#x200B;](./automation.md){target="_blank"}

Ga terug naar [&#x200B; Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

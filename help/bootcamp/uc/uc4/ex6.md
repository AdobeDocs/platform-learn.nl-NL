---
title: Bootkamp - Customer Journey Analytics - Van inzichten tot actie
description: Bootkamp - Customer Journey Analytics - Van inzichten tot actie
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
source-git-commit: e5c2ad88967d7f6a45d3a5cc09ca4c9bc9a62a08
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 4.6 Van inzichten naar actie

## Doelen

- Begrijp hoe te om een publiek te bouwen dat op een mening wordt gebaseerd die in Customer Journey Analytics wordt verzameld
- Dit publiek gebruiken in Real-Time CDP en Adobe Journey Optimizer

## 4.6.1 Een publiek maken en dit publiceren

In uw project, creeerde u een filter genoemd **Bellen** en konden het aantal gebruikers bekijken die hun vraag aan het vraagcentrum hadden geclassificeerd als **positief**. U kunt nu een segment maken met deze gebruikers en deze activeren via reizen of communicatiekanalen.

De eerste stap is: Selecteer regel in het deelvenster dat u tijdens de laatste oefening hebt gemaakt **1. Bellen - Positief**, klikt u met de rechtermuisknop en selecteert u de **publiek maken van selectie** optie:

![demo](./images/aud1.png)

Geef daarna een naam aan uw publiek volgens het model **yourLastName - CJA-publieksoproep voelt positief**:

![demo](./images/aud2.png)

U kunt een voorvertoning weergeven van het publiek dat wordt gemaakt:

![demo](./images/aud3.png)

Tot slot klikt u op **Publiceren**.

![demo](./images/aud4.png)

## 4.6.2 Gebruik uw publiek als onderdeel van een segment

Ga terug naar de Adobe Experience Platform, ga naar **Segmenten > Bladeren** en u zult uw segment die in CJA wordt gecreeerd klaar en beschikbaar kunnen zien om in uw activeringen en reizen worden gebruikt!

![demo](./images/aud5.png)

Laten we dit segment nu gebruiken in een Facebook-activering en in een klantentransport!

## 4.6.3 Gebruik uw segment in Real-Time CDP in real-time

Ga in Adobe Experience Platform naar **Segmenten > Bladeren** en zoek het publiek dat u in CJA hebt gemaakt:

![demo](./images/aud6.png)

Klik op uw segment en klik vervolgens op **Activeren naar doel**:

![demo](./images/aud7.png)

Benoemde bestemming selecteren **bootkamp-facebook** en klik vervolgens op **Volgende**.

![demo](./images/aud8.png)

Klikken **Volgende** opnieuw.

![demo](./images/aud9.png)

Selecteer **Oorsprong van uw publiek** en instellen op **Direct van klanten**, klikt u op **Volgende**.

![demo](./images/aud10.png)

Klikken **Voltooien**.

![demo](./images/aud11.png)

Uw segment is nu verbonden met Aangepast publiek voor Facebook. Laten we dat zelfde segment nu gebruiken in Adobe Journey Optimizer.

## 4.6.4 Gebruik uw segment in Adobe Journey Optimizer

Klik in Adobe Experience Platform op **Journey Optimizer** en klik vervolgens in het linkermenu op **Reizen** en begin een reis te maken door op **Reis maken**.

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Dan, in het linkerzijmenu, onder **Gebeurtenissen**, selecteert u **Segmentkwalificatie** en sleep het naar de reis:

![demo](./images/aud23.png)

Klik onder Segment op **Bewerken** om een segment te selecteren:

![demo](./images/aud24.png)

Selecteer het publiek dat u eerder in CJA hebt gemaakt en klik op  **Opslaan**.

![demo](./images/aud25.png)

Klaar! Van hier kunt u een reis voor klanten tot stand brengen die voor dit segment kwalificeren.

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)

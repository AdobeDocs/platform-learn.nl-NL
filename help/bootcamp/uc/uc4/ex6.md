---
title: Bootkamp - Customer Journey Analytics - Van inzichten tot actie
description: Bootkamp - Customer Journey Analytics - Van inzichten tot actie
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Audiences
exl-id: 7a38a0a4-46e4-41f2-9a75-316dfde7128f
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# 4.6 Van inzichten naar actie

## Doelen

- Begrijp hoe te om een publiek te bouwen dat op een mening wordt gebaseerd die in Customer Journey Analytics wordt verzameld
- Dit publiek gebruiken in Real-Time CDP en Adobe Journey Optimizer

## 4.6.1 Een publiek maken en dit publiceren

In uw project, creeerde u een filter riep **de Ontvangingen van de Vraag** en kon het aantal gebruikers bekijken die hun vraag aan het vraagcentrum hadden geclassificeerd als **positief**. U kunt nu een segment maken met deze gebruikers en deze activeren via reizen of communicatiekanalen.

De eerste stap is: In het paneel dat in de laatste oefening wordt gecreeerd, uitgezochte lijn **1. Het Etiketteren van de vraag - Positief**, klik met de rechtermuisknop aan en selecteer **creeer publiek van selectie** optie:

![ demo ](./images/aud1.png)

Daarna, geef een naam aan uw publiek na het model **yourLastName - CJA publieksvraag positief** voelen:

![ demo ](./images/aud2.png)

U kunt een voorvertoning weergeven van het publiek dat wordt gemaakt:

![ demo ](./images/aud3.png)

Tot slot klik **Publish**.

![ demo ](./images/aud4.png)

## 4.6.2 Gebruik uw publiek als onderdeel van een segment

Ga terug naar Adobe Experience Platform, ga naar **Segmenten > doorbladeren** en u zult uw segment kunnen zien dat in CJA klaar en beschikbaar wordt gecreeerd om in uw activeringen en reizen worden gebruikt!

![ demo ](./images/aud5.png)

Laten we dit segment nu gebruiken in een Facebook-activering en in een klantentransport!

## 4.6.3 Gebruik uw segment in Real-Time CDP in real-time

In Adobe Experience Platform, ga naar **Segmenten > doorbladeren** en het publiek vinden u in CJA hebt gecreeerd:

![ demo ](./images/aud6.png)

Klik uw segment, en klik dan **activeren aan Bestemming**:

![ demo ](./images/aud7.png)

Selecteer de bestemming genoemd **bootkamp-facebook**, en klik dan **daarna**.

![ demo ](./images/aud8.png)

Klik **daarna** opnieuw.

![ demo ](./images/aud9.png)

Selecteer de **Oorsprong van uw publiek** optie en plaats het aan **direct van klanten**, klik **daarna**.

![ demo ](./images/aud10.png)

Klik **Afwerking**.

![ demo ](./images/aud11.png)

Uw segment is nu verbonden met Aangepast publiek voor Facebook. Laten we dat zelfde segment nu gebruiken in Adobe Journey Optimizer.

## 4.6.4 Gebruik uw segment in Adobe Journey Optimizer

In Adobe Experience Platform, klik **Journey Optimizer**, en dan in het linkerzijmenu, klik **Reizen** en begin een reis te creëren door **te klikken creeer Weg**.

![ demo ](./images/aud20.png)

![ demo ](./images/aud21.png)

![ demo ](./images/aud22.png)

Dan, in het linkerzijmenu, onder **Gebeurtenissen**, selecteer **de Kwalificatie van het Segment** en sleep het aan de reis:

![ demo ](./images/aud23.png)

Onder Segment, geeft de klik **** uit om een segment te selecteren:

![ demo ](./images/aud24.png)

Selecteer het publiek u vroeger in CJA creeerde en **klik sparen**.

![ demo ](./images/aud25.png)

Klaar! Van hier kunt u een reis voor klanten tot stand brengen die voor dit segment kwalificeren.

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)

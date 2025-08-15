---
title: Verrijken publiek met opslaggegevens
seo-title: Enrich Audiences with warehouse data | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Verrijken publiek met opslaggegevens
description: In deze oefening, wordt een publiek van Experience Platform verrijkt met pakhuisgegevens.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
exl-id: 3f6aa121-0dbd-4ad9-b136-d1455eed03ca
source-git-commit: 7e2f7bbb392eba51c0d6b9ccc8224c2081a01c7c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Verrijken publiek met pakhuisgegevens

De Federatieve Samenstelling van het Publiek laat u toe om bestaand publiek in Adobe Experience Platform (AEP) te verrijken door samengestelde publieksgegevens te gebruiken die van het entrepot van ondernemingsgegevens zijn gefederaliseerd. Deze gegevens blijven niet behouden in Adobe Experience Platform-klantprofielen.

## Een publiek lezen in een federatieve compositie

In deze oefening, gebruiken wij het **SecurFinancial de Bezoeker van de Pagina van de Toepassing van de Lening** publiek dat in de Dienst van het Profiel van Experience Platform wordt opgeslagen om onze gefedereerde samenstelling te beginnen. De federatieve gegevens in Snowflake worden gebruikt om de pregoedkeuring te bepalen op basis van de kredietscore en de leningsactiviteit.

![ federated-composition-example ](assets/snowflake-preapproval.png)

### Stappen

1. **het publiek van AEP van de Kaart** aan de Federatieve bestemming van de Samenstelling van het Publiek.
2. **bouwt uw samenstelling** met het in kaart gebrachte publiek als Gelezen publiek.
3. **sluit de identiteiten** in uw gelezen publiek aan om met gefederaliseerde gegevens samen te voegen.

![ federated-method-1-1 ](assets/federated-method-1-1.png)

![ federated-method-1-2 ](assets/federated-method-1-2.png)

Wij zullen naar een ander voorbeeld bekijken om gefederaliseerde gegevens te gebruiken [ &quot;verpersoonlijking op het ogenblik&quot;leveren ](deliver-in-the-moment-personalization.md)!

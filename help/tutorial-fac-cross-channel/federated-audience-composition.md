---
title: Het Experience Platform-publiek verrijken met gefederaliseerde gegevens
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Het Experience Platform-publiek verrijken met gefederaliseerde gegevens
description: In deze visuele oefening, wordt een publiek van Experience Platform verrijkt met gefederaliseerde gegevens.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
exl-id: 3f6aa121-0dbd-4ad9-b136-d1455eed03ca
source-git-commit: 3de9721332379f9fd3dd45768ba2ca2308e09357
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Experience Platform-soorten publiek verrijken met gefederaliseerde gegevens

De Federatieve Samenstelling van het Publiek laat u toe om bestaand publiek in Adobe Experience Platform (AEP) te verrijken door samengestelde publieksgegevens te gebruiken die van het entrepot van ondernemingsgegevens zijn gefederaliseerd. Deze gegevens blijven niet behouden in Adobe Experience Platform-klantprofielen.

## Een AEP-publiek lezen binnen een Federale compositie

In deze visuele oefening, gebruiken wij het **SecurFinancial de Bezoeker van de Pagina van de Toepassing van de Lening** publiek dat in de Dienst van het Profiel van AEP wordt opgeslagen om onze gefedereerde samenstelling te beginnen. De federatieve gegevens in Snowflake worden gebruikt om de pregoedkeuring te bepalen op basis van de kredietscore en de leningsactiviteit.

![ federated-composition-example ](assets/snowflake-preapproval.png)

### Stappen

1. **het publiek van AEP van de Kaart** aan de Federatieve bestemming van de Samenstelling van het Publiek.
2. **bouwt uw samenstelling** met het in kaart gebrachte publiek als Gelezen publiek.
3. **sluit de identiteiten** in uw gelezen publiek aan om met gefederaliseerde gegevens samen te voegen.

![ federated-method-1-1 ](assets/federated-method-1-1.png)

![ federated-method-1-2 ](assets/federated-method-1-2.png)

Wij zullen naar een ander voorbeeld van het gebruiken van gefedereerde gegevens aan [ steun &quot;in-de-ogenblik&quot;verpersoonlijking ](drive-in-the-moment-personalization.md) bekijken!

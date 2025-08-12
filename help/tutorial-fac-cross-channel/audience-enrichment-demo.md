---
title: Het Experience Platform-publiek verrijken met gefederaliseerde gegevens
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Het Experience Platform-publiek verrijken met gefederaliseerde gegevens
description: In deze les verrijken we een Experience Platform-publiek met gefederaliseerde gegevens.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
hide: true
source-git-commit: a5ae2695763bc3d6dce786861dcbc15f3422c035
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---


# Samenstelling van Federated-doelgroep

De Federatieve Samenstelling van het Publiek laat u toe om bestaand publiek in Adobe Experience Platform (AEP) te verrijken door samengestelde publieksgegevens te gebruiken die van het entrepot van ondernemingsgegevens zijn gefederaliseerd. Deze gegevens blijven niet behouden in Adobe Experience Platform-klantprofielen.

## Manieren om een Federatieve Samenstelling van het Publiek te verrijken

Er zijn twee primaire methodes om een Federated Samenstelling van het Publiek te verrijken.

### &#x200B;1. Een AEP-publiek lezen binnen een federatieve samenstelling

In dit eerste voorbeeld, zullen wij **SecurFinancial de Bezoeker van de Pagina van de Toepassing van de Lening** die in de Dienst van het Profiel van AEP wordt opgeslagen gebruiken om onze gefedereerde samenstelling te beginnen. We zullen het publiek verrijken door gebruik te maken van gefedereerde gegevens in Snowflake om de voorafgaande goedkeuring te bepalen op basis van de kredietscore en de leningsactiviteit.

![ federated-composition-example ](assets/snowflake-preapproval.png)

1. **het publiek van AEP van de Kaart** aan de Federatieve bestemming van de Samenstelling van het Publiek.
2. **bouwt uw samenstelling** met het in kaart gebrachte publiek als Gelezen publiek.
3. **sluit de identiteiten** in uw gelezen publiek aan om met gefederaliseerde gegevens samen te voegen.

![ federated-method-1-1 ](assets/federated-method-1-1.png)

![ federated-method-1-2 ](assets/federated-method-1-2.png)

### &#x200B;2. De Experience Platform Audience Rule verrijken met een Federatieve Publiek

In het tweede voorbeeld gebruiken we het gefedereerde publiek dat wordt gevraagd met kredietscore en leningsactiviteit, om het gedragspubliek van webpaginasites voor toepassingen van leningen te verrijken.

Door dit publiek op de Edge te evalueren, kunnen we de vooraf goedgekeurde bezoekers van de pagina&#39;s met toepassingen voor leningen direct heroriënteren met persoonlijke aanbiedingen op de site.

![ rand-publiek-verrijkt ](assets/edge-audience-enrich.png)

1. **sparen en Begin** uw gefedereerde publiekssamenstelling. Zodra de samenstelling is gelopen, zal uw gefedereerde publiek in het publieksportaal verschijnen.
2. **bouwt een publieksregel** gebruikend profielattributen en ervaringsgebeurtenissen van de Dienst van het Profiel, die uw gefedereerd publiek opnemen.

Laten wij dit met a [ samenvatting van lessen en definitieve meta&#39;s ](conclusion.md) samenvatten!

---
title: De gegevens van uw klant opladen voor elektrificatieervaringen
description: Leer hoe u de impact van gegevens van lage kwaliteit kunt beperken, tijd tot waarde kunt beperken en rendement op investeringen kunt vermenigvuldigen door dezelfde gegevens te gebruiken voor een groot aantal gebruiksgevallen.
role: Data Engineer, Data Architect, Developer
feature: Queries
jira: KT-10323
thumbnail: 342533.jpeg
exl-id: 30574cc5-66fa-4ab8-83ed-7af710294dbf
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# De gegevens van uw klant opladen voor elektrificatieervaringen

Omnichannel-gegevens zijn een essentieel ingrediënt van energieke klantprofielen die door marketers worden gebruikt om activering te organiseren en de resulterende klantritten te meten. Organisaties staan echter voor uitdagingen bij het beheer van de kwaliteit, schaal en diversiteit van deze gegevens. Ze vereisen gestroomlijnde oplossingen om de impact van gegevens van lage kwaliteit te beperken, tijd tot waarde te beperken en rendement te vermenigvuldigen door dezelfde gegevens te gebruiken voor een groot aantal gebruiksgevallen.

In deze video wordt het volgende besproken:

* Adobe Experience Platform-mogelijkheden voor gegevensvoorbereiding die u kunt benutten
* Het verhogen van ROI van Adobe Real-Time CDP, Adobe Journey Optimizer, en Customer Journey Analytics

>[!VIDEO](https://video.tv.adobe.com/v/342533?quality=12&learn=on)

## SQL-voorbeeld

```sql
INSERT INTO summit_adv_data_prep_dataset
SELECT STRUCT(
customerId AS crmCustomerId, struct(sku AS sku, price AS sku_price, abandonTS AS abandonTS) AS abandonBrowse) AS _pfreportingonprod
FROM
(SELECT
B.personKey.sourceID AS customerId,
A.productListItems[0].SKU AS sku,
max(A.timestamp) AS abandonTS,
max(C._pfreportingonprod.price) AS price
FROM summit_adobe_analytics_dataset A,profile_attribute_14adf268_2a20_4dee_bee6_a6b0e34616a9 B,summit_product_dataset C
WHERE A._experience.analytics.customDimensions.eVars.eVar1 = B.personKey.sourceID
AND A.productListItems[0].sku = C._pfreportingonprod.sku
AND A.web.webpagedetails.URL NOT LIKE '%orderconfirmation%'
AND timestamp > current_date - interval '4 day'
GROUP BY customerId,sku
order by price desc)D;
```

Ga voor meer informatie naar de [Documentatie bij Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=nl).

>[!NOTE]
>
>Deze video is een fragment uit de Adobe Summit 2020-sessie *[Omnichannel-gegevens opnieuw opladen voor elektrificerende ervaringen](https://business.adobe.com/summit/2022/sessions/recharging-omnichannel-data-for-electrifying-exper-s409.html)*.

---
title: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - Gegevens laden van BigQuery naar Adobe Experience Platform
description: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - Gegevens laden van BigQuery naar Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 793b35c6-761f-4b0a-b0bc-3eab93c82162
source-git-commit: 608fc570f9aa172db3578664e793f35fb3f1bf50
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# 4.2.4 Gegevens laden van BigQuery naar Adobe Experience Platform

## Doelstellingen

- BigQuery-gegevens toewijzen aan een XDM-schema
- BigQuery-gegevens in Adobe Experience Platform laden
- Word vertrouwd met de BigQuery Source Connector UI

## Voordat u begint

Na de vorige oefening, zou u deze pagina in Adobe Experience Platform moeten openen:

![ demo ](./images/datasets.png)

**als u het open hebt, ga met de volgende oefening verder.**

**als u het niet open hebt, ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform/home).**

Ga in het linkermenu naar Bronnen. U zult dan de **Bronnen** homepage zien. In het **Bronnen** menu, ga naar de **** bronschakelaar van Google BigQuery en klik **Opstelling**.

![ demo ](./images/sourceshome.png)

U ziet dan het selectiescherm voor Google BigQuery-accounts. Selecteer uw rekening en klik **daarna**.

![ demo ](./images/0c.png)

U zult dan het **Uitgezochte gegevens** scherm zien.

![ demo ](./images/datasets.png)

## 4.2.4.1 Selectie van BigQuery-tabel

In het **Uitgezochte gegevens** scherm, selecteer uw dataset BigQuery. U kunt nu een voorbeeld van voorbeeldgegevens van de gegevens van Googles Analytics in BigQuery zien.

Klik **daarna**.

![ demo ](./images/datasets1.png)

## 4.2.4.2 XDM-toewijzing

U ziet nu het volgende:

![ demo ](./images/xdm4a.png)

U moet nu of een nieuwe dataset creëren of een bestaande dataset selecteren om de gegevens van Googles Analytics in te laden. Voor deze oefening, zijn een dataset en een schema reeds gecreeerd. U hoeft geen nieuw schema of nieuwe gegevensset te maken.

Selecteer **Bestaande dataset**. Open het vervolgkeuzemenu om een dataset te selecteren. Zoek naar de dataset genoemd `Demo System - Event Dataset for BigQuery (Global v1.1)` en selecteer het. Klik **daarna**.

![ demo ](./images/xdm6.png)

Omlaag schuiven. U moet nu elk **Gebied van Source** van Googles Analytics/BigQuery aan een XDM **Gebied van het Doel** in kaart brengen, gebied door gebied. U ziet mogelijk een aantal fouten, die worden verholpen door onderstaande toewijzingsexercitie.

![ demo ](./images/xdm8.png)

Gebruik de onderstaande toewijzingstabel voor deze oefening.

| Source-veld | Doelveld |
| ----------------- |-------------| 
| `_id` | `_id` |
| `_id` | kanaal._id |
| `timeStamp` | tijdstempel |
| `GA_ID` | ``--aepTenantId--``.identification.core.gaid |
| `customerID` | ``--aepTenantId--``. identification.core.crmId |
| `Page` | web.webPageDetails.name |
| `Device` | device.type |
| `Browser` | environment.browserDetails.vendor |
| `MarketingChannel` | marketing.trackingCode |
| `TrafficSource` | channel.typeAtSource |
| `TrafficMedium` | channel.mediaType |
| `TransactionID` | commerce.order.payments.transactionID |
| `Ecommerce_Action_Type` | eventType |
| `Pageviews` | web.webPageDetails.pageViews.value |


Voor sommige gebieden, moet u de originele afbeelding verwijderen en nieuwe creëren, voor a **Berekend Gebied**.

| Berekend veld | Doelveld |
| ----------------- |-------------| 
| `iif(Unique_Purchases == null, 0, Unique_Purchases)` | commerce.purchases.value |
| `iif(Product_Detail_Views == null, 0, Product_Detail_Views)` | commerce.productViews.value |
| `iif(Adds_To_Cart == null, 0, Adds_To_Cart)` | commerce.productListAdds.value |
| `iif(Product_Removes_From_Cart == null, 0, Product_Removes_From_Cart), 1, 0)` | commerce.productListRemovals.value |
| `iif(Product_Checkouts == null, 0, Product_Checkouts)` | commerce.checkouts.value |

Om a **Berekend Gebied** tot stand te brengen, klik **+ Nieuw gebiedstype** en klik dan **Berekend gebied**.

![ demo ](./images/xdm8a.png)

Plak de bovengenoemde regel en klik **sparen** voor elk van de gebieden in de bovengenoemde lijst.

![ demo ](./images/xdm8b.png)

U hebt nu a **Afbeelding** als dit.

De brongebieden **GA_ID** en **customerID** worden in kaart gebracht aan een Herkenningsteken in dit Schema XDM. Hierdoor kunt u gegevens van Googles Analytics (web/app-gedragsgegevens) verrijken met andere gegevenssets, zoals Loyalty of Call Center-data.

Klik **daarna**.

![ demo ](./images/xdm34.png)

## 4.2.4.3 Verbinding en planning van gegevensinvoer

U zult nu **het plannen** tabel {zien:

In het **Plannend** lusje, kunt u een frequentie voor het proces van gegevensopname voor dit **Afbeelding** en gegevens bepalen.

Aangezien u demo gegevens in Google BigQuery gebruikt die niet zullen worden verfrist, is er geen echte behoefte om een programma in deze oefening te plaatsen. U moet wel iets selecteren en om te veel nutteloze processen voor het opnemen van gegevens te voorkomen, moet u de frequentie als volgt instellen:

- Frequentie: **Week**
- Interval: **200**
- De tijd van het begin: **om het even welke tijd in het volgende uur**

**Belangrijk**: ben zeker u de **Achtergrond** schakelaar activeert.

Last but not least, moet u a **delta** gebied bepalen.

Het **delta** gebied wordt gebruikt om de verbinding te plannen en slechts nieuwe rijen te uploaden die in uw dataset BigQuery komen. Een deltaveld is doorgaans altijd een tijdstempelkolom. Voor toekomstige geplande gegevensinvoer worden dus alleen de rijen met een nieuwe, recentere tijdstempel opgenomen.

Selecteer **timeStamp** als deltagebied.
Klik **daarna**.

![ demo ](./images/ex437.png)

## 4.2.4.4 Verbinding controleren en starten

U ziet nu een gedetailleerd overzicht van uw verbinding. Zorg ervoor dat alles juist is voordat u verdergaat, aangezien sommige instellingen achteraf niet meer kunnen worden gewijzigd, zoals bijvoorbeeld de XDM-toewijzing.

Klik **Afwerking**.

![ demo ](./images/xdm46.png)

Zodra de verbinding is gecreeerd, zult u dit zien:

![ demo ](./images/xdm48.png)

U bent nu klaar om met de volgende oefening verder te gaan, waarin u Customer Journey Analytics zult gebruiken om krachtige visualisaties bovenop de gegevens van Googles Analytics te bouwen.

Volgende Stap: [ 4.2.5 analyseert de Gegevens van Googles Analytics gebruikend Customer Journey Analytics ](./ex5.md)

[Terug naar module 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Terug naar alle modules](./../../../overview.md)

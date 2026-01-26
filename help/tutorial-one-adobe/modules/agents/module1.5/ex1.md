---
title: CJA & ChatGPT met MCP-server
description: CJA & ChatGPT met MCP-server
kt: 5342
doc-type: tutorial
source-git-commit: ca2812e14a22b80b7f00066f9cc482e708b4ac6a
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# 1.5.1 CJA en ChatGPT met MCP-server

>[!IMPORTANT]
>
>Dit laboratorium gebruikt een eigenschap die nog niet is vrijgegeven. De functie wordt nog steeds ontwikkeld, zodat deze nog niet algemeen beschikbaar is.


>[!NOTE]
>
>Deze oefening op vestiging en het gebruiken van een Server MCP met ChatGPT om met CJA te verbinden is verwant met deze oefening [&#x200B; 1.1 Customer Journey Analytics: Bouw een dashboard gebruikend Analysis Workspace bovenop Adobe Experience Platform &#x200B;](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md). De CJA-gegevensweergave en -verbinding die in de onderstaande exercitie worden gebruikt, zijn de gegevensweergave en de verbinding die in die oefening is ingesteld. Als u de onderstaande resultaten wilt herhalen, volgt u deze instructies eerst.

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3479159?quality=12&learn=on)

## 1.5.1.1 Een aangepaste app maken in ChatGPT voor CJA

>[!NOTE]
>
>Voor het gebruik van CJA in ChatGPT is het volgende vereist:
>- een betaalde versie van ChatGPT van OpenAI
>- de ChatGPT-webclient gebruiken

Ga naar [&#x200B; https://chatgpt.com/ &#x200B;](https://chatgpt.com/){target="_blank"} en login die uw rekeningsdetails gebruiken. Nadat u zich hebt aangemeld, kunt u dit beter zien. Klik op uw gebruikersnaam.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt1.png)

Selecteer **Montages**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt2.png)

Ga naar **Apps** en selecteer dan **Geavanceerde montages**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt3.png)

Zet **wijze van de Ontwikkelaar** aan en klik dan **terug**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt4.png)

Klik **Create app**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt5.png)

Vul de velden als volgt in:

- **Naam**: `CJA`
- **URL van de Server MCP**: controle met uw vertegenwoordiger van Adobe
- **Authentificatie**: `OAuth`

Controleer checkbox voor **ik begrijp en wil** verdergaan.

Klik **creëren**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt6.png)

Nadat u zich hebt aangemeld, ziet u dat de CJA-toepassing nu verbinding heeft.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt8.png)

## 1.5.1.2 Context instellen in CJA

Sluit dit venster.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt9.png)

Dan moet je dit zien. Klik **+** pictogram, ga **Meer** en selecteer dan **CJA**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt10.png)

Voordat u via ChatGPT verder kunt gaan met CJA, moet de context worden ingesteld.

Voor deze exercitie moet de context worden ingesteld op:

- **Dataview**: **- aepUserLDAP - de Mening van Gegevens Omnichannel**

Met de gegevensweergave-instelling kunt u bepalen naar welke gegevensweergave ChatGPT moet worden gekeken wanneer u vragen stelt.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
list dataviews
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt11.png)

Vervolgens wordt een vergelijkbare lijst met beschikbare gegevensweergaven weergegeven.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt11a.png)

Om dat aan de gegevensmening te veranderen die moet worden gebruikt, ga de volgende **Herinnering** in en klik **verzend** knoop.

```javascript
switch to dataview --aepUserLdap-- - Omnichannel Data View
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt12.png)

Dan moet je dit zien.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt16.png)

Uw context is nu correct ingesteld, zodat u volgende specifieke vragen kunt verzenden.

## 1.5.1.3 De gegevensweergave verkennen

>[!NOTE]
>
>De gegevensmening die hier wordt gebruikt is opstelling als deel van oefening [&#x200B; creeert een gegevensmening &#x200B;](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md).

Ga de volgende **Herinnering** in en klik **verzenden** knoop om te onderzoeken welke metriek en afmetingen aan u beschikbaar zijn.

```javascript
list the available metrics and dimensions
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt101.png)

U zou deze reactie dan moeten zien, die de metriek en de dimensies omvat die opstelling als deel van de oefening [&#x200B; creeert een gegevensmening &#x200B;](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md).

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt102.png)

## 1.5.1.4 Vrije-vormtabel - Productweergaven

U kunt nu de gegevens gaan verkennen. Begin door de hieronder herinnering in te gaan en **te klikken verzendt** om uw rapportverzoek voor te leggen.

```javascript
how many product views happened on January 21?
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt103.png)

Selecteer **RunReport**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt104.png)

Dan zie je een reactie als deze.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt105.png)

U kunt de reactie nu onderbreken door een dimensie toe te voegen. Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
break down product views by product name
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt106.png)

Dan zie je een reactie als deze.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt107.png)

U kunt nu ook een visualisatie maken. Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
create a line visualization by hour for product views on January 21
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt108.png)

Selecteer **UpsertProject**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt109.png)

Selecteer **RunReport**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt110.png)

Dan moet je dit zien.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt111.png)

Omlaag schuiven.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt112.png)

U kunt deze lijngrafiek nu ook downloaden. Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
export this chart to PNG
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt113.png)

Dan moet je dit zien. Klik **Download PNG**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt114.png)

Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
can you breakdown product views by user agent?
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt115.png)

Selecteer **RunReport**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt116.png)

Dan moet je dit zien.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt117.png)

## 1.5.1.5 Visualisatie van de val

Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
can you create a fallout visualization for the product interaction funnel, starting with all traffic and then in the next steps add Product Views, Add to Cart and purchases?
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt118.png)

Selecteer **UpsertProject**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt119.png)

Selecteer **RunReport**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt120.png)

Dan moet je iets dergelijks zien. Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
can you show me a visualization of the above fallout analysis?
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt120a.png)

Klik **Download PNG**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt121.png)

Je ziet nu de visualisatie van je falloutanalyse.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt122.png)

Ga de volgende **herinnering** in en klik **verzenden** knoop.

```javascript
break down the fallout analysis at the touchpoint of the add to carts
```

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt123.png)

Selecteer **RunReport**.

![&#x200B; ChatGPT &amp; CJA &#x200B;](./images/chatgpt124.png)

Ga terug naar [&#x200B; Analytics &amp; Agenten &#x200B;](./analyticsagents.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
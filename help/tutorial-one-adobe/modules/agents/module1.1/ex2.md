---
title: Adobe Marketing Agent met ChatGPT
description: Adobe Marketing Agent met ChatGPT
kt: 5342
doc-type: tutorial
source-git-commit: 9663ef2838024e293acc72c203b1e3578911d57f
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# 1.1.2 Adobe Marketing Agent met ChatGPT

>[!IMPORTANT]
>
>Dit laboratorium gebruikt een eigenschap die nog niet is vrijgegeven. De functie wordt nog steeds ontwikkeld, zodat deze nog niet algemeen beschikbaar is.

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3478410?quality=12&learn=on)

## 1.1.2.1 Een aangepaste app maken in ChatGPT voor Adobe Marketing Agent

>[!NOTE]
>
>Voor het gebruik van Adobe Marketing Agent in ChatGPT is het volgende vereist:
>- een betaalde versie van ChatGPT van OpenAI
>- de ChatGPT-webclient gebruiken

Ga naar https://chatgpt.com/ en meld u aan met uw accountgegevens. Nadat u zich hebt aangemeld, kunt u dit beter zien. Klik op uw gebruikersnaam.

![ ChatGPT ](./images/chatgpt1.png)

Selecteer **Montages**.

![ ChatGPT ](./images/chatgpt2.png)

Ga naar **Apps** en selecteer dan **Geavanceerde montages**.

![ ChatGPT ](./images/chatgpt3.png)

Zet **wijze van de Ontwikkelaar** aan en klik dan **terug**.

![ ChatGPT ](./images/chatgpt4.png)

Klik **Create app**.

![ ChatGPT ](./images/chatgpt5.png)

Vul de velden als volgt in:

- **Naam**: `Adobe Marketing Agent`
- **URL van de Server MCP**: controle met uw vertegenwoordiger van Adobe
- **Authentificatie**: `OAuth`

Controleer checkbox voor **ik begrijp en wil** verdergaan.

Klik **creëren**.

![ ChatGPT ](./images/chatgpt6.png)

ChatGPT probeert nu verbinding te maken met uw Adobe-account. Selecteer **Toestaan Toegang** en dan zult u login met uw rekening van Adobe moeten.

![ ChatGPT ](./images/chatgpt7.png)

Zodra u zich met succes hebt aangemeld, zou u moeten zien dat uw Adobe Marketing Agent nu met succes wordt verbonden.

![ ChatGPT ](./images/chatgpt8.png)

## 1.1.2.2 Context instellen in Adobe Marketing Agent

Sluit dit venster.

![ Agent Orchestrator ](./images/chatgpt9.png)

Dan moet je dit zien. Klik **+** pictogram, ga **Meer** en selecteer dan **Adobe Marketing Agent**.

![ Agent Orchestrator ](./images/chatgpt10.png)

Voordat u via ChatGPT verder kunt gaan met Adobe Marketing Agent, moet de context worden ingesteld.

Voor deze exercitie moet de context worden ingesteld op:

- **Sandbox**: **Prod - versnelt (VA7)**

Met de instelling Sandbox kunt u bepalen naar welke sandbox AI-assistent moet worden gekeken wanneer vragen worden gesteld.

- **Dataview**: **versnelt 2026 B2C**

Met de instelling Gegevensweergave kunt u bepalen naar welke AI-assistent voor gegevensweergave moet worden gekeken wanneer u vragen stelt.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
list sandboxes
```

![ Agent Orchestrator ](./images/chatgpt11.png)

Vervolgens wordt een vergelijkbare lijst met beschikbare sandboxen weergegeven. De huidige zandbak in dit voorbeeld wordt geplaatst aan **prod**.

Om dat aan zandbak te veranderen die moet worden gebruikt, ga de volgende **Herinnering** in en klik **verzend** knoop.

```javascript
switch to sandbox accelerate
```

![ Agent Orchestrator ](./images/chatgpt12.png)

Dan moet je dit zien. Klik **Vastgestelde Context**.

![ Agent Orchestrator ](./images/chatgpt13.png)

Dan moet je dit zien. Ga de volgende **Herinnering** in en klik **verzenden** knoop om de gegevensmening te plaatsen om te gebruiken.

```javascript
list dataviews
```

![ Agent Orchestrator ](./images/chatgpt14.png)

Vervolgens wordt een vergelijkbare lijst met beschikbare sandboxen weergegeven. De huidige zandbak in dit voorbeeld wordt geplaatst aan **prod**.

Om dat aan zandbak te veranderen die moet worden gebruikt, ga de volgende **Herinnering** in en klik **verzend** knoop.

```javascript
switch to Accelerate 2026 B2C
```

![ Agent Orchestrator ](./images/chatgpt15.png)

Dan moet je dit zien. Klik **Vastgestelde Context**.

![ Agent Orchestrator ](./images/chatgpt16.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/chatgpt17.png)

Uw context heeft nu de juiste set, zodat u volgende specifieke aanwijzingen kunt verzenden.

## 1.1.2.3 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![ Agent Orchestrator ](./images/chatgpt18.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/chatgpt19.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![ Agent Orchestrator ](./images/chatgpt20.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

![ Agent Orchestrator ](./images/chatgpt21.png)

## 1.1.2.4 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat een voorkeur voor een specifieke genre (bijvoorbeeld, SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Eerst moet u erachter komen welk veld wordt gebruikt om de voorkeur voor genre op te slaan.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which field is used to store the preferred genre in the sandbox accelerate?
```

![ Agent Orchestrator ](./images/chatgpt22.png)

Vervolgens ziet u dit. Het veld dat voor genre wordt gebruikt, is **_experiencePlatform.individualCharacteristics.preferences.preferredGenre** .

![ Agent Orchestrator ](./images/chatgpt23.png)

Met deze informatie kunt u beginnen met het uitboren in de aankoopgegevens.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![ Agent Orchestrator ](./images/chatgpt24.png)

Dan moet je dit zien. Klik **Onderzoek**.

![ Agent Orchestrator ](./images/chatgpt25.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/chatgpt26.png)

Schuif omlaag voor meer informatie.

![ Agent Orchestrator ](./images/chatgpt27.png)

## 1.1.2.5 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![ Agent Orchestrator ](./images/chatgpt28.png)

Dan moet je dit zien. Klik **Onderzoek**.

![ Agent Orchestrator ](./images/chatgpt29.png)

Daarna moet u een lijst met reizen zien.

![ Agent Orchestrator ](./images/chatgpt30.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![ Agent Orchestrator ](./images/chatgpt31.png)

Dan moet je dit zien. Klik **Onderzoek**.

![ Agent Orchestrator ](./images/chatgpt32.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/chatgpt33.png)

Schuif omlaag voor meer details.

![ Agent Orchestrator ](./images/chatgpt34.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![ Agent Orchestrator ](./images/chatgpt35.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/chatgpt36.png)

## 1.1.2.6 De reisprestaties valideren via een falloutanalyse

**Intentie**

U wilt de gevolgen van de reisprestaties begrijpen om te weten of zijn er om het even welke knopen of omstandigheden binnen de reis die een groot percentage van profielen ervaren die worden gelaten vallen. Dit is nuttig om te begrijpen of er extra aanpassingen nodig zijn in de reis.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![ Agent Orchestrator ](./images/chatgpt37.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/chatgpt38.png)

Schuif een beetje omlaag. U kunt de lijst nu herzien door elke knoop en zijn respectieve ingaat aantallen, valutanummers, en valutarief te inspecteren.

![ Agent Orchestrator ](./images/chatgpt39.png)

Schuif een beetje meer omlaag om waarnemingen en aanbevelingen te zien.

![ Agent Orchestrator ](./images/chatgpt40.png)

Je hebt dit lab voltooid.

Ga terug naar [ Agent Orchestrator ](./agentorchestrator.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
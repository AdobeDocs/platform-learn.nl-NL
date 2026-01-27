---
title: Adobe Marketing Agent for ChatGPT Enterprise
description: Adobe Marketing Agent for ChatGPT Enterprise
kt: 5342
doc-type: tutorial
source-git-commit: 44d0e98ae4c7568411cb0e01ed8eff38b4a34137
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 0%

---

# 1.1.2 Adobe Marketing Agent for ChatGPT Enterprise

>[!IMPORTANT]
>
>Dit laboratorium gebruikt een eigenschap die nog niet is vrijgegeven. De functie wordt nog steeds ontwikkeld, zodat deze nog niet algemeen beschikbaar is.

[!BADGE &#x200B; In Ontwikkeling &#x200B;]

+++In details over ontwikkeling
Door de Adobe Marketing Agent for ChatGPT Enterprise Beta te gebruiken, bevestigt u hierbij dat de Beta &quot;as is&quot; wordt geleverd zonder enige garantie. Adobe is niet verplicht de Beta te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen. U wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de juiste werking of prestaties van dergelijke Beta en/of begeleidende materialen. De Beta wordt beschouwd als vertrouwelijke informatie van Adobe.  Alle &quot;Feedback&quot; (informatie over de Beta, inclusief maar niet beperkt tot problemen of defecten die u tegenkomt bij het gebruik van de Beta, suggesties, verbeteringen en aanbevelingen) die u aan Adobe verstrekt, worden hierbij aan Adobe toegewezen, inclusief alle rechten, titel en interesse in en voor dergelijke feedback.

+++

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3478410?quality=12&learn=on)

## 1.1.2.1 Een aangepaste app maken in ChatGPT Enterprise voor Adobe Marketing Agent

>[!NOTE]
>
>Voor het gebruik van Adobe Marketing Agent in ChatGPT is het volgende vereist:
>- Een betaalde versie van ChatGPT Enterprise van OpenAI
>- de ChatGPT Enterprise-webclient gebruiken

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

- **Naam**: `Adobe Marketing Agent`
- **URL van de Server MCP**: controle met uw vertegenwoordiger van Adobe
- **Authentificatie**: `OAuth`

Controleer checkbox voor **ik begrijp en wil** verdergaan.

Klik **creëren**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt6.png)

ChatGPT probeert nu verbinding te maken met uw Adobe-account. Selecteer **Toestaan Toegang** en dan zult u login met uw rekening van Adobe moeten.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt7.png)

Zodra u zich met succes hebt aangemeld, zou u moeten zien dat uw Adobe Marketing Agent nu met succes wordt verbonden.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt8.png)

## 1.1.2.2 Context instellen in Adobe Marketing Agent

Sluit dit venster.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt9.png)

Dan moet je dit zien. Klik **+** pictogram, ga **Meer** en selecteer dan **Adobe Marketing Agent**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt10.png)

Voordat u via ChatGPT verder kunt gaan met Adobe Marketing Agent, moet de context worden ingesteld.

Voor deze exercitie moet de context worden ingesteld op:

- **Sandbox**: **Prod - versnelt (VA7)**

Met de instelling Sandbox kunt u bepalen naar welke sandbox ChatGPT moet worden gekeken wanneer u vragen stelt.

- **Dataview**: **versnelt 2026 B2C**

Met de gegevensweergave-instelling kunt u bepalen naar welke gegevensweergave ChatGPT moet worden gekeken wanneer u vragen stelt.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
list sandboxes
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt11.png)

Vervolgens wordt een vergelijkbare lijst met beschikbare sandboxen weergegeven. De huidige zandbak in dit voorbeeld wordt geplaatst aan **prod**.

Om dat aan zandbak te veranderen die moet worden gebruikt, ga de volgende **Herinnering** in en klik **verzend** knoop.

```javascript
switch to sandbox accelerate
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt12.png)

Dan moet je dit zien. Klik **Vastgestelde Context**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt13.png)

Dan moet je dit zien. Ga de volgende **Herinnering** in en klik **verzenden** knoop om de gegevensmening te plaatsen om te gebruiken.

```javascript
list dataviews
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt14.png)

Vervolgens wordt een vergelijkbare lijst met beschikbare gegevensweergaven weergegeven.

Om de gegevensmening te plaatsen die moet worden gebruikt, ga de volgende **Herinnering** in en klik **verzendt** knoop.

```javascript
switch to Accelerate 2026 B2C
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt15.png)

Dan moet je dit zien. Klik **Vastgestelde Context**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt16.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt17.png)

Uw context heeft nu de juiste set, zodat u volgende specifieke aanwijzingen kunt verzenden.

## 1.1.2.3 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt18.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt19.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt20.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt21.png)

## 1.1.2.4 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat een voorkeur voor een specifieke genre (bijvoorbeeld, SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Eerst moet u erachter komen welk veld wordt gebruikt om de voorkeur voor genre op te slaan.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which field is used to store the preferred genre in the sandbox accelerate?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt22.png)

Vervolgens ziet u dit. Het veld dat voor genre wordt gebruikt, is **_experiencePlatform.individualCharacteristics.preferences.preferredGenre** .

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt23.png)

Met deze informatie kunt u beginnen met het uitboren in de aankoopgegevens.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt24.png)

Dan moet je dit zien. Klik **Onderzoek**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt25.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt26.png)

Schuif omlaag voor meer informatie.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt27.png)

## 1.1.2.5 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt28.png)

Dan moet je dit zien. Klik **Onderzoek**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt29.png)

Daarna moet u een lijst met reizen zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt30.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt31.png)

Dan moet je dit zien. Klik **Onderzoek**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt32.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt33.png)

Schuif omlaag voor meer details.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt34.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt35.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt36.png)

## 1.1.2.6 De reisprestaties valideren via een falloutanalyse

**Intentie**

U wilt de gevolgen van de reisprestaties begrijpen om te weten of zijn er om het even welke knopen of omstandigheden binnen de reis die een groot percentage van profielen ervaren die worden gelaten vallen. Dit is nuttig om te begrijpen of er extra aanpassingen nodig zijn in de reis.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt37.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt38.png)

Schuif een beetje omlaag. U kunt de lijst nu herzien door elke knoop en zijn respectieve ingaat aantallen, valutanummers, en valutarief te inspecteren.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt39.png)

Schuif een beetje meer omlaag om waarnemingen en aanbevelingen te zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt40.png)

Je hebt dit lab voltooid.

Ga terug naar [&#x200B; Agent Orchestrator &#x200B;](./agentorchestrator.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
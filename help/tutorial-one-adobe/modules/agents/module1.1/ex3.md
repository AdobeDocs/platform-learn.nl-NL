---
title: Adobe Marketing Agent met Microsoft Copilot
description: Adobe Marketing Agent met Microsoft Copilot
kt: 5342
doc-type: tutorial
source-git-commit: 1eafbf27de93b45288bec8cb3cd70f04e8cc715e
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---

# 1.1.3 Adobe Marketing Agent met Microsoft Copilot

[!BADGE Bèta]

+++Zie details
Door de Adobe Marketing Agent samen met Microsoft Copilot Beta te gebruiken, bevestigt u hierbij dat de Beta wordt geleverd &quot;zoals is&quot; zonder enige garantie van welke aard ook. Adobe is niet verplicht de Beta te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen. U wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de juiste werking of prestaties van dergelijke Beta en/of begeleidende materialen. De Beta wordt beschouwd als vertrouwelijke informatie van Adobe.  Alle &quot;Feedback&quot; (informatie over de Beta, inclusief maar niet beperkt tot problemen of defecten die u tegenkomt bij het gebruik van de Beta, suggesties, verbeteringen en aanbevelingen) die u aan Adobe verstrekt, worden hierbij aan Adobe toegewezen, inclusief alle rechten, titel en interesse in en voor dergelijke feedback.

+++

>[!IMPORTANT]
>
>Dit laboratorium gebruikt een eigenschap die nog niet is vrijgegeven. De functie wordt nog steeds ontwikkeld, zodat deze nog niet algemeen beschikbaar is.

## Vereisten

Om de stappen in dit laboratorium te volgen zoals hieronder gedocumenteerd, wordt de volgende toegang vereist:

- Toegang tot Real-Time CDP, Journey Optimizer en Customer Journey Analytics
- Toegang tot AI Assistant in Adobe Experience Cloud
- Toegang tot AEP Agent Orchestrator
- Toegang tot Microsoft Copilot

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3479158?quality=12&learn=on)

## 1.1.3.1 Adobe Marketing Agent toevoegen aan Microsoft Teams en Copilot

Open Microsoft Teams en meld u aan met uw accountgegevens. Nadat u zich hebt aangemeld, kunt u dit beter zien.

Klik **Apps**.

![&#x200B; ChatGPT &#x200B;](./images/copilot1.png)

Selecteer **beheer uw apps**.

![&#x200B; ChatGPT &#x200B;](./images/copilot2.png)

Selecteer **uploadt app**.

![&#x200B; ChatGPT &#x200B;](./images/copilot3.png)

Selecteer **uploadt een douanetoepassing**.

![&#x200B; ChatGPT &#x200B;](./images/copilot4.png)

Selecteer het manifestdossier dat aan u door uw instructeur werd gegeven en klik **Open**.

![&#x200B; ChatGPT &#x200B;](./images/copilot5.png)

Klik **toevoegen**.

![&#x200B; ChatGPT &#x200B;](./images/copilot6.png)

Klik **Open met Copilot**.

![&#x200B; ChatGPT &#x200B;](./images/copilot7.png)

Adobe Marketing Agent is nu geladen.

![&#x200B; ChatGPT &#x200B;](./images/copilot8.png)

Ga de herinnering `login` in en klik **verzenden** knoop.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin1.png)

Klik **Teken binnen aan Adobe Marketing Agent**.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin2.png)

Er wordt een nieuw venster geopend waarin u wordt gevraagd u aan te melden met uw Adobe-accountgegevens.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin3.png)

Na succesvolle authentificatie, kunt u de specifieke instantie moeten selecteren u wilt gebruiken. Selecteer de instantie aepImsOrgName als dit scherm wordt weergegeven.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin4.png)

Vervolgens wordt een vergelijkbare code gegenereerd. Klik **Exemplaar** om de code te kopiëren.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin5.png)

Plak de code in het venster van Adobe Marketing Agent in Copilot en klik **verzenden** knoop.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin6.png)

Dan zou je iets gelijkaardigs moeten zien. U bent nu aangemeld bij Adobe Marketing Agent in Microsoft Copilot.

![&#x200B; ChatGPT &#x200B;](./images/copilotlogin7.png)

## 1.1.3.2 Context instellen in Adobe Marketing Agent

Voordat we verder kunnen gaan met Adobe Marketing Agent via Copilot, moet de context worden vastgesteld.

Voor deze exercitie moet de context worden ingesteld op:

- **Sandbox**: **Prod - versnelt (VA7)**

  Met de instelling van de sandbox kunt u bepalen naar welke sandbox AI-assistent moet worden gekeken wanneer vragen worden gesteld.

- **Dataview**: **versnelt 2026 B2C**

  Met de instelling voor gegevensweergave kunt u bepalen naar welke AI-assistent voor gegevensweergave moet worden gekeken wanneer u vragen stelt.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilotlogin7.png)

Om de zandbak te veranderen, ga het volgende bevel in en klik **verzend** knoop.

```javascript
change sandbox
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot9.png)

Dan zou je iets gelijkaardigs moeten zien. Selecteer zandbak u moet gebruiken en **selecteren** klikken.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot10.png)

Dan moet je dit zien. Om de gegevensmening te veranderen, ga het volgende bevel in en klik **verzend** knoop.

```javascript
change dataview
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot11.png)

Dan zou je iets gelijkaardigs moeten zien. Selecteer de gegevensmening u moet gebruiken en **selecteren** klikken.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot12.png)

Dan moet je dit zien. De context is nu op de juiste wijze ingesteld, zodat u nu specifieke aanwijzingen kunt verzenden.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot13.png)

## 1.1.3.3 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 4 months.
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot18.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot19.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory = Fiber over the last 4 months broken down by week
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot20.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot21.png)

## 1.1.3.4 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat een voorkeur voor een specifieke genre (bijvoorbeeld, SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Eerst moet u erachter komen welk veld wordt gebruikt om de voorkeur voor genre op te slaan.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which field is used to store the preferred genre
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot22.png)

Vervolgens ziet u dit. Het veld dat voor genre wordt gebruikt, is **_experiencePlatform.individualCharacteristics.preferences.preferredGenre** .

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot23.png)

Met deze informatie kunt u beginnen met het uitboren in de aankoopgegevens.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 4 months
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot24.png)

Dan moet je dit zien. Klik **Gegevens van de Mening**.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot25.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot26.png)

## 1.1.3.5 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot28.png)

Daarna moet u een lijst met reizen zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot29.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot31.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot33.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot35.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot36.png)

## 1.1.3.6 De reisprestaties valideren via een falloutanalyse

**Intentie**

U wilt de gevolgen van de reisprestaties begrijpen om te weten of zijn er om het even welke knopen of omstandigheden binnen de reis die een groot percentage van profielen ervaren die worden gelaten vallen. Dit is nuttig om te begrijpen of er extra aanpassingen nodig zijn in de reis.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot37.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot38.png)

Schuif een beetje meer omlaag om waarnemingen en aanbevelingen te zien. Klik de 3 punten **..** en selecteer dan **Details van de Reis** om de specifieke reis in Adobe Journey Optimizer te openen.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot40.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/copilot41.png)

Je hebt dit lab voltooid.

Ga terug naar [&#x200B; Agent Orchestrator &#x200B;](./agentorchestrator.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
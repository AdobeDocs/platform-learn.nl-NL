---
title: Adobe Marketing Agent for Google Gemini Enterprise
description: Adobe Marketing Agent for Google Gemini Enterprise
kt: 5342
doc-type: tutorial
exl-id: 62b0b307-599b-4165-819b-cac61a8c5d28
source-git-commit: 2b80701ddfd40896bc4dc149de1008f3ff86df4b
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 0%

---

# 1.1.4 Adobe Marketing Agent voor Google Gemini Enterprise

[!BADGE Bèta]

+++Beta-gegevens
Door de Adobe Marketing Agent samen met Google Gemini Enterprise Beta te gebruiken, bevestigt u hierbij dat de Beta &quot;as is&quot; wordt geleverd zonder enige garantie. Adobe is niet verplicht de Beta te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen. U wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de juiste werking of prestaties van dergelijke Beta en/of begeleidende materialen. De Beta wordt beschouwd als vertrouwelijke informatie van Adobe.  Alle &quot;Feedback&quot; (informatie over de Beta, inclusief maar niet beperkt tot problemen of defecten die u tegenkomt bij het gebruik van de Beta, suggesties, verbeteringen en aanbevelingen) die u aan Adobe verstrekt, worden hierbij aan Adobe toegewezen, inclusief alle rechten, titel en interesse in en voor dergelijke feedback.

+++

## Vereisten

Om de stappen in dit laboratorium te volgen zoals hieronder gedocumenteerd, wordt de volgende toegang vereist:

- Toegang tot Real-Time CDP, Journey Optimizer en Customer Journey Analytics
- Toegang tot AI Assistant in Adobe Experience Cloud
- Toegang tot AEP Agent Orchestrator
- Toegang tot Google Gemini Enterprise

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3481322?quality=12&learn=on)

Dit lab is in ontwikkeling.

## 1.1.4.1 Toegang tot Google Gemini Enterprise

Ga naar [&#x200B; https://cloud.google.com/gemini-enterprise &#x200B;](https://cloud.google.com/gemini-enterprise). Klik **Begin 30 dag vrije proef**.

![&#x200B; Gemini &#x200B;](./images/gemini1.png)

Ga het e-mailadres van uw Google rekening in en klik **verdergaan met e-mail**.

![&#x200B; Gemini &#x200B;](./images/gemini2.png)

Verstrek uw eerste en achternaam en klik dan **akkoord &amp; begonnen worden**.

![&#x200B; Gemini &#x200B;](./images/gemini3.png)

Klik **ik zal dit later** doen.

![&#x200B; Gemini &#x200B;](./images/gemini4.png)

Dan moet je dit zien.

![&#x200B; Gemini &#x200B;](./images/gemini5.png)

Ga naar [&#x200B; https://cloud.google.com/gemini-enterprise &#x200B;](https://cloud.google.com/gemini-enterprise).

Dan moet je iets dergelijks zien. Mogelijk moet u ook eerst uw factureringsaccount maken en deze daarna hier selecteren.

![&#x200B; Gemini &#x200B;](./images/gemini6.png)

Klik **Begin 30 dag kostenvrije proef**.

![&#x200B; Gemini &#x200B;](./images/gemini7.png)

Klik **verdergaan en activeren API**.

![&#x200B; Gemini &#x200B;](./images/gemini8.png)

Klik **creëren**.

![&#x200B; Gemini &#x200B;](./images/gemini9.png)

Dan moet je dit zien.

![&#x200B; Gemini &#x200B;](./images/gemini10.png)

## 1.1.4.2 Een aangepaste agent maken met A2A

Ga naar [&#x200B; https://console.cloud.google.com/gemini-enterprise &#x200B;](https://console.cloud.google.com/gemini-enterprise). Klik **Agenten**.

![&#x200B; Gemini &#x200B;](./images/gemini10a.png)

Klik **+ voeg agent** toe.

![&#x200B; Gemini &#x200B;](./images/gemini11.png)

Selecteer **de agent van de Douane via A2A**.

![&#x200B; Gemini &#x200B;](./images/gemini12.png)

Plak de **Kaart JSON van de Agent**.

>[!NOTE]
>
>Controle met uw vertegenwoordiger van Adobe om de **Kaart JSON van de Agent** informatie te krijgen.

![&#x200B; Gemini &#x200B;](./images/gemini13.png)

Na het kleven van de **Kaart JSON van de Agent**, klik **de agentendetails van de Voorproef**.

![&#x200B; Gemini &#x200B;](./images/gemini14.png)

Dan moet je iets dergelijks zien. De rol neer en klikt **daarna**.

![&#x200B; Gemini &#x200B;](./images/gemini15.png)

Dan moet je iets dergelijks zien.

![&#x200B; Gemini &#x200B;](./images/gemini16.png)

Vul de velden voor uw instantie in.

- **identiteitskaart van de Cliënt**:

```
--aepImsOrgId--
```

- **Geheim van de Cliënt**:

```
AdobeMarketingAgent
```

- **Vergunning URL**:

```
https://XXX.adobe.io/authorize
```

- **Symbolische URL**:

```
https://XXX.adobe.io/token
```

- **Scopes**:

```
openid email profile
```

Klik **Afwerking**.

![&#x200B; Gemini &#x200B;](./images/gemini17.png)

Dan moet je dit zien.

![&#x200B; Gemini &#x200B;](./images/gemini18.png)

## 1.1.4.3 Aanmelden bij Adobe Marketing Agent

Ga naar **Overzicht** en klik dan **Voorproef**.

![&#x200B; Gemini &#x200B;](./images/gemini19.png)

Klik **begonnen krijgen**

![&#x200B; Gemini &#x200B;](./images/gemini20.png)

Ga naar **Agenten**. U zou **Adobe Marketing Agent** daar moeten zien.

![&#x200B; Gemini &#x200B;](./images/gemini21.png)

Klik de 3 punten **..** en selecteer dan **Vastzetten**.

![&#x200B; Gemini &#x200B;](./images/gemini22.png)

Ga naar **Nieuwe praatje** en ga het symbool **@** in het praatje in. Klik **Adobe Marketing Agent**.

![&#x200B; Gemini &#x200B;](./images/gemini23.png)

Ga het bevel `login` in en klik dan **verzenden**.

![&#x200B; Gemini &#x200B;](./images/gemini24.png)

Dan moet je dit zien. Klik **autoriseren**.

![&#x200B; Gemini &#x200B;](./images/gemini25.png)

Klik **Toestaan Toegang** en voltooi login gebruikend uw Adobe ID, en selecteer de instantie `--aepImsOrgName--` wanneer ertoe aangezet.

![&#x200B; Gemini &#x200B;](./images/gemini26.png)

Dan moet je dit zien.

![&#x200B; Gemini &#x200B;](./images/gemini27.png)

## 1.1.4.4 Context instellen in Adobe Marketing Agent

Voordat we verder kunnen gaan met Adobe Marketing Agent via Copilot, moet de context worden vastgesteld.

Voor deze exercitie moet de context worden ingesteld op:

- **Sandbox**: **Prod - versnelt (VA7)**

  Met de instelling van de sandbox kunt u bepalen naar welke sandbox AI-assistent moet worden gekeken wanneer vragen worden gesteld.

- **Dataview**: **versnelt 2026 B2C**

Met de instelling voor gegevensweergave kunt u bepalen naar welke AI-assistent voor gegevensweergave moet worden gekeken wanneer u vragen stelt.

Om de zandbak te veranderen, ga het volgende bevel in en klik **verzend** knoop.

```javascript
list sandboxes
```

![&#x200B; Agent Orchestrator &#x200B;](./images/gemini28.png)

Dan zou je iets gelijkaardigs moeten zien. Ga het bevel `switch to sandbox accelerate` in en klik **verzenden** knoop.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab10.png)

Dan moet je dit zien. Om de gegevensmening te veranderen, ga het volgende bevel in en klik **verzend** knoop.

```javascript
list dataviews
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab11.png)

Dan zou je iets gelijkaardigs moeten zien. Ga het bevel `switch dataview to Accelerate 2026 B2C` in en klik **verzenden** knoop.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab12.png)

Dan moet je dit zien. De context is nu op de juiste wijze ingesteld, zodat u nu specifieke aanwijzingen kunt verzenden.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab13.png)

## 1.1.4.5 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 7 months.
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab18.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab19.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory = Fiber over the last 7 months broken down by week
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab20.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab21.png)

## 1.1.4.6 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat een voorkeur voor een specifieke genre (bijvoorbeeld, SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Eerst moet u erachter komen welk veld wordt gebruikt om de voorkeur voor genre op te slaan.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which field is used to store the preferred genre
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab22.png)

Vervolgens ziet u dit. Het veld dat voor genre wordt gebruikt, is **_experiencePlatform.individualCharacteristics.preferences.preferredGenre** .

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab23.png)

Met deze informatie kunt u beginnen met het uitboren in de aankoopgegevens.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 7 months
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab24.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab25.png)

## 1.1.4.7 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab28.png)

Daarna moet u een lijst met reizen zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab29.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab31.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab33.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab35.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab36.png)

## 1.1.4.8 De reisprestaties valideren via een falloutanalyse

**Intentie**

U wilt de gevolgen van de reisprestaties begrijpen om te weten of zijn er om het even welke knopen of omstandigheden binnen de reis die een groot percentage van profielen ervaren die worden gelaten vallen. Dit is nuttig om te begrijpen of er extra aanpassingen nodig zijn in de reis.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab37.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/geminilab38.png)

Je hebt dit lab voltooid.

Ga terug naar [&#x200B; Agent Orchestrator &#x200B;](./agentorchestrator.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

---
title: Aan de slag met Agent Orchestrator
description: Aan de slag met Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: dee5b0855eeeb455bf22f511d11cd13f7e904889
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Agent Orchestrator

## 1.1.1.1 Context instellen in Agent Orchestrator

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao1.png)

Klik het **context** venster.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao2.png)

Stel de context in op:

- **Documentatie Source**: **Customer Journey Analytics**
- **Sandbox**: **versnelt**
- **Dataview**: **versnelt 2026 B2C**

Klik **Vastgestelde context**.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao3.png)

## 1.1.1.2 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao4.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/ao5.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![&#x200B; Agent Orchestrator &#x200B;](./images/ao6.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

**Actie**: Noteer de de groeicurve en regionale pieken.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao7.png)

## 1.1.1.3 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat de voorkeur van de inhoud (b.v., SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao8.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/ao9.png)

## 1.1.1.4 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao12.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/ao13.png)

Maak een lijst actief of verleden reizen met het overseinen van de Vezel.

Actie: Kortstondige snelritten voor klonen.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao14.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/ao15.png)

## 1.1.1.5 Controleer het zaad

**Intentie**:

Begrijp de zaaddefinitie van de &quot;CitiSignal - Fiber Max Launch Promotion&quot;-reis - welke kenmerken reden voor het kiezen van doelen (bijvoorbeeld &quot;SciFi Genre Preference&quot;, &quot;4+ devices&quot;, &quot;stream ≥ 300 GB/maand&quot;).

Ga de volgende **Herinnering** in en typ dan in **+CitiSignal fib** om autocomplete toe te laten. Selecteer de reis **CitiSignal - de Max Bevordering van de Lancering van de Vezel**.

```javascript
What was the initial audience in the journey named 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao16.png)

Dan moet je dit zien. Klik **verzenden** knoop.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao17.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao18.png)

## 1.1.1.6 De reisprestaties valideren via een falloutanalyse

**Intentie**

Een stapsgewijze funnel maken in Customer Journey Analytics

Geleverd → Geopend → Geklikt → Aangeland → Productweergave → Toevoegen aan winkelwagentje → Afhandeling voltooid

Inclusief aan vezels gerelateerde SKU-weergaven als vertakking.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao19.png)

## 1.1.1.7 Een nieuw publiek maken

**Intentie**

Op basis van de bovenstaande bevindingen is er een correlatie tussen klanten die veel gegevens gebruiken en die een genre van sci-fi of fantasie bij voorkeur hebben. U gaat deze kenmerken nu combineren in een publiek.

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

>[!NOTE]
>
>Gelieve te verifiëren dat de context van de medewerker aan zandbak **richt versnelt** en gegevensmening **versnelt 2026 B2C**

```javascript
Create an audience that combines people with an average download per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao32.png)

Controleer het plan. Ga `yes` in en klik **verzenden**.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao33.png)

Herzie de uitdrukking van de segmentvraag. Ga `yes` in en klik **verzenden** knoop.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao34.png)

Herzie de raming van de segmentgrootte. Ga `yes` in en klik **verzenden** knoop.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao35.png)

Klik **Overzicht**.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao36.png)

Herzie de segmentdefinitie. Klik **creëren**.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao37.png)

Uw publiek is nu gemaakt.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao38.png)

>[!NOTE]
>
>Wanneer het creëren van een nieuw publiek, zal het 24 uren vergen alvorens het publiek aan de medewerker voor verder gebruik beschikbaar is.

## 1.1.1.8 Bestaande doelgroepen zoeken die zijn uitgelijnd op hoog gebruik en controleren of ze in gebruik zijn

**Intentie**:

Zoek een publiek met de naam &quot;zware downloaders&quot;, gedefinieerd door drempels voor maandelijks gegevensgebruik.

>[!NOTE]
>
>In de vorige stap hebt u een nieuw publiek gemaakt. Vergeet niet dat het 24 uur zal duren voordat het publiek beschikbaar is voor de assistent voor verder gebruik. U moet nu een ander, reeds bestaand publiek gebruiken.

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

>[!NOTE]
>
>Gelieve te verifiëren dat de context van de medewerker aan zandbak **richt versnelt** en gegevensmening **versnelt 2026 B2C**

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao30.png)

Dan moet je dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao31.png)

Er zijn al een aantal bestaande doelgroepen voor &quot;zware downloaders&quot;. Laten we eens kijken of ze al in gebruik zijn.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of the above are used in a journey? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao50.png)

Dan zou je iets gelijkaardigs moeten zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao51.png)

Nu moet u controleren of die reis actief is. Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of the above are used in a journey? 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/ao52.png)

Dan zou je iets gelijkaardigs moeten zien. Die reis loopt op dit moment niet.

![&#x200B; Agent Orchestrator &#x200B;](./images/ao53.png)

Voor de aanstaande lancering van Fiber Max, zou u nu een nieuwe reis moeten creëren.

## 1.1.1.9 Nieuwe reis maken voor maximale start van Fibre

**Intentie**:

Een nieuwe reis maken voor het samengestelde publiek:

Zware downloaders ∩ voorkeur SciFi (kbaa_5207bf publiekssleutel).

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

>[!NOTE]
>
>Gelieve te verifiëren dat de context van de medewerker aan zandbak **richt versnelt** en gegevensmening **versnelt 2026 B2C**

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj1.png)

Dan moet je dit zien. Voer `yes` in en klik op Genereren.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj2.png)

Dan moet je dit zien. Voer `yes` in en klik op Genereren.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj3.png)

Dan moet je dit zien. Voer `The first one` in en klik op Genereren.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj4.png)

Dan moet je dit zien. Voer `yes` in en klik op Genereren.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj5.png)

Bekijk het antwoord. Voer `yes` in en klik op Genereren.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj6.png)

Klik **Overzicht**.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj7.png)

Werk de reisnaam bij met uw LDAP om deze uniek te maken. Klik **sparen**.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj8.png)

Uw reis is nu gecreeerd in ontwerp wijze.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj9.png)

## 1.1.1.10 Beheer van geschillen op reis

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

>[!NOTE]
>
>Gelieve te verifiëren dat de context van de medewerker aan de documentatiebron **Journey Optimizer** richt, versnelt zandbak **&#x200B;**&#x200B;en gegevensmening **versnelt 2026 B2C**

```javascript
How can I manage journey conflicts?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj80.png)

Controleer de gegevens.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj81.png)

De rol neer en selecteert de **Bronnen** om te vinden dat de informatie uit Experience League wordt voortgebracht.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj82.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
List any conflicts for "CitiSignal - Fiber Max Launch Promotion" journey
```

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj70.png)

Controleer de gegevens van het reisconflict.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj71.png)

Schuif omlaag om meer details over het transportconflict te vinden.

![&#x200B; Agent Orchestrator &#x200B;](./images/aocj72.png)

## 1.1.1.11 Experimenten

Ga naar [&#x200B; https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat &#x200B;](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

>[!NOTE]
>
>Gelieve te verifiëren dat de context van de medewerker aan zandbak **richt versnelt** en gegevensmening **versnelt 2026 B2C**

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/aoea0.png)

U zou dan dit moeten zien:

![&#x200B; Agent Orchestrator &#x200B;](./images/aoea1.png)

Klik de suggestie om de omzettingspercentages van elke behandeling te vergelijken en dan te klikken **verzendt**.

![&#x200B; Agent Orchestrator &#x200B;](./images/aoea2.png)

Vervolgens ziet u een gedetailleerde vergelijking zoals deze:

![&#x200B; Agent Orchestrator &#x200B;](./images/aoea4.png)

Ga terug naar [&#x200B; Agent Orchestrator &#x200B;](./agentorchestrator.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
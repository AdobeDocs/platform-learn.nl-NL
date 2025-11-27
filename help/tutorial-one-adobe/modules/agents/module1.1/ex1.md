---
title: Aan de slag met Agent Orchestrator
description: Aan de slag met Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: bb31fe8a36f1c9ee9d212500e2e58e01be1129b8
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Agent Orchestrator

## 1.1.1.1 Context instellen in Agent Orchestrator

Ga naar [ https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat ](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Dan moet je dit zien. Zorg ervoor u in de org **Internationale Experience Platform** bent.

![ Agent Orchestrator ](./images/ao1.png)

Klik het **context** venster.

![ Agent Orchestrator ](./images/ao2.png)

Stel de context in op:

- **Documentatie Source**: **Journey Optimizer**

Met de instelling Documentation Source kunt u de voorkeur geven aan documenten met de league (Engelstalig) waarin u kunt controleren op vragen die betrekking hebben op productkennis/Experience League.

- **Sandbox**: **Prod - versnelt (VA7)**

Met de instelling Sandbox kunt u bepalen naar welke sandbox AI-assistent moet worden gekeken wanneer vragen worden gesteld.

- **Dataview**: **versnelt 2026 B2C**

Met de instelling Gegevensweergave kunt u bepalen naar welke AI-assistent voor gegevensweergave moet worden gekeken wanneer u vragen stelt.

Klik **Vastgestelde context**.

![ Agent Orchestrator ](./images/ao3.png)

## 1.1.1.2 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**

Krijg een impuls op topniveau op vraag-mobiel, Landline, Internet, TV, vezel-specifiek voor de recentste 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de uitrol van New York.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![ Agent Orchestrator ](./images/ao4.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/ao5.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![ Agent Orchestrator ](./images/ao6.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

![ Agent Orchestrator ](./images/ao7.png)

## 1.1.1.3 Orders correleren met voorkeuren voor inhoud

**Intentie**

Test de hypothese dat een voorkeur voor een specifieke genre (bijvoorbeeld, SciFi, Sport, Drama) breedbandverbeteringsgedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

Eerst moet u erachter komen welk veld wordt gebruikt om de voorkeur voor genre op te slaan.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which field is used to store the preferred genre?
```

![ Agent Orchestrator ](./images/ao7a.png)

Vervolgens ziet u dit. Het veld dat voor genre wordt gebruikt, is **_experiencePlatform.individualCharacteristics.preferences.preferredGenre** .

![ Agent Orchestrator ](./images/ao7b.png)

Met deze informatie kunt u beginnen met het uitboren in de aankoopgegevens.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![ Agent Orchestrator ](./images/ao8.png)

Dan moet je dit zien. Klik het pictogram op het **Volledige** blok van de Redding volledig {om te begrijpen wat in Agent Orchestrator achter de scènes gebeurt.

![ Agent Orchestrator ](./images/ao9.png)

Dan zou je een vergelijkbare verklaring moeten zien.

![ Agent Orchestrator ](./images/ao10.png)

## 1.1.1.4 Bestaande vezelreizen identificeren

**Intentie**

Ontdek welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in de titel omvatten - bv., &quot;vezel verbetering NYC - Sept&quot;, &quot;de Proefversie van de Vezel - de Bundel van de Streaming&quot;.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
What journeys exist? 
```

![ Agent Orchestrator ](./images/ao12.png)

Dan moet je dit zien. Klik **tonen meer**.

![ Agent Orchestrator ](./images/ao13.png)

Daarna moet u een grotere lijst zien van actieve of vroegere reizen. Klik het **download** pictogram om een lijst van deze reizen te downloaden.

![ Agent Orchestrator ](./images/ao13a.png)

Hiermee wordt een CSV-bestand voor u gegenereerd dat alle uitvoer van de AI-assistent bevat.

![ Agent Orchestrator ](./images/ao13b.png)

Klik om het rechterdeelvenster te sluiten. Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![ Agent Orchestrator ](./images/ao14.png)

Dan moet je dit zien. Klik de verbinding op één van de reizen en selecteer **Details van de Reis**.

![ Agent Orchestrator ](./images/ao15.png)

Er wordt een nieuw venster geopend en u wordt meteen doorgestuurd naar het overzicht met reisgegevens.

![ Agent Orchestrator ](./images/ao15a.png)

## 1.1.1.5 Controleren welk publiek wordt gebruikt

**Intentie**:

Begrijp de zaaddefinitie van de &quot;CitiSignal - Fiber Max Launch Promotion&quot;-reis - welke kenmerken reden voor het kiezen van doelen (bijvoorbeeld &quot;SciFi Genre Preference&quot;, &quot;4+ devices&quot;, &quot;stream ≥ 300 GB/maand&quot;).

Ga de volgende **Herinnering** in:

```javascript
What was the initial audience in the journey named 
```

Typ vervolgens handmatig in `+CitiSignal fib` om automatisch aanvullen in te schakelen. Selecteer de reis **CitiSignal - de Max Bevordering van de Lancering van de Vezel**.

![ Agent Orchestrator ](./images/ao16.png)

Dan moet je dit zien. Klik **verzenden** knoop.

![ Agent Orchestrator ](./images/ao17.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/ao18.png)

## 1.1.1.6 De reisprestaties valideren via een falloutanalyse

**Intentie**

U wilt de gevolgen van de reisprestaties begrijpen om te weten of zijn er om het even welke knopen of omstandigheden binnen de reis die een groot percentage van profielen ervaren die worden gelaten vallen. Dit is nuttig om te begrijpen of er extra aanpassingen nodig zijn in de reis.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![ Agent Orchestrator ](./images/ao19.png)

Dan moet je dit zien.

![ Agent Orchestrator ](./images/ao20.png)

Schuif een beetje omlaag. U kunt de lijst nu herzien door elke knoop en zijn respectieve ingaat aantallen, valutanummers, en valutarief te inspecteren.

In de AI Assistant vindt u opmerkingen en aanbevelingen.

Klik de zin **hier is hoe ik de resultaten** kreeg.

![ Agent Orchestrator ](./images/ao21.png)

U kunt dan de stappen zien die door AI Medewerker worden gevolgd om aan de resultaten te krijgen.

![ Agent Orchestrator ](./images/ao22.png)

## 1.1.1.7 Een nieuw publiek maken

**Intentie**

Op basis van de bovenstaande bevindingen en het onderzoek is er een correlatie tussen klanten die veel gegevens gebruiken en die een genre van sci-fi of fantasie bij voorkeur hebben. U gaat deze kenmerken nu combineren in een publiek.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create an audience that combines people with an average download per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![ Agent Orchestrator ](./images/ao32.png)

Controleer het plan. Ga `yes` in en klik **verzenden**.

>[!NOTE]
>
>Dit plan wordt geproduceerd gebaseerd op een verwijzingsgids in het systeem. De klanten zullen uiteindelijk plannen kunnen aanpassen en hun eigen plannen toevoegen, maar voor nu zijn zij statisch.

![ Agent Orchestrator ](./images/ao33.png)

Herzie de uitdrukking van de segmentvraag. Ga `yes` in en klik **verzenden** knoop.

![ Agent Orchestrator ](./images/ao34.png)

Herzie de raming van de segmentgrootte. Ga `yes` in en klik **verzenden** knoop.

![ Agent Orchestrator ](./images/ao35.png)

Klik **Overzicht**.

![ Agent Orchestrator ](./images/ao36.png)

Herzie de segmentdefinitie. Klik **creëren**.

![ Agent Orchestrator ](./images/ao37.png)

Uw publiek is nu gemaakt.

![ Agent Orchestrator ](./images/ao38.png)

>[!NOTE]
>
>Wanneer u een nieuw publiek maakt, duurt het 24 uur voordat het publiek beschikbaar is voor AI Assistant voor verder gebruik.

## 1.1.1.8 Bestaande doelgroepen zoeken die zijn uitgelijnd op hoog gebruik en controleren of ze in gebruik zijn

**Intentie**:

Zoek een publiek met de naam &quot;zware downloaders&quot;, gedefinieerd door drempels voor maandelijks gegevensgebruik.

>[!NOTE]
>
>In de vorige stap hebt u een nieuw publiek gemaakt. Vergeet niet dat het 24 uur duurt voordat het publiek beschikbaar is voor AI Assistant voor verder gebruik. U moet nu een ander, reeds bestaand publiek gebruiken.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![ Agent Orchestrator ](./images/ao30.png)

Dan moet je dit zien. U wilt nu al uw publiek zien en hoeveel er de afgelopen dagen veranderd is.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
List how much these audiences changed over the last few days.
```

![ Agent Orchestrator ](./images/ao31.png)

Dan moet je dit zien. Klik **tonen meer**.

![ Agent Orchestrator ](./images/ao31a.png)

Dan moet je dit zien. Klik om het rechterdeelvenster te sluiten.

![ Agent Orchestrator ](./images/ao31b.png)

Schuif een beetje omlaag om de stappen te bekijken die door AI Assistant zijn uitgevoerd.

![ Agent Orchestrator ](./images/ao31c.png)

Er zijn al een aantal bestaande doelgroepen voor &quot;zware downloaders&quot;. Laten we eens kijken of ze al in gebruik zijn.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Which of the above are used in a journey? 
```

![ Agent Orchestrator ](./images/ao50.png)

Dan zou je iets gelijkaardigs moeten zien.

![ Agent Orchestrator ](./images/ao51.png)

Nu moet u controleren of die reis actief is. Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Are these journeys active? 
```

![ Agent Orchestrator ](./images/ao52.png)

Dan zou je iets gelijkaardigs moeten zien. Geen van deze reizen loopt momenteel.

![ Agent Orchestrator ](./images/ao53.png)

Voor de aanstaande lancering van Fiber Max, zou u nu een nieuwe reis moeten creëren.

## 1.1.1.9 Nieuwe reis maken voor maximale start van Fibre

**Intentie**:

Een nieuwe reis maken voor het samengestelde publiek:

Zware downloaders ∩ voorkeur SciFi.

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![ Agent Orchestrator ](./images/aocj1.png)

Dan moet je dit zien. Voer `yes` in en klik op Genereren.

![ Agent Orchestrator ](./images/aocj2.png)

Dan moet je dit zien. Voer `yes` in en klik op Genereren.

![ Agent Orchestrator ](./images/aocj3.png)

Dan moet je dit zien. Voer `The first one` in en klik op Verzenden.

![ Agent Orchestrator ](./images/aocj4.png)

Dan moet je dit zien. Voer `yes` in en klik op Verzenden.

![ Agent Orchestrator ](./images/aocj5.png)

Bekijk het antwoord. Voer `yes` in en klik op Verzenden.

![ Agent Orchestrator ](./images/aocj6.png)

Klik **Overzicht**.

![ Agent Orchestrator ](./images/aocj7.png)

Werk de reisnaam bij met uw LDAP om deze uniek te maken. Klik **sparen**.

![ Agent Orchestrator ](./images/aocj8.png)

Uw reis is nu gecreeerd in ontwerp wijze.

![ Agent Orchestrator ](./images/aocj9.png)

## 1.1.1.10 Beheer van geschillen op reis

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
How can I manage journey conflicts?
```

![ Agent Orchestrator ](./images/aocj80.png)

Controleer de gegevens.

![ Agent Orchestrator ](./images/aocj81.png)

De rol neer en selecteert de **Bronnen** om te vinden dat de informatie uit Experience League wordt voortgebracht.

![ Agent Orchestrator ](./images/aocj82.png)

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
List any conflicts for the journey +CitiSignal Fiber Max
```

Dan selecteer manueel de reis **CitiSignal - de Max Bevordering van de Lancering van de Vezel** van de lijst.

![ Agent Orchestrator ](./images/aocj70.png)

Dan moet je dit zien. Klik **verzenden**.

![ Agent Orchestrator ](./images/aocj70a.png)

Controleer de gegevens van het reisconflict.

![ Agent Orchestrator ](./images/aocj71.png)

Schuif omlaag om meer details over het transportconflict te vinden.

![ Agent Orchestrator ](./images/aocj72.png)

## 1.1.1.11 Experimenten

Ga de volgende **Herinnering** in en klik **verzenden** knoop.

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![ Agent Orchestrator ](./images/aoea0.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/aoea1.png)

Blader omlaag en klik op een van de suggesties. Klik **verzenden**.

>[!NOTE]
>
>De suggesties zijn dynamisch zodat zou u moeten verwachten om verschillende suggesties te zien telkens als een reactie wordt geproduceerd. Uw suggesties zullen waarschijnlijk anders zijn dan de suggesties die in deze schermafbeelding worden getoond.

![ Agent Orchestrator ](./images/aoea2.png)

Dan zou u een gedetailleerd antwoord moeten zien over de suggestie die is gekozen.

![ Agent Orchestrator ](./images/aoea4.png)

Je hebt dit lab voltooid.

Ga terug naar [ Agent Orchestrator ](./agentorchestrator.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
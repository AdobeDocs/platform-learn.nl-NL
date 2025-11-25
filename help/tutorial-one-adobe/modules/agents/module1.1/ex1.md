---
title: Aan de slag met Agent Orchestrator
description: Aan de slag met Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: 9011c4093b5fd6612426baf7003cd7b99523b6e8
workflow-type: tm+mt
source-wordcount: '1296'
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

- **Documentatie Source**: **Customer Journey Analytics**
- **Sandbox**: **versnelt**
- **Dataview**: **versnelt 2026 B2C**

Klik **Vastgestelde context**.

![ Agent Orchestrator ](./images/ao3.png)

>[!NOTE]
>
>In dit laboratorium, zult u context schakelen wanneer het bewegen tussen analyse en orchestratie.

## 1.1.1.2 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Intentie**: Krijg een impuls op hoogste niveau op vraag-mobiel, Landline, Internet, TV, specifiek voor de meest recente 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de NY-rollout.

**het Dinken**:

&quot;Krijgt Vezel postNY? Ziet u kannibalisatie van het internet van Copper/DSL? Wat is de mix verschuiven ten opzichte van tv-bundels?&quot;

&quot;Dit zal me helpen het adresseerbare publiek voor Wenen te meten en realistische doelen te stellen.&quot;

**de Handelbare lezingen de teller verwacht**:

Een gestapelde staaf/lijngrafiek van Aankopen door mainCategorie (dagelijkse/wekelijkse korrel).

Percentage van de aankopen per categorie versus voorafgaande periode.

Opvallende pieken correleren met promotiedata.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![ Agent Orchestrator ](./images/ao4.png)

U zou dan dit moeten zien:

>[!NOTE]
>
>Houd de aandacht op achterblijvende attributie-De orden van de vezel kunnen onder &quot;Internet&quot;in sommige erfenisschema&#39;s worden gevangen. Zo ja, de taxonomie vóór de beslissingen met elkaar in overeenstemming brengen.

![ Agent Orchestrator ](./images/ao5.png)

Ga de volgende **Herinnering** in en klik **produceren** knoop.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![ Agent Orchestrator ](./images/ao6.png)

Je zou dan dit moeten zien, die naar vezelspecifieke tendensen daalt.

**Actie**: Noteer de de groeicurve en regionale pieken.

![ Agent Orchestrator ](./images/ao7.png)

## 1.1.1.3 Orders correleren met voorkeuren voor inhoud

**Intentie**: Test de hypothese dat de inhoudsvoorkeur (b.v., SciFi, Sport, Drama) breedbandverbetering gedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

**het Dinken**

&quot;SciFi-ventilatoren kijken vaak naar 4 kB en streamen vanaf meerdere apparaten; dit is waarschijnlijk een goede waarde voor lage latentie.&quot;

&quot;Bepaal of SciFi (en misschien Sport) verband houdt met recente bestellingen.&quot;

**Verwachte output**

Een draaipunt van bestellingen (toegepast YTD-filter) uitgesplitst naar genre bij voorkeur, beperkt tot twee maanden.

Rankgenres volgens de orderomrekeningskoers en AOV (gemiddelde orderwaarde).

Besluit: als SciFi een sterk signaal geeft, wordt dit een primaire creatieve pijler voor de Fiber Max-lancering van Wenen (bv. &quot;nooit meer bufferen&quot; berichten, premiebundels).

**Intentie**

Conversie via genre analyseren (bv. Sci-Fi, Sport).

**Doel** bevestigt als de ventilatoren Sci-Fi over-index voor de verbeteringen van de Vezel.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![ Agent Orchestrator ](./images/ao8.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/ao9.png)

## 1.1.1.4 Bestaande vezelreizen identificeren

Klik het **context** venster.

![ Agent Orchestrator ](./images/ao10.png)

Stel de context in op:

- **Documentatie Source**: **Adobe Journey Optimizer**
- **Sandbox**: **versnelt**
- **Dataview**: **versnelt 2026 B2C**

![ Agent Orchestrator ](./images/ao11.png)

**Intentie** ontdekt welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in titel-bv, &quot;de Verbetering van de Vezel NYC - Zin&quot;omvatten, &quot;de Proefversie van de Vezel - het Streamen Bundel&quot;.

**het Dinken**

&quot;Welke van deze reizen hebben goed gepresteerd, en wat waren hun triggers?&quot;

&quot;Kan ik de winnende orkestlogica opnieuw gebruiken voor Wenen?&quot;

**Verwachte output**

Lijst van reizen met status (actief, gepauzeerd, beëindigd), datumbereiken, doelsegmenten, KPI&#39;s (open snelheid, CTR, conversie).

Volgende stap: Korte lijst met een of twee geslaagde vezelritten voor klonen/aanpassen.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
What journeys exist? 
```

![ Agent Orchestrator ](./images/ao12.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/ao13.png)

Maak een lijst actief of verleden reizen met het overseinen van de Vezel.

Actie: Kortstondige snelritten voor klonen.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![ Agent Orchestrator ](./images/ao14.png)

U zou dan dit moeten zien:

![ Agent Orchestrator ](./images/ao15.png)

## 1.1.1.5 Controleer het zaad

**Intentie**:

Begrijp de zaaddefinitie van de &quot;CitiSignal - Fiber Max Launch Promotion&quot;-reis - welke kenmerken reden voor het kiezen van doelen (bijvoorbeeld &quot;SciFi Genre Preference&quot;, &quot;4+ devices&quot;, &quot;stream ≥ 300 GB/maand&quot;).

**het Dinken**

&quot;Ik wil beproefde creatieve SciFi met de prestatiesoverseinen van Fiber Max combineren.&quot;

&quot;Als het publiek overlapt met zware downloaders, kunnen we de neiging stapelen.&quot;

**Verwachte output**

Criteria van het publiek (inclusie/uitsluiting), publieksgrootte, regiofilters, recentie, frequentiedrempels.

>[!NOTE]
>
>Context wijzigen in CJA

Vanaf dit punt schakelt de markeerteken over naar de analysemodus om een juiste rapportage te garanderen.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
What was the initial audience in the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![ Agent Orchestrator ](./images/ao16.png)
Bekijk de publiekscriteria (streaminggewoonten, aantal apparaten).

**Doel**: Begrijp eigenschappen voor hoge bandbreedtebehoeften.

## 1.1.1.6 De reisprestaties valideren via een falloutanalyse

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

>[!NOTE]
>
>Context wijzigen in CJA)

**Intentie**:

Een stapsgewijze funnel maken in Customer Journey Analytics

Geleverd → Geopend → Geklikt → Aangeland → Productweergave → Toevoegen aan winkelwagentje → Afhandeling voltooid

Inclusief aan vezels gerelateerde SKU-weergaven als vertakking.

**het Dinken**:

&quot;Waar verliezen wij mensen—e-mail open, het laden van de landingspagina, PDPs, de wrijving van de checkout?&quot;

&quot;Stuiteren SciFi-gebruikers meer of minder dan gemiddeld op Fibre PDP?&quot;

**Verwachte output**:

Een uitvalvisualisatie met uitvalpercentages bij elke stap.

Segmentbedekkingen (SciFi versus Sport vs. Andere).

Apparaat/browser defect voor technische wrijving.

**Besluiten**:

Als de afrekenactie hoog is, moet u coördineren met product/UX om de betalingsstroom te herstellen.

Als de PDP uitgang hoog is, eisen de herwerkbaarheid helderheid (snelheden, installatietijden, bundelwaarde).

>[!NOTE]
>
>Context wijzigen in JO

Nu beweegt de markator naar Adobe Journey Optimizer voor orkest en publiek.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey 
```

Funnel-visualisatie bouwen: geleverd → geopend → geklikt → Afhandeling → Bestelling.

**Actie**: Identificeer drop-off punten en optimaliseer overseinen of UX.

## 1.1.1.7 Bestaande doelgroepen zoeken die zijn uitgelijnd op hoog gebruik

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

>[!NOTE]
>
>Context wijzigen in Adobe Journey Optimizer

**Intentie**:

Zoek een JO-publiek met de naam &quot;zware downloaders&quot;. Dit wordt mogelijk gedefinieerd door de maandelijkse drempels voor gegevensgebruik, streaminguren of gelijktijdige uitvoering van apparaten.

**het Dinken**:

&quot;Als er een publiek als Zware downloaders bestaat, is dit ideaal voor maximale positionering van de vezel: snelheid, betrouwbaarheid, onbeperkte lagen.&quot;

**Verwachte output**:

Metagegevens van het publiek: definitiecriteria, grootte, laatste verfrissing, governance markeringen, gebiedsbeschikbaarheid.

Zoek een publiek met veel gegevensgebruik.

**Doel**: Combineer met Sci-Fi voorkeur voor Max het richten van Vezel.

## 1.1.1.8 Bepalen of dat publiek al in gebruik is

**Intentie**:

Koppeling publiek-naar-reis controleren: zorg dat we geen dubbele vlek maken of botsen met de huidige programma&#39;s.

**het Dinken**:

&quot;Als de Zware Downloaders reeds in een retentietraject is, hebben wij redelogica of frequentiegrenzen nodig om vermoeidheid te vermijden.&quot;

**Verwachte output**:

Toewijzingen: publiek → naam, status, contactbeleid, laatste verzending, prestaties.

**Besluit**:

Indien in gebruik, creeer uitsluitingen of gedeelde onderdrukking voor de lancering van Wenen.

Als het niet in gebruik is, groen licht voor een nieuwe reis.

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Which of the above are used in a journey? 
```

Zorg ervoor dat actieve campagnes elkaar niet overlappen.

**Actie**: Pas onderdrukking indien nodig toe.

## 1.1.1.9 Nieuwe reis maken voor maximale start van Fibre

**Intentie**:

Een nieuwe reis maken voor het samengestelde publiek:

Zware downloaders ∩ voorkeur SciFi (kbaa_5207bf publiekssleutel).

**het Dinken**:

&quot;Dit is de zoete plek voor Fiber Max: hoge neiging + creatieve relevantie.&quot;

&quot;We organiseren een multitouch-ervaring met Wenen.&quot;

**het ontwerp van de Reis (JO)**:

Invoercriteria:

Publiek: Zware downloaders - Sciencefiction_kbaa_5207bf

Geografie: Wenen metro (ZIP/postcode-lijst of geo-veelhoek)

Geschiktheid: Niet in actieve campagne &quot;Fiber Upgrade NYC - Sept&quot;; geen huidige abonnee van Fibre.

Trigger en timing:

T14 dagen voor Wenen starten (januari 2026): Voorbeeld-e-mail—&quot;Fiber Max komt.&quot;

Start week: primaire e-mail + in-app banner + betaalde mediasynchronisatie (via CDP-bestemming).

T+3 dagen: Gedrag splitsen—als er geen klik is, verplaatst SMS-code; als erop wordt geklikt maar niet is besteld, kunt u dit opnieuw afstemmen met een CTA voor beschikbaarheid van het installatieprogramma.

T+10 dagen: test - gratis installatie versus korting van 1 maand (A/B).

Personalization:

Dynamische kopie voor SciFi-lovers (latentie/4K streaminghaken).

De eisen van de snelheid/van de latentie die aan apparatenmengeling (gokkenconsoles, stroomsgewijze dozen) worden aangepast.

Aanbeveling voor de bundel: Fiber Max + premium TV scifi content pack.

Bestuur:

Frequentiedop: maximaal 3 touches per 10 dagen.

Onderdruk als huidige abonnee van de Vezel of als het kaartje voor installatie bestaat.

Voorkeuren voor de optie Respect.

Meetplan (CJA):

Track: levering, openen, klikken, PDP-weergave, start van afhandeling, voltooiing van bestelling.

KPI&#39;s: conversiesnelheid naar Fiber Max, uplift versus controle, tijdstoepassing.

Diagnostiek: valrapport per apparaat/genre-segment.

Vorm

Hoe dit allemaal samenpast (het mentale model van de markeerster)

Diagnose van de vraag (algemene categorieën → Vezel specifiek).

Inhoud aantonen tot conversiesignaal (orders per genre).

Mijn reis is geslaagd (zoek naar Fiberbenoemde reizen en het SciFi-promo-publiek).

Valideer wrijvingspunten (CJA fallout op reis SciFi).

Activeer tegen segmenten met hoge dichtheid (zware downloaders ∩ SciFi).

Ga de volgende **Herinnering** in en klik **produceren** knoop.

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

Ga terug naar [ Agent Orchestrator ](./agentorchestrator.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
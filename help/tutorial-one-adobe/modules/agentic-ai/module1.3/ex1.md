---
title: Aan de slag met Agent Orchestrator
description: Aan de slag met Agent Orchestrator
kt: 5342
doc-type: tutorial
source-git-commit: e90dee164dfe098c9fc56a04c481a733c0843858
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Agent Orchestrator

## 1.3.1 Context instellen in Agent Orchestrator

Navigeer naar de AI-assistent en zet deze in de weergave Groot.

Bevestig dat u in CJA-context werkt voor analytische taken.

>[!NOTE]
>
>Gebruik contextomschakeling bij het schakelen tussen analyse (CJA) en orkest (JO).

## 1.3.2 Begin met algemene aankooptrends om context te verankeren en in vezel te zoomen

**Herinnering**:

```javascript
Show me purchases by mainCategory over the last 2 month
```

**Intentie**: Krijg een impuls op hoogste niveau op vraag-mobiel, Landline, Internet, TV, specifiek voor de meest recente 60 dagen. Dit bepaalt basislijnen voor seizoensgebondenheid, bevorderingeffecten, en regionale variantie na de NY-rollout.

Dacht:

&quot;Krijgt Vezel postNY? Ziet u kannibalisatie van het internet van Copper/DSL? Wat is de mix verschuiven ten opzichte van tv-bundels?&quot;

&quot;Dit zal me helpen het adresseerbare publiek voor Wenen te meten en realistische doelen te stellen.&quot;

De markeertekens worden in actie gebracht en worden verwacht:

Een gestapelde staaf/lijngrafiek van Aankopen door mainCategorie (dagelijkse/wekelijkse korrel).

Percentage van de aankopen per categorie versus voorafgaande periode.

Opvallende pieken correleren met promotiedata.

>[!NOTE]
>
>Houd de aandacht op achterblijvende attributie-De orden van de vezel kunnen onder &quot;Internet&quot;in sommige erfenisschema&#39;s worden gevangen. Zo ja, de taxonomie vóór de beslissingen met elkaar in overeenstemming brengen.

 

**Herinnering**:

```javascript
Show me purchases by mainCategory over the last 2 monthzoom into fiber performance
```

**Volgende Herinnering**

`Show me purchases by mainCategory = Fiber over the last 2 months`

Bouw neer in Vezel-specifieke tendensen.

**de groeicurve van de Actie van 0&rbrace; &lbrace;en regionale pieken.**

## 1.3.3 Orders correleren met voorkeuren voor inhoud

**Herinnering**:

```javascript
Show me ordersYTD by preferred genre for the last 2 months
```

**Intentie** test de hypothese dat de inhoudvoorkeur (b.v., SciFi, Sport, Drama) breedbandverbetering gedrag-vooral voor hoge bandbreedtebehoeften voorspelt.

**het Dinken**

&quot;SciFi-ventilatoren kijken vaak naar 4 kB en streamen vanaf meerdere apparaten; dit is waarschijnlijk een goede waarde voor lage latentie.&quot;

&quot;Bepaal of SciFi (en misschien Sport) verband houdt met recente bestellingen.&quot;

**Verwachte output**

Een draaipunt van bestellingen (toegepast YTD-filter) uitgesplitst naar genre bij voorkeur, beperkt tot twee maanden.

Rankgenres volgens de orderomrekeningskoers en AOV (gemiddelde orderwaarde).

Besluit: als SciFi een sterk signaal geeft, wordt dit een primaire creatieve pijler voor de Fiber Max-lancering van Wenen (bv. &quot;nooit meer bufferen&quot; berichten, premiebundels).

**Vragen**

`Show me ordersYTD by preferred genre for the last 2 months`

**Intentie**

Conversie via genre analyseren (bv. Sci-Fi, Sport).

**Doel** bevestigt als de ventilatoren Sci-Fi over-index voor de verbeteringen van de Vezel.

## 1.3.4 Bestaande vezelreizen identificeren

**Herinnering**:

```javascript
What journey was running and had Fiber in the name
```

**Intentie** ontdekt welke actieve of onlangs voltooide reizen &quot;Vezel&quot;in titel-bv, &quot;de Verbetering van de Vezel NYC - Zin&quot;omvatten, &quot;de Proefversie van de Vezel - het Streamen Bundel&quot;.

**het Dinken**

&quot;Welke van deze reizen hebben goed gepresteerd, en wat waren hun triggers?&quot;

&quot;Kan ik de winnende orkestlogica opnieuw gebruiken voor Wenen?&quot;

**Verwachte output**

Lijst van reizen met status (actief, gepauzeerd, beëindigd), datumbereiken, doelsegmenten, KPI&#39;s (open snelheid, CTR, conversie).

Volgende stap: Korte lijst met een of twee geslaagde vezelritten voor klonen/aanpassen.

**Vragen**

`What journey was running and had Fiber in the name?`

Maak een lijst actief of verleden reizen met het overseinen van de Vezel.

Actie: Kortstondige snelritten voor klonen.

## 1.3.5 Controleer het publiek van de zaadjes voor een relevante historische protestactie

**Herinnering**:

```javascript
What was the initial audience in that SCi-Fi promo 2024 - jl journey
```

**Intentie** begrijpt de zaaddefinitie van &quot;SciFi Promo 2024 - jl&quot;reis-welke eigenschappen reden het richten (b.v., &quot;SciFi Genre Voorkeur,&quot;4+ apparaten,&quot;stroom ≥ 300GB/maand&quot;).

**het Dinken**

&quot;Ik wil beproefde creatieve SciFi met de prestatiesoverseinen van Fiber Max combineren.&quot;

&quot;Als het publiek overlapt met zware downloaders, kunnen we de neiging stapelen.&quot;

**Verwachte output**

Criteria van het publiek (inclusie/uitsluiting), publieksgrootte, regiofilters, recentie, frequentiedrempels.

>[!NOTE]
>
>Context wijzigen in CJA

Vanaf dit punt schakelt de markeerteken over naar de analysemodus om een juiste rapportage te garanderen.

**Herinnering**:

```javascript
What was the initial audience in that SCi-Fi promo 2024 - jl journey?
```

Bekijk de publiekscriteria (streaminggewoonten, aantal apparaten).

Doel: Begrijp de kenmerken voor hoge bandbreedtebehoeften.

## 1.3.6 De reisprestaties valideren via een valutanalyse

**Herinnering**:

```javascript
Create a fall-out report on the "Sci-Fi Promo 2024 - jl" journey
```

>[!NOTE]
>
>Context wijzigen in CJA)

**Intentie** bouwt een stapsgewijze funnel in Customer Journey Analytics

Geleverd → Geopend → Geklikt → Aangeland → Productweergave → Toevoegen aan winkelwagentje → Afhandeling voltooid

Inclusief aan vezels gerelateerde SKU-weergaven als vertakking.

Dacht:

&quot;Waar verliezen wij mensen—e-mail open, het laden van de landingspagina, PDPs, de wrijving van de checkout?&quot;

&quot;Stuiteren SciFi-gebruikers meer of minder dan gemiddeld op Fibre PDP?&quot;

Verwachte uitvoer:

Een uitvalvisualisatie met uitvalpercentages bij elke stap.

Segmentbedekkingen (SciFi versus Sport vs. Andere).

Apparaat/browser defect voor technische wrijving.

Besluiten:

Als de afrekenactie hoog is, moet u coördineren met product/UX om de betalingsstroom te herstellen.

Als de PDP uitgang hoog is, eisen de herwerkbaarheid helderheid (snelheden, installatietijden, bundelwaarde).

>[!NOTE]
>
>Context wijzigen in JO

Nu beweegt de markator naar Adobe Journey Optimizer voor orkest en publiek.

**Herinnering**:

```javascript
Create a fall-out report on the "Sci-Fi Promo 2024 - jl" journey 
```

Funnel-visualisatie bouwen: geleverd → geopend → geklikt → Afhandeling → Bestelling.

Actie: Identificeer drop-down punten en optimaliseer overseinen of UX.


## 1.3.7 Bestaande doelgroepen zoeken die zijn uitgelijnd op hoog gebruik

**Herinnering**:

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

>[!NOTE]
>
>Context wijzigen in Adobe Journey Optimizer

Intentie: zoek een JO-publiek met de naam &quot;zware downloaders&quot;. Dit wordt waarschijnlijk gedefinieerd door de maandelijkse drempels voor gegevensgebruik, de streaminguren of de gelijktijdige aansluiting van apparaten.

Dacht:

&quot;Als er een publiek als Zware downloaders bestaat, is dit ideaal voor maximale positionering van de vezel: snelheid, betrouwbaarheid, onbeperkte lagen.&quot;

Verwachte uitvoer:

Metagegevens van het publiek: definitiecriteria, grootte, laatste verfrissing, governance markeringen, gebiedsbeschikbaarheid.

**Herinnering**:

```javascript
Is there an audience that has " heavy downloaders" in the title 
```

Zoek een publiek met veel gegevensgebruik.

Doel: Combineer met de voorkeur van Sci-Fi voor het Max richten van de Vezel.

## 1.3.8 Bepalen of dit publiek al in gebruik is

**Herinnering**:

```javascript
Which of the above are used in a journey? 
```

Intentie: controleer de koppeling tussen publiek en reis. Controleer of u geen dubbele vlek hebt of niet botst met de huidige programma&#39;s.

Dacht:

&quot;Als de Zware Downloaders reeds in een retentietraject is, hebben wij redelogica of frequentiegrenzen nodig om vermoeidheid te vermijden.&quot;

Verwachte uitvoer:

Toewijzingen: publiek → naam, status, contactbeleid, laatste verzending, prestaties.

Besluit:

Indien in gebruik, creeer uitsluitingen of gedeelde onderdrukking voor de lancering van Wenen.

Als het niet in gebruik is, groen licht voor een nieuwe reis.

Vragen:

welke van de bovenstaande gegevens worden gebruikt op een reis ?

Zorg ervoor dat actieve campagnes elkaar niet overlappen.

Handeling: onderdrukking toepassen indien nodig.

## 1.3.9 Nieuwe reis maken voor maximale start van Fibre

**Herinnering**:

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

Intent: Bouw een nieuwe JO-reis voor het samengestelde publiek:

Zware downloaders ∩ voorkeur SciFi (kbaa_5207bf publiekssleutel).

Dacht:

&quot;Dit is de zoete plek voor Fiber Max: hoge neiging + creatieve relevantie.&quot;

&quot;We organiseren een multitouch-ervaring met Wenen.&quot;

Reisontwerp (JO):

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

Inhoud conversiesignaal (orders per genre) aantonen.

Mijn reis is geslaagd (zoek naar Fiberbenoemde reizen en het SciFi-promo-publiek).

Valideer wrijvingspunten (CJA fallout op reis SciFi).

Activeer tegen segmenten met hoge dichtheid (zware downloaders ∩ SciFi).


Ga terug naar [&#x200B; Agent Orchestrator &#x200B;](./agentorchestrator.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
---
title: Customer Journey Analytics - Customer Journey Analytics 101
description: Customer Journey Analytics - Customer Journey Analytics 101
kt: 5342
doc-type: tutorial
exl-id: ea1469a4-cbfd-4633-8678-9467c2146a2a
source-git-commit: 1e3a8d585503eddad4c642a3b13d2b5f7ddc9943
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# 1.1.1 Customer Journey Analytics 101

## Doelstellingen

- De CJA-toepassingsservice begrijpen
- Leer hoe u CJA kunt plaatsen
- Begrijp de CJA-workflow: van gegevensverbinding tot inzichten

## 1.1.1.1 Wat is Customer Journey Analytics?

Customer Journey Analytics (CJA) biedt een toolkit aan de business intelligence- en data science-teams voor het naasten en analyseren van kanaalgegevens (online en offline). De mogelijkheden binnen CJA leveren context en helderheid aan de complexe multi-kanaals klantenreis. De verstrekte context leidt tot actioneel inzicht in het verwijderen van pijnpunten uit het proces van de klantenomzetting en het ontwerpen van en het leveren van uitzonderlijke ervaringen voor de momenten die het belangrijkst zijn.

CJA brengt Analysis Workspace bovenop Adobe Experience Platform. Adobe Experience Platform is het brein voor communicatie en orchestratie en met CJA kunnen merken nu al die gegevens contextualiseren en visualiseren, zodat Business en Insight teams er van kunnen leren door de volledige online naar offline reis van klanten te analyseren.

Bedrijfs en Insight teams kunnen met CJA spreken, vragen stellen en op de vlucht antwoorden krijgen met belemmering-en-daling, punt-en-klik en gebruikersvriendelijke UI van Analysis Workspace.

![ demo ](./images/cja-adv-analysis1.png)

## 1.1.1.2 Belangrijkste voordelen

De drie belangrijkste voordelen voor klanten zijn:

- De mogelijkheid om inzichten voor iedereen beschikbaar te maken (d.w.z., het democratiseren van de toegang tot gegevens)
- De mogelijkheid om de klant in een contextuele reis te zien (d.w.z. gegevens kunnen opeenvolgend worden bekeken, die veelvoudige kanalen zowel online als offline overspannen)
- De mogelijkheid om de kracht van gegevens te benutten zonder dat dit nodig is (d.w.z. normale mensen kunnen gegevens gebruiken om diepe inzichten en analyses te ontsluiten voor activering van de marketing)

## 1.1.1.3 Waarom kiest u Customer Journey Analytics?

CJA is niet bedoeld om een huidige toepassing van BI zoals Power BI, Microstrategy, Locker of Tableau te vervangen. Deze toepassingen van BI zijn bedoeld om gegevens te visualiseren om collectieve dashboards tot stand te brengen zodat iedereen in een organisatie belangrijke metriek snel kan bekijken.\
Het doel van CJA is om analysemacht aan Marketing en Bedrijfsteams te brengen die het een &quot;moet&quot;analysehulpmiddel voor die mensen maken.

Van oudsher, zijn de toepassingen van BI niet in staat om ware klantenintelligentie toe te laten:

- Ze kunnen geen toeschrijving doen en maken geen analyse van de klantenterichting.
- BI-toepassingen moeten de vraag van tevoren kennen
- Interactieve query&#39;s worden beperkt door de structuur van de database
- SQL-vaardigheden zijn vereist.
- BI-toepassingen geven je niet de mogelijkheid om je af te vragen waarom er iets is gebeurd.
- BI-toepassingen hebben geen directe verbinding met aanraakpunten van klanten.

Om deze redenen hebben zakelijke gebruikers en analisten bijna onmiddellijk de dood gevonden, waardoor de analyse duur, traag, inflexibel en losgekoppeld van de systemen van actie is.

Met CJA kunt u een 360 mening van de klantenreis hebben, gebruikend off-line en online gegevens, met de juiste hulpmiddelen om de tijd aan inzicht te verminderen, die bedrijfsgebruikers onafhankelijk maken in het begrijpen waarom iets gebeurde, en hoe te om aan het te antwoorden.

![ demo ](./images/cja-use-case.png)

## 1.1.1.4 Begrijp de Customer Journey Analytics-workflow

Voordat u de volgende oefeningen start, is het van essentieel belang om te begrijpen welke stappen nodig zijn om gegevens van Adobe Experience Platform naar CJA te brengen om deze zichtbaar te maken en diepgaande inzichten te krijgen. Dat noemen we CJA Workflow. Laten we er eens naar kijken:

![ demo ](./images/cja-work-flow.jpg)

Vergeet voor het starten van de bovenstaande stappen niet stap 0, namelijk de gegevens te begrijpen die beschikbaar zijn in Adobe Experience Platform.

**huisvuil binnen, huisvuil uit.** Herinner je? U moet een duidelijk idee hebben van welke gegevens beschikbaar zijn en hoe de schema&#39;s in Adobe Experience Platform worden gevormd. Kennis van de gegevens in Adobe Experience Platform maakt dingen gemakkelijker, niet alleen op het onderdeel voor gegevensverbinding, maar ook bij het maken van visualisaties en het uitvoeren van analyses.

## 1.1.1.5 Stap 0: Het begrip van de schema&#39;s en datasets van Adobe Experience Platform

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Bekijk deze schema&#39;s en datasets in Adobe Experience Platform alstublieft.

| Gegevensset | Schema |
| ----------------- |-------------| 
| Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1) | Demosysteem - Gebeurtenisschema voor website (Global v1.1) |
| Het Systeem van de manifestatie - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) | Het Systeem van de demonstratie - het Schema van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) |
| Demosysteem - Dataset van de Gebeurtenis voor de Medewerkers van de Stem (Globale v1.1) | Demosysteem - Gebeurtenisschema voor spraakassistenten (Global v1.1) |

Zorg ervoor dat u op zijn minst de volgende zaken hebt gecontroleerd:

- Identiteiten: CRMID, phoneNumber, ECID, e-mail. Welke identiteiten zijn de primaire herkenningstekens, welke degenen zijn secundaire herkenningstekens?
U vindt de id&#39;s door een schema te openen en het object `--aepTenantId--.identification.core` te bekijken. Heb een blik bij het schema [ Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1) ](https://experience.adobe.com/platform/schema).

![ demo ](./images/identity.png)

- Onderzoek het handelsobject binnen het schema [ Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1) ](https://experience.adobe.com/platform/schema).

![ demo ](./images/commerce.png)

- Voorproef alle [ datasets ](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) en hebben een blik bij de gegevens

U kunt nu de gebruikersinterface van Customer Journey Analytics gebruiken.

## Volgende stappen

Ga naar [ 1.1.2 Connect de Datasets van Adobe Experience Platform in Customer Journey Analytics ](./ex2.md){target="_blank"}

Ga terug naar [ Customer Journey Analytics ](./customer-journey-analytics-build-a-dashboard.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

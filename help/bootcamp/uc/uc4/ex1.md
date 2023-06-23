---
title: Bootkamp - Customer Journey Analytics - Customer Journey Analytics 101
description: Bootkamp - Customer Journey Analytics - Customer Journey Analytics 101
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 587be8bc-8ebe-4f30-99d8-ba88ce40caf7
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# 4,1 Customer Journey Analytics 101

## Doelstellingen

- De CJA Application Service begrijpen
- Leer hoe u CJA kunt positioneren
- Begrijp de CJA-workflow: van gegevensverbinding tot inzichten

## 4.1.1 Wat is Customer Journey Analytics?

Customer Journey Analytics (CJA) verstrekt toolkit aan de bedrijfsintelligentie en gegevenswetenschapsteams voor het stitching en de analyse van kanaalgegevens (online en off-line). De mogelijkheden binnen CJA leveren context en helderheid aan de complexe multi-kanaals klantenreis. De verstrekte context leidt tot actioneel inzicht in het verwijderen van pijnpunten uit het proces van de klantenomzetting en het ontwerpen van en het leveren van uitzonderlijke ervaringen voor de momenten die het belangrijkst zijn.

CJA brengt Analysis Workspace bovenop Adobe Experience Platform. Adobe Experience Platform is het brein voor communicatie en orchestratie en met CJA kunnen merken nu al die gegevens contextualiseren en visualiseren, zodat Business en Insight teams er van kunnen leren door de volledige online naar offline reis van klanten te analyseren.

Bedrijfs en Insight teams kunnen met CJA spreken, vragen stellen en op de vlucht antwoorden krijgen met belemmering-en-daling, punt-en-klik en gebruikersvriendelijke UI van Analysis Workspace.

![demo](./images/cja-adv-analysis1.png)

## 4.1.2 Belangrijkste voordelen

De drie belangrijkste voordelen voor klanten zijn:

- De mogelijkheid om inzichten voor iedereen beschikbaar te maken (d.w.z., het democratiseren van de toegang tot gegevens)
- De mogelijkheid om de klant in een contextuele reis te zien (d.w.z. gegevens kunnen opeenvolgend worden bekeken, die veelvoudige kanalen zowel online als off-line overspannen)
- De mogelijkheid om de kracht van gegevens te benutten zonder dat dit nodig is (d.w.z. normale mensen kunnen gegevens gebruiken om diepe inzichten en analyses te ontsluiten voor activering van de marketing)

## 4.1.3 Waarom kiest u Customer Journey Analytics?

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

![demo](./images/cja-use-case.png)

## 4.1.4 Begrijpen wat de Customer Journey Analytics-workflow is

Voordat u de volgende oefeningen start, is het van essentieel belang om te begrijpen welke stappen nodig zijn om gegevens van Adobe Experience Platform naar CJA te brengen om deze zichtbaar te maken en diepgaande inzichten te krijgen. Dat noemen we CJA Workflow. Laten we er eens naar kijken:

![demo](./images/cja-work-flow.jpg)

Vergeet voor het starten van de bovenstaande stappen niet stap 0, namelijk de gegevens te begrijpen die beschikbaar zijn in Adobe Experience Platform.

**Vuil in, vuilnis uit.** Herinner je? U moet een duidelijk idee hebben van welke gegevens beschikbaar zijn en hoe de schema&#39;s in Adobe Experience Platform worden gevormd. Kennis van de gegevens in Adobe Experience Platform maakt dingen gemakkelijker, niet alleen op het onderdeel voor gegevensverbinding, maar ook bij het maken van visualisaties en het uitvoeren van analyses.

## 4.1.5 Stap 0: Adobe Experience Platform-schema&#39;s en gegevenssets

Meld u aan bij Adobe Experience Platform door naar deze URL te gaan: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensopname](../uc1/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Prod]** in de rechterbovenhoek van het scherm. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![Gegevensopname](../uc1/images/sb1.png)

Bekijk deze schema&#39;s en datasets in Adobe Experience Platform alstublieft.

| Gegevensset | Schema |
| ----------------- |-------------| 
| Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1) | Demosysteem - Gebeurtenisschema voor website (Global v1.1) |
| Het Systeem van de manifestatie - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) | Het Systeem van de demonstratie - het Schema van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) |
| Demosysteem - Dataset van de Gebeurtenis voor de Medewerkers van de Stem (Globale v1.1) | Demosysteem - Gebeurtenisschema voor spraakassistenten (Global v1.1) |

Zorg ervoor dat u op zijn minst de volgende zaken hebt gecontroleerd:

- Identiteiten: CRMID, phoneNumber, ECID, email. Welke identiteiten zijn de primaire herkenningstekens, welke degenen zijn secundaire herkenningstekens?
U kunt de id&#39;s vinden door een schema te openen en het object te bekijken `_experienceplatform.identification.core`. Bekijk het schema [Demosysteem - Gebeurtenisschema voor website (Global v1.1)](https://experience.adobe.com/platform/schema).

![demo](./images/identity.png)

- Het handelsobject binnen het schema verkennen [Demosysteem - Gebeurtenisschema voor website (Global v1.1)](https://experience.adobe.com/platform/schema).

![demo](./images/commerce.png)

- Voorvertoning van alle [gegevenssets](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) en bekijk de gegevens

U kunt nu de gebruikersinterface van de Customer Journey Analytics gebruiken.

Volgende stap: [4.2 Connect Adobe Experience Platform-gegevensbestanden in Customer Journey Analytics](./ex2.md)

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Terug naar alle modules](../../overview.md)

---
title: Migratieoverzicht - Migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie kiezen
description: Ontdek de belangrijkste verschillen tussen at.js en Platform Web SDK en hoe u uw migratie-inspanning kunt plannen.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: 6e442413c178e76183f88454d97d3896f8efa8bc
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Doel: migratie van SDK naar platform - Web

Het niveau van inspanning om van de uitbreiding van het Doel aan de uitbreiding van het Besluit te migreren hangt van de ingewikkeldheid van uw huidige implementatie en producteigenschappen af die worden gebruikt.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie en bepaal een migratiebenadering
1. De eerste componenten instellen voor verbinding met de Adobe Experience Platform-Edge Network
1. Werk uw implementatie bij om de Target SDK te vervangen door de XYZ
1. Verbeter de implementatie van Platform Mobile SDK voor uw specifieke gebruiksgevallen. Hiervoor moeten mogelijk aanvullende parameters worden doorgegeven, XYZ.
1. Objecten in de interface Doel bijwerken, zoals profielscripts, activiteiten en publieksdefinities??
1. De definitieve implementatie valideren voordat u uw bijgewerkte app publiceert

## Belangrijkste verschillen tussen at.js en Platform Web SDK

Alvorens het migratieproces te beginnen, is het belangrijk om de verschillen tussen at.js en het Web SDK van het Platform te begrijpen.

### Operationele verschillen

Het Web SDK van het Platform combineert de functionaliteit van veelvoudige Adobe toepassingen in één enkele bibliotheek. Deze verenigde benadering betekent u over teamoverschrijdende verantwoordelijkheden en processen zou moeten nadenken om een gezonde implementatie te verzekeren.

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Eigendom | De extensie Doel is onafhankelijk van andere SDK&#39;s van toepassingen (DENK NIET DAT DIT VOOR MOBILE WAAR IS). Aanpassingen en eigendom van deze verschillende bibliotheken kunnen worden uitgelijnd op verschillende teams in de organisatie. | De bibliotheek van SDK van het Web van het Platform en de overgegaane gegevens zijn verenigd voor alle toepassingen van de Adobe. De eigendom van de Web SDK-implementatie van het Platform moet de belanghebbenden van alle downstreamtoepassingen vertegenwoordigen. |
| Onderhoud | Afzonderlijke teams kunnen werken aan implementatieverbeteringen voor elke Adobe-toepassing, zoals Doel en Analyse. | Idealiter is één team verantwoordelijk voor verbeteringen die van invloed zijn op de Web SDK-implementatie van het platform. |
| Proces | Wijzigingen in een doelimplementatie kunnen plaatsvinden na een proces dat andere eisen stelt aan de snelheid of kwaliteit van de kwaliteit in vergelijking met andere toepassingen, zoals Analytics. | De veranderingen in een implementatie van het Web SDK van het Platform zouden alle stroomafwaartse toepassingen moeten overwegen, en het QA en publicatieproces zouden dienovereenkomstig moeten worden aangepast. |
| Collaboration | De gegevens specifiek voor Doel kunnen direct in de vraag van het Doel worden overgegaan. Afhankelijk van de implementatie, kunnen er extra vraag van het Doel zijn. Dit heeft geen directe gevolgen voor de gegevens van Adobe Analytics en de coördinatie met het analytisch team is niet zo cruciaal. | Gegevens die in de vraag van SDK van het Web van het Platform worden overgegaan kunnen aan zowel Doel als Analytics door:sturen. Coördinatie tussen teams is vereist om ervoor te zorgen dat wijzigingen geen negatieve gevolgen hebben voor een specifieke toepassing. |

### Technische verschillen

De Platform Web SDK is geen evolutie van het Doel in.js bibliotheek. Het is een nieuwe en verenigde benadering voor het uitvoeren van alle toepassingen van de Adobe voor het Webkanaal. Er zijn verschillende technische verschillen om op de hoogte te zijn.

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Bibliotheekfunctionaliteit | Doelfunctionaliteit verstrekt door at.js. Integratie met andere toepassingen van Visitor.js en AppMeasurement.js | Functionaliteit voor alle toepassingen van de Adobe die door één enkele bibliotheek van de SDK van het Web van het Platform worden verstrekt: alloy.js |
| Prestaties | at.js is één van veelvoudige bibliotheken die voor juiste integratie over toepassingen moeten worden geladen. Dit resulteert in minder dan optimale laadtijd. | Het Web SDK van het Platform is één enkele lichtgewichtbibliotheek die de behoefte aan veelvoudige toepassing-specifieke bibliotheken elimineert resulterend in betere prestaties van de paginading. |
| Verzoeken | Afzonderlijke vraag voor elke toepassing van de Adobe. De vraag van het doel is grotendeels onafhankelijk van andere netwerkvraag. | Één enkele vraag voor alle toepassingen van de Adobe. De veranderingen in de gegevens die in deze vraag worden overgegaan zouden veelvoudige stroomafwaartse toepassingen kunnen beïnvloeden. |
| Laadvolgorde | De correcte integratie met andere toepassingen van de Adobe vereist een specifieke ladingsorde van bibliotheken en netwerkvraag. | De juiste integratie baseert zich niet op het stitching van gegevens van verschillende toepassing-specifieke netwerkvraag, zodat is de ladingsorde geen zorg. |
| Edge Network | Gebruikt de Edge Network van Adobe Experience Cloud (tt.omtrdc.net), naar keuze met een CNAME specifiek voor Doel. | Gebruikt de Edge Network van Adobe Experience Platform (edge.adobedc.net), naar keuze met één enkele NAAM. |
| Standaardterminologie | at.js-naamgeving: <br> - `mbox` <br> - `pageLoad` -gebeurtenis (global mbox) <br> - `offer` | Het equivalent van Platform Web SDK: <br> - `decisionScope` <br> - `__view__` DecisionScope <br> - `proposition` |

### Video-overzicht

De volgende video geeft een overzicht van de Adobe Experience Platform Web SDK en Adobe Experience Platform Edge Network.


Nu u de verschillen op hoog niveau tussen at.js en het Web SDK van het Platform begrijpt, kunt u [ de migratie ](plan-migration.md) plannen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

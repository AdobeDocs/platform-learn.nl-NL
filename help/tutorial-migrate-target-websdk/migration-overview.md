---
title: Migratieoverzicht - Doel migreren van at.js 2.x naar Web SDK
description: Ontdek de belangrijkste verschillen tussen at.js en Platform Web SDK en hoe u uw migratie-inspanning kunt plannen.
exl-id: a8ed78e4-c8c2-4505-b4b5-e5d508f5ed87
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Doel: migratie van SDK naar platform - Web

De mate van inspanning om van om.js aan het Web SDK van het Platform te migreren hangt van de ingewikkeldheid van uw huidige implementatie en producteigenschappen af die worden gebruikt.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie en bepaal een migratiebenadering
1. De eerste componenten instellen om verbinding te maken met de Adobe Experience Platform Edge Network
1. Werk de stitionele implementatie bij om at.js met het Web SDK van het Platform te vervangen
1. Verbeter de implementatie van het Web SDK van het Platform voor uw specifieke gebruiksgevallen. Dit kan het overgaan van extra parameters omvatten, rekenend voor de veranderingen van de enig-pagina app (SPA) mening, gebruikend reactietokens, en meer.
1. Objecten in de interface Doel bijwerken, zoals profielscripts, activiteiten en publieksdefinities
1. Valideer de definitieve implementatie alvorens de schakelaar in uw productiemilieu te maken

## Belangrijkste verschillen tussen at.js en Platform Web SDK

Alvorens het migratieproces te beginnen, is het belangrijk om de verschillen tussen at.js en het Web SDK van het Platform te begrijpen.

### Operationele verschillen

Het Web SDK van het Platform combineert de functionaliteit van veelvoudige toepassingen van Adobe in één enkele bibliotheek. Deze verenigde benadering betekent u over teamoverschrijdende verantwoordelijkheden en processen zou moeten nadenken om een gezonde implementatie te verzekeren.

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Eigendom | De bibliotheek at.js is onafhankelijk van andere toepassingsbibliotheken. Aanpassingen en eigendom van deze verschillende bibliotheken kunnen worden uitgelijnd op verschillende teams in de organisatie. | De Platform Web SDK-bibliotheek en de gegevens die worden doorgegeven, zijn voor alle Adobe-toepassingen gelijk. De eigendom van de Web SDK-implementatie van het Platform moet de belanghebbenden van alle downstreamtoepassingen vertegenwoordigen. |
| Onderhoud | Afzonderlijke teams kunnen werken aan implementatieverbeteringen voor elke Adobe-toepassing, zoals Target en Analytics. | Idealiter is één team verantwoordelijk voor verbeteringen die van invloed zijn op de Web SDK-implementatie van het platform. |
| Proces | Wijzigingen in een doelimplementatie kunnen plaatsvinden na een proces dat andere eisen stelt aan de snelheid of kwaliteit van de kwaliteit in vergelijking met andere toepassingen, zoals Analytics. | De veranderingen in een implementatie van het Web SDK van het Platform zouden alle stroomafwaartse toepassingen moeten overwegen, en het QA en publicatieproces zouden dienovereenkomstig moeten worden aangepast. |
| Collaboration | De gegevens specifiek voor Doel kunnen direct in de vraag van het Doel worden overgegaan. Afhankelijk van de implementatie, kunnen er extra vraag van het Doel zijn. Dit heeft geen directe gevolgen voor de gegevens van Adobe Analytics en de coördinatie met het analytisch team is niet zo cruciaal. | Gegevens die in de vraag van SDK van het Web van het Platform worden overgegaan kunnen aan zowel Doel als Analytics door:sturen. Coördinatie tussen teams is vereist om ervoor te zorgen dat wijzigingen geen negatieve gevolgen hebben voor een specifieke toepassing. |

### Technische verschillen

De Platform Web SDK is geen evolutie van het Doel in.js bibliotheek. Het is een nieuwe en uniforme aanpak voor de implementatie van alle Adobe-toepassingen voor het webkanaal. Er zijn verschillende technische verschillen om op de hoogte te zijn.

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Bibliotheekfunctionaliteit | Doelfunctionaliteit verstrekt door at.js. Integratie met andere toepassingen van Visitor.js en AppMeasurement.js | Functionaliteit voor alle Adobe-toepassingen die worden geleverd door één webbibliotheek van het platform: alloy.js |
| Prestaties | at.js is één van veelvoudige bibliotheken die voor juiste integratie over toepassingen moeten worden geladen. Dit resulteert in minder dan optimale laadtijd. | Het Web SDK van het Platform is één enkele lichtgewichtbibliotheek die de behoefte aan veelvoudige toepassing-specifieke bibliotheken elimineert resulterend in betere prestaties van de paginading. |
| Verzoeken | Afzonderlijke aanroepen voor elke Adobe-toepassing. De vraag van het doel is grotendeels onafhankelijk van andere netwerkvraag. | Eén oproep voor alle Adobe-toepassingen. De veranderingen in de gegevens die in deze vraag worden overgegaan zouden veelvoudige stroomafwaartse toepassingen kunnen beïnvloeden. |
| Laadvolgorde | De correcte integratie met andere toepassingen van Adobe vereist een specifieke ladingsorde van bibliotheken en netwerkvraag. | De juiste integratie baseert zich niet op het stitching van gegevens van verschillende toepassing-specifieke netwerkvraag, zodat is de ladingsorde geen zorg. |
| Edge Network | Gebruikt de Adobe Experience Cloud Edge Network (tt.omtrdc.net), optioneel met een CNAME specifiek voor Doel. | Gebruikt de Adobe Experience Platform Edge Network (edge.adobedc.net), optioneel met één CNAME. |
| Standaardterminologie | at.js-naamgeving: <br> - `mbox` <br> - `pageLoad` -gebeurtenis (global mbox) <br> - `offer` | Het equivalent van Platform Web SDK: <br> - `decisionScope` <br> - `__view__` DecisionScope <br> - `proposition` |

### Video-overzicht

De volgende video geeft een overzicht van de Adobe Experience Platform Web SDK en Adobe Experience Platform Edge Network.

>[!VIDEO](https://video.tv.adobe.com/v/34141/?learn=on&enablevpops)

Nu u de verschillen op hoog niveau tussen at.js en het Web SDK van het Platform begrijpt, kunt u [&#x200B; de migratie &#x200B;](plan-migration.md) plannen.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw doelmigratie van at.js naar Web SDK. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=nl#M463) te posten.

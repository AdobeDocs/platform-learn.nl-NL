---
title: Offer decisioning - Offer decisioning 101
description: Offer decisioning - Offer decisioning 101
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
exl-id: 8a627c29-7780-455f-abe1-a69f8fe145ea
source-git-commit: 21718a7c3a4df2793ae257a9b7cbe4466f1193f5
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# 3.3.1 Offer decisioning 101

## 3.3.1.1 Terminologie

Om een beter begrip over Offer decisioning te krijgen, adviseren wij hoogst u om het [ overzicht ](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=nl-NL) te lezen over hoe de Dienst van de Toepassing van de Offer decisioning met Adobe Experience Platform werkt.

Als u met Offer decisioning werkt, moet u de volgende concepten begrijpen:

| Term | Toelichting |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Aanbieding** | Een aanbieding is een marketingbericht waaraan regels kunnen zijn gekoppeld die bepalen wie in aanmerking komt om de aanbieding te zien. Een voorstel heeft een status: concept, goedgekeurd of gearchiveerd. |
| **Plaatsing** | De combinatie van locatie (of Kanaaltype) en context (of Inhoudstype) waarin een aanbieding voor een eindgebruiker wordt weergegeven. In feite is het de combinatie van Tekst, HTML, Beeld, JSON in Mobiel, Web, Sociaal, Onmiddellijk Overseinen, en niet-Digitale kanalen. |
| **Regel** | De logica die bepaalt en controleert of eindgebruikers in aanmerking komen voor een aanbieding. |
| **Gepersonaliseerde Aanbieding** | Een aanpasbaar marketingbericht op basis van geschiktheidsregels en -beperkingen. |
| **Aanbieding van de Fallback** | Het standaardaanbod dat wordt weergegeven wanneer een eindgebruiker niet in aanmerking komt voor een van de aanbiedingen in de gebruikte collectie. |
| **Aftappen** | Gebruikt in een aanbiedingsdefinitie om te bepalen hoe vaak een aanbieding in totaal en aan een specifieke gebruiker kan worden voorgesteld. |
| **Prioriteit** | Niveau om de prioritaire rang van een resultaatreeks aanbiedingen te bepalen. |
| **Inzameling** | Wordt gebruikt om een subset met aanbiedingen uit de lijst met gepersonaliseerde aanbiedingen te filteren om het proces van de offer decisioning te versnellen. |
| **Besluit** | Een combinatie van een reeks aanbiedingen, plaatsing en profiel die de marktleider wil de besluitvormingsmotor de beste aanbieding voor verstrekken. |
| **Hoofdzaak van AEM Assets** | Een universele en gecentraliseerde ervaring voor het opslaan, zoeken en selecteren van middelen in Adobe Experience Cloud Solutions en Adobe Experience Platform. |

{style="table-layout:auto"}

## 3.3.1.2 Offer decisioning

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

In het linkermenu, klik **Aanbiedingen**. U ziet nu het menu Aanbiedingen, dat dingen als Aanbiedingen, Verzamelingen en Besluiten bevat.

![ Plaatsingen ](./images/homedec.png)

Klik **Componenten**. U zult nu dingen zoals Plaatsen, het kwalificeren van de Inzameling, Regels en Rankingen zien.

![ Plaatsingen ](./images/components.png)

## 3.3.1.3 Plaatsingen

Ga naar **Plaatsen**.

![ Plaatsingen ](./images/placements.png)

In het **lusje van Plaatsen** kunt u uw plaatsingen voor uw aanbiedingen bepalen. Wanneer u een beslissing definieert, bepaalt de plaatsing waar de resulterende aanbieding wordt weergegeven (Kanaaltype) en in welke vorm of vorm (Inhoudstype).

Als u geen plaatsingen in uw milieu ziet, te creëren gelieve hen zoals hieronder en in het screenshot wordt vermeld.

| Naam | Kanaaltype | Inhoudstype |
| ---------------------- | ------------ | ------------ |
| **niet-digitaal - Tekst** | Niet-digitaal | Tekst |
| **Web - JSON** | Web | JSON |
| **Web - HTML** | Web | HTML |
| **Web - Tekst** | Web | Tekst |
| **Web - Beeld** | Web | Afbeelding |
| **E-mail - JSON** | Email | JSON |
| **E-mail - HTML** | Email | HTML |
| **E-mail - Tekst** | Email | Tekst |
| **E-mail - Beeld** | Email | Afbeelding |

{style="table-layout:auto"}

**Nota**: Gelieve te veranderen niets in de reeds beschikbare plaatsen.

Klik op een willekeurige locatie om de instellingen van de locatie te visualiseren.

![ Plaatsingen ](./images/placement1.png)

U ziet nu alle velden van de Placement:

- **Naam** van de Plaatsing
- **identiteitskaart van de Plaatsing**
- **Type van Kanaal** voor de Plaatsing
- **Type van Inhoud** van de Plaatsing, die **Tekst** kan zijn, **HTML**, **Beeld** of **JSON**
- **Beschrijving** gebied dat toestaat om extra beschrijving voor de Plaatsing toe te voegen

## 3.3.1.4 Regels voor besluiten

Een regel (ook genoemd toelatingsregel) is het equivalent van een **publiek**. Een regel is in feite een publiek zelf met het enige verschil dat een regel met een aanbieding kan worden gebruikt om de beste aanbieding aan een profiel in Adobe Experience Platform te verstrekken.

Aangezien u reeds weet hoe te om publiek te bepalen dat op de vorige enablement modules wordt gebaseerd, herzien wij enkel snel het Milieu van de Segmentatie:

Ga naar **Regels**. Klik op **+ Regel maken** .

![ Regels van het Besluit ](./images/rules.png)

Dan zie je de interface Audience creation van Adobe Experience Platform.

![ Regels van het Besluit ](./images/createrule1.png)

U kunt tot alle gebieden nu toegang hebben die deel van het Schema van de Vereniging voor het Profiel van de Klant in real time uitmaken en om het even welke regel kunnen bouwen.

Het is ook goed om te weten dat u reeds bepaald publiek in Adobe Experience Platform eenvoudig kunt hergebruiken, door **Soorten van publiek** te gaan > ``--aepTenantId--``.

U zult dan dit zien:

![ Regel van het Besluit ](./images/decisionruleaud.png)

Als u wenst, kunt u uw eigen Regels nu vormen. Hiervoor hebt u twee regels nodig:

- all - Mannelijke klanten
- all - Vrouwelijke klanten

Als deze regels nog niet bestaan, kunt u ze maken. Gebruik deze regels als ze al bestaan en maak geen nieuwe regels.

Het attribuut om de regel te gebruiken te bouwen is **XDM Individueel Profiel** > **Persoon** > **Geslacht**.

Als voorbeeld, hier is de regeldefinitie voor de regel **allen - Mannelijke Klanten**:

![ Regel van het Besluit ](./images/allmale.png)

Als voorbeeld, hier is de regeldefinitie voor de regel **allen - Vrouwelijke Klanten**:

![ Regel van het Besluit ](./images/allfemale.png)

## 3.3.1.5 Aanbiedingen

Ga naar **Aanbiedingen** en selecteer **Aanbiedingen**. Klik op **+ Voorstel maken** .

![ Regel van het Besluit ](./images/offers1.png)

Dan zie je deze popup.

![ Regel van het Besluit ](./images/offers2.png)

Maak nu geen aanbiedingen, dat doe je in de volgende oefening.

U ziet nu dat er twee soorten aanbiedingen zijn:

- Persoonlijke aanbiedingen
- Terugvalvoorstellen

Een persoonlijk voorstel is specifieke inhoud die in een specifieke situatie moet worden getoond. Een persoonlijk aanbod is speciaal ontworpen om een persoonlijke en contextuele ervaring te bieden als aan specifieke criteria wordt voldaan.

Een Fallback-aanbieding is een aanbieding die wordt weergegeven als niet wordt voldaan aan de criteria voor persoonlijke aanbiedingen.

## 3.3.1.6 Besluiten

In een besluit worden stages, een verzameling persoonlijke aanbiedingen en een terugvalaanbieding gecombineerd die uiteindelijk door de Offer decisioning-engine worden gebruikt om de beste aanbieding voor een specifiek profiel te vinden, op basis van elk van de individuele kenmerken van gepersonaliseerde aanbiedingen, zoals prioriteit, geschiktheidsbeperking en totale/gebruikersbeperking.

Om uw **Besluit** te vormen, klik **Besluiten**.

![ Regel van het Besluit ](./images/activity.png)

In de volgende oefening, zult u uw eigen aanbiedingen en besluit vormen.

Volgende Stap: [ 3.3.2 vormt uw Aanbiedingen en Besluit ](./ex2.md)

[Terug naar module 3.3](./offer-decisioning.md)

[Terug naar alle modules](./../../../overview.md)

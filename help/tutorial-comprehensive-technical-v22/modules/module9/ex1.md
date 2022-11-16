---
title: offer decisioning - Offer decisioning 101
description: offer decisioning - Offer decisioning 101
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: e7cfe551-c8b4-47b0-b048-05e1869da7f9
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 1%

---

# 9.1 Offer decisioning 101

## 9.1.1 Terminologie

Voor een beter inzicht in Offer decisioning raden we u aan de [overzicht](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=en) op hoe de Offer decisioning Application Service met Adobe Experience Platform werkt.

Als u met Offer decisioning werkt, moet u de volgende concepten begrijpen:

| Term | Toelichting |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Voorstel** | Een aanbieding is een marketingbericht waaraan regels kunnen zijn gekoppeld die bepalen wie in aanmerking komt om de aanbieding te zien. Een voorstel heeft de status: ontwerp, goedgekeurd of gearchiveerd. |
| **Plaatsing** | De combinatie van locatie (of Kanaaltype) en context (of Inhoudstype) waarin een aanbieding voor een eindgebruiker wordt weergegeven. In feite is het de combinatie van Tekst, HTML, Beeld, JSON in Mobiel, Web, Sociaal, Onmiddellijk Overseinen, en niet-Digitale kanalen. |
| **Regel** | De logica die bepaalt en controleert of eindgebruikers in aanmerking komen voor een aanbieding. |
| **Persoonlijk voorstel** | Een aanpasbaar marketingbericht op basis van geschiktheidsregels en -beperkingen. |
| **Herkansingsaanbod** | Het standaardaanbod dat wordt weergegeven wanneer een eindgebruiker niet in aanmerking komt voor een van de aanbiedingen in de gebruikte verzameling. |
| **Afbeelding** | Gebruikt in een aanbiedingsdefinitie om te bepalen hoe vaak een aanbieding in totaal en aan een specifieke gebruiker kan worden voorgesteld. |
| **Prioriteit** | Niveau om de prioritaire rang van een resultaatreeks aanbiedingen te bepalen. |
| **Verzameling** | Wordt gebruikt om een subset met aanbiedingen uit de lijst met gepersonaliseerde aanbiedingen te filteren om het proces van de offer decisioning te versnellen. |
| **Besluit** | Een combinatie van een reeks aanbiedingen, plaatsing en profiel wil de marktleider de beslissingsmotor de beste aanbieding voor verstrekken. |
| **AEM Assets Essentials** | Een universele en gecentraliseerde ervaring voor het opslaan, zoeken en selecteren van middelen in Adobe Experience Cloud Solutions en Adobe Experience Platform. |

{style=&quot;table-layout:auto&quot;}

## 9.1.2 Offer decisioning

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

Klik in het linkermenu op **Aanbiedingen**. U ziet nu het menu Aanbiedingen, dat dingen als Aanbiedingen, Verzamelingen en Besluiten bevat.

![Plaatsingen](./images/homedec.png)

Klikken **Componenten**. U ziet nu het menu Aanbiedingen, dat elementen als Plaatsen, Markeringen, Regels en Waarderingen bevat.

![Plaatsingen](./images/components.png)

## 9.1.3 Plaatsen

Ga naar **Plaatsen**.

![Plaatsingen](./images/placements.png)

In de **Plaatsen** kunt u uw plaatsingen voor uw aanbiedingen bepalen. Wanneer u een beslissing definieert, bepaalt de plaatsing waar de resulterende aanbieding wordt weergegeven (Kanaaltype) en in welke vorm of vorm (Inhoudstype).

Als u geen plaatsingen in uw Adobe Experience Platform-exemplaar ziet, gelieve te creëren zoals hieronder en in het screenshot wordt vermeld.

| Naam | Kanaaltype | Inhoudstype |
| ---------------------- | ------------ | ------------ |
| **Niet-digitaal - tekst** | Niet-digitaal | Tekst |
| **Web - JSON** | Web | JSON |
| **Web - HTML** | Web | HTML |
| **Web - tekst** | Web | Tekst |
| **Web - Afbeelding** | Web | Afbeelding |
| **E-mail - JSON** | Email | JSON |
| **E-mail - HTML** | E-mail | HTML |
| **E-mail - tekst** | E-mail | Tekst |
| **E-mail - Afbeelding** | E-mail | Afbeelding |

{style=&quot;table-layout:auto&quot;}

**Opmerking**: Wijzig niets in de reeds beschikbare plaatsingen.

Klik op een willekeurige locatie om de instellingen van de locatie te visualiseren.

![Plaatsingen](./images/placement1.png)

U ziet nu alle velden van de Placement:

- **Naam** van de plaatsing
- **Plaatsing-id**
- **Kanaaltype** voor de plaatsing
- **Inhoudstype** van de plaats, die **Tekst**, **HTML**, **Afbeelding** of **JSON**
- **Beschrijving** veld voor het toevoegen van een aanvullende beschrijving voor de plaatsing

## 9.1.4 Regels voor besluiten

Een regel (ook wel subsidiabiliteitsregel genoemd) is het equivalent van een **Segment**. Een regel is in feite een Segment zelf met het enige verschil dat een Regel met een Voorstel kan worden gebruikt om de beste aanbieding aan een profiel in Adobe Experience Platform te verstrekken.

Aangezien u reeds weet hoe te om Segmenten te bepalen die op de vorige enablement modules worden gebaseerd, herzien enkel snel het Milieu van de Segmentatie:

Ga naar **Regels**. Klikken **+ Regel maken**.

![Besluitvormingsregels](./images/rules.png)

Dan zie je de segmentatieomgeving van Adobe Experience Platform.

![Besluitvormingsregels](./images/createrule1.png)

U kunt tot alle gebieden nu toegang hebben die deel van het Schema van de Vereniging voor het Profiel van de Klant in real time uitmaken en om het even welke regel kunnen bouwen.

Het is ook interessant om te weten dat u reeds bepaalde segmenten in Adobe Experience Platform eenvoudig kunt hergebruiken, door te gaan naar **Soorten publiek** > ``--aepTenantIdSchema--``.

![Beslissingsregel](./images/decisionruleaud.png)

U zult dan dit zien:

![Beslissingsregel](./images/decisionruleaud1.png)

Als u wenst, kunt u uw eigen Regels nu vormen. Voor deze oefening, zult u twee regels nodig hebben:

- all - Mannelijke klanten
- all - Vrouwelijke klanten

Als deze regels nog niet bestaan, kunt u ze maken. Gebruik deze regels als ze al bestaan en maak geen nieuwe regels.

Het attribuut om de regel te gebruiken te bouwen is **Afzonderlijk XDM-profiel** > **Persoon** > **Geslacht**.

Als voorbeeld, hier is de regeldefinitie voor de regel **all - Mannelijke klanten**:

![Beslissingsregel](./images/allmale.png)

Als voorbeeld, hier is de regeldefinitie voor de regel **all - Vrouwelijke klanten**:

![Beslissingsregel](./images/allfemale.png)

## 9.1.5 Aanbiedingen

Ga naar **Aanbiedingen** en selecteert u **Aanbiedingen**. Klikken **+ Voorstel maken**.

![Beslissingsregel](./images/offers1.png)

Dan zie je deze popup.

![Beslissingsregel](./images/offers2.png)

Maak nu geen aanbiedingen, dat doe je in de volgende oefening.

U ziet nu dat er twee soorten aanbiedingen zijn:

- Persoonlijke aanbiedingen
- Terugvalvoorstellen

Een persoonlijk voorstel is specifieke inhoud die in een specifieke situatie moet worden getoond. Een persoonlijk aanbod is speciaal ontworpen om een persoonlijke en contextuele ervaring te bieden als aan specifieke criteria wordt voldaan.

Een Fallback-aanbieding is een aanbieding die wordt weergegeven als niet wordt voldaan aan de criteria voor persoonlijke aanbiedingen.

## 9.1.6 Besluiten

In een besluit worden stages, een verzameling persoonlijke aanbiedingen en een terugvalaanbieding gecombineerd die uiteindelijk door de Offer decisioning-engine worden gebruikt om de beste aanbieding voor een specifiek profiel te vinden, op basis van elk van de individuele kenmerken van gepersonaliseerde aanbiedingen, zoals prioriteit, geschiktheidsbeperking en totale/gebruikersbeperking.

Om uw te vormen **Besluit**, klikt u op **Besluiten**.

![Beslissingsregel](./images/activity.png)

In de volgende oefening, zult u uw eigen aanbiedingen en besluit vormen.

Volgende stap: [9.2 Configureer uw aanbiedingen en besluit](./ex2.md)

[Ga terug naar module 9](./offer-decisioning.md)

[Terug naar alle modules](./../../overview.md)

---
title: Uw mobiele app migreren van de Adobe Target naar de Adobe Journey Optimizer - De beslissingsextensie
description: Leer hoe u uw mobiele app-implementatie van de Adobe Target naar de Adobe Journey Optimizer kunt migreren - De extensie voor beslissingen
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: 32363b95-b6ad-44af-a3b0-e1fbbbf5a8f1
source-git-commit: 24effdb0905c6fd146a80031e0a39eed9672306d
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# Uw mobiele app migreren van de Adobe Target naar de Adobe Journey Optimizer - De beslissingsextensie

Deze handleiding is bedoeld voor ervaren Adobe Target-implementatoren die leren hoe u bestaande Adobe Experience Platform Mobile SDK-implementaties kunt migreren van de Adobe Target-extensie naar de Adobe Journey Optimizer - Decisioning-extensie.

Adobe Experience Platform Mobile SDK biedt volledige betrokkenheid bij uw mobiele toepassingen. De extensie Doel bouwt verder op de Mobile SDK om u te helpen uw app-ervaringen met Adobe Target aan te passen. De extensie Decisioning is een nieuwere benadering voor het implementeren van Adobe Target in mobiele apps die gebruikmaken van Adobe Experience Platform Edge Network-mogelijkheden die helpen bij de integratie van Target met platformgebaseerde apps zoals Real-Time CDP en Journey Optimizer.

![ Diagram die Mobiele SDK tonen die met Doel door Edge Network met de Decisioning uitbreiding verbinden ](assets/datacollection.png)

## Belangrijkste voordelen

Enkele voordelen van de Adobe Journey Optimizer-decisioning-extensie in vergelijking met de Target-extensie zijn:

* Sneller het delen van publiek van [ Real-Time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* Het integreren Doel met Journey Optimizer om [ levering van Offer Decisioning te steunen ](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Een nauwere integratie met Adobe Analytics die niet afhankelijk is van het koppelen van informatie van afzonderlijke netwerkoproepen
* Extra implementatieflexibiliteit voor ontwikkelaars

Het grootste voordeel van migratie voor klanten van Target is waarschijnlijk de integratie met Real-Time Customer Data Platform. Real-Time CDP biedt enorme mogelijkheden voor publieksopbouw op basis van het volledige scala aan gegevens die in Experience Platform worden ingevoerd en de mogelijkheid om in realtime een klantprofiel te maken. Een ingebouwd kader voor gegevensbeheer automatiseert verantwoord gebruik van die gegevens. Met AI van de klant kunt u eenvoudig modellen voor machinaal leren gebruiken voor het samenstellen van eigenschappen en churn-modellen waarvan de uitvoer naar Adobe Target kan worden gedeeld. Tot slot kunnen klanten van de optionele toevoegingen aan de gezondheidszorg en het privacyschild de functie voor het afdwingen van toestemming gebruiken om de voorkeuren voor toestemming van individuele klanten af te dwingen. Platform Mobile SDK en de extensie Decisioning zijn een vereiste om deze Real-Time CDP-functies in uw mobiele kanaal te kunnen gebruiken.

## Migratiestappen

Het niveau van inspanning om van de uitbreiding van het Doel aan de uitbreiding van het Besluit te migreren hangt van de ingewikkeldheid van uw huidige implementatie en gebruikte eigenschappen van het Doel af.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie, inclusief:
   1. Alle doel-SDK-API&#39;s gebruikt
   1. Wijzigingen in de algemene instellingen van Target
   1. Integratie met Adobe Analytics
   1. Het gebruik van mbox-, profiel- en entiteitsparameters
   1. Gebruik van profielscripts en publiek
   1. Aangepaste code die uniek is voor uw implementatie
1. De eerste componenten instellen om verbinding te maken met de Adobe Experience Platform Edge Network
1. Werk de fundamentele implementatie bij om de uitbreiding van het Doel met de Decisioning uitbreiding te vervangen
1. Verbeter de implementatie van SDK optimaliseren voor uw specifieke gebruiksgevallen. Dit kan het doorgeven van extra parameters, het gebruiken van reactietokens, en meer impliceren.
1. Objecten in de interface Doel bijwerken, zoals profielscripts, activiteiten en publieksdefinities
1. Valideer de definitieve implementatie alvorens de schakelaar in uw productieapp te maken


>[!INFO]
>
>In het ecosysteem van Adobe Experience Platform Mobile SDK worden extensies geïmplementeerd door SDK&#39;s die zijn geïmporteerd in uw toepassingen en die verschillende namen kunnen hebben:
>
> * **SDK van het Doel** voert de **uitbreiding van Adobe Target** uit
> * **optimaliseer SDK** voert **Adobe Journey Optimizer uit - Beslissende uitbreiding**

Daarna, herzie de gedetailleerde [ vergelijking van de uitbreiding van het Doel en de Decisioning uitbreiding ](comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

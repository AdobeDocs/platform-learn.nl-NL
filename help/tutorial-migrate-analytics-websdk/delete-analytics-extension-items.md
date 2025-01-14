---
title: De Adobe Analytics-extensie-items verwijderen
description: Wanneer het zuiveren en de bevestiging volledig is, verwijder alle verwijzingen naar de de uitbreidingspunten van Adobe Analytics en verwijder de uitbreiding zelf.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16766
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---


# De Adobe Analytics-extensie-items verwijderen

Wanneer het zuiveren en de bevestiging volledig is, verwijder alle verwijzingen naar de de uitbreidingspunten van Adobe Analytics en verwijder de uitbreiding zelf.

## Overzicht

Zodra u wordt tevredengesteld dat alles in uw bezit over aan het Web SDK is gemigreerd, en u hebt het zuiveren en bevestiging (in uw ontwikkelomgeving) voltooid, bent u bereid om de verwijzingen naar de uitbreiding van Adobe Analytics te verwijderen. Hoe snel u deze items verwijdert en hoe vaak u test terwijl u dit doet, is aan u. Als u meer voorzichtig wilt zijn, verwijdert u de referenties langzaam en test u de tussenliggende verwijdering. Als u zeker weet dat alles correct werkt en correct is gemigreerd, kunt u de bandhulp verwijderen en alle items verwijderen. We raden natuurlijk nog steeds aan om aan het einde van de oefening te testen.

## Oude handelingen verwijderen uit regels

We gaan ervan uit dat je alles al hebt getest en dat het correct werkt. Op dit punt kunt u één voor één in uw regels gaan en de acties verwijderen die tot de uitbreiding van Adobe Analytics behoren.

1. Open een van uw regels, bijvoorbeeld de standaard laadregel voor de pagina.
1. Na de migratie voor deze regel hebt u waarschijnlijk 4 (of meer) acties uitgevoerd.

   ![ Alle 4 acties ](assets/all-four-actions.jpg)

1. Je kunt zien dat de eerste twee de id &#39;Adobe Analytics&#39; hebben. Dit zijn de acties die we willen verwijderen.
1. Plaats de muis boven de eerste actie, zoals de actie &quot;Adobe Analytics - Set Variables&quot;, en een X staat verwijdering toe. Klik op de X en zie de handeling verdwijnen. Verwijder om het even welke en alle acties van Adobe Analytics in de regel, in dit geval de Vastgestelde actie van de Variabele en de Send actie van het Band.
1. Hiermee blijven alleen de Web SDK-acties behouden

   ![ de acties van SDK van het Web slechts ](assets/websdk-actions-only.jpg)

1. Opslaan in bibliotheek
1. Bouw de bibliotheek en test uw plaats, om ervoor te zorgen dat er geen nieuwe fouten zijn en dat alles behoorlijk werkt
1. Herhaal deze handeling voor uw andere regels, bouw aan uw ontwikkelingsbibliotheek en het testen tussen elke verwijdering (of zo vaak aangezien u comfortabel bent). U kunt enkel in debugger testen, of ook de rapporten in de reeks van het migratierapport, opnieuw afhankelijk van uw comfortniveau controleren.

## Extensies verwijderen

Nu u de verwijzingen naar uw Adobe Analytics-extensie hebt verwijderd, kunt u de extensie verwijderen (of uitschakelen) en alle andere extensies die deze gebruiken of er afhankelijk van zijn. Persoonlijk hou ik van een voorzichtige benadering, en dus &quot;maak onbruikbaar&quot;is mijn keus in plaats van, in ieder geval aanvankelijk, te verwijderen.

1. Selecteer **Uitbreidingen** van het linkerspoor in UI.
1. Zorg ervoor dat het **Geïnstalleerde** lusje wordt geselecteerd.
1. Selecteer de extensie Adobe Analytics.
1. Kies in het rechterspoor of u de extensie wilt uitschakelen (of klik op de drie stippen en verwijder desgewenst de installatie).

   ![ maak de uitbreiding van Analytics ](assets/disable-analytics-extension.jpg) onbruikbaar

1. Doe het zelfde voor de uitbreiding van de Dienst van identiteitskaart van het Experience Cloud, aangezien u dat niet meer nodig zult hebben. De extensie Web SDK handelt de id af en u hebt dus geen extra extensie nodig.
1. Doe het zelfde voor andere uitbreidingen die met de uitbreiding van Adobe Analytics worden geassocieerd, maar slechts nadat u de noodzakelijke migratieveranderingen hebt aangebracht.
1. Bouw de veranderingen in uw ontwikkelomgeving.


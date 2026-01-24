---
title: De migratie plannen - De Adobe Target-implementatie in uw mobiele app migreren naar de Offer Decisioning- en Target-extensie
description: Ontdek de belangrijkste verschillen tussen at.js en Platform Web SDK en hoe u uw migratie-inspanning kunt plannen.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# De migratie plannen

De mate van inspanning om van de uitbreiding van het Doel aan de uitbreiding van Offer Decisioning en van het Doel te migreren hangt van de ingewikkeldheid van uw huidige implementatie en gebruikte eigenschappen van het Doel af.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie en bepaal een migratiebenadering
1. De eerste componenten instellen om verbinding te maken met de Adobe Experience Platform Edge Network
1. Werk de fundamentele implementatie bij om de uitbreiding van het Doel met Offer Decisioning en de uitbreiding van het Doel te vervangen
1. Verbeter de implementatie van SDK optimaliseren voor uw specifieke gebruiksgevallen. Dit kan het doorgeven van extra parameters, het gebruiken van reactietokens, en meer impliceren.
1. Objecten in de interface Doel bijwerken, zoals profielscripts, activiteiten en publieksdefinities
1. Valideer de definitieve implementatie alvorens de schakelaar in uw productieapp te maken

>[!INFO]
>
>In het ecosysteem van Adobe Experience Platform Mobile SDK worden extensies geïmplementeerd door SDK&#39;s die zijn geïmporteerd in uw toepassingen en die verschillende namen kunnen hebben:
>
> * **SDK van het Doel** voert de **uitbreiding van Adobe Target** uit
> * **optimaliseer SDK** voert **Offer Decisioning en de uitbreiding van het Doel** uit


Daarna, herzie de gedetailleerde [&#x200B; vergelijking van de uitbreiding van het Doel en de uitbreiding van Offer Decisioning en van het Doel &#x200B;](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de doelextensie naar de Offer Decisioning en de doelextensie. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=nl#M625) te posten.

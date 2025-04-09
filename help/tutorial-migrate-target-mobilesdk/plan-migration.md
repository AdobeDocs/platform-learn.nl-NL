---
title: De migratie plannen - De Adobe Target-implementatie in uw mobiele app migreren naar de Adobe Journey Optimizer - De beslissingsextensie
description: Ontdek de belangrijkste verschillen tussen at.js en Platform Web SDK en hoe u uw migratie-inspanning kunt plannen.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: 2ebad2014d4c29a50af82328735258958893b42c
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# De migratie plannen

Het niveau van inspanning om van de uitbreiding van het Doel aan de uitbreiding van het Besluit te migreren hangt van de ingewikkeldheid van uw huidige implementatie en gebruikte eigenschappen van het Doel af.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie en bepaal een migratiebenadering
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


Daarna, herzie de gedetailleerde [ vergelijking van de uitbreiding van het Doel en de Decisioning uitbreiding ](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) te posten.

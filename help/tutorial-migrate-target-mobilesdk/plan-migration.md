---
title: De migratie plannen - migreren van de Adobe Target naar de Adobe Journey Optimizer - Mobiele extensie kiezen
description: Ontdek de belangrijkste verschillen tussen at.js en Platform Web SDK en hoe u uw migratie-inspanning kunt plannen.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
source-git-commit: f3fd5f45412900dcb871bc0b346ce89108fa8913
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# De migratie plannen

Het niveau van inspanning om van de uitbreiding van het Doel aan de uitbreiding van het Besluit te migreren hangt van de ingewikkeldheid van uw huidige implementatie en producteigenschappen af die worden gebruikt.

Hoe eenvoudig of complex uw implementatie ook is, het is belangrijk dat u de huidige status volledig begrijpt voordat u gaat migreren. Deze gids helpt u om de componenten van uw huidige implementatie te breken en een handelbaar plan te ontwikkelen om elk stuk te migreren.

Het migratieproces omvat de volgende belangrijke stappen:

1. Evalueer uw huidige implementatie en bepaal een migratiebenadering
1. De eerste componenten instellen voor verbinding met de Adobe Experience Platform-Edge Network
1. Werk de fundamentele implementatie bij om de uitbreiding van het Doel en de Decisioning uitbreiding te vervangen
1. Verbeter de implementatie van SDK optimaliseren voor uw specifieke gebruiksgevallen. Dit kan het doorgeven van extra parameters, het gebruiken van reactietokens, en meer impliceren.
1. Objecten in de interface Doel bijwerken, zoals profielscripts, activiteiten en publieksdefinities
1. Valideer de definitieve implementatie alvorens de schakelaar in uw productiemilieu te maken

## Belangrijkste verschillen tussen de extensie Doel en de extensie Beslissing

Alvorens het migratieproces te beginnen, is het belangrijk om de verschillen tussen de uitbreiding van het Doel en de uitbreiding van het Beslissen te begrijpen.

### Operationele verschillen

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Proces | Wijzigingen in een doelimplementatie kunnen plaatsvinden na een proces dat andere eisen stelt aan de snelheid of kwaliteit van de kwaliteit in vergelijking met andere toepassingen, zoals Analytics. | Bij wijzigingen in een implementatie van een beslissingsextensie moeten alle downstreamtoepassingen in aanmerking worden genomen en moet het kwaliteitscontroleproces en het publicatieproces dienovereenkomstig worden aangepast. |
| Collaboration | De gegevens specifiek voor Doel kunnen direct in de vraag van het Doel worden overgegaan. Als Doel-rapportagebron Adobe Analytics is, kunnen gegevens die specifiek zijn voor Doel ook worden doorgegeven aan Adobe Analytics wanneer de juiste traceermethoden in de doelextensie worden aangeroepen voor weergave en interactie van Target-inhoud. | Gegevens die in de vraag van de de uitbreidingsuitbreiding van het Besluit worden overgegaan kunnen aan zowel Doel als Analytics worden door:sturen als het Doel rapporteringsbron Adobe Analytics is, wordt Adobe Analytics toegelaten in de gegevensstroom, en de aangewezen volgende methodes in de uitbreiding van het Beslissen worden geroepen wanneer de inhoud van het Doel wordt getoond en met interactie heeft. |

### Technische verschillen

| | Doelextensie | Decisitie-extensie |
|---|---|---|
| Afhankelijkheden | Alleen afhankelijk van Mobile Core SDK | Afhankelijk van de Mobile Core en Edge Network SDK |
| Bibliotheekfunctionaliteit | Ondersteunt het ophalen van inhoud van alleen Adobe Target | Inhoud ophalen van Adobe Target en Offer decisioning |
| Verzoeken | De vraag van het doel is grotendeels onafhankelijk van andere netwerkvraag | De het netwerkvraag van het doel wordt een rij gevormd samen met netwerkvraag naar andere op Edge-Gebaseerde oplossingen zoals Overseinen in Edge SDK en serieel uitgevoerd. |
| Edge Network | Gebruikt de waarde van de server van het Doel of de Edge Network van Adobe Experience Cloud met de cliëntcode (clientcode.tt.omtrdc.net), beide gespecificeerd in de [ configuratie van het Doel ](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in de Inzameling UI van Gegevens | Gebruikt het het netwerkdomein van Edge dat in de configuratie van de Edge Network van Adobe Experience Platform [ ](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) in de inzameling UI van Gegevens wordt gespecificeerd. |
| Standaardterminologie | mbox, TargetParameters | DecisionScope, Map (Android)/dictionary (iOS) voor doelparameters |
| Standaardinhoud | Staat het overgaan van cliënt-kant standaardinhoud in TargetRequest toe die is teruggekeerd als de netwerkvraag ontbreekt of in fout resulteert. | Hiermee wordt het doorgeven van standaardinhoud aan de clientzijde niet toegestaan. Retourneert geen inhoud als de netwerkaanroep mislukt of als er een fout optreedt. |
| Doelparameters | Hiermee worden algemene TargetParameters per aanvraag en verschillende TargetParameters per mbox doorgegeven | Staat het overgaan van globale TargetParameters per slechts verzoek toe |

Daarna, herzie de gedetailleerde [ vergelijking van de uitbreiding van het Doel en de Decisioning uitbreiding ](detailed-comparison.md) om een beter inzicht in de technische verschillen te krijgen en gebieden te identificeren die extra nadruk vereisen.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

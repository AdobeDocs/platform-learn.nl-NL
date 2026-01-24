---
title: Vergelijking van de extensie Doel met de extensie Offer Decisioning en Target
description: Leer meer over de verschillen tussen de extensie Target voor de Offer Decisioning en de extensie Target, zoals functies, instellingen en gegevensstroom.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Vergelijking van de extensie Doel met de extensie Offer Decisioning en Target

De extensie Offer Decisioning en Target verschilt van de extensie Adobe Target voor mobiele apps. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie van de uitbreiding van het Doel, zou u het volgende moeten kunnen begrijpen:

- Welke doelfuncties door Offer Decisioning en Target worden ondersteund
- Welke Adobe Target-uitbreidingsfuncties hebben Offer Decisioning- en Target-equivalenten
- Hoe de montages van het Doel met Offer Decisioning en Doel worden toegepast
- De gegevensstromen met de extensie Offer Decisioning en Target

## Operationele verschillen

| | Doelextensie | Offer Decisioning en Target-extensie |
|---|---|---|
| Proces | Wijzigingen in een doelimplementatie kunnen plaatsvinden na een proces dat andere eisen stelt aan de snelheid of kwaliteit van de kwaliteit in vergelijking met andere toepassingen, zoals Analytics. | Bij wijzigingen in een Offer Decisioning- en Target-extensie-implementatie moeten alle downstreamtoepassingen in aanmerking worden genomen en moet het kwaliteitscontroleproces en het publicatieproces dienovereenkomstig worden aangepast. |
| Collaboration | De gegevens specifiek voor Doel kunnen direct in de vraag van het Doel worden overgegaan. Als het Doel rapporteringsbron Adobe Analytics (A4T) is, kunnen de gegevens specifiek voor Doel ook aan Adobe Analytics worden overgegaan wanneer de aangewezen het volgen methodes in de uitbreiding van het Doel voor de inhoudvertoning en interactie van het Doel worden geroepen. | Gegevens die in de Offer Decisioning en de uitbreidingsvraag van het Doel worden overgegaan kunnen aan zowel Doel als Analytics door:sturen als het Doel rapporteringsbron Adobe Analytics (A4T) is, Adobe Analytics wordt toegelaten in de gegevensstroom, en de aangewezen het volgen methodes in Offer Decisioning en de uitbreiding van het Doel worden geroepen wanneer de inhoud van het Doel wordt getoond en met interactie gecommuniceerd. |

## Basisverschillen

| | Doelextensie | Offer Decisioning en Target-extensie |
|---|---|---|
| Afhankelijkheden | Alleen afhankelijk van Mobile Core SDK | Afhankelijk van de Mobile Core en Edge Network SDK |
| Bibliotheekfunctionaliteit | Ondersteunt het ophalen van inhoud van alleen Adobe Target | Ondersteuning voor het ophalen van inhoud van Adobe Target en de beslissing over aanbiedingen |
| Verzoeken | De vraag van het doel is grotendeels onafhankelijk van andere netwerkvraag | De het netwerkvraag van het doel wordt een rij gevormd samen met netwerkvraag naar andere op Edge-Gebaseerde oplossingen zoals Overseinen in Edge SDK en serieel uitgevoerd. |
| Edge Network | Gebruikt de de serverwaarde van het Doel of Adobe Experience Cloud Edge Network met de cliëntcode (clientcode.tt.omtrdc.net), allebei die in de [&#x200B; configuratie van het Doel &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in de Inzameling UI van Gegevens wordt gespecificeerd | Gebruikt het het netwerkdomein van Edge in de configuratie van Adobe Experience Platform [&#x200B; wordt gespecificeerd Edge Network &#x200B;](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) in de inzameling UI die van Gegevens. |
| Standaardterminologie | mbox, TargetParameters | DecisionScope, Map (Android)/dictionary (iOS) voor Target-parameters |
| Standaardinhoud | Staat het overgaan van cliënt-kant standaardinhoud in TargetRequest toe die is teruggekeerd als de netwerkvraag ontbreekt of in fout resulteert. | Hiermee wordt het doorgeven van standaardinhoud aan de clientzijde niet toegestaan. Retourneert geen inhoud als de netwerkaanroep mislukt of als er een fout optreedt. |
| Doelparameters | Hiermee worden algemene TargetParameters per aanvraag en verschillende TargetParameters per mbox doorgegeven | Staat het overgaan van globale TargetParameters per slechts verzoek toe |



## Functievergelijking

| Functie | Doelextensie | Offer Decisioning and Target extension (Target via Edge) |
|---|---|---|
| Prefetmodus | Ondersteund | Ondersteund |
| Uitvoeren, modus | Ondersteund | Niet ondersteund |
| Aangepaste parameters | Ondersteund | Ondersteund* |
| Profielparameters | Ondersteund | Ondersteund* |
| Parameters entiteit | Ondersteund | Ondersteund* |
| Doelpubliek | Ondersteund | Ondersteund |
| Real-Time CDP-publiek | Niet ondersteund | Ondersteund |
| Real-Time CDP-kenmerken | Niet ondersteund | Ondersteund |
| Levenscycluswaarden | Ondersteund | Ondersteund via regels voor gegevensverzameling |
| thirdPartyId (mbox3rdPartyId) | Ondersteund | Ondersteund via Identity Map en Target Third Party ID Namespace in de gegevensstroom |
| Meldingen (weergeven, klikken) | Ondersteund | Ondersteund |
| Reactietokens | Ondersteund | Ondersteund |
| Mobiele voorvertoningen (QA-modus) | Ondersteund | Beperkte ondersteuning voor Assurance |

>[!IMPORTANT]
>
> \* De parameters die in een verzoek worden verzonden zijn op alle werkingsgebied in het verzoek van toepassing. Als u verschillende parameters voor verschillende werkingsgebieden moet plaatsen, moet u extra verzoeken doen.



## Aanbiedingswaardige callouts

>[!NOTE]
>
>Zorg dat de configuratie en instellingen van de tags voor de extensie Doel op de juiste plaats blijven staan, zelfs nadat u uw toepassingscode hebt gemigreerd naar de Offer Decisioning- en Target-extensie. Hierdoor blijft Target werken voor klanten die de app nog niet naar de nieuwe versie hebben bijgewerkt.
>
>Als u Analytics for Target integration (A4T) gebruikt, moet u ook uw Analytics-implementatie migreren met de Edge Bridge-extensie en tegelijkertijd uw Target-implementatie migreren naar de Offer Decisioning- en Target-extensie.





>[!IMPORTANT]
>
> Houd de extensie-instellingen voor Doel op de plaats, zelfs nadat u uw toepassingscode hebt gemigreerd naar de Offer Decisioning- en Target-extensie. Zo blijft Target werken voor gebruikers die hun app nog niet hebben bijgewerkt.

## Schema voor Offer Decisioning- en Target-extensiesystemen

Het volgende diagram zou u moeten helpen de gegevensstroom begrijpen gebruikend de uitbreiding van Offer Decisioning en van het Doel.

![&#x200B; Adobe Target Edge die met cliënt-kant Mobiele SDK &#x200B;](assets/diagram.png) beslist


>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de doelextensie naar de Offer Decisioning en de doelextensie. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484?profile.language=nl#M625) te posten.

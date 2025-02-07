---
title: Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding
description: Leer over de verschillen tussen de uitbreiding van het Doel aan de uitbreiding van het Besluit met inbegrip van eigenschappen, functies, montages, en gegevensstroom.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: cb08ad8a1ffd687d7748ca02643b11b2243cd1a7
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 0%

---

# Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding

De Adobe Journey Optimizer - beslissingsextensie verschilt van de Adobe Target-extensie voor mobiele apps. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie van de uitbreiding van het Doel, zou u het volgende moeten kunnen begrijpen:

- Welke doelfuncties door Adobe Journey Optimizer worden ondersteund - Beslissing
- Welke Adobe Target-extensiefuncties hebben Adobe Journey Optimizer-beslissingsequivalenten
- Hoe de montages van het Doel met Adobe Journey Optimizer worden toegepast - Beslissing
- Hoe de gegevens stromen gebruikend Adobe Journey Optimizer - Beslissende uitbreiding

## Operationele verschillen

| | Doelextensie | Decisitie-extensie |
|---|---|---|
| Proces | Wijzigingen in een doelimplementatie kunnen plaatsvinden na een proces dat andere eisen stelt aan de snelheid of kwaliteit van de kwaliteit in vergelijking met andere toepassingen, zoals Analytics. | Bij wijzigingen in een implementatie van een beslissingsextensie moeten alle downstreamtoepassingen in aanmerking worden genomen en moet het kwaliteitscontroleproces en het publicatieproces dienovereenkomstig worden aangepast. |
| Collaboration | De gegevens specifiek voor Doel kunnen direct in de vraag van het Doel worden overgegaan. Als het Doel rapporteringsbron Adobe Analytics (A4T) is, kunnen de gegevens specifiek voor Doel ook aan Adobe Analytics worden overgegaan wanneer de aangewezen het volgen methodes in de uitbreiding van het Doel voor de inhoudvertoning en interactie van het Doel worden geroepen. | De gegevens die in de de uitbreidingsvraag van het Beslissen worden overgegaan kunnen aan zowel Doel als Analytics worden door:sturen als het Doel rapporteringsbron Adobe Analytics (A4T) is, wordt Adobe Analytics toegelaten in de gegevensstroom, en de aangewezen volgende methodes in de uitbreiding van het Beslissen worden geroepen wanneer de inhoud van het Doel wordt getoond en met interactie heeft. |

## Basisverschillen

| | Doelextensie | Decisitie-extensie |
|---|---|---|
| Afhankelijkheden | Alleen afhankelijk van Mobile Core SDK | Afhankelijk van de Mobile Core en Edge Network SDK |
| Bibliotheekfunctionaliteit | Ondersteunt het ophalen van inhoud van alleen Adobe Target | Inhoud ophalen van Adobe Target en Offer decisioning |
| Verzoeken | De vraag van het doel is grotendeels onafhankelijk van andere netwerkvraag | De het netwerkvraag van het doel wordt een rij gevormd samen met netwerkvraag naar andere op Edge-Gebaseerde oplossingen zoals Overseinen in Edge SDK en serieel uitgevoerd. |
| Edge Network | Gebruikt de waarde van de server van het Doel of de Edge Network van Adobe Experience Cloud met de cliëntcode (clientcode.tt.omtrdc.net), beide gespecificeerd in de [ configuratie van het Doel ](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in de Inzameling UI van Gegevens | Gebruikt het het netwerkdomein van Edge dat in de configuratie van de Edge Network van Adobe Experience Platform [ ](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) in de inzameling UI van Gegevens wordt gespecificeerd. |
| Standaardterminologie | mbox, TargetParameters | DecisionScope, Map (Android)/dictionary (iOS) voor Target-parameters |
| Standaardinhoud | Staat het overgaan van cliënt-kant standaardinhoud in TargetRequest toe die is teruggekeerd als de netwerkvraag ontbreekt of in fout resulteert. | Hiermee wordt het doorgeven van standaardinhoud aan de clientzijde niet toegestaan. Retourneert geen inhoud als de netwerkaanroep mislukt of als er een fout optreedt. |
| Doelparameters | Hiermee worden algemene TargetParameters per aanvraag en verschillende TargetParameters per mbox doorgegeven | Staat het overgaan van globale TargetParameters per slechts verzoek toe |



## Functievergelijking

| Functie | Doelextensie | Decisioning-extensie (Doel via Edge) |
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
| Analyses voor doel (A4T) | Alleen client | Client en server |
| Mobiele voorvertoningen (QA-modus) | Ondersteund | Beperkte ondersteuning voor Assurance |

>[!IMPORTANT]
>
> \* De parameters die in een verzoek worden verzonden zijn op alle werkingsgebied in het verzoek van toepassing. Als u verschillende parameters voor verschillende werkingsgebieden moet plaatsen, moet u extra verzoeken doen.



## Aanbiedingswaardige callouts

>[!NOTE]
>
>Houd de configuratie en de instellingen van de tags voor de extensie Doel op zijn plaats, zelfs nadat u uw toepassingscode hebt gemigreerd naar de extensie Decisioning. Hierdoor blijft Target werken voor klanten die de app nog niet naar de nieuwe versie hebben bijgewerkt.
>
>Als u Analytics voor de integratie van het Doel (A4T) gebruikt, ben zeker ook om uw implementatie Analytics met de uitbreiding van Edge Bridge tezelfdertijd te migreren u uw implementatie van het Doel aan de uitbreiding van het Beslissen migreert.

## Doelextensiefuncties en equivalente beslissingsextensies

Vele functies van de uitbreiding van het Doel hebben een gelijkwaardige benadering gebruikend de uitbreiding van het Besluit die in de lijst hieronder wordt geschetst. Voor meer details over de [ functies ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), verwijs naar de Gids van de Ontwikkelaar van Adobe Target.

| Doelextensie | Decisitie-extensie | Notities |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  |
| `retrieveLocationContent` | `getPropositions` | Wanneer u de API van `getPropositions` gebruikt, wordt geen externe aanroep gemaakt om niet-caching-bereik op te halen in de SDK. |
| `displayedLocations` | Voorstel -> `displayed()` | Daarnaast kan de methode `generateDisplayInteractionXdm` Offer worden gebruikt om de XDM voor itemweergave te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| `clickedLocation` | Voorstel -> `tapped()` | Daarnaast kan de methode `generateTapInteractionXdm` Aanbieding worden gebruikt om de XDM voor het tikken van items te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| `clearPrefetchCache` | `clearCachedPropositions` |  |
| `resetExperience` | nvt | Gebruik de API `removeIdentity` van Identity voor Edge Network-extensie voor de SDK om te stoppen met het verzenden van de bezoeker-id naar het Edge-netwerk. Voor meer details, zie [ de removeIdentity API documentatie ](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br> Nota: De `resetIdentities` API van de Mobiele Kern ontruimt alle opgeslagen identiteiten in SDK, met inbegrip van Experience Cloud identiteitskaart (ECID) en het zou spaarzaam moeten worden gebruikt! |
| `getSessionId` | nvt | `state:store` reactiehandgreep bevat informatie over sessies. De Edge-netwerkextensie helpt het te beheren door items in een niet-verlopen frameopslag aan volgende aanvragen toe te voegen. |
| `setSessionId` | nvt | `state:store` reactiehandgreep bevat informatie over sessies. De Edge-netwerkextensie helpt het te beheren door items in een niet-verlopen frameopslag aan volgende aanvragen toe te voegen. |
| `getThirdPartyId` | nvt | Gebruik de updateIdentities-API van Identity voor de extensie Edge Network om de waarde van de id van derden op te geven. Dan, vorm derde identiteitskaart namespace in de datastream. Voor meer details, zie [ de mobiele documentatie van Identiteitskaart van de Derde van het Doel ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| `setThirdPartyId` | nvt | Gebruik de updateIdentities-API van Identity voor de extensie Edge Network om de waarde van de id van derden op te geven. Dan, vorm derde identiteitskaart namespace in de datastream. Voor meer details, zie [ de mobiele documentatie van Identiteitskaart van de Derde van het Doel ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| `getTntId` | nvt | `locationHint:result` reactiehandgreep bevat de informatie over de doellocatiehint. Aangenomen wordt dat Target edge zich op dezelfde locatie bevindt als Experience Edge. <br> <br> het netwerkuitbreiding van Edge gebruikt de het plaatswenk van EdgeNetwork om de het netwerkcluster van Edge te bepalen om verzoeken naar te verzenden. Als u Edge-netwerklocatiehint wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` - en `setLocationHint` -API&#39;s van Edge Network-extensie. Voor meer details, zie [ de `getLocationHint` API documentatie ](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| `setTntId` | nvt | `locationHint:result` reactiehandgreep bevat de informatie over de doellocatiehint. Aangenomen wordt dat Target edge zich op dezelfde locatie bevindt als Experience Edge. <br> <br> het netwerkuitbreiding van Edge gebruikt de het plaatswenk van EdgeNetwork om de het netwerkcluster van Edge te bepalen om verzoeken naar te verzenden. Als u Edge-netwerklocatiehint wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` - en `setLocationHint` -API&#39;s van Edge Network-extensie. Voor meer details, zie [ de `getLocationHint` API documentatie ](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |

## Instellingen voor doelextensies en equivalente beslissingsextensies

De uitbreiding van het Doel heeft [ configureerbare montages ](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) die [ in de datastream ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup) met de Decisioning uitbreiding worden gevormd.

| Doelextensie | Decisitie-extensie | Notities |
| --- | --- | --- | 
| Clientcode | nvt | Automatisch aan de rand instellen met de details van de IMS-organisatie |
| Milieu-id | Id van doelomgeving | Gevormd in de datastream |
| Doel Workspace-eigenschap | Eigenschapstoken | Gevormd in de datastream |
| Time-out | Niet configureerbaar | De onderbreking met de uitbreiding van het Beslissen is 10 seconden |
| Serverdomein | Edge Network-domein | Instellen in de extensie Adobe Experience Platform Edge Network |

>[!IMPORTANT]
>
> Houd de instellingen voor de extensie Doel op zijn plaats, zelfs nadat u uw toepassingscode hebt gemigreerd naar de extensie Decisioning. Zo blijft Target werken voor gebruikers die hun app nog niet hebben bijgewerkt.

## Schema voor extensiesysteem voor besluitvorming

Het volgende diagram zou u moeten helpen de gegevensstroom begrijpen gebruikend Adobe Journey Optimizer - Beslissende uitbreiding.

![ Adobe Target Edge die met cliënt-kant Mobiele SDK ](assets/diagram.png) beslist


>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

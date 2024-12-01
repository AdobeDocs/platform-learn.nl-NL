---
title: Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding
description: Leer over de verschillen tussen de uitbreiding van het Doel aan de uitbreiding van het Besluit met inbegrip van eigenschappen, functies, montages, en gegevensstroom.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
source-git-commit: 8e4e23413c842f84159891287d09e8a6cfbbbc53
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Vergelijking van de uitbreiding van het Doel met de Decisioning uitbreiding

De Adobe Journey Optimizer - beslissingsextensie verschilt van de Adobe Target-extensie voor mobiele apps. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie van de uitbreiding van het Doel, zou u het volgende moeten kunnen begrijpen:

- Welke doelfuncties door Adobe Journey Optimizer worden ondersteund - Beslissing
- Welke Adobe Target-extensiefuncties hebben Adobe Journey Optimizer-beslissingsequivalenten
- Hoe de montages van het Doel met Adobe Journey Optimizer worden toegepast - Beslissing
- Hoe de gegevens stromen gebruikend Adobe Journey Optimizer - Beslissende uitbreiding


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
| `retrieveLocationContent` | `getPropositions` | Wanneer u de `getPropositions` API gebruikt, wordt geen externe aanroep uitgevoerd om niet-caching bereik op te halen in de SDK. |
| `displayedLocations` | Voorstel -> `displayed()` | Daarnaast kan de methode `generateDisplayInteractionXdm` Offer worden gebruikt om de XDM voor itemweergave te genereren. Vervolgens kan de sendEvent-API van de SDK van het Edge-netwerk worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| `clickedLocation` | Voorstel -> `tapped()` | Daarnaast kan de methode `generateTapInteractionXdm` Aanbieding worden gebruikt om de XDM voor het tikken van items te genereren. Vervolgens kan de sendEvent-API van de SDK van het Edge-netwerk worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
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

![ Adobe Target Edge die met cliënt-kant Mobiele SDK besluit ](assets/diagram.png)


>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

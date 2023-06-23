---
title: Denk na bewegend verkopermarkeringen aan gebeurtenis door:sturen
description: Leer hoe u een client-side leverancierstag voor gegevensdistributie op de server evalueert.
feature: Event Forwarding, Tags, Integrations
solution: Data Collection
jira: KT-9921
level: Intermediate, Experienced
role: Admin, Developer, Architect
exl-id: f8fd351a-435c-4cc1-b987-ed2ead20d4d6
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 1%

---

# Overweeg client-side leverancierstags naar gebeurtenis door:sturen

Er zijn verschillende dwingende redenen om te overwegen tags van leveranciers aan de clientzijde uit browsers en apparaten en naar een server te verplaatsen. In dit artikel, bespreken wij hoe te om een cliënt-zijverkopersmarkering voor potentieel het bewegen van het naar een gebeurtenis te evalueren die bezit door:sturen.

Deze evaluatie is slechts noodzakelijk als u overweegt verwijderend een cliënt-zijverkopersmarkering en het te vervangen met server-zijgegevensdistributie in een gebeurtenis die bezit door:sturen. In dit artikel wordt ervan uitgegaan dat u bekend bent met de basisbeginselen van [gegevensverzameling](https://experienceleague.adobe.com/docs/data-collection.html), en [gebeurtenis doorsturen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html).

>[!NOTE]
>
>Adobe Experience Platform Launch is omgedoopt tot een reeks technologieën voor gegevensverzameling in Adobe Experience Platform. Diverse terminologische wijzigingen zijn als gevolg hiervan in de productdocumentatie doorgevoerd. Raadpleeg het volgende [document](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html) voor een geconsolideerde referentie van de terminologische wijzigingen.

Browser de verkopers veranderen hoe zij derdekoekjes behandelen. Adverteer- en marketingleveranciers en -technologieën vereisen vaak het gebruik van vele tags aan de clientzijde. Deze uitdagingen zijn slechts twee dwingende redenen dat onze klanten server-zijgegevensdistributie toevoegen.

>[!NOTE]
>
>`Tag` in dit artikel wordt onder clientcode verstaan, meestal JavaScript van een leverancier die wordt gebruikt voor gegevensverzameling in de browser of het apparaat terwijl een bezoeker communiceert met de site of de app. `Website` of `site` Hier wordt verwezen naar een website, een webtoepassing of een toepassing voor een mobiel apparaat. Een &quot;tag&quot; voor deze doeleinden wordt ook vaak een pixel genoemd.

## Gebruik gevallen en gegevens {#use-cases-data}

De eerste stap bestaat uit het definiëren van de gebruiksgevallen die worden geïmplementeerd met de client-side leverancierstag. Neem bijvoorbeeld de Facebook-pixel (Meta). Het van onze site naar de [Facebook Conversies-API](https://exchange.adobe.com/apps/ec/105509/facebook-conversions-api-extension) met de door:sturen uitbreiding van de gebeurtenis betekent het documenteren van de specifieke gebruiksgevallen eerst.

Voor de huidige clientleveranciercode:

- Welke specifieke gebeurtenis en andere gegevenspunten worden blootgesteld en tot de cliënt-zijmarkering overgegaan?
- Wanneer en waar vindt die gegevensoverdracht plaats?

Het is nuttig om een lijst, spreadsheet, diagram, of ander verslag van de gegevens en de opeenvolging van gebeurtenissen te maken om deze evaluatie te documenteren - zelfs als het slechts voor uw eigen gebruik is. Ben zeker om etiketten voor gegevensbronnen-waar te omvatten het komt uit? Doelen—waar gaat het heen? En transformaties—wat gebeurt er tussen bron en doel?

In ons voorbeeld volgen we conversies met de Facebook-pixel wanneer bezoekers op onze site reageren nadat ze een Facebook-advertentie hebben bekeken. Ze kunnen ook met onze site communiceren nadat ze verwante advertenties op een ander sociaal platform hebben bekeken. Om deze omzettingen in de reclamemiddelen en -rapporten van Facebook te kunnen zien, moeten de vereiste gegevens naar Facebook gaan. Deze gegevens kunnen conversiegebeurtenissen zoals downloads, registraties, zoals of aankopen bevatten.

### Gegevens {#data}

Met de bestaande client-side tag, wanneer deze wordt uitgevoerd of uitgevoerd op onze site, wat gebeurt er dan met de gegevens voor ons gebruik? Kunnen wij de gegevens vangen wij in de cliënt, zonder de verkoperstag nodig hebben, zodat kunnen wij het naar gebeurtenis verzenden die door:sturen? Wanneer u [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) Voor andere systemen voor tagbeheer zijn de meeste interactiegegevens van bezoekers beschikbaar voor verzameling en distributie. Maar zijn de gegevens die wij voor ons gebruiksgeval nodig hebben beschikbaar wanneer wij het nodig hebben, waar wij het, en in het formaat nodig hebben wij het-zonder de cliënt-zijverkoperstag nodig hebben? Hieronder volgen nog enkele vragen over de gegevens die u in overweging wilt nemen:

- Is er een gebruiker-id van de leverancier vereist met elke gebeurtenis?
- Zo ja, hoe kan het worden verzameld of gegenereerd zonder de client-side tag?
- Vereist de leverancier specifiek hun cliënt-zijcode bij runtime?
- Welke andere gegevens zijn vereist? Waar komen die gegevens vandaan?

De meeste client-side leverancierstags vereisen niet veel gegevenspunten voor een bepaald gebruiksgeval, maar het is handig om de gebruiksgevallen en de vereiste gegevens tijdens deze evaluaties te noteren.

## Leverancier-API&#39;s {#vendor-apis}

Nu kennen we de specifieke te implementeren gebruiksgevallen, de vereiste gegevens en de volgorde van gebeurtenissen van bron tot bestemming. Om te bepalen als het gebruiksgeval geschikt voor gebeurtenis het door:sturen is, kunnen wij de verkoper API details nu onderzoeken.

>[!IMPORTANT]
>
>Hoewel veel leveranciers API&#39;s inschakelen voor server-naar-server-overdracht, zijn er ook veel die momenteel geen API&#39;s hebben die geschikt zijn voor deze doeleinden.

### API&#39;s onderzoeken {#investigate-apis}

Hier volgen enkele stappen die we kunnen uitvoeren om de eindpunten van de API van leveranciers te onderzoeken.

Beschikt de leverancier over API&#39;s die zijn ontworpen voor overdracht van gebeurtenisgegevens van server naar server? Zoek eerst de vereisten voor die specifieke API-eindpunten:

- Bestaan de API eindpunten om de vereiste gegevens te verzenden? Raadpleeg de ontwikkelaar- of API-documentatie van de leverancier voor informatie over de eindpunten die uw gebruiksgevallen ondersteunen.
- Sta zij het stromen gebeurtenisgegevens, of slechts partijgegevens toe?
- Welke authentificatiemethodes steunen zij? Token, HTTP, OAuth versie van de cliëntgeloofsbrieven, of ander? Zie [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html) voor methodes die door gebeurtenis door:sturen worden gesteund.
- Wat is de vernieuwingsverschuiving van hun API? Is die beperking verenigbaar met de gebeurtenis die minima door:sturen? Details [hier](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
- Welke gegevens hebben zij voor de relevante eindpunten nodig?
- Vereisen zij een verkoper-specifiek gebruikersherkenningsteken met elke vraag aan het eindpunt?
- Als zij die herkenningsteken vereisen, waar en hoe kan het worden geproduceerd of worden gevangen, zonder cliënt-zijcode?

Met andere woorden:

- Levert de leverancier de API eindpunten die voor onze gebruiksgevallen worden vereist?
- Hebben zij een compatibele authentificatiemethode voor gebeurtenis het door:sturen?
- Kunnen wij tot alle gegevens toegang hebben die voor een gebeurtenis worden vereist die implementatie (of van de cliënt-kant, of van andere API vraag) door:sturen?

De markering is waarschijnlijk een goede kandidaat om zich van de cliënt aan onze servers in een gebeurtenis te bewegen die bezit door:sturen als wij ja op die vragen kunnen antwoorden.

Als de leverancier niet de API eindpunten heeft om onze gebruiksgevallen te steunen, dan duidelijk is die verkoperstag geen goede kandidaat voor het gebruiken van gebeurtenis door:sturen in plaats van de cliënt-zijverkoperstag.

Wat gebeurt er als ze API&#39;s hebben, maar ook een unieke bezoeker- of gebruikers-id nodig hebben voor elke API-aanroep? Hoe kunnen wij tot die identiteitskaart toegang hebben als wij niet de verkoper cliënt-zijcode (markering) hebben die op de plaats loopt?

Sommige leveranciers veranderen hun systemen voor de nieuwe wereld zonder derdekoekjes. Deze wijzigingen omvatten het gebruik van alternatieve unieke id&#39;s, zoals een [UUID](https://developer.mozilla.org/en-US/docs/Glossary/UUID) of andere [door klant gegenereerde id](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html). Als de verkoper een klant-geproduceerde identiteitskaart toestaat, kunnen wij of het van de cliënt naar het Netwerk van de Rand van het Platform met Web of Mobiele SDK verzenden, of het misschien krijgen van een API vraag in gebeurtenis het door:sturen. Wanneer wij gegevens naar die verkoper in een gebeurtenis verzenden die regel door:sturen, omvatten wij eenvoudig die herkenningsteken zoals-nodig.

Als de leverancier gegevens (zoals een leverancier-specifieke unieke identiteitskaart, bijvoorbeeld) vereist die slechts door hun eigen cliënt-zijmarkering kunnen worden geproduceerd of worden betreden, dan is die verkoperstag waarschijnlijk geen goede kandidaat om zich te bewegen. _Het wordt afgeraden om een client-side tag om te buigen met het idee om die gegevensverzameling te verplaatsen naar het doorsturen van gebeurtenissen zonder de juiste API&#39;s._

De [Adobe Experience Platform Cloud Connector](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html) met leveranciers die over de juiste API&#39;s beschikken voor gegevensoverdracht van server naar server, kan de extensie naar wens HTTP-aanvragen indienen. Terwijl verkoper-specifieke uitbreidingen aardig zijn om te hebben, en meer uitbreidingen zijn momenteel onder actieve ontwikkeling, kunnen wij gebeurtenis uitvoeren die regels vandaag gebruikend de uitbreiding van de Verbinding van de Wolk door:sturen, zonder op extra verkopersuitbreidingen te wachten.

## Tools {#tools}

Het onderzoeken van en het testen van leveranciers API eindpunten is gemakkelijker met hulpmiddelen zoals [Postman](https://www.postman.com/)of teksteditoruitbreidingen zoals Visual Studio Code [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), of [HTTP-client](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client).

## Volgende stappen {#next-steps}

Dit artikel verstrekte een opeenvolging van stappen om een verkoper cliënt-zijmarkering te evalueren en potentieel het server-kant in een gebeurtenis te bewegen die bezit door:sturen. Zie de volgende koppelingen voor meer informatie over verwante onderwerpen:

- [Tagbeheer](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) in Adobe Experience Platform
- [Gebeurtenis doorsturen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) voor verwerking op de server
- [Terminologie-updates](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html) in gegevensverzameling

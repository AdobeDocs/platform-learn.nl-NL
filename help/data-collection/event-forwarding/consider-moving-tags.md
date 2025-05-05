---
title: Denk na bewegend verkopermarkeringen aan gebeurtenis door:sturen
description: Leer hoe u een client-side leverancierstag voor gegevensdistributie op de server evalueert.
feature: Event Forwarding, Tags, Integrations
role: Admin, Developer, Architect, Data Engineer
level: Intermediate, Experienced
jira: KT-9921
exl-id: f8fd351a-435c-4cc1-b987-ed2ead20d4d6
source-git-commit: 7edf8fc46943ae2f1e6e2e20f4d589d7959310c8
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---

# Overweeg client-side leverancierstags naar gebeurtenis door:sturen

Er zijn verschillende dwingende redenen om te overwegen tags van leveranciers aan de clientzijde uit browsers en apparaten en naar een server te verplaatsen. In dit artikel, bespreken wij hoe te om een cliënt-zijverkopersmarkering voor potentieel het bewegen van het naar een gebeurtenis te evalueren die bezit door:sturen.

Deze evaluatie is slechts noodzakelijk als u overweegt verwijderend een cliënt-zijverkopersmarkering en het te vervangen met server-zijgegevensdistributie in een gebeurtenis die bezit door:sturen. Dit artikel veronderstelt u met de grondbeginselen van [ gegevensinzameling ](https://experienceleague.adobe.com/docs/data-collection.html?lang=nl-NL) vertrouwd bent, en [ gebeurtenis door:sturen ](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=nl-NL).

>[!NOTE]
>
>Adobe Experience Platform Launch is omgedoopt tot een reeks technologieën voor gegevensverzameling in Adobe Experience Platform. Diverse terminologische wijzigingen zijn als gevolg hiervan in de productdocumentatie doorgevoerd. Gelieve te verwijzen naar het volgende [ document ](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=nl-NL) voor een geconsolideerde verwijzing van de terminologieveranderingen.

Browser de verkopers veranderen hoe zij derdekoekjes behandelen. Advertising- en marketingleveranciers en -technologieën vereisen vaak het gebruik van veel tags aan de clientzijde. Deze uitdagingen zijn slechts twee dwingende redenen die onze klanten server-zijgegevensdistributie toevoegen.

>[!NOTE]
>
>`Tag` in dit artikel staat voor clientcode, meestal JavaScript van een leverancier die wordt gebruikt voor gegevensverzameling in de browser of het apparaat terwijl een bezoeker communiceert met de site of de app. `Website` of `site` hier verwijst naar een website, een webtoepassing of een toepassing voor een mobiel apparaat. Een &quot;tag&quot; voor deze doeleinden wordt ook vaak een pixel genoemd.

## Gebruik gevallen en gegevens {#use-cases-data}

De eerste stap bestaat uit het definiëren van de gebruiksgevallen die worden geïmplementeerd met de client-side leverancierstag. Neem bijvoorbeeld de Facebook-pixel (Meta). Bewegend het van onze plaats aan de [ Conversies API van Meta ](https://exchange.adobe.com/apps/ec/109168/meta-conversions-api) met de gebeurtenis door:sturen uitbreiding betekent het documenteren van de specifieke gebruiksgevallen eerst.

Voor de huidige clientleveranciercode:

- Welke specifieke gebeurtenis en andere gegevenspunten worden blootgesteld en tot de cliënt-zijmarkering overgegaan?
- Wanneer en waar vindt die gegevensoverdracht plaats?

Het is nuttig om een lijst, spreadsheet, diagram, of ander verslag van de gegevens en de opeenvolging van gebeurtenissen te maken om deze evaluatie te documenteren - zelfs als het slechts voor uw eigen gebruik is. Ben zeker om etiketten voor gegevensbronnen-waar te omvatten het komt uit? Doelen—waar gaat het heen? En transformaties—wat gebeurt er tussen bron en doel?

In ons voorbeeld volgen we conversies met de Facebook-pixel wanneer bezoekers op onze site reageren nadat ze een Facebook-advertentie hebben bekeken. Ze kunnen ook met onze site communiceren nadat ze verwante advertenties op een ander sociaal platform hebben bekeken. Om deze omzettingen in de reclamemiddelen en -rapporten van Facebook te kunnen zien, moeten de vereiste gegevens naar Facebook gaan. Deze gegevens kunnen conversiegebeurtenissen zoals downloads, registraties, zoals of aankopen bevatten.

### Gegevens {#data}

Met de bestaande client-side tag, wanneer deze wordt uitgevoerd of uitgevoerd op onze site, wat gebeurt er dan met de gegevens voor ons gebruik? Kunnen wij de gegevens vangen wij in de cliënt, zonder de verkoperstag nodig hebben, zodat kunnen wij het naar gebeurtenis verzenden die door:sturen? Wanneer het gebruiken van [ markeringen ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) of andere systemen van het markeringsbeheer, zijn de meeste gegevens van de bezoekersinteractie beschikbaar voor inzameling en distributie. Maar zijn de gegevens die wij voor ons gebruiksgeval nodig hebben beschikbaar wanneer wij het nodig hebben, waar wij het, en in het formaat nodig hebben wij het-zonder de cliënt-zijverkoperstag nodig hebben? Hieronder volgen nog enkele vragen over de gegevens die u in overweging wilt nemen:

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
- Welke authentificatiemethodes steunen zij? Token, HTTP, OAuth versie van de cliëntgeloofsbrieven, of ander? Zie [ hier ](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html?lang=nl-NL) voor methodes die door gebeurtenis door:sturen worden gesteund.
- Wat is de vernieuwingsverschuiving van hun API? Is die beperking verenigbaar met de gebeurtenis die minima door:sturen? Details [ hier ](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html?lang=nl-NL#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
- Welke gegevens hebben zij voor de relevante eindpunten nodig?
- Vereisen zij een verkoper-specifiek gebruikersherkenningsteken met elke vraag aan het eindpunt?
- Als zij die herkenningsteken vereisen, waar en hoe kan het worden geproduceerd of worden gevangen, zonder cliënt-zijcode?

Met andere woorden:

- Levert de leverancier de API eindpunten die voor onze gebruiksgevallen worden vereist?
- Hebben zij een compatibele authentificatiemethode voor gebeurtenis het door:sturen?
- Kunnen wij tot alle gegevens toegang hebben die voor een gebeurtenis worden vereist die implementatie (of van de cliënt-kant, of van andere API vraag) door:sturen?

De markering is waarschijnlijk een goede kandidaat om zich van de cliënt aan onze servers in een gebeurtenis te bewegen die bezit door:sturen als wij ja op die vragen kunnen antwoorden.

Als de leverancier niet de API eindpunten heeft om onze gebruiksgevallen te steunen, dan duidelijk is die verkoperstag geen goede kandidaat voor het gebruiken van gebeurtenis het door:sturen in plaats van de cliënt-zijverkoperstag.

Wat gebeurt er als ze API&#39;s hebben, maar ook een unieke bezoeker- of gebruikers-id nodig hebben voor elke API-aanroep? Hoe kunnen wij tot die identiteitskaart toegang hebben als wij niet de verkoper cliënt-zijcode (markering) hebben die op de plaats loopt?

Sommige leveranciers veranderen hun systemen voor de nieuwe wereld zonder derdekoekjes. Deze veranderingen omvatten het gebruik van alternatieve unieke herkenningstekens, als a [ UUID ](https://developer.mozilla.org/en-US/docs/Glossary/UUID) of andere [ klant-geproduceerde identiteitskaart ](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html?lang=nl-NL). Als de verkoper een klant-geproduceerde identiteitskaart toestaat, kunnen wij of het van de cliënt naar de Edge Network van het Platform met Web of Mobiele SDK verzenden, of misschien het van een API vraag in gebeurtenis krijgen door:sturen. Wanneer wij gegevens naar die verkoper in een gebeurtenis verzenden die regel door:sturen, omvatten wij eenvoudig die herkenningsteken zoals-nodig.

Als de leverancier gegevens (zoals een leverancier-specifieke unieke identiteitskaart, bijvoorbeeld) vereist die slechts door hun eigen cliënt-zijmarkering kunnen worden geproduceerd of worden betreden, dan is die verkoperstag waarschijnlijk geen goede kandidaat om zich te bewegen. _het proberen om een cliënt-zijmarkering met het idee om die gegevensinzameling aan gebeurtenis te bewegen die zonder aangewezen APIs door:sturen wordt ontmoedigd._

De [&#128279;](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html?lang=nl-NL) uitbreiding van de Schakelaar van de Wolk van Adobe Experience Platform  kan HTTP- verzoeken zoals-nodig met verkopers maken die aangewezen APIs voor server-aan-server overdracht van gebeurtenisgegevens hebben. Terwijl verkoper-specifieke uitbreidingen aardig zijn om te hebben, en meer uitbreidingen zijn momenteel onder actieve ontwikkeling, kunnen wij gebeurtenis uitvoeren die regels vandaag gebruikend de uitbreiding van de Verbinding van de Wolk door:sturen, zonder op extra verkopersuitbreidingen te wachten.

## Tools {#tools}

Het onderzoeken van en het testen van leveranciersAPI eindpunten is gemakkelijker met hulpmiddelen zoals [ Postman ](https://www.postman.com/), of de uitbreidingen van de tekstredacteur zoals de Code van Visual Studio [ Donder Cliënt ](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), of [ Cliënt van HTTP ](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client).

## Volgende stappen {#next-steps}

Dit artikel verstrekte een opeenvolging van stappen om een verkoper cliënt-zijmarkering te evalueren en potentieel het server-kant in een gebeurtenis te bewegen die bezit door:sturen. Zie de volgende koppelingen voor meer informatie over verwante onderwerpen:

- [ het beheer van de Markering ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) in Adobe Experience Platform
- [ Gebeurtenis door:sturen ](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=nl-NL) voor server-zij verwerking
- [ de updates van de Terminologie ](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=nl-NL) in gegevensinzameling

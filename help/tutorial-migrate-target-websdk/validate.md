---
title: Bevestig de implementaties van het Doel met Web SDK - Migreer Doel van at.js 2.x aan Web SDK
description: Leer hoe u activiteiten valideert en fouten opspoort in een Adobe Target-implementatie met de Adobe Experience Platform Web SDK.
exl-id: 09b4ebeb-fae9-470d-8ea9-f6e3c7d7da5e
source-git-commit: 070fc02801d3403bf65ca732323338481e25b581
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# Valideer de implementatie van het Web SDK van het Platform

Nadat u uw implementatie van het Doel van at.js aan het Web SDK van het Platform hebt gemigreerd, is het belangrijk om alles te bevestigen behoorlijk werkt alvorens om het even welke veranderingen in uw productiesite te publiceren. Adobe raadt het volgende aan, dat in detail op deze pagina wordt besproken:

* Voer een technische bevestiging uit om de basisimplementatie te verzekeren en de verzoeken en de antwoorden van SDK van het Web van het Platform van het Platform correct kijken
* Zorgen dat doelactiviteiten correct worden geleverd en weergegeven
* Controleren of rapporten correct werken
* Reviseer publiek en profielscripts om ervoor te zorgen dat deze compatibel zijn met Platform Web SDK
* Ervoor zorgen dat integratie met Adobe- of externe toepassingen correct werkt

Elke implementatie van het Doel is afhankelijk van de gebruikte sitearchitectuur en -functies. U kunt de onderstaande tabellen als beginpunt gebruiken en items toevoegen die uniek zijn voor uw implementatie. De [&#x200B; het Zuiveren pagina &#x200B;](debugging.md) van dit leerprogramma toont u hulpmiddelen u kunt gebruiken om met deze bevestiging te helpen.

## Technische validatie

| Validatie-item | Notities |
|---|---|
| Het voorverborgen fragment at.js is niet meer aanwezig op de pagina | De Platform Web SDK verwijdert niet automatisch de stijl met identiteitskaart `at-body-style`. Als u dit oude fragment op de pagina laat staan, resulteert dit in verborgen inhoud totdat de time-out van het fragment wordt bereikt. |
| De bibliotheek at.js is niet meer aanwezig op de pagina | Controleer of er geen &quot;adobe.target&quot;-object is in de console voor ontwikkelprogramma&#39;s van uw browser. Als zowel Platform Web SDK als at.js worden opgenomen, resulteert dit in onbedoeld rendergedrag |
| De verwachte parameters bevinden zich in de XDM- en gegevensobjecten van de `sendEvent` -aanvraag | |
| De catalogus met aanbevelingen wordt op de verwachte manier bijgewerkt als u paginaverzoeken gebruikt om de catalogus te vullen | |
| Profielparameters worden aan doel doorgegeven | Edge-sporen weergeven in Foutopsporing |
| Parameters die aan XDM in de datastream mapper worden toegewezen, worden correct aan Doel doorgegeven | Valideren met de functie Edge Trace van Foutopsporing en/of Assurance |
| Retourneert de doelinhoud in de toepasselijke `sendEvent` reacties | Wordt verwacht wanneer de optie `renderDecisions` is ingesteld op `true` of het bereik wordt aangevraagd en de gebruiker in aanmerking komt voor een bepaalde doelactiviteit |
| Een `decisioning.propositionDisplay` -gebeurtenis wordt geactiveerd nadat op VEC gebaseerde activiteiten zijn gerenderd | Van activiteiten die automatisch en op bestelling worden teruggegeven wordt verwacht dat ze afzonderlijke gebeurtenisaanroepen hebben |
| Een `decisioning.propositionDisplay` -gebeurtenis wordt geactiveerd nadat op formulieren gebaseerde activiteiten zijn gegenereerd | Alleen van toepassing op bepaalde implementaties. Vereist aangepaste code om deze aanroep uit te voeren. |
| De gebeurtenis `decisioning.propositionDisplay` wordt geactiveerd wanneer een aanbieding wordt toegepast op een wijziging in de SPA-weergave | Alleen van toepassing voor SPA-implementaties |
| Een `decisioning.propositionDisplay` -gebeurtenis wordt NIET geactiveerd wanneer een SPA-component voor een bepaalde weergave opnieuw wordt gerenderd | Alleen van toepassing voor SPA-implementaties |
| Een gebeurtenis `decisioning.propsitionInteract` wordt geactiveerd na een activiteitsconversie | Van &#39;Op een element klikken&#39; en aangepaste conversies die van at.js `trackEvent` of `sendNotifications` zijn gemigreerd, wordt verwacht dat ze aparte gebeurtenisaanroepen hebben |
| Responstokens worden geretourneerd in de reactie van `sendEvent` en hebben verwachte waarden | De tokens van de reactie zouden normaal met Web SDK moeten werken |
| ECID&#39;s zijn op pagina&#39;s consistent met Web SDK en at.js | Is van toepassing op paginamigraties. Van omleidingsaanbiedingen wordt niet verwacht dat ze in dit soort migraties werken |


## Activiteit leveren en renderen

| Validatie-item | Notities |
|---|---|
| Op VEC gebaseerde activiteiten worden correct weergegeven bij het laden van de pagina | U kunt het beste aangepaste codewijzigingen en basiswijzigingen valideren, zoals het opnieuw rangschikken van elementen of het vervangen van tekst |
| De op VEC-Gebaseerde activiteiten geven behoorlijk op de veranderingen van de mening van het KUUROORD terug | Alleen van toepassing voor SPA-implementaties |
| Op formulieren gebaseerde activiteiten worden correct weergegeven | Alleen van toepassing op bepaalde implementaties. Voor het weergeven van formuliergebaseerde activiteiten is aangepaste code vereist, vergelijkbaar met at.js. |
| Activiteiten die omleidingen gebruiken, werken naar behoren | Omleidingen worden ondersteund als zowel de bron- als de bestemmingspagina Platform Web SDK gebruiken. Een doel wordt omgeleid van een pagina at.js naar een SDK-pagina van het Web Platform of de omgekeerde manier wordt niet ondersteund. |
| De activiteiten die verre aanbiedingen gebruiken werken behoorlijk | Niet gebruikelijk, controleer uw aanbiedingen van het Doel voor Verre Aanbiedingen |
| Flikkering wordt op de juiste wijze beperkt | De flikkering is optioneel, maar zorg ervoor dat alle aanwezige mitigatietactieken naar behoren werken voor optimale paginaprestaties en gebruikerservaring. |
| QA-koppelingen werken naar verwachting | Als u dit niet doet, controleert u of de URL van web.webPageDetails.URL exact overeenkomt met de URL in de browser. |
| Al uw algemeen gebruikte aanbiedingstypes worden teruggegeven zoals verwacht |  |

## Rapportage

| Validatie-item | Notities |
|---|---|
| Bezoekers worden toegeschreven aan VEC-activiteiten | Het is best om het melden van werken zoals verwacht voor zowel de veranderingen van de paginading als de meningswijzigingen van het KUUROORD te bevestigen |
| Bezoekers worden toegeschreven aan op formulieren gebaseerde activiteiten | Afhankelijk van de gebruikte rendermethode kan het zijn dat uw implementatie aangepaste code nodig heeft om een `decisioning.propositionDisplay` -gebeurtenis uit te voeren |
| Standaardconversiedoelstellingen worden correct vastgelegd | Is op of Doel of Analyse als rapporteringsbron van toepassing |
| De omzettingen en details van bestellingen worden correct vastgelegd | Controleer het auditrapport |
| Conversies voor het bijhouden van klikken worden correct vastgelegd |  |
| Aangepaste conversiedoelstellingen worden correct vastgelegd | Conversiedoelen die bijvoorbeeld zijn gemigreerd van at.js `trackEvent` of `sendNotifications` en die veel worden gebruikt met het doel &#39;Een box weergeven&#39; |

## Scripts voor soorten publiek en profielen

| Validatie-item | Notities |
|---|---|
| Soorten publiek gebruikt in live activiteiten zijn compatibel met Platform Web SDK | Soorten publiek die de component &quot;Custom&quot; (mbox parameter) gebruiken, moeten worden bijgewerkt om XDM-kenmerken op te nemen |
| Alle profielscripts zijn compatibel met Platform Web SDK | Alle profielscripts die mbox-parameters gebruiken, moeten worden bijgewerkt om XDM-kenmerken op te nemen |
| Activiteitenrendement voor doelpubliek | Het is best om bevestiging van begin tot eind op publiek uit te voeren u wijzigt om compatibel met het Web SDK van het Platform te maken |
| Profielscripts worden geëvalueerd zoals verwacht | Edge-sporen weergeven in Foutopsporing |

## Integratie met Adobe-toepassingen

| Validatie-item | Notities |
|---|---|
| Rendement activiteiten voor Experience Cloud-publiek | Bijvoorbeeld een segment dat is gepubliceerd vanuit Adobe Analytics |
| Rendement activiteiten voor Experience Platform-publiek | Alleen van toepassing als u een licentie hebt voor een Experience Platform-toepassing zoals RTCDP |
| Rendement activiteiten voor Audience Manager-publiek | Bijvoorbeeld een segment dat is gebaseerd op het bezoeken van een specifieke pagina |
| Weergaven van doelactiviteitgegevens in Analysis Workspace | Is van toepassing op activiteiten die Adobe Analytics als bron van rapportage gebruiken |

## Integraties met toepassingen van derden

| Validatie-item | Notities |
|---|---|
| De het symbolische gegevens van de reactie worden behoorlijk overgegaan tot derdetoepassingen | De benaderingen van de integratie kunnen variëren, maar een gemeenschappelijke methode moet de tokens van de Reactie van het Doel gebruiken om activiteit en ervaringsinformatie tot andere analysehulpmiddelen zoals Google Analytics over te gaan |
| Informatie van derden wordt doorgegeven als XDM- of profielgegevens | Alle relevante informatie van derden moet worden doorgegeven in `sendEvent` -oproepen aan Target |

Na het uitvoeren van de bevestigingsstappen hierboven, kunt u erop vertrouwen dat de implementatie van het Web SDK van het Platform klaar is om aan productie te bewegen.

Daarna, leer hoe te [&#x200B; een implementatie van het Doel problemen oplossen gebruikend het Web SDK van het Platform &#x200B;](debugging.md).

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw doelmigratie van at.js naar Web SDK. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587?profile.language=nl#M463) te posten.

---
title: Bevestig de implementaties van het Doel met Web SDK | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe te om activiteiten te bevestigen en een implementatie van Adobe Target te zuiveren gebruikend het Web SDK van Adobe Experience Platform.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 0%

---

# Bevestig de implementatie van SDK van het Web van het Platform

Nadat u uw implementatie van het Doel van at.js aan het Web SDK van het Platform hebt gemigreerd, is het belangrijk om alles te bevestigen behoorlijk werkt alvorens om het even welke veranderingen in uw productiesite te publiceren. Adobe raadt het volgende aan, dat in detail op deze pagina wordt besproken:

* Voer een technische bevestiging uit om de basisimplementatie en de verzoeken en de antwoorden van SDK van het Web van het Platform te verzekeren correct kijken
* Zorgen dat doelactiviteiten correct worden geleverd en weergegeven
* Controleren of rapporten correct werken
* Reviseer publiek en profielmanuscripten om ervoor te zorgen zij met het Web SDK van het Platform compatibel zijn
* Ervoor zorgen dat integratie met Adobe- of externe toepassingen correct werkt

Elke implementatie van het Doel is afhankelijk van de gebruikte sitearchitectuur en -functies. U kunt de onderstaande tabellen als beginpunt gebruiken en items toevoegen die uniek zijn voor uw implementatie. De [Pagina met foutopsporing](debugging.md) In deze zelfstudie ziet u gereedschappen waarmee u deze validatie kunt gebruiken.

## Technische validatie

| Validatie-item | Notities |
|---|---|
| Het voorverborgen fragment at.js is niet meer aanwezig op de pagina | De Platform-web-SDK verwijdert de stijl niet automatisch met id `at-body-style`. Als u dit oude fragment op de pagina laat staan, resulteert dit in verborgen inhoud totdat de time-out van het fragment wordt bereikt. |
| De bibliotheek at.js is niet meer aanwezig op de pagina | Controleer of er geen &quot;adobe.target&quot;-object is in de console voor ontwikkelprogramma&#39;s van uw browser. Het opnemen van zowel Platform Web SDK als at.js resulteert in onbedoeld rendergedrag |
| De verwachte parameters zijn in XDM en gegevensvoorwerpen van `sendEvent` verzoek |  |
| De Recommendations-catalogus wordt naar behoren bijgewerkt als u paginaverzoeken gebruikt om de catalogus te vullen |  |
| Profielparameters worden aan doel doorgegeven | Edge-sporen weergeven in Foutopsporing |
| Parameters die aan XDM in de datastream mapper worden toegewezen, worden correct aan Doel doorgegeven | Valideren met de functie Edge Trace van Foutopsporing en/of Betrouwbaarheid |
| Retourneert doelinhoud in de toepasselijke `sendEvent` reacties | Verwacht wanneer `renderDecisions` optie is ingesteld op `true` of het bereik wordt aangevraagd en de gebruiker komt in aanmerking voor een bepaalde doelactiviteit |
| A `decisioning.propositionDisplay` gebeurtenisbranden na op VEC gebaseerde activiteiten | Van activiteiten die automatisch en op bestelling worden teruggegeven wordt verwacht dat ze afzonderlijke gebeurtenisaanroepen hebben |
| A `decisioning.propositionDisplay` gebeurtenissen branden na genereren van formuliergebaseerde activiteiten | Alleen van toepassing op bepaalde implementaties. Vereist aangepaste code om deze aanroep uit te voeren. |
| A `decisioning.propositionDisplay` gebeurtenis wordt geactiveerd wanneer een aanbieding wordt toegepast op een wijziging in de SPA | Alleen van toepassing voor SPA implementaties |
| A `decisioning.propositionDisplay` gebeurtenis wordt NIET geactiveerd wanneer een SPA onderdeel opnieuw wordt gerenderd voor een bepaalde weergave | Alleen van toepassing voor SPA implementaties |
| A `decisioning.propsitionInteract` gebeurtenis wordt geactiveerd na conversie van een activiteit | De &#39;Op een element klikken&#39; en aangepaste conversies die zijn gemigreerd van at.js `trackEvent` of `sendNotifications` wordt verwacht dat er afzonderlijke gebeurtenisaanroepen zijn |
| De tokens van de reactie zijn teruggekeerd in `sendEvent` reactie en verwachte waarden hebben | De tokens van de reactie zouden normaal met Web SDK moeten werken |
| ECIDs is verenigbaar over pagina&#39;s met Web SDK en at.js | Is van toepassing op paginamigraties. Van omleidingsaanbiedingen wordt niet verwacht dat ze in dit soort migraties werken |


## Activiteit leveren en renderen

| Validatie-item | Notities |
|---|---|
| Op VEC gebaseerde activiteiten worden correct weergegeven bij het laden van de pagina | U kunt het beste aangepaste codewijzigingen en basiswijzigingen valideren, zoals het opnieuw rangschikken van elementen of het vervangen van tekst |
| VEC-activiteiten worden correct weergegeven op SPA weergavewijzigingen | Alleen van toepassing voor SPA implementaties |
| Op formulieren gebaseerde activiteiten worden correct weergegeven | Alleen van toepassing op bepaalde implementaties. Voor het weergeven van formuliergebaseerde activiteiten is aangepaste code vereist, vergelijkbaar met at.js. |
| Activiteiten die omleidingen gebruiken, werken naar behoren | Omleiding wordt gesteund als zowel de bron als bestemmingspagina het Web SDK van het Platform gebruiken. Een doel richt van een pagina at.js aan een pagina van SDK van het Web van het Platform opnieuw of de tegenovergestelde manier wordt niet gesteund. |
| De activiteiten die verre aanbiedingen gebruiken werken behoorlijk | Niet gebruikelijk, controleer uw aanbiedingsvoorraad van het Doel voor Verre Aanbiedingen |
| Flikkering wordt op de juiste wijze beperkt | De flikkering is optioneel, maar zorg ervoor dat alle aanwezige mitigatietactieken naar behoren werken voor optimale paginaprestaties en gebruikerservaring |
| QA-koppelingen werken naar verwachting | Als u dit niet doet, controleert u of de URL van web.webPageDetails.URL exact overeenkomt met de URL in de browser. |
| Al uw algemeen gebruikte aanbiedingstypes worden teruggegeven zoals verwacht |  |

## Rapportage

| Validatie-item | Notities |
|---|---|
| Bezoekers worden toegeschreven aan VEC-activiteiten | Het is best om het melden te bevestigen werkt zoals verwacht voor zowel pagina ladingswijzigingen als SPA meningswijzigingen |
| Bezoekers worden toegeschreven aan op formulieren gebaseerde activiteiten | Afhankelijk van de gebruikte rendermethode kan het zijn dat uw implementatie aangepaste code nodig heeft om een `decisioning.propositionDisplay` event |
| Standaardconversiedoelstellingen worden correct vastgelegd | Is op of Doel of Analyse als rapporteringsbron van toepassing |
| De omzettingen en details van bestellingen worden correct vastgelegd | Controleer het auditrapport |
| Conversies voor het bijhouden van klikken worden correct vastgelegd |  |
| Aangepaste conversiedoelstellingen worden correct vastgelegd | Conversiedoelstellingen zijn bijvoorbeeld gemigreerd van at.js `trackEvent` of `sendNotifications` die vaak worden gebruikt met het doel &quot;Bekeken een mbox&quot; |

## Scripts voor soorten publiek en profielen

| Validatie-item | Notities |
|---|---|
| Het publiek dat in levende activiteiten wordt gebruikt is compatibel met het Web SDK van het Platform | Soorten publiek die de component &quot;Custom&quot; (mbox parameter) gebruiken, moeten worden bijgewerkt om XDM-kenmerken op te nemen |
| Alle profielmanuscripten zijn compatibel met Platform Web SDK | Alle profielscripts die mbox-parameters gebruiken, moeten worden bijgewerkt om XDM-kenmerken op te nemen |
| Activiteitenrendement voor doelpubliek | Het is best om bevestiging van begin tot eind op publiek uit te voeren u wijzigt om compatibel met het Web SDK van het Platform te maken |
| Profielscripts worden geëvalueerd zoals verwacht | Edge-sporen weergeven in Foutopsporing |

## Integratie met Adobe-toepassingen

| Validatie-item | Notities |
|---|---|
| Rendement activiteiten voor Experience Cloud-publiek | Bijvoorbeeld een segment dat is gepubliceerd vanuit Adobe Analytics |
| Rendement activiteiten voor publiek in de Experience Platform | Alleen van toepassing als u een licentie hebt voor een toepassing op basis van een Experience Platform, zoals RTCDP |
| Rendement activiteiten voor publiek in de Audience Manager | Bijvoorbeeld een segment dat is gebaseerd op het bezoeken van een specifieke pagina |
| Weergaven van doelactiviteitgegevens in Analysis Workspace | Is van toepassing op activiteiten die Adobe Analytics als bron van rapportage gebruiken |

## Integraties met toepassingen van derden

| Validatie-item | Notities |
|---|---|
| De het symbolische gegevens van de reactie worden behoorlijk overgegaan tot derdetoepassingen | De benaderingen van de integratie kunnen variëren, maar een gemeenschappelijke methode moet de tokens van de Reactie van het Doel gebruiken om activiteit en ervaringsinformatie tot andere analysehulpmiddelen zoals Google Analytics over te gaan |
| Informatie van derden wordt doorgegeven als XDM- of profielgegevens | Alle relevante informatie van derden moet worden doorgegeven `sendEvent` vraag aan Doel |

Na het uitvoeren van de bevestigingsstappen hierboven, kunt u erop vertrouwen dat de implementatie van SDK van het Web van het Platform klaar is om aan productie te bewegen.

Leer nu hoe u [Los een implementatie van het Doel problemen op gebruikend het Web SDK van het Platform](debugging.md).

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).
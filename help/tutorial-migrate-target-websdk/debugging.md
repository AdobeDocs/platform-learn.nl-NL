---
title: Foutopsporing | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u fouten in een Adobe Target-implementatie kunt opsporen met de SDK van Adobe Experience Platform Web. De onderwerpen omvatten het zuiveren opties, browser uitbreidingen, en verschillen tussen at.js en het Web SDK van het Platform.
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 1%

---

# Zuiver Doel met het Web SDK van het Platform

Het verifiëren van de activiteiten van het Doel en het zuiveren Web SDK om implementatie, inhoudslevering, of kwesties van de publiekskwalificatie problemen op te lossen. Deze pagina van de migratiegids verklaart de verschillen tussen het zuiveren met at.js en het Web SDK van het Platform.

De onderstaande tabel geeft een overzicht van functies en ondersteuning voor het testen en opsporen van fouten.

| Functie of gereedschap | at.js-ondersteuning | Platform Web SDK-ondersteuning |
| --- | --- | --- |
| Activiteit QA URLs | Ja | Ja |
| `mboxDisable` URL-parameter | Ja | Zie de onderstaande informatie [functionaliteit Doel uitschakelen](#disable-target-functionality) |
| `mboxDebug` URL-parameter | Ja | Gebruiken `alloy_debug` parameter voor vergelijkbare foutopsporingsinformatie |
| `mboxTrace` URL-parameter | Ja | De browserextensie Foutopsporing Experience Platform gebruiken |
| Adobe Experience Platform Debugger-extensie | Ja | Ja |
| `alloy_debug` URL-parameter | Niet van toepassing | Ja |
| Adobe Experience Platform Assurance | Niet van toepassing | Ja |

## Browserextensie Adobe Experience Platform Debugger

De Adobe Experience Platform Debugger-extensie voor Chrome en Firefox controleert uw webpagina&#39;s en helpt u bij het valideren van uw Adobe Experience Cloud-implementaties.

U kunt Foutopsporing voor Platforms uitvoeren op elke webpagina en de extensie heeft toegang tot openbare gegevens. Om tot niet openbare gegevens toegang te hebben die de uitbreiding, zoals de spoorinformatie van het Doel gebruiken, moet u aan Experience Cloud via verifiëren **[!UICONTROL Aanmelden]** koppeling.

### Adobe Experience Platform Debugger ophalen en installeren

Foutopsporing voor Adobe Experience Platform kan worden geïnstalleerd in Google Chrome- of Mozilla Firefox-browsers. Volg de onderstaande koppeling om de extensie te installeren in uw voorkeursbrowser:

- [Chroom](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)
- [Firefox](https://addons.mozilla.org/en-US/firefox/addon/adobe-experience-platform-dbg/)

Nadat u de Chrome-extensie of de Firefox-invoegtoepassing hebt geïnstalleerd, verschijnt er een pictogram (![](assets/start-icon.jpg)) wordt toegevoegd aan de extensiebalk. Selecteer dit pictogram om de extensie te openen.

Raadpleeg de speciale handleiding voor meer informatie over de [Adobe Experience Platform Debugger-extensie](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) en hoe u fouten opspoort in alle Adobe-webtoepassingen.

## Voorvertoning van doelactiviteiten weergeven met URL&#39;s met kwaliteitscontrole

Zowel at.js als het Web SDK van het Platform staan u toe om de activiteiten van het Doel te voorproef gebruikend doel QA URLs, en beide implementatiemethodes steunen de zelfde eigenschappen QA.

Doel QA URLs die door te instrueren bij.js of het Web SDK van het Platform werken om een specifiek koekje aan uw browser te schrijven genoemd `at_qa_mode`. Dit cookie wordt gebruikt om kwalificatie voor een bepaalde activiteit en ervaring af te dwingen.

>[!CAUTION]
>
>De functionaliteit van de doel-QA-modus wordt ondersteund door Platform Web SDK versie 2.13.0 of hoger. De doel-QA-modus is ingeschakeld op basis van de `xdm.web.webPageDetails.URL` waarde doorgegeven in het dialoogvenster `sendEvent` vraag. Eventuele wijzigingen in deze waarde, zoals het verlagen van alle tekens, kunnen ertoe leiden dat de modus Doel-QA niet goed werkt.

Raadpleeg de speciale handleiding voor meer informatie over [Doelactiviteit QA](https://experienceleague.adobe.com/docs/target/using/activities/activity-qa/activity-qa.html).

## Implementatie van foutopsporing

De onderstaande tabel geeft een overzicht van de verschillen tussen de foutopsporingstactiek van at.js en Platform Web SDK:

| at.js, functie | Platform Web SDK equivalent |
| --- | --- |
| **Mbox uitschakelen** - schakel Doel uit van ophalen en renderen om te controleren of de pagina wordt verbroken zonder doelinteracties<br><br>Pagina laden met URL-parameter: `mboxDisable=true` | Geen direct equivalent. U kunt alle verzoeken van SDK van het Web van het Platform van het Web met de ontwikkelaarshulpmiddelen van uw browser blokkeren. |
| **Mbox Debug** - logt elke actie at.js in de browser console om het oplossen van teruggevende kwesties te helpen<br><br>Pagina laden met URL-parameter: `mboxDebug=true` | **Alloy Debug** - registreert gedetailleerde acties van SDK, met inbegrip van maar niet beperkt tot de acties van het Doel van de verpersoonlijking.<br><br>Pagina laden met URL-parameter: `alloy_debug=true`  <br /><br />Of voer uit `alloy("setDebug", { "enabled": true });` in uw ontwikkelaarsconsole |
| **Doelovertrek** - met een mbox spoorteken dat in het Doel UI wordt geproduceerd, is een spoorvoorwerp met details die aan het besluitvormingsproces deelnamen beschikbaar onder `window.___target_trace` object.<br><br>Pagina laden met URL-parameter: `mboxTrace=window&authorization={TOKEN}` | Gebruik de Debugger van Adobe Experience Platform uitbreiding of de Verzekering van het Platform. |

>[!NOTE]
>
>Alle bovenstaande foutopsporingsfuncties in het bestand at.js zijn beschikbaar met verbeterde functies in Adobe Experience Platform Debugger.

### Doelfunctionaliteit uitschakelen

De SDK van het Web van het Platform heeft momenteel geen eigenschap om de reacties van het Doel selectief te onderdrukken. Nochtans, is het mogelijk om de verzoeken van SDK van het Web van het Platform met de de ontwikkelaarshulpmiddelen van uw browser, diverse browser uitbreidingen, of derdetoepassingen te onderdrukken. Bijvoorbeeld, om het Web SDK van het Platform met Google Chrome te blokkeren:

1. Klik met de rechtermuisknop ergens op de pagina en selecteer **Inspect**
1. Selecteer **Netwerk** tab
1. Filteren op tekenreeks `//ee//` om slechts de vraag van SDK van het Web van Platforms te bekijken
1. De pagina opnieuw laden
1. Klik met de rechtermuisknop op een van de gefilterde netwerkaanvragen en selecteer **Toepassingsdomein voor aanvragen blokkeren**
1. Laad de pagina opnieuw en merk op dat het netwerkverzoek wordt geblokkeerd
1. Als u de foutopsporing hebt voltooid, klikt u met de rechtermuisknop op de geblokkeerde netwerkaanvraag en selecteert u **Blok opheffen** of sluit het deelvenster Gereedschappen voor ontwikkelaars

### Foutopsporingslogbestand weergeven

Foutopsporingsregistratie voor at.js met behulp van de `mboxDebug=true` URL-parameter bevat gedetailleerde informatie over elk verzoek, elke reactie en elke poging om de inhoud op de pagina te renderen. De SDK van het Web van het Platform heeft gelijkaardig zuivert registreren gebruikend `alloy_debug=true` URL-parameter.

| Informatie geregistreerd | at.js (`mboxDebug=true`) | Platform Web SDK (`alloy_debug=true`) |
| --- | --- | --- |
| Logboekvoorvoegsel voor filteren | `AT:` | `[alloy]` |
| Gegevens verzoek bij laden van pagina | Ja | Ja |
| Gegevens over een box- of bereikverzoek | Ja | Ja |
| Status aanvragen | Ja | Ja |
| Antwoorddetails | Ja | Ja |
| Status van weergave | Succes en fouten | Alleen fouten |
| Details renderen | Ja | Ja |

>[!NOTE]
>
>Zuiver logboeken voor at.js en het Web SDK van het Platform verstrekken gelijkaardig niveau van detail met de opmerkelijke uitzondering dat het Web SDK slechts van het teruggeven van fouten toe te schrijven aan ongeldige selecteurs op de hoogte brengt. De logfunctie voor foutopsporing bevestigt momenteel niet dat rendering is gelukt.

### Doelsporen weergeven

De doelsporen verstrekken gedetailleerde informatie over activiteitenkwalificaties en het profiel van het Doel van de bezoeker. Aangezien de sporen van het Doel informatie bevatten die niet openbaar beschikbaar is, vereist het bekijken van hen een toestemmingstoken of het voor authentiek verklaren binnen het browser van Adobe Experience Platform Debugger uitbreidingsvenster.

| Doeltraceermethode | at.js | Platform Web SDK |
| --- | --- | --- |
| `mboxTrace` URL-parameter | Ja | Nee |
| Browserextensie Adobe Experience Platform Debugger | Ja | Ja |
| Adobe Experience Platform Assurance | Nee | Ja |


Ga als volgt te werk om Platform Web SDK Target-sporen met Adobe Experience Platform Debugger weer te geven:

1. Navigeer aan een pagina op uw plaats die Doel met het Web SDK van het Platform heeft uitgevoerd
1. Open de extensie Adobe Experience Platform Debugger door het pictogram te selecteren (![](assets/start-icon.jpg)) in de navigatiebalk van uw browser
1. Selecteer **[!UICONTROL Aanmelden]** link
1. Verifiëren met uw Adobe Experience Cloud-aanmelding
1. Selecteer **[!UICONTROL Logboeken]** links
1. Selecteer **[!UICONTROL Rand]** tab bovenaan
1. Geef uw foutopsporingssessie optioneel een naam en klik op de knop **[!UICONTROL Verbinden]** knop
1. Laad de pagina opnieuw en het logboek zou met gedetailleerde informatie over de interacties van het randnetwerk moeten bevolken
1. Focus op de logitems die beginnen met &quot;Doelsporen&quot; in de beschrijving en selecteer **[!UICONTROL Weergave]** om de details van het Doel spoor te zien

![Doelsporen weergeven met Adobe Experience Platform Debugger](assets/target-trace-debugger.png)

Na het selecteren **[!UICONTROL Weergave]** Er wordt een overlay weergegeven waarmee u de volgende informatie over het verzoek kunt zien:

- Gelijktijdige activiteiten
- Niet-afgedekte activiteiten
- Gegevens aanvragen
- Momentopname profiel

Raadpleeg de speciale handleiding over [foutopsporing levering van doelinhoud](https://experienceleague.adobe.com/docs/target/using/activities/troubleshoot-activities/content-trouble.html) voor meer informatie over doelsporen.

### Problemen oplossen met Betrouwbaarheid

De informatie van het spoor van het doel is viewable in zowel de browser van Foutopsporing van Adobe Experience Platform als binnen de toepassing van de Verzekering (vroeger gekend als Project Griffon). Ga als volgt te werk om de doelsporen in Verzekering weer te geven:

1. Open de browserextensie van Adobe Experience Platform Debugger en verbind een externe foutopsporingssessie zoals hierboven beschreven
1. Selecteer de koppeling met uw sessienaam boven het foutopsporingslogbestand
1. De Verzekering van het Platform laadt en toont gedetailleerd registreren voor alle toepassingen van Adobe die in de gegevensstroom voor uw implementatie worden gevormd
1. Logbestand filteren op `adobe.target`
1. Selecteer een logbestandvermelding met het type `com.adobe.target.trace`
1. Breid de details van de lading uit en bekijk de informatie onder `context > targetTrace`

![Hoe te om de sporen van het Doel met Verzekering te bekijken](assets/target-trace-assurance.png)

## Onderzoek netwerkverzoek en reactie

De verzoeklading en de reactie van het Web SDK van het Platform `sendEvent` de vraag verschilt van at.js. Het overzicht hieronder zou u moeten helpen de structuur van het verzoek en de reactie begrijpen terwijl het onderzoeken van de netwerkvraag met de ontwikkelaarshulpmiddelen van uw browser.

### Payload voor inhoudsverzoek

![Doelspecifieke elementen van de SDK van het Web Platform](assets/target-payload.png)

- Profiel, entiteit en andere parameters anders dan mbox worden doorgegeven in de gebeurtenisarray onder `data.__adobe.target`
- Beslissingsbereiken bevinden zich in de gebeurtenissenarray onder `query.personalization.decisionScopes`
- XDM-gegevens die aan mbox-parameters zijn toegewezen, bevinden zich in de gebeurtenisarray onder `xdm`

### Inhoudsresponsinstantie

![Doelspecifieke elementen van het de reactielichaam van SDK van het Web van het Platform](assets/target-response.png)

- De SDK van het Web van de Platform keert acties voor alle toepassingen van de Adobe onder terug `handle` object
- De `personalization:decisions` handeling betekent een reactie van Doel of offer decisioning
- Doelvoorstellingen worden gepresenteerd als een array, elk met een unieke propositie-id vooraf vastgelegd met `AT:`
- Het bereik en de activiteitdetails van de beslissing zijn te vinden in de reeks voorstellen
- De details van de aanbieding bevinden zich in `items` array onder `data`
- De reactietokens bevinden zich in de `items` array onder `meta`

### lading propositiegebeurtenis

![Voorbeeld van doelpropositie](assets/target-proposition-event.png)

- Doelspecifieke SDK-gebeurtenissen zijn: `decisioning.propositionDisplay` voor een indruk of `decisioning.propositionInteract` voor een interactie, zoals een klik
- De details van de proposition-gebeurtenis bevinden zich in de events-array onder `xdm._experience.decisioning`
- De propositie-id van de weergave- of interactiegebeurtenis moet overeenkomen met de propositie-id van de inhoud die door Doel wordt geretourneerd


Gefeliciteerd, u hebt het einde van de zelfstudie bereikt! Veel succes bij het migreren van uw Adobe Target-implementatie naar Web SDK!

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).

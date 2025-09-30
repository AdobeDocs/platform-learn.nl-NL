---
title: Vergelijking van at.js 2.x met Web SDK - Migreer Doel van at.js 2.x aan Web SDK
description: Leer over de verschillen tussen at.js 2.x en Platform Web SDK met inbegrip van eigenschappen, functies, montages, en gegevensstroom.
exl-id: b6f0ac2b-0d8e-46ce-8e9f-7bbc61eb20ec
source-git-commit: 7d3c1728925e322f9313cf71f081500e0c0bac0b
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 1%

---

# Vergelijking van at.js met Platform Web SDK

De zelfstandige Adobe Target at.js-bibliotheek verschilt aanzienlijk van Platform Web SDK. De volgende tabellen zijn een referentie om u te helpen gebieden van uw implementatie te evalueren waarop u zich tijdens het migratieproces moet concentreren.

Na het herzien van de informatie hieronder en het beoordelen van uw huidige technische implementatie at.js, zou u het volgende moeten kunnen begrijpen:

- Welke eigenschappen van het Doel door het Web SDK van het Platform worden gesteund
- Welke functies at.js hebben de equivalenten van SDK van het Web van het Platform
- Hoe de montages van het Doel met het Web SDK van het Platform worden toegepast
- Hoe de gegevensstroom van at.js en het Web SDK van het Platform verschillen

Maak je geen zorgen als je nog geen ervaring hebt met Platform Web SDK. Onderstaande onderdelen worden in deze zelfstudie in detail besproken.

## Functievergelijking

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Doelprofiel bijwerken | Ondersteund | Ondersteund |
| Triggerweergave voor SPA&#39;s | Ondersteund | Ondersteund |
| Doelaanbevelingen | Ondersteund | Ondersteund |
| Formuliergebaseerde aanbiedingen ophalen | Ondersteund | Ondersteund |
| Gebeurtenissen bijhouden | Ondersteund | Ondersteund |
| A4T: Toepassing op één pagina | Ondersteund | Ondersteund |
| A4T: klik op bijhouden | Ondersteund | Ondersteund |
| A4T: Logboekregistratie op de client | Ondersteund | Ondersteund |
| A4T: logboekregistratie op de server | Ondersteund | Ondersteund |
| Aanbiedingen toepassen | Ondersteund | Ondersteund |
| Weergave opnieuw renderen in SPA zonder meldingen | Ondersteund | Ondersteund |
| Hybride toepassingen | Ondersteund | Ondersteund |
| URL&#39;s kwaliteitscontrole | Ondersteund | Ondersteund |
| Id&#39;s van derden van box | Ondersteund | Ondersteund |
| Klantkenmerken | Ondersteund | Ondersteund |
| Externe aanbiedingen | Ondersteund | Gedeeltelijk ondersteund. Dynamische externe aanbiedingen worden niet ondersteund. |
| Aanbiedingen omleiden | Ondersteund | Ondersteund. Een omleiding van een pagina met Platform Web SDK naar een pagina met at.js (en in de tegenovergestelde richting) wordt echter niet ondersteund. |
| Apparaatbeslissingen | Ondersteund | Momenteel niet ondersteund |
| Prefetch Mboxes | Ondersteund voor aangepaste scènes en SPA VEC | Prefetch is de standaardmodus voor Web SDK |
| Aangepaste gebeurtenissen | Ondersteund | Niet ondersteund. Zie [ openbare roadmap ](https://github.com/orgs/adobe/projects/18/views/1?pane=item&itemId=17372355{target="_blank"}) voor huidige status. |
| Reactietokens | Ondersteund | Ondersteund. Verwijs naar de [ specifieke documentatie van reactietokens ](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html) voor codevoorbeelden en verschillen tussen at.js en het Web SDK van het Platform |
| Gegevensleveranciers | Ondersteund | Niet ondersteund. De code van de douane kan worden gebruikt om een bevel van het Web SDK van het Platform `sendEvent` teweeg te brengen nadat het gegeven van een andere leverancier wordt teruggewonnen. |


## Aanbiedingswaardige callouts

| | Doel op.js 2.x | Platform Web SDK |
|---|---|---|
| Verzadiging flikkering | In het bovenliggende codefragment voor asynchrone implementaties wordt de stijl-id `at-body-style` gebruikt. at.js zoekt naar deze element-id om de stijl te verwijderen zodra een reactie is ontvangen. | In het standaard voorverborgen fragment wordt de stijl-id `alloy-prehiding` gebruikt. Het Web SDK is niet compatibel met het bij.js prehide fragment zodat moet het als deel van het migratieproces worden veranderd. |
| Inhoud automatisch renderen bij laden van pagina | Gecontroleerd met de globale instelling Doel. Wordt ingeschakeld wanneer `pageLoadEnabled` is ingesteld op `true` . | Opgegeven in de opdracht Platform Web SDK `sendEvent` . Ingeschakeld door de optie `renderDecisions` in te stellen op `true` . |
| Inhoud handmatig renderen | De functies `applyOffer()` en `applyOffers()` ondersteunen alleen het instellen van HTML | De opdracht `applyPropositions` ondersteunt het instellen, vervangen of toevoegen van HTML voor extra flexibiliteit |
| Aangepaste gebeurtenissen bijhouden | Ondersteund met functies `trackEvent()` en `sendNotifications()` . Deze functies zijn specifiek voor Target en hebben geen invloed op de metriek van Adobe Analytics. | Alle gegevens van SDK van het Web van het Platform `sendEvent` vraag door:sturen aan Doel. Aanvullende gegevens die specifiek nodig zijn voor Target, moeten worden opgenomen in de opdracht `sendEvent` met het gebeurtenistype `decisioning.propositionDisplay` of `decisioning.propositionInteract` om ervoor te zorgen dat de metriek van Adobe Analytics niet wordt beïnvloed. |
| DoelNAAM | Ondersteund. Dit staat los van de CNAME die wordt gebruikt voor Analytics en de Experience Cloud ID Service. | Niet langer relevant. Één enkele CNAME kan voor alle vraag van SDK van het Web van het Platform worden gebruikt. |
| Foutopsporing | De URL-parameters `mboxDisable` , `mboxDebug` en `mboxTrace` kunnen worden gebruikt voor foutopsporing met de ontwikkelaarsgereedschappen van uw browser.<br><br> Adobe Experience Platform Debugger is ook gesteund het zuiveren hulpmiddel. | De URL-parameters `mboxDisable` , `mboxDebug` en `mboxTrace` worden niet ondersteund.<br><br> u kunt het zuiveren van SDK van het Web door `alloy_debug=true` aan uw vraagkoord toe te voegen of `alloy("setDebug", { "enabled": true });` in uw ontwikkelaarsconsole uit te voeren inschakelen.<br><br> de browser van Adobe Experience Platform Debugger uitbreiding kan worden gebruikt om een randspoor voor het zuiveren in werking te stellen.<br><br> verwijs naar [ het zuiveren van de documentatie van SDK van het Web van het Platform ](debugging.md) voor meer informatie. |
| Analyses voor doel (A4T) | Gebruikt waarden SDID om de vraag van het Doel en van de Analyse te bevestigen | Native ondersteund zonder dat stitching nodig is |

>[!NOTE]
>
>Migrating Target to Platform Web SDK while keeping an existing AppMeasurement Adobe Analytics implementation for a given page wordt niet ondersteund.
>
> Het is mogelijk om uw at.js (en AppMeasurement.js) implementatie aan het Web SDK van het Platform één pagina tegelijk te migreren. Als u deze benadering gebruikt, is het best om [`idMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) en [`targetMigrationEnabled` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) opties aan `true` met het `configure` bevel te plaatsen.

## at.js functies en Platform Web SDK equivalenten

Vele functies at.js hebben een gelijkwaardige benadering gebruikend het Web SDK van het Platform die in de hieronder lijst wordt geschetst. Voor meer details over [ at.js functies ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), verwijs naar de Gids van de Ontwikkelaar van Adobe Target.

| at.js 2.x, functie | Platform Web SDK equivalent |
| --- | --- | 
| `getOffer()` en `getOffers()` | Om te verzoeken en [ terug te geven ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#automatically-rendering-content) op VEC-Gebaseerde ervaringen van het Doel automatisch, gebruik het `sendEvent` bevel en plaats de `renderDecisions` optie aan waar.<br><br> om vorm-gebaseerde ervaringen te verzoeken of [ manueel terug te geven ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#manually-rendering-content) inhoud, specificeer een serie van `decisionScopes` (dozen) met het `sendEvent` bevel. |
| `applyOffer()` en `applyOffers()` | Gebruik de opdracht [`applyPropositions` ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html#applypropositions) om inhoud toe te passen. U kunt ervoor kiezen HTML in te stellen, te vervangen of toe te voegen aan een specifieke kiezer. |
| `triggerView()` | Het Web SDK van het platform brengt automatisch a [ meningsverandering ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-trigger-a-view-change-in-a-single-page-application) ten behoeve van het KUUROORD VEC in werking als het `web.webPageDetails.viewName` bezit onder de `xdm` optie van het `sendEvent` bevel wordt geplaatst. |
| `trackEvent()` en `sendNotifications()` | Gebruik het `sendEvent` bevel met a [ specifieke `eventType` ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/web-sdk-atjs-comparison.html#how-to-track-events) plaats:<br><br>`decisioning.propositionDisplay` signalen het teruggeven van een activiteit <br><br>`decisioning.propositionInteract` signalen een gebruikersinteractie met een activiteit, zoals een muisklik. |
| `targetGlobalSettings()` | Geen direct equivalent. Verwijs naar de [ de montagesvergelijking van het Doel ](detailed-comparison.md) voor extra details. |
| `targetPageParams()` en `targetPageParamsAll()` | Alle gegevens die worden doorgegeven in de optie `xdm` van de opdracht `sendEvent` , worden toegewezen aan de parameters van Target. Aangezien mbox de parameters gebruikend in series vervaardigde puntaantekening worden genoemd, kan het migreren aan het Web SDK van het Platform u vereisen om bestaande publiek en activiteiten bij te werken om de nieuwe namen van de mbox parameternamen te gebruiken. <br><br> Gegevens die als deel van `data.__adobe.target` van het `sendEvent` bevel worden overgegaan wordt in kaart gebracht aan [ profiel van het Doel en specifieke parameters van Aanbevelingen ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/target-overview.html#single-profile-update). |
| at.js, aangepaste gebeurtenissen | Niet ondersteund. Zie [ openbare roadmap ](https://github.com/orgs/adobe/projects/18/views/1?pane=item&itemId=17372355{target="_blank"}) voor huidige status. [ de tokens van de Reactie ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/accessing-response-tokens.html) worden blootgesteld als deel van `propositions` in de reactie van de `sendEvent` vraag. |

## at.js-instellingen en Platform Web SDK-equivalenten

De bibliotheek at.js kan met diverse montages in het Doel UI worden gevormd en worden gedownload. Deze instellingen kunnen ook worden bijgewerkt met de functie [`targetGlobalSettings()` ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/targetglobalsettings/) . In de onderstaande tabel worden deze instellingen vergeleken met de instellingen die beschikbaar zijn op Platform Web SDK.

| at.js-instelling | Platform Web SDK equivalent |
| --- | --- |
| `bodyHiddenStyle` | Stel de opdracht [`prehidingStyle` ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) in met de opdracht `configure` |
| `bodyHidingEnabled` | Als een `prehidingStyle` wordt gedefinieerd met de opdracht `configure` , wordt deze functie ingeschakeld. Als er geen stijl is gedefinieerd, probeert de Platform Web SDK geen inhoud te verbergen. |
| `clientCode` | Automatisch geconfigureerd |
| `cookieDomain` | Niet van toepassing |
| `crossDomain` | Stel de optie `thirdPartyCookiesEnabled` in op `true` met de opdracht `configure` om cookies van derden in te schakelen voor gebruik in andere domeinen |
| `cspScriptNonce` en `cspStyleNonce` | Verwijs naar de documentatie voor [ vormend CSP ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-a-csp.html) |
| `dataProviders` | Niet ondersteund |
| `decisioningMethod` | Alle Platform Web SDK `sendEvent` -opdrachten maken gebruik van serverbeslissingen. Hybride en op-apparaat beslissingen worden niet ondersteund. |
| `defaultContentHiddenStyle` en `defaultContentVisibleStyle` | Alleen van toepassing met at.js 1.x. Net als bij at.js 2.x, kan elke flikkeronderdrukking voor op vorm-gebaseerde ervaringen worden verwezenlijkt gebruikend douanecode. |
| `deviceIdLifetime` | Niet ondersteund. Als `targetMigrationEnabled` op `true` is ingesteld met de opdracht `configure` , wordt het `mbox` -cookie ingesteld met de levensduur van het apparaat ingesteld op 2 jaar. Deze waarde kan niet worden geconfigureerd. |
| `enabled` | Doelfunctionaliteit is in- of uitgeschakeld met de configuratie van de gegevensstroom |
| `globalMboxAutoCreate` | Stel de optie `renderDecisions` in op `true` met de opdracht `sendEvent` om VEC-ervaringen automatisch op te halen en weer te geven.<br><br> vraag a `decisionScope` voor `__view__` als u verkiest om op VEC-Gebaseerde ervaringen manueel terug te geven. |
| `imsOrgId` | Stel de `orgId` in met de opdracht `configure` |
| `optinEnabled` en `optoutEnabled` | Verwijs naar het Web SDK van het Platform [ privacyopties ](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html). De optie `defaultConsent` is van toepassing op alle Adobe-oplossingen die door Platform Web SDK worden ondersteund. |
| `overrideMboxEdgeServer` en `overrideMboxEdgeServerTimeout` | Niet van toepassing. Alle verzoeken van het Web SDK van het Platform gebruiken het netwerk van Adobe Experience Platform Edge. |
| `pageLoadEnabled` | Stel de optie `renderDecisions` in op `true` met de opdracht `sendEvent` |
| `secureOnly` | Niet ondersteund. Het Web SDK van het Platform plaatst alle koekjes met de `secure` en `sameSite="none"` attributen. |
| `selectorsPollingTimeout` | Niet ondersteund. De SDK van het Web van het Platform gebruikt een waarde van 5 seconden. Aangepaste code kan worden gebruikt om inhoud handmatig te renderen. |
| `serverDomain` | De instelling `edgeDomain` gebruiken met de opdracht `configure` |
| `telemetryEnabled` | Niet van toepassing |
| `timeout` | Niet ondersteund. Het wordt geadviseerd dat u ervoor zorgt om het even welke flikkerende matigingscode een aangewezen onderbreking omvat. |
| `viewsEnabled` | Niet ondersteund. Inhoud voor doelweergaven wordt altijd opgehaald bij de eerste `sendEvent()` oproep als `renderDecisions` is ingesteld op `true` of als `__view__` DecisionScope is opgenomen in de aanvraag. |
| `visitorApiTimeout` | Niet van toepassing |


## Vergelijking systeemdiagram

De volgende diagrammen zouden u moeten helpen de verschillen van de gegevensstroom tussen een implementatie van het Doel begrijpen gebruikend at.js en een implementatie gebruikend het Web SDK van het Platform.

### at.js 2.x systeemdiagram

![ at.js 2.0 gedrag op paginading ](assets/target-at-js-2x-diagram.png){zoomable="yes"}

| Bellen | Details |
| --- | --- |
| 1 | De vraag keert Experience Cloud ID (ECID) terug. Als de gebruiker voor authentiek wordt verklaard, synchroniseert een andere vraag de klantenidentiteitskaart |
| 2 | De bibliotheek at.js wordt synchroon geladen en de hoofdtekst van het document verborgen (at.js kan ook asynchroon worden geladen met een optioneel vooraf verborgen fragment dat op de pagina is geïmplementeerd). |
| 3 | Het verzoek om het laden van de pagina wordt ingediend met inbegrip van alle gevormde parameters, ECID, SDID, en klant ID. |
| 4 | Profielscripts worden uitgevoerd en toegevoegd aan de profielopslag. De winkel vraagt om gekwalificeerd publiek uit de Audience Library (bijvoorbeeld een publiek dat wordt gedeeld door Analytics, Audience Manager enzovoort). Klantkenmerken worden in een batchproces naar de profielwinkel verzonden. |
| 5 | Gebaseerd op URL, verzoekparameters, en profielgegevens, beslist Target welke Activiteiten en Ervaringen aan de bezoeker voor de huidige pagina en de toekomstige meningen terug te keren. |
| 6 | Gerichte inhoud die naar pagina wordt teruggestuurd, eventueel inclusief profielwaarden voor extra personalisatie.<br><br> de gerichte inhoud op de huidige pagina wordt getoond zo snel mogelijk zonder flikkering van standaardinhoud.<br><br> de gerichte inhoud voor toekomstige meningen van een enig-paginatoepassing wordt in het voorgeheugen ondergebracht in browser, zodat kan het onmiddellijk zonder een extra servervraag worden toegepast wanneer de meningen worden teweeggebracht. |
| 7 | Analysegegevens die van de pagina naar de Servers van de Inzameling van Gegevens worden verzonden. |
| 8 | De doelgegevens worden via de SDID aangepast aan de analysegegevens en worden verwerkt in de analytische rapportageopslag. De analysegegevens kunnen dan in zowel Analytics als Doel via A4T- rapporten worden bekeken. |

Verwijs naar de ontwikkelaarsgids voor meer informatie hoe te [ Doel uitvoeren gebruikend at.js voor enig-paginatoepassingen ](https://developer.adobe.com/target/implement/client-side/atjs/how-to-deployatjs/target-atjs-single-page-application/).

### Platform Web SDK systeemdiagram

![ Diagram van de randbeslissing van Adobe Target met het Web SDK van het Platform ](assets/target-platform-web-sdk.png)

| Bellen | Details |
| --- | --- |
| 1 | Het apparaat laadt de Platform Web SDK. Het Web SDK van het Platform verzendt een verzoek naar het randnetwerk met XDM- gegevens, milieu identiteitskaart van Datastreams, overgegaan parameters, en identiteitskaart van de Klant (facultatief). De pagina (of containers) is vooraf verborgen. |
| 2 | Het Edge-netwerk verzendt de aanvraag naar de Edge-services om deze te verrijken met de informatie over de bezoeker-id, toestemming en andere bezoekerscontext, zoals geolocatie en apparaatvriendelijke namen. |
| 3 | Het randnetwerk verzendt het verrijkte verpersoonlijkingsverzoek naar de rand van het Doel met identiteitskaart van de Bezoeker en overgegaan parameters. |
| 4 | Profielscripts worden uitgevoerd en vervolgens opgenomen in de opslag van het doelprofiel. De opslag van het profiel haalt segmenten van de Bibliotheek van de Publiek (bijvoorbeeld, segmenten die van Adobe Analytics, Adobe Audience Manager, Adobe Experience Platform worden gedeeld). |
| 5 | Op basis van URL-aanvraagparameters en -profielgegevens bepaalt Target welke activiteiten en ervaringen moeten worden weergegeven voor de bezoeker voor de huidige paginaweergave en voor toekomstige vooraf ingestelde weergaven. Het doel verzendt dit dan terug naar het randnetwerk. |
| 6 | a. Het Edge-netwerk stuurt de verpersoonlijkingsreactie terug naar de pagina, eventueel inclusief profielwaarden voor extra personalisatie. Gepersonaliseerde inhoud op de huidige pagina wordt zo snel mogelijk weergegeven zonder flikkering van de standaardinhoud.<br><br> b. De gepersonaliseerde inhoud voor meningen die als resultaat van gebruikersacties in Één enkele Toepassing van de Pagina (SPA) worden getoond wordt in het voorgeheugen ondergebracht voor onmiddellijk teruggeven zonder extra servervraag.<br><br> c. Het Edge-netwerk verzendt de bezoeker-id en andere waarden in cookies (bijvoorbeeld toestemming, sessie-id, identiteit, cookie-controle, personalisatie enzovoort). |
| 7 | Het randnetwerk forwards Analytics voor de details van het Doel (A4T) (activiteit, ervaring, en omzettingsmeta-gegevens) aan de rand van de Analyse. |

Verwijs naar de ontwikkelaarsgids voor meer informatie hoe te [ Doel uitvoeren gebruikend het Web SDK van het Platform voor Enige-pagina toepassingen ](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/spa-implementation.html).

Nadat u een goed technisch inzicht in uw huidige implementatie van het Doel en de eigenschappen hebt u gebruikt, moet de volgende stap de [ aanvankelijke opstelling ](initial-setup.md) uitvoeren.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw doelmigratie van at.js naar Web SDK. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.

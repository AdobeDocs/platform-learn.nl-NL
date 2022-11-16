---
title: Gegevenselement en regel maken voor het bijhouden van downloads van apps
description: Gegevenselement en regel maken voor het bijhouden van downloads van apps
feature: Web SDK
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: cb322540-e8ef-4226-b537-a67c7ca273f5
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Gegevenselement en regel maken voor het bijhouden van downloads van apps

Als herinnering, wanneer het volgen wanneer een gebruiker klikt [!UICONTROL De app downloaden] koppeling hebt u als volgt naar de gegevenslaag geduwd:

```js
window.adobeDataLayer.push({
  "event": "downloadAppClicked",
  "eventInfo": {
    "web": {
      "webInteraction": {
        "URL": "https://example.com/download",
        "name": "App Download",
        "type": "download"
      }
    }
  }
});
```

U hebt de `eventInfo` key, die de gegevenslaag vertelt om deze gegevens samen met de gebeurtenis mee te delen, maar aan _niet_ de gegevens in de gegevenslaag behouden. Voor een verbindingsklik, is het niet nuttig om informatie over de geklikte verbinding aan de gegevenslaag toe te voegen omdat het niet op andere gebeurtenissen van toepassing is die later op de pagina kunnen voorkomen.

Voor deze implementatie verzendt u een ervaringsgebeurtenis naar Adobe Experience Platform met het samengevoegde resultaat van (1) de berekende status van de gegevenslaag en (2) de inhoud van `eventInfo`.

Hiervoor moet u eerst een gegevenselement maken waarin deze twee blokken informatie worden samengevoegd.

## Een data-element maken

Klik op [!UICONTROL Gegevenselementen] in het linkermenu. Klik op de knop [!UICONTROL Gegevenselement toevoegen] koppeling.

Voer voor de naam van het gegevenselement `computedStateAndEventInfo`. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Kern] als deze nog niet is geselecteerd. Voor de [!UICONTROL Type gegevenselement] veld, selecteren [!UICONTROL Samengevoegde objecten]. Met dit gegevenselement kunt u meerdere objecten diep samenvoegen. Het samengevoegde resultaat wordt geretourneerd door het gegevenselement.

Voor het eerste object dat u in de samenvoeging wilt opnemen, voert u `%event.fullState%`. Wanneer gebruikt binnen een regel die door a wordt teweeggebracht [!UICONTROL Gegevens geplakt] regelgebeurtenis, verwijst dit naar de gegevens verwerkte staat van de Laag van Gegevens van de Cliënt van Adobe toen de regel werd teweeggebracht.

Klikken [!UICONTROL Nog een toevoegen].

Voor het tweede object voert u `%event.eventInfo%`. Wanneer gebruikt binnen een regel die door a wordt teweeggebracht [!UICONTROL Gegevens geplakt] regelgebeurtenis, verwijst dit naar de `eventInfo` Deel dat aan de Laag van Gegevens van de Cliënt van Adobe werd geduwd.

![computedStateAndEventInfo, gegevenselement](../../../assets/implementation-strategy/computed-state-and-event-info-data-element.png)

Het gegevenselement is voltooid. Sla het gegevenselement op door op de knop [!UICONTROL Opslaan] knop.

## Een regel maken

Als u de regel voor bijhouden wilt maken, klikt u op de knop [!UICONTROL De app downloaden] koppeling, eerste klik [!UICONTROL Regels] in het linkermenu.

Klikken [!UICONTROL Regel toevoegen].

Voor de regelnaam voert u _Klikte app-koppeling downloaden_.

## Een gebeurtenis toevoegen

Klik op de knop [!UICONTROL Toevoegen] knop onder [!UICONTROL Gebeurtenissen]. U kunt nu tonen dat deze zich in de gebeurtenisweergave bevindt. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Gegevenslaag Adobe-client]. Voor de [!UICONTROL Type gebeurtenis] veld, selecteren [!UICONTROL Gegevens geplakt].

Omdat u deze regel alleen wilt activeren als de `downloadAppClicked` -gebeurtenis naar de gegevenslaag wordt geduwd, selecteert u de [!UICONTROL Specifieke gebeurtenis] radio onder [!UICONTROL Luisteren naar] en type _downloadAppClicked_ in de [!UICONTROL Gebeurtenis/sleutel waarvoor u zich wilt registreren]  tekstveld dat wordt weergegeven.

![Aangeklikte gebeurtenis voor app downloaden](../../../assets/implementation-strategy/download-app-clicked-event.png)

Klikken [!UICONTROL Wijzigingen behouden].

## Een handeling toevoegen

Nu u bij de regelweergave bent, klikt u op de knop [!UICONTROL Toevoegen] knop onder [!UICONTROL Handelingen]. U moet nu in de actieweergave zijn. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Adobe Experience Platform Web SDK]. Voor de [!UICONTROL Type handeling] veld, selecteren [!UICONTROL Gebeurtenis Send].

Zoek aan de rechterkant van het scherm de [!UICONTROL Type] veld en selecteer `web.webinteraction.linkClicks`.

Voor de [!UICONTROL XDM-gegevens] veld, klik op de selectieknop voor gegevenselement en selecteer [!UICONTROL computedStateAndEventInfo]. Dit is het gegevenselement dat u zojuist hebt gemaakt.

Voor deze regel (in tegenstelling tot de andere regels die u hebt gemaakt), controleert u de [!UICONTROL Document wordt verwijderd] selectievakje. Dit vertelt de SDK in feite dat de gebruiker bij het klikken op de koppeling weg van de pagina navigeert. Dit is belangrijk, omdat het SDK toestaat om het verzoek op een manier te maken dat zelfs als de gebruiker vanaf de pagina navigeert, het verzoek nog op de achtergrond zal lopen en de server bereikt. Als dit selectievakje is uitgeschakeld, wordt het verzoek niet op deze manier uitgevoerd en wordt het waarschijnlijk geannuleerd wanneer het huidige document wordt verwijderd.

Je vraagt je misschien af: &quot;Dat klinkt mooi. Waarom is deze optie dan niet altijd ingeschakeld?&quot;

Wel, het is een beetje gecompliceerd, maar wanneer het gebruiken van deze eigenschap, gebruikt SDK een browser methode genoemd [`sendBeacon`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/sendBeacon) om het verzoek te verzenden. Wanneer u een aanvraag verzendt met `sendBeacon`, staat browser niet SDK (of om het even wat anders) toe om tot om het even welke gegevens toegang te hebben die van de server zijn teruggekeerd. Als de SDK deze functie voor elk verzoek zou gebruiken, zou de SDK nooit gegevens van de server kunnen ontvangen. Daarom is het belangrijk om de [!UICONTROL Document wordt verwijderd] Schakel het selectievakje alleen in wanneer het huidige document wordt verwijderd. In dat geval kunnen de reactiegegevens toch worden verwijderd.

![Het selectievakje Document wordt verwijderd](../../../assets/implementation-strategy/document-will-unload.png)

Sla de handeling op door op de knop [!UICONTROL Wijzigingen behouden] knop.

## De regel opslaan

Uw regel moet nu volledig zijn.

![Aangeklikte regel voor app-koppeling downloaden](../../../assets/implementation-strategy/download-app-link-clicked-rule.png)

Sla de regel op door op [!UICONTROL Opslaan].

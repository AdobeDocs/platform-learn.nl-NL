---
title: Gegevenselement en regel maken voor het bijhouden van downloads van apps
description: Gegevenselement en regel maken voor het bijhouden van downloads van apps
feature: Web SDK
exl-id: 8012ba48-38ac-4fb5-9876-8f57d1c5da5d
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '812'
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

Hiervoor moet u een gegevenselement maken waarin deze twee blokken informatie worden samengevoegd.

## Een data-element maken

Het juiste gegevenselement maken:

1. Klikken [!UICONTROL Gegevenselementen] in het linkerzijmenu.
1. Klik op de knop [!UICONTROL Nieuw gegevenselement maken] koppeling.
1. Voer de naam van het gegevenselement in. `computedStateAndEventInfo`.
1. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Kern] als deze nog niet is geselecteerd.
1. Voor de [!UICONTROL Type gegevenselement] veld, selecteren **[!UICONTROL Samengevoegde objecten]**. Met dit gegevenselement kunt u meerdere objecten samenvoegen. Het samengevoegde resultaat wordt geretourneerd door het gegevenselement.
1. Voeg het eerste object toe dat u in de samenvoeging wilt opnemen. Enter `%event.fullState%` in de [!UICONTROL Object(vereist)] veld. Wanneer gebruikt binnen een regel die door a wordt teweeggebracht [!UICONTROL Gegevens geplakt] regelgebeurtenis, verwijst dit naar de gegevens verwerkte staat van de Laag van Gegevens van de Cliënt van Adobe toen de regel werd teweeggebracht.
1. Klik op de knop  **[!UICONTROL Nog een toevoegen]** gebruiken.
1. Voeg het tweede object toe. Enter `%event.eventInfo%` in de [!UICONTROL Object(vereist)] veld. Wanneer gebruikt binnen een regel die door a wordt teweeggebracht [!UICONTROL Gegevens geplakt] regelgebeurtenis, verwijst dit naar de `eventInfo` Deel dat aan de Laag van Gegevens van de Cliënt van Adobe werd geduwd.
1. Sla het gegevenselement op door op de knop [!UICONTROL Opslaan] knop.
   ![computedStateAndEventInfo, gegevenselement](../assets/computed-state-and-event-info-data-element.png)

Het gegevenselement is voltooid.

## Een regel maken

Als u de regel voor bijhouden wilt maken, klikt u op de knop [!UICONTROL De app downloaden] koppeling:

1. Klikken **[!UICONTROL Regels]** in het linkerzijmenu.
1. Klikken **[!UICONTROL Regel toevoegen]**.
1. Enter **_Klikte app-koppeling downloaden_** in de [!UICONTROL Naam] veld.

## Een gebeurtenis toevoegen

1. Klik op de knop **[!UICONTROL Toevoegen]** knop onder [!UICONTROL Gebeurtenissen]. U kunt nu tonen dat deze zich in de gebeurtenisweergave bevindt.
1. Voor de [!UICONTROL Extensie] veld, selecteren **[!UICONTROL Gegevenslaag Adobe-client]**.
1. Voor de [!UICONTROL Type gebeurtenis] veld, selecteren **[!UICONTROL Gegevens geplakt]**.
1. Klikken **[!UICONTROL Wijzigingen behouden]**.
   ![Aangeklikte gebeurtenis voor app downloaden](../assets/download-app-clicked-event.png)
Omdat u deze regel alleen wilt activeren als de `downloadAppClicked` -gebeurtenis naar de gegevenslaag wordt geduwd, selecteert u de **[!UICONTROL Specifieke gebeurtenis]** radio onder [!UICONTROL Luisteren naar] en type **_downloadAppClicked_** in de [!UICONTROL Gebeurtenis/sleutel waarvoor u zich wilt registreren]  tekstveld dat wordt weergegeven.

## Een handeling toevoegen

Nu u weer bij de regelweergave bent:

1. Klik op de knop **[!UICONTROL Toevoegen]** knop onder [!UICONTROL Handelingen].
1. U moet nu in de actieweergave zijn. Voor de [!UICONTROL Extensie] veld, selecteren **[!UICONTROL Adobe Experience Platform Web SDK]**. Voor de [!UICONTROL Type handeling] veld, selecteren **[!UICONTROL Gebeurtenis Send]**.
1. In de [!UICONTROL Type] veld rechts, selecteer `web.webinteraction.linkClicks`.
1. Voor de [!UICONTROL XDM-gegevens] veld, klik op de selectieknop voor gegevenselement rechts en selecteer **[!UICONTROL computedStateAndEventInfo]**. Dit is het gegevenselement dat u onlangs hebt gemaakt.
1. Voor deze regel (in tegenstelling tot de andere regels u hebt gecreeerd), controleer **[!UICONTROL Document wordt verwijderd]** selectievakje.
   ![Het selectievakje Document wordt verwijderd](../assets/document-will-unload.png)
1. Sla de handeling op door op de knop **[!UICONTROL Wijzigingen behouden]** knop.

>[!TIP]
>
>De [!UICONTROL Document wordt verwijderd, functie] vertelt de SDK dat de gebruiker bij de pagina vandaan navigeert wanneer hij op de koppeling klikt. Dit is belangrijk, omdat de SDK hiermee de aanvraag kan uitvoeren, zelfs als de gebruiker buiten de pagina navigeert, omdat de aanvraag op de achtergrond wordt uitgevoerd en de server bereikt. Als dit selectievakje is uitgeschakeld, wordt het verzoek niet op deze manier uitgevoerd en wordt het daarom waarschijnlijk geannuleerd wanneer het huidige document wordt verwijderd.
>
>Je vraagt je misschien af: &quot;Dat klinkt mooi. Waarom is deze optie dan niet altijd ingeschakeld?&quot;
>
>Wel, het is een beetje gecompliceerd, maar wanneer het gebruiken van deze eigenschap, gebruikt SDK een browser methode genoemd [`sendBeacon`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/sendBeacon) om het verzoek te verzenden. Wanneer u een aanvraag verzendt met `sendBeacon`, staat browser niet SDK (of om het even wat anders) toe om tot om het even welke gegevens toegang te hebben die van de server zijn teruggekeerd. Als de SDK deze functie voor elk verzoek zou gebruiken, zou de SDK nooit gegevens van de server kunnen ontvangen. Daarom is het belangrijk om de [!UICONTROL Document wordt verwijderd] Schakel het selectievakje alleen in wanneer het huidige document wordt verwijderd. In dat geval kunnen de reactiegegevens toch worden verwijderd.

## De regel opslaan

Uw regel moet nu volledig zijn.

1. Klikken **[!UICONTROL Opslaan]** in de rechterbovenhoek.
   ![Aangeklikte regel voor app-koppeling downloaden](../assets/download-app-link-clicked-rule.png)

[Volgende: ](publish-the-library.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
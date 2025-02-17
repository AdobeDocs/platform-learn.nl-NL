---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - de Inzameling van Gegevens van het Web aan de cliënt-kant
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - de Inzameling van Gegevens van het Web aan de cliënt-kant
kt: 5342
doc-type: tutorial
exl-id: 6ba82c35-1087-45c5-85a3-8bca7408cfec
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# 1.1.4 Clientside Web Data Collection

## De gegevens in de aanvraag valideren

### De Adobe Experience Platform Debugger installeren

De Experience Platform Debugger is een extensie die beschikbaar is voor Chrome- en Firefox-browsers en waarmee u de Adobe-technologie kunt bekijken die in uw webpagina&#39;s is geïmplementeerd. Installeer de versie voor uw voorkeursbrowser:

- [ uitbreiding Firefox ](https://addons.mozilla.org/nl/firefox/addon/adobe-experience-platform-dbg/)

- [ de uitbreiding van Chrome ](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

Als u de foutopsporing nog nooit eerder hebt gebruikt - en deze is anders dan de vorige Adobe Experience Cloud Debugger - kunt u deze overzichtsvideo van vijf minuten bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/32156?quality=12&learn=on)

Aangezien u de demo-website in de incognitomodus gaat laden, moet u ervoor zorgen dat de Experience Platform Debugger ook beschikbaar is in de incognitomodus. Om dit te doen, ga **chrome://extensions** in uw browser en open de Debugger van Experience Platform uitbreiding.

Controleer of deze twee instellingen zijn ingeschakeld:

- Modus voor ontwikkelaars
- Toestaan in incognito

![ EXP de Homepage van Nieuws ](./images/ext1.png)

### De demo-website openen

Ga naar [ https://dsn.adobe.com ](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![ DSN ](./images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](./../../../getting-started/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](./../../../getting-started/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](./../../../getting-started/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](./../../../getting-started/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](./../../../getting-started/gettingstarted/images/web7.png)

### Gebruik Foutopsporing van Experience Platform om de vraag te zien die naar Edge gaat

Zorg ervoor dat de demo-website is geopend en klik op het extensiepictogram van Experience Platform Debugger.

![ EXP de Homepage van Nieuws ](./images/ext2.png)

Foutopsporing opent en toont de details van de implementatie die in uw bezit van de Inzameling van Gegevens van Adobe Experience Platform wordt gecreeerd. Herinner dat u de Uitbreiding en de regels zuivert die u enkel hebt uitgeeft.

Klik op de knop **[!UICONTROL Sign In]** rechtsboven om te verifiëren. Als u al een browsertabblad hebt geopend met de interface van Adobe Experience Platform Data Collection, wordt de verificatiestap automatisch uitgevoerd en hoeft u uw gebruikersnaam en wachtwoord niet meer in te voeren.

![ Debugger AEP ](./images/validate2.png)

U wordt dan aangemeld bij Foutopsporing.

![ Debugger AEP ](./images/validate2ab.png)

Druk op de knop Opnieuw laden op uw demowebsite om de foutopsporing te verbinden met dat specifieke tabblad.

![ Debugger AEP ](./images/validate2a.png)

Controleer of Foutopsporing **[!UICONTROL Connected to Home]** de bovenstaande afbeelding heeft en klik op het pictogram **[!UICONTROL lock]** om Foutopsporing te vergrendelen op de demowebsite. Als u dit niet doet, zal Debugger blijven overschakelen om de implementatiedetails van om het even welk browser lusje in nadruk bloot te stellen, wat verwarrend kan zijn. Zodra debugger wordt gesloten, zal het pictogram in **ontgrendelen** veranderen.

![ Debugger AEP ](./images/validate3.png)

Daarna, ga naar om het even welke pagina op de demowebsite zoals bijvoorbeeld, de **Plannen** categoriepagina.

![ Debugger AEP de uitbreiding van SDK van het Web van AEP ](./images/validate4.png)

Klik nu op **[!UICONTROL Experience Platform Web SDK]** in de linkernavigatie om de **[!UICONTROL Network Requests]** weer te geven.

Elke aanvraag bevat een **[!UICONTROL events]** rij.

![ Debugger AEP de uitbreiding van SDK van het Web van AEP ](./images/validate5.png)

Klik om een **[!UICONTROL events]** rij te openen. Merk op hoe u de {**gebeurtenis 0} web.webpagedetails.pageViews, evenals andere, uit-van-de-doosvariabelen die aan het** SDK ExperienceEvent XDM **formaat vasthouden van het Web kunt zien.**

![ waarde van Gebeurtenissen ](./images/validate8.png)

Deze types van verzoekdetails zijn ook zichtbaar in het Netwerk tabel. Filter voor verzoeken met **wisselt** in om van de verzoeken de plaats te bepalen die door SDK van het Web worden verzonden. U kunt alle details van de XDM lading in de sectie van de Lading vinden:

![ lusje van het Netwerk ](./images/validate9.png)

## Volgende stappen

Ga naar [ 1.1.5 uitvoeren Adobe Analytics en Adobe Audience Manager ](./ex5.md){target="_blank"}

Ga terug naar [ Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de de markeringsuitbreiding van SDK van het Web ](./data-ingestion-launch-web-sdk.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

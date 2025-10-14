---
title: Offer Decisioning - Test je beslissing
description: Offer Decisioning - Test je beslissing
kt: 5342
doc-type: tutorial
exl-id: c40b9b8c-9717-403c-bf02-6b8f42a59c05
source-git-commit: 2e856759e1a9b5509ad0632e28b269bcfc4ae861
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 3.3.3 Een campagne configureren met berichten in de app

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak** zijn.`--aepSandboxName--`

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.3.3.1 Kanaalconfiguratie voor in-app berichten

In het linkermenu, ga naar **Kanalen** en selecteer dan **configuraties van het Kanaal**. Klik **creeer kanaalconfiguratie**.

![&#x200B; InApp &#x200B;](./images/inapp1.png)

Ga de naam in: `--aepUserLdap--_In-app_Messages`, selecteer het kanaal **In-app overseinen** en laat dan de platforms **Web**, **iOS** en **Android** toe.

![&#x200B; InApp &#x200B;](./images/inapp2.png)

Schuif omlaag, dan ziet u dit.

![&#x200B; InApp &#x200B;](./images/inapp3.png)

Zorg ervoor dat **Enige pagina** wordt toegelaten.

Voor **Web**, ga URL van de website in die vroeger als deel van **werd gecreeerd Begonnen** module, die als dit kijkt: `https://dsn.adobe.com/web/--aepUserLdap---XXXX`. Vergeet niet **XXXX** in de unieke code van uw website te veranderen.

Voor **iOS** en **Android**, ga `com.adobe.dsn.dxdemo` in.

![&#x200B; InApp &#x200B;](./images/inapp4.png)

De rol omhoog en klikt **voorleggen**.

![&#x200B; InApp &#x200B;](./images/inapp5.png)

Uw kanaalconfiguratie is nu klaar om te worden gebruikt.

![&#x200B; InApp &#x200B;](./images/inapp6.png)

## 3.3.3.2 Een geplande campagne voor In-app-berichten configureren

In het linkermenu, ga naar **Campagnes** en klik dan **creeer campagne**.

![&#x200B; InApp &#x200B;](./images/inapp7.png)

Selecteer **Gepland - Op de markt brengend** en klik dan **creeer**.

![&#x200B; InApp &#x200B;](./images/inapp8.png)

Ga de naam `--aepUserLdap-- - CitiSignal Fiber Max` in en klik dan **Acties**.

![&#x200B; InApp &#x200B;](./images/inapp9.png)

Klik **+ voeg actie** toe en selecteer dan **In-app bericht**.

![&#x200B; InApp &#x200B;](./images/inapp10.png)

Selecteer de in-app berichtkanaalconfiguratie die u in de vorige stap hebt gemaakt en die de naam `--aepUserLdap--_In-app_Messages` heeft. Klik **uitgeven inhoud**.

![&#x200B; InApp &#x200B;](./images/inapp11.png)

Dan moet je dit zien. Klik **Modal**.

![&#x200B; InApp &#x200B;](./images/inapp12.png)

Klik **lay-out van de Verandering**.

![&#x200B; InApp &#x200B;](./images/inapp13.png)

Klik het **pictogram van Media URL** om activa van AEM Assets te kiezen.

![&#x200B; InApp &#x200B;](./images/inapp14.png)

Ga naar de omslag **burgerschap-beelden** en selecteer het beelddossier **neon-rabbit.jpg**. Klik **Uitgezocht**.

![&#x200B; InApp &#x200B;](./images/inapp15.png)

Voor de **tekst van de Kopbal**, gebruik: `CitiSignal Fiber Max`.
Voor de **tekst van het Lichaam**, gebruik: `Conquer lag with Fiber Max`.

![&#x200B; InApp &#x200B;](./images/inapp16.png)

Plaats de **tekst van Knoop #1** aan: `Go to Plans`.
Plaats het **doel** aan `com.adobe.dsn.dxdemo://plans`.

Klik **Overzicht om** te activeren.

![&#x200B; InApp &#x200B;](./images/inapp17.png)

Klik **activeren**.

![&#x200B; InApp &#x200B;](./images/inapp18.png)

Het statuut van uw campagne wordt nu geplaatst aan **het Activeren**. Het kan een paar minuten duren voordat de campagne live gaat.

![&#x200B; InApp &#x200B;](./images/inapp19.png)

Zodra de status in **Levend** is veranderd, kunt u uw campagne testen.

![&#x200B; InApp &#x200B;](./images/inapp20.png)

## 3.3.3.3 Test uw in-app-berichtcampagne op mobiele apparaten

Open de app op uw mobiele apparaat. Het nieuwe bericht in de app wordt dan weergegeven nadat u de app hebt gestart. Klik de knoop **gaan naar Abonnementen**.

![&#x200B; InApp &#x200B;](./images/inapp21.png)

U zult dan aan de **Punten** pagina worden genomen.

![&#x200B; InApp &#x200B;](./images/inapp22.png)

## Volgende stappen

Ga naar [&#x200B; Samenvatting en voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Journey Optimizer: Duw en In-app Berichten &#x200B;](ajopushinapp.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

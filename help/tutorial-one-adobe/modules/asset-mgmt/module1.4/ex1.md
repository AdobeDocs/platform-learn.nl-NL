---
title: Uw elementen en dynamische mediasjablonen maken
description: Uw elementen en dynamische mediasjablonen maken
kt: 5342
doc-type: tutorial
exl-id: 3867f23b-9b88-4971-a892-5821800e39ac
source-git-commit: 3c56760cee47197130cdf7bfc32540c208a86917
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# 1.4.1 Uw elementen en dynamische mediasjablonen maken

>[!IMPORTANT]
>
>U hebt toegang nodig tot een werkende AEM Assets CS Author-omgeving met AEM Assets Dynamic Media ingeschakeld om deze oefening te kunnen voltooien.
>
>Als u zulk een milieu niet hebt, ga naar [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.4.1.1 Uw Dynamic Media-bedrijf maken

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp1.png)

De rol neer aan **Dynamische Bedrijven van Media**. Klik op het pictogram **+** om een nieuw Dynamic Media Company te maken.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp2.png)

Voer de volgende gegevens in:

- **Bedrijfsnaam**: `--aepUserLdap---CitiSignal`.
- **gebied van het Bedrijf**: selecteer het gebied dat aan u het dichtst is.
- **Bedrijfs admin e-mails**: ga uw admin e-mail in.

Klik **creëren**.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp3.png)

Dan moet je dit zien.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp4.png)

U ontvangt nu een e-mail zoals hieronder, die uw tijdelijk wachtwoord bevat. Om uw wachtwoord te veranderen, of het terug te winnen voor het geval u geen e-mail ontving, zou u **Adobe Dynamic Media Classic Desktop app** moeten installeren. U kunt installatieinstructies hier vinden: [ https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app ](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app).

Volg de instructies hier en kom hier terug zodra de app op uw systeem is geïnstalleerd.

Open de **Desktopapp van Adobe Dynamic Media Classic**. Als u het wachtwoord kent, voert u dit hier in en volgt u de instructies om het wachtwoord bij de eerste aanmelding te wijzigen.

Als u uw wachtwoord niet kent, klik **vergeten uw wachtwoord** verbinding en volg de instructie om uw wachtwoord terug te stellen, dan hier terug te komen en binnen te registreren.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp5.png)

Na succesvolle login, zou u een scherm gelijkend op dit moeten zien.

![ Dynamische Media van AEM Assets ](./images/aaemassdmcomp6.png)

## 1.4.1.2 Dynamische media configureren in AEM

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`.

Klik hierop om het Cloud Manager-programma te openen. Dit wordt `--aepUserLdap-- - CitiSignal AEM+ACCS` genoemd.

![ Dynamische Media van AEM Assets ](./images/accsaemassets1.png)

Klik op uw omgeving.

![ Dynamische Media van AEM Assets ](./images/accsaemassets3.png)

Klik op de URL van de omgeving.

![ Dynamische Media van AEM Assets ](./images/accsaemassets2.png)

Ga naar **Hulpmiddelen**, naar **de Diensten van de Wolk** en dan naar **Dynamische Configuratie van Media**.

![ Dynamische Media van AEM Assets ](./images/accsaemassets4.png)

Selecteer **Globaal** (controleer niet checkbox), en klik dan **creeer**.

![ Dynamische Media van AEM Assets ](./images/accsaemassets5.png)

Voer de volgende gegevens in:

- **Titel**: gebruik deze titel: `--aepUserLdap-- - CitiSignal`.
- **E-mail**: ga uw e-mailadres in.
- **Wachtwoord**: ga uw Dynamisch de rekeningswachtwoord van Media in
- **Gebied**: selecteer het gebied dat u wanneer het creëren van uw Dynamisch bedrijf van Media, in dit voorbeeld, **Europa** koos.

Klik **verbinden met Dynamische Media**.

![ Dynamische Media van AEM Assets ](./images/accsaemassets6.png)

Dan moet je dit zien. Configureer het volgende:

- Selecteer het **Bedrijf**: `--aepUserLdap-- - CitiSignal`.
- Plaats **publiceer Assets** aan **Onmiddellijk**.
- Controle checkbox aan **synchroniseer alle inhoud**.

Klik **sparen**.

![ Dynamische Media van AEM Assets ](./images/accsaemassets7.png)

De configuratie van DYnamic Media is nu voltooid. Klik **OK**.

![ Dynamische Media van AEM Assets ](./images/accsaemassets8.png)

## 1.4.1.3 Uw elementen exporteren

Download dit dossier [ burgerschap-vezel-max-is-coming.psd ](./assets/citisignal-fiber-max-is-coming.psd){target="_blank"} en open het met Adobe Photoshop.

Dan moet je dit zien. CitiSignal plant een uitrol van Fiber Max in drie steden: New York, Parijs en Dubai.

Door specifieke lagen weer te geven of te verbergen, kunt u de afbeelding weergeven die door de ontwerpers is gemaakt.

Hieronder vindt u de instructies voor het exporteren van de afbeeldingsbestanden uit de Photoshop PSD-sjabloon. Als u verkiest, kunt u de gebeëindigde beelden hier ook downloaden [ burgerschap-dm-email-assets.zip ](./assets/citisignal-dm-email-assets.zip){target="_blank"} en het dossier op uw Desktop openen.

Dit is de versie voor New York.

![ Dynamische Media van AEM Assets ](./images/aemdm1.png)

Dit is de versie voor Dubai.

![ Dynamische Media van AEM Assets ](./images/aemdm2.png)

Dit is de versie voor Parijs.

![ Dynamische Media van AEM Assets ](./images/aemdm3.png)

Er zullen mogelijk nog veel andere steden zijn waar CitiSignal in de toekomst de Fiber Max-versie van start zal gaan. Er kunnen nieuwe lagen in dit bestand worden gemaakt. Voorlopig ligt de nadruk op de drie steden die al genoemd zijn.

Als u deze variaties wilt gebruiken in combinatie met AEM Assets Dynamic Media, moeten de lagen voor elke stad worden geëxporteerd als afbeeldingen. Om dat te doen, ga naar **Dossier** > **Uitvoer** > **Lagen aan Dossiers...**.

![ Dynamische Media van AEM Assets ](./images/aemdm4.png)

Dan moet je iets dergelijks zien. Selecteer een plaats om de dossiers naar uit te voeren, het dossiertype **PNG-8** te selecteren en **te klikken in werking stelt**.

![ Dynamische Media van AEM Assets ](./images/aemdm5.png)

Na een paar seconden moet je dit zien. Klik **OK**.

![ Dynamische Media van AEM Assets ](./images/aemdm6.png)

Deze bestanden moeten vervolgens beschikbaar zijn op de exportlocatie die u hebt geselecteerd.

![ Dynamische Media van AEM Assets ](./images/aemdm7.png)

## 1.4.1.4 Uw elementen uploaden naar AEM Assets CS

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Ga naar **Experience Manager Assets**.

![ Dynamische Media van AEM Assets ](./images/aemdm8.png)

Selecteer de opslagplaats met de naam `--aepUserLdap-- - CitiSignal AEM + ACCS` .

![ Dynamische Media van AEM Assets ](./images/aemdm9.png)

Ga naar **Assets** en klik dan **creeer Omslag**.

![ Dynamische Media van AEM Assets ](./images/aemdm10.png)

Gebruik voor de map de naam: `--aepUserLdap-- - CitiSignal Dynamic Media` . Klik **creëren**.

![ Dynamische Media van AEM Assets ](./images/aemdm11.png)

Dubbelklik om de map te openen die u net hebt gemaakt.

![ Dynamische Media van AEM Assets ](./images/aemdm12.png)

Klik **toevoegen Assets**.

![ Dynamische Media van AEM Assets ](./images/aemdm13.png)

Klik **doorbladeren** en selecteer dan **doorbladeren Dossiers**.

![ Dynamische Media van AEM Assets ](./images/aemdm15.png)

Selecteer de 4 PNG-bestanden die u in de vorige stap hebt geëxporteerd.

![ Dynamische Media van AEM Assets ](./images/aemdm16.png)

Klik **uploaden**.

![ Dynamische Media van AEM Assets ](./images/aemdm17.png)

Uw afbeeldingen zijn nu beschikbaar in AEM Assets CS.

![ Dynamische Media van AEM Assets ](./images/aemdm18.png)

Wacht een paar notulen en open dan de **Desktopapp van Adobe Dynamic Media Classic**, zou u ook de geuploade beelden moeten nu zien beschikbaar binnen Dynamische Media worden.

![ Dynamische Media van AEM Assets ](./images/aemdm19.png)

## 1.4.1.5 Dynamische mediasjabloon configureren

In het linkermenu, ga naar **Dynamische Media Assets**. Klik om de map te openen `--aepUserLdap-- - CitiSignal Dynamic Media` . Dan, klik **creeer Malplaatje**.

![ Dynamische Media van AEM Assets ](./images/aemdm20.png)

Voer de volgende gegevens in:

- **Naam van het Malplaatje**: `--aepUserLdap-- - CitiSignal Fiber Max Launch Email Assets`
- **de Breedte van het Canvas**: `600px`
- **Hoogte van Canvas**: `600px`

Klik **creëren**.

![ Dynamische Media van AEM Assets ](./images/aemdm21.png)

Dan moet je dit zien. Klik **voeg het pictogram van het Beeld** toe.

![ Dynamische Media van AEM Assets ](./images/aemdm22.png)

Sleep het dossier **burgerschap-fiber-max-is-coming_Citisignaal-background.png** op het canvas en maak het het canvas passen.

![ Dynamische Media van AEM Assets ](./images/aemdm23.png)

Daarna, sleep het dossier **burgerschap-vezel-max-is-coming_Citisignaal-newyork.png** op het canvas en maak het het canvas passen.

![ Dynamische Media van AEM Assets ](./images/aemdm24.png)

Daarna, sleep het dossier **burgerschap-vezel-max-is-coming_Citisignaal-dubai.png** op het canvas en maak het het canvas passen.

![ Dynamische Media van AEM Assets ](./images/aemdm25.png)

Daarna, sleep het dossier **burgerschap-vezel-max-is-coming_Citisignaal-paris.png** op het canvas en maak het het canvas passen.

![ Dynamische Media van AEM Assets ](./images/aemdm26.png)

U hebt nu alle drie variaties in de sjabloon als afzonderlijke lagen tegelijk. U kunt specifieke lagen tonen/verbergen door het **lagen** pictogram te klikken, waar u ziet dat alle lagen momenteel zichtbaar zijn.

![ Dynamische Media van AEM Assets ](./images/aemdm27.png)

Door een aantal lagen te verbergen, kunt u bepalen hoe het beeld eruit ziet. In dit voorbeeld, slechts is de laag voor **Parijs** en de achtergrondlaag zichtbaar.

![ Dynamische Media van AEM Assets ](./images/aemdm28.png)

Vervolgens moet u een tekstlaag toevoegen. Klik het **pictogram van de tekstlaag**.

![ Dynamische Media van AEM Assets ](./images/aemdm29.png)

Dan moet je dit zien.

![ Dynamische Media van AEM Assets ](./images/aemdm30.png)

Voel u vrij om het tekstveld aan te passen op de manier die u nodig acht, hier is een voorbeeld. Vergeet niet om de optie **Slimme Tekst toe te laten vergroot** zodat de echte tekst die in een recentere fase wordt opgenomen fijn zal kijken.

![ Dynamische Media van AEM Assets ](./images/aemdm31.png)

Voeg een tweede tekstlaag toe en zorg ervoor dat deze er zo uitziet. Vergeet niet om de optie **Slimme Tekst toe te laten vergroot** zodat de echte tekst die in een recentere fase wordt opgenomen fijn zal kijken.

![ Dynamische Media van AEM Assets ](./images/aemdm32.png)

Selecteer de eerste tekstlaag. Klik de 3 punten **..** en selecteer dan **uitgeven**.

![ Dynamische Media van AEM Assets ](./images/aemdm33.png)

Dan moet je dit zien. Omlaag schuiven.

![ Dynamische Media van AEM Assets ](./images/aemdm34.png)

Klik het **schakelaar** pictogram zodat de gebied **Tekst** wordt toegelaten. Verander de **Naam van de Parameter** in `title`.

![ Dynamische Media van AEM Assets ](./images/aemdm35.png)

Selecteer de tweede tekstlaag. Klik de 3 punten **..** en selecteer dan **uitgeven**.

![ Dynamische Media van AEM Assets ](./images/aemdm36.png)

Dan moet je dit zien. Omlaag schuiven.

![ Dynamische Media van AEM Assets ](./images/aemdm37.png)

Klik het **schakelaar** pictogram zodat de gebied **Tekst** wordt toegelaten. Verander de **Naam van de Parameter** in `body`.

![ Dynamische Media van AEM Assets ](./images/aemdm38.png)

Selecteer de laag voor **Parijs**. Klik de 3 punten **..** en klik **uitgeven**.

![ Dynamische Media van AEM Assets ](./images/aemdm39.png)

Ga naar **Paramaters**. Laat het gebied **toe Verbergen** en ga de **Naam van de Parameter** in: `city_paris`. Klik **sparen**.

![ Dynamische Media van AEM Assets ](./images/aemdm40.png)

Selecteer de laag voor **Dubai**. Klik de 3 punten **..** en klik **uitgeven**.

![ Dynamische Media van AEM Assets ](./images/aemdm41.png)

Ga naar **Paramaters**. Laat het gebied **toe Verbergen** en ga de **Naam van de Parameter** in: `city_dubai`. Klik **sparen**.

![ Dynamische Media van AEM Assets ](./images/aemdm42.png)

Selecteer de laag voor **New York**. Klik de 3 punten **..** en klik **uitgeven**.

![ Dynamische Media van AEM Assets ](./images/aemdm43.png)

Ga naar **Paramaters**. Laat het gebied **toe Verbergen** en ga de **Naam van de Parameter** in: `city_ny`. Klik **sparen**.

![ Dynamische Media van AEM Assets ](./images/aemdm44.png)

Klik **Voorproef**.

![ Dynamische Media van AEM Assets ](./images/aemdm45.png)

Laat de schakelaar voor **toe omvat alle parameters** en verandert sommige inputvariabelen zoals die in het schermschot worden vermeld. De afbeelding wordt dynamisch gewijzigd op basis van de ingevoerde gegevens. Voor de gebieden **city_paris**, **city_dubai** en **city_ny**, betekent een waarde van 0 dat dit beeld NIET zal worden verborgen en een waarde van 1 betekent dit beeld zal worden verborgen.

![ Dynamische Media van AEM Assets ](./images/aemdm46.png)

Door sommige variabelen te wijzigen, wordt nu een andere afbeelding weergegeven.

![ Dynamische Media van AEM Assets ](./images/aemdm47.png)

Als u meer variabelen wijzigt, wordt nu een andere afbeelding weergegeven.

![ Dynamische Media van AEM Assets ](./images/aemdm48.png)

Uw sjabloon Dynamische media is nu geconfigureerd. In de volgende oefening, zult u dat malplaatje in combinatie met een e-mailcampagne in Adobe Journey Optimizer gebruiken.

## Volgende stappen

Volgende Stap: [ gebruik uw dynamisch media malplaatje met Adobe Journey Optimizer ](./ex2.md){target="_blank"}

Ga terug naar [ Adobe Experience Manager Assets &amp; Dynamische Media ](./aemassetsdm.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

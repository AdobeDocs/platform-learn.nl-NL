---
title: Openingspagina's in Adobe Journey Optimizer
description: Openingspagina's in Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
exl-id: bf499aad-91d0-4fb5-a38c-db8fcd56480b
source-git-commit: 83e8418b1a9e5e0e37f97473d2c7539ccd3fd803
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 8%

---

# 3.6.2 Landingspagina&#39;s

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak** zijn.`--aepSandboxName--`

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.6.2.1 Abonnementenlijsten

Het landen van Pagina&#39;s in Adobe Journey Optimizer werken samen met **Lijsten van het Abonnement**. Om opstellings landende pagina&#39;s te plaatsen, moet u **Lijsten van het Abonnement** eerst vormen.

CitiSignal wil hun klanten vragen naar hun interesse in de volgende domeinen:

- Smart Home
- Werk van thuis
- Online gamen

Zodra een klant zijn belangstelling in één van deze domeinen heeft aangegeven, zou die klant aan een specifieke lijst moeten worden toegevoegd zodat zij met specifieke inhoud achteraf als deel van komende campagnes kunnen worden gericht.

U maakt nu 3 abonnementenlijsten.

In het linkermenu, ga naar **Lijsten van het Abonnement**. Klik **creëren abonnementenlijst**.

![Landingspagina&#39;s](./images/lp1.png)

Voor **Titel**, gebruik: `--aepUserLdap--_SL_Interest_in_Smart_Home`.
Voor **Beschrijving**, gebruik: `Interest in Smart Home`.

Klik **voorleggen**.

![Landingspagina&#39;s](./images/lp2.png)

Klik **creëren abonnementenlijst** om een andere lijst tot stand te brengen.

![Landingspagina&#39;s](./images/lp3.png)

Voor **Titel**, gebruik: `--aepUserLdap--_SL_Interest_WFH`.
Voor **Beschrijving**, gebruik: `Interest in Work From Home`.

Klik **voorleggen**.

![Landingspagina&#39;s](./images/lp4.png)

Klik **creëren abonnementenlijst** om een andere lijst tot stand te brengen.

![Landingspagina&#39;s](./images/lp5.png)

Voor **Titel**, gebruik: `--aepUserLdap--_SL_Interest_Online_Gaming`.
Voor **Beschrijving**, gebruik: `Interest in Online Gaming`.

Klik **voorleggen**.

![Landingspagina&#39;s](./images/lp6.png)

U hebt nu de drie lijsten gemaakt die u nodig hebt.

![Landingspagina&#39;s](./images/lp7.png)

## 3.6.2.2 Voorinstelling bestemmingspagina

Als u bestemmingspagina&#39;s in Adobe Journey Optimizer wilt gebruiken, moet u een voorinstelling maken.

In het linkermenu, ga naar **Beleid** > **Kanalen** en selecteer dan **het Bestaan pagina vooraf instelt**.

Klik **creeer het landen van pagina vooraf ingesteld**.

![Landingspagina&#39;s](./images/lp8.png)

Voor het gebied **Naam**, gebruik: `--aepUserLdap-- - CitiSignal LP` en selecteer subdomain dat in uw instantie beschikbaar is.

>[!NOTE]
>
>Als u geen subdomein ziet in uw instantie, raadpleegt u uw AJO-beheerder om er een toe te voegen.

Klik **voorleggen**.

![Landingspagina&#39;s](./images/lp9.png)

De voorinstelling voor de openingspagina is nu gemaakt.

![Landingspagina&#39;s](./images/lp10.png)

## 3.6.2.3 Openingspagina

U kunt nu uw openingspagina maken. In het linkermenu, ga naar **het Beheer van de Inhoud** > **Landing Pagina&#39;s**.

Klik **creëren het landen pagina**.

![Landingspagina&#39;s](./images/lp11.png)

Voor het gebied **Titel**, gebruik: `vangeluw - CitiSignal Interests`. Daarna, selecteer de **Aanvoerende Vooraf ingestelde Pagina** die u in de vorige stap vormde.

Klik **creëren**.

![Landingspagina&#39;s](./images/lp12.png)

Dan moet je dit zien.

![Landingspagina&#39;s](./images/lp13.png)

Verander de gebied **Naam van de Pagina** in `--aepUserLdap-- - CitiSignal Interests`.

Ga deze douanenaam onder **montages van de Toegang** in: `--aepUserLdap---citisignal-interests`.

Klik **Open Designer**.

![Landingspagina&#39;s](./images/lp14.png)

Selecteer **Ontwerp van kras**.

![Landingspagina&#39;s](./images/lp15.png)

Dan moet je dit zien.

![Landingspagina&#39;s](./images/lp16.png)

Voeg een structuurcomponent **1:1 kolom** aan het canvas toe.

![Landingspagina&#39;s](./images/lp17.png)

Voeg een inhoudscomponent **Vorm** aan het canvas toe.

![Landingspagina&#39;s](./images/lp18.png)

Werk het gebied **Etiket** voor **Checkbox 1** bij aan `Keep me updated about CitiSignal's offering for Smart Home`.

Zorg ervoor dat checkbox **Opt binnen als gecontroleerd** wordt toegelaten, en dat **Lijst van het Abonnement** wordt geselecteerd.

Dan, klik **Uitgezochte abonnementenlijst**.

![Landingspagina&#39;s](./images/lp19.png)

Daarna, selecteer de lijst `--aepUserLdap--_SL_Interest_in_Smart_Home` en klik **Uitgezocht**.

![Landingspagina&#39;s](./images/lp20.png)

Klik **+ voeg gebied** toe en selecteer dan **Checkbox**.

![Landingspagina&#39;s](./images/lp21.png)

Dan moet je dit zien.

![Landingspagina&#39;s](./images/lp22.png)

Werk het gebied **Etiket** voor **Checkbox 2** bij aan `Keep me updated about CitiSignal's offering for Work From Home`.

Zorg ervoor dat checkbox **Opt binnen als gecontroleerd** wordt toegelaten, en dat **Lijst van het Abonnement** wordt geselecteerd.

Dan, klik **Uitgezochte abonnementenlijst**.

![Landingspagina&#39;s](./images/lp23.png)

Daarna, selecteer de lijst `--aepUserLdap--_SL_Interest_WFH` en klik **Uitgezocht**.

![Landingspagina&#39;s](./images/lp24.png)

Klik **+ voeg gebied** toe en selecteer dan **Checkbox**.

![Landingspagina&#39;s](./images/lp25.png)

Dan moet je dit zien.

![Landingspagina&#39;s](./images/lp26.png)

Werk het gebied **Etiket** voor **CheckBox 3** aan `Keep me updated about CitiSignal's offering for Online Gaming` bij.

Zorg ervoor dat checkbox **Opt binnen als gecontroleerd** wordt toegelaten, en dat **Lijst van het Abonnement** wordt geselecteerd.

Dan, klik **Uitgezochte abonnementenlijst**.

![Landingspagina&#39;s](./images/lp27.png)

Daarna, selecteer de lijst `--aepUserLdap--_SL_Interest_Online_Gaming` en klik **Uitgezocht**.

![Landingspagina&#39;s](./images/lp28.png)

Dan moet je dit zien.

![Landingspagina&#39;s](./images/lp29.png)

Ga naar het vormgebied **CALL TO ACTION**.

Werk de volgende velden bij:

- **Tekst** - het etiket van de Knoop: `Save`.
- **Bevestiging actie**: uitgezochte **Tekst van de Bevestiging**.
- **Tekst van de Bevestiging**: gebruik: `Thanks for updating your preferences!`
- **actie van de Fout**: uitgezochte **tekst van de Fout**.
- **op foutentekst**: gebruik: `There was an error updating your preferences.`

Klik **sparen** en klik dan de pijl in de hoogste linkerhoek om terug naar het vorige scherm te gaan.

![Landingspagina&#39;s](./images/lp30.png)

Klik **publiceren**.

![Landingspagina&#39;s](./images/lp31.png)

Klik **publiceren** opnieuw.

![Landingspagina&#39;s](./images/lp32.png)

De bestemmingspagina is nu gepubliceerd en kan in een e-mail worden gebruikt.

![Landingspagina&#39;s](./images/lp33.png)

## 3.6.2.4 Openingspagina opnemen in e-mail

In oefening 3.1 creeerde u een reis die `--aepUserLdap-- - Registration Journey` wordt genoemd.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/published.png)

U moet het e-mailbericht in die reis nu bijwerken om de koppeling naar de bestemmingspagina op te nemen.

In het linkermenu, ga naar **Reizen** en klik om de reis `--aepUserLdap-- - Registration Journey` te openen.

![Landingspagina&#39;s](./images/lp34.png)

Klik **Meer...** en selecteer dan **creeer een nieuwe versie**.

![Landingspagina&#39;s](./images/lp35.png)

Klik **creeer een nieuwe versie**.

![Landingspagina&#39;s](./images/lp36.png)

Klik om de **E-mail** actie te selecteren, en dan **te selecteren geef inhoud** uit.

![Landingspagina&#39;s](./images/lp37.png)

Klik **uitgeeft e-maillichaam**.

![Landingspagina&#39;s](./images/lp38.png)

Dan moet je iets dergelijks zien. Voeg een nieuwe structuurcomponent **1:1 kolom** aan het canvas toe.

![Landingspagina&#39;s](./images/lp39.png)

Voeg een nieuwe inhoudscomponent **Tekst** in de pas gecreëerde structuurcomponent toe.

![Landingspagina&#39;s](./images/lp40.png)

Plak de volgende tekst in de **** inhoudscomponent van de Tekst.

`Would you like to hear from us about Smart Home news? Do you work from home and would you like to hear our tips? Or are you an avid online gamer and do you want to receive our game reviews? Click here to update your preferences and interests!`

Maak de tekst zodanig op dat deze er uitziet en selecteer het woord `here` . Klik het **verbindings** pictogram.

Plaats het **Type** van de verbinding aan **het Bestaan pagina** en plaats het gebied **Doel** aan **Lege**.

Klik **uitgeven** pictogram om de het landen pagina te selecteren om te verbinden.

![Landingspagina&#39;s](./images/lp41.png)

Selecteer de openingspagina `--aepUserLdap-- - CitiSignal Interests` . Klik **Uitgezocht**.

![Landingspagina&#39;s](./images/lp42.png)

Dan moet je dit zien. Klik **sparen**.

![Landingspagina&#39;s](./images/lp43.png)

Klik op de pijl in de linkerbovenhoek om terug te keren naar het vorige scherm.

![Landingspagina&#39;s](./images/lp44.png)

Klik op de pijl in de linkerbovenhoek om opnieuw naar het vorige scherm te gaan.

![Landingspagina&#39;s](./images/lp45.png)

Klik **sparen**.

![Landingspagina&#39;s](./images/lp46.png)

Klik **publiceren**.

![Landingspagina&#39;s](./images/lp47.png)

Klik **publiceren** opnieuw.

![Landingspagina&#39;s](./images/lp48.png)

Uw wijzigingen zijn nu gepubliceerd en u kunt uw reis testen.

![Landingspagina&#39;s](./images/lp49.png)

## 3.6.2.5 Test uw reis- en landingspagina

Ga naar [ https://dsn.adobe.com ](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![ DSN ](./../../datacollection/dc1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](../../../getting-started/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](../../../getting-started/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](../../../getting-started/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](../../../getting-started/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden. Ga naar **binnen Teken**

![ DSN ](../../../getting-started/gettingstarted/images/web7.png)

Klik **CREËREN EEN ACCOUNT**. Vul uw details in en klik **Register**.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv9.png)

U wordt nu omgeleid naar de startpagina. Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![ Demo ](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv10.png)

1 minuut nadat je je account hebt gemaakt, ontvang je een e-mail over het aanmaken van je account van Adobe Journey Optimizer.

Klik op de koppeling in de e-mail om uw voorkeuren bij te werken.

![ Opstelling van de Lancering ](./images/email.png)

Vervolgens ziet u het formulier dat u hebt gemaakt. Laat sommige controledozen toe en klik **sparen**.

![ Opstelling van de Lancering ](./images/email1.png)

Vervolgens wordt een bevestigingsbericht weergegeven.

![ Opstelling van de Lancering ](./images/email2.png)

## 3.6.2.6 Rapportage abonnementenlijst

Om de beschikbare rapportering over abonnementenlijsten te bekijken, ga naar **lijsten van het Abonnement** in het linkermenu en klik om één pf te openen de abonnementenlijsten u vóór vormde.

![Landingspagina&#39;s](./images/lp50.png)

Klik **Rapport**.

![Landingspagina&#39;s](./images/lp51.png)

Vervolgens ziet u het overzicht van de lijst, met het aantal personen dat zich erop heeft geabonneerd of dat zich niet heeft geabonneerd.

![Landingspagina&#39;s](./images/lp52.png)

## Volgende stappen

Ga naar [ 3.6.3 AJO en GenStudio for Performance Marketing ](./ex3.md)

Ga terug naar [ Adobe Journey Optimizer: Het Beheer van de inhoud ](./ajocontent.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Een aangepaste webhaak maken en configureren
description: Een aangepaste webhaak maken en configureren
kt: 5342
doc-type: tutorial
exl-id: 80f8ca6d-5540-4c39-89c2-361941fe168b
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%

---

# 2.5.3 Een aangepaste webhaak maken en configureren

## Uw aangepaste webhaak maken

Ga naar [ https://pipedream.com/requestbin ](https://pipedream.com/requestbin). U gebruikte reeds deze toepassing in [ oefent 2.3.6 Doelen SDK ](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-3/ex6.md) uit

Als u die service nog niet hebt gebruikt, maakt u een account en maakt u een werkruimte. Als de werkruimte eenmaal is gemaakt, ziet u iets gelijkaardigs.

Klik **exemplaar** om url te kopiëren. U zult deze url in de volgende oefening moeten specificeren. De URL in dit voorbeeld is `https://eodts05snjmjz67.m.pipedream.net` .

![ demo ](./images/webhook1.png)

Deze website heeft deze website nu voor u gemaakt en u kunt deze webhaak in uw **[!DNL Event Forwarding property]** configureren om het doorsturen van gebeurtenissen te testen.

## Werk uw Event Forwarding-eigenschap bij: Maak een Data Element

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/) en ga naar **Gebeurtenis door:sturen**. Zoek in de eigenschap Event Forwarding en klik erop om deze te openen.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/prop1.png)

In het linkermenu, ga naar **Elementen van Gegevens**. Klik **creëren Nieuw Element van Gegevens**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/de1.png)

U zult dan een nieuw gegevenselement zien om te vormen.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/de2.png)

Maak de volgende selectie:

- Als **Naam**, ga **Gebeurtenis XDM** in.
- Als **Uitbreiding**, uitgezochte **Kern**.
- Als het **Type van Element van Gegevens**, uitgezochte **Weg**.
- Als **Weg**, uitgezochte **Gelezen gegevens van XDM (arc.event.xdm)**. Door deze weg te selecteren, zult u uit de **XDM** sectie van de gebeurtenislading filtreren die door de website of mobiele toepassing in de Rand van Adobe wordt verzonden.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/de3.png)

Nu heb je dit. Klik **sparen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/de3a.png)

>[!NOTE]
>
>In de bovengenoemde weg, wordt een verwijzing gemaakt aan **boog**. **boog** staat voor de Context van het Middel van Adobe en **boog** altijd voor het hoogste beschikbare voorwerp dat in de Server zijcontext beschikbaar is. De verbeteringen en de transformaties kunnen aan dat **boog** voorwerp worden toegevoegd gebruikend de functies van de Server van de Inzameling van Gegevens van Adobe Experience Platform.
>
>In de bovengenoemde weg, wordt een verwijzing gemaakt aan **gebeurtenis**. **gebeurtenis** staat voor een unieke gebeurtenis en de Server van de Inzameling van Gegevens van Adobe Experience Platform zal altijd elke gebeurtenis individueel evalueren. Soms, kunt u een verwijzing naar **gebeurtenissen** in de nuttige lading zien die door de Kant van de Cliënt van SDK van het Web wordt verzonden, maar in de Server van de Inzameling van Gegevens van Adobe Experience Platform, wordt elke gebeurtenis individueel geëvalueerd.

## Werk uw Adobe Experience Platform-eigenschap voor de gegevensverzamelingsserver bij: Een regel maken

In het linkermenu, ga naar **Regels**. Klik **creëren Nieuwe Regel**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl1.png)

U zult dan een nieuwe regel zien om te vormen. Ga de **Naam** in: **Alle Pagina&#39;s**. Voor deze oefening, zult u geen voorwaarde moeten vormen. In plaats daarvan stelt u een handeling in. Klik **+ toevoegen** knoop onder **Acties**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl2.png)

Dan zie je dit. Maak de volgende selectie:

- Selecteer de **Uitbreiding**: **Verbinding van de Wolk van Adobe**.
- Selecteer het **Type van Actie**: **maak Vraag van de Vetch**.

Dat zou u deze **Naam** moeten geven: **de Schakelaar van de Wolk van Adobe - maak Vraag van de Ophalen**. U zou nu dit moeten zien:

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl4.png)

Configureer daarna het volgende:

- Verandering de verzoekmethode van GET in **POST**
- Voer de URL in van de aangepaste webhaak die u in een van de vorige stappen hebt gemaakt en die er als volgt uitziet: `https://eodts05snjmjz67.m.pipedream.net`

Dat zou u nu moeten doen. Daarna, ga naar **Lichaam**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl6.png)

Dan zie je dit. Klik op het pictogram voor het gegevenselement zoals hieronder aangegeven.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl7.png)

In popup, selecteer de gebeurtenis van het gegevenselement **XDM** die u in de vorige stap creeerde. Klik **Uitgezocht**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl8.png)

Dan zie je dit. Klik **houden Veranderingen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl9.png)

Dan zie je dit. Klik **sparen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl10.png)

U hebt nu uw eerste regel in een Gebeurtenis gevormd die bezit door:sturen. Ga naar **het Publiceren Stroom** om uw veranderingen te publiceren.
Open uw bibliotheek van de Ontwikkeling **Belangrijkste** door **te klikken geef** zoals vermeld uit.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl11.png)

Klik **toevoegen Alle Gewijzigde Middelen** knoop, waarna zult u uw Regel en Element van Gegevens in deze bibliotheek zien verschijnen. Daarna, klik **sparen &amp; bouwt voor Ontwikkeling**. Uw wijzigingen worden nu geïmplementeerd.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl13.png)

Na een paar minuten zult u zien dat de implementatie klaar is en klaar om te worden getest.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/rl14.png)

## Uw configuratie testen

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

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](../../../getting-started/gettingstarted/images/web7.png)

Wanneer u uw browser de Mening van de Ontwikkelaar opent, kunt u de verzoeken van het Netwerk zoals hieronder vermeld inspecteren. Wanneer u het filter **gebruikt in wisselwerking treedt**, zult u de netwerkverzoeken zien die door de Cliënt van de Inzameling van Gegevens van Adobe Experience Platform aan de Rand van Adobe worden verzonden.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook1.png)

Als u onbewerkte lading selecteert, ga [ https://jsonformatter.org/json-pretty-print ](https://jsonformatter.org/json-pretty-print) en kleef de nuttige lading. Klik **Minify/Beautify**. U zult dan de nuttige lading JSON, het **gebeurtenissen** voorwerp en het **xdm** voorwerp zien. In één van de vorige stappen, toen u het Element van Gegevens bepaalde, gebruikte u de verwijzing **arc.event.xdm**, die in u het **xdm** voorwerp van deze nuttige lading zal resulteren ontleden.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook2.png)

Schakelaar uw mening aan uw douane webhaak [ https://pipedream.com/requestbin ](https://pipedream.com/requestbin) die u in één van de vorige stappen gebruikte. U zou nu een mening gelijkend op dit moeten hebben, met netwerkverzoeken die in het linkermenu worden getoond. U ziet de **xdm** nuttige lading die uit het netwerkverzoek filterde dat hierboven werd getoond.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook3.png)

De rol neer een beetje in de nuttige lading om de paginanaam te vinden, die in dit geval **huis** is.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook4.png)

Als u nu door de website navigeert, zult u extra netwerkverzoeken zien die op deze douanewebsite in real time beschikbaar worden.

![ de Opstelling van de Inzameling van Gegevens van Adobe Experience Platform ](./images/hook5.png)

U hebt nu de server-side Gebeurtenis gevormd door:sturen van de nuttige ladingen van SDK/XDM van het Web aan een externe douane webhaak. In de volgende oefeningen, zult u een gelijkaardige benadering vormen, en u zult die zelfde gegevens naar Google Cloud Platform en AWS verzenden.

## Volgende stappen

Ga naar [ 2.5.4 Voorwaartse gebeurtenissen aan GCP Pub/Sub ](./ex4.md){target="_blank"}

Ga terug naar [ Verbindingen van Real-Time CDP: Gebeurtenis door:sturen ](./aep-data-collection-ssf.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

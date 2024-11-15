---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Inleiding aan de Inzameling van Gegevens van Adobe Experience Platform
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Inleiding aan de Inzameling van Gegevens van Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 391c79d6-9c42-465e-bce8-60fa6474979c
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 0%

---

# 1.1.3 - Inleiding tot Adobe Experience Platform-gegevensverzameling

## Context

Laten we nu dieper kijken naar de bouwstenen van Adobe Experience Platform Data Collection, om te begrijpen wat er op uw demo-website is geïnstalleerd. U zult een dichtere blik bij de Uitbreiding van SDK van het Web van Adobe Experience Platform hebben, zult u een gegevenselement en een regel vormen en u zult leren hoe te om een bibliotheek te publiceren.

## 1.1.3.1 - Adobe Experience Platform Web SDK Extension

Een extensie is een set verpakte code waarmee de interface van Adobe Experience Platform Data Collection en de bibliotheekfunctionaliteit worden uitgebreid. Adobe Experience Platform Data Collection is het platform en extensies zijn vergelijkbaar met apps die op het platform worden uitgevoerd. Alle extensies die in de zelfstudie worden gebruikt, worden gemaakt en beheerd door Adobe, maar derden kunnen hun eigen extensies maken om de hoeveelheid aangepaste code te beperken die Adobe Experience Platform-gebruikers moeten beheren.

Ga naar [ de Inzameling van Gegevens van Adobe Experience Platform ](https://experience.adobe.com/launch/) en selecteer **Markeringen**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![ pagina van Eigenschappen ](./images/launch1.png)

In **Aan de slag**, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: voor de website en voor mobiele app. Zoek naar `--aepUserLdap--` in het vak **[!UICONTROL Search]** .
Klik om het **bezit te openen 0} van het Web {.**

![ vakje van het Onderzoek ](./images/property6.png)



U zult dan de pagina van het Overzicht van het Bezit zien. Klik op **[!UICONTROL Extensions]** in het linkerspoor, dan klik op **het Web SDK van Adobe Experience Platform** en klik dan **[!UICONTROL Configure]**.

![ pagina van het Overzicht van het Bezit ](./images/property7.png)

Welkom bij de Adobe Experience Platform Web SDK! Hier kunt u de uitbreiding met DataStream vormen u in [ het Begonnen Worden ](./../../../modules/gettingstarted/gettingstarted/ex2.md) evenals één of andere geavanceerdere configuratie creeerde.

Het standaardranddomein is altijd **edge.adobedc.net**. Als u een CNAME-configuratie hebt geïmplementeerd in uw Adobe Experience Cloud- of Adobe Experience Platform-omgeving, moet u de **[!UICONTROL Edge Domain]** bijwerken.

Als het Edge-domein van de instantie afwijkt van het standaarddomein, moet u het Edge-domein hier bijwerken. Als u niet zeker bent, gebruik het standaarddomein. Een randdomein maakt het mogelijk om een 1st partij volgende server te vormen, die dan een configuratie CNAME in het achterste eind gebruikt om gegevens te verzekeren wordt verzameld in Adobe.

![ het huis van Uitbreidingen ](./images/property9edgedomain.png)

Onder **[!UICONTROL Datastreams]**, selecteerde u reeds uw gegevensstroom in **Begonnen het Worden** sectie. U hebt deze gegevensstroom geselecteerd: `--aepUserLdap-- - Demo System Datastream` in de lijst in het vak **[!UICONTROL Datastream]** voor elke omgeving.

Klik op **[!UICONTROL Save]** om terug te gaan naar de weergave Extensies.

![ het huis van Uitbreidingen ](./images/property9edge.png)

## 1.1.3.2 Gegevenselementen

Gegevenselementen zijn de bouwstenen voor uw gegevenswoordenboek (of gegevenskaart). Gebruik gegevenselementen om gegevens te verzamelen, te organiseren en te leveren over marketing- en advertentietechnologie.

Eén gegevenselement is een variabele waarvan de waarde kan worden toegewezen aan querytekenreeksen, URL&#39;s, cookie-waarden, JavaScript-variabelen enzovoort. U kunt naar deze waarde verwijzen met de variabelenaam in de hele Adobe Experience Platform-gegevensverzameling. Deze verzameling gegevenselementen wordt het woordenboek met gedefinieerde gegevens dat u kunt gebruiken om uw regels (gebeurtenissen, voorwaarden en handelingen) samen te stellen. Dit gegevenswoordenboek wordt door alle Adobe Experience Platform-gegevensverzameling gedeeld voor gebruik met extensies die u aan uw eigenschap hebt toegevoegd.

U gaat nu een reeds bestaand gegevenselement in een vriendschappelijk formaat van SDK van het Web uitgeven.

Klik op Data Elements in de linkertrack die naar de pagina Data Elements moet worden verplaatst.

![ Homepage van de Elementen van Gegevens ](./images/dataelement1.png)

>[!NOTE]
>
>U bewerkt alleen een gegevenselement in deze oefening, maar u kunt de knop **[!UICONTROL Add Data Element]** op deze pagina zien, die wordt gebruikt om een nieuwe variabele toe te voegen aan het gegevenswoordenboek. Dit kan vervolgens worden gebruikt in de hele gegevensverzameling van Adobe Experience Platform. U kunt naar sommige andere reeds bestaande gegevenselementen kijken, meestal met lokale opslag als gegevensbron.

In de onderzoeksbar, type **XDM - de Mening van het Product** en klik op het Element van Gegevens het terugkeert.

![ Onderzoek naar ruleArticlePages ](./images/dataelement2.png)

Dit scherm toont het XDM Voorwerp u zult uitgeven. Het model van de Gegevens van de Ervaring (XDM) is een concept dat veel verder door dit Technische Leerprogramma zal worden onderzocht, maar voor nu is het genoeg om het als formaat te begrijpen dat Adobe Experience Platform Web SDK vereist. U voegt wat meer informatie toe aan de gegevens die op artikelpagina&#39;s van de demo-website worden verzameld.

Klik plus knoop naast **Web** bij de bodem van de boom.

Klik plus knoop naast **webPageDetails**.

Klik op **siteSection**. U ziet nu dat **siteSection** nog niet met om het even welk gegevenselement verbonden is. Laten we dat veranderen.

![ navigeer aan de plaatssectie ](./images/dataelement3.png)

Schuif omhoog en voer de tekst in `%Product Category%` . Klik op **[!UICONTROL Save]**.

![ sparen ](./images/dataelement4.png)

Op dit punt, is de Uitbreiding van SDK van het Web van Adobe Experience Platform geïnstalleerd en u hebt een gegevenselement bijgewerkt om gegevens tegen een structuur te verzamelen XDM. Daarna, controleren de regels die gegevens op de correcte tijd zullen verzenden.

## 1.1.3.3 Regels

Adobe Experience Platform Data Collection is een op regel gebaseerd systeem. Er wordt gezocht naar gebruikersinteractie en bijbehorende gegevens. Wanneer aan de criteria die in uw regels worden geschetst wordt voldaan, teweegbrengt de regel de uitbreiding, het manuscript, of cliënt-zijcode in werking u identificeerde.

Bouw regels om de gegevens en de functionaliteit van marketing en advertentietechnologie te integreren die ongelijksoortige producten in één enkele oplossing verenigt.

Laten we de regel die gegevens verzendt op artikelpagina&#39;s opsplitsen.

Klik op **[!UICONTROL Rules]** in de linkertrack.

**[!UICONTROL Search]** for `Product View` .

Klik op de regel die is teruggekeerd.

![ Media - de regelonderzoek van de Pagina&#39;s van het Artikel ](./images/rule1.png)

Laten we eens kijken naar de afzonderlijke elementen waaruit deze regel bestaat.

Voor alle regels: als een opgegeven **[!UICONTROL Event]** voorkomt, wordt de instructie **[!UICONTROL Conditions]** geëvalueerd, en vindt de opgegeven **[!UICONTROL Actions]** plaats indien nodig.

![ Media - de regel van de Pagina&#39;s van het Artikel ](./images/rule2.png)

Klik op de Kern van de Gebeurtenis **- de Gebeurtenis van de Douane**. Dit is de weergave die wordt geladen.

Klik op het **Type van Gebeurtenis** drop down.

Dit maakt een lijst van sommige standaardinteractie u kunt gebruiken om de Inzameling van Gegevens van Adobe Experience Platform te signaleren om de acties in werking te stellen, als de voorwaarden waar zijn.

![Gebeurtenissen](./images/rule3.png)

Klik op **[!UICONTROL Cancel]** om terug te gaan naar de regel.

Klik op de Actie **verzenden de Gebeurtenis van de Ervaring van de Mening van het Product**.

![ verzendt de actie van de Gebeurtenis ](./images/rule5a.png)

Hier kunt u de gegevens zien die door de SDK van het Web van Adobe Experience Platform naar de rand worden verzonden. Specifieker, gebruikt dit de **legering** **[!UICONTROL Instance]** van het Web SDK. De gebeurtenis **[!UICONTROL Type]** wordt geplaatst aan **het Productweergaven van Commerce (Cart)** en de Gegevens XDM u verzendt is **XDM - het gegevenselement van de Mening van het Product** u vroeger veranderde.

![ verzendt de actie van de Gebeurtenis ](./images/rule5.png)

Nu u naar de Regel hebt gekeken, kunt u al uw veranderingen in de Inzameling van Gegevens van Adobe Experience Platform publiceren.

## 1.1.3.4 Publish in een bibliotheek

Tot slot om de regel en het gegevenselement te bevestigen u enkel hebt bijgewerkt, moet u een bibliotheek publiceren die de uitgegeven punten in ons bezit bevatten. In de sectie **[!UICONTROL Publishing]** van de Adobe Experience Platform-gegevensverzameling moeten enkele snelle stappen worden uitgevoerd.

Klik op **[!UICONTROL Publishing Flow]** in de linkernavigatie

Klik op de bestaande bibliotheek, genoemd **Hoofd**.

![ de toegang van de Bibliotheek ](./images/publish1.png)

Klik **toevoegen Alle Gewijzigde Middelen** knoop. Volgende,
Klik **sparen &amp; bouwt voor Ontwikkeling** knoop.

![ de toegang van de Bibliotheek ](./images/publish1a.png)

Het kan enkele minuten duren voordat de bibliotheek is gemaakt. Als de bibliotheek is voltooid, wordt links van de naam van de bibliotheek een groene stip weergegeven.

![ de Bibliotheek van de Inhoud ](./images/publish2.png)

Zoals u op het het Publiceren scherm van de Stroom kunt zien, is er veel meer aan het het publiceren proces in de Inzameling van Gegevens van Adobe Experience Platform die buiten het werkingsgebied van dit leerprogramma is. We gaan gewoon één bibliotheek gebruiken in onze ontwikkelomgeving.

Volgende Stap: [ 1.1.4 Cliënt-zij de Inzameling van de Gegevens van het Web ](./ex4.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)

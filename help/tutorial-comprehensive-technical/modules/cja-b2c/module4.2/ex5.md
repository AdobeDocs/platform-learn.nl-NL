---
title: Gegevens van Googles Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector - Gegevens van Googles Analytics analyseren met Customer Journey Analytics
description: Gegevens van Googles Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector - Gegevens van Googles Analytics analyseren met Customer Journey Analytics
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '3338'
ht-degree: 0%

---

# 4.2.5 Gegevens van Googles Analytics analyseren met behulp van Customer Journey Analytics

## Doelstellingen

- Verbind onze Dataset BigQuery aan Customer Journey Analytics (CJA)
- Verbind en sluit zich aan bij Googles Analytics met Loyalty Gegevens.
- Bekend worden met de gebruikersinterface van CJA

## 4.2.5.1 Verbinding maken

Ga naar [ analytics.adobe.com ](https://analytics.adobe.com) om tot Customer Journey Analytics toegang te hebben.

![ demo ](./images/1a.png)

Op de homepage van de Customer Journey Analytics, ga naar **Verbindingen**.

![ demo ](./images/conn1.png)

Hier kunt u alle verschillende verbindingen zien die tussen CJA en Platform worden gemaakt. Deze verbindingen hebben hetzelfde doel als rapportsuites in Adobe Analytics. De gegevensverzameling is echter totaal anders. Alle gegevens komen uit de datasets van Adobe Experience Platform.

![ demo ](./images/2.png)

Klik **creëren nieuwe verbinding**.

![ demo ](./images/conn3.png)

U zult dan **** UI zien creëren Verbinding.

![ demo ](./images/5.png)

Ten eerste moet u de juiste sandbox selecteren om te gebruiken. Selecteer de sandbox in het menu van de sandbox, die `--aepSandboxId--` moet zijn. In dit voorbeeld, is de zandbak aan gebruik **AEP Enablement FY21**.

![ demo ](./images/cjasb.png)

Nadat u de sandbox hebt geselecteerd, worden de beschikbare gegevenssets bijgewerkt.

![ demo ](./images/cjasb1.png)

In het linkermenu, kunt u alle beschikbare datasets van Adobe Experience Platform zien. Zoek naar de dataset `Demo System - Event Dataset for BigQuery (Global v1.1)`. Klik **+** om de dataset aan deze verbinding toe te voegen.

![ demo ](./images/6.png)

Na het toevoegen van het, zult u de dataset binnen de verbinding zien.

U moet nu **identiteitskaart van de Persoon** selecteren. Gelieve te verzekeren **loyaltyId** als identiteitskaart van de Persoon wordt geselecteerd.

![ demo ](./images/8.png)

U zult nu de gegevens van de Interactie van de Website van Googles Analytics met een andere dataset van Adobe Experience Platform verrijken.

Zoek naar de dataset `Demo System - Profile Dataset for Loyalty (Global v1.1)` gegevensreeks en voeg het aan deze verbinding toe.

![ demo ](./images/10.png)

U zult dan dit zien:

![ demo ](./images/10a.png)

Om beide datasets samen te voegen, moet u identiteitskaart van de a **Persoon** selecteren die het zelfde type van IDs bevat. De dataset `Demo System - Profile Dataset for Loyalty (Global v1.1)` gebruikt **loyaltyId** als identiteitskaart van de Persoon, die het zelfde type van IDs zoals `Demo System - Event Dataset for BigQuery (Global v1.1)` bevat, die ook **loyaltyId** als identiteitskaart van de Persoon gebruikt.

![ demo ](./images/12.png)

Klik **daarna**.

![ demo ](./images/14.png)

U zult dan dit zien:

![ demo ](./images/15.png)

Hier moet u een naam aan uw verbinding geven.

Gebruik deze naamgevingsconventie: `ldap - GA + Loyalty Data Connection` .

Voorbeeld: `vangeluw - GA + Loyalty Data Connection`

Alvorens te voltooien, gelieve **ook te activeren automatisch alle nieuwe gegevens voor alle datasets in deze verbinding, die vandaag beginnen.** zoals in de onderstaande afbeelding.

![ demo ](./images/16.png)

Hierdoor wordt om de 60 minuten een gegevensstroom van Adobe Experience Platform naar CJA gestart, maar met grote hoeveelheden gegevens kan dit tot 24 uur duren.

U moet ook backfill historische gegevens, zodat gelieve te controleren checkbox voor **invoer alle bestaande gegevens** en **minder dan 1 miljoen** selecteren onder **Gemiddeld aantal dagelijkse gebeurtenissen**.

![ demo ](./images/17.png)

Na het creëren van uw **Verbinding** kan het een paar uren nemen alvorens uw gegevens in CJA beschikbaar zijn.

Klik **sparen** en ga naar de volgende oefening.

![ demo ](./images/cjasave.png)

U zult dan uw verbinding in de lijst van beschikbare verbindingen zien.

![ demo ](./images/18.png)

## 4.2.5.2 Een gegevensweergave maken

Als de verbinding tot stand is gebracht, kunt u nu de visualisatie beïnvloeden. Een verschil tussen Adobe Analytics en CJA is dat CJA een gegevensweergave nodig heeft om de gegevens vóór visualisatie te kunnen opschonen en voorbereiden.

Een gegevensmening is gelijkaardig aan het concept virtuele rapportsuites in Adobe Analytics, waar u context-bewuste bezoekdefinities bepaalt, filtrerend en ook, hoe de componenten worden geroepen.

U hebt minimaal één gegevensweergave per verbinding nodig. Nochtans, voor sommige gebruik-gevallen, is het groot om veelvoudige gegevensmeningen voor de zelfde verbinding te hebben, met het doel om verschillende inzichten aan verschillende teams te geven.

Als u uw bedrijf gegevensgedreven wilt worden, zou u moeten aanpassen hoe de gegevens in elk team worden bekeken. Enkele voorbeelden:

- UX-meetgegevens alleen voor het UX-ontwerpteam
- Gebruik dezelfde namen voor KPI&#39;s en Metriek voor Googles Analytics als voor Customers Journey Analytics, zodat het digitale analyseteam slechts één taal kan spreken.
- gegevensweergave gefilterd om bijvoorbeeld gegevens weer te geven voor 1 markt, of 1 merk, of alleen voor mobiele apparaten.

Voor het **scherm van Verbindingen**, controleer checkbox voor de verbinding u enkel creeerde.

![ demo ](./images/exta.png)

Nu klik **creeer de Mening van Gegevens**.

![ demo ](./images/extb.png)

U zult aan **worden opnieuw gericht creeer het werkschema van de Mening van Gegevens**.

![ demo ](./images/extc.png)

U kunt de basisdefinities voor uw gegevensmening nu vormen. Dingen zoals Tijdzone, Sessietime-out of het filteren van de gegevensweergave (het segmenteringsonderdeel dat lijkt op Virtuele rapportsets in Adobe Analytics).

De **Verbinding** u in de vorige oefening creeerde is reeds geselecteerd. Uw verbinding heeft de naam `ldap - GA + Loyalty Data Connection` .

![ demo ](./images/ext5.png)

Geef de gegevensweergave vervolgens een naam die volgt op de naamgevingsconventie: `ldap - GA + Loyalty Data View` .

Voer dezelfde waarde in voor de beschrijving: `ldap - GA + Loyalty Data View` .

Voordat we een analyse of visualisatie kunnen uitvoeren, moeten we een gegevensweergave maken met alle velden, afmetingen en metriek en hun attributie-instellingen.

| Veld | Naamgevingsconventie | Voorbeeld |
| ----------------- |-------------|-------------|  
| Naam van verbinding | LDAP - GA + Loyalty Data View | vangeluw - GA + Loyalty Data View |
| Beschrijving | LDAP - GA + Loyalty Data View | vangeluw - GA + Loyalty Data View |

![ demo ](./images/22.png)

Klik **sparen en ga** verder.

![ demo ](./images/23.png)

U kunt nu componenten toevoegen aan uw gegevensweergave. Zoals u kunt zien, worden sommige metriek en afmetingen automatisch toegevoegd.

![ demo ](./images/24.png)

Voeg de volgende componenten aan de gegevensmening toe:

| Componentnaam | Componenttype | Componentpad |
| -----------------|-----------------|-----------------|
| niveau | Dimension | _experiencePlatform.loyaltyDetails.level |
| punten | Metrisch | _experiencePlatform.loyaltyDetails.points |
| commerce.checkouts.value | Metrisch | commerce.checkouts.value |
| commerce.productListRemovals.value | Metrisch | commerce.productListRemovals.value |
| commerce.productListAdds | Metrisch | commerce.productListAdds |
| commerce.productViews.value | Metrisch | commerce.productViews.value |
| commerce.purchases.value | Metrisch | commerce.purchases.value |
| web.webPageDetails.pageViews | Metrisch | web.webPageDetails.pageViews |
| Transactie-id | Dimension | commerce.order.payments.transactionID |
| channel.mediaType | Dimension | channel.mediaType |
| channel.typeAtSource | Dimension | channel.typeAtSource |
| Code bijhouden | Dimension | marketing.trackingCode |
| onbeschaamd | Dimension | _ExperiencePlatform.identification.core.gaid |
| web.webPageDetails.name | Dimension | web.webPageDetails.name |
| Type gebeurtenis | Dimension | eventType |
| Leverancier | Dimension | environment.browserDetails.vendor |
| Id | Dimension | _id |
| Tijdstempel | Dimension | tijdstempel |
| Type | Dimension | device.type |
| loyaltyId | Dimension | _ExperiencePlatform.identification.core.loyaltyId |

Dan heb je het volgende:

![ demo ](./images/25.png)

Vervolgens moet u de vriendelijke naam wijzigen van enkele van de bovenstaande metriek en dimensies, zodat u deze eenvoudig kunt gebruiken wanneer u de analyse maakt. Om dat te doen, selecteer metrisch of afmeting en werk het **gebied van de Naam** zoals vermeld in hieronder beeld bij.

![ demo ](./images/25a.png)

| Oorspronkelijke naam component | Weergavenaam |
| -----------------|-----------------|
| niveau | Loyaliteitsniveau |
| punten | Loyalty-punten |
| commerce.checkouts.value | Afbeeldingen |
| commerce.productListRemovals.value | Winkelwagentjes |
| commerce.productListAdds | Extra winkelwagentjes |
| commerce.productViews.value | Productweergaven |
| commerce.purchases.value | Aankopen |
| web.webPageDetails.pageViews | Paginaweergaven |
| channel.mediaType | Traffic Medium |
| channel.typeAtSource | Traffic Source |
| Code bijhouden | Marketingkanaal |
| onbeschaamd | Googles Analytics-id |
| Naam | Paginatitel |
| Leverancier | Browser |
| Type | Apparaattype |
| loyaltyId | Loyalty-id |

Dan heb je iets als dit:

![ demo ](./images/25b.png)

Daarna, moet u sommige veranderingen in de Persoon en context van de Zitting voor sommige van deze componenten aanbrengen door de **Montages van de Attributie** te veranderen.

![ demo ](./images/25c.png)

Gelieve te veranderen de **Montages van de Attributie** voor de hieronder componenten:

| Component |
| -----------------|
| Traffic Source |
| Marketingkanaal |
| Browser |
| Traffic Medium |
| Apparaattype |
| Googles Analytics-id |
| Loyalty-id |
| Loyaliteitsniveau |
| Loyalty-punten |

Om dat te doen, selecteer de component, klik **model van de douaneattributie van het Gebruik** en plaats het **Model** aan **Laatste Aanraak**, en de **Vervalsing** aan **Persoon (Meldend Venster)**. Herhaal dit voor alle bovengenoemde componenten.

![ demo ](./images/27a.png)

Na het aanbrengen van de veranderingen in attributie montages voor alle bovengenoemde componenten, zou u deze mening dan moeten hebben:

![ demo ](./images/27.png)

Uw gegevensweergave is nu geconfigureerd. Klik **sparen**.

![ demo ](./images/30.png)

U kunt nu de gegevens van Googles Analytics analyseren in Adobe Analytics Analysis Workspace. Laten we naar de volgende oefening gaan.

## 4.2.5.3 Uw project maken

In Customer Journey Analytics, ga naar **Projecten**.

![ demo ](./images/pro1.png)

U zult dan dit zien:

![ demo ](./images/pro2.png)

Creeer een Project door **te klikken leidt tot Nieuw Project**.

![ demo ](./images/pro3.png)

U hebt nu een leeg project:

![ demo ](./images/pro4.png)

Sla eerst het project op en geef het een naam. U kunt de volgende opdracht gebruiken om op te slaan:

| OS | Korte snede |
| ----------------- |-------------| 
| Windows | Control + S |
| Mac | Command + S |

U ziet deze pop-up:

![ demo ](./images/prsave.png)

Gebruik deze naamgevingsconventie:

| Naam | Beschrijving |
| ----------------- |-------------| 
| ldap - GA + Loyalty Workspace | ldap - GA + Loyalty Workspace |

Daarna, klik **sparen Project**.

![ demo ](./images/prsave2.png)

Selecteer vervolgens de juiste gegevensweergave in de rechterbovenhoek van het scherm. Dit is de gegevensweergave die u in de vorige exercitie hebt gemaakt, met de naamgevingsconventie `ldap - GA + Loyalty Data View` . In dit voorbeeld is de gegevensweergave die moet worden geselecteerd `ldap - GA + Loyalty Data View` .

![ demo ](./images/prdvlist.png)

![ demo ](./images/prdv.png)

### 12.5.3.1 Vrije-vormtabellen

Vrije-vormtabellen werken min of meer als draaitabellen in Excel. U kiest iets van de linkerbar en u sleept en laat vallen het in de Vrije vorm en u zult een lijstrapport krijgen.

Vrije-vormtabellen zijn bijna oneindig. U kunt (bijna) om het even wat doen en dit brengt zoveel waarde in vergelijking met Googles Analytics (aangezien dit hulpmiddel sommige analysebeperkingen heeft). Dit is een van de redenen om gegevens van Googles Analytics in een ander analysehulpmiddel te laden.

Laat twee voorbeelden zien waar u SQL, BigQuery en wat tijd moet gebruiken om eenvoudige vragen te beantwoorden die niet mogelijk zijn om binnen de Googles Analytics UI of de Studio van Gegevens van Google te doen:

- Hoeveel mensen komen aan de controle van Safari Browser die door marketing kanaal wordt verdeeld? Gelieve te zien dat metrische checkout door Browser Safari wordt gefiltreerd. We hebben net de variabele Browser = Safari gesleept en neergezet boven op de uitcheckkolom.

- Als analist kan ik zien dat het Social Marketing Channel lage omzettingen heeft. Ik gebruik de kenmerk Last Touch standaard, maar hoe zit het met First Touch? De metrische instellingen worden weergegeven wanneer u de muis boven metrische instellingen houdt. Daar kan ik het gewenste attributiemodel selecteren. U kunt Attribution in GA (niet in gegevensstudio) als standalone activiteit doen, maar u kunt geen andere metriek of dimensies hebben die niet aan attributieanalyse binnen de zelfde lijst verwant zijn.

Laten we deze vragen en nog wat meer beantwoorden met Analysis Workspace in CJA.

Eerst, selecteer de juiste datumwaaier (**Laatste 53 volledige weken**) op de rechterkant van het paneel.

![ demo ](./images/pro11.png)

Dan klik **toepassen** om de datumwaaier toe te passen. Onthoud deze stap voor volgende oefeningen.

![ demo ](./images/apply.png)

>[!NOTE]
>
>Als u enkel de **verbinding van Gegevens** creeerde en **mening van Gegevens** u een paar uren zou kunnen moeten wachten. CJA heeft enige tijd nodig om historische gegevens terug te vullen wanneer er een enorme hoeveelheid gegevensverslagen is.

Laten wij wat dimensies en metriek slepen en laten vallen om de kanalen van de Marketing te analyseren. Eerst gebruik het afmetings **In de handel brengen Kanaal** en sleep en laat vallen het aan het canvas van de **Vrije lijst van de Vorm**. (Klik op **tonen allen** in het geval u metrisch onmiddellijk in het menu van Metriek niet ziet)

![ demo ](./images/pro14.png)

U zult dan dit zien:

![ demo ](./images/pro14a.png)

Vervolgens moet u de metriek toevoegen aan de tabel Vrije vorm. U zou deze Metriek moeten toevoegen: **Mensen**, **Sessies**, **de Kijken van het Product**, **Controles**, **Aankopen**, **Tarief van de Omzetting** (Berekend Metrisch).

Alvorens u dat kunt doen, moet u het Berekende Metrische **Tarief van de Omzetting** tot stand brengen. Klik hiertoe op het pictogram **+** naast Metrisch:

![ demo ](./images/procalc1.png)

Als naam voor Berekend Metrisch, gebruik **Tarief van de Omzetting**. Dan sleep de metrieke **aankoop** en **Zittingen** op het canvas. Plaats **Formaat** aan **Percentage** en **Decimale Plaatsen** aan **2**. Tot slot klik **sparen**.

![ demo ](./images/procalc2.png)

Daarna, om al deze Metriek in de **Vrije Lijst** te gebruiken, sleep en laat vallen hen één voor één op de **Vrije Lijst van de Vorm**. Zie het onderstaande voorbeeld.

![ demo ](./images/pro16.png)

U zult eindigen met een tabel als deze:

![ demo ](./images/pro16a.png)

Zoals hierboven vermeld, **de lijsten van de Vrije vorm** geven u de vrijheid u diepe duikanalyse moet uitvoeren. U kunt bijvoorbeeld elk ander Dimension kiezen om een specifieke metrische waarde in de tabel op te splitsen.

Als voorbeeld, ga naar afmetingen en onderzoek en selecteer de **Browser** variabele.

![ demo ](./images/new1.png)

Vervolgens ziet u een overzicht van de beschikbare waarden voor dit Dimension.

![ demo ](./images/new2.png)

Kies het Dimension **Safari** en sleep en laat vallen het bovenop een Metrisch, bijvoorbeeld **Controles**. U zult dan dit zien:

![ demo ](./images/new3.png)

Als u dit doet, hebt u zojuist een potentiële vraag beantwoord die u had: hoeveel mensen komen bij de kassa met Safari, gesplitst naar Marketing Channel?

Laten we nu de Attribution-vraag beantwoorden.

Vind de **metrisch van de Aankoop** in de lijst.

![ demo ](./images/pro20.png)

Beweeg over metrisch en a **pictogram van Montages** zal verschijnen. Klik erop.

![ demo ](./images/pro21.png)

Er wordt een contextueel menu weergegeven. Controleer checkbox voor **niet-gebrek attributiemodel**.

![ demo ](./images/pro22.png)

In popup zult u zien, kunt u de attributiemodellen en het raadplegingsvenster gemakkelijk veranderen (dat vrij complex is om met SQL te bereiken).

![ demo ](./images/pro23.png)

Selecteer **Eerste Aanraak** als uw attributiemodel.

![ demo ](./images/pro24.png)

Kies **Persoon** voor het Venster van de Lookback.

![ demo ](./images/pro25.png)

Klik nu **toepassen**.

![ demo ](./images/pro26.png)

U kunt nu zien dat het attributiemodel voor die bepaalde metrische waarde nu First Touch is.

![ demo ](./images/pro27.png)

U kunt net zo veel uitsplitsen als u wilt, zonder beperkingen van typen variabelen, segmenten, dimensies of datumbereiken.

Nog iets bijzonders is de mogelijkheid om zich bij elke dataset van Adobe Experience Platform aan te sluiten om de digitale gedragsgegevens van Googles Analytics te verrijken. Bijvoorbeeld, off-line, vraag centrum, loyaliteit of CRM gegevens.

Om die functionaliteit te tonen, vormen wij uw eerste uitsplitsing die off-line gegevens met online gegevens combineert. Kies het afmetings **Niveau van de Loyalty** en sleep en laat vallen het op om het even welk **Marketing Kanaal**, bijvoorbeeld, **Organic Onderzoek**:

![ demo ](./images/pro28.png)

Daarna, analyseren welk **Type van Apparaat** door klanten wordt gebruikt die aan de plaats gebruikend **biologisch Onderzoek** met a **Niveau van de Loyaliteit** kwamen dat **** Bronze is. Neem het Type van Apparaat van het Dimension **** en sleep en laat vallen het op **Bronze**. U zult dan dit zien:

![ demo ](./images/pro29.png)

Je ziet dat voor je eerste uitsplitsing Loyalty Level wordt gebruikt. Deze afmeting komt uit een verschillende dataset en verschillend schema dan die u voor de schakelaar BigQuery gebruikte. Identiteitskaart van de Persoon **loyaltyID** (Systeem van de Manifestatie - het Schema van de Gebeurtenis voor BigQuery (Globale v1.1)) en **loyaltyID** (het Systeem van de Manifest - het Schema van het Profiel voor Loyalty (Globale v1.1)) passen met elkaar aan. Daarom kunt u de Gebeurtenissen van de Ervaring van Googles Analytics met de Gegevens van het Profiel van het Schema van de Loyaliteit combineren.

We kunnen de rijen blijven splitsen met segmenten of specifieke datumbereiken (misschien om bepaalde tv-campagnes te weerspiegelen) om vragen te stellen aan de Customer Journey Analytics en de antwoorden onderweg te krijgen.

Het bereiken van het zelfde eindresultaat met SQL en dan een derdevisualisatiehulpmiddel is vrij een uitdaging. Vooral als je vragen stelt en probeert de antwoorden direct te krijgen. De Customer Journey Analytics heeft deze uitdaging niet en staat de Analysten van Gegevens toe om de gegevens flexibel en in real time te vragen.

## 4.2.5.3.2 Trechter- of valutanotanalyse

De trechters zijn een groot mechanisme om de belangrijkste stappen in een klantenreis te begrijpen. Deze stappen kunnen ook afkomstig zijn van offline interacties (bijvoorbeeld vanuit het callcenter) en vervolgens kunt u ze combineren met digitale aanraakpunten in dezelfde trechter.

Met Customer Journey Analytics kun je dat doen en nog veel meer. Als u Module 13 herinnert, wij waar het mogelijk is om met de rechtermuisknop aan te klikken en dingen te doen zoals:

- Analyseren waar de gebruikers naar toe gaan na een uitvalstap
- Een segment maken van een willekeurig punt in de trechter
- Zie Trend in om het even welk stadium in een Grafiek van de Lijn visualisatie


Laten we nog iets zien wat je kunt doen: Hoe is mijn reis van de Klant deze maand in vergelijking met de vorige maand? Hoe zit het met mobiel versus desktop?

Onder u zult twee panelen creëren:

- Kanaalanalyse (januari)
- Kanaalanalyse (februari)

U zult zien dat wij een trechter over verschillende tijdsperiodes (Januari en Februari) vergelijken die door het Type van Apparaat worden verdeeld.

Dit soort analyse is niet mogelijk binnen de gebruikersinterface van de Googles Analytics of is zeer beperkt. Dus CJA voegt weer veel waarde toe aan de gegevens die door Googles Analytics worden vastgelegd.

Om uw eerste fallout visualisatie te maken. Sluit het huidige deelvenster om te beginnen met een nieuw deelvenster.

Kijk naar de rechterkant van het deelvenster en klik op de pijl om het te sluiten.

![ demo ](./images/pro33.png)

Klik vervolgens op **+** om een nieuw deelvenster te maken.

![ demo ](./images/pro35.png)

Nu selecteer de **Vallout** Visualisatie.

![ demo ](./images/pro36.png)

Als analist stelt u zich voor dat u wilt begrijpen wat er gebeurt met uw belangrijkste e-commercetrechter: Home > Intern zoeken > Productdetails > Afhandeling > Aanschaffen.

Laten we beginnen met het toevoegen van nieuwe stappen aan de trechter. Om dat te doen, open de **dimensie van de Naam van de 0} Pagina.**

![ demo ](./images/pro37.png)

U zult dan alle beschikbare pagina&#39;s zien die zijn bezocht.

![ demo ](./images/pro38.png)

De belemmering en laat vallen **Huis** aan de eerste stap.

![ demo ](./images/pro39.png)

Als tweede stap, gebruik de **onderzoeksresultaten van de Opslag**

![ demo ](./images/pro40.png)

Nu moet u wat e-commerce acties toevoegen. In de Dimensionen, onderzoek naar de dimensie van het Type van de Gebeurtenis van het Dimension ****. Klik om de dimensie te openen.

![ demo ](./images/pro41.png)

Selecteer **Product_Detail_Views** en sleep en laat vallen het in de volgende stap.

![ demo ](./images/pro43.png)

Selecteer **Product_Checkouts** en sleep en laat vallen het in de volgende stap.

![ demo ](./images/pro44.png)

Pas de grootte van uw uitvalweergave aan.

![ demo ](./images/pro45.png)

Uw uitvalvisualisatie is nu gereed.

Beginnen de inzichten te analyseren en te documenteren, is het altijd een goed idee aan a **Tekst** visualisatie. Om a **Tekst** visualisatie toe te voegen, klik op het **Grafiek** pictogram in het linkermenu om alle beschikbare visualisaties te zien. Dan belemmering en laat vallen de **Tekst** visualisatie op het canvas. Wijzig het formaat en verplaats het zodat het lijkt op de afbeelding onder.

![ demo ](./images/pro48.png)

En opnieuw, resize het om het dashboard te passen:

![ demo ](./images/pro49.png)

Bij valutamatievisualisaties zijn ook uitsplitsingen mogelijk. Gebruik de **dimensie van het Type van Apparaat** door het te openen en sommige waarden op één voor één op visualisatie te slepen:

![ demo ](./images/pro50.png)

U krijgt dan een geavanceerdere visualisatie:

![ demo ](./images/pro51.png)

Met Customer Journey Analytics kun je dat doen en nog veel meer. Door met de rechtermuisknop ergens in de fallout te klikken, kunt u...

- Analyseren waar de gebruikers van een reservestap gaan
- Een segment maken van een willekeurig punt in de trechter
- Teken om het even welke stap in een Lijnvisualisatie
- Vergelijk een trechter visueel met verschillende tijdsperiodes.

Als voorbeeld, doe een met de rechtermuisknop aan klik in om het even welke stap van de reserve om sommige van deze analyseopties te zien.

![ demo ](./images/pro52.png)

## 4.2.5.3.3 Stroomanalyse en visualisatie

Als u geavanceerde stroomanalyse wilt doen gebruikend Googles Analytics, moet u SQL gebruiken om de gegevens te halen en dan een derdeoplossing voor het visualisatiedeel te gebruiken. Customer Journey Analytics zal daarbij helpen.

In deze stap, zult u een stroomanalyse vormen om deze vraag te beantwoorden: wat zijn de belangrijkste bijdragende kanalen vóór een specifieke het Bestanden Pagina.  Als analist kunt u met twee slepen en neerzetten en met één muisklik de richting van de landingspagina van de gebruiker vaststellen met de twee laatste aanrakingen van de marketingkanalen.

Andere vragen die de Customer Journey Analytics u kan helpen beantwoorden:

- Wat is de belangrijkste combinatie kanalen vóór een specifieke het Bestaan Pagina?
- Wat veroorzaakt een gebruiker om de zitting weg te gaan wanneer hij/zij aan Product_Checkout aankomt? Waar de vorige stappen?

Laten we opnieuw met een leeg deelvenster beginnen om deze vragen te beantwoorden. Sluit het huidige paneel en klik **+**.

![ demo ](./images/pro53.png)

Nu selecteer de **Stroom** visualisatie.

![ demo ](./images/pro54.png)

Stel nu een Meerwegs Analyse van de Stroom van het Kanaal van de Marketing. De belemmering en laat vallen de **dimensie van het Kanaal van de Marketing** op het **gebied van de Dimensionen van de Ingang**.

![ demo ](./images/pro55.png)

U kunt nu de eerste toegangspaden zien:

![ demo ](./images/pro56.png)

Klik op het eerste pad om er omlaag over te boren.

![ demo ](./images/pro58.png)

U kunt nu het volgende pad zien (Marketingkanaal).

![ demo ](./images/pro59.png)

Laten we een derde boor-down doen. Klik op de eerste optie binnen de nieuwe weg, **Verwijzing**.

![ demo ](./images/pro60.png)

Nu moet je de visualisatie als volgt zien:

![ demo ](./images/pro61.png)

Laten we dingen compliceren. Stel dat u wilt analyseren wat de landingspagina was na twee marketingpaden? Hiervoor kunt u een secundaire dimensie gebruiken om het laatste pad te wijzigen. Vind de **dimensie van de Naam van de 0} Pagina {en sleep en laat vallen het als dit:**

![ demo ](./images/pro62n.png)

U ziet nu het volgende:

![ demo ](./images/pro63n.png)

Laten we nog een flowanalyse uitvoeren. Deze keer zult u analyseren wat na een specifiek uitgangspunt gebeurde. Andere analytische oplossingen vereisen het gebruik van SQL/ETL en opnieuw, een derdevisualisatiehulpmiddel om het zelfde ding te bereiken.

Breng een nieuwe **Visualisatie van de Stroom** aan het paneel.

![ demo ](./images/pro64.png)

Dan heb je het volgende:

![ demo ](./images/pro64a.png)

Vind het Type van de Gebeurtenis van het Dimension **** en sleep en laat vallen het aan het **afmeting van de Uitgang** gebied.

![ demo ](./images/pro65.png)

Nu kunt u zien welk **Type van Gebeurtenis** - wegen klanten aan de uitgang dreden.

![ demo ](./images/pro66.png)

Laten we onderzoeken wat er is gebeurd voordat de kassa-actie is afgesloten. Klik op de **Product_Checkouts** weg:

![ demo ](./images/pro67.png)

Er wordt een nieuw actiepad weergegeven met gegevens die niet begrijpelijk zijn.

![ demo ](./images/pro68.png)

Laten we verder analyseren! Onderzoek de Naam van de Dimension **Pagina** en sleep en laat vallen het aan de nieuwe geproduceerde weg.

![ demo ](./images/pro69.png)

U hebt nu een geavanceerde flowanalyse uitgevoerd in minuten. U kunt op de verschillende paden klikken om te zien hoe ze een verbinding tot stand brengen vanaf het einde tot aan de vorige stappen.

![ demo ](./images/pro70.png)

U beschikt nu over een krachtige kit om trechters te analyseren en wegen van klantengedrag over digitaal maar ook, off-line aanraakpunten te verkennen.

Vergeet niet uw wijzigingen op te slaan!

## 4.2.5.4 Het project delen

>[!IMPORTANT]
>
>De hieronder inhoud is bedoeld als FYI - u **NIET** moet uw project met iedereen anders delen.

FYI - U kunt dit project met collega&#39;s delen om samen te werken of bedrijfsvragen samen te analyseren.

![ demo ](./images/pro99.png)

![ demo ](./images/pro100.png)

Volgende Stap: [ Samenvatting &amp; voordelen ](./summary.md)

[Terug naar module 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Terug naar alle modules](./../../../overview.md)

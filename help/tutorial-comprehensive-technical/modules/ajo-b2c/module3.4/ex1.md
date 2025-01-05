---
title: Adobe Journey Optimizer - Een op trigger gebaseerde reis configureren - Bestelbevestiging
description: In deze sectie zult u een op trekker-gebaseerde reis - de Bevestiging van de Orde vormen
kt: 5342
doc-type: tutorial
exl-id: b9d9b357-08d1-4f65-9e0b-46224d035602
source-git-commit: 9865b5697abe2d344fb530636a1afc3f152a9e8f
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 0%

---

# 3.4.1 Een op een trigger gebaseerde reis configureren - Bestelbevestiging

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.1.1 Uw gebeurtenis maken

In het menu, ga naar **Configuraties** en klik **leiden** onder **Gebeurtenissen**.

![ Journey Optimizer ](./images/oc30.png)

Op het **scherm van Gebeurtenissen**, zult u een mening gelijkend op dit zien. Klik **creëren Gebeurtenis**.

![ Journey Optimizer ](./images/oc31.png)

U ziet dan een lege gebeurtenisconfiguratie.

Geef uw gebeurtenis eerst een naam als deze: `--aepUserLdap--PurchaseEvent` en voeg een beschrijving als deze toe: `Purchase Event` .

Voor **Type**, uitgezochte **Eenheids**.
Voor **Type van identiteitskaart van de Gebeurtenis**, uitgezochte **Gegenereerd Systeem**.

![ Journey Optimizer ](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1` .

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. Klik het **uitgeven/Potlood** pictogram om extra gebieden aan deze gebeurtenis toe te voegen.

![ Journey Optimizer ](./images/oc36.png)

Dan zie je deze popup. U moet nu extra selectievakjes inschakelen om toegang te krijgen tot aanvullende gegevens wanneer deze gebeurtenis wordt geactiveerd.

![ Journey Optimizer ](./images/oc37.png)

Schakel eerst het selectievakje op de regel `--aepTenantId--` in.

![ Journey Optimizer ](./images/oc38.png)

Blader vervolgens omlaag en schakel het selectievakje op de regel in `commerce` .

![ Journey Optimizer ](./images/oc391.png)

Blader vervolgens omlaag en schakel het selectievakje op de regel in `productListItems` . Klik **OK**.

![ Journey Optimizer ](./images/oc39.png)

Vervolgens ziet u dat er extra velden zijn toegevoegd aan de gebeurtenis. Klik **sparen**.

![ Journey Optimizer ](./images/oc40.png)

Uw nieuwe gebeurtenis wordt dan opgeslagen en u zult uw gebeurtenis in de lijst van beschikbare gebeurtenissen nu zien.

Klik opnieuw op uw gebeurtenis om **te openen geef het 1} scherm van de Gebeurtenis {opnieuw uit.**
Beweeg over het **gebied van de Lading** opnieuw om de 3 pictogrammen opnieuw te zien. Klik op het **pictogram van de Payload van de Mening**.

![ Journey Optimizer ](./images/oc41.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien. Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

![ Journey Optimizer ](./images/oc42.png)

De gebeurtenis-id is wat naar Adobe Journey Optimizer moet worden verzonden om de reis te activeren die u in de volgende stap maakt. Schrijf deze eventID neer, aangezien u het in één van de volgende stappen zult nodig hebben.
`"eventID": "1c8148a8ab1993537d0ba4e6ac293dd4f2a88d80b2ca7be6293c3b28d4ff5ae6"`

Klik **O.K.**, die door **wordt gevolgd annuleert**.

Uw gebeurtenis is nu geconfigureerd en klaar om te worden gebruikt.

## 3.4.1.2 Maak uw reis

In het menu, ga naar **Reizen** en klik **creeer Reizen**.

![ Journey Optimizer ](./images/oc43.png)

Dan zie je dit. Geef je reis een naam. Gebruik `--aepUserLdap-- - Order Confirmation journey` . Klik **sparen**.

![ Journey Optimizer ](./images/oc45.png)

Eerst, moet u uw gebeurtenis toevoegen als uitgangspunt van uw reis. Zoek de gebeurtenis `--aepUserLdap--PurchaseEvent` en sleep deze naar het canvas. Klik **sparen**.

![ Journey Optimizer ](./images/oc46.png)

Daarna, onder **Acties**, onderzoek naar de **E-mail** actie en voeg het op het canvas toe.

![ Journey Optimizer ](./images/oc47.png)

Plaats de **Categorie** aan **Marketing** en selecteer een e-mailoppervlakte die u toelaat om e-mail te verzenden. In dit geval, is de e-mailoppervlakte om te selecteren **E-mail**. Zorg ervoor dat checkboxes voor **klikt op e-mail** en **e-mail opent** allebei worden toegelaten.

![ ACOP ](./images/journeyactions1.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klik **geef inhoud** uit.

![ ACOP ](./images/journeyactions2.png)

U ziet dit nu. Klik het **Onderwerplijn** tekstgebied.

![ ACOP ](./images/journeyactions3.png)

In het tekstgebied begint te schrijven **Dank voor uw orde,** en klik het **Personalization** pictogram.

![ Journey Optimizer ](./images/oc5.png)

De onderwerpregel is nog niet gereed. Daarna moet u het verpersoonlijkingstoken voor het gebied **Eerste naam** brengen die onder `profile.person.name.firstName` wordt opgeslagen. In het linkermenu, scrol neer om **Persoon** > **Volledige naam** > **Voornaam** gebied te vinden en op **+** pictogram te klikken om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klik **sparen**.

![ Journey Optimizer ](./images/oc6.png)

Dan ben je hier weer. Klik **uitgeeft e-maillichaam** om de inhoud van e-mail tot stand te brengen.

![ Journey Optimizer ](./images/oc7.png)

In het volgende scherm, klik **Ontwerp van kras**.

![ Journey Optimizer ](./images/oc8.png)

In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen 8 keer a **1:1 kolom** op het canvas, dat u dit zou moeten geven:

![ Journey Optimizer ](./images/oc9.png)

In het linkermenu, ga naar **Fragments**. Sleep de kopbal u vroeger in [ oefening 3.1.2.1 ](./../module3.1/ex2.md) op de eerste component in het canvas creeerde. Sleep de footer u vroeger in [ oefening 3.1.2.2 ](./../module3.1/ex2.md) op de laatste component in het canvas creeerde.

![ Journey Optimizer ](./images/fragm1.png)

Klik op het pictogram **+** in het linkermenu. Ga naar **Inhoud** beginnen inhoud op het canvas toe te voegen.

![ Journey Optimizer ](./images/oc10.png)

Ga naar **Inhoud** en sleep en laat vallen een **component van het Beeld** op de tweede rij. Klik **doorbladeren**.

![ Journey Optimizer ](./images/oc15.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **te selecteren burgerschap-preparing.png**, en klik **Uitgezocht**.

![ Journey Optimizer ](./images/oc14.png)

Onder **Stijlen**, verander de breedte in **40%**.

![ Journey Optimizer ](./images/oc14a.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen a **** component van de Tekst op de derde rij.

![ Journey Optimizer ](./images/oc17.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervang deze door de onderstaande tekst:

```javascript
You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![ Journey Optimizer ](./images/oc18.png)

Plaats de curseur naast de tekst **Hi** en klik **toevoegen Personalization**.

![ Journey Optimizer ](./images/oc19.png)

Navigeer aan de **Persoon** > **Volledige naam** > **Voornaam** gebied en klik op **+** pictogram om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klik **sparen**.

![ Journey Optimizer ](./images/oc20.png)

U zult dan dit zien:

![ Journey Optimizer ](./images/oc21.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen a **** component van de Tekst op de vierde rij.

![ Journey Optimizer ](./images/oc22.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervang deze door de onderstaande tekst:

`Order Information`

Verander de doopvontgrootte in **26px** en centrum uw tekst in deze cel. Dan heb je het volgende:

![ Journey Optimizer ](./images/oc23.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de vijfde rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![ Journey Optimizer ](./images/oc24.png)

In **geef HTML** popup uit, kleef deze HTML:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Klik **sparen**.

![ Journey Optimizer ](./images/oc25.png)

Dan heb je dit. Klik **sparen** om uw vooruitgang te bewaren.

![ Journey Optimizer ](./images/oc26.png)

Ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de zesde rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![ Journey Optimizer ](./images/oc57.png)

In **geef HTML** popup uit, kleef deze HTML:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

Dan heb je het volgende:

![ Journey Optimizer ](./images/oc58.png)

U moet nu **xxx** door een verwijzing naar het productListItems voorwerp vervangen dat deel van de gebeurtenis uitmaakt die de reis teweegbrengt.

![ Journey Optimizer ](./images/oc59.png)

Eerst, schrap **xxx** in uw code van HTML eerst.

![ Journey Optimizer ](./images/oc60.png)

In het linkermenu, klik **Contextafhankelijke attributen**. Deze context wordt doorgegeven aan de boodschap van de reis.

Dan zie je dit. Klik de pijl naast **Journey Orchestration** om dieper te boren.

![ Journey Optimizer ](./images/oc601.png)

Klik de pijl naast **Gebeurtenissen** om dieper te boren.

![ Journey Optimizer ](./images/oc62.png)

Klik op de pijl naast `--aepUserLdap--PurchaseEvent` om dieper te boren.

![ Journey Optimizer ](./images/oc63.png)

Klik de pijl naast **productListItems** om dieper te boren.

![ Journey Optimizer ](./images/oc64.png)

Klik het **+** pictogram naast **Naam** om het aan het canvas toe te voegen. Dan heb je dit. U moet nu **.name** selecteren zoals die in hieronder het schermschot wordt vermeld, en dan zou u **moeten verwijderen.name**.

![ Journey Optimizer ](./images/oc65.png)

Dan heb je dit. Klik **sparen**.

![ Journey Optimizer ](./images/oc66.png)

Je bent nu weer in de e-mail-Designer. Klik **sparen** om uw vooruitgang te bewaren.

![ Journey Optimizer ](./images/oc67.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de zevende rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![ Journey Optimizer ](./images/oc68.png)

In **geef HTML** popup uit, kleef deze HTML:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

Er zijn 2 verwijzingen van **xxx** in deze code van HTML. U moet nu elk **xxx** door een verwijzing naar het productListItems voorwerp vervangen dat deel van de gebeurtenis uitmaakt die de reis teweegbrengt.

![ Journey Optimizer ](./images/oc69.png)

Eerst, schrap eerste **xxx** in uw code van HTML.

![ Journey Optimizer ](./images/oc71.png)

In het linkermenu, klik **Contextafhankelijke Attributen**.
Klik de pijl naast **Journey Orchestration** om dieper te boren.

![ Journey Optimizer ](./images/oc72.png)

Klik de pijl naast **Gebeurtenissen** om dieper te boren.

![ Journey Optimizer ](./images/oc722.png)

Klik op de pijl naast `--aepUserLdap--PurchaseEvent` om dieper te boren.

![ Journey Optimizer ](./images/oc73.png)

Klik de pijl naast **Commerce** om dieper te boren.

![ Journey Optimizer ](./images/oc733.png)

Klik de pijl naast **Orde** om dieper te boren.

![ Journey Optimizer ](./images/oc74.png)

Klik het **+** pictogram naast **Totaal van de Prijs** om dat aan het canvas toe te voegen.

![ Journey Optimizer ](./images/oc75.png)

Dan heb je dit. Nu schrap tweede **xxx** in uw code van HTML.

![ Journey Optimizer ](./images/oc76.png)

Klik opnieuw het **+** pictogram naast **Totaal van de Prijs** om dat aan het canvas toe te voegen.
U kunt het gebied **Valuta** van binnen het **voorwerp van de Orde** op het canvas ook toevoegen, aangezien u hier kunt zien.
Wanneer u wordt gedaan, klik **sparen** om uw veranderingen te bewaren.

![ Journey Optimizer ](./images/oc77.png)

Je bent dan terug in de e-mail Designer. Klik **sparen** opnieuw.

![ Journey Optimizer ](./images/oc78.png)

Ga terug naar het berichtdashboard door de **pijl** naast de onderwerplijntekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/oc79.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![ Journey Optimizer ](./images/oc79a.png)

Klik **sparen** om uw e-mailactie te sluiten.

![ Journey Optimizer ](./images/oc79b.png)

Klik **Publish** om uw reis te publiceren.

![ Journey Optimizer ](./images/oc511.png)

Klik **opnieuw Publish**.

![ Journey Optimizer ](./images/oc512.png)

Uw reis is nu gepubliceerd.

![ Journey Optimizer ](./images/oc513.png)

## 3.4.1.5 Werk uw Adobe Experience Platform Data Collection Client-eigenschap bij

Ga naar [ de Inzameling van Gegevens van Adobe Experience Platform ](https://experience.adobe.com/launch/) en selecteer **Markeringen**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![ pagina van Eigenschappen ](./../../../modules/datacollection/module1.1/images/launch1.png)

In **Aan de slag**, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: voor de website en voor mobiele app. Zoek naar `--aepUserLdap--` in het vak **[!UICONTROL Search]** . Klik om het **bezit te openen 0} van het Web {.**

![ vakje van het Onderzoek ](./../../../modules/datacollection/module1.1/images/property6.png)

Ga naar **Elementen van Gegevens**. Onderzoek en open het gegevenselement **XDM - Schaf** aan.

![ Journey Optimizer ](./images/oc91.png)

Dan zie je dit. Navigeer naar het veld **_experience.campagne.orchestration.eventID** en vul hier uw eventID in. EventID om hier te vullen, is eventID u als deel van oefening 3.4.1.1 creeerde klikt **sparen** of **sparen aan Bibliotheek**.

![ Journey Optimizer ](./images/oc92.png)

Sla de wijzigingen in de eigenschap op en publiceer de wijzigingen door de ontwikkelingsbibliotheek bij te werken.

![ Journey Optimizer ](./images/oc93.png)

Uw wijzigingen worden nu geïmplementeerd en kunnen worden getest.

## 3.4.1.6 Test het bevestigingsbericht voor uw bestelling via de demo-website

Laten we de bijgewerkte reis testen door een product te kopen op de demo-website.

Ga naar [ https://dsn.adobe.com ](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![ DSN ](./../../datacollection/module1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![ DSN ](../../gettingstarted/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![ DSN ](../../gettingstarted/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![ DSN ](../../gettingstarted/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![ DSN ](../../gettingstarted/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![ DSN ](../../gettingstarted/gettingstarted/images/web7.png)

Heb een blik bij het paneel van de Kijker van het Profiel en het Profiel van de Klant in real time met **identiteitskaart van het Experience Cloud** als primaire herkenningsteken voor deze momenteel onbekende klant.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv2.png)

Ga naar de pagina Registreren/Aanmelden. Klik **CREËREN EEN ACCOUNT**.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv9.png)

Vul uw details in en klik **Register** waarna u aan de vorige pagina opnieuw zult worden gericht.

![ Demo ](./../../../modules/datacollection/module1.2/images/pv10.png)

Elk product aan uw winkelwagentje toevoegen

![ Journey Optimizer ](./images/cart1a.png)

Ga naar de **Kar** pagina. Klik **Controle**.

![ Journey Optimizer ](./images/cart1.png)

Controleer vervolgens de velden en vul deze zo nodig in. Klik **ga** verder.

![ Journey Optimizer ](./images/cart2.png)

Klik **bevestigen Orde**.

![ Journey Optimizer ](./images/cart2a.png)

Uw bestelling wordt nu bevestigd.

![ Journey Optimizer ](./images/cart2b.png)

U ontvangt dan binnen enkele seconden een bevestigingsbericht voor uw bestelling.

![ Journey Optimizer ](./images/oc98.png)

U hebt deze oefening voltooid.

Volgende Stap: [ 3.4.2 vormt een op partij-gebaseerde nieuwsbrief reis ](./ex2.md)

[Terug naar module 3.4](./journeyoptimizer.md)

[Terug naar alle modules](../../../overview.md)

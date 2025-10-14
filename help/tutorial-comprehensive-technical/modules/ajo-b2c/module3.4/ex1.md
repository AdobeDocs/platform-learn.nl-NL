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

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak `--aepSandboxName--` zijn.**

![&#x200B; ACOP &#x200B;](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.1.1 Uw gebeurtenis maken

In het menu, ga naar **Configuraties** en klik **leiden** onder **Gebeurtenissen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc30.png)

Op het **scherm van Gebeurtenissen**, zult u een mening gelijkend op dit zien. Klik **creëren Gebeurtenis**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc31.png)

U ziet dan een lege gebeurtenisconfiguratie.

Geef uw gebeurtenis eerst een naam als deze: `--aepUserLdap--PurchaseEvent` en voeg een beschrijving als deze toe: `Purchase Event` .

Voor **Type**, uitgezochte **Eenheids**.
Voor **Type van identiteitskaart van de Gebeurtenis**, uitgezochte **Gegenereerd Systeem**.

![&#x200B; Journey Optimizer &#x200B;](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1` .

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. Klik het **uitgeven/Potlood** pictogram om extra gebieden aan deze gebeurtenis toe te voegen.

![&#x200B; Journey Optimizer &#x200B;](./images/oc36.png)

Dan zie je deze popup. U moet nu extra selectievakjes inschakelen om toegang te krijgen tot aanvullende gegevens wanneer deze gebeurtenis wordt geactiveerd.

![&#x200B; Journey Optimizer &#x200B;](./images/oc37.png)

Schakel eerst het selectievakje op de regel `--aepTenantId--` in.

![&#x200B; Journey Optimizer &#x200B;](./images/oc38.png)

Blader vervolgens omlaag en schakel het selectievakje op de regel in `commerce` .

![&#x200B; Journey Optimizer &#x200B;](./images/oc391.png)

Blader vervolgens omlaag en schakel het selectievakje op de regel in `productListItems` . Klik **OK**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc39.png)

Vervolgens ziet u dat er extra velden zijn toegevoegd aan de gebeurtenis. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc40.png)

Uw nieuwe gebeurtenis wordt dan opgeslagen en u zult uw gebeurtenis in de lijst van beschikbare gebeurtenissen nu zien.

Klik opnieuw op uw gebeurtenis om **te openen geef het 1&rbrace; scherm van de Gebeurtenis &lbrace;opnieuw uit.**
Beweeg over het **gebied van de Lading** opnieuw om de 3 pictogrammen opnieuw te zien. Klik op het **pictogram van de Payload van de Mening**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc41.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien. Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

![&#x200B; Journey Optimizer &#x200B;](./images/oc42.png)

De gebeurtenis-id is wat naar Adobe Journey Optimizer moet worden verzonden om de reis te activeren die u in de volgende stap maakt. Schrijf deze eventID neer, aangezien u het in één van de volgende stappen zult nodig hebben.
`"eventID": "1c8148a8ab1993537d0ba4e6ac293dd4f2a88d80b2ca7be6293c3b28d4ff5ae6"`

Klik **O.K.**, die door **wordt gevolgd annuleert**.

Uw gebeurtenis is nu geconfigureerd en klaar om te worden gebruikt.

## 3.4.1.2 Maak uw reis

In het menu, ga naar **Reizen** en klik **creeer Reizen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc43.png)

Dan zie je dit. Geef je reis een naam. Gebruik `--aepUserLdap-- - Order Confirmation journey` . Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc45.png)

Eerst, moet u uw gebeurtenis toevoegen als uitgangspunt van uw reis. Zoek de gebeurtenis `--aepUserLdap--PurchaseEvent` en sleep deze naar het canvas. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc46.png)

Daarna, onder **Acties**, onderzoek naar de **E-mail** actie en voeg het op het canvas toe.

![&#x200B; Journey Optimizer &#x200B;](./images/oc47.png)

Plaats de **Categorie** aan **Marketing** en selecteer een e-mailoppervlakte die u toelaat om e-mail te verzenden. In dit geval, is de e-mailoppervlakte om te selecteren **E-mail**. Zorg ervoor dat checkboxes voor **klikt op e-mail** en **e-mail opent** allebei worden toegelaten.

![&#x200B; ACOP &#x200B;](./images/journeyactions1.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klik **geef inhoud** uit.

![&#x200B; ACOP &#x200B;](./images/journeyactions2.png)

U ziet dit nu. Klik het **Onderwerplijn** tekstgebied.

![&#x200B; ACOP &#x200B;](./images/journeyactions3.png)

In het tekstgebied begint te schrijven **Dank voor uw orde,** en klik het **Personalization** pictogram.

![&#x200B; Journey Optimizer &#x200B;](./images/oc5.png)

De onderwerpregel is nog niet gereed. Daarna moet u het verpersoonlijkingstoken voor het gebied **Eerste naam** brengen die onder `profile.person.name.firstName` wordt opgeslagen. In het linkermenu, scrol neer om **Persoon** > **Volledige naam** > **Voornaam** gebied te vinden en op **+** pictogram te klikken om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc6.png)

Dan ben je hier weer. Klik **uitgeeft e-maillichaam** om de inhoud van e-mail tot stand te brengen.

![&#x200B; Journey Optimizer &#x200B;](./images/oc7.png)

In het volgende scherm, klik **Ontwerp van kras**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc8.png)

In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen 8 keer a **1:1 kolom** op het canvas, dat u dit zou moeten geven:

![&#x200B; Journey Optimizer &#x200B;](./images/oc9.png)

In het linkermenu, ga naar **Fragments**. Sleep de kopbal u vroeger in [&#x200B; oefening 3.1.2.1 &#x200B;](./../module3.1/ex2.md) op de eerste component in het canvas creeerde. Sleep de footer u vroeger in [&#x200B; oefening 3.1.2.2 &#x200B;](./../module3.1/ex2.md) op de laatste component in het canvas creeerde.

![&#x200B; Journey Optimizer &#x200B;](./images/fragm1.png)

Klik op het pictogram **+** in het linkermenu. Ga naar **Inhoud** beginnen inhoud op het canvas toe te voegen.

![&#x200B; Journey Optimizer &#x200B;](./images/oc10.png)

Ga naar **Inhoud** en sleep en laat vallen een **component van het Beeld** op de tweede rij. Klik **doorbladeren**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc15.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **te selecteren burgerschap-preparing.png**, en klik **Uitgezocht**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc14.png)

Onder **Stijlen**, verander de breedte in **40%**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc14a.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen a **&#x200B;**&#x200B;component van de Tekst op de derde rij.

![&#x200B; Journey Optimizer &#x200B;](./images/oc17.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervang deze door de onderstaande tekst:

```javascript
You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![&#x200B; Journey Optimizer &#x200B;](./images/oc18.png)

Plaats de curseur naast de tekst **Hi** en klik **toevoegen Personalization**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc19.png)

Navigeer aan de **Persoon** > **Volledige naam** > **Voornaam** gebied en klik op **+** pictogram om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc20.png)

U zult dan dit zien:

![&#x200B; Journey Optimizer &#x200B;](./images/oc21.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen a **&#x200B;**&#x200B;component van de Tekst op de vierde rij.

![&#x200B; Journey Optimizer &#x200B;](./images/oc22.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervang deze door de onderstaande tekst:

`Order Information`

Verander de doopvontgrootte in **26px** en centrum uw tekst in deze cel. Dan heb je het volgende:

![&#x200B; Journey Optimizer &#x200B;](./images/oc23.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de vijfde rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc24.png)

In **geef HTML** popup uit, kleef deze HTML:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc25.png)

Dan heb je dit. Klik **sparen** om uw vooruitgang te bewaren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc26.png)

Ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de zesde rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc57.png)

In **geef HTML** popup uit, kleef deze HTML:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

Dan heb je het volgende:

![&#x200B; Journey Optimizer &#x200B;](./images/oc58.png)

U moet nu **xxx** door een verwijzing naar het productListItems voorwerp vervangen dat deel van de gebeurtenis uitmaakt die de reis teweegbrengt.

![&#x200B; Journey Optimizer &#x200B;](./images/oc59.png)

Eerst, schrap **xxx** in uw code van HTML eerst.

![&#x200B; Journey Optimizer &#x200B;](./images/oc60.png)

In het linkermenu, klik **Contextafhankelijke attributen**. Deze context wordt doorgegeven aan de boodschap van de reis.

Dan zie je dit. Klik de pijl naast **Journey Orchestration** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc601.png)

Klik de pijl naast **Gebeurtenissen** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc62.png)

Klik op de pijl naast `--aepUserLdap--PurchaseEvent` om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc63.png)

Klik de pijl naast **productListItems** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc64.png)

Klik het **+** pictogram naast **Naam** om het aan het canvas toe te voegen. Dan heb je dit. U moet nu **.name** selecteren zoals die in hieronder het schermschot wordt vermeld, en dan zou u **moeten verwijderen.name**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc65.png)

Dan heb je dit. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc66.png)

Je bent nu weer in de e-mail-Designer. Klik **sparen** om uw vooruitgang te bewaren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc67.png)

Daarna, ga naar **Inhoud** en sleep en laat vallen een **HTML** component op de zevende rij. Klik de component van de HTML en klik dan **tonen de broncode**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc68.png)

In **geef HTML** popup uit, kleef deze HTML:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

Er zijn 2 verwijzingen van **xxx** in deze code van HTML. U moet nu elk **xxx** door een verwijzing naar het productListItems voorwerp vervangen dat deel van de gebeurtenis uitmaakt die de reis teweegbrengt.

![&#x200B; Journey Optimizer &#x200B;](./images/oc69.png)

Eerst, schrap eerste **xxx** in uw code van HTML.

![&#x200B; Journey Optimizer &#x200B;](./images/oc71.png)

In het linkermenu, klik **Contextafhankelijke Attributen**.
Klik de pijl naast **Journey Orchestration** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc72.png)

Klik de pijl naast **Gebeurtenissen** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc722.png)

Klik op de pijl naast `--aepUserLdap--PurchaseEvent` om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc73.png)

Klik de pijl naast **Commerce** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc733.png)

Klik de pijl naast **Orde** om dieper te boren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc74.png)

Klik het **+** pictogram naast **Totaal van de Prijs** om dat aan het canvas toe te voegen.

![&#x200B; Journey Optimizer &#x200B;](./images/oc75.png)

Dan heb je dit. Nu schrap tweede **xxx** in uw code van HTML.

![&#x200B; Journey Optimizer &#x200B;](./images/oc76.png)

Klik opnieuw het **+** pictogram naast **Totaal van de Prijs** om dat aan het canvas toe te voegen.
U kunt het gebied **Valuta** van binnen het **voorwerp van de Orde** op het canvas ook toevoegen, aangezien u hier kunt zien.
Wanneer u wordt gedaan, klik **sparen** om uw veranderingen te bewaren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc77.png)

Je bent dan terug in de e-mail Designer. Klik **sparen** opnieuw.

![&#x200B; Journey Optimizer &#x200B;](./images/oc78.png)

Ga terug naar het berichtdashboard door de **pijl** naast de onderwerplijntekst in de top-left hoek te klikken.

![&#x200B; Journey Optimizer &#x200B;](./images/oc79.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![&#x200B; Journey Optimizer &#x200B;](./images/oc79a.png)

Klik **sparen** om uw e-mailactie te sluiten.

![&#x200B; Journey Optimizer &#x200B;](./images/oc79b.png)

Klik **Publish** om uw reis te publiceren.

![&#x200B; Journey Optimizer &#x200B;](./images/oc511.png)

Klik **opnieuw Publish**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc512.png)

Uw reis is nu gepubliceerd.

![&#x200B; Journey Optimizer &#x200B;](./images/oc513.png)

## 3.4.1.5 Werk uw Adobe Experience Platform Data Collection Client-eigenschap bij

Ga naar [&#x200B; de Inzameling van Gegevens van Adobe Experience Platform &#x200B;](https://experience.adobe.com/launch/) en selecteer **Markeringen**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![&#x200B; pagina van Eigenschappen &#x200B;](./../../../modules/datacollection/module1.1/images/launch1.png)

In **Aan de slag**, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: voor de website en voor mobiele app. Zoek naar `--aepUserLdap--` in het vak **[!UICONTROL Search]** . Klik om het **bezit te openen 0&rbrace; van het Web &lbrace;.**

![&#x200B; vakje van het Onderzoek &#x200B;](./../../../modules/datacollection/module1.1/images/property6.png)

Ga naar **Elementen van Gegevens**. Onderzoek en open het gegevenselement **XDM - Schaf** aan.

![&#x200B; Journey Optimizer &#x200B;](./images/oc91.png)

Dan zie je dit. Navigeer naar het veld **_experience.campagne.orchestration.eventID** en vul hier uw eventID in. EventID om hier te vullen, is eventID u als deel van oefening 3.4.1.1 creeerde klikt **sparen** of **sparen aan Bibliotheek**.

![&#x200B; Journey Optimizer &#x200B;](./images/oc92.png)

Sla de wijzigingen in de eigenschap op en publiceer de wijzigingen door de ontwikkelingsbibliotheek bij te werken.

![&#x200B; Journey Optimizer &#x200B;](./images/oc93.png)

Uw wijzigingen worden nu geïmplementeerd en kunnen worden getest.

## 3.4.1.6 Test het bevestigingsbericht voor uw bestelling via de demo-website

Laten we de bijgewerkte reis testen door een product te kopen op de demo-website.

Ga naar [&#x200B; https://dsn.adobe.com &#x200B;](https://dsn.adobe.com). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik de 3 punten **..** op uw websiteproject en klik dan **Looppas** om het te openen.

![&#x200B; DSN &#x200B;](./../../datacollection/module1.1/images/web8.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web3.png)

Open een nieuw Incognito-browservenster.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke oefening, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![&#x200B; DSN &#x200B;](../../gettingstarted/gettingstarted/images/web7.png)

Heb een blik bij het paneel van de Kijker van het Profiel en het Profiel van de Klant in real time met **identiteitskaart van het Experience Cloud** als primaire herkenningsteken voor deze momenteel onbekende klant.

![&#x200B; Demo &#x200B;](./../../../modules/datacollection/module1.2/images/pv2.png)

Ga naar de pagina Registreren/Aanmelden. Klik **CREËREN EEN ACCOUNT**.

![&#x200B; Demo &#x200B;](./../../../modules/datacollection/module1.2/images/pv9.png)

Vul uw details in en klik **Register** waarna u aan de vorige pagina opnieuw zult worden gericht.

![&#x200B; Demo &#x200B;](./../../../modules/datacollection/module1.2/images/pv10.png)

Elk product aan uw winkelwagentje toevoegen

![&#x200B; Journey Optimizer &#x200B;](./images/cart1a.png)

Ga naar de **Kar** pagina. Klik **Controle**.

![&#x200B; Journey Optimizer &#x200B;](./images/cart1.png)

Controleer vervolgens de velden en vul deze zo nodig in. Klik **ga** verder.

![&#x200B; Journey Optimizer &#x200B;](./images/cart2.png)

Klik **bevestigen Orde**.

![&#x200B; Journey Optimizer &#x200B;](./images/cart2a.png)

Uw bestelling wordt nu bevestigd.

![&#x200B; Journey Optimizer &#x200B;](./images/cart2b.png)

U ontvangt dan binnen enkele seconden een bevestigingsbericht voor uw bestelling.

![&#x200B; Journey Optimizer &#x200B;](./images/oc98.png)

U hebt deze oefening voltooid.

Volgende Stap: [&#x200B; 3.4.2 vormt een op partij-gebaseerde nieuwsbrief reis &#x200B;](./ex2.md)

[Terug naar module 3.4](./journeyoptimizer.md)

[Terug naar alle modules](../../../overview.md)

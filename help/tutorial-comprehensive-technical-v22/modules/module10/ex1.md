---
title: Adobe Journey Optimizer - Een op trigger gebaseerde reis configureren - Bestelbevestiging
description: In deze sectie zult u een op trekker-gebaseerde reis - de Bevestiging van de Orde vormen
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 69bb9eca-3942-4c31-a3d2-0b218143e1eb
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---

# 10.1 Een op trigger gebaseerde reis configureren - Bestelbevestiging

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.1.1 Uw gebeurtenis maken

Ga in het menu naar **Configuraties** en klik op **Beheren** krachtens **Gebeurtenissen**.

![Journey Optimizer](./images/oc30.png)

Op de **Gebeurtenissen** -scherm, ziet u een vergelijkbare weergave. Klikken **Gebeurtenis maken**.

![Journey Optimizer](./images/oc31.png)

U ziet dan een lege gebeurtenisconfiguratie.

![Journey Optimizer](./images/oc32.png)

Geef uw gebeurtenis als volgt een naam: `--demoProfileLdap--PurchaseEvent`en voeg een beschrijving als deze toe: `Purchase Event`.

![Journey Optimizer](./images/oc34.png)

Volgende is de **Type gebeurtenis** selectie. Selecteren **Unitair**.

![Journey Optimizer](./images/eventidtype1.png)

Volgende is de **Type gebeurtenis-id** selectie. Selecteren **Door systeem gegenereerd**

![Journey Optimizer](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![Journey Optimizer](./images/oc35.png)

Nadat u het schema hebt geselecteerd, ziet u een aantal velden die worden geselecteerd in het dialoogvenster **Payload** sectie. Klik op de knop **Bewerken/Potlood** pictogram om extra velden aan deze gebeurtenis toe te voegen.

![Journey Optimizer](./images/oc36.png)

Dan zie je deze popup. U moet nu extra selectievakjes inschakelen om toegang te krijgen tot aanvullende gegevens wanneer deze gebeurtenis wordt geactiveerd.

![Journey Optimizer](./images/oc37.png)

Schakel eerst het selectievakje op de regel in `--aepTenantId--`.

![Journey Optimizer](./images/oc38.png)

Blader vervolgens omlaag en schakel het selectievakje in op de regel `productListItems`.

![Journey Optimizer](./images/oc39.png)

Blader vervolgens omlaag en schakel het selectievakje in op de regel `commerce`.

![Journey Optimizer](./images/oc391.png)

Klik op Volgende **OK**.

Vervolgens ziet u dat er extra velden zijn toegevoegd aan de gebeurtenis. Klikken **Opslaan**.

![Journey Optimizer](./images/oc40.png)

Uw nieuwe gebeurtenis wordt dan gedeeld en u zult uw gebeurtenis in de lijst van beschikbare gebeurtenissen nu zien.

Klik nogmaals op de gebeurtenis om het dialoogvenster **Gebeurtenis bewerken** opnieuw.
Houd de aanwijzer boven de **Payload** nogmaals in om de 3 pictogrammen weer te zien. Klik op de knop **Payload weergeven** pictogram.

![Journey Optimizer](./images/oc41.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien. Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u ziet `_experience.campaign.orchestration.eventID`.

![Journey Optimizer](./images/oc42.png)

De gebeurtenis-id is wat naar Adobe Journey Optimizer moet worden verzonden om de reis te activeren die u in de volgende stap maakt. Schrijf deze eventID neer, aangezien u het in één van de volgende stappen zult nodig hebben.
`"eventID": "ef6dd943c94fe1b4763c098ccd1772344662f2a9f614513106cb5ada8be36857"`

Klikken **OK**, gevolgd door **Annuleren**.

Uw gebeurtenis is nu geconfigureerd en klaar om te worden gebruikt.

## 10.1.2 Maak uw reis

Ga in het menu naar **Reizen** en klik op **Reis maken**.

![Journey Optimizer](./images/oc43.png)

Dan zie je dit. Geef je reis een naam. Gebruik `--demoProfileLdap-- - Order Confirmation journey`. Klikken **OK**.

![Journey Optimizer](./images/oc45.png)

Eerst, moet u uw gebeurtenis toevoegen als uitgangspunt van uw reis. Zoeken naar uw gebeurtenis `--demoProfileLdap--PurchaseEvent` en sleep het naar het canvas. Klikken **OK**.

![Journey Optimizer](./images/oc46.png)

Volgende, onder **Handelingen**, zoekt u naar de **E-mail** en voegt u deze toe aan het canvas.

![Journey Optimizer](./images/oc47.png)

Stel de **Categorie** tot **Marketing** en selecteer een e-mailoppervlak waarmee u e-mail kunt verzenden. In dit geval is het te selecteren e-mailoppervlak **E-mail**. Zorg ervoor dat de selectievakjes **Klik op e-mail** en **e-mail wordt geopend** zijn beide ingeschakeld.

![ACOP](./images/journeyactions1.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klikt u op **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

U ziet dit nu. Klik op de knop **Onderwerpregel** tekstveld.

![ACOP](./images/journeyactions3.png)

Begin met schrijven in het tekstgebied **Hartelijk dank voor uw bestelling,**

![Journey Optimizer](./images/oc5.png)

De onderwerpregel is nog niet gereed. Vervolgens moet u het personalisatietoken voor het veld introduceren **Voornaam** dat is opgeslagen onder `profile.person.name.firstName`. Blader in het linkermenu omlaag om de **Persoon** > **Volledige naam** >  **Voornaam** en klik op de knop **+** pictogram om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klikken **Opslaan**.

![Journey Optimizer](./images/oc6.png)

Dan ben je hier weer. Klikken **E-mailontwerper** om de inhoud van de e-mail te maken.

![Journey Optimizer](./images/oc7.png)

Klik in het volgende scherm op **Ontwerpen vanaf nul**.

![Journey Optimizer](./images/oc8.png)

In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

Slepen en 8 keer per keer neerzetten **1:1, kolom** op het canvas, dat u dit zou moeten geven:

![Journey Optimizer](./images/oc9.png)

Ga naar **Inhoudscomponenten**.

![Journey Optimizer](./images/oc10.png)

Sleep een **Afbeelding** op de eerste rij. Klikken **Bladeren**.

![Journey Optimizer](./images/oc11.png)

Ga naar de map **vermogensbestanddelen**, selecteert u het bestand **luma-logo.png** en klik op **Selecteren**.

![Journey Optimizer](./images/oc12.png)

Je bent nu weer hier. Klik op de afbeelding om deze te selecteren en gebruik vervolgens de **Grootte** om de afbeelding van het logo iets kleiner te maken.

![Journey Optimizer](./images/oc13.png)

Ga naar **Inhoudscomponenten** en sleep een **Afbeelding** op de tweede rij. Selecteer **Afbeeldingscomponent** maar klik niet op Bladeren.

![Journey Optimizer](./images/oc15.png)

Deze afbeeldings-URL in het veld plakken **Bron**: `https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/29043bedcde632a9cbe8a02a164189c9_preparing.png`. Deze afbeelding wordt buiten Adobe gehost.

![Journey Optimizer](./images/oc14.png)

Wanneer u het bereik in een ander veld wijzigt, wordt de afbeelding gerenderd en ziet u het volgende:

![Journey Optimizer](./images/oc16.png)

Ga vervolgens naar **Inhoudscomponenten** en sleep een **Tekst** op de derde rij.

![Journey Optimizer](./images/oc17.png)

De standaardtekst in die component selecteren **Typ hier uw tekst.** en vervangen door de onderstaande tekst:

```javascript
You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![Journey Optimizer](./images/oc18.png)

De cursor naast de tekst plaatsen **Hallo** en klik op **Persoonlijkheid toevoegen**.

![Journey Optimizer](./images/oc19.png)

Ga naar de **Persoon** > **Volledige naam** > **Voornaam** en klik op de knop **+** pictogram om het verpersoonlijkingstoken in de onderwerpregel toe te voegen. Klikken **Opslaan**.

![Journey Optimizer](./images/oc20.png)

U zult dan dit zien:

![Journey Optimizer](./images/oc21.png)

Ga vervolgens naar **Inhoudscomponenten** en sleep een **Tekst** op de vierde rij.

![Journey Optimizer](./images/oc22.png)

De standaardtekst in die component selecteren **Typ hier uw tekst.** en vervangen door de onderstaande tekst:

`Order Information`

De tekengrootte wijzigen in **26 px** en centreer de tekst in deze cel. Dan heb je het volgende:

![Journey Optimizer](./images/oc23.png)

Ga vervolgens naar **Inhoudscomponenten** en sleep een **HTML** op de vijfde rij. Klik op de component HTML en klik vervolgens op **De broncode weergeven**.

![Journey Optimizer](./images/oc24.png)

In de **HTML bewerken** popup, plak deze HTML:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Klikken **Opslaan**.

![Journey Optimizer](./images/oc25.png)

Dan heb je dit. Klikken **Opslaan** om de voortgang op te slaan.

![Journey Optimizer](./images/oc26.png)

Ga naar **Inhoudscomponenten** en sleep een **HTML** op de zesde rij. Klik op de component HTML en klik vervolgens op **De broncode weergeven**.

![Journey Optimizer](./images/oc57.png)

In de **HTML bewerken** popup, plak deze HTML:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

Dan heb je het volgende:

![Journey Optimizer](./images/oc58.png)

U moet nu vervangen **xxx** door een verwijzing naar het productListItems-object dat deel uitmaakt van de gebeurtenis die de reis activeert.

![Journey Optimizer](./images/oc59.png)

Eerst verwijderen **xxx** in uw HTML code eerst.

![Journey Optimizer](./images/oc60.png)

Klik in het linkermenu op **Contextafhankelijke kenmerken**. Deze context wordt doorgegeven aan de boodschap van de reis.

![Journey Optimizer](./images/oc601.png)

Dan zie je dit. Klik op de pijl naast **Journey Orchestration** dieper boren.

![Journey Optimizer](./images/oc61.png)

Klik op de pijl naast **Gebeurtenissen** dieper boren.

![Journey Optimizer](./images/oc62.png)

Klik op de pijl naast `--demoProfileLdap--PurchaseEvent` dieper boren.

![Journey Optimizer](./images/oc63.png)

Klik op de pijl naast **productListItems** dieper boren.

![Journey Optimizer](./images/oc64.png)

Klik op de knop **+** pictogram naast **Naam** om het aan het canvas toe te voegen. Dan heb je dit. U moet nu  **.name** zoals aangegeven in de onderstaande schermafbeelding, en dan moet u **.name**.

![Journey Optimizer](./images/oc65.png)

Dan heb je dit. Klikken **Opslaan**.

![Journey Optimizer](./images/oc66.png)

U bent nu weer in de e-mailontwerper. Klikken **Opslaan** om de voortgang op te slaan.

![Journey Optimizer](./images/oc67.png)

Ga vervolgens naar **Inhoudscomponenten** en sleep een **HTML** op de zevende rij. Klik op de component HTML en klik vervolgens op **De broncode weergeven**.

![Journey Optimizer](./images/oc68.png)

In de **HTML bewerken** popup, plak deze HTML:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

Er zijn twee verwijzingen naar **xxx** in deze HTML-code. U moet nu elke **xxx** door een verwijzing naar het productListItems-object dat deel uitmaakt van de gebeurtenis die de reis activeert.

![Journey Optimizer](./images/oc69.png)

Eerst verwijdert u de eerste **xxx** in uw HTML-code.

![Journey Optimizer](./images/oc71.png)

Klik in het linkermenu op **Contextafhankelijke kenmerken**.

![Journey Optimizer](./images/oc711.png)

Klik op de pijl naast **Journey Orchestration** dieper boren.

![Journey Optimizer](./images/oc72.png)

Klik op de pijl naast **Gebeurtenissen** dieper boren.

![Journey Optimizer](./images/oc722.png)

Klik op de pijl naast `--demoProfileLdap--PurchaseEvent` dieper boren.

![Journey Optimizer](./images/oc73.png)

Klik op de pijl naast **Handel** dieper boren.

![Journey Optimizer](./images/oc733.png)

Klik op de pijl naast **Volgorde** dieper boren.

![Journey Optimizer](./images/oc74.png)

Klik op de knop **+** pictogram naast **Prijs totaal** om dat aan het canvas toe te voegen.

![Journey Optimizer](./images/oc75.png)

Dan heb je dit. Verwijder nu de tweede **xxx** in uw HTML-code.

![Journey Optimizer](./images/oc76.png)

Klik op de knop **+** pictogram naast **Prijs totaal** nogmaals om dat aan het canvas toe te voegen.

![Journey Optimizer](./images/oc77.png)

U kunt ook het veld toevoegen **Valuta** van binnen **Volgorde** -object op het canvas plaatsen, zoals u hier kunt zien.
Als u klaar bent, klikt u op **Opslaan** om uw wijzigingen op te slaan.

![Journey Optimizer](./images/oc771.png)

U bent dan weer in de e-mailontwerper. Klikken **Opslaan** opnieuw.

![Journey Optimizer](./images/oc78.png)

Ga terug naar het berichtdashboard door op het **pijl** naast de tekst van de onderwerpregel in de linkerbovenhoek.

![Journey Optimizer](./images/oc79.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![Journey Optimizer](./images/oc79a.png)

Klikken **OK** om uw e-mailactie te sluiten.

![Journey Optimizer](./images/oc79b.png)

Klikken **Publiceren** om uw reis te publiceren.

![Journey Optimizer](./images/oc511.png)

Klikken **Publiceren** opnieuw.

![Journey Optimizer](./images/oc512.png)

Uw reis is nu gepubliceerd.

![Journey Optimizer](./images/oc513.png)

## 10.1.5 Werk uw Adobe Experience Platform Data Collection Client-eigenschap bij

Ga naar [Adobe Experience Platform-gegevensverzameling](https://experience.adobe.com/launch/) en selecteert u **Tags**.

Dit is de pagina Eigenschappen van Adobe Experience Platform-gegevensverzameling die u eerder hebt gezien.

![Pagina Eigenschappen](../module1/images/launch1.png)

In module 0, leidde het Systeem van de Demo tot twee eigenschappen van de Cliënt voor u: één voor de website en één voor de mobiele app. Zoeken naar `--demoProfileLdap--` in de **[!UICONTROL Zoeken]** doos. Klik om het dialoogvenster **Web** eigenschap.

![Zoekvak](../module1/images/property6.png)

Ga naar **Gegevenselementen**. Het gegevenselement zoeken en openen **XDM - Aankoop**.

![Journey Optimizer](./images/oc91.png)

Dan zie je dit. Naar het veld navigeren **_experience.campagne.orchestration.eventID** en vul hier uw eventID in. De eventID die u hier moet invullen, is de eventID die u hebt gemaakt als onderdeel van oefening 10.1.2. Klikken **Opslaan** of **Opslaan in bibliotheek**.

![Journey Optimizer](./images/oc92.png)

Sla uw wijzigingen op in de eigenschap Client en publiceer uw wijzigingen door uw ontwikkelingsbibliotheek bij te werken.

![Journey Optimizer](./images/oc93.png)

Uw wijzigingen worden nu geïmplementeerd en kunnen worden getest.

## 10.1.6 Test het bevestigingsbericht voor uw bestelling via de demo-website

Laten we de bijgewerkte reis testen door een product te kopen op de demo-website.

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![DSN](../module0/images/web8.png)

Op de **Schermen** pagina, klikt u op **Uitvoeren**.

![DSN](../module1/images/web2.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![DSN](../module0/images/web3.png)

Open een nieuw Incognito-browservenster.

![DSN](../module0/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![DSN](../module0/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![DSN](../module0/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![DSN](../module0/images/web7.png)

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![Demo](../module2/images/pv1.png)

Bekijk het deelvenster Profielviewer en het realtime klantprofiel met de **Experience Cloud-id** als primaire identificator voor deze momenteel onbekende klant.

![Demo](../module2/images/pv2.png)

Ga naar de pagina Registreren/Aanmelden. Klikken **EEN ACCOUNT MAKEN**.

![Demo](../module2/images/pv9.png)

Vul uw gegevens in en klik op **Registreren** waarna u naar de vorige pagina wordt omgeleid.

![Demo](../module2/images/pv10.png)

Voeg om het even welk product aan uw kar toe en ga naar **Kar** pagina. Klikken **Doorgaan naar afhandeling**.

![Journey Optimizer](./images/cart1.png)

Controleer vervolgens de velden op de uitcheckpagina en klik op **Afhandeling**.

![Journey Optimizer](./images/cart2.png)

U ontvangt dan binnen enkele seconden een bevestigingsbericht voor uw bestelling.

![Journey Optimizer](./images/oc98.png)

U hebt deze oefening voltooid.

Volgende stap: [10.2 Vorm een op partij-gebaseerde nieuwsbrief reis](./ex2.md)

[Ga terug naar module 10](./journeyoptimizer.md)

[Terug naar alle modules](../../overview.md)

---
title: Journey Optimizer Maak je reis en e-mailbericht
description: Journey Optimizer Je e-mailbericht maken
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 2b7333c3-5b6a-41c5-a7a7-b048d1579ddd
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# 7.2 Maak uw reis en e-mailbericht

In deze oefening, zult u de reis en het bericht vormen die moeten worden teweeggebracht wanneer iemand een rekening op de demowebsite creeert.

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](./images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](./images/acoptriglp.png)

## 7.2.1 Maak uw reis

Klik in het linkermenu op **Reizen**. Klik op Volgende **Reis maken** om een nieuwe reis te maken.

![ACOP](./images/createjourney.png)

Dan zie je een leeg reisscherm.

![ACOP](./images/journeyempty.png)

In de vorige oefening creeerde u een nieuw **Gebeurtenis**. U noemde het zo `ldapAccountCreationEvent` en vervangen `ldap` met uw ldap. Dit was het resultaat van het maken van de gebeurtenis:

![ACOP](./images/eventdone.png)

U moet deze gebeurtenis nu als begin van deze reis nemen. U kunt dit doen door naar de linkerkant van het scherm te gaan en naar uw gebeurtenis in de lijst met gebeurtenissen te zoeken.

![ACOP](./images/eventlist.png)

Selecteer de gebeurtenis, sleep deze naar het canvas Reis. Uw reis ziet er nu als volgt uit:

![ACOP](./images/journeyevent.png)

Als tweede stap in de reis, moet u een korte toevoegen **Wachten** stap. Naar de linkerkant van het scherm **Orchestratie** voor meer informatie. U zult profielattributen gebruiken en moet ervoor zorgen zij in het Profiel van de Klant in real time worden bevolkt.

![ACOP](./images/journeywait.png)

Je reis ziet er nu zo uit. Aan de rechterkant van het scherm moet u de wachttijd configureren. Stel dit in op 1 minuut. Dit geeft voldoende tijd om de profielkenmerken beschikbaar te maken nadat de gebeurtenis is gestart.

![ACOP](./images/journeywait1.png)

Klikken **OK** om uw wijzigingen op te slaan.

Als derde stap in de reis, moet u toevoegen **E-mail** handeling. Naar de linkerkant van het scherm gaan **Handelingen**, selecteert u de **E-mail** actie, dan belemmering en laat vallen het op de tweede knoop in uw reis. U ziet dit nu.

![ACOP](./images/journeyactions.png)

Stel de **Categorie** tot **Marketing** en selecteer een e-mailoppervlak waarmee u e-mail kunt verzenden. In dit geval is het te selecteren e-mailoppervlak **E-mail**. Zorg ervoor dat de selectievakjes **Klik op e-mail** en **e-mail wordt geopend** zijn beide ingeschakeld.

![ACOP](./images/journeyactions1.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klikt u op **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

## 7.2.2 Uw bericht maken

Klik op **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

U ziet dit nu.

![ACOP](./images/journeyactions3.png)

Klik op de knop **Onderwerpregel** tekstveld.

![Journey Optimizer](./images/msg5.png)

Begin met schrijven in het tekstgebied **Hallo**

![Journey Optimizer](./images/msg6.png)

De onderwerpregel is nog niet gereed. Vervolgens moet u het personalisatietoken voor het veld introduceren **Voornaam** dat is opgeslagen onder `profile.person.name.firstName`. Blader in het linkermenu omlaag om de **Persoon** en klik op de pijl om een niveau dieper te gaan.

![Journey Optimizer](./images/msg7.png)

Zoek nu de **Volledige naam** en klik op de pijl om een niveau dieper te gaan.

![Journey Optimizer](./images/msg8.png)

Tot slot, vind **Voornaam** en klik op de knop **+** onderteken ernaast. Vervolgens ziet u het personalisatietoken in het tekstveld.

![Journey Optimizer](./images/msg9.png)

Voeg vervolgens de tekst toe **, dank u dat u zich hebt aangemeld!**. Klikken **Opslaan**.

![Journey Optimizer](./images/msg10.png)

Dan ben je hier weer. Klikken **E-mailontwerper** om de inhoud van de e-mail te maken.

![Journey Optimizer](./images/msg11.png)

In het volgende scherm krijgt u drie verschillende methoden om de inhoud van de e-mail te verschaffen:

- **Ontwerpen vanaf nul**: Begin met een leeg canvas en gebruik de WYSIWYG-redacteur om structuur en inhoudscomponenten te slepen en te laten vallen om de inhoud van e-mail visueel op te bouwen.
- **Uw eigen code schrijven**: Uw eigen e-mailsjabloon maken door deze te coderen met HTML
- **HTML importeren**: Importeer een bestaande HTML-sjabloon, die u kunt bewerken.

Klikken **Ontwerpen vanaf nul**.

![Journey Optimizer](./images/msg12.png)

In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

![Journey Optimizer](./images/msg13.png)

Sleep een **1:2, kolom links** in het menu naar het canvas. Dit is de plaatsaanduiding voor de logoafbeelding.

![Journey Optimizer](./images/msg14.png)

Sleep een **1:1, kolom** onder de vorige component. Dit wordt het bannerblok.

![Journey Optimizer](./images/msg15.png)

Sleep een **1:2, kolom links** onder de vorige component. Dit is de werkelijke inhoud met een afbeelding aan de linkerkant en tekst aan de rechterkant.

![Journey Optimizer](./images/msg16.png)

Vervolgens sleept u een **1:1, kolom** onder de vorige component. Dit wordt de voettekst van e-mail. Uw canvas moet er nu als volgt uitzien:

![Journey Optimizer](./images/msg17.png)

Vervolgens gebruiken we Inhoud-componenten om inhoud toe te voegen binnen deze blokken. Klik op de knop **Inhoudscomponenten** menu-item

![Journey Optimizer](./images/msg18.png)

Sleep een **Afbeelding** in de eerste cel op de eerste rij. Klikken **Bladeren**.

![Journey Optimizer](./images/msg19.png)

Dan zie je dit. Ga naar de map **vermogensbestanddelen** en selecteer het bestand **luma-logo.png**. Klikken **Selecteren**.

![Journey Optimizer](./images/msg21.png)

U bent nu weer hier:

![Journey Optimizer](./images/msg25.png)

Ga naar **Inhoudscomponenten** en sleep een **Afbeelding** in de eerste cel op de eerste rij. Klikken **Bladeren**.

![Journey Optimizer](./images/msg26.png)

In de **Activa** pop-up, ga naar **vermogensbestanddelen** map. In deze map vindt u alle middelen die eerder door het creatieve team zijn voorbereid en geüpload. Selecteren **module23-thankyou-new.png** en klik op **Selecteren**.

![Journey Optimizer](./images/msg28.png)

Dan heb je het volgende:

![Journey Optimizer](./images/msg30.png)

Selecteer de afbeelding en schuif omlaag in het rechtermenu totdat u het dialoogvenster **Grootte** component width slider. Gebruik de schuifregelaar om de breedte te wijzigen in f.i. **60%**.

![Journey Optimizer](./images/msg31.png)

Ga vervolgens naar **Inhoudscomponenten** en sleep een **Tekst** in de structuurcomponent op de vierde rij.

![Journey Optimizer](./images/msg33.png)

De standaardtekst selecteren **Typ hier uw tekst.** zoals u met om het even welke tekstredacteur zou doen. Schrijven **Beste** in plaats daarvan. De werkbalk Tekst wordt weergegeven in de tekstmodus.

![Journey Optimizer](./images/msg34.png)

Klik op de werkbalk op de knop **Aanpassing toevoegen** pictogram.

![Journey Optimizer](./images/msg35.png)

Nu moet u de **Voornaam** personalisatietoken dat onder wordt opgeslagen `profile.person.name.firstName`. Zoek in het menu de **Persoon** element, naar beneden boren naar de **Volledige naam** en klik vervolgens op de knop **+** pictogram om het veld Voornaam toe te voegen aan de expressieeditor.

Klikken **Opslaan**.

![Journey Optimizer](./images/msg36.png)

U zult nu zien hoe het verpersoonlijkingsgebied aan uw tekst is toegevoegd.

![Journey Optimizer](./images/msg37.png)

Klik in hetzelfde tekstveld op **Enter** twee keer om twee regels toe te voegen en te schrijven **Hartelijk dank voor het maken van uw account met Luma!**.

![Journey Optimizer](./images/msg38.png)

De laatste controle die moet worden uitgevoerd om te controleren of uw e-mail gereed is, is een voorvertoning ervan. Klik op de knop **Inhoud simuleren** knop.

![Journey Optimizer](./images/msg50.png)

Geef eerst aan welk profiel u voor de voorvertoning wilt gebruiken. Selecteer **email** naamruimte door te klikken op het pictogram naast **Naamruimte invoeren** veld.

Selecteer in de lijst met naamruimten de optie **E-mail** naamruimte.

In de **Identiteitswaarde** voert u het e-mailadres in van een eerder demoprofiel dat al is opgeslagen in het realtime profiel van de klant. Bijvoorbeeld **woutervangeluwe+06022022-01@gmail.com** en klik op de knop **Testprofiel zoeken** knop

![Journey Optimizer](./images/msg53.png)

Als uw profiel in de tabel wordt weergegeven, klikt u op de knop **Voorvertoning** om het voorvertoningsscherm te openen.

Wanneer de voorvertoning gereed is, controleert u of de personalisatie correct is in de onderwerpregel. De hoofdtekst en de koppeling voor het opzeggen van het abonnement worden dan gemarkeerd als een hyperlink.

Klikken **Sluiten** om de voorvertoning te sluiten.

![Journey Optimizer](./images/msg54.png)

Klikken **Opslaan** om uw bericht op te slaan.

![Journey Optimizer](./images/msg55.png)

Ga terug naar het berichtdashboard door op het **pijl** naast de tekst van de onderwerpregel in de linkerbovenhoek.

![Journey Optimizer](./images/msg56.png)

Je hebt je registratiebericht nu gemaakt. Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![Journey Optimizer](./images/msg57.png)

Klikken **OK**.

![Journey Optimizer](./images/msg57a.png)

## 7.2.3 Uw reis publiceren

Je moet je reis nog steeds een naam geven. U kunt dat doen door op de knop **Eigenschappen** in de rechterbovenhoek van het scherm.

![ACOP](./images/journeyname.png)

Je kunt hier de naam van de reis invoeren. Gebruik `--demoProfileLdap-- - Account Creation Journey`. Klikken **OK** om uw wijzigingen op te slaan.

![ACOP](./images/journeyname1.png)

U kunt uw reis nu publiceren door te klikken **Publiceren**.

![ACOP](./images/publishjourney.png)

Klikken **Publiceren** opnieuw.

![ACOP](./images/publish1.png)

Vervolgens ziet u een groene bevestigingsbalk met de mededeling dat uw reis nu is gepubliceerd.

![ACOP](./images/published.png)

Je hebt deze oefening nu afgerond.

Volgende stap: [7.3 Werk uw bezit van de Inzameling van Gegevens bij en test uw reis](./ex3.md)

[Ga terug naar module 7](./journey-orchestration-create-account.md)

[Terug naar alle modules](../../overview.md)

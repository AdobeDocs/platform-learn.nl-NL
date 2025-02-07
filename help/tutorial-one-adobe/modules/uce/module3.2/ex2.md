---
title: Maak uw campagne met AJO Translation Services
description: Maak uw campagne met AJO Translation Services
kt: 5342
doc-type: tutorial
source-git-commit: 3b3c62499bfed86ab13a657a816424879cab4f42
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 0%

---

# 3.2.2 Uw campagne maken

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik **Journey Optimizer**.

![ Vertalingen ](./images/ajolp1.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![ ACOP ](./images/ajolp2.png)

## 3.2.2.1 Een koptekstfragment maken

In het linkermenu, klik **Fragmenten**. Een fragment is een herbruikbare component in Journey Optimizer die dubbel werk voorkomt en toekomstige wijzigingen vergemakkelijkt die van invloed zijn op alle berichten, zoals wijzigingen in een kop- of voettekst in een e-mailbericht.

Klik **tot fragment** leiden.

![ ACOP ](./images/fragm1.png)

Ga de naam `--aepUserLdap-- - CitiSignal - Header` in en selecteer het **Type: Visuele Fragment**. Klik **creëren**.

![ ACOP ](./images/fragm2.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen a **1:1 kolom** van het menu in het canvas. Dit is de plaatsaanduiding voor de logoafbeelding.

![ Journey Optimizer ](./images/fragm3.png)

Vervolgens kunt u Inhoud-componenten gebruiken om inhoud binnen deze blokken toe te voegen. De belemmering en laat vallen een **component van het Beeld** in de eerste cel op de eerste rij. Klik **doorbladeren**.

![ Journey Optimizer ](./images/fragm4.png)

Dan zie je een popup opening, die je je AEM Assets Media Library toont. Ga naar de omslag **citi-signaal-beelden**, klik om het beeld **te selecteren CitiSignal-Logo-White.png** en **Uitgezocht** te klikken.

>[!NOTE]
>
>Als u niet de beelden van het Signaal van Citi in uw Bibliotheek van AEM Assets ziet, kunt u hen [ hier ](../../../assets/ajo/CitiSignal-images.zip) vinden. Download hen aan uw Desktop, creeer de omslag **citi-signaal-beelden** en upload alle beelden in die omslag.

![ Journey Optimizer ](./images/fragm5.png)

Dan zie je dit. Uw afbeelding is wit en wordt nog niet weergegeven. U moet nu een achtergrondkleur definiëren om de afbeelding correct weer te geven. Klik **Stijlen**, dan klik de **Achtergrondkleur** doos.

![ Journey Optimizer ](./images/fragm6.png)

In popup, verander de **kleurencode 0} Hex {in** #8821F4 **en verander dan nadruk door in het** 100% **gebied te klikken.** Vervolgens ziet u de nieuwe kleur die op de afbeelding is toegepast.

![ Journey Optimizer ](./images/fragm7.png)

De afbeelding is nu ook een beetje te groot. Laat ons de breedte veranderen door de **schakelaar van de Breedte** aan **40%** te schuiven.

![ Journey Optimizer ](./images/fragm8.png)

Het koptekstfragment is nu gereed. Klik **sparen** en klik dan de pijl om terug naar het vorige scherm te gaan.

![ Journey Optimizer ](./images/fragm9.png)

Uw fragment moet worden gepubliceerd voordat het kan worden gebruikt. Klik **Publish**.

![ Journey Optimizer ](./images/fragm10.png)

Na een paar notulen, zult u zien dat u de status van het fragment in **Levend** is veranderd.
Maak vervolgens een nieuw fragment voor de voettekst van uw e-mailberichten. Klik **tot fragment** leiden.

![ Journey Optimizer ](./images/fragm11.png)

## 3.2.2.2 Een voettekstfragment maken

Klik **tot fragment** leiden.

![ Journey Optimizer ](./images/fragm11.png)

Ga de naam `--aepUserLdap-- - CitiSignal - Footer` in en selecteer het **Type: Visuele Fragment**. Klik **creëren**.

![ Journey Optimizer ](./images/fragm12.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen a **1:1 kolom** van het menu in het canvas. Dit is de plaatsaanduiding voor de voettekstinhoud.

![ Journey Optimizer ](./images/fragm13.png)

Vervolgens kunt u Inhoud-componenten gebruiken om inhoud binnen deze blokken toe te voegen. De belemmering en laat vallen een **HTML** component in de eerste cel op de eerste rij. Klik de component om het te selecteren en dan, **&lt;/>** te klikken pictogram om de HTML broncode uit te geven.

![ Journey Optimizer ](./images/fragm14.png)

Dan zie je dit.

![ Journey Optimizer ](./images/fragm15.png)

Kopieer het hieronder codefragment van HTML en kleef het in **uitgeven HTML** venster in Journey Optimizer.

```html
<!--[if mso]><table cellpadding="0" cellspacing="0" border="0" width="100%"><tr><td style="text-align: center;" ><![endif]-->
<table style="width: auto; display: inline-block;">
  <tbody>
    <tr class="component-social-container">
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.facebook.com" data-component-social-icon-id="facebook">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://x.com" data-component-social-icon-id="twitter">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.instagram.com" data-component-social-icon-id="instagram">
         
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!--[if mso]></td></tr></table><![endif]-->
```

Dan heb je dit. Op de regels 7, 12 en 17 moet u nu een afbeeldingsbestand invoegen met de elementen in uw AEM Assets-bibliotheek.

![ Journey Optimizer ](./images/fragm16.png)

Zorg ervoor dat uw curseur op lijn 7 wordt gevestigd, en klik dan **Assets** in het linkermenu. Klik **Open activa selecteur** om uw beeld te selecteren.

![ Journey Optimizer ](./images/fragm17.png)

Open de omslag **citi-signaal-beelden** en klik om het beeld **Icon_Facebook.png** te selecteren. Klik **Uitgezocht**.

![ Journey Optimizer ](./images/fragm18.png)

Zorg ervoor dat uw curseur op lijn 12 wordt gevestigd, en klik dan **Open activaselecteur** om uw beeld te selecteren.

![ Journey Optimizer ](./images/fragm19.png)

Open de omslag **citi-signaal-beelden** en klik om het beeld **Icon_X.png** te selecteren. Klik **Uitgezocht**.

![ Journey Optimizer ](./images/fragm20.png)

Zorg ervoor dat uw curseur op lijn 17 wordt gevestigd, en klik dan **Open activaselecteur** om uw beeld te selecteren.

![ Journey Optimizer ](./images/fragm21.png)

Open de omslag **citi-signaal-beelden** en klik om het beeld **Icon_Instagram.png** te selecteren. Klik **Uitgezocht**.

![ Journey Optimizer ](./images/fragm22.png)

Dan zie je dit. Klik **sparen**.

![ Journey Optimizer ](./images/fragm23.png)

Dan ben je weer in de editor. De pictogrammen zijn nog niet zichtbaar omdat de achtergrond en de afbeeldingsbestanden allemaal wit zijn. Om de achtergrondkleur te veranderen, ga naar **Stijlen** en klik **de achtergrondkleur** checkbox.

![ Journey Optimizer ](./images/fragm24.png)

Verander de **kleurencode 0} Hex {in** #000000 **.**

![ Journey Optimizer ](./images/fragm25.png)

De uitlijning wijzigen die moet worden gecentreerd.

![ Journey Optimizer ](./images/fragm26.png)

Laten we andere onderdelen toevoegen aan de voettekst. De belemmering en laat vallen een **component van het Beeld** boven de component van HTML u enkel creeerde. Klik **doorbladeren**.

![ Journey Optimizer ](./images/fragm27.png)

Klik om het beelddossier **`CitiSignal_Footer_Logo.png`** te selecteren en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/fragm28.png)

Ga naar **Stijlen** en klik **de kleur van de Achtergrond** checkbox, veranderen het opnieuw in zwart. Verander de **kleurencode 0} Hex {in** #000000 **.**

![ Journey Optimizer ](./images/fragm29.png)

Verander de breedte in **20%** en verifieer dat de groepering wordt geplaatst om worden gecentreerd.

![ Journey Optimizer ](./images/fragm30.png)

Daarna, belemmering en laat vallen de component van de a **Tekst** onder de component van HTML u creeerde. Klik **doorbladeren**.

![ Journey Optimizer ](./images/fragm31.png)

Kopieer en plak de onderste tekst door de plaatsaanduidingstekst te vervangen.

```
1234 N. South Street, Anywhere, US 12345

Unsubscribe

©2024 CitiSignal, Inc and its affiliates. All rights reserved.
```

Plaats de **uitlijning van de Tekst** om worden gecentreerd.

![ Journey Optimizer ](./images/fragm32.png)

Verander de **kleur van de Doopvont** in wit, **#FFFFFF**.

![ Journey Optimizer ](./images/fragm33.png)

Verander de **Achtergrondkleur** in zwart, **#000000**.

![ Journey Optimizer ](./images/fragm34.png)

Selecteer de tekst **Unsubscribe** in footer, en klik het **pictogram van de Verbinding** in de menubar. Plaats het **Type** aan **Externe Opt-out/Unsubscription** en plaats URL aan **https://aepdemo.net/unsubscribe.html** (het is niet toegestaan om een lege URL voor unsubscribe verbinding te hebben).

![ Journey Optimizer ](./images/fragm35.png)

Dan heb je dit. Uw voettekst is nu klaar. Klik **sparen** en klik dan de pijl om terug naar de vorige pagina te gaan.

![ Journey Optimizer ](./images/fragm36.png)

Klik **Publish** om uw footer te publiceren zodat kan het in een e-mail worden gebruikt.

![ Journey Optimizer ](./images/fragm37.png)

Na een paar notulen, zult u zien dat het statuut van uw footer is veranderd in **Levend**.

![ Journey Optimizer ](./images/fragm38.png)

## 3.2.2.3 Fiber-reis maken

Nu maak je een reis. In tegenstelling tot op gebeurtenissen gebaseerde reizen die afhankelijk zijn van gebeurtenissen uit de inkomende ervaring, zal deze reis zich richten op het lezen van een bestaand publiek en zal deze reis één keer gericht zijn op een heel publiek met unieke inhoud, zoals nieuwsbrieven, eenmalige promoties of specifieke campagnes.

In het menu, ga naar **Reizen** en klik **creeer reis**.

![ Journey Optimizer ](./images/campaign1.png)

Voor het scherm van de reisverwezenlijking, plaats de **Naam** aan `--aepUserLdap-- - Fiber`. Klik **sparen**.

![ Journey Optimizer ](./images/campaign2.png)

In het **Orchestration** menu, sleep en laat vallen het **Gelezen voorwerp van het Publiek** op het canvas.

![ Journey Optimizer ](./images/campaign2a.png)

Klik **uitgeven** pictogram om een publiek te selecteren.

![ Journey Optimizer ](./images/campaign2b.png)

Voor het **publiek**, selecteer het publiek u in de vorige stap, `--aepUserLdap-- - CitiSignal Eligible for Fiber` creeerde. Klik **sparen**.

![ Journey Optimizer ](./images/campaign2c.png)

Dan moet je dit zien. Plaats **Namespace** aan **E-mail**. Klik **sparen**.

![ Journey Optimizer ](./images/campaign3.png)

Onder **Acties**, belemmering en laat vallen de **E-mail** actie op het canvas.

![ Journey Optimizer ](./images/campaign4.png)

Plaats de **Categorie** aan **Marketing** en selecteer a **Configuratie** voor **E-mail**. Klik **uitgeven inhoud**.

![ Journey Optimizer ](./images/campaign5.png)

Dan zie je dit. Klik **uitgeven** pictogram naast de **Onderworpen lijn**.

![ Journey Optimizer ](./images/campaign6.png)

Stel de onderwerpregel in op:

```
{{profile.person.name.firstName}}, here's your Fiber offer!
```

Klik **sparen**.

![ Journey Optimizer ](./images/campaign5a.png)

Dan moet je dit zien. Daarna, klik **uitgeeft e-maillichaam**.

![ Journey Optimizer ](./images/campaign5b.png)

Kies **Ontwerp van kras**.

![ Journey Optimizer ](./images/campaign7.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen 2 keer a **1:1 kolom** op het canvas, dat u deze structuur zou moeten geven:

![ Journey Optimizer ](./images/campaign8.png)

In het linkermenu, ga naar **Fragments**. Sleep de koptekst die u eerder hebt gemaakt naar de eerste component op het canvas. Sleep de voettekst die u eerder hebt gemaakt naar de laatste component op het canvas.

![ Journey Optimizer ](./images/campaign9.png)

Klik op het pictogram **+** in het linkermenu. Ga naar **Inhoud** beginnen inhoud op het canvas toe te voegen.

![ Journey Optimizer ](./images/campaign10.png)

De belemmering en laat vallen component van de a **Tekst** op de tweede rij.

![ Journey Optimizer ](./images/campaign11.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst. Verander de groepering aan **groepering van het Centrum**.

```javascript
Hi {{profile.person.name.firstName}}

As a CitiSignal member, you're part of a dynamic community that's constantly evolving to meet your needs. We're committed to delivering innovative solutions that enhance your digital lifestyle and keep you ahead of the curve.

Stay connected.
```

![ Journey Optimizer ](./images/campaign12.png)

De belemmering en laat vallen een **component van het Beeld** op de 3de en 4de rij. Klik **doorbladeren** op de 3de rij.

![ Journey Optimizer ](./images/campaign13.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **Offer_AirPods.jpg** te selecteren, en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/campaign14.png)

Klik **doorbladeren** op beeldplaceholder op de 4de rij.

![ Journey Optimizer ](./images/campaign15.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **Offer_Phone.jpg** te selecteren, en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/campaign16.png)

De belemmering en laat vallen a **component van de Tekst van 0} {op de 3de en 4de rij.**

![ Journey Optimizer ](./images/campaign17.png)

Selecteer de standaardtekst in de component op de 3de rij **Gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst.

```javascript
Get AirPods for free:

Experience seamless connectivity like never before with CitiSignal. Sign up for select premium plans and receive a complimentary pair of Apple AirPods. Stay connected in style with our unbeatable offer.
```

Selecteer de standaardtekst in de component op de 4de rij **Gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst.

```javascript
We'll pay off your phone:

Make the switch to CitiSignal and say goodbye to phone payments! Switching to CitiSignal has never been more rewarding. Say farewell to hefty phone bills as we help pay off your phone, up to 800$!
```

![ Journey Optimizer ](./images/campaign18.png)

Je standaardnieuwsbrief is nu klaar. Klik **sparen**.

Ga terug naar het campagnesdashboard door de **pijl** naast de onderwerpregel tekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/campaign19.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./images/campaign20.png)

Deze fout kan dan optreden. Als dat het geval is, dan kunt u tot 24 uur moeten wachten tot het publiek is geëvalueerd, en dan proberen om uw campagne opnieuw te activeren. Mogelijk moet u ook het programma van uw campagne bijwerken zodat deze later kan worden uitgevoerd.

Klik **activeren**.

![ Journey Optimizer ](./images/campaign21.png)

Als de campagne eenmaal is geactiveerd, wordt deze gepland.

![ Journey Optimizer ](./images/campaign22.png)

Uw campagne is nu geactiveerd. Uw e-mailbericht voor de nieuwsbrief wordt verzonden zoals u het in uw programma hebt gedefinieerd. Uw campagne wordt beëindigd zodra het laatste e-mailbericht is verzonden.

U ontvangt de e-mail ook op het e-mailadres dat u hebt gebruikt voor het demoprofiel dat u eerder hebt gemaakt.

![ Journey Optimizer ](./images/campaign23.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ 3.2.3.. ](./ex3.md)

Ga terug naar [ Module 3.2 ](./ajotranslationsvcs.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}

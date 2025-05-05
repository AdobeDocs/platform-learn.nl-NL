---
title: Maak uw campagne met AJO Translation Services
description: Maak uw campagne met AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: 441b3b6a-74e5-4294-9a30-9c44ea4bbf84
source-git-commit: 7438a1289689c5c3fb3deb398aa9898d7ac26cf8
workflow-type: tm+mt
source-wordcount: '1596'
ht-degree: 0%

---

# 3.5.2 Uw campagne maken

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik **Journey Optimizer**.

![ Vertalingen ](./images/ajolp1.png)

U zult aan de **1&rbrace; mening van het Huis &lbrace;in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![ ACOP ](./images/ajolp2.png)

>[!NOTE]
>
>Voor het geval u reeds uw fragmenten van de Kopbal en van de Voettekst als deel van oefening [ oefening 3.1.2.1 ](./../module3.1/ex2.md) en [ oefening 3.1.2.2 ](./../module3.1/ex2.md) hebt gecreeerd, gelieve vooruit te springen om 3.5.2.3 uit te oefenen creeer de campagne van de Vezel. Maak niet opnieuw kop- en voettekstfragmenten.

## 3.5.2.1 Een koptekstfragment maken

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

U ziet dan een popup opening, die u uw Bibliotheek van de Media van AEM Assets toont. Ga naar de omslag **citi-signaal-beelden**, klik om het beeld **te selecteren CitiSignal-Logo-White.png** en **Uitgezocht** te klikken.

>[!NOTE]
>
>Als u niet de beelden van het Signaal van Citi in uw Bibliotheek van AEM Assets ziet, kunt u hen [ hier ](../../../assets/ajo/CitiSignal-images.zip) vinden. Download hen aan uw Desktop, creeer de omslag **citi-signaal-beelden** en upload alle beelden in die omslag.

![ Journey Optimizer ](./images/fragm5.png)

Dan zie je dit. Uw afbeelding is wit en wordt nog niet weergegeven. U moet nu een achtergrondkleur definiëren om de afbeelding correct weer te geven. Klik **Stijlen**, dan klik de **Achtergrondkleur** doos.

![ Journey Optimizer ](./images/fragm6.png)

In popup, verander de **kleurencode 0&rbrace; Hex &lbrace;in** #8821F4 **en verander dan nadruk door in het** 100% **gebied te klikken.** Vervolgens ziet u de nieuwe kleur die op de afbeelding is toegepast.

![ Journey Optimizer ](./images/fragm7.png)

De afbeelding is nu ook een beetje te groot. Laat ons de breedte veranderen door de **schakelaar van de Breedte** aan **40%** te schuiven.

![ Journey Optimizer ](./images/fragm8.png)

Het koptekstfragment is nu gereed. Klik **sparen** en klik dan de pijl om terug naar het vorige scherm te gaan.

![ Journey Optimizer ](./images/fragm9.png)

Uw fragment moet worden gepubliceerd voordat het kan worden gebruikt. Klik **publiceren**.

![ Journey Optimizer ](./images/fragm10.png)

Na een paar notulen, zult u zien dat u de status van het fragment in **Levend** is veranderd.
Maak vervolgens een nieuw fragment voor de voettekst van uw e-mailberichten. Klik **tot fragment** leiden.

![ Journey Optimizer ](./images/fragm11.png)

## 3.5.2.2 Een voettekstfragment maken

Klik **tot fragment** leiden.

![ Journey Optimizer ](./images/fragm11.png)

Ga de naam `--aepUserLdap-- - CitiSignal - Footer` in en selecteer het **Type: Visuele Fragment**. Klik **creëren**.

![ Journey Optimizer ](./images/fragm12.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen a **1:1 kolom** van het menu in het canvas. Dit is de plaatsaanduiding voor de voettekstinhoud.

![ Journey Optimizer ](./images/fragm13.png)

Vervolgens kunt u Inhoud-componenten gebruiken om inhoud binnen deze blokken toe te voegen. De belemmering en laat vallen een **HTML** component in de eerste cel op de eerste rij. Klik de component om het te selecteren en dan, klik **&lt;/>** pictogram om de HTML broncode uit te geven.

![ Journey Optimizer ](./images/fragm14.png)

Dan zie je dit.

![ Journey Optimizer ](./images/fragm15.png)

Kopieer het hieronder codefragment van HTML en kleef het in **HTML** venster in Journey Optimizer uitgeven.

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

Verander de **kleurencode 0&rbrace; Hex &lbrace;in** #000000 **.**

![ Journey Optimizer ](./images/fragm25.png)

De uitlijning wijzigen die moet worden gecentreerd.

![ Journey Optimizer ](./images/fragm26.png)

Laten we andere onderdelen toevoegen aan de voettekst. De belemmering en laat vallen een **component van het Beeld** boven de component van HTML u enkel creeerde. Klik **doorbladeren**.

![ Journey Optimizer ](./images/fragm27.png)

Klik om het beelddossier **`CitiSignal_Footer_Logo.png`** te selecteren en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/fragm28.png)

Ga naar **Stijlen** en klik **de kleur van de Achtergrond** checkbox, veranderen het opnieuw in zwart. Verander de **kleurencode 0&rbrace; Hex &lbrace;in** #000000 **.**

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

Klik **publiceren** om uw footer te publiceren zodat kan het in e-mail worden gebruikt.

![ Journey Optimizer ](./images/fragm37.png)

Na een paar notulen, zult u zien dat het statuut van uw footer is veranderd in **Levend**.

![ Journey Optimizer ](./images/fragm38.png)

## 3.5.2.3 Vezelcampagne maken

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![ Journey Optimizer ](./images/oc43.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![ Journey Optimizer ](./images/campaign1.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap-- - CitiSignal Fiber`.
- **Beschrijving**: De campagne van de Vezel
- **Type van Identiteit**: verandering in E-mail

![ Journey Optimizer ](./images/campaign2.png)

De rol neer aan **Actie**. Voor de **Actie**, uitgezochte **E-mail**.

![ Journey Optimizer ](./images/campaign3.png)

Dan, selecteer een bestaande **E-mailconfiguratie**. U gaat de inhoud over een paar minuten bewerken.

![ Journey Optimizer ](./images/campaign3a.png)

De rol omhoog aan **Publiek**. Klik **Uitgezochte publiek**.

![ Journey Optimizer ](./images/campaign2b.png)

Voor het **publiek**, selecteer het publiek u in [ 1.3.3 creeerde een gefedereerde samenstelling ](./../../datacollection/module1.3/ex3.md), die `--aepUserLdap-- - CitiSignal Eligible for Fiber` wordt genoemd. Klik **sparen**.

![ Journey Optimizer ](./images/campaign2a.png)

De rol neer aan **Programma**. Voor het **Programma**, kies **op een specifieke datum en een tijd** en plaats een tijd van keus.

![ Journey Optimizer ](./images/campaign4.png)

U kunt nu het e-mailbericht zelf maken. De rol omhoog, en klikt **geeft inhoud** uit.

![ Journey Optimizer ](./images/campaign5.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit:

```
{{profile.person.name.firstName}}, here's your Fiber offer!
```

Daarna, klik **uitgeeft e-maillichaam**.

![ Journey Optimizer ](./images/campaign6.png)

Kies **Ontwerp van kras**.

![ Journey Optimizer ](./images/campaign7.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen 4 keer a **1:1 kolom** op het canvas, dat u deze structuur zou moeten geven:

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

As a CitiSignal customer, you're in pole position to discover our new Fiber offering. Have a look at the below offer and update your contract!

Stay connected.
```

![ Journey Optimizer ](./images/campaign12.png)

De belemmering en laat vallen een **component van het Beeld** op de 3de rij. Klik **doorbladeren**.

![ Journey Optimizer ](./images/campaign13.png)

Selecteer de AEM Assets-opslagplaats die u als onderdeel van vorige modules hebt gemaakt. Die gegevensopslagruimte moet de naam `--aepUserLdap-- - Citi Signal dev` hebben. Klik om de map `--aepUserLdap-- - Workfront Assets` te openen.

![ Journey Optimizer ](./images/campaign15a.png)

Klik om het beeld **2048x2048_buynow.png** te selecteren, en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/campaign14.png)

Je standaardnieuwsbrief is nu klaar. Klik **sparen**.

![ Journey Optimizer ](./images/ready.png)

Ga terug naar het campagnesdashboard door de **pijl** naast de onderwerpregel tekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/campaign19.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./images/campaign20.png)

Deze fout kan dan optreden. Als dat het geval is, dan kunt u tot 24 uur moeten wachten tot het publiek is geëvalueerd, en dan proberen om uw campagne opnieuw te activeren. Mogelijk moet u ook het programma van uw campagne bijwerken zodat deze later kan worden uitgevoerd.

![ Journey Optimizer ](./images/campaign21a.png)

Klik **activeren**.

![ Journey Optimizer ](./images/campaign21.png)

Nadat de campagne is geactiveerd, wordt deze gepland.

![ Journey Optimizer ](./images/campaign22.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ 3.5.3 toevoegen Talen aan uw E-mail ](./ex3.md)

Ga terug naar [ Module 3.5 ](./ajotranslationsvcs.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}

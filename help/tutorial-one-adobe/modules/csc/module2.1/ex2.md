---
title: Cloud Manager-programma maken
description: Cloud Manager-programma maken
kt: 5342
doc-type: tutorial
source-git-commit: 89611537cad42082af1b9aa753752d5450f103a5
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---

# 2.1.2 De AEM CS-omgeving instellen

## 2.1.2.1 Opstelling uw repo van GitHub

Ga naar [ https://github.com ](https://github.com). Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup1.png)

Voer uw referenties in. Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup2.png)

Zodra binnen ondertekend, zult u uw dashboard zien GitHub.

![ AEMCS ](./images/aemcssetup3.png)

Ga naar [ https://github.com/AdobeDevXSC/citisignal-one ](https://github.com/AdobeDevXSC/citisignal-one). Dan zie je dit. Klik **Gebruik dit malplaatje** en klik dan **creeer een nieuwe bewaarplaats**.

![ AEMCS ](./images/aemcssetup4.png)

Voor de **naam van de Bewaarplaats**, gebruik `citisignal`. Plaats het zicht aan **Privé**. Klik **creeer bewaarplaats**.

![ AEMCS ](./images/aemcssetup5.png)

Na een paar seconden wordt de repository gemaakt.

![ AEMCS ](./images/aemcssetup6.png)

Daarna, ga naar [ https://github.com/apps/aem-code-sync ](https://github.com/apps/aem-code-sync). Klik **vormen**.

![ AEMCS ](./images/aemcssetup7.png)

Klik op uw GitHub-account.

![ AEMCS ](./images/aemcssetup8.png)

Klik **slechts uitgezochte bewaarplaatsen** en voeg dan de bewaarplaats toe die u enkel creeerde. Daarna, klik **installeren**.

![ AEMCS ](./images/aemcssetup9.png)

Je krijgt deze bevestiging.

![ AEMCS ](./images/aemcssetup10.png)

## 2.1.2.2 Bestand fstab.yaml bijwerken

Klik in uw GitHub-repo om het bestand `fstab.yaml` te openen.

![ AEMCS ](./images/aemcssetup11.png)

Klik **uitgeven** pictogram.

![ AEMCS ](./images/aemcssetup12.png)

U moet nu de waarde voor het gebied **url** op lijn 4 bijwerken.

![ AEMCS ](./images/aemcssetup13.png)

U moet de huidige waarde door URL van uw specifiek milieu van AEMCS in combinatie met de montages van uw reactie vervangen GitHub.

Dit is de huidige waarde van de URL: `https://author-p131639-e1282833.adobeaemcloud.com/bin/franklin.delivery/adobedevxsc/citisignal-one/main` .

Er zijn 3 delen van de URL die moeten worden bijgewerkt

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX moet worden vervangen door de URL van de AEM CS Author-omgeving.

YYYY zou door uw GitHub gebruiksrekening moeten worden vervangen.

ZZZ zou door de naam van de bewaarplaats moeten worden vervangen GitHub die u in de vorige oefening gebruikte.

U kunt URL van uw AEM milieu van de Auteur van CS vinden door [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com) te gaan. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Daarna, klik de 3 punten **..** op het **milieu&#39;s** lusje en klik **Details van de Mening**.

![ AEMCS ](./images/aemcs9.png)

U zult dan uw milieudetails, met inbegrip van URL van uw **milieu van de Auteur** zien. De URL kopiëren.

![ AEMCS ](./images/aemcs10.png)

XXX = `author-p148073-e1511503.adobeaemcloud.com`

Voor de naam van de GitHub-gebruikersaccount kunt u dat gemakkelijk vinden in de URL van uw browser. In dit voorbeeld is de naam van de gebruikersaccount `woutervangeluwe` .

YYY = `woutervangeluwe`

![ AEMCS ](./images/aemcs11.png)

Voor de bewaarplaatsnaam GitHub, kunt u het in het browser venster ook vinden dat u in GitHub hebt geopend. In dit geval is de naam van de gegevensopslagruimte `citisignal` .

ZZZ = `citisignal`

![ AEMCS ](./images/aemcs12.png)

Deze drie waarden samen leiden tot deze nieuwe URL die moet worden geconfigureerd in het bestand `fstab.yaml` .

`https://author-p148073-e1511503.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal/main`

Klik **Veranderingen vastleggen...**.

![ AEMCS ](./images/aemcs13.png)

Klik **veranderingen** vastleggen.

![ AEMCS ](./images/aemcs14.png)

Het bestand `fstab.yaml` is nu bijgewerkt.

## 2.1.2.3 CitiSignal-middelen uploaden

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com). Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png)

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png)

U ziet dan de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup20.png)

Uw URL ziet er als volgt uit: `https://author-p148073-e1511503.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

U moet nu tot het **milieu van de Manager van het Pakket van CRX** van AEM toegang hebben. U doet dit door `ui#/aem/aem/start.html?appId=aemshell` te verwijderen van de URL en deze te vervangen door `crx/packmgr` . Dit houdt in dat uw URL er nu als volgt moet uitzien:
`https://author-p148073-e1511503.adobeaemcloud.com/crx/packmgr` .
Het greep **gaat** binnen om het milieu van de pakketmanager te laden

![ AEMCS ](./images/aemcssetup22.png)

Daarna, klik **uploadt pakket**.

![ AEMCS ](./images/aemcssetup21.png)

Klik **doorbladeren** om van het te uploaden pakket de plaats te bepalen.

Het te uploaden pakket wordt genoemd **burgersignaal-assets.zip** en kan hier worden gedownload: [ https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip ](https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip).

![ AEMCS ](./images/aemcssetup23.png)

Selecteer het pakket en klik **Open**.

![ AEMCS ](./images/aemcssetup24.png)

Daarna, klik O.K. ****.

![ AEMCS ](./images/aemcssetup25.png)

Het pakket wordt vervolgens geüpload.

![ AEMCS ](./images/aemcssetup26.png)

Daarna, klik **installeer** op het pakket u enkel uploadde.

![ AEMCS ](./images/aemcssetup27.png)

Klik **installeren**.

![ AEMCS ](./images/aemcssetup28.png)

Na een paar minuten wordt uw pakket geïnstalleerd.

![ AEMCS ](./images/aemcssetup29.png)

U kunt dit venster nu sluiten.


## 2.1.2.4 Publish CitiSignal-activa

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com). Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png)

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png)

U ziet dan de omgeving van uw auteur. Klik **Plaatsen**.

![ AEMCS ](./images/aemcsassets1.png)

Klik **Dossiers**.

![ AEMCS ](./images/aemcsassets2.png)

Klik om de omslag **te selecteren CitiSignal** en dan **te klikken leidt Publicatie**.

![ AEMCS ](./images/aemcsassets3.png)

Klik **daarna**.

![ AEMCS ](./images/aemcsassets4.png)

Klik **Publish**.

![ AEMCS ](./images/aemcsassets5.png)

Uw middelen zijn nu gepubliceerd.

## 2.1.2.5 CitiSignal-website maken

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com). Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png)

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png)

U ziet dan de omgeving van uw auteur. Klik **Plaatsen**.

![ AEMCS ](./images/aemcssetup30.png)

Klik **creëren** en klik dan **Plaats van malplaatje**.

![ AEMCS ](./images/aemcssetup31.png)

Klik **Invoer**.

![ AEMCS ](./images/aemcssetup32.png)

U moet nu een vooraf geconfigureerde sjabloon voor uw site importeren. U kunt het malplaatje [ hier ](./../../../assets/aem/citisignal-edge-delivery-services-template-0.0.4.zip) downloaden. Sla het bestand op uw bureaublad op.

Daarna, selecteer het dossier `citisignal-edge-delivery-services-template-0.0.4.zip` en klik **Open**.

![ AEMCS ](./images/aemcssetup33.png)

Dan zie je dit. Klik om het malplaatje te selecteren u enkel uploadde en dan, klik **daarna**.

![ AEMCS ](./images/aemcssetup34.png)

U moet nu enkele details invullen.

- Plaats titel: gebruik **CitiSignal**
- De naam van de plaats: gebruik **burgersignaal-één**
- GitHub URL: kopieer URL van de reactie GitHub u vóór gebruikte

![ AEMCS ](./images/aemcssetup35.png)

Dan heb je dit. Klik **creëren**.

![ AEMCS ](./images/aemcssetup36.png)

Uw site wordt nu gemaakt. Dit kan een paar minuten duren. Klik **OK**.

![ AEMCS ](./images/aemcssetup37.png)

Vernieuw het scherm na een paar minuten en dan ziet u de zojuist gemaakte CitiSignal-website.

![ AEMCS ](./images/aemcssetup38.png)

## 2.1.2.6 Publish CitiSignal-website

Daarna, klik checkbox vóór **CitiSignal**. Dan, klik **leiden Publicatie**.

![ AEMCS ](./images/aemcssetup39.png)

Klik **daarna**.

![ AEMCS ](./images/aemcssetup40.png)

Klik **omvatten de Montages van Kinderen**.

![ AEMCS ](./images/aemcssetup41.png)

Klik om checkbox **te selecteren omvat kinderen** en klik dan om andere checkboxes te deselecteren. Klik **OK**.

![ AEMCS ](./images/aemcssetup42.png)

Klik **Publish**.

![ AEMCS ](./images/aemcssetup43.png)

Je wordt hier teruggestuurd. Navigeer aan **CitiSignal** > **gebruiken** > **en**. Klik checkbox voor **index** en klik dan **uitgeven**.

![ AEMCS ](./images/aemcssetup44.png)

Uw website zal dan in de **Universele Redacteur** openen.

![ AEMCS ](./images/aemcssetup45.png)

U kunt nu ook naar uw website navigeren door naar `main--citisignal--woutervangeluwe.aem.live/us/en` te gaan



[Terug naar module 2.1](./aemcs.md)

[Terug naar alle modules](./../../../overview.md)

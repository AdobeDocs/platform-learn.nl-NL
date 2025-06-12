---
title: AEM CS-omgeving instellen
description: AEM CS-omgeving instellen
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
source-git-commit: 457e7d0dec233edf75717fb9930585a3511bdc65
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# 1.1.3 De AEM CS-omgeving instellen

## 1.1.3.1 Uw GitHub-repo instellen

Ga naar [ https://github.com ](https://github.com){target="_blank"}. Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup1.png){zoomable="yes"}

Voer uw referenties in. Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup2.png){zoomable="yes"}

Zodra binnen ondertekend, zult u uw dashboard zien GitHub.

![ AEMCS ](./images/aemcssetup3.png){zoomable="yes"}

Ga naar [ https://github.com/AdobeDevXSC/citisignal-one ](https://github.com/AdobeDevXSC/citisignal-one){target="_blank"}. Dan zie je dit. Klik **Gebruik dit malplaatje** en klik dan **creeer een nieuwe bewaarplaats**.

![ AEMCS ](./images/aemcssetup4.png){zoomable="yes"}

Voor de **naam van de Bewaarplaats**, gebruik `citisignal`. Plaats het zicht aan **Privé**. Klik **creeer bewaarplaats**.

![ AEMCS ](./images/aemcssetup5.png){zoomable="yes"}

Na een paar seconden wordt de repository gemaakt.

![ AEMCS ](./images/aemcssetup6.png){zoomable="yes"}

Daarna, ga naar [ https://github.com/apps/aem-code-sync ](https://github.com/apps/aem-code-sync){target="_blank"}. Klik **vormen**.

![ AEMCS ](./images/aemcssetup7.png){zoomable="yes"}

Klik op uw GitHub-account.

![ AEMCS ](./images/aemcssetup8.png){zoomable="yes"}

Klik **slechts uitgezochte bewaarplaatsen** en voeg dan de bewaarplaats toe die u enkel creeerde. Daarna, klik **installeren**.

![ AEMCS ](./images/aemcssetup9.png){zoomable="yes"}

Je krijgt deze bevestiging.

![ AEMCS ](./images/aemcssetup10.png){zoomable="yes"}

## 1.1.3.2 Bestand fstab.yaml bijwerken

Klik in uw GitHub-repo om het bestand `fstab.yaml` te openen.

![ AEMCS ](./images/aemcssetup11.png){zoomable="yes"}

Klik **uitgeven** pictogram.

![ AEMCS ](./images/aemcssetup12.png){zoomable="yes"}

U moet nu de waarde voor het gebied **url** op lijn 4 bijwerken.

![ AEMCS ](./images/aemcssetup13.png){zoomable="yes"}

U moet de huidige waarde door URL van uw specifiek milieu van AEM CS in combinatie met de montages van uw reactie vervangen GitHub.

Dit is de huidige waarde van de URL: `https://author-p131639-e1282833.adobeaemcloud.com/bin/franklin.delivery/adobedevxsc/citisignal-one/main` .

Er zijn 3 delen van de URL die moeten worden bijgewerkt

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX moet worden vervangen door de URL van uw AEM CS Author-omgeving.

YYY zou door uw GitHub gebruikersrekening moeten worden vervangen.

ZZZ zou door de naam van de bewaarplaats moeten worden vervangen GitHub die u in de vorige oefening gebruikte.

U kunt URL van uw milieu van de Auteur van AEM CS vinden door [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"} te gaan. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png){zoomable="yes"}

Daarna, klik de 3 punten **..** op het **milieu&#39;s** lusje en klik **Details van de Mening**.

![ AEMCS ](./images/aemcs9.png){zoomable="yes"}

U zult dan uw milieudetails, met inbegrip van URL van uw **milieu van de Auteur** zien. De URL kopiëren.

![ AEMCS ](./images/aemcs10.png){zoomable="yes"}

XXX = `author-p148073-e1511503.adobeaemcloud.com`

Voor de naam van de GitHub-gebruikersaccount kunt u dat gemakkelijk vinden in de URL van uw browser. In dit voorbeeld is de naam van de gebruikersaccount `woutervangeluwe` .

YYY = `woutervangeluwe`

![ AEMCS ](./images/aemcs11.png){zoomable="yes"}

Voor de bewaarplaatsnaam GitHub, kunt u het in het browser venster ook vinden dat u in GitHub hebt geopend. In dit geval is de naam van de gegevensopslagruimte `citisignal` .

ZZZ = `citisignal`

![ AEMCS ](./images/aemcs12.png){zoomable="yes"}

Deze drie waarden samen leiden tot deze nieuwe URL die moet worden geconfigureerd in het bestand `fstab.yaml` .

`https://author-p148073-e1511503.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal/main`

Klik **Veranderingen vastleggen...**.

![ AEMCS ](./images/aemcs13.png){zoomable="yes"}

Klik **veranderingen** vastleggen.

![ AEMCS ](./images/aemcs14.png){zoomable="yes"}

Het bestand `fstab.yaml` is nu bijgewerkt.

## 1.1.3.3 CitiSignal-elementen uploaden

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png){zoomable="yes"}

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png){zoomable="yes"}

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png){zoomable="yes"}

U ziet dan de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup20.png){zoomable="yes"}

Uw URL ziet er als volgt uit: `https://author-p148073-e1511503.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

U moet nu tot het **milieu van de Manager van het Pakket van CRX** van AEM toegang hebben. U doet dit door `ui#/aem/aem/start.html?appId=aemshell` te verwijderen van de URL en deze te vervangen door `crx/packmgr` . Dit houdt in dat uw URL er nu als volgt moet uitzien:
`https://author-p148073-e1511503.adobeaemcloud.com/crx/packmgr` .
Het greep **gaat** binnen om het milieu van de pakketmanager te laden

![ AEMCS ](./images/aemcssetup22.png){zoomable="yes"}

Daarna, klik **uploadt pakket**.

![ AEMCS ](./images/aemcssetup21.png){zoomable="yes"}

Klik **doorbladeren** om van het te uploaden pakket de plaats te bepalen.

Het te uploaden pakket wordt genoemd **burgersignaal-assets.zip** en kan hier worden gedownload: [ https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip ](https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip){target="_blank"}.

![ AEMCS ](./images/aemcssetup23.png){zoomable="yes"}

Selecteer het pakket en klik **Open**.

![ AEMCS ](./images/aemcssetup24.png){zoomable="yes"}

Daarna, klik O.K. ****.

![ AEMCS ](./images/aemcssetup25.png){zoomable="yes"}

Het pakket wordt vervolgens geüpload.

![ AEMCS ](./images/aemcssetup26.png){zoomable="yes"}

Daarna, klik **installeer** op het pakket u enkel uploadde.

![ AEMCS ](./images/aemcssetup27.png){zoomable="yes"}

Klik **installeren**.

![ AEMCS ](./images/aemcssetup28.png){zoomable="yes"}

Na een paar minuten wordt uw pakket geïnstalleerd.

![ AEMCS ](./images/aemcssetup29.png){zoomable="yes"}

U kunt dit venster nu sluiten.


## 1.1.3.4 CitiSignal-elementen publiceren

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png){zoomable="yes"}

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png){zoomable="yes"}

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png){zoomable="yes"}

U ziet dan de omgeving van uw auteur. Klik **Assets**.

![ AEMCS ](./images/aemcsassets1.png){zoomable="yes"}

Klik **Dossiers**.

![ AEMCS ](./images/aemcsassets2.png){zoomable="yes"}

Klik om de omslag **te selecteren CitiSignal** en dan **te klikken leidt Publicatie**.

![ AEMCS ](./images/aemcsassets3.png){zoomable="yes"}

Klik **daarna**.

![ AEMCS ](./images/aemcsassets4.png){zoomable="yes"}

Klik **publiceren**.

![ AEMCS ](./images/aemcsassets5.png){zoomable="yes"}

Uw middelen zijn nu gepubliceerd.

## 1.1.3.5 CitiSignal-website maken

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png){zoomable="yes"}

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png){zoomable="yes"}

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png){zoomable="yes"}

U ziet dan de omgeving van uw auteur. Klik **Plaatsen**.

![ AEMCS ](./images/aemcssetup30.png){zoomable="yes"}

Klik **creëren** en klik dan **Plaats van malplaatje**.

![ AEMCS ](./images/aemcssetup31.png){zoomable="yes"}

Klik **Invoer**.

![ AEMCS ](./images/aemcssetup32.png){zoomable="yes"}

U moet nu een vooraf geconfigureerde sjabloon voor uw site importeren. U kunt het malplaatje [ hier ](./../../../assets/aem/citisignal-edge-delivery-services-template-0.0.4.zip){target="_blank"} downloaden. Sla het bestand op uw bureaublad op.

Daarna, selecteer het dossier `citisignal-edge-delivery-services-template-0.0.4.zip` en klik **Open**.

![ AEMCS ](./images/aemcssetup33.png){zoomable="yes"}

Dan zie je dit. Klik om het malplaatje te selecteren u enkel uploadde en dan, klik **daarna**.

![ AEMCS ](./images/aemcssetup34.png){zoomable="yes"}

U moet nu enkele details invullen.

- Plaats titel: gebruik **CitiSignal**
- De naam van de plaats: gebruik **burgersignaal-één**
- GitHub URL: kopieer URL van de reactie GitHub u vóór gebruikte

![ AEMCS ](./images/aemcssetup35.png){zoomable="yes"}

Dan heb je dit. Klik **creëren**.

![ AEMCS ](./images/aemcssetup36.png){zoomable="yes"}

Uw site wordt nu gemaakt. Dit kan een paar minuten duren. Klik **OK**.

![ AEMCS ](./images/aemcssetup37.png){zoomable="yes"}

Vernieuw het scherm na een paar minuten en dan ziet u de zojuist gemaakte CitiSignal-website.

![ AEMCS ](./images/aemcssetup38.png){zoomable="yes"}

## 1.1.3.6 CitiSignal-website publiceren

Daarna, klik checkbox vóór **CitiSignal**. Dan, klik **leiden Publicatie**.

![ AEMCS ](./images/aemcssetup39.png){zoomable="yes"}

Klik **daarna**.

![ AEMCS ](./images/aemcssetup40.png){zoomable="yes"}

Klik **omvatten de Montages van Kinderen**.

![ AEMCS ](./images/aemcssetup41.png){zoomable="yes"}

Klik om checkbox **te selecteren omvat kinderen** en klik dan om andere checkboxes te deselecteren. Klik **OK**.

![ AEMCS ](./images/aemcssetup42.png){zoomable="yes"}

Klik **publiceren**.

![ AEMCS ](./images/aemcssetup43.png){zoomable="yes"}

Je wordt hier teruggestuurd. Navigeer aan **CitiSignal** > **gebruiken** > **en**. Klik checkbox voor **index** en klik dan **uitgeven**.

![ AEMCS ](./images/aemcssetup44.png){zoomable="yes"}

Uw website zal dan in de **Universele Redacteur** openen.

![ AEMCS ](./images/aemcssetup45.png){zoomable="yes"}

U kunt nu toegang krijgen tot uw website door naar `main--citisignal--XXX.aem.page/us/en/` en/of `main--citisignal--XXX.aem.live/us/en/` te gaan, nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, die in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` en/of `https://main--citisignal--woutervangeluwe.aem.live/us/en/` .

Het kan enige tijd duren voordat alle activa correct zijn weergegeven, aangezien deze eerst moeten worden gepubliceerd.

U zult dan dit zien:

![ AEMCS ](./images/aemcssetup46.png){zoomable="yes"}

Na een paar minuten worden alle elementen correct geladen.

![ AEMCS ](./images/aemcssetup47.png){zoomable="yes"}

## 1.1.3.7 Paginaprestaties testen

Ga naar [ https://pagespeed.web.dev/ ](https://pagespeed.web.dev/){target="_blank"}. Ga uw URL in en klik **analyseren**.

![ AEMCS ](./images/aemcssetup48.png){zoomable="yes"}

Vervolgens ziet u dat uw website, zowel voor mobiele als voor desktoptoepassingen, een hoge score haalt:

**Mobiel**:

![ AEMCS ](./images/aemcssetup49.png){zoomable="yes"}

**Desktop**:

![ AEMCS ](./images/aemcssetup50.png){zoomable="yes"}

Volgende Stap: [ 1.1.4 vormt een douaneblok ](./ex4.md){target="_blank"}

Ga terug naar [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./aemcs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

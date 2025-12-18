---
title: AEM CS-omgeving instellen
description: AEM CS-omgeving instellen
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
source-git-commit: 13f74467a74eb3d8bbd135f5b8c7d9bb1a177f8b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---

# 1.1.2 De AEM CS-omgeving instellen

## 1.1.2.1 Uw GitHub-repo instellen

Ga naar [ https://github.com ](https://github.com){target="_blank"}. Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup1.png)

Voer uw referenties in. Klik **Teken binnen**.

![ AEMCS ](./images/aemcssetup2.png)

Zodra binnen ondertekend, zult u uw dashboard zien GitHub.

![ AEMCS ](./images/aemcssetup3.png)

Ga naar [ https://github.com/adobe-rnd/aem-boilerplate-xcom ](https://github.com/adobe-rnd/aem-boilerplate-xcom){target="_blank"}. Dan zie je dit. Klik **Gebruik dit malplaatje** en klik dan **creeer een nieuwe bewaarplaats**.

![ AEMCS ](./images/aemcssetup4.png)

Voor de **naam van de Bewaarplaats**, gebruik `citisignal-aem-accs`. Plaats het zicht aan **Privé**. Klik **creeer bewaarplaats**.

![ AEMCS ](./images/aemcssetup5.png)

Na een paar seconden wordt de repository gemaakt.

![ AEMCS ](./images/aemcssetup6.png)

Daarna, ga naar [ https://github.com/apps/aem-code-sync ](https://github.com/apps/aem-code-sync){target="_blank"}. Klik **installeren** of **vormen**.

![ AEMCS ](./images/aemcssetup7.png)

Klik **verdergaan** knoop naast uw GitHub gebruikersrekening.

![ AEMCS ](./images/aemcssetup8.png)

Klik **vormen** naast uw GitHub gebruikersrekening.

![ AEMCS ](./images/aemcssetup8a.png)

Klik **slechts uitgezochte bewaarplaatsen** en voeg dan de bewaarplaats toe die u enkel creeerde.

![ AEMCS ](./images/aemcssetup9.png)

De rol neer en klikt **sparen**.

![ AEMCS ](./images/aemcssetup9a.png)

Je krijgt deze bevestiging.

![ AEMCS ](./images/aemcssetup10.png)

## 1.1.2.2 Bestand fstab.yaml bijwerken

Klik in uw GitHub-repo om het bestand `fstab.yaml` te openen.

![ AEMCS ](./images/aemcssetup11.png)

Klik **uitgeven** pictogram.

![ AEMCS ](./images/aemcssetup12.png)

U moet nu de waarde voor het gebied **url** op lijn 3 bijwerken.

![ AEMCS ](./images/aemcssetup13.png)

U moet de huidige waarde door URL van uw specifiek milieu van AEM Sites CS in combinatie met de montages van uw reactie vervangen GitHub.

Dit is de huidige waarde van de URL: `https://author-p130360-e1272151.adobeaemcloud.com/bin/franklin.delivery/adobe-rnd/aem-boilerplate-xcom/main` .

Er zijn 3 delen van de URL die moeten worden bijgewerkt

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX moet worden vervangen door de URL van uw AEM CS Author-omgeving.

YYY zou door uw GitHub gebruikersrekening moeten worden vervangen.

ZZZ zou door de naam van de bewaarplaats moeten worden vervangen GitHub die u in de vorige oefening gebruikte.

U kunt URL van uw milieu van de Auteur van AEM CS vinden door [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"} te gaan. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Daarna, klik de 3 punten **..** op het **milieu&#39;s** lusje en klik **Details van de Mening**.

![ AEMCS ](./images/aemcs9.png)

U zult dan uw milieudetails, met inbegrip van URL van uw **milieu van de Auteur** zien. De URL kopiëren.

![ AEMCS ](./images/aemcs10.png)

XXX = `author-p166717-e1786231.adobeaemcloud.com`

Voor de naam van de GitHub-gebruikersaccount kunt u dat gemakkelijk vinden in de URL van uw browser. In dit voorbeeld is de naam van de gebruikersaccount `woutervangeluwe` .

YYY = `woutervangeluwe`

![ AEMCS ](./images/aemcs11.png)

Voor de bewaarplaatsnaam GitHub, kunt u het in het browser venster ook vinden dat u in GitHub hebt geopend. In dit geval is de naam van de gegevensopslagruimte `citisignal` .

ZZZ = `citisignal-aem-accs`

![ AEMCS ](./images/aemcs12.png)

Deze drie waarden samen leiden tot deze nieuwe URL die moet worden geconfigureerd in het bestand `fstab.yaml` .

`https://author-p166717-e1786231.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal-aem-accs/main`

U moet ook controleren of deze coderegels ook aan het bestand worden toegevoegd:

```
folders:
  /products/: /products/default
```

>[!IMPORTANT]
>
>Deze coderegels worden weergegeven op de lijnen 6 en 7 in de onderstaande afbeelding. Voeg de regels handmatig toe als deze regels ontbreken.

Klik **Veranderingen vastleggen...**.

![ AEMCS ](./images/aemcs13.png)

Klik **veranderingen** vastleggen.

![ AEMCS ](./images/aemcs14.png)

Het bestand `fstab.yaml` is nu bijgewerkt.

## 1.1.2.3 CitiSignal-middelen en -site uploaden

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png)

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png)

U ziet dan de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup20.png)

Uw URL ziet er als volgt uit: `https://author-p166717-e1786231.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

U moet nu tot het **milieu van de Manager van het Pakket van CRX** van AEM toegang hebben. U doet dit door `ui#/aem/aem/start.html?appId=aemshell` te verwijderen van de URL en deze te vervangen door `crx/packmgr` . Dit houdt in dat uw URL er nu als volgt moet uitzien:
`https://author-p166717-e1786231.adobeaemcloud.com/crx/packmgr` .
Het greep **gaat** binnen om het milieu van de pakketmanager te laden

![ AEMCS ](./images/aemcssetup22.png)

Daarna, klik **uploadt pakket**.

![ AEMCS ](./images/aemcssetup21.png)

Klik **doorbladeren** om van het te uploaden pakket de plaats te bepalen.

Het te uploaden pakket wordt genoemd **burgersignaal-assets.zip** en kan hier worden gedownload: [ https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal_aem_accs.zip ](https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal_aem_accs.zip){target="_blank"}.

![ AEMCS ](./images/aemcssetup23.png)

Selecteer het pakket `citisignal_aem_accs.zip` en klik **Open**.

![ AEMCS ](./images/aemcssetup24.png)

Daarna, klik O.K. ****.

![ AEMCS ](./images/aemcssetup25.png)

Het pakket wordt vervolgens geüpload. Daarna, klik **installeer** op het pakket u enkel uploadde.

![ AEMCS ](./images/aemcssetup27.png)

Klik **installeren**.

![ AEMCS ](./images/aemcssetup28.png)

Na een paar minuten wordt uw pakket geïnstalleerd.

![ AEMCS ](./images/aemcssetup29.png)

U kunt dit venster nu sluiten.

## 1.1.2.4 CitiSignal-elementen publiceren

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png)

Klik vervolgens op de URL van de omgeving van uw auteur.

![ AEMCS ](./images/aemcssetup18.png)

Klik **Teken binnen met Adobe**.

![ AEMCS ](./images/aemcssetup19.png)

U ziet dan de omgeving van uw auteur. Klik **Assets**.

![ AEMCS ](./images/aemcsassets1.png)

Klik **Dossiers**.

![ AEMCS ](./images/aemcsassets2.png)

Klik om de omslag **te selecteren CitiSignal** en dan **te klikken leidt Publicatie**.

![ AEMCS ](./images/aemcsassets3.png)

Klik **daarna**.

![ AEMCS ](./images/aemcsassets4.png)

Klik **publiceren**.

![ AEMCS ](./images/aemcsassets5.png)

Uw middelen zijn nu gepubliceerd.

## 1.1.2.5 CitiSignal-website publiceren

Klik de **productnaam van 0} Adobe Experience Manager {in de hoogste linkerhoek van uw scherm en klik dan de** pijl **naast** Assets **.**

![ AEMCS ](./images/aemcssetup30a.png)

Daarna, klik **Plaatsen**.

![ AEMCS ](./images/aemcssetup30.png)

U zou dan uw **CitiSignal** website moeten zien die na het installeren van het pakket alvorens werd gecreeerd.

![ AEMCS ](./images/aemcssetup31.png)

Om uw plaats aan de bewaarplaats te verbinden GitHub die u vóór creeerde, moet u een **Configuratie van Edge Delivery Services** tot stand brengen.

De eerste stap om dat te doen is de Configuratie van de a **Wolk** tot stand te brengen.

Om dat te doen, klik de **het productnaam van Adobe Experience Manager** in de hoogste linkerhoek van uw scherm, dan klik het **hulpmiddelen** pictogram en selecteer dan **Algemeen**. Klik om **Browser van de Configuratie te openen**.

![ AEMCS ](./images/aemcssetup31a.png)

Dan moet je dit zien. Klik **creëren**

![ AEMCS ](./images/aemcssetup31b.png)

Plaats de gebieden **Titel** en **Naam** aan `CitiSignal`. Laat checkbox voor **de Configuraties van de Wolk** toe.

Klik **creëren**.

![ AEMCS ](./images/aemcssetup31c.png)

Dan moet je dit hebben.

![ AEMCS ](./images/aemcssetup31d.png)

Daarna, moet u sommige gebieden van de **Configuratie van de Wolk** bijwerken u enkel creeerde.

Om dat te doen, klik de **productnaam van 0} Adobe Experience Manager {in de hoogste linkerhoek van uw scherm, dan klik het** hulpmiddelen **pictogram en selecteer dan** de Diensten van de Wolk **.** Klik om **Configuratie van Edge Delivery Services** te openen.

![ AEMCS ](./images/aemcssetup32.png)

Selecteer **CitiSignal**, klik **creeer** en selecteer **Configuratie**.

![ AEMCS ](./images/aemcssetup31e.png)

U moet nu de gebieden **Organisatie** en **Naam van de Plaats** invullen. Om dat te doen, heb eerst een blik door URL van uw bewaarplaats GitHub.

![ AEMCS ](./images/aemcssetup31f.png)

- **Organisatie**: gebruik de naam van uw naam van GitHub org, in dit voorbeeld is het `woutervangeluwe`
- **Naam van de Plaats**: gebruik de naam van de bewaarplaats GitHub, die `citisignal-aem-accs` zou moeten zijn.

Klik **sparen &amp; Sluiten**.

![ AEMCS ](./images/aemcssetup33.png)

Dan moet je dit hebben. Laat checkbox vóór uw nieuw creëren de Configuratie van de Wolk van Edge toe en klik **publiceren**.

![ AEMCS ](./images/aemcssetup34.png)

## 1.1.2.6 Bestandspaden.json bijwerken

Klik in uw GitHub-repo om het bestand `paths.json` te openen.

![ AEMCS ](./images/aemcssetupjson1.png)

Klik **uitgeven** pictogram.

![ AEMCS ](./images/aemcssetupjson2.png)

U moet nu de tekst vervangen `aem-boilerplate-commerce` door `CitiSignal` op de regels 3, 4, 5, 6, 7 en 10.

Klik **Veranderingen** vastleggen.

![ AEMCS ](./images/aemcssetupjson3.png)

Klik **Veranderingen** vastleggen.

![ AEMCS ](./images/aemcssetupjson4.png)

Het bestand `paths.json` is nu bijgewerkt.

## 1.1.2.7 CitiSignal-website publiceren

Klik de **productnaam van 0} Adobe Experience Manager {in de hoogste linkerhoek van uw scherm en selecteer dan** Plaatsen **.**

![ AEMCS ](./images/aemcssetup38.png)

Daarna, klik checkbox vóór **CitiSignal**. Dan, klik **leiden Publicatie**.

![ AEMCS ](./images/aemcssetup39.png)

Klik **daarna**.

![ AEMCS ](./images/aemcssetup40.png)

Klik **omvatten de Montages van Kinderen**.

![ AEMCS ](./images/aemcssetup41.png)

Klik om checkbox **te selecteren omvat kinderen** en klik dan om andere checkboxes te deselecteren. Klik **OK**.

![ AEMCS ](./images/aemcssetup42.png)

Klik **publiceren**.

![ AEMCS ](./images/aemcssetup43.png)

Je wordt hier teruggestuurd. Klik **CitiSignal**, selecteer checkbox voor **index** en klik dan **uitgeven**.

![ AEMCS ](./images/aemcssetup44.png)

Uw website zal dan in de **Universele Redacteur** openen.

![ AEMCS ](./images/aemcssetup45.png)

U kunt nu toegang krijgen tot uw website door naar `main--citisignal-aem-accs--XXX.aem.page` en/of `main--citisignal-aem-accs--XXX.aem.live` te gaan, nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, die in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` en/of `https://main--citisignal-aem-accs--woutervangeluwe.aem.live` .

Het kan enige tijd duren voordat alle activa correct zijn weergegeven, aangezien deze eerst moeten worden gepubliceerd.

U zult dan dit zien:

![ AEMCS ](./images/aemcssetup46.png)

## 1.1.2.8 Paginaprestaties testen

Ga naar [ https://pagespeed.web.dev/ ](https://pagespeed.web.dev/){target="_blank"}. Ga uw URL in en klik **analyseren**.

![ AEMCS ](./images/aemcssetup48.png)

Vervolgens ziet u dat uw website, zowel voor mobiele als voor desktoptoepassingen, een hoge score haalt:

**Mobiel**:

![ AEMCS ](./images/aemcssetup49.png)

**Desktop**:

![ AEMCS ](./images/aemcssetup50.png)

Volgende Stap: [ ontwikkelt een douaneblok ](./ex3.md){target="_blank"}

Ga terug naar [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./aemcs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

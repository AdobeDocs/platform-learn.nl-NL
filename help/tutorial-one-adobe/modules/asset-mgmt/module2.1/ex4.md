---
title: AEM CS - Aangepast basisblok
description: AEM CS - Aangepast basisblok
kt: 5342
doc-type: tutorial
exl-id: 57c08a88-d885-471b-ad78-1dba5992da9d
source-git-commit: 457e7d0dec233edf75717fb9930585a3511bdc65
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# 1.1.4 Een basisblok met aangepaste inhoud ontwikkelen

## 1.1.4.1 De lokale ontwikkelomgeving instellen

Ga naar [ https://desktop.github.com/download/ ](https://desktop.github.com/download/){target="_blank"}, download en installeer **Desktop van Github**.

![ Blok ](./images/block1.png){zoomable="yes"}

Zodra de Desktop van Github geïnstalleerd is, ga naar de reactie GitHub u in de vorige oefening creeerde. Klik **&lt;> Code** en klik dan **Open met Desktop GitHub**.

![ Blok ](./images/block2.png){zoomable="yes"}

Uw reactie GitHub zal dan in de Desktop worden geopend GitHub. Voel vrij om de **Lokale Weg** te veranderen. Klik **Kloon**.

![ Blok ](./images/block3.png){zoomable="yes"}

Er wordt nu een lokale map gemaakt.

![ Blok ](./images/block4.png){zoomable="yes"}

Open Visual Studio Code. Ga naar **Dossier** > **Open Omslag**.

![ Blok ](./images/block5.png){zoomable="yes"}

Selecteer de omslag die door uw opstelling GitHub voor **burgersignaal** wordt gebruikt.

![ Blok ](./images/block6.png){zoomable="yes"}

U zult nu die omslag open in de Code van Visual Studio zien, bent u nu bereid om een nieuw blok tot stand te brengen.

![ Blok ](./images/block7.png){zoomable="yes"}

## 1.1.4.2 Een aangepast basisblok maken

Adobe raadt u aan blokken te ontwikkelen in drie fasen:

- Maak de definitie en het model voor het blok, herzie het, en breng het aan productie.
- Maak inhoud met het nieuwe blok.
- Implementeer de decoratie en stijlen voor het nieuwe blok.

### component-definition.json

In de Code van Visual Studio, open het dossier **component-definition.json**.

![ Blok ](./images/block8.png){zoomable="yes"}

De rol neer tot u de component **Citaat** ziet. Plaats uw curseur naast de sluitende steun van de laatste component.

![ Blok ](./images/block9.png){zoomable="yes"}

Plak deze code en voer een komma **&#x200B;**&#x200B;na het codeblok in:

```json
{
  "title": "FiberOffer",
  "id": "fiberoffer",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "FiberOffer",
          "model": "fiberoffer",
          "offerText": "<p>Fiber will soon be available in your region!</p>",
          "offerCallToAction": "Get your offer now!",
          "offerImage": ""
        }
      }
    }
  }
}
```

Sla uw wijzigingen op.

![ Blok ](./images/block10.png){zoomable="yes"}

### component-models.json

In de Code van Visual Studio, open het dossier **component-models.json**.

![ Blok ](./images/block11.png){zoomable="yes"}

Schuif omlaag totdat u het laatste item ziet. Plaats uw curseur naast de sluitende steun van de laatste component.

![ Blok ](./images/block12.png){zoomable="yes"}

Voer een komma **&#x200B;**&#x200B;in en druk op Enter en op de volgende regel en plak deze code:

```json
{
  "id": "fiberoffer",
  "fields": [
     {
       "component": "richtext",
       "name": "offerText",
       "value": "",
       "label": "Offer Text",
       "valueType": "string"
     },
     {
       "component": "richtext",
       "valueType": "string",
       "name": "offerCallToAction",
       "label": "Offer CTA",
       "value": ""
     },
     {
       "component": "reference",
       "valueType": "string",
       "name": "offerImage",
       "label": "Offer Image",
        "multi": false
     }
   ]
}
```

Sla uw wijzigingen op.

![ Blok ](./images/block13.png){zoomable="yes"}

### component-filters.json

In de Code van Visual Studio, open het dossier **component-filters.json**.

![ Blok ](./images/block14.png){zoomable="yes"}

Onder **sectie**, ga een komma **in,** en identiteitskaart van uw component **fiberaanbieding** na de huidige laatste lijn.

Sla uw wijzigingen op.

![ Blok ](./images/block15.png){zoomable="yes"}

## 1.1.4.3 Uw wijzigingen vastleggen

U hebt nu verscheidene veranderingen in uw project aangebracht die terug naar uw bewaarplaats moeten worden geëngageerd GitHub. Om dat te doen, open **Desktop GitHub**.

U zou dan de 3 dossiers moeten zien die u enkel onder **Veranderingen** uitgeeft. Controleer uw wijzigingen.

![ Blok ](./images/block16.png){zoomable="yes"}

Voer een naam in voor uw PR, `Fiber Offer custom block` . Klik **Vastleggen aan hoofd**.

![ Blok ](./images/block17.png){zoomable="yes"}

Dan moet je dit zien. Klik **Push oorsprong**.

![ Blok ](./images/block18.png){zoomable="yes"}

Na een paar seconden, zijn uw veranderingen geduwd aan uw bewaarplaats GitHub.

![ Blok ](./images/block19.png){zoomable="yes"}

Ga in uw browser naar uw GitHub-account en naar de opslagplaats die u voor CitiSignal hebt gemaakt. Dan zou je iets dergelijks moeten zien, waaruit blijkt dat je wijzigingen zijn ontvangen.

![ Blok ](./images/block20.png){zoomable="yes"}

## 1.1.4.4 Voeg uw blok toe aan een pagina

Nu uw basis citaatblok wordt bepaald en aan het project CitiSignal geëngageerd, kunt u a **fiberbied** blok aan een bestaande pagina toevoegen.

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![ AEMCS ](./images/aemcs6.png){zoomable="yes"}

Daarna, klik de 3 punten **..** op het **milieu&#39;s** lusje en klik **Details van de Mening**.

![ AEMCS ](./images/aemcs9.png){zoomable="yes"}

Dan zie je de omgevingsdetails. Klik URL van uw **milieu van de Auteur**.

>[!NOTE]
>
>Het is mogelijk dat uw omgeving gehiberd is. Als dat het geval is, zult u uw milieu eerst moeten ontberen.

![ AEMCS ](./images/aemcs10.png){zoomable="yes"}

Je moet dan de AEM Author-omgeving zien. Ga naar **Plaatsen**.

![ AEMCS ](./images/block21.png){zoomable="yes"}

Ga naar **CitiSignal** > **gebruiken** > **en**.

![ AEMCS ](./images/block22.png){zoomable="yes"}

Klik **creëren** en selecteren **Pagina**.

![ AEMCS ](./images/block23.png){zoomable="yes"}

Selecteer **Pagina** en klik **daarna**.

![ AEMCS ](./images/block24.png){zoomable="yes"}

Voer de volgende waarden in:

- Titel: **CitiSignal Fiber**
- Naam: **burgerschap-vezel**
- De Titel van de pagina: **CitiSignal Vezel**

Klik **creëren**.

![ AEMCS ](./images/block25.png){zoomable="yes"}

Dan moet je dit zien.

![ AEMCS ](./images/block26.png){zoomable="yes"}

Klik op het lege gebied om de **sectie** component te selecteren. Klik vervolgens op de plusknop **+** in het rechtermenu.

![ AEMCS ](./images/block27.png){zoomable="yes"}

Vervolgens wordt het aangepaste blok weergegeven in de lijst met beschikbare blokken. Klik om het te selecteren.

![ AEMCS ](./images/block28.png){zoomable="yes"}

U zult dan gebieden als **Tekst van de Aanbieding** zien, **CTA van de Aanbieding** en **Beeld van de Aanbieding** wordt toegevoegd aan de redacteur. Klik **+ voeg** op het **gebied van het Beeld van de Aanbieding** toe om een beeld te selecteren.

![ AEMCS ](./images/block29.png){zoomable="yes"}

Dan moet je dit zien. Klik om de omslag **burgersignaal** te openen.

![ AEMCS ](./images/blockpub1.png){zoomable="yes"}

Selecteer het beeld **product-verrijking-1.png**. Klik **Uitgezocht**.

![ AEMCS ](./images/blockpub2.png){zoomable="yes"}

Dan moet je dit hebben. Klik **publiceren**.

![ AEMCS ](./images/blockpub3.png){zoomable="yes"}

Klik **publiceren** opnieuw.

![ AEMCS ](./images/blockpub4.png){zoomable="yes"}

Uw nieuwe pagina is nu gepubliceerd.

## 1.1.4.5 Nieuwe pagina toevoegen aan het navigatiemenu

In uw overzicht van AEM Sites, ga **CitiSignal** > **Fragments** en controleer checkbox voor **Kopbal**. Klik **uitgeven**.

![ AEMCS ](./images/nav0.png){zoomable="yes"}

Voeg met de tekst `Fiber` een menuoptie toe aan het navigatiemenu. Selecteer de tekst **Vezel** en klik het **verbindings** pictogram.

![ AEMCS ](./images/nav1.png){zoomable="yes"}

Ga dit voor **URL** in `/us/en//citisignal-fiber` en klik het **V** pictogram om te bevestigen.

![ AEMCS ](./images/nav3.png){zoomable="yes"}

Dan moet je dit hebben. Klik **publiceren**.

![ AEMCS ](./images/nav4.png){zoomable="yes"}

Klik **publiceren** opnieuw.

![ AEMCS ](./images/nav5.png){zoomable="yes"}

U kunt nu de wijzigingen in uw website bekijken door naar `main--citisignal--XXX.aem.page/us/en/` en/of `main--citisignal--XXX.aem.live/us/en/` te gaan, nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, die in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` en/of `https://main--citisignal--woutervangeluwe.aem.live/us/en/` .

Dan moet je dit zien. Klik **Vezel**.

![ AEMCS ](./images/nav6.png){zoomable="yes"}

Hier is uw standaard aangepaste blok, maar nu weergegeven op de website.

![ AEMCS ](./images/nav7.png){zoomable="yes"}

Volgende Stap: [ 1.1.5 Geavanceerd Blok van de Douane ](./ex5.md){target="_blank"}

Ga terug naar [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./aemcs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

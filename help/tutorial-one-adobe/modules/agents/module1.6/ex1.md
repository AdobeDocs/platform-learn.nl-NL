---
title: Aan de slag met AEM Agents
description: Aan de slag met AEM Agents
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
source-git-commit: d2b746d50ec559e0b29a7adb27c3521b0e00d386
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 0%

---

# 1.6.1 Aan de slag met AEM Agents

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een werkende AEM Sites en Assets CS met milieu EDS en de diverse agenten van AEM worden toegelaten voor IMS Org u gebruikt.
>
>Als u zulk een milieu nog niet hebt, ga [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Sites- en Assets CS-omgeving, kan het zijn dat uw AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.6.1.1 Discovery Agent

De Adobe Experience Manager (AEM) Discovery Agent is een door AI aangedreven tool in AEM as a Cloud Service waarmee gebruikers inhoud (waaronder Assets, Content Fragments en Adaptive Forms) kunnen zoeken, ophalen en gebruiken met behulp van natuurlijke taalaanwijzingen. Het elimineert de behoefte aan manueel, klik-zwaar, of complex filtreren door intent te begrijpen en over de bewaarplaats te zoeken.

Om **Agent van de Ontdekking te gebruiken**, zult u eerst sommige Markeringen in Adobe Experience Manager creëren, en u zult dan sommige activa etiketteren gebruikend die markeringen. Zodra dat wordt gedaan, zult u AI Medewerker kunnen gebruiken om activa op een gemakkelijke en bedrijfsvriendelijke manier te ontdekken.

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`.

### Tags maken en gebruiken met Assets

Klik hierop om het Cloud Manager-programma te openen. Dit wordt `--aepUserLdap-- - CitiSignal AEM+ACCS` genoemd.

![ de Agenten van AEM ](./images/aemagents1.png)

Klik op de URL van de omgeving om deze te openen.

![ de Agenten van AEM ](./images/aemagents2.png)

Klik het **hammer** pictogram.

![ de Agenten van AEM ](./images/aemagents3.png)

Onder **Algemeen**, klik **Tags**.

![ de Agenten van AEM ](./images/aemagents4.png)

Dan moet je dit zien. Klik **creëren** en selecteer dan **Namespace** creëren.

![ de Agenten van AEM ](./images/aemagents5.png)

Op het gebied **Titel**, ga binnen: `CitiSignal`. Klik **creëren**.

![ de Agenten van AEM ](./images/aemagents6.png)

Boor neer in namespace **CitiSignal** door het te klikken. Klik **creeer** en selecteer dan **creeer Markering**.

![ de Agenten van AEM ](./images/aemagents7.png)

Op het gebied **Titel**, ga binnen: `Campaign`. Klik **voorleggen**.

![ de Agenten van AEM ](./images/aemagents8.png)

Selecteer de markering **Campagne** door het te klikken. Klik **creeer** en selecteer dan **creeer Markering**.

![ de Agenten van AEM ](./images/aemagents9.png)

Op het gebied **Titel**, ga binnen: `Winter 2026`. Klik **voorleggen**.

![ de Agenten van AEM ](./images/aemagents10.png)

Selecteer de markering **Campagne** door het te klikken. Klik **creeer** en selecteer dan **creeer Markering**.

![ de Agenten van AEM ](./images/aemagents11.png)

Op het gebied **Titel**, ga binnen: `Spring 2026`. Klik **voorleggen**.

![ de Agenten van AEM ](./images/aemagents12.png)

Dat zou u nu moeten doen.

![ de Agenten van AEM ](./images/aemagents13.png)

Klik **Adobe Experience Manager** en klik dan **Assets**.

![ de Agenten van AEM ](./images/aemagents14.png)

Klik **Dossiers**.

![ de Agenten van AEM ](./images/aemagents15.png)

Dubbelklik de omslag **CitiSignal** om het te openen.

![ de Agenten van AEM ](./images/aemagents16.png)

Klik **creëren** en selecteer dan **Dossiers**.

![ de Agenten van AEM ](./images/aemagents17.png)

Download het dossier [ burgersignaal-beelden-campagne.zip ](./assets/citisignal-images-campaign.zip) en unzip het op uw Desktop.

![ de Agenten van AEM ](./images/aemagents17a.png)

Selecteren. de 3 dossiers die u enkel downloadde en **open** klikt.

![ de Agenten van AEM ](./images/aemagents18.png)

Klik **uploaden**.

![ de Agenten van AEM ](./images/aemagents19.png)

Dan moet je dit zien.

![ de Agenten van AEM ](./images/aemagents20.png)

Selecteer het eerste beeld en klik dan **Eigenschappen**.

![ de Agenten van AEM ](./images/aemagents21.png)

Klik het **omslag** - pictogram onder Markeringen.

![ de Agenten van AEM ](./images/aemagents22.png)

Selecteer de markering **Lente 2026** en klik **Uitgezocht**. Herhaal dat proces voor deze afbeeldingen:

- burgerschap_lion.png
- burgersignaal_leopard.png
- burgersignaal_gorilla.png
- burgersignaal_konijn.png

![ de Agenten van AEM ](./images/aemagents23.png)

Zodra u die markering voor alle beelden hebt geselecteerd, ga naar **Experience Manager Assets**.

![ de Agenten van AEM ](./images/aemagents24.png)

Selecteer de reactie die u gebruikt.

![ de Agenten van AEM ](./images/aemagents25.png)

Ga naar **Assets** en open de omslag **CitiSignal**.

![ de Agenten van AEM ](./images/aemagents26.png)

Open de eerste afbeelding.

![ de Agenten van AEM ](./images/aemagents27.png)

Selecteer **Goedgekeurd** en klik dan **sparen**.

![ de Agenten van AEM ](./images/aemagents28.png)

Onder **Markeringen**, kunt u de markering zien die u eerder selecteerde.

![ de Agenten van AEM ](./images/aemagents29.png)

Herhaal dat proces zodat alle vier de beelden worden goedgekeurd.

![ de Agenten van AEM ](./images/aemagents30.png)

Daarna, ga naar **Mijn werkruimte** en klik om **Medewerker AI** te openen.

![ de Agenten van AEM ](./images/aemagents31.png)

Ga de volgende herinnering in en klik **verzenden**.

```javascript
find all assets tagged with 'Spring 2026'
```

![ de Agenten van AEM ](./images/aemagents32.png)

Als u toegang hebt tot meerdere AEM Assets CS-omgevingen, ziet u zoiets. Klik het voorgestelde antwoord voor het milieu u wenst te gebruiken en dan **te klikken verzend**.

![ de Agenten van AEM ](./images/aemagents34.png)

Dan zou je een vergelijkbaar antwoord moeten zien. Klik op het pictogram om de AI-assistent uit te breiden naar het volledige scherm.

![ de Agenten van AEM ](./images/aemagents35.png)

Bekijk de antwoorden.

![ de Agenten van AEM ](./images/aemagents36.png)

Vanuit het venster AI Assistant kunt u op deze elementen klikken om ze weer te geven.

![ de Agenten van AEM ](./images/aemagents37.png)

Vervolgens wordt u rechtstreeks naar AEM Assets CS geleid, naar die specifieke afbeelding.

![ de Agenten van AEM ](./images/aemagents38.png)

U kunt dan ook alle andere beschikbare metagegevens controleren.

![ de Agenten van AEM ](./images/aemagents39.png)

## 1.6.1.2 Experience Production Agent

### Update van inhoud - Assets

De vaardigheden van de Update van de Inhoud werken bestaande inhoud — met inbegrip van inhoudsfragmenten, pagina&#39;s, vormen en activa bij - met gemak bij. De agent kan acties uitvoeren zoals het bijwerken, verwijderen, vervangen of toevoegen van inhoudselementen om ervaringen nauwkeurig en actueel te houden. Invoer kan een natuurlijke taalbeschrijving zijn en bij Jira PDF&#39;s en screenshots kan ook invoer worden geleverd.

Ga terug naar het scherm AI Assistant.

![ de Agenten van AEM ](./images/aemagents40.png)

Ga de volgende herinnering in en klik **verzenden**.

`Generate multiple social media formats (Instagram 1080x1920, Facebook 1200x630, Twitter 1200x675) for the third image`

![ de Agenten van AEM ](./images/aemagents40a.png)

Na een paar minuten moet u een vergelijkbare reactie zien.

![ de Agenten van AEM ](./images/aemagents41.png)

Bekijk de gegenereerde afbeeldingen.

![ de Agenten van AEM ](./images/aemagents42.png)

### Inhoud bijwerken - Pagina&#39;s

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager en ga dan naar **Plaatsen**.

![ de Agenten van AEM ](./images/aemagents43.png)

Ga naar **CitiSignal**. Klik **creëren** en selecteren **Pagina**.

![ de Agenten van AEM ](./images/aemagents44.png)

Selecteer **Pagina** en klik **daarna**.

![ de Agenten van AEM ](./images/aemagents45.png)

Voer de volgende waarden in:

- Titel: **Max van Vezel**
- Naam: **vezel-maximum**
- De Titel van de pagina: **Max van Vezel**

Klik **creëren**.

![ de Agenten van AEM ](./images/aemagents46.png)

Selecteer **Open**.

![ de Agenten van AEM ](./images/aemagents47.png)

Dan moet je dit zien.

![ de Agenten van AEM ](./images/aemagents48.png)

Klik op het lege gebied om de **sectie** component te selecteren. Dan, klik plus **+** pictogram in het juiste menu en selecteer **Hero**.

![ de Agenten van AEM ](./images/aemagents49.png)

Dan moet je dit zien. Klik op **+ Toevoegen** om een afbeelding toe te voegen.

![ de Agenten van AEM ](./images/aemagents50.png)

Selecteer de opslagplaats voor uw middelen. Dan, open de omslag **CitiSignal**.

![ de Agenten van AEM ](./images/aemagents51.png)

Kies de afbeelding van de leeuw die u eerder uploadde. Klik **Uitgezocht**.

![ de Agenten van AEM ](./images/aemagents52.png)

Dan moet je dit zien. Klik het **tekst** gebied om de tekst te veranderen.

![ de Agenten van AEM ](./images/aemagents53.png)

Plak deze tekst in de are:

```
This winter, be as fast as a lion.
```

Selecteer **Kop 1** en klik dan **Gedaan**.

![ de Agenten van AEM ](./images/aemagents54.png)

Dan moet je dit zien. Ga naar **de boom van de Inhoud** en selecteer het gebied **Sectie**.

![ de Agenten van AEM ](./images/aemagents55.png)

Klik **+** pictogram en selecteer dan **Kaarten**.

![ de Agenten van AEM ](./images/aemagents56.png)

Dan moet je dit zien. Zorg ervoor dat in de **boom van de Inhoud**, **Kaarten** wordt geselecteerd.

Klik vervolgens viermaal op de knop **+** .

![ de Agenten van AEM ](./images/aemagents57.png)

U zou dit nu moeten zien, waar er 4 **Kaart** voorwerpen in het **Kaarten** voorwerp zijn.

![ de Agenten van AEM ](./images/aemagents58.png)

Selecteer de eerste **Kaart**. Klik het **tekst** gebied om de tekst te veranderen.

![ de Agenten van AEM ](./images/aemagents59.png)

Plak de volgende tekst. Zorg ervoor de eerste lijn van tekst **Kop 1** gebruikt. Klik **Gedaan**.

```
99.9% network reliability

Game, video chat and stream on multiple devices with ultra low lag.
```

![ de Agenten van AEM ](./images/aemagents60.png)

Selecteer de tweede **Kaart**. Klik het **tekst** gebied om de tekst te veranderen.

![ de Agenten van AEM ](./images/aemagents61.png)

Plak de volgende tekst. Zorg ervoor de eerste lijn van tekst **Kop 1** gebruikt. Klik **Gedaan**.

```
3-year

price lock guarantee

For new and existing Fiber Max customers on all internet plans.

No hidden fees.
```

![ de Agenten van AEM ](./images/aemagents62.png)

Selecteer de derde **Kaart**. Klik het **tekst** gebied om de tekst te veranderen.

![ de Agenten van AEM ](./images/aemagents63.png)

Plak de volgende tekst. Zorg ervoor de eerste lijn van tekst **Kop 1** gebruikt. Klik **Gedaan**.

```
More ways to save

Save over 45% on the best entertainment with CitiSignal
```

![ de Agenten van AEM ](./images/aemagents64.png)

Selecteer de vierde **Kaart**. Klik het **tekst** gebied om de tekst te veranderen.

![ de Agenten van AEM ](./images/aemagents65.png)

Plak de volgende tekst. Zorg ervoor de eerste lijn van tekst **Kop 1** gebruikt. Klik **Gedaan**.

```
Get Fiber Max now!

Fill out the form here to get started.
```

![ de Agenten van AEM ](./images/aemagents66.png)

Dat zou u nu moeten doen. Klik **publiceren**.

![ de Agenten van AEM ](./images/aemagents67.png)

Klik **publiceren** opnieuw.

![ de Agenten van AEM ](./images/aemagents68.png)

Klik **Open Pagina**.

![ de Agenten van AEM ](./images/aemagents69.png)

Kopieer de URL van de pagina naar wens.

De URL moet er ongeveer als volgt uitzien: `https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/content/CitiSignal/fiber-max.html` .

![ de Agenten van AEM ](./images/aemagents70.png)

Ga naar [ https://experience.adobe.com/#/experiencemanager/ ](https://experience.adobe.com/#/experiencemanager/). Klik om **Medewerker AI** te openen.

![ de Agenten van AEM ](./images/aemagents71.png)

Plak de volgende herinnering en klik **verzenden**. Vervang XXX in deze vraag door URL die u in de vorige stap kopieerde.

```
On the page XXX, please make the following changes:

- change the word 'winter' to 'spring'
- change the word 'lion' to 'leopard'
- change the image in the hero block to use the image 'citisignal_leopard.png'
- change the text '99.9% network reliability' to '99.999% network reliability'
```

![ de Agenten van AEM ](./images/aemagents72.png)

Na 1-2 minuten moet u dit zien. Ga de herinnering `generate` in en klik **verzenden**.

![ de Agenten van AEM ](./images/aemagents74.png)

Een paar minuten later ziet u een bevestiging als deze dat de wijzigingen zijn uitgevoerd. Klik **Voorproef de bijgewerkte pagina**.

![ de Agenten van AEM ](./images/aemagents75.png)

U krijgt nu een visuele bevestiging van de veranderingen die zijn gedaan. Deze voorvertoningspagina is louter ter informatie. U kunt geen actie ondernemen vanaf deze pagina.

![ de Agenten van AEM ](./images/aemagents76.png)

Om actie te voeren, klik **uitgeven in AEM**.

![ de Agenten van AEM ](./images/aemagents75a.png)

In de Universele Redacteur, ziet u nu alle veranderingen in detail, met de capaciteit om het even wat veranderen. Zodra u de pagina hebt herzien, klik **publiceren**.

![ de Agenten van AEM ](./images/aemagents77.png)

Klik **publiceren** opnieuw. De wijziging die u hebt aangebracht, wordt nog niet gepubliceerd in uw productieomgeving. In plaats daarvan, is het gepubliceerd onder **Lanceringen** in AEM.

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Er wordt een Starten gemaakt waarmee u wijzigingen kunt aanbrengen in de voorbereidingen voor toekomstige publicatie, terwijl uw huidige pagina&#39;s behouden blijven. Dit betekent dat u in feite twee versies tegelijk bewerkt: pagina&#39;s die momenteel worden gepubliceerd en een versie van deze pagina&#39;s die in de toekomst tegelijk worden gepubliceerd. Zodra dat tijdstip is bereikt, kunt u de originele pagina&#39;s vervangen en de nieuwe versie publiceren.

![ de Agenten van AEM ](./images/aemagents78.png)

Om **te bevorderen** uw hangende veranderingen voor een toekomstige versie, ga terug naar AEM. Klik **Adobe Experience Manager** bij de bovenkant van de pagina, klik het **hammer** pictogram en selecteer dan **Lanceringen**.

![ de Agenten van AEM ](./images/aemagents79.png)

U zou een hangende **Lancering** nu moeten zien. Controleer checkbox vóór hangende **Lancering**.

![ de Agenten van AEM ](./images/aemagents80.png)

Klik **bevorderen**.

![ de Agenten van AEM ](./images/aemagents81.png)

Selecteer **bevorderen volledige lancering** en klik **daarna**.

![ de Agenten van AEM ](./images/aemagents82.png)

Klik **bevorderen**.

![ de Agenten van AEM ](./images/aemagents83.png)

U moet dit nu zien. Uw wijzigingen zijn nu in productie.

![ de Agenten van AEM ](./images/aemagents84.png)

Vernieuw de pagina. Alle wijzigingen op de gepubliceerde pagina worden nu weergegeven.

![ de Agenten van AEM ](./images/aemagents85.png)

U kunt ook de vraag `accept` in AI Assistant invoeren in plaats van het handmatige promotieproces te doorlopen.

![ de Agenten van AEM ](./images/aemagents86.png)

U zou dan een bevestiging moeten krijgen dat de veranderingen worden gepubliceerd.

![ de Agenten van AEM ](./images/aemagents87.png)

### Inhoud bijwerken - Formulier maken

In module [ Adobe Experience Manager Forms met Edge Delivery Services ](./../../asset-mgmt/module1.3/aemforms.md){target="_blank"} kunt u de stappen vinden betrokken bij verwezenlijking een vorm op een handmatige manier.

Met de vaardigheden voor het maken van formulieren kunnen gebruikers nu adaptieve formulieren maken via natuurlijke taalaanwijzingen zonder afhankelijk te zijn van ontwikkelings- of IT-teams. Deze mogelijkheid versnelt de ontwikkeling van formulieren met behoud van de consistentie van merken en stelt zakelijke gebruikers in staat formulieren te maken zonder diepgaande technische productkennis.

Ga naar [ https://experience.adobe.com/#/ai-assistant/chat ](https://experience.adobe.com/#/ai-assistant/chat).

![ de Agenten van AEM ](./images/aemagentsforms1.png)

Ga de volgende herinnering in en klik **verzenden**.

```
Create a new adaptive form using Edge Delivery Services and the existing CitiSignal site, with the following details:
- Form name: "citisignal-fiber-max-interest-2"
- Form fields: 4 text input fields are needed, for "first-name", "last-name", "email" and "city"
- When the form is submitted, send the submission to a spreadsheet, with this URL: https://docs.google.com/spreadsheets/d/1WwKrcM8mZ2d_W3sMheUAw3nFhP_OFk05TsqxhHkudfQ/edit?usp=sharing.
```

## Volgende stappen

Ga naar [ 1.6.2 de Servers &amp; Cursor van AEM MCP ](./ex2.md){target="_blank"}

Ga terug naar [ AEM &amp; Agenten ](./aemagents.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

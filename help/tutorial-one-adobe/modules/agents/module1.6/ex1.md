---
title: Content Production Agent
description: Content Production Agent
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
source-git-commit: 7ea3bdc9557ea9e88ddd9693f9ffbfbc634857f8
workflow-type: tm+mt
source-wordcount: '859'
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

### Inhoud bijwerken

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

### Formulier maken

Met de vaardigheden voor het maken van formulieren kunnen gebruikers adaptieve formulieren maken via natuurlijke taalaanwijzingen zonder afhankelijk te zijn van ontwikkelings- of IT-teams. Deze mogelijkheid versnelt de ontwikkeling van formulieren met behoud van de consistentie van merken en stelt zakelijke gebruikers in staat formulieren te maken zonder diepgaande technische productkennis.


## Volgende stappen

Ga terug naar [ AEM &amp; Agenten ](./aemagents.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

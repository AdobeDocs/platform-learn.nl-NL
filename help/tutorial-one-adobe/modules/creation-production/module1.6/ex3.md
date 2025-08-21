---
title: Uw externe DAM-app maken
description: Uw externe DAM-app maken
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 6823e8a0-dde7-460a-a48a-6787e65e4104
source-git-commit: 1f9a868c5e4ef4aa0e09d7f5d73a951006ee6c5a
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---

# 1.6.3 Een externe DAM-app maken en implementeren

## 1.6.3.1 Download voorbeeldbestanden voor de app

Ga naar [ https://github.com/woutervangeluwe/genstudio-external-dam-app ](https://github.com/woutervangeluwe/genstudio-external-dam-app). Klik **Code** en selecteer dan **ZIP van de Download**.

![ Ext DAM ](./images/extdam1.png)

Pak het ZIP-bestand uit op uw bureaublad.

![ Ext DAM ](./images/extdam2.png)

## 1.6.3.2 De Adobe Developer-opdrachtregelinterface configureren

Klik met de rechtermuisknop op de **genstudio-extern-dam-app-main** omslag en selecteer **Nieuwe Terminal bij Omslag**.

![ Ext DAM ](./images/extdam5.png)

Dan moet je dit zien. Voer de opdracht `aio login` in. Deze opdracht wordt omgeleid naar uw browser en u wordt verwacht dat u zich aanmeldt.

![ Ext DAM ](./images/extdam6.png)

Na succesvolle login, zou u dit in browser moeten zien.

![ Ext DAM ](./images/extdam7.png)

De browser zal dan naar het eindvenster opnieuw richten. U zou een bericht moeten zien dat **succesvolle Login** en een lang teken zegt dat door browser is teruggekeerd.

![ Ext DAM ](./images/extdam8.png)

De volgende stap bestaat uit het configureren van de instantie en het Adobe IO-project dat u wilt gebruiken voor de externe DAM-app.

Hiervoor moet u een bestand downloaden van het Adobe IO-project dat u eerder hebt geconfigureerd.

Ga naar [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home){target="_blank"} en open het project u eerder creeerde, dat `--aepUserLdap-- GSPeM EXT` wordt genoemd. Open de **Werkruimte van de Productie**.

![ Ext DAM ](./images/extdam9.png)

Klik **Download allen**. Hiermee wordt een JSON-bestand gedownload.

![ Ext DAM ](./images/extdam10.png)

Kopieer het JSON- dossier van uw **Downloads** folder in de wortelfolder van externe DAM app.

![ Ext DAM ](./images/extdam11.png)

Ga terug naar uw eindvenster. Voer de opdracht `aio app use XXX-YYY-Production.json` in.

>[!NOTE]
>
>U moet de naam van het bestand in de bovenstaande opdracht wijzigen, zodat deze overeenkomt met de naam van het bestand.

Nadat de opdracht is uitgevoerd, wordt uw externe DAM-toepassing nu verbonden met het eerder gemaakte Adobe IO-project met App Builder.

![ Ext DAM ](./images/extdam12.png)

## 1.6.3.3 Installeer de GenStudio Extenability SDK

Daarna, moet u **SDK van de Uitbreidbaarheid van GenStudio** installeren. U kunt meer details over SDK hier vinden: [ https://github.com/adobe/genstudio-extensibility-sdk ](https://github.com/adobe/genstudio-extensibility-sdk).

Als u de SDK wilt installeren, voert u deze opdracht uit in uw terminalvenster:

`npm install @adobe/genstudio-extensibility-sdk`

![ Ext DAM ](./images/extdam13.png)

Na een paar minuten wordt de SDK geïnstalleerd.

![ Ext DAM ](./images/extdam14.png)

## 1.6.3.4 Controleer de externe DAM-toepassing in Visual Studio Code

Open Visual Studio Code. Klik **Open...** om een omslag te openen.

![ Ext DAM ](./images/extdam15.png)

Selecteer de omslag **genstudio-extern-dam-app-main** die app bevat u vóór downloadde. Klik **Open**.

![ Ext DAM ](./images/extdam16.png)

Klik om het bestand **.env** te openen.

![ Ext DAM ](./images/extdam17.png)

Het bestand **.env** is gemaakt met de opdracht `aio app use` die u in de vorige stap hebt uitgevoerd en bevat de informatie die nodig is om verbinding te maken met uw Adobe IO-project met App Builder.

![ Ext DAM ](./images/extdam18.png)

U moet nu de volgende details toevoegen aan het bestand **.env** , zodat de externe DAM-toepassing verbinding kan maken met de eerder gemaakte AWS S3-emmertje.

```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=
AWS_BUCKET_NAME=
```

Het veld **`AWS_ACCESS_KEY_ID`** en **`AWS_SECRET_ACCESS_KEY`** waren beschikbaar nadat de IAM-gebruiker in de vorige exercitie was gemaakt. U werd gevraagd om hen neer te schrijven, kunt u nu de waarden kopiëren.

![ ETL ](./images/cred1.png)

Het veld **`AWS_REGION`** kan naast de naam van het emmertje uit de weergave AWS S3 Home worden genomen. In dit voorbeeld, is het gebied **us-west-2**.

![ ETL ](./images/bucket2.png)

Het veld **`AWS_BUCKET_NAME`** moet `--aepUserLdap---gspem-dam` zijn.

Met deze informatie kunt u de waarden van elk van deze variabelen bijwerken.

```
AWS_ACCESS_KEY_ID=XXX
AWS_SECRET_ACCESS_KEY=YYY
AWS_REGION=us-west-2
AWS_BUCKET_NAME=--aepUserLdap---gspem-dam
```

U moet deze tekst nu in beide bestanden plakken, `.env.dev` en `.env.prod` . Vergeet niet uw wijzigingen op te slaan.

![ Ext DAM ](./images/extdam21.png)

Ga vervolgens terug naar uw terminalvenster. Voer deze opdracht uit:

`export $(grep -v '^#' .env | xargs)`

![ Ext DAM ](./images/extdam23.png)

Ten slotte moet u het label wijzigen dat in GenStudio for Performance Marketing wordt weergegeven, zodat u uw externe DAM-toepassing kunt onderscheiden van andere integraties. Om dat te doen, open het dossier **Constants.ts** dat u kunt vinden door neer in ontdekkingsreiziger te boren aan **src/genstudiopem > web-src > src**.

Regel 14 moet worden gewijzigd in

`export const extensionLabel: string = "--aepUserLdap-- - External S3 DAM";`

Vergeet niet uw wijzigingen op te slaan.

![ Ext DAM ](./images/extdam22.png)

## 1.6.3.5 De externe DAM-app uitvoeren

Voer de opdracht `aio app run` uit in uw terminalvenster. U moet dit na 1-2 minuten zien.

![ Ext DAM ](./images/extdam24.png)

U hebt nu bevestigd dat uw app wordt uitgevoerd. De volgende stap is het opstellen.

Eerst, duw **CTRL+C** om app tegen het lopen te houden. Voer vervolgens de opdracht `aio app deploy` in. Met deze opdracht wordt uw code geïmplementeerd op Adobe IO.

Dientengevolge, zult u een gelijkaardige URL ontvangen om tot uw opgestelde toepassing toegang te hebben:

`https://133309-201burgundyguan.adobeio-static.net/index.html`

![ Ext DAM ](./images/extdam27.png)

Voor testdoeleinden kunt u die URL nu gebruiken als parameter voor een querytekenreeks door `?ext=` als voorvoegsel toe te voegen aan de bovenstaande URL. Dit resulteert in deze parameter van het vraagkoord:

`?ext=https://133309-201burgundyguan.adobeio-static.net/index.html`

Ga naar [ https://experience.adobe.com/genstudio/create ](https://experience.adobe.com/genstudio/create).

![ Ext DAM ](./images/extdam25.png)

Voeg vervolgens de parameter voor de querytekenreeks toe vlak voor **#** . Uw nieuwe URL moet er als volgt uitzien:

`https://experience.adobe.com/?ext=https://133309-201burgundyguan.adobeio-static.net/index.html#/@experienceplatform/genstudio/create`

De pagina wordt normaal geladen. Klik **Banners** beginnen een nieuwe banner te creëren.

![ Ext DAM ](./images/extdam26.png)

Selecteer een malplaatje en klik **Gebruik**.

![ Ext DAM ](./images/extdam28.png)

Klik **Uitgezocht van inhoud**.

![ Ext DAM ](./images/extdam29.png)

Vervolgens kunt u de externe DAM selecteren. Deze krijgt de naam `--aepUserLdap-- - External S3 DAM` uit de vervolgkeuzelijst.

![ Ext DAM ](./images/extdam30.png)

Dan moet je dit zien. Selecteer het beeld **neon_rabbit_banner.jpg** en klik **Gebruik**.

![ Ext DAM ](./images/extdam31.png)

U hebt nu een afbeelding uit uw externe DAM geselecteerd die in een S3-emmertje wordt uitgevoerd. Als de afbeelding is geselecteerd, kunt u nu de normale workflow volgen die wordt beschreven in [1.3.3.4 Meta-advertentie maken en goedkeuren ](./../module1.3/ex3.md#create--approve-meta-ad) .

![ Ext DAM ](./images/extdam32.png)

Wanneer u wijzigingen aanbrengt in de code op uw lokale computer, moet u uw app opnieuw implementeren. Wanneer u herstelt, gebruik dit eindbevel:

`aio app deploy --force-build --force-deploy`

![ Ext DAM ](./images/extdam33.png)

Uw app is nu klaar om te worden gepubliceerd.

## Volgende stappen

Ga naar [ publiceer uw app privé ](./ex4.md){target="_blank"}

Ga terug naar [ GenStudio for Performance Marketing - Uitbreidbaarheid ](./genstudioext.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

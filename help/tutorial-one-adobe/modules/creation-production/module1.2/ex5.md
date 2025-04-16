---
title: Frame I/O en Workfront Fusion
description: Frame I/O en Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 37de6ceb-833e-4e75-9201-88bddd38a817
source-git-commit: 7d4970479ff1a7dcb3ebb1f46660f418ba768da3
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# 1.2.5 Frame I/O en Workfront Fusion

In de vorige oefening vormde u het scenario `--aepUserLdap-- - Firefly + Photoshop` en vormde een inkomende webhaak om het scenario, en een webhaakreactie teweeg te brengen wanneer het scenario met succes voltooide. Vervolgens hebt u Postman gebruikt om dat scenario te activeren. Postman is een groot hulpmiddel voor het testen, maar in een echt bedrijfsscenario, zouden de bedrijfsgebruikers Postman niet gebruiken om een scenario teweeg te brengen. In plaats daarvan zouden ze een andere toepassing gebruiken en verwachten ze dat andere toepassing een scenario in Workfront Fusion activeert. In deze oefening, is dat precies wat u met Kader I/O zult doen.

## 1.2.5.1 Toegang tot frame I/O

>[!NOTE]
>
>Om deze oefening met succes te voltooien, moet u een gebruiker Admin in uw Kader I/O rekening zijn. De onderstaande exercitie is gemaakt voor frame I/O V3 en zal in een later stadium worden bijgewerkt voor frame I/O V4.

Ga naar [ https://app.frame.io/projects ](https://app.frame.io/projects).

Klik het **+ pictogram** om uw eigen project in Kader I/O tot stand te brengen.

![ Kader IO ](./images/frame1.png)

Ga de naam `--aepUserLdap--` in en klik **creeer Project**.

![ Kader IO ](./images/frame2.png)

U zult dan uw project in het linkermenu zien.
In één van de vorige oefeningen, downloadde u [ burgersignaal-fiber.psd ](./../../../assets/ff/citisignal-fiber.psd){target="_blank"} aan uw Desktop. Selecteer dat bestand en sleep het naar de net gemaakte projectmap.

![ Kader IO ](./images/frame3.png)

## 1.2.5.2 Workfront Fusion en frame I/O

In de vorige oefening, creeerde u het scenario `--aepUserLdap-- - Firefly + Photoshop`, dat met een douane webhaak begon en dat met een webshreactie beëindigde. Het gebruik van de webhaken werd vervolgens getest met Postman, maar het is duidelijk dat het punt van een dergelijk scenario moet worden genoemd door een externe toepassing. Zoals eerder vermeld, zal Frame I/O die oefening zijn, maar tussen Frame I/O en `--aepUserLdap-- - Firefly + Photoshop` is een ander Workfront Fusion-scenario nodig. u zult nu dat scenario vormen.

In het linkermenu, ga naar **Scenario&#39;s** en selecteer uw omslag `--aepUserLdap--`. Klik **creeer een nieuw scenario**.

![ Kader IO ](./images/frame4.png)

Gebruik de naam `--aepUserLdap-- - Frame IO Custom Action` .

![ Kader IO ](./images/frame5.png)

Klik het **voorwerp van het vraagteken** op het canvas. Ga de tekst `webhook` in het onderzoeksvakje in en klik **Webhooks**.

![ Kader IO ](./images/frame6.png)

Klik **WebHaak van de Douane**.

![ Kader IO ](./images/frame7.png)

Klik **toevoegen** om een nieuwe webhaakURL tot stand te brengen.

![ Kader IO ](./images/frame8.png)

Voor de **naam van Webhaak**, gebruik `--aepUserLdap-- - Frame IO Custom Action Webhook`. Klik **sparen**.

![ Kader IO ](./images/frame9.png)

Dan moet je dit zien. Laat dit scherm open en onaangeroerd zoals u het in een volgende stap nodig hebt. U zult WebHaak URL in een volgende stap moeten kopiëren, door **adres van het Exemplaar aan klembord** te klikken.

![ Kader IO ](./images/frame10.png)

Ga naar [ https://developer.frame.io/ ](https://developer.frame.io/). Klik **TOOLS VAN DE ONTWIKKELAAR** en kies dan **de Acties van de Douane**.

![ Kader IO ](./images/frame11.png)

Klik **creeer een Actie van de Douane**.

![ Kader IO ](./images/frame12.png)

Voer de volgende waarden in:

- **NAAM**: gebruik `vangeluw - Frame IO Custom Action Fusion`
- **BESCHRIJVING**: gebruik `vangeluw - Frame IO Custom Action Fusion`
- **GEBEURTENIS**: gebruik `fusion.tutorial`.
- **URL**: ga URL van de webhaak in die u enkel in de Fusie van Workfront creeerde
- **TEAM**: selecteer het aangewezen Kader I/O team, in dit geval, **Één Leerprogramma van Adobe**.

Klik **voorleggen**.

![ Kader IO ](./images/frame15.png)

Dan moet je dit zien.

![ Kader IO ](./images/frame14.png)

Ga terug naar [ https://app.frame.io/projects ](https://app.frame.io/projects). Vernieuw de pagina.

![ Kader IO ](./images/frame16.png)

Na het hebben van de pagina verfrist, klik de 3 punten **...** op de activa **burgersignaal-fiber.psd**. De aangepaste handeling die u eerder hebt gemaakt, wordt dan weergegeven in het menu dat wordt weergegeven. Klik op de aangepaste handeling `vangeluw - Frame IO Custom Action Fusion` .

![ Kader IO ](./images/frame17.png)

U zou dan een gelijkaardig **Succes moeten zien!** popup. Deze pop-up is het resultaat van de communicatie tussen Frame I/O en Workfront Fusion.

![ Kader IO ](./images/frame18.png)

Zet het scherm terug op Workfront Fusion. U zou nu **met succes moeten zien bepaalde** verschijnen op het voorwerp van de Verbinding van de Douane WebHaak. Klik **OK**.

![ Kader IO ](./images/frame19.png)

Klik **Looppas eens** om testwijze toe te laten, en de mededeling met Kader I/O opnieuw te testen.

![ Kader IO ](./images/frame20.png)

Ga terug naar frame I/O en klik nogmaals op de aangepaste handeling `vangeluw - Frame IO Custom Action Fusion` .

![ Kader IO ](./images/frame21.png)

Schakel het scherm weer in op Workfront Fusion. U zou nu een groen controleteken, en een bel moeten zien die **1** tonen. Klik op de ballon om de details weer te geven.

![ Kader IO ](./images/frame22.png)

De gedetailleerde mening van de bel toont u de gegevens die van Kader I/O werden ontvangen. Je moet verschillende id&#39;s zien. Als voorbeeld, toont het gebied **resource.id** unieke identiteitskaart in Kader I/O van de activa **burgerschap-fiber.psd**

![ Kader IO ](./images/frame23.png)

Nu communicatie tot stand is gebracht tussen frame I/O en Workfront Fusion, kunt u doorgaan met de configuratie.

## 1.2.5.3 Een aangepaste formulierreactie voor frame-I/O opgeven.



## Volgende stappen

Ga naar [ 1.2.6 Kader I/O aan Fusie aan AEM Assets ](./ex6.md){target="_blank"}

Ga terug naar [ de Automatisering van het Werkschema van Creative met Workfront Fusion ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}


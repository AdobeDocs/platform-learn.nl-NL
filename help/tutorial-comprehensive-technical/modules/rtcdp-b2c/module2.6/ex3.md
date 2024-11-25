---
title: Het HTTP API-eindpunt in Adobe Experience Platform configureren
description: Het HTTP API-eindpunt in Adobe Experience Platform configureren
kt: 5342
doc-type: tutorial
exl-id: a29dd01d-4415-45d6-ad52-7f14aef60565
source-git-commit: 6485bfa1c75c43bb569f77c478a273ace24a61d4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 2.6.3 Het HTTP API-streamingeindpunt in Adobe Experience Platform configureren

Voordat u de Adobe Experience Platform Sink Connector kunt instellen in Kafka, moet u een HTTP API Source Connector maken in Adobe Experience Platform. De URL voor het HTTP API-streamingeindpunt is vereist voor het instellen van de Adobe Experience Platform Sink Connector.

Om een Schakelaar van HTTP API Source tot stand te brengen, login aan Adobe Experience Platform door aan dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het linkermenu, ga naar **Bronnen** en rol neer in de **Broncatalogus** tot u **HTTP API** ziet. Klik **Opstelling**.

![ Ingestie van Gegevens ](./images/kaep1.png)

Klik **Nieuwe rekening**. Gebruik `--aepUserLdap-- - Kafka` als naam voor uw verbinding van HTTP API, in dit geval **vangeluw - Kafka**. Laat checkbox voor **Compatible XDM** toe. Klik **verbinden met bron**.

![ Ingestie van Gegevens ](./images/kaep2.png)

U zult dan dit zien, klik **daarna**.

![ Ingestie van Gegevens ](./images/kaep3.png)

Selecteer **Bestaande dataset**, open het dropdown menu. Onderzoek en selecteer het dataset **Systeem van de Demo - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1)**.

Klik **daarna**.

![ Ingestie van Gegevens ](./images/kaep4.png)

Klik **Afwerking**.

![ Ingestie van Gegevens ](./images/kaep8.png)

Vervolgens ziet u een overzicht van de HTTP API Source Connector die u zojuist hebt gemaakt.

U zult het **Streaming eindpunt** URL moeten kopiëren, die als hieronder kijkt, aangezien u het in de volgende oefening zult nodig hebben.

`https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`

![ Ingestie van Gegevens ](./images/kaep9.png)

U hebt deze oefening voltooid.

Volgende Stap: [ 2.6.4 installeer en vorm Kafka verbindt en de Schakelaar van het Sink van Adobe Experience Platform ](./ex4.md)

[Terug naar module 2.6](./aep-apache-kafka.md)

[Terug naar alle modules](../../../overview.md)

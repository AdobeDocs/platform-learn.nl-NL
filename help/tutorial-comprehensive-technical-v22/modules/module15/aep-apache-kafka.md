---
title: Gegevens van Apache Kafka streamen naar Adobe Experience Platform
description: In deze module leert u hoe u uw eigen Apache Kafka-cluster instelt, onderwerpen, producenten en consumenten definieert en gegevens stroomt naar Adobe Experience Platform met behulp van de Adobe Experience Platform Sink Connector voor Kafka Connect.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: e1e283b1-93b7-4d06-b9ed-beac48a99c3f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# 15. Gegevens van Apache Kafka streamen naar Adobe Experience Platform

**Auteurs: [Vivek Tiwari](https://www.linkedin.com/in/vivek-tiwari-25092656/), [Nipun Nair](https://www.linkedin.com/in/nipunnair/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module leert u hoe u uw eigen Apache Kafka-cluster instelt, onderwerpen, producenten en consumenten definieert en gegevens stroomt naar Adobe Experience Platform met behulp van de Adobe Experience Platform Sink Connector via Kafka Connect.

## Leerdoelen

- Een basisconfiguratie van een lokale Kafka-cluster uitvoeren
- Maak een Kafka-onderwerp, gebruik een Kafka-producent en een Kafka-consument
- Kafka Connect en de Adobe Experience Platform Sink Connector configureren
- Handmatig gebeurtenissen maken en deze gebeurtenissen bekijken die in Adobe Experience Platform worden opgenomen
- Een bestaande Twitter-productebibliotheek van Kafka Connect gebruiken om Twitter-gegevens naar Adobe Experience Platform te streamen

## Vereisten

- Java JDK11 of hoger moet op uw computer zijn geïnstalleerd. U kunt die JDK hier downloaden: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- Toegang tot Adobe Experience Platform

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem24.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[15.1 Inleiding tot Apache Kafka](./ex1.md)

In deze oefening leert u de grondbeginselen van Apache Kafka

[15.2 Installeer en configureer uw Kafka-cluster](./ex2.md)

In deze oefening, zult u uw basisApache Kafka cluster downloaden, installeren en vormen.

[15.3 Het HTTP API-streamingeindpunt in Adobe Experience Platform configureren](./ex3.md)

In deze oefening, zult u een HTTP API BronSchakelaar in Adobe Experience Platform vormen.

[15.4 Kafka Connect en de Adobe Experience Platform Sink Connector installeren en configureren](./ex4.md)

Hierbij gebruikt u Kafka Connect om de Adobe Experience Platform Sink Connector te installeren en gebruiken en u verzendt gebeurtenissen handmatig naar Adobe Experience Platform.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)

---
title: Uw Kafka-cluster installeren en configureren
description: Uw Kafka-cluster installeren en configureren
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: adffeead-9bcb-4632-9a2c-c6da1c40b7f2
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# 2.6.2 Uw Kafka-cluster installeren en configureren

## 2.6.2.1 Apache Kafka downloaden

Ga naar [ https://kafka.apache.org/downloads ](https://kafka.apache.org/downloads) en download de recentste vrijgegeven versie. Selecteer de recentste binaire versie, in dit geval **Scala 2.13**.

![ Kafka ](./images/kafka1.png)

Je wordt dan naar een spiegelsite gebracht. Klik op de voorgestelde koppeling om Kafka te downloaden.

![ Kafka ](./images/kafka2.png)

Creeer een omslag op uw Desktop genoemd **Kafka_AEP** en plaats het gedownloade dossier in die folder.

![ Kafka ](./images/kafka3.png)

Open a **Eind** venster door uw omslag met de rechtermuisknop aan te klikken en **Nieuwe Eind in Omslag** te klikken.

![ Kafka ](./images/kafka4.png)

Voer dit bevel in uw Eind venster in werking om het gedownloade dossier te decomprimeren:

`tar -xvf kafka_2.13-3.1.0.tgz`

>[!NOTE]
>
>Controleer of de bovenstaande opdracht overeenkomt met de versie van het bestand dat u hebt gedownload. Als uw versie recenter is, zult u het bovengenoemde bevel moeten bijwerken om die versie aan te passen.

![ Kafka ](./images/kafka5.png)

U zult dan dit zien:

![ Kafka ](./images/kafka6.png)

Na het decomprimeren van dat bestand hebt u nu een map als deze:

![ Kafka ](./images/kafka7.png)

En in die folder, zult u deze subdirecteuren zien:

![ Kafka ](./images/kafka8.png)

Ga terug naar uw Eind venster. Voer de volgende opdracht in:

`cd kafka_2.13-3.1.0`

>[!NOTE]
>
>Controleer of de bovenstaande opdracht overeenkomt met de versie van het bestand dat u hebt gedownload. Als uw versie recenter is, zult u het bovengenoemde bevel moeten bijwerken om die versie aan te passen.

![ Kafka ](./images/kafka9.png)

Voer vervolgens de opdracht `bin/kafka-topics.sh` in.

![ Kafka ](./images/kafka10a.png)

U zou dan deze reactie moeten zien. Dit betekent dat Kafka correct is geïnstalleerd en dat Java prima werkt. (Herinnering: dit werkt alleen als Java 8 JDK of Java 11 JDK is geïnstalleerd. U kunt zien welke Java-versie u hebt geïnstalleerd met de opdracht `java -version` .)

![ Kafka ](./images/kafka10.png)

## 2.6.2.2 Kafka starten

Om Kafka te starten, moet je Kafka Zookeeper en Kafka starten, in deze volgorde.

Open a **Eind** venster door uw omslag **kafka_2.13-3.1.0** met de rechtermuisknop aan te klikken en **Nieuwe Eind bij Omslag** te klikken.

![ Kafka ](./images/kafka11.png)

Voer deze opdracht in:

`bin/zookeeper-server-start.sh config/zookeeper.properties`

![ Kafka ](./images/kafka12.png)

U zult dan dit zien:

![ Kafka ](./images/kafka13.png)

Houd dit venster open terwijl u deze oefeningen doorloopt!

Open een ander, nieuw **Eind** venster door uw omslag **kafka_2.13-3.1.0** met de rechtermuisknop aan te klikken en **Nieuwe Eind bij Omslag** te klikken.

![ Kafka ](./images/kafka11.png)

Voer deze opdracht in:

`bin/kafka-server-start.sh config/server.properties`

![ Kafka ](./images/kafka14.png)

U zult dan dit zien:

![ Kafka ](./images/kafka15.png)

Houd dit venster open terwijl u deze oefeningen doorloopt!

## 2.6.2.3 Een Kafka-onderwerp maken

Open a **Eind** venster door uw omslag **kafka_2.13-3.1.0** met de rechtermuisknop aan te klikken en **Nieuwe Eind bij Omslag** te klikken.

![ Kafka ](./images/kafka11.png)

Ga dit bevel in om een nieuw onderwerp Kafka met de naam **te creëren ontvankelijk**. Dit onderwerp zal voor het testen in deze oefening worden gebruikt.

`bin/kafka-topics.sh --create --topic aeptest --bootstrap-server localhost:9092`

![ Kafka ](./images/kafka16a.png)

Je ziet dan een vergelijkbare bevestiging:

![ Kafka ](./images/kafka17a.png)

Ga dit bevel in om een nieuw onderwerp Kafka met de naam **te creëren aep**. Dit onderwerp zal door de Schakelaar worden gebruikt van het Sink van Adobe Experience Platform die u in de volgende oefeningen zult vormen.

`bin/kafka-topics.sh --create --topic aep --bootstrap-server localhost:9092`

![ Kafka ](./images/kafka16.png)

Je ziet dan een vergelijkbare bevestiging:

![ Kafka ](./images/kafka17.png)

## 2.6.2.4 Productieevenementen

Ga terug naar het Eind venster waarin u uw eerste Kafka onderwerp creeerde en het volgende bevel ingaat:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aeptest`

![ Kafka ](./images/kafka18.png)

Dan zie je dit. Elke nieuwe lijn die door de Enter knoop wordt gevolgd zal in een nieuw bericht resulteren dat in het onderwerp **wordt verzonden ontvankelijk**.

![ Kafka ](./images/kafka19.png)

Voer `Hello AEP` in en druk op Enter. Uw eerste gebeurtenis is nu verzonden naar uw lokale instantie Kafka, in het onderwerp **ontvankelijk**.

![ Kafka ](./images/kafka20.png)

Voer `Hello AEP again.` in en druk op Enter.

Voer `AEP Data Collection is the best.` in en druk op Enter.

U hebt nu 3 gebeurtenissen in het onderwerp **ontvankelijk** geproduceerd. Deze gebeurtenissen kunnen nu worden verbruikt door een toepassing die deze gegevens nodig heeft.

![ Kafka ](./images/kafka21.png)

Klik op het toetsenbord op `Control` en `C` tegelijk om de producent te sluiten.

![ Kafka ](./images/kafka22.png)

## 2.6.2.4 Consumptie

In het zelfde Eindvenster dat u gebruikte om gebeurtenissen te veroorzaken, ga het volgende bevel in:

`bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic aeptest --from-beginning`

U zult dan alle berichten zien die in de vorige oefening voor het onderwerp **aeptest** werden veroorzaakt, in de consument verschijnen. Zo werkt Apache Kafka: een producent creëert evenementen in een pijpleiding en een consument verbruikt die evenementen.

![ Kafka ](./images/kafka23.png)

Klik op het toetsenbord op `Control` en `C` tegelijk om de producent te sluiten.

![ Kafka ](./images/kafka24.png)

In deze oefening, hebt u alle grondbeginselen doorlopen om een lokale cluster Kafka op te zetten, een onderwerp van Kafka tot stand te brengen, gebeurtenissen te produceren en gebeurtenissen te verbruiken.

Het doel van deze module is om te simuleren wat er zou gebeuren als een echte organisatie al een Apache Kafka-cluster heeft geïmplementeerd en gegevens van hun Kafka-cluster naar Adobe Experience Platform wil streamen.

Om een dergelijke implementatie te vergemakkelijken, is een Adobe Experience Platform Sink Connector gemaakt die kan worden geïmplementeerd met Kafka Connect. U kunt de documentatie van die Schakelaar van Adobe Experience Platform hier vinden: [ https://github.com/adobe/experience-platform-streaming-connect ](https://github.com/adobe/experience-platform-streaming-connect).

Bij de volgende oefeningen implementeert u alles wat u nodig hebt om die Adobe Experience Platform Sink Connector vanuit uw eigen lokale Kafka-cluster te gebruiken.

Sluit uw eindvenster.

U hebt deze oefening voltooid.

Volgende Stap: [ 2.6.3 vormt HTTP API eindpunt in Adobe Experience Platform ](./ex3.md)

[Terug naar module 2.6](./aep-apache-kafka.md)

[Terug naar alle modules](../../../overview.md)

---
title: Uw Kafka-cluster installeren en configureren
description: Uw Kafka-cluster installeren en configureren
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: adffeead-9bcb-4632-9a2c-c6da1c40b7f2
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# 15.2 Installeer en configureer uw Kafka-cluster

## 15.2.1 Apache Kafka downloaden

Ga naar [https://kafka.apache.org/downloads](https://kafka.apache.org/downloads) en downloadt u de meest recente uitgebrachte versie. Selecteer in dit geval de meest recente binaire versie **Scala 2,13**.

![Kafka](./images/kafka1.png)

Je wordt dan naar een spiegelsite gebracht. Klik op de voorgestelde koppeling om Kafka te downloaden.

![Kafka](./images/kafka2.png)

Een map op uw bureaublad maken met de naam **Kafka_AEP** en plaats het gedownloade bestand in die map.

![Kafka](./images/kafka3.png)

Een **Terminal** venster door met de rechtermuisknop op de map te klikken en op **Nieuwe terminal bij map**.

![Kafka](./images/kafka4.png)

Voer dit bevel in uw Eind venster in werking om het gedownloade dossier te decomprimeren:

`tar -xvf kafka_2.13-3.1.0.tgz`

>[!NOTE]
>
>Controleer of de bovenstaande opdracht overeenkomt met de versie van het bestand dat u hebt gedownload. Als uw versie recenter is, zult u het bovengenoemde bevel moeten bijwerken om die versie aan te passen.

![Kafka](./images/kafka5.png)

U zult dan dit zien:

![Kafka](./images/kafka6.png)

Na het decomprimeren van dat bestand hebt u nu een map als deze:

![Kafka](./images/kafka7.png)

En in die folder, zult u deze subdirecteuren zien:

![Kafka](./images/kafka8.png)

Ga terug naar uw Eind venster. Voer de volgende opdracht in:

`cd kafka_2.13-3.1.0`

>[!NOTE]
>
>Controleer of de bovenstaande opdracht overeenkomt met de versie van het bestand dat u hebt gedownload. Als uw versie recenter is, zult u het bovengenoemde bevel moeten bijwerken om die versie aan te passen.

![Kafka](./images/kafka9.png)

Voer vervolgens de opdracht in `bin/kafka-topics.sh`.

![Kafka](./images/kafka10a.png)

U zou dan deze reactie moeten zien. Dit betekent dat Kafka correct is geïnstalleerd en dat Java prima werkt. (Herinnering: u hebt Java 8 JDK of Java 11 JDK nodig geïnstalleerd om dit te laten werken!. U kunt zien welke Java-versie u hebt geïnstalleerd met de opdracht `java -version`.)

![Kafka](./images/kafka10.png)

## 15.2.2 Start Kafka

Om Kafka te starten, moet je Kafka Zookeeper en Kafka starten, in deze volgorde.

Een **Terminal** venster door met de rechtermuisknop op uw map te klikken **kafka_2.13-3.1.0** en klikken **Nieuwe terminal bij map**.

![Kafka](./images/kafka11.png)

Voer deze opdracht in:

`bin/zookeeper-server-start.sh config/zookeeper.properties`

![Kafka](./images/kafka12.png)

U zult dan dit zien:

![Kafka](./images/kafka13.png)

Houd dit venster open terwijl u deze oefeningen doorloopt!

Een andere, nieuwe openen **Terminal** venster door met de rechtermuisknop op uw map te klikken **kafka_2.13-3.1.0** en klikken **Nieuwe terminal bij map**.

![Kafka](./images/kafka11.png)

Voer deze opdracht in:

`bin/kafka-server-start.sh config/server.properties`

![Kafka](./images/kafka14.png)

U zult dan dit zien:

![Kafka](./images/kafka15.png)

Houd dit venster open terwijl u deze oefeningen doorloopt!

## 15.2.3 Een Kafka-onderwerp maken

Een **Terminal** venster door met de rechtermuisknop op uw map te klikken **kafka_2.13-3.1.0** en klikken **Nieuwe terminal bij map**.

![Kafka](./images/kafka11.png)

Ga dit bevel in om een nieuw Kafka onderwerp met de naam tot stand te brengen **aanvaardbaar**. Dit onderwerp zal voor het testen in deze oefening worden gebruikt.

`bin/kafka-topics.sh --create --topic aeptest --bootstrap-server localhost:9092`

![Kafka](./images/kafka16a.png)

Je ziet dan een vergelijkbare bevestiging:

![Kafka](./images/kafka17a.png)

Ga dit bevel in om een nieuw Kafka onderwerp met de naam tot stand te brengen **aep**. Dit onderwerp zal door de Schakelaar worden gebruikt van het Sink van Adobe Experience Platform die u in de volgende oefeningen zult vormen.

`bin/kafka-topics.sh --create --topic aep --bootstrap-server localhost:9092`

![Kafka](./images/kafka16.png)

Je ziet dan een vergelijkbare bevestiging:

![Kafka](./images/kafka17.png)

## 15.2.4 Productieevenementen

Ga terug naar het Eind venster waarin u uw eerste Kafka onderwerp creeerde en het volgende bevel ingaat:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aeptest`

![Kafka](./images/kafka18.png)

Dan zie je dit. Elke nieuwe lijn die door de Enter knoop wordt gevolgd zal in een nieuw bericht resulteren dat naar het onderwerp wordt verzonden **aanvaardbaar**.

![Kafka](./images/kafka19.png)

Enter `Hello AEP` en drukt u op Enter. Uw eerste gebeurtenis is nu verzonden naar uw lokale instantie Kafka, in het onderwerp **aanvaardbaar**.

![Kafka](./images/kafka20.png)

Enter `Hello AEP again.` en drukt u op Enter.

Enter `AEP Data Collection is the best.` en drukt u op Enter.

U hebt nu 3 gebeurtenissen in het onderwerp geproduceerd **aanvaardbaar**. Deze gebeurtenissen kunnen nu worden verbruikt door een toepassing die deze gegevens nodig heeft.

![Kafka](./images/kafka21.png)

Klik op het toetsenbord op `Control` en `C` om de producent te sluiten.

![Kafka](./images/kafka22.png)

## 15.2.4 Consumptiegebeurtenissen

In het zelfde Eindvenster dat u gebruikte om gebeurtenissen te veroorzaken, ga het volgende bevel in:

`bin/kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic aeptest --from-beginning`

U zult dan alle berichten zien die in de vorige oefening voor het onderwerp werden veroorzaakt **aanvaardbaar**, in de consument. Zo werkt Apache Kafka: een producent creëert evenementen in een pijpleiding en een consument verbruikt deze evenementen .

![Kafka](./images/kafka23.png)

Klik op het toetsenbord op `Control` en `C` om de producent te sluiten.

![Kafka](./images/kafka24.png)

In deze oefening, hebt u alle grondbeginselen doorlopen om een lokale cluster Kafka op te zetten, een onderwerp van Kafka tot stand te brengen, gebeurtenissen te produceren en gebeurtenissen te verbruiken.

Het doel van deze module is om te simuleren wat er zou gebeuren als een echte organisatie al een Apache Kafka-cluster heeft geïmplementeerd en gegevens van hun Kafka-cluster naar Adobe Experience Platform wil streamen.

Om een dergelijke implementatie te vergemakkelijken, is een Adobe Experience Platform Sink Connector gemaakt die kan worden geïmplementeerd met Kafka Connect. Hier vindt u de documentatie van die Adobe Experience Platform Sink Connector: [https://github.com/adobe/experience-platform-streaming-connect](https://github.com/adobe/experience-platform-streaming-connect).

Bij de volgende oefeningen implementeert u alles wat u nodig hebt om die Adobe Experience Platform Sink Connector vanuit uw eigen lokale Kafka-cluster te gebruiken.

Sluit uw eindvenster.

U hebt deze oefening voltooid.

Volgende stap: [15.3 Het eindpunt van HTTP API in Adobe Experience Platform configureren](./ex3.md)

[Ga terug naar module 15](./aep-apache-kafka.md)

[Terug naar alle modules](../../overview.md)

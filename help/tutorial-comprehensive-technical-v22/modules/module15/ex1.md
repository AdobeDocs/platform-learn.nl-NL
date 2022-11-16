---
title: Inleiding tot Apache Kafka
description: Inleiding tot Apache Kafka
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 7b600c79-03c5-46fc-9ac9-a15599608c35
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# 15.1 Inleiding tot Apache Kafka

## 15.1.1 Inleiding

Elke organisatie begint op een zeer eenvoudige manier vanuit gegevensperspectief. Het gegevensecosysteem van een organisatie begint met één bronsysteem en één doel. Het bronsysteem verzendt gegevens naar het doelsysteem, en dat is het. Eenvoudig, toch?
Als het alleen zo eenvoudig zou blijven. Organisaties overtreffen snel die eenvoudige installatie en het aantal bronsystemen en doelsystemen neemt snel toe. Al deze verschillende bronnen en bestemmingen moeten gegevens met elkaar uitwisselen, en de zaken worden snel zeer complex.
Bijvoorbeeld, als een organisatie 4 bronnen en 6 bestemmingen heeft en al deze toepassingen met elkaar moeten spreken, zult u 24 integraties moeten bouwen.. Elk van deze integraties heeft zijn eigen problemen:

- protocol: hoe gegevens worden vervoerd (TCP, HTTP, REST, FTP, ...)
- gegevensindeling: hoe worden de gegevens geparseerd (binair, CSV, JSON, Parquet, ...)
- gegevensschema en evolutie: wat is het gegevensmodel en hoe zal het evolueren ?

Bovendien, telkens als u een bronsysteem aan een bestemmingssysteem aansluit, zal er een verhoogde lading op die systemen van die verbinding zijn.

Hoe los je dit op? Daar komt Apache Kafka op. Apache Kafka staat een organisatie toe om gegevensstromen en systemen te ontkoppelen door een gemeenschappelijk, hoog-productie, verdeeld overseinensysteem te verstrekken. Bronsystemen sturen hun gegevens naar Apache Kafka en doelsystemen gebruiken gegevens van Apache Kafka.

Denk aan alle types van gegevensbronnen ervaren de ondernemingen moeten leiden:

- websitegebeurtenissen
- mobiele app-gebeurtenissen
- POS-gebeurtenissen
- CRM-gegevens
- callcenter-gegevens
- transactiegeschiedenis
- ...

En denk aan alle soorten bestemmingen ondernemingen gebruiken in hun ecosysteem die allen gegevens van die bronsystemen zouden kunnen vereisen:

- CRM
- gegevensmeer
- e-mailsysteem
- audit
- analyse
- ...

Apache Kafka werd door LinkedIn opgericht en is nu een open-sourceproject dat voornamelijk door Confluent wordt onderhouden.
Apache Kafka biedt een gedistribueerde, veerkrachtige architectuur die fouttolerant is. Het kan horizontaal aan 100s van makelaars schrapen en aan miljoenen berichten per seconde schrapen. Deze laptop biedt hoge prestaties met een latentie van minder dan 10 ms. Deze is ideaal voor gebruikssituaties in real-time.

Enkele voorbeelden van gebruikssituaties:

- Messaging System
- Activiteit bijhouden
- Metrische gegevens verzamelen van vele verschillende locaties
- Toepassingslogbestanden verzamelen
- Stroomverwerking (met Kafka Streams API of Spark)
- Ontkoppeling van systeemafhankelijkheden
- Integratie met Spark, Flink, Storm, Hadoop en vele andere Big Data-technologieën.

Bijvoorbeeld:

- Netflix gebruikt Kafka om aanbevelingen in real time toe te passen terwijl u TV toont
- Uber gebruikt Kafka om gebruikers, taxigegevens en reisgegevens in real time te verzamelen om de vraag te berekenen en te voorspellen en piekprijzen in real time te berekenen
- linkedIn gebruikt Kafka om spam te voorkomen, verzamelt gebruikersinteracties om betere verbindingsaanbevelingen in real time te doen

Voor al deze gebruiksgevallen wordt Kafka alleen gebruikt als transportmechanisme. Kafka is echt goed in het verplaatsen van gegevens tussen toepassingen.

## 15.1.2 Terminologie van Kafka

### Bericht

Een bericht is een mededeling die door een systeem naar Kafka wordt verzonden. Een bericht bevat een lading, en een lading bevat gegevenselementen. Een ervaringsgebeurtenis die door een website naar Adobe Experience Platform wordt verzonden, wordt bijvoorbeeld als een bericht beschouwd.

### Onderwerp, partities, verschuivingen

Een onderwerp is een bepaalde stroom van gegevens, gelijkend op een lijst in een gegevensbestand. U kunt zo vele onderwerpen hebben aangezien u wilt, en een onderwerp door zijn naam wordt geïdentificeerd. Onderwerpen worden in partities gesplitst. Elke verdeling wordt bevolen en elk bericht binnen een verdeling krijgt stijgende identiteitskaart, die wordt geroepen **offset**. De berichten worden opgeslagen in een onderwerp, op een verdeling en van verwijzingen voorzien gebruikend een compensatie. Berichten worden slechts gedurende een beperkte tijd bewaard (standaard is 1 week). Zodra een bericht aan een verdeling wordt geschreven, kan het niet meer worden veranderd.

### Brokers

Een makelaar is vergelijkbaar met een server. Een Kafka-cluster bestaat uit meerdere makelaars (servers). Elke makelaar wordt geïdentificeerd met identiteitskaart en bevat bepaalde onderwerpverdelingen.

### Replicatie

Kafka is een gedistribueerd systeem. Één van de belangrijke dingen van een verdeeld systeem is dat het gegeven veilig wordt opgeslagen en als dusdanig, replicatie nodig is. Per slot van rekening, wanneer één makelaar (server) daalt, zou een andere makelaar (server) nog toegang tot berichten moeten kunnen verlenen die aanvankelijk op de makelaar werden opgeslagen die daalde. De replicatie zal exemplaren van berichten over veelvoudige makelaars tot stand brengen om ervoor te zorgen dat geen gegevens wordt verloren.

### Producenten

Hoe worden gegevens naar Kafka verzonden? Dat is de rol van een producent. Een producent verbindt met een bronsysteem en neemt gegevens van het bronsysteem, en schrijft dan die gegevens aan onderwerpen op verdelingen. Op basis van de configuratie van uw Kafka-cluster weten producenten automatisch naar welke tussenpersoon en partitie moet worden geschreven. In een verdeeld systeem met veelvoudige makelaars en replicatiestrategie, zal een producent gegevens willekeurig over veelvoudige makelaars opslaan, zo betekent het dat het lading automatisch in evenwicht brengen zal doen.

### Berichtsleutels

Producenten kunnen ervoor kiezen een sleutel met het bericht te verzenden. Een sleutel kan elke tekenreeks, elk getal, enzovoort zijn. Als geen sleutel wordt verstrekt, zal een bericht willekeurig naar makelaars worden verzonden. Als een sleutel wordt verzonden, dan zullen alle berichten voor die sleutel altijd naar de zelfde verdeling gaan. Een berichtsleutel als dusdanig wordt gebruikt aan ordeberichten die op een specifiek gebied worden gebaseerd.

### Consumenten

De consumenten lezen gegevens van een Apache Kafka onderwerp en delen dan die gegevens met bestemmingssystemen. Consumenten weten van welke tussenpersoon ze moeten lezen. De gegevens worden gelezen door een consument in orde, binnen elke verdeling. Consumenten lezen gegevens in consumentengroepen.

### Zookeeper

ZooKeeper is hoofdzakelijk de dienst voor verdeelde systemen die een hiërarchische sleutel-waarde opslag aanbieden, die wordt gebruikt om de verdeelde configuratiedienst, synchronisatiedienst, en noemend registratie voor grote verdeelde systemen te verlenen. Zookeeper moet actief zijn voordat u Apache Kafka kunt gebruiken. Zookeeper is een soort van master ceremonie voor Kafka, die gedistribueerde services op de achtergrond beheert terwijl Kafka evenementen produceert en consumeert.

U hebt deze oefening voltooid.

Volgende stap: [15.2 Installeer en configureer uw Kafka-cluster](./ex2.md)

[Ga terug naar module 15](./aep-apache-kafka.md)

[Terug naar alle modules](../../overview.md)

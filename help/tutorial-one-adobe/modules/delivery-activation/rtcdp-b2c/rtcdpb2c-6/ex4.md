---
title: Kafka Connect en de Adobe Experience Platform Sink Connector installeren en configureren
description: Kafka Connect en de Adobe Experience Platform Sink Connector installeren en configureren
kt: 5342
doc-type: tutorial
exl-id: 51ddfdfc-fa5c-4bf4-bfc2-b4a88b0b8a4d
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 0%

---

# 2.6.4 Kafka Connect en de Adobe Experience Platform Sink Connector installeren en configureren

## Download de Adobe Experience Platform Sink Connector

Ga naar [ https://github.com/adobe/experience-platform-streaming-connect/releases ](https://github.com/adobe/experience-platform-streaming-connect/releases) en download de recentste officiële versie van de Schakelaar van de Zink van Adobe Experience Platform.

![ Kafka ](./images/kc1.png)

Download het dossier **streaming-connect-sink-0.0.27-java-11.jar**.

![ Kafka ](./images/kc1a.png)

Plaats het downloaddossier, **het stromen-verbinden-goot-0.0.27-java-11.jar**, op uw Desktop.

![ Kafka ](./images/kc2.png)

## Kafka Connect configureren

Ga naar de omslag op uw Desktop genoemd **Kafka_AEP** en navigeer aan de omslag `kafka_2.13-3.9.0/config`.
In die omslag, open het dossier **connect-distribute.properties** gebruikend om het even welke Redacteur van de Tekst.

![ Kafka ](./images/kc3a.png)

Ga in de Teksteditor naar regel 34 en 35 en stel de velden in op `key.converter.schemas.enable` en `value.converter.schemas.enable` op `false`

```json
key.converter.schemas.enable=false
value.converter.schemas.enable=false
```

Sla uw wijzigingen in dit bestand op.

![ Kafka ](./images/kc3.png)

Ga vervolgens terug naar de map `kafka_2.13-3.1.0` en maak handmatig een nieuwe map en noem deze `connectors` .

![ Kafka ](./images/kc4.png)

Klik de nieuwe omslag met de rechtermuisknop aan en klik **Nieuwe terminal bij Omslag**.

![ Kafka ](./images/kc5.png)

Dan zie je dit. Voer de opdracht `pwd` in om het volledige pad voor die map op te halen. Selecteer het volledige pad en kopieer het naar het klembord.

![ Kafka ](./images/kc6.png)

Ga terug naar uw Redacteur van de Tekst, aan het dossier **connect-distribute.properties** en rol neer aan de laatste lijn (lijn 89 in het schermafbeelding). Verwijder de commentaarmarkering van de regel (verwijder `#` ) die begint met `# plugin.path=` en plak het volledige pad naar de map met de naam `connectors` . Het resultaat moet er ongeveer als volgt uitzien:

`plugin.path=/Users/woutervangeluwe/Desktop/Kafka_AEP/kafka_2.13-3.9.0/connectors`

Sparen uw veranderingen in het dossier **connect-distribute.properties** en sluit uw Redacteur van de Tekst.

![ Kafka ](./images/kc7.png)

Kopieer vervolgens de meest recente officiële release van de Adobe Experience Platform Sink Connector die u naar de map met de naam `connectors` hebt gedownload. Het dossier dat u alvorens wordt gedownload wordt genoemd **streaming-verbinden-goot-0.0.27-java-11.jar**, kunt u het eenvoudig in de `connectors` omslag bewegen.

![ Kafka ](./images/kc8.png)

Daarna, open een nieuw Eind venster op het niveau van **kafka_2.13-3.9.0** omslag. Klik die omslag met de rechtermuisknop aan en klik **Nieuwe Terminal bij Omslag**.

In het Eind venster, kleef dit bevel: `bin/connect-distributed.sh config/connect-distributed.properties` en klik **gaat** binnen. Met deze opdracht start u Kafka Connect en laadt u de bibliotheek van de Adobe Experience Platform Sink Connector.

![ Kafka ](./images/kc9.png)

Na een paar seconden zie je iets als dit:

![ Kafka ](./images/kc10.png)

## Adobe Experience Platform Sink Connector maken met Postman

U kunt nu communiceren met Kafka Connect via Postman. Om dit te doen, download [ deze Inzameling van Postman ](./../../../../assets/postman/postman_kafka.zip) en uncompress het aan uw lokale computer op de Desktop. Vervolgens hebt u een bestand met de naam `Kafka_AEP.postman_collection.json` .

![ Kafka ](./images/kc11a.png)

U moet dit bestand importeren in Postman. Om dit te doen, open Postman, klik **Invoer**, sleep en laat vallen het dossier `Kafka_AEP.postman_collection.json` in popup en klik **de Invoer**.

![ Kafka ](./images/kc11b.png)

U zult dan deze inzameling in het linkermenu van Postman vinden. Klik het eerste verzoek, **GET Beschikbare Kafka verbindt schakelaars** om het te openen.

![ Kafka ](./images/kc11c.png)

Dan zie je dit. Klik de blauwe **verzenden** knoop, waarna u een lege reactie `[]` zou moeten zien. De lege reactie is het gevolg van het feit dat er momenteel geen Kafka Connect-connectors zijn gedefinieerd.

![ Kafka ](./images/kc11.png)

Om een schakelaar tot stand te brengen, klik om het tweede verzoek in de inzameling te openen Kafka, **POST leidt tot Schakelaar van de Zink AEP** en gaat naar **Lichaam**. Dan zie je dit. Op lijn 11, waar het **&quot;aep.Endend&quot; zegt: &quot;&quot;**, moet u in het HTTP API die eindpunt URL stromen plakken die u aan het eind van één van de vorige oefeningen ontving. De URL voor het HTTP API-streamingeindpunt ziet er als volgt uit: `https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`.

![ Kafka ](./images/kc12a.png)

Na het plakken zou de tekst van uw verzoek als dit moeten kijken. Klik de blauwe **verzenden** knoop om uw schakelaar tot stand te brengen. U zult een directe reactie van de verwezenlijking van uw schakelaar krijgen.

![ Kafka ](./images/kc12.png)

Klik het eerste verzoek, **GET Beschikbare Kafka verbindt schakelaars** om het opnieuw te openen en de blauwe **te klikken verzenden** knoop opnieuw. U ziet nu dat er een Kafka Connect-aansluiting bestaat.

![ Kafka ](./images/kc13.png)

Daarna, open het derde verzoek in de inzameling Kafka, **GET Check Kafka verbindt de Status van de Schakelaar**. Klik de blauwe **verzenden** knoop, zult u dan een reactie zoals hieronder krijgen, verklarend dat de schakelaar loopt.

![ Kafka ](./images/kc14.png)

## Een ervaringsgebeurtenis maken

Open een nieuw **Eind** venster door uw omslag **kafka_2.13-3.9.0** met de rechtermuisknop aan te klikken en **Nieuwe Eind bij Omslag** te klikken.

![ Kafka ](./images/kafka11.png)

Voer de volgende opdracht in:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aep`

Dan zie je dit. Elke nieuwe lijn die door de Enter knoop wordt gevolgd zal in een nieuw bericht resulteren dat in het onderwerp **wordt verzonden aep**.

![ Kafka ](./images/kc16.png)

U kunt nu een bericht verzenden dat zal resulteren in het gebruik door de Adobe Experience Platform Sink Connector, en dat in real time in Adobe Experience Platform zal worden opgenomen.

Neem de onderstaande voorbeeldervaring op bij het laden van de gebeurtenis en kopieer deze naar een teksteditor.

```json
{
  "header": {
    "datasetId": "61fe23fd242870194a6d779c",
    "imsOrgId": "--aepImsOrgID--",
    "source": {
      "name": "Launch"
    },
    "schemaRef": {
      "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
      "contentType": "application/vnd.adobe.xed-full+json;version=1"
    }
  },
  "body": {
    "xdmMeta": {
      "schemaRef": {
        "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
        "contentType": "application/vnd.adobe.xed-full+json;version=1"
      }
    },
    "xdmEntity": {
      "eventType": "callCenterInteractionKafka",
      "_id": "",
      "timestamp": "2024-11-25T09:54:12.232Z",
      "_experienceplatform": {
        "identification": {
          "core": {
            "phoneNumber": ""
          }
        },
        "interactionDetails": {
          "core": {
            "callCenterAgent": {
              "callID": "Support Contact - 3767767",
              "callTopic": "contract",
              "callFeeling": "negative"
            }
          }
        }
      }
    }
  }
}
```

Dan zie je dit. U moet twee velden handmatig bijwerken:

- **_id**: te plaatsen gelieve willekeurige identiteitskaart, iets als `--aepUserLdap--1234`
- **timestamp**: werk timestamp aan de huidige datum en de tijd bij
- **phoneNumber**: ga phoneNumber van de rekening in die vroeger op de demowebsite werd gecreeerd. U kunt het op het paneel van de Kijker van het Profiel onder **Identiteiten** vinden.

U moet ook deze velden controleren en mogelijk bijwerken:

- **datasetId**: u moet identiteitskaart van de Dataset voor het Systeem van de Dataset van de Demo kopiëren - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1)

![ Kafka ](./images/kc20ds.png)

- **imsOrgID**: uw IMS Org identiteitskaart is `--aepImsOrgId--`

>[!NOTE]
>
>Het veld **_id** moet uniek zijn voor elke gegevensinvoer. Als u veelvoudige gebeurtenissen veroorzaakt, gelieve ervoor te zorgen dat u het gebied **_id** telkens aan een nieuwe, unieke waarde bijwerkt.

Dan zou je iets als dit moeten hebben:

![ Kafka ](./images/kc21.png)

Kopieer vervolgens de volledige ervaringsgebeurtenis naar het klembord. De witruimte van uw JSON-lading moet worden verwijderd en daarvoor gebruiken we een online tool. Ga naar [ http://jsonviewer.stack.hu/ ](http://jsonviewer.stack.hu/) om dat te doen.

Plak uw ervaringsgebeurtenis in de redacteur en klik **verwijdert witte ruimte**.

![ Kafka ](./images/kc22a.png)

Selecteer vervolgens alle uitvoertekst en kopieer deze naar het klembord.

![ Kafka ](./images/kc23.png)

Ga terug naar uw Eind venster.

![ Kafka ](./images/kc16.png)

Plak de nieuwe nuttige lading zonder whitespaces in het Eind venster en klik **gaat** binnen.

![ Kafka ](./images/kc23a.png)

Ga vervolgens terug naar uw demowebsite en vernieuw de pagina. U zou nu een ervaringsgebeurtenis op uw profiel, onder **Gebeurtenissen van de Ervaring**, enkel als hieronder moeten zien:

![ Kafka ](./images/kc24.png)

>[!NOTE]
>
>Als u uw interacties van het vraagcentrum op het paneel van de Kijker van het Profiel wilt verschijnen, moet u het hieronder etiket en de filter in uw project op [ https://dsn.adobe.com ](https://dsn.adobe.com) toevoegen, door naar de lusje **Kijker van het Profiel** te gaan en een nieuwe lijn onder **Gebeurtenissen** toe te voegen, met deze variabelen:
>- **Etiket van het Type van Gebeurtenis**: De Interacties van het Centrum van de vraag
>- **Filter van het Type van Gebeurtenis**: callCenterInteractionKafka
>- **Titel**: `--aepTenantId--.interactionDetails.core.callCenterAgent.callID`

![ Kafka ](./images/kc25.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ Samenvatting en voordelen ](./summary.md){target="_blank"}

Ga terug naar [ gegevens van de Stroom van Apache Kafka in Adobe Experience Platform ](./aep-apache-kafka.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

---
title: Uw aangepaste workflow programmatisch uitvoeren
description: Uw aangepaste workflow programmatisch uitvoeren
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
source-git-commit: a3a78b12f8244c8288eb0fffc82ad769776eb118
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# 1.7.2 De aangepaste workflow programmatisch uitvoeren

## 1.7.2.1 Uw aangepaste workflow uitvoeren met Postman

Na het publiceren van uw werkschema in de vorige oefening, zou u iets als dit moeten zien. Klik de **knoop van het Exemplaar** om de steekproeflading te kopiëren.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw61.png)

Open Postman en creeer een nieuwe **Inzameling** gebruikend de naam **Aangepaste Werkschema&#39;s van Firefly**. Dan, klik **verzoek** toevoegen.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw62.png)

Er wordt dan een nieuw leeg verzoek weergegeven. Plak in de adresbalk de lading die u hebt gekopieerd uit de gepubliceerde workflow.

Postman herkent de geplakte cURL-opdracht en voegt deze op de juiste manier toe aan de aanvraag en neemt alle informatie van de payload.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw63.png)

U zou deze **variabelen van de Kopbal** nu moeten zien.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw64.png)

Ga naar **Lichaam**, waar u iets gelijkend op dit zou moeten zien.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw65.png)

U moet nu de vereiste instructies in het lichaam van dit verzoek verstrekken. Wanneer u op programmatische wijze met bestanden werkt, is het gebruik van vooraf ondertekende URL&#39;s vereist. Voor deze oefening, kunt u presigned URLs hieronder voor de 3 beelden vinden die deel van deze oefening uitmaken. Deze vooraf ondertekende URL&#39;s zijn gemaakt met Microsoft Azure Storage-mogelijkheden. Als u meer over zou willen leren hoe te om presigned URLs tot stand te brengen, hier een blik hebben: [&#x200B; optimaliseer uw proces van Firefly gebruikend Microsoft Azure en presigned URLs &#x200B;](./../module1.1/ex2.md).

Voor deze oefening, kunt u hieronder URLs gebruiken zodat te hoeven u geen nieuwe vooraf ondertekende URLs tot stand te brengen zelf.

- **airpods.jpg**

```
https://techinsiders.blob.core.windows.net/vangeluw/airpods.jpg?sv=2023-01-03&st=2026-03-11T01%3A22%3A04Z&se=2027-03-12T01%3A22%3A00Z&sr=b&sp=r&sig=MmQi9lS4lm4DJM1BELmZZM7VLa4ln5zYOcuGisLnrz4%3D
```

- **watch.jpg**

```
https://techinsiders.blob.core.windows.net/vangeluw/watch.jpg?sv=2023-01-03&st=2026-03-11T01%3A26%3A54Z&se=2027-03-12T01%3A26%3A00Z&sr=b&sp=r&sig=xCwQ09E%2F%2FT%2B7RLcb31Fum4uUBfsX0xHITKZTz4Ds9Zs%3D
```

- **phone.jpg**

```
https://techinsiders.blob.core.windows.net/vangeluw/phone.png?sv=2023-01-03&st=2026-03-11T01%3A27%3A20Z&se=2027-03-12T01%3A27%3A00Z&sr=b&sp=r&sig=VVbX88P2sFSHHo9lmgoRhXRIXb42c0nDQhM9Z8nUG%2Bc%3D
```

U moet ook vragen opgeven als onderdeel van het Postman-verzoek. Hieronder vindt u de aanwijzingen die u kunt gebruiken.

- **Herinnering 1**:

```
magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts
```

- **Herinnering 2**:

```
background hearts fluttering
```

Hier is een steekproeflading, maar u kunt dit niet kopiëren en opnieuw gebruiken aangezien de **node_id** gebieden aan uw werkschema uniek zijn, zodat moet dit u enkel een idee van geven hoe de lading als zou moeten kijken:

```json
{
    "workflow": {
        "workflowId": "e0c63806-cf7c-442d-8884-26d57e9c0518",
        "inputs": [
            [
                {
                    "node_id": "node_1772156869527_d8mjasues_1_u10dlg",
                    "content": [
                        {
                            "presignedUrl": "https://techinsiders.blob.core.windows.net/vangeluw/airpods.jpg?sv=2023-01-03&st=2026-03-11T01%3A22%3A04Z&se=2027-03-12T01%3A22%3A00Z&sr=b&sp=r&sig=MmQi9lS4lm4DJM1BELmZZM7VLa4ln5zYOcuGisLnrz4%3D",
                            "storageType": "Azure"
                        }
                    ]
                },
                {
                    "node_id": "node_1772157264659_oq2csr2nn_5_fh5hek",
                    "content": "magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts"
                },
                {
                    "node_id": "node_1772157397147_qdwxiyktg_8_nm0o2k",
                    "content": "background hearts fluttering"
                }
            ]
        ]
    }
}
```

Na het aanbrengen van de veranderingen in uw lading, zou het als dit moeten kijken. Zodra gedaan, verzend de klik **&#x200B;**. Dan, gebruik **CMD + S** of **CTRL + S** aan **sparen** uw verzoek.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw66.png)

In de antwoordlading kunt u nu een paar verbindingen vinden. Deze verbindingen maken het mogelijk om de **status** van het werkschema te vragen, en zodra de status **wordt voltooid**, kunt u **resultaten** URL gebruiken om het beeld en de video terug te winnen die werden geproduceerd.

Selecteer **status** URL en kopieer het.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw67.png)

Klik de 3 punten op het verzoek u momenteel gebruikt en dan **selecteert Dupliceert**.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw69.png)

In het nieuwe verzoek, verander het verzoektype in **GET** en vervang URL door status-URL die u enkel kopieerde.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw70.png)

Onder **Lichaam**, zorg ervoor alles wordt geschrapt. Dan, klik **verzenden**. Vervolgens ontvangt u een vergelijkbare antwoordlading, die een status weergeeft. U kunt dit verzoek opnieuw verzenden tot de status in **voltooide** is veranderd. Vergeet niet **CMD + S** of **CTRL + S** te gebruiken **sparen** uw verzoek.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw71.png)

Ga terug naar het eerste **POST** verzoek. Kopieer nu de **resultaten** URL.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw72.png)

Klik de 3 punten **..** op het tweede verzoek u creeerde, en selecteer dan **Dupliceren**.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw73.png)

In het nieuwe verzoek, kleef de **resultaten** URL u kopieerde en dan **&#x200B;**&#x200B;verzendt klikt. Vergeet niet **CMD + S** of **CTRL + S** te gebruiken **sparen** uw verzoek.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw74.png)

Blader omlaag in de antwoordlading, waar u verwijzingen zult vinden naar het beeld en de video die werden gecreeerd. Klik op de koppelingen om deze bestanden te openen.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw75.png)

Hier is de afbeelding die is gegenereerd.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw76.png)

## 1.7.2.2 Voer uw aangepaste workflow uit met Workfront Fusion

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/){target="_blank"}. Open **de Fusie van Workfront**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion1.png)

Ga naar **Scenario&#39;s**. Als u nog geen map hebt, maakt u een map en gebruikt u: `--aepUserLdap--` . Selecteer uw omslag, en selecteer dan **nieuw scenario** creëren.

![&#x200B; WF Fusion &#x200B;](./images/wffusion2.png)

Dan moet je dit zien.

![&#x200B; WF Fusion &#x200B;](./images/wffusion3.png)

Na het publiceren van uw werkschema in de vorige oefening, zou u iets als dit moeten zien. Klik de **knoop van het Exemplaar** om de steekproeflading te kopiëren.

![&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./images/ffcw61.png)

Ga terug naar je Workfront Fusion-scenario. Gebruik **CMD + V** of **CTRL + V** om de nuttige lading te kleven die u in het scenario kopieerde. De Fusie van Workfront zal automatisch het cURL- verzoek ontdekken en zal een nieuw **HTTP tot stand brengen - doe automatisch een verzoek** module.

Sleep het **klok** pictogram op **HTTP - maak een verzoek** module.

![&#x200B; WF Fusion &#x200B;](./images/wffusion5.png)

Dan moet je dit zien. Klik **HTTP - doe een verzoek** module om het te openen.

![&#x200B; WF Fusion &#x200B;](./images/wffusion6.png)

U zou dan moeten zien dat de **1&rbrace; variabelen van de Kopbal &lbrace;reeds beschikbaar zijn.**

![&#x200B; WF Fusion &#x200B;](./images/wffusion7.png)

Schuif omlaag om de standaardlading te zien. Klik het **pictogram** zoals vermeld om de nuttige lading goed te maken JSON.

![&#x200B; WF Fusion &#x200B;](./images/wffusion8.png)

Ga terug naar Postman, aan het eerste **POST** verzoek. Kopieer de lading.

![&#x200B; WF Fusion &#x200B;](./images/wffusion9.png)

Ga terug naar je Workfront Fusion-scenario. Vervang de bestaande standaardlading door de lading u van Postman kopieerde. Klik het **pictogram** zoals vermeld om de nuttige lading goed te maken JSON.

Controle checkbox voor **ontleed reactie**.

Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion10.png)

Sparen uw veranderingen en klik dan **Looppas eens**.

![&#x200B; WF Fusion &#x200B;](./images/wffusion11.png)

Als je scenario eenmaal is uitgevoerd, kun je een vergelijkbare reactie zien als in Postman. Met deze informatie beschikbaar in de Fusie van Workfront, kunt u nu op dat bouwen om **status** URL te pollen tot de status wordt voltooid, en zodra dat is gebeurd kunt u **resultaten** URL gebruiken om het beeld en de video te verzamelen die werden geproduceerd.

![&#x200B; WF Fusion &#x200B;](./images/wffusion12.png)

## Volgende stappen

Ga terug naar [&#x200B; de Aangepaste Werkschema&#39;s van Firefly &#x200B;](./workflowbuilder.md){target="_blank"}

Ga terug naar [&#x200B; Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

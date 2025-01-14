---
title: Aan de slag met Firefly Services
description: Aan de slag met Firefly Services
kt: 5342
doc-type: tutorial
exl-id: 23ebf8b4-3f16-474c-afe1-520d88331417
source-git-commit: a0c16a47372d322a7931578adca30a246b537183
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# 1.2.2 Adobe-API&#39;s gebruiken in Workfront Fusion

## 1.2.2.1 Gebruik Firefly Text To Image API met Workfront Fusion

Plaats over de tweede **plaats veelvoudige variabelen** knoop en klik **+** om een andere module toe te voegen.

![ WF Fusion ](./images/wffusion48.png)

Onderzoek naar **http**, dan uitgezocht **HTTP**.

![ WF Fusion ](./images/wffusion49.png)

Selecteer **maak een verzoek**.

![ WF Fusion ](./images/wffusion50.png)

Selecteer deze variabelen:

- **URL**: `https://firefly-api.adobe.io/v3/images/generate`
- **Methode**: `POST`

Klik **toevoegen een kopbal**.

![ WF Fusion ](./images/wffusion51.png)

U moet de volgende kopteksten ingaan:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `x-api-key` | opgeslagen variabele voor `CONST_client_id` |
| `Authorization` | `Bearer ` + de opgeslagen variabele voor `bearer_token` |
| `Content-Type` | `application/json` |
| `Accept` | `*/*` |

Voer de details in voor `x-api-key` . Klik **toevoegen**.

![ WF Fusion ](./images/wffusion52.png)

Klik **toevoegen een kopbal**.

![ WF Fusion ](./images/wffusion53.png)

Voer de details in voor `Authorization` . Klik **toevoegen**.

![ WF Fusion ](./images/wffusion54.png)

Klik **toevoegen een kopbal**. Voer de details in voor `Content-Type` . Klik **toevoegen**.

![ WF Fusion ](./images/wffusion541.png)

Klik **toevoegen een kopbal**. Voer de details in voor `Accept` . Klik **toevoegen**.

![ WF Fusion ](./images/wffusion542.png)

Plaats het **type van Lichaam** aan **Onbewerkte**. Voor **inhoudstype**, uitgezochte **JSON (toepassing/json)**.

![ WF Fusion ](./images/wffusion55.png)

Plak deze nuttige lading in het **inhoud van het Verzoek** gebied.

```json
{
  "numVariations": 1,
  "size": {
    "width": 2048,
    "height": 2048
  },
  "prompt": "Horses in a field",
  "promptBiasingLocaleCode": "en-US"
}
```

Controle checkbox voor **ontleed reactie**. Klik **OK**.

![ WF Fusion ](./images/wffusion56.png)

Klik **Looppas eens**.

![ WF Fusion ](./images/wffusion57.png)

Zodra uw scenario in werking is gesteld, zou u dit moeten zien.

![ WF Fusion ](./images/wffusion58.png)

Klik op **?** op het vierde knooppunt, HTTP, om het antwoord te zien. Er wordt een afbeeldingsbestand weergegeven in het antwoord.

![ WF Fusion ](./images/wffusion59.png)

Kopieer de URL van de afbeelding en open deze in een browservenster. Dan zou je iets als dit moeten zien:

![ WF Fusion ](./images/wffusion60.png)

Klik het **voorwerp van HTTP** met de rechtermuisknop aan en noem het aan **Firefly T2I** anders.

![ WF Fusion ](./images/wffusion62.png)

Klik **sparen** om uw veranderingen te bewaren.

![ WF Fusion ](./images/wffusion61.png)

## 1.2.2.2 Photoshop API gebruiken met Workfront Fusion

Klik het **moersleutelpictogram** tussen de knopen **plaats Token van de Drager** en **Firefly T2I**. Selecteer **een router** toevoegen.

![ WF Fusion ](./images/wffusion63.png)

Klik het **Firefly T2I** voorwerp met de rechtermuisknop aan en selecteer **Kloon**.

![ WF Fusion ](./images/wffusion64.png)

Sleep en laat vallen het gekloonde voorwerp dicht bij het **voorwerp van de Router**, en het zal auto-verbinden met de **Router**. Dan moet je dit hebben.

![ WF Fusion ](./images/wffusion65.png)

U hebt nu een identiek exemplaar gebaseerd op het **Firefly T2I** HTTP- verzoek. Sommige montages van de **Firefly T2I** HTTP- verzoek zijn gelijkaardig aan wat u met **Photoshop API** moet in wisselwerking staan, die een tijdspaarder is. U hoeft nu alleen de variabelen te wijzigen die niet gelijk zijn, zoals de aanvraag-URL en de payload.

Verander **URL** in `https://image.adobe.io/pie/psdService/text`.

![ WF Fusion ](./images/wffusion66.png)

Vervang de **inhoud van het Verzoek** door de hieronder nuttige lading:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/sevoi-psd.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-button",
        "text": {
          "content": "Click here"
        }
      },
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Buy this stuff"
        }
      }
    ]
  },
  "outputs": [
    {
      "storage": "azure",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/sevoi-psd-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
      "type": "vnd.adobe.photoshop",
      "overwrite": true
    }
  ]
}
```

![ WF Fusion ](./images/wffusion67.png)

Opdat dit **inhoud van het Verzoek** om behoorlijk te functioneren, zijn er sommige variabelen die ontbreken:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Ga terug naar uw eerste knoop, klik **initialiseert Constanten** en selecteer dan **punt** voor elk van deze variabelen toevoegen.

![ WF Fusion ](./images/wffusion69.png)

| Sleutel | Voorbeeldwaarde |
|:-------------:| :---------------:| 
| `AZURE_STORAGE_URL` | `https://vangeluw.blob.core.windows.net` |
| `AZURE_STORAGE_CONTAINER` | `vangeluw` |
| `AZURE_STORAGE_SAS_READ` | `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D` |
| `AZURE_STORAGE_SAS_WRITE` | `?sv=2023-01-03&st=2025-01-13T17%3A21%3A09Z&se=2025-01-14T17%3A21%3A09Z&sr=c&sp=racwl&sig=FD4m0YyyqUj%2B5T8YyTFJDi55RiTDC9xKtLTgW0CShps%3D` |

U kunt uw variabelen vinden door terug naar Postman te gaan, en uw **Variabelen van het Milieu** te openen.

![ Azure Opslag ](./../module1.1/images/az105.png)

Kopieer deze waarden naar Workfront Fusion en voeg een nieuw item toe voor elk van deze 4 variabelen.

Dan moet je dit hebben. Klik **OK**.

![ WF Fusion ](./images/wffusion68.png)

Daarna, ga terug naar het gekloonde verzoek van HTTP om de **inhoud van het Verzoek** bij te werken. U zult deze zwarte variabelen in de **inhoud van het Verzoek** opmerken, die de variabelen zijn u over van Postman kopieerde. U moet deze nu wijzigen in de variabelen die u zojuist hebt gedefinieerd in Workfront Fusion. Vervang elke variabele één door één door de zwarte tekst te schrappen en het te vervangen door de correcte variabele.

![ WF Fusion ](./images/wffusion70.png)

Er zijn 3 veranderingen in de **input** sectie aan te brengen.

![ WF Fusion ](./images/wffusion71.png)

Er zijn ook 3 verandering in de **output** sectie aan te brengen. Klik **OK**.

![ WF Fusion ](./images/wffusion72.png)

Klik de gekloonde knoop met de rechtermuisknop aan, en selecteer **anders noemen**. Verander de naam in **de Tekst van de Verandering van Photoshop**.

![ WF Fusion ](./images/wffusion73.png)

Dan moet je dit hebben.

![ WF Fusion ](./images/wffusion74.png)

Volgende Stap: [ 1.2.3.. ](./ex3.md)

[Terug naar module 1.2](./automation.md)

[Terug naar alle modules](./../../../overview.md)

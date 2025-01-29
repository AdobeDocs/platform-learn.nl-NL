---
title: Adobe-API's gebruiken in Workfront Fusion
description: Leer hoe u Adobe-API's kunt gebruiken in Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 23ebf8b4-3f16-474c-afe1-520d88331417
source-git-commit: e419f07dbef519d9cf2f0100878e4cc880ad5f94
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 0%

---

# Adobe-API&#39;s gebruiken in Workfront Fusion

Leer hoe u Adobe-API&#39;s kunt gebruiken in Workfront Fusion.

## Firefly Text To Image API gebruiken met Workfront Fusion

1. Plaats over de tweede **plaats veelvoudige variabelen** knoop en selecteer **+** om een andere module toe te voegen.

![ WF Fusion ](./images/wffusion48.png)

1. Onderzoek naar **http** en selecteer **HTTP**.

![ WF Fusion ](./images/wffusion49.png)

1. Selecteer **maak een verzoek**.

![ WF Fusion ](./images/wffusion50.png)

1. Selecteer deze variabelen:

- **URL**: `https://firefly-api.adobe.io/v3/images/generate`
- **Methode**: `POST`

1. Selecteer **toevoegen een kopbal**.

![ WF Fusion ](./images/wffusion51.png)

1. Voer de volgende kopteksten in:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `x-api-key` | opgeslagen variabele voor `CONST_client_id` |
| `Authorization` | `Bearer ` + de opgeslagen variabele voor `bearer_token` |
| `Content-Type` | `application/json` |
| `Accept` | `*/*` |

1. Voer de details in voor `x-api-key` . Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion52.png)

1. Selecteer **toevoegen een kopbal**.

![ WF Fusion ](./images/wffusion53.png)

1. Voer de details in voor `Authorization` . Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion54.png)

1. Selecteer **toevoegen een kopbal**. Voer de details in voor `Content-Type` . Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion541.png)

1. Selecteer **toevoegen een kopbal**. Voer de details in voor `Accept` . Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion542.png)

1. Plaats het **type van Lichaam** aan **Onbewerkte**. Voor **inhoudstype**, uitgezochte **JSON (toepassing/json)**.

![ WF Fusion ](./images/wffusion55.png)

1. Plak deze nuttige lading in het **inhoud van het Verzoek** gebied.

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

1. Controle de doos voor **ontleed reactie**. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion56.png)

1. Selecteer **Looppas eens**.

![ WF Fusion ](./images/wffusion57.png)

Het scherm moet er zo uitzien.

![ WF Fusion ](./images/wffusion58.png)

1. Wilt u de **selecteren?** op het vierde knooppunt, HTTP, om het antwoord te zien. Er wordt een afbeeldingsbestand weergegeven in het antwoord.

![ WF Fusion ](./images/wffusion59.png)

1. Kopieer de URL van de afbeelding en open deze in een browservenster. Uw scherm moet er als volgt uitzien:

![ WF Fusion ](./images/wffusion60.png)

1. Klik **HTTP** met de rechtermuisknop aan en noem aan **Firefly T2I** anders.

![ WF Fusion ](./images/wffusion62.png)

1. Selecteer **sparen** om uw veranderingen te bewaren.

![ WF Fusion ](./images/wffusion61.png)

## Photoshop API gebruiken met Workfront Fusion

1. Selecteer **moersleutel** tussen de knopen **plaats Token van de Drager** en **Firefly T2I**. Selecteer **een router** toevoegen.

![ WF Fusion ](./images/wffusion63.png)

1. Klik **Firefly T2I** voorwerp met de rechtermuisknop aan en selecteer **Kloon**.

![ WF Fusion ](./images/wffusion64.png)

1. Sleep en laat vallen het gekloonde voorwerp dicht bij **Router** voorwerp-het auto-verbindt met de **Router**. Uw scherm moet er als volgt uitzien:

![ WF Fusion ](./images/wffusion65.png)

U hebt nu een identiek exemplaar gebaseerd op het **Firefly T2I** HTTP- verzoek. Sommige montages van de **Firefly T2I** HTTP- verzoek zijn gelijkaardig aan wat u met **Photoshop API** moet in wisselwerking staan, die een tijdspaarder is. Nu, moet u slechts de variabelen veranderen die niet het zelfde, zoals verzoek URL en de lading zijn.

1. Verander **URL** in `https://image.adobe.io/pie/psdService/text`.

![ WF Fusion ](./images/wffusion66.png)

1. Vervang **inhoud van het Verzoek** door de hieronder nuttige lading:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-button-text",
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
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
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

1. Ga terug naar uw eerste knoop, uitgezochte **initialiseert Constanten** en kies dan **punt** voor elk van deze variabelen toevoegen.

![ WF Fusion ](./images/wffusion69.png)

| Sleutel | Voorbeeldwaarde |
|:-------------:| :---------------:| 
| `AZURE_STORAGE_URL` | `https://vangeluw.blob.core.windows.net` |
| `AZURE_STORAGE_CONTAINER` | `vangeluw` |
| `AZURE_STORAGE_SAS_READ` | `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D` |
| `AZURE_STORAGE_SAS_WRITE` | `?sv=2023-01-03&st=2025-01-13T17%3A21%3A09Z&se=2025-01-14T17%3A21%3A09Z&sr=c&sp=racwl&sig=FD4m0YyyqUj%2B5T8YyTFJDi55RiTDC9xKtLTgW0CShps%3D` |

U kunt uw variabelen vinden door terug naar Postman te gaan, en uw **Variabelen van het Milieu** te openen.

![ Azure Opslag ](./../module1.1/images/az105.png)

1. Kopieer deze waarden naar Workfront Fusion en voeg een nieuw item toe voor elk van deze 4 variabelen.

1. Het scherm moet er zo uitzien. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion68.png)

Daarna, ga terug naar het gekloonde verzoek van HTTP om de **inhoud van het Verzoek** bij te werken. Merk de zwarte variabelen in de **inhoud van het Verzoek** op, die de variabelen zijn u over van Postman kopieerde. U moet de variabelen wijzigen die u zojuist hebt gedefinieerd in Workfront Fusion. Vervang elke variabele één door één door de zwarte tekst te schrappen en het te vervangen door de correcte variabele.

![ WF Fusion ](./images/wffusion70.png)

1. Maak deze 3 veranderingen in de **input** sectie. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion71.png)

1. Maak deze 3 veranderingen in de **output** sectie. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion72.png)

1. Klik de gekloonde knoop met de rechtermuisknop aan, en selecteer **anders noemen**. Verander de naam in **de Tekst van de Verandering van Photoshop**.

![ WF Fusion ](./images/wffusion73.png)

Uw scherm moet er als volgt uitzien:

![ WF Fusion ](./images/wffusion74.png)

1. Selecteer **Looppas eens**.

![ WF Fusion ](./images/wffusion75.png)

1. Selecteer het **onderzoek** pictogram op de **knoop van de Tekst van de Verandering van Photoshop** om de reactie te zien. U moet een reactie hebben die er als volgt uitziet, met een koppeling naar een statusbestand.

![ WF Fusion ](./images/wffusion76.png)

1. Alvorens met de interactie van Photoshop API verder te gaan, maak de route aan de **Firefly T2I** knoop onbruikbaar om onnodige API vraag aan dat API eindpunt niet te verzenden. Selecteer het **moersleutelpictogram**, en selecteer dan **maak route** onbruikbaar.

![ WF Fusion ](./images/wffusion77.png)

Uw scherm moet er als volgt uitzien:

![ WF Fusion ](./images/wffusion78.png)

1. Daarna, voeg een andere **Vastgestelde veelvoudige variabelen** knoop toe.

![ WF Fusion ](./images/wffusion79.png)

1. Plaats het na de **knoop van de Tekst van de Verandering van Photoshop**.

![ WF Fusion ](./images/wffusion80.png)

1. Selecteer de **Vastgestelde veelvoudige variabelen** knoop, uitgezocht **punt** toevoegen. Selecteer de waarde van de variabele in het antwoord op de vorige aanvraag.

| Naam variabele | Waarde variabele |
|:-------------:| :---------------:| 
| `psdStatusUrl` | `data > _links > self > href` |

1. Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion81.png)

1. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion82.png)

1. Klik op de **knoop van de Tekst van de Verandering van Photoshop** met de rechtermuisknop aan en selecteer **Kloon**.

![ WF Fusion ](./images/wffusion83.png)

1. Sleep het gekloonde HTTP- verzoek na de **Vastgestelde veelvoudige variabelen** knoop die u enkel creeerde.

![ WF Fusion ](./images/wffusion83.png)

1. Klik met de rechtermuisknop op de gekloonde HTTP-aanvraag, selecteer **Naam wijzigen** en wijzig de naam in **Photoshop Check Status** .

![ WF Fusion ](./images/wffusion84.png)

1. Selecteer deze optie om de HTTP-aanvraag te openen. Verander URL zodat het verwijzingen de variabele die u in de vorige stap creeerde, en plaats de **Methode** aan **GET**.

![ WF Fusion ](./images/wffusion85.png)

1. Verwijder het **Lichaam** door de lege optie te selecteren.

![ WF Fusion ](./images/wffusion86.png)

1. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion87.png)

1. Selecteer **Looppas eens**.

![ WF Fusion ](./images/wffusion88.png)

Een reactie die het gebied **status** bevat, met status die aan **wordt geplaatst lopend** verschijnt. Het duurt een paar seconden voordat Photoshop het proces heeft voltooid.

![ WF Fusion ](./images/wffusion89.png)

Nu u weet dat de reactie iets meer tijd nodig heeft om te worden gebeëindigd, kan het een goed idee zijn om een tijdopnemer vóór deze HTTP- verzoek toe te voegen zodat het niet onmiddellijk loopt.

1. Selecteer de **knoop van Hulpmiddelen** en selecteer dan **Slaap**.

![ WF Fusion ](./images/wffusion90.png)

1. Plaats de **Slaap** knoop binnen tussen **vastgestelde veelvoudige variabelen** en **Status van de Controle van Photoshop**. Plaats de **Vertraging** aan **5** seconden. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion91.png)

Het scherm moet er zo uitzien. De uitdaging met de onderstaande configuratie is dat 5 seconden wachten genoeg kan zijn, maar misschien is het niet genoeg. In werkelijkheid, zou het beter zijn om een intelligentere oplossing zoals een do.. terwijl lijn te hebben die de status om de 5 seconden controleert tot de status **** wordt geëist. Dus je kunt zo&#39;n tactiek in de volgende stappen implementeren.

![ WF Fusion ](./images/wffusion92.png)

1. Selecteer het **moersleutelpictogram** binnen tussen **plaats veelvoudige variabelen** en **Slaap**. Selecteer **module** toevoegen.

![ WF Fusion ](./images/wffusion93.png)

1. Onderzoek naar `flow` en selecteer dan **de Controle van de Stroom**.

![ WF Fusion ](./images/wffusion94.png)

1. Selecteer **Repeater**.

![ WF Fusion ](./images/wffusion95.png)

1. Plaats **herhaalt** aan **20**. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion96.png)

1. Daarna, uitgezochte **+** op de **Status van de Controle van Photoshop** om een andere module toe te voegen.

![ WF Fusion ](./images/wffusion97.png)

1. Onderzoek naar **stroom** en selecteer **de Controle van de Stroom**.

![ WF Fusion ](./images/wffusion98.png)

1. Selecteer **de Samenvoegaar van de Serie**.

![ WF Fusion ](./images/wffusion99.png)

1. Plaats **Module van Source** aan **Repeater**. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion100.png)

Uw scherm moet er als volgt uitzien:

![ WF Fusion ](./images/wffusion101.png)

1. Selecteer het **moersleutelpictogram** en selecteer **een module** toevoegen.

![ WF Fusion ](./images/wffusion102.png)

1. Onderzoek naar **hulpmiddelen** en selecteer **Hulpmiddelen**.

![ WF Fusion ](./images/wffusion103.png)

1. Selecteer **krijgen veelvoudige variabelen**.

![ WF Fusion ](./images/wffusion104.png)

1. Selecteer **+ voeg punt** toe en plaats **Veranderlijke naam** aan `done`.

![ WF Fusion ](./images/wffusion105.png)

1. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion106.png)

1. Selecteer de **Vastgestelde veelvoudige variabelen** knoop die u vóór vormde. Om veranderlijk **te initialiseren gedaan**, moet u het aan `false` hier plaatsen. Selecteer **+ toevoegen punt**.

![ WF Fusion ](./images/wffusion107.png)

1. Gebruik `done` voor de **Veranderlijke naam**

1. Voor het instellen van de status is een booleaanse waarde nodig. Om de booleaanse waarde te vinden, selecteer **versnelling** en selecteer dan `false`. Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion108.png)

1. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion109.png)

1. Daarna, selecteer het **moersleutelpictogram** na **krijgt veelvoudige variabelen** knoop die u vormde.

![ WF Fusion ](./images/wffusion110.png)

1. Selecteer **Opstelling een filter**. U moet nu de waarde van veranderlijk controleren **gedaan**. Als die waarde aan **vals** wordt geplaatst, dan moet het volgende deel van de lijn worden uitgevoerd. Als de waarde aan **waar** wordt geplaatst, betekent het dat het proces reeds met succes heeft voltooid zodat is er geen behoefte om met het volgende deel van de lijn verder te gaan.

![ WF Fusion ](./images/wffusion111.png)

1. Voor het etiket, gebruik **zijn wij gedaan?**. Plaats de **Voorwaarde** gebruikend reeds bestaande variabele **gereed**, zou de exploitant aan **Gelijk aan** moeten worden geplaatst en de waarde zou de booleaanse variabele `false` moeten zijn. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion112.png)

1. Daarna, maak één of andere ruimte tussen de knopen **Status van de Controle van Photoshop** en **de aggregator van de Serie**. Dan, selecteer het **moersleutelpictogram** en selecteer **een router** toevoegen. U doet dit omdat er na het controleren van de status van het Photoshop-bestand twee paden moeten zijn. Als de status `succeeded` is, dan zou de variabele van **gedaan** aan `true` moeten worden geplaatst. Als de status niet gelijk is aan `succeeded` , moet de lus worden voortgezet. De router zal het mogelijk maken om dit te controleren en te plaatsen.

![ WF Fusion ](./images/wffusion113.png)

1. Na het toevoegen van de router, selecteer het **moersleutelpictogram** en selecteer **Opstelling een filter**.

![ WF Fusion ](./images/wffusion114.png)

1. Voor het etiket, gebruik **wij worden gedaan**. Plaats de **Voorwaarde** gebruikend de reactie van de **3} knoop van de Status van de Controle van Photoshop door het antwoordgebied te kiezen** data.outputs [] .status **, zou de exploitant aan** Gelijk aan **moeten worden geplaatst en de waarde zou `succeeded` moeten zijn.** Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion115.png)

1. Daarna, selecteer de lege knoop met het vraagteken en onderzoek naar **hulpmiddelen**. Dan, selecteer **Hulpmiddelen**.

![ WF Fusion ](./images/wffusion116.png)

1. Selecteer **Vastgestelde veelvoudige variabelen**.

![ WF Fusion ](./images/wffusion117.png)

1. Wanneer deze tak van de router wordt gebruikt, betekent het de status van het het dossierverwezenlijking van Photoshop met succes heeft voltooid. Dit betekent dat de lus do.. while niet langer de status in Photoshop hoeft te controleren, dus u moet de variabele `done` instellen op `true` .

1. Voor de **naam van de Variabele**, gebruik `done`.

1. Voor de **Variabele waarde**, zou u de booleaanse waarde `true` moeten gebruiken. Selecteer het **tandwiel** pictogram en selecteer dan `true`. Selecteer **toevoegen**.

![ WF Fusion ](./images/wffusion118.png)

1. Selecteer **O.K.**.

![ WF Fusion ](./images/wffusion119.png)

1. Daarna, klik de **Reeks veelvoudige variabelen** knoop met de rechtermuisknop aan u enkel creeerde en **Kloon** selecteert.

![ WF Fusion ](./images/wffusion120.png)

1. Sleep de gekloonde knoop zodat het met de **aggregator van de Serie** verbindt. Dan, klik de knoop met de rechtermuisknop aan en selecteer **anders noemen**, en verander de naam in `Placeholder End`.

![ WF Fusion ](./images/wffusion122.png)

1. Verwijder de bestaande variabele en selecteer **+ Punt toevoegen**. Voor de **Veranderlijke naam**, gebruik `placeholder`, voor de **Variabele waarde**, gebruik `end`. Selecteer **toevoegen** en dan selecteren **O.K.**.

![ WF Fusion ](./images/wffusion123.png)

1. Selecteer **sparen** om uw scenario te bewaren. Selecteer vervolgens   **Looppas eens**.

![ WF Fusion ](./images/wffusion124.png)

Uw scenario wordt dan uitgevoerd en zou met succes moeten beëindigen. Bericht dat doe...while lijn die u vormde het werk fijn. In de onderste looppas, kunt u zien dat de **Repeater** 20 keer liep die op de bel op **wordt gebaseerd Hulpmiddelen > krijgt veelvoudige variabelen** knoop. Na die knoop, vormde u een filter dat de status controleerde en slechts als de status niet gelijk was aan **succesvol**, werden de volgende knopen uitgevoerd. In deze looppas, liep het deel na de filter slechts eenmaal, omdat de status reeds **** in de eerste looppas werd succesvol.

![ WF Fusion ](./images/wffusion125.png)

1. U kunt het statuut van de verwezenlijking van uw nieuw dossier van Photoshop verifiëren door de bel op het **verzoek van HTTP van de Status van de Controle van Photoshop** te klikken en neer te boren aan het **status** gebied.

![ WF Fusion ](./images/wffusion126.png)

U hebt nu de basisversie van een herhaalbaar scenario gevormd dat een aantal stappen automatiseert. In de volgende oefening, zult u op dat herhalen door ingewikkeldheid toe te voegen.

## Volgende stappen

Ga naar [ automatisering van het Proces met de Fusie van Workfront ](./ex3.md){target="_blank"}

Ga terug naar [ Automating de Diensten van de Adobe Firefly ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

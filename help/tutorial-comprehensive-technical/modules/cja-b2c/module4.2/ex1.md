---
title: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - Maak uw Google Cloud Platform-account
description: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - Maak uw Google Cloud Platform-account
kt: 5342
doc-type: tutorial
exl-id: 6dbfb5a3-adc2-4818-8f79-bbb00e56fbdf
source-git-commit: d6f6423adbc8f0ce8e20e686ea9ffd9e80ebb147
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# 4.2.1 Start Google Cloud Platform

>[!NOTE]
>
>Hiervoor hebt u toegang nodig tot een Google Cloud Platform-omgeving. Als u nog geen toegang hebt tot GCP, maakt u een nieuw account met uw persoonlijke e-mailadres.

## 4.2.1.1 Waarom maakt u verbinding met Google BigQuery met Adobe Experience Platform om gegevens van Googles Analytics op te halen

Google Cloud Platform (GCP) is een pakket openbare cloudcomputingdiensten die door Google worden aangeboden. Het Google Cloud Platform bevat een reeks gehoste services voor computer-, opslag- en toepassingsontwikkeling die op Google-hardware worden uitgevoerd.

BigQuery is één van deze diensten en het is altijd inbegrepen met Googles Analytics 360. Gegevens van Googles Analytics worden vaak gesampled wanneer we proberen gegevens er direct van te krijgen (bijvoorbeeld API). Daarom bevat Google BigQuery om niet-gesamplede gegevens te verkrijgen, zodat merken geavanceerde analyses kunnen uitvoeren met SQL en kunnen profiteren van de kracht van GCP.

Gegevens van Googles Analytics worden dagelijks in BigQuery geladen via een batchmechanisme. Daarom heeft het geen zin om deze integratie van GCP/BigQuery te gebruiken voor realtime personalisatie en activeringsgebruiksgevallen.

Als een merk gebruiksgevallen voor realtime personalisatie wil aanbieden op basis van gegevens van Googles Analytics, kan het die gegevens verzamelen op de website met Google Tag Manager en deze vervolgens in real-time naar Adobe Experience Platform streamen.

De connector GCP/BigQuery Source moet worden gebruikt voor...

- Volg al klantengedrag op de website en laad die gegevens in Adobe Experience Platform voor analyse, gegevenswetenschap en verpersoonlijking gebruiksgevallen die geen activering in real time vereisen.
- historische gegevens van Googles Analytics naar Adobe Experience Platform laden, ook voor gebruik in analysen en gegevenswetenschappen

## 4.2.1.2 Uw Google-account

>[!NOTE]
>
>Hiervoor hebt u toegang nodig tot een Google Cloud Platform-omgeving. Als u nog geen toegang hebt tot GCP, maakt u een nieuw account met uw persoonlijke e-mailadres.

## 4.2.1.3 Een project selecteren of maken

Ga naar [&#x200B; https://console.cloud.google.com/ &#x200B;](https://console.cloud.google.com/).

Daarna, klik op **selecteer een project** of klik een bestaand project.

![&#x200B; demo &#x200B;](./images/ex12.png)

Als u nog geen project hebt, klik op **NIEUW PROJECT**. Als u al een project hebt, kunt u ervoor kiezen om dat te selecteren en door te gaan naar de volgende stap.

![&#x200B; demo &#x200B;](./images/ex1createproject.png)

Geef uw project een naam volgens deze naamgevingsconventie. Klik **CREËREN**.

| Conventie |
| ----------------- |
| `--aepUserLdap---googlecloud` |

![&#x200B; demo &#x200B;](./images/ex13.png)

Wacht tot het bericht in de rechterbovenhoek van het scherm u vertelt dat het maken is voltooid. Dan, klik **UITGEZOCHT PROJECT**.

![&#x200B; demo &#x200B;](./images/ex14.png)

Daarna, ga naar de onderzoeksbar bovenop het scherm en type **BigQuery**. Selecteer het eerste resultaat.

![&#x200B; demo &#x200B;](./images/ex17.png)

Het doel van deze module is om gegevens van Googles Analytics in Adobe Experience Platform te krijgen. Om dat te doen, hebt u dummygegevens in een dataset van Googles Analytics nodig om met te beginnen.

Klik op **+ voeg** toe, en klik dan **Openbare datasets** in het juiste menu.

![&#x200B; demo &#x200B;](./images/ex118.png)

U ziet dan dit venster:

![&#x200B; demo &#x200B;](./images/ex119.png)

Ga de steekproef van de Googles Analytics van de onderzoekstermijn **&#x200B;**&#x200B;in de onderzoeksbar in en klik het eerste onderzoeksresultaat.

![&#x200B; demo &#x200B;](./images/ex120.png)

U zult het volgende scherm met een beschrijving van de dataset zien. Klik op **DATASET VAN DE MENING**.

![&#x200B; demo &#x200B;](./images/ex121.png)

U zult dan aan BigQuery opnieuw worden gericht waar u dit **bigquery-public-data** dataset onder **Ontdekkingsreiziger** zult zien.

![&#x200B; demo &#x200B;](./images/ex122a.png)

In **Ontdekkingsreiziger**, zou u een aantal lijsten nu moeten zien. Voel je vrij om ze te verkennen. Ga naar `google_analytics_sample` .

![&#x200B; demo &#x200B;](./images/ex122.png)

Klik om de tabel te openen `ga_sessions` .

![&#x200B; demo &#x200B;](./images/ex123.png)

Voordat u verdergaat met de volgende oefening, noteer gelieve de volgende dingen in een afzonderlijk tekstdossier op uw computer:

| Credentials | Naamgeving | Voorbeeld |
| ----------------- |-------------| -------------|
| Projectnaam | `--aepUserLdap---googlecloud` | vangeluw-googlecloud |
| Project-id | random | mogelijk-bijen-447102-h3 |

U kunt uw Naam van het Project en identiteitskaart van het Project vinden door op uw **Naam van het Project** in de hoogste menubar te klikken:

![&#x200B; demo &#x200B;](./images/ex1projectMenu.png)

U ziet dan uw project-id aan de rechterkant:

![&#x200B; demo &#x200B;](./images/ex1projetcselection.png)

Je kunt nu naar de volgende oefening gaan waar je handen vuil wordt door de gegevens van Googles Analytics te vragen.

Volgende Stap: [&#x200B; 4.2.2 leidt tot uw eerste vraag in BigQuery &#x200B;](./ex2.md)

[Terug naar module 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Terug naar alle modules](./../../../overview.md)

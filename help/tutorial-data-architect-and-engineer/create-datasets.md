---
title: Gegevenssets maken
seo-title: Create datasets | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Gegevenssets maken
description: In deze les, zult u datasets creëren om uw gegevens te ontvangen.
role: Data Architect, Data Engineer
feature: Data Management
jira: KT-4348
thumbnail: 4348-create-datasets.jpg
exl-id: 80227af7-4976-4fd2-b1d4-b26bc4626fa0
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Gegevenssets maken

<!--15min-->

In deze les, zult u datasets creëren om uw gegevens te ontvangen. U zult blij zijn om te weten dat dit de kortste les in de zelfstudie is!

Alle gegevens die met succes in Adobe Experience Platform worden opgenomen, blijven in het gegevensmeer als datasets bestaan. Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens, typisch een lijst, die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan.

**Architecten van Gegevens** zullen datasets buiten dit leerprogramma moeten tot stand brengen.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over gegevenssets:
>[!VIDEO](https://video.tv.adobe.com/v/27269?learn=on&enablevpops)

## Vereiste machtigingen

In [&#x200B; vorm toestemmingen &#x200B;](configure-permissions.md) les, u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Gegevenssets maken in de gebruikersinterface

In deze oefening, zullen wij datasets in UI creëren. Laten we beginnen met de loyaliteitsgegevens:

1. Ga naar **[!UICONTROL Datasets]** in de linkernavigatie van de gebruikersinterface van Platform
1. Selecteer de knop **[!UICONTROL Create dataset]**
   ![&#x200B; creeer een dataset &#x200B;](assets/datasets-createDataset.png)

1. Voor het volgende scherm, creeer **dataset van schema**
1. Selecteer in het volgende scherm de `Luma Loyalty Schema` -toets en selecteer vervolgens de **[!UICONTROL Next]** -knop
   ![&#x200B; selecteer de dataset &#x200B;](assets/datasets-selectSchema.png)

1. Geef de gegevensset een naam `Luma Loyalty Dataset` en selecteer de knop **[!UICONTROL Finish]** .
   ![&#x200B; Naam de dataset &#x200B;](assets/datasets-nameDataset.png)
1. Wanneer de dataset heeft bewaard, zult u aan een scherm als dit worden genomen:
   ![&#x200B; gecreeerde Dataset &#x200B;](assets/datasets-created.png)

Dat is het! Ik vertelde je dat dit snel zou gaan. Creeer deze andere datasets gebruikend de zelfde stappen:

1. `Luma Offline Purchase Events Dataset` voor uw `Luma Offline Purchase Events Schema`
1. `Luma Web Events Dataset` voor uw `Luma Web Events Schema`
1. `Luma Product Catalog Dataset` voor uw `Luma Product Catalog Schema`


## Een gegevensset maken met behulp van API

Maak nu de `Luma CRM Dataset` met behulp van de API.

>[!NOTE]
>
>Als u de API-oefening wilt overslaan en de `Luma CRM Dataset` in de gebruikersinterface wilt maken die prima is. Noem het `Luma CRM Dataset` en gebruik `Luma CRM Schema`.

### Krijg identiteitskaart van het schema dat in de dataset moet worden gebruikt

Eerst moeten we de `$id` van de `Luma CRM Schema` ophalen:

1. Openen [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteer **verzend** om een nieuw toegangstoken aan te vragen, enkel zoals u in de [!DNL Postman] les deed.
1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Selecteer **verzenden** knoop
1. Je moet 200 reacties krijgen
1. Zoek in het antwoord op het item `Luma CRM Schema` en kopieer de waarde `$id` .
   ![&#x200B; Exemplaar $id &#x200B;](assets/dataset-crm-getSchemaId.png)

### De gegevensset maken

Nu kunt u de dataset tot stand brengen:

1. De dienst API.postman_collection.json van de Catalogus van de download [&#128279;](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Catalog%20Service%20API.postman_collection.json) aan uw `Luma Tutorial Assets` omslag.
1. De verzameling importeren in [!DNL Postman]
1. Selecteer de aanvraag **[!DNL Catalog Service API > Datasets > Create a new dataset.]**
1. Plak het volgende als **Lichaam** van het verzoek, ***die de waarde van identiteitskaart met uw vervangen***:

   ```json
   {
       "name": "Luma CRM Dataset",
   
       "schemaRef": {
           "id": "REPLACE_WITH_YOUR_OWN_ID",
           "contentType": "application/vnd.adobe.xed-full+json;version=1"
       },
       "fileDescription": {
           "persisted": true,
           "containerFormat": "parquet",
           "format": "parquet"
       }
   }
   ```

1. Selecteer **verzenden** knoop
1. U zou 201 moeten krijgen leidde reactie die identiteitskaart van uw nieuwe dataset bevat!
   ![&#x200B; Dataset die met API wordt gecreeerd, uw douane $id die in het lichaam &#x200B;](assets/datasets-crm-created.png) wordt gebruikt

>[!TIP]
>
> Gemeenschappelijke kwesties die dit verzoek indienen en waarschijnlijk oplossen:
>
> * `400: There was a problem retrieving xdm schema`. Controleer of u de id in het bovenstaande voorbeeld hebt vervangen door de id van uw eigen id `Luma CRM Schema`
> * Geen autetoken: stel **OAuth in werking: Verzoek om Token van de Toegang** verzoek om een nieuw token te produceren
> * `401: Not Authorized to PUT/POST/PATCH/DELETE for this path : /global/schemas/`: Werk **CONTAINER_ID** milieu variabele van `global` aan `tenant` bij
> * `403: PALM Access Denied. POST access is denied for this resource from access control`: controleer uw gebruikersmachtigingen in de Admin Console


U kunt terug naar het **[!UICONTROL Datasets]** scherm in het gebruikersinterface van het Platform gaan, kunt u de succesvolle verwezenlijking van alle vijf datasets verifiëren!
![&#x200B; Vijf datasets volledig &#x200B;](assets/datasets-allComplete.png)


## Aanvullende bronnen

* [&#x200B; documentatie van Datasets &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=nl-NL)
* [&#x200B; Datasets API (deel van de Dienst van de Catalogus) verwijzing &#x200B;](https://www.adobe.io/experience-platform-apis/references/catalog/#tag/Datasets)

Nu al onze schema&#39;s, identiteiten, en datasets op zijn plaats zijn, kunnen wij [&#x200B; hen voor het Profiel van de Klant in real time &#x200B;](enable-profiles.md) toelaten.

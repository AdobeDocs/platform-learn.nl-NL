---
title: Gegevens van groep samenvoegen
seo-title: Ingest batch data | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Gegevens van groep samenvoegen
description: In deze les, zult u partijgegevens in Experience Platform opnemen gebruikend diverse methodes.
role: Data Engineer
feature: Data Ingestion
jira: KT-4348
thumbnail: 4348-ingest-batch-data.jpg
exl-id: fc7db637-e191-4cc7-9eec-29f4922ae127
source-git-commit: adbe8f4476340abddebbf9231e3dde44ba328063
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 0%

---

# Gegevens van groep samenvoegen

<!-- 1hr-->
In deze les, zult u partijgegevens in Experience Platform opnemen gebruikend diverse methodes.

Met gegevensinvoer via batch kunt u een grote hoeveelheid gegevens tegelijk in Adobe Experience Platform innemen. U kunt batchgegevens invoeren in één keer uploaden binnen de interface van het Platform of met de API. U kunt regelmatig geplande batch-uploads van de derdediensten zoals de diensten van de wolkenopslag ook vormen gebruikend Bron schakelaars.

**Gegevensengineers** moet u batchgegevens buiten deze zelfstudie invoeren.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over gegevensinvoer:

>[!VIDEO](https://video.tv.adobe.com/v/27106?quality=12&learn=on)


## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission item **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]**, **[!UICONTROL Manage Datasets]** and **[!UICONTROL Data Monitoring]**
* Permission items **[!UICONTROL Data Ingestion]** > **[!UICONTROL View Sources]** and **[!UICONTROL Manage Sources]**
* Permission item **[!UICONTROL Profile Management]** > **[!UICONTROL View Profiles]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

Voor de Bronenoefening hebt u toegang nodig tot een (S)FTP-server of cloudopslagoplossing. Er is een oplossing als u er geen hebt.

## Gegevens batchgewijs samenvoegen met gebruikersinterface van Platform

De gegevens kunnen direct in een dataset op het datasetscherm in JSON en parquet formaten worden geupload. Dit is een goede manier om inname van sommige gegevens te testen nadat u een

### Gegevens downloaden en voorbereiden

Eerst, krijg de steekproefgegevens en pas het voor uw huurder aan:

>[!NOTE]
>
>Gegevens in de [luma-data.zip](assets/luma-data.zip) het bestand is fictief en mag alleen voor demonstratiedoeleinden worden gebruikt.

1. Downloaden [luma-data.zip](assets/luma-data.zip) aan uw **Luminantieleidingselementen** map.
1. Pak het bestand uit en maak een map met de naam `luma-data` die de vier gegevensbestanden bevat die we in deze les zullen gebruiken
1. Openen `luma-loyalty.json` in een teksteditor en vervang alle instanties van `_techmarketingdemos` met uw eigen underscore-huurder identiteitskaart, zoals die in uw eigen schema&#39;s wordt gezien:
   ![Onderstrepingshuurder-id](assets/ingestion-underscoreTenant.png)

1. Het bijgewerkte bestand opslaan

### De gegevens samenvoegen

1. Selecteer in de gebruikersinterface van het Platform de optie **[!UICONTROL Gegevenssets]** in de linkernavigatie
1. Open uw `Luma Loyalty Dataset`
1. Schuif omlaag totdat u de **[!UICONTROL Gegevens toevoegen]** in de rechterkolom
1. Upload de `luma-loyalty.json` bestand.
1. Wanneer het bestand is geüpload, wordt een rij voor de batch weergegeven
1. Als u de pagina na een paar minuten opnieuw laadt, ziet u dat de batch is geüpload met 1000 records en 1000 profielfragmenten.

   ![Inname](assets/ingestion-loyalty-uploadJson.png)
   <!--do i need to explain error diagnostics and partial ingestion-->

>[!NOTE]
>
>Er zijn een paar opties. **[!UICONTROL Foutdiagnostiek]** en **[!UICONTROL Gedeeltelijke inname]**, die u op verschillende schermen in deze les zult zien. Deze opties worden niet behandeld in de zelfstudie. Enkele snelle informatie:
>
>* Als u foutdiagnostiek inschakelt, worden gegevens over de inname van uw gegevens gegenereerd. U kunt deze gegevens vervolgens controleren met de API voor gegevenstoegang. Meer informatie hierover vindt u in [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html).
>* Gedeeltelijke invoer maakt het mogelijk gegevens met fouten in te voeren, tot een bepaalde drempel die u kunt opgeven. Meer informatie hierover vindt u in [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/partial.html)

### De gegevens valideren

Er zijn een paar manieren om te bevestigen dat de gegevens met succes werden opgenomen.

#### Valideren in de gebruikersinterface van het Platform

Om te bevestigen dat de gegevens in de dataset werden opgenomen:

1. Selecteer op dezelfde pagina waar u de gegevens hebt ingevoerd de optie **[!UICONTROL Gegevensset voorvertoning]** knop rechtsboven
1. Selecteer **Voorvertoning** en u zou sommige ingebedde gegevens moeten kunnen zien.

   ![Een voorvertoning weergeven van de voltooide gegevensset](assets/ingestion-loyalty-preview.png)


Om te bevestigen dat de in Profiel aangelande gegevens (kan een paar minuten duren voor de gegevens aan land zijn):

1. Ga naar **[!UICONTROL Profielen]** in de linkernavigatie
1. Selecteer het pictogram naast **[!UICONTROL Naamruimte selecteren]** veld om het modale
1. Selecteer uw `Luma Loyalty Id` namespace
1. Voer vervolgens een van de `loyaltyId` waarden uit uw gegevensset,  `5625458`
1. Selecteren **[!UICONTROL Weergave]**
   ![Een profiel uit de gegevensset bevestigen](assets/ingestion-loyalty-profile.png)

#### Valideren met gebeurtenissen voor gegevensinvoer

Als u zich in de vorige les hebt geabonneerd op gegevensinsluitingsgebeurtenissen, controleert u de unieke URL van website.site. U zou drie verzoeken moeten zien verschijnen in de volgende orde, met wat tijd tussen hen, met het volgende: `eventCode` waarden:

1. `ing_load_success`—de partij als ingeslikt
1. `ig_load_success`—de batch is in de identiteitsgrafiek opgenomen
1. `ps_load_success`—de batch is in de profielservice opgenomen

![Gegevensopname-webhaak](assets/ingestion-loyalty-webhook.png)

Zie de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/quality/subscribe-events.html#available-status-notification-events) voor meer informatie over de kennisgevingen .

## Gegevens batchgewijs samenvoegen met Platform-API

Laten we nu gegevens uploaden met behulp van de API.

>[!NOTE]
>
>Gegevensarchitecten kunnen de CRM-gegevens gratis uploaden via de gebruikersinterfacemethode.

### Gegevens downloaden en voorbereiden

1. U had al gedownload en gedecomprimeerd moeten zijn [luma-data.zip](assets/luma-data.zip) in uw `Luma Tutorial Assets` map.
2. Openen `luma-crm.json` in een teksteditor en vervang alle instanties van `_techmarketingdemos` met uw eigen underscore-huurder-id, zoals die in uw schema&#39;s wordt gezien
3. Het bijgewerkte bestand opslaan

### Hiermee wordt de gegevensset-id opgehaald

Eerst krijgen wij identiteitskaart van dataset identiteitskaart van de dataset waarin wij gegevens willen opnemen:

1. Open [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteert u **Verzenden** om een nieuw toegangstoken aan te vragen, enkel zoals u in [!DNL Postman] les.
1. Open uw omgevingsvariabelen en zorg ervoor dat de waarde van **CONTAINER_ID** nog steeds `tenant`
1. De aanvraag openen **[!DNL Catalog Service API > Datasets > Retrieve a list of datasets.]** en selecteert u **Verzenden**
1. U moet een `200 OK` reactie
1. De id van het dialoogvenster kopiëren `Luma CRM Dataset` van het responsorgaan
   ![Hiermee wordt de gegevensset-id opgehaald](assets/ingestion-crm-getDatasetId.png)

### De batch maken

Nu kunnen wij een partij in de dataset tot stand brengen:

1. Downloaden [Gegevensinname API.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Data%20Ingestion%20API.postman_collection.json) aan uw `Luma Tutorial Assets` map
1. De verzameling importeren in [!DNL Postman]
1. Selecteer de aanvraag **[!DNL Data Ingestion API > Batch Ingestion > Create a new batch in Catalog Service.]**
1. Plak het volgende als de **Lichaam** van het verzoek, ***het vervangen van de waarde datasetId met uw eigen***:

   ```json
   {
       "datasetId":"REPLACE_WITH_YOUR_OWN_DATASETID",
       "inputFormat": {
           "format": "json"
       }
   }
   ```

1. Selecteer **Verzenden** knop
1. Er moet een 201 Created-reactie komen met de id van de nieuwe batch!
1. Kopieer de `id` van de nieuwe partij
   ![Batch gemaakt](assets/ingestion-crm-createBatch.png)

### De gegevens samenvoegen

Nu kunnen we de gegevens uploaden naar de batch:

1. Selecteer de aanvraag **[!DNL Data Ingestion API > Batch Ingestion > Upload a file to a dataset in a batch.]**
1. In de **Params** tabblad, voert u de id van uw gegevensset en batch-id in de desbetreffende velden in
1. In de **Params** tab, enter `luma-crm.json` als de **filePath**
1. In de **Lichaam** selecteert u de **binair** option
1. Selecteer gedownloade `luma-crm.json` van uw lokale `Luma Tutorial Assets` map
1. Selecteren **Verzenden** en u zou een 200 O.K. reactie met &quot;1&quot;in het reactievermogen moeten krijgen

   ![Geüploade gegevens](assets/ingestion-crm-uploadFile.png)

Op dit punt, als u uw partij in het gebruikersinterface van het Platform bekijkt, zult u zien dat het in &quot;[!UICONTROL Laden]&quot; status:
![Batch laden](assets/ingestion-crm-loading.png)

Omdat de batch-API vaak wordt gebruikt om meerdere bestanden te uploaden, moet u het Platform op de hoogte stellen wanneer een batch voltooid is. Dat zullen we in de volgende stap doen.

### De batch voltooien

De batch voltooien:

1. Selecteer de aanvraag **[!DNL Data Ingestion API > Batch Ingestion > Finish uploading a file to a dataset in a batch.]**
1. In de **Params** tab, enter `COMPLETE` als de **action**
1. In de **Params** voert u de batch-id in. Maak zich geen zorgen over dataset id of filePath, als zij aanwezig zijn.
1. Controleer of de URL van de POST `https://platform.adobe.io/data/foundation/import/batches/:batchId?action=COMPLETE` en dat er geen onnodige verwijzingen naar `datasetId` of `filePath`
1. Selecteren **Verzenden** en u zou een 200 O.K. reactie met &quot;1&quot;in het reactievermogen moeten krijgen

   ![Batch voltooid](assets/ingestion-crm-complete.png)

### De gegevens valideren

#### Valideren in de gebruikersinterface van het Platform

Bevestig de gegevens in het gebruikersinterface van het Platform enkel zoals u voor de dataset van de Loyalty hebt geland.

Bevestig eerst de batch waaruit blijkt dat er 1000 records zijn ingeslikt:

![Batch-succes](assets/ingestion-crm-success.png)

Bevestig vervolgens de batch met de gegevensset Voorvertoning:

![Batchvoorvertoning](assets/ingestion-crm-preview.png)

Ten slotte kunt u bevestigen dat een van uw profielen is gemaakt door een van de profielen op te zoeken door de `Luma CRM Id` naamruimte, bijvoorbeeld `112ca06ed53d3db37e4cea49cc45b71e`

![Profiel toegevoegd](assets/ingestion-crm-profile.png)

Er is één interessant ding dat zojuist is gebeurd en waarop ik wil wijzen. Open `Danny Wright` profiel. Het profiel heeft een `Lumacrmid` en `Lumaloyaltyid`. Onthoud de `Luma Loyalty Schema` bevatte twee identiteitsgebieden, Luma Loyalty ID en CRM Identiteitskaart Nu we beide gegevenssets hebben geüpload, zijn ze samengevoegd tot één profiel. De Loyalty-gegevens hadden `Daniel` als voornaam en &quot;New York City&quot; als huisadres, terwijl de CRM-gegevens `Danny` als voornaam en `Portland` als het huisadres voor de klant met zelfde identiteitskaart van de Loyalty. We zullen terugkomen op de reden waarom de voornaam wordt weergegeven `Danny` in de les over samenvoegingsbeleid.

U hebt zojuist profielen samengevoegd.

![Profiel samengevoegd ](assets/ingestion-crm-profileLinkedIdentities.png)

#### Valideren met gebeurtenissen voor gegevensinvoer

Als u zich in de vorige les hebt geabonneerd op gegevensinsluitingsgebeurtenissen, controleert u de unieke URL van website.site. U zou drie verzoeken moeten zien binnen komen, enkel zoals met de loyaliteitsgegevens:

![Gegevensopname-webhaak](assets/ingestion-crm-webhook.png)

Zie de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/quality/subscribe-events.html#available-status-notification-events) voor meer informatie over de kennisgevingen .

## Gegevens samenvoegen met workflows

Laten we eens kijken naar een andere manier om gegevens te uploaden. Met de workflows kunt u CSV-gegevens invoeren die nog niet in XDM zijn gemodelleerd.

### Gegevens downloaden en voorbereiden

1. U had al gedownload en gedecomprimeerd moeten zijn [luma-data.zip](assets/luma-data.zip) in uw `Luma Tutorial Assets` map.
1. Bevestig dat u`luma-products.csv`

### Een workflow maken

Laten we nu een workflow instellen:

1. Ga naar **[!UICONTROL Workflows]** in de linkernavigatie
1. Selecteren **[!UICONTROL CSV toewijzen aan XDM-schema]** en selecteert u de **[!UICONTROL Starten]** knop
   ![De workflow starten](assets/ingestion-products-launchWorkflow.png)
1. Selecteer uw `Luma Product Catalog Dataset` en selecteert u de **[!UICONTROL Volgende]** knop
   ![Uw gegevensset selecteren](assets/ingestion-products-selectDataset.png)
1. Voeg de `luma-products.csv` bestand dat u hebt gedownload en selecteer **[!UICONTROL Volgende]** knop
   ![Uw gegevensset selecteren](assets/ingestion-products-selectData.png)
1. Nu bevindt u zich in de mapperinterface, waarin u een veld kunt toewijzen vanuit de brongegevens (een van de kolomnamen in het dialoogvenster `luma-products.csv` bestand) naar XDM-velden in het doelschema. In ons voorbeeld, zijn de kolomnamen dicht genoeg aan de namen van het schemagebied dat mapper de juiste afbeelding kan auto-ontdekken! Als de mapper het juiste veld niet automatisch kan detecteren, selecteert u het pictogram rechts van het doelveld om het juiste XDM-veld te selecteren. Ook, als u niet één van de kolommen van CSV wilt opnemen, kon u de rij van mapper schrappen. Voel u vrij om rond te spelen en kolomrubrieken in te veranderen `luma-products.csv` om vertrouwd te raken met hoe de mapper werkt.
1. Selecteer **[!UICONTROL Voltooien]** knop
   ![Uw gegevensset selecteren](assets/ingestion-products-mapper.png)

### De gegevens valideren

Wanneer de partij heeft geupload, verifieer upload door de dataset te bekijken.

Aangezien `Luma Product SKU` is een naamruimte zonder personen. Er worden geen profielen voor de productskus weergegeven.

Je moet de drie hits op je website zien.

## Gegevens samenvoegen met bronnen

Oké, je deed dingen op de moeilijke manier. Laten we nu het beloofde land van _geautomatiseerd_ batch-opname! Als ik zeg: &quot;SET IT!&quot; je zegt: &quot;VERGEET HET!&quot; &quot;SET IT!&quot; &quot;VERGEET HET!&quot; &quot;SET IT!&quot; &quot;VERGEET HET!&quot; Grapje, je zou zoiets nooit doen! Oké, weer aan het werk. Je bent bijna klaar.

Ga naar **[!UICONTROL Bronnen]** in de linkernavigatie om de Broncatalogus te openen. Hier ziet u verschillende kant-en-klare integraties met toonaangevende gegevens- en opslagproviders.

![Broncatalogus](assets/ingestion-offline-sourceCatalog.png)

Oké, we nemen gegevens in met een bronaansluiting.

Deze oefening zal kiezen-uw-eigen-avontuurstijl zijn. Ik ga het werkschema tonen gebruikend de bron van FTP schakelaar. U kunt of een verschillende Bron van de Opslag van de Wolk gebruiken die u bij uw bedrijf gebruikt, of het JSON dossier uploaden gebruikend het gegevenssetgebruikersinterface zoals wij met de loyaliteitsgegevens deden.

Veel van de Bronnen hebben een gelijkaardige configuratiewerkschema, waarin u:

1. Voer uw verificatiegegevens in
1. Selecteer de gegevens die u wilt invoeren
1. Selecteer de dataset van het Platform waarin u het wilt opnemen
1. De velden toewijzen aan uw XDM-schema
1. Kies de frequentie waarmee u gegevens van die plaats wilt opnieuw opnemen

>[!NOTE]
>
>De gegevens voor offline aanschaf die we in deze exercitie gebruiken, bevatten gegevens over datumtijd. Datumtijdgegevens moeten in een van beide staan [Tekenreeksen met ISO 8061-indeling](https://www.iso.org/iso-8601-date-and-time-format.html) (&quot;2018-07-10T15&quot;):05:59,000-08:00&quot;) of Unix Tijd die in milliseconden (1531263959000) wordt geformatteerd en bij inname in het doelXDM type wordt omgezet. Voor meer informatie over gegevensconversie en andere beperkingen raadpleegt u [de documentatie van de API voor batchverwerking](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/api-overview.html#types).

### Download, prep en upload de gegevens naar de voorkeursleverancier voor cloudopslag

1. U had al gedownload en gedecomprimeerd moeten zijn [luma-data.zip](assets/luma-data.zip) in uw `Luma Tutorial Assets` map.
1. Openen `luma-offline-purchases.json` in een teksteditor en vervang alle instanties van `_techmarketingdemos` met uw eigen underscore-huurder-id, zoals die in uw schema&#39;s wordt gezien
1. Werk alle tijdstempels bij zodat de gebeurtenissen in de laatste maand voorkomen (bijvoorbeeld, onderzoek naar `"timestamp":"2022-06` en vervang het jaar en de maand)
1. Kies uw voorkeursleverancier voor cloudopslag, zodat deze beschikbaar is in het dialoogvenster [!UICONTROL Bronnen] catalogus
1. Uploaden `luma-offline-purchases.json` naar een locatie in uw voorkeursprovider voor cloudopslag

### Vermeld de gegevens naar de gewenste locatie voor cloudopslag

1. In het gebruikersinterface van het Platform, filter [!UICONTROL Bronnen] catalogus naar **[!UICONTROL Cloud-opslag]**
1. Er zijn handige koppelingen naar documentatie onder de `...`
1. Selecteer in het vak van uw voorkeursleverancier voor cloudopslag de optie **[!UICONTROL Configureren]** knop
   ![Configureer](assets/ingestion-offline-selectFTP.png)
1. **[!UICONTROL Verificatie]** is de eerste stap. Voer bijvoorbeeld de naam van uw account in `Luma's FTP Account` en uw verificatiegegevens. Deze stap zou voor alle bronnen van de wolkenopslag vrij gelijkaardig moeten zijn, hoewel de gebieden lichtjes kunnen variëren. Zodra u de authentificatiedetails voor een rekening hebt ingegaan, kunt u hen voor andere bronverbindingen opnieuw gebruiken die verschillende gegevens over verschillende programma&#39;s van andere dossiers in de zelfde rekening zouden kunnen verzenden
1. Selecteer **[!UICONTROL Verbinding maken met bronknop]**
1. Wanneer het Platform met succes met de Bron heeft verbonden, selecteer **[!UICONTROL Volgende]** knop
   ![Verifiëren voor de bron](assets/ingestion-offline-authentication.png)

1. Op de **[!UICONTROL Gegevens selecteren]** stap, gebruikt de gebruikersinterface uw gegevens om de map op uw cloudopslagoplossing te openen
1. Selecteer de bestanden die u wilt invoeren, bijvoorbeeld `luma-offline-purchases.json`
1. Als de **[!UICONTROL Gegevensindeling]**, selecteert u `XDM JSON`
1. U kunt dan een voorbeeld van de verbindingsstructuur en voorbeeldgegevens in uw bestand bekijken
1. Selecteer **[!UICONTROL Volgende]** knop
   ![Gegevensbestand(en) selecteren](assets/ingestion-offline-selectData.png)

1. Op de **[!UICONTROL Toewijzing]** stap, selecteer uw `Luma Offline Purchase Events Dataset` en selecteert u de **[!UICONTROL Volgende]** knop. Let op: aangezien de gegevens die we invoeren een JSON-bestand zijn, is er geen toewijzingsstap waarin we het bronveld aan het doelveld toewijzen. JSON-gegevens moeten zich al in XDM bevinden. Als u een CSV opnam, zou u de volledige kaartgebruiker interface op deze stap zien:
   ![Uw gegevensset selecteren](assets/ingestion-offline-mapping.png)
1. Op de **[!UICONTROL Planning]** kiest u de frequentie waarmee u gegevens uit de bron opnieuw wilt opnemen. Neem even de tijd om naar de opties te kijken. We gaan gewoon een eenmalige opname doen, dus laten we de **[!UICONTROL Frequentie]** op **[!UICONTROL Eenmaal]** en selecteert u de **[!UICONTROL Volgende]** knop:
   ![Uw gegevensstroom plannen](assets/ingestion-offline-scheduling.png)
1. Op de **[!UICONTROL Gegevens]** stap, kunt u een naam voor uw gegevensstroom kiezen, een facultatieve beschrijving ingaan, fout diagnostiek, en gedeeltelijke opname aanzetten. Laat de instellingen ongewijzigd en selecteer de **[!UICONTROL Volgende]** knop:
   ![Details van de gegevensstroom bewerken](assets/ingestion-offline-detail.png)
1. Op de **[!UICONTROL Controleren]** stap, kunt u al uw montages samen herzien en of hen uitgeven of selecteert **[!UICONTROL Voltooien]** knop
1. Nadat u hebt opgeslagen, landt u op een scherm als dit:
   ![Voltooid](assets/ingestion-offline-complete.png)

### De gegevens valideren

Wanneer de partij heeft geupload, verifieer upload door de dataset te bekijken.

Je moet de drie hits op je website zien.

Profiel opzoeken met waarde `5625458` in de `loyaltyId` naamruimte opnieuw gebruiken om te controleren of er aankoopgebeurtenissen in hun profiel voorkomen. Je moet één aankoop zien. U kunt de details van de aankoop bekijken door **[!UICONTROL JSON weergeven]**:

![Gebeurtenis aanschaffen in profiel](assets/ingestion-offline-eventInProfile.png)

## ETL-gereedschappen

Adobe partners met veelvoudige verkopers ETL om gegevensopname in Experience Platform te steunen. Wegens de verscheidenheid van derdeverkopers, is ETL niet behandeld in dit leerprogramma, hoewel u welkom bent om sommige van deze middelen te herzien:

* [Ontwikkeling van ETL-integratie voor Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/etl/home.html)
* [Informatica Adobe Experience Platform Connector page on Adobe Exchange](https://exchange.adobe.com/experiencecloud.details.101570.informatica-adobe-experience-cloud-connector.html)
* [Informatica documentatie van de Adobe Experience Platform-connector](https://docs.informatica.com/integration-cloud/cloud-data-integration-connectors/current-version/adobe-experience-platform-connector/preface.html)
* [[!DNL Snaplogic] Adobe Experience Platform Snap Pack](https://www.snaplogic.com/resources/videos/august-2020-aep)

## Aanvullende bronnen

* [Batchdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html)
* [Referentie voor API voor batchverwerking](https://developer.adobe.com/experience-platform-apis/references/batch-ingestion/)

Laten we nu [stroomgegevens met de SDK van het Web](ingest-streaming-data.md)

---
title: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
description: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 93d9f4ef-9cbd-4310-879e-d69106b70404
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 1%

---

# 2.5 Gegevenslandingszone

In deze oefening, is het doel om uw Bron van de Gebied van Gegevens te installeren Landing van de Zone met de opslag van Azure Blob.

Data Landing Zone is een Azure Blob-opslaginterface die door Adobe Experience Platform is ingericht en u toegang biedt tot een veilige, op de cloud gebaseerde opslagvoorziening voor bestanden om bestanden in Platform te brengen. Data Landing Zone ondersteunt verificatie op basis van SAS en de bijbehorende gegevens zijn beveiligd met standaard Azure Blob-opslagbeveiligingsmechanismen in rust en in doorvoer. Met SAS-verificatie hebt u via een openbare internetverbinding veilig toegang tot uw Data Landing Zone-container.

>[!NOTE]
>
> Adobe Experience Platform **dwingt strikte tijd-aan-levende (TTL) zeven dagen af** op alle bestanden die zijn geüpload naar een container van een gegevenslandingszone. Alle bestanden worden na zeven dagen verwijderd.


## 2.5.1 Vereisten

Als u lobs of bestanden naar de Adobe Experience Platform Data Landing Zone wilt kopiëren, gebruikt u AzCopy, een opdrachtregelprogramma. U kunt een versie voor uw besturingssysteem downloaden via [https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10).

![dlz-install-az-copy.png](./images/dlz-install-az-copy.png)

- Het gedownloade bestand uitpakken

![dlz-install-az-copy.png](./images/dlz1.png)

- Download het bestand met voorbeeldgegevens [global-context-website interactions.csv](../../assets/csv/data-ingestion/global-context-websiteinteractions.csv), die voorbeeldwebsiteinteracties bevat en deze opslaat in de map waarin u het item hebt uitgepakt **azcopy**.

![dlz-install-az-copy.png](./images/dlz2.png)

- Open een terminalvenster en navigeer naar de map op uw bureaublad. De volgende inhoud (azcopy en global-context-websiteinteractions.csv) wordt weergegeven, bijvoorbeeld op OSX:

![dlz-unzip-azcopy.png](./images/dlz-unzip-azcopy.png)

## 2.5.2 Verbinding maken tussen gegevenslandingszone en Adobe Experience Platform

Meld u aan bij Adobe Experience Platform door naar deze URL te gaan: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--module2sandbox--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![Gegevensinname](./images/sb1.png)

Ga in het linkermenu naar **Bronnen**. Zoek in de Broncatalogus naar **gegevensuitvoer**. Op de **Gegevenslandingszone** kaart, klik **...** en selecteert u **Credentials weergeven**.

![dlz-view-credentials.png](./images/dlz-view-credentials.png)

Klik op Kopie tikken **SASUri**.

![dlz-copy-sas-uri.png](./images/dlz-copy-sas-uri.png)

## 2.5.3 Kopieer het CSV-bestand naar uw AEP-gegevenslandingszone

U gaat nu gegevens in Adobe Experience Platform opnemen met de Azure-opdrachtregelprogramma&#39;s van AZCopy.

Open een terminal op de locatie waar u de installatielocatie wilt kopiëren en voer de volgende opdracht uit om een bestand naar de landingszone van AEP te kopiëren:

``./azcopy copy <your-local-file> <your SASUri>``

Zorg ervoor dat u de SASUri omringt met dubbele aanhalingstekens. Vervangen `<your-local-file>` door het pad naar uw lokale kopie van het bestand **global-context-website interactions.csv** in de azcopy directory en vervang `<your SASUri>` door de **SASUri** waarde die u hebt gekopieerd uit de gebruikersinterface van Adobe Experience Platform. Uw opdracht moet er als volgt uitzien:

```command
./azcopy copy global-context-websiteinteractions.csv "https://sndbxdtlnd2bimpjpzo14hp6.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-xxxxxxx-9843-4973-ae52-xxxxxxxx&sr=c&sp=racwdlm&sig=DN3kdhKzard%2BQwKASKg67Zxxxxxxxxxxxxxxxx"
```

Na het uitvoeren van het bovengenoemde bevel in uw terminal, zult u dit zien:

![dlz-exec-copy-command.png](./images/dlz-exec-copy-command.png)

## 2.5.4 Het dossier van de opzoeker in uw Gebied van Gegevens

Ga naar je Data Landing Zone in Adobe Experience Platform.

Selecteren **Bronnen**, zoeken naar **gegevensuitvoer** en klik op de knop **Instellen** knop.

![dlz-inspect-datalanding-zone.png](./images/dlz-inspect-datalanding-zone.png)

Hiermee wordt de gegevenslandingszone geopend. U ziet het bestand dat u net hebt geüpload in de landingszone voor gegevens **gegevens selecteren** deelvenster.

![dlz-datalanding-zone-open.png](./images/dlz-datalanding-zone-open.png)

## 2.5.5 Het bestand verwerken

Selecteer uw bestand en selecteer **Gescheiden** als gegevensindeling. U ziet dan een voorvertoning van uw gegevens. Klik op **Next**.

![dlz-datalanding-select-file.png](./images/dlz-datalanding-select-file.png)

U kunt nu beginnen de geüploade gegevens in kaart te brengen om het XDM-schema van uw dataset aan te passen.

Selecteren **Bestaande gegevensset** en selecteert u de gegevensset **Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1)**. Klik op **Next**.

![dlz-target-dataset.png](./images/dlz-target-dataset.png)

Nu bent u klaar om de inkomende brongegevens van uw csv- dossier aan de doelgebieden van het schema XDM van de dataset in kaart te brengen.

![dlz-start-mapping.png](./images/dlz-start-mapping.png)

>[!NOTE]
>
> Let niet op de mogelijke fouten met de toewijzing. U zult de afbeelding in de volgende stap verbeteren.

## 2.5.6 Kaartvelden

Klik eerst op de knop **Alle toewijzingen wissen** knop. Vervolgens kunt u beginnen met een schone toewijzing.

![dlz-clear-mappings.png](./images/mappings1.png)

Klik op Volgende **Nieuw veldtype** en selecteer vervolgens **Nieuw veld toevoegen**.

![dlz-clear-mappings.png](./images/dlz-clear-mappings.png)

Om de **ecid** bronveld, selecteert het veld **identities.ecid** en klik op **Selecteren**.

![dlz-map-identity.png](./images/dlz-map-identity.png)

Klik op Volgende **Doelveld voor toewijzing**.

![dlz-map-select-target-field.png](./images/dlz-map-select-target-field.png)

Selecteer het veld ``--aepTenantId--``.identification.core.ecid in de schemastructuur.

![dlz-map-target-field.png](./images/dlz-map-target-field.png)

U moet een paar andere gebieden in kaart brengen, klik **+ Nieuw veldtype** gevolgd door **Nieuw veld toevoegen** en voeg velden toe voor deze toewijzing

| bron | target |
|---|---|
| resource.info.pagename | web.webPageDetails.name |
| timestamp | tijdstempel |
| tijdstempel | _id |

![dlz-add-other-mapping.png](./images/dlz-add-other-mapping.png)

Als het scherm klaar is, ziet het er zo uit. Klik op **Next**.

![dlz-mapping-result.png](./images/dlz-mapping-result.png)

Klik op **Next**.

![dlz-default-Scheduling.png](./images/dlz-default-scheduling.png)

Klikken **Voltooien**.

![dlz-import-finish.png](./images/dlz-import-finish.png)

## 2.5.7 Monitorgegevensstroom

Ga naar **Bronnen**, **Gegevensstromen** en klik op uw gegevensstroom:

![dlz-monitor-dataflow.png](./images/dlz-monitor-dataflow.png)

Het laden van de gegevens kan een paar minuten duren. Als dit lukt, ziet u de status **Succes**:

![dlz-monitor-dataflow-result.png](./images/dlz-monitor-dataflow-result.png)

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 2](./data-ingestion.md)

[Terug naar alle modules](../../overview.md)

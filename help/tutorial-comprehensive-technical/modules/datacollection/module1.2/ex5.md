---
title: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
description: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
kt: 5342
doc-type: tutorial
exl-id: 21b84a77-4115-4ba7-b847-b236aa14bbdd
source-git-commit: 8bdcd03bd38a6da98b82439ad86482cad5f4e684
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# 1.2.5 Gegevenslandingszone

In deze oefening, is het doel om uw schakelaar van Source van de Landing van Gegevens met Azure Blob opslag te installeren.

Data Landing Zone is een Azure Blob-opslaginterface die door Adobe Experience Platform is ingericht en u toegang biedt tot een veilige, op de cloud gebaseerde opslagvoorziening voor bestanden om bestanden naar Platform te brengen. Data Landing Zone ondersteunt verificatie op basis van SAS en de bijbehorende gegevens zijn beveiligd met standaard Azure Blob-opslagbeveiligingsmechanismen in rust en in doorvoer. Met SAS-verificatie hebt u via een openbare internetverbinding veilig toegang tot uw Data Landing Zone-container.

>[!NOTE]
>
> Adobe Experience Platform **dwingt strikte zeven-dag tijd-aan-levende (TTL)** op alle dossiers af die aan een Gegevens Landing container van de Zone worden geupload. Alle bestanden worden na zeven dagen verwijderd.


## Vereisten

Als u lobs of bestanden naar de Adobe Experience Platform Data Landing Zone wilt kopiëren, gebruikt u AzCopy, een opdrachtregelprogramma. U kunt een versie voor uw werkend systeem via [ https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10 ](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) downloaden, scrol neer op die pagina aan **Download het draagbare binaire getal AzCopy** en selecteer de aangewezen versie voor uw OS.

![ dlz-install-az-copy.png ](./images/dlzinstallazcopy.png)

- Het gedownloade bestand uitpakken

![ dlz-install-az-copy.png ](./images/dlz1.png)

- Download het dossier van steekproefgegevens globaal-context-website interactions.csv, die de interactie van de steekproefwebsite bevat en het in de omslag bewaren waarin u **azcopy** uitzette.

![ dlz-install-az-copy.png ](./images/dlz2.png)

- Open een terminalvenster en navigeer naar de map op uw bureaublad. De volgende inhoud (azcopy en global-context-websiteinteractions.csv) wordt weergegeven, bijvoorbeeld op OSX:

![ dlz-unzip-azcopy.png ](./images/dlzunzipazcopy.png)

## 1.2.5.2 Verbinding maken tussen gegevenslandingszone en Adobe Experience Platform

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` .  Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./images/sb1.png)

In het linkermenu, ga naar **Bronnen**. In de Broncatalogus, onderzoek naar **gegevens die** landen.

![ Ingestie van Gegevens ](./images/sourcesdlz.png)

Klik de **Gegevens LandingZone** kaart, zult u de geloofsbrieven op het juiste lusje zien.

![ dlz-view-credentials.png ](./images/dlzviewcredentials.png)

Klik het pictogram zoals vermeld om **SASUri** te kopiëren.

![ dlz-copy-sas-uri.png ](./images/dlzcopysasuri.png)

## Kopieer het CSV-bestand naar uw AEP-gegevenslandingszone

U gaat nu gegevens in Adobe Experience Platform opnemen met de Azure-opdrachtregelprogramma&#39;s van AZCopy.

Open een terminal op de locatie waar u de installatielocatie wilt kopiëren en voer de volgende opdracht uit om een bestand naar de landingszone van AEP te kopiëren:

``./azcopy copy <your-local-file> <your SASUri>``

Zorg ervoor dat u de SASUri omringt met dubbele aanhalingstekens. Vervang `<your-local-file>` door de weg aan uw lokale exemplaar van het dossier **global-context-website interactions.csv** in de folder azcopy, en vervang `<your SASUri>` door de **SASUri** waarde die u van Adobe Experience Platform UI kopieerde. Uw opdracht moet er als volgt uitzien:

```command
./azcopy copy global-context-websiteinteractions.csv "https://sndbxdtlnd2bimpjpzo14hp6.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-xxxxxxx-9843-4973-ae52-xxxxxxxx&sr=c&sp=racwdlm&sig=DN3kdhKzard%2BQwKASKg67Zxxxxxxxxxxxxxxxx"
```

Na het uitvoeren van het bovengenoemde bevel in uw terminal, zult u dit zien:

![ dlz-exec-copy-command.png ](./images/dlzexeccopycommand.png)

## Het bestand opzoeken in uw landingszone voor gegevens

Ga naar je Data Landing Zone in Adobe Experience Platform.

Selecteer **Bronnen**, onderzoek naar **gegevens die** landen en klik de **knoop van de Opstelling** landen.

![ dlz-inspect-datalanding-zone.png ](./images/dlzinspectdatalandingzone.png)

Hiermee wordt de gegevenslandingszone geopend. U zult het dossier zien dat u enkel in het gegevens het landen zone **uitgezochte gegevens** paneel uploadde.

![ dlz-datalanding-zone-open.png ](./images/dlzdatalandingzoneopen.png)

## Uw bestand verwerken

Selecteer uw dossier en selecteer **Gescheiden** als gegevensformaat. U ziet dan een voorvertoning van uw gegevens. Klik **daarna**.

![ dlz-datalanding-select-file.png ](./images/dlzdatalandingselectfile.png)

U kunt nu beginnen de geüploade gegevens in kaart te brengen om het XDM-schema van uw dataset aan te passen.

Selecteer **Bestaande dataset** en selecteer het dataset **Systeem van de Demo - de Dataset van de Gebeurtenis voor Website (Globale v1.1)**. Klik **daarna**.

![ dlz-target-dataset.png ](./images/dlztargetdataset.png)

Nu bent u klaar om de inkomende brongegevens van uw csv- dossier aan de doelgebieden van het schema XDM van de dataset in kaart te brengen.

![ dlz-start-mapping.png ](./images/dlzstartmapping.png)

>[!NOTE]
>
> Let niet op de mogelijke fouten met de toewijzing. U zult de afbeelding in de volgende stap verbeteren.

## Toewijzingsvelden

Eerst van alles, klik **Duidelijk alle afbeeldingen** knoop. Vervolgens kunt u beginnen met een schone toewijzing.

![ dlz-duidelijk-mappings.png ](./images/mappings1.png)

Daarna, klik **Nieuw gebiedstype** en selecteer dan **nieuw gebied** toevoegen.

![ dlz-duidelijk-mappings.png ](./images/dlzclearmappings.png)

Om het **ecid** brongebied in kaart te brengen, selecteer het gebied **identities.ecid** en klik **Uitgezocht**.

![ dlz-map-identity.png ](./images/dlzmapidentity.png)

Daarna, klik **het doelgebied van de Kaart**.

![ dlz-map-select-target-field.png ](./images/dlzmapselecttargetfield.png)

Selecteer het veld ``--aepTenantId--``.identification.core.ecid in de schemastructuur.

![ dlz-map-target-field.png ](./images/dlzmaptargetfield.png)

U moet een paar andere gebieden in kaart brengen, **+ Nieuw gebiedstype** klikken dat door **wordt gevolgd voeg nieuw gebied** toe en voeg gebieden voor deze afbeelding toe

| bron | target |
|---|---|
| resource.info.pagename | web.webPageDetails.name |
| tijdstempel | tijdstempel |
| tijdstempel | _id |

![ dlz-add-other-mapping.png ](./images/dlzaddothermapping.png)

Als het scherm klaar is, ziet het er zo uit. Klik **daarna**.

![ dlz-afbeelding-result.png ](./images/dlzmappingresult.png)

Klik **daarna**.

![ dlz-gebrek-planning.png ](./images/dlzdefaultscheduling.png)

Klik **Afwerking**.

![ dlz-import-finish.png ](./images/dlzimportfinish.png)

## Gegevensstroom controleren

Om u te controleren dataflow, ga naar **Bronnen**, **Dataflows** en klik op uw dataflow:

![ dlz-monitor-dataflow.png ](./images/dlzmonitordataflow.png)

Het laden van de gegevens kan een paar notulen nemen, wanneer succesvol, zult u een status van **Succes** zien:

![ dlz-monitor-dataflow-result.png ](./images/dlzmonitordataflowresult.png)

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 1.2](./data-ingestion.md)

[Terug naar alle modules](../../../overview.md)

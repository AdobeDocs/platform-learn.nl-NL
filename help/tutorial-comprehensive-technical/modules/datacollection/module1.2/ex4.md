---
title: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
description: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '1587'
ht-degree: 0%

---

# 1.2.4 Gegevensinname uit offlinebronnen

In deze oefening, is het doel om externe gegevens zoals Gegevens CRM in Platform aan te nemen.

## Leerdoelen

- Leer hoe u testgegevens kunt genereren
- Leer hoe u CSV inneemt
- Leer hoe u de webinterface kunt gebruiken voor gegevensinvoer via Workflows
- Begrijp de eigenschappen van het gegevensbeheer van Experience Platform

## Bronnen

- Mockaroo UI: [ https://www.mockaroo.com/](https://www.mockaroo.com/)
- Experience Platform UI: [ https://experience.adobe.com/platform/](https://experience.adobe.com/platform/)

## Taken

- Maak een CSV-bestand met de demodatum. Maak gebruik van de beschikbare workflows om het CSV-bestand in Adobe Experience Platform op te nemen.
- Opties voor gegevensbeheer in Adobe Experience Platform begrijpen

## 1.2.4.1 Creeer uw Dataset van CRM door een hulpmiddel van de gegevensgenerator

Hiervoor hebt u 1000 voorbeeldlijnen van CRM-gegevens nodig.

Open het Malplaatje Mockaroo door [ https://www.mockaroo.com/12674210 ](https://www.mockaroo.com/12674210) te gaan.

![ Ingestie van Gegevens ](./images/mockaroo.png)

In de sjabloon ziet u de volgende velden:

- id
- first_name
- last_name
- email
- sekse
- geboortedatum
- home_latitude
- home_longitude
- country_code
- stad
- land

Al deze gebieden zijn bepaald om gegevens te veroorzaken die met Platform compatibel zijn.

Als u het CSV-bestand wilt genereren, klikt u op de knop **[!UICONTROL Download Data]** , waarmee u een CSV-bestand met 1000 regels aan demo-gegevens krijgt.

![ Ingestie van Gegevens ](./images/dd.png)

Open uw CSV-bestand in Microsoft Excel om de inhoud ervan te visualiseren.

![ Ingestie van Gegevens ](./images/excel.png)

Als het CSV-bestand gereed is, kunt u doorgaan met het toewijzen ervan aan XDM.

### 1.2.4.2 Controleer de CRM-gegevensset aan boord in Adobe Experience Platform

Open [ Adobe Experience Platform ](https://experience.adobe.com/platform) en ga naar **[!UICONTROL Datasets]**.

Selecteer een **[!UICONTROL sandbox]** voordat u verdergaat. De te selecteren sandbox krijgt de naam ``--module2sandbox--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./images/sb1.png)

Klik in Adobe Experience Platform op **[!UICONTROL Datasets]** in het menu aan de linkerkant van het scherm.

![ Ingestie van Gegevens ](./images/menudatasetssb.png)

U gaat een gedeelde dataset gebruiken die in dit toelaat wordt gebaseerd. De gedeelde gegevensset is al gemaakt en wordt **[!UICONTROL Demo System - Profile Dataset for CRM (Global v1.1)]** genoemd.

![ Ingestie van Gegevens ](./images/emeacrm.png)

Open de dataset **[!UICONTROL Demo System - Profile Dataset for CRM (Global v1.1)]**.

![ Ingestie van Gegevens ](./images/emeacrmoverview.png)

Op het overzichtsscherm kunt u drie belangrijke stukken van informatie zien.

![ Ingestie van Gegevens ](./images/dashboard.png)

Ten eerste toont het dashboard van [!UICONTROL Dataset Activity] het totale aantal CRM-records in de dataset en de opgenomen batches en hun status

![ Ingestie van Gegevens ](./images/batchids.png)

Ten tweede kunt u door omlaag te schuiven op de pagina controleren wanneer batches met gegevens zijn ingesloten, hoeveel records zijn ingecheckt en of de batch is ingecheckt. **[!UICONTROL Batch ID]** is de id voor een specifieke batchtaak en **[!UICONTROL Batch ID]** is belangrijk omdat deze kan worden gebruikt voor het oplossen van problemen waarom een specifieke batch niet is geactiveerd.

![ Ingestie van Gegevens ](./images/datasetsettings.png)

Ten slotte bevat het tabblad [!UICONTROL Dataset Info] belangrijke informatie zoals [!UICONTROL Dataset ID] (ook hier belangrijk vanuit het oogpunt van probleemoplossing), de naam van de gegevensset en of de gegevensset is ingeschakeld voor Profiel.

![ Ingestie van Gegevens ](./images/ds_ups_link.png)

Het belangrijkste plaatsen hier is het verband tussen de dataset en het Schema. Het schema bepaalt welke gegevens kunnen worden opgenomen en hoe die gegevens eruit moeten zien.

In dit geval gebruiken we **[!UICONTROL Demo System - Profile Schema for CRM (Global v1.1)]** , dat is toegewezen aan de klasse **[!UICONTROL Profile]** en extensies heeft geïmplementeerd, ook wel veldgroepen genoemd.

![ Ingestie van Gegevens ](./images/ds_schemalink.png)

Door op de naam van het schema te klikken, gaat u naar het [!UICONTROL Schema] -overzicht waar u alle velden ziet die voor dit schema zijn geactiveerd.

![ Ingestie van Gegevens ](./images/schemads.png)

Voor elk schema moet een aangepaste, primaire descriptor zijn gedefinieerd. In het geval van onze dataset van CRM, heeft het schema bepaald dat het gebied **[!UICONTROL crmId]** het primaire herkenningsteken zou moeten zijn. Als u een schema wilt maken en dit aan de [!UICONTROL Real-time Customer Profile] wilt koppelen, moet u een aangepaste [!UICONTROL Field Group] definiëren die naar uw primaire descriptor verwijst.

![ Ingestie van Gegevens ](./images/schema_descriptor.png)

In de bovenstaande schermafbeelding ziet u dat uw descriptor zich in `--aepTenantId--.identification.core.crmId` bevindt, die is ingesteld als de [!UICONTROL Primary Identifier] -afbeelding, gekoppeld aan de [!UICONTROL namespace] van **[!UICONTROL Demo System - CRMID]** .

Elk schema en dus elke gegevensset die in [!UICONTROL Real-time Customer Profile] moet worden gebruikt, moet er één hebben [!UICONTROL Primary identifier] . This [!UICONTROL Primary Identifier] is the identifier user by the brand for a customer in that dataset. In het geval van een dataset van CRM zou het e-mail-adres of identiteitskaart van CRM kunnen zijn, in het geval van een dataset van het Centrum van de Vraag het het mobiele aantal van een klant kunnen zijn.

Het is beste praktijken om een afzonderlijk, specifiek schema voor elke dataset tot stand te brengen en de beschrijver voor elke dataset specifiek te plaatsen om aan te passen hoe de huidige oplossingen die door het merk worden gebruikt werken.

### 1.2.4.3 Een workflow gebruiken om een CSV-bestand toe te wijzen aan een XDM-schema

Het doel hiervan is om CRM-gegevens in het platform aan boord te hebben. Alle gegevens die in Platform worden opgenomen zouden tegen het specifieke Schema XDM in kaart moeten worden gebracht. Wat u momenteel hebt is een dataset CSV met 1000 lijnen op de ene kant, en een dataset die met een schema aan de andere kant verbonden is. Om dat CSV-bestand in die dataset te laden, moet een toewijzing plaatsvinden. Om deze toewijzingsoefening mogelijk te maken, hebben we **[!UICONTROL Workflows]** beschikbaar in Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/workflows.png)

De [!UICONTROL workflow] die we hier gebruiken, is de [!UICONTROL workflow] named **[!UICONTROL Map CSV to XDM Schema]** in het [!UICONTROL Data Ingestion] -menu.

Klik op de knop **[!UICONTROL Map CSV to XDM Schema]**. Klik op **[!UICONTROL Launch]** om het proces te starten.

![ Ingestie van Gegevens ](./images/mapcsvxdm.png)

Op het volgende scherm, moet u een dataset selecteren om uw dossier binnen in te nemen. U kunt kiezen tussen het selecteren van een bestaande gegevensset of het maken van een nieuwe gegevensset. Voor deze oefening, zullen wij bestaande hergebruiken: gelieve te selecteren **[!UICONTROL Demo System - Profile Dataset for CRM (Global v1.1)]** zoals hieronder vermeld en de andere montages te verlaten aan gebrek.

![ Ingestie van Gegevens ](./images/datasetselection.png)

Klik op **[!UICONTROL Next]** om naar de volgende stap te gaan.

![ Ingestie van Gegevens ](./images/next.png)

Sleep het CSV-bestand of klik op **[!UICONTROL Browse]** en navigeer op de computer naar het bureaublad en selecteer het gewenste CSV-bestand.

![ Ingestie van Gegevens ](./images/dragdrop.png)

Nadat u het CSV-bestand hebt geselecteerd, wordt het meteen geüpload en wordt binnen enkele seconden een voorvertoning van het bestand weergegeven.

![ Ingestie van Gegevens ](./images/previewcsv.png)

Klik op **[!UICONTROL Next]** om naar de volgende stap te gaan. Het kan een paar seconden duren als het bestand volledig is verwerkt.

![ Ingestie van Gegevens ](./images/next.png)

U moet nu uw kopballen CSV van de Kolom met een XDM-bezit in uw **[!UICONTROL Demo System - Profile Dataset for CRM]** in kaart brengen.

Adobe Experience Platform heeft al enkele voorstellen voor u gedaan door de [!UICONTROL Source Attributes] te koppelen aan de [!UICONTROL Target Schema Fields] .

![ Ingestie van Gegevens ](./images/mapschema.png)

Voor [!UICONTROL Schema Mappings] heeft Adobe Experience Platform al geprobeerd velden aan elkaar te koppelen. Niet alle voorstellen voor het in kaart brengen zijn echter juist. U moet nu **doelgebieden** één voor één goedkeuren.

#### geboortedatum

Het gebied van het Schema van Source **bornDate** zou aan het doelgebied **person.geboordeDate** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfbd.png)

#### stad

Het gebied van het Schema van Source **plaats** zou aan het doelgebied **homeAddress.city** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfcity.png)

#### land

Het gebied van het Schema van Source **land** zou aan het doelgebied **homeAddress.country** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfcountry.png)

#### country_code

Het gebied van het Schema van Source **country_code** zou aan het doelgebied **homeAddress.countryCode** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfcountrycode.png)

#### email

Het gebied van het Schema van Source **e-mail** zou met het doelgebied **PersonalEmail.address** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfemail.png)

#### crmid

Het Source-schemaveld ** crmid** moet worden gekoppeld aan het doelveld **`--aepTenantId--`.identification.core.crmId** .

![ Ingestie van Gegevens ](./images/tfemail1.png)

#### first_name

Het gebied van het Schema van Source **first_name** zou met het doelgebied **person.name.firstName** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tffname.png)

#### sekse

Het gebied van het Schema van Source **geslacht** zou aan het doelgebied **person.gender** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfgender.png)

#### home_latitude

Het gebied van het Schema van Source **home_latitude** zou aan het doelgebied **homeAddress moeten worden verbonden._schema.latitude**.

![ Ingestie van Gegevens ](./images/tflat.png)

#### home_longitude

Het gebied van het Schema van Source **home_longitude** zou met het doelgebied **homeAddress moeten worden verbonden._schema.longitude**.

![ Ingestie van Gegevens ](./images/tflon.png)

#### id

Het gebied van het Schema van Source **identiteitskaart** zou aan het doelgebied **_id** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tfid1.png)

#### last_name

Het gebied van het Schema van Source **last_name** zou met het doelgebied **person.name.lastName** moeten worden verbonden.

![ Ingestie van Gegevens ](./images/tflname.png)

U zou nu het volgende moeten hebben:

![ Ingestie van Gegevens ](./images/overview.png)

Klik op de knop **[!UICONTROL Finish]** om de workflow te voltooien.

![ Ingestie van Gegevens ](./images/finish.png)

Na het klikken **[!UICONTROL Finish]**, zult u dan het **Dataflow** overzicht zien, en na een paar notulen kunt u uw scherm verfrissen om te zien of kan uw werkschema met succes voltooid zijn. Klik uw **naam van de gegevensset van het Doel**.

![ Ingestie van Gegevens ](./images/dfsuccess.png)

U zult dan de dataset zien waar uw opname heeft verwerkt.

![ Ingestie van Gegevens ](./images/ingestdataset.png)

Op de dataset ziet u een [!UICONTROL Batch ID] die net is opgenomen, met 1000 records ingesloten en de status **[!UICONTROL Success]** .

![ Ingestie van Gegevens ](./images/batchsuccess1.png)

Klik op de knop **[!UICONTROL Preview Dataset]** - voor een snelle weergave van een klein voorbeeld van de gegevensset om te controleren of de geladen gegevens juist zijn.

![ Ingestie van Gegevens ](./images/preview.png)

![ Ingestie van Gegevens ](./images/previewdata.png)

Zodra het gegeven wordt geladen, kunt u de correcte benadering van het gegevensbeheer voor onze dataset bepalen.

### 1.2.5.4 Gegevensbeheer toevoegen aan uw gegevensset

Nu uw klantengegevens worden opgenomen, moet u ervoor zorgen dat deze dataset behoorlijk voor gebruik en de uitvoercontrole wordt geregeerd. Klik op het tabblad **[!UICONTROL Data Governance]** en controleer of u drie typen beperkingen kunt instellen: Contractueel, Identiteit en Gevoelige gegevens.

U kunt meer informatie over de verschillende etiketten vinden en hoe zij in de toekomst door het beleidskader op deze verbinding zullen worden afgedwongen: [ https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html ](https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html)

![ Ingestie van Gegevens ](./images/dsgovernance.png)

Laten wij identiteitsgegevens voor de volledige dataset beperken. Houd de muis boven de naam van de gegevensset en klik op het pictogram Potlood om de instellingen te bewerken.

![ Ingestie van Gegevens ](./images/pencil.png)

Ga naar **[!UICONTROL Identity Data]** en u zult zien dat de optie **[!UICONTROL I2]** wordt gecontroleerd - dit veronderstelt dat alle stukken van informatie in deze dataset ten minste onrechtstreeks identificeerbaar voor de persoon zijn.

![ Ingestie van Gegevens ](./images/identity.png)

Klik op **[!UICONTROL Save Changes]** en controleer of **[!UICONTROL I2]** nu is ingesteld voor alle gegevensvelden in de gegevensset.

U kunt deze markeringen ook instellen voor afzonderlijke gegevensvelden. Het veld **[!UICONTROL firstName]** wordt bijvoorbeeld waarschijnlijk geclassificeerd als een **[!UICONTROL I1]** -niveau voor rechtstreeks identificeerbare gegevens.

Selecteer het veld **[!UICONTROL firstName]** door het selectievakje in te schakelen en klik op **[!UICONTROL Edit Governance Labels]** in de rechterbovenhoek van het scherm.

![ Ingestie van Gegevens ](./images/editfirstname.png)

Ga naar **[!UICONTROL Identity Data]** en u zult zien dat de **[!UICONTROL I2]** optie reeds wordt gecontroleerd (die van de dataset wordt geërft). Het veld firstName heeft ook een veldspecifieke configuratie en wordt ingesteld als **[!UICONTROL I1 - Directly Identifiable Data]** .

![ Ingestie van Gegevens ](./images/fndii.png)

Met dit, hebt u met succes en geclassificeerde Gegevens van CRM in Adobe Experience Platform opgenomen.

Volgende Stap: [ 1.2.5 Gegevens Landing Zone ](./ex5.md)

[Terug naar module 1.2](./data-ingestion.md)

[Terug naar alle modules](../../../overview.md)

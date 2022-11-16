---
title: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
description: Stichting - de Ingestie van Gegevens - de Ingestie van Gegevens van Off line Bronnen
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 0d79f013-042a-4d2e-a031-c81319a8955d
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1742'
ht-degree: 0%

---

# 2.4 Gegevensinname uit offlinebronnen

In deze oefening, is het doel aan boord externe gegevens zoals de Gegevens van CRM in Platform.

## Leerdoelen

- Leer hoe u testgegevens kunt genereren
- Leer hoe u CSV inneemt
- Leer hoe u de webinterface kunt gebruiken voor gegevensinvoer via Workflows
- Begrijp de eigenschappen van het gegevensbeheer van Experience Platform

## Bronnen

- Mockaroo UI: [https://www.mockaroo.com/](https://www.mockaroo.com/)
- UI Experience Platform: [https://experience.adobe.com/platform/](https://experience.adobe.com/platform/)

## Taken

- Maak een CSV-bestand met de demodatum. Maak gebruik van de beschikbare workflows om het CSV-bestand in Adobe Experience Platform op te nemen.
- Opties voor gegevensbeheer in Adobe Experience Platform begrijpen

## 2.4.1 Creeer uw Dataset van CRM door een hulpmiddel van de gegevensgenerator

Hiervoor hebt u 1000 voorbeeldlijnen van CRM-gegevens nodig.

Open de Mockaroo-sjabloon door naar [https://www.mockaroo.com/12674210](https://www.mockaroo.com/12674210).

![Gegevensinname](./images/mockaroo.png)

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

Als u het CSV-bestand wilt genereren, klikt u op de knop **[!UICONTROL Gegevens downloaden]** een CSV-bestand met 1000 regels demo-data.

![Gegevensinname](./images/dd.png)

Open uw CSV-bestand in Microsoft Excel om de inhoud ervan te visualiseren.

![Gegevensinname](./images/excel.png)

Als het CSV-bestand gereed is, kunt u doorgaan met het toewijzen ervan aan XDM.

### 2.4.2 Controleer de CRM-gegevensset aan boord in Adobe Experience Platform

Openen [Adobe Experience Platform](https://experience.adobe.com/platform) en ga naar **[!UICONTROL Gegevenssets]**.

Voordat u verdergaat, moet u een **[!UICONTROL sandbox]**. De sandbox die moet worden geselecteerd, krijgt een naam ``--module2sandbox--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

Klik in Adobe Experience Platform op **[!UICONTROL Gegevenssets]** in het menu aan de linkerkant van het scherm.

![Gegevensinname](./images/menudatasetssb.png)

U gaat een gedeelde dataset gebruiken die in dit toelaat wordt gebaseerd. De gedeelde dataset is reeds gecreeerd en genoemd **[!UICONTROL Demosysteem - profielgegevensset voor CRM (Global v1.1)]**.

![Gegevensinname](./images/emeacrm.png)

De dataset openen **[!UICONTROL Demosysteem - profielgegevensset voor CRM (Global v1.1)]**.

![Gegevensinname](./images/emeacrmoverview.png)

Op het overzichtsscherm kunt u drie belangrijke stukken van informatie zien.

![Gegevensinname](./images/dashboard.png)

Allereerst de [!UICONTROL Gegevensactiviteit] het dashboard toont het totale aantal verslagen van CRM in de dataset en de opgenomen partijen en hun status

![Gegevensinname](./images/batchids.png)

Ten tweede kunt u door omlaag te schuiven op de pagina controleren wanneer batches met gegevens zijn ingesloten, hoeveel records zijn ingecheckt en of de batch is ingecheckt. De **[!UICONTROL Batch-id]** is de id voor een specifieke batchtaak en de **[!UICONTROL Batch-id]** is belangrijk aangezien het voor het oplossen van problemen kan worden gebruikt waarom een specifieke partij niet met succes werd ingezien.

![Gegevensinname](./images/datasetsettings.png)

Tot slot [!UICONTROL Gegevensset-info] tab bevat belangrijke informatie zoals [!UICONTROL Dataset-id] (opnieuw, belangrijk vanuit een het oplossen van problemenperspectief), de Naam van de Dataset en of de dataset voor Profiel werd toegelaten.

![Gegevensinname](./images/ds_ups_link.png)

Het belangrijkste plaatsen hier is het verband tussen de dataset en het Schema. Het schema bepaalt welke gegevens kunnen worden opgenomen en hoe die gegevens eruit moeten zien.

In dit geval gebruiken we de **[!UICONTROL Demosysteem - Profielschema voor CRM (Global v1.1)]**, die aan de klasse van **[!UICONTROL Profiel]** en heeft extensies geïmplementeerd, ook wel veldgroepen genoemd.

![Gegevensinname](./images/ds_schemalink.png)

Als u op de naam van het schema klikt, gaat u naar de [!UICONTROL Schema] overzicht waar u alle velden kunt zien die voor dit schema zijn geactiveerd.

![Gegevensinname](./images/schemads.png)

Voor elk schema moet een aangepaste, primaire descriptor zijn gedefinieerd. In het geval van onze dataset van CRM, heeft het schema bepaald dat het gebied **[!UICONTROL crmId]** moet de primaire identificator zijn. Als u een schema wilt maken en dit aan de [!UICONTROL Klantprofiel in realtime], moet u een aangepaste [!UICONTROL Veldgroep] die naar uw primaire descriptor verwijst.

![Gegevensinname](./images/schema_descriptor.png)

In de bovenstaande schermafbeelding kunt u zien dat uw descriptor zich bevindt in `--aepTenantId--.identification.core.crmId`, die wordt ingesteld als de [!UICONTROL Primaire id], gekoppeld aan de [!UICONTROL namespace] van **[!UICONTROL Demosysteem - CRMID]**.

Elk schema en als zodanig, elke dataset die in zou moeten worden gebruikt [!UICONTROL Klantprofiel in realtime] moet er één hebben [!UICONTROL Primaire id]. Dit [!UICONTROL Primaire id] is de herkenningstekengebruiker door het merk voor een klant in die dataset. In het geval van een dataset van CRM zou het e-mail-adres of identiteitskaart van CRM kunnen zijn, in het geval van een dataset van het Centrum van de Vraag het het mobiele aantal van een klant kunnen zijn.

Het is beste praktijken om een afzonderlijk, specifiek schema voor elke dataset tot stand te brengen en de beschrijver voor elke dataset specifiek te plaatsen om aan te passen hoe de huidige oplossingen die door het merk worden gebruikt werken.

### 2.4.3 Een workflow gebruiken om een CSV-bestand toe te wijzen aan een XDM-schema

Het doel hiervan is om CRM-gegevens in Platform aan boord te hebben. Alle gegevens die in Platform worden opgenomen zouden tegen het specifieke Schema XDM in kaart moeten worden gebracht. Wat u momenteel hebt is een dataset CSV met 1000 lijnen op de ene kant, en een dataset die met een schema aan de andere kant verbonden is. Om dat CSV-bestand in die dataset te laden, moet een toewijzing plaatsvinden. Om deze inventarisatie te vergemakkelijken, moeten we **[!UICONTROL Workflows]** beschikbaar in Adobe Experience Platform.

![Gegevensinname](./images/workflows.png)

De [!UICONTROL werkstroom] die we hier zullen gebruiken, is de [!UICONTROL werkstroom] benoemd **[!UICONTROL CSV toewijzen aan XDM-schema]** in de [!UICONTROL Gegevensinname] -menu.

Klik op de knop **[!UICONTROL CSV toewijzen aan XDM-schema]** knop. Klikken **[!UICONTROL Starten]** om het proces te starten.

![Gegevensinname](./images/mapcsvxdm.png)

Op het volgende scherm, moet u een dataset selecteren om uw dossier binnen in te nemen. U kunt kiezen tussen het selecteren van een bestaande gegevensset of het maken van een nieuwe gegevensset. Voor deze oefening, zullen wij bestaande hergebruiken: Selecteer **[!UICONTROL Demosysteem - profielgegevensset voor CRM (Global v1.1)]** zoals hieronder aangegeven, en laat de andere instellingen op de standaardwaarde staan.

![Gegevensinname](./images/datasetselection.png)

Klikken **[!UICONTROL Volgende]** om naar de volgende stap te gaan.

![Gegevensinname](./images/next.png)

Sleep het CSV-bestand of klik op **[!UICONTROL Bladeren]** en navigeer op uw computer naar uw bureaublad en selecteer uw CSV-bestand.

![Gegevensinname](./images/dragdrop.png)

Nadat u het CSV-bestand hebt geselecteerd, wordt het meteen geüpload en wordt binnen enkele seconden een voorvertoning van het bestand weergegeven.

![Gegevensinname](./images/previewcsv.png)

Klikken **[!UICONTROL Volgende]** om naar de volgende stap te gaan. Het kan een paar seconden duren als het bestand volledig is verwerkt.

![Gegevensinname](./images/next.png)

U moet nu uw Kopballen van de Kolom CSV met een XDM-bezit in kaart brengen **[!UICONTROL Demosysteem - profielgegevensset voor CRM]**.

Adobe Experience Platform heeft al een aantal voorstellen voor u gedaan door te proberen de [!UICONTROL Bronkenmerken] met de [!UICONTROL Doelschemavelden].

![Gegevensinname](./images/mapschema.png)

Voor de [!UICONTROL Schema-toewijzingen], Adobe Experience Platform heeft al geprobeerd velden aan elkaar te koppelen. Niet alle voorstellen voor het in kaart brengen zijn echter juist. U moet nu **Doelvelden accepteren** één voor één.

#### geboortedatum

Het veld Bronschema **geboortedatum** moet worden gekoppeld aan het doelveld **person.bornDate**.

![Gegevensinname](./images/tfbd.png)

#### stad

Het veld Bronschema **stad** moet worden gekoppeld aan het doelveld **homeAddress.city**.

![Gegevensinname](./images/tfcity.png)

#### land

Het veld Bronschema **land** moet worden gekoppeld aan het doelveld **homeAddress.country**.

![Gegevensinname](./images/tfcountry.png)

#### country_code

Het veld Bronschema **country_code** moet worden gekoppeld aan het doelveld **homeAddress.countryCode**.

![Gegevensinname](./images/tfcountrycode.png)

#### email

Het veld Bronschema **email** moet worden gekoppeld aan het doelveld **PersonalEmail.address**.

![Gegevensinname](./images/tfemail.png)

#### crmid

Het veld Bronschema ** crmid* moet aan het doelveld worden gekoppeld **`--aepTenantId--`.identification.core.crmId**.

![Gegevensinname](./images/tfemail1.png)

#### first_name

Het veld Bronschema **first_name** moet worden gekoppeld aan het doelveld **person.name.firstName**.

![Gegevensinname](./images/tffname.png)

#### sekse

Het veld Bronschema **sekse** moet worden gekoppeld aan het doelveld **persoon.geslacht**.

![Gegevensinname](./images/tfgender.png)

#### home_latitude

Het veld Bronschema **home_latitude** moet worden gekoppeld aan het doelveld **homeAddress._schema.latitude**.

![Gegevensinname](./images/tflat.png)

#### home_longitude

Het veld Bronschema **home_longitude** moet worden gekoppeld aan het doelveld **homeAddress._schema.longitude**.

![Gegevensinname](./images/tflon.png)

#### id

Het veld Bronschema **id** moet worden gekoppeld aan het doelveld **_id**.

![Gegevensinname](./images/tfid1.png)

#### last_name

Het veld Bronschema **last_name** moet worden gekoppeld aan het doelveld **person.name.lastName**.

![Gegevensinname](./images/tflname.png)

U zou nu het volgende moeten hebben:

![Gegevensinname](./images/overview.png)

Klik op de knop **[!UICONTROL Voltooien]** om de workflow te voltooien.

![Gegevensinname](./images/finish.png)

Na klikken **[!UICONTROL Voltooien]**, dan zie je de **Gegevensstroom** en na een paar minuten kunt u het scherm vernieuwen om te zien of de workflow is voltooid. Klik op **Naam doelgegevensset**.

![Gegevensinname](./images/dfsuccess.png)

U zult dan de dataset zien waar uw opname heeft verwerkt.

![Gegevensinname](./images/ingestdataset.png)

Op de dataset, zult u een zien [!UICONTROL Batch-id] dat nu is ingeslikt , met 1000 records ingegeten en een status van **[!UICONTROL Succes]**.

![Gegevensinname](./images/batchsuccess1.png)

Klik op de knop **[!UICONTROL Gegevensset voorvertoning]**- om een snelle mening van een kleine steekproef van de dataset te krijgen om ervoor te zorgen dat de geladen gegevens correct zijn.

![Gegevensinname](./images/preview.png)

![Gegevensinname](./images/previewdata.png)

Zodra het gegeven wordt geladen, kunt u de correcte benadering van het gegevensbeheer voor onze dataset bepalen.

### 2.5.4 Gegevensbeheer toevoegen aan uw gegevensset

Nu uw klantengegevens worden opgenomen, moet u ervoor zorgen dat deze dataset behoorlijk voor gebruik en de uitvoercontrole wordt geregeerd. Klik op de knop **[!UICONTROL Gegevensbeheer]** en ziet u dat u drie typen beperkingen kunt instellen: Contractueel, Identiteit en Gevoelige Gegevens.

U vindt meer informatie over de verschillende labels en hoe deze in de toekomst worden gehandhaafd via het beleidskader op deze koppeling: [https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html](https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html)

![Gegevensinname](./images/dsgovernance.png)

Laten wij identiteitsgegevens voor de volledige dataset beperken. Houd de muis boven de naam van de gegevensset en klik op het pictogram Potlood om de instellingen te bewerken.

![Gegevensinname](./images/pencil.png)

Ga naar **[!UICONTROL Identiteitsgegevens]** en je zult zien dat de **[!UICONTROL I2]** optie wordt gecontroleerd - hierbij wordt ervan uitgegaan dat alle gegevens in deze gegevensset ten minste indirect voor de persoon identificeerbaar zijn.

![Gegevensinname](./images/identity.png)

Klikken **[!UICONTROL Wijzigingen opslaan]** en merkt op dat **[!UICONTROL I2]** is nu ingesteld voor alle gegevensvelden in de gegevensset.

U kunt deze markeringen ook instellen voor afzonderlijke gegevensvelden, zoals de **[!UICONTROL firstName]** waarschijnlijk als een **[!UICONTROL I1]** niveau voor rechtstreeks identificeerbare informatie.

Selecteer het veld **[!UICONTROL firstName]** door het selectievakje in te schakelen en op **[!UICONTROL Regelgevingslabels bewerken]** in de rechterbovenhoek van het scherm.

![Gegevensinname](./images/editfirstname.png)

Ga naar **[!UICONTROL Identiteitsgegevens]** en je zult zien dat de **[!UICONTROL I2]** optie is reeds gecontroleerd (die van de dataset wordt geërft). Het veld firstName heeft ook een veldspecifieke configuratie en wordt ingesteld als **[!UICONTROL I1 - Direct identificeerbare gegevens]**.

![Gegevensinname](./images/fndii.png)

Met dit, hebt u met succes en geclassificeerde Gegevens van CRM in Adobe Experience Platform opgenomen.

Volgende stap: [2.5 Gegevenslandingszone](./ex5.md)

[Ga terug naar module 2](./data-ingestion.md)

[Terug naar alle modules](../../overview.md)

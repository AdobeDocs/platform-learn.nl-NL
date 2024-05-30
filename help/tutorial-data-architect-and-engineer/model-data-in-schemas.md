---
title: Modelgegevens in schema's
seo-title: Model data in schemas | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Modelgegevens in schema's
description: In deze les, zult u de gegevens van Luma in schema's modelleren. Dit is een van de langste lessen in de zelfstudie, dus maak een glas water en sluit op!
role: Data Architect
feature: Schemas
jira: KT-4348
thumbnail: 4348-model-data-in-schemas.jpg
exl-id: 317f1c39-7f76-4074-a246-ef19f044cb85
source-git-commit: 8e470d8a0c9fee7389ac60a743431fe81012fa0f
workflow-type: tm+mt
source-wordcount: '2476'
ht-degree: 0%

---

# Modelgegevens in schema&#39;s

<!-- 60min -->
In deze les, zult u de gegevens van Luma in schema&#39;s modelleren. Dit is een van de langste lessen in de zelfstudie, dus maak een glas water en sluit op!

Standaardisering en interoperabiliteit zijn de belangrijkste concepten achter Adobe Experience Platform. Het Model van Gegevens van de ervaring (XDM) is een inspanning om de gegevens van de klantenervaring te standaardiseren en schema&#39;s voor het beheer van de klantenervaring te bepalen.

XDM is een openbaar gedocumenteerde specificatie die wordt ontworpen om de macht van digitale ervaringen te verbeteren. Het verstrekt gemeenschappelijke structuren en definities voor om het even welke toepassing om met de diensten van het Platform te gebruiken te communiceren. Door zich aan de normen van XDM te houden, kunnen alle gegevens van de klantenervaring in een gemeenschappelijke vertegenwoordiging worden opgenomen die inzichten op een snellere, meer geïntegreerde manier kan leveren. U kunt waardevolle inzichten van klantenacties bereiken, klantenpubliek door segmenten bepalen, en klantenattributen voor verpersoonlijkingsdoeleinden uitdrukken.

XDM is het grondkader dat Adobe Experience Cloud, aangedreven door Experience Platform, toestaat om het juiste bericht aan de juiste persoon, op het juiste kanaal, op precies het juiste moment te leveren. de methode waarop het Experience Platform is gebouwd; **XDM-systeem**, exploiteert de Modelschema&#39;s van de Gegevens van de Ervaring voor gebruik door de diensten van het Platform.

<!--
This seems too lengthy. The video should suffice

Key terms:

* **Schema**: a representation of your data. A schema is comprised of a class and optional field groups and is used to create datasets. A schema includes behavioral attributes, timestamp, identity, attribute definitions, and relationships.
* **XDM Profile Class**: a common schema class used to represent record data
* **XDM ExperienceEvent Class**: a common schema class used to represent time-series data
* **Field group**: allows users to extend reusable fields that contain variables defining one or more attribute intended to be included in a schema or added to a class.
* **Standard Field group**: an open-source Field group built to conform to common industry standards, used to accelerate implementation and support repeatable services operating on the data
* **Data type**: a reusable object with properties in a hierarchical representation. These can be standard types or custom-defined defined types to describe your own data in your own way (for example, a collection of fields that you use to describe your products). Unlike Field groups, data types can be used in schemas regardless of the class.
* **Field**: a field is the lowest level element of a schema. Each field has a name for referencing and a type to identify the type of data that it contains. Field types can include, integer, number, string, Boolean and schema.
-->

**Gegevensarchitecten** buiten deze zelfstudie schema&#39;s maken, maar **Gegevensengineers** zal nauw samenwerken met de schema&#39;s die door de Architect van Gegevens worden gecreeerd.

Voordat u met de oefeningen begint, bekijk deze korte video om meer over schema&#39;s en het Model van de Gegevens van de Ervaring te leren (XDM):
>[!VIDEO](https://video.tv.adobe.com/v/27105?learn=on)

>[!TIP]
>
> Voor een diepere duik in gegevensmodellering in Experience Platform, adviseren wij het nemen van de cursus [Uw klantgegevens modelleren met XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm), gratis beschikbaar op Experience League!

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--, specifically:

* Permission items **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)-->


<!--
## Luma's goals
-->

## Loyalty-schema maken via gebruikersinterface

In deze oefening, zullen wij een schema voor de loyaliteitsgegevens van Luma tot stand brengen.

1. Ga naar de gebruikersinterface van het Platform en zorg ervoor dat uw zandbak wordt geselecteerd.
1. Ga naar **[!UICONTROL Schemas]** in de linkernavigatie.
1. Selecteer de **[!UICONTROL Create schema]** aan de rechterbovenzijde.
   ![Schema met OTB-veldgroep](assets/schemas-loyaltyCreateSchema.png)

1. Selecteer in de workflow Schema maken de optie **[!UICONTROL Individual Profile]** als basisklasse voor uw schema, aangezien wij attributen van een individuele klant (punten, status, etc.) zullen modelleren.
1. Selecteren **[!UICONTROL Next]**.
   ![Basisklasse selecteren](assets/schemas-loyaltySelectBaseClass.png)

1. Enter `Luma Loyalty Schema` in de **[!UICONTROL Schema display name]** tekstveld. In het onderstaande canvas kunt u ook de basisschemastructuur bekijken en verifiëren die wordt geleverd door de klasse die u hebt gekozen.
1. Selecteren **[!UICONTROL Finish]** om uw schema te maken.
   ![Het maken van het loyaliteitsschema voltooien](assets/schemas-loyaltyFinishSchemaCreation.png)

### Standaardveldgroepen toevoegen

Zodra het schema wordt gecreeerd, zult u aan de redacteur van het Schema worden opnieuw gericht waar u gebieden aan het schema kunt toevoegen. U kunt afzonderlijke velden rechtstreeks aan het schema toevoegen of veldgroepen gebruiken. Houd er rekening mee dat alle afzonderlijke velden nog steeds zijn gekoppeld aan een klasse of veldgroep. U kunt kiezen uit een groot aantal industriestandaard veldgroepen die door Adobe worden geleverd, of u kunt uw eigen veldgroepen maken. Wanneer u uw eigen gegevens in het Experience Platform gaat modelleren, is het goed om vertrouwd te raken met de industriestandaard veldgroepen die door de Adobe worden geleverd. Waar mogelijk, is het beste praktijken om hen te gebruiken aangezien zij soms stroomafwaartse diensten, zoals KlantenAI, Attribution AI, en Adobe Analytics aandrijven.

Wanneer u met uw eigen gegevens werkt, is het belangrijk te bepalen welke van uw eigen gegevens in Platform moeten worden vastgelegd en hoe deze moeten worden gemodelleerd. Dit grote onderwerp wordt besproken meer diepgaand in cursus [Uw klantgegevens modelleren met XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm). In deze zelfstudie zal ik u enkel door de implementatie van sommige vooraf bepaalde schema&#39;s begeleiden.

Veld toevoegen:

1. Selecteren **[!UICONTROL Add]** onder de **[!UICONTROL Field Groups]** kop.
   ![Een nieuwe veldgroep toevoegen](assets/schemas-loyalty-addFieldGroup.png)
1. In de **[!UICONTROL Add Field groups]** modal, selecteer de volgende gebiedsgroepen:
   1. **[!UICONTROL Demographic Details]** voor elementaire klantgegevens zoals naam en geboortedatum
   1. **[!UICONTROL Personal Contact Details]** voor standaardcontactgegevens zoals e-mailadres en telefoonnummer
1. U kunt een voorvertoning van de toegevoegde velden weergeven in de veldgroep door het pictogram aan de rechterkant van de rij te selecteren.
   ![Standaardveldgroepen selecteren](assets/schemas-loyalty-addFirstTwoFieldGroups.png)

1. Controleer de **[!UICONTROL Industry]** > **[!UICONTROL Retail]** om industriespecifieke veldgroepen beschikbaar te maken.
1. Selecteren **[!UICONTROL Loyalty Details]** om de gebieden van het loyaliteitsprogramma toe te voegen.
1. Selecteren **[!UICONTROL Add field groups]** om alle drie gebiedsgroepen aan het schema toe te voegen.
   ![Standaardveldgroepen toevoegen aan loyaliteitsschema](assets/schemas-loyalty-saveOotbMixins.png)


Nu, neem wat tijd om de huidige staat van het schema te onderzoeken. De veldgroepen hebben standaardvelden toegevoegd die betrekking hebben op een persoon, de contactgegevens en de status van het loyaliteitsprogramma. Deze twee veldgroepen zijn wellicht handig wanneer u schema&#39;s voor de gegevens van uw eigen bedrijf maakt. Selecteer een specifieke veldgroeprij of schakel het selectievakje naast de naam van de veldgroep in om te zien hoe de visualisatie verandert.

Selecteer **[!UICONTROL Save]**.
![Het schema opslaan](assets/schemas-loyalty-saveSchema.png)

>[!NOTE]
>
>Het is oké als een veldgroep een veld toevoegt voor een gegevenspunt dat u niet verzamelt. &#39;faxPhone&#39; kan bijvoorbeeld een veld zijn waarvoor Luma geen gegevens verzamelt. Dat is prima. Alleen omdat een veld in het schema is gedefinieerd, betekent dit niet dat er gegevens voor zijn *moet* later worden ingeslikt. U kunt het veld ook uit het schema verwijderen.

### Een aangepaste veldgroep toevoegen

Laten we nu een aangepaste veldgroep maken.

Terwijl de groep van het loyaliteitsgebied een `loyaltyID` veld, wil Luma al hun systeem-id&#39;s in één groep beheren om consistentie tussen de schema&#39;s te garanderen.

Veldgroepen moeten worden gemaakt in de schemaworkflow. U kunt:

* Voeg eerst een nieuw aangepast veld toe aan uw schema en maak vervolgens een aangepaste veldgroep, of
* Maak eerst een aangepaste veldgroep en voeg daar vervolgens velden aan toe.

In deze zelfstudie beginnen we met het maken van een aangepaste veldgroep.

De veldgroep maken:

1. Selecteren **[!UICONTROL Add]** onder de **[!UICONTROL Schema Field Groups]** kop
   ![Een nieuwe veldgroep toevoegen](assets/schemas-loyalty-addFieldGroup.png)
1. Selecteren **[!UICONTROL Create new field group]**
1. Gebruiken `Luma Identity profile field group` als de **[!UICONTROL Display name]**
1. Gebruiken `system identifiers for XDM Individual Profile class` als de **[!UICONTROL Description]**
1. Selecteren **[!UICONTROL Add field groups]**
   ![Een nieuwe veldgroep toevoegen](assets/schemas-loyalty-nameFieldGroup.png)

De nieuwe, lege veldgroep wordt toegevoegd aan uw schema. De **[!UICONTROL +]** U kunt knoppen gebruiken om nieuwe velden toe te voegen aan elke locatie in de hiërarchie. In ons geval willen we velden toevoegen op het hoofdniveau:

1. Selecteren **[!UICONTROL +]** naast de naam van het schema. Hiermee wordt een nieuw veld onder de naamruimte voor id van een huurder toegevoegd voor het beheer van conflicten tussen uw aangepaste velden en standaardvelden.
1. In de **[!UICONTROL Field properties]** zijbalk voegt de details van het nieuwe veld toe:
   1. **[!UICONTROL Field name]**: `systemIdentifier`
   1. **[!UICONTROL Display name]**: `System Identifier`
   1. **[!UICONTROL Type]**: **[!UICONTROL Object]**
   1. In de **[!UICONTROL Field Group]** vervolgkeuzelijst selecteert u **Luminantiekenprofielgroep** dat wij hebben gecreëerd.
      ![Een nieuwe veldgroep toevoegen](assets/schemas-loyalty-addSystemIdentifier.png)
   1. Selecteren **[!UICONTROL Apply]**
      ![Nieuwe veldeigenschappen toepassen](assets/schemas-loyalty-applySystemIdentifier.png)

Voeg nu twee velden toe onder de `systemIdentifier` object:

1. Eerste veld
   1. **[!UICONTROL Field name]**: `loyaltyId`
   1. **[!UICONTROL Display name:]** `Loyalty Id`
   1. **[!UICONTROL Type]**: **[!UICONTROL String]**
1. Tweede veld
   1. **[!UICONTROL Field Name]**: `crmId`
   1. **[!UICONTROL Display Name]**: `CRM Id`
   1. **[!UICONTROL Type]**: **[!UICONTROL String]**

Uw nieuwe veldgroep moet er zo uitzien. Selecteer de **[!UICONTROL Save]** om uw schema op te slaan, maar laat het schema open voor de volgende oefening.
![Loyalty, veldgroep voltooid](assets/schemas-loyalty-identityFieldGroupComplete.png)

## Een gegevenstype maken

Veldgroepen, zoals uw nieuwe `Luma Identity profile field group`, kan in andere schema&#39;s opnieuw worden gebruikt, toestaand u om standaardgegevensdefinities op veelvoudige systemen af te dwingen. Maar ze kunnen alleen opnieuw worden gebruikt _in schema&#39;s die een klasse delen_, in dit geval de klasse Individueel profiel XDM.

Het gegevenstype is een andere constructie met meerdere velden die opnieuw kan worden gebruikt in schema&#39;s _over meerdere klassen_. Laten we onze nieuwe `systemIdentifier` -object in een gegevenstype:

Met de `Luma Loyalty Schema` nog open, selecteer `systemIdentifier` object en selecteer  **[!UICONTROL Convert to new data type]**

![Loyalty, veldgroep voltooid](assets/schemas-loyalty-convertToDataType.png)

Als u **[!UICONTROL Cancel]** uit het schema en navigeer naar de **[!UICONTROL Data types]** wordt het nieuwe gegevenstype weergegeven. Dit gegevenstype wordt later in de les gebruikt.

![Loyalty, veldgroep voltooid](assets/schemas-loyalty-confirmDataType.png)


## CRM-schema maken via API

Nu maken we een schema met de API.

>[!TIP]
>
> Als u liever de API-oefening overslaat, kunt u het volgende schema maken met de gebruikersinterfacemethode:
>
> 1. Gebruik de [!UICONTROL Individual Profile] class
> 1. Naam geven `Luma CRM Schema`
> 1. Gebruik de volgende veldgroepen: Demografische details, Persoonlijke contactgegevens en Luminimitatieprofielveldgroep

Eerst maken we het lege schema:

1. Openen [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteert u **Verzenden** om een nieuw toegangstoken aan te vragen.
1. Omgevingsvariabelen openen en de waarde wijzigen van **CONTAINER_ID** van `global` tot `tenant`. Vergeet niet dat u `tenant` wanneer u met uw eigen douaneelementen in Platform wilt in wisselwerking staan, zoals het creëren van een schema.
1. Selecteren **Opslaan**
   ![CONTAINER_ID wijzigen in huurder](assets/schemas-crm-changeContainerId.png)
1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Create a new custom schema.]**
1. Open de **Lichaam** en plak de volgende code en selecteer **Verzenden** om de API aan te roepen. Deze vraag leidt tot een nieuw schema gebruikend het zelfde `XDM Individual Profile` basisklasse:

   ```json
   {
     "type": "object",
     "title": "Luma CRM Schema",
     "description": "Schema for CRM data of Luma Retail ",
     "allOf": [{
       "$ref": "https://ns.adobe.com/xdm/context/profile"
     }]
   }
   ```

   >[!NOTE]
   >
   >De naamruimte verwijst in dit en volgende codevoorbeelden (bijvoorbeeld `https://ns.adobe.com/xdm/context/profile`), kan worden verkregen door API-aanroepen van lijsten te gebruiken met de **[!DNL CONTAINER_ID]** en accepteer de header die op de juiste waarden is ingesteld. Sommige zijn ook gemakkelijk toegankelijk in het gebruikersinterface.

1. U moet een `201 Created` reactie
1. Kopiëren `meta:altId` van het responsorgaan. We zullen het later in een andere oefening gebruiken.
   ![Het CRM-schema maken](assets/schemas-crm-createSchemaCall.png)

1. Het nieuwe schema moet zichtbaar zijn in de gebruikersinterface, maar zonder veldgroepen
   ![Het CRM-schema maken](assets/schemas-loyalty-emptySchemaInTheUI.png)

>[!NOTE]
>
> De `meta:altId` of schema-id kan ook worden verkregen door de API-aanvraag in te dienen **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]** met de **[!UICONTROL CONTAINER_ID]** instellen op `tenant` en accepteert header `application/vnd.adobe.xdm+json`.

>[!TIP]
>
> Gemeenschappelijke kwesties met deze vraag en waarschijnlijke moeilijke situaties:
>
> * Geen auteur-token: voer de opdracht **OAuth: Toegangstoken aanvragen** verzoek om een nieuw token te genereren
> * `401: Not Authorized to PUT/POST/PATCH/DELETE for this path : /global/schemas/`: Werk de **CONTAINER_ID** omgevingsvariabele van `global` tot `tenant`
> * `403: PALM Access Denied. POST access is denied for this resource from access control`: Controleer de gebruikersmachtigingen in de Admin Console

### Standaardveldgroepen toevoegen

Nu is het tijd om de gebiedsgroepen aan het schema toe te voegen:

1. In [!DNL Postman], Open het verzoek **[!DNL Schema Registry API > Schemas > Update one or more attributes of a custom schema specified by ID.]**
1. In de **Params** plakken, `meta:altId` waarde van het vorige antwoord als `SCHEMA_ID`
1. Open het tabblad Body en plak de volgende code en selecteer **Verzenden** om de API aan te roepen. Deze vraag voegt de standaardgebiedsgroepen aan uw toe `Luma CRM Schema`:

   ```json
   [{
       "op": "add",
       "path": "/allOf/-",
       "value": {
         "$ref": "https://ns.adobe.com/xdm/context/profile-personal-details"
       }
     },
     {
       "op": "add",
       "path": "/allOf/-",
       "value": {
         "$ref": "https://ns.adobe.com/xdm/context/profile-person-details"
       }
     }
   ]
   ```

1. U zou een 200 O.K. status voor de reactie moeten krijgen en de gebiedsgroepen zouden als deel van uw schema in UI zichtbaar moeten zijn

   ![Standaard toegevoegde veldgroepen](assets/schemas-crm-addMixins.png)


### Aangepaste veldgroep toevoegen

Laten we nu onze `Luma Identity profile field group` naar het schema. Ten eerste moeten we de id van onze nieuwe veldgroep vinden met een lijst-API:

1. De aanvraag openen **[!DNL Schema Registry API > Field groups > Retrieve a list of field groups within the specified container.]**
1. Selecteer de **Verzenden** om een lijst op te halen met alle aangepaste veldgroepen in uw account
1. Pak de `$id` waarde van de `Luma Identity profile field group` (uw waarde verschilt van de waarde in deze schermafbeelding)
   ![De lijst met veldgroepen ophalen](assets/schemas-crm-getListOfMixins.png)
1. De aanvraag openen **[!DNL Schema Registry API > Schemas > Update one or more attributes of a custom schema specified by ID.]** opnieuw
1. De **Params** de tab moet nog steeds de `$id` van uw schema
1. Open de **Lichaam** de volgende code, die vervangt `$ref` met de `$id` van u `Luma Identity profile field group`:

   ```json
   [{
     "op": "add",
     "path": "/allOf/-",
     "value": {
       "$ref": "REPLACE_WITH_YOUR_OWN_FIELD_GROUP_ID"
     }
   }]
   ```

1. Selecteren **Verzenden**
   ![De groep Identiteitsveld toevoegen](assets/schemas-crm-addIdentityMixin.png)

Controleer of de veldgroep aan het schema is toegevoegd door zowel de API-reactie als de interface te controleren.

## Offline schema Aankoopgebeurtenissen maken

Laten we nu een schema maken op basis van het **[!UICONTROL Experience Event]** klasse voor de offlineaankoopgegevens van Luma. Aangezien u nu vertrouwd met het gebruikersinterface van de schemaredacteur wordt, zal ik het aantal screenshots in de instructies verminderen:

1. Een schema maken met de opdracht **[!UICONTROL Experience Event]** klasse.
1. Geef uw schema een naam `Luma Offline Purchase Events Schema`.
1. De standaardveldgroep toevoegen **[!UICONTROL Commerce Details]** om algemene orderdetails vast te leggen. Besteed een paar minuten om de objecten daarbinnen te verkennen.
1. Zoeken naar `Luma Identity profile field group`. Het is niet beschikbaar! Herinner dat de gebiedsgroepen aan een klasse gebonden zijn, en aangezien wij een verschillende klasse voor dit schema gebruiken kunnen wij het niet gebruiken. We moeten een nieuwe veldgroep toevoegen voor de klasse XDM ExperienceEvent die de identiteitsvelden bevat. Ons gegevenstype maakt dat echt gemakkelijk!
1. Selecteer de **[!UICONTROL Create new field group]** keuzerondje
1. Voer de **[!UICONTROL Display name]** als `Luma Identity ExperienceEvent field group` en selecteert u de **[!UICONTROL Add field groups]** knop
1. Selecteren **[!UICONTROL +]** naast de naam van het schema.
1. Als de **[!UICONTROL Field Name]**, enter `systemIdentifier`.
1. Als de **[!UICONTROL Display Name]**, enter `System Identifier`.
1. Als de **[!UICONTROL Type]**, selecteert u **Systeem-id** Dit is het aangepaste gegevenstype dat u eerder hebt gemaakt.
1. Als de **[!UICONTROL Field Group]** selecteren **Luma Identity ExperienceEvent, veldgroep**.
1. Selecteer de **[!UICONTROL Apply]** knop.
1. Selecteer de **[!UICONTROL Save]** knop.

Houd er rekening mee hoe het gegevenstype alle velden heeft toegevoegd!

![Het gegevenstype toevoegen aan de veldgroep](assets/schemas-offlinePurchases-addDatatype.png)

Selecteer ook **[!UICONTROL XDM ExperienceEvent]** onder de **[!UICONTROL Class]** enkele velden die door deze klasse worden toegevoegd, te doorlopen en te inspecteren. _id- en tijdstempelvelden zijn vereist bij gebruik van de XDM ExperienceEvent-klasse. Deze velden moeten worden ingevuld voor elke record die u opgeeft bij gebruik van dit schema:

![Basisstructuur van gebeurtenissen beleven](assets/schemas-offlinePurchase-experienceEventbase.png)

## Webgebeurtenissenschema maken

Nu gaan we nog een schema maken voor de websitegegevens van Luma. Op dit punt zou u een deskundige in het creëren van schema&#39;s moeten zijn! Het volgende schema samenstellen met deze eigenschappen

| Eigenschap | Waarde |
|---------------|-----------------|
| Klasse | Experience Event |
| Schemanaam | Luma-webgebeurtenissenschema |
| Veldgroep | AEP Web SDK ExperienceEvent |
| Veldgroep | Consumentenervaringsgebeurtenis |

Selecteer de **[!UICONTROL Consumer Experience Event]** veldgroep. Deze veldgroep bevat de objecten commerce en productListItems die zich ook in [!UICONTROL Commerce Details]. Inderdaad [!UICONTROL Consumer Experience Event] is een combinatie van verschillende andere standaardveldgroepen die ook afzonderlijk beschikbaar zijn. [!UICONTROL AEP Web SDK ExperienceEvent] de veldgroep bevat ook andere veldgroepen, waaronder enkele van dezelfde in [!UICONTROL Consumer Experience Event]. Gelukkig vloeien ze naadloos samen.

We hebben de `Luma Identity ExperienceEvent field group` naar dit schema. Dit komt doordat de SDK van het Web een andere manier heeft om identiteiten te verzamelen. Als u **[!UICONTROL XDM ExperienceEvent]** in de **[!UICONTROL Composition]** in de schema-editor. Een van de velden die standaard worden toegevoegd, wordt genoemd **[!UICONTROL IdentityMap]**. [!DNL IdentityMap] wordt gebruikt door diverse Adobe toepassingen om aan Platform te verbinden. U zult zien hoe identiteiten via identityMap naar Platform worden verzonden in de streaming opname les.


## Productcatalogusschema maken

Met de opdracht  [!UICONTROL Commerce Details] en [!UICONTROL Consumer Experience Event] veldgroepen. Luma rapporteert details van productgerelateerde gebeurtenissen via het standaardgegevenstype productListItems. Maar ze hebben ook extra productdetailvelden die ze naar Platform willen sturen. In plaats van al deze velden op te nemen in hun verkooppunten en e-commercesystemen, zou Luma liever deze velden rechtstreeks uit hun productcatalogussysteem innemen. Een &quot;schemaverhouding&quot;staat u toe om een verhouding tussen twee schema&#39;s voor classificaties of raadplegingen te bepalen. Luma gebruikt een relatie om hun productdetails in te delen. We beginnen het proces nu en voltooien het aan het einde van de volgende les.

>[!NOTE]
>
>Als u een bestaande klant van Analytics of van het Doel bent, is het classificeren van entiteiten met schemaverhoudingen analoog aan SAINT classificaties of het uploaden van uw productcatalogus voor Recommendations

Eerst moeten we een schema voor de productcatalogus van Luma maken met behulp van een aangepaste klasse:

1. Selecteer de **[!UICONTROL Create schema]** knop.
1. Selecteer in de workflow Schema maken de optie **[!UICONTROL Other]** -optie.
   ![Nieuw schema maken](assets/schemas-newSchema-browseClasses.png)
1. Selecteer de **[!UICONTROL Create class]** knop
1. Naam geven `Luma Product Catalog Class`
1. Laat de **[!UICONTROL Behavior]** als **[!UICONTROL Record]**
1. Selecteer de **[!UICONTROL Create]** knop.
   ![Nieuwe klasse maken](assets/schemas-productClass.png)
1. De **Luminageproductcatalogus, klasse** u hebt gecreeerd verschijnt in de lijst van Klassen hieronder. Zorg ervoor dat de klasse is geselecteerd en selecteer vervolgens **[!UICONTROL Next]**.
   ![Nieuwe klasse toegevoegd](assets/schemas-productClassSelected.png)
1. Geef het schema een naam `Luma Product Catalog Schema`.
1. Een nieuwe [!UICONTROL field group] gebeld `Luma Product Catalog field group` met de volgende velden:
   1. productName: Product Name: String
   1. productCategorie: Productcategorie: String
   1. productColor: Product Color: String
   1. productSku: Product SKU: String | Vereist
   1. productSize : Product Size : String
   1. productPrice: Product Price: Double
1. **[!UICONTROL Save]** het schema

Uw nieuwe schema zou als dit moeten kijken. Let op het volgende: `productSku` wordt weergegeven in het dialoogvenster [!UICONTROL Required fields] sectie:
![Productschema](assets/schemas-productSchema.png)

De volgende stap bestaat uit het definiëren van de relatie tussen de twee ExperienceEvent-schema&#39;s en de `Luma Product Catalog Schema`Er zijn echter nog een paar extra stappen die we in de volgende les moeten zetten voordat we dat kunnen doen.


## Aanvullende bronnen

* [XDM-systeemdocumentatie (Experience Data Model)](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=nl)
* [Schema-register-API](https://www.adobe.io/experience-platform-apis/references/schema-registry/)


Nu hebt u uw schema&#39;s u kunt [map-id&#39;s](map-identities.md)!

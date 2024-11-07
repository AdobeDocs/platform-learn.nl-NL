---
title: Intelligente services - Voorbereiding van AI-gegevens van klanten (Ingest)
description: AI van de klant - Gegevensvoorbereiding (samenvatting)
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# 2.2.1 AI van klant - Gegevensvoorbereiding (overzicht)

Om de Intelligente Diensten inzichten van uw marketing gebeurtenisgegevens te ontdekken, moeten de gegevens semantisch worden verrijkt en in een standaardstructuur worden gehandhaafd. Intelligent Services gebruikt de schema&#39;s van het Model van de Gegevens van de Ervaring van de Adobe (XDM) om dit te bereiken.
Specifiek, moeten alle datasets die in de Intelligente Diensten worden gebruikt met het **schema van XDM van de Gebeurtenis van de Consumentenervaring** in overeenstemming zijn.

## 2.2.1.1 Schema maken

In deze oefening, zult u een schema tot stand brengen dat de **mix van de Gebeurtenis van de Ervaring van de Consumenten** bevat, die door de **Intelligente Dienst van de Klant AI** wordt vereist.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](../../datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--module10sandbox--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](../../datacollection/module1.2/images/sb1.png)

Van het linkermenu, klik **Schema&#39;s** en ga **doorbladeren**. Klik **creëren Schema**.

![ creeer nieuw schema ](./images/create-schema-button.png)

In popup, uitgezochte **XDM ExperienceEvent**.

![ creeer nieuw schema ](./images/xdmee.png)

Dan zie je dit.

![ creeer nieuw schema ](./images/xdmee1.png)

Onderzoek en selecteer de volgende **Mixins** om aan dit Schema toe te voegen:

- Consumentenervaringsgebeurtenis

  ![ Nieuw CEE schema ](./images/cee.png)

- Gegevens van eindgebruiker

  ![ Nieuw CEE schema ](./images/identitymap.png)

Klik **toevoegen de Groepen van het Gebied**.

![ de zeer belangrijke definitie van de Identiteit ](./images/addmixin.png)

Dan zie je dit. Selecteer de Gegevens van de Gebruiker van het Eind van de Mixin ****.

![ creeer nieuw schema ](./images/eui1.png)

Ga aan het gebied **endUserIDs._experience.emailid.id**.

![ creeer nieuw schema ](./images/eui2.png)

In het juiste menu voor het gebied **endUserIDs._experience.emailid.id**, scrol neer en controleer checkbox voor **Identiteit**, controleer checkbox voor **Primaire Identiteit** en selecteer **Identiteit namespace** van **E-mail**.

![ creeer nieuw schema ](./images/eui3.png)

Ga aan het gebied **endUserIDs._experience.mcid.id**. Controleer checkbox voor **Identiteit** en selecteer **Identiteit namespace** van **ECID**. Klik **toepassen**.

![ creeer nieuw schema ](./images/eui4.png)

Geef uw schema nu een naam.

Als naam voor ons schema, zult u dit gebruiken:

- `--demoProfileLdap-- - Demo System - Customer Experience Event`

Als voorbeeld, voor ldap **vangeluw**, zou dit de naam van het schema moeten zijn:

- **vangeluw - het Systeem van de Demo - de Gebeurtenis van de Ervaring van de Klant**

Dat zou je iets dergelijks moeten geven. Klik **+ toevoegen** knoop om nieuwe **Mixins** toe te voegen.

![ creeer nieuw schema ](./images/xdmee2.png)

Selecteer de naam van het schema. U zou uw schema voor **Profiel** nu moeten toelaten, door de **knevel van het Profiel** te klikken.

![ creeer nieuw schema ](./images/xdmee3.png)

Dan zie je dit. Klik **toelaten**.

![ creeer nieuw schema ](./images/xdmee4.png)

Dat zou u nu moeten doen. Klik **sparen** om uw schema te bewaren.

![ creeer nieuw schema ](./images/xdmee5.png)

## 2.2.1.2 Gegevensset maken

Van het linkermenu, klik **Datasets** en ga **doorbladeren**. Klik **creëren dataset**.

![ Dataset ](./images/createds.png)

Klik **creëren dataset van schema**.

![ Dataset ](./images/createdatasetfromschema.png)

In het volgende scherm, selecteer de dataset u in de vorige oefening creeerde, die **[!UICONTROL ldap - Demo System - Customer Experience Event]** wordt genoemd. Klik **daarna**.

![ Dataset ](./images/createds1.png)

Gebruik `--demoProfileLdap-- - Demo System - Customer Experience Event Dataset` als naam voor uw gegevensset. Klik **Afwerking**.

![ Dataset ](./images/createds2.png)

Uw dataset wordt nu gecreeerd. Laat de **knevel van het Profiel** toe.

![ Dataset ](./images/createds3.png)

Klik **toelaten**.

![ Dataset ](./images/createds4.png)

U zou nu het volgende moeten hebben:

![ Dataset ](./images/createds5.png)

U bent nu klaar om gegevens van de Gebeurtenis van de Ervaring van de Consumenten te beginnen en de dienst van AI van de Klant te gebruiken.

## 2.2.1.3 Testgegevens van downloadervaring

Zodra het **Schema** en **Dataset** worden gevormd, bent u nu klaar om de gegevens van de Gebeurtenis van de Ervaring in te voeren. Aangezien AI van de Klant gegevens over **2 kwartalen minstens** vereist, zult u extern voorbereide gegevens moeten opnemen.

De gegevens die voor de ervaringsgebeurtenissen worden voorbereid moeten aan de vereisten en het schema van de [ Mixin van de Gebeurtenis XDM van de Ervaring van de Consumenten ](https://github.com/adobe/xdm/blob/797cf4930d5a80799a095256302675b1362c9a15/docs/reference/context/experienceevent-consumer.schema.md) voldoen.

Gelieve te downloaden het dossier dat steekproefgegevens van deze plaats bevat: [ https://dashboard.adobedemo.com/data](https://dashboard.adobedemo.com/data). Klik de **knoop van de Download**.

![ Dataset ](./images/dsn1.png)

Alternatief, als u tot de bovengenoemde verbinding niet kunt toegang hebben, kunt u het dossier ook van deze plaats downloaden: [ https://aepmodule10.s3-us-west-2.amazonaws.com/retail-v1-dec2020-xl.json.zip ](https://aepmodule10.s3-us-west-2.amazonaws.com/retail-v1-dec2020-xl.json.zip).

U hebt nu een dossier genoemd **retail-v1-dec2020-xl.json.zip** gedownload. Plaats het dossier op de Desktop van uw computer en unzip het, waarna zult u een dossier genoemd **retail-v1.json** zien. U hebt dit bestand nodig in de volgende oefening.

![ Dataset ](./images/ingest.png)

## 2.2.1.4 Testgegevens over gebeurtenissen met het overzicht

In Adobe Experience Platform, ga naar **Datasets** en open uw dataset, die **[!UICONTROL ldap - Demo System - Customer Experience Event Dataset]** wordt genoemd.

![ Dataset ](./images/ingest1.png)

In uw dataset, kiest de klik **dossiers** om gegevens toe te voegen.

![ Dataset ](./images/ingest2.png)

In popup, selecteer het dossier **retail-v1.json** en klik **Open**.

![ Dataset ](./images/ingest3.png)

U zult dan de gegevens zien die worden ingevoerd, en een nieuwe partij wordt gecreeerd in de **Lading** staat. Navigeer niet van deze pagina weg tot het dossier wordt geupload.

![ Dataset ](./images/ingest4.png)

Zodra het dossier is geupload, zult u de verandering van de partijstatus van **het Lading** aan **Verwerking** zien.

![ Dataset ](./images/ingest5.png)

Het installeren en verwerken van de gegevens kan 10 tot 20 minuten duren.

Zodra gegevensopname succesvol is, zal de partijstatus in **Succes** veranderen.

![ Dataset ](./images/ingest7.png)

![ Dataset ](./images/ingest8.png)

Volgende Stap: [ 2.2.2 Klant AI - creeer een Nieuwe Instantie (vorm) ](./ex2.md)

[Terug naar module 2.2](./intelligent-services.md)

[Terug naar alle modules](./../../../overview.md)

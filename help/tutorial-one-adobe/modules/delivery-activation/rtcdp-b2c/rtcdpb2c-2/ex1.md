---
title: Intelligente services - Voorbereiding van AI-gegevens van klanten (Ingest)
description: AI van de klant - Gegevensvoorbereiding (samenvatting)
kt: 5342
doc-type: tutorial
exl-id: 2b49d86a-af75-4ecd-ab3f-0182f3b8da2f
source-git-commit: 15adbf950115f0b6bb6613e69a60b310f25de058
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# 2.2.1 AI van klant - Gegevensvoorbereiding (overzicht)

Om de Intelligente Diensten inzichten van uw marketing gebeurtenisgegevens te ontdekken, moeten de gegevens semantisch worden verrijkt en in een standaardstructuur worden gehandhaafd. Intelligent Services gebruikt de schema&#39;s van het Model van de Gegevens van de Ervaring van Adobe (XDM) om dit te bereiken.
Specifiek, moeten alle datasets die in de Intelligente Diensten worden gebruikt met het **schema van XDM van de Gebeurtenis van de Consumentenervaring** in overeenstemming zijn.

## Schema maken

In deze oefening, zult u een schema tot stand brengen dat de **mix van de Gebeurtenis van de Ervaring van de Consumenten** bevat, die door de **Intelligente Dienst van de Klant AI** wordt vereist.

Login aan Adobe Experience Platform door naar dit URL te gaan: [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](../../datacollection/dc1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![&#x200B; Ingestie van Gegevens &#x200B;](../../datacollection/dc1.2/images/sb1.png)

Van het linkermenu, klik **Schema&#39;s** en ga **doorbladeren**. Klik **creëren Schema**.

![&#x200B; creeer nieuw schema &#x200B;](./images/createschemabutton.png)

In popup, uitgezochte **Handboek** en klik **Uitgezocht**.

![&#x200B; creeer nieuw schema &#x200B;](./images/schmanual.png)

Daarna, uitgezochte **Gebeurtenis van de Ervaring** en klik **daarna**.

![&#x200B; creeer nieuw schema &#x200B;](./images/xdmee.png)

U moet nu een naam voor uw schema opgeven. Als naam voor ons schema, gebruik dit: `--aepUserLdap-- - Demo System - Customer Experience Event` en klik **Afwerking**.

![&#x200B; creeer nieuw schema &#x200B;](./images/schname.png)

Dan zie je dit. Klik op **+ Toevoegen** onder Veldgroepen.

![&#x200B; creeer nieuw schema &#x200B;](./images/xdmee1.png)

Onderzoek en selecteer de volgende **Groepen van het Gebied** om aan dit Schema toe te voegen:

- Consumentenervaringsgebeurtenis

![&#x200B; Nieuw CEE schema &#x200B;](./images/cee1.png)

- IdentityMap

Klik **toevoegen de Groepen van het Gebied**.

![&#x200B; Nieuw CEE schema &#x200B;](./images/cee2.png)

Dan zie je dit. Selecteer vervolgens de naam van het schema. U zou uw schema voor **Profiel** nu moeten toelaten, door de **knevel van het Profiel** te klikken.

![&#x200B; creeer nieuw schema &#x200B;](./images/xdmee3.png)

Dan zie je dit. Controle checkbox voor **Gegevens voor dit schema zal een primaire identiteit op het identityMap gebied bevatten.**. Klik **toelaten**.

![&#x200B; creeer nieuw schema &#x200B;](./images/xdmee4.png)

Dat zou u nu moeten doen. Klik **sparen** om uw schema te bewaren.

![&#x200B; creeer nieuw schema &#x200B;](./images/xdmee5.png)

## Gegevensset maken

Van het linkermenu, klik **Datasets** en ga **doorbladeren**. Klik **creëren dataset**.

![&#x200B; Dataset &#x200B;](./images/createds.png)

Klik **creëren dataset van schema**.

![&#x200B; Dataset &#x200B;](./images/createdatasetfromschema.png)

In het volgende scherm, selecteer de dataset u in de vorige oefening creeerde, die `--aepUserLdap-- - Demo System - Customer Experience Event` wordt genoemd. Klik **daarna**.

![&#x200B; Dataset &#x200B;](./images/createds1.png)

Gebruik `--aepUserLdap-- - Demo System - Customer Experience Event Dataset` als naam voor uw gegevensset. Klik **Afwerking**.

![&#x200B; Dataset &#x200B;](./images/createds2.png)

Uw dataset wordt nu gecreeerd. Laat de **knevel van het Profiel** toe.

![&#x200B; Dataset &#x200B;](./images/createds3.png)

Klik **toelaten**.

![&#x200B; Dataset &#x200B;](./images/createds4.png)

U zou nu het volgende moeten hebben:

![&#x200B; Dataset &#x200B;](./images/createds5.png)

U bent nu klaar om gegevens van de Gebeurtenis van de Ervaring van de Consumenten te beginnen en de dienst van AI van de Klant te gebruiken.

## Testgegevens van Gebeurtenis downloaden

Zodra het **Schema** en **Dataset** worden gevormd, bent u nu klaar om de gegevens van de Gebeurtenis van de Ervaring in te voeren. Aangezien voor AI specifieke gegevensvereisten zijn vereist, moet u extern voorbereide gegevens invoeren.

De gegevens die voor de ervaringsgebeurtenissen in deze oefening worden voorbereid moeten aan de vereisten en het schema van de [&#x200B; Groep van het Gebied van de Gebeurtenis XDM van de Consumentenervaring &#x200B;](https://github.com/adobe/xdm/blob/797cf4930d5a80799a095256302675b1362c9a15/docs/reference/context/experienceevent-consumer.schema.md) voldoen.

Gelieve te downloaden het zip dossier met demo gegevens van deze plaats: [&#x200B; https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/CUSTOM-CAI-EVENTS-WEB.zip &#x200B;](https://one-adobe-tech-insiders.s3.us-west-2.amazonaws.com/CUSTOM-CAI-EVENTS-WEB.zip).

U hebt nu een dossier genoemd **CUSTOM-CAI-EVENTS-WEB.zip** gedownload. Plaats het dossier op de Desktop van uw computer en unzip het, waarna zult u een omslag genoemd **CUSTOM-CAI-EVENTS-WEB** zien.

![&#x200B; Dataset &#x200B;](./images/ingest.png)

In die omslag, zult u veelvoudige geordende JSON dossiers vinden, die allen in de volgende oefening moeten worden opgenomen.

![&#x200B; Dataset &#x200B;](./images/ingest1a.png)

## Testgegevens van Ingest Experience Event

In Adobe Experience Platform, ga naar **Datasets** en open uw dataset, die **[!UICONTROL ldap - Demo System - Customer Experience Event Dataset]** wordt genoemd.

![&#x200B; Dataset &#x200B;](./images/ingest1.png)

In uw dataset, kiest de klik **dossiers** om gegevens toe te voegen.

![&#x200B; Dataset &#x200B;](./images/ingest2.png)

In popup, selecteer de dossiers **WEBSITE-EE-1.json** tot **WEBSITE-EE-5.json** en klik **Open**.

![&#x200B; Dataset &#x200B;](./images/ingest3.png)

Herhaal dit insluitingsproces voor de dossiers **WEBSITE-EE-6.json** en **WEBSITE-EE-7.json**.

U zult dan de gegevens zien die worden ingevoerd, en een nieuwe partij wordt gecreeerd in de **Lading** staat. Navigeer niet van deze pagina weg tot het dossier wordt geupload.

![&#x200B; Dataset &#x200B;](./images/ingest4.png)

Zodra het dossier is geupload, zult u de verandering van de partijstatus van **het Lading** aan **Verwerking** zien.

![&#x200B; Dataset &#x200B;](./images/ingest5.png)

Het installeren en verwerken van de gegevens kan 10 tot 20 minuten duren.

Zodra gegevensopname succesvol is, zal de partijstatus van diverse uploads in **Succes** veranderen.

![&#x200B; Dataset &#x200B;](./images/ingest7.png)

## Volgende stappen

Ga naar [&#x200B; 2.2.2 Klant AI - creeer een Nieuwe Instantie (vorm) &#x200B;](./ex2.md){target="_blank"}

Ga terug naar [&#x200B; Intelligente Diensten &#x200B;](./intelligent-services.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

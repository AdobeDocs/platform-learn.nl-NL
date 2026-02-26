---
title: De stichting van uw relationele gegevens instellen
description: De stichting van uw relationele gegevens instellen
kt: 5342
doc-type: tutorial
exl-id: 532e5f2c-971f-488f-bef4-3a8141408cc8
source-git-commit: defdae3329e1409159f59c4a0ef2aa21c7e3949b
workflow-type: tm+mt
source-wordcount: '2159'
ht-degree: 0%

---

# 3.8.1 De stichting van uw relationele gegevens instellen

Login aan Adobe Journey Optimizer door naar [&#x200B; https://experience.adobe.com &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; AJO OC &#x200B;](./images/aechome.png)

U zult aan de **1&rbrace; mening van het Huis &lbrace;in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![&#x200B; AJO OC &#x200B;](./images/ajohome.png)

## 3.8.1.1 Instellingen voor relationeel schema

Een relationeel-gebaseerd schema is de formele definitie van het op model-gebaseerde gegevensmodel.

Hier wordt aangegeven:

- De reeks tabellen
- De kolommen in elke tabel
- De beperkingen
- De relaties tussen tabellen

Het organiseren van schema&#39;s of lijsten in een model-gebaseerd gegevensmodel is over het structureren van uw gegevens in veelvoudige lijsten. Zorg ervoor dat elke tabel één type entiteit/schema&#39;s opslaat.

Bij het opnemen van gegevens in voor gebruik met Adobe Journey Optimizer Orchestrated Campaigns zijn de volgende bronnen beschikbaar:

- Amazon S3
- Google Cloud Storage
- SFTP
- Snowflake
- Google BigQuery
- Gegevenslandingszone
- Azure Databricks
- Lokaal bestand uploaden

De eerste stap in deze oefening is de configuratie van uw op relationele-Gebaseerde schema&#39;s XDM. In het linkermenu, scrol neer aan **Beheer van Gegevens** en selecteer **Schema&#39;s**. Klik op **+ Schema maken** .

![&#x200B; AJO OC &#x200B;](./images/ajoocdata1.png)

Selecteer **Relationeel**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata2.png)

Selecteer **uploadt Ddl- dossier** en klik dan **kiezen dossiers**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata3.png)

Download het dossier [&#x200B; burgersignaal_ddl_tables_only.sql &#x200B;](./assets/citisignal_ddl_tables_only.sql) aan uw Desktop.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata4.png)

Selecteer het dossier **`citisignal_ddl_tables_only.sql`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata5.png)

Dan moet je dit zien. Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata6.png)

### Identiteit

Sommige van uw schema&#39;s bevatten persoonlijke herkenningstekens en die gebieden zouden als **Identiteit** moeten worden gemerkt, en u moet **Namespace** selecteren die op dat specifieke type van identiteit van toepassing is.

**`citisignal_accounts`**

Voor dit schema, ga naar het gebied **account_id** en plaats het **Type van Identiteit** aan **Systeem van de Manifestatie - CRMID**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata7.png)

**`citisignal_recipients`**

Voor dit schema, ga naar het gebied **account_id** en plaats het **Type van Identiteit** aan **het Systeem van de Manifestatie - CRMID** en ga naar het gebied **e-mail** en plaats het **type van Identiteit** aan **E-mail**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata8.png)

### Versioning

Om updates van de gegevens bij te houden die tegen deze schema&#39;s zullen worden opgenomen, is het vereist om een gebied te plaatsen dat zal worden gebruikt om de versie van de geuploade gegevens te volgen. Het gebied dat voor dit in al deze schema&#39;s wordt gebruikt is het gebied **laatst gewijzigd**, dat timestamp van de geuploade gegevens bevat.

U moet nu checkbox voor **Versioning** voor het gebied **laatst gewijzigd** in elk van deze schema&#39;s controleren.

**`citisignal_products`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata9.png)

**`citisignal_product_bundles`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata10.png)

**`citisignal_product_relationships`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata11.png)

**`citisignal_accounts`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata12.png)

**`citisignal_recipients`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata13.png)

**`citisignal_mobile_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata14.png)

**`citisignal_internet_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata15.png)

**`citisignal_tv_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata16.png)

**`citisignal_equipment_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata17.png)

**`citisignal_mobile_usage_summary`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata18.png)

**`citisignal_internet_usage_summary`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata19.png)

**`citisignal_offers`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata20.png)

**`citisignal_offer_eligibility`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata21.png)

### Schemanaam

Wanneer u deze schema&#39;s opneemt voor activering in een gedeelde sandbox, moet u de naam van elk schema wijzigen zodat het uniek is in die specifieke sandbox. De reden voor deze wijziging is om conflicten met schemanamen te voorkomen.

Voor dit laboratorium, zou u uw LDAP vóór elke schemanaam moeten toevoegen, wat betekent dat elke schemanaam dit voorvoegsel zou moeten hebben: `--aepUserLdap--_`

**`citisignal_products`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_products`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan9.png)

**`citisignal_product_bundles`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_product_bundles`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan10.png)

**`citisignal_product_relationships`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_product_relationships`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan11.png)

**`citisignal_accounts`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_accounts`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan12.png)

**`citisignal_recipients`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_recipients`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan13.png)

**`citisignal_mobile_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_mobile_subscriptions`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan14.png)

**`citisignal_internet_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_subscriptions`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan15.png)

**`citisignal_tv_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_subscriptions`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan16.png)

**`citisignal_equipment_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_equipment_subscriptions`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan17.png)

**`citisignal_mobile_usage_summary`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_mobile_usage_summary`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan18.png)

**`citisignal_internet_usage_summary`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_usage_summary`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan19.png)

**`citisignal_offers`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_offers`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan20.png)

**`citisignal_offer_eligibility`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_offer_eligibility`.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatan21.png)

Uw schema&#39;s kunnen nu worden opgeslagen. Klik **Gedaan**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata22.png)

Dan moet je dit zien. Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata23.png)

Klik **Open banen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata24.png)

Dan moet je dit zien. U moet wachten tot de taak met succes is voltooid voordat u verdergaat met de volgende stap.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata25.png)

Als de taak met succes is voltooid, kunt u verdergaan met de volgende stap. Dit kan 5-10 minuten duren.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata26.png)

Nu uw relationele schema&#39;s XDM en met gegevens worden gevormd die worden opgenomen, kunt u beginnen die gegevens te gebruiken om uw georkestreerde campagne in de volgende oefening tot stand te brengen.

## 3.8.1.2 Gegevensinvoer

Ga naar **Datasets**. U zou dan een dataset moeten zien die voor elk schema werd gecreeerd dat u creeerde.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata27.png)

Download het dossier [&#x200B; data.zip &#x200B;](./assets/data.zip) aan uw Desktop en decomprimeer het.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata28.png)

Open de omslag **gegevens**. U zou een CSV dossier voor elk van de schema&#39;s moeten zien die werden gecreeerd. U moet nu die gegevens in elke overeenkomstige dataset uploaden. Voor dit laboratorium, zult u dat doen door een lokaal dossier te doen uploadt in elke dataset.

![&#x200B; AJO OC &#x200B;](./images/ajoocdata29.png)

**`vangeluw_citisignal_products`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_products` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas9a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_products.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas9b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas9c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas9d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas9e.png)

**`vangeluw_citisignal_product_bundles`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_product_bundles` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_product_bundles.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10e.png)

**`vangeluw_citisignal_product_relationships`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_product_relationships` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas11a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_product_relationships.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas11b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas11c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas11d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas11e.png)

**`vangeluw_citisignal_accounts`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_accounts` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas12a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_accounts.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas12b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas12c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas12d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas12e.png)

**`vangeluw_citisignal_recipients`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_recipients` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas13a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_recipients.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas13b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas13c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas13d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas13e.png)

**`vangeluw_citisignal_mobile_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_mobile_subscriptions` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas14a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_mobile_subscriptions.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas14b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas14c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas14d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas14e.png)

**`vangeluw_citisignal_internet_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_internet_subscriptions` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas15a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_internet_subscriptions.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas15b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas15c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas15d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas15e.png)

**`vangeluw_citisignal_tv_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_tv_subscriptions` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas16a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_tv_subscriptions.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas16b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas16c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas16d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas16e.png)

**`vangeluw_citisignal_equipment_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_equipment_subscriptions` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas17a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_equipment_subscriptions.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas17b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas17c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas17d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas17e.png)

**`vangeluw_citisignal_mobile_usage_summary`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_mobile_usage_summary` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas18a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_mobile_usage_summary.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas18b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas18c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas18d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas18e.png)

**`vangeluw_citisignal_internet_usage_summary`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_internet_usage_summary` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas19a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_internet_usage_summary.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas19b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas19c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas19d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas19e.png)

**`vangeluw_citisignal_offers`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_offers` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas20a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_offers.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas20b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas20c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas20d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas20e.png)

**`vangeluw_citisignal_offer_eligibility`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_offer_eligibility` .

Klik **daarna**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas21a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_offer_eligibility.csv`** en klik **open**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas21b.png)

Klik **daarna**

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas21c.png)

Klik **Afwerking**.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas21d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![&#x200B; AJO OC &#x200B;](./images/ajoocdatas21e.png)

Alle gegevens worden nu opgenomen.

## 3.8.1.3 Profieldoel Dimension

Met Geordende Campagnes, kunt u gerichte mededelingen op entiteitniveau ontwerpen en leveren, leveraging Adobe Experience Platform&#39;s relationele schemamogelijkheden. Experience Platform gebruikt schema&#39;s om de gegevensstructuur op een consistente en herbruikbare manier te beschrijven. Wanneer gegevens in Experience Platform worden opgenomen, worden ze gestructureerd volgens een XDM-schema.

Hoewel de segmentatie voor Geordende Campagnes hoofdzakelijk op relationele regelingen werkt, komt de daadwerkelijke berichtlevering altijd op het niveau van het Profiel voor.

Wanneer het vormen richt, bepaalt u twee zeer belangrijke aspecten:

- Doelschema&#39;s: u geeft op welke relationele schema&#39;s geschikt zijn voor doelframes. Standaard wordt het schema met de naam Ontvanger gebruikt, maar u kunt alternatieven configureren, zoals Bezoekers, Klanten enzovoort.

- Profielkoppeling: het systeem moet begrijpen hoe het doelschema wordt toegewezen aan het profielschema. Dit wordt bereikt door een gedeeld identiteitsgebied — dat zowel in het doelschema als het schema van het Profiel bestaat en als identiteit namespace wordt gevormd.

U moet nu uw afmetingen van het Doel van het Profiel vormen. Ga naar **Beleid** > **Configuratie** en klik dan **leiden** onder **het Doel Dimension van het Profiel**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd1.png)

Dan moet je dit zien. Klik **creëren**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd2.png)

Voor het **Schema**, uitgezochte `--aepUserLdap--_citisignal_accounts`. Voor de **waarde van de Identiteit**, uitgezochte **account_id**.

Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd3.png)

Klik **creeer opnieuw**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd4.png)

Voor het **Schema**, uitgezochte `--aepUserLdap--_citisignal_recipients`. Voor de **waarde van de Identiteit**, uitgezochte **account_id**.

Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd5.png)

Klik **creeer opnieuw**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd6.png)

Voor het **Schema**, uitgezochte `--aepUserLdap--_citisignal_recipients`. Voor de **waarde van de Identiteit**, uitgezochte **e-mail**.

Klik **sparen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd7.png)

Dan moet je dit hebben.

![&#x200B; AJO OC &#x200B;](./images/ajoocptd8.png)

## 3.8.1.4 Email channel

In het linkermenu, ga naar **Kanalen**. Klik **creeer kanaalconfiguratie**.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel1.png)

Gebruik de naam: `--aepUserLdap---citisignal-email-oc` . Selecteer het kanaal **E-mail**

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel2.png)

Selecteer een beschikbare **subdomain** en **IP pool**.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel3.png)

De rol neer en vult de **parameters van de Kopbal** uit.

- **van naam**: `info@techinsiders.org`
- **van e-mailprefix**: `info`
- **Antwoord aan naam**: `info@techinsiders.org`
- **Antwoord aan e-mail**: `info@techinsiders.org`
- **E-mailprefix van de Fout**: `error`

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel4.png)

Omlaag schuiven. Ga naar **Geordende campagne**. Controle checkbox voor **Toegelaten**. Selecteer **het richten dimensie**.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel5.png)

Voor **het Doel Dimension van het Profiel**, uitgezochte `--aepUserLdap--_citisignal_recipients - email`.

Selecteer **Dimension van het Doel** en klik het **open omslag** pictogram.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel6.png)

Klik op `--aepUserLdap--_citisignal_recipients`.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel7.png)

Selecteer het gebied **e-mail** en klik **Uitgezocht**.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel8.png)

De rol omhoog en klikt **voorleggen**.

![&#x200B; AJO OC &#x200B;](./images/ajoocchannel9.png)

In de volgende oefening zult u beginnen om die gegevens als deel van een georkestreerde campagne te gebruiken.

## Volgende stappen

Ga naar [&#x200B; creeer uw georkestreerde campagne &#x200B;](./ex2.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Journey Optimizer: Geordende Campagnes &#x200B;](./ajocampaigns.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

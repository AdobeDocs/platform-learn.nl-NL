---
title: De stichting van uw relationele gegevens instellen
description: De stichting van uw relationele gegevens instellen
kt: 5342
doc-type: tutorial
exl-id: 532e5f2c-971f-488f-bef4-3a8141408cc8
source-git-commit: 7a595d9b1fb3dc6a3b5b413e65dbaaaf5ac143c4
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---

# 3.8.1 De stichting van uw relationele gegevens instellen

Login aan Adobe Journey Optimizer door naar [ https://experience.adobe.com ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ AJO OC ](./images/aechome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![ AJO OC ](./images/ajohome.png)

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

![ AJO OC ](./images/ajoocdata1.png)

Selecteer **Relationeel**.

![ AJO OC ](./images/ajoocdata2.png)

Selecteer **uploadt Ddl- dossier** en klik dan **kiezen dossiers**.

![ AJO OC ](./images/ajoocdata3.png)

Download het dossier [ burgersignaal_ddl_tables_only.sql ](./assets/citisignal_ddl_tables_only.sql) aan uw Desktop.

![ AJO OC ](./images/ajoocdata4.png)

Selecteer het dossier **`citisignal_ddl_tables_only.sql`** en klik **open**.

![ AJO OC ](./images/ajoocdata5.png)

Dan moet je dit zien. Klik **daarna**.

![ AJO OC ](./images/ajoocdata6.png)

### Identiteit

Sommige van uw schema&#39;s bevatten persoonlijke herkenningstekens en die gebieden zouden als **Identiteit** moeten worden gemerkt, en u moet **Namespace** selecteren die op dat specifieke type van identiteit van toepassing is.

**`citisignal_accounts`**

Voor dit schema, ga naar het gebied **account_id** en plaats het **Type van Identiteit** aan **Systeem van de Manifestatie - CRMID**.

![ AJO OC ](./images/ajoocdata7.png)

**`citisignal_recipients`**

Voor dit schema, ga naar het gebied **account_id** en plaats het **Type van Identiteit** aan **het Systeem van de Manifestatie - CRMID** en ga naar het gebied **e-mail** en plaats het **type van Identiteit** aan **E-mail**.

![ AJO OC ](./images/ajoocdata8.png)

### Versioning

Om updates van de gegevens bij te houden die tegen deze schema&#39;s zullen worden opgenomen, is het vereist om een gebied te plaatsen dat zal worden gebruikt om de versie van de geuploade gegevens te volgen. Het gebied dat voor dit in al deze schema&#39;s wordt gebruikt is het gebied **laatst gewijzigd**, dat timestamp van de geuploade gegevens bevat.

U moet nu checkbox voor **Versioning** voor het gebied **laatst gewijzigd** in elk van deze schema&#39;s controleren.

**`citisignal_products`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata9.png)

**`citisignal_product_bundles`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata10.png)

**`citisignal_product_relationships`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata11.png)

**`citisignal_accounts`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata12.png)

**`citisignal_recipients`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata13.png)

**`citisignal_mobile_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata14.png)

**`citisignal_internet_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata15.png)

**`citisignal_tv_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata16.png)

**`citisignal_equipment_subscriptions`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata17.png)

**`citisignal_mobile_usage_summary`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata18.png)

**`citisignal_internet_usage_summary`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata19.png)

**`citisignal_offers`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata20.png)

**`citisignal_offer_eligibility`**

Controleer checkbox voor **Versioning** voor het gebied **laatst gewijzigd**.

![ AJO OC ](./images/ajoocdata21.png)

### Schemanaam

Wanneer u deze schema&#39;s opneemt voor activering in een gedeelde sandbox, moet u de naam van elk schema wijzigen zodat het uniek is in die specifieke sandbox. De reden voor deze wijziging is om conflicten met schemanamen te voorkomen.

Voor dit laboratorium, zou u uw LDAP vóór elke schemanaam moeten toevoegen, wat betekent dat elke schemanaam dit voorvoegsel zou moeten hebben: `--aepUserLdap--_`

**`citisignal_products`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_products`.

![ AJO OC ](./images/ajoocdatan9.png)

**`citisignal_product_bundles`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_product_bundles`.

![ AJO OC ](./images/ajoocdatan10.png)

**`citisignal_product_relationships`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_product_relationships`.

![ AJO OC ](./images/ajoocdatan11.png)

**`citisignal_accounts`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_accounts`.

![ AJO OC ](./images/ajoocdatan12.png)

**`citisignal_recipients`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_recipients`.

![ AJO OC ](./images/ajoocdatan13.png)

**`citisignal_mobile_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_mobile_subscriptions`.

![ AJO OC ](./images/ajoocdatan14.png)

**`citisignal_internet_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_subscriptions`.

![ AJO OC ](./images/ajoocdatan15.png)

**`citisignal_tv_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_subscriptions`.

![ AJO OC ](./images/ajoocdatan16.png)

**`citisignal_equipment_subscriptions`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_equipment_subscriptions`.

![ AJO OC ](./images/ajoocdatan17.png)

**`citisignal_mobile_usage_summary`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_mobile_usage_summary`.

![ AJO OC ](./images/ajoocdatan18.png)

**`citisignal_internet_usage_summary`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_internet_usage_summary`.

![ AJO OC ](./images/ajoocdatan19.png)

**`citisignal_offers`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_offers`.

![ AJO OC ](./images/ajoocdatan20.png)

**`citisignal_offer_eligibility`**

Verander de naam van uw schema in `--aepUserLdap--_ citisignal_offer_eligibility`.

![ AJO OC ](./images/ajoocdatan21.png)

Uw schema&#39;s kunnen nu worden opgeslagen. Klik **Gedaan**.

![ AJO OC ](./images/ajoocdata22.png)

Dan moet je dit zien. Klik **sparen**.

![ AJO OC ](./images/ajoocdata23.png)

Klik **Open banen**.

![ AJO OC ](./images/ajoocdata24.png)

Dan moet je dit zien. U moet wachten tot de taak met succes is voltooid voordat u verdergaat met de volgende stap.

![ AJO OC ](./images/ajoocdata25.png)

Als de taak met succes is voltooid, kunt u verdergaan met de volgende stap. Dit kan 5-10 minuten duren.

![ AJO OC ](./images/ajoocdata26.png)

Nu uw relationele schema&#39;s XDM en met gegevens worden gevormd die worden opgenomen, kunt u beginnen die gegevens te gebruiken om uw georkestreerde campagne in de volgende oefening tot stand te brengen.

## 3.8.1.2 Gegevensinvoer

Ga naar **Datasets**. U zou dan een dataset moeten zien die voor elk schema werd gecreeerd dat u creeerde.

![ AJO OC ](./images/ajoocdata27.png)

Download het dossier [ data.zip ](./assets/data.zip) aan uw Desktop en decomprimeer het.

![ AJO OC ](./images/ajoocdata28.png)

Open de omslag **gegevens**. U zou een CSV dossier voor elk van de schema&#39;s moeten zien die werden gecreeerd. U moet nu die gegevens in elke overeenkomstige dataset uploaden. Voor dit laboratorium, zult u dat doen door een lokaal dossier te doen uploadt in elke dataset.

![ AJO OC ](./images/ajoocdata29.png)

**`vangeluw_citisignal_products`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_products` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas9a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_products.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas9b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas9c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas9d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas9e.png)

**`vangeluw_citisignal_product_bundles`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_product_bundles` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas10a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_product_bundles.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas10b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas10c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas10d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas10e.png)

**`vangeluw_citisignal_product_relationships`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_product_relationships` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas11a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_product_relationships.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas11b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas11c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas11d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas11e.png)

**`vangeluw_citisignal_accounts`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_accounts` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas12a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_accounts.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas12b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas12c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas12d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas12e.png)

**`vangeluw_citisignal_recipients`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_recipients` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas13a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_recipients.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas13b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas13c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas13d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas13e.png)

**`vangeluw_citisignal_mobile_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_mobile_subscriptions` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas14a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_mobile_subscriptions.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas14b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas14c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas14d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas14e.png)

**`vangeluw_citisignal_internet_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_internet_subscriptions` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas15a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_internet_subscriptions.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas15b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas15c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas15d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas15e.png)

**`vangeluw_citisignal_tv_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_tv_subscriptions` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas16a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_tv_subscriptions.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas16b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas16c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas16d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas16e.png)

**`vangeluw_citisignal_equipment_subscriptions`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_equipment_subscriptions` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas17a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_equipment_subscriptions.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas17b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas17c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas17d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas17e.png)

**`vangeluw_citisignal_mobile_usage_summary`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_mobile_usage_summary` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas18a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_mobile_usage_summary.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas18b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas18c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas18d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas18e.png)

**`vangeluw_citisignal_internet_usage_summary`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_internet_usage_summary` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas19a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_internet_usage_summary.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas19b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas19c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas19d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas19e.png)

**`vangeluw_citisignal_offers`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_offers` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas20a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_offers.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas20b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas20c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas20d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas20e.png)

**`vangeluw_citisignal_offer_eligibility`**

Ga naar **Bronnen**, onderzoek naar `local` en klik dan **gegevens** toevoegen onder **Lokaal Dossier uploadt**.

![ AJO OC ](./images/ajoocdatas10.png)

Laat knevel voor **toe toelaten veranderingsgegevens vangen**.

Selecteer de gegevensset `vangeluw_citisignal_offer_eligibility` .

Klik **daarna**.

![ AJO OC ](./images/ajoocdatas21a.png)

Klik **kiezen dossiers**. Selecteer het dossier **`citisignal_offer_eligibility.csv`** en klik **open**.

![ AJO OC ](./images/ajoocdatas21b.png)

Klik **daarna**

![ AJO OC ](./images/ajoocdatas21c.png)

Klik **Afwerking**.

![ AJO OC ](./images/ajoocdatas21d.png)

Na een paar notulen, kunt u de gegevens zien die in uw dataset worden opgenomen.

![ AJO OC ](./images/ajoocdatas21e.png)

Alle gegevens worden nu opgenomen. In de volgende oefening zult u beginnen om die gegevens als deel van een georkestreerde campagne te gebruiken.

## Volgende stappen

Ga naar [ creeer uw georkestreerde campagne ](./ex2.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer: Campagnes ](./ajocampaigns.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

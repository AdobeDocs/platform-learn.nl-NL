---
title: Gegevensverzameling - FAC - Uw Snowflake-account instellen
description: Stichting - FAC - Opstelling uw rekening van de Snowflake
kt: 5342
doc-type: tutorial
exl-id: fb8a70d9-9789-4fca-90e4-771be2cfc3dc
source-git-commit: 1c91cb2129f827fd39dc065baf5d8ea067a5731a
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 1.3.1 De Snowflake-omgeving instellen

## 1.3.1.1 Uw account maken

Ga naar [ https://snowflake.com ](https://snowflake.com). Klik **BEGINNEN VOOR VRIJ**.

![ FAC ](./images/sf1.png)

Ga uw details in en klik **verdergaan**.

![ FAC ](./images/sf2.png)

Ga uw details in, kies uw wolkenleverancier en klik **begonnen worden**.

![ FAC ](./images/sf3.png)

Ga uw details in of klik **Overslaan** (x2).

![ FAC ](./images/sf4.png)

Dan zie je dit. Controleer uw e-mail en klik op het bevestigingsbericht dat naar u is verzonden.

![ FAC ](./images/sf5.png)

Klik op de koppeling in het bevestigingsbericht om uw account te activeren en geef uw gebruikersnaam en wachtwoord op. Klik **krijgen Begonnen**. U zult deze gebruikersnaam en wachtwoord in de volgende oefening moeten gebruiken.

![ FAC ](./images/sf6.png)

U wordt dan aangemeld bij de Snowflake. Klik **Overslaan voor nu**.

![ FAC ](./images/sf7.png)

## 1.3.1.2 Uw database maken

Ga naar **Gegevens > Gegevensbestanden**. Klik **+ Gegevensbestand**.

![ FAC ](./images/db1.png)

Gebruik de naam **CITISIGNAL** voor uw gegevensbestand. Klik **CREËREN**.

![ FAC ](./images/db2.png)

## 1.3.1.3 Tabellen maken

U kunt nu uw tabellen maken in Snowflake. Hieronder vindt u scripts waarmee u uw tabellen kunt maken.

### Tabel CK_PERSONS

Klik **+ creëren**, dan klik **Lijst** en klik dan **Standaard**.

![ FAC ](./images/tb1.png)

Dan zie je dit. Kopieer de onderstaande query en plak deze in Snowflake. Zorg ervoor om het **CITISIGNAAL** gegevensbestand in de hoogste linkerhoek van uw scherm te selecteren alvorens uw lijst te creëren.

```sql
create or replace TABLE CITISIGNAL.PUBLIC.CK_PERSONS (
	PERSON_ID NUMBER(38,0) NOT NULL,
	NAME VARCHAR(255),
	AGE NUMBER(38,0),
	EMAIL VARCHAR(255),
	PHONE_NUMBER VARCHAR(20),
	GENDER VARCHAR(10),
	OCCUPATION VARCHAR(100),
	ISATTMOBILESUB BOOLEAN,
	primary key (PERSON_ID)
);
```

Klik **creëren Lijst**.

![ FAC ](./images/tb2.png)

Zodra het manuscript in werking is gesteld, kunt u uw lijst onder **Gegevensbestanden > CITISIGNAL > PUBLIC** vinden.

![ FAC ](./images/tb3.png)

### Tabel CK_HOUSEHOLDS

Klik **+ creëren**, dan klik **Lijst** en klik dan **Standaard**.

![ FAC ](./images/tb1.png)

Dan zie je dit. Kopieer de onderstaande query en plak deze in Snowflake. Zorg ervoor om het **CITISIGNAAL** gegevensbestand in de hoogste linkerhoek van uw scherm te selecteren alvorens uw lijst te creëren.

```sql
create or replace TABLE CITISIGNAL.PUBLIC.CK_HOUSEHOLDS (
	HOUSEHOLD_ID NUMBER(38,0) NOT NULL,
	ADDRESS VARCHAR(255),
	CITY VARCHAR(100),
	STATE VARCHAR(50),
	POSTAL_CODE VARCHAR(20),
	COUNTRY VARCHAR(100),
	ISELIGIBLEFORFIBER BOOLEAN,
	PRIMARY_PERSON_ID NUMBER(38,0),
	ISFIBREENABLED BOOLEAN,
	primary key (HOUSEHOLD_ID)
);
```

Klik **creëren Lijst**.

![ FAC ](./images/tb4.png)

Zodra het manuscript in werking is gesteld, kunt u uw lijst onder **Gegevensbestanden > CITISIGNAL > PUBLIC** vinden.

![ FAC ](./images/tb5.png)

### Tabel CK_USERS

Klik **+ creëren**, dan klik **Lijst** en klik dan **Standaard**.

![ FAC ](./images/tb1.png)

Dan zie je dit. Kopieer de onderstaande query en plak deze in Snowflake. Zorg ervoor om het **CITISIGNAAL** gegevensbestand in de hoogste linkerhoek van uw scherm te selecteren alvorens uw lijst te creëren.

```sql
create or replace TABLE CITISIGNAL.PUBLIC.CK_USERS (
	USER_ID NUMBER(38,0) NOT NULL,
	PERSON_ID NUMBER(38,0),
	HOUSEHOLD_ID NUMBER(38,0),
	primary key (USER_ID),
	foreign key (PERSON_ID) references CITISIGNAL.PUBLIC.CK_PERSONS(PERSON_ID),
	foreign key (HOUSEHOLD_ID) references CITISIGNAL.PUBLIC.CK_HOUSEHOLDS(HOUSEHOLD_ID)
);
```

Klik **creëren Lijst**.

![ FAC ](./images/tb6.png)

Zodra het manuscript in werking is gesteld, kunt u uw lijst onder **Gegevensbestanden > CITISIGNAL > PUBLIC** vinden.

![ FAC ](./images/tb7.png)

### Tabel CK_MONTHLY_DATA_USAGE

Klik **+ creëren**, dan klik **Lijst** en klik dan **Standaard**.

![ FAC ](./images/tb1.png)

Dan zie je dit. Kopieer de onderstaande query en plak deze in Snowflake. Zorg ervoor om het **CITISIGNAAL** gegevensbestand in de hoogste linkerhoek van uw scherm te selecteren alvorens uw lijst te creëren.

```sql
create or replace TABLE CITISIGNAL.PUBLIC.CK_MONTHLY_DATA_USAGE (
	USAGE_ID NUMBER(38,0) NOT NULL autoincrement start 1 increment 1 noorder,
	USER_ID NUMBER(38,0),
	MONTH DATE,
	DATA_USAGE_GB NUMBER(10,2),
	primary key (USAGE_ID)
);
```

Klik **creëren Lijst**.

![ FAC ](./images/tb8.png)

Zodra het manuscript in werking is gesteld, kunt u uw lijst onder **Gegevensbestanden > CITISIGNAL > PUBLIC** vinden.

![ FAC ](./images/tb9.png)

### Tabel CK_MOBILE_DATA_USAGE

Klik **+ creëren**, dan klik **Lijst** en klik dan **Standaard**.

![ FAC ](./images/tb1.png)

Dan zie je dit. Kopieer de onderstaande query en plak deze in Snowflake. Zorg ervoor om het **CITISIGNAAL** gegevensbestand in de hoogste linkerhoek van uw scherm te selecteren alvorens uw lijst te creëren.


```sql
create or replace TABLE CITISIGNAL.PUBLIC.CK_MOBILE_DATA_USAGE (
	USAGE_ID NUMBER(38,0) NOT NULL autoincrement start 1 increment 1 noorder,
	USER_ID NUMBER(38,0),
	DATE DATE,
	TIME TIME(9),
	APP_NAME VARCHAR(255),
	DATA_USAGE_MB NUMBER(10,2),
	NETWORK_TYPE VARCHAR(50),
	DEVICE_TYPE VARCHAR(50),
	COUNTRY_CODE VARCHAR(10),
	primary key (USAGE_ID)
);
```

Klik **creëren Lijst**.

![ FAC ](./images/tb10.png)

Zodra het manuscript in werking is gesteld, kunt u uw lijst onder **Gegevensbestanden > CITISIGNAL > PUBLIC** vinden.

![ FAC ](./images/tb11.png)

Alle tabellen worden nu gemaakt.


## 1.3.1.4 Gegevens van de steekproef

U kunt nu voorbeeldgegevens in uw database laden.

...

U hebt nu de opstelling in Snowflake gebeëindigd.


Volgende Stap: [ 1.3.2 leidt schema&#39;s, gegevensmodel en verbindingen ](./ex2.md)

[Terug naar module 1.3](./fac.md)

[Terug naar alle modules](../../../overview.md)

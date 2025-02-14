---
title: Gegevensverzameling - FAC - Schema's, gegevensmodel en koppelingen maken
description: Stichting - FAC - creeer schema's, gegevensmodel en verbindingen
kt: 5342
doc-type: tutorial
exl-id: e863ab3a-44df-4bb4-b081-a62616aaa1f1
source-git-commit: b78460ab562c2b435988942b219787ed07af24d4
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# 1.3.2 Schema&#39;s, gegevensmodel en koppelingen maken

U kunt nu uw gefedereerde database configureren in Adobe Experience Platform.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../module1.2/images/sb1.png)

## 1.3.2.1 Een gefederaliseerde database in AEP instellen

Klik **Verdeelde gegevensbestanden** in het linkermenu. Dan, klik **voegt gefederaliseerde gegevensbestand** toe.

![ FAC ](./images/fdb1.png)

Als a **Etiket**, gebruik `--aepUserLdap-- - CitiSignal Snowflake` en voor het type, kies **Snowflake**.

Onder details, moet u uw geloofsbrieven invullen, die als dit zullen kijken:

![ FAC ](./images/fdb2.png)

**Server**:

In Snowflake, ga naar **Admin > Rekeningen**. Klik 3 **...** naast uw rekening en klik **leiden URLs**.

![ FAC ](./images/fdburl1.png)

Dan zie je dit. Kopieer **Huidige URL** en kleef het op het **gebied van de Server** in AEP.

![ FAC ](./images/fdburl2.png)

**Gebruiker**: De gebruikersnaam u vroeger, in oefening 1.3.1.1 creeerde
**Wachtwoord**: het wachtwoord u vroeger, in oefening 1.3.1.1 creeerde
**Gegevensbestand**: gebruik **CITISIGNAL**

Dus ten slotte, zou je dit moeten hebben. Klik **Verbinding van de Test**. Als de test succesvol is, stelt de klik **Functies** op, die tot functies op de kant van Snowflake zullen leiden die noodzakelijk voor de werkschemamotor zijn.

Zodra de verbinding met succes werd getest en de functies worden opgesteld, zal uw configuratie worden opgeslagen.

![ FAC ](./images/fdb3.png)

Wanneer u dan terug naar het **Verbond gegevensbestanden** menu gaat, zult u uw verbinding daar zien.

![ FAC ](./images/fdb4.png)

## 1.3.2.2 Schema&#39;s maken in AEP

In het linkermenu, klik **Modellen** en ga dan naar **Schema&#39;s**. Klik **creeer schema**.

![ FAC ](./images/fdb5.png)

Selecteer uw gefedereerde database en klik op **+ Tabellen toevoegen** .

![ FAC ](./images/fdb6.png)

Dan zie je dit. Selecteer de vijf tabellen die u eerder in Snowflake hebt gemaakt:

- `--aepUserLdap--_HOUSEHOLDS`
- `--aepUserLdap--_MOBILE_DATA_USAGE`
- `--aepUserLdap--_MONTHLY_DATA_USAGE`
- `--aepUserLdap--_PERSONS`
- `--aepUserLdap--_USERS`

Klik **toevoegen**.

![ FAC ](./images/fdb7.png)

AEP zal dan de informatie van elke lijst laden en het tonen in UI.

Voor elke tabel kunt u:

- wijzigt het label van het schema
- een beschrijving toevoegen
- naam van alle velden wijzigen en zichtbaarheid instellen
- Selecteer de primaire sleutel voor het schema

Voor deze oefening zijn geen veranderingen nodig.

Klik **creëren**.

![ FAC ](./images/fdb8.png)

Dan zie je dit. U kunt op elk schema klikken en de gegevens bekijken. Als voorbeeld, klik **—aepUserLoad—_PERSONS**.

![ FAC ](./images/fdb9.png)

U zult dan dit zien, met de capaciteit om de configuratie uit te geven. Klik **Gegevens** om een steekproef van het gegeven te zien dat in het gegevensbestand van Snowflake is.

![ FAC ](./images/fdb10.png)

U ziet dan een voorbeeld van de gegevens.

![ FAC ](./images/fdb11.png)

## 1.3.2.3 Een model maken in AEP

In het linkermenu, ga naar **Modellen** en ga dan naar **het model van Gegevens**. Klik **creëren gegevensmodel**.

![ FAC ](./images/fdb12.png)

Gebruik `--aepUserLdap-- - CitiSignal Snowflake Data Model` voor het label. Klik **creëren**.

![ FAC ](./images/fdb13.png)

Klik **schema&#39;s** toevoegen.

![ FAC ](./images/fdb14.png)

Selecteer uw schema&#39;s en klik **toevoegen**.

![ FAC ](./images/fdb15.png)

Dan zie je dit. Klik **sparen**.

![ FAC ](./images/fdb16.png)

### PERSONEN - GEBRUIKERS

U kunt nu koppelingen tussen schema&#39;s definiëren. Begin bepalend een verbinding, moet u **klikken creeert verbindingen**.

![ FAC ](./images/fdb16.png)

Eerst, bepalen wij de verbinding tussen de lijst `--aepUserLdap--_USERS` en `--aepUserLdap--_PERSONS`.

Klik **toevoegen**.

![ FAC ](./images/fdb18.png)

### HUISHOUDENS - PERSONEN

Dan ben je hier weer. Klik **creeer verbindingen** om een andere verbinding tot stand te brengen.

![ FAC ](./images/fdb17.png)

Vervolgens definiëren we de koppeling tussen de tabel `--aepUserLdap--_HOUSEHOLDS` en `--aepUserLdap--_PERSONS` .

![ FAC ](./images/fdb19.png)

### GEBRUIKERS - MONTHLY_DATA_USAGE

Dan ben je hier weer. Klik **creeer verbindingen** om een andere verbinding tot stand te brengen.

![ FAC ](./images/fdb20.png)

Vervolgens definiëren we de koppeling tussen de tabel `--aepUserLdap--_USERS` en `--aepUserLdap--_MONTHLY_DATA_USAGE` .

![ FAC ](./images/fdb21.png)


### GEBRUIKERS - HUISHOUDENS

Dan ben je hier weer. Klik **creeer verbindingen** om een andere verbinding tot stand te brengen.

![ FAC ](./images/fdb22.png)

Vervolgens definiëren we de koppeling tussen de tabel `--aepUserLdap--_USERS` en `--aepUserLdap--_HOUSEHOLDS` .

![ FAC ](./images/fdb23.png)

### GEBRUIKERS - MOBILE_DATA_USAGE

Dan ben je hier weer. Klik **creeer verbindingen** om een andere verbinding tot stand te brengen.

![ FAC ](./images/fdb24.png)

Vervolgens definiëren we de koppeling tussen de tabel `--aepUserLdap--_USERS` en `--aepUserLdap--_MOBILE_DATA_USAGE` .

![ FAC ](./images/fdb25.png)

Dan moet je dit zien. Klik **sparen**.

![ FAC ](./images/fdb26.png)

Uw installatie in AEP is nu voltooid. U kunt nu uw gefedereerde gegevens in een gefederaliseerde publiekscompositie gebruiken.

Volgende Stap: [ 1.3.3 leidt tot een gefederaliseerde samenstelling ](./ex3.md)

[Terug naar module 1.3](./fac.md)

[Terug naar alle modules](../../../overview.md)

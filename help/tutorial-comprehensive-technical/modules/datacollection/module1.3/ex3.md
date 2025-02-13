---
title: Gegevensverzameling - FAC - Een gefederaliseerde compositie maken
description: Foundation - FAC - Een gefederaliseerde compositie maken
kt: 5342
doc-type: tutorial
exl-id: 293bf825-d0d6-48cf-9cbf-69f622597678
source-git-commit: e32d415d2997b43834e9fc2495c4394b13f4d49f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 1.3.3 Een gefederaliseerde compositie maken

U kunt uw gefederaliseerde publiekssamenstelling in AEP nu vormen.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../module1.2/images/sb1.png)

## 1.3.3.1 Uw publiek maken

In het linkermenu, ga naar **Soorten publiek** en ga dan naar **Verbond samenstellingen**. Klik **creeer samenstelling**.

![ FAC ](./images/fedcomp1.png)

Gebruik voor het label het volgende: `--aepUserLdap-- - CitiSignal Fiber` . Selecteer het gegevensmodel dat u in de vorige oefening creeerde, die `--aepUserLdap-- - CitiSignal Snowflake Data Model` wordt genoemd. Klik **creëren**.

![ FAC ](./images/fedcomp2.png)

Dan zie je dit.

![ FAC ](./images/fedcomp3.png)

Klik het **+** pictogram en klik **het publiek van de Bouwstijl**.

![ FAC ](./images/fedcomp4.png)

Dan zie je dit. Selecteer **tot publiek** leiden. Klik het **onderzoek** pictogram om een schema te selecteren.

![ FAC ](./images/fedcomp5.png)

Selecteer het schema **—aepUserLoad—_HOUSEHOLDS**. Klik **bevestigen**.

![ FAC ](./images/fedcomp6.png)

Daarna, klik **verdergaan**.

![ FAC ](./images/fedcomp7.png)

U kunt nu beginnen met het maken van de query die naar Snowflake wordt verzonden. Klik **+** pictogram en klik dan **de voorwaarde van de Douane**.

![ FAC ](./images/fedcomp8.png)

Selecteer de attributen **ISELIGIBLEFORFIBER** klik **bevestigen**.

![ FAC ](./images/fedcomp9.png)

Dan zie je dit. Plaats de gebied **Waarde** aan **Waar**. Klik **berekenen** om de vraag neer aan Snowflake te duwen en een schatting van de profielen te krijgen die nu kwalificeren.

![ FAC ](./images/fedcomp10.png)

Dan, klik opnieuw het **+** pictogram en klik **de voorwaarde van de Douane** opnieuw om een andere voorwaarde toe te voegen.

![ FAC ](./images/fedcomp11.png)

De tweede voorwaarde die moet worden toegevoegd, is: `Is the user an existing CitiSignal Mobile subscriber?` . De manier om die vraag te beantwoorden is het verband tussen het huishouden en de primaire klant in het huishouden te gebruiken, dat in een andere lijst wordt bepaald, **- aepUserLDAP—_PERSONS**. U kunt neer in het attributenmenu boren gebruikend de **huishouden2person** verbinding.

![ FAC ](./images/fedcomp12.png)

Selecteer de attributen **ISMOBILESUB** en klik **bevestigen**.

![ FAC ](./images/fedcomp13.png)

Plaats de gebied **Waarde** aan **Ware** klik **berekent** opnieuw om het aantal profielen bij te werken die zullen worden gericht. Klik **bevestigen**.

![ FAC ](./images/fedcomp14.png)

Klik **+** pictogram en klik dan **sparen Publiek**.

![ FAC ](./images/fedcomp15.png)

Plaats het **etiket van het Publiek** aan `--aepUserLdap-- - CitiSignal Eligible for Fiber`.

Klik op **+ Toewijzing publiek toevoegen** .

![ FAC ](./images/fedcomp16.png)

Selecteer **HOUSEHOLD_ID** en klik **bevestigen**.

![ FAC ](./images/fedcomp17.png)

Klik op **+ Toewijzing publiek toevoegen** .

![ FAC ](./images/fedcomp18.png)

Boor neer door **het richten dimensie** te klikken.

![ FAC ](./images/fedcomp18a.png)

Boor neer door de verbinding **te klikken huishouden2person**.

![ FAC ](./images/fedcomp18b.png)

Selecteer de gebied **NAAM**. Klik **bevestigen**.

![ FAC ](./images/fedcomp18c.png)

Klik op **+ Toewijzing publiek toevoegen** .

![ FAC ](./images/fedcomp20.png)

Boor neer door **het richten dimensie** te klikken.

![ FAC ](./images/fedcomp20a.png)

Boor neer door de verbinding **te klikken huishouden2person**.

![ FAC ](./images/fedcomp20b.png)

Selecteer het gebied **EMAIL**. Klik **bevestigen**.

![ FAC ](./images/fedcomp20c.png)

Dan zie je dit. U moet nu het **Primaire identiteitsgebied** plaatsen, het plaatsen aan **Household2person_EMAIL**. Plaats **Namespace van de Identiteit** aan **E-mail**.

Klik **sparen**.

![ FAC ](./images/fedcomp21.png)

Uw compositie is nu voltooid. Klik **Begin** om het in werking te stellen.

![ FAC ](./images/fedcomp21a.png)

De query wordt nu omlaag geduwd naar Snowflake, die de brongegevens daar zal opvragen. De resultaten worden teruggezet naar AEP, maar de brongegevens blijven in Snowflake.

Het publiek is nu bevolkt en het publiek is gericht vanuit het ecosysteem van AEP.

![ FAC ](./images/fedcomp22.png)

Volgende Stap: [ Samenvatting &amp; voordelen ](./summary.md)

[Terug naar module 1.3](./fac.md)

[Terug naar alle modules](../../../overview.md)

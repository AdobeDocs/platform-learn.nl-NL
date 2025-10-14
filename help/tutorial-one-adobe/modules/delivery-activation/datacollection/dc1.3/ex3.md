---
title: Gegevensverzameling - FAC - Een gefederaliseerde compositie maken
description: Foundation - FAC - Een gefederaliseerde compositie maken
kt: 5342
doc-type: tutorial
exl-id: 6c1773d1-ca2e-43e5-bfa7-6e5e0fbcf859
source-git-commit: 2beb052927f88e13f42b2af940a637cbc3caa19d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 1.3.3 Een gefederaliseerde compositie maken

U kunt nu uw gefederaliseerde publiekscompositie configureren in AEP.

Login aan Adobe Experience Platform door naar dit URL te gaan: [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./../dc1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam `--aepSandboxName--` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![&#x200B; Ingestie van Gegevens &#x200B;](./../dc1.2/images/sb1.png)

## 1.3.3.1 Uw publiek maken

In het linkermenu, ga naar **Soorten publiek** en ga dan naar **Verbond samenstellingen**. Klik **creeer samenstelling**.

![&#x200B; FAC &#x200B;](./images/fedcomp1.png)

Gebruik voor het label het volgende: `--aepUserLdap-- - CitiSignal Fiber` . Selecteer het gegevensmodel dat u in de vorige oefening creeerde, die `--aepUserLdap-- - CitiSignal Snowflake Data Model` wordt genoemd. Klik **creëren**.

![&#x200B; FAC &#x200B;](./images/fedcomp2.png)

Dan zie je dit.

![&#x200B; FAC &#x200B;](./images/fedcomp3.png)

Klik het **+** pictogram en klik **het publiek van de Bouwstijl**.

![&#x200B; FAC &#x200B;](./images/fedcomp4.png)

Dan zie je dit. Selecteer **tot publiek** leiden. Klik het **onderzoek** pictogram om een schema te selecteren.

![&#x200B; FAC &#x200B;](./images/fedcomp5.png)

Selecteer het schema **`--aepUserLdap--_HOUSEHOLDS`** . Klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp6.png)

Daarna, klik **verdergaan**.

![&#x200B; FAC &#x200B;](./images/fedcomp7.png)

U kunt nu beginnen met het maken van de query die naar Snowflake wordt verzonden. Klik **+** pictogram en klik dan **de voorwaarde van de Douane**.

![&#x200B; FAC &#x200B;](./images/fedcomp8.png)

Selecteer de attributen **ISELIGIBLEFORFIBER** klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp9.png)

Dan zie je dit. Plaats de gebied **Waarde** aan **Waar**. Klik **berekenen** om de vraag neer aan Snowflake te duwen en een schatting van de profielen te krijgen die nu kwalificeren.

![&#x200B; FAC &#x200B;](./images/fedcomp10.png)

Dan, klik opnieuw het **+** pictogram en klik **de voorwaarde van de Douane** opnieuw om een andere voorwaarde toe te voegen.

![&#x200B; FAC &#x200B;](./images/fedcomp11.png)

De tweede voorwaarde die moet worden toegevoegd, is: `Is the user an existing CitiSignal Mobile subscriber?` . De manier om die vraag te beantwoorden is de verhouding tussen het huishouden en de primaire klant in het huishouden te gebruiken, die in een andere lijst, **`--aepUserLdap--_PERSONS`** wordt bepaald. U kunt neer in het attributenmenu boren gebruikend de **huishouden2person** verbinding.

![&#x200B; FAC &#x200B;](./images/fedcomp12.png)

Selecteer de attributen **ISMOBILESUB** en klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp13.png)

Plaats de gebied **Waarde** aan **Ware** klik **berekent** opnieuw om het aantal profielen bij te werken die zullen worden gericht. Klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp14.png)

Klik **+** pictogram en klik dan **sparen Publiek**.

![&#x200B; FAC &#x200B;](./images/fedcomp15.png)

Plaats het **etiket van het Publiek** aan `--aepUserLdap-- - CitiSignal Eligible for Fiber`.

Klik op **+ Toewijzing publiek toevoegen** .

![&#x200B; FAC &#x200B;](./images/fedcomp16.png)

Selecteer **HOUSEHOLD_ID** en klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp17.png)

Klik op **+ Toewijzing publiek toevoegen** .

![&#x200B; FAC &#x200B;](./images/fedcomp18.png)

Boor neer door **het richten dimensie** te klikken.

![&#x200B; FAC &#x200B;](./images/fedcomp18a.png)

Boor neer door de verbinding **te klikken huishouden2person**.

![&#x200B; FAC &#x200B;](./images/fedcomp18b.png)

Selecteer de gebied **NAAM**. Klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp18c.png)

Klik op **+ Toewijzing publiek toevoegen** .

![&#x200B; FAC &#x200B;](./images/fedcomp20.png)

Boor neer door **het richten dimensie** te klikken.

![&#x200B; FAC &#x200B;](./images/fedcomp20a.png)

Boor neer door de verbinding **te klikken huishouden2person**.

![&#x200B; FAC &#x200B;](./images/fedcomp20b.png)

Selecteer het gebied **EMAIL**. Klik **bevestigen**.

![&#x200B; FAC &#x200B;](./images/fedcomp20c.png)

Dan zie je dit. U moet nu het **Primaire identiteitsgebied** plaatsen, het plaatsen aan **Household2person_EMAIL**. Plaats **Namespace van de Identiteit** aan **E-mail**.

Klik **sparen**.

![&#x200B; FAC &#x200B;](./images/fedcomp21.png)

Uw compositie is nu voltooid. Klik **Begin** om het in werking te stellen.

![&#x200B; FAC &#x200B;](./images/fedcomp21a.png)

De query wordt nu omlaag geduwd naar Snowflake, die de brongegevens daar zal opvragen. De resultaten worden teruggezet naar AEP, maar de brongegevens blijven in Snowflake.

Het publiek is nu bevolkt en het publiek is gericht vanuit het ecosysteem van AEP.

![&#x200B; FAC &#x200B;](./images/fedcomp22.png)

## Volgende stappen

Ga naar [&#x200B; Samenvatting &amp; voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; Federated de Samenstelling van het Publiek &#x200B;](./fac.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}

---
title: GenStudio for Performance Marketing Create Email Experience for AJO
description: GenStudio for Performance Marketing Create Email Experience for AJO
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 9837c076-e6ca-47a0-96b9-5fa5fdba3fd2
source-git-commit: 917ebcd2dd5d8316413a183bd2c1a048c090428c
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# 1.3.4 E-mailbeleving voor AJO maken

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang hebben tot een milieu van Adobe Journey Optimizer dat voor de integratie met GenStudio for Performance Marketing wordt voorzien, die momenteel in bèta is.

>[!IMPORTANT]
>
>Om alle stappen in deze oefening uit te voeren, moet u toegang tot een bestaande milieu van Adobe Workfront hebben, en in die milieu moet u een project en een goedkeuringswerkschema hebben gecreeerd. Als u oefening [ Beheer van het Werkschema met Adobe Workfront ](./../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} volgt zult u de vereiste beschikbare opstelling hebben.

## 1.3.4.1 E-mailbeleving maken en goedkeuren

In het linkermenu, ga **creëren**. Selecteer **E-mail**.

![ GSPeM ](./images/gsemail1.png)

Selecteer het **E-mail** malplaatje dat u vroeger invoerde, dat `--aepUserLdap---citisignal-email-template` wordt genoemd. Klik **Gebruik**.

![ GSPeM ](./images/gsemail2.png)

Dan moet je dit zien. Wijzig de naam van de advertentie in `--aepUserLdap-- - Email Online Gamers Fiber Max` .

![ GSPeM ](./images/gsemail3.png)

Onder **Paramaters**, selecteer de volgende opties:

- **Merk**: `--aepUserLdap-- - CitiSignal`
- **Taal**: `English (US)`
- **Persona**: `--aepUserLdap-- - Online Gamers`
- **Product**: `--aepUserLdap-- - CitiSignal Fiber Max`

Klik **Uitgezocht van Inhoud**.

![ GSPeM ](./images/gsemail4.png)

Selecteer het element `--aepUserLdap-- - neon rabbit.png` . Klik **Gebruik**.

![ GSPeM ](./images/gsemail5.png)

Ga de herinnering `convince online gamers to start playing online multiplayer games using CitiSignal internet` in en klik **produceert**.

![ GSPeM ](./images/gsemail6.png)

Dan zou je iets als dit moeten zien, met 4 e-mailvariaties die worden gegenereerd. De standaardmening toont de **mobiele** mening, kunt u aan de Desktopmening schakelen door het **computer** pictogram te klikken.

![ GSPeM ](./images/gsemail7.png)

Voor elke e-mail wordt automatisch een compatibiliteitsscore berekend. Klik op de score voor meer details.

![ GSPeM ](./images/gsemail8.png)

Klik **Mening en los kwesties** op.

![ GSPeM ](./images/gsemail9.png)

U kunt dan meer details zien over wat u kunt doen om de compliancescore te optimaliseren.

![ GSPeM ](./images/gsemail10.png)

Daarna, klik **Goedkeuring van het Verzoek**, die met Adobe Workfront zal verbinden.

![ GSPeM ](./images/gsemail11.png)

Selecteer uw Adobe Workfront-project met de naam `--aepUserLdap-- - CitiSignal Fiber Launch` . Ga uw eigen e-mailadres onder **in nodigt mensen** uit en verzekert uw rol aan **wordt geplaatst fiatteur**.

![ GSPeM ](./images/gsemail12.png)

U kunt ook een bestaande goedkeuringsworkflow in Adobe Workfront gebruiken. Om dat te doen, klik **malplaatje van het Gebruik** en selecteer het malplaatje `--aepuserLdap-- - Approval Workflow`. Klik **verzenden**.

![ GSPeM ](./images/gsemail13.png)

Klik **commentaren van de Mening in Workfront**, zult u nu naar de UI van het Bewijs van Adobe Workfront worden verzonden.

![ GSPeM ](./images/gsemail14.png)

In het Bewijs van Adobe Workfront UI, klik **besluit van het Merk**.

![ GSPeM ](./images/gsemail15.png)

Selecteer **Goedgekeurd** en klik **besluit** maken.

![ GSPeM ](./images/gsemail16.png)

Klik **publiceren**.

![ GSPeM ](./images/gsemail17.png)

Selecteer uw Campagne `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` en klik **publiceren**.

![ GSPeM ](./images/gsemail18.png)

Klik **Open in Inhoud**.

![ GSPeM ](./images/gsemail19.png)

De 4 e-mailervaringen zijn nu beschikbaar onder **Inhoud** > **Ervaringen**.

![ GSPeM ](./images/gsemail20.png)

## 1.3.4.2 Een campagne maken in AJO

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak** zijn.`--aepSandboxName--`

![ ACOP ](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![ Journey Optimizer ](./images/gsemail21.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![ Journey Optimizer ](./images/gsemail22.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap--  - Online Gamers CitiSignal Fiber Max`.
- **Beschrijving**: De campagne van de Vezel voor Online Gamers

Klik **Acties**.

![ Journey Optimizer ](./images/gsemail23.png)

Klik **+ voeg Actie** toe en selecteer dan **E-mail**.

![ Journey Optimizer ](./images/gsemail24.png)

Dan, selecteer een bestaande **E-mailconfiguratie** en klik dan **uitgeven inhoud**.

![ Journey Optimizer ](./images/gsemail25.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit:

```
{{profile.person.name.firstName}}, say goodbye to delays!
```

Daarna, klik **uitgeven inhoud**.

![ Journey Optimizer ](./images/gsemail26.png)

Klik **de Invoer HTML**.

![ Journey Optimizer ](./images/gsemail27.png)

Daarna, klik de knoop voor **Adobe GenStudio for Performance Marketing**.

![ Journey Optimizer ](./images/gsemail28.png)

Vervolgens wordt een pop-upvenster weergegeven met alle e-mailervaringen die in GenStudio for Performance Marketing zijn gepubliceerd. Selecteer één van de beschikbare e-mailervaringen en klik **Gebruik**.

![ Journey Optimizer ](./images/gsemail29.png)

Selecteer uw eigen bewaarplaats van AEM Assets CS, die `--aepUserLdap-- - CitiSignal dev` zou moeten worden genoemd, en **de Invoer** klikken.

![ Journey Optimizer ](./images/gsemail30.png)

Dan moet je dit zien. Selecteer de ontbrekende beeldknoop en klik **Selecteer een activa**.

![ Journey Optimizer ](./images/gsemail31.png)

Ga naar de omslag die als dit kijkt, beginnend met **GenStudio.zip....** en selecteert u de afbeelding `--aepUserLdap-- - neon rabbit.png` . CLick **Uitgezochte**

![ Journey Optimizer ](./images/gsemail32.png)

Dan moet je dit zien.

![ Journey Optimizer ](./images/gsemail33.png)

De rol neer aan footer, selecteert het woord **Unsubscribe** en klikt het **verbindings** pictogram.

![ Journey Optimizer ](./images/gsemail38.png)

Plaats het **Type** aan **Externe Opt-out/Unsubscription** en plaats url aan `https://techinsiders.org/unsubscribe.html` (het is niet toegestaan om een lege URL voor te hebben unsubscribe verbinding).

Klik **sparen** en klik dan de **pijl** in de hoogste linkerhoek van uw scherm om terug naar de campagneconfiguratie te gaan.

![ Journey Optimizer ](./images/gsemail39.png)

Ga naar **Publiek**.

![ Journey Optimizer ](./images/gsemail34.png)

Klik **Uitgezochte publiek**.

![ Journey Optimizer ](./images/gsemail35.png)

Selecteer het publiek van de abonnementenlijst voor Online gamers, die `--aepUserLdap--_SL_Interest_Online_Gaming` zou moeten worden genoemd. Klik **sparen**.

![ Journey Optimizer ](./images/gsemail36.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./images/gsemail37.png)

Als uw campagneconfiguratie geen kwesties heeft, zult u **kunnen klikken activeert**.

![ Journey Optimizer ](./images/gsemail40.png)

Uw campagne wordt dan geactiveerd, wat een paar minuten in beslag neemt.

![ Journey Optimizer ](./images/gsemail41.png)

Na een paar minuten is de campagne live en wordt het e-mailbericht verzonden naar de abonnementenlijst die u hebt geselecteerd.

![ Journey Optimizer ](./images/gsemail42.png)

Je hebt deze oefening nu voltooid.

## Volgende stappen

Ga naar [ Samenvatting &amp; voordelen ](./summary.md){target="_blank"}

Ga terug naar [ GenStudio for Performance Marketing ](./genstudio.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

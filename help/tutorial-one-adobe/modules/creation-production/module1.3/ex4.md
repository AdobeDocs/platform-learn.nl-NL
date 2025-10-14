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
>Om alle stappen in deze oefening uit te voeren, moet u toegang tot een bestaande milieu van Adobe Workfront hebben, en in die milieu moet u een project en een goedkeuringswerkschema hebben gecreeerd. Als u oefening [&#x200B; Beheer van het Werkschema met Adobe Workfront &#x200B;](./../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} volgt zult u de vereiste beschikbare opstelling hebben.

## 1.3.4.1 E-mailbeleving maken en goedkeuren

In het linkermenu, ga **creëren**. Selecteer **E-mail**.

![&#x200B; GSPeM &#x200B;](./images/gsemail1.png)

Selecteer het **E-mail** malplaatje dat u vroeger invoerde, dat `--aepUserLdap---citisignal-email-template` wordt genoemd. Klik **Gebruik**.

![&#x200B; GSPeM &#x200B;](./images/gsemail2.png)

Dan moet je dit zien. Wijzig de naam van de advertentie in `--aepUserLdap-- - Email Online Gamers Fiber Max` .

![&#x200B; GSPeM &#x200B;](./images/gsemail3.png)

Onder **Paramaters**, selecteer de volgende opties:

- **Merk**: `--aepUserLdap-- - CitiSignal`
- **Taal**: `English (US)`
- **Persona**: `--aepUserLdap-- - Online Gamers`
- **Product**: `--aepUserLdap-- - CitiSignal Fiber Max`

Klik **Uitgezocht van Inhoud**.

![&#x200B; GSPeM &#x200B;](./images/gsemail4.png)

Selecteer het element `--aepUserLdap-- - neon rabbit.png` . Klik **Gebruik**.

![&#x200B; GSPeM &#x200B;](./images/gsemail5.png)

Ga de herinnering `convince online gamers to start playing online multiplayer games using CitiSignal internet` in en klik **produceert**.

![&#x200B; GSPeM &#x200B;](./images/gsemail6.png)

Dan zou je iets als dit moeten zien, met 4 e-mailvariaties die worden gegenereerd. De standaardmening toont de **mobiele** mening, kunt u aan de Desktopmening schakelen door het **computer** pictogram te klikken.

![&#x200B; GSPeM &#x200B;](./images/gsemail7.png)

Voor elke e-mail wordt automatisch een compatibiliteitsscore berekend. Klik op de score voor meer details.

![&#x200B; GSPeM &#x200B;](./images/gsemail8.png)

Klik **Mening en los kwesties** op.

![&#x200B; GSPeM &#x200B;](./images/gsemail9.png)

U kunt dan meer details zien over wat u kunt doen om de compliancescore te optimaliseren.

![&#x200B; GSPeM &#x200B;](./images/gsemail10.png)

Daarna, klik **Goedkeuring van het Verzoek**, die met Adobe Workfront zal verbinden.

![&#x200B; GSPeM &#x200B;](./images/gsemail11.png)

Selecteer uw Adobe Workfront-project met de naam `--aepUserLdap-- - CitiSignal Fiber Launch` . Ga uw eigen e-mailadres onder **in nodigt mensen** uit en verzekert uw rol aan **wordt geplaatst fiatteur**.

![&#x200B; GSPeM &#x200B;](./images/gsemail12.png)

U kunt ook een bestaande goedkeuringsworkflow in Adobe Workfront gebruiken. Om dat te doen, klik **malplaatje van het Gebruik** en selecteer het malplaatje `--aepuserLdap-- - Approval Workflow`. Klik **verzenden**.

![&#x200B; GSPeM &#x200B;](./images/gsemail13.png)

Klik **commentaren van de Mening in Workfront**, zult u nu naar de UI van het Bewijs van Adobe Workfront worden verzonden.

![&#x200B; GSPeM &#x200B;](./images/gsemail14.png)

In het Bewijs van Adobe Workfront UI, klik **besluit van het Merk**.

![&#x200B; GSPeM &#x200B;](./images/gsemail15.png)

Selecteer **Goedgekeurd** en klik **besluit** maken.

![&#x200B; GSPeM &#x200B;](./images/gsemail16.png)

Klik **publiceren**.

![&#x200B; GSPeM &#x200B;](./images/gsemail17.png)

Selecteer uw Campagne `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` en klik **publiceren**.

![&#x200B; GSPeM &#x200B;](./images/gsemail18.png)

Klik **Open in Inhoud**.

![&#x200B; GSPeM &#x200B;](./images/gsemail19.png)

De 4 e-mailervaringen zijn nu beschikbaar onder **Inhoud** > **Ervaringen**.

![&#x200B; GSPeM &#x200B;](./images/gsemail20.png)

## 1.3.4.2 Een campagne maken in AJO

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak** zijn.`--aepSandboxName--`

![&#x200B; ACOP &#x200B;](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail21.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail22.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap--  - Online Gamers CitiSignal Fiber Max`.
- **Beschrijving**: De campagne van de Vezel voor Online Gamers

Klik **Acties**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail23.png)

Klik **+ voeg Actie** toe en selecteer dan **E-mail**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail24.png)

Dan, selecteer een bestaande **E-mailconfiguratie** en klik dan **uitgeven inhoud**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail25.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit:

```
{{profile.person.name.firstName}}, say goodbye to delays!
```

Daarna, klik **uitgeven inhoud**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail26.png)

Klik **de Invoer HTML**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail27.png)

Daarna, klik de knoop voor **Adobe GenStudio for Performance Marketing**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail28.png)

Vervolgens wordt een pop-upvenster weergegeven met alle e-mailervaringen die in GenStudio for Performance Marketing zijn gepubliceerd. Selecteer één van de beschikbare e-mailervaringen en klik **Gebruik**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail29.png)

Selecteer uw eigen bewaarplaats van AEM Assets CS, die `--aepUserLdap-- - CitiSignal dev` zou moeten worden genoemd, en **de Invoer** klikken.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail30.png)

Dan moet je dit zien. Selecteer de ontbrekende beeldknoop en klik **Selecteer een activa**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail31.png)

Ga naar de omslag die als dit kijkt, beginnend met **GenStudio.zip....** en selecteert u de afbeelding `--aepUserLdap-- - neon rabbit.png` . CLick **Uitgezochte**

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail32.png)

Dan moet je dit zien.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail33.png)

De rol neer aan footer, selecteert het woord **Unsubscribe** en klikt het **verbindings** pictogram.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail38.png)

Plaats het **Type** aan **Externe Opt-out/Unsubscription** en plaats url aan `https://techinsiders.org/unsubscribe.html` (het is niet toegestaan om een lege URL voor te hebben unsubscribe verbinding).

Klik **sparen** en klik dan de **pijl** in de hoogste linkerhoek van uw scherm om terug naar de campagneconfiguratie te gaan.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail39.png)

Ga naar **Publiek**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail34.png)

Klik **Uitgezochte publiek**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail35.png)

Selecteer het publiek van de abonnementenlijst voor Online gamers, die `--aepUserLdap--_SL_Interest_Online_Gaming` zou moeten worden genoemd. Klik **sparen**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail36.png)

Klik **Overzicht om** te activeren.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail37.png)

Als uw campagneconfiguratie geen kwesties heeft, zult u **kunnen klikken activeert**.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail40.png)

Uw campagne wordt dan geactiveerd, wat een paar minuten in beslag neemt.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail41.png)

Na een paar minuten is de campagne live en wordt het e-mailbericht verzonden naar de abonnementenlijst die u hebt geselecteerd.

![&#x200B; Journey Optimizer &#x200B;](./images/gsemail42.png)

Je hebt deze oefening nu voltooid.

## Volgende stappen

Ga naar [&#x200B; Samenvatting &amp; voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; GenStudio for Performance Marketing &#x200B;](./genstudio.md){target="_blank"}

Ga terug naar [&#x200B; Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

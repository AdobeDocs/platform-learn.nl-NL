---
title: AJO en GenStudio for Performance Marketing
description: AJO en GenStudio for Performance Marketing
kt: 5342
doc-type: tutorial
exl-id: 1424f649-d004-4b14-b8af-927ca1d47de5
source-git-commit: 10f1f6a1f77c41e3c912b3d03b73da7b6c68670c
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# 3.6.3 AJO en GenStudio for Performance Marketing

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang hebben tot een milieu van Adobe Journey Optimizer dat voor de integratie met GenStudio for Performance Marketing wordt voorzien, die momenteel in bèta is.

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een geval hebben dat voor Adobe GenStudio for Performance Marketing wordt voorzien.

>[!IMPORTANT]
>
>Om alle stappen in deze oefening uit te voeren, moet u toegang tot een bestaande milieu van Adobe Workfront hebben, en in die milieu moet u een project en een goedkeuringswerkschema hebben gecreeerd. Als u oefening [ Beheer van het Werkschema met Adobe Workfront ](./../../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} volgt zult u de vereiste beschikbare opstelling hebben.

## 1.3.4.1 E-mailbeleving maken en goedkeuren in Adobe GenStudio

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Open **GenStudio**.

![ GSPeM ](./../../../creation-production/module1.3/images/gspem1.png)

Dan moet je dit zien. In het linkermenu, ga **creëren**. Selecteer **E-mail**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail1.png)

Selecteer het **E-mail** malplaatje dat u vroeger invoerde, dat `--aepUserLdap---citisignal-email-template` wordt genoemd. Klik **Gebruik**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail2.png)

Dan moet je dit zien. Wijzig de naam van de advertentie in `--aepUserLdap-- - Email Online Gamers Fiber Max` .

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail3.png)

Onder **Paramaters**, selecteer de volgende opties:

- **Merk**: `--aepUserLdap-- - CitiSignal`
- **Taal**: `English (US)`
- **Persona**: `--aepUserLdap-- - Smart Home Families`
- **Product**: `--aepUserLdap-- - CitiSignal Fiber Max`

Klik **Uitgezocht van Inhoud**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail4.png)

Selecteer het element `--aepUserLdap-- - neon rabbit.png` . Klik **Gebruik**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail5.png)

Ga de herinnering `convince online gamers to start playing online multiplayer games using CitiSignal internet` in en klik **produceert**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail6.png)

Dan zou je iets als dit moeten zien, met 4 e-mailvariaties die worden gegenereerd. De standaardmening toont de **mobiele** mening, kunt u aan de Desktopmening schakelen door het **computer** pictogram te klikken.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail7.png)

Voor elke e-mail wordt automatisch een compatibiliteitsscore berekend. Klik op de score voor meer details.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail8.png)

Klik **Mening en los kwesties** op.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail9.png)

U kunt dan meer details zien over wat u kunt doen om de ingewikkeldheidsscore te optimaliseren.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail10.png)

Daarna, klik **Goedkeuring van het Verzoek**, die met Adobe Workfront zal verbinden.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail11.png)

Selecteer uw Adobe Workfront-project met de naam `--aepUserLdap-- - CitiSignal Fiber Launch` . Ga uw eigen e-mailadres onder **in nodigt mensen** uit en verzekert uw rol aan **wordt geplaatst fiatteur**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail12.png)

U kunt ook een bestaande goedkeuringsworkflow in Adobe Workfront gebruiken. Om dat te doen, klik **malplaatje van het Gebruik** en selecteer het malplaatje `--aepuserLdap-- - Approval Workflow`. Klik **verzenden**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail13.png)

Klik **commentaren van de Mening in Workfront**, zult u nu naar de UI van het Bewijs van Adobe Workfront worden verzonden.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail14.png)

In het Bewijs van Adobe Workfront UI, klik **besluit van het Merk**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail15.png)

Selecteer **Goedgekeurd** en klik **besluit** maken.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail16.png)

Klik **publiceren**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail17.png)

Selecteer uw Campagne `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` en klik **publiceren**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail18.png)

Klik **Open in Inhoud**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail19.png)

De 4 e-mailervaringen zijn nu beschikbaar onder **Inhoud** > **Ervaringen**.

![ GSPeM ](./../../../creation-production/module1.3/images/gsemail20.png)

## 1.3.4.2 Een campagne maken in AJO

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak** zijn.`--aepSandboxName--`

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail21.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail22.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap--  - Online Gamers CitiSignal Fiber Max`.
- **Beschrijving**: De campagne van de Vezel voor Online Gamers

Klik **Acties**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail23.png)

Klik **+ voeg Actie** toe en selecteer dan **E-mail**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail24.png)

Dan, selecteer een bestaande **E-mailconfiguratie** en klik dan **uitgeven inhoud**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail25.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit:

```
{{profile.person.name.firstName}}, say goodbye to delays!
```

Daarna, klik **uitgeven inhoud**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail26.png)

Klik **de Invoer HTML**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail27.png)

Daarna, klik de knoop voor **Adobe GenStudio for Performance Marketing**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail28.png)

Vervolgens wordt een pop-upvenster weergegeven met alle e-mailervaringen die in GenStudio for Performance Marketing zijn gepubliceerd. Selecteer één van de beschikbare e-mailervaringen en klik **Gebruik**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail29.png)

Selecteer uw eigen bewaarplaats van AEM Assets CS, die `--aepUserLdap-- - CitiSignal dev` zou moeten worden genoemd, en **de Invoer** klikken.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail30.png)

Dan moet je dit zien. Selecteer de ontbrekende beeldknoop en klik **Selecteer een activa**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail31.png)

Ga naar de omslag die als dit kijkt, beginnend met **GenStudio.zip....** en selecteert u de afbeelding `--aepUserLdap-- - neon rabbit.png` . CLick **Uitgezochte**

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail32.png)

Dan moet je dit zien.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail33.png)

De rol neer aan footer, selecteert het woord **Unsubscribe** en klikt het **verbindings** pictogram.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail38.png)

Plaats het **Type** aan **Externe Opt-out/Unsubscription** en plaats url aan `https://techinsiders.org/unsubscribe.html` (het is niet toegestaan om een lege URL voor te hebben unsubscribe verbinding).

Klik **sparen** en klik dan de **pijl** in de hoogste linkerhoek van uw scherm om terug naar de campagneconfiguratie te gaan.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail39.png)

Ga naar **Publiek**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail34.png)

Klik **Uitgezochte publiek**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail35.png)

Selecteer het publiek van de abonnementenlijst voor Online gamers, die `--aepUserLdap--_SL_Interest_Online_Gaming` zou moeten worden genoemd. Klik **sparen**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail36.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail37.png)

Als uw campagneconfiguratie geen kwesties heeft, zult u **kunnen klikken activeert**.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail40.png)

Uw campagne wordt dan geactiveerd, wat een paar minuten in beslag neemt.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail41.png)

Na een paar minuten is de campagne live en wordt het e-mailbericht verzonden naar de abonnementenlijst die u hebt geselecteerd.

![ Journey Optimizer ](./../../../creation-production/module1.3/images/gsemail42.png)

Je hebt deze oefening nu voltooid.

## Volgende stappen

Ga naar [ Samenvatting en Voordelen ](./summary.md)

Ga terug naar [ Adobe Journey Optimizer: Het Beheer van de inhoud ](./ajocontent.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}

---
title: Dynamische mediasjabloon gebruiken met Adobe Journey Optimizer
description: Dynamische mediasjabloon gebruiken met Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
source-git-commit: 261475b85bfb15f7e9f630d1c5203732c2d4c254
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 1.4.2 Gebruik uw dynamische mediasjabloon met Adobe Journey Optimizer

## 1.4.2.1 Uw campagne maken in Adobe Journey Optimizer

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak** zijn.`--aepSandboxName--`

![ ACOP ](./images/acoptriglp.png)

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![ Journey Optimizer ](./images/gsemail21.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![ Journey Optimizer ](./images/gsemail22.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap-- - CitiSignal Fiber Max DM Email Campaign`.

Klik **Acties**.

![ Journey Optimizer ](./images/gsemail23.png)

Klik **+ voeg Actie** toe en selecteer dan **E-mail**.

![ Journey Optimizer ](./images/gsemail24.png)

Dan, selecteer een bestaande **E-mailconfiguratie** en klik dan **uitgeven inhoud**.

![ Journey Optimizer ](./images/gsemail25.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit:

```
{{profile.person.name.firstName}}, say hello to CitiSignal Fiber Max!
```

Daarna, klik **uitgeven inhoud**.

![ Journey Optimizer ](./images/gsemail26.png)

Selecteer **Ontwerp van kras**.

![ Journey Optimizer ](./images/gsemail27.png)

Dan moet je dit zien.

![ Journey Optimizer ](./images/gsemail28.png)

Voeg 2x **1 :1 kolom** aan het canvas toe.

![ Journey Optimizer ](./images/gsemail29.png)

Ga naar **Fragmenten**, sleep het **kopbal** fragment aan de eerste 1 :1 kolom en sleep dan het **footer** fragment aan de tweede 1 :1 kolom.

![ Journey Optimizer ](./images/gsemail30.png)

Voeg een nieuwe 1 :1 kolom binnen tussen de 2 fragmenten toe, en voeg dan een **Beeld** in die 1 :1 kolom toe. Dan, klik **doorbladeren**.

![ Journey Optimizer ](./images/gsemail31.png)

Navigeer naar de map waarin u de sjabloon Dynamische media hebt opgeslagen. Selecteer uw Dynamische malplaatje van Media en klik dan **Uitgezocht**.

![ Journey Optimizer ](./images/gsemail32.png)

Dan moet je dit zien.

![ Journey Optimizer ](./images/gsemail33.png)

## Volgende stappen

Ga terug naar [ Adobe Experience Manager Assets &amp; Dynamische Media ](./aemassetsdm.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

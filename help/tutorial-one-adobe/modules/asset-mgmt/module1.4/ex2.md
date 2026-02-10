---
title: Dynamische mediasjabloon gebruiken met Adobe Journey Optimizer
description: Dynamische mediasjabloon gebruiken met Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
exl-id: 0dd499cc-ec3b-42c3-9c08-6512ea5b9377
source-git-commit: 8f746831d4a1481f8ccc14539273c4b16ca5170b
workflow-type: tm+mt
source-wordcount: '637'
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

Dan moet je dit zien. Ook jij. merk de **PARAMETERS** op die u toestaan om de parameters van het dynamische media malplaatje te veranderen.

![ Journey Optimizer ](./images/gsemail33.png)

## 1.4.2.2 De sjabloon voor dynamische media aanpassen

Zoals in de vorige oefening is besproken, moet AJO nu dynamisch beslissen welke waarden deel moeten uitmaken van de Dynamic Media-sjabloon.

Enkel als in de **stap van de Voorproef** in de vorige oefening, zouden de gebieden **city_paris**, **city_dubai** en **city_ny**, aan 1 moeten worden geplaatst wat betekent dat deze beelden zullen worden verborgen.

Voor het gebied **titel**, klik het verpersoonlijkingspictogram.

![ Journey Optimizer ](./images/gsemail34.png)

Vervang de standaardtekst door: `Hi {{profile.person.name.firstName}}`. Klik **sparen**.

![ Journey Optimizer ](./images/gsemail35.png)

Voor het gebied **lichaam**, klik het verpersoonlijkingspictogram.

![ Journey Optimizer ](./images/gsemail36.png)

Vervang de standaardtekst door: `CitiSignal is coming to {{profile.homeAddress.city}}!`. Klik **sparen**.

![ Journey Optimizer ](./images/gsemail37.png)

Zorg ervoor dat het veld **`dynamic_city_hide`** is ingesteld op 0. Klik op het verpersoonlijkingspictogram voor het veld **`dynamic_city_image`** .

![ Journey Optimizer ](./images/gsemail38.png)

Vervang de standaardtekst door: `--aepUserLdap--CitiSignalDM/citisignal-fiber-max-is-coming_citisignal-{{profile._experienceplatform.individualCharacteristics.fiber_rollout.closest_rollout_city}}-1`. Klik **sparen**.

![ Journey Optimizer ](./images/gsemail39.png)

Dan moet je dit zien. De afbeelding wordt hier niet meer weergegeven, wat wordt verwacht omdat de dynamische variabelen niet beschikbaar zijn in de context van de e-maileditor.

Klik **sparen**.

![ Journey Optimizer ](./images/gsemail40.png)

Bovenste test uw configuratie, klik **Simuleer Inhoud** en selecteer dan **Inhoud** simuleren.

![ Journey Optimizer ](./images/gsemail41.png)

Dan moet je iets dergelijks zien. Als u geen beschikbare testprofielen hebt, kunt u hen toevoegen door **te gaan testprofielen beheren**.

Als er testprofielen beschikbaar zijn die de gegevens bevatten die nodig zijn om dit gebruik te testen, kunt u van het ene naar het andere profiel overschakelen om te zien hoe de wijzigingen dynamisch plaatsvinden.

Hier is een profiel dat is gekoppeld aan de oprollingsstad New York.

![ Journey Optimizer ](./images/gsemail42.png)

Hier is een profiel dat is gekoppeld aan de rollout city Paris.

![ Journey Optimizer ](./images/gsemail43.png)

Hier is een profiel dat is gekoppeld aan de rollout city Dubai.

Klik **dicht**.

![ Journey Optimizer ](./images/gsemail44.png)

Je hebt deze oefening nu afgerond. U hoeft uw e-mailcampagne niet te publiceren.

## Volgende stappen

Ga terug naar [ Adobe Experience Manager Assets &amp; Dynamische Media ](./aemassetsdm.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
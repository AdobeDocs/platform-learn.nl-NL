---
title: Aan de slag met Workfront, Frame.io en ESM
description: Aan de slag met Workfront, Frame.io en ESM
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 2f9a3eef-16ef-497c-97f7-377ff9ed2f82
source-git-commit: 8f746831d4a1481f8ccc14539273c4b16ca5170b
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# 1.8.1 Aan de slag met Workfront, Frame.io en ESM

## 1.8.1.1 Workfront Workflow Terminology

Hier volgen de belangrijkste Workfront-objecten en -concepten:

| Naam | Laatste update |
| ---------------------- | ------------ | 
| Portfolio | Een verzameling projecten met verenigende kenmerken. Deze projecten concurreren doorgaans met dezelfde middelen, hetzelfde budget of dezelfde tijd. |
| Programma | Een subset binnen een portefeuille, waar soortgelijke projecten kunnen worden gegroepeerd om een welomschreven voordeel te behalen. |
| Project | Een groot deel van de werkzaamheden moet binnen een bepaald tijdsbestek worden voltooid en moet een specifiek budget en een bepaald aantal middelen gebruiken. Om het beheersbaar te maken, verdeelt u het project in een reeks taken. Als u alle taken uitvoert, wordt het project voltooid. |
| Projectsjabloon | U kunt projectmalplaatjes gebruiken om de meeste herhaalbare processen, informatie, en montages te vangen verbonden aan de projecten in uw organisatie. Na het creëren van malplaatjes, kunt u hen aan bestaande projecten vastmaken, of u kunt hen gebruiken om nieuwe projecten te bouwen. |
| Taak | Een activiteit die als stap naar het bereiken van een definitief doel (het voltooien van het Project) moet worden uitgevoerd. Taken kunnen nooit zelfstandig bestaan. Ze maken altijd deel uit van een project. |
| Toewijzing | Een gebruiker, taakrol of team die is toegewezen aan een uitgave of een taak. Projecten, portfolio&#39;s of programma&#39;s kunnen geen toewijzingen hebben. |
| Document/versie | Elk bestand dat binnen Workfront aan een object is gekoppeld. Telkens wanneer hetzelfde document naar hetzelfde object wordt geüpload, wordt er een versienummer aan toegewezen. Gebruikers kunnen verschillende opties voor een vorige versie van een document weergeven en wijzigen. |
| Goedkeuring | Een bepaald het werkpunt, zoals een taak, een document, of een timesheet, kunnen vereisen dat een supervisor of een andere gebruiker weg op het het werkpunt ondertekent. Dit proces van het ondertekenen van weg wordt genoemd goedkeuring. |


Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Klik om **Workfront** te openen.

![ Planning van Workfront ](./images/wfpl1.png)

Dan zie je dit.

![ WF ](./images/wfb1.png)

## 1.8.1.2 Workfront-vervaging inschakelen

In de volgende stap maakt u een nieuw project met een sjabloon. Adobe Workfront biedt u een aantal beschikbare blauwdrukken die u alleen moet activeren.

Voor het gebruiksgeval van CitiSignal, is de blauwdruk **Geïntegreerde Uitvoering van de Campagne** één u moet gebruiken.

Om die blauwdruk te installeren, open het menu en selecteer **Vervagen**.

![ WF ](./images/blueprint1.png)

Selecteer de filter **Marketing** en scrol neer om de blauwdruk **Geïntegreerde Uitvoering van de Campagne** te vinden. Klik **installeren**.

![ WF ](./images/blueprint2.png)

Klik **verdergaan**.

![ WF ](./images/blueprint3.png)

Verander de **Naam van het Malplaatje van het Project** in `--aepUserLdap-- - Integrated Campaign Execution`.

Klik **installeer Vervaging**.

![ WF ](./images/blueprint4.png)

Na een paar minuten wordt de blauwdruk geïnstalleerd.

![ WF ](./images/blueprint6.png)

## 1.8.1.3 Een nieuw project maken

Open het **menu** en ga naar **Porftolios**.

![ WF ](./images/wfp6a.png)

Klik **+ Nieuwe Portfolio**.

![ WF ](./images/wfpfolio1.png)

Voer de naam van het portfolio in `--aepUserLdap-- - CitiSignal` .

![ WF ](./images/wfpfolio2.png)

Ga naar **Programma&#39;s** en klik **+ Nieuw Programma**. Selecteer **Nieuw Programma**.

![ WF ](./images/wfnp1.png)

Voer de programmanaam in: `--aepUserLdap-- - CitiSignal Fiber Launch`.

![ WF ](./images/wfp6b.png)

In uw programma, ga naar **Projecten**. Klik **+ Nieuw Project** en selecteer dan **Nieuw Project van Malplaatje**.

![ WF ](./images/wfp6.png)

Selecteer het malplaatje `--aepUserLdap-- - Integrated Campaign Execution` en klik **malplaatje van het Gebruik**.

![ WF ](./images/wfp6g.png)

Dan moet je dit zien. Verander de naam in `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` en klik **creeer project**.

![ WF ](./images/wfp6c.png)

Uw project is nu gemaakt. Ga naar **Details van het Project**.

![ WF ](./images/wfp6h.png)

Ga naar **Details van het Project**. Klik om de huidige tekst onder **Beschrijving** te selecteren.

De beschrijving instellen op `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Klik **sparen Veranderingen**.

![ WF ](./images/wfp6e.png)

Uw project is nu klaar om te worden gebruikt.

![ WF ](./images/wfp7.png)

De taken en gebiedsdelen in het project zijn gecreeerd gebaseerd op het malplaatje dat u koos en u is geplaatst als. eigenaar van het project. Het statuut van het project is geplaatst aan **Planning**. U kunt de status van het project wijzigen door een andere waarde in de lijst te selecteren.

![ WF ](./images/wfp7z.png)

## 1.8.1.4 Projectweergave in Frame.io

Ga naar [ https://next.frame.io/ ](https://next.frame.io/){target="_blank"}. Login, en selecteer de instantie aan gebruik, in dit voorbeeld **Experience Platform Internationaal ESM**. U zult merken dat een omslag reeds in Frame.io voor het project bestaat dat u enkel creeerde. De map krijgt de naam van het project dat u eerder hebt ingevoerd.

Dit is een functie van Enterprise Storage Management, een op cloud gebaseerde opslagoplossing die fungeert als centrale opslagplaats voor bedrijfsmiddelen in Adobe, waaronder Workfront en Frame.io.

De belangrijkste voordelen van Adobe Enterprise Storage zijn:

- Geïntegreerde opslaglaag voor creatieve middelen en bedrijfsbeheermiddelen
- Gecentraliseerde machtigingen via het Adobe Identity Management-systeem (IMS) voor veilig toegangsbeheer
- De zichtbaarheid van end-to-end middelen in Workfront en Frame.io
- Schaalbare opslag en quotabeheer voor bedrijfsbehoeften

![ WF ](./images/fio1.png)

## 1.8.1.5 Een nieuwe taak maken

Ga terug naar Workfront. Ga naar **Taken**, houd over de taak **beginnen om de Malplaatjes van het Ontwerp** tot stand te brengen en de 3 punten **te klikken...**.

![ WF ](./images/wfp7a.png)

Selecteer de optie **Taak van het Tussenvoegsel onder**.

![ WF ](./images/wfp7x.png)

Voer deze naam in voor uw taak: `Create layout using approved assets and copy` .

Plaats de gebied **Taken** aan de rol **Designer**.
Plaats de gebied **Duur** aan **5 dagen**.
Plaats het gebiedsvoorganger aan **9**.
Ga een datum voor de gebieden **Begin op** en **Geldig op** in (de begindatum van deze taak zou na de einddatum van de vorige taak moeten worden gepland).

Klik ergens anders op het scherm om de nieuwe taak op te slaan.

![ WF ](./images/wfp8.png)

Dan moet je dit zien. Klik op de taak om deze te openen.

![ WF ](./images/wfp9.png)

Ga naar **taakdetails** en plaats het gebied **Beschrijving** aan: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klik **sparen Veranderingen**.

![ WF ](./images/wfp9a.png)

Dan moet je dit zien. Klik het **gebied van Taken** en selecteer **toewijzen aan me**.

![ WF ](./images/wfpwlb7.png)

Klik **sparen**.

![ WF ](./images/wfpwlb8.png)

Klik **Werk op het**.

![ WF ](./images/wfpwlb9.png)

Dan moet je dit zien.

![ WF ](./images/wfpwlb10.png)

In het kader van deze taak moet een nieuw middel worden gecreëerd. In de volgende stap geeft u eerst referentieafbeeldingen op in Workfront, zodat de ontwerper weet wat er wordt verwacht. Vervolgens verandert u de rol van Designer en maakt u die asset zelf met Adobe Express.

## 1.8.1.6 Referentieafbeeldingen uploaden

Download de verwijzingsbeelden [ hier ](./assets/reference_images.zip) aan uw Desktop en unzip hen.

![ WF ](./images/wfrefimg1.png)

In Workfront, navigeer aan het **niveau van het Project**.

![ WF ](./images/wfrefimg2.png)

Ga naar **Documenten**, klik **+ voeg nieuw** toe en selecteer dan **Document**.

![ WF ](./images/wfrefimg3.png)

Navigeer naar de map die u hebt gedownload en die de referentieafbeeldingen bevat. Selecteer alle beelden en klik **Open**.

![ WF ](./images/wfrefimg4.png)

Na een paar minuten worden alle afbeeldingen geüpload en aan het project gekoppeld.

![ WF ](./images/wfrefimg5.png)

Met de referentieafbeeldingen op zijn plaats kan de ontwerper nu het nieuwe middel voor deze campagne maken.

## Volgende stappen

Volgende Stap: [ creeer een nieuw middel, herzie en keur het ](./ex2.md){target="_blank"} goed

Ga terug naar [ Verenigde Overzicht &amp; Goedkeuring met Workfront, Frame.io en het Beheer van de Opslag van de Onderneming ](./esm.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

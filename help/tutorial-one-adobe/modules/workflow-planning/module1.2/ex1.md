---
title: Aan de slag met Workfront
description: Aan de slag met Workfront
kt: 5342
doc-type: tutorial
exl-id: 0867d7fd-4d12-46d8-a5ae-bb8db1575635
source-git-commit: a63c01ebe81df39569981d62b85d0461119ecf66
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 0%

---

# 1.2.1 Workfront + AEM Assets CS Metadata Integration

>[!IMPORTANT]
>
>Als u deze bewerking wilt voltooien, hebt u toegang nodig tot een werkende AEM Assets CS Author-omgeving.
>
>Er zijn twee opties die u kunt overwegen:
>
>- Als u de GenStudio for CSC Technical Enablement workshop bijwoont, hebben uw instructeurs een AEM Assets CS Author-omgeving voor u gemaakt. Controleer bij hen wat de naam is en hoe u verder wilt gaan.
>
>- Als u de volledige Één de zelfstudie van Adobe volgt, ga [&#x200B; Adobe Experience Manager Cloud Service &amp; Edge Delivery Services &#x200B;](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.2.1.1 Workfront Workflow Terminology

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


Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/){target="_blank"}. Klik om **Workfront** te openen.

![&#x200B; Planning van Workfront &#x200B;](./../module1.1/images/wfpl1.png)

Dan zie je dit.

![&#x200B; WF &#x200B;](./images/wfb1.png)

## 1.2.1.1 Uw AEM Assets-integratie configureren

Klik het **menu** pictogram en selecteer dan **Opstelling**.

![&#x200B; WF &#x200B;](./images/wfb2.png)

In het linkermenu, scrol neer aan **Documenten** en klik dan **Experience Manager Assets**. Klik op **+ Experience Manager-integratie toevoegen** .

![&#x200B; WF &#x200B;](./images/wfb3.png)

Gebruik `--aepUserLdap-- - CitiSignal AEM` voor de naam van uw integratie.

Open de **bewaarplaats van Experience Manager** dropdown en selecteer uw instantie van AEM CS, die zou moeten worden genoemd `--aepUserLdap-- - CitiSignal`.

![&#x200B; WF &#x200B;](./images/wfb5.png)

Onder **Meta-gegevens**, vorm de volgende afbeelding:

| Workfront-veld | Experience Manager Assets-veld |
| --------------- | ------------------------------ | 
| **Document** > **Naam** | **wm:documentName** |
| **Project** > **Naam** | **wm:projectName** |
| **Project** > **Beschrijving** | **wm:projectDescription** |
| **Verzoek van het Document** > **Status** | **wm :wm: documentStatus** |
| **Taak** > **Naam** | **wm:taskName** |
| **Taak** > **Beschrijving** | **wm:taskDescription** |
| **Project** > **identiteitskaart** | **wm:projectId** |

Laat de schakelaar voor **objecten meta-gegevens van de Synchronisatie** toe.

Klik **sparen**.

![&#x200B; WF &#x200B;](./images/wfb6.png)

Uw integratie van Workfront naar AEM Assets CS is nu geconfigureerd.

![&#x200B; WF &#x200B;](./images/wfb7.png)

## 1.2.1.2 Integratie van metagegevens met AEM Assets configureren

Vervolgens moet u AEM Assets CS zodanig configureren dat de metagegevensvelden van het element in Workfront worden gedeeld met AEM Assets CS.

Om dat te doen, ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/). Klik **Experience Manager Assets**.

![&#x200B; WF &#x200B;](./images/wfbaem1.png)

Klik om de AEM Assets-omgeving te selecteren. Deze moet de naam `--aepUserLdap-- - CitiSignal dev` hebben.

![&#x200B; WF &#x200B;](./images/wfbaem2.png)

Dan moet je dit zien. In het linkermenu, ga naar **Assets**.

![&#x200B; WF &#x200B;](./images/wfbaem3.png)

Daarna, klik **creeer Omslag**.

![&#x200B; WF &#x200B;](./images/wfbaem3a.png)

Noem uw omslag `--aepUserLdap-- - CitiSignal Fiber Launch Assets` en klik **creëren**.

![&#x200B; WF &#x200B;](./images/wfbaem4.png)

Daarna, ga naar **Meta-gegevens Forms** in het linkermenu en klik dan **creeer**.

![&#x200B; WF &#x200B;](./images/wfbaem5.png)

Gebruik de naam `--aepUserLdap-- - Metadata Form` en klik **creëren**.

![&#x200B; WF &#x200B;](./images/wfbaem6.png)

Voeg 7 nieuwe **Enige gebieden van de Tekst van de Lijn** aan de vorm toe en selecteer het eerste gebied. Dan, klik het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied voor het eerste gebied.

![&#x200B; WF &#x200B;](./images/wfbaem7.png)

Dan zie je deze popup. Op het onderzoeksgebied, ga `wm:project` in en selecteer dan de gebied **Naam van het Project**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem11.png)

Wijzig de label van het veld in `Project Name` . Klik **sparen**.

![&#x200B; WF &#x200B;](./images/wfbaem12.png)

Ga naar het tweede gebied en klik het **Schema** pictogram naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem12a.png)

Op het onderzoeksgebied, ga `wm:project` in en selecteer dan de gebied **Beschrijving van het Project**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem8.png)

Wijzig de label van het veld in `Project Description` .

![&#x200B; WF &#x200B;](./images/wfbaem9.png)

Daarna, selecteer het derde gebied en klik opnieuw het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem10b.png)

Dan zie je deze popup weer. Op het onderzoeksgebied, ga `wm:project` in en selecteer dan identiteitskaart van het gebied **Project**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem10.png)

Wijzig de label van het veld in `Project ID` .

![&#x200B; WF &#x200B;](./images/wfbaem10a.png)

Daarna, selecteer het vierde gebied en klik opnieuw het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem11a.png)

Dan zie je deze popup weer. Op het onderzoeksgebied, ga `wm:document` in en selecteer dan identiteitskaart van het gebied **Project**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem101.png)

Wijzig de label van het veld in `Document Status` .

![&#x200B; WF &#x200B;](./images/wfbaem102.png)

Daarna, selecteer het vijfde gebied en klik opnieuw het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem103.png)

Dan zie je deze popup weer. Op het onderzoeksgebied, ga `wm:document` in en selecteer dan identiteitskaart van het gebied **Project**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem104.png)

Wijzig de label van het veld in `Document Name` .

![&#x200B; WF &#x200B;](./images/wfbaem105.png)

Daarna, selecteer het zesde gebied en klik opnieuw het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem106.png)

Dan zie je deze popup weer. Op het onderzoeksgebied, ga `wm:task` in en selecteer dan de 1&rbrace; Naam van de Taak van het gebied **.** Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem107.png)

Wijzig de label van het veld in `Task Name` .

![&#x200B; WF &#x200B;](./images/wfbaem108.png)

Daarna, selecteer het zevende gebied en klik opnieuw het **pictogram van het Schema** naast het **bezit van Meta-gegevens** gebied.

![&#x200B; WF &#x200B;](./images/wfbaem109.png)

Dan zie je deze popup weer. Op het onderzoeksgebied, ga `wm:task` in en selecteer dan het gebied **Beschrijving van de Taak**. Klik **Uitgezocht**.

![&#x200B; WF &#x200B;](./images/wfbaem110.png)

Wijzig de label van het veld in `Task Description` .

![&#x200B; WF &#x200B;](./images/wfbaem111.png)

Verander de **naam van het Lusje** op de vorm in `--aepUserLdap-- - Workfront Metadata`.

![&#x200B; WF &#x200B;](./images/wfbaem13.png)

Klik **sparen** en **dicht**.

![&#x200B; WF &#x200B;](./images/wfbaem13a.png)

Uw **Vorm van Meta-gegevens** wordt nu gevormd.

![&#x200B; WF &#x200B;](./images/wfbaem14.png)

Vervolgens moet u het metagegevensformulier toewijzen aan de map die u eerder hebt gemaakt. Controleer checkbox voor uw Vorm van Meta-gegevens en klik **toewijzen aan Omslag(s)**.

![&#x200B; WF &#x200B;](./images/wfbaem15.png)

Selecteer de map met de naam `--aepUserLdap-- - CitiSignal Fiber Launch Assets` . Klik **toewijzen**.

![&#x200B; WF &#x200B;](./images/wfbaem16.png)

Het metagegevensformulier is nu toegewezen aan uw map.

![&#x200B; WF &#x200B;](./images/wfbaem17.png)

Volgende Stap: [&#x200B; 1.2.2 het Bewijzen met Workfront &#x200B;](./ex2.md){target="_blank"}

Ga terug naar [&#x200B; Beheer van het Werkschema met Adobe Workfront &#x200B;](./workfront.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

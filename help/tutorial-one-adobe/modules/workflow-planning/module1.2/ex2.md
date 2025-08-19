---
title: Proofing met Workfront
description: Proofing met Workfront
kt: 5342
doc-type: tutorial
exl-id: 5feb9486-bdb4-4d59-941c-09fc2e38163b
source-git-commit: 917ebcd2dd5d8316413a183bd2c1a048c090428c
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---

# 1.2.2 Proofing met Workfront

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.2.2.1 Een nieuwe goedkeuringsstroom maken

Ga terug naar **Adobe Workfront**. Klik het **menu** pictogram en selecteer **het Bewijzen**.

![ WF ](./images/wfp1.png)

Ga naar **Werkschema&#39;s**, klik **+ Nieuw** en selecteer dan **Nieuw malplaatje**.

![ WF ](./images/wfp2.png)

Plaats de **naam van het Malplaatje** aan `--aepUserLdap-- - Approval Workflow` en plaats de **eigenaar van het Malplaatje** aan zich.

![ WF ](./images/wfp3.png)

De rol neer, en onder **Staven** > **Stadium 1**, verandert de **rol van de Maker van het Bewijs** aan **Reviewer &amp; Approver**. U kunt iedereen anders, zo als voorbeeld ook toevoegen, zelf door uw gebruiker te selecteren en de **Rol** van **Recensent &amp; Fiatteur** te plaatsen.

Klik **creëren**.

![ WF ](./images/wfp4.png)

Uw basisgoedkeuringswerkstroom is nu klaar om te worden gebruikt.

![ WF ](./images/wfp5.png)

## 1.2.2.2 Workfront-vervaging inschakelen

In de volgende stap maakt u een nieuw project met een sjabloon. Adobe Workfront biedt u een aantal beschikbare blauwdrukken die u alleen moet activeren.

Voor het gebruiksgeval van CitiSignal, is de blauwdruk **Geïntegreerde Uitvoering van de Campagne** één u moet gebruiken.

Om die blauwdruk te installeren, open het menu en selecteer **Vervagen**.

![ WF ](./images/blueprint1.png)

Selecteer de filter **Marketing** en scrol neer om de blauwdruk **Geïntegreerde Uitvoering van de Campagne** te vinden. Klik **installeren**.

![ WF ](./images/blueprint2.png)

Klik **verdergaan**.

![ WF ](./images/blueprint3.png)

Klik **installeren zoals is...**.

![ WF ](./images/blueprint4.png)

Dan moet je dit zien. De installatie kan een paar minuten duren.

![ WF ](./images/blueprint5.png)

Na een paar minuten wordt de blauwdruk geïnstalleerd.

![ WF ](./images/blueprint6.png)

## 1.2.2.3 Een nieuw project maken

Open het **menu** en ga naar **Programma&#39;s**.

![ WF ](./images/wfp6a.png)

Klik op het programma dat u eerder hebt gemaakt en dat de naam `--aepUserLdap-- CitiSignal Fiber Launch` heeft.

>[!NOTE]
>
>U creeerde een programma als deel van de oefening op [ Planning van Workfront ](./../module1.1/ex1.md) met de automatisering u creeerde en liep. Als je dat nog niet hebt gedaan, kun je daar de instructies vinden.

![ WF ](./images/wfp6b.png)

In uw programma, ga naar **Projecten**. Klik **+ Nieuw Project** en selecteer dan **Nieuw Project van Malplaatje**.

![ WF ](./images/wfp6.png)

Selecteer het malplaatje **Geïntegreerde Uitvoering van de Campagne** en klik **malplaatje van het Gebruik**.

![ WF ](./images/wfp6g.png)

Dan moet je dit zien. Verander de naam in `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` en klik **creeer project**.

![ WF ](./images/wfp6c.png)

Uw project is nu gemaakt. Ga naar **Details van het Project**.

![ WF ](./images/wfp6h.png)

Ga naar **Details van het Project**. Klik om de huidige tekst onder **Beschrijving** te selecteren.

![ WF ](./images/wfp6d.png)

De beschrijving instellen op `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Klik **sparen Veranderingen**.

![ WF ](./images/wfp6e.png)

Uw project is nu klaar om te worden gebruikt.

![ WF ](./images/wfp7.png)

De taken en gebiedsdelen in het project zijn gecreeerd gebaseerd op het malplaatje dat u koos en u is geplaatst als. eigenaar van het project. Het statuut van het project is geplaatst aan **Planning**. U kunt de status van het project wijzigen door een andere waarde in de lijst te selecteren.

![ WF ](./images/wfp7z.png)

## 1.2.2.4 Een nieuwe taak maken

Beweeg over de taak **begin om de Malplaatjes van het Ontwerp** tot stand te brengen en de 3 punten **te klikken...**.

![ WF ](./images/wfp7a.png)

Selecteer de optie **Taak van het Tussenvoegsel onder**.

![ WF ](./images/wfp7x.png)

Voer deze naam in voor uw taak: `Create layout using approved assets and copy` .

Plaats de gebied **Taken** aan de rol **Designer**.
Plaats de gebied **Duur** aan **5 dagen**.
Plaats het gebiedsvoorganger aan **9**.
Ga een datum voor de gebieden in **Begin op** en **Gelverschuldigd op**.

Klik ergens anders op het scherm om de nieuwe taak op te slaan.

![ WF ](./images/wfp8.png)

Dan moet je dit zien. Klik op de taak om deze te openen.

![ WF ](./images/wfp9.png)

Ga naar **taakdetails** en plaats het gebied **Beschrijving** aan: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klik **sparen Veranderingen**.

![ WF ](./images/wfp9a.png)

Dan moet je dit zien. Klik op het **gebied van het Project** om terug naar uw project te gaan.

![ WF ](./images/wfp9b.png)

In de **mening van het Project**, ga **de Balancer van de Werkbelasting**.

![ WF ](./images/wfpwlb1.png)

Klik **BulkToewijzingen**.

![ WF ](./images/wfpwlb2.png)

Selecteer de **taak van de Rol** van **Designer** en klik dan op het gebied **Gebruiker om** toe te wijzen. Dit zal alle gebruikers tonen die de rol van a **Designer** in uw instantie van Workfront hebben. In dit geval, selecteer de fictieve gebruiker **Melissa Jenkins**.

![ WF ](./images/wfpwlb3.png)

Klik **toewijzen**. De gebruiker u selecteerde zal nu aan de taken in het project worden toegewezen die met de **rol van Designer** verbonden zijn.

![ WF ](./images/wfpwlb4.png)

De taken worden nu toegewezen. Klik **Taken** om terug naar de **het overzichtspagina van Taken** te gaan.

![ WF ](./images/wfpwlb5.png)

Klik op de taak die u hebt gemaakt en die een naam heeft
**creeer lay-out gebruikend goedgekeurde activa en exemplaar**.

![ WF ](./images/wfpwlb6.png)

U zult nu in het kader van deze oefening aan deze taak beginnen te werken. U ziet dat Melissa Jenkins op dit moment aan deze taak is toegewezen. Om dat aan zich te veranderen, klik het **gebied van Taken** en selecteer **toewijzen aan me**.

![ WF ](./images/wfpwlb7.png)

Klik **sparen**.

![ WF ](./images/wfpwlb8.png)

Klik **Werk op het**.

![ WF ](./images/wfpwlb9.png)

Dan moet je dit zien.

![ WF ](./images/wfpwlb10.png)

Als onderdeel van deze taak moet u een nieuwe afbeelding maken en deze vervolgens als document uploaden in Workfront. U gaat dat middel nu zelf maken met Adobe Express.

## 1.2.2.5 Asset maken met Adobe Firefly Services en Adobe Express

Ga naar [ https://firefly.adobe.com/ ](https://firefly.adobe.com/){target="_blank"}. Ga de herinnering `a neon rabbit running very fast through space` in en klik **produceert**.

![ GSPeM ](./images/gsasset1.png)

Er worden dan verschillende afbeeldingen gegenereerd. Kies het beeld u van de meesten houdt, klik het **pictogram van het Aandeel** op het beeld en selecteer dan **Open in Adobe Express**.

![ GSPeM ](./images/gsasset2.png)

Vervolgens ziet u dat de afbeelding die u zojuist hebt gegenereerd, beschikbaar is in Adobe Express voor bewerking. U moet nu het CitiSignal-logo aan de afbeelding toevoegen. Om dat te doen, ga naar **Banden**.

![ GSPeM ](./images/gsasset3.png)

Vervolgens ziet u een CitiSignal-merksjabloon. die in GenStudio for Performance Marketing is gemaakt, wordt weergegeven in Adobe Express. Klik om een merksjabloon te selecteren die `CitiSignal` in de naam heeft.

![ GSPeM ](./images/gsasset4.png)

Ga naar **Logo&#39;s** en klik het **witte** embleem van het Citisignaal om het op het beeld te laten vallen.

![ GSPeM ](./images/gsasset5.png)

Plaats het CitiSignal-logo boven aan de afbeelding, niet te ver van het midden.

![ GSPeM ](./images/gsasset6.png)

Ga naar **Tekst**.

![ GSPeM ](./images/gsasset6a.png)

Klik **toevoegen uw tekst**.

![ GSPeM ](./images/gsasset6b.png)

Ga de tekst `Timetravel now!` in, verander de doopvontkleur en de doopvontgrootte, plaats de tekst aan **Vet** zodat u een beeld gelijkend op dit hebt.

![ GSPeM ](./images/gsasset6c.png)

Daarna, klik **Aandeel**.

![ GSPeM ](./images/gsasset7.png)

Selecteer **AEM Assets**.

![ GSPeM ](./images/gsasset8.png)

Wijzig de bestandsnaam in `CitiSignal - Neon Rabbit - Timetravel now!` .
Klik **Uitgezochte omslag**.

![ GSPeM ](./images/gsasset9.png)

Selecteer uw AEM Assets CS-opslagplaats met de naam `--aepUserLdap-- - CitiSignal` en selecteer vervolgens de map `--aepUserLdap-- - CitiSignal Fiber Campaign` . Klik **Uitgezocht**.

![ GSPeM ](./images/gsasset11.png)

Dan moet je dit zien. Klik **uploaden 1 activa**. Uw afbeelding wordt nu geüpload naar AEM Assets CS.

![ GSPeM ](./images/gsasset12.png)

## 1.2.2.6 Voeg een nieuw Document aan uw Taak toe en begin de goedkeuringsstroom

Ga terug naar het **scherm van het Detail van de Taak**. Ga naar **Documenten**. Klik op **+ Nieuw toevoegen** en selecteer vervolgens de AEM Assets CS-opslagplaats met de naam `--aepUserLdap-- - CitiSignal` .

![ WF ](./images/wfp10.png)

Dubbelklik om de map `--aepUserLdap-- CitiSignal Fiber Campaign` te openen.

![ WF ](./images/wfp10a.png)

Selecteer het dossier u in de vorige stap creeerde, die **CitiSignal - Neon konijn - Timetravel nu wordt genoemd!png** . Klik **Uitgezocht**.

![ WF ](./images/2048x2048.png){width="50px" align="left"}

Dan moet je dit hebben. Houd de muisaanwijzer boven het geüploade document. Klik **creeer proef** en kies dan **Geavanceerde Bewijs**.

![ WF ](./images/wfp13.png)

In het **nieuwe proefdruk** venster, selecteer **Geautomatiseerd** en selecteer dan het werkschemamalplaatje dat u eerder creeerde, dat zou moeten worden genoemd `--aepUserLdap-- - Approval Workflow`. Klik **creëren Bewijs**.

![ WF ](./images/wfp14.png)

Klik **Open Bewijs**

![ WF ](./images/wfp18.png)

U kunt de proefdruk nu controleren. Selecteer **toevoegen commentaar** om een opmerking toe te voegen die het document vereist om worden veranderd.

![ WF ](./images/wfp19.png)

Ga uw commentaar in en klik **Post**. Daarna, klik **maak een besluit**.

![ WF ](./images/wfp20.png)

Selecteer **vereiste Veranderingen** en klik **besluit** nemen.

![ WF ](./images/wfp24.png)

Ga terug naar uw **Taak** en het **Document**. U zult de vereiste tekst **Veranderingen** ook daar zien verschijnen.

![ WF ](./images/wfp25.png)

U moet nu ontwerpwijzigingen aanbrengen, die u in Adobe Express zult uitvoeren.

## 1.2.2.7 Ontwerpwijzigingen aanbrengen in Adobe Express

Ga naar [ https://new.express.adobe.com/your-stuff/files ](https://new.express.adobe.com/your-stuff/files) en open het beeld u vroeger opnieuw creeerde.

![ WF ](./images/wfp25a.png)

Wijzig de CTA-tekst in `Get On Board Now!` .

![ WF ](./images/wfp25b.png)

Klik **Aandeel** en selecteer dan **AEM Assets**.

![ WF ](./images/wfp25c.png)

Ga de naam `CitiSignal - Neon Rabbit - Get On Board Now!` in en klik dan **Uitgezochte Omslag** om een bestemmingsomslag te selecteren.

![ WF ](./images/wfp25d.png)

Selecteer uw AEM Assets CS-opslagplaats met de naam `--aepUserLdap-- - CitiSignal` en selecteer vervolgens de map `--aepUserLdap-- - CitiSignal Fiber Campaign` . Klik **Uitgezocht**.

![ WF ](./images/wfp25e.png)

Klik **uploadt 1 activa**.

![ WF ](./images/wfp25f.png)

Uw nieuwe middel wordt nu gecreeerd en opgeslagen in AEM Assets.

## 1.2.2.8 Voeg een nieuwe versie van uw Document aan uw Taak toe

Selecteer in de taakweergave in Adobe Workfront het oude afbeeldingsbestand dat niet is goedgekeurd. Dan, klik **+ voeg nieuw** toe, selecteer **Versie** en selecteer dan uw bewaarplaats van AEM Assets CS, die `--aepUserLdap-- - CitiSignal` zou moeten worden genoemd.

![ WF ](./images/wfp26.png)

Ga naar de map `--aepUserLdap-- CitiSignal Fiber Campaign` en selecteer het bestand `CitiSignal - Neon Rabit - Get On Board Now!.png` . Klik **Uitgezocht**.

![ WF ](./images/wfp26a.png)

Dan moet je dit hebben. Klik **creeer proef** en selecteer dan **Geavanceerde Bewijs** opnieuw.

![ WF ](./images/wfp28.png)

Dan zie je dit. Het **malplaatje van het Werkschema** wordt nu vooraf geselecteerd aangezien Workfront veronderstelt dat het vorige goedkeuringswerkschema nog geldig is. Klik **creëren Bewijs**.

![ WF ](./images/wfp29.png)

Selecteer **Open Bewijs**.

![ WF ](./images/wfp30.png)

U ziet nu twee versies van het bestand naast elkaar. Klik de **Compare Proofs** knoop.

![ WF ](./images/wfp31.png)

Vervolgens ziet u beide versies van de afbeelding naast elkaar. Klik **besluit van het Merk**.

![ WF ](./images/wfp32.png)

Selecteer **Goedgekeurd** en klik **besluit** opnieuw maken.

![ WF ](./images/wfp32a.png)

Sluit **vergelijkt de 1&rbrace; mening van Bewijzen &lbrace;door de linkerversie van het beeld te sluiten.** Klik de **Naam van de Taak** terug naar het overzicht van de Taak.

![ WF ](./images/wfp33.png)

U zult dan terug in uw mening van de Taak, met goedgekeurd activa zijn. Dit middel moet nu worden gedeeld met AEM Assets.

![ WF ](./images/wfp34.png)

Selecteer het goedgekeurde document. Klik het **pijlpictogram van het Aandeel** en selecteer uw integratie van AEM Assets, die zou moeten worden genoemd `--aepUserLdap-- - CitiSignal AEM`.

![ WF ](./images/wfp35.png)

Dubbelklik op de map die u eerder hebt gemaakt en die u de naam `--aepUserLdap-- - CitiSignal Fiber Launch Assets` moet geven.

![ WF ](./images/wfp36.png)

Klik **Uitgezochte omslag**.

![ WF ](./images/wfp37.png)

Na 1-2 minuten wordt uw document nu gepubliceerd in AEM Assets. Er verschijnt een AEM-pictogram naast de documentnaam.

![ WF ](./images/wfp37a.png)

Klik **Teken zoals gedaan** om deze taak te beëindigen.

![ WF ](./images/wfp37b.png)

Dan moet je dit zien.

![ WF ](./images/wfp37c.png)

## 1.2.2.9 Je bestand weergeven in AEM Assets

Ga naar de map in AEM Assets CS met de naam `--aepUserLdap-- - CitiSignal Fiber Launch Assets` .

![ WF ](./images/wfppaem1.png)

Selecteer het beeld, en kies dan **Details**.

![ WF ](./images/wfppaem2.png)

Vervolgens ziet u het eerder gemaakte metagegevensformulier met de waarden die automatisch zijn ingevuld door de integratie tussen Workfront en AEM Assets.

![ WF ](./images/wfppaem3.png)

Ga terug naar [ Beheer van het Werkschema met Adobe Workfront ](./workfront.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

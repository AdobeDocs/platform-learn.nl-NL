---
title: Proofing met Workfront
description: Proofing met Workfront
kt: 5342
doc-type: tutorial
exl-id: 5feb9486-bdb4-4d59-941c-09fc2e38163b
source-git-commit: 9af7cc3e221ddacd8b6ddc02a2215b7d9c134d0a
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---

# 1.2.2 Proofing met Workfront

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.2.2.1 Een nieuwe goedkeuringsstroom maken

Ga terug naar **Adobe Workfront**. Klik het **menu** pictogram en selecteer **het Bewijzen**.

![&#x200B; WF &#x200B;](./images/wfp1.png)

Ga naar **Werkschema&#39;s**, klik **+ Nieuw** en selecteer dan **Nieuw malplaatje**.

![&#x200B; WF &#x200B;](./images/wfp2.png)

Plaats de **naam van het Malplaatje** aan `--aepUserLdap-- - Approval Workflow` en plaats de **eigenaar van het Malplaatje** aan zich.

![&#x200B; WF &#x200B;](./images/wfp3.png)

De rol neer, en onder **Staven** > **Stadium 1**, verandert de **rol van de Maker van het Bewijs** aan **Reviewer &amp; Approver**. U kunt iedereen anders, zo als voorbeeld ook toevoegen, zelf door uw gebruiker te selecteren en de **Rol** van **Recensent &amp; Fiatteur** te plaatsen.

Klik **creëren**.

![&#x200B; WF &#x200B;](./images/wfp4.png)

Uw basisgoedkeuringswerkstroom is nu klaar om te worden gebruikt.

![&#x200B; WF &#x200B;](./images/wfp5.png)

## 1.2.2.2 Workfront-vervaging inschakelen

In de volgende stap maakt u een nieuw project met een sjabloon. Adobe Workfront biedt u een aantal beschikbare blauwdrukken die u alleen moet activeren.

Voor het gebruiksgeval van CitiSignal, is de blauwdruk **Geïntegreerde Uitvoering van de Campagne** één u moet gebruiken.

Om die blauwdruk te installeren, open het menu en selecteer **Vervagen**.

![&#x200B; WF &#x200B;](./images/blueprint1.png)

Selecteer de filter **Marketing** en scrol neer om de blauwdruk **Geïntegreerde Uitvoering van de Campagne** te vinden. Klik **installeren**.

![&#x200B; WF &#x200B;](./images/blueprint2.png)

Klik **verdergaan**.

![&#x200B; WF &#x200B;](./images/blueprint3.png)

Verander de **Naam van het Malplaatje van het Project** in `--aepUserLdap-- - Integrated Campaign Execution`.

Klik **installeren zoals is...**.

![&#x200B; WF &#x200B;](./images/blueprint4.png)

Dan moet je dit zien. De installatie kan een paar minuten duren.

![&#x200B; WF &#x200B;](./images/blueprint5.png)

Na een paar minuten wordt de blauwdruk geïnstalleerd.

![&#x200B; WF &#x200B;](./images/blueprint6.png)

## 1.2.2.3 Een nieuw project maken

Open het **menu** en ga naar **Programma&#39;s**.

![&#x200B; WF &#x200B;](./images/wfp6a.png)

Klik op het programma dat u eerder hebt gemaakt en dat de naam `--aepUserLdap-- CitiSignal Fiber Launch` heeft.

>[!NOTE]
>
>U creeerde een programma als deel van de oefening op [&#x200B; Planning van Workfront &#x200B;](./../module1.1/ex1.md) met de automatisering u creeerde en liep. Als je dat nog niet hebt gedaan, kun je daar de instructies vinden.

![&#x200B; WF &#x200B;](./images/wfp6b.png)

In uw programma, ga naar **Projecten**. Klik **+ Nieuw Project** en selecteer dan **Nieuw Project van Malplaatje**.

![&#x200B; WF &#x200B;](./images/wfp6.png)

Selecteer het malplaatje `--aepUserLdap-- - Integrated Campaign Execution` en klik **malplaatje van het Gebruik**.

![&#x200B; WF &#x200B;](./images/wfp6g.png)

Dan moet je dit zien. Verander de naam in `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` en klik **creeer project**.

![&#x200B; WF &#x200B;](./images/wfp6c.png)

Uw project is nu gemaakt. Ga naar **Details van het Project**.

![&#x200B; WF &#x200B;](./images/wfp6h.png)

Ga naar **Details van het Project**. Klik om de huidige tekst onder **Beschrijving** te selecteren.

![&#x200B; WF &#x200B;](./images/wfp6d.png)

De beschrijving instellen op `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Klik **sparen Veranderingen**.

![&#x200B; WF &#x200B;](./images/wfp6e.png)

Uw project is nu klaar om te worden gebruikt.

![&#x200B; WF &#x200B;](./images/wfp7.png)

De taken en gebiedsdelen in het project zijn gecreeerd gebaseerd op het malplaatje dat u koos en u is geplaatst als. eigenaar van het project. Het statuut van het project is geplaatst aan **Planning**. U kunt de status van het project wijzigen door een andere waarde in de lijst te selecteren.

![&#x200B; WF &#x200B;](./images/wfp7z.png)

## 1.2.2.4 Een nieuwe taak maken

Beweeg over de taak **begin om de Malplaatjes van het Ontwerp** tot stand te brengen en de 3 punten **te klikken...**.

![&#x200B; WF &#x200B;](./images/wfp7a.png)

Selecteer de optie **Taak van het Tussenvoegsel onder**.

![&#x200B; WF &#x200B;](./images/wfp7x.png)

Voer deze naam in voor uw taak: `Create layout using approved assets and copy` .

Plaats de gebied **Taken** aan de rol **Designer**.
Plaats de gebied **Duur** aan **5 dagen**.
Plaats het gebiedsvoorganger aan **9**.
Ga een datum voor de gebieden in **Begin op** en **Gelverschuldigd op**.

Klik ergens anders op het scherm om de nieuwe taak op te slaan.

![&#x200B; WF &#x200B;](./images/wfp8.png)

Dan moet je dit zien. Klik op de taak om deze te openen.

![&#x200B; WF &#x200B;](./images/wfp9.png)

Ga naar **taakdetails** en plaats het gebied **Beschrijving** aan: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klik **sparen Veranderingen**.

![&#x200B; WF &#x200B;](./images/wfp9a.png)

Dan moet je dit zien. Klik op het **gebied van het Project** om terug naar uw project te gaan.

![&#x200B; WF &#x200B;](./images/wfp9b.png)

In de **mening van het Project**, ga **de Balancer van de Werkbelasting**.

![&#x200B; WF &#x200B;](./images/wfpwlb1.png)

Klik **BulkToewijzingen**.

![&#x200B; WF &#x200B;](./images/wfpwlb2.png)

Selecteer de **taak van de Rol** van **Designer** en klik dan op het gebied **Gebruiker om** toe te wijzen. Dit zal alle gebruikers tonen die de rol van a **Designer** in uw instantie van Workfront hebben. In dit geval, selecteer de fictieve gebruiker **Melissa Jenkins**.

![&#x200B; WF &#x200B;](./images/wfpwlb3.png)

Klik **toewijzen**. De gebruiker u selecteerde zal nu aan de taken in het project worden toegewezen die met de **rol van Designer** verbonden zijn.

![&#x200B; WF &#x200B;](./images/wfpwlb4.png)

De taken worden nu toegewezen. Klik **Taken** om terug naar de **het overzichtspagina van Taken** te gaan.

![&#x200B; WF &#x200B;](./images/wfpwlb5.png)

Klik op de taak die u hebt gemaakt en die een naam heeft
**creeer lay-out gebruikend goedgekeurde activa en exemplaar**.

![&#x200B; WF &#x200B;](./images/wfpwlb6.png)

U zult nu in het kader van deze oefening aan deze taak beginnen te werken. U ziet dat Melissa Jenkins op dit moment aan deze taak is toegewezen. Om dat aan zich te veranderen, klik het **gebied van Taken** en selecteer **toewijzen aan me**.

![&#x200B; WF &#x200B;](./images/wfpwlb7.png)

Klik **sparen**.

![&#x200B; WF &#x200B;](./images/wfpwlb8.png)

Klik **Werk op het**.

![&#x200B; WF &#x200B;](./images/wfpwlb9.png)

Dan moet je dit zien.

![&#x200B; WF &#x200B;](./images/wfpwlb10.png)

Als onderdeel van deze taak moet u een nieuwe afbeelding maken en deze vervolgens als document uploaden in Workfront. U gaat dat middel nu zelf maken met Adobe Express.

## 1.2.2.5 Voeg een nieuw document toe aan uw project en start de goedkeuringsstroom

Voor deze oefening, moet u dit activa downloaden en gebruiken: [&#x200B; timetravelnow.png &#x200B;](./images/timetravelnow.png)

![&#x200B; WF &#x200B;](./images/timetravelnow.png)

Ga naar **Documenten** voor uw Taak. Klik **+ voeg nieuw** toe en selecteer dan **Document**.

![&#x200B; WF &#x200B;](./images/wfp10.png)

Klik om het bestand te selecteren `timetravelnow.png` . Klik **Open**.

![&#x200B; WF &#x200B;](./images/wfp10a.png)

Dan moet je dit hebben.

![&#x200B; WF &#x200B;](./images/wfp10b.png)

Houd de muisaanwijzer boven het geüploade document. Klik **creeer proef** en kies dan **Geavanceerde Bewijs**.

![&#x200B; WF &#x200B;](./images/wfp13.png)

In het **nieuwe proefdruk** venster, selecteer **Geautomatiseerd** en selecteer dan het werkschemamalplaatje dat u eerder creeerde, dat zou moeten worden genoemd `--aepUserLdap-- - Approval Workflow`. Klik **creëren Bewijs**.

![&#x200B; WF &#x200B;](./images/wfp14.png)

Klik **Open Bewijs**

![&#x200B; WF &#x200B;](./images/wfp18.png)

U kunt de proefdruk nu controleren. Selecteer **toevoegen commentaar** om een opmerking toe te voegen die het document vereist om worden veranderd.

![&#x200B; WF &#x200B;](./images/wfp19.png)

Ga uw commentaar in en klik **Post**. Daarna, klik **maak een besluit**.

![&#x200B; WF &#x200B;](./images/wfp20.png)

Selecteer **vereiste Veranderingen** en klik **besluit** nemen.

![&#x200B; WF &#x200B;](./images/wfp24.png)

Ga terug naar uw **Taak** en het **Document**. U zult de vereiste tekst **Veranderingen** ook daar zien verschijnen.

![&#x200B; WF &#x200B;](./images/wfp25.png)

U moet nu ontwerpwijzigingen aanbrengen en een nieuwe versie van de afbeelding uploaden.

## 1.2.2.6 Voeg een nieuwe versie van uw Document aan uw Taak toe

Voor deze oefening, moet u dit activa downloaden en gebruiken: [&#x200B; getonboard.png &#x200B;](./images/getonboard.png)

![&#x200B; WF &#x200B;](./images/getonboard.png)

Selecteer in de taakweergave in Adobe Workfront het oude afbeeldingsbestand dat niet is goedgekeurd. Dan, klik **+ voeg nieuw** toe, selecteer **Versie** en kies dan **Document**.

![&#x200B; WF &#x200B;](./images/wfp26.png)

Klik om het bestand te selecteren `getonboardnow.png` . Klik **Open**.

![&#x200B; WF &#x200B;](./images/wfp26a.png)

Dan moet je dit hebben. Klik **creeer proef** en selecteer dan **Geavanceerde Bewijs** opnieuw.

![&#x200B; WF &#x200B;](./images/wfp28.png)

Dan zie je dit. Het **malplaatje van het Werkschema** wordt nu vooraf geselecteerd aangezien Workfront veronderstelt dat het vorige goedkeuringswerkschema nog geldig is. Klik **creëren Bewijs**.

![&#x200B; WF &#x200B;](./images/wfp29.png)

Selecteer **Open Bewijs**.

![&#x200B; WF &#x200B;](./images/wfp30.png)

U ziet nu twee versies van het bestand naast elkaar. Klik de **Compare Proofs** knoop.

![&#x200B; WF &#x200B;](./images/wfp31.png)

Vervolgens ziet u beide versies van de afbeelding naast elkaar. Klik **besluit van het Merk**.

![&#x200B; WF &#x200B;](./images/wfp32.png)

Selecteer **Goedgekeurd** en klik **besluit** opnieuw maken.

![&#x200B; WF &#x200B;](./images/wfp32a.png)

Sluit **vergelijkt de 1&rbrace; mening van Bewijzen &lbrace;door de linkerversie van het beeld te sluiten.** Klik de **Naam van de Taak** terug naar het overzicht van de Taak.

![&#x200B; WF &#x200B;](./images/wfp33.png)

U zult dan terug in uw mening van de Taak, met goedgekeurd activa zijn. Dit middel moet nu worden gedeeld met AEM Assets.

![&#x200B; WF &#x200B;](./images/wfp34.png)

Selecteer het goedgekeurde document. Klik het **pijlpictogram van het Aandeel** en selecteer uw integratie van AEM Assets, die zou moeten worden genoemd `--aepUserLdap-- - CitiSignal AEM+ACCS`.

![&#x200B; WF &#x200B;](./images/wfp35.png)

Dubbelklik op de map die u eerder hebt gemaakt en die u de naam `--aepUserLdap-- - CitiSignal Fiber Campaign` moet geven.

![&#x200B; WF &#x200B;](./images/wfp36.png)

Klik **Uitgezochte omslag**.

![&#x200B; WF &#x200B;](./images/wfp37.png)

Na 1-2 minuten wordt uw document nu gepubliceerd in AEM Assets. Er verschijnt een AEM-pictogram naast de documentnaam.

![&#x200B; WF &#x200B;](./images/wfp37a.png)

Klik **Teken zoals gedaan** om deze taak te beëindigen.

![&#x200B; WF &#x200B;](./images/wfp37b.png)

Dan moet je dit zien.

![&#x200B; WF &#x200B;](./images/wfp37c.png)

## 1.2.2.7 Je bestand weergeven in AEM Assets

Ga naar de map in AEM Assets CS met de naam `--aepUserLdap-- - CitiSignal Fiber Campaign` .

![&#x200B; WF &#x200B;](./images/wfppaem1.png)

Selecteer het beeld, en kies dan **Details**.

![&#x200B; WF &#x200B;](./images/wfppaem2.png)

Vervolgens ziet u het eerder gemaakte metagegevensformulier met de waarden die automatisch zijn ingevuld door de integratie tussen Workfront en AEM Assets.

![&#x200B; WF &#x200B;](./images/wfppaem3.png)

Ga terug naar [&#x200B; Beheer van het Werkschema met Adobe Workfront &#x200B;](./workfront.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}

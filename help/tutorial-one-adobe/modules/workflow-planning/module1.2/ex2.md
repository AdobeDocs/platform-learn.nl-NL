---
title: Proofing met Workfront
description: Proofing met Workfront
kt: 5342
doc-type: tutorial
exl-id: 5feb9486-bdb4-4d59-941c-09fc2e38163b
source-git-commit: 19291afe2d8101fead734fa20212a3db76369522
workflow-type: tm+mt
source-wordcount: '810'
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

De rol neer, en onder **Staven** > **Stadium 1**, voegt me met de **Rol** van **Reviewer &amp; Approver** toe.

Klik **creëren**.

![ WF ](./images/wfp4.png)

Uw basisgoedkeuringswerkstroom is nu klaar om te worden gebruikt.

![ WF ](./images/wfp5.png)

## 1.2.2.2 Een nieuw project maken

Open het **menu** en ga naar **Programma&#39;s**.

![ WF ](./images/wfp6a.png)

Klik op het programma dat u eerder hebt gemaakt en dat de naam `--aepUserLdap-- CitiSignal Fiber Launch` heeft.

>[!NOTE]
>
>U creeerde een programma als deel van de oefening op [ Planning van Workfront ](./../module1.1/ex1.md) met de automatisering u creeerde en liep. Als je dat nog niet hebt gedaan, kun je daar de instructies vinden.

![ WF ](./images/wfp6b.png)

In uw programma, ga naar **Projecten**. Klik **+ Nieuw Project** en selecteer dan **Nieuw Project**.

![ WF ](./images/wfp6.png)

Dan moet je dit zien. Wijzig de naam in `--aepUserLdap-- - CitiSignal Fiber Launch` .

![ WF ](./images/wfp6c.png)

Ga naar **Details van het Project**. Klik **+ toevoegen** onder **Beschrijving**.

![ WF ](./images/wfp6d.png)

De beschrijving instellen op `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Klik **sparen Veranderingen**.

![ WF ](./images/wfp6e.png)

Uw project is nu gemaakt.

![ WF ](./images/wfp7.png)

## 1.2.2.3 Een nieuwe taak maken

Ga naar **Taken** en klik **+ Nieuwe Taak**.

![ WF ](./images/wfp7a.png)

Voer deze naam in voor uw taak: `Create assets for Fiber campaign` .

Plaats het gebied **Beschrijving** aan: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Klik **creëren Taak**.

![ WF ](./images/wfp8.png)

Dan moet je dit zien.

![ WF ](./images/wfp9.png)

In de kolom **Taak**, voeg uw eigen naam toe.

![ WF ](./images/wfp9a.png)

De taak zal dan aan u worden toegewezen.

![ WF ](./images/wfp9b.png)

## 1.2.2.4 Voeg een nieuw Document aan uw Taak toe ga door de goedkeuringsstroom

Klik het **Workfront** embleem terug naar de overzichtspagina. Het zojuist gemaakte project wordt dan weergegeven in het overzicht. Klik op uw project om het te openen.

![ WF ](./images/wfp9c.png)

In **Taken**, klik om de taak te openen.

![ WF ](./images/wfp9d.png)

Ga naar **Documenten**. Klik **+ voeg nieuw** toe en selecteer dan **Document**.

![ WF ](./images/wfp10.png)

Download [ dit dossier ](./images/2048x2048.png) aan uw Desktop.

![ WF ](./images/2048x2048.png){width="50px" align="left"}

Selecteer het dossier **2048x2048.png** en klik **Open**.

![ WF ](./images/wfp12.png)

Dan moet je dit hebben. Houd de muisaanwijzer boven het geüploade document. Klik **creeer proef** en kies dan **Geavanceerde Bewijs**.

![ WF ](./images/wfp13.png)

In het **nieuwe proefdruk** venster, selecteer **Geautomatiseerd** en selecteer dan het werkschemamalplaatje dat u eerder creeerde, dat zou moeten worden genoemd `--aepUserLdap-- - Approval Workflow`. Klik **creëren Bewijs**.

![ WF ](./images/wfp14.png)

Klik **Werk op het**.

![ WF ](./images/wfp17.png)

Klik **Open Bewijs**

![ WF ](./images/wfp18.png)

U kunt de proefdruk nu controleren. Selecteer **toevoegen commentaar** om een opmerking toe te voegen die het document vereist om worden veranderd.

![ WF ](./images/wfp19.png)

Ga uw commentaar in en klik **Post**. Klik **dicht**.

![ WF ](./images/wfp20.png)

Daarna, moet u uw rol van **Recensent** in **Recensent &amp; Approver** veranderen. Om dat te doen, ga terug naar uw Taak en klik **het Beproeven Werkschema**.

![ WF ](./images/wfp21.png)

Verander uw rol van **Recensent** in **Recensent &amp; Fiatteur**.

![ WF ](./images/wfp22.png)

Ga terug naar je taak en open de proefdruk opnieuw. U ziet nu een nieuwe knoop, **besluit van het Merk**. Klik erop.

![ WF ](./images/wfp23.png)

Selecteer **vereiste Veranderingen** en klik **besluit** nemen.

![ WF ](./images/wfp24.png)

Ga terug naar uw **Taak** en het **Document**. U moet nu een tweede afbeelding uploaden die rekening houdt met de opmerkingen die zijn opgegeven.

![ WF ](./images/wfp25.png)

Download [ dit dossier ](./images/2048x2048_buynow.png) aan uw Desktop.

![ dit dossier ](./images/2048x2048_buynow.png){width="50px" align="left"}

Selecteer in de taakweergave het oude afbeeldingsbestand dat niet is goedgekeurd. Dan, klik **+ voeg nieuw** toe, selecteer **Versie** en selecteer dan **Document**.

![ WF ](./images/wfp26.png)

Selecteer het dossier **2048x2048_buynow.png** en klik **Open**.

![ WF ](./images/wfp27.png)

Dan moet je dit hebben. Klik **creeer proef** en selecteer dan **Geavanceerde Bewijs** opnieuw.

![ WF ](./images/wfp28.png)

Dan zie je dit. Het **malplaatje van het Werkschema** wordt nu vooraf geselecteerd aangezien Workfront veronderstelt dat het vorige goedkeuringswerkschema nog geldig is. Klik **creëren Bewijs**.

![ WF ](./images/wfp29.png)

Selecteer **Open Bewijs**.

![ WF ](./images/wfp30.png)

U ziet nu twee versies van het bestand naast elkaar.

![ WF ](./images/wfp31.png)

Klik **besluit van het Merk**, selecteer **Goedgekeurd** en klik **besluit** opnieuw maken.

![ WF ](./images/wfp32.png)

Klik de **Naam van de Taak** terug naar het overzicht van de Taak.

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

## 1.2.2.5 Je bestand weergeven in AEM Assets

Ga naar de map in AEM Assets CS met de naam `--aepUserLdap-- - CitiSignal Fiber Launch Assets` .

![ WF ](./images/wfppaem1.png)

Selecteer het beeld, en kies dan **Details**.

![ WF ](./images/wfppaem2.png)

Vervolgens ziet u het eerder gemaakte metagegevensformulier met de waarden die automatisch zijn ingevuld door de integratie tussen Workfront en AEM Assets.

![ WF ](./images/wfppaem3.png)

Ga terug naar [ Beheer van het Werkschema met Adobe Workfront ](./workfront.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

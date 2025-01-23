---
title: Proofing met Workfront
description: Proofing met Workfront
kt: 5342
doc-type: tutorial
source-git-commit: 246bb91496104818f357848f41b79523b7771638
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 2.2.2 Proofing met Workfront

## 2.2.2.1 Nieuwe goedkeuringsstroom maken

Ga naar [ https://experienceplatform.my.workfront.com/ ](https://experienceplatform.my.workfront.com/) {target="_blank"}.

Klik het 9 punten **hamburger** pictogram en selecteren **het Bewijzen**.

![ WF ](./images/wfp1.png)

Ga naar **Werkschema&#39;s**, klik **+ Nieuw** en selecteer dan **Nieuw malplaatje**.

![ WF ](./images/wfp2.png)

Plaats de **naam van het Malplaatje** aan `--aepUserLdap-- - Approval Workflow` en plaats de **eigenaar van het Malplaatje** aan zich.

![ WF ](./images/wfp3.png)

De rol neer, en onder **Staven** > **Stadium 1**, voegt **Wouter van Geluwe** met de **Rol** van **Reviewer &amp; Approver** toe.

Klik **creëren**.

![ WF ](./images/wfp4.png)

Uw basisgoedkeuringswerkstroom is nu klaar om te worden gebruikt.

![ WF ](./images/wfp5.png)

## 2.2.2.2 Een nieuw project maken

Van de homepage van Workfront, klik **Nieuw** in **Mijn Projecten** tabel. Selecteer **Leeg Project**.

![ WF ](./images/wfp6.png)

Dan moet je dit zien. Wijzig de naam in `--aepUserLdap-- - CitiSignal Fiber Launch` .

![ WF ](./images/wfp6a.png)

Uw project is nu gemaakt.

![ WF ](./images/wfp7.png)

## 2.2.2.3 Nieuwe taak maken

Ga deze naam voor uw taak in: **creeer activa voor de campagne van de Vezel**. Klik **creëren Taak**.

![ WF ](./images/wfp8.png)

Dan moet je dit zien.

![ WF ](./images/wfp9.png)

## 2.2.2.4 Voeg een nieuw Document aan uw Taak toe gaat door de goedkeuringsstroom

Klik **+ voeg nieuw** toe en selecteer dan **Document**.

![ WF ](./images/wfp10.png)

Download [ dit dossier ](./images/2048x2048.png) aan uw Desktop.

![ WF ](./images/2048x2048.png){width="50px" align="left"}

Selecteer het dossier **2048x2048.png** en klik **Open**.

![ WF ](./images/wfp12.png)

Dan moet je dit hebben. Klik **creeer proef** en kies dan **Geavanceerde Bewijs**.

![ WF ](./images/wfp13.png)

In het **nieuwe proefdruk** venster, selecteer het werkschemamalplaatje dat u eerder creeerde, dat zou moeten worden genoemd `--aepuserLdap-- - Approval Workflow`. Klik **creëren Bewijs**.

![ WF ](./images/wfp14.png)

Dan ben je weer aan het werk. Klik **toewijzen aan** knoop en selecteer **toewijzen aan me**.

![ WF ](./images/wfp15.png)

Klik **sparen**.

![ WF ](./images/wfp16.png)

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

Dan moet je hier weer zijn. U moet nu een tweede afbeelding uploaden die rekening houdt met de opmerkingen die zijn opgegeven.

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

Sluit de proefdrukvoorvertoning.

![ WF ](./images/wfp33.png)

U zult dan terug in uw mening van de Taak, met goedgekeurd activa zijn. Dit middel moet nu worden gedeeld met AEM Assets.

![ WF ](./images/wfp34.png)

Klik het **pijlpictogram van het Aandeel** en selecteer uw integratie van AEM Assets, die zou moeten worden genoemd `--aepUserLdap-- - Citi Signal AEM`.

![ WF ](./images/wfp35.png)

Dubbelklik op de map die u eerder hebt gemaakt en die u de naam `--aepUserLdap-- - Workfront Assets` moet geven.

![ WF ](./images/wfp36.png)

Klik **Uitgezochte omslag**.

![ WF ](./images/wfp37.png)

Na 1-2 minuten wordt uw document nu gepubliceerd in AEM Assets. Er verschijnt een AEM naast de documentnaam.

![ WF ](./images/wfp37a.png)

Klik **Open samenvatting**.

![ WF ](./images/wfp38.png)

Ga naar **Meta-gegevens**, zou u dit moeten zien:

![ WF ](./images/wfp39.png)

Ga naar **Overzicht** en klik **+** toevoegen om een beschrijving toe te voegen.

![ WF ](./images/wfp40.png)

Voer je beschrijving in. Uw proefdruk- en documentinstellingen zijn nu klaar.

![ WF ](./images/wfp41.png)

## 2.2.2.5 Bekijk uw bestand in AEM Assets

Ga naar de map in AEM Assets met de naam `--aepUserLdap - Workfront Assets` .

![ WF ](./images/wfppaem1.png)

Klik de 3 punten onder uw beeld, en selecteer dan **Details**.

![ WF ](./images/wfppaem2.png)

Vervolgens ziet u het eerder gemaakte metagegevensformulier met de waarden die automatisch zijn ingevuld door de integratie tussen Workfront en AEM Assets.

![ WF ](./images/wfppaem3.png)

[ ga terug naar Module 2.2 ](./workfront.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}

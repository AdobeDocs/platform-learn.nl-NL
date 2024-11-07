---
title: Adobe Journey Optimizer - Pas personalisatie toe in een e-mailbericht
description: Deze oefening verklaart hoe te om segment personalisatie binnen een e-mailinhoud te gebruiken
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# 3.4.3 Verpersoonlijking toepassen in een e-mailbericht

Login aan Adobe Experience Cloud door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Adobe Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepTenantId--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken.

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.3.1 personalisatie op basis van segmenten

In deze exercitie zult u uw nieuwsbrief e-mailbericht met een gepersonaliseerde tekst verbeteren die op segmentlidmaatschap wordt gebaseerd.

Ga naar **Reizen**. Vind de nieuwsbrief die u in de vorige oefening hebt gecreeerd. Zoeken naar `--aepUserLdap-- - Newsletter` . Klik op uw reis om deze te openen.

![ Journey Optimizer ](./images/sbp1.png)

Dan zie je dit. Klik **Dupliceren**.

![ Journey Optimizer ](./images/sbp2.png)

Klik **Dupliceren**.

![ Journey Optimizer ](./images/sbp3.png)

Selecteer uw **E-mail** actie en klik **uitgeven inhoud**.

![ Journey Optimizer ](./images/sbp3a.png)

Klik **E-mail Designer**.

![ Journey Optimizer ](./images/sbp4.png)

Dan zie je dit.

![ Journey Optimizer ](./images/sbp5.png)

Open {de Componenten van 0} Inhoud **en sleep de component van de a** Tekst **onder de huidige nieuwsbrief inhoud.**

![ Journey Optimizer ](./images/sbp6.png)

Selecteer de volledige standaardtekst en verwijder deze. Dan klik op **verpersoonlijking** knoop in de toolbar toevoegen.

![ Journey Optimizer ](./images/sbp7.png)

U zult dan dit zien:

![ Journey Optimizer ](./images/seg1.png)

In het linkermenu, klik **Lidmaatschappen van het Segment**.

![ Journey Optimizer ](./images/seg2.png)

>[!NOTE]
>
>Als u uw segment niet in deze lijst kunt vinden, scrol neer een beetje om instructies op te zoeken hoe te om segmentidentiteitskaart manueel terug te winnen.

Selecteer het segment `Luma - Women's Category Interest` en klik het **+** pictogram, dat als volgt zou moeten kijken:

![ Journey Optimizer ](./images/seg3.png)

Vervolgens laat u de eerste regel ongewijzigd en vervangt u regel 2 en 3 door de volgende code:

``
    Psssst... a private sale in the women category will launch soon, we will keep you posted
{%else%}
    Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: READER10
{%/if%}
``

Dan heb je het volgende:

![ Journey Optimizer ](./images/seg4.png)

Klik **bevestigen** om ervoor te zorgen de code correct is. Klik **sparen**.

![ Journey Optimizer ](./images/sbp8.png)

U kunt dit bericht nu bewaren door **te klikken sparen** knoop in de hoger-juiste hoek. Dan, klik **Simuleer Inhoud**.

![ Journey Optimizer ](./images/sbp9.png)

Selecteer één van de profielen u als deel van dit leerprogramma creeerde en **Voorproef** klikt. U zult dan het resultaat van uw configuratie zien.

![ Journey Optimizer ](./images/sbp10.png)

Dan zie je dit. Dan, klik **dicht**.

![ Journey Optimizer ](./images/sbp10fff.png)

Ga terug naar het berichtdashboard door de **pijl** naast de onderwerplijntekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/sbp11.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![ Journey Optimizer ](./images/oc79afff.png)

Klik **O.K.** om uw e-mailactie te sluiten.

![ Journey Optimizer ](./images/oc79bfff.png)

Verander uw **Programma** aan **eens** en bepaal a **Datum/Tijd**. Klik **OK**.

>[!NOTE]
>
>De verzenddatum en -tijd van het bericht moeten binnen een uur liggen.

![ Journey Optimizer ](./images/sbp18.png)

Klik op de **Publish** knoop in de reis.

![ Journey Optimizer ](./images/sbp19.png)

In het pop-up venster, klik opnieuw **Publish**.

![ Journey Optimizer ](./images/sbp20.png)

Uw standaardnieuwsbrief is nu gepubliceerd. Uw e-mailbericht voor nieuwsbrieven wordt op basis van uw planning verzonden en uw reis wordt beëindigd zodra het laatste e-mailbericht is verzonden.

![ Journey Optimizer ](./images/sbp20fff.png)

U hebt deze oefening voltooid.

Volgende Stap: [ 3.4.4 Opstelling en de pushberichten van het gebruik voor iOS ](./ex4.md)

[Terug naar module 3.4](./journeyoptimizer.md)

[Terug naar alle modules](../../../overview.md)

---
title: Adobe Journey Optimizer - Pas personalisatie toe in een e-mailbericht
description: Deze oefening verklaart hoe te om segment personalisatie binnen een e-mailinhoud te gebruiken
kt: 5342
doc-type: tutorial
exl-id: bb5f8130-0237-4381-bc1e-f6b62950b1fc
source-git-commit: 9865b5697abe2d344fb530636a1afc3f152a9e8f
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# 3.4.3 Pas segment-gebaseerde verpersoonlijking in een e-mailbericht toe

Login aan Adobe Experience Cloud door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Adobe Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis &lbrace;in Journey Optimizer worden opnieuw gericht.** Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepTenantId--`` .

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.3.1 personalisatie op basis van segmenten

In deze oefening zult u het nieuwsbrief e-mailbericht verbeteren dat u in de vorige oefening met een gepersonaliseerde tekst creeerde die op segmentlidmaatschap wordt gebaseerd.

Ga naar **Campagnes**. Vind de nieuwsbrief die u in de vorige oefening hebt gecreeerd. Zoeken naar `--aepUserLdap-- - CitiSignal Newsletter` . Klik op de 3 punten **met de rechtermuisknop aan...** en klik **Dupliceren**.

![ Journey Optimizer ](./images/sbp1.png)

Dan zie je dit. Gebruik dit voor de **Titel**: `--aepUserLdap-- - CitiSignal Newsletter (SBP)`. Klik **Dupliceren**.

![ Journey Optimizer ](./images/sbp2.png)

Klik op de gedupliceerde campagne om deze te openen.

![ Journey Optimizer ](./images/sbp3.png)

Klik **uitgeven** om de inhoud te veranderen.

![ Journey Optimizer ](./images/sbp3a.png)

Klik **uitgeeft e-maillichaam**.

![ Journey Optimizer ](./images/sbp4.png)

Dan zie je dit.

![ Journey Optimizer ](./images/sbp5.png)

Open {de Componenten van 0} Inhoud **en sleep a** 1:1 kolom **boven de aanbieding AirPods.**

![ Journey Optimizer ](./images/sbp6.png)

De belemmering en laat vallen component van de a **Tekst** in die 1:1 kolom.

![ Journey Optimizer ](./images/sbp6a.png)

Selecteer de volledige standaardtekst en verwijder deze. Dan klik op **verpersoonlijking** knoop in de toolbar toevoegen.

![ Journey Optimizer ](./images/sbp7.png)

Dan zie je dit. In het linkermenu, klik **Soorten publiek**.

![ Journey Optimizer ](./images/seg1.png)

Selecteer het segment `--aepUserLdap-- - Interest in Plans` en klik **+** pictogram om het aan het canvas toe te voegen.

![ Journey Optimizer ](./images/seg3.png)

Vervolgens laat u de eerste regel ongewijzigd en vervangt u regel 2 en 3 door de volgende code:

&grave;&grave;
    PS: It may be a good idea to check if your plan still meets your needs! Click here to be contacted by one of our experts!
{%else%}
    PS: Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: NEWSLETTER10
{%/if%}
&grave;&grave;

Dan heb je dit. Klik **sparen**.

![ Journey Optimizer ](./images/seg4.png)

Verander de tekstgroepering in **groepering van het Centrum**.

![ Journey Optimizer ](./images/sbp9.png)

U kunt dit bericht nu bewaren door **te klikken sparen** knoop in de hoger-juiste hoek. Dan, klik **pijl** naast de onderwerpregel tekst in de top-left hoek.

![ Journey Optimizer ](./images/sbp9a.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./images/oc79afff.png)

Klik **activeren**.

![ Journey Optimizer ](./images/oc79bfff.png)

Uw nieuwsbrief met op segment-gebaseerde verpersoonlijking wordt nu gepubliceerd. Uw e-mailbericht voor nieuwsbrieven wordt op basis van uw planning verzonden en uw reis wordt beëindigd zodra het laatste e-mailbericht is verzonden.

Als u in aanmerking komt voor het gebruikte segment, ziet u dit in de e-mail die u ontvangt:

![ Journey Optimizer ](./images/sbp20fff.png)

U hebt deze oefening voltooid.

Volgende Stap: [ 3.4.4 Opstelling en de pushberichten van het gebruik voor iOS ](./ex4.md)

[Terug naar module 3.4](./journeyoptimizer.md)

[Terug naar alle modules](../../../overview.md)

---
title: Aan de slag met AJO Translation Services
description: Aan de slag met AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: 28c925dd-8a7b-4b9a-a128-ecbfbfbeaf04
source-git-commit: 7438a1289689c5c3fb3deb398aa9898d7ac26cf8
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 3.5.1 Vertaalbureau

## 3.5.1.1 Microsoft Azure Translator configureren

Ga naar [&#x200B; https://portal.azure.com/#home &#x200B;](https://portal.azure.com/#home).

![&#x200B; Vertalingen &#x200B;](./images/transl1.png)

Typ `translators` in de zoekbalk. Klik vervolgens op **+ Maken** .

![&#x200B; Vertalingen &#x200B;](./images/transl2.png)

Selecteer **creeer Vertaler**.

![&#x200B; Vertalingen &#x200B;](./images/transl3.png)

Kies uw **identiteitskaart van het Abonnement** en **groep van het Middel**.
Plaats **Gebied** aan **Globaal**.
Plaats **het Tarief Rij** aan **Vrije F0**.

Selecteer **Overzicht + creeer**.

![&#x200B; Vertalingen &#x200B;](./images/transl4.png)

Selecteer **creeer**.

![&#x200B; Vertalingen &#x200B;](./images/transl5.png)

Selecteer **gaan naar middel**.

![&#x200B; Vertalingen &#x200B;](./images/transl6.png)

In het linkermenu, ga naar **Beheer van het Middel** > **Sleutels en Eindpunt**. Klik om uw sleutel te kopiëren.

![&#x200B; Vertalingen &#x200B;](./images/transl7.png)

## 3.5.1.2 Landinstellingenwoordenboek

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/). Klik **Journey Optimizer**.

![&#x200B; Vertalingen &#x200B;](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Woordenboek van de Plaats**. Als u dit bericht ziet, klik **toevoegen StandaardLandinstellingen**.

![&#x200B; Vertalingen &#x200B;](./images/locale1.png)

Dan moet je dit zien.

![&#x200B; Vertalingen &#x200B;](./images/locale2.png)

## 3.5.1.3 De aanbieder van vertalingen configureren in AJO

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/). Klik **Journey Optimizer**.

![&#x200B; Vertalingen &#x200B;](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Leveranciers**. Klik **toevoegen Leverancier**.

![&#x200B; Vertalingen &#x200B;](./images/transl8.png)

Onder **Leveranciers**, uitgezochte **Vertaler van Microsoft**. Schakel het selectievakje in om het gebruik van de vertaalprovider in te schakelen. Plak de sleutel die u hebt gekopieerd van Microsoft Azure Translators. Dan, klik **Bevestig Geloofsbrieven**.

![&#x200B; Vertalingen &#x200B;](./images/transl9.png)

Uw referenties moeten dan worden gevalideerd. Als dat het geval is, schuift u omlaag om de talen voor vertaling te selecteren.

![&#x200B; Vertalingen &#x200B;](./images/transl10.png)

Selecteer `[en-US] English`, `[es] Spanish`, `[fr] French`, `[nl] Dutch` .

![&#x200B; Vertalingen &#x200B;](./images/transl11.png)

De rol omhoog en klikt **sparen**.

![&#x200B; Vertalingen &#x200B;](./images/transl12.png)

Uw **Vertaalleverancier** is nu klaar om te worden gebruikt.

![&#x200B; Vertalingen &#x200B;](./images/transl13.png)

## 3.5.1.4 Vertaalproject configureren

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/). Klik **Journey Optimizer**.

![&#x200B; Vertalingen &#x200B;](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Woordenboek van de Plaats**. Als u dit bericht ziet, klik **leidt tot Project**.

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider1.png)

Ga de naam `--aepUserLdap-- - Translations` in, plaats de **Landinstelling van Source** aan `[en-US] English - United States` en controleer checkboxes om zowel **toe te laten publiceren automatisch goedgekeurde vertalingen** en **toelaten overzichtswerkschema**. Klik vervolgens op **+ Een landinstelling toevoegen** .

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider1a.png)

Onderzoek naar `fr`, laat checkbox voor `[fr] French` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider2.png)

Onderzoek naar `es`, laat checkbox voor `[es] Spanish` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider3.png)

Onderzoek naar `nl`, laat checkbox voor `[nl] Spanish` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider6.png)

Klik **sparen**.

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider8.png)

Uw **Vertalingen** project is nu klaar om worden gebruikt.

![&#x200B; Vertalingen &#x200B;](./images/ajoprovider9.png)

## 3.5.1.5 Taalinstellingen configureren

Ga naar **Kanalen** > **Algemene Montages** > **Montages van de Taal**. Klik **creeer taalmontages**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc6.png)

Gebruik de naam `--aepUserLdap--_translations` . Selecteer **Vertaalproject**. Dan, klik **uitgeven** pictogram.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc7.png)

Selecteer het vertaalproject dat u in de vorige stap hebt gemaakt. Klik **Uitgezocht**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc8.png)

Dan moet je dit zien. Plaats de **voorkeur van de Fallback** aan **Engels - Verenigde Staten**. Klik om **te selecteren Uitgezochte de aangewezen attribuut van de profieltaal**, die zal beslissen welk gebied van het klantenprofiel om de vertalingen te gebruiken te laden. Dan, klik **uitgeven** pictogram om te selecteren welk gebied zal worden gebruikt.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc9.png)

Ga **aangewezen taal** in de onderzoeksbar in, dan selecteer het gebied **Voorkeur taal**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc10.png)

Klik **uitgeven** pictogram voor zowel **Engels - Verenigde Staten** en **Nederlands** om zijn configuratie te herzien.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc11.png)

Hier is de configuratie voor **Engels - Verenigde Staten**. Klik **annuleren**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc12.png)

Klik om de configuratie voor **Nederlands** te bekijken. Klik **annuleren**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc13.png)

De rol omhoog en klikt **voorleggen**.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc14.png)

Uw taalinstellingen zijn nu geconfigureerd.

![&#x200B; Journey Optimizer &#x200B;](./images/camploc15.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [&#x200B; 3.5.2 creeer uw Campagne &#x200B;](./ex2.md)

Ga terug naar [&#x200B; Module 3.5 &#x200B;](./ajotranslationsvcs.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../overview.md){target="_blank"}

---
title: Aan de slag met AJO Translation Services
description: Aan de slag met AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: ee0b8650-a59f-4888-8228-4caafe4143e4
source-git-commit: 3b3c62499bfed86ab13a657a816424879cab4f42
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 3.2.1 Vertaalbureau

## 3.2.1.1 Microsoft Azure Translator configureren

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home).

![ Vertalingen ](./images/transl1.png)

Typ `translators` in de zoekbalk. Klik vervolgens op **+ Maken** .

![ Vertalingen ](./images/transl2.png)

Selecteer **creeer Vertaler**.

![ Vertalingen ](./images/transl3.png)

Kies uw **identiteitskaart van het Abonnement** en **groep van het Middel**.
Plaats **Gebied** aan **Globaal**.
Plaats **het Tarief Rij** aan **Vrije F0**.

Selecteer **Overzicht + creeer**.

![ Vertalingen ](./images/transl4.png)

Selecteer **creeer**.

![ Vertalingen ](./images/transl5.png)

Selecteer **gaan naar middel**.

![ Vertalingen ](./images/transl6.png)

In het linkermenu, ga naar **Beheer van het Middel** > **Sleutels en Eindpunt**. Klik om uw sleutel te kopiëren.

![ Vertalingen ](./images/transl7.png)

## 3.2.1.2 Landinstellingenwoordenboek

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik **Journey Optimizer**.

![ Vertalingen ](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Woordenboek van de Plaats**. Als u dit bericht ziet, klik **toevoegen StandaardLandinstellingen**.

![ Vertalingen ](./images/locale1.png)

Dan moet je dit zien.

![ Vertalingen ](./images/locale2.png)

## 3.2.1.3 De aanbieder van vertalingen configureren in AJO

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik **Journey Optimizer**.

![ Vertalingen ](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Leveranciers**. Klik **toevoegen Leverancier**.

![ Vertalingen ](./images/transl8.png)

Onder **Leveranciers**, uitgezochte **Vertaler van Microsoft**. Schakel het selectievakje in om het gebruik van de vertaalprovider in te schakelen. Plak de sleutel die u hebt gekopieerd van Microsoft Azure Translators. Dan, klik **Bevestig Geloofsbrieven**.

![ Vertalingen ](./images/transl9.png)

Uw referenties moeten dan worden gevalideerd. Als dat het geval is, schuift u omlaag om de talen voor vertaling te selecteren.

![ Vertalingen ](./images/transl10.png)

Selecteer `[en-US] English`, `[es] Spanish`, `[fr] French`, `[nl] Dutch` .

![ Vertalingen ](./images/transl11.png)

De rol omhoog en klikt **sparen**.

![ Vertalingen ](./images/transl12.png)

Uw **Vertaalleverancier** is nu klaar om te worden gebruikt.

![ Vertalingen ](./images/transl13.png)

## 3.2.1.4 Het vertaalproject configureren

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Klik **Journey Optimizer**.

![ Vertalingen ](./images/ajolp1.png)

In het linkermenu, ga naar **Vertalingen** en ga dan naar **Woordenboek van de Plaats**. Als u dit bericht ziet, klik **leidt tot Project**.

![ Vertalingen ](./images/ajoprovider1.png)

Ga de naam `--aepUserLdap-- - Translations` in, plaats de **Landinstelling van Source** aan `[en-US] English - United States` en controleer checkbox om **toe te laten publiceren automatisch goedgekeurde vertalingen**. Klik vervolgens op **+ Een landinstelling toevoegen** .

![ Vertalingen ](./images/ajoprovider1a.png)

Onderzoek naar `fr`, laat checkbox voor `[fr] French` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![ Vertalingen ](./images/ajoprovider2.png)

Onderzoek naar `es`, laat checkbox voor `[es] Spanish` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![ Vertalingen ](./images/ajoprovider3.png)

Onderzoek naar `nl`, laat checkbox voor `[nl] Spanish` toe en laat dan checkbox voor **Vertaler van Microsoft** toe. Klik op **+ Een landinstelling toevoegen** .

![ Vertalingen ](./images/ajoprovider6.png)

Klik **sparen**.

![ Vertalingen ](./images/ajoprovider8.png)

Uw **Vertalingen** project is nu klaar om worden gebruikt.

![ Vertalingen ](./images/ajoprovider9.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ 3.2.2 tot uw Campagne ](./ex2.md) leiden

Ga terug naar [ Module 3.2 ](./ajotranslationsvcs.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
---
title: Aan de slag met Firefly Creative Production for Enterprise
description: Aan de slag met Firefly Creative Production for Enterprise
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 7d9ad7ec-7744-4ba6-9c11-c434e6cdef09
source-git-commit: 7850713bf116c8a9aa9dc4e055d0e501aa783cb0
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 0%

---

# 1.7.1 Aan de slag met Firefly Creative Production for Enterprise

Ga naar [ https://firefly.adobe.com ](https://firefly.adobe.com). Klik op het profielpictogram in de rechterbovenhoek en controleer of u de juiste instantie hebt geselecteerd, die `--aepImsOrgName--` moet zijn.

Ga naar **Productie**.

![ Firefly Creative Production for Enterprise ](./images/ffcw1.png)

Dan moet je dit zien. Klik **creeer werkschema (bèta)**.

![ Firefly Creative Production for Enterprise ](./images/ffcw2.png)

## 1.7.1.1 Achtergrond verwijderen

Om Firefly Creative Production for Enterprise te leren kennen, implementeert u nu een standaardgebruiksscenario dat is gericht op het verwijderen van de achtergrond van een specifieke afbeelding.

Wijzig de naam van de workflow in `vangeluw - remove background` .

![ Firefly Creative Production for Enterprise ](./images/ffcw3.png)

Open het **Beeld**

![ Firefly Creative Production for Enterprise ](./images/ffcw4.png)

Selecteer **verwijderen Achtergrond**, dan belemmering en laat vallen deze knoop op het canvas.

U moet nu een knoop van het inputbeeld en een knoop van het outputbeeld met **verbinden verwijdert Achtergrond**.

![ Firefly Creative Production for Enterprise ](./images/ffcw5.png)

De rol omhoog en gaat naar **Input en Output**. Klik de **knoop van de Beelden van de Input** en sleep het op het canvas.

![ Firefly Creative Production for Enterprise ](./images/ffcw6.png)

Dan moet je dit hebben. Verbind de **knoop van de Beelden van de Input** met **verwijder Achtergrond** knoop door over de blauwe punt naast **Beeld** op de **7} knoop van de Beelden van de Input, en tekenend een lijn aan de blauwe punt naast** Beeld van de Input **op** verwijdert Achtergrond **knoop.**

![ Firefly Creative Production for Enterprise ](./images/ffcw7.png)

Dan moet je dit hebben. Daarna, klik de **knoop van de Beelden van de Output** en sleep het op het canvas.

![ Firefly Creative Production for Enterprise ](./images/ffcw8.png)

Dan moet je dit hebben. Verbind de **verwijder Achtergrond** knoop met de **3} knoop van de Beelden van de Output door over de blauwe punt naast** Beeld van de Output **op** verwijdert Achtergrond **knoop, en tekenend een lijn aan de blauwe punt naast** Beeld **op de** knoop van de Beelden van de Output **.**

![ Firefly Creative Production for Enterprise ](./images/ffcw9.png)

Dan moet je dit hebben.

![ Firefly Creative Production for Enterprise ](./images/ffcw10.png)

Uw basisworkflow kan nu worden getest. Download het beeld [ phone.png ](./assets/phone.png) aan uw Desktop.

![ Firefly Creative Production for Enterprise ](./images/ffcw11.png)

Ga terug naar uw workflow. Klik het **belemmering en dalings** gebied van de **3} knoop van de Beelden van de Input {.**

![ Firefly Creative Production for Enterprise ](./images/ffcw11a.png)

Selecteer het dossier **phone.png**. Klik **Open**.

![ Firefly Creative Production for Enterprise ](./images/ffcw12.png)

Dan moet je dit zien. Klik **Looppas**.

![ Firefly Creative Production for Enterprise ](./images/ffcw13.png)

Na 1-2 minuten moet dit resultaat zichtbaar zijn.

![ Firefly Creative Production for Enterprise ](./images/ffcw14.png)

## 1.7.1.2 Achtergrond verwijderen + Uitsnijden

U zou a **knoop van het Gewas {nu moeten toevoegen 0} {aan het canvas.** In het menu, ga naar **Beeld** en scrol neer om **Uitsnijden** te vinden. Sleep het naar het canvas.

![ Firefly Creative Production for Enterprise ](./images/ffcw15.png)

Plaats de **knoop van het Gewas** tussen **verwijdert Achtergrond** knoop en de **knoop van het Beeld van de Output**.

U moet nu de verbinding tussen **verwijderen verwijdert Achtergrond** knoop en de **knoop van het Beeld van de Output**. U kunt dat doen door op de lijn tussen beide knooppunten te dubbelklikken.

![ Firefly Creative Production for Enterprise ](./images/ffcw16.png)

Dan moet je dit hebben. Verbind **Achtergrond** knoop aan de **knoop van het Gewas** verwijdert, en sluit dan de **knoop van het Gewas** aan de **knoop van het Beeld van de Output** aan.

![ Firefly Creative Production for Enterprise ](./images/ffcw17.png)

Controle checkbox aan **AutoUitsnijden**, en dan kunt u uw werkschema testen door **Looppas** te klikken.

![ Firefly Creative Production for Enterprise ](./images/ffcw18.png)

Na 1-2 minuten, zou u dit moeten zien, die een beeld met een verschillende resolutie nu toont.

![ Firefly Creative Production for Enterprise ](./images/ffcw19.png)

## 1.7.1.3 Achtergrond verwijderen + Uitsnijden + Samengestelde afbeelding

In het menu, onder **Beeld** selecteer a **Samengestelde Beelden (2D)** knoop en sleep het op het canvas.

![ Firefly Creative Production for Enterprise ](./images/ffcw20.png)

Voeg een tweede verbinding aan de **knoop van het Gewas** toe, door de blauwe punt naast **Uitgesneden beeld** aan de blauwe punt naast **beeld van de Input** op de **Samengestelde Beelden (2D)** knoop aan te sluiten.

![ Firefly Creative Production for Enterprise ](./images/ffcw21.png)

In het menu, onder **Input en Output**, selecteer een **3} knoop van de Tekst van de Input {en sleep het op het canvas.**

Verbind de groene punt naast **Tekst** op de **3} knoop van de Tekst van de Input {met de groene punt naast** Herinnering **op de** Samengestelde Beelden (2D) **knoop.**

![ Firefly Creative Production for Enterprise ](./images/ffcw22.png)

Dan moet je dit hebben. Ga hieronder herinnering in de **knoop van de Tekst van de Input** in.

`magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts`

In het menu, onder **Input en Output**, selecteer een **knoop van de Beelden van de Output** en sleep het op het canvas.

Verbind de blauwe punt naast **Samengesteld beeld** op de **Samengestelde Beelden (2D)** knoop met de blauwe punt naast **beeld van de Input** op de **knoop van het Beeld van de Output**.

Klik **Looppas**.

![ Firefly Creative Production for Enterprise ](./images/ffcw23.png)

Na een paar minuten, zou u iets als dit moeten zien, die uw originele beeld in een samenstelling toont die op de herinnering wordt gebaseerd die, in een specifieke resolutie werd verstrekt.

![ Firefly Creative Production for Enterprise ](./images/ffcw24.png)

## 1.7.1.4 Achtergrond verwijderen + Uitsnijden + Samengestelde afbeelding + Video genereren

In het menu, ga naar **Video**. Selecteer **produceer Video** knoop en sleep het op het canvas.

Verbind de blauwe punt naast **Samengesteld beeld** van de **Samengestelde Beelden (2D)** knoop met de blauwe punt naast **beeld van de Input** van **produceer Video** knoop.

![ Firefly Creative Production for Enterprise ](./images/ffcw25.png)

In het menu, ga naar **Input en Output**. Selecteer de **knoop van de Tekst van de Input** en sleep het op het canvas.

Verbind de groene punt naast **Tekst** op de **3} knoop van de Tekst van de Input {aan de groene punt naast** Herinnering **van** produceer Video **knoop.**

Ga de herinnering `background hearts fluttering` in de **tekst van de Input** knoop in.

In het menu, ga naar **Input en Output**. Selecteer de **Video van de Output** knoop en sleep het op het canvas.

Verbind de paarse punt naast **VideoOutput** van **produceer Video** knoop aan de paarse punt naast **Video** op de **Video van de Output** knoop.

Klik **Looppas**.

![ Firefly Creative Production for Enterprise ](./images/ffcw26.png)

Na een paar video&#39;s, zou u dit moeten zien die een video toont die op de combinatie van het verstrekte beeld en de herinnering wordt gebaseerd.

![ Firefly Creative Production for Enterprise ](./images/ffcw27.png)

## 1.7.1.5 Schalen

U hebt dit nu gedaan voor 1 afbeelding. Laten we deze workflow nu gebruiken, maar voor meerdere afbeeldingen.

Download deze afbeeldingen naar uw bureaublad:

- [ watch.jpg ](./assets/watch.jpg)
- [ airpods.jpg ](./assets/airpods.jpg)

![ Firefly Creative Production for Enterprise ](./images/ffcw28.png)

In uw werkschema, ga terug naar de eerste knoop, **Beelden van de Input**. Verwijder de momenteel geselecteerde afbeelding.

![ Firefly Creative Production for Enterprise ](./images/ffcw29.png)

Klik het **belemmering en dalings** gebied.

![ Firefly Creative Production for Enterprise ](./images/ffcw30.png)

Selecteer de 3 afbeeldingen die u hebt gedownload. Klik **Open**.

![ Firefly Creative Production for Enterprise ](./images/ffcw31.png)

Dan moet je dit zien. klik **Looppas**.

![ Firefly Creative Production for Enterprise ](./images/ffcw32.png)

Na enkele minuten ziet u een vergelijkbare uitvoer, met 3 afbeeldingen die worden gegenereerd en 3 video&#39;s.

![ Firefly Creative Production for Enterprise ](./images/ffcw33.png)

## 1.7.1.5 Opslaan in AEM Assets CS

In deze oefening, zult u de activa opslaan die als deel van uw douanewerkschema in AEM Assets CS worden gecreeerd.

Maak eerst een nieuwe map in de AEM Assets CS-omgeving.

Om dat te doen, ga naar [ https://experience.adobe.com ](https://experience.adobe.com). Klik om **Experience Manager Assets** te openen.

![ Firefly Creative Production for Enterprise ](./images/ffcw50.png)

Selecteer de AEM Assets CS-omgeving met de naam `--aepUserLdap-- - CitiSignal AEM + ACCS` .

![ Firefly Creative Production for Enterprise ](./images/ffcw51.png)

Ga naar **Assets** en klik **creeer Omslag**.

![ Firefly Creative Production for Enterprise ](./images/ffcw52.png)

Voer de naam in: `--aepUserLdap-- - Firefly Creative Production for Enterprise`. Klik **creëren**.

![ Firefly Creative Production for Enterprise ](./images/ffcw53.png)

Ga terug naar uw douanewerkschema en ga naar de **knoop van de Beelden van de Output**. Klik **Gebrek** en selecteer dan **AEM Assets**.

![ Firefly Creative Production for Enterprise ](./images/ffcw57.png)

Dan zie je deze popup. Selecteer uw AEM Assets CS-opslagplaats en selecteer vervolgens de map die u net hebt gemaakt en die u de volgende naam moet geven: `--aepUserLdap-- - Firefly Creative Production for Enterprise` . Klik **Uitgezocht**.

![ Firefly Creative Production for Enterprise ](./images/ffcw54.png)

Ga naar de **Video van de Output** knoop. Klik **Gebrek** en selecteer dan **AEM Assets**.

![ Firefly Creative Production for Enterprise ](./images/ffcw55.png)

Dan zie je deze popup. Selecteer uw AEM Assets CS-opslagplaats en selecteer vervolgens de map die u net hebt gemaakt en die u de volgende naam moet geven: `--aepUserLdap-- - Firefly Creative Production for Enterprise` . Klik **Uitgezocht**.

![ Firefly Creative Production for Enterprise ](./images/ffcw56.png)

Dan moet je dit hebben. Klik **Looppas**.

![ Firefly Creative Production for Enterprise ](./images/ffcw56a.png)

Na een paar minuten worden de gemaakte middelen beschikbaar in de map in AEM Assets CS.

![ Firefly Creative Production for Enterprise ](./images/ffcw58.png)

Ga terug naar uw workflow. Klik **publiceren**.

![ Firefly Creative Production for Enterprise ](./images/ffcw59.png)

Dan moet je dit zien.

![ Firefly Creative Production for Enterprise ](./images/ffcw60.png)

Uw workflow wordt nu gepubliceerd en kan nu via programmacode worden uitgevoerd als onderdeel van de volgende oefening.

## Volgende stappen

Ga naar [ 1.7.2 uitvoeren programmatically uw douanewerkschema ](./ex2.md){target="_blank"}

Ga terug naar [ Firefly Creative Production for Enterprise ](./workflowbuilder.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

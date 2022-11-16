---
title: Foundation - Real-time klantprofiel - Van onbekend naar bekend op de website
description: Foundation - Real-time klantprofiel - Van onbekend naar bekend op de website
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 065d79c5-8979-4992-afb1-4da47bbff74b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---

# 3.1 Van onbekend naar bekend op de website

## Context

De reis van onbekend naar bekend is tegenwoordig een van de belangrijkste onderwerpen onder merken, evenals de reis van de klant van aankoop naar bewaring.

Adobe Experience Platform speelt een enorme rol in deze reis. Platform is het brein voor communicatie, het &quot;ervaringssysteem of record&quot;.

Platform is een omgeving waarin het woord klant breder is dan alleen de bekende klanten. Een onbekende bezoeker op de website is ook een klant vanuit het perspectief van Platform en als zodanig wordt al het gedrag als onbekende bezoeker ook naar het Platform verzonden. Dankzij deze aanpak, wanneer deze bezoeker uiteindelijk een bekende klant wordt, kan een merk ook visualiseren wat er voor dat moment gebeurde. Dit helpt vanuit een attributie- en ervaringsperspectief.

## Vervoersstroom voor klanten

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![DSN](../module0/images/web8.png)

Op de **Schermen** pagina, klikt u op **Uitvoeren**.

![DSN](../module1/images/web2.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![DSN](../module0/images/web3.png)

Open een nieuw Incognito-browservenster.

![DSN](../module0/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![DSN](../module0/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![DSN](../module0/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![DSN](../module0/images/web7.png)

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![Demo](../module2/images/pv1.png)

Bekijk het deelvenster Profielviewer en het realtime klantprofiel met de **Experience Cloud-id** als primaire identificator voor deze momenteel onbekende klant.

![Demo](../module2/images/pv2.png)

U kunt ook alle Experience Events zien die zijn verzameld op basis van het gedrag van de klant. De lijst is momenteel leeg, maar dat zal binnenkort veranderen.

![Demo](../module2/images/pv3.png)

Ga naar de **Mannen** productcategorie. Klik vervolgens op het product **Montana Wind Jacket**.

![Demo](../module2/images/pv4.png)

Vervolgens ziet u de pagina met productdetails. Een ervaringsgebeurtenis van het type **Productweergave** is nu verzonden naar Adobe Experience Platform gebruikend de implementatie van SDK van het Web die u in Module 1 controleerde.

![Demo](../module2/images/pv5.png)

Open het deelvenster Providerviewer en bekijk uw **Experience Events**.

![Demo](../module2/images/pv6.png)

Ga terug naar de **Vrouwen** en klik op een ander product. Er is een andere Experience Event verzonden naar Adobe Experience Platform.

![Demo](../module2/images/pv7.png)

Open het deelvenster Profielviewer. U ziet nu 2 Experience Events van het type **Productweergave**. Hoewel het gedrag anoniem is, kunnen we elke klik volgen en deze opslaan in Adobe Experience Platform. Zodra de anonieme klant wordt gekend, zullen wij al anoniem gedrag automatisch aan het knowhowprofiel kunnen samenvoegen.

![Demo](../module2/images/pv8.png)

Ga naar de pagina Registreren/Aanmelden. Klikken **EEN ACCOUNT MAKEN**.

![Demo](../module2/images/pv9.png)

Vul uw gegevens in en klik op **Registreren** waarna u naar de vorige pagina wordt omgeleid.

![Demo](../module2/images/pv10.png)

Open het deelvenster Profielviewer en ga naar Klantprofiel in realtime. In het deelvenster Profielviewer worden al uw persoonlijke gegevens weergegeven, zoals de zojuist toegevoegde e-mail- en telefoon-id&#39;s.

![Demo](../module2/images/pv11.png)

Ga in het deelvenster Profile Viewer naar Experience Events. De twee producten die u eerder hebt bekeken, worden weergegeven in het deelvenster Profielviewer. Beide gebeurtenissen zijn nu ook verbonden met uw &#39;gekende&#39; profiel.

![Demo](../module2/images/pv12.png)

U hebt nu gegevens in Adobe Experience Platform ingevoerd en u hebt die gegevens gekoppeld aan id&#39;s zoals ECID&#39;s en e-mailadressen. Het doel hiervan is om de zakelijke context te begrijpen van wat je gaat doen. In de volgende oefening, zult u beginnen alles te vormen u nodig hebt om al die gegevensopname mogelijk te maken.

### Navigeren door de mobiele app

Nadat u een bekende klant bent geworden, is het tijd om de mobiele app te gaan gebruiken. Open de mobiele app op uw iPhone en meld u vervolgens aan bij de app.

Als u de app niet meer hebt geïnstalleerd of als u niet meer weet hoe u deze moet installeren, kunt u het volgende doen: [0.5 De mobiele app gebruiken](../module0/ex5.md)

Nadat u de app hebt geïnstalleerd zoals u is uitgelegd, ziet u de openingspagina van de app met het merk Luma geladen. Klik op het accountpictogram in het linkerbovengedeelte van het scherm.

![Demo](./images/app_hp.png)

Meld u aan met het e-mailadres dat u op de bureaubladwebsite hebt gebruikt in het aanmeldingsscherm. Klikken **Aanmelden**.

![Demo](./images/app_acc.png)

Ga naar het beginscherm van de app en klik om een product te openen.

![Demo](./images/app_hp.png)

Vervolgens ziet u de pagina met productdetails.

![Demo](./images/app_carst.png)

Ga naar het beginscherm in de app en vegen naar links op het scherm om het deelvenster Profielviewer weer te geven. Vervolgens ziet u het product dat u zojuist hebt bekeken in het dialoogvenster **Experience Events** , samen met alle productweergaven van de vorige websitesessie.

![Demo](./images/app_after_carst.png)

Ga nu terug naar uw desktopcomputer en vernieuw de homepage, waarna u het product ook daar zult zien.

![Demo](./images/lb_x_aftermobile.png)

U hebt nu gegevens in Adobe Experience Platform ingevoerd en u hebt die gegevens gekoppeld aan id&#39;s zoals ECID&#39;s en e-mailadressen. Het doel van deze oefening was om de bedrijfscontext te begrijpen van wat u op het punt staat te doen. U hebt nu effectief een real-time, cross-device klantenprofiel gebouwd. In de volgende oefening, ga u verder en visualiseer uw profiel in Adobe Experience Platform.

Volgende stap: [3.2 Visualiseer uw eigen real-time klantenprofiel - UI](./ex2.md)

[Ga terug naar module 3](./real-time-customer-profile.md)

[Terug naar alle modules](../../overview.md)

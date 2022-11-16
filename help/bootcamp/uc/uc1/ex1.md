---
title: Bootkamp - Real-time klantprofiel - Van onbekend naar bekend op de website
description: Bootkamp - Real-time klantprofiel - Van onbekend naar bekend op de website
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 32a084a3-4c04-4367-947e-f7151fdad73b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 1.1 Van onbekend naar bekend op de website

## Context

De reis van onbekend naar bekend is tegenwoordig een van de belangrijkste onderwerpen onder merken, evenals de reis van de klant van aankoop naar bewaring.

Adobe Experience Platform speelt een enorme rol in deze reis. Platform is de hersenen voor communicatie, de **ervaringssysteem**.

Platform is een omgeving waarin het woord klant breder is dan alleen de bekende klanten. Een onbekende bezoeker op de website is ook een klant vanuit het perspectief van Platform en als zodanig wordt al het gedrag als onbekende bezoeker ook naar het Platform verzonden. Dankzij deze aanpak, wanneer deze bezoeker uiteindelijk een bekende klant wordt, kan een merk ook visualiseren wat er voor dat moment gebeurde. Dit helpt vanuit een attributie- en ervaringsperspectief.

## Vervoersstroom voor klanten

Ga naar [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Klikken **Alles toestaan**.

![DSN](./images/web8.png)

Klik op het Adobe-logopictogram in de linkerbovenhoek van het scherm om de Profile Viewer te openen.

![Demo](./images/pv1.png)

Bekijk het deelvenster Profielviewer en het realtime klantprofiel met de **Experience Cloud-id** als primaire id voor deze momenteel onbekende klant.

![Demo](./images/pv2.png)

U kunt ook alle Experience Events zien die zijn verzameld op basis van het gedrag van de klant. De lijst is momenteel leeg, maar dat zal binnenkort veranderen.

![Demo](./images/pv3.png)

Ga naar de **Toepassingsservices** en klik op het product **Real-Time CDP**.

![Demo](./images/pv4.png)

Vervolgens ziet u de pagina met productdetails. Een ervaringsgebeurtenis van het type **Productweergave** is nu verzonden naar Adobe Experience Platform gebruikend de implementatie van SDK van het Web die u in Module 1 controleerde. Open het deelvenster Profielviewer en bekijk uw **Experience Events**.

![Demo](./images/pv5.png)

Ga naar de **Toepassingsservices** en klik op het product **Adobe Journey Optimizer**. Er is een andere Experience Event verzonden naar Adobe Experience Platform.

![Demo](./images/pv7.png)

Open het deelvenster Profielviewer. U ziet nu 2 Experience Events van het type **Productweergave**. Terwijl het gedrag anoniem is, wordt elke klik gevolgd en in Adobe Experience Platform opgeslagen. Zodra de anonieme klant wordt gekend, zullen wij al anoniem gedrag automatisch aan het knowhowprofiel kunnen samenvoegen.

![Demo](./images/pv8.png)

Analyseer nu uw klantenprofiel en gebruik dan uw gedrag om uw klantenervaring op de website te personaliseren.

Volgende stap: [1.2 Visualiseer uw eigen real-time klantprofiel - UI](./ex2.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)

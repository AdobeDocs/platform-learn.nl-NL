---
title: Bootkamp - Journey Optimizer Maak je reis
description: Bootkamp - Journey Optimizer Maak je reis
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Journeys
exl-id: e4464502-60c8-4fba-a429-169b7a4516c8
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 2.4 Test uw reis

## Vervoersstroom voor klanten

Open een nieuw, schoon, incognito browser venster en ga naar [ https://bootcamp.aepdemo.net ](https://bootcamp.aepdemo.net). Klik **allen** toestaan. Gebaseerd op uw het doorbladeren gedrag in de vorige gebruikersstroom, zult u personalisering zien gebeuren op de homepage van de website.

![ DSN ](./images/web8a.png)

Klik het **pictogram van het Profiel** in de hoogste juiste hoek van uw scherm.

![ Demo ](./images/web8b.png)

Klik **creeer een rekening**.

![ Demo ](./images/pv5.png)

Vul alle velden van het formulier in. Gebruik een echte waarde voor e-mailadres en telefoonnummer, aangezien deze worden gebruikt bij latere oefeningen voor het verzenden van e-mail en sms.

![ Demo ](./images/pv7a.png)

Omlaag schuiven. U moet nu de eventID invoeren van uw aangepaste gebeurtenis die u in oefening 2.2 hebt gemaakt. U kunt het hier vinden:

![ ACOP ](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de reis te activeren die u hebt gemaakt. Dit is de eventID in dit voorbeeld: `19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f`

Vul eventID op het gebied **uit Uw identiteitskaart van de Gebeurtenis van de Aanmaak van de Rekening** en klik **Register**.

![ Demo ](./images/pv8a.png)

Dan zie je dit.

![ Demo ](./images/pv9.png)

U ontvangt deze e-mail ook. Dit is de e-mail die u zelf hebt gemaakt als onderdeel van deze exercitie.

![ Demo ](./images/pv10a.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 2.5 installeer en gebruik mobiele app ](./ex5.md)

[Ga terug naar Gebruikersstroom 2](./uc2.md)

[Terug naar alle modules](../../overview.md)

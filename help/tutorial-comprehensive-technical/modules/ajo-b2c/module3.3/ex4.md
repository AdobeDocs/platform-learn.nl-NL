---
title: Offer decisioning - Test uw besluit met de demo-website
description: Uw beslissing testen met de demo-website
kt: 5342
doc-type: tutorial
exl-id: 5cc9f134-1434-4e76-9d26-9d73dbf6c0be
source-git-commit: fc24f3c9fb1683db35026dc53d0aaa055aa87e34
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 3.3.4 Combineer Adobe Target en Offer decisioning

## 3.3.4.1 Verzamel de shareable link van uw demo-project

Als u het demo-websiteproject in Adobe Target wilt laden, moet u eerst een speciale koppeling verzamelen waarmee Adobe Target uw demo-websiteproject kan laden.

Om dat te doen, ga naar [&#x200B; https://dsn.adobe.com/projects &#x200B;](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![&#x200B; RTCDP &#x200B;](./images/builder1.png)

Dit zie je nu. Ga naar **Aandeel**. Klik **produceer Verbinding** en kopieer dan de verbinding aan uw klembord.

![&#x200B; RTCDP &#x200B;](./images/builder2.png)

Ga naar [&#x200B; https://bitly.com &#x200B;](https://bitly.com), kleef de verbinding u kopieerde en **klikt creeer uw verbinding**.

![&#x200B; RTCDP &#x200B;](./images/builder4.png)

U krijgt nu een verkorte koppeling, die er als volgt uitziet: `https://adobe.ly/3PpGcFk` . Je hebt die link nodig in de volgende oefening.

![&#x200B; RTCDP &#x200B;](./images/builder5.png)

## 3.3.4.2 Verzamelen

Ga nu naar de homepage van Adobe Experience Cloud door [&#x200B; https://experiencecloud.adobe.com/ &#x200B;](https://experiencecloud.adobe.com/) te gaan. Klik **Doel**.

![&#x200B; RTCDP &#x200B;](./../../../modules/rtcdp-b2c/module2.3/images/excl.png)

Op **Adobe Target** homepage, zult u alle bestaande Activiteiten zien. Klik **creeer Activiteit** en klik dan **Ervaring richtend**.

![&#x200B; RTCDP &#x200B;](./../../../modules/rtcdp-b2c/module2.3/images/exclatov.png)

Nu uitgezochte **Visuele** en kleeft uw verkorte verbinding op het gebied **ga Activiteit URL** in. Klik **creëren**.

![&#x200B; RTCDP &#x200B;](./images/exclatcrxt1.png)

Vervolgens ziet u hoe uw demo-websiteproject wordt geladen in de Visuel Experience Composer.

>[!NOTE]
>
>Voor het geval dat uw website niet correct laadt, gelieve te installeren en deze uitbreiding van Chrome toe te laten: **de Helper van Adobe Target VEC** van de Opslag van het Web van Chrome, dan probeer opnieuw.

![&#x200B; RTCDP &#x200B;](./images/vec1.png)

Klik op het gebied dat de Disney+-aanbieding bevat. Zorg ervoor om de volledige **Container** te selecteren. Klik **Tussenvoegsel vóór** en selecteer dan **Besluit van de Aanbieding**.

![&#x200B; RTCDP &#x200B;](./images/vec3.png)

Dan zie je deze popup. Selecteer uw zandbak `--aepSandboxName--` en selecteer dan de plaatsing **Web - Beeld**.

![&#x200B; RTCDP &#x200B;](./images/vec4.png)

Selecteer vervolgens uw beslissing `--aepUserLdap-- - CitiSignal Decision` . Klik **sparen**.

![&#x200B; RTCDP &#x200B;](./images/vec5.png)

Dan zie je dit. Klik **Regel van het Overzicht**.

![&#x200B; RTCDP &#x200B;](./images/vec5a.png)

Zorg ervoor een extra malplaatjeregel **URL** **toevoegt** **uw-project-naam**. Klik **sparen**.

![&#x200B; RTCDP &#x200B;](./images/vec6.png)

Dan zie je dit. Klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/vec7.png)

Voer een naam in voor uw aanbieding. Gebruik deze naam: `--aepUserLdap-- - XT with Offers (VEC)` . Klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/vec8.png)

Dan zie je dit. Bepaal uw **metrische Goal** zoals vermeld. Klik **sparen &amp; Sluiten**.

![&#x200B; RTCDP &#x200B;](./images/vec9.png)

Je voorstel is nu gemaakt en wordt gepubliceerd. Zodra je voorstel is gepubliceerd, kun je het activeren.

![&#x200B; RTCDP &#x200B;](./images/vec11.png)

Volgende Stap: [&#x200B; 3.3.5 gebruik uw besluit in e-mail en sms &#x200B;](./ex5.md)

[Terug naar module 3.3](./offer-decisioning.md)

[Terug naar alle modules](./../../../overview.md)

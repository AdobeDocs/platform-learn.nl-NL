---
title: Offer decisioning - Test uw besluit met de demo-website
description: Uw beslissing testen met de demo-website
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# 3.3.4 Combineer Adobe Target en Offer decisioning

## 3.3.4.1 Verzamel de shareable link van uw demo-project

Als u het demo-websiteproject in Adobe Target wilt laden, moet u eerst een speciale koppeling verzamelen waarmee Adobe Target uw demo-websiteproject kan laden.

Om dat te doen, ga naar [ https://builder.adobedemo.com/projects ](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![ RTCDP ](./images/builder1.png)

Dit zie je nu. Klik **Aandeel**.

![ RTCDP ](./images/builder2.png)

Klik **produceer Verbinding** en kopieer dan de verbinding aan uw klembord.

![ RTCDP ](./images/builder3.png)

Ga naar [ https://bitly.com ](https://bitly.com), kleef de verbinding u kopieerde en klik **korter**. U krijgt nu een verkorte koppeling, die er als volgt uitziet: `https://bit.ly/3JxN7aG` . Je hebt die link nodig in de volgende oefening.

![ RTCDP ](./images/builder4.png)

## 3.3.4.2 Verzamelen

Ga nu naar de homepage van Adobe Experience Cloud door [ https://experiencecloud.adobe.com/ ](https://experiencecloud.adobe.com/) te gaan. Klik **Doel**.

![ RTCDP ](./../../../modules/rtcdp-b2c/module2.3/images/excl.png)

Op **Adobe Target** homepage, zult u alle bestaande Activiteiten zien.

![ RTCDP ](./../../../modules/rtcdp-b2c/module2.3/images/exclatov.png)

Klik op **+ Activiteit maken** om een nieuwe activiteit te maken.

![ RTCDP ](./../../../modules/rtcdp-b2c/module2.3/images/exclatcr.png)

Selecteer **Ervaring richtend**.

![ RTCDP ](./images/exclatcrxt.png)

Nu uitgezochte **Visuele** en kleeft uw verkorte verbinding op het gebied **ga Activiteit URL** in. Klik **daarna**.

![ RTCDP ](./images/exclatcrxt1.png)

Vervolgens ziet u hoe uw demo-websiteproject wordt geladen in de Visuel Experience Composer.

![ RTCDP ](./images/vec1.png)

Ga naar **doorbladeren** wijze om **te klikken allen** op popup van de koekjestoestemming toestaat.

![ RTCDP ](./images/vec2.png)

Klik het gebied dat de tekst **Aanbevolen Categorieën** bevat. Klik **Tussenvoegsel vóór** en selecteer dan **Besluit van de Aanbieding**.

![ RTCDP ](./images/vec3.png)

Dan zie je deze popup. Selecteer uw zandbak `--aepSandboxName--` en selecteer dan de plaatsing **Web - Beeld**.

![ RTCDP ](./images/vec4.png)

Selecteer vervolgens uw beslissing `--aepUserLdap-- - Luma Decision` . Klik **sparen**.

![ RTCDP ](./images/vec5.png)

Dan zie je dit. Zorg ervoor een extra malplaatjeregel **URL** **toevoegt** **uw-project-naam**. CLick **sparen**.

![ RTCDP ](./images/vec6.png)

Dan zie je dit. Klik **daarna**.

![ RTCDP ](./images/vec7.png)

Voer een naam in voor uw aanbieding. Gebruik deze naam: `--aepUserLdap-- - XT with Offers (VEC)` . Klik **daarna**.

![ RTCDP ](./images/vec8.png)

Dan zie je dit. Bepaal uw **metrische Goal** zoals vermeld. Klik **sparen &amp; Sluiten**.

![ RTCDP ](./images/vec9.png)

Je voorstel is nu gemaakt en wordt gepubliceerd.

![ RTCDP ](./images/vec10.png)

Zodra je voorstel is gepubliceerd, kun je het inschakelen.

Volgende Stap: [ 3.3.5 gebruik uw besluit in e-mail en sms ](./ex5.md)

[Terug naar module 3.3](./offer-decisioning.md)

[Terug naar alle modules](./../../../overview.md)

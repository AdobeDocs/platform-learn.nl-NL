---
title: offer decisioning - Test uw besluit met behulp van de demo-website
description: Uw beslissing testen met de demo-website
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: cdb2ba7d-bfc3-43ce-b9a1-1f0866322589
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 2%

---

# 9.4 Combineer Adobe Target en Offer decisioning

## 9.4.1 Verzamel de shareable link van uw demo-project

Als u het demo-websiteproject in Adobe Target wilt laden, moet u eerst een speciale koppeling verzamelen waarmee Adobe Target uw demo-websiteproject kan laden.

Ga om dat te doen naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![RTCDP](./images/builder1.png)

Dit zie je nu. Klikken **Delen**.

![RTCDP](./images/builder2.png)

Klikken **Koppeling genereren** en kopieer de koppeling naar het klembord.

![RTCDP](./images/builder3.png)

Ga naar [https://bitly.com](https://bitly.com), plak de gekopieerde koppeling en klik op **Shorten**. U krijgt nu een verkorte koppeling, die er als volgt uitziet: `https://bit.ly/3JxN7aG`. Je hebt die link nodig in de volgende oefening.

![RTCDP](./images/builder4.png)

## 9.4.2 Verzamelen

Ga nu naar de Adobe Experience Cloud-homepage door naar [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klikken **Doel**.

![RTCDP](../module6/images/excl.png)

Op de **Adobe Target** homepage, zult u alle bestaande Activiteiten zien.

![RTCDP](../module6/images/exclatov.png)

Klikken **+ Activiteit maken** om een nieuwe Activiteit te creëren.

![RTCDP](../module6/images/exclatcr.png)

Selecteren **Gericht op ervaring**.

![RTCDP](./images/exclatcrxt.png)

Nu selecteren **Zichtbaar** en plak uw verkorte koppeling in het veld **URL voor activiteit invoeren**. Klik op **Next**.

![RTCDP](./images/exclatcrxt1.png)

Vervolgens ziet u hoe uw demo-websiteproject wordt geladen in de Visuel Experience Composer.

![RTCDP](./images/vec1.png)

Ga naar **Bladeren** modus om te klikken **Alles toestaan** in de keuzelijst met cookies.

![RTCDP](./images/vec2.png)

Klik op het gebied dat de tekst bevat **Toprubrieken**. Klikken **Invoegen voor** en selecteer vervolgens **Beslissing voorstel**.

![RTCDP](./images/vec3.png)

Dan zie je deze popup. Sandbox selecteren `--aepSandboxId--` en selecteer vervolgens de plaatsing **Web - Afbeelding**.

![RTCDP](./images/vec4.png)

Selecteer vervolgens uw beslissing `--demoProfileLdap-- - Luma Decision`. Klikken **Opslaan**.

![RTCDP](./images/vec5.png)

Dan zie je dit. Zorg ervoor dat u een extra sjabloonregel toevoegt **URL** **contains** **your-project-name**. CLick **Opslaan**.

![RTCDP](./images/vec6.png)

Dan zie je dit. Klik op **Next**.

![RTCDP](./images/vec7.png)

Voer een naam in voor uw voorstel. Gebruik deze naam: `--demoProfileLdap-- - XT with Offers (VEC)`. Klik op **Next**.

![RTCDP](./images/vec8.png)

Dan zie je dit. Definieer uw **Goal Metric** zoals aangegeven. Klikken **Opslaan en sluiten**.

![RTCDP](./images/vec9.png)

Je voorstel is nu gemaakt en wordt gepubliceerd.

![RTCDP](./images/vec10.png)

Zodra je voorstel is gepubliceerd, kun je het inschakelen.

Volgende stap: [9.5 Gebruik uw beslissing in een e-mail en sms](./ex5.md)

[Ga terug naar module 9](./offer-decisioning.md)

[Terug naar alle modules](./../../overview.md)

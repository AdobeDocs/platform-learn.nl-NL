---
title: Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360
description: Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7a78260f-cd25-4ed0-801b-87174babaffe
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 6.3 Actie ondernemen: verzend uw segment naar DV360

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](../module2/images/sb1.png)

Ga in het linkermenu naar **Doelen** en ga vervolgens naar **Catalogus**. Dan zie je de **Doelcatalogus**.

![RTCDP](./images/rtcdpmenudest.png)

In **Doelen** klikt u op de knop **Segmenten activeren** op de **Google Display &amp; Video 360** kaart.

![RTCDP](./images/rtcdpgoogleseg.png)

Selecteer uw bestemming en klik op **Volgende**.

![RTCDP](./images/rtcdpcreatedest2.png)

Selecteer in de lijst met beschikbare segmenten het segment dat u in de vorige exercitie hebt gemaakt. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

Op de **Segmentatieschema** pagina, klikt u op **Volgende**.

![RTCDP](./images/rtcdpcreatedest4.png)

Tot slot, over de **Controleren** pagina, klikt u op **Voltooien**.

![RTCDP](./images/rtcdpcreatedest5.png)

Uw segment is nu gekoppeld aan Google DV360. Telkens wanneer een klant voor dit segment in aanmerking komt, wordt een signaal verzonden naar Google DV360 om die klant op te nemen in het Publiek aan de kant van Google DV360.

Volgende stap: [6.4 Actie nemen: verzend uw segment naar S3-bestemming](./ex4.md)

[Ga terug naar module 6](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../overview.md)

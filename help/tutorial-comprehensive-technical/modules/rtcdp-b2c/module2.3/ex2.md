---
title: Real-time CDP - Bouw een segment en neem actie - Vorm een Bestemming van Advertising zoals Google DV360
description: Real-time CDP - Bouw een segment en neem actie - Vorm een Bestemming van Advertising zoals Google DV360
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 2.3.2 Een Advertising-bestemming configureren, zoals Google DV360

>[!IMPORTANT]
>
>De hieronder inhoud is voorgenomen als FYI - u **NIET** moet een nieuwe bestemming voor DV360 vormen. De bestemming is reeds gecreeerd en u kunt het in de volgende oefening gebruiken.

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het linkermenu, ga naar **Doelen**, dan gaan naar **Catalogus**. U zult dan de **Catalogus van Doelen** zien.

![ RTCDP ](./images/rtcdp.png)

In **Doelen**, klik op **de Vertoning van Google &amp; Video 360** en klik dan **+ Opstelling**.

![ RTCDP ](./images/rtcdpgoogle.png)

Dan zie je dit. Klik **verbinden met bestemming**.

![ RTCDP ](./images/rtcdpgooglecreate1.png)

In het volgende scherm kunt u uw bestemming configureren naar Google DV360.

![ RTCDP ](./images/rtcdpgooglecreatedest.png)

Ga een waarde op de gebieden **Naam** en **Beschrijving** in.

Het gebied **identiteitskaart van de Rekening** is **Advertiser identiteitskaart** van de Rekening DV360. Dat kun je hier vinden:

![ RTCDP ](./images/rtcdpgoogledv360advid.png)

Het **Type van Rekening** zou aan **moeten worden geplaatst Advertiser** uitnodigen.

Nu heb je dit. Klik **daarna**.

![ RTCDP ](./images/rtcdpgoogldv360new.png)

>[!NOTE]
>
>Google moet Adobe toestaan voor lijsten om gegevens naar Google DV360 te kunnen verzenden. Neem contact op met uw Google-accountmanager om deze gegevensstroom in te schakelen.

Na het creëren van de bestemming, zult u dit zien. U kunt desgewenst een beleid voor gegevensbeheer selecteren. Daarna, klik **sparen en uitgang**.

![ RTCDP ](./images/rtcdpcreatedest1.png)

U zult dan een lijst van beschikbare bestemmingen zien.
In de volgende oefening, zult u het segment verbinden u in de vorige oefening bouwde aan de bestemming van Google DV360.

Volgende Stap: [ 2.3.3 Actie nemen: verzend uw segment naar DV360 ](./ex3.md)

[Terug naar module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../../overview.md)

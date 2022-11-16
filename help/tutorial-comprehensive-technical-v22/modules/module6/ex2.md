---
title: CDP in real time - Bouw een segment en neem actie - Vorm een Advertising Doel zoals Google DV360
description: CDP in real time - Bouw een segment en neem actie - Vorm een Advertising Doel zoals Google DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 40441815-428a-48dc-a12e-91220d4ba307
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 6.2 Een advertentiebestemming configureren, zoals Google DV360

>[!IMPORTANT]
>
>De onderstaande inhoud is bedoeld als FYI - U doet dit **NOT** moet een nieuwe bestemming voor DV360 vormen. De bestemming is reeds gecreeerd en u kunt het in de volgende oefening gebruiken.

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](../module2/images/sb1.png)

Ga in het linkermenu naar **Doelen** en ga vervolgens naar **Catalogus**. Dan zie je de **Doelcatalogus**.

![RTCDP](./images/rtcdp.png)

In **Doelen**, klikt u op **Google Display &amp; Video 360** en klik vervolgens op **+ Instellen**.

![RTCDP](./images/rtcdpgoogle.png)

Dan zie je dit. Klikken **Verbinden met doel**.

![RTCDP](./images/rtcdpgooglecreate1.png)

In het volgende scherm kunt u uw bestemming configureren naar Google DV360.

![RTCDP](./images/rtcdpgooglecreatedest.png)

Geef een waarde op in de velden **Naam** en **Beschrijving**.

Het veld **Account-id** is de **Adverteerder-id** van de DV360-rekening. U kunt dat hier vinden:

![RTCDP](./images/rtcdpgoogledv360advid.png)

De **Accounttype** moet worden ingesteld op **Adverteerder uitnodigen**.

Nu heb je dit. Klik op **Next**.

![RTCDP](./images/rtcdpgoogldv360new.png)

>[!NOTE]
>
>Google moet de lijst met Adobe toestaan om gegevens naar Google DV360 te kunnen verzenden. Neem contact op met uw Google-accountmanager om deze gegevensstroom in te schakelen.

Na het creëren van de bestemming, zult u dit zien. U kunt desgewenst een beleid voor gegevensbeheer selecteren. Klik op Volgende **Opslaan en afsluiten**.

![RTCDP](./images/rtcdpcreatedest1.png)

U zult dan een lijst van beschikbare bestemmingen zien.
In de volgende oefening, zult u het segment verbinden u in de vorige oefening bouwde aan de bestemming van Google DV360.

Volgende stap: [6.3 Actie ondernemen: verzend uw segment naar DV360](./ex3.md)

[Ga terug naar module 6](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../overview.md)

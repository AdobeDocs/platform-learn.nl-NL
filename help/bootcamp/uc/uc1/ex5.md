---
title: Bootkamp - Real-time CDP - Bouw een publiek op en neem actie - verzend uw publiek naar DV360
description: Bootkamp - Real-time CDP - Bouw een publiek en neem actie - verzend uw publiek naar DV360
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: 31f46e37-f1c0-4730-8520-1ccd98df6501
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# 1.5 Actie nemen: stuur je publiek naar Facebook

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

Ga in het linkermenu naar **Doelen** en ga vervolgens naar **Catalogus**. Dan zie je de **Doelcatalogus**. In **Doelen**, klikt u op **Soorten publiek activeren** op de **Facebook Aangepast publiek** kaart.

![RTCDP](./images/rtcdpgoogleseg.png)

Het doel selecteren **bootkamp-facebook** en klik op **Volgende**.

![RTCDP](./images/rtcdpcreatedest2.png)

Selecteer in de lijst met beschikbare doelgroepen het publiek dat u in de vorige oefening hebt gemaakt. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

Op de **Toewijzing** pagina, zorg ervoor dat **Transformatie toepassen** selectievakje is ingeschakeld. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Op de **Poortschema** pagina, selecteert u de **Oorsprong van uw publiek** en stel deze in op **Direct van klanten**. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest4.png)

Tot slot, over de **Controleren** pagina, klikt u **Voltooien**.

![RTCDP](./images/rtcdpcreatedest5.png)

Uw publiek is nu gekoppeld aan het aangepaste publiek van Facebook. Telkens wanneer een klant voor dit publiek in aanmerking komt, wordt een signaal verzonden naar de Facebook-server om die klant op te nemen in het aangepaste publiek aan Facebook-zijde.

In Facebook vindt u uw publiek in Adobe Experience Platform onder Aangepast publiek:

![RTCDP](./images/rtcdpcreatedest5b.png)

Je kunt nu een aangepast publiek weergeven in Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)

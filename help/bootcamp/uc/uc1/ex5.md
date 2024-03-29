---
title: Bootkamp - Echte-tijd CDP - bouw een segment en neem actie - verzend uw segment naar DV360
description: Bootkamp - Echte-tijd CDP - bouw een segment en neem actie - verzend uw segment naar DV360
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: 31f46e37-f1c0-4730-8520-1ccd98df6501
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 3%

---

# 1.5 Actie nemen: Uw segment verzenden naar Facebook

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensopname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensopname](./images/sb1.png)

Ga in het linkermenu naar **Doelen** en ga vervolgens naar **Catalogus**. Dan zie je de **Doelcatalogus**. In **Doelen**, klikt u op **Segmenten activeren** op de **Facebook Aangepast publiek** kaart.

![RTCDP](./images/rtcdpgoogleseg.png)

Het doel selecteren **bootkamp-facebook** en klik op **Volgende**.

![RTCDP](./images/rtcdpcreatedest2.png)

Selecteer in de lijst met beschikbare segmenten het segment dat u in de vorige exercitie hebt gemaakt. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

Op de **Toewijzing** pagina, zorg ervoor dat **Transformatie toepassen** selectievakje is ingeschakeld. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Op de **Segmentatieschema** pagina, selecteert u de **Oorsprong van uw publiek** en stel deze in op **Direct van klanten**. Klik op **Next**.

![RTCDP](./images/rtcdpcreatedest4.png)

Tot slot, over de **Controleren** pagina, klikt u op **Voltooien**.

![RTCDP](./images/rtcdpcreatedest5.png)

Uw segment is nu gekoppeld aan Aangepast publiek van Facebook. Telkens wanneer een klant voor dit segment in aanmerking komt, wordt een signaal verzonden naar de Facebook-server om die klant op te nemen in het aangepaste publiek aan Facebook-zijde.

In Facebook vindt u uw segment van Adobe Experience Platform onder Aangepast publiek:

![RTCDP](./images/rtcdpcreatedest5b.png)

Je kunt nu een aangepast publiek weergeven in Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
